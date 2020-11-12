# ELK-Project Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Project Network Diagram](https://github.com/sanchezna86/ELK-Project/blob/main/ELK_Project%20Network%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK Intall Playbook file may be used to install only certain pieces of it, such as Filebeat.

- _[ELK Install Playbook](https://github.com/sanchezna86/ELK-Project/blob/main/Install%20playbook)_


This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
-Load balancers affect the availability aspect of the CIA security triad. The advantage of a jump box is that one person can administer multiple machines from one workstation.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system logs.
- Filebeat monitors log files, collects log events, and sends them to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics and ships them to Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux Ubuntu     |
| Web-1    | Server   | 10.0.0.5   | Linux Ubuntu     |
| Web-2    | Server   | 10.0.0.6   | Linux Ubuntu     |
| ELK      | Server   | 10.1.0.4   | Linux Ubuntu     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Private IP Address

Machines within the network can only be accessed by SSH.
- Only the Jump Box can connect to ELk Server using Private IP address 10.1.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Personal IP Address  |
| Web-1    | No                  | 10.0.0.1             |
| Web-2    | No                  | 10.0.0.1             |
| ELK      | No                  | 10.0.0.1 and Personal|
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- Create VM in Azure and make sure to write down the Public and Private IP addresses. Great inbound rules to be able to connect via ssh to the server using     ssh.Install Docker; download image; etc.
- Using Terminal ssh into your jump box via ssh. Download docker container. Once you download the docker container you need to edit (nano) your host.conf file. Here you need to add the ELk server to the webserver section and add the IP address. Create and install playbook to configure the Elk server and configure your ports.
- Now lauch the container and ssh to the elk server from the container. use sudo docker ps command in the elk server to verify the container is working.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
