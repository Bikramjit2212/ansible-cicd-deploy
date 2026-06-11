# 🚀 Ansible CI/CD Deployment with GitHub Actions

A lightweight DevOps project demonstrating how to automate remote server configuration using **Ansible** and **GitHub Actions**.

This repository provisions a Linux server by automatically installing and configuring Nginx whenever changes are pushed to the main branch.

---

## 📌 Project Overview

This project integrates:

* GitHub Actions for CI/CD automation
* Ansible for configuration management
* SSH authentication using GitHub Secrets
* Automated Nginx installation on remote Linux servers

The deployment workflow enables infrastructure changes to be applied automatically through a GitOps-style approach.

---

## 🏗️ Architecture

```
Developer
    ↓
Git Push
    ↓
GitHub Actions
    ↓
Install Ansible
    ↓
Configure SSH
    ↓
Update Inventory
    ↓
Execute Playbook
    ↓
Target Linux Server
    ↓
Install & Configure Nginx
```

---

## 📂 Project Structure

```
ansible-cicd-deploy-main/
├── .github/
│   └── workflows/
│       └── deploy.yml
├── inventory.yml
└── playbook.yml
```

---

## ⚙️ Technologies Used

* GitHub Actions
* Ansible
* YAML
* SSH
* Ubuntu/Linux
* Nginx

---

## 📜 Inventory Configuration

The inventory file defines the target host dynamically.

```yaml
all:
  hosts:
    target_host:
      ansible_host: "{{ host_placeholder }}"
      ansible_user: "{{ user_placeholder }}"
      ansible_ssh_private_key_file: ~/.ssh/id_rsa
```

The placeholders are replaced during pipeline execution using GitHub Secrets.

---

## 📜 Ansible Playbook

The playbook performs the following tasks:

### Install Nginx

```yaml
apt:
  name: nginx
  state: present
  update_cache: yes
```

### Start and Enable Nginx

```yaml
service:
  name: nginx
  state: started
  enabled: yes
```

---

## 🔄 GitHub Actions Workflow

The CI/CD pipeline is triggered automatically when code is pushed to the main branch.

Workflow responsibilities include:

* Checking out source code
* Installing Ansible
* Configuring SSH authentication
* Injecting inventory variables
* Executing the Ansible playbook

---

## 🔐 Required GitHub Secrets

Configure the following repository secrets:

| Secret Name         | Description                                |
| ------------------- | ------------------------------------------ |
| ANSIBLE_PRIVATE_KEY | SSH private key for target server access   |
| HOST                | Public IP or hostname of the target server |
| USER                | SSH username used by Ansible               |

---

## ▶️ Deployment Process

1. Push changes to the `main` branch.
2. GitHub Actions automatically starts the workflow.
3. SSH authentication is configured.
4. Inventory placeholders are replaced.
5. Ansible connects to the remote server.
6. Nginx is installed if not already present.
7. The Nginx service is started and enabled.

---

## 📈 Key DevOps Concepts Demonstrated

* Infrastructure Automation
* Configuration Management
* Continuous Deployment
* Secure Secret Management
* SSH-based Remote Provisioning
* GitOps Principles
* Idempotent Deployments

---

## 🚀 Future Improvements

* Support multiple environments (Dev, QA, Production)
* Introduce Ansible Roles
* Add Nginx validation checks
* Integrate Slack notifications
* Implement Ansible Vault for encrypted secrets
* Add rollback strategies

---

# 👨‍💻 Author

**Bikramjit Roy**

DevOps & Cloud Engineering Enthusiast passionate about automation, CI/CD, cloud-native practices, and building reliable software delivery pipelines.

GitHub:
https://github.com/Bikramjit2212

---

## ⭐ If you found this project useful, consider giving it a star.
