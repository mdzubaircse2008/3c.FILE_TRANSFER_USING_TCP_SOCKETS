# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
### Server.py
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print('Server listening...')
c, addr = s.accept()
print('Got connection from', addr)
filename = 'mytext.txt'
with open(filename, 'rb') as f:
    data = f.read(1024)
    while data:
        c.send(data)
        print('Sending data...')
        data = f.read(1024)
f.close()
print('Done sending')
c.close()
s.close()
```

### Client.py
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data = %s' % (data))
        if not data:
            break
        f.write(data)
        break
print('Successfully received the file')
s.close()
print('Connection closed')
```
## OUTPUT
### Server Side:
<img width="1474" height="922" alt="image" src="https://github.com/user-attachments/assets/3d852f53-6063-4d5d-8e1e-23153390e307" />

### Client Side:
<img width="1500" height="952" alt="image" src="https://github.com/user-attachments/assets/db3d3cbb-0e3a-48e4-8a91-088a45099720" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
