# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM
```
Echo Server:

import socket

def start_echo_server():
    # Create a socket object
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # Bind the socket to a specific address and port
    server_address = ('localhost', 5555)
    server_socket.bind(server_address)

    # Listen for incoming connections
    server_socket.listen(1)
    print('Server listening on {}:{}'.format(*server_address))

    while True:
        # Wait for a connection
        print('Waiting for a connection...')
        client_socket, client_address = server_socket.accept()
        print('Connection from', client_address)

        # Receive and echo back the data
        data = client_socket.recv(1024)
        while data:
            print('Received:', data.decode())
            client_socket.sendall(data)
            data = client_socket.recv(1024)

        # Close the connection
        print('Connection closed by', client_address)
        client_socket.close()

if __name__ == "__main__":
    start_echo_server()
```
```
Echo Client :

import socket

def start_echo_client():
    # Create a socket object
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # Connect to the server
    server_address = ('localhost', 5555)
    client_socket.connect(server_address)

    # Send and receive messages
    message = input('Enter a message to send to the server (type "exit" to quit): ')
    while message.lower() != 'exit':
        # Send the message
        client_socket.sendall(message.encode())

        # Receive the echoed message
        data = client_socket.recv(1024)
        print('Received from server:', data.decode())

        # Ask for the next message
        message = input('Enter a message to send to the server (type "exit" to quit): ')

    # Close the connection
    client_socket.close()

if __name__ == "__main__":
    start_echo_client()
```

## OUPUT
## SERVER
![Screenshot 2024-03-12 182756](https://github.com/Srikaavyaathamizh/3a.Sockets_Creation_for_Echo_Client_and_Echo_Server/assets/144870938/8cd2cb6a-e6ab-4f0b-a345-a717069d6ef6)

## CLIENT
![Screenshot 2024-03-12 182809](https://github.com/Srikaavyaathamizh/3a.Sockets_Creation_for_Echo_Client_and_Echo_Server/assets/144870938/53bcdd2b-b279-42d3-982e-dc24510e7d26)


## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
