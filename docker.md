# Docker Tutorial for Windows 11

## Table of Contents
- [Docker Tutorial for Windows 11](#docker-tutorial-for-windows-11)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Docker Concepts](#docker-concepts)
  - [Part 1: Deploying a .NET Application](#part-1-deploying-a-net-application)
  - [Part 2: Deploying a Python Application](#part-2-deploying-a-python-application)
  - [Part 3: Deploying a Web Application (HTML, CSS, JavaScript)](#part-3-deploying-a-web-application-html-css-javascript)
  - [Part 4: Docker Compose (Optional)](#part-4-docker-compose-optional)
  - [Further Steps](#further-steps)

---

Here's a detailed Docker tutorial for deploying .NET, Python, and web apps (HTML, CSS, JavaScript) on Windows 11. This tutorial will cover the essential steps with clear examples.

---

## Prerequisites

1. **Windows 11:** Ensure you have Windows 11 Professional, Enterprise, or Education edition. Docker Desktop for Windows utilizes the Windows Subsystem for Linux 2 (WSL 2), which is not available on Windows 11 Home.

2. **WSL 2:**  Enable WSL 2 and install a Linux distribution (e.g., Ubuntu). You can do this via PowerShell (as Administrator):

    ```powershell
    wsl --install
    ```

    After installation, you might need to update the WSL 2 Linux kernel. Follow the instructions provided during the process.

3. **Docker Desktop for Windows:** Download and install Docker Desktop from the official Docker website. During installation, make sure to choose the "Use WSL 2 instead of Hyper-V" option.

4. **Basic command-line familiarity:** You should be comfortable navigating the command line (PowerShell or your WSL terminal).

5. **Text editor or IDE:** Have a text editor (like VS Code, Sublime Text, or Notepad++) or an IDE for editing your code.

---

## Docker Concepts

* **Images:** Read-only templates used to create containers. They contain the OS, application code, libraries, dependencies, and other configurations.
* **Containers:** Running instances of Docker images. They are isolated environments for running your applications.
* **Dockerfile:** A text file that contains instructions to build a Docker image.
* **Docker Hub:** A cloud-based registry for storing and sharing Docker images.
* **Docker Compose:** A tool for defining and running multi-container Docker applications using a YAML file (`docker-compose.yml`).

---

## Part 1: Deploying a .NET Application

Let's deploy a simple .NET console application.

**1. Create a .NET Application**

* Open PowerShell or your preferred terminal in a new directory.
* Create a new .NET console app:

    ```bash
    dotnet new console -o mydotnetapp
    cd mydotnetapp
    ```

* Edit `Program.cs` (optional): You can modify the code, for example:

    ```csharp
    using System;

    namespace mydotnetapp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello from .NET in Docker!");
            }
        }
    }
    ```

**2. Create a Dockerfile**

* In the `mydotnetapp` directory, create a file named `Dockerfile` (no extension) with the following content:

    ```dockerfile
    # Use the official .NET SDK image as a base image
    FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env

    # Set the working directory inside the container
    WORKDIR /app

    # Copy everything from the current directory to the container
    COPY . ./

    # Restore as distinct layers
    RUN dotnet restore

    # Build the application
    RUN dotnet publish -c Release -o out

    # Build runtime image
    FROM mcr.microsoft.com/dotnet/aspnet:7.0
    WORKDIR /app
    COPY --from=build-env /app/out .
    ENTRYPOINT ["dotnet", "mydotnetapp.dll"]
    ```

**Dockerfile Explanation**

* **`FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build-env`:**  Uses the official .NET 7.0 SDK image as the base for the build environment. This image contains tools to build the app. We give it the alias "build-env".
* **`WORKDIR /app`:** Sets the working directory inside the container to `/app`.
* **`COPY . ./`:** Copies all files from your project directory to the `/app` directory in the container.
* **`RUN dotnet restore`**: Restores the required dependencies for the .NET project.
* **`RUN dotnet publish -c Release -o out`:** Builds the application in Release mode and publishes the output to the `/app/out` directory.
* **`FROM mcr.microsoft.com/dotnet/aspnet:7.0`:** Specifies a new base image, this time for running the application. It uses the ASP.NET Core runtime image (smaller than the SDK).
* **`COPY --from=build-env /app/out .`:** Copies the published output from the `build-env` stage (our build environment) to the current directory (`/app`) in this new runtime image.
* **`ENTRYPOINT ["dotnet", "mydotnetapp.dll"]`:** Defines the command to run when the container starts (runs the .NET application).

**3. Build the Docker Image**

* In the `mydotnetapp` directory, run:

    ```bash
    docker build -t mydotnetapp-image .
    ```

  * `-t mydotnetapp-image`: Tags the image with the name `mydotnetapp-image`.
  * `.`: Specifies the current directory as the build context (where Docker will look for the `Dockerfile`).

**4. Run the Docker Container**

* Run the following command:

    ```bash
    docker run mydotnetapp-image
    ```

    You should see the output "Hello from .NET in Docker!" in your terminal.

---

## Part 2: Deploying a Python Application

Let's deploy a simple Python Flask web application.

**1. Create a Python Application**

* Create a new directory:

    ```bash
    mkdir mypythonapp
    cd mypythonapp
    ```

* Create a file named `app.py`:

    ```python
    from flask import Flask
    app = Flask(__name__)

    @app.route("/")
    def hello():
        return "Hello from Python in Docker!"

    if __name__ == "__main__":
        app.run(host='0.0.0.0', debug=True)
    ```

* Create a file named `requirements.txt`:

    ```
    Flask
    ```

**2. Create a Dockerfile**

* In the `mypythonapp` directory, create a `Dockerfile`:

    ```dockerfile
    # Use the official Python image as a base
    FROM python:3.9-slim-buster

    # Set the working directory
    WORKDIR /app

    # Copy the requirements file
    COPY requirements.txt requirements.txt

    # Install dependencies
    RUN pip install -r requirements.txt

    # Copy the application code
    COPY . .

    # Expose port 5000
    EXPOSE 5000

    # Run the application
    CMD ["python", "app.py"]
    ```

**Dockerfile Explanation**

* **`FROM python:3.9-slim-buster`:** Uses a slim Python 3.9 image as the base.
* **`WORKDIR /app`:** Sets the working directory to `/app`.
* **`COPY requirements.txt requirements.txt`:** Copies the `requirements.txt` file.
* **`RUN pip install -r requirements.txt`:** Installs the Python packages listed in `requirements.txt`.
* **`COPY . .`:** Copies the rest of your application code into the container.
* **`EXPOSE 5000`:** Informs Docker that the container listens on port 5000 (the default Flask port).
* **`CMD ["python", "app.py"]`:** Sets the command to run when the container starts (runs your Python app).

**3. Build the Docker Image**

* In the `mypythonapp` directory, run:

    ```bash
    docker build -t mypythonapp-image .
    ```

**4. Run the Docker Container**

* Run the container, mapping port 5000 on your host to port 5000 in the container:

    ```bash
    docker run -p 5000:5000 mypythonapp-image
    ```

* Open your web browser and go to `http://localhost:5000/`. You should see "Hello from Python in Docker!".

---

## Part 3: Deploying a Web Application (HTML, CSS, JavaScript)

Let's deploy a simple static website using Nginx.

**1. Create a Web Application**

* Create a new directory:

    ```bash
    mkdir mywebapp
    cd mywebapp
    ```

* Create an `index.html` file:

    ```html
    <!DOCTYPE html>
    <html>
    <head>
        <title>My Web App</title>
        <style>
            body {
                font-family: sans-serif;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <h1>Hello from Docker!</h1>
        <p>This is a static web app.</p>
    </body>
    </html>
    ```

**2. Create a Dockerfile**

* In the `mywebapp` directory, create a `Dockerfile`:

    ```dockerfile
    # Use the official Nginx image
    FROM nginx:alpine

    # Copy the web content to the Nginx default web root
    COPY . /usr/share/nginx/html
    ```

**Dockerfile Explanation**

* **`FROM nginx:alpine`:** Uses a lightweight Nginx image based on Alpine Linux.
* **`COPY . /usr/share/nginx/html`:** Copies your `index.html` (and any other files you have, like CSS or JS) to the default directory where Nginx serves files from (`/usr/share/nginx/html`).

**3. Build the Docker Image**

```bash
docker build -t mywebapp-image .
```

**4. Run the Docker Container**

```bash
docker run -p 80:80 mywebapp-image
```

* Open your web browser and go to `http://localhost/`. You should see your web page.

---

## Part 4: Docker Compose (Optional)

Docker Compose is great for managing multi-container applications. Let's create a simple example using Docker Compose to run our Python app and a Redis database.

**1. Modify the Python App**

* Update `app.py`:

    ```python
    from flask import Flask
    import redis

    app = Flask(__name__)
    cache = redis.Redis(host='redis', port=6379)

    @app.route("/")
    def hello():
        count = cache.incr('hits')
        return f"Hello from Python and Redis! I have been seen {count} times."

    if __name__ == "__main__":
        app.run(host='0.0.0.0', debug=True)
    ```

* Update `requirements.txt`:

    ```
    Flask
    redis
    ```

**2. Create `docker-compose.yml`**

* In the `mypythonapp` directory, create a file named `docker-compose.yml`:

    ```yaml
    version: "3.9"
    services:
      web:
        build: .
        ports:
          - "5000:5000"
      redis:
        image: "redis:alpine"
    ```

**`docker-compose.yml` Explanation**

* **`version: "3.9"`:** Specifies the Docker Compose file format version.
* **`services:`:** Defines the services (containers) in your application.
* **`web:`:**
  * **`build: .`:** Tells Compose to build the image for the `web` service using the `Dockerfile` in the current directory.
  * **`ports: - "5000:5000"`:** Maps port 5000 on the host to port 5000 in the container.
* **`redis:`:**
  * **`image: "redis:alpine"`:** Uses the official Redis image from Docker Hub.

**3. Run with Docker Compose**

* In the `mypythonapp` directory, run:

    ```bash
    docker-compose up -d
    ```

  * `-d`: Runs the containers in detached mode (in the background).

* Docker Compose will build the `web` image, pull the `redis` image, and start both containers.

* Access `http://localhost:5000/` in your browser. You should see the message from your Python app, and the visit count will increment each time you refresh, thanks to Redis.

**4. Stop with Docker Compose**

* To stop the containers:

    ```bash
    docker-compose down
    ```

---

## Further Steps

* **Docker Hub:** Push your images to Docker Hub to share them or deploy them to other environments.
* **Orchestration:** For production deployments, consider using container orchestration tools like Kubernetes or Docker Swarm.
* **Volumes:** Use Docker volumes to persist data outside of containers.
* **Networking:** Learn more about Docker networking to connect containers and services.
* **Security:** Understand Docker security best practices to secure your containers.

This comprehensive tutorial provides a solid foundation for using Docker on Windows 11 to deploy various types of applications. Remember to explore the official Docker documentation for in-depth information and advanced features. Good luck!
