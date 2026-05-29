# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 5000
s.bind((host, port))
s.listen(5)
print("ARP Server Ready...")
arp_table = { "192.168.1.1": "AA:BB:CC:DD:EE:01","192.168.1.2": "AA:BB:CC:DD:EE:02","192.168.1.3": "AA:BB:CC:DD:EE:03"}
c, addr = s.accept()
print("Connection from:", addr)
ip = c.recv(1024).decode()
mac = arp_table.get(ip, "MAC Address Not Found")
c.send(mac.encode())
c.close()


import socket
s = socket.socket()
host = socket.gethostname()
port = 5000
s.connect((host, port))
ip = input("Enter IP address: ")
s.send(ip.encode())
mac = s.recv(1024).decode()
print("MAC Address is:", mac)
s.close()

```
## OUPUT -ARP
<img width="1920" height="1080" alt="Screenshot 2026-05-19 143143" src="https://github.com/user-attachments/assets/5535a0a5-0f7e-44de-a4e3-345994b99fd2" />
## RESULT

Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
