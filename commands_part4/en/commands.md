# Commands ubuntu part 4


**Networks**

---

## Checking the IP configuration of the network cards
ip a 

## View routing routes
ip route
	
## Network card status handling
ip l set enp1s0 down/up 

> (l-link or connection, card)

> if you disable it, you will not see the IP settings and the status next to the NIC (Network Interface Card) name will be DOWN


---

**Configuring IP settings - NETPLAN**

---

- recorded as YAML (YAML is an IT language designed to present data in a structured way; a descriptive language)

- syntax-sensitive language
> (indentation is not done with tabs but spaces)

- the configuration files can be found in the location /etc/netplan/*.yaml

- we can have the configuration of several NICs in one file

0. We add a second network card to the VM. Both are set as bridged to their currently used network interface on the laptop.

1. We check what files we have in the /etc/netplan directory. By default there is only one - this is where we will configure the IP settings of the network cards.

2. We are interested in the following passage :   

configuration of network cards
ethernets: 

network interface name (to be checked e.g. via ip a)
       
DEVICE_NAME:

whether the IPv4 address will be taken from the dhcp server?
          
Dhcp4: true/false

IP address for network card / netmask
          
Addresses: [IP_ADDRESS/NETMASK].

IP address of the router
          
Gateway4: GATEWAY

DNS servers configuration section
          
Nameservers:

setting IP addresses of DNS servers  
             Addresses: [NAMESERVER_1, NAMESERVER_2].
             
**Exercise - for the first network card, set it to get its IP address from a DHCP server, for the second, assign the address 192.168.1.200/24 (netplan.png)**

	ethernets:

     enp0s3:

        dhcp4: true

     enp0s8:

        dhcp4: false

        addresses: [192.168.1.200/24]

        gateway4: 192.168.1.1

        nameservers:

           addresses: [8.8.8.8,1.1.1.1]

3. Checking the netplan configuration:

netplan try

4. If the above did not return errors apply the settings:

netplan apply

## Change of hostname (hostname is the network name of the host)
hostname (display current name)

change occurs in two places:

/etc/hostname

/etc/hosts

> you have to replace the old name with the new one


## Diagnosis of network communication
ping

1.1.1.1 (by IP address)

facebook.com (after the domain name - here an additional option to check the DNS server, which will first translate the domain name into an IP address, then ping it)
	
> if no ping command is available, install the iputils-ping package

---

**Management of services**

---

## System services are managed using the systemctl tool
systemctl 

enable (start at boot)

disable (do not run on startup)

start (start service now)

stop (stop service now)

restart (restart service)

status (check service status)

reload (reload configuration files, without restarting the service)
	
> systemctl enable --now service_name <- make it start at startup, but also make the service start at this point; enable+start
	
> using the SSH service as an example

> systemctl status ssh

> systemctl restart ssh

---

**SSH server**

---

## Local login
Directly to a virtual machine or physical computer.

## Remote login - SSH
SSH (Secure Shell) - a protocol for remote host management. Successor to the telnet protocol. It is distinguished by the fact that all client-server traffic is encrypted.
By default, it operates on port 22/TCP.

## Software installation
server package: openssh-server

client package: openssh-client

## Connecting to the server
From Windows:
	
Putty program, enter IP address, port, login and password

from Linux:

ssh login@host (ip, or domain name)

ssh -p 1234 technik@1.1.1.1
	
> Before making changes, let's check how the server works on the default settings.

> Let's try locking out the user (usermod -L user), and then log into the user via SSH.
	
> 1. We log in to the user, logout.
	
> 2. We block.
	
> 3. We try to log on to it.
	
> 4. We unblock.
	
> 5. We try to log in again.

## Changing the server configuration
In order for the changes made to the configuration files to take effect, the service in question must be restarted

SSH server configuration file:

/etc/ssh/sshd_config 

**always backup the configuration files before making changes, e.g. cp /etc/ssh/sshd_config /etc/ssh/sshd_config_bckp**.

Change the default port:

Port 22 

Default entry. 

A hashtag at the beginning of a line indicates a comment (the line in question is not taken into account).

We remove the comment and change the port to any port above 1024. Let's set 1234:

Port 1234
	
Disable root login:

#PermitRootLogin prohibit-password

We enable the option, so we delete the comment. We change the argument to no:

PermitRootLogin no
	
Assign user access: (add at the end)

DenyUsers user_name (all others have access except the users specified here)

AllowUsers user1 , user2 (if I give Allow it only allows the users specified in this statement)

**Comma space**
			
Disable banner display

#Banner none

We enable the option, so we delete the comment.

Banner is the information that is displayed when you log into ssh. It contains, among other things, system or kernel versions. When an unauthorised person obtains such information, it will make it easier for them to hack / take over the server.

## Login without password
Up to now we have been using login with username and password.
It is possible to log in using an SSH key (much more secure, as the password can be cracked / stolen).

> We are performing this exercise on Linux systems

On the client we generate the ssh key:

ssh-keygen -t rsa -b 4096 
	
We copy the generated key to the server:

ssh-copy-id username_user_on_server@ip_server

enter the password of the user on the server
	
If you want to log in with different users, you have to copy the ssh key for each one separately.
	
If the server is listening on a port other than the default port, we need to specify the port in the command:

ssh-copy-id -p port_nr user@host
	
In the SSH server configuration file, disable the password login options:
	
#PasswordAuthentication yes
	
PasswordAuthentication no
	
> If we want some users to log in by ssh key and some by password we need to leave the above statement with the yes argument.

---

**BONUS - terminal communicator**

---

We will use a tool called socat for this

## We are starting the server:
socat TCP4-LISTEN:81 STDOUT

> (port any)

## We connect with the client:
socat - TCP4:1.1.1.1:81

> enter IP and PORT of the server

> at this point we can send messages between the two hosts

## Back to part 3
[Click](https://github.com/pokczampDev/Ubuntu-guide/blob/main/commands_part3/en/commands.md)