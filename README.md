# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
server side:
```
import socket

s = socket.socket()
s.bind(('localhost', 1234))
s.listen(1)

print("Server started, waiting for client...")
conn, addr = s.accept()
print("Connected with", addr)

while True:
    frame = conn.recv(1024).decode()
    if frame == "END":
        print("Transmission completed")
        break

    print("Frame received:", frame)
    conn.send("ACK".encode())

conn.close()
s.close()
```

client side:
```
import socket

c = socket.socket()
c.connect(('localhost', 1234))

frame_size = int(input("Enter number of frames: "))

for i in range(frame_size):
    frame = f"Frame {i+1}"
    print("Sending:", frame)
    c.send(frame.encode())

    ack = c.recv(1024).decode()
    print("Received:", ack)

c.send("END".encode())
c.close()```
```
## OUTPUT
server side:
<img width="1122" height="955" alt="image" src="https://github.com/user-attachments/assets/baeda56a-9efc-4135-aea2-bf0879755b00" />
client side:
<img width="979" height="971" alt="image" src="https://github.com/user-attachments/assets/5cd4f9d7-0996-4474-a267-db9b7ce13e89" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
