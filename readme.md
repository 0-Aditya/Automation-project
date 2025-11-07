# Automation Project

This project demonstrates a **DevOps automation setup** using **Python, Docker, Kubernetes, Jenkins, and Ansible**. It includes infrastructure setup, deployment automation, and a Flask application running inside a container orchestrated by Kubernetes.

---

## Features

- **Python Flask App** – Simple REST API for demonstration.
- **Dockerized Application** – Containerized with Docker.
- **Kubernetes Deployment** – Runs the Flask app in a Minikube cluster.
- **Ansible Automation** – Automates installation and configuration of Docker, kubectl, and other dependencies.
- **Jenkins Integration** – Optional CI/CD setup (can be extended).

---

## Prerequisites

- [WSL2 Ubuntu](https://learn.microsoft.com/en-us/windows/wsl/install) (for Windows users)
- Python 3.x
- [Docker](https://www.docker.com/get-started)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [Ansible](https://docs.ansible.com/)
- Git

---

## Project Structure

main-project/
│
├── ansible/
│ └── playbook.yml # Ansible playbook for environment setup
├── k8s/
│ ├── deployment.yaml # Kubernetes deployment manifest
│ └── service.yaml # Kubernetes service manifest
├── app.py # Flask application
├── requirements.txt # Python dependencies
├── hosts # Ansible inventory file
├── .gitignore # Git ignore file
└── README.md

yaml
Copy code

---

## Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/automation-project.git
cd automation-project/main-project
2. Create Python virtual environment
bash
Copy code
python3 -m venv .venv
source .venv/bin/activate    # For WSL/Linux
pip install -r requirements.txt
3. Run Ansible Playbook (setup environment)
bash
Copy code
ansible-playbook -i hosts ansible/playbook.yml
This will install Docker, kubectl, and other dependencies required to run the project.

4. Build Docker image
bash
Copy code
docker build -t 0-aditya/main-project:local .
5. Load image into Minikube
bash
Copy code
minikube image load 0-aditya/main-project:local
6. Deploy on Kubernetes
bash
Copy code
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
7. Access the Flask application
bash
Copy code
minikube service devops-project-svc
Opens the Flask app in your browser.

Notes
Make sure Minikube is running before applying Kubernetes manifests:

bash
Copy code
minikube start
The Ansible playbook assumes local deployment (127.0.0.1) and is configured for WSL/Ubuntu environment.

License
This project is for learning and demonstration purposes.

Author
Aditya
🔥🖤
