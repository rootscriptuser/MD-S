```bash

sudo apt install ufw
sudo ufw allow ssh
sudo ufw allow 2040/tcp
sudo ufw allow proto tcp from 103.1.2.3 to 192.168.5.5
sudo ufw allow http
sudo ufw allow https
ufw show added
sudo ufw status
sudo ufw enable

#DEFAULT POLICIES
/etc/default/ufw:

sudo grep -i '^default_' /etc/default/ufw

DEFAULT_INPUT_POLICY="DROP"
DEFAULT_OUTPUT_POLICY="ACCEPT"
DEFAULT_FORWARD_POLICY="DROP"
DEFAULT_APPLICATION_POLICY="SKIP"

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw route allow in on eth1 to 172.0.0.0/24

sudo ufw allow in on lxdbr0 comment 'lxdbr0 for LXD'
sudo ufw route allow in on lxdbr0 comment 'lxdbr0 for LXD'
sudo ufw route allow out on lxdbr0 comment 'lxdbr0 for LXD'

sudo systemctl status ufw.service

sudo ufw status
sudo ufw status verbose
sudo ufw status numbered

# block port 25
sudo ufw deny 25
sudo ufw deny from 192.168.1.0/24

# delete  rules
sudo ufw status numbered
sudo ufw delete 4

# prepend rules
sudo ufw prepend deny from 1.2.3.4
sudo ufw prepend deny from 123.1.2.3/29
sudo ufw prepend allow from 192.168.1.0/24

# APPS
sudo ufw app list
sudo ufw app info {name}
sudo ufw app list
sudo ufw app info 'WWW Cache'
sudo ufw allow from 192.168.0.0/16 to any app {name}

# reports
sudo ufw show listening

```
