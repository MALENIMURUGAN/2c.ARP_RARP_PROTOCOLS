# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME: MALENI M
## REGISTER NO: 212223040110
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
CLIENT.PY:
```
import socket 
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

SERVER.PY
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
CLIENT.PY
![image](https://github.com/user-attachments/assets/0fd40b97-a06f-48c5-bdbc-e807ae9f7af4)



SERVER.PY
![image](https://github.com/user-attachments/assets/ef572b5c-4a48-415a-a999-d1805b557fd7)




## PROGRAM - RARP
CLIENT.PY
```
import socket 
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())


```
SERVER.PY
``` 
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
   ip=input("Enter MAC Address: ")
   s.send(ip.encode())
   print("IP Address",s.recv(1024).decode())


```
## OUPUT -RARP
CLIENT.PY

![image](https://github.com/user-attachments/assets/33f760b4-d40f-4036-8fcd-4785962fb4a3)


SERVER.PY

![image](https://github.com/user-attachments/assets/c7715845-61fd-4a9a-b078-1a74a08ddd2d)


## RESULT
Thus, the python program for simulating ARP and RARP protocols using TCP was successfully 
executed.
