Here’s a professional README.md draft for your Ansible playbook that uses blocks to handle package installation differently depending on the operating system:

# Ansible Playbook: Block Example (Nginx & Git)

This playbook demonstrates how to use **blocks** in Ansible to group related tasks together and apply conditional logic based on the operating system distribution. It installs and configures **Nginx** and **Git** on web servers, with separate blocks for **CentOS/RHEL** and **Ubuntu/Debian** systems.

---

## 📌 Features
- Uses **blocks** to organize tasks logically.
- Installs **Nginx** and ensures the service is running.
- Installs **Git** for version control.
- Applies OS-specific package managers (`yum` for CentOS, `apt` for Ubuntu).
- Demonstrates conditional execution with `ansible_facts`.

---

## 🛠️ Playbook Details

### Main Playbook (`block-example.yml`)
```yaml
---
- name: Block Example
  hosts: web
  become: yes

  tasks:
    - block:
        - name: Install nginx on Web Servers
          yum:
            name: nginx
            state: present
        - name: Start and Enable nginx Service
          service:
            name: nginx
            state: started
            enabled: yes
        - name: Install git on Web Servers
          yum:
            name: git
            state: present

    - block:
        - name: Install nginx on Web Servers
          apt:
            name: nginx
            state: present
        - name: Start and Enable nginx Service
          service:
            name: nginx
            state: started
            enabled: yes
        - name: Install git on Web Servers
          apt:
            name: git
            state: present

      when: ansible_facts['distribution'] == "Ubuntu"

```

▶️ Execution
Run the playbook with:
ansible-playbook block-example.yml



🚀 Benefits
- Modularity: Groups related tasks into blocks for clarity.
- Flexibility: Handles multiple operating systems in one playbook.
- Maintainability: Easier to extend with additional OS-specific logic.
- Reliability: Ensures services are installed and running correctly.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
