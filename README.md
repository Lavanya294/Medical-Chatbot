# How to run?

### STEPS:
Clone the repository

```bash
Project repo: https://github.com/
```

### STEP 01 - Create a conda environment after opening the repository

```bash
conda create -n medibot python=3.10 -y
```

```bash
conda activate medibot
```

### STEP 02- install the requirements

```bash
pip install -r requirements.txt
```
### Environment Setup and Local Deployment Instructions

#### 1. Create a `.env` file in the root directory and add your credentials:

```env
PINECONE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
GOOGLE_API_KEY = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

#### 2. Store embeddings to Pinecone:

```bash
python store_index.py
```

#### 3. Run the Flask app:

```bash
python app.py
```

#### 4. Open up `http://localhost:8080` in your browser.

---

### Tech Stack Used

* **Python**
* **LangChain**
* **Flask**
* **Gemini API (Google Generative AI)**
* **Pinecone**
* **AWS CICD Deployment with GitHub Actions**

---

### AWS Deployment Guide

#### Step 1: Login to AWS Console

#### Step 2: Create an IAM User with the following access:

* **AmazonEC2FullAccess**
* **AmazonEC2ContainerRegistryFullAccess**

#### Step 3: Create ECR Repository

* Example URI: `315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot`

#### Step 4: Build and Push Docker Image

```bash
docker build -t medibot .
docker tag medibot:latest 315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot
docker push 315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot
```

#### Step 5: Launch EC2 (Ubuntu)

#### Step 6: SSH into EC2 and Install Docker

```bash
sudo apt-get update -y
sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker
```

#### Step 7: Configure EC2 as GitHub Self-Hosted Runner

* Go to GitHub repo > Settings > Actions > Runners > New self-hosted runner
* Select OS (Ubuntu) and run the setup commands provided

#### Step 8: Set GitHub Repository Secrets:

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`
* `AWS_DEFAULT_REGION`
* `ECR_REPO`
* `PINECONE_API_KEY`
* `GOOGLE_API_KEY`
