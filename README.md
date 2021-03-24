## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/zghanniaiman/Week13/blob/main/Diagrams/AzureDiagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/install-elk.yml)
  - [Filebeat Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/filebeat-playbook.yml)
  - [Metricbeat Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/metricbeat-playbook.yml)


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_ Load blanacers protect against DDoS attacks and jump box gives you access to your network from a single node that is secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- _TODO: What does Filebeat watch for?_ info in the file system which has been changed
- _TODO: What does Metricbeat record?_ it collects metrics and statistics and outputs them to what you specify

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.1.4   | Linux            |
| Web-1    | Server   | 10.0.1.5   | Linux            |
| Web-2    | Server   | 10.0.1.6   | Linux            |
| ELK      | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ Home public IP

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ Jump Box, 10.0.1.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 184.144.39.92        |
| Web-1    | Yes                 | 10.0.1.4             |
| Web-2    | Yes                 | 10.0.1.4             |
| ELK      | Yes                 | 10.0.1.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_ Input commands into multiple servers from a single playbook

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
Install: docker.io
Install: python-pip
Install: docker
Command: sysctl -w vm.max_map_count=262144
Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 https://github.com/zghanniaiman/Week13/blob/main/Diagrams/sudodockerps.PNG 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_ 10.0.1.5 and 10.0.1.6

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ Filebeat and MEtricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
Filebeat collects the changes that were done and metricbeats collects metrics and statictics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to /etc/ansible.
- Update the /etc/ansible/host file to include the hosts group, private IP address and the following line ansible_python_interpreter=/usr/bin/python3.
- Run the playbook, and navigate to curl localhost/setup.php to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_ 
- _Which file is the playbook? Where do you copy it?_ /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
edit the host file in /etc/ansible/ to add the web/elk server ip address
- _Which URL do you navigate to in order to check that the ELK server is running? www.publicip:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
ansible-playbook filebeat-playbook.yml
