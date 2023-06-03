# EX-3
## DATE:22-03-2023
## AIM :

To write a python program to perform sliding window protocol
## ALGORITHM :

    Start the program.
    Get the frame size from the user
    To create the frame based on the user request.
    To send frames to server from the client side.
    If your frames reach the server it will send ACK signal to client otherwise it will sendNACK signal to client.
    Stop the program
## CLIENT PROGRAM :
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send:"))
l=list(range(size))
s=int(input("Enter Window Size:"))
st=0
i=0
while True:
	while(i<len(l)):
		st+=s
		c.send(str(l[i:st]).encode())
		ack=c.recv(1024).decode()
		if ack:
			print(ack)
			i+=s
```
## SERVER PROGRAM :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
	print(s.recv(1024).decode())
	s.send("acknowledgement recieved from the server".encode())
```
## SERVER OUTPUT :
![241174922-6843d7a2-aa4b-449e-8c00-30a4a95672ae](https://github.com/Amruthavarshnibs/EX-3/assets/119103704/7b5ab011-4ed7-4ee6-90de-13593158d8ac)
## CLIENT OUTPUT :
![241175011-6c74257e-da99-4c20-8f89-3ba4de8e0d9e](https://github.com/Amruthavarshnibs/EX-3/assets/119103704/9033303f-e54f-4047-a7b8-aa45cc43ee9b)
## RESULT :

Thus, python program to perform stop and wait protocol was successfully executed.
