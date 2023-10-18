# webuzo-install-ansible
#Ansible Script to Install a webuzo control panel on Almalinux 8
#Author: Sihabul Hasan
#Created on: 22 November 2022

# Run the task using: (Development)
```
ansible-playbook main.yaml -i hosts
```

# For production server:
```
ansible-playbook production.yaml -i hosts
```


## After the installation is complete, run:
```
yum reinstall -y lvemanager lve-utils alt-python27-cllib cagefs
wget -N https://files.webuzo.com/plugins/cloudlinux/cloudlinux.sh
chmod +x cloudlinux.sh
./cloudlinux.sh
```


* Install SSL Certificate for Hostname: Apps > Mange Service Certificate

Set Default PHP Version from Apps > Default Apps

* To enable cggroupv2 follow the guide: https://webuzo.com/docs/how-tos/how-to-enable-cgroups-v2/  #It is needed to use resource limit without cloudlinux

* The PHP versions have not been started automatically. I tried to start them manually but got an error.
>> When you create a user then the default php version will start automatically.
PHP needs atleast one pool to run the service.  Once you assign php for domains from webuzo admin panel >> multi-php manager then those php will start automatically.


* Immunify360 and Softacullous was not installed automatically. After contacting the webuzo support They have fixed it.
>> Sir we have not added imunify 360 in our installer yet, you need to install it manually.
>> About the softaculous issue we checked on your server and noticed that for some reason it was not able to resolve install.sh file.        
So we installed it manually.

* Using this script Immunify and Softaculous aren't installed automatically. So we need to install these manually. After contacing Weubuzo support I coppied the following commands from server history to install these.

>> Command from the  history:
Install Softaculous:
wget -N https://files.softaculous.com/install.sh
    5  chmod 755 install.sh
    6  ./install.sh

    Istall tumux # tumux is used for opening multiple tabs in terminal
    9  yum install tmux -y
   10  tmux

Install Immunify 360
   12  wget -N https://files.webuzo.com/plugins/imunify360/imunify360.sh
   13  chmod +x imunify360.sh
   14  ./imunify360.sh



* After installtion if you want to change the port, Run the commands below:
   sed -i -e 's/#Port 22/Port 1157/g' /etc/ssh/sshd_config
   iptables -I INPUT -p tcp -m tcp --dport 1157 -j ACCEPT
   firewall-cmd --add-port=1157/tcp --permanent
   service sshd restart
