# 2a-Stop-and-Wait-Protocol.

### Name:Loshini.G
### Register Number:212223220051
### Department:IT
### Date:

## AIM:
To write a python program to perform stop and wait protocol.

## ALGORITHM:
Start the program.
Get the frame size from the user
To create the frame based on the user request.
To send frames to server from the client side.
If your frames reach the server it will send ACK signal to client
Stop the Program.

## PROGRAM:

### Server:
```py
import socket

def server_program():
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM) 
    server_socket.bind(('localhost', 12345)) 
    
    print("Server is listening...")

    while True:
        data, addr = server_socket.recvfrom(1024) 
        print(f"Received frame of size: {len(data)} bytes from {addr}")

        server_socket.sendto(b'ACK', addr)
        print("Sent ACK to client.")

if __name__ == '__main__':
    server_program()
```

### Client:
```py
import socket

def client_program():
    frame_size = int(input("Enter the frame size (in bytes): "))
    
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

    frame = b'A' * frame_size 
    
    server_address = ('localhost', 12345)
    
    try:
        print("Sending frame to server...")
        client_socket.sendto(frame, server_address)
        
        data, addr = client_socket.recvfrom(1024)  
        print("Received ACK from server:", data.decode())
    
    finally:
        client_socket.close()

if __name__ == '__main__':
    client_program()
```

## OUTPUT:

### Server:
![image](https://github.com/user-attachments/assets/5ae0909a-26cd-4f51-a9a0-b8df826f590e)

### Client:
![image](https://github.com/user-attachments/assets/fe57c3f4-5bc1-41c5-9076-a091874f2d1d)

## RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
