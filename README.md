# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
Implementation of sliding window protocol and it's execution on  VS code.

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```python
server.py

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

client.py

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

## OUTPUT

server.py:

<img width="932" height="393" alt="Screenshot 2026-11-19 135649" src="https://github.com/user-attachments/assets/92bc57f5-1f43-4a72-84f0-73dd41210a99" />

client.py:

<img width="966" height="435" alt="Screenshot 2026-11-19 135758" src="https://github.com/user-attachments/assets/18816e4e-29f5-4510-8f4d-3881099c43bc" />


## RESULT
Thus, python program to perform sliding window protocol was successfully executed
