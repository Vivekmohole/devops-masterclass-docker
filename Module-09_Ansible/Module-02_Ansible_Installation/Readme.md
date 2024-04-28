# Setting up the environment for Ansible Playbooks execution (CentOS)

There will be two machines in this setup:

1. <b>AnsibleServer</b>, where we will execute all the playbooks. We are using CentOS 7.x machine in this lab.
2. <b>TargetMachine</b>, to which "AnsibleServer" will send the instructions mentioned via playbook tasks and eventually will be executed here. It could be any linux machine.
3. Make sure there is a connectivity between both the machines over SSH/RDP

<img src="https://github.com/novatecstack/ansible-masterclass/assets/121426292/89409280-97b1-4c22-b2da-e6fe43c52417" data-canonical-src="https://github.com/novatecstack/ansible-masterclass/assets/121426292/89409280-97b1-4c22-b2da-e6fe43c52417" width="600" height="180" />

```
# Install epel-release packages in AnsibleServer
$ sudo yum install epel-release

# Install Ansible on CentOS
$ sudo yum install -y ansible

# Check ansible version
$ ansible --version
```
