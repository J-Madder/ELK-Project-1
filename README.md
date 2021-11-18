# ELK-Project-1
A project that sets up a cloud monitoring system by configuring an ELK stack server.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/J-Madder/ELK-Project-1/blob/main/Diagrams/Network_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  [filebeat-playbook.yml](https://github.com/J-Madder/ELK-Project-1/blob/main/Ansible/filebeat-playbook.yml)
  
  [filebeat-config.yml.txt](https://github.com/J-Madder/ELK-Project-1/blob/main/Linux/filebeat-config.yml.txt)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? 
  - It prevents strain on the servers which optimizes productivity and maximizes uptime.
  - It can also protect the system from DDOS attacks by shifting traffic.
  
- What is the advantage of a jump box?
  - It can allow the user to access a point where it is secure enough to launch administrative tasks or as an origin point to connect to other servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Logs and system Traffic.
- What does Filebeat watch for?
  - Filebeat watches the log files and location the user specifies, it collects these log events and sends them to Elasticsearch or Logstash.
  
- What does Metricbeat record?
  - Metricbeat records metrics and statistics and ships them to a specified output like Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1     |    Server      |   10.0.0.5         |       Linux           |
| Web-2     |       Server   |       10.0.0.6     |          Linux        |
| Elk-Server     |     Elk Server     |    10.1.0.4        |         Linux         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  - 98.47.88.196

Machines within the network can only be accessed by the Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address?
  - Jump-Box-Provisioner (10.0.0.4)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes              | 98.47.88.196    |
|    Web-1      |       No              |          10.0.0.4            |
|    Web-2      |       No              |          10.0.0.4            |
|     Elk-Server     |         No            |         10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  - The main advantage of Ansible would be YAML Playbooks, the automation helps with the Infrastructure as Code.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
  - Install docker.io
  - Install Python-pip
  - Install docker container
  - Install virtual memory
  - Download and launch docker

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.0.0.5)
- Web-2 (10.0.0.6)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect log events, it does this by monitoring log files or locations that are specified.
- Metricbeat collects metrics from the operating system and from services running on the server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/files/.
- Update the configuration file to include the ELK private IP.
- Run the playbook, and navigate to http://20.98.202.43:5601 to check that the installation worked as expected.

Which file is the playbook? Where do you copy it?
- filebeat-playbook.yml is the playbook and you copy it to /etc/ansible/roles/

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- Configure the /etc/ansible/hosts file to add the webservers and elk IP addresses.

Which URL do you navigate to in order to check that the ELK server is running?
-http://20.98.202.43:5601/app/kibana

