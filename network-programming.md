Okay, let's create a comprehensive tutorial on network programming in C# 12 and .NET 8, focusing on creating servers and making HTTP requests. We'll then build a network monitoring application as a practical project.

**Chapter 5: Network Programming in C# 12 and .NET 8**

**5.1 Introduction to Network Programming**

Network programming involves writing applications that communicate with each other over a network (like the internet or a local network). Key concepts include:

* **IP Addresses:** Unique addresses that identify devices on a network (e.g., 192.168.1.1).
* **Ports:** Virtual endpoints on a device used to direct network traffic to specific applications (e.g., port 80 for HTTP, port 443 for HTTPS).
* **Protocols:** Sets of rules that govern how data is formatted and transmitted (e.g., TCP, UDP, HTTP).
* **Sockets:** Programming interfaces that allow applications to send and receive data over a network.
* **Clients and Servers:**
  * **Client:** Initiates a connection to a server.
  * **Server:** Listens for incoming connections from clients.

**5.2 TCP/IP Basics**

TCP (Transmission Control Protocol) and IP (Internet Protocol) are the foundation of much of the internet.

* **TCP:** A connection-oriented protocol that provides reliable, ordered delivery of data. It establishes a connection before transmitting data and uses acknowledgments to ensure delivery.
* **IP:** A connectionless protocol responsible for addressing and routing data packets across networks.

**5.3 Working with `TcpClient` and `TcpListener`**

These are the fundamental classes for TCP communication in .NET.

* **`TcpClient`:** Used to create client applications that connect to TCP servers.

    ```csharp
    using System.Net.Sockets;
    using System.Text;

    public class TcpClientExample
    {
        public static async Task ConnectAndSendAsync(string server, int port, string message)
        {
            try
            {
                using TcpClient client = new();
                await client.ConnectAsync(server, port); // Connect to the server

                using NetworkStream stream = client.GetStream();

                // Send data
                byte[] data = Encoding.ASCII.GetBytes(message);
                await stream.WriteAsync(data);

                Console.WriteLine($"Sent: {message}");

                // Receive response (optional)
                data = new byte[256];
                int bytes = await stream.ReadAsync(data);
                string responseData = Encoding.ASCII.GetString(data, 0, bytes);
                Console.WriteLine($"Received: {responseData}");
            }
            catch (SocketException ex)
            {
                Console.WriteLine($"Socket error: {ex.SocketErrorCode} - {ex.Message}");
            }
            catch (WebSocketException ex)
            {
                Console.WriteLine($"WebSocket error: {ex.WebSocketErrorCode} - {ex.Message}");
            }
            catch (IOException ex)
            {
                Console.WriteLine($"IO error: {ex.Message}");
            }
            catch (ObjectDisposedException)
            {
                Console.WriteLine("Connection was unexpectedly closed");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.GetType().Name} - {ex.Message}");
            }
        }
    }
    ```

* **`TcpListener`:** Used to create server applications that listen for incoming TCP connections.

    ```csharp
    using System.Net;
    using System.Net.Sockets;
    using System.Text;

    public class TcpListenerExample
    {
        public static async Task StartListenerAsync(int port)
        {
            TcpListener server = null;
            try
            {
                // Listen on all network interfaces
                IPAddress localAddr = IPAddress.Any; 
                server = new TcpListener(localAddr, port);
                server.Start();

                Console.WriteLine("Waiting for a connection...");

                while (true)
                {
                    TcpClient client = await server.AcceptTcpClientAsync(); // Accept connection
                    Console.WriteLine("Connected!");

                    _ = HandleClientAsync(client); // Handle client communication asynchronously
                }
            }
            catch (SocketException ex)
            {
                Console.WriteLine($"Socket error: {ex.SocketErrorCode} - {ex.Message}");
            }
            catch (IOException ex)
            {
                Console.WriteLine($"IO error: {ex.Message}");
            }
            catch (ObjectDisposedException)
            {
                Console.WriteLine("Connection was unexpectedly closed");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.GetType().Name} - {ex.Message}");
            }
            finally
            {
                server?.Stop();
            }
        }

        static async Task HandleClientAsync(TcpClient client)
        {
            try
            {
                using NetworkStream stream = client.GetStream();
                byte[] data = new byte[256];
                int bytes;

                // Read data from client
                while ((bytes = await stream.ReadAsync(data)) != 0)
                {
                    string requestData = Encoding.ASCII.GetString(data, 0, bytes);
                    Console.WriteLine($"Received: {requestData}");

                    // Send response (echo)
                    string responseMessage = $"Echo: {requestData}";
                    byte[] responseData = Encoding.ASCII.GetBytes(responseMessage);
                    await stream.WriteAsync(responseData);
                    Console.WriteLine($"Sent: {responseMessage}");
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Client handler exception: {ex.Message}");
            }
            finally
            {
                client.Close();
            }
        }
    }
    ```

