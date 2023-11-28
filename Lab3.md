# Docker Environment Management and Application Update Guide

This guide provides instructions on managing Docker containers and updating a Dockerized application.

## Part 1: Removing a Docker Container

### Overview

Learn how to stop and remove a Docker container using the command line interface (CLI). This is a crucial skill for managing Docker resources efficiently.

### Steps

1. **Get the ID of the Running Container**:
   ```bash
   docker ps
   ```
   _Lists all currently running containers. Note the container ID of the container you wish to stop._

2. **Stop the Container**:
   ```bash
   docker stop <the-container-id>
   ```
   _Stops the specified container. Replace `<the-container-id>` with the actual ID obtained from `docker ps`._

3. **Remove the Container**:
   ```bash
   docker rm <the-container-id>
   ```
   _Removes the stopped container from your system. Again, replace `<the-container-id>` with the actual container ID._

---

## Part 2: Updating the Application and Image

### Overview

In this part, you'll learn how to update the application's source code and rebuild the Docker image. This process is typical in software development and deployment.

### Update the Source Code

1. **Modify the Application File**:
   In the `src/static/js/app.js` file, change the line of code as specified:
   - From: `<p className="text-center">No items yet! Add one above!</p>`
   - To: `<p className="text-center">You have no todo items yet! Add one above!</p>`
   _This updates the text displayed in the application when no todo items are present._

### Build the Updated Docker Image

1. **Build the Updated Image**:
   ```bash
   docker build -t getting-started .
   ```
   _Builds a new Docker image from the Dockerfile in the current directory. The `-t` flag tags the new image with the name 'getting-started'._

### Start a New Container with the Updated Code

1. **Run the Updated Container**:
   ```bash
   docker run -dp 127.0.0.1:3000:3000 getting-started
   ```
   _Runs a new container from the updated 'getting-started' image. `-d` runs the container in detached mode. `-p 127.0.0.1:3000:3000` maps port 3000 of the localhost to port 3000 of the container._

2. Open your web browser to http://...ip...:3000. You should see your app.

---

This guide provides a comprehensive approach to managing Docker containers and updating Dockerized applications, ensuring you can efficiently handle development and deployment tasks.
