Here’s a polished README.md for your playbook that demonstrates the use of block, rescue, and always in Ansible:

# Ansible Playbook: Block, Rescue, and Always Example

This playbook demonstrates how to use **error handling constructs** in Ansible:  
- **Block**: Groups tasks together.  
- **Rescue**: Defines tasks to run if the block fails.  
- **Always**: Defines tasks that run regardless of success or failure.  

---

## 📌 Features
- Attempts to copy a file that does not exist (`/etc/pass`).
- Uses **rescue** to recover by creating the missing file.
- Uses **always** to display a message that runs no matter what.
- Demonstrates robust error handling in automation workflows.

---

## 🛠️ Playbook Details

### Main Playbook (`block-rescue-always.yml`)
```yaml
---
- name: rescue and always example
  hosts: web
  become: yes

  tasks:
    - block:
        - name: try to copy file that does not exist
          copy:
            src: /etc/pass # this file does not exist
            dest: /tmp/app
      rescue:
        - name: create a file with the correct name
          file:
            path: /tmp/app
            state: touch
      always:
        - name: display a message
          debug:
            msg: "This task will always run regardless of the block result"

```

▶️ Execution
Run the playbook with:
ansible-playbook block-rescue-always.yml



🔍 Expected Behavior
- The block task fails because /etc/pass does not exist.
- The rescue section runs, creating /tmp/app as a new file.
- The always section runs, displaying the debug message regardless of success or failure.

🚀 Benefits
- Resilience: Playbooks can recover gracefully from errors.
- Clarity: Separates normal tasks, error handling, and always-run tasks.
- Reliability: Ensures critical steps (like logging or notifications) always execute.

🙌 Author
Mohamed Khattab
DevOps Engineer 
Focused on automation, reproducibility, and sharing technical knowledge through hands-on labs.
