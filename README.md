# 📝 TODO App Dockerized – From Code to Container 🐳

> 🚀 A hands-on journey from cloning a real-world TODO web app to fully containerizing it using Docker and deploying it like a pro!

---

## 📁 Project Overview

This project demonstrates how to:

- Clone a frontend React TODO App
- Create a multi-stage Dockerfile
- Build and run the Docker image locally
- Push the image to Docker Hub
- Run the container anywhere and access it via `localhost`
- Debug using Docker commands
- Clean up Docker resources

---

## 📦 Tech Stack

- React (Frontend)
- Node.js (Build Stage)
- NGINX (Production Server)
- Docker 🐳

---

## 🧱 Dockerfile Breakdown

```dockerfile
FROM node:18-alpine AS installer
WORKDIR /app
COPY package*.json ./
RUN npm install 
COPY . .
RUN npm run build

FROM nginx:latest AS deployer
COPY --from=installer /app/build /usr/share/nginx/html
```

- **Stage 1:** Build the React app with Node.js
- **Stage 2:** Serve the static build with NGINX

---

## 🚀 Step-by-Step Guide

### ✅ Clone the Repo

```bash
git clone https://github.com/piyushsachdeva/todoapp-docker.git
cd todoapp-docker/
```

### ✅ Create Dockerfile

Create a file named `Dockerfile` and paste the above content.

### ✅ Build Docker Image

```bash
docker build -t todoapp-docker .
```

### ✅ Run Docker Container

```bash
docker run -dp 3000:80 todoapp-docker
```

Open your browser at 👉 `http://localhost:3000`

### ✅ Docker Push to Hub

```bash
docker login
docker tag todoapp-docker tanishprashar/todoapp-docker:latest
docker push tanishprashar/todoapp-docker:latest
```

### ✅ Pull and Run Anywhere

```bash
docker pull tanishprashar/todoapp-docker:latest
docker run -dp 3000:80 tanishprashar/todoapp-docker:latest
```

---

## 🔍 Useful Docker Commands

| Task | Command |
|------|---------|
| View containers | `docker ps` |
| View logs | `docker logs <container_id>` |
| Enter container | `docker exec -it <container_id> sh` |
| Inspect container | `docker inspect <container_id>` |
| Stop container | `docker stop <container_id>` |
| Remove image | `docker rmi <image_id>` |

---

## 🧠 What I Learned

✅ Multi-stage builds reduce image size  
✅ NGINX is perfect for serving static files  
✅ Port mapping is critical (`3000:80` vs `3000:3000`)  
✅ Debugging containers builds real-world confidence  
✅ From "just student" to **serious builder** 🔥

---

## 🧾 Author

**Tanish Prashar**  
📌 Learning Docker & DevOps the hands-on way!

---

## 🕓 Last Updated

2025-06-23

---
