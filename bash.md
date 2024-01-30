# Bash introduction - James Pannacciulli

> @ OSCON2014


```bash
type cd
info man
man man

```

## Return Status
```bash
0
1 to 255
$?
```
```bash
while read var1 var1; do
echo $var1 $var2
done
```
```bash
for name in words; do list; done

for(( expr1 ; expr2: expr3; ))


for (( i=0 ; i<4 ; i++ ))
do
echo $i
done
```
## Select
```bash
select name in words; do list; done
```

## Evaluate Expresionss

```bash
[ expression] [[ conditional exp ]]
[[ -n  string ]]
[[ -z  string ]]
[[ string != string ]]
[[ string =~ regex ]]
[[ string == string ]]
[[ -e  string ]]
[[ -d  file ]]
[[ -f  file ]]
[[ -t  string ]]
[[ -n  string ]]
[[ -n  string ]]
```

```bash
if [[ 'a' == 'a' ]]
then
    echo "yes"
else
    echo "nope"
fi
```

## CASE

```bash
case word in
    pattern1);
        list1:;
    patern2 | pattern3);
        list;;
esac
```
```bash
case one in
    o)
    echo "noooo";;
    o*)
    echo "yeeees";;
    *)
    echo "anything else";;    
esac
```
## Group command

> subshell (list)
> groupcommand { list ; } # trailing ; and space for bash parsing
> group command lets you run a command in current shell /w same vars
> groping commands to pipe them 


> $$ PID of ccurrent shell

`echo $(</etc/os-release)`


## Fedirecting; Command and Process Subst

```bash
$(list)
>(list)
<(list)
$*
$@
$-
$$
$!
%?
$_
${12}

```
## Parameter expansion

```bash
# extraction
${param:offset}
${param:offset:lenght}
# removal from left
${param#pattern}
${param##pattern}
# removal from right
${param%pattern}
${param%%pattern}


```

## Indexed && associative array

> indexed [1] => "potato"
> associative 

## arithmetic expansion

> (( math stuff ))

```bash
name++
++name
--name
name--

echo $(( 3+4 ))
# echo the value of eval

```

# Brace exp

```bash
echo {10..55..5}%


```
## Functions

```bash
# use function name and params

words ()
{
for word in "$@";
do
    echo "$word";
done
}
```

## Session Portability

```bash
$(declare -f xxxxx); xxx

```

# Advanced Bash tut YT

```bash
grep -i string filename
# -i for case insensitive

# string manipultaion
man sed
man awk
# cut delimiter filed
cut -d ; -f 4
```
## dot slash is not part of env

```bash
./myscipt.sh
sudo cp ./myscript /usr/bin
```
> echo is output to stind

```bash
a=Hello
b="Hello world!"
echo $a$b
# declaring int
declare -i d=123
declare -r # read-only
declare -l #loweracse
declare -u #uppercase
# built-in
$BASH_VERSION
$MACHTYPE
```

```bash
$0 # scriptname
```

> Storing the value of the command
> into a varabile

```bash
a=$(ping -c 1 8.8.8.8)
a=$(COMMAND)
```

## arithmetic operaions

```bash
d=2
e=$((d+d))
((e++))
echo $e
```
## Comparison operation

> [[ EXPRESSION ]]

> -gt -lt -eq -le -ge -ne

Logical op
* [[ $a && $b ]]
* [[ $a || $b ]]
* [[ ! $a ]]

> [[ -z $a && -n $b ]]

## reading files

```bash
while read f ; do
    echo $f
done < file.txt

```

```bash
#!/bin/bash

[[ -f ./file.txt ]] && touch file.txt

echo "potato">> file.txt
echo "new stuff" >> file.txt
echo "nowhere to be" >> file.txt
echo "rooomba" >>  file.txt
# test
i=1
while read f ; do
    echo "line $i is: $f"
    ((i++))
done < file.txt

cat file.txt
exit 0
```

## here doc

```bash
cat << EndOfTxt
potaoto
motato
roomba
EndOfTxt
```

```bash
# - dash erase leading tabs
cat <<- END
    tomato
END
```

```bash
#!/bin/bash

greentxt="\033[32m"
bold="\033[1m"
normal="\033[0m"
logdate=$(date +"%Y%m%d")
logfile="$logdate"_report.log

echo -e $bold"Quick sys report for: "$greentxt"$HOSTNAME"$normal
printf "\tSystemType:\t%s\n" $MACHTYPE

cat <<- EOF > $logfile
    Report was successfully created!
    Check the report!
EOF

printf "BASH:\t%s\n" $BASH_VERSION >> $logfile
```
---
title:
	- Awesome Bash Commands
---

# Tar

```bash
tar -cvf file1.tar file2.txt	# compress a file
tar -xvf file1.tar						# extract a file
```

# Netcat

```bash
netcat -k -l 9999 >> example_log.txt		# listening server
date | nc 192.168.0.4 9999							# send output of command
nc localhost 4444 < /bin/bash						# 
```

# Nmap

```bash
nmap -sP		# ping
nmap -sT		# 3-way handshake
nmap -sV		# system version
sudo nmap -O 

# nmap scripts
# agressive / non agressive scripts
nmap -sC 192.168.0.22
nmap --script "http-*" 192.168.0.34
nmap --script "(ssh and not brute)"
nmap -A			# not recommanded, agressive
```

```
xz -d someting.img.xz
dd if=smthin.img of=/dev/s bs=4MB status=progress
```
---
title:
	- Awesome Bash Commands
---

# Tar

```bash
tar -cvf file1.tar file2.txt	# compress a file
tar -xvf file1.tar						# extract a file
```

# Netcat

```bash
netcat -k -l 9999 >> example_log.txt		# listening server
date | nc 192.168.0.4 9999							# send output of command
nc localhost 4444 < /bin/bash						# 
```

# Nmap

```bash
nmap -sP		# ping
nmap -sT		# 3-way handshake
nmap -sV		# system version
sudo nmap -O 

# nmap scripts
# agressive / non agressive scripts
nmap -sC 192.168.0.22
nmap --script "http-*" 192.168.0.34
nmap --script "(ssh and not brute)"
nmap -A			# not recommanded, agressive
```

```
xz -d someting.img.xz
dd if=smthin.img of=/dev/s bs=4MB status=progress
```
---
title:
	- Awesome Bash Commands
---

# Tar

```bash
tar -cvf file1.tar file2.txt	# compress a file
tar -xvf file1.tar						# extract a file
```

# Netcat

```bash
netcat -k -l 9999 >> example_log.txt		# listening server
date | nc 192.168.0.4 9999							# send output of command
nc localhost 4444 < /bin/bash						# 
```

# Nmap

```bash
nmap -sP		# ping
nmap -sT		# 3-way handshake
nmap -sV		# system version
sudo nmap -O 

# nmap scripts
# agressive / non agressive scripts
nmap -sC 192.168.0.22
nmap --script "http-*" 192.168.0.34
nmap --script "(ssh and not brute)"
nmap -A			# not recommanded, agressive
```

```
xz -d someting.img.xz
dd if=smthin.img of=/dev/s bs=4MB status=progress
```
