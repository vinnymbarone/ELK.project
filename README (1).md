## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Disagram] (https://github.com/vinnymbarone/ELK.project/blob/master/Images/Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ![Filebeat-Playbook] (https://github.com/vinnymbarone/ELK.project/blob/master/filebeat-playbook.yml) may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly distributed, in addition to restricting traffic to the network.
The load balancer separates workloads across different servers. Load balancers also reroute live traffic to prevent the possibility of DDoS attacks that could make servers unavailable.

A jump server or jump host or jumpbox is a (special-purpose) computer on a network typically used to access devices in a separate security zone. The most common example is managing a host in a DMZ from trusted networks or computers. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.

Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box |Gateway   | 10.0.0.4   | Linux            |
| DVWA VM1 |Load Blncr| 10.0.0.5   | Linux            |
| ELK-Servr|ELK-Stack | 10.0.0.7   | Linux            |
|          |          |            |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
10.0.0.4 and 13.82.93.18

Machines within the network can only be accessed by SSH Key.
Allowed access from DVWA - VM1 to the ELK - VM 10.0.0.5

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes.                |10.0.0.1 13.82.93.18  |
| DVWA VM1 | No.                 |10.0.0.5              |
| ELK-SRVR | Yes.                |10.0.0.7 23.96.88.187 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because all the remote hosts will be updated with the details from configuring security details on the control machine to run the associated playbook. This helps because you will not need to monitor each machine for security compliance.

The playbook implements the following tasks:

1. Install Docker and verify you are the Ansible container.
2. Create a new playbook: touch /etc/ansible/install-elk.yml.
3. Ensure that that header of the playbook must specify elkservers as the target hosts.
4. Write tasks that do the following:
  -Run this command through the shell: sysctl -w vm.max_map_count=262144
  -Installs following packages
      docker.io - Used for running containers
      python-pip - installs python
      
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
