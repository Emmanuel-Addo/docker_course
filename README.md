# Docker Course Projects

This repository contains various projects demonstrating Docker setups, configurations, and best practices for different web development stacks (React, Next.js, MERN, etc.).

## Repository Structure

The workspace is organized into separate directories, each focusing on a specific Docker containerization scenario:

*   **[hello-docker](./hello-docker/)**: A basic introductory Docker project.
*   **[react-docker](./react-docker/)**: A React application built with Vite and dockerized. Demonstrates bind mounts, ports mapping, and Hot Module Replacement (HMR) polling configuration to allow hot-reloading on Windows hosts.
*   **[next-docker](./next-docker/)**: A Next.js application containerized with Docker. Features advanced configurations like Compose File Watch (`develop.watch` sync/rebuild) for developer productivity.
*   **[mern-docker](./mern-docker/)**: A full-stack MERN (MongoDB, Express, React, Node) application configured using Docker Compose to orchestrate multiple services (frontend, backend, database).
*   **[vite-project](./vite-project/)**: Another Vite-based application configuration with Docker.

---

## Getting Started

### Prerequisites

*   [Docker Desktop](https://www.docker.com/products/docker-desktop) installed and running.
*   Node.js and npm/yarn (optional, for running locally without Docker).

### Configuration & Secrets

Some services (like `next-docker`) require environment variables. 
1. Create a `.env` file in the sub-project directory (e.g., `next-docker/.env`).
2. Add your environment variables as shown in the respective `.env.example` files:
   ```env
   DB_URL=mongodb+srv://username:password@cluster.mongodb.net/
   ```

> [!WARNING]
> Never commit `.env` files containing actual passwords or secret tokens to GitHub. They are ignored by the `.gitignore` rules in this repository.

---

## Common Development Commands

### 1. React Project (using Docker Run)

Run the container with a bind mount to enable live updates:
```bash
cd react-docker
docker run -p 5173:5173 -v ${PWD}:/app -v /app/node_modules react-docker
```

### 2. Next.js Project (using Docker Compose Watch)

To spin up the service and automatically rebuild or sync changes on edit:
```bash
cd next-docker
docker compose up
```
