
Flask + NGINX + Docker Compose Project 🛠

This project demonstrates a real-world production setup where a Flask app runs behind an NGINX reverse proxy using Docker Compose.

Project Structure:
------------------
flask-nginx-compose/
├── app/
│   ├── main.py
│   └── requirements.txt
├── nginx/
│   └── default.conf
├── Dockerfile
├── docker-compose.yml
└── .github/workflows/ci.yml

Features:
---------
✅ Flask API with two endpoints
✅ NGINX as a reverse proxy
✅ Docker Compose for container orchestration
✅ GitHub Actions CI for build validation

How It Works:
-------------
- NGINX listens on port 80 and forwards traffic to the Flask app running on port 5000.
- Flask container is built from a custom Dockerfile.
- Docker Compose manages both containers on a shared network.

How to Run:
-----------
1. Build and run with Docker Compose:
   docker-compose up --build

2. Visit in browser:
   http://localhost

3. View logs:
   docker-compose logs flask
   docker-compose logs nginx

GitHub Actions CI:
------------------
- Automatically builds Docker images when code is pushed to main.
- Ensures the Dockerfile and docker-compose.yml work as expected.

CI Workflow (in .github/workflows/ci.yml):
------------------------------------------
- Uses ubuntu-latest
- Builds the Flask Docker image
- Runs docker-compose config to validate syntax

Sample Workflow:
----------------
name: CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2

      - name: Docker Compose Config Test
        run: docker-compose -f docker-compose.yml config

      - name: Build Flask app
        run: docker-compose build --no-cache

This setup gives you a powerful starting point for full-stack app deployments using Docker and CI/CD practices.

Author:
-------
Simon Coker
Created by @kornerstonecoker – DevOps Journey 💻🚀
