# Prerequisites
- Ansible 2.10
- Ansible Azure [extension](https://galaxy.ansible.com/azure/azcollection)
- Ansible MySQL [extension](https://galaxy.ansible.com/community/mysql)
# Setup 
## Install Python3 requirements using pip
```user@localhost:~/Project-Endava# pip3 install -r requirements.txt```
## Complete the infrastructure setup
```user@localhost:~/Project-Endava# ansible-playbook playbooks/infrastructure-init.yaml```
## Add the newly created services to your Ansible hosts file
```user@localhost:~/Project-Endava# vim /etc/ansible/hosts```
## Deploy the Python web app
```user@localhost:~/Project-Endava# ansible-playbook playbooks/webapp-setup.yaml```
## Deploy the MySQL DB 
```user@localhost:~/Project-Endava# ansible-playbook playbooks/mysql-setup.yaml```
## Verify by visiting the IP address of your Azure VM:
![Example:](https://imgur.com/a/mWlR40w)
