# webuzo-install-ansible
#Ansible Script to Install a webuzo control panel on Almalinux 8
#Author: Sihabul Hasan
#Created on: 22 November 2022

# Run the task using:
```
ansible-playbook main.yaml -i hosts
```


* Install SSL Certificate from Apps > Mange Service Certificate

* The PHP versions have not been started automatically. I tried to start them manually but got an error.
>> When you create a user then the default php version will start automatically.
PHP needs atleast one pool to run the service.  Once you assign php for domains from webuzo admin panel >> multi-php manager then those php will start automatically.


* Immunify360 and Softacullous was not installed automatically. After contacting the webuzo support They have fixed it.
>> Sir we have not added imunify 360 in our installer yet, you need to install it manually.
>> About the softaculous issue we checked on your server and noticed that for some reason it was not able to resolve install.sh file.        
So we installed it manually.

>> Command from the  history:
wget -N https://files.softaculous.com/install.sh
    5  chmod 755 install.sh
    6  ./install.sh
    7  ./install.sh
    8  yum
    9  yum install tmux -y
   10  tmux
   11  ./install.sh
   12  wget -N https://files.webuzo.com/plugins/imunify360/imunify360.sh
   13  chmod +x imunify360.sh
   14  ./imunify360.sh