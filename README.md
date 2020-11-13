# project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project#1_Diagram](https://github.com/pibo47/project1/blob/main/Project%231_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/roles/filebeat-playbook.yml
  - /etc/ansible/roles/metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availible, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the usage and system files.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Elk-VM   | Server   | 10.1.0.4   | Linux            |
| Web1     | Server   | 10.0.0.5   | DVWA             |
| Web2     | Server   | 10.0.0.6   | DVWA             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 108.71.180.87

Machines within the network can only be accessed by Elk-VM.
- 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 108.71.180.87        |
| Elk-VM   | No                  | 10.0.0.4             |
| Ansible  | No                  | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- ansible allows automatic deployment to multiple machines with the playbook function

The playbook implements the following tasks:
- _Install and Download docker, curl filebeat/metricbeat config files, load and install filebeat/metricbeat, install and setup filebeat/metricbeat

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docker Image](https://github.com/pibo47/project1/blob/main/Docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
- Metricbeat and Filebeat

These Beats allow us to collect the following information from each machine:
- Metricbeat allows the analysis and logging of docker container usage, while Filebeat detects the traffic and usage of files on the machine.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to /etc/Filebeat/filebeat.yml, also /etc/Metricbeat/metricbeat.yml.
- Update the filebeat/metricbeat file to include updated host and port settings, along with password and username for the machine.
- Run the playbook, and navigate to kibana to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook <filename>
curl
service start
setup -e
