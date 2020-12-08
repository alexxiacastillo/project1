## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagramming the Network https://app.diagrams.net/#G1-oMOEUXLO15TrOfLB2VxAK1cF4OqlxLx

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/my-elkservers.yml
  - install_elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting in-bound access to the network.
- What aspect of security do load balancers protect? A load balancer intelligently distributes traffic from clients across multiple servers without the clients having to understand how many servers are in use or how they are configured. Because the load balancer sits between the clients and the servers it can enhance the user experience by providing additional security, performance, resilience and simplify scaling your website.
- What is the advantage of a jump box? A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jump box and system network.
- What does Filebeat watch for? Filebeat watches for any information in the file system which has been changed and when it has.
- What does Metricbeat record? Metricbeat takes the metrics and statistics that collects and ships them to the output you specify

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Elk VM   |Monitoring| 10.1.0.5   | Linux            |
| Web 1    |DWVAserver| 10.0.0.5   | Linux            |
| Web 2    |DWVAserver| 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 67.163.61.18 (MY IP)

Machines within the network can only be accessed by the Jump-Box Provisoner.
- Which machine did you allow to access your ELK VM? Jumpbox Provisioner VM 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 67.163.61.18         |
| Web 1    | No                  | 10.1.0.5             |
| Web 2    | No                  | 10.1.0.5             |
| Elk VM   | No                  | 67.163.61.18         |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? 
- Free: Ansible is an open-source tool.
- Very simple to set up and use: No special coding skills are necessary to use Ansible’s playbooks (more on playbooks later).
- Powerful: Ansible lets you model even highly complex IT workflows.
- Flexible: You can orchestrate the entire application environment no matter where it’s deployed. You can also customize it based on your needs.
- Agentless: You don’t need to install any other software or firewall ports on the client systems you want to automate. You also don’t have to set up a separate management structure.
- Efficient: Because you don’t need to install any extra software, there’s more room for application resources on your server.

The playbook implements the following tasks:
- _In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
- Install docker.io
- Install pip3
- Instal Docker python module
- Download and Lunch a docker
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/Screen Shot 2020-12-06 at 11.04.19 PM)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1 10.0.0.5
- Web 2 10.0.0.6
We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeat collects the changes done and collects data about the file system.
- Metricbeat collects machine metrics and statistics, such as uptime. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to Ansible Control Node.
- Update the hosts file to include webserver and elk
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_Which file is the playbook? Where do you copy it? /etc/ansible/file/filebeat-configuration.yml
_Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to _install the ELK server on versus which to install Filebeat on? Edit the /etc/ansible/host file to add webserver/elkserver ip addresses
_Which URL do you navigate to in order to check that the ELK server is running?
http://publicIP/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
- ansible-playbook filebeat-playbook.yml
