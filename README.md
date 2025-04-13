HARDENING A WINDOWS 10 PRO SYSTEM FOR SECURITY

 What Is “System Hardening”?

Hardening means reducing the attack surface of your system by:
•	Disabling unnecessary services
•	Applying best security policies
•	Restricting access
•	Enabling monitoring and logging *Remmber the first project

Tools: 
Built-in Windows tools (no installs needed)

You'll Accomplish
•	Apply baseline security configurations
•	Lock down user and administrative privileges
•	Enable and verify system auditing/logging
•	Disable vulnerable services and ports
Lets get started:  
STEP 1: Create a Restore Point (Safety First)
1.	Search "Create a restore point"
2.	Click “Create” under the System Protection tab
3.	Name it Before Hardening and save

![Windows Hardening Guide](https://github.com/user-attachments/assets/1cd6370c-0d67-4a33-bf73-d8206ab758b4)
![Windows Hardening Guide (2)](https://github.com/user-attachments/assets/97c49be0-127e-44bb-a6f5-9f51e389a1e2)
![Windows Hardening Guide (3)](https://github.com/user-attachments/assets/aafb29e0-afc3-4662-b0b5-0afc2e522542)
![Windows Hardening Guide (4)](https://github.com/user-attachments/assets/8f75490a-e2c1-47ee-9492-f0d07f4ac600)

Next we're going to open up the Local Group Policy Editor (Built-in)
Open with:
gpedit.msc
Change Key Settings:
•	Account Lockout Policy
→ Account Lockout Threshold: 5
→ Reset account lockout counter after: 15 minutes
•	Password Policy
→ Minimum length: 12
→ Enforce complexity: Enabled
→ Maximum password age: 60 days
•	Audit Policy (Enable Logging)
o	Audit logon events: Success and Failure
o	Audit object access: Success and Failure
o	Audit process tracking: Success
![Windows Hardening Guide (5)](https://github.com/user-attachments/assets/0d1fc3a0-27dc-4f57-8f20-3ba2f9a098ae)
![Windows Hardening Guide (6)](https://github.com/user-attachments/assets/514cc7f7-ca90-47e7-97b4-c168f4f5a14a)
![Windows Hardening Guide (8)](https://github.com/user-attachments/assets/9a179da4-0a83-4849-b15b-f8a976537d9e)
![Windows Hardening Guide (7)](https://github.com/user-attachments/assets/ba0a518c-9adb-4b38-bf44-ad8a1de90698)
![Windows Hardening Guide (8)](https://github.com/user-attachments/assets/e018d790-0913-4b66-bed8-fec61bec41c8)


Open Services (services.msc) and set these to Disabled or Manual:
Service Name	Status
Remote Registry	Disabled
Windows Remote Management	Manual
Xbox Services	Disabled
Print Spooler (if not needed)	Disabled
Bluetooth (if not used)	Disabled
![Windows Hardening Guide (10)](https://github.com/user-attachments/assets/92fbda62-1afc-45c8-ada0-ebf2bf95ed1b)

Enable & Configure Windows Firewall (~15 min)
Open Windows Security > Firewall & Network Protection
•	Ensure firewall is ON for all profiles
•	Create custom inbound rules:
o	Block all except required services (RDP, SMB, etc.)
o	Disable unnecessary file/printer sharing if unused
![Windows Hardening Guide (11)](https://github.com/user-attachments/assets/4d3e9f0d-b1e2-4aee-b534-688c142cbfef)


Enable Windows Defender & Exploit Protection 
Open Windows Security > Virus & Threat Protection
•	Ensure Real-time protection is ON
•	Go to App & browser control > Exploit protection settings
o	Turn ON settings like:
	Data Execution Prevention (DEP)
	ASLR (Address Space Layout Randomization)
	Control Flow Guard
![Windows Hardening Guide (12)](https://github.com/user-attachments/assets/3c5a177b-4643-4293-87cb-51409aca7489)
![Windows Hardening Guide (13)](https://github.com/user-attachments/assets/e63663c0-5cb5-40b2-b9ad-5670a12c461a)
![Windows Hardening Guide (14)](https://github.com/user-attachments/assets/1225a5d3-d4dc-44e4-b065-67a852c45d5c)
