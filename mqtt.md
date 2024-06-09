Setup MQTT Portal


# Setup Docker Rootles and configure yaml
```bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker $USER
sudo mkdir -p /opt/mqtt
cd /opt/mqtt
sudo vim compose.yaml
```

```yaml
services:
  mosquitto:
    image: eclipse-mosquitto
    container_name: mosquitto
    volumes:
      - ./config:/mosquitto/config
      - ./data:/mosquitto/data
      - ./log:/mosquitto/log
    ports:
      - 1883:1883
      - 9001:9001 # websocket
    restart: unless-stopped
    stdin_open: true 
    tty: true
```

# Configure Mosquitto

```bash
mkdir ./config
sudo nano ./config/mosquitto.conf
```

```
listener 1883
listener 9001
protocol websockets
persistence true
persistence_file mosquitto.db
persistence_location /mosquitto/data/
# log_dest file /mosquitto/log/mosquitto.log

#Authentication
allow_anonymous false
password_file /mosquitto/config/pwfile
#ADD LOGGING
```
# Setup Mosquitto pass
```bash
sudo touch ./config/pwfile
sudo chmod 0700 ./config/pwfile
docker compose up -d
docker compose exec mosquitto sh
mosquitto_passwd -c /mosquitto/config/pwfile <USERNAME>
exit
docker compose restart mosquitto
```

### Let us start Publising to that topic

```bash

# Without authentication
mosquitto_pub -t 'hello/topic' -m 'hello MQTT'

# With authentication
mosquitto_pub -t 'hello/topic' -m 'hello MQTT' -u user1 -P <password>

# Alternate way in url format 
# Format => mqtt(s)://[username[:password]@]host[:port]/topic
mosquitto_pub -L mqtt://user1:abc123@localhost/test/topic -m 'hello MQTT'

```
## You can find C/C++ code for mosquitto client
Check [main.cpp](main.cpp) for the mosquitto client code.

## You can also install a nice MQTT Web Client
Read more about it here => https://mqttx.app/  

```bash
sudo docker run -d --name mqttx-web -p 80:80 emqx/mqttx-web
```

```bash
#https://manpages.debian.org/testing/systemd/systemd.service.5.en.html
ExecStart =mosquitto_sub -v -t "topic/name" >> mylog.mqtt 
#and enable it with e.g. 
sudo systemctl enable path/to/mylogmqtt.service
```

# Additional commands

```
docker pull eclipse-mosquitto
docker run -it --entrypoint /bin/sh eclipse-mosquitto
``
