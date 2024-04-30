# Setting up the environment for Ansible


## 01. On CentOS

There will be two machines in this setup:

1. <b>AnsibleServer</b>, where we will execute all the playbooks. We are using CentOS 7.x machine in this lab.
2. <b>TargetMachine</b>, to which "AnsibleServer" will send the instructions mentioned via playbook tasks and eventually will be executed here. It could be any linux machine.
3. Make sure there is a connectivity between both the machines over SSH/RDP

<img src="https://github.com/novatecstack/ansible-masterclass/assets/121426292/89409280-97b1-4c22-b2da-e6fe43c52417" data-canonical-src="https://github.com/novatecstack/ansible-masterclass/assets/121426292/89409280-97b1-4c22-b2da-e6fe43c52417" width="600" height="180" />

## Setup Ansible Server on EC2 Instance (Amazon Linux 2)

### Step-01: Provision an EC2 instance with below specifications:

- AMI: Amazon Linux 2 (5.10 Kernel)
- Instance Type: t2.micro
- Key Pair: Create a new key pair
- VPC & Subnet: Default
- Security group: Allow SSH(22) ingress | Outbound allow all
- Storage: 10 GB (root volume)

### Step-02: Install and configure Ansible

- Connect to the EC2 instance that you created in Step#1.
- Now, execute following commands:

```
# Install epel-release packages in AnsibleServer
$ sudo amazon-linux-extras install -y epel

# Install Ansible on CentOS
$ sudo yum install -y ansible

# Check ansible version
$ ansible --version
```

## 02. On Amazon Linux 2 AMI 

```
sudo amazon-linux-extras install epel

# Install Ansible
sudo yum install -y ansible

# ansible --version
```
