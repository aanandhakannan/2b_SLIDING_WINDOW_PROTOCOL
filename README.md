# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

Name: AANANDHA KANNAN S

Reg No: 212224040003

## AIM
Ro write a python program to perform stop and wait protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
Server.py
~~~
import socket

s = socket.socket()
s.bind(('localhost', 6000))   
s.listen(5)
c, addr = s.accept()

size = int(input("Enter number of frames to send : "))
l = list(range(size))
w = int(input("Enter Window Size : "))

st = 0
i = 0
while True:
    while i < len(l):
        st += w
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print("Received ACK:", ack)
            i += w
~~~

Client.py
~~~
import socket

c = socket.socket()
c.connect(('localhost', 6000)) 

while True:
    data = c.recv(1024).decode()
    if not data:
        break
    print("Received frames:", data)
    ack = input("Enter ACK to send back: ")
    c.send(ack.encode())
~~~

## OUPUT
<img width="1040" height="402" alt="Screenshot 2025-09-16 094629" src="https://github.com/user-attachments/assets/b8920d19-b552-45a1-8de6-468f475dd03f" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
