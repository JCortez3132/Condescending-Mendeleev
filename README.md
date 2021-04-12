## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://raw.githubusercontent.com/JCortez3132/Condescending-Mendeleev/main/Diagrams/Untitled%20Diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible-Playbook elk.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly AVAILABLE, in addition to restricting ACCESS to the network.
Load balancers add additional layers of security by their off-loading function which allows load balancers to assist in protecting against distributed denial of service attacks. A jump box server provides a secure connection to other servers or untrusted environments. It can manage devices in different security zones and provides a controlled means of access to them. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
Filebeat watches and monitors the log files or locations that users specify, collects log events, and forwards them for indexing.
Metricbeat collects and records statistics of the servers and sends them to the output that one specifies.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function   | IP Address | Operating System |
|---------- |------------|------------|------------------|
| Jump Box  | Gateway    | 10.0.0.1   | Linux            |
| Web-1     | Web Server | 10.0.0.4   | Linux            |
| Web-2     | Web Server | 10.0.0.5   | Linux            |
| ELK-Server| Monitoring | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox Proivisioner machine can accept connections from the Internet. Access to this machine is only allowed from my personal laptop.

Machines within the network can only be accessed by peer servers and a connection via JumpBox. I used my personal laptop to access the JumpBox Provisioner's public IP address: 13.66.253.10

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses   |
|---------- |---------------------|----------------------  |
| Jump Box  | Yes                 | Personal laptop public |
| Web 1     | No                  | 10.0.0.4               |
| Web 2     | No                  | 10.0.0.4               |
| ELK-Server| No                  | 10.0.0.4
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it automates IT configuration management and simultaneously deploys to multiple servers. Automating configuration with Ansible allows the simplification of repetitive and complex operations. This saves time and resources for the user and/or organization they're working for.

The playbook implements the following tasks:

- Install docker.io
- Install pip3
- Install Docker python module
- Download/Launch docker ELK container
- Enable service docker on boot

You can run the command "docker ps" to verify the containers are up and running. 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5 and Web-2 10.0.0.6

We have installed the following Beats on these machines:
Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:

Filebeat monitors log files, collects log events, and forwards them to elasticsearch or Logstash for indexing. Metricbeat collects data from a specific service or operating system and ships them to an output of the users choice.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Replace IP address with ELK server private IP address in filebeat-configuration.yml ans save to /etc/ansible/files/filebeat-config.yml.
- Update the hosts file to include the ELK server
- Run the playbook, and navigate to the web page to check that the installation worked as expected.

- The filebeat-playbook.yml file is the playbook. Copy to /etc/ansible/files
- Update /etc/ansible/hosts file to run the playbook on a specific machine. To specify which machine to install the ELK server, choose the ELK server group. 
- Navigate to http://X.X.X.X:5601/app/kibana to check ELK server is up and running.


