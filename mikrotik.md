```
sudo dnsmasq -i enp0s25 -u mint --log-dhcp --bootp-dynamic --dhcp-range=192.168.1.2,192.168.1.20 -d -p0 -K --dhcp-boot=rb.elf --enable-tftp --tftp-root=/home/mint/tftp
systemctl status isc-dhcp-server
sudo vim /etc/dhcp/dhcpd.conf 



default-lease-time 600;
max-lease-time 7200;

subnet 192.168.88.0 netmask 255.255.255.0 {
  range 192.168.88.1 192.168.88.3;
}
sudo ip add add 192.168.88.2/24 dev enp0s25
```


```
tcpdump -i wlo1
nmap 192.168.88.0/24 -sP
sudo ./netinstall-cli -e -b -i enp0s25 -a 192.168.88.3 ./tftp/ros.npk ./wireless-mipsbe.npk
scp -P 2222 LOCALFILE root@192.168.1.1:/tmp
sysupgrade -n

```
