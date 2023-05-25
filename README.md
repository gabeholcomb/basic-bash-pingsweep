#!/bin/bash

# Specify the network prefix as a command line argument
network=$1

# Perform a ping sweep
for host in {1..254}; do
    ip=$network.$host
    ping -c 1 $ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
done

#to run in terminal save the file as a .sh then when in your terminal run the command below
./nameofyourfile.sh yournetworkaddress i.e. 192.168.1 assumming you have a /24 network with a subnetmask of 255.255.255.0
