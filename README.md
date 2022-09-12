# OpenStack-Tutorial-Operate-Your-Own-Private-Cloud

##

https://www.youtube.com/watch?v=_gWfFEuert8

##

https://raw.githubusercontent.com/RodrigoMvs123/OpenStack-Tutorial-Operate-Your-Own-Private-Cloud/main/README.md

##


##

OpenStack Tutorial – Operate Your Own Private Cloud 

https://www.youtube.com/watch?v=_gWfFEuert8

Open Stack
https://www.openstack.org/

https://openmetal.io/
https://central.openmetal.io/clouds/start

~ ssh-keygen
cd .ssh
ls
vim id_rsa.pub

SSH Key  ( … ) 
My Cloud 
Assets 
Access Details 
SSH Key ( Private Cloud Deployment ) 
ssh - i ~./ssh/id_rsa.pem root@173.231.217.21 ( Password Key ) 
[root@modest-galliform ~]#  grep keystone_admin_password / etc/kolla/passwords.yml
keystone_admin_password: 5d2vpI7BoXauA4azpxZxjD8edOgTwBqV9qAqged
 [root@modest-galliform ~]#

Open Stack
User Name: admin 
Password: 5d2vpI7BoXauA4azpxZxjD8edOgTwBqV9qAqged

Create Project 
Edit Quotas 
Create User 
  
Glence
Open Stack
User Name: beau 
Password: …..

Create Image +
Nova 
Project 
Network 
Networks
Create Network
subnet ( private-subnet ) 
Network Address 192.168.0.1/24 Ip 
Version IPv4

Project 
Network
Router 
Create Router 
Router Name ( Router )
External Network ( External ) 
create router 

router 
Interfaces 
Add Interface 
Subnet
Private: 192.168.0.0/24
submit 

Project 
Network
Network Topology 

Project 
Network
Security Groups 
Create Security Groups 
Name ( SSH ) 
Create Security Groups
Manage Rules
Add Rule
Assets 
Public IP ( 173.231.217.21 )
Rule ( SSH )
Description ( Allows SSH from 173.231.217.21)
Remote ( CIDR )
CIDR ( 173.231.217.21 ) Add
Security Groups 


[root@modest-galliform ~]# ( Hardware Node / admin password) 
[root@modest-galliform ~]# ssh-keygen -b 4096
Generating public/private rsa key pair.
Enter file in which to save the key ( /root/.ssh/id_rsa ):
Overwrite (y/n) ?
y
Enter passphrase ( Empty for no passphrase ): 

[root@modest-galliform ~]# cat /root/ .ssh/id_rsa.pub 
Public Key ( … ) // copy 

Project 
Compute 
Instances 
Launch Instance 
Details
Instance name ( Jumpstation ) 
Source 
Available Name ( CentOS 8 Stream (el8-x86_64) 
Allocated 
Flavor ( m1.small )
Allocated 
Networks ( Private ) 
Allocated 
Security Groups ( SSH ) 
Allocated
Key Pair ( Import Key Pair ) 
Key Pair Name ( jumpstation-key )
Key Type ( SSH Key ) choose file or past 
Import Key Pair
Launch Instance

Project
Compute  
Instances  
Instances

IP
Project 
Network
Floating IPs
Allocate IP To Project
Allocate Floating IP 
Pool ( External ) Allocate IP
Floating IPs / Actions / Associate 
Manage Floating IP Associations 
IP Address ( 173.231.255.46 )
Port to be associated / select a port / Jumpstation 192.168.0.88 
Associate - Mapped Fixed IP Address 
 

[root@modest-galliform ~]#  ssh -i / root/.ssh/id_rsa centos@173.231.255.46
Are you sure you want  to continue connecting ( yes/no [fingerprint]) ? 
[root@modest-galliform ~]#  ssh -i / root/.ssh/id_rsa centos@173.231.255.46
Are you sure you want  to continue connecting ( yes/no [fingerprint]) ? Yes
Enter passphrase for key ‘ /root/ .ssh/id_rsa’: ( … ) 
[centos@jumpstation ~]$ 

OpenStack 
Overview 
API Access 
Download OpenStack RC File 
OpenStack clouds.yaml File 
OpenStack RC File 
[centos@jumpstation ~]$ mkdir -p ~/.config/openstack
[centos@jumpstation ~]$ vi ~/.config/openstack/clouds.yaml [New File]

clouds:
openstack:
auth:
auth_url: https://173.231.217.20:5000
username: “beau”
project_id: 4154c8a4f53d42768687b969c1a41d48
project_name: “Development”
user_domain_name: “Default”
region_name: “iad3”
interface: “public”
identify_api_version:3 
[centos@jumpstation ~]$ vi ~/.config/openstack/clouds.yaml [New File] :wq
[centos@jumpstation ~]$ vi Development-openrc.sh 
“Development-openrc.sh” [New File]
#!/usr/bin/env bash … Copy and Paste 
 [centos@jumpstation ~]$ vi ~/.config/openstack/clouds.yaml [New File] :wq
[centos@jumpstation ~]$ source Development-openrc.sh 
Please enter your Open Stack password for project Development as user beau: ( … ) 
[centos@jumpstation ~]$ /usr/libexec/platform-python -m venv ~/venv
[centos@jumpstation ~]$ source ~/venv/bin/activate
( venv ) [centos@jumpstation ~]$ pip install - - upgrande pip 
( venv ) [centos@jumpstation ~]$ pip install python-openstackclient 
( venv ) [centos@jumpstation ~]$ openstack server list 
( venv ) [centos@jumpstation ~]$ openstack
( openstack ) server list 
( openstack ) exit 
( venv ) [centos@jumpstation ~]$ openstack - - help
( venv ) [centos@jumpstation ~]$ openstack help server
( venv ) [centos@jumpstation ~]$ openstack server list 
( venv ) [centos@jumpstation ~]$ openstack server show jumpstation 

https://ceph.io/en/
[root@modest-galliform ~]# status 
[root@modest-galliform ~]# ceph df
[root@modest-galliform ~]# grep keystone _admin_password /etc/kolla/passwords.yml
keystone_adim_password: 52dvpI7BoXauA4ayzpxZxjD8edOgTwBqV9qAqged
[root@modest-galliform ~]# 

https://www.openstack.org/passport/
admin 
compute 
Hypervisors 
Hypervisors Summary 
Admin 
Compute 
Instances 
[root@modest-galliform ~]# ceph -s
[root@modest-galliform ~]# ceph df
[root@modest-galliform ~]# ceph health detail
[root@modest-galliform ~]# ceph osd pool ls
[root@modest-galliform ~]# ceph osd pool images











