# 1. Introduction
In this repo I will be creating a VLAN network using Cisco Packet tracer in this and will show and explain
the steps one by one.


# 2. Implementation 
I will assume that you already drag and dropped the devices and created links between them.  

## 3.DHCP Configuration
### 3.1 Configure the servers
You probably noticed the computer in the pdf file doesn't have any ip address the truth is that we are running
two DHCP servers EISC and INFO and these two servers will automatically assign ip addresses given a certain pool.

But those servers have to get fixed ip addresses to pick from the EISC will get the ip address `192.168.10.200`
and network mask `255.255.255.0` and INFO is `192.168.20.200` and network mask is `255.255.255.0`.

Do to that follow the following steps : 
1. Click on the server
2. Go to desktop than ip configuration
3. Pick Static and fill the information you need (Ip Address and Network Mask)
### 3.2 Configure the router
The most important element while configuring DHCP is configuring the rooter because he is the one that is going
to propagate the address. to do so follow these steps :
1. Click on the router
2. Go to CLI
3. Write enable than conf t
4. Write the and write the following command lines
```
when you see this // that means a comment not smth to add to the COMMAND 

ip dhcp pool 20 // the 20 is the dhcp pool name 
network 192.168.20.0 255.255.255.0 // the network address 
default-router 192.168.20.254 // the default gateway addresss
ip dhcp pool 10 
network 192.168.10.0 255.255.255.0
default-router 192.168.10.254

```
## VLAN Configuration
the vlan configuration is going to be one of the longest one to, but it's not the hardest because you will repeat 
the same command, before that you have to keep in mind one rule links between the hosts and the switch are called access
ports and the links between switches are trunked

Trunk mode configuration
```
interface <INTERFACE-NAME>
switchport trunk native vlan <PORT>
switchport trunk allowed vlan <VLAN-NUMBER>,<VLAN-NUMBER> ...
switchport mode trunk 
```
Access mode configuration
```
interface <INTERFACE-NAME>    
switchport access vlan <VLAN-NUMBER>
switchport mode access
```


