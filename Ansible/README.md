# Ansible Files
# Files utilized to Deploy ELK Container used for monitoring webservers running Metricbeat and Filebeat

- Ansible.cfg: Ansible configuration file
- Pentest.yml: Webserver configuration file
- Install-elk.yml: Utilizes ansible to install and configure ELK stack
- filebeat-config.yml: configuration file for installing Filebeat
- filebeat-playbook.yml: ansible playbook for install and configuration process for Filebeat on webservers
- metricbeat-config.yml: configuration file for installing Metricbeat
- metricbeat-playbook.yml: ansible playbook for install and configuration process for Metricbeat on webservers
- remove-elk.yml: removes elk install in the event that the program needs to be re-installed

