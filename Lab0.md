# Environment Setup Guide for Development

This guide outlines the steps to set up a development environment on Ubuntu. It includes the installation of essential tools such as Git and Docker.

---

## Part 1: Installing Git

### Overview

Git is a distributed version control system. It's essential for managing the versions of your source code. This section covers the installation of Git.

1. Update the package lists to ensure you get the latest version:
   ```bash
   sudo apt-get update
   ```
   _This command updates the list of packages and their versions available in your repository._

2. Install Git:
   ```bash
   sudo apt-get install git-all
   ```
   _Installs the Git software and all its dependencies._

3. Verify the Git installation:
   ```bash
   git version
   ```
   _This command checks the installed version of Git._

---

## Part 2: Installing Docker

### Overview

Docker is a platform for developing, shipping, and running applications inside containers. This section guides you through Docker's installation.

1. Update the package lists again:
   ```bash
   sudo apt-get update
   ```
   _Ensures that your local package index is up-to-date._

2. Install prerequisites for Docker:
   ```bash
   sudo apt-get install ca-certificates curl gnupg
   ```
   _Installs the necessary packages to securely download and install Docker._

3. Create a directory for Docker's keyring:
   ```bash
   sudo install -m 0755 -d /etc/apt/keyrings
   ```
   _Creates a directory with the appropriate permissions for storing Docker's GPG key._

4. Download and add Docker's official GPG key:
   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   ```
   _Downloads Docker's GPG key and saves it to the specified directory._

5. Modify file permissions for the key:
   ```bash
   sudo chmod a+r /etc/apt/keyrings/docker.gpg
   ```
   _Changes the permissions of the Docker GPG key file to be readable by all users._

6. Add Docker repository to the list of sources:
   ```bash
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```
   _Adds the Docker repository to your system's software sources list._

7. Update the package lists post repository addition:
   ```bash
   sudo apt-get update
   ```
   _Updates your package list with the Docker packages from the newly added Docker repository._

8. Install Docker Engine and related components:
   ```bash
   sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   ```
   _Installs Docker Engine, CLI, containerd, and additional Docker plugins._

9. Test the Docker installation:
   ```bash
   sudo docker run hello-world
   ```
   _Runs the `hello-world` Docker image to verify if Docker is correctly installed and working._

---

## Part 3: Docker account

Go to https://hub.docker.com/login and create an account.

---

This guide provides a comprehensive approach to setting up a development environment, ensuring you have Git for version control and Docker for containerization.
