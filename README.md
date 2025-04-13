# Real-Time Network Scanning Detection on Windows Using Open-Source Tools
Detect and respond to suspicious network scans (like Nmap or ping sweeps) on local machine using native Windows tools + open-source utilities.

Tools Utilized: 
Wireshark	Packet | Capture and analysis of packets
Npcap	| Required for packet capture on Windows
Nmap	| Simulate port scans (attacker side)
PowerShell | Logging, scripting, basic automation

Platform: Windows OS

#Introduction
First thing, you’re going to want to do for this project is we're going to want to adjust our environment by first ensuring that we download all the proper tools we'll be using.  In this project we'll be using Wireshark to capture and analyze our packets we'll be using the Npcap whic will be using for packet capture and Nmap to simulate port scan or attacker side.  So we'll be simulating an attack or some type of disruption in a network and then we'll be using PowerShell because we're going to go ahead and we're going to script an alert as well.  


#1. Install Tools
Wireshark is a free tool that helps you see exactly what's happening on a computer network. Think of it like a magnifying glass for your internet traffic—it captures and shows the data being sent and received in real time. This makes it super useful for people who manage networks, work in cybersecurity, or develop software. Even though it supports hundreds of different network types and can handle complex traffic, Wireshark has a user-friendly interface that makes it easier to understand what’s going on. You can use it to find problems, spot unusual activity, or just learn how networks work. Plus, it runs on Windows, Mac, and Linux, so it works on most computers.

![Screenshot (178)](https://github.com/user-attachments/assets/ea4b2c46-8320-4438-be72-d313cd4a5099)
#Note: when you are downloading Wireshark remeber to check and also download Npcap (FORGOT IMAGE)

Npcap is a small but important piece of software that works with tools like Wireshark to capture network data on a Windows computer. It runs in the background and gives these tools access to the raw network traffic—kind of like opening a window to watch all the information going in and out of your computer. Npcap is designed to be fast, secure, and compatible with modern versions of Windows. It replaces an older tool called WinPcap and is now the recommended option because it offers better performance, more features, and stronger security.

Nmap (short for Network Mapper) is a free and open-source tool used to discover devices and services on a computer network. It's often used by IT professionals and cybersecurity experts to see what computers, servers, or other devices are connected to a network, what ports are open, and what services are running. You can think of Nmap as a kind of digital scanner—it helps you "map out" everything on a network.

Even though it runs in a command-line interface, it's very powerful and can do things like:

Find live devices on a network
Identify operating systems and software versions
Detect security risks or unusual behavior
Run advanced scans for deeper analysis

![Screenshot (168)](https://github.com/user-attachments/assets/fbe80f87-7244-43df-83f6-f14b12df2661)

Now that all the tools are installed lets gets started on captureing traffic:
![Screenshot (169)](https://github.com/user-attachments/assets/c395d7ed-ca75-4352-8f1b-a04a7d509bd0)

First well open up Wireshark and you will notice all of your Network connectors will display for mine I am using my local. You may have various traffic you will notice the sytoloic line or a rythma line letting you know there is traffic to look at.  
1.	Open Wireshark
2.	Select your active network interface
3.	Start capturing traffic
4.	Filter using:
5.	tcp.flags.syn == 1 and tcp.flags.ack == 0

Now to simulate something cuasing a potential issue or attacker.  
In Command Prompt (not PowerShell well get to that later), run:
nmap -sS -p 1-1000 127.0.0.1
This performs a stealthy SYN scan on your system.
Back in Wireshark, you’ll now see a burst of SYN packets in your capture.


![Screenshot (172)](https://github.com/user-attachments/assets/143974c4-2996-48a7-b854-7b675f56c226)








![Screenshot (170)](https://github.com/user-attachments/assets/be82a047-5a04-49b5-a30a-9a702eed0204)

Analyze Patterns 
Look for:
•	Repeated SYN packets
•	Empty payloads
•	Unusual port targets

Now that we found the problem let solve with a solution with just a local powershell basic but effective !!!

Write a script to detect spikes in TCP SYN packets:
# syn_alert.ps1
$timestamp = Get-Date -Format "yyyy-MM-dd_HH-mm-ss"
$logPath = "$env:USERPROFILE\Desktop\scan_log_$timestamp.txt"

netstat -an | findstr SYN >> $logPath

Write-Output "SYN connections logged to $logPath"

#Note I'll give you the code this time this took a minute still learning.  

![Screenshot (177)](https://github.com/user-attachments/assets/b99eec54-2055-4277-a423-16a2237b6b99)

There you have it folks. Designed and executed a local network intrusion detection project on Windows 10 Pro using Wireshark and Nmap. Simulated TCP SYN scan attacks and captured malicious traffic patterns without VMs. Developed a basic PowerShell-based SYN logging tool for real-time detection.






![Screenshot (176)](https://github.com/user-attachments/assets/5e9b35d3-7175-41ae-8cba-82ab494f8a37)
