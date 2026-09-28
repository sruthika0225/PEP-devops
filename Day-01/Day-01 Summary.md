# PEP-DevOps – Day 1 Summary

## Topics Covered

### 1. Introduction to DevOps

DevOps is a software development methodology that brings Development (Dev) and Operations (Ops) together to improve the software development and delivery process.

The main focus is on automation, collaboration, continuous integration, continuous delivery/deployment, and monitoring.

### 2. DevOps Lifecycle

The DevOps process consists of several stages:

**Plan → Code → Build → Test → Release → Deploy → Operate → Monitor**

- **Plan** – Define requirements and plan the work.
- **Code** – Developers write and manage source code.
- **Build** – Convert source code into a build/package.
- **Test** – Verify that the application works correctly.
- **Release** – Prepare a tested version for delivery.
- **Deploy** – Deploy the application to the required environment.
- **Operate** – Manage the application in its running environment.
- **Monitor** – Continuously observe application and infrastructure performance.

The cycle is continuous, with feedback from monitoring being used to improve future development.

---

## 3. Automation in DevOps

DevOps uses automation throughout the lifecycle to reduce manual work and make software delivery faster and more consistent.

| Stage                  | Tools / Examples                |
| ---------------------- | ------------------------------- |
| Source Code Management | Git, GitHub                     |
| Build                  | Maven, Gradle, Python packaging |
| Testing                | Selenium, Postman               |
| Release / CI/CD        | Jenkins, GitHub Actions         |
| Deployment             | Docker                          |
| Operations             | Kubernetes                      |
| Monitoring             | CloudWatch, Prometheus, Grafana |

---

## 4. CI/CD

### CI – Continuous Integration

Developers frequently integrate their code changes into a shared repository. Automated builds and tests can then verify the changes.

### CD – Continuous Delivery / Continuous Deployment

After the code passes the required checks, it can be prepared for or automatically deployed to the target environment.

A simplified pipeline:

```text
Code
  ↓
Commit
  ↓
Build
  ↓
Test
  ↓
Release
  ↓
Deploy
  ↓
Monitor
```

---

# Source Code Management (SCM)

**SCM (Source Code Management)** is used to manage changes made to source code and other project files.

It helps developers:

- Track changes
- Maintain different versions
- Collaborate with other developers
- Revert unwanted changes
- Maintain project history

**Git** is a distributed version control system commonly used for SCM, while **GitHub** provides remote repository hosting and collaboration features.

---

# Centralized vs Distributed Version Control

## Centralized Version Control

In a centralized system, the main repository is maintained on a central server.

```text
             Server
              Repo
           /    |    \
          /     |     \
       PC #1   PC #2   PC #3
       Working Working Working
       Copy    Copy    Copy
```

Developers depend heavily on the central repository for version control operations.

## Distributed Version Control

In a distributed system, each developer has a local repository containing the project's history.

```text
              Remote Repository
               /      |      \
              /       |       \
          Local     Local    Local
           Repo      Repo     Repo
            |         |        |
         Working   Working  Working
          Copy      Copy     Copy
```

Git follows the **distributed version control** model.

The local repository maintains project history, allowing developers to perform many Git operations without constantly depending on the remote repository.

---

# Git Basics

## Clone a Repository

```bash
git clone <repository-url>
```

Downloads/clones a remote repository to the local machine.

## Check the Current Branch

```bash
git branch
```

## Create and Switch to a Branch

```bash
git checkout -b <branch-name>
```

Modern equivalent:

```bash
git switch -c <branch-name>
```

## Push Changes

```bash
git push origin main
```

Uploads local commits to the remote repository.

---

# Basic Git Workflow

```text
Working Directory
       ↓
     git add
       ↓
   Staging Area
       ↓
    git commit
       ↓
 Local Repository
       ↓
    git push
       ↓
 Remote Repository
```

---

# SSH Authentication

SSH authentication was also introduced.

An SSH key pair can be generated using:

```bash
ssh-keygen
```

The generated public key has the `.pub` extension.

The public key can be added to GitHub to authenticate Git operations through SSH.

---

# Important Git Commands

### Check Repository Status

```bash
git status
```

Shows the current state of the working directory.

### Stage a File

```bash
git add <file>
```

Stages a file for commit.

### Commit Changes

```bash
git commit -m "message"
```

Creates a commit with a descriptive message.

### Push Changes

```bash
git push
```

Uploads local commits to the remote repository.

### Pull Changes

```bash
git pull
```

Fetches and integrates changes from the remote repository.

### Clone a Repository

```bash
git clone <URL>
```

Creates a local copy of a remote repository.

---

# Key Takeaways

- DevOps combines development and operations practices.
- Automation is an important part of the DevOps lifecycle.
- The DevOps lifecycle includes **Plan, Code, Build, Test, Release, Deploy, Operate, and Monitor**.
- CI/CD helps automate building, testing, releasing, and deploying software.
- SCM helps manage and track source-code changes.
- Git is a distributed version control system.
- GitHub is commonly used to host Git repositories and collaborate on projects.
- Git uses concepts such as **repositories, branches, commits, staging, push, pull, and clone**.
- Docker can be used for deployment and containerization, while Kubernetes can manage containers.
- Monitoring tools help observe applications and infrastructure after deployment.

---

## Short Summary

> **Day 1 – PEP DevOps:** Introduction to DevOps and its lifecycle, including planning, coding, building, testing, releasing, deployment, operations, and monitoring. Covered CI/CD, automation, Source Code Management (SCM), centralized vs distributed version control, and Git/GitHub fundamentals including repositories, branches, commits, cloning, pushing, pulling, and SSH authentication.
