# 🏙️ Docker Town - Multi-Service City Setup

This project sets up a small Docker-based "city" with multiple interconnected services: an Nginx web server, a proxy, a DNS server, and a database.

---
<img width="715" alt="Screenshot 2025-06-14 at 9 33 47 AM" src="https://github.com/user-attachments/assets/500998ba-6233-4f6f-a2dc-9c068dd214ff" />


---


## 📦 Services

| Service      | Description                     | Port Mapping       | Container Name   |
|--------------|---------------------------------|--------------------|------------------|
| **Nginx**     | Main web server                  | `80 → 80`          | `nginxcity_v2`   |
| **Proxy**     | Reverse proxy or test gateway    | `8080 → 80`        | `proxycity`      |
| **DNS**       | DNS server (dnsmasq)             | `5354 → 5353/udp`  | `dnscity`        |
| **Postgres**  | PostgreSQL database              | `5432` (internal)  | `dbcity`         |

---

## 🐳 Running Containers

You can start the containers manually:


# Build and run Nginx
cd city-nginx
docker build -t city-nginx .
docker run -d -p 80:80 --name nginxcity_v2 city-nginx

# Start database
cd ../city-db
docker run -d --name dbcity docker-town-dbcity

# Start proxy
cd ../city-proxy
docker run -d -p 8080:80 --name proxycity docker-town-proxycity

# Start DNS on non-conflicting port (5354)
cd ../city-dns
docker run -d --name dnscity -p 5354:5353/udp docker-town-dnscity

---
<img width="272" alt="Screenshot 2025-06-14 at 9 31 50 AM" src="https://github.com/user-attachments/assets/19f255bb-1ba0-4ef4-a761-78f0d0ac2c8f" />







