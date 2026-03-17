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

## client 
~~~
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping ")
    s.send(ip.encode())
    print(s.recv(1024).decode())
~~~
## server
~~~

import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

c, addr = s.accept()

while True:
    try:
        hostname = c.recv(1024).decode()
        if not hostname:
            break
        result = ping(hostname, verbose=False)
        c.send(str(result).encode())
    except Exception:
        c.send("Not Found".encode())

c.close()
s.close()
~~~
## Tranceroute command
~~~
from scapy.all import *

target = ["www.google.com"]
result, unans = traceroute(target, maxttl=32)
print(result, unans)
~~~

## Output
##client
<img width="751" height="51" alt="Screenshot 2026-03-17 201157" src="https://github.com/user-attachments/assets/2ab3008e-9942-413f-afe7-2609bfffb5bb" />
##server

<img width="835" height="262" alt="Screenshot 2026-03-17 201218" src="https://github.com/user-attachments/assets/55d1ee71-11cf-4ed7-87de-195b893757d8" />
##tranceroute
<img width="808" height="516" alt="Screenshot 2026-03-17 201243" src="https://github.com/user-attachments/assets/b077d96a-0f1a-49fa-943d-1000feb4441d" />


## Result
Thus Execution of Network commands Performed 
