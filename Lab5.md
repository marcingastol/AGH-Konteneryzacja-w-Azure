
# Exploring Docker Volumes with Nginx on Ubuntu

## Introduction

In this workshop, you will gain hands-on experience with Docker volumes, learning how to create, manage, and use them for persistent data storage in Docker containers. This workshop is designed to solidify your understanding of Docker volumes through practical application.

---

## Part 1: Introduction to Docker Volumes

### Overview

Gain an understanding of what Docker volumes are, their importance in persistent data storage, and how they differ from other storage options.

---

## Part 2: Setting Up a Custom Nginx Container

### Overview

Learn to create a Dockerfile, build a custom Docker image from it, and run a container using this image. This part lays the foundation for understanding how Docker images and containers work.

### Create a Dockerfile for Nginx

1. Create a new directory and navigate into it:
    ```bash
   mkdir nginx-vol-workshop && cd nginx-vol-workshop
   ```
   _This command creates a dedicated directory for the workshop files (`mkdir`) and then changes the current directory to it (`cd`)._

2. Create a Dockerfile using `vim`:
     ```bash
   sudo vim Dockerfile
   ```
   _`vim` is a simple text editor in Ubuntu. This command opens `vim` to create a new file named `Dockerfile`._

3. Write the Dockerfile:
    ```bash
   FROM nginx:latest
   COPY custom-index.html /usr/share/nginx/html/index.html
   ```
   Save file as ESC + wq!

   _`FROM nginx:latest` starts the build process from the latest Nginx image. `COPY` takes the custom HTML file from the host and places it inside the container._

4. Create a custom HTML file:
    ```bash
    sudo vim custom-index.html
   
   "<h1>Welcome to Custom Nginx!</h1>"
   ```
   Save file as ESC + wq!

   This command creates an HTML file with custom content.

### Build the Custom Nginx Image

1. Build the Docker image:
    ```bash
   sudo docker build -t custom-nginx .
   ```
   _This builds a new Docker image named `custom-nginx` from the Dockerfile in the current directory._

### Run the Custom Nginx Container without a Volume

1. Run the container:
    ```bash
   sudo docker run --name my-nginx -d -p 8080:80 custom-nginx
   ```
   _`docker run` creates and starts a container. `--name my-nginx` names the container. `-d` runs it in detached mode. `-p 8080:80` maps port 8080 on the host to port 80 in the container._

---

## Part 3: Implementing Docker Volumes

### Overview

Understand how to create Docker volumes and attach them to containers. This part demonstrates how volumes are used for persisting data across container lifecycles.

### Creating and Using a Volume

1. Create a Docker volume:
    ```bash
   sudo docker volume create nginx-vol
   ```
   _Creates a new volume named `nginx-vol` in Docker._

2. Run Nginx with the volume attached:
    ```bash
   sudo docker run --name my-nginx-vol -d -p 8081:80 -v nginx-vol:/usr/share/nginx/html custom-nginx
   ```
   _`-v nginx-vol:/usr/share/nginx/html` mounts the `nginx-vol` volume at the specified path in the container._

### Data Persistence Demonstration

1. Modify the HTML file and copy it to the volume:
    ```bash
   sudo vim custom-index.html
   
   "<h1>Updated Nginx Page</h1>"

   ESC > wq!

   sudo docker cp custom-index.html my-nginx-vol:/usr/share/nginx/html/index.html
   ```
   _Updates the HTML file and uses `docker cp` to copy it into the volume inside the running container._

---

## Part 4: Advanced Volume Management

### Overview

Explore advanced volume management techniques, including inspecting volumes and backing up and restoring data, to understand how Docker handles data beyond container lifecycles.

### Inspecting Volumes

1. Inspect the Docker volume:
    ```bash
   sudo docker volume inspect nginx-vol
   ```
   _This command shows detailed information about the specified volume._

### Backup and Restore Volume Data

1. Backup and restore commands:
    ```bash
   sudo docker cp my-nginx-vol:/usr/share/nginx/html ./backup
   sudo docker volume create nginx-vol-backup
   sudo docker cp ./backup/. my-nginx-vol:/usr/share/nginx/html
   ```
   _These commands demonstrate backing up data from a volume and restoring it to a new volume._

---

## Part 5: Cleaning Up

### Overview

Learn how to clean up Docker resources, an essential skill for managing Docker environments efficiently.

### Volume Cleanup

1. Remove containers and volumes:
```bash
   sudo docker rm -f my-nginx my-nginx-vol
   sudo docker volume rm nginx-vol nginx-vol-backup
   ```
   _These commands remove the containers and volumes created during the workshop._

---

