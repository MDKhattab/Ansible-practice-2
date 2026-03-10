Here’s a clear and professional README.md for your playbook that demonstrates using ignore_errors when installing a package that may not exist:

# Ansible Playbook: Ignore Errors Example

This playbook demonstrates how to use the **`ignore_errors`** directive in Ansible. It attempts to install a package (`hhhhhh`) on web servers, but if the package is not found or the task fails, the playbook continues executing without stopping.

---

## 📌 Features
- Installs a package using the `yum` module.
- Uses `ignore_errors: yes` to allow the playbook to continue even if the task fails.
- Useful for testing, experimentation, or handling optional packages.

---

## 🛠️ Playbook Details

### Main Playbook (`ignore-errors.yml`)
```yaml
---
- name: Install anything on Web Servers
  hosts: web
  become: yes

  tasks:
    - name: Install hhhhhh on Web Servers
      yum:
        name: hhhhhh
        state: present
      ignore_errors: yes


```
▶️ Execution
Run the playbook with:
ansible-playbook ignore-errors.yml



🔍 Expected Behavior
- Ansible will attempt to install the package hhhhhh.
- If the package does not exist, the task will fail but the playbook will not stop.
- The play recap will show the task as failed, but subsequent tasks (if any) will still run.

🚀 Use Cases
- Testing error handling in playbooks.
- Skipping non-critical tasks that may fail.
- Ensuring automation continues even when optional components are unavailable.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
