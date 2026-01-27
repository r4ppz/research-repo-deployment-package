# Research Repository - Setup & User Guide

This system runs entirely inside **Docker**. You do not need to install any databases or programming languages.
See the documentation for more info about the project: [research-repo-docs](https://r4ppz.github.io/research-repo-docs/)

---

## 1. Prerequisites (One-Time Setup)

1. **Install Docker Desktop**: Download and install for Windows:
   [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/).
2. **Start Docker**: Open the "Docker Desktop" app. Wait until the whale icon in your taskbar turns green.

---

## Managing User Roles (Admin/Teacher/Student)

The system uses your **Google Email** to determine what you see. By default, everyone is a **Student**. To test the Admin or Teacher interfaces, you must manually "promote" your email.

1. Open `privileged-users.yaml` in Notepad or VS Code.
2. Add your email address under the desired category:

- **Super Admin**: Full control over all departments.
- **Department Admin (Teacher)**: Control over a specific department ID.

3. **Important**: If your email is NOT in this file, the system defaults you to the **Student** role.

### To Apply Role Changes:

Whenever you edit `privileged-users.yaml`, you **must restart** the backend to load the new permissions. Run this in your terminal:

```bash
docker compose restart backend
```

---

## 3. How to Run the System

1. Open this folder in Windows File Explorer.
2. Right-click on any empty space inside the folder and select "Open in Terminal" (or "Open PowerShell window here").
3. In the terminal window that opens, type the following command and press Enter:

```bash
docker compose up -d
```

4. **Access the App**: Open your browser to [http://localhost](http://localhost)

---

## 4. Control Commands

| Action         | Command                  | Description                                                                                        |
| -------------- | ------------------------ | -------------------------------------------------------------------------------------------------- |
| **Start**      | `docker compose up -d`   | Starts everything in the background.                                                               |
| **Stop**       | `docker compose stop`    | Halts the app but keeps your data/uploads safe.                                                    |
| **Resume**     | `docker compose start`   | Quickly wakes the app back up.                                                                     |
| **Shutdown**   | `docker compose down`    | Fully stops and removes the temporary containers.                                                  |
| **Full Reset** | `docker compose down -v` | **WARNING**: Deletes all uploaded papers and database entries. Use this for a "Day 1" clean slate. |
