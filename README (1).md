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
  
  -Run this command through the shell: 
  
      sysctl -w vm.max_map_count=262144
  
  -Installs following packages
      
      docker.io - Used for running containers
      
      python-pip - installs python
      
      ![DockerPS path] (https://github.com/vinnymbarone/ELK.project/blob/master/Images/Dockerps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5

We have installed the following Beats on these machines:

    -Filebeat

These Beats allow us to collect the following information from each machine:

    Filebeat is built to collect data, such as log events about specific files on remote machines, it must be installed on the VMs that you want to monitor.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file from your Ansible container to your ELK VM.
- Update the configuration file to include the private IP of our ELK Server.
- Run the playbook, and navigate to curl localhost/setup.phpto to check that the installation worked as expected.

- The ansible-playbook command will run the contents of the playbook.yml file. The name can be anything as long as it ends in ".yml"
         
         -"ansible-playbook [name]-playbook.yml

- _Which file do you update to make Ansible run the playbook on a specific machine? 
   
      - Update /etc/ansible/filebeat-configuration.yml and add remote machines (machine's IP) to it. 

How do I specify which machine to install the ELK server on versus which to install Filebeat on?

    Filebeat: we are connecting our DVWA-VM1 to ELK Server, so we need to include ELK Server IP. In the filebeat-configuration.yml file, we replace the IP address with the IP of the ELK Machine.

ELK Server: We specify a remote user (machine admin name) in the ansible.cfg file and we list the IP address of our ELK server in the hosts file. 

- _Which URL do you navigate to in order to check that the ELK server is running?
    
      -https://23.96.86.187:5601/

