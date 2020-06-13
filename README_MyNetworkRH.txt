## Automated ELK Stack Deployment (Rick Hart)

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _install-elk.yml._

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
- _Having load balancing will help protect my network from DDoS attachs. I am using a Jump Box to ensure all of the management tools are maintained on a single system.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system metrics.
- _Filebeat looks for log data
- _Metricbeat collects metrics and statistics

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA-VM1 | webserver| 10.0.0.5   | Linux            |
| DVWA-VM2 | webserver| 10.0.0.6   | Linux            |
| DVWA-VM3 | Elk Box  | 10.0.0.7   | Linux            |
| DVWA-VM4 | webserver| 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _73.207.87.98_

Machines within the network can only be accessed by the Jump Box.
- _10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes                 | All                  |
| DVWA-VM1 | No                  | 10.0.0.4             |
| DVWA-VM2 | No                  | 10.0.0.4            |
| DVWA-VM3 | Yes                 | 73.207.87.98         |
| DVWA-VM4 | No                  | 10.0.0.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- All VMs were configured with the same base image.

The playbook implements the following tasks:
- _ Installs the Docker.io
- Installs the Python-pip
- ... publishes required ports.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _10.0.0.5
- _10.0.0.6

We have installed the following Beats on these machines:
- _Filebeat
- _Metricbeat

These Beats allow us to collect the following information from each machine:
- _ Filebeat will collect logs from each of the webservers on my network. 
- _ Metricbeat will collect performance metrics from each of the webservers on my network.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat and metricbeat configuration.yml files to /etc/ansible/roles/
- Update the configuration files to include your elk server host ip address and port.
- Run the playbook, and navigate to installation directories to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? "-playbook.yml Where do you copy it to. /etc/ansible/roles/
- _Which file do you update to make Ansible run the playbook on a specific machine? (hosts file) How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ you have to place a 
heading in the hosts file for "elkservers". under that heading you will add the ip of your elkserver only.
- _Which URL do you navigate to in order to check that the ELK server is running? http://"elkserver external ip:port"

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

