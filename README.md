# Cybersecurity
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Virtual_Network](/Diagrams/Virtual_Network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK_Stack | Ansible Container | 10.1.0.5 | Linux(Ubuntu 18.04)|
| Web-1 | DVWA Container | 10.0.0.5 | Linux(Ubuntu 18.04) |
| Web-2 | DVWA Container | 10.0.0.6 | Linux(Ubuntu 18.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load balencer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
73.95.217.210

Machines within the network can only be accessed by the jump box (10.0.0.4).

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No | 73.95.217.210 |
| Load Balencer | No | 73.95.217.210 |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the room for
expansion is much greater with a higher efficency in the long run.

The playbook implements the following tasks:
- Installs docker.io and checks to make sure it is present on the system
- Installs python3-pip and checks to make sure it is present on the system
- Installs the Docker module and checks to make sure it is present on the system
- Increases virtual memory so the ELK installation has room to run
- Enables the Docker service on bootup

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Running the Docker playbook](/Diagrams/running_docker.yml.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web_1 10.0.0.5
- Web_2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Logs in each Virtual Machine, how many visitors there are and where they log in from, any error codes they recieve, how much data is being used,
- and how much traffic there is at each hour of the day.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible.
- Update the hosts file to include *virtual machine ip* ansible_python_interpreter=/usr/bin/python3 under the webservers section
- Run the playbook, and navigate to http://*your web ip*:5601/ to check that the installation worked as expected.

