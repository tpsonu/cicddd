# BarterBee Infrastructure : Multi-AZ AWS Cloud Architecture & Automated CI/CD Pipeline

<p align="center">
  <img src="projectpic/work-flow.png" alt="BarterBee Cloud Architecture Workflow" width="850"/>
</p>

Deploying stateful production workloads on cloud environments requires robust, fault-tolerant infrastructure designed to handle single-zone outages, dynamic traffic surges, and continuous software releases without downtime. Without proper load balancing, multi-AZ redundancy, and deployment automation, cloud applications remain vulnerable to single-point-of-failure outages and high operational overhead.

**BarterBee Infrastructure** is a multi-AZ AWS cloud deployment showcasing production-grade DevOps engineering practices. It hosts a full-stack peer-to-peer web application across multiple Availability Zones, backed by an AWS Application Load Balancer, AWS S3 media storage, MongoDB Atlas, and a fully automated zero-downtime GitHub Actions CI/CD pipeline.

Using this infrastructure setup, key DevOps patterns demonstrate:
- Multi-Availability Zone (Multi-AZ) Redundancy & High Availability
- Application Load Balancing (ALB) & Active Health Check Isolation
- Decoupled Stateless Compute & AWS S3 Cloud Storage Integration
- Zero-Downtime Automated CI/CD via GitHub Actions & SSH Workflows
- Process Management, Logging, & Crash Recovery with PM2

---

## Built With

* AWS EC2 (Ubuntu 22.04 LTS)
* AWS Application Load Balancer (ALB)
* AWS S3 (Simple Storage Service)
* GitHub Actions (CI/CD Automation)
* PM2 (Node Process Manager)
* Node.js & Express
* React
* MongoDB Atlas

---

## Key Infrastructure Features

The cloud infrastructure encompasses multi-tier redundancy and deployment automation designed to ensure 99.9% uptime SLA.

* **Multi-AZ EC2 Compute Fleet**: Concurrent compute nodes running across separate Availability Zones (`us-east-1a`, `us-east-1b`).
* **Application Load Balancing**: Intelligent HTTP traffic distribution across instances with continuous target group health checking.
* **Automated CI/CD Pipeline**: Instant multi-node code synchronization and building triggered automatically on GitHub pushes.
* **Stateless Media Storage**: Offloaded file uploads directly to AWS S3, removing local filesystem dependencies from application nodes.
* **Managed PM2 Runtime**: Automated process daemonization, log management, and instant recovery upon node failure.

---

# Getting Started

### Prerequisites
* An active **AWS Account** with permissions for EC2, ALB, S3, and Security Groups.
* **GitHub Repository** with Actions enabled.
* **MongoDB Atlas** cluster connection string.

---

### Automated Deployment (GitHub Actions CI/CD)

To ease the deployment process across all EC2 nodes, pushing updates to the repository automatically triggers the GitHub Actions pipeline.

**Step 1.** Fork or clone this repository to your GitHub account.

**Step 2.** Set up your GitHub Repository Secrets (`Settings -> Secrets and variables -> Actions`):

```env
EC2_HOST       # Public IP / DNS of EC2 Instance 1
EC2_HOST_2     # Public IP / DNS of EC2 Instance 2
EC2_HOST_3     # Public IP / DNS of EC2 Instance 3
EC2_USERNAME   # SSH Username (e.g. ubuntu)
EC2_SSH_KEY    # Private SSH Key for EC2 access
