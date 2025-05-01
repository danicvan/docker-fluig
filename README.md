# 🚀 Fluig in Docker (Development Environment)

[![Docker](https://img.shields.io/badge/Docker-Supported-blue)](https://www.docker.com/)
[![License Required](https://img.shields.io/badge/License-TOTVS--Fluig-yellow)](https://suporte.totvs.com/)
[![Fluig Version](https://img.shields.io/badge/Fluig-1.8.1-green)](https://suporte.totvs.com/)
[![MailDev](https://img.shields.io/badge/MailDev-Enabled-orange)](https://github.com/maildev/maildev)

This project provides a Docker setup to run **Fluig** in a local development environment.

> ⚠️ **Important:** This repository **DOES NOT** include the Fluig installer, as it is restricted to authorized TOTVS users. You must download it manually from the official TOTVS website.

---

## 📌 Requirements

- Valid **License Server** (Fluig only runs in demo mode for 7 days without one).
- Fluig Installer 1.8.1 for Linux (download from the [TOTVS Download Center](https://suporte.totvs.com/portal/p/10098/suporte-fluig-download#000035/FLUIG%201.8/Fluig/)).

---

## 🐳 Containers

This setup includes the following services via Docker:

- `Fluig`
- `MySQL 8.0`
- `MailDev` (for testing email delivery)

---

## ⚙️ Getting Started

1. Download the Fluig 1.8.1 installer (Linux) and extract it into the folder:

   ```
   image/installer/
   ```

2. (Optional) Change the `TZ` (timezone) in the `.env` file (default is `America/Sao_Paulo`).

3. Run the following command to start the containers:

   ```bash
   docker compose up -d
   ```

   On first run, Docker will build the custom Fluig image, run the installer, and apply initial settings.

---

## 🔐 Default Login (Initial Setup)

After installation, access Fluig and create your company via **WCMAdmin**:

- **URL:** [http://127.0.0.1:8080](http://127.0.0.1:8080)  
- **Login:** `wcmadmin`  
- **Password:** `adm`  

---

## 🗂 Persistent Volumes

Fluig volumes are persisted at:

```
/var/fluig-volume
```

For each company, use a dedicated subdirectory, e.g.:

```
/var/fluig-volume/company001
```

---

## 📧 MailDev & Database Access

- **MailDev (view sent emails):** [http://127.0.0.1:1080](http://127.0.0.1:1080)
- **MySQL Database:**
  - Host: `localhost`
  - Port: `3306`
  - User: `root`
  - Password: `rootpassword`
  - JDBC URL (for DBeaver, use URL connection mode):
  
    ```
    jdbc:mysql://localhost:3306/fluig?allowPublicKeyRetrieval=true&useSSL=false
    ```

---

## 🧪 Useful Docker Commands

Run the following in your terminal:

| Action                                   | Command                                 |
|------------------------------------------|------------------------------------------|
| Start all services                       | `docker compose up -d`                   |
| Stop services                            | `docker compose stop`                    |
| Stop and remove all containers¹          | `docker compose down`                    |
| Access Fluig container bash              | `docker compose exec fluig bash`         |
| View Fluig logs (inside the container)   | `log`                                    |

> ¹ If you want a clean install, remove the Docker volume manually via Docker Desktop or CLI to avoid residual data.
