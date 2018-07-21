# Ansible Playbook for Automation Installation & Configuration LAMP (Linux Apache MariaDB PHP) + CMS WordPress

Automate installation & configuration of CentOS Server with software package specification LAMP (Linux Apache MariaDB PHP)

## Requirments
- Git
- Ansible 2+

## Installation
First you need to install Git and Ansible first on your server and the following commands you can follow:

```
yum install epel-release -y
yum update -y
yum install git ansible -y
cd /opt/
git clone https://github.com/xnxmx/ansible-lamp-wordpress.git
```

To see which version of Ansible is installed, type the following command:

```
ansible --version
```

The next step is to generate the SSH Key, this is done to generate the Private Key and Public Key which will be used as the authentication of the search for communication between two or more hosts, the following commands are:

```
ssh-keygen -t rsa -b 4096
```

Make changes to the host according to your needs:

```
vi /etc/ansible/hosts
```

and add the following line of code below:

```
[ansiblehost]
192.168.1.1
```

The next process is to authenticate login on host 192.168.1.1, and following the command:

```
ssh-copy-id root@192.168.1.1
```

To perform connection checks on previously added hosts, run the following commands:

```
ansible -m ping ansiblehost
```

To run this Ansible Playbook, run the following command:

```
ansible-playbook /opt/ansible-lamp-wordpress/roles/playbook.yml
```

## Notes
- Ansible Playbook is still tried on CentOS 7 x86_64 only
- If you are using another operating system, feel free to make changes to an existing role
- To make changes to the Ansible configuration file, you can change the following files:

```
/etc/ansible/hosts
/opt/ansible-lamp-wordpress/.my.cnf
/opt/ansible-lamp-wordpress/wp-config-sample.php
/opt/ansible-lamp-wordpress/roles/wp-dependencies/tasks/main.yml
/opt/ansible-lamp-wordpress/roles/wp-dependencies/defaults/main.yml
/opt/ansible-lamp-wordpress/roles/wp-install-config/tasks/main.yml
```
