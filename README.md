# Ansible-Configure - Controller Node & Managed Node

- Ansible Controller - RedHat Server/Centos
- Ansible Managed - Ubuntu

*Login to Ubuntu Server - Make Modification in Managed Ubuntu Server
---------------------------------------------------------------------

* echo "ubuntu ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/ubuntu
* sudo su

*Change the ubuntu password
passwd ubuntu

*Change sshd_config file - Change two paramters

* vi /etc/ssh/sshd_config

PubkeyAuthentication yes
PasswordAuthentication yes


*Login to Red Hat
------------------------------------------------------
*Install Ansible

* sudo dnf install -y ansible-core

* dnf list ansible-core

* dnf info ansible-core

* ansible --version

* ssh-keygen

* ssh-copy-id ubuntu@43.205.237.80

* mkdir automation

----------------------------------
* Create ansible configuration file
------------------------------------
* vim ansible.cfg

[defaults]
inventory = ./inventory \
host_key_checking = false \
- remote_user = ubuntu
- ask_pass = false

[privilege_escaltion]
- become=true
- become_method=sudo
- become_user=root
- become_ask_pass=False

-----------------------
* Create Inventory file
------------------------
* vim inventory

[ubuntu]
43.205.237.80

*Everything is set!

* Use ping module and Check if ping is working

ansible all -m ping
