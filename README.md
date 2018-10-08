# AWS MESOS MARATHON STACK using Ansible and Cloudformation

Albert Monfà - 2016

## ANSIBLE ENVIRONMENT PROVISION
=============================

Ansible Playbooks needs Ansible >2.0, if you are using OSX or you won't
install ansible on your machine you can be use Vagrant from HashiCorp
like this:
- vagrant up --provision (first time)
- vagrant up (after first time)

Note: inside vagrant machine you can found the Ansible playbooks under
/vagrant directory


## PREVIUSLY TUNES
===============

Ansible aws-env role needs setting AWS keys like environment vars
 - export AWS_ACCESS_KEY_ID=FOO
 - export AWS_SECRET_ACCESS_KEY=BAR

Altought it's also necessary in your AWS Account the creation of a key pair
used to associate EC2 Instance from yourself and ansible, and place it in ./ansible

We recommend revising the AWS vars file present in ./ansible/group_vars/all
and make changes if it's necessary

Another important step it's the provisioning ssh public-key of aspirants inside
the directory ./Ansible/files/sshkeys/

To gathering facts from EC2 instances is necessary add next config to ansible.cfg

[defaults]
host_key_checking = False


## PROVISIONING WITH ANSIBLE
========================

When all is done, the final step is running Ansible, this procces should be
long

 - ansible-playbook -v site.yml

When the execution ends, look the summary output and note the public IP assigned
for Cloudformation, you need these from connect to ssh.


## TWEAKS
======

For testing pruposals you can create a Socks proxy on your machine
only needs a ssh command that will be see:
 - ssh -vv -ND 8080 root@<pub_ip>
 - add socks server 127.0.0.1:8080 in your browser
