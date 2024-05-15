#!/bin/bash

#COLORS
RED='\033[0;31m'
NC='\033[0m' # No Color
#printf "I ${RED}red${NC no color ."}

# usage

usage() { echo "Usage: $0 [-s <45|90>] [-p <string>]" 1>&2; exit 1; }

while getopts ":s:p:" o; do
    case "${o}" in
        s)
            s=${OPTARG}
            ((s == 45 || s == 90)) || usage
            ;;
        p)
            p=${OPTARG}
            ;;
        *)
            usage
            ;;
esac
done

shift $((OPTIND-1))

if [ -z "${s}" ] || [ -z "${p}" ]; then
    usage
fi

echo "s = ${s}"
echo "p = ${p}"

# menu

# update and upgrade sys
sudo apt update -y  1>/dev/null
sudo apt upgrade -y 1>/dev/null
sudo apt autoremove -y 1>/dev/null


# install base terminal stuff
pkg={tmux
net-tools
git
tcpdump
ncat
nmap
}


# install heavy terminal stuff

# install gui stuff

gui_pkg="terminator
thonny
qutebrowser
"

# setup keyboard swap

# setup vimrc

# setup bash rc
# setup arkenfox
curl https://raw.githubusercontent.com/arkenfox/user.js/master/updater.sh >> updater.sh
curl https://raw.githubusercontent.com/arkenfox/user.js/master/user.js >> user.js
echo " move user.js to firefox user folder and run updater"
