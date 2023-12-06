# Project Name

## Overview

This project automates the setup of a multi-server environment for a Java web application using Ansible and Vagrant. It includes configurations for various backend services such as MySQL, Memcached, RabbitMQ, Nginx, and Tomcat. The automation scripts provided aim to streamline the deployment process and ensure a consistent environment across different servers.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Ansible Playbook](#ansible-playbook)
- [Vagrant Configuration](#vagrant-configuration)
- [Automation Scripts](#automation-scripts)
  - [backend.sh](#backendsh)
  - [memcache.sh](#memcachesh)
  - [mysql.sh](#mysqlsh)
  - [nginx.sh](#nginxsh)
  - [rabbitmq.sh](#rabbitmqsh)
  - [tomcat.sh](#tomcatsh)
  - [tomcat_ubuntu.sh](#tomcat_ubuntush)
- [Usage](#usage)
- [Notes](#notes)

## Prerequisites

Ensure the following software is installed on your local machine:

- Ansible
- Vagrant
- VirtualBox (or another supported provider)

## Ansible Playbook

The Ansible playbook (`ansible/playbook.yml`) automates common tool setup on all servers defined in the `appsrvgrp` group.

### Playbook Tasks

- Install JDK on CentOS 6/7 or Ubuntu 14/15/16/18.
- Download Tomcat binaries from a specified URL.
- Add Tomcat group and user.
- Extract and synchronize Tomcat files.
- Set up Tomcat service files based on the OS version.
- Change ownership of Tomcat directory.
- Reload Tomcat service configuration.
- Start and enable Tomcat 8 service.

## Vagrant Configuration

The Vagrant configuration (`Vagrantfile`) defines virtual machines for each component of the infrastructure.

### VM Definitions

- **db01:** MySQL database server
- **mc01:** Memcached server
- **rmq01:** RabbitMQ server
- **app01:** Tomcat application server
- **web01:** Nginx web server

Each VM is provisioned with a shell script that sets up the respective backend services.

## Automation Scripts

### backend.sh

The `backend.sh` script automates the setup of backend services on a VM. It includes steps for installing Memcached, RabbitMQ, MySQL, and configuring them. Additionally, it restores the MySQL dump file for your application.

### memcache.sh

The `memcache.sh` script focuses on installing and configuring Memcached on a VM.

### mysql.sh

The `mysql.sh` script installs MariaDB on a VM, secures the installation, sets passwords, and imports the MySQL dump file.

### nginx.sh

The `nginx.sh` script sets up Nginx, a web server, on a VM.

### rabbitmq.sh

The `rabbitmq.sh` script installs and configures RabbitMQ, a message broker, on a VM.

### tomcat.sh

The `tomcat.sh` script installs and configures Apache Tomcat on a VM.

### tomcat_ubuntu.sh

The `tomcat_ubuntu.sh` script is a version or configuration of the Tomcat setup tailored for Ubuntu-based systems.

## Usage

1. Clone the repository.
2. Navigate to the project directory.
3. Run `vagrant up` to create and provision the virtual machines.

## Notes

- Ensure that the necessary dependencies, such as JDK 11, Maven 3, and MySQL 8, are installed on the target environment.
- Follow the instructions in the provided Ansible playbook and Vagrant configuration to set up the infrastructure.
- Customize the configurations and scripts based on your specific project requirements.
- Refer to the documentation for Ansible, Vagrant, and the backend services for more detailed information.

Feel free to reach out for any questions or assistance!
