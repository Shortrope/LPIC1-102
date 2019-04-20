# Network Manager

## Device Naming
    en = ethernet
    wl = wireless

    eno1        # o     onboard device
    ens1        # s     device in PCI Express hotplug slots. Index provided by BIOS
    enp2s0      # p s   devices in specific physical locations. p = bus, s = slot

    eth0        # Older traditional naming


## nmcli
Utility for configuring network devices and connection settings  


## nmcli dev
Device:  Network hardware  

    nmcli dev show
    nmcli dev status

## nmcli con
Connection:  Configuration of the device

    nmcli con show
    nmcli con down "Wired connection 1"
    nmcli dev status
    nmcli con up "Wired connection 1"

    nmcli con delete "Wired connection 1"
    nmcli dev status

    nmcli con add con-name "backup" type ethernet ip4 192.168.122.75/24 gw4 192.168.122.1 ifname ens11 autoconnect
    nmcli con show backup

    nmcli con mod backup ipv4.dns "192.168.122.1"
    nmcli -f ipv4.dns con show backup

    nmcli con edit      # prompts for each option

## ip

    ip addr show
    ip addr add 192.168.122.76/24 dev ens11
    ip addr del 192.168.122.75/24 dev ens11

    ip link set ens11 down
    ip link set ens11 up 

    ip route show
    ip route add default via 192.168.122.2 dev eth1
    ip route del default via 192.168.122.2 dev eth1
     
    ip -s addr          # show statistics

## hostnamectl

    hostname            # display the host name
    hostnamectl set-hostname server1

## Legacy Networking Tools
Part of net-tools package

    yum install net-tools

### ifconfig
    ifconfig
    ifconfig eth0 192.168.122.250
    ifdown eth0
    ifup eth0

### route
    route del default
    route add default gw 192.168.122.1
    route add -net 192.168.10.0 netmask 255.255.255.0 gw 192.168.122.25

## Testing Connectivity

### ping, ping6
    ping 192.168.122.33
    ping -c 4 192.168.122.1
    ping -6 -c 3 ::1

### traceroute, traceroute6
    traceroute 192.168.122.1
    !N      # network unreachable
    traceroute -T google.com        # use tcp (80). some firewalls block icmp
    traceroute -6 ::1
    traceroute6 ::1

### tracepath
Replacement for traceroute  
Uses udp.  Some hops will not allow udp scan.  
Does not require elevated privaledges  

    tracepath 192.168.122.1
    tracepath6 ::1

### netstat
Depricated

    netstat             # lists all connections
    netstat -tl         # list tcp listening ports
    netstat -ul         # list udp listening ports
    netstat -tlp        # -p  show proccess id associated w the listening port

    netstat -r          # -r show routing table

### ss
Socket Statistics  
Modern netstat

    ss
    ss -tl         # list tcp listening ports

