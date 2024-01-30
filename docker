```
sudo docker network ls
sudo docker network rm network_name
sudo docker run -it /bin/bash --name ubuntu rm ubuntu
sudo docker pull ubuntu
sudo docker ps
sudo docker inspect transmission
sudo docker create --diver=macvlan --subnet=192.168.8.6/24 -- gateway 192.168.8.1 -o parent=eth0 -o macvlan_mode=bride macvlan
sudo docker compose up -d
```
# Docker Networks

TYPES:
* HOST
* BRIDGE
* MACVLAN
* IPVLAN

## Default network - Bridge network
* docker0 , dhcp server in subne 172.
* host ip
* ip might change 
* cant nameresolve !!
* netshoot

```
ip a | grep docker0
docker network ls
docker network create customname

docker inspect portainer | less

docker run -it /bin/sh  --name custom_name --network custom_network --rm
```

## host network type

* removes isolation
* use same route tables
* app connected directly to other hosts/services
* like default service on host !!
* no more isolation layer 
```
docker run nginx --rm -d -name nginx --network host nginx

```

## mac-clan && ip-vlan

* separate IP
* diffenrent diver
* still uses own DHCP server and makes a conflicting IP
* specify parent IP addri == physical interface of docker host
* mac vlan and ip vlan differences, IP only at asigns one mac to all containers
* macvlan asings different mac to every container
```
docker create network -d macvlan --subnet 192.168.8.0./24 --gateway 192.168.8.1 --ip-range -o parent=esn18 custommacClan
# in docker run specify -ip for static ip , even if out of subnet

```
