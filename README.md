
# Project Title
Deploy nodejs app using ansible .
# Description
This project aims to deploy nodejs app using ansible playbook which consist of two plays every one contains some to deploy this app .
# prerequisites
Before start to create ansible playbook some prerequisites such as:

1- Create two ubuntu ec2 on aws 

2- Create vm on  vmware workstation (locally) using centos 7 os act as ansible controller

3- Create user called ansible on each vm (local vm and ec2) and add it to sudoers users  

4- Install ansible on centos 7 vm 

5- Connect to each ec2 using ssh connection

6- Create inventory file to include ec2 hosts under group name "nodes"

7- Create ansible.cfg file to include two main ansible configuration as following:

- default

  - inventory=inventory
  - host_key_checking=false
   - remote_user=ansible

- privilege_escalation

  - become=true
  - become_user=root
  - become_method=sudo
  - become_ask_pass=no


# Install node and npm Play
 This play has many tasks :

 - Update system cache => using apt module and save cache for 3600 sec
 - Install nodejs => using apt module
 - Install npm => using apt module
 # Delpoy nodejs app play
 This play has many tasks:

 - Copy nodejs folder => using Copy module to copy nodejs.tar  from current directory to /root/
 - Unpack nodjs file => using unarchive module 
 - install dependancy => using npm (not buit in module) which install in first play
 - start app => using command module to run cmd command " node sever"
 - ensure app is running => using shell module and save output in register module with variable name called "output"
 - print output => using debug module to print output from register

 # Variable
 Create file called group_vars/nodes which ansible will understand it without need to referance it in every play in playbook .

 nodes=> group of two ec2 hosts in inventory file.











