## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![alt text](https://github.com/zghanniaiman/Week13/blob/main/Diagrams/AzureDiagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - [Elk Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/install-elk.yml)
  - [Filebeat Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/filebeat-playbook.yml)
  - [Metricbeat Playbook](https://github.com/zghanniaiman/Week13/blob/main/Ansible/metricbeat-playbook.yml)


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load blanacers protect against DDoS attacks. The jump box gives you access to your network from a single node that is secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
Filebeat is an agent installed on your severs, it gives you info in the file system which has been changed
Metricberat collects metrics and statistics and outputs them to what you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.1.4   | Linux            |
| Web-1    | Server   | 10.0.1.5   | Linux            |
| Web-2    | Server   | 10.0.1.6   | Linux            |
| ELK      | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioning machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Home public IP (184.144.39.92) can access this machine

Machines within the network can only be accessed by SSH.
- The Jump-Box-Provisioning machine (10.0.1.4) can access the ELK VM

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 184.144.39.92        |
| Web-1    | Yes                 | 10.0.1.4, LB IP      |
| Web-2    | Yes                 | 10.0.1.4, LB IP      |
| ELK      | No                  | 10.0.1.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-

The playbook implements the following tasks:
- Config Web VM with Docker
- Install docker.io, python, pip3
- Download and Launch ELK Docker Container
- Enable docker service
- Increase Virtual Memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt text](https://github.com/zghanniaiman/Week13/blob/main/Diagrams/sudodockerps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.1.5
- 10.0.1.6

We have installed the following Beats on these machines:
- Filebeat
- MEtricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors what you specify, collects log events and forwards them to Elasticsearch or Logstash
- Metricbeats collects metrics and statictics from the operating system and services running

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-configuration.yml file to /etc/ansible/file/.
- Update the config file to include the hosts group, private IP address and the following line ansible_python_interpreter=/usr/bin/python3.
- Run the playbook, and navigate to ELK to check that the installation worked as expected.
- Filebeat-playbook.yml, metricbeat-playbook.yml are copied to /etc/ansible/
- Edit the host file in /etc/ansible/host.cfg to add the web/elk server ip address
- Access through www.publicip:5601

