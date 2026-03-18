# Basesystem Guide

## Prerequisites

Before starting the installation, ensure you have the following software installed:

* **Docker Desktop:** [Download here](https://www.docker.com)
* **Python 3.x:** For running the Backend Server.
* **Pip:** Python package manager.

---

## Installation Steps

Follow these steps to deploy both the Frontend and Backend services with a single command:

### 1. Prepare Your Files
Ensure the following 3 files are located in the same directory:
1.  `frontend-image.tar` (The Web UI Image)
2.  `backend-image.tar` (The Python Control System Image)
3.  `docker-compose.yml` (The configuration file to link both systems)

### 2. Load Docker Images
Open your Terminal or Command Prompt in that directory and run:
```bash
docker load -i frontend-image.tar
docker load -i backend-image.tar
```

### 3. Start the System
Launch the entire stack using Docker Compose:
```bash
docker-compose up -d
```
Status: Once the terminal shows Started, the dashboard will be live at: http://localhost:3000

## How to Use

Once `server.py` is running, your terminal should display:
`WebSocket Server is running on ws://localhost:8765...`

1.  Open your web browser.
2.  Navigate to: **[http://localhost:3000](http://localhost:3000)** (Reload once if it shown disconnect from python)

---

### How to Stop and Remove the Container
If you need to stop the system or clean up the container, use these commands:

* Stops and removes all containers and networks.
    ```bash
    docker-compose down
    ```
* Verifies if both Frontend and Backend are currently running.
    ```bash
    docker-compose ps
    ```
* View error messages or activity from the Python Backend.
    ```bash
    docker-compose logs backend
    ```
* Restarts all containers without deleting them.
    ```bash
    docker-compose restart
    ```
---

> [!TIP]
> Use `docker ps -a` to check the status of all your containers.


> [!IMPORTANT]
> Ensure that port **3000** (Web UI) and port **8765** (WebSocket) are not being used by other applications.

---