**5.4 Building a Simple HTTP Server**

Let's create a basic HTTP server that can handle GET requests.

```csharp
using System;
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Threading.Tasks;

public class SimpleHttpServer
{
    private readonly TcpListener _listener;
    private readonly int _port;

    public SimpleHttpServer(int port)
    {
        _port = port;
        _listener = new TcpListener(IPAddress.Any, port);
    }

    public async Task StartAsync()
    {
        _listener.Start();
        Console.WriteLine($"HTTP Server listening on port {_port}...");

        while (true)
        {
            TcpClient client = await _listener.AcceptTcpClientAsync();
            _ = HandleClientAsync(client);
        }
    }

    private async Task HandleClientAsync(TcpClient client)
    {
        using NetworkStream stream = client.GetStream();
        using StreamReader reader = new(stream, Encoding.ASCII);
        using StreamWriter writer = new(stream, Encoding.ASCII) { AutoFlush = true };

        try
        {
            // Read request line
            string requestLine = await reader.ReadLineAsync();
            Console.WriteLine($"Received request: {requestLine}");

            string[] requestParts = requestLine?.Split(' ');
            if (requestParts?.Length == 3 && requestParts[0] == "GET")
            {
                string requestedPath = requestParts[1];

                // Basic file serving (very simplified)
                if (requestedPath == "/")
                {
                    requestedPath = "/index.html"; // Default to index.html
                }

                string filePath = $"wwwroot{requestedPath}"; // Assuming a wwwroot folder

                if (File.Exists(filePath))
                {
                    string contentType = GetContentType(filePath);
                    string fileContent = await File.ReadAllTextAsync(filePath);

                    // Send response headers
                    await writer.WriteLineAsync("HTTP/1.1 200 OK");
                    await writer.WriteLineAsync($"Content-Type: {contentType}");
                    await writer.WriteLineAsync($"Content-Length: {fileContent.Length}");
                    await writer.WriteLineAsync(); // Empty line to separate headers and body

                    // Send response body
                    await writer.WriteAsync(fileContent);
                }
                else
                {
                    // 404 Not Found
                    await writer.WriteLineAsync("HTTP/1.1 404 Not Found");
                    await writer.WriteLineAsync();
                }
            }
            else
            {
                // 400 Bad Request
                await writer.WriteLineAsync("HTTP/1.1 400 Bad Request");
                await writer.WriteLineAsync();
            }
        }
        catch (SocketException ex)
        {
            Console.WriteLine($"Socket error: {ex.SocketErrorCode} - {ex.Message}");
        }
        catch (IOException ex)
        {
            Console.WriteLine($"IO error: {ex.Message}");
        }
        catch (ObjectDisposedException)
        {
            Console.WriteLine("Connection was unexpectedly closed");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Unexpected error: {ex.GetType().Name} - {ex.Message}");
        }
        finally
        {
            client.Close();
        }
    }

    private string GetContentType(string filePath)
    {
        string extension = Path.GetExtension(filePath).ToLowerInvariant();
        switch (extension)
        {
            case ".html":
            case ".htm":
                return "text/html";
            case ".txt":
                return "text/plain";
            case ".css":
                return "text/css";
            case ".js":
                return "application/javascript";
            case ".jpg":
            case ".jpeg":
                return "image/jpeg";
            case ".png":
                return "image/png";
            default:
                return "application/octet-stream"; // Default binary
        }
    }
}
```

