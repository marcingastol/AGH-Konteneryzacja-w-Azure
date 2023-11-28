# Sharing Your Docker Application

## Introduction

This guide walks through the process of sharing a Docker image. You'll use Docker Hub, the default registry for Docker images, to push and share your image.

## Part 1: Creating a Repository on Docker Hub

### Overview

To share a Docker image, you first need to create a repository on Docker Hub where the image will be stored and shared.

### Steps

1. **Sign in to Docker Hub from the CLI**:
   Sign in to Docker Hub using the command:
   ```bash
   docker login -u YOUR-USER-NAME
   ```
   _Replace `YOUR-USER-NAME` with your Docker Hub username. This command authenticates your Docker CLI with Docker Hub._

2. **Create a Repository on Docker Hub**:
   - Navigate to [Docker Hub](https://hub.docker.com/).
   - Sign up or sign in to your Docker Hub account.
   - Select the **Create Repository** button.
   - For the repository name, use `getting-started`.
   - Ensure the Visibility is set to Public.
   - Click on **Create**.
   _This sets up a repository on Docker Hub where you can push your Docker images._

---

## Part 2: Tagging and Pushing the Docker Image

### Overview

Tagging gives your Docker image a specific reference, and pushing uploads it to Docker Hub for sharing.

### Steps

1. **Tag the Docker Image**:
   ```bash
   docker tag getting-started YOUR-USER-NAME/getting-started
   ```
   _Replace `YOUR-USER-NAME` with your Docker ID. This command tags the `getting-started` image with your Docker Hub username, making it identifiable on Docker Hub._

2. **Push the Docker Image**:
   ```bash
   docker push YOUR-USER-NAME/getting-started
   ```
   _Pushes the tagged image to your Docker Hub repository. If no tag is specified, Docker defaults to using the `latest` tag._

3. Go back to Docker account and review a new image.

---

## Conclusion

By following these steps, you have successfully pushed your Docker image to Docker Hub, making it available for others to use and deploy. This process is essential for sharing Docker images and collaborating in Docker-based projects.
