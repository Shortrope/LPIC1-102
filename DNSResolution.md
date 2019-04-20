# DNS Resolution
## /etc/hosts
    127.0.0.1       localhost localhost.localdomain
    ::1       localhost localhost.localdomain

## /etc/hostname
Contains the hostname

## /etc/resolv.conf
Contains DNS addresses

## /etc/nsswitch.conf
contains list of db's that contain a service  
and the files and sources to query  
in order

## bind-utils
    yum bind-utils

### host
resolves domain names to IP addresses

    host localhost
    host google.com 

### dig
Used to query DNS servers for specific types of DNS records

    dig google.com
    dig @8.8.8.8 google.com         # query specific DNS server
    dig -t MX google.com            # query for mail servers
    dig @8.8.8.8 -t A google.com
    dig @8.8.8.8 -t  any google.com

### getent
Directly queries /etc/nsswitch and its db locations for info

    getent hosts