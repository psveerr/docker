Deploy a 3-tier Messages Application using Docker.

Architecture: We upgraded the standard 3-tier model into a 4-layer robust architecture:

    Database Tier: MongoDB (mongo-db container) for persistence.

    Application Tier: Node.js/Express API (backend-api container) for logic and database interaction.

    Proxy/Web Tier: Nginx (nginx-proxy container) for serving static files and routing API calls.

    Client Tier: Simple HTML/JavaScript (index.html) running in the browser.
<img width="1920" height="1080" alt="Screenshot from 2025-09-29 20-02-44" src="https://github.com/user-attachments/assets/4380c875-0c74-4e05-9b86-81fd25222a91" />

<img width="1920" height="1080" alt="Screenshot from 2025-09-29 20-03-06" src="https://github.com/user-attachments/assets/731b4e5d-728d-4a05-ad62-059ed185f5d6" />

The Journey: Steps and Obstacles Overcome

We successfully moved from raw application code to a fully functioning, containerized deployment by completing the following phases:

Phase 1: Container Preparation (Dockerfiles & Configuration)

    Backend Dockerfile: Defined instructions to build the Node.js API image (app-backend). This involved setting the working directory, copying package.json, installing dependencies, and running index.js on port 5000.

    Nginx Configuration (nginx.conf): Configured Nginx to act as both a static server and a reverse proxy. This was crucial for:

        Serving index.html from the root path (/).

        Forwarding all API calls (/api/) to the internal backend-api:5000 service.

    Nginx Dockerfile: Defined instructions to build the Nginx image (app-nginx) by pulling the base Nginx image and copying the nginx.conf and index.html files into it.

<img width="1920" height="1080" alt="Screenshot from 2025-09-29 20-03-33" src="https://github.com/user-attachments/assets/e2c5afde-36e6-4682-a247-c1d688d9cdf7" />
