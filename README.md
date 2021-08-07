Description of Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly responsive, in addition to restricting Traffic to the network.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the JumpBox and system Network.
Name 
Function 
IP Address 
Operating system 
Jump box 
Gateway 
10.0.0.4
Linux 
Web 01
Web Server
10.0.0.5
Linux
Web 02
Web Server 
10.0.0.6
Linux 
Elk-server
Monitor 
10.1.0.4
LInux 

Access Policies 
The machines on the internal network are not exposed to the public Internet.
Only the Jumpbox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:108.94.48.150
Machines within the network can only be accessed by Jumpbox
A summary of the access policies in place can be found in the table below.
Name 
Publicly Accessible 
Allowed IP Addresses 
Jumpbox
yes
108.94.48.150
web01
no
10.1.0.4
web02
no
10.1.0.4
ElK Server
no
10.1.0.4

ElK Configuration 
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it speeds up the deployment of changes and allows for quick deployment. It's also Advantageous because no human error on the setup can occur , they are all golden images , it's efficient.
The playbook implements the following tasks:
Installs docker.io, pip3, and docker
Increases virtual memory 
Implements the increased memory 
Downloads and launches the elk container 
Target Machine and beats
This ELK server is configured to monitor the following machines:
The elk Server is monitoring web01 (ip of: 10.0.0.5) and web02 (ip of: 10.0.0.6)
We have installed the following Beats on these machines:
Metricbeats
filebeats 
These Beats allow us to collect the following information from each machine:
Metricbeats are used to collect system information that has been specified on servers periodically by giving statistical information. 
Filebeats is also for the servers but monitors specified log files instead of the system info , these both get forwarded to a file for indexing. 
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:
Copy the configuration file from the ansible container file to Webs VM.
Update the etc/ansible/host file to include ip address of the elk server vm and web servers 
Run the playbook, and navigate to http://[Elk_VM_IP]:5601/app/kibana to check that the installation worked as expected.
Which file is the playbook? The Filebeat-configuration
Where do you copy it? copy /etc/ansible/files/filebeat-config.yml to /etc/filebeat/filebeat.yml

Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? update filebeat-config.yml -- specify which machine to install by updating the host files with ip addresses of web/elk servers and selecting which group to run on in ansible
_Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana.
