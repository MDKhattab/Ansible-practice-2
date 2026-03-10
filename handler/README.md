Here’s a professional README.md for your Apache playbook that installs, configures, and manages the service with handlers:

# Ansible Playbook: Install and Configure Apache (httpd)

This playbook demonstrates how to install and configure the **Apache HTTP Server (httpd)** on web servers using Ansible. It also shows how to use **handlers** to restart services when configuration files change.

---

## 📌 Features
- Installs the Apache `httpd` package.
- Starts and enables the Apache service.
- Deploys a custom `index.html` file with proper permissions.
- Uses a **handler** to restart Apache automatically when the file changes.

---

## 🛠️ Playbook Details

### Main Playbook (`install-apache.yml`)
```yaml
---
- name: Install Apache on Web Servers
  hosts: web
  become: yes

  tasks:
    - name: Install Apache httpd
      yum:
        name: httpd
        state: present

    - name: Start and Enable Apache Service
      service:
        name: httpd
        state: started
        enabled: yes

    - name: Create index.html with Hostname
      copy:
        src: index.html
        dest: /var/www/html/index.html
        mode: "0644"
      notify: Restart Apache web service

  handlers:
    - name: Restart Apache web service
      service:
        name: httpd
        state: restarted

```

▶️ Execution
Run the playbook with:
ansible-playbook install-apache.yml



🔍 Expected Behavior
- Apache (httpd) will be installed if not already present.
- The service will be started and enabled at boot.
- A custom index.html file will be copied to /var/www/html/.
- If the file changes, the handler will restart Apache automatically.

🚀 Benefits
- Automation: No manual installation or configuration needed.
- Reliability: Ensures Apache is always running and enabled.
- Maintainability: Handlers restart services only when necessary.
- Scalability: Can be applied to multiple servers in the web group.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
