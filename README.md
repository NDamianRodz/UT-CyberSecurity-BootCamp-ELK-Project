# UT-CyberSecurity-BootCamp-ELK-Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Network Diagram](https://github.com/NDamianRodz/UT-CyberSecurity-BootCamp-ELK-Project/blob/main/ELK%20Network%20Diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  [filebeat-playbook.yml](https://github.com/NDamianRodz/UT-CyberSecurity-BootCamp-ELK-Project/blob/main/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting attacks to the network.
By adding a load balancer we ensures that the traffic is divided between the available machines, and no machine is overloaded. This helps ensure availability of the system for the users. Meanwhile by placing a Jump Box server between the user and the virual machines in the network we can improve the security of the system by allowing us better control of who can access the network. This is also a more efficent method to increase security since we mostly have to harden the Jump Box, and not every machine in the network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Log and system traffic. Two applications that are used for these purposeses are Filebeat and Metricbeat. Filebeat monitors are records system logs, such as logon attempts, while Metricbeat records metric data from the system, such as CPU usage.

The configuration details of each machine may be found below.


| Name            | Function       | Public IP Address | Private IP Address | Operating System     |
|-----------------|----------------|-------------------|--------------------|----------------------|
| RedTeam Jumpbox | Gateway        | 20.127.107.35     | 10.0.0.4           | Linux (ubuntu 18.04) |
| ELK Server      | Monitoring     | 40.113.204.5      | 10.1.0.4           | Linux (ubuntu 18.04) |
| RedTeam Web-1   | Virtual Server | 20.120.113.23     | 10.0.0.5           | Linux (ubuntu 18.04) |
| RedTeam Web-2   | Virtual Server | 20.120.113.23     | 10.0.0.6           | Linux (ubuntu 18.04) |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from IP addresses that have been white listed in the Network Security Group.

Machines within the network can only be accessed by Jumpbox Provisioners.
The ELK server is only accesible via SSH from the Jumpbox, and via webaccess from white listed ip addresses, using port 5601.

A summary of the access policies in place can be found in the table below.

| Name            | Publicly Accessible | Allowed IP Address        |
|-----------------|---------------------|---------------------------|
| RedTeam Jumpbox | No                  | White Listed IP Only      |
| ELK Server      | Through Jumpbox     | 10.1.0.4 and White Listed |
| RedTeam Web-1   | No                  | 10.0.0.5                  |
| RedTeam Web-2   | No                  | 10.0.0.6                  |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for faster deployment of servers, is more repeatable, less prone to human error, and more cost effective.

The playbook implements the following tasks:
- Configure Webservers
- Install ELK Server
- Install Filebeat
- Install Metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://github.com/NDamianRodz/UT-CyberSecurity-BootCamp-ELK-Project/blob/main/ELK%20PS%20Output%20Screenshot.png)

### Target Machines & Beats

This ELK server is configured to monitor the following machines:

- Web-1 10.0.0.5 
- Web-2 10.0.0.6 

We have installed the following Beats on these machines:

- Filebeat 
- Metricbeat 

These Beats allow us to collect the following information from each machine:

- Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch) 
- Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics) 

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

