# 🧩 DevOps Mini Project – Flask CI/CD + Kubernetes + Security Scan

## 👨‍💻 Author
**Name:** Aryan Bhoi  
**Tools Used:** Docker, Jenkins, Git, Kubernetes, Trivy  
**Objective:** Demonstrate end-to-end DevOps pipeline, containerization, deployment, and image security scanning.

---

## 🔹 Task 1 – Docker + Jenkins CI/CD Pipeline

### Objective
Implement CI/CD integration for a simple Flask web app using Jenkins and Docker.

### Steps
1. **Flask App Setup**
   Files:
app.py
Dockerfile
Jenkinsfile
requirements.txt
Flask app prints “Hello DevOps” on localhost:5000.

2. **Dockerfile**
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
Build and Run Container
docker build -t hello-devops .
docker run -d -p 5000:5000 hello-devops
Jenkins Pipeline
Stage 1: Build Docker image
Stage 2: Run container
Stage 3: Deploy or test
✅ Result: Jenkins pipeline built and deployed the container successfully.
🔹 Task 2 – Git Branching and Merging Workflow
Objective
Showcase proper Git workflow using feature branches and merges.
Steps
git checkout -b feature/login
# Add login feature
git add .
git commit -m "Add login feature"

git checkout -b feature/signup
# Add signup feature
git add .
git commit -m "Add signup feature"

git checkout dev
git merge feature/login
git merge feature/signup
Verification
git log --oneline --graph --all
✅ Result: Both feature branches successfully merged into dev with clean history.
🔹 Task 3 – Kubernetes Deployment (Mini Infra Challenge)
Objective
Deploy and scale an Nginx container using Kubernetes.
deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
    nodePort: 30007
Commands
kubectl apply -f deployment.yaml
kubectl get pods
kubectl get svc
kubectl scale deployment nginx-deployment --replicas=2
✅ Result:
Nginx deployed successfully on Kubernetes.
Verified scaling (2 running pods).
🔹 Task 4 – Docker Image Security Scan (DevSecOps)
Objective
Scan Docker image for vulnerabilities using Trivy.
Commands
brew install trivy
trivy image hello-devops
Sample Output
hello-devops (alpine 3.18)
Total: 25 (LOW: 8, MEDIUM: 12, HIGH: 4, CRITICAL: 1)
Recommended Fixes
Update base image to the latest version:
FROM python:3.12-slim
Rebuild and rescan regularly.
✅ Result: Identified vulnerabilities and documented security improvements.
📁 Repository Structure
📦 flask-app
 ┣ 📜 app.py
 ┣ 📜 Dockerfile
 ┣ 📜 Jenkinsfile
 ┣ 📜 requirements.txt
 ┣ 📜 deployment.yaml
 ┣ 📜 README.md
🏁 Final Outcome
Task	Description	Status
Task 1	CI/CD with Docker & Jenkins	✅ Completed
Task 2	Git Branching & Merge	✅ Completed
Task 3	K8s Deployment & Scaling	✅ Completed
Task 4	Docker Image Scan (Trivy)	✅ Completed
💬 Summary
This project integrates DevOps concepts including containerization, automation, version control, cloud-native deployment, and security — forming a complete CI/CD + DevSecOps workflow.