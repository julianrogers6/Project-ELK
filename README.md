## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/julianrogers6/Project-ELK/blob/main/Diagrams/ELK%20PROJECT%201.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  [• Filebeat Configuration](https://github.com/julianrogers6/Project-ELK/blob/main/Ansible/filebeat_configuration)

 • [Install Filebeat](https://github.com/julianrogers6/Project-ELK/blob/main/Ansible/install_filebeat)

  • [Install Elk.yml](https://github.com/julianrogers6/Project-ELK/blob/main/Ansible/install_elk%2Cyml)

  • [Metricbeat Configuration](https://github.com/julianrogers6/Project-ELK/blob/main/Ansible/metricbeat_configuration)

  • [Install Metricbeat](https://github.com/julianrogers6/Project-ELK/blob/main/Ansible/install_metricbeat)

This document contains the following details:

  • Description of the Topology

  • Access Policies

  • ELK Configuration

  • Beats in Use

  • Machines Being Monitored

  • How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

  • Load balancing ensures that the application will be highly available, in addition to restricting access to the network. What aspect of     security do load balancers protect? Load Balancers help protect against denial of service attacks (DDoS), when the load balancer   inspects the traffic received it will decide which server to send it to. What is the advantage of a jump box? Advantages of using a jump box are they limit any access that the public would have to your virtual network. A jump box will allow more control when deciding access to a virtual network and its contents. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

​    • What does Filebeat watch for? Filebeat generates and organizes log files while searching for changes and when those changes accrued.

​    • What does Metricbeat record? Metricbeat records metrics from the OS and services running on that server. Elastic and Logstash allow  you to visually see the metrics that Metricbeat generates. 

The configuration details of each machine may be found below.

| Name     | Function   | IP Address | Operating System |
| :------- | ---------- | ---------- | ---------------- |
| Jump Box | Gateway    | 10.0.0.4   | Linux            |
| Web-1    | Web Server | 10.0.0.5   | Linux            |
| Web-2    | Web Server | 10.0.0.6   | Linux            |
| Web-3    | Web Server | 10.0.0.8   | Linux            |
| Elk      | Log Server | 10.1.0.4   | Linux            |

### Access Policies

  • The machines on the internal network are not exposed to the public Internet. 

  • Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

  • The public IP of the host computer through port 22

  • Machines within the network can only be accessed by the JumpBox Provisioner machine.

  • Which machine did you allow to access your ELK VM? JumpBox Provisioner 

  • What was its IP address? 13.83.40.212

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
| -------- | ------------------- | -------------------- |
| Jump Box | Yes                 | 13.83.40.212         |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |
| Web-3    | No                  | 10.0.0.8             |
| Elk      | Yes                 | 10.1.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because automation allows for quick configuration of the containers being used making it easy to run each playbook on multiple machines. Having the ability to atomize can save time and assure less mistakes. 

The playbook implements the following tasks:

  • Install docker.io

  • Install python3-pip

  • Install docker module

  • Increase virtual memory

  • Download and launch docker elk container

### Target Machines & Beats

This ELK server is configured to monitor the following machines: 

  • Web-1 10.0.0.5       

  • Web-2 10.0.0.6

  • Web-3 10.0.0.8

We have installed the following Beats on these machines: 

  • Filebeat 

  • Metricbeat

These Beats allow us to collect the following information from each machine:

  • Filebeat gathers information about the log file system and determines which files have been changed and when. 

  • Metricbeat on the other hand shows the statistics on every running process on the system whether it be CPU usage, memory or    network stats.  

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

  • Verify the Public IP address to see if it has changed.

  • If changed then update the Security Rules that uses the My Public IPv4

SSH into the control node and follow the steps below:

  • Copy the configuration file to /etc/ansible/files/filebeat.config.yml 

  • Update the filebeat-config.yml configuration file to include the IP address on the network.

  • Run the playbook, and navigate to Kibana (Elk GUI) and select "Check Data" to check that the installation worked as expected.  
