# Docker Tutorial - 01_dockerfile_sample

This folder contains an example Dockerfile for building a simple Docker image.

## Getting Started

To build the Docker image from this Dockerfile, follow these steps:

1. Make sure you have Docker installed on your system.

2. Clone the repository using the following command:
   ```shell
    git clone https://github.com/nguyenbuitk/docker-tutorial.git
   ```
3. Navigate to the 01_dockerfile_sample folder:
    ```
    cd docker-tutorial/01_dockerfile_sample
    ```
4. Build the Docker image:
    ```
    docker build -t docker-tutorial:01 .
    ```
5. Verify that the image was successfully built:
    ```
    docker images
    ```