
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
- [Handlers](#handlers)
- [Roles](#roles)
- [Tags](#tags)
- [Running Playbooks](#running-playbooks)


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

# Ansible Playbook

This Ansible playbook contains tasks for various operations, such as installing packages, creating directories, and executing commands.

## Prerequisites

Before running this playbook, make sure you have the following:

- Ansible installed on your system
- SSH access to the target hosts

## Usage

To execute this playbook, run the following command:

```shell
$ ansible-playbook playbook.yml
```

Replace `playbook.yml` with the name of your playbook file.

## Playbook Tasks

### Print message

```yaml
- name: Print message
  debug:
    msg: Hello Ansible World
```

This task prints the message "Hello Ansible World" to the console.

### Print facts

```yaml
- name: Print facts
  debug:
    msg: "IPv4 address: {{ ansible_default_ipv4.address }}"
```

This task prints the IPv4 address of the host.

### Install Apache

```yaml
- name: Ansible apt install Apache
  apt:
    name: apache2
    state: present
```

This task installs the Apache web server using the `apt` module.

### Create directory

```yaml
- name: Create directory
  file:
    path: /home/ubuntu/xyz
    state: directory
```

This task creates a directory at `/home/ubuntu/xyz` using the `file` module.

### Install Maven

```yaml
- name: Ansible apt install Maven
  apt:
    name: maven
    state: present
```

This task installs Maven using the `apt` module.

### Install JDK

```yaml
- name: Ansible apt install JDK
  apt:
    name: openjdk-11-jre
    state: present
```

This task installs the OpenJDK 11 runtime environment using the `apt` module.

### Change directory

```yaml
- name: Change directory
  apt:
    name: openjdk-11-jre
    state: present
```

This task changes the directory. Please note that the task name and module don't seem to match in this case.

### Git clone

```yaml
- name: Git clone
  shell: |
    git clone url
```

This task clones a Git repository using the `shell` module. Replace `url` with the actual repository URL.

## SAMPLE PLAYBOOK TO DEPLOY AN APPLICATION TO TOMCAT

```yaml
---
- name: Build and Deploy Application to Tomcat Server
  hosts: tomcat-server
  become: true

  tasks:
    - name: Check if Tomcat is running
      systemd:
        name: tomcat
        state: started
      register: tomcat_status
      ignore_errors: true

    - name: Stop Tomcat if running
      systemd:
        name: tomcat
        state: stopped
      when: tomcat_status.changed

    - name: Clean Tomcat webapps directory
      file:
        path: /opt/tomcat/webapps
        state: absent

    - name: Copy WAR file to Tomcat webapps directory
      copy:
        src: /path/to/application.war
        dest: /opt/tomcat/webapps/
        mode: 0644

    - name: Start Tomcat
      systemd:
        name: tomcat
        state: started
```

In this playbook:

1. The playbook starts by checking if the Tomcat service is already running on the target server.
2. If Tomcat is running, it stops the service to ensure a clean deployment.
3. The playbook then removes any existing applications in the Tomcat `webapps` directory.
4. The application's WAR file is copied from the local machine to the Tomcat `webapps` directory on the target server.
5. Finally, the playbook starts the Tomcat service again.

Make sure to replace `tomcat-server` with the actual hostname or IP address of your Tomcat server. Also, update `/path/to/application.war` with the path to your application's WAR file on your local machine.

You can execute this playbook using the `ansible-playbook` command:

```shell
$ ansible-playbook deploy.yml
```

Replace `deploy.yml` with the name of your playbook file.
