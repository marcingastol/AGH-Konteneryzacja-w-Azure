# Additional Exercises for Managing a Simple Web Server Container

## Introduction

These additional exercises are designed to encourage exploration of basic Docker and Nginx functionalities. They are simple yet effective for understanding fundamental concepts and operations in Docker.

---

## Exercise 1: Interact with Nginx Server from the Container

### Overview

Understand how to interact with the Nginx server directly from within the container.

### Task

1. Access the Nginx Container:
   ```bash
   sudo docker exec -it my-nginx /bin/bash
   ```
   _This command accesses the shell of the `my-nginx` container._

2. Once inside the container, list the contents of the Nginx web root:
   ```bash
   ls /usr/share/nginx/html
   ```
   _This will list the files in the Nginx web root directory._

3. Exit the container:
   ```bash
   exit
   ```
   _This will bring you back to your host machine's command prompt._

---

## Exercise 2: Modify the Nginx Welcome Page

### Overview

Learn how to modify the default Nginx welcome page inside the container.

### Task

1. Copy a new HTML file into the running container:
   ```bash
   sudo docker cp new-index.html my-nginx:/usr/share/nginx/html/index.html
   ```
   _This replaces the default Nginx index page with your `new-index.html`._

2. Refresh `http://localhost:8080` in your browser to see the changes.

---

## Exercise 3: Monitoring Container Logs

### Overview

Practice monitoring real-time logs of the Nginx container.

### Task

1. Monitor Logs in Real-Time:
   ```bash
   sudo docker logs -f my-nginx
   ```
   _The `-f` flag tails the logs, allowing you to see logs in real-time._

2. Access `http://localhost:8080` from your browser and observe the log outputs.

---

## Exercise 4: Restarting the Nginx Service within the Container

### Overview

Learn how to restart the Nginx service inside the container without stopping the container itself.

### Task

1. Access the container:
   ```bash
   sudo docker exec -it my-nginx /bin/bash
   ```

2. Inside the container, restart Nginx:
   ```bash
   nginx -s reload
   ```
   _This command reloads the Nginx configuration._

3. Exit the container and verify the Nginx server is still running.

---

## Exercise 5: Exploring Docker Network

### Overview

Understand how Docker handles networking by inspecting the network settings of your container.

### Task

1. Inspect Network Settings:
   ```bash
   sudo docker inspect my-nginx
   ```
   _Look for the "NetworkSettings" section to understand the network configuration of your container._

---

These exercises are intended to give you a practical understanding of managing a web server in Docker and exploring some basic but crucial functionalities.
