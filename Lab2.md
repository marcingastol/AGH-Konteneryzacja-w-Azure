# Setting Up a Docker Environment with a Sample Application

## Introduction

This guide walks through the process of setting up a Docker environment and building a simple Dockerized application. This includes cloning a repository, creating a Dockerfile, building an image, and running a container.

---

## Part 1: Cloning the Repository

### Overview

Cloning a repository is the first step in obtaining the application source code. Here, you will clone a sample Docker application repository.

1. Clone the Repository:
   ```bash
   git clone https://github.com/docker/getting-started-app.git
   ```
   _This command clones the 'getting-started-app' repository from GitHub to your local machine._

2. Change Directory:
   ```bash
   cd getting-started-app/
   ```
   _Changes the current directory to the cloned repository's directory._

---

## Part 2: Creating and Editing the Dockerfile

### Overview

A Dockerfile is a text document that contains instructions for Docker to build an image. Creating and editing a Dockerfile is essential in defining how your application runs in a container.

1. Create a Dockerfile:
   ```bash
   touch Dockerfile
   ```
   _Creates a new file named 'Dockerfile' in the current directory._

2. Edit the Dockerfile:
   ```bash
   vim Dockerfile 
   ```
   Close file by ESC and :wq!
   
   ```bash
   # syntax=docker/dockerfile:1
   
   FROM node:18-alpine
   WORKDIR /app
   COPY . .
   RUN yarn install --production
   CMD ["node", "src/index.js"]
   EXPOSE 3000
   ```
   
   _Opens the 'Dockerfile' in Vim editor for editing. Add necessary Docker instructions here._

4. Display the Dockerfile Contents:
   ```bash
   cat Dockerfile
   ```
   _Displays the contents of the 'Dockerfile'._

---

## Part 3: Building and Running the Docker Container

### Overview

After defining your Dockerfile, the next steps involve building a Docker image from it and running a container based on this image.

1. Build the Docker Image:
   ```bash
   sudo docker build -t getting-started .
   ```
   _Builds a Docker image from the Dockerfile in the current directory. The `-t` flag tags the image with the name 'getting-started'._

2. Run the Docker Container:
   ```bash
   sudo docker run -dp 0.0.0.0:3000:3000 getting-started
   ```
   _Runs a container from the 'getting-started' image. `-d` runs the container in detached mode. `-p 0.0.0.0:3000:3000` maps port 3000 of the host to port 3000 of the container, allowing external access._

3. Open your web browser to http://...ip...:3000. You should see your app.

---

This guide provides a comprehensive approach to setting up a Docker environment for development purposes, including cloning a repository, setting up a Dockerfile, and running a Docker container.
