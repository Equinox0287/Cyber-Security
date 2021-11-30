## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Stack Diagram for week 13](https://github.com/Equinox0287/Cyber-Security/blob/main/Diagrams/Draw-iO_13F.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - [YML playbooks](https://github.com/Equinox0287/Cyber-Security/tree/main/Ansible)

This document contains the following details:
- Description of the Topology
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

Machines within the network can only be accessed by the Ansible container running on the Jump Box via SSH protocol on port 22.
- Jump-Box-Provisioner, 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes                 | Public IP            |
| Web-1                | No                  | 10.1.0.4             |
| Web-2                | No                  | 10.1.0.4             |
| Web-3                | No                  | 10.1.0.4             |
| ELK-1                | No                  | 10.1.0.4             |
| RedTeam-LB           | Yes                 | Public IP            |

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

![Docker ps output](https://github.com/Equinox0287/Cyber-Security/blob/main/Images/ELK_Screenshot_part-4_Step-9.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5
- 10.1.0.6
- 10.1.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the admin specified locations or log files, collects log events, and forwards them to Logstash or Elasticsearch.
- Metricbeat takes its collected metrics and Statistics and ships this data to ELK. Metricbeat assists by monitoring servers by collecting metrics from the system and services running on the server, such as: Apache, MySQL, or Zookeeper.

Kibana
In the last 7 days, 224 unique visitors were located in India.
In the last 24 hours, 13 visitors from China were using Mac OSX.
In the last 2 days, 5.74% of visitors received 404 errors, and 2.73% received 503 errors.
In the last 7 days, China produced the majority of the traffic on the website.

Of the traffic that's coming from that country, noon had the highest amount of activity.

Over the last 7 days,these file types were downloaded:
gz=archive file
css=cascading style sheets
zip=archive files
deb=debian management file
rpm=redhat package management

1 visitor succeeded (response code 200) in downloading a 16,837 byte RedHat Package Management file on November 29th at 9:07pm from India

The source IP address of this activity was 81.32.253.92 on Windows 7, at geo-coordinates "lat": 47.25996056, "lon": -95.92809778. The user accessed https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-6.3.2-i686.rpm
From http://nytimes.com/success/lodewijk-van-den-berg

In my opinion, the user was downloading A metricbeat red hat package. On the surface, this file itself does not seem to be malicious, however collecting log data from an untrusted location in a foreign country from an American site seems questionable. This is a strange place to get files for metricbeat, seems outside of compliance guidlines.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Playbook file to Ansible.
- Update the hosts file to include the webservers IP addresses and ELK server IP address to the proper resource groups.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

- Install-elk.yml copied to /etc/ansible directory to run.
- Edit Hosts file to identify the correct machine to run playbook on by specifying the IP addresses for their appropriate groups.
- http://20.110.249.70:5601/app/kibana

Bonus

- Edit hosts file: nano hosts
- within hosts file, under [webservers], add: [webserver-IP] ansible_python_interpreter=usr/bin/python3
- within hosts file, under [elk], add:[ELK server-IP] ansible_python_interpreter=usr/bin/python3
- Save updated hosts file (ctrl-x, y, ensure correct filename, enter)
- verify you are in correct install-elk.yml file location (cd /etc/ansible)
- (nano install-elk.yml)
- Verify install-elk.yml file is correctly syncronized with repository
- Save updated yml file (ctrl-x, y, ensure correct filename, enter)
- Run command: ansible-playbook install-elk.yml
- Modify filebeat-config.yml and metricbeat-config.yml files to incorporate ELK stack ((nano filebeat-config.yml)(nano metricbeat-config.yml))
- Save updated yml files (ctrl-x, y, ensure correct filename, enter)
- Create playbooks for both ((nano filebeat-playbook.yml)(nano metricbeat-playbook.yml))
- Verify both playbook.yml files are configured correctly and syncronized with repository
- Save updated yml files (ctrl-x, y, ensure correct filename, enter)
- Run both playbooks ((ansible-playbook filebeat-playbook.yml)(ansible-playbook metricbeat-playbook.yml))
- Verify ELK is receiving data from both
- connect to Kibana (http://20.110.249.70:5601/app/kibana)
- click link (Add log data)
- click link (System logs)
- Navigate to bottom of page and click (Check data). Verify 'data successfully received from this module' is the result.
- Navigate to metrics tab and click (Docker Metrics). 
- Navigate to bottom of page and click (Check data). Verify 'data successfully received from this module' is the result.
