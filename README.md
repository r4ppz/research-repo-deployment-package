# Research Repository - Setup & User Guide

This system is fully containerized with Docker, so you don't need to install databases or languages on your machine. It is currently in alpha (v0.1.0), which means it is unstable and has bugs. For more project details, see our [documentation website](https://r4ppz.github.io/research-repo-docs/).

**NOTE**: This containerized setup is provided exclusively for distribution and local testing. There isn't a server yet, so in order to test it out, running the system via Docker is the only way to evaluate the system locally without requiring you to pull the whole codebase and build it yourself.

## Prerequisites (One-Time Setup)

1. **Install Docker Desktop**: Download and install for Windows:
   [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/).
2. **Start Docker**: Open the Docker Desktop app. Ensure Docker is running in the background for this to work.

> If you dont know how to download and set up docker watch youtube :p

---

## How to Run the System

### Steps:

1. **Open the project folder in File Explorer:**
   - Right-click inside the folder and select "Open in Terminal" or "Open command window here" to launch Command Prompt in the folder.

2. **Run the Application:**
   - In the terminal, execute the following command:
     ```bash
     docker compose up -d
     ```

3. **Access the App:**
   - Open your web browser and navigate to [http://localhost](http://localhost).

---

## Managing User Roles (Admin/Teacher/Student)

The system uses your **Google Email** to determine what you see. By default, everyone is a **Student**. To test roles and capabilities you must edit the config file manually.

1. Open `privileged-users.yaml` in any text editor.
2. Add your email address under the desired category:

> For more info about roles and capabilities, read: [Role and Capabilities](https://r4ppz.github.io/research-repo-docs/specification/#roles-capabilities)

### To Apply Role Changes:

Whenever you edit `privileged-users.yaml`, you **must restart** the backend to load the new permissions. Run this in your terminal:

```bash
docker compose restart backend
```

---

## Control Commands

| Action         | Command                  | Description                                                 |
| -------------- | ------------------------ | ----------------------------------------------------------- |
| **Start**      | `docker compose up -d`   | Starts everything in the background.                        |
| **Stop**       | `docker compose stop`    | Halts the app but keeps your data/uploads safe.             |
| **Resume**     | `docker compose start`   | Quickly wakes the app back up.                              |
| **Shutdown**   | `docker compose down`    | Fully stops and removes the temporary containers.           |
| **Full Reset** | `docker compose down -v` | Deletes all uploaded papers and drop database. (clean data) |

For full reset including pulling the latest image:

> Run this if the devs update the image(modify the code upstream)

```bash
docker compose down -v # <-- shutdown the system and clean the database/mocks
docker image rm r4ppzf/research-repo-backend:latest r4ppzf/research-repo-frontend:latest # <--- remove local image
docker compose pull # <--- pull the latest image
docker compose up -d # <--- run the system again
```

For more info about docker: [dockerdocsAI](https://docs.docker.com/)
