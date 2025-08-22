# 📘 End-to-End Text Summarizer Project using NLP  

📌 Project Description

This project implements an NLP-based Text Summarizer that takes long text passages and generates concise summaries. It is built using Hugging Face Transformers and deployed with a complete MLOps workflow including modular pipelines, configuration management, and cloud deployment via AWS with CI/CD pipelines.
The project is structured into stages (pipelines) for data transformation, model training, and prediction, making it highly scalable, reproducible, and production-ready.

---

## flowchart TD

    A[📂 Raw Data] --> B[🔄 Data Transformation<br>(📝 Tokenization, Padding)]
    
    B --> C[🧠 Model Training<br>(⚙️ Fine-tune Transformer Model)]
    
    C --> D[💾 Save Model Artifacts]
    
    D --> E[⚡ Prediction Pipeline<br>(✂️ Summarization Inference)]
    
    E --> F[🐳 Dockerized App]
    
    F --> G[☁️ AWS Deployment<br>(EC2 + ECR)]
    
    G --> H[🤖 CI/CD with GitHub Actions]

## 🔄 Workflows  

1. Update `config.yaml`
     
2. Update `params.yaml`
   
3. Update entity
   
4. Update the configuration manager in `src/config`
    
5. Update the components
    
6. Update the pipeline
      
7. Update the `main.py`
     
8. Update the `app.py`  

---
## 🛠 Tech Stack

Programming Language: Python

NLP Library: Hugging Face Transformers (AutoTokenizer, pipeline)

Deep Learning: PyTorch / TensorFlow backend (via Transformers)

Configuration Management: YAML (config.yaml, params.yaml)

Logging: Custom logging utilities (logger)

Deployment: AWS EC2, ECR, Docker, GitHub Actions

## 🚀 Key Features

End-to-End Modular Pipelines → Easy to train, transform, and deploy models.

Config-Driven Workflow → Centralized parameters for flexible experimentation.

Prediction API → Real-time summarization via a PredictionPipeline.

MLOps Ready → Integrated with CI/CD pipelines, Docker, AWS for deployment.

Reproducibility → Experiment tracking using configurations and modular design.

# ☁️ AWS CICD Deployment with GitHub Actions  

### 🔹 1. Login to AWS Console  

### 🔹 2. Create IAM User for Deployment  

**With specific access:**  
- **EC2 Access** → Virtual machine hosting environment
  
- **ECR Access** → Elastic Container Registry for storing Docker images  

**Deployment Description:**  
1. Build Docker image of the source code
    
2. Push Docker image to ECR
   
3. Launch EC2 instance
   
4. Pull the image from ECR into EC2
   
5. Run the Docker image on EC2  

**IAM Policies Required:**  
- `AmazonEC2ContainerRegistryFullAccess`
  
- `AmazonEC2FullAccess`  

---

### 🔹 3. Create ECR Repository  

- Example URI:


---

### 🔹 4. Create EC2 Machine (Ubuntu)  

Launch an Ubuntu EC2 instance to host the application.  

---

### 🔹 5. Install Docker in EC2  

```bash
# Optional

sudo apt-get update -y

sudo apt-get upgrade -y

# Required
curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

sudo usermod -aG docker ubuntu

newgrp docker

###🔹 6. Configure EC2 as Self-Hosted Runner

Navigate to:

GitHub Repository > Settings > Actions > Runners > New self-hosted runner

Select OS (Ubuntu) → Run setup commands provided by GitHub.

###🔹 7. Setup GitHub Secrets

Add the following secrets in GitHub → Settings → Secrets and variables → Actions:

AWS_ACCESS_KEY_ID = <your-access-key>

AWS_SECRET_ACCESS_KEY = <your-secret-key>

AWS_REGION = us-east-1

AWS_ECR_LOGIN_URI = 566373416292.dkr.ecr.ap-south-1.amazonaws.com

ECR_REPOSITORY_NAME = simple-app  

