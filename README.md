# GitHub Actions CI/CD: Java App Deployment with Docker & AWS EC2

This project demonstrates a complete **CI/CD pipeline** using **GitHub Actions**, **Docker**, and **AWS EC2**.  
Whenever code is pushed to the repository, the workflow automatically builds a Docker image, pushes it to Docker Hub, and deploys it to an AWS EC2 instance.

---

## 🚀 Project Overview

This pipeline performs the following steps:

1. **Build Java Application**  
   - Uses Maven to compile and package the Spring Boot application.

2. **Build Docker Image**  
   - Creates a Docker image of the Java application.

3. **Push to Docker Hub**  
   - Authenticates and pushes the Docker image to your Docker Hub repository.

4. **Deploy to AWS EC2**  
   - Connects to an AWS EC2 instance via SSH and pulls the latest Docker image.
   - Stops the old container (if any), and runs the new container.

The entire process is automated via GitHub Actions workflow.

---

## 📦 Architecture Diagram
                ┌──────────────────────┐
                │      Developer       │
                └──────────┬───────────┘
                           │
                           │ Push Code
                           ▼
                ┌──────────────────────┐
                │   GitHub Repository  │
                └──────────┬───────────┘
                           │
                           │ Triggers Workflow
                           ▼
                ┌──────────────────────────────┐
                │       GitHub Actions         │
                │------------------------------│
                │ 1. Build with Maven          │
                │ 2. Build Docker Image        │
                │ 3. Push to Docker Hub        │
                └──────────┬───────────────────┘
                           │
                           ▼
                ┌──────────────────────┐
                │      Docker Hub      │
                │  (Image Registry)    │
                └──────────┬───────────┘
                           │
                           │ Pull Image
                           ▼
                ┌──────────────────────┐
                │     AWS EC2          │
                │----------------------│
                │ - Pull Docker Image  │
                │ - Stop Old Container │
                │ - Run New Container  │
                └──────────────────────┘

🔁 Flow Summary

Developer → GitHub → GitHub Actions → Docker Hub → AWS EC2 → Application Running




**Description:**  
- GitHub Actions workflow is triggered on push to the `master` branch.  
- The workflow runs on GitHub-hosted Ubuntu runner.  
- After building the image, it is pushed to **Docker Hub**.  
- The EC2 instance pulls the image and runs it using Docker.

---

## 🧪 Getting Started

### 🔹 Prerequisites

Before using this project, you need:

- Docker Hub account
- AWS EC2 instance
- SSH key for EC2 access
- Secrets configured in GitHub repository

---

## 🔧 GitHub Secrets

Add the following repository secrets:

| Secret Name            | Description |
|------------------------|-------------|
| `DOCKERHUB_USERNAME`   | Docker Hub username |
| `DOCKERHUB_TOKEN`      | Docker Hub access token |
| `EC2_HOST`             | AWS EC2 public IP |
| `EC2_USER`             | EC2 SSH username (e.g., ubuntu) |
| `EC2_SSH_KEY`          | SSH private key for EC2 access |

---

## 📈 Workflow Summary

The GitHub Actions workflow (`.github/workflows/cicd.yml`) contains:

- **Checkout Code**
- **Setup Java & Maven**
- **Build with Maven**
- **Docker Login to Docker Hub**
- **Build & Push Docker Image**
- **SSH to EC2 and Deploy Container**

---

## 📌 How to Use

1. Fork this repository.
2. Configure your Docker Hub credentials in GitHub Secrets.
3. Configure your AWS EC2 host details in GitHub Secrets.
4. Push your code to the `master` branch.
5. Go to **Actions** tab in GitHub to monitor the workflow.

After successful execution, the application will be accessible at:


---

## 🛠 Technologies Used

- GitHub Actions (CI/CD)
- Docker
- Docker Hub
- AWS EC2
- Java (Spring Boot)
- Maven

---

## 📂 Folder Structure

├── .github/
│ └── workflows/
│ └── cicd.yml # GitHub Actions workflow
├── src/
│ └── main/
│ └── java/ # Java source code
├── Dockerfile # Docker build file
├── pom.xml # Maven config



---

## 📄 Notes & Tips

- Ensure your EC2 security group allows inbound traffic on port **8080**.
- Restrict SSH access to known IPs for security.
- Tag Docker images appropriately to avoid conflicts.

---

## 🤝 Contributions

Contributions, issues, and feature requests are welcome!

---

## 👍 License

Distributed under the MIT License.

---

# 🟢 End of README



