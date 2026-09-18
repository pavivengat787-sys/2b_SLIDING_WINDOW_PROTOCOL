# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
SERVER PROGRAM:

import socket 
s = socket.socket() 
s.bind(('localhost', 8000)) 
s.listen(1) 

print("Waiting for connection...") 
conn, addr = s.accept() 
print("Connected to", addr) 
while True:
     data = conn.recv(1024).decode() 
     if not data: 
         break 
     print("Frames received:", data) 
     ack = "ACK for " + data
     conn.send(ack.encode())
conn.close()

CLIENT PROGRAM:
import socket 
s = socket.socket() 
s.connect(('localhost', 8000)) 
n = int(input("Enter number of frames: ")) 
w = int(input("Enter window size: ")) 
frames = list(range(1, n+1)) 
i = 0 
while i < n: 
    send_frames = frames[i:i+w]
    msg = " ".join(map(str, send_frames)) 
    print("Sending frames:", msg) 

    s.send(msg.encode()) 

    ack = s.recv(1024).decode() 
    print("Received:", ack) 
    i += w 
s.close() 

```
## OUPUT


<img width="1285" height="312" alt="image" src="https://github.com/user-attachments/assets/3b7daa23-1ca1-484e-9d3f-b717ae1a8968" />
<img width="1285" height="342" alt="image" src="https://github.com/user-attachments/assets/900b01b1-908f-4801-9329-90348f2d36d1" />

<img width="717" height="480" alt="image" src="https://github.com/user-attachments/assets/41f255ad-257d-4fa2-9776-7546a011c274" />
<img width="667" height="517" alt="image" src="https://github.com/user-attachments/assets/256e666b-6053-4145-9fb5-4d31f3841e33" />
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
