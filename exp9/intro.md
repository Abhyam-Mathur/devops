# Experiment 9: Ansible

## Aim
Study Ansible as an agentless automation tool for configuration management and application deployment.

## Objectives
- Understand why manual server administration does not scale
- Learn the role of control nodes, managed nodes, inventory, and playbooks
- Run a basic Ansible ping test
- Build a simple SSH-enabled Docker image for automation practice

## Theory
Ansible is an open-source automation tool used for configuration management, application deployment, and orchestration.

It uses an agentless model:
- Control node: machine with Ansible installed
- Managed nodes: target servers
- Inventory: list of hosts
- Playbooks: YAML files describing tasks

## Key Concepts
| Component | Description |
|---|---|
| Control Node | Machine that runs Ansible |
| Managed Nodes | Remote machines being configured |
| Inventory | Host list used by Ansible |
| Playbook | YAML automation script |
| Task | One action in a playbook |
| Module | Built-in function such as `apt`, `yum`, or `service` |

## Install Ansible
```bash
pip install ansible
ansible --version
```

On Ubuntu:
```bash
sudo apt update -y
sudo apt install ansible -y
ansible --version
```

## Basic Test
```bash
ansible localhost -m ping
```

Expected output:
```bash
localhost | SUCCESS => {
  "changed": false,
  "ping": "pong"
}
```

## SSH Key and Docker Demo
Generate a key pair and copy it into the working directory:
```bash
ssh-keygen -t rsa -b 4096
cp ~/.ssh/id_rsa .
cp ~/.ssh/id_rsa.pub .
```

Example Dockerfile for an SSH-enabled Ubuntu container:
```Dockerfile
FROM ubuntu

RUN apt update -y && \
    apt install -y python3 python3-pip openssh-server && \
    mkdir -p /var/run/sshd

RUN mkdir -p /run/sshd && \
    echo 'root:password' | chpasswd && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh
COPY id_rsa /root/.ssh/id_rsa
COPY id_rsa.pub /root/.ssh/authorized_keys
RUN chmod 600 /root/.ssh/id_rsa && chmod 644 /root/.ssh/authorized_keys

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
```

## Sample Inventory
```ini
[servers]
172.17.0.3
172.17.0.4
172.17.0.5
172.17.0.6

[servers:vars]
ansible_user=root
ansible_ssh_private_key_file=./id_rsa
ansible_python_interpreter=/usr/bin/python3
```

## Sample Playbook
```yaml
---
- name: Configure servers
  hosts: servers
  become: yes
  tasks:
    - name: Update apt package index
      apt:
        update_cache: yes

    - name: Install packages
      apt:
        name:
          - vim
          - htop
          - wget
        state: present

    - name: Create test file
      copy:
        dest: /root/ansible_test.txt
        content: "Configured by Ansible"
```

Run it with:
```bash
ansible-playbook -i inventory.ini playbook.yml
```

## Result
Ansible removes repetitive SSH-based administration by turning server setup into a reusable, idempotent playbook workflow.
