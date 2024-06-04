---
title : NMAP HANDBOOK
geometry:
    - top=10mm
    - left=10mm
    - right=20mm
    - bottom=10mm
---

# COMPILE FROM SOURCE

```bash
# install dependencies ( open ssl)
svn co https://svn.nmap.org/nmap/
cd nmap
./configure --help
./configure
make
make install 
```


# SIMPLE SCANS

```bash
nmap -h 
man nmap
# version
nmap -V     
# verbose output
nmap -v
nmap -vv <TARGET.IP>
# CIDR notation
nmap 192.168.8.0/24
nmap 192.168.8.5-192.168.8.10
# extract ip in textfile and scan them
# use space tab newline, for delimiter
nmap -iL ip.txt 
# exclude /  ommit hosts
nmap IP --exclude IP
nmap -F IP/24 --excludefile ip.txt
# select interface for scanning
nmap -e <INTERFACE> <TARGET.IP>
nmap -e lo 192.168.0.1
# version 6 IP
nmap -6 <IPv6.TARGET>
# random hosts
nmap -iR 3
nmap --packet-trace IP
```

## ports states

* open
* closed
* filtered
* unfiltered
* open|filtered
* closed|filtered

```bash
# reason for port state 
nmap --reason 192.168.88.5
# show only open ports
nmap --open  192.168.8.1
```

#  MORE BASICS

```bash
# -F 100 ports
nmap -F IP
# specify ports
nmap -p 80,54,23 192.168.8.4
# specify nmap service name
nmap -p msrpc,http,apex-mesh 192.168.7.1
# wildcard port scan
nmap -p "*" 192.168.2.2
nmap -sU -sT -p U:53,T:25 192.168.8.1
# top ports to scan - quantity
nmap --top-port 200 192.168.7.1
# sequential port scan
nmap -r 192.168.4.1
nmap -v -r 192.168.3.1
```

# NETWORK DISCOVERY

```bash
nmap -PN 192.167.4.4
# Ping only with mac of locals
nmap -sP <IP>
# syn ping (when ICMP blocked)
nmap -PS <IP>
# tcp ack
nmap -PA <IP>
# udp ping
nmap -PU <IP>
# sctp - stream control (voip)
nmap -PY <IP>
# ICMP echo
nmap -PE <IP>
# ICMP timestamp
nmap -PP <IP>
# icmp addres mask ping
nmap -PM <IP>
# ip protocol ping
nmap -PO 10.0.2.2
# ARP ping - faster
nmap -PR <IP>
# traceroute
nmap --traceroute <IP>
# reverse dns
nmap -R <IP>
# swift
nmap -N <IP>
# troubleshoot dns - slow
nmap --system-dns <IP>
# manually specify dns server
nmap --dns-server 8.8.8.8,1.1.1.1 <TARGET.IP>
```

# TCP/UDP ACK

```bash
# stealth syn scan 1000 ports
nmap -sS <IP>
# tcp connect scann
nmap -sT <IP>
# UDP
nmap -sU <IP>
# tcp null scan - no flags 
nmap -sN <ip>
# tcp fin scan
nmap -sF <IP>
# X-mas 
nmap -sX <TARGET.IP>
# tcp ack
nmap -sA <IP>
# custom tcp scan
nmap -sS --scanflags SYNFIN -T4 <IP>
# icmp tcp udp ,.. proto
nmap -sO  <IP>
```

```bash
# raw ethernet packets
nmap --send-eth 192.168.8.1
# send IP packets 
nmap --send-ip <IP>
```

# OS && SERVICE DETECTION

```bash
# os discovery
nmap -O <IP>
nmap -v -O <IP>
nmap -O --osscanguess
# service version detection
nmap -sV 
# debuging
nmap -sV --version-trace <IP>
```

# TIMING PARAM  && PARALLELISM 

```bash
nmap -T4s <IP>
nmap -T4m <IP>
nmap -T4h <IP>
# number of paraller scans
nmap --min.parallelism 100 <IP>
nmap --min-hostgroup 20 <IP>
# rtt round trip time
nmap --initial-rtt-timeout 1000ms <IP>
nmap --max-retries 5 <IP>
nmap --ttl 2s <IP>
nmap --host-timeout 1s 192.168.2.1
nmap --scan-delay 10ms <IP>
```

# NAVIGATING FIREWALLS

```bash
# fragment 8,16,32,64,...
nmap --mtu 16 <IP>
# decoy addr
nmap -D  RND:5 <IP>
# idle zombie
nmap -sI <ZOMBIE.IP> <HOST.IP>
nmap --source-port 253 192.168.8.1
# add bytes random
nmap --data-lenght 25 192.168.50.1
# rand
nmap --randomize-hosts <IP>
# spoof MAC
nmap --spoof-mac <MAC> <TATGET.IP>
# send packs with bad checksum
nmap --badsum <IP>
```

# NSE

```bash
nmap -sn --script whois-* <DOMAIN>
nmap --traceroute --script traceroute.geolocation
```
