# PEP DevOps — Day 01
**Date:** 28 September 2026

## 1. Git Basics

### SSH Key Generation
```bash
ssh-keygen -t rsa
```
- Generates an SSH key pair.
- The public key is saved with the `.pub` extension.
- The public key can be added to GitHub for authentication.

### Rename Branch
```bash
git branch -M main
```
- Renames the current branch to `main`.

### Push to Remote
```bash
git push origin main
```
- Pushes the local `main` branch to the remote repository.

---

## 2. Clone a Git Repository

### Clone with the Repository Name
```bash
git clone <repository-url>
```
- Clones the repository into the current directory.
- A folder with the repository name is created automatically.

### Clone with a Custom Folder Name
```bash
git clone <repository-url> <new-folder>
```
- Clones the repository into a folder with the specified local name.

---

## 3. Git Checkout

```bash
git checkout main
```
- Switches from the current branch to the `main` branch.
- Checkout can be used to switch between branches.

---

## 4. Git Stash

Git stash is used to temporarily save uncommitted changes so that the working directory becomes clean.

### Common Commands

```bash
git stash
```
- Temporarily stores the current uncommitted changes.

```bash
git stash list
```
- Displays the stashes that have been saved.

```bash
git stash pop
```
- Applies the most recent stash and removes it from the stash list.

```bash
git stash apply
```
- Applies a stash without removing it from the stash list.

```bash
git stash drop
```
- Deletes a selected stash.

### Example
If changes are being made on one branch but you need to switch to another branch:

```bash
git stash
git checkout main
```

Later, return to the original branch and restore the changes:

```bash
git stash pop
```

---

## 5. Git Rebase

Git rebase is used to move or replay commits from one branch on top of another branch.

### Basic Syntax

```bash
git rebase main
```

- Takes the commits from the current branch and reapplies them on top of the latest `main`.
- This can help maintain a cleaner, linear commit history.

### Typical Workflow

```bash
git checkout feature-branch
git rebase main
```

If conflicts occur:
1. Resolve the conflicts in the affected files.
2. Stage the resolved files:

```bash
git add .
```

3. Continue the rebase:

```bash
git rebase --continue
```

To cancel the rebase:

```bash
git rebase --abort
```

> **Note:** Rebase rewrites commit history, so care should be taken when rebasing branches that are already shared with others.

---

## 6. Git Staging Area

- The **staging area** is common to the working tree/repository, but a change only appears in a commit after it is staged and committed on that branch.
- A commit belongs to the branch on which the commit was created.

### Example

```bash
git status
```

If a file is shown as staged, it is ready to be included in the next commit.

Switching branches can show different committed states depending on the branch history.

---

## 7. Git Status and Commit Example

```bash
git status
```

Shows the current state of the working directory and staging area.

Example workflow:

```bash
git checkout main
git status
git add .
git commit -m "Update project"
git status
```

After committing, `git status` should show that the working tree is up to date if there are no other changes.

---

## 8. File Explorer / Opening Documents

- **Explorer** opens the file/folder explorer.
- Windows documents can be opened using File Explorer.
- Git Bash is mainly used for command-line Git operations.
- PowerShell can also be used for general Windows command-line operations.

---

# Virtualization

### Virtualization
- Virtualization means creating a virtual version of a computer/resource.
- A virtual machine (VM) allows an operating system to run inside another physical computer.

### Hypervisor
A hypervisor is software that creates and manages virtual machines.

### Practical Task
Install **Ubuntu Server OS** or create a VM for Ubuntu Server.

Example VM configuration:
- **VM Name:** Ubuntu Server
- **OS:** Ubuntu Server

---

# Monolithic Architecture

In a monolithic architecture, the application is built and deployed as a single unit.

Typical structure:

```text
UI
 ↓
Business Logic
 ↓
Data Access Layer
 ↓
Database
```

- The different application layers are part of one overall application.
- Deployment can involve deploying the complete application together.

---

# Microservices Architecture

In a microservices architecture, the application is divided into multiple small and independent services.

Each microservice performs a specific function and can have its **own database**.


                              UI
                          /    |    \
                         ↓     ↓     ↓
                  ┌───────────┐ ┌───────────┐ ┌───────────┐
                  │   Micro   │ │   Micro   │ │   Micro   │
                  │  service  │ │  service  │ │  service  │
                  └─────┬─────┘ └─────┬─────┘ └─────┬─────┘
                        ↓              ↓              ↓
                     ┌────┐         ┌────┐         ┌────┐
                     │ DB │         │ DB │         │ DB │
                     └────┘         └────┘         └────┘

### Microservice Concept

The idea behind microservices is that an application can be broken down into smaller, composable pieces that work together.