**To run this server:**

1. Create a folder named `wwwroot` in your project directory.
2. Place an `index.html` file (or other files) inside `wwwroot`.
3. In your `Program.cs`, add:

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        SimpleHttpServer server = new SimpleHttpServer(8080);
        await server.StartAsync();
    }
}
```

Now, you can access the server in your browser at `http://localhost:8080/`.

**5.5 Making HTTP Requests with `HttpClient`**

`HttpClient` is the recommended class for making HTTP requests in .NET.

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
using System.Net.Http.Json; // For JSON extension methods
using System.Text;

public class HttpClientExamples
{
    public static async Task MakeGetRequestAsync(string url)
    {
        using HttpClient client = new();
        try
        {
            HttpResponseMessage response = await client.GetAsync(url);
            response.EnsureSuccessStatusCode(); // Throws if not successful

            string responseBody = await response.Content.ReadAsStringAsync();
            Console.WriteLine(responseBody);
        }
        catch (HttpRequestException ex)
        {
            Console.WriteLine($"Request error: {ex.Message}");
        }
    }

    public static async Task MakePostRequestAsync(string url, object data)
    {
        using HttpClient client = new();
        try
        {
            // Serialize data to JSON (if it's not already a string or byte[])
            string jsonData = System.Text.Json.JsonSerializer.Serialize(data);
            StringContent content = new(jsonData, Encoding.UTF8, "application/json");

            HttpResponseMessage response = await client.PostAsync(url, content);
            response.EnsureSuccessStatusCode();

            string responseBody = await response.Content.ReadAsStringAsync();
            Console.WriteLine(responseBody);
        }
        catch (HttpRequestException ex)
        {
            Console.WriteLine($"Request error: {ex.Message}");
        }
    }

    public static async Task DownloadFileAsync(string url, string filePath)
    {
        using HttpClient client = new();
        try
        {
            using Stream stream = await client.GetStreamAsync(url);
            using FileStream fileStream = new(filePath, FileMode.Create);
            await stream.CopyToAsync(fileStream);
        }
        catch (HttpRequestException ex)
        {
            Console.WriteLine($"Download error: {ex.Message}");
        }
    }

    public static async Task SendHeadersAsync(string url)
    {
        using HttpClient client = new();
        try
        {
            client.DefaultRequestHeaders.Add("X-Custom-Header", "MyValue");

            HttpResponseMessage response = await client.GetAsync(url);

            // ... process response
        }
        catch (HttpRequestException ex)
        {
            Console.WriteLine($"Request error: {ex.Message}");
        }
    }

    // Example of using HttpClient with JSON serialization/deserialization
    public record User(string Name, int Age);

    public static async Task PostJsonAsync(string url)
    {
        using HttpClient client = new();

        var user = new User("Alice", 30);

        // Post as JSON (using extension method)
        HttpResponseMessage response = await client.PostAsJsonAsync(url, user);
        response.EnsureSuccessStatusCode();

        // Read response as JSON (using extension method)
        User createdUser = await response.Content.ReadFromJsonAsync<User>();
        Console.WriteLine($"Created user: {createdUser.Name}, {createdUser.Age}");
    }
}
```

**5.6 Using `HttpClientFactory` (Recommended for Long-Lived Applications)**

In ASP.NET Core and other applications that run for a long time, directly instantiating `HttpClient` can lead to socket exhaustion. `HttpClientFactory` helps manage the lifetime of `HttpClient` instances and provides additional benefits:

* Centralized configuration of HTTP clients
* Automatic disposal of HttpClientMessageHandlers
* Integration with dependency injection
* Support for named and typed clients
* Built-in retry and circuit breaker policies

**Basic Setup:**

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

var builder = Host.CreateApplicationBuilder(args);

// Register HttpClientFactory with default configuration
builder.Services.AddHttpClient();

// Register named client with custom configuration
builder.Services.AddHttpClient("GitHubClient", client =>
{
    client.BaseAddress = new Uri("https://api.github.com/");
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    client.DefaultRequestHeaders.UserAgent.ParseAdd("MyApp/1.0");
    client.Timeout = TimeSpan.FromSeconds(30);
});

// Register typed client
builder.Services.AddHttpClient<GitHubService>();

using var host = builder.Build();

// Example usage of named client
var httpClientFactory = host.Services.GetRequiredService<IHttpClientFactory>();
using var client = httpClientFactory.CreateClient("GitHubClient");

// Example usage of typed client
var gitHubService = host.Services.GetRequiredService<GitHubService>();
```

