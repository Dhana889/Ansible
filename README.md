ANSIBLE:

An Ansible is an open-source IT automation tool that automates manual IT processes such as provisioning, configuration management, application deployment, orchestration, and more. It is used by system administrators, developers, and architects to install software, automate daily tasks, provision infrastructure, improve security and compliance, patch systems, and share automation across the entire organization. 

Ansible is a cross-platform tool for resource provisioning automation that DevOps professionals use for continuous delivery of software code by taking advantage of an "infrastructure as code" approach.

Ansible is Agentless: Ansible is an agentless automation platform that automates deployment, configuration management, and orchestration of multiple applications in order. 

It reads information about the machines it manages from the inventory file, which can be created by the user. 

Ansible is popular due to its simplicity, efficiency, and use of YAML. 

It uses an agentless approach, unlike competing offerings such as Chef, Puppet, Salt, and PowerShell DSC, which install agents.

Master machine = Control node
Slave machine = Managed node

Modules: Ansible modules are units of code that can control system resources or execute system commands. Ansible provides a module library that can be executed directly on remote hosts or through playbooks. Custom modules can also be written. 

Modules are the main building blocks of Ansible playbooks and interact with local machines, APIs, or remote systems to perform specific tasks like changing a database password or spinning up a cloud instance. Each module provides a defined interface, accepts arguments, and returns information to Ansible by printing a JSON string to stdout before exiting.

Ansible YAML concepts:

Adhoc - ad hoc commands are great for tasks you repeat rarely. Ad-hoc tasks can be used to reboot servers, copy files, manage packages and users, and much more. They achieve a form of idempotence by checking the current state before they begin and doing nothing unless the current state is different from the specified final state.

Modules - Ansible provides a module library that you can execute directly on remote hosts or through playbooks
Playbook - A playbook is a list of tasks that are executed automatically on a specified inventory or group of hosts. 
Loop - Allows to install multiple packages using a single yaml file
Variables - Ansible uses variables to manage differences between systems.
Vault - Ansible Vault is a feature of Ansible that allows you to encrypt sensitive data, such as passwords or keys, in your Ansible projects.
Roles - Ansible Roles provide a well-defined framework and structure for setting your tasks, variables, handlers, metadata, templates, and other files. They enable us to reuse and share our Ansible code efficiently.

Commands:

$ ansible all -i inventoryfile.txt -m ping
$ ansible all -i inventoryfile.txt -a “uname -a”
$ ansible all -i inventoryfile.txt -a “uptime”

States of programs:

Install == present
Uninstall == absent
Start == started
Stop == stopped
Restart == restarted

# To install httpd
$ ansible all -i inventoryfile.txt -m yum -a “name=httpd state=present” -b

m > module
a > action
b > run as root-user 

# To start httpd
$ ansible all -i inventoryfile.txt -m systemctl -a “name=httpd state=started” -b

# To copy index.html to managed nodes
$ ansible all -i inventoryfile.txt -m copy -a “src=/home/ec2-user/index.html dest=/var/www/html/index.html” -b

Playbook status: Ok, Changed and Failed

Ansible is Idempotent, because Ansible won't perform a task repeatedly. For example, we write a playbook to create a directory but if the directory is already created then it won't recreate it, it would skip that part.

In simplest terms, idempotency means you can be sure of a consistent state in your environment.
