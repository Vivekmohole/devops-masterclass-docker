# Ansible Key Concepts

In this module, we will try to understand the some of the important building blocks of Ansible based automation. Here is the Ansible Playbook structure:
![image](https://github.com/novatecstack/ansible-masterclass/assets/121426292/59325439-61f5-4da3-bfc1-f5ef139097f8)

Now, lets explore these components in detail:

## 1. Ansible Inventory
- The Ansible inventory file defines the hosts and groups of hosts upon which commands, modules, and tasks in a playbook operate. 
- The file can be in one of many formats depending on your Ansible environment and plugins: <b>include INI and YAML</b>. 
- Ansible establishes connectivity with the hosts using SSH (for linux) and PowerShell remoting (for Windows) machines which makes Ansible agentless
- The default location for the inventory file is /etc/ansible/hosts. 
- You can also create project-specific inventory files in alternate locations

Example: Sample inventory file with hosts details:
```
webserver ansible_host=webserver.novatec.com ansible_connection=winrm ansible_user=root
dbserver  ansible_host=dbserver.novatec.com ansible_connection=ssh ansible_user=root
webserver ansible_host=server1.novatec.com ansible_connection=ssh ansible_user=root
```
## 2. Ansible Playbook
- An Ansible Playbook is a set of automation tasks—which are complex IT actions executed with limited or no human involvement.
- Are written in YAML
- Ansible Playbooks are executed on a set, group, or classification of hosts, which together make up an <b>Ansible inventory</b>.
- It helps IT staff program applications, services, server nodes, or other devices without the manual overhead of creating everything manually from scratch
- 
## 3. Ansible Modules

## 4. Ansible Roles

## 5. Ansible Playbook Execution
