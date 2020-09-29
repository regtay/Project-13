# Project-13
# Reggie Taylor
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/diagram_filename.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  -Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting traffic to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box? 
The offloading function of a loadbalancer protects the organization from a denial-of-service(DDoS) attack.
The main advantage to having a jump box is to add an additional layer of protection with MFA

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system files.
- What does Filebeat watch for? Data about the file system
- What does Metricbeat record? Machine metrics such as uptime

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Client   | 10.0.0.5   | Linux            |
| Web-2    | Client   | 10.0.0.6   | Linux            |
| Web-3    | Client   | 10.0.0.7   | Linux            |
|ELK-SERVER| Gateway  | 10.2.0.4   | Linux            |
/Images/Network Interfaces

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses 68.117.68.138

Machines within the network can only be accessed by ssh from the Jump-box VM.
- Which machine did you allow to access your ELK VM? What was its IP address? Jump-Box can access the ELK-SERVER private ip is 10.0.0.4:22

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes.                | 10.0.0.4 10.0.0.30   |
|          |                     |                      |
|          |                     |                      |
/Images/SSHAccess
/Images/Jump-Box-ip

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? configuration management and provisioning

The playbook implements the following tasks:
- .Install docker
- .Install pip3
- .Install docker python module
- .Increase and set memory to 262144
- .Download and launch docker elk container:761

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
/Images/Install Elk Playbook

Images/docker ps

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6 
Web-3 10.0.0.7
ELK-SERVER 10.2.0.4
/Images/Network Interfaces

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed 
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat - Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing
- Metricbeat - It records the metrics and statistics such as up time, that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible .
- Update the hosts file to include each vm client IP address (10.0.0.5 - 10.0.0.7) ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to 10.0.0.5 and curl localhost/setup.php to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it? Ansible-playbook.yml /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? It is updated on the hosts file, add hosts name elk into the webservers group followed by the IP address for the ELK-SERVER in this case 10.2.0.4
/Ansible/hosts-file.txt
- _Which URL do you navigate to in order to check that the ELK server is running? Public IP address on port 5601/app (168.62.6.70:5601/app)

ansible-playbook *.yml
nano hosts
nano ansible.cfg
nano *.yml 
