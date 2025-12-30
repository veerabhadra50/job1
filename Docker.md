# =========================================================
# DOCKER, DOCKER COMPOSE & MULTISTAGE BUILD (ONE PAGE)
# =========================================================

# -------------------------
# WHAT IS DOCKER?
# -------------------------
# Docker is a container tool that packages:
# - Application code
# - Dependencies
# - Environment
# So the app runs the same everywhere.

# -------------------------
# BUILD DOCKER IMAGE
# -------------------------
# Builds image using Dockerfile in current directory
docker build -t myapp .

# -------------------------
# RUN DOCKER CONTAINER
# -------------------------
# Runs container in background and maps port 3000
docker run -d -p 3000:3000 myapp

# -------------------------
# LIST IMAGES & CONTAINERS
# -------------------------
docker images        # list images
docker ps            # running containers
docker ps -a         # all containers

# -------------------------
# STOP & REMOVE CONTAINER
# -------------------------
docker stop container_id
docker rm container_id

# -------------------------
# REMOVE IMAGE
# -------------------------
docker rmi image_id


# =========================================================
# DOCKER COMPOSE
# =========================================================
# Docker Compose runs multiple containers using one file

# Start services
docker-compose up

# Start services in background
docker-compose up -d

# Stop and remove services
docker-compose down

# Build services
docker-compose build

# View logs
docker-compose logs

# List running services
docker-compose ps


# =========================================================
# WHY MULTISTAGE BUILD?
# =========================================================
# Problem:
# - Large image size
# - Build tools included (npm, gcc)
# - Less secure
#
# Solution:
# - Multistage build
# - One stage for build
# - One stage for runtime
# - Final image is small & secure


# =========================================================
# MULTISTAGE DOCKERFILE (NODE.JS)
# =========================================================

FROM node:18 AS builder
# Build stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:18-alpine
# Runtime stage
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/package*.json ./
RUN npm install --only=production
EXPOSE 3000
CMD ["node", "dist/index.js"]


# =========================================================
# docker-compose.yml (EXAMPLE)
# =========================================================

version: "3.9"
services:
  app:
    build: .
    ports:
      - "3000:3000"
    restart: always


# =========================================================
# RUN APPLICATION USING COMPOSE
# =========================================================
docker-compose build
docker-compose up -d

# =========================================================
# STOP APPLICATION
# =========================================================
docker-compose down

# =========================================================
# END
# =========================================================