**Typed Client Implementation:**

```csharp
public class GitHubService
{
    private readonly HttpClient _httpClient;

    public GitHubService(HttpClient httpClient)
    {
        _httpClient = httpClient;
        _httpClient.BaseAddress = new Uri("https://api.github.com/");
        _httpClient.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
        _httpClient.DefaultRequestHeaders.UserAgent.ParseAdd("MyApp/1.0");
    }

    public async Task<string> GetUserRepositoriesAsync(string username)
    {
        var response = await _httpClient.GetAsync($"/users/{username}/repos");
        response.EnsureSuccessStatusCode();
        return await response.Content.ReadAsStringAsync();
    }
}
```

**Adding Resilience with Polly:**

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Polly;
using Polly.Extensions.Http;

var builder = Host.CreateApplicationBuilder(args);

// Configure retry policy
var retryPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .WaitAndRetryAsync(3, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));

// Configure circuit breaker policy
var circuitBreakerPolicy = HttpPolicyExtensions
    .HandleTransientHttpError()
    .CircuitBreakerAsync(5, TimeSpan.FromSeconds(30));

builder.Services.AddHttpClient("ResilientClient")
    .AddPolicyHandler(retryPolicy)
    .AddPolicyHandler(circuitBreakerPolicy);

// Combine policies
builder.Services.AddHttpClient("CombinedClient")
    .AddPolicyHandler(retryPolicy)
    .AddPolicyHandler(circuitBreakerPolicy)
    .AddTransientHttpErrorPolicy(p => p.RetryAsync(3))
    .AddPolicyHandler(Policy.TimeoutAsync<HttpResponseMessage>(TimeSpan.FromSeconds(10)));

// Best Practices:
// 1. Always use HttpClientFactory instead of creating HttpClient instances directly
// 2. Configure timeouts for all clients
// 3. Use typed clients for better organization and testability
// 4. Implement proper error handling and retry mechanisms
// 5. Monitor and log HTTP request metrics
// 6. Use appropriate caching strategies where applicable
// 7. Implement proper authentication and authorization
// 8. Validate all responses and handle errors gracefully
// 9. Use content compression where appropriate
// 10. Implement proper connection pooling configuration

**5.7 WebSockets**

WebSockets provide full-duplex communication channels over a single TCP connection. They're ideal for real-time applications like chat systems, live updates, and gaming.

