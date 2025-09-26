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
Client
```
  import socket

s=socket.socket()

s.bind(('localhost',8000))

s.listen(5)

c,addr=s.accept()

address={"10.255.144.126":"98-BD-80-D9-83-4D","10.136.126.196":"98-BD-80-DD-50-C2"};

while True:

      ip=c.recv(1024).decode()
      
      try:
      
          c.send(address[ip].encode())
          
      except KeyError:
      
          c.send("Not Found".encode())
```
Server
```
  import socket

s=socket.socket()

s.connect(('localhost',8000))

while True:

  ip=input("Enter logical Address : ")

  s.send(ip.encode())

  print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
Client

  <img width="571" height="79" alt="image" src="https://github.com/user-attachments/assets/f9fdd48d-86c5-4958-ab51-8b3b0356db76" />
  
 Server

  <img width="906" height="118" alt="image" src="https://github.com/user-attachments/assets/3eeb1924-e720-4208-bdcb-ad954128be3f" />

## PROGRAM - RARP
Client
```
import socket

s=socket.socket()

s.bind(('localhost',8080))

s.listen(5)

c,addr=s.accept()

address={"98-BD-80-D9-83-4D":"10.255.144.126","98-BD-80-DD-50-C2":"10.136.126.196"};

while True:

      ip=c.recv(1024).decode()
      
      try:
      
          c.send(address[ip].encode())
          
      except KeyError:
      
          c.send("Not Found".encode())
```
Server
```
import socket

s=socket.socket()

s.connect(('localhost',8080))

while True:

  ip=input("Enter MAC Address : ")

  s.send(ip.encode())

  print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP

Client

  <img width="602" height="87" alt="image" src="https://github.com/user-attachments/assets/d7db958d-b2ed-40d3-bbad-edbe8827db0b" />

Server
   
   <img width="642" height="156" alt="image" src="https://github.com/user-attachments/assets/f5025294-c437-41e3-951b-dda85eb4647b" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
