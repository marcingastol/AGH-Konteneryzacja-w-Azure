# Added Simple Exercises to the Workshop

## Overview

These exercises are designed to provide practical, hands-on experience with Docker, encouraging exploration and solidifying the concepts taught in the workshop. They are intentionally simple, catering to a range of skill levels.

---

## Exercise 1: Customizing the Nginx Welcome Page

### Objective

Modify the Nginx welcome page to include custom text or HTML.

### Task

1. Edit the `custom-index.html` file to add personalized content (e.g., "Hello Docker Workshop!").
2. Rebuild the Docker image with `sudo docker build -t custom-nginx .`.
3. Run the new container and check the changes by visiting `http://localhost:8080`.

### Outcome

Understand how changes in the Dockerfile and the HTML file reflect on the web page.

---

## Exercise 2: Exploring Volume Data on the Host

### Objective

Inspect the contents of the Docker volume on the host system.

### Task

1. Find the volume's mount point using `sudo docker volume inspect nginx-vol`.
2. Use `sudo ls <mount-point>` to list the contents of the volume.

### Outcome

Learn how to locate and inspect the data stored in Docker volumes.

---

## Exercise 3: Volume Backup and Restoration

### Objective

Practice backing up and restoring data from a Docker volume.

### Task

1. Backup the `nginx-vol` volume's data to a directory on the host.
2. Create a new volume, `nginx-vol-backup`.
3. Restore the backup to this new volume.
4. Run a new Nginx container using `nginx-vol-backup` and verify that the web page is the same.

### Outcome

Gain hands-on experience in data persistence and volume management.

---

## Exercise 4: Clean Up and Resource Management

### Objective

Practice cleaning up Docker containers and volumes.

### Task

1. Stop and remove all running containers related to the workshop.
2. Remove all volumes created during the workshop.

### Outcome

Understand the importance of managing and cleaning up Docker resources.

---

## Exercise 5: Changing Container Ports

### Objective

Learn to map different host ports to a container's exposed port.

### Task

1. Run the custom Nginx container, but this time map it to a different host port (e.g., 8082).
2. Access the Nginx page using the new port.

### Outcome

Understand how port mapping works in Docker and how to access the same container application via different ports.
