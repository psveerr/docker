Containerizing a Static Website with Docker & Nginx

This project is a hands-on guide to containerizing a basic static HTML website using Docker. It explores two different approaches to building the image—one using a general-purpose ubuntu base and another using the specialized nginx base—to demonstrate key concepts in image optimization.

This repository contains the files and explanations needed to build, run, and compare the resulting Docker images.

Project Files

    index.html: A simple HTML file that acts as the website's content.

    Dockerfile: A script with instructions to build our web server image using the nginx:latest tag.

Prerequisites

Before you begin, ensure you have Docker installed and running on your system.

    Docker Desktop Download Link

How to Run This Project

Follow these steps to get the website running on your local machine.

1. Get the Project Files

Makes these files mentioned below.
<img width="1850" height="586" alt="Screenshot from 2025-09-21 22-25-49" src="https://github.com/user-attachments/assets/031c4283-6386-4b2b-b623-e53e1d1d2285" />

<img width="1850" height="586" alt="Screenshot from 2025-09-21 22-25-36" src="https://github.com/user-attachments/assets/be091e8e-b622-4cb3-bc5e-b9160cee8eef" />

2. Build the Docker Image

From the project's root directory, run the docker build command. This will read the Dockerfile and create an image named my-website.
Bash

docker build -t my-website .
<img width="1856" height="777" alt="Screenshot from 2025-09-21 22-41-29" src="https://github.com/user-attachments/assets/270e4db4-43fa-4867-b2bb-c1afb2b79ac5" />


3. Run the Docker Container

Launch a container from the image you just built.
Bash

docker run -d -p 8080:80 --name my-running-website my-website
<img width="1086" height="137" alt="Screenshot from 2025-09-21 22-43-57" src="https://github.com/user-attachments/assets/cab0edf9-7d5d-4c1f-8456-2f4c1f2706fc" />


4. View Your Website ✅

Your website is now live! Open any web browser and go to: http://localhost:8080
<img width="1092" height="152" alt="Screenshot from 2025-09-21 22-28-41" src="https://github.com/user-attachments/assets/f3d453ef-bcf7-4dd6-bb13-8467ff65092b" />


Understanding the Image Sizes: An Important Lesson

After building images using different methods, you might run the docker images command and see a surprising result similar to this:
REPOSITORY	TAG	SIZE
my-web-app-nginx	latest	192MB
my-web-app	latest	139MB

<img width="1086" height="137" alt="Screenshot from 2025-09-21 22-41-52" src="https://github.com/user-attachments/assets/1a4c0ed7-e965-4f3b-9b6a-62fc2aa3201a" />

At first glance, it looks like the Ubuntu-based image is smaller, which contradicts the idea that specialized images are better. Here is the explanation.

Why the ubuntu Image is Surprisingly Small

The modern ubuntu:latest base image is highly optimized and starts very small (around 78MB). When you run apt-get install nginx, you add Nginx and its essential dependencies, which adds about 61MB.

    Calculation: Ubuntu Base (~78MB) + Nginx Install (~61MB) = ~139MB

This process creates a lean image with only the components you asked for.

Why the nginx Image is Larger

The nginx:latest tag is designed for broad compatibility and ease of use. It is built on top of a full Debian operating system, which is larger than the minimal Ubuntu base. It includes extra modules, utilities, and libraries to handle a wide variety of use cases out of the box. This focus on features makes the default image larger.


