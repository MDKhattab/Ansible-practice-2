Here’s a professional README.md for your playbook that checks the status of the Nginx service and restarts it if it’s not running:

# Ansible Playbook: Check and Restart Nginx Service

This playbook demonstrates how to use **registered variables** and conditional logic in Ansible to ensure that the **Nginx** service is running on web servers. If the service is not active, Ansible will automatically restart it.

---

## 📌 Features
- Runs `systemctl status nginx` to check service status.
- Registers the command result in a variable (`nginx_status`).
- Uses a conditional (`when`) to restart Nginx only if it is not running.
- Ensures service reliability across multiple hosts.

---

## 🛠️ Playbook Details

### Main Playbook (`check-nginx.yml`)
```yaml
---
- name: check nginx service
  hosts: web
  become: yes

  tasks:
    - name: check nginx service
      command: systemctl status nginx
      register: nginx_status

    - name: restart nginx service if not running
      service:
        name: nginx
        state: restarted
      when: nginx_status.rc != 0

```

▶️ Execution
Run the playbook with:
ansible-playbook check-nginx.yml



🔍 Expected Behavior
- If Nginx is running, the playbook will skip the restart task.
- If Nginx is not running, the restart task will execute and bring the service back online.
- The play recap will show whether the restart was triggered.

🚀 Benefits
- Reliability: Ensures Nginx is always running.
- Efficiency: Restarts only when necessary.
- Automation: Eliminates manual service checks and restarts.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
