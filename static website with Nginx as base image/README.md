Of course. Here is a complete documentation for your project, formatted perfectly for a GitHub README.md file.

Deploy a Static HTML Website with Docker and Nginx

This project demonstrates how to take a simple static HTML website and deploy it inside a Docker container using an Nginx web server. The entire environment is built from an Ubuntu base image.

Project Overview

The goal of this project is to containerize a web application. We start with a basic index.html file. Then, we write a Dockerfile that contains all the instructions needed to create a runnable environment. These instructions include:

    Starting with a clean Ubuntu operating system.

    Installing the Nginx web server software.

    Copying the website files into the container.

    Configuring the server to start automatically.

Finally, we build an image from these instructions and run it as a container, making the website accessible from a web browser on our local machine.

Prerequisites

Before you begin, ensure you have Docker Desktop or the Docker Engine installed and running on your system.

Project Structure

For this project, you will need a single folder containing two files. The folder can be named anything you like, such as my-website.

    index.html: This is your static website page. It contains the text and content you want to display.

    Dockerfile: This is the instruction manual for Docker. It's a plain text file that tells Docker exactly how to build the container image step-by-step.

Step-by-Step Guide

1. Create Your Project Files

First, create your main project folder. Inside this folder, create your index.html file and add some basic HTML content to it for your website. Next, create the empty Dockerfile in the same folder.

<img width="1850" height="586" alt="Screenshot from 2025-09-21 22-25-49" src="https://github.com/user-attachments/assets/b34a4211-2feb-46c7-b9d1-df048564b988" />


2. Write the Dockerfile Instructions

Open the Dockerfile and add the necessary instructions. The configuration will tell Docker to perform the following actions in order:

    Use the latest version of Ubuntu as the base.

    Use a faster regional package server to speed up downloads.

    Run the commands to update Ubuntu's software lists and install Nginx.

    Copy your index.html file from your project folder into the default web directory that Nginx uses inside the container.

    Inform Docker that the container will listen for traffic on port 80.

    Set the final command to start the Nginx server when the container launches.
    
<img width="1850" height="586" alt="Screenshot from 2025-09-21 22-25-36" src="https://github.com/user-attachments/assets/be091e8e-b622-4cb3-bc5e-b9160cee8eef" />

3. Build the Docker Image

Open your terminal or command prompt and navigate into your project folder. Run the docker build command. You should give the image a memorable name or "tag" using the -t flag, for example, my-web-app. This command reads your Dockerfile, executes each instruction, and creates a self-contained, runnable image.

<img width="1850" height="586" alt="Screenshot from 2025-09-21 22-27-06" src="https://github.com/user-attachments/assets/ade050da-6e27-4927-a067-473afede35f6" />


4. Run the Docker Container

Once the image is built successfully, use the docker run command to start a container from your new image. In this command, you will need to:

    Map a port from your computer to the container's port using the -p flag. For example, mapping port 8080 on your machine to port 80 in the container.

    Optionally, give your running container a unique name with the --name flag to make it easier to manage.

    Run the container in detached mode using the -d flag so it runs in the background.

<img width="1092" height="152" alt="Screenshot from 2025-09-21 22-27-37" src="https://github.com/user-attachments/assets/3d2262a8-9efa-416f-baf7-f50da6a8c2e5" />


Upon running the command, the terminal will display a long Container ID, confirming that it has started.

5. View Your Live Website

Your website is now live! Open any web browser and navigate to http://localhost:8080. You should see the content from your index.html file displayed on the page.

<img width="1092" height="152" alt="Screenshot from 2025-09-21 22-28-41" src="https://github.com/user-attachments/assets/fd71d00c-b2cd-4a1c-864a-6464a460ca8d" />

