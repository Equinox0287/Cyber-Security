## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Stack Diagram for week 13](https://github.com/Equinox0287/Cyber-Security/blob/main/Diagrams/Draw-iO_13.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - [YML playbooks](https://github.com/Equinox0287/Cyber-Security/tree/main/Ansible)

This document contains the following details:
- Description of the Topologie
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers are a tool to protect the availability aspect of Internet based security by keeping any server in the model from being overloaded with web-traffic. The advantage of a Jump Box is that it acts as a secure computer that any admin must connect to prior to launching any relevant task or use as a primary point of origin to connect to untrusted environments or servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and system logs.
- Filebeat is a lightweight shipping program for forwarding and centralizing log data. Filebeat monitors log files or specified locations, collects log events and forwards them into Logstash or Elasticsearch to be indexed.
- Metricbeat takes data as well as collected statistics and metrics captured from the system and services running on the server and ships them to the output specified by the user, such as Logstash or Elasticsearch. 

The configuration details of each machine may be found below.

| Name                 | Function     | IP Address | Operating System |
|----------------------|--------------|------------|------------------|
| Jump-Box-Provisioner | Gateway      | 10.0.0.1   | Linux            |
| Web-1                |DVWA Container| 10.1.0.5   | Linux            |
| Web-2                |DVWA Container| 10.1.0.6   | Linux            |
| Web-3                |DVWA Container| 10.1.0.7   | Linux            |
| ELK-1                | ELK Server   | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.20.218.78

Machines within the network can only be accessed by the Ansible container running on the Jump Box.
- Jump-Box-Provisioner, 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | 70.20.218.78         |
| Web-1                | No                  | 10.1.0.4             |
| Web-2                | No                  | 10.1.0.4             |
| Web-3                | No                  | 10.1.0.4             |
| ELK-1                | No                  | 10.1.0.4             |
| RedTeam-LB           | Yes                 | 70.20.218.78         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Rapid deployment of a single or multiple VMs while minimizing the potential for human error to have an impact on the process.

The playbook implements the following tasks:
- Configure ELK VM with Docker
- Change the memory on the ELK VM
- Install docker.io
- Install pip3
- Install docker module
- Download and launch a docker elk container
- Start docker service

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
