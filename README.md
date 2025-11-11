#  Mediplus 3-Tier Application Deployment (AWS + Docker + HAProxy + CI/CD)

###  Project Overview
**Mediplus** is a three-tier healthcare web application built to demonstrate modern DevOps and cloud deployment workflows.  
This project shows how to containerize, automate, and deploy an application using **AWS**, **Docker**, **HAProxy**, and **GitHub Actions**.

Even though my previous EC2 instance and ECR repository have been deleted, this documentation outlines how I set up the full CI/CD pipeline and how I plan to rebuild it for future updates.

---

##  Architecture Overview

![Mediplus 3-Tier Architecture](img/architecture-diagram.png)

**Flow:**
User → HAProxy (SSL + Load Balancer)
↳ Frontend (React/Nginx)
↳ Backend (FastAPI)
↳ MongoDB

yaml
Copy code

**Core Components**
| Layer | Technology | Purpose |
|-------|-------------|----------|
| Frontend | React + Nginx | Delivers the web interface |
| Backend | FastAPI (Python) | Handles API logic & communication |
| Database | MongoDB | Stores application data |
| Proxy | HAProxy + Let’s Encrypt SSL | Provides secure load balancing |
| Hosting | AWS EC2 (to be recreated) | Runs containerized services |
| Registry | AWS ECR (to be recreated) | Stores Docker images |
| CI/CD | GitHub Actions | Automates build, test, and deployment |

---

##  CI/CD Workflow Summary

1. **Code Commit:** Push to the `main` branch triggers GitHub Actions.  
2. **Build Stage:** GitHub builds Docker images for frontend and backend.  
3. **Push Stage:** Images are pushed to **AWS ECR**.  
4. **Deploy Stage:** EC2 instance (via SSH) pulls the latest images and restarts containers.  
5. **Result:** Updated version of the Mediplus application runs live.

*Currently, the CI/CD workflow remains active for testing, but the AWS resources (ECR/EC2) will be re-provisioned soon.*

---

## Lessons Learned
- Dockerizing multi-tier applications improves portability and scalability.  
- CI/CD automation using GitHub Actions saves manual deployment time.  
- HAProxy simplifies SSL termination and traffic distribution.  
- AWS ECR and EC2 integration builds a cost-efficient deployment pipeline.

---

## Project Structure
mediplus/
│
├── backend/
│ ├── Dockerfile
│ ├── app/
│ └── requirements.txt
│
├── frontend/
│ ├── Dockerfile
│ └── build/
│
├── docker-compose.yml
├── haproxy.cfg
└── .github/workflows/cicd.yml

yaml
Copy code

---

##  Next Steps
- Recreate AWS **ECR** and **EC2** resources to enable full pipeline deployment again.  
- Add **Terraform** for Infrastructure-as-Code provisioning.  
- Integrate **CloudFront + Route 53** for DNS and HTTPS.  
- Add **Prometheus + Grafana** for monitoring and visualization.

---

## Author
**Rita**  
Cloud & DevOps Engineer | AWS | Docker | Terraform | CI/CD | Kubernetes  
 [LinkedIn Profile](https://www.linkedin.com/in/rita-nnenna)  


---


> 💬 *This repository is actively being rebuilt as part of my ongoing DevOps practice. The documentation remains for transparency and learning purposes.*
