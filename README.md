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

![Docker ps](https://github.com/sanchezna86/ELK-Project/blob/main/Images/Screen%20Shot%202020-11-11%20at%2011.07.34%20PM.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 nd 10.0.0.6

We have installed the following Beats on these machines:
-Filebeat and Metricbeat are loaded on the VM.

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files, collects log events, and sends them to Elasticsearch or Logstash for indexing.
- Metricbeat takes the metrics and statistics and ships them to Elasticsearch or Logstash

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-config.yml file to /etc/ansible/roles.
- Update the configuration file to include the Elk Server's IP address.
- Run the playbook, and navigate to ELK server to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filesbeat-playbook.yml Where do you copy it? /etc/ansible/hosts
- _Which file do you update to make Ansible run the playbook on a specific machine? filebeat-config.yml How do I specify which machine to install the ELK server on versus which to install Filebeat on? by adding the IP address for the ELK server to the webserver section.
- _Which URL do you navigate to in order to check that the ELK server is running? Public_IP_Address:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
cd /etc/ssh
ssh username@IPaddress -yes
sudo docker container list -a
sudo docker start container (container name)
sudo docker attach container (container name)
cd /etc/ansible/
ansible-playbook elk.yml 
ansible-playbook filebeat-playbook.yml
ansible-playbook metricbeat-playbook.yml
cd /etc/ansible/roles
nano filebeat-playbook.yml (to configure file)
nano metricbeat-playbook.yml 
open a new web browser (Elk-Server PublicIP:5601) This will bring up the Kibana Web Portal
