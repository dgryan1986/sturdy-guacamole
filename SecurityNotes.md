# sturdy-guacamole
Tools &amp; Notes I like or need for System Security and/or Hacking

I will organize this better later on but for now it's just thoughts which will be later organized:

Use NTFS | Alternate Data Streams to cover tracks once you have gained access and are finished - a few ways: 

Using Admininstrator - Powershell 
//This is gathering all the Entries Log for us to view what we did/or changed. Which we will then Delete, respectively.
> Get-EventLog -LogName * <br>
> Get-EventLog -LogName * | ForEach { Clear-EventLog $_.log } 

//NOw if we need to view the System Audit Policy we can do that below and then clear it: 
> auditpol /get /category:* <br>
> auditpol /clear /y

