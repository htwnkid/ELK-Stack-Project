## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/Network_Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly REDUNDANT, in addition to restricting TRAFFIC to the network.
- _TODO: 

         What aspect of security do load balancers protect? Load Balancers distribute network
              traffic across multiple VM's, thereby protecting against DDOS attacks
                                  
         What is the advantage of a jump box?_It restricts or reduces traffic to the VM's running the Web Application

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.

        _TODO: What does Filebeat watch for? File system
        _TODO: What does Metricbeat record?  Machine metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function   | IP Address | Operating System |
|----------|------------|------------|------------------|
| Jump Box | Gateway    | 10.1.0.4   | Linux            |
| Web-1    | Web Server | 10.1.0.5   | Linux            |
| Web-2    | Web Server | 10.1.0.6   | Linux            |
| Web-3    | Web Server | 10.1.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

        _TODO: Add whitelisted IP addresses_40.70.135.108 (JumpBox Public IP)

Machines within the network can only be accessed by _____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

         The ELK VM is only accessible from the ansible container running on the JumpBox VM.
         IP Address - 10.1.0.4 Private IP Addr 


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses            |
|----------|---------------------|---------------------------------|
| Jump Box |        Yes          |    40.70.135.108                |
| Web-1    |        No           |    10.1.0.5                     |
| Web-2    |        No           |    10.1.0.6                     |
| Web-3    |        No           |    10.1.0.7                     |
| Elk-VM   |        No           |    10.1.0.5, 10.1.0.6, 10.1.0.7 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- _TODO: What is the main advantage of automating configuration with Ansible?_

         Answr - The main advantage of automating configuration with Ansible is
                the ease of configuring Standardized VM across one or more VM's.

The playbook implements the following tasks:

- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._

        - Install Docker (docker.io) high-level API, which contains the core docker components
        - Install Python3
        - Increase Virtual Memory
        - Download and launch the docker elk container
        - Start Docker

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/Elk_Container_Running.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

    - _TODO: List the IP addresses of the machines you are monitoring
             - 10.1.0.5 Web VM-1
             - 10.1.0.6 Web VM-2
             - 10.1.0.7 Web VM-3

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed

        Answr - Filebeat

These Beats allow us to collect the following information from each machine:

- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide         1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

        Answr - Filebeat is responsible for monitoring log files or user-specified events, as well as collecting log events on the installed servers and sending that info to Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_

- _Which file is the playbook? Where do you copy it?_

        - OffSecyaml.yml is the name of the playbook
        - Copy it to the ansible roles directory

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

        - The host file contains the IP Addresses of the installation machines

        - You would create separate group tags for each server in question. For example [Elk] for the machine on which the ELK Server is to be installed and [webservers] for the machines on which to install filebeat.

- _Which URL do you navigate to in order to check that the ELK server is running?

        - Navigate to the kibana page running on the ELK VM. The URL is: 

          [Elk VM Public IP]:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._