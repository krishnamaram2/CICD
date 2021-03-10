# Project Title

Jenkins is used for Continuous Integration/Continuous Delivery/Continuous Deployment purpose

Jenkins installation and Set up
=====================================

https://linuxize.com/post/how-to-install-jenkins-on-centos-7/


Step 1: install openjdk and set up environment variables
$sudo yum install java-1.8.0-openjdk-devel

Step 2: install Jenkins server
$curl --silent --location http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo | sudo tee /etc/yum.repos.d/jenkins.repo

$sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key

$sudo yum install jenkins

$sudo systemctl start jenkins

$sudo systemctl enable jenkins

Step 3: configure jenkins job to build and deploy war file




Automation Installation 
==============================

$yum update -y && yum upgrade -y

$yum install git -y && yum install wget -y && yum install unzip -y && yum install curl -y

$yum install ansible -y

Set up
==============

Step 1: switch to root user

sudo su -l

passwd root

step 2: enable password authentication

vi /etc/ssh/sshd_config

PasswordAuthentication yes

permitroorlogin yes

systemctl restart sshd

step 3: generate ssh keys for key based authentication

ssh-keygen

ssh-copy-id root@localhost


Execution Flow
=======================
step 1: clone repo

$git clone https://github.com/krishnamaram2/Configuration_Manager.git

Step 2:

$cd Configuration_Manager/src

$ansible-playbook -i hosts jenkins.yml



