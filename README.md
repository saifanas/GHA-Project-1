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

Add your architecture diagram below:

