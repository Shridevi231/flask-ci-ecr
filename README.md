# CI/CD Pipeline with GitHub Actions, Docker & AWS ECR  
**Automated Testing → Docker Build → Push to AWS ECR**

This repository demonstrates a simple CI/CD pipeline that runs tests, builds a Docker image, and pushes the image to **AWS Elastic Container Registry (ECR)** using **GitHub Actions**.

---



## Project Summary

- GitHub Actions runs `pytest` on every push to `main`.
- If tests pass, Actions builds a Docker image and pushes it to AWS ECR.
- Images are tagged with the commit SHA for traceability.
- This project focuses on CI and image publishing (no automatic deployment to EC2/ECS in this repo).

---

## Files & Structure
flask-ci-ecr/
├─ app.py
├─ requirements.txt
├─ Dockerfile
├─ tests/
│ └─ test_app.py
└─ .github/
└─ workflows/
└─ ci.yml


---

## How to run locally 

1. Create virtualenv & install:
```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
2.Run tests:
```bash
PYTHONPATH=. pytest -q
```
3.Build Docker image:
```bash
docker build -t flask-demo:latest .
```

4.Run container:
```bash
docker run -d -p 5000:5000 --name flask-demo flask-demo:latest
curl http://localhost:5000
```


---
## GitHub Actions pipeline (Overview)

- The GitHub Actions CI workflow does the following:

- Checkout code

- Install Python & dependencies

- Run pytest

- AWS authentication using GitHub Secrets

- Build Docker image

- Tag using commit SHA

- Push to AWS ECR

---






