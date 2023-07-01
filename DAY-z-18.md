
# DAY-18 | Ansible Tutorial

This tutorial will guide you through the basics of using Ansible for automation and configuration management.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Inventory](#inventory)
- [Playbooks](#playbooks)
- [Variables](#variables)
- [Modules](#modules)
- [Templates](#templates)
- [Handlers](#handlers)
- [Roles](#roles)
- [Tags](#tags)
- [Running Playbooks](#running-playbooks)
- [Conclusion](#conclusion)

## Introduction

Ansible is an open-source automation tool that simplifies the management and configuration of servers, applications, and network devices. It uses a declarative language to define the desired state of the system and handles the necessary steps to achieve that state.

This tutorial assumes you have a basic understanding of Linux systems and command-line usage.

## Prerequisites

Before getting started, make sure you have the following:

- A Linux-based system (local machine or remote servers)
- Python 3 installed on your system
- SSH access to the target servers

## Installation

To install Ansible on your system, follow these steps:

1. Open a terminal or command prompt.
2. Install Ansible using the package manager for your operating system. For example, on Ubuntu, run:

   ```shell
   $ sudo apt update
   $ sudo apt install ansible
   ```

   On other Linux distributions, refer to the appropriate package manager.

3. Verify the installation by running the following command:

   ```shell
   $ ansible --version
   ```

   You should see the version number and other information about your Ansible installation.

## Inventory

The inventory file in Ansible contains the list of hosts or network devices that you want to manage. It is usually located at `/etc/ansible/hosts` by default.

To define hosts in the inventory file, open it in a text editor and add the IP addresses or domain names of your servers. You can organize hosts into groups and assign variables to them.

Example inventory file:

```ini
[web]
webserver1 ansible_host=192.168.0.10 ansible_user=admin ansible_ssh_private_key_file=~/.ssh/id_rsa

[database]
dbserver1 ansible_host=192.168.0.20 ansible_user=admin ansible_ssh_private_key_file=~/.ssh/id_rsa
```

## Playbooks

Ansible playbooks are YAML files that describe the desired state of your system. Playbooks consist of plays, which are sets of tasks executed on a specific group of hosts.

A simple playbook example:

```yaml
---
- name: Install and start Apache
  hosts: web
  become: true

  tasks:
    - name: Install Apache package
      apt:
        name: apache2
        state: present

    - name: Start Apache service
      service:
        name: apache2
        state: started
        enabled: true
```

Save the above YAML code to a file named `webserver.yml`.

## Variables

Ansible allows you to define variables and use them in your playbooks. Variables can be defined at various levels, such as inventory, playbooks, or roles.

Example playbook with variables:

```yaml
---
- name: Configure Nginx
  hosts: web
  become: true

  vars:
    nginx_port: 80
    nginx_user: www-data

  tasks:
    - name: Install Nginx package
      apt:
        name: nginx
        state: present

    - name:

 Configure Nginx
      template:
        src: nginx.conf.j2
        dest: /etc/nginx/nginx.conf
      notify: restart nginx
```

In this example, the `nginx_port` and `nginx_user` variables are defined in the playbook and used in the tasks.

## Modules

Ansible provides a wide range of modules to perform various tasks on managed hosts. Modules are self-contained scripts that Ansible uses to perform actions such as installing packages, managing services, copying files, and more.

You can find a list of available modules in the Ansible documentation: [Ansible Modules](https://docs.ansible.com/ansible/latest/modules/modules_by_category.html)

Example playbook using modules:

```yaml
---
- name: Manage users
  hosts: web
  become: true

  tasks:
    - name: Create user
      user:
        name: john
        state: present
        groups: sudo
        shell: /bin/bash

    - name: Copy SSH key
      authorized_key:
        user: john
        key: "{{ lookup('file', '/path/to/john.pub') }}"
```

This playbook creates a user named "john" and copies the SSH public key to their authorized keys file.

## Templates

Ansible allows you to use Jinja2 templates to generate configuration files dynamically. Templates can contain variables, loops, conditionals, and other constructs.

Example template file `nginx.conf.j2`:

```nginx
user {{ nginx_user }};
worker_processes auto;
pid /run/nginx.pid;

events {
  worker_connections 1024;
}

http {
  server {
    listen {{ nginx_port }};
    server_name localhost;
    root /var/www/html;

    location / {
      index index.html;
    }
  }
}
```

This template generates an Nginx configuration file with the variables `nginx_user` and `nginx_port` filled in.

## Handlers

Handlers in Ansible are tasks that are triggered by notifications from other tasks. They are typically used to restart services or perform other actions when a change is made.

Example playbook with handlers:

```yaml
---
- name: Configure Nginx
  hosts: web
  become: true

  tasks:
    - name: Install Nginx package
      apt:
        name: nginx
        state: present
      notify: restart nginx

  handlers:
    - name: restart nginx
      service:
        name: nginx
        state: restarted
```

In this example, the `restart nginx` handler is triggered by the notification from the `Install Nginx package` task.

## Roles

Roles in Ansible provide a way to organize and reuse playbooks and related files. A role is a directory structure that contains tasks, templates, variables, and other components.

To create a role, use the following command:

```shell
$ ansible-galaxy init myrole
```

This will create a directory named `myrole` with the necessary files and directories.

## Tags

Ansible allows you to assign tags to tasks in your playbooks. Tags are useful when you want to run specific tasks or groups of tasks selectively.

Example playbook with tags:

```yaml
---
- name: Manage web servers
  hosts: web
  become: true

  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
      tags: [install, web]

    - name: Configure Apache
      template:
        src: apache.conf.j2
        dest: /etc/apache2/apache.conf
      tags: [config, web]
```

In this example, you can run specific tags using the `--tags` option when executing the playbook.

## Running Playbooks

To

 run a playbook, use the following command:

```shell
$ ansible-playbook webserver.yml
```

Replace `webserver.yml` with the name of your playbook.

## Conclusion

Congratulations! You've completed this Ansible tutorial. You should now have a good understanding of Ansible's key concepts and how to use it for automation and configuration management.

For more information, refer to the official Ansible documentation: [Ansible Documentation](https://docs.ansible.com/ansible/latest/index.html)

Happy automating!
