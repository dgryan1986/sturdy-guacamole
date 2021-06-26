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