- Each component/service can be developed separately.
- Services can be maintained independently.
- The complete application is formed by combining the services.

### Monolithic vs Microservices

| Monolithic | Microservices |
|---|---|
| One major application unit | Multiple smaller services |
| Components are tightly grouped | Services are independently developed |
| Often deployed as one unit | Services can be deployed independently |
| Usually uses a shared application structure | Each service can have its own database |

---

# Docker

## Docker Registry

A Docker registry is a storage/distribution component for Docker images.

Docker images can be stored in:
- Public registries
- Private registries

### Docker Hub
**Docker Hub** is Docker's public cloud-based registry.

It can be used to:
- Store Docker images
- Search for images
- Pull images
- Push images

Official Docker documentation:
**https://docs.docker.com/**

---

# Docker Architecture

Main Docker components:

```text
User / Client
     ↓
Docker Host
     ↓
Docker Daemon
     ↓
Containers
     ↓
Images

Docker Registry
```

### Docker Client
The Docker CLI is used to send commands such as:

```bash
docker build
docker pull
docker run
```

### Docker Daemon
- The Docker daemon (`dockerd`) is the engine responsible for managing Docker objects such as containers and images.

### Docker Host
- The machine where Docker is running.
- It contains the Docker daemon, containers, images, etc.

### Docker Registry
- Stores and distributes Docker images.
- Docker Hub is a commonly used public registry.

---

# Docker Images

## Search for an Image

```bash
docker search <image-name>
```

Example:

```bash
docker search node
```

- Searches for images in Docker Hub.
- Official images are marked as official on Docker Hub.

## Pull an Image

```bash
docker pull <image-name>
```

Example:

```bash
docker pull node
```

- Downloads the image from the registry to the local machine.

## List Local Images

```bash
docker images
```

- Lists the Docker images available locally.
- Each Docker image has an image ID.

---

# Creating and Running Containers

## Create a Container

```bash
docker create <image-name>
```

- Creates a container from an image.
- Creation does not start the container.

## Create a Container with a Custom Name

```bash
docker create --name <container-name> <image-name>
```

Example:

```bash
docker create --name demon httpd
```

- `--name` assigns a custom name to the container.

## List All Containers

```bash
docker ps -a
```

- Lists all containers, including stopped containers.

## List Running Containers

```bash
docker ps
```

- Lists only currently running containers.

## Start a Container

```bash
docker start <container-name>
```

or

```bash
docker start <container-id>
```

Example:

```bash
docker start optimistic_mclean
```

---

# Docker Ports

Some common ports discussed:

| Service | Port |
|---|---:|
| HTTP | 80 |
| HTTPS | 443 |
| SSH | 22 |
| RDP | 3389 |

### HTTP
- HTTP is commonly used for web traffic.
- Port **80** is the default HTTP port.

### HTTPS
- HTTPS is the secure version of HTTP.
- Port **443** is the default HTTPS port.

---

# Web Servers

### Apache HTTP Server
- Apache is a popular web server.
- It can be used to host static websites.

### Nginx
- Nginx is another popular web server.
- It is commonly used for web hosting, reverse proxying, and handling high traffic.

---

# Docker Container Lifecycle

Basic flow:

```text
Docker Image
     ↓
docker create
     ↓
Container Created
     ↓
docker start
     ↓
Running Container
```

Another common command is:

```bash
docker run <image-name>
```

`docker run` generally creates a container from the image and starts it.

---

# Important Commands — Quick Revision

```bash
# Git
git branch -M main
git push origin main
git clone <repository-url>
git clone <repository-url> <folder-name>
git checkout main
git status

# Git Stash
git stash
git stash list
git stash pop
git stash apply
git stash drop

# Git Rebase
git rebase main
git add .
git rebase --continue
git rebase --abort

# Docker
docker search <image-name>
docker pull <image-name>
docker images
docker create <image-name>
docker create --name <container-name> <image-name>
docker ps
docker ps -a
docker start <container-name>
docker run <image-name>
```

## Key Takeaways

- **Git Clone** → downloads a repository to the local machine.
- **Git Checkout** → switches branches.
- **Git Stash** → temporarily stores uncommitted changes.
- **Git Rebase** → reapplies commits on top of another branch.
- **Virtualization** → runs a virtual computer/OS using a VM.
- **Monolithic Architecture** → application is organized as one major unit.
- **Microservices Architecture** → application is split into smaller independent services.
- **Docker Image** → template used to create containers.
- **Docker Container** → running/created instance based on an image.
- **Docker Registry** → stores and distributes Docker images.
- **Docker Hub** → a public Docker registry.
- **Docker Daemon** → manages Docker containers, images, and other Docker resources.
