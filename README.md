## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


![alt text](https://github.com/reynoldsan3/Elk-Stack-Project/blob/main/diagrams/Project%20Diagram.drawio.png "Diagram")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and config file may be used to install only certain pieces of it, such as Filebeat.

[Ansible ELK Installation and VM Configuration](ansible/install-elk2.yml)  
[Ansible Hosts](ansible/DVWA/hosts)  
[Ansible Configuration](ansible/DVWA/ansible.cfg)  
[Filebeat Configuration](ansible/Filebeat/filebeat-config.yml)  
[Filebeat Playbook](ansible/Filebeat/filebeat-playbook.yml)  
[Metricbeat Configuration](ansible/Metricbeat/metricbeat-config.yml)  
[Metricbeat Playbook](ansible/Metricbeat/metricbeat-playbook.yml)  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
* What aspect of security do load balancers protect?
  * Answer: Availability, Web Security and Web Traffic

 * What is the advantage of a jump box?
   * Answer: Security, Access Control

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
* What does Filebeat watch for?
  * Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
* What does Metricbeat record?
  * Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name               | Function       | IP Address  | Operating System |
|--------------------|----------------|-------------|------------------|
| JumpBoxProvisioner | Gateway        | 10.0.0.5    | Linux            |
| Web 1              | Web Server     | 10.0.0.6    | Linux            |
| Web 2              | Web Server     | 10.0.0.8    | Linux            |
| Web 3              | Web Server     | 10.0.0.9    | Linux            |
| Elk VM             | Elk Server     | 10.1.0.4    | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  * Workstation Public IP- my personal IP

Machines within the network can only be accessed by the Docker Container that is running on the Jumpbox Provisioner.
- _Which machine did you allow to access your ELK VM? What was its IP address?_
  * JumpBoxProvisionser IP: 10.0.0.5 via Port 22
  * Workstation Public IP via TCP 5601 
  * Only the Jumpbox Provisioner is allowed to access the ELK VM via SSH connection. The IP of the Jumpbox, per the above table is 10.0.0.5. Only my personal IP address can access the ELK server/Kibana page via port 5601.

A summary of the access policies in place can be found in the table below.

| Name               | Publicly Accessible | Allowed IP Addresses         |
|--------------------|---------------------|------------------------------|
| JumpBoxProvisioner | Yes                 | My Personal IP               |
| Web 1              | No                  | 10.0.0.5                     |
| Web 2              | No                  | 10.0.0.5                     |
| Web 3              | No                  | 10.0.0.5                     |
| Elk VM             | Yes/No              | My Personal IP:5601/10.0.0.5 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible lets you quickly and easily deploy apps. You won't need to write custom code to automate your systems; you list the tasks required to be done by writing a playbook, and Ansible will figure out how to get your systems to the state you want them to be in. In other words, it frees up time and increases efficiency.

The playbook implements the following tasks:
* Installs docker.io to the ELK machine (VM)
* Installs pip3 (python3) to the ELK machine
* Installs the Docker python module
* Increase the virtual memory of the ELK machine
* Download and launch the Docker ELK container, configuring/publishing the ports for elasticsearch, logstash, and kibana

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  | IP Addresses |
|-------|--------------|
| Web 1 | 10.0.0.6     |
| Web 2 | 10.0.0.8     |
| Web 3 | 10.0.0.9     |
| ELK   | 10.1.0.4     |

We have installed the following Beats on these machines:
* Filebeat
* Metricbeat

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
