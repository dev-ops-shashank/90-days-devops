# 90-Days DevOps Learning Roadmap

Welcome to the **90-Days DevOps Learning Roadmap** repository! This README outlines a structured, three-month journey designed to transform you into a confident, hands-on DevOps practitioner. Each week contains clear learning objectives, hands-on exercises, resources, and deliverables. Use this roadmap to post daily updates on your progress.

---

## Table of Contents

1. [Introduction](#introduction)
2. [Repository Structure](#repository-structure)
3. [Environment Setup](#environment-setup)
4. [3-Month Learning Path Overview](#3-month-learning-path-overview)
   - [Month 1: Fundamentals (Weeks 1–4)](#month-1-fundamentals-weeks-1-4)
   - [Month 2: Intermediate Tools (Weeks 5–8)](#month-2-intermediate-tools-weeks-5-8)
   - [Month 3: Advanced DevOps & Capstone (Weeks 9–12)](#month-3-advanced-devops--capstone-weeks-9-12)
5. [Weekly Routine & Time Management](#weekly-routine--time-management)
6. [How to Use This Repo](#how-to-use-this-repo)
7. [Daily Updates](#daily-updates)
8. [Reflection & Next Steps](#reflection--next-steps)

---

## Introduction

This repository documents a **90-day, self-paced DevOps learning path** built to provide a strong foundation in Linux, networking, Git, CI/CD, containerization, infrastructure as code, configuration management, Kubernetes, monitoring, and more. By following this plan:

- You’ll gain practical, hands-on experience using free tools on a WSL Ubuntu environment.
- You’ll build small projects and scripts to reinforce learning.
- You’ll end each week with deliverables you can add to your resume or GitHub portfolio.
- You’ll post daily updates (Monday–Saturday) on your progress.

**Who is this for?**  
- Beginners with minimal hands-on DevOps exposure.  
- Professionals looking to transition into DevOps roles.  
- Anyone who prefers a structured, incremental plan.

> **Note**: This plan assumes you have a Windows host with WSL Ubuntu installed, and that you’ve installed Git, Docker (via Docker Desktop), Terraform, Ansible, Kind, Python, and a CI/CD tool (e.g., GitHub Actions). Adjust paths and commands if you use a different environment.

---

## Repository Structure

Each week’s content will live in its own directory under `weekX/`. Folders and files will include scripts, Markdown notes, logs, and project deliverables. Example structure:

```
90-days-devops/
├─ week1/
│   ├─ commands/
│   ├─ scripts/
│   ├─ projects/
│   ├─ logs/
│   └─ README.md
├─ week2/
│   └─ ...
├─ ...
└─ README.md
```

Your **daily posts** (Monday–Saturday) will reflect which files you updated, what you learned, and any challenges you overcame.

---

## Environment Setup

Before starting Week 1, ensure your environment is ready. On your Windows host:

1. **Install WSL Ubuntu 20.04**  
   ```powershell
   wsl --install -d Ubuntu-20.04
   ```
   Complete the Linux user setup when prompted.

2. **Limit WSL Memory & CPU**  
   Create a `C:/Users/<YourUser>/.wslconfig` file with:
   ```ini
   [wsl2]
   memory=4GB
   processors=2
   swap=0
   ```
   Then run:
   ```powershell
   wsl --shutdown
   ```

3. **Update Ubuntu & Install Core Packages**  
   In WSL Ubuntu:
   ```bash
   sudo apt update && sudo apt upgrade -y
   sudo apt install git python3 python3-pip ansible docker.io curl wget net-tools tree -y
   ```

4. **Install Docker Desktop**  
   - Download Docker Desktop (Community) for Windows.
   - Enable “Use the WSL 2 based engine” and integrate with Ubuntu-20.04.
   - Verify in WSL:  
     ```bash
     docker --version
     docker run hello-world
     ```

5. **Install Terraform**  
   ```bash
   curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
   sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
   sudo apt update && sudo apt install terraform -y
   terraform -v
   ```

6. **Install Kind (Kubernetes in Docker)**  
   ```bash
   curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
   chmod +x ./kind
   sudo mv kind /usr/local/bin/
   kind version
   ```

7. **Install Kubectl**  
   ```bash
   sudo apt install kubectl -y
   kubectl version --client
   ```

8. **Install Jenkins (optional)**  
   If you prefer Jenkins locally, install on Windows host and access via `http://localhost:8080`. For this plan, we primarily use **GitHub Actions**.

---

## 3-Month Learning Path Overview

### Month 1: Fundamentals (Weeks 1–4)

> **Goal**: Build a solid foundation in Linux, shell scripting, Git, networking basics, and introductory CI/CD.

- **Week 1**: Linux & Shell Scripting  
  - Filesystem navigation, commands, permissions  
  - Editors (nano/vim), STDIN/STDOUT/STDERR, redirection, pipes  
  - Bash scripting: variables, conditionals, loops, functions  
  - Small projects: cleanup scripts, log analyzer, backup automation  

- **Week 2**: Git & Version Control  
  - Git fundamentals: init, commit, branch, merge, conflict resolution  
  - Remote workflows: GitHub repo creation, PRs, branching strategies  
  - Hands-on: Set up a personal GitHub repo, push commits, open pull requests  

- **Week 3**: Networking & Linux System Administration  
  - Network basics: IP, ports, DNS, HTTP vs. HTTPS  
  - Linux process management (`ps`, `top`), services (`systemctl`), logs (`/var/log`)  
  - Package management (`apt`) and basic service configuration (e.g., Apache2)  

- **Week 4**: Basic CI/CD with GitHub Actions  
  - Introduction to CI/CD concepts and workflow  
  - Build simple GitHub Actions workflows: checkout, build, test steps  
  - Hands-on: Create a sample Node.js or Python project and automate builds/tests  

### Month 2: Intermediate DevOps Tools (Weeks 5–8)

> **Goal**: Gain proficiency in containerization, configuration management, and Infrastructure as Code.

- **Week 5**: Docker Fundamentals  
  - Container vs. VM, Docker architecture basics  
  - `docker run`, `docker build`, `docker ps`, `docker images`, `docker rm`, `docker rmi`  
  - Hands-on: Build and run a simple Python “Hello, Docker!” image; push to Docker Hub  

- **Week 6**: Advanced Docker & Docker Compose  
  - Docker networking (bridge, host), volumes for persistent storage  
  - Docker Compose: define multi-container applications (`docker-compose.yml`)  
  - Hands-on: Build a Node.js + MongoDB stack with Compose, persist data with volumes  

- **Week 7**: Configuration Management with Ansible  
  - Ansible architecture: control node, inventory, modules, playbooks  
  - Playbook basics: install packages, copy files, manage services  
  - Hands-on: Create playbooks to configure and deploy a simple web server  

- **Week 8**: Infrastructure as Code (Terraform)  
  - Terraform basics: providers, resources, variables, state files  
  - Local testing with `null_resource` and file provisioners (no cloud cost)  
  - Hands-on: Write Terraform config to create a local file, run `terraform apply` and `destroy`  

### Month 3: Advanced DevOps & Capstone (Weeks 9–12)

> **Goal**: Master advanced CI/CD pipelines, Kubernetes orchestration, and monitoring.

- **Week 9**: Advanced CI/CD (GitHub Actions & Jenkins Pipelines)  
  - Complex GitHub Actions workflows: matrix builds, caching, Docker build/push  
  - Jenkins Pipeline (Declarative) examples: build, test, deploy stages  
  - Hands-on: Automate Docker image build and push for a sample microservice  

- **Week 10**: Kubernetes with Kind (Setup & Basics)  
  - Kubernetes architecture: Pods, Services, Deployments, ReplicaSets  
  - Spin up a Kind cluster, interact with `kubectl`  
  - Hands-on: Deploy Nginx Deployment & Service, scale replicas, perform rollouts  

- **Week 11**: Helm & Advanced Kubernetes Concepts  
  - Helm charts: package, install, upgrade applications  
  - ConfigMaps, Secrets, Ingress Controllers, StatefulSets  
  - Hands-on: Deploy a MongoDB Helm chart, configure Ingress for Nginx  

- **Week 12**: Monitoring & Logging (Prometheus & Grafana)  
  - Monitoring stack: Prometheus for metrics, Grafana for dashboards  
  - Deploy Prometheus & Grafana on Kind via Helm  
  - Hands-on: Build a simple Python app exposing Prometheus metrics; visualize in Grafana  

---

## Weekly Routine & Time Management

- **Monday–Friday**:  
  - **1.5 hours/day** in the evening.  
  - Watch tutorial videos, read documentation, practice commands.  

- **Saturday (3 hours)**:  
  - Complete hands-on projects, write scripts/playbooks/manifests.  
  - Document progress in a Markdown file under each `weekX/` directory.  

- **Sunday**: Rest & self-reflection.  
  - Prepare for the next week: skim upcoming topics, gather resources.  

Use techniques like the Pomodoro (25 min focus, 5 min break) to maintain consistency. Maintain a **DevOps Journal** (Markdown) summarizing:
- What you learned.
- Challenges you faced.
- Commands/scripts you wrote.
- Links to relevant resources.

---

## How to Use This Repo

1. **Clone the Repo**  
   ```bash
   git clone https://github.com/<your-username>/90-days-devops.git
   cd 90-days-devops
   ```

2. **Navigate to Each Week’s Folder**  
   - Example: `cd week1` to review Linux & Shell Scripting content.  
   - Each folder will contain:  
     - `commands/`: sample command outputs or notes.  
     - `scripts/`: Bash scripts you create.  
     - `projects/`: mini-projects and their deliverables.  
     - `logs/`: any logs or reports generated.  
     - `README.md`: summary and instructions for that week.  

3. **Daily Updates**  
   - Create or update Markdown or text files describing your daily progress.  
   - Commit changes regularly, e.g.:  
     ```bash
     git add .
     git commit -m "Day 3: Completed log_analyzer.sh and summary report"
     git push origin main
     ```  
   - This way, your GitHub history reflects your learning journey.

---

## Daily Updates

Post **six** updates per week (Monday–Saturday) as small commits and optionally on social media. For inspiration, refer to these example X (Twitter) posts:

1. **Day 1**: “Day 1: Kicked off Week 1—explored Linux filesystem (`ls`, `cd`, `mkdir`), modified permissions (`chmod`), and logged actions. #Linux #DevOps”
2. **Day 2**: “Day 2: Mastered nano/vim, deep-dived into `chmod` and `chown`. Built `perm_check.sh` and `cleanup.sh`. CLI is clicking! #ShellScripting”
3. **Day 3**: “Day 3: Redirection and piping—redirected stdout/stderr, used `grep` and wrote `log_analyzer.sh`. Data flows like a pro! #Bash”
4. **Day 4**: “Day 4: Variables, conditionals, loops in Bash. Created `greet_user.sh`, `check_file.sh`, and `bulk_backup.sh`. One step closer! #Coding”
5. **Day 5**: “Day 5: Wrote math functions in `math_ops.sh`, handled errors in `safe_run.sh`, and modularized code in `common.sh`. Bash fun! #Scripting”
6. **Day 6**: “Day 6: Completed `health_check.sh` for system metrics. Pushed Week 1 to GitHub: `90-days-devops/week1`. Ready for Week 2! #GitHub #DevOps”

Feel free to adapt these for your own style or platform.

---

## Reflection & Next Steps

- At the end of each month, review your progress. Identify weak areas (e.g., syntax errors, conceptual gaps) and adjust upcoming weeks accordingly.
- Engage with DevOps communities:  
  - Reddit: r/devops, r/linux, r/kubernetes  
  - Slack/Discord channels (e.g., KodeKloud, Kubernetes Slack)  
- By Day 90, you will have a solid portfolio demonstrating:  
  - Linux command line mastery  
  - Git version control proficiency  
  - CI/CD pipeline automation with GitHub Actions  
  - Containerization with Docker & Compose  
  - Configuration management using Ansible  
  - Infrastructure as Code with Terraform  
  - Kubernetes cluster deployments (Kind) and Helm chart usage  
  - Monitoring and observability with Prometheus & Grafana  

Congratulations on embarking on this journey! Remember: consistent practice beats cramming. Good luck, and happy learning! 🚀

---

*(This README was generated to guide and document your 90-day DevOps learning path. Feel free to fork, tweak, and personalize as needed.)*
