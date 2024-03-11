# base apt stuff

```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install tmux uidmap  git -y
```

# setup .vimrc && .bashrc
```bash
touch .vimrc
echo "set rnu" >> .vimrc
echo "set cursorline" >> .vimrc
echo "set tabstop=2" >> .vimrc
source .vimrc

echo "set -o vi" >> .bashrc
```


# setup docker

```bash
curl https://get.docker.com/ >> install_docker.sh
sudo install_docker.sh

cd /usr/bin/
dockerd-rootless-setuptool.sh install
cd ~

mkdir transmission
cd transmission
curl
```
