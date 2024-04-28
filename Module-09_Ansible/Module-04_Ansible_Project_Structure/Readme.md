# Ansible Project Structure - Inventory, Roles, Hosts and Playbooks
A typical ansible project will have below entities:
- <b>Inventory File:</b>
  - The Ansible Inventory File defines all the hosts and groups of hosts that you want to automate with Ansible
  - Also called the Ansible Hosts File 
  - It tells Ansible about the hosts that it can connect to, you can also define custom options per host e.g. different port number or credentials
  - The default Ansible inventory file is located in <b>/etc/ansible/hosts</b>
- Playbooks
- Roles
- Other supporting files
- 
![image](https://github.com/novatecstack/ansible-masterclass/assets/121426292/cc7c1ac4-f6b7-4a34-b8f3-b56246101a9d)

## Securing Ansible with SSH Keys
   In this section, we will try to understand how you can use Public and Private key in Ansible in order to securely perform tasks.
   
