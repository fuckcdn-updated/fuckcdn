# w8Fuckcdn
> Bypassing the CDN by scanning the entire network to obtain the website IP address

## use
- target.log Configure the scanned IP range
- config.py Set the text to look for, the website domain name, and configure whether to support HTTPS scanning
- run `python2.7 fuckcdn.py` 

## Procedure flow chart
Based on masscan scanning the open port 80 on the IP side, the program automatically connects to each IP test, and filters out the qualified IPs and saves them to result.txt  
The program provides a method of "obtaining IP segments based on scanning subdomains" to reduce the range of IP segments as much as possible 
- updated usage by cheeze: `python2.7 get_ips.py -d target`
- Of course, you can search for relevant domain names yourself, and use `python2.7 get_ips.py -f target.txt --ips` to generate IP segments

## characteristic
1. Support windows/linux
2. gevent coroutine IO maximizes resource utilization
3. masscan scan, the fastest can scan the whole network in 6 minutes
4. HTTPS support
5. Support to adjust the masscan rate (rate)

## Installation Environment - Updated by Cheeze - old codes and method
```sh
git clone https://github.com/fuckcdn-updated/fuckcdn.git && cd fuckcdn && sudo apt -y update && sudo add-apt-repository universe && sudo apt -y install python2.7 && sudo apt -y install curl && curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py && sudo python2 get-pip.py && pip2 install --upgrade pip setuptools wheel && sudo apt-get -y install libxml2-dev libxmlsec1-dev && sudo apt-get -y install python-dev && sudo apt-get -y install libffi-dev && pip2 install gevent dnspython && sudo apt-get -y install libpcap* && chmod +x * && chmod +x bin/linux_64/masscan
```
+ Latest Usages Command:
```sh
python2.7 get_ips.py -d target
```

+ after running get_ips.py then run fuckcdn.py to check the entire cdn:
```sh
python2.7 fuckcdn.py -d target
```

+ to check result see it on:
```sh
vim target.log
```
```sh
cd result
```
```sh
ls
```
+ you should see "www.site.com.log"
```sh
vim www.site.com.log
```
