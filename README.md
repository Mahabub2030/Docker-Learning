# 🐳 Docker 101: Core Concepts & 50 Essential Q&As

Welcome to the ultimate Docker interview prep and foundational guide! This repository provides a comprehensive breakdown of what Docker is, how it works, and a curated list of **50 essential questions and answers** categorized to help you master containerization.

---

## 📌 What is Docker?

**Docker** is an open-source platform that automates the deployment, scaling, and management of applications using **containerization**.

Instead of packaging an application along with an entire operating system (like a traditional Virtual Machine), Docker bundles the application code, runtime, system tools, libraries, and settings into a lightweight, isolated unit called a **container**. This ensures that the application runs exactly the same way regardless of the environment—whether it's on a local laptop, a testing server, or a production cloud environment. It effectively solves the classic developer excuse: _"But it works on my machine!"_

---

## 🗺️ Table of Contents

1. [Core Concepts & Architecture (1–15)](#part-1-core-concepts--architecture-115)
2. [Basic Operations & Essential CLI Commands (16–30)](#part-2-basic-operations--essential-cli-commands-1630)
3. [Data Management & Networking (31–40)](#part-3-data-management--networking-3140)
4. [Advanced Operations & Best Practices (41–50)](#part-4-advanced-operations--best-practices-4150)

---

## 🧠 Questions & Answers

### Part 1: Core Concepts & Architecture (1–15)

<details>
<summary><b>1. What is the main difference between a Docker container and a Virtual Machine (VM)?</b></summary>
Virtual Machines include a full guest operating system and run on physical hardware via a hypervisor, making them heavy and slow to boot. Docker containers share the host OS kernel and isolate the application processes from each other, making them lightweight, fast, and resource-efficient.
</details>

<details>
<summary><b>2. What is a Docker Image?</b></summary>
A Docker Image is a read-only, immutable blueprint or template containing the source code, libraries, dependencies, and tools required to run an application. Images are used to create Docker containers.
</details>

<details>
<summary><b>3. What is a Docker Container?</b></summary>
A Docker Container is a live, runnable runtime instance of a Docker Image. It represents an isolated environment where the application actually executes.
</details>

<details>
<summary><b>4. What is a Dockerfile?</b></summary>
A Dockerfile is a plain-text script that contains an ordered collection of instructions and commands. Docker reads these instructions sequentially to automatically build a Docker Image.
</details>

<details>
<summary><b>5. What is the Docker Daemon (`dockerd`)?</b></summary>
The Docker Daemon is a persistent background process that runs on the host operating system. It listens for Docker API requests and manages Docker objects like images, containers, networks, and volumes.
</details>

<details>
<summary><b>6. What is the Docker Client?</b></summary>
The Docker Client (`docker`) is the primary Command Line Interface (CLI) tool that users interact with. When you type a command like `docker run`, the client transmits the command to the Docker Daemon via a REST API to carry out the operation.
</details>

<details>
<summary><b>7. What is Docker Hub?</b></summary>
Docker Hub is a public, cloud-based registry service provided by Docker. It allows developers to find, share, and store public or private Docker images.
</details>

<details>
<summary><b>8. What is a Docker Registry?</b></summary>
A Docker Registry is a centralized storage and distribution system for Docker images. Docker Hub is a public registry, but organizations can also host private registries (e.g., AWS ECR, Google Artifact Registry).
</details>

<details>
<summary><b>9. What is the purpose of the `FROM` instruction in a Dockerfile?</b></summary>
The `FROM` instruction initializes a new build stage and sets the **Base Image** for subsequent instructions (e.g., `FROM node:20` or `FROM ubuntu:latest`). Every valid Dockerfile must start with a `FROM` instruction.
</details>

<details>
<summary><b>10. What is the difference between `RUN`, `CMD`, and `ENTRYPOINT` in a Dockerfile?</b></summary>

- **`RUN`:** Executes commands during the image _building_ process to install packages and layers.
- **`CMD`:** Defines the default command and arguments that run when a container _starts_. It can be overridden by CLI arguments.
- **`ENTRYPOINT`:** Configures a container to run as an executable. CLI arguments are appended to it rather than overriding it.
</details>

<details>
<summary><b>11. What are Docker Layers?</b></summary>
A Docker image consists of a series of read-only layers. Each instruction in a Dockerfile (like `RUN`, `COPY`) creates a new layer. Docker caches these layers to speed up subsequent image builds.
</details>

<details>
<summary><b>12. What is the Copy-on-Write (CoW) strategy?</b></summary>
When a container is started, Docker adds a thin, writable layer on top of the read-only image layers. If a process inside the container needs to modify a file from the image, Docker copies the file up to the writable container layer before modifying it, leaving the original image layer untouched.
</details>

<details>
<summary><b>13. What is Docker Compose?</b></summary>
Docker Compose is a tool used for defining and running multi-container applications. It utilizes a single YAML file (`docker-compose.yml`) to configure application services, networks, and volumes, allowing you to spin up the entire stack with a single command (`docker-compose up`).
</details>

<details>
<summary><b>14. What is Docker Swarm?</b></summary>
Docker Swarm is Docker’s native clustering and container orchestration tool. It allows you to manage multiple Docker hosts as a single virtual host, handling scaling, rolling updates, and service discoveries.
</details>

<details>
<summary><b>15. How do namespaces provide isolation in Docker?</b></summary>
Docker utilizes Linux **namespaces** to provide isolated workspaces for containers. When a container runs, Docker creates namespaces for various aspects (like `pid` for processes, `net` for networking, and `mnt` for file systems) to ensure the container cannot see or affect resources outside its scope.
</details>

---

### Part 2: Basic Operations & Essential CLI Commands (16–30)

<details>
<summary><b>16. How do you check the installed version of Docker on your machine?</b></summary>

```bash
docker --version
# Or for detailed information:
docker version
```
