# Project: Scalable Web Solutions: PostgreSQL, Node.js, React with Ansible, Docker, and Terraform Integration

## Description

The Web-Page Application aims to deploy a web page written with Node.js and React frameworks on AWS Cloud Infrastructure using Ansible. The infrastructure setup is managed from a control node utilizing Ansible. This setup includes one control node and three EC2 instances as worker nodes. These EC2 instances are launched via the AWS console. The web page has three main components: PostgreSQL, Node.js, and React. Each component runs in a Docker container on dedicated EC2 instances. PostgreSQL serves as the database, Node.js manages the backend, and React handles the frontend.

## Problem Statement

Registration data is stored in a PostgreSQL database located on one of the EC2 instances. The Node.js framework handles the backend and connects to the PostgreSQL database on port 5432, serving on port 5000. The React framework manages the frontend, connecting to the Node.js server on port 5000, and broadcasts the web page on port 3000.

### Project Requirements
The web application should be accessible via a web browser on port 3000.
EC2 instances and their security groups must be created on the AWS console.
Security groups must be configured with the necessary permission rules.
The deployment process must be managed from the control node via SSH.
PostgreSQL, Node.js, and React components must run in Docker containers.
Separate EC2 instances should be launched for each PostgreSQL, Node.js, and React Docker container.
Three playbooks should be written:
A playbook to manage each worker instance separately.
A playbook to manage all processes in one playbook without roles.
A playbook to manage all processes in one playbook using roles.
Architecture Configuration
All processes are controlled from the control node.
Dynamic inventory is used for the inventory file.
The Ansible configuration file is placed on the control node.
Docker is installed on all worker nodes using Ansible.
Worker Node Configurations

### PostgreSQL Worker Node:
PostgreSQL files (Dockerfile and init.sql) are sent from the control node using Ansible.
A Docker image is created for the PostgreSQL container, with the init.sql file placed in the necessary folder.
The PostgreSQL container is created, and its password is set as an environmental variable, protected with Ansible Vault.
The instance's security group must accept traffic from the PostgreSQL port from the Node.js EC2 and port 22 from anywhere.
A Docker volume is created to persist database data.

### Node.js Worker Node:
Ensure the .env file in the server folder is configured based on PostgreSQL environment variables.
The Node.js server folder is sent from the control node using Ansible.
A Docker image is built for the Node.js container.
The Node.js container is created and published on port 5000.
The instance's security group must accept traffic from port 5000 and port 22 from anywhere.

### React Worker Node:
Ensure the .env file in the client folder is configured based on Node.js environment variables.
The React client folder is sent from the control node using Ansible.
A Docker image is created for the React container.
The React container is created and published on port 3000.
The instance's security group must accept traffic from ports 3000 and 80 from anywhere.

## Project Skeleton 

```text
Scalable Web Solutions: PostgreSQL, Node.js, React with Ansible, Docker, and Terraform Integration (folder)
|
|----Readme.md               
|----solutions_files (folder)  
|       1.ansible-project (folder)
|       2.playbooks (folder) 
|       3.roles (folder)
|----terraform-files (folder)  
```

## Expected Outcome

### Project Coverage;

At the end of the project, the following topics will be covered:

- Writing Ansible playbooks without roles.

- Writing Ansible playbooks with roles.

- Bash scripting.

- Creating and attaching AWS Security groups to EC2 instances.

- Launching and configuring EC2 instances.

- Writing Dockerfiles for PostgreSQL, Node.js, and React images.

- Creating Docker images for PostgreSQL, Node.js, and React containers using Ansible playbooks.

- Launching Docker containers using created images with Ansible playbooks.


### Learning Outcomes;

By the end of the project, students will be able to:

- Write Ansible playbooks in various ways, both with and without roles.

- Apply web programming skills using Node.js and React frameworks.

- Write Dockerfiles for different environments.

- Create containers using React, Node.js, and PostgreSQL Docker images.

- Configure connections to the PostgreSQL database.

- Connect the backend server to the database.

- Configure the Node.js framework.

- Connect the frontend server to the backend server.

- Configure the React framework for development and production environments.

- Demonstrate bash scripting skills using Ansible playbooks to set up a web page on an EC2 instance.

## Resources

- [Ansible Documentation Framework](https://docs.ansible.com/ansible/2.5/user_guide/index.html)

- [AWS CLI Command Reference](https://docs.aws.amazon.com/cli/latest/index.html)