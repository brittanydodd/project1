# project1

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- Load balancers distribute traffic among servers, lightening the load & managing traffic. The avantage of of a jumpbox is everything is managed on a secure system, & allows admins to access the environment remotely in a secure zone.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.

- Filbeat is used to forward, monitor, & log data
- Metricbeat collects statistics from the target servers & the seervices running on them & sends them to elasticsearch (in the instance). Can also monitor filebeat & elk stack

The configuration details of each machine may be found below.

| name    	| function 	| ip address   	| operating system 	|
|---------	|----------	|--------------	|------------------	|
| jumpbox 	| gateway  	| 20.115.80.94 	| linux            	|
| web1    	| ansible  	| 10.0.0.5     	| linux            	|
| web2    	| ansible  	| 10.0.0.6     	| linux            	|
| elk     	| elkstack 	| 10.1.0.4     	| linux            	|

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- my ip 69.117.190.27
- jumpbox ip 10.0.0.4

Machines within the network can only be accessed by
- jumpbox 10.0.0.4

A summary of the access policies in place can be found in the table below.

| name    	| publically accessible 	| allowed ip addresses 	|
|---------	|-----------------------	|----------------------	|
| jumpbox 	| no                    	| 69.117.190.27        	|
| web1    	| no                    	| 10.0.0.5             	|
| web2    	| no                    	| 10.0.0.6             	|
| elk     	| no                    	| 10.0.0.4             	|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- you can reuse your playbooks & modify to use on any number of machines multiple times. saves time from using single commands & helps you to be able to check your work & troubleshoot in one place. you can also keep track of what each command is, helping other users who may need to run these commands

The playbook implements the following tasks:
- install docker, install python3, install docker module, increase virtual memory, use more memory, download & launch a docker elk container, enable docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- metric is collecting CPU usage, memory perentage, # of containers etc.
- filbeat is collecting the processes going on in each VM & logging the data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk.yml file to the ansible control node
- Update the config file to include webserver & elk
- Run the playbook, and navigate to http://20.109.1.194:5601/app/kibana to check that the installation worked as expected.


curl https://github.com/brittanydodd/project1/blob/main/ansible/elk.yml
