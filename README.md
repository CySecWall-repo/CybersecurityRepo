# CybersecurityRepo
Intended to showcase Cybersecurity work by ddiaz



## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Secure Private Infrastructure On Public Cloud - Deivis Diaz.zip

https://github.com/CySecWall-repo/CybersecurityRepo/blob/e85120c31cd1f66c308639d97755e66cceb2e55f/Diagrams/Secure%20Private%20Infrastructure%20On%20Public%20Cloud%20-%20Deivis%20Diaz.zip

![image](https://user-images.githubusercontent.com/86539199/123533190-52cbb680-d6e1-11eb-910b-38f4c9ac656d.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - Enter the playbook file._
  https://github.com/CySecWall-repo/CybersecurityRepo/blob/c3c1248687d2e4f9360a26d2f9be023206788168/Ansible/filebeat.-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available,in addition to restricting access to the network.
- What aspect of security do load balancers protect? 
ANSWER:

What is the advantage of a jump box?
ANSWER: Acts as a gateway for managing the environment, which makes the system easier to secure than allowing direct access to resources

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the applications and system logs.

- What does Filebeat watch for?
ANSWER: Changes in applications and system files

- What does Metricbeat record?
ANSWER: Metricbeat records metrics from the operating system and from services running on the server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
|Webserver1| webserver| 10.1.0.5   | Linux            |
|Webserver2| webserver| 10.1.0.6   | Linux            |
| ELKHost  |Monitoring| 10.2.0.4   | Linux            |
|  DVWA    | webserver| 10.1.0.8   | Linux            |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My public IP (hidden) was whitelisted

Machines within the network can only be accessed by the Jump Box.
- Which machine did you allow to access your ELK VM? What was its IP address?
Ansible container in Jump Box with IP 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | My Public Ip (hidden)|
|Webserver1| No                  | 10.1.0.4             |
|Webserver2| No                  | 10.1.0.4             |
| ELKHost  | Yes                 | My Public Ip (hidden)|
|  DVWA    | No                  | 10.1.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
I would says that the main advantage of using Ansible is efficiency as it streamlines the process of deployment

The playbook implements the following tasks:

- Installs teh Docker container
- Downloads image
- Copies files for deployment of the stack
- Sets up published ports
- Sets up systemd booting parameter


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![image](https://user-images.githubusercontent.com/86539199/123532973-d1bfef80-d6df-11eb-92b7-2b4fe61c44a2.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

10.1.0.5  
10.1.0.6  
10.1.0.8  


We have installed the following Beats on these machines:
- FileBeat was succesfully installed on DVWA VM and Webservers

These Beats allow us to collect the following information from each machine:

Filebeat harvest files state data and logs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to destination path
- Update the YAML file to include Instructions
- Run the playbook, and navigate to container to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_

- _Which file is the playbook?
   Ansible-playbook.yml
 Where do you copy it?
 Docker container
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
   Host file needs to be updated - uncommnenting the webservers section or creating a new section and adding the interpreter path

- _Which URL do you navigate to in order to check that the ELK server is running?

   Elk public IP:5601/app/kibana. 

