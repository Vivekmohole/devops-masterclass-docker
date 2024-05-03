# Ansible Variables

## What are Variables in ansible?

- Variables stores information that varies with each host or a group of hosts.
- Ansible variables are dynamic values used within Ansible playbooks and roles to enable customization, flexibility, and reusability of configurations.

## Why are variables useful in Ansible?

- The use of variables simplifies the management of dynamic values throughout an Ansible project and can potentially reduce the number of human errors.
- We have a convenient way to handle variations and differences between different environments and systems with variables.
- We have the flexibility to define them in multiple places with different precedence according to our use case.
- We can also register new variables in our playbooks by using the returned value of a task.

## Variable naming convention

- Variable names can contain only letters, numbers, and underscores and must start with a letter or underscore.
- Some strings are reserved for other purposes and aren't valid variable names, such as [Python Keywords](https://docs.python.org/3/reference/lexical_analysis.html#keywords) or [Playbook Keywords](https://docs.ansible.com/ansible/latest/reference_appendices/playbooks_keywords.html#playbook-keywords).
- The variable names should be short and meaningful, because otherwise, you will have a hard time while debugging the issues.

- **Good Variable Names**
  - ssh_private_key
  - web_server_port
  - max_retries
  - key_pair_path

## Type of Variables in Ansible

Variables in Ansible can come from different sources and can be used in playbooks, roles, inventory files, and even within modules.

- **Playbook variables** – These variables are used to pass values into playbooks and roles and can be defined inline in playbooks or included in external files.
- **Task variables** – These variables are specific to individual tasks within a playbook. These can override other variable types for the scope of the task in which they are defined.
- **Host variables** – Specific to hosts, these variables are defined in the inventory or loaded from external files or scripts and can be used to set attributes that differ between hosts.
- **Group variables** – Similar to host variables but used for a group of hosts and are defined in the inventory or separate files in the group_vars directory.
- **Inventory variables** – These variables are defined in the inventory file itself and can be applied at different levels (host, group, all groups).
- **Fact variables** – Gathered by Ansible from the target machines, facts are a rich set of variables - (including IP addresses, operating system, disk space, etc.) that represent the current state of the system and are automatically discovered by Ansible.
- **Role variables** – Defined within a role, these variables are usually part of the role’s default variables (defaults/main.yaml file) or variables intended to be set by the role user (vars/main.yaml file) and are used to enable reusable and configurable roles.
- **Extra variables** – Passed to Ansible at runtime using the -e or –extra-vars command-line option. They have the highest precedence and can be used to override other variables or to pass data that might change between executions.
- **Magic variables** – Special variables such as hostvars, group_names, groups, inventory_hostname, and ansible_playbook_python, provide information about the execution context and allow access to inventory data programmatically.
- **Environment variables** – Used within Ansible playbooks to access environment variables from the system running the playbook or from remote systems.

### Playbook Variables

- **String variable**

```
---
- name: Variable Demo
  hosts: all
  become: yes
  become_user: root
  vars:
    username: bindesh
  tasks:
  - name: Add the user {{ username }}
    ansible.builtin.user:
      name: "{{ username }}"
      state: present
```

- **List Variable**

```
---
- name: List variables demo
  hosts: all
  become: true
  become_user: root
  vars:
    cidr_blocks:
        production:
          vpc_cidr: "172.31.0.0/16"
        staging:
          vpc_cidr: "10.0.0.0/24"
  tasks:
  - name: Print Production CIDR
    ansible.builtin.debug:
      var:
        cidr_blocks['production']['vpc_cidr']

  - name: Print staging CIDR
    ansible.builtin.debug:
      var:
        cidr_blocks['staging']['vpc_cidr']

```

### Special variables

- Ansible special variables are a set of predefined variables that contain information about the system data, inventory, or execution context inside an Ansible playbook or role.
- The names of these variables are reserved.

### Magic variables

- Magic variables are automatically created by Ansible and cannot be changed by a user.
- These variables will always reflect the internal state of Ansible, so they can be used only as they are.
- For more details, refer https://docs.ansible.com/ansible/latest/reference_appendices/special_variables.html#magic-variables

```
---
- name: Echo playbook
  hosts: localhost
  gather_facts: no
  tasks:
    - name: Echo Inventory_hostname
      ansible.builtin.debug:
        msg:
          - "Hello from Ansible playbook!"
          - "This is running on {{ inventory_hostname }}"

```
