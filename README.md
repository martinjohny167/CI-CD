# 🚀 Jenkins CI/CD Pipeline with GitHub Integration

## 📌 Overview  
This repository demonstrates how to integrate **Jenkins** with **GitHub** for automated CI/CD. The pipeline is configured to trigger builds automatically whenever changes are detected in the GitHub repository.  

## ✅ Prerequisites  
Ensure you have the following:  
- 🏗 **Jenkins** installed ([Download](https://www.jenkins.io/download/))  
- 🖥 **GitHub repository** with a Jenkinsfile  
- 🔑 **GitHub Personal Access Token (PAT)** for authentication  
- 🌐 **Ngrok** (or a public Jenkins server) for webhooks  
- 📩 **Email notification setup** in Jenkins  

## 🔧 Pipeline Stages  
1️⃣ **Checkout** - Clone the GitHub repository  
2️⃣ **Build** - Simulate the build process  
3️⃣ **Test** - Run a simple test  
4️⃣ **Deploy (Optional)** - Deploy the application  
5️⃣ **Notification** - Send an email notification on success/failure  

## 📝 Jenkinsfile  
```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') { steps { checkout scm } }
        stage('Build') { steps { echo '🔨 Building...' } }
        stage('Test') { steps { echo '✅ Running tests...' } }
        stage('Deploy') { steps { echo '🚀 Deploying...' } }
    }
    post { failure { echo '❌ Pipeline failed!' } }
}
```


### ** Webhook-Based Approach (Recommended)**  
- In GitHub, go to **Settings > Webhooks > Add Webhook**  
- Set the **Payload URL** to `<JENKINS_URL>/github-webhook/`  
- Select **Content type** as `application/json`  
- Choose **Just the push event** and save  
- Ensure **Jenkins GitHub Plugin** is installed and configured  

## 📸 Screenshots
### **1️⃣ Jenkins Pipeline Job Configuration**
![Image](https://github.com/user-attachments/assets/d51e997b-1150-4026-b82f-61b68e96c161)

### **2️⃣ GitHub Webhook Setup**
 ![Image](https://github.com/user-attachments/assets/1f766bf0-8015-4811-96c4-afe68446e07c)

### **3️⃣ Jenkins Build Log**
 ![Image](https://github.com/user-attachments/assets/90479169-8dcb-4f03-877b-ece7188c7d8a)

## 🔍 Testing & Verification  
1. Make a small change in the repository (e.g., update `README.md`)  
2. Confirm Jenkins detects the change and starts a build  
3. Verify each pipeline stage executes successfully  
4. Check the Jenkins build log and email notifications  

## ⚠️ Troubleshooting  
- **Webhook not triggering?** ➝ Ensure Jenkins is accessible from the internet using Ngrok or a public server  
- **Polling not detecting changes?** ➝ Check GitHub credentials and pipeline configurations  
- **Jenkins build fails?** ➝ Review logs and confirm correct pipeline syntax  



