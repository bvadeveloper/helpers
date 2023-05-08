# linux

    whoami
    uname -a - linux version 
    pwd - current root directory
    ls -la - show all files and dirs
    locate bash - show all bash places

    passwd - change password
    sudo su
    su john - switch to user John 

    man ls

    chmod +x or chmod 777 file.txt

    ifconfig - network settings
    iwconfig - is similar to ifconfig, but is dedicated to wireless networking interfaces
    arp -a - show MAC address
    netstat -ano - shows open connections 
    route - shows route table
    ip n - arp table
    
    nc -nvlp 7777 - open and listen input connection on the port 7777

    cat ip.txt | grep “something” | cut -d “ “ -f 4 | tr -d “:” - get the 4th world in string
