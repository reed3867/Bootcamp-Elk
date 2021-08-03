## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram] (Project 1-Elk Stack Network Topology.png![Project 1-Elk Stack Network Topology](https://user-images.githubusercontent.com/78981096/127951920-dc336284-8107-4feb-a5b3-ebb758d3a662.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file.my-playbook.yml

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
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?  The DVWA, Filebeat and Metricbeat Docker containers are placed behind Load Balencers. The load balancers will allow access for non regular accessable WebVM's that carry pertinent information. The Load Balancer distributes the work load across the various machines to aid in preventing a single point machine failure.

The JumpBox primary advantage, is that it explicitly restricts access to the network.  This is accomplished by requiring those who request access to SSH into the JumpBox in order to enter into the docker containers and or move to any other machines on the network.  The JumpBox allows only a single point of entry, which allows for easier monitoring or modifying security procedures, thus, hardening the network overall. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Network and system Files.
- _TODO: What does Filebeat watch for? Filebeat monitors the locations that the user  specifies, monitors log files, gathers log events and forwards those logs to the Elasticsearch or Logstash for indexing. 
- _TODO: What does Metricbeat record? Metricbeat periodically collects metrics from the operating system and services running on the server.  It then transfers those statistics over to  Elasticsearch or Logstash for output. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web1     | Webserver | 10.0.0.5   | Linux            |
| Web2     | Webserver | 10.0.0.6   | Linux            |
| Web3     | Webserver | 10.0.0.9   | Linux            |
| ElkVM    | Elk Server| 10.5.0.4   | Linux            |
  
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 73.122.211.161
In addition, a modification to the firewall rules is necessary to allow traffic from the Public IP it represents. 
- _TODO: Add whitelisted IP addresses 73.122.211.161

Machines within the network can only be accessed by The JumpBox address.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Name         | Publicly Accessible | Allowed IP Addresses |
|--------------|---------------------|----------------------|
| Jump Box     | Yes                 | 73.122.211.161       |
| Web 1        | No                  |    10.0.0.5          |
| Web 2        | No                  |    10.0.0.6          |
| Web 3        | No                  |    10.0.0.9          |
| Elk VM       | Yes                 | 73.122.211.161       |
| Load Balancer| Yes                 | 73.122.211.161       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? Automating with Ansible in short allows IT adminstrators the time to work on more prioritized tasks while Ansible works through some of the more mondane repetitive daily tasks.  

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- .Install Docker.io .Install pip3 as an addition to the python Docker Module .Allows an increase of Virtual Memory .Ensures that ELK runs every time the machine is booted .Downloads and launches a docker ELK container via the following published ports: 5044 5601 9200
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Elk Stack Project 1-Docker ps running.png![Elk Stack Project 1-Docker ps running](https://user-images.githubusercontent.com/78981096/127952384-68dcac32-e91b-445d-a31a-a7caf61c1459.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring; 10.0.0.5  10.0.0.6  10.0.0.9

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed; We successfully installed Filebeat and Metricbeat.
Filebeat monitors the traffic by collecting log data on devices.
Metricbeat collects data from the CPU/OS and any memory running on the server. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Deployment file to /etc/ansible/roles.
- Update the /etc/ansible/hosts file to include remote_user=AZADMIN the user for each VM.
- Update the /etc/ansible/hosts file to include the IP address in the webservers and ELK groups.  You must uncomment the webservers selection and add the ELK section so it will work.
- Run the playbook, and navigate to 13.77.157.37:5601/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks: /etc/ansible/elk-playbook.yml should be copied to your directory.
- _Which URL do you navigate to in order to check that the ELK server is running? 13.77.157.37:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
