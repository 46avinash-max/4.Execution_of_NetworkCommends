# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## PROGRAM
## SERVER
~~~
server.py
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
~~~
## CLIENT
~~~
client.py
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
~~~

## Output
## SERVER
<img width="1326" height="279" alt="4server" src="https://github.com/user-attachments/assets/66eb89d3-ecb1-4d32-9098-b8fb9f9cabde" />
## CLIENT

<img width="1312" height="197" alt="client" src="https://github.com/user-attachments/assets/1251120b-523a-4549-be0f-506b0d7699ae" />
## TRACEROUTE

<img width="1920" height="1080" alt="TRACERT" src="https://github.com/user-attachments/assets/2c80bfdf-1baf-46ec-a820-54ffa721d780" />

## IPCONFIG

<img width="1920" height="1080" alt="IPCONFIG" src="https://github.com/user-attachments/assets/9d4308b0-e8a1-44bb-8bd0-3a4bad5d6fed" />

## NSLOOKUP
<img width="1920" height="1080" alt="NSLOOKUP" src="https://github.com/user-attachments/assets/a53e185b-e864-482c-ae37-985962b5bd39" />
## NETSTAT

<img width="1920" height="1080" alt="NETSTAT (2)" src="https://github.com/user-attachments/assets/fdba119c-a4e0-4dc3-b037-e46a869be3d6" />
## TCPDUMP
![TCP DUMP](https://github.com/user-attachments/assets/21874f55-a031-427b-a342-533f545652c6)






## Result
Thus Execution of Network commands Performed 
