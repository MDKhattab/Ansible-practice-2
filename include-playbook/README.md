Here’s a complete and professional README.md for your modular playbook that installs Nginx and Git on web servers, verifies them, and shows their versions:

# Ansible Playbook: Install Nginx and Git on Web Servers

This repository contains an Ansible playbook that demonstrates how to use **task inclusion** to keep automation modular and organized. The main playbook includes separate task files for installing and verifying **Nginx** and **Git**.

## 📌 Features
- Modular design using `include_tasks`.
- Installs and configures **Nginx** web server.
- Installs **Git** for version control.
- Verifies installation by checking versions.
- Runs on all hosts in the `web` group.

---

## 🛠️ Playbook Details

### Main Playbook (`site.yml`)
```yaml
---
- name: Install Nginx and Git on Web Servers
  hosts: web
  become: yes

  tasks:
    - include_tasks: install-nginx.yml
    - include_tasks: install-git.yml


install-nginx.yml
- name: Install Nginx on Web Servers
  yum:
    name: nginx
    state: present

- name: Start and Enable nginx Service
  service:
    name: nginx
    state: started
    enabled: yes

- name: Get nginx version
  command: nginx -v
  register: nginx_version

- name: Show nginx version
  ansible.builtin.debug:
    var: nginx_version.stdout


install-git.yml
- name: Install Git on Web Servers
  yum:
    name: git
    state: present

- name: Verify git installation
  command: git --version
  register: git_version

- name: Show git version
  ansible.builtin.debug:
    var: git_version.stdout



▶️ Execution
Run the main playbook with:
ansible-playbook site.yml

```
🚀 Benefits
- Modularity: Each component (Nginx, Git) is managed in its own file.
- Reusability: Task files can be reused in other playbooks.
- Clarity: Easier to maintain and extend as projects grow.
- Verification: Ensures both Nginx and Git are installed and working.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
