# sample-cisco-commands
To set up static routing, use the ip route command followed by the destination network, subnet mask, and next-hop address or exit interface. For example: ip route 192.168.2.0 255.255.255.0 192.168.1.2 or ip route 192.168.2.0 255.255.255.0 Serial0/0/0.

To add a neighbor, use the router eigrp command followed by the autonomous system number to enter router configuration mode for EIGRP.

Use the network command followed by the network address and wildcard mask to specify the networks to be advertised by EIGRP. For example: network 192.168.1.0 0.0.0.255.

Use the neighbor command followed by the neighbor’s IP address and the interface on which the neighbor is connected to add the neighbor to EIGRP. For example: neighbor 192.168.1.2 Serial0/0/0.

============================================================

Enable access security for the router’s admin environment:

Connect to the router using a console cable and open a terminal program to access the router’s command line interface (CLI).
Enter global configuration mode by typing enable and then configure terminal.
Use the line vty 0 4 command to enter line configuration mode for the virtual terminal lines.
Use the login local command to require local authentication for remote access.
Use the transport input ssh command to allow only SSH connections to the router.
Use the exit command to return to global configuration mode.
Use the crypto key generate rsa command to generate an RSA key pair for SSH authentication.
Use the ip ssh version 2 command to enable SSH version 2.
Configure an Encrypted password for the router:

In global configuration mode, use the enable secret command followed by the desired password. For example: enable secret mypassword.
Create a routing scheme to route traffic from one designated network to another. Set up static routing, and also add a neighbor:

In global configuration mode, use the ip route command followed by the destination network, subnet mask, and next-hop address or exit interface. For example: ip route 192.168.2.0 255.255.255.0 192.168.1.2 or ip route 192.168.2.0 255.255.255.0 Serial0/0/0.
Use the router eigrp command followed by the autonomous system number to enter router configuration mode for EIGRP.
Use the network command followed by the network address and wildcard mask to specify the networks to be advertised by EIGRP. For example: network 192.168.1.0 0.0.0.255.
Use the neighbor command followed by the neighbor’s IP address and the interface on which the neighbor is connected to add the neighbor to EIGRP.
Configure a router to implement specified traffic control measures:

In global configuration mode, use the class-map command followed by the desired class name to create a traffic class.
Use the match command followed by the desired match criteria to specify the traffic to be matched by the class.
Use the exit command to return to global configuration mode.
Use the policy-map command followed by the desired policy name to create a traffic policy.
Use the class command followed by the class name to enter policy-map class configuration mode for the specified traffic class.
Use action commands such as bandwidth, police, or priority to specify actions for traffic that matches this class.
Use the exit command twice to return to global configuration mode.
Use the interface command followed by an interface name or type/number combination (e.g., GigabitEthernet0/1) to enter interface configuration mode.
Use service-policy input or service-policy output commands followed by policy-map name.
Configure an enterprise router to log network system events for incident response auditing:

In global configuration mode, use logging commands such as logging buffered or logging host commands.



























































































































































































































































































Python 3:

import os

network = input("Enter the network address: ")
os.system(f"nmap -sn {network}")


Powershell 7:

$network = Read-Host "Enter the network address"
nmap -sn $network


Bash:

read -p "Enter the network address: " network
nmap -sC -sV -T4 $network



======

import socket

ip = input("Enter the IP address: ")
try:
    hostname = socket.gethostbyaddr(ip)[0]
    print(f"The hostname for {ip} is {hostname}")
except socket.herror:
    print(f"No reverse DNS record found for {ip}")



read -p "Enter the IP address: " ip
hostname=$(dig -x $ip +short)
if [ -z "$hostname" ]; then
    echo "No reverse DNS record found for $ip"
else
    echo "The hostname for $ip is $hostname"
fi




#!/usr/bin/ruby

Get the IP address from the user
print "Enter the IP address to scan: "
ip_address = gets.chomp

Run the nmap scan
output = `nmap -sV #{ip_address}`

Print the results
puts output