* **Client-Side (`ClientWebSocket`):**

    ```csharp
    using System.Net.WebSockets;
    using System.Text;

    public class WebSocketClientExample
    {
        public static async Task ConnectAndCommunicateAsync(string url)
        {
            using var ws = new ClientWebSocket();
            try
            {
                // Configure WebSocket options
                ws.Options.KeepAliveInterval = TimeSpan.FromSeconds(30);
                ws.Options.SetRequestHeader("X-Client-Version", "1.0");

                // Connect with timeout
                using var cts = new CancellationTokenSource(TimeSpan.FromSeconds(10));
                await ws.ConnectAsync(new Uri(url), cts.Token);

                Console.WriteLine("WebSocket connected!");

                // Start message processing
                var receiveTask = ReceiveMessagesAsync(ws);
                var sendTask = SendMessagesAsync(ws);

                await Task.WhenAll(receiveTask, sendTask);
            }
            catch (SocketException ex)
            {
                Console.WriteLine($"Socket error: {ex.SocketErrorCode} - {ex.Message}");
            }
            catch (IOException ex)
            {
                Console.WriteLine($"IO error: {ex.Message}");
            }
            catch (ObjectDisposedException)
            {
                Console.WriteLine("Connection was unexpectedly closed");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.GetType().Name} - {ex.Message}");
            }

        static async Task SendMessagesAsync(ClientWebSocket ws)
        {
            while (ws.State == WebSocketState.Open)
            {
                Console.Write("Enter message (or 'exit' to quit): ");
                string message = Console.ReadLine();

                if (message == "exit") break;

                byte[] buffer = Encoding.UTF8.GetBytes(message);
                await ws.SendAsync(new ArraySegment<byte>(buffer), 
                    WebSocketMessageType.Text, 
                    true, 
                    CancellationToken.None);
            }
        }

        static async Task ReceiveMessagesAsync(ClientWebSocket ws)
        {
            byte[] buffer = new byte[1024 * 4];
            while (ws.State == WebSocketState.Open)
            {
                WebSocketReceiveResult result;
                var message = new StringBuilder();

                do
                {
                    result = await ws.ReceiveAsync(new ArraySegment<byte>(buffer), CancellationToken.None);
                    if (result.MessageType == WebSocketMessageType.Close)
                    {
                        await ws.CloseAsync(WebSocketCloseStatus.NormalClosure, string.Empty, CancellationToken.None);
                        Console.WriteLine("Connection closed by server.");
                        return;
                    }

                    string receivedChunk = Encoding.UTF8.GetString(buffer, 0, result.Count);
                    message.Append(receivedChunk);
                }
                while (!result.EndOfMessage);

                Console.WriteLine($"Received: {message}");
            }
        }
    }
    ```

* **Server-Side Implementation (ASP.NET Core):**

    ```csharp
    public class WebSocketMiddleware
    {
        private readonly RequestDelegate _next;

        public WebSocketMiddleware(RequestDelegate next)
        {
            _next = next;
        }

        public async Task InvokeAsync(HttpContext context)
        {
            if (context.WebSockets.IsWebSocketRequest)
            {
                using var webSocket = await context.WebSockets.AcceptWebSocketAsync();
                await HandleWebSocketConnection(webSocket);
            }
            else
            {
                context.Response.StatusCode = StatusCodes.Status400BadRequest;
            }
        }

        private async Task HandleWebSocketConnection(WebSocket webSocket)
        {
            var buffer = new byte[1024 * 4];
            var receiveResult = await webSocket.ReceiveAsync(
                new ArraySegment<byte>(buffer), CancellationToken.None);

            while (!receiveResult.CloseStatus.HasValue)
            {
                // Process message
                string message = Encoding.UTF8.GetString(buffer, 0, receiveResult.Count);
                Console.WriteLine($"Received: {message}");

                // Echo message back
                await webSocket.SendAsync(
                    new ArraySegment<byte>(buffer, 0, receiveResult.Count),
                    receiveResult.MessageType,
                    receiveResult.EndOfMessage,
                    CancellationToken.None);

                receiveResult = await webSocket.ReceiveAsync(
                    new ArraySegment<byte>(buffer), CancellationToken.None);
            }

            await webSocket.CloseAsync(
                receiveResult.CloseStatus.Value,
                receiveResult.CloseStatusDescription,
                CancellationToken.None);
        }
    }

    // In Program.cs:
    app.UseWebSockets();
    app.UseMiddleware<WebSocketMiddleware>();
    ```

* **Security Considerations:**
    - Always use `wss://` (WebSocket Secure) in production
    - Validate and sanitize all incoming messages
    - Implement rate limiting to prevent abuse
    - Use authentication and authorization
    - Set appropriate message size limits
    - Handle connection timeouts gracefully

**Project: Network Monitoring Application**

Let's build a console application that monitors the availability and response time of a list of websites.

**1. Project Setup:**

