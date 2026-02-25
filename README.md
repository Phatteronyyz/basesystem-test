# Basesystem Guide

## Prerequisites

Before starting the installation, ensure you have the following software installed:

* **Docker Desktop:** [Download here](https://www.docker.com)
* **Python 3.x:** For running the Backend Server.
* **Pip:** Python package manager.

---

## Installation Steps

### 1. Docker Setup (Interface)

Follow these steps to deploy the Dashboard using Docker:

1.  **Prepare File:** Ensure you have the `basesystem.tar` file in your local directory.
2.  **Load Image:** Open your terminal, navigate to the directory containing the file, and run:
    ```bash
    docker load -i basesystem.tar
    ```
3.  **Run Container:** Start the UI container with the following command:
    ```bash
    docker run -d -p 3000:80 --name interface basesystem:latest
    ```
    > The UI will be accessible at [http://localhost:3000](http://localhost:3000) once the container is running.

### 2. Python Setup (Backend Server)

*It is recommended to use a virtual environment (venv) for the following steps.*

1.  **Install Requirements:**
    Install all necessary dependencies using pip:
    ```bash
    pip install -r requirements.txt
    ```
2.  **Run Server:**
    Execute the server file:
    ```bash
    python server.py
    ```

## How to Use

Once `server.py` is running, your terminal should display:
`WebSocket Server is running on ws://localhost:8765...`

1.  Open your web browser.
2.  Navigate to: **[http://localhost:3000](http://localhost:3000)** (Reload once if it shown disconnect from python)

---

### How to Stop and Remove the Container
If you need to stop the system or clean up the container, use these commands:

* **To Stop the container:** (The container remains but stops running)
    ```bash
    docker stop interface
    ```
* **To Remove the container:** (Deletes the container instance)
    ```bash
    docker rm -f interface
    ```

### How to Restart or Run Again
Depending on what you did in the previous step, follow these instructions to run the system again:

* **If you only stopped it:** Just start it again:
    ```bash
    docker start interface
    ```
* **If you removed it (or want to run a fresh instance):**
    Run the original `docker run` command again:
    ```bash
    docker run -d -p 3000:80 --name interface basesystem:latest
    ```
* **If you updated the `.tar` file:**
    You must remove the old container and image first, then re-run the `docker load` and `docker run` steps.

---

> [!TIP]
> Use `docker ps -a` to check the status of all your containers.


> [!IMPORTANT]
> Ensure that port **3000** (Web UI) and port **8765** (WebSocket) are not being used by other applications.

---
