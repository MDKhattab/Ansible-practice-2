
# 🛠️ Ansible Automation Labs Portfolio

This repository contains a collection of Ansible playbooks that demonstrate key automation concepts, error handling, and service management. Each project is designed to be modular, reproducible, and educational — ideal for building a strong DevOps foundation.

---

## 📁 Project Index

| Project | Description |
|---------|-------------|
| `install-packages` | Installs packages like **Nginx**, **Git**, and **Apache** with proper service management. |
| `include-tasks` | Demonstrates modular playbooks using `include_tasks` for Nginx and Git installation. |
| `block-example` | Uses **blocks** to handle OS-specific logic (CentOS with `yum`, Ubuntu with `apt`). |
| `ignore-errors` | Shows how to continue execution even if a task fails using `ignore_errors`. |
| `apache-with-handler` | Installs Apache, deploys `index.html`, and restarts the service via **handlers**. |
| `check-nginx` | Checks Nginx service status and restarts it if not running using `register` + `when`. |
| `block-rescue-always` | Demonstrates **block**, **rescue**, and **always** for error handling and recovery. |

---

## 📌 Key Concepts Covered
- ✅ Package installation (`yum`, `apt`)
- 🔄 Service management (`service` module, handlers)
- 🧩 Modular playbooks (`include_tasks`)
- 🧠 Conditional logic (`when`, `ansible_facts`)
- 🚨 Error handling (`ignore_errors`, `block`, `rescue`, `always`)
- 🔍 Verification tasks (`command`, `register`, `debug`)

---

## ▶️ How to Run

Each playbook can be executed with:

```bash
ansible-playbook <playbook-name>.yml


Examples:
ansible-playbook install-apache.yml
ansible-playbook block-example.yml
ansible-playbook check-nginx.yml
```




🚀 Learning Goals
- Build reproducible automation workflows.
- Understand Ansible modules and task structure.
- Practice safe deployment strategies.
- Gain confidence in Infrastructure as Code.
- Showcase professional documentation and portfolio-ready labs.

📷 Visual Summary
This portfolio demonstrates a progression from basic installs → service management → error handling → modular playbooks → advanced blocks and handlers.

![Ansible Diagram](Ansible%20projects%20por.png)

🙌 Author
Mohamed Khattab
DevOps Engineer 
Passionate about automation, reproducibility, and sharing technical knowledge through hands-on labs.