```bash
dotnet new console -o NetworkMonitor
cd NetworkMonitor
```

**2. `WebsiteStatus.cs` (Model):**

```csharp
public class WebsiteStatus
{
    public string Url { get; set; }
    public bool IsUp { get; set; }
    public long ResponseTimeMs { get; set; }
    public DateTime LastCheck { get; set; }
}
```

**3. `NetworkMonitorService.cs`:**

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading.Tasks;

public class NetworkMonitorService
{
    private readonly HttpClient _httpClient;
    private readonly List<string> _urls;

    public NetworkMonitorService(HttpClient httpClient, List<string> urls)
    {
        _httpClient = httpClient;
        _urls = urls;
    }

    public async Task<List<WebsiteStatus>> CheckWebsitesAsync()
    {
        var results = new List<WebsiteStatus>();
        foreach (var url in _urls)
        {
            results.Add(await CheckWebsiteAsync(url));
        }
        return results;
    }

    private async Task<WebsiteStatus> CheckWebsiteAsync(string url)
    {
        var status = new WebsiteStatus { Url = url, LastCheck = DateTime.Now };
        var stopwatch = Stopwatch.StartNew();

        try
        {
            HttpResponseMessage response = await _httpClient.GetAsync(url);
            status.IsUp = response.IsSuccessStatusCode;
        }
        catch (Exception)
        {
            status.IsUp = false;
        }
        finally
        {
            stopwatch.Stop();
            status.ResponseTimeMs = stopwatch.ElapsedMilliseconds;
        }

        return status;
    }

    public void DisplayStatus(List<WebsiteStatus> statuses)
    {
        Console.Clear();
        Console.WriteLine($"Network Monitoring Report - {DateTime.Now}");
        Console.WriteLine("-------------------------------------------");
        foreach (var status in statuses)
        {
            Console.WriteLine($"- {status.Url}:");
            Console.WriteLine($"  Status: {(status.IsUp ? "Up" : "Down")}");
            Console.WriteLine($"  Response Time: {status.ResponseTimeMs} ms");
            Console.WriteLine($"  Last Check: {status.LastCheck}");
            Console.WriteLine();
        }
    }
}
```

**4. `Program.cs`:**

```csharp
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = Host.CreateApplicationBuilder(args);

        // Add HttpClient
        builder.Services.AddHttpClient();

        // URLs to monitor (you can load these from a config file)
        var urls = new List<string>
        {
            "https://www.google.com",
            "https://www.microsoft.com",
            "https://www.amazon.com",
            "https://ThisWebsiteDoesNotExist.com" // Example of a down site
        };

        // Register NetworkMonitorService
        builder.Services.AddSingleton(new NetworkMonitorService(
            builder.Services.BuildServiceProvider().GetRequiredService<IHttpClientFactory>().CreateClient(),
            urls));

        using var host = builder.Build();

        // Get the NetworkMonitorService
        var monitorService = host.Services.GetRequiredService<NetworkMonitorService>();

        // Run the monitoring loop
        while (true)
        {
            var statuses = await monitorService.CheckWebsitesAsync();
            monitorService.DisplayStatus(statuses);
            await Task.Delay(TimeSpan.FromSeconds(10)); // Check every 10 seconds
        }
    }
}
```

**Enhancements:**

* **Configuration:** Load the list of URLs from a configuration file (e.g., `appsettings.json`).
* **Logging:** Use a logging framework (like Serilog or the built-in `ILogger`) to log errors and events.
* **Alerting:** Implement alerting mechanisms (e.g., send an email or SMS) when a website goes down.
* **UI:** Create a more interactive UI (e.g., using a console UI library or a web front-end with ASP.NET Core).
* **Background Service:** Turn the monitoring loop into a background service so it runs continuously.

This tutorial has provided you with a solid understanding of network programming in C# and .NET 8, including creating servers, making HTTP requests, and using `HttpClientFactory` effectively. The network monitoring application project demonstrates how to apply these concepts in a practical scenario. Keep exploring and expanding upon these examples to further enhance your network programming skills!
