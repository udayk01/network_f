#  Task 1 

## Socket program for the communication between single client and single sever without in any encryption(one way)

server.py 

![image](https://github.com/udayk01/network_f/assets/52235763/8a553545-4982-448e-9ef5-4e4f85d1167c)

client.py

![image](https://github.com/udayk01/network_f/assets/52235763/ab16401c-c46b-47d7-b24a-86128e4b005f)

![image](https://github.com/udayk01/network_f/assets/52235763/0a21e255-1361-4589-9adc-78b9258ccff1)

![image](https://github.com/udayk01/network_f/assets/52235763/82e696fd-cb15-4e15-a547-a9a50ced0dc8)

# Task 2

## Socket program for the communication between single client and single sever with RSA encryption (one way)

```
rsaserver.py

import socket
import rsa  # Ensure you have the rsa package installed

# Generating the public key and the private key
public_key, private_key = rsa.newkeys(2048)

# Save the public key and private key to files
with open("public.pem", "wb") as f:
    f.write(public_key.save_pkcs1("PEM"))

with open("private.pem", "wb") as f:
    f.write(private_key.save_pkcs1("PEM"))

# Create a socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to a specific address and port
server_address = ('localhost', 12345)
server_socket.bind(server_address)

# Listen for incoming connections
server_socket.listen(1)

print("Waiting for a connection...")

# Accept a connection
client_socket, client_address = server_socket.accept()
print(f"Connection from {client_address}")

while True:
    # Receive data from the client
    data = client_socket.recv(1024)

    # Check if there is no more data
    if not data:
        break

    # Load the private key from file
    with open("private.pem", "rb") as f:
        private_key = rsa.PrivateKey.load_pkcs1(f.read())

    # Decrypt the received data using the private key
    plain_text = rsa.decrypt(data, private_key)

    # Print the decrypted message
    print(f"Received: {plain_text.decode()}")

# Close the client and server sockets
client_socket.close()
server_socket.close() 
```

```
rsaclient.py

import socket
import rsa  # Make sure to have the rsa package installed

# Create a socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Server address and port
server_address = ('localhost', 12345)

# Connect to the server
client_socket.connect(server_address)

while True:
    # Get user input for the message
    message = input("Enter a message: ")
    
    # Store the original message to check for the 'exit' condition
    msg = message
    
    # Load the server's public key from the 'public.pem' file
    with open("public.pem", "rb") as f:
        public_key = rsa.PublicKey.load_pkcs1(f.read())
    
    # Encrypt the message using the server's public key
    encrypted_message = rsa.encrypt(message.encode(), public_key)
    
    # Send the encrypted message to the server
    client_socket.send(encrypted_message)
    
    # Check if the user entered 'exit' to exit the loop
    if msg == 'exit':
        break

# Close the client socket
client_socket.close()
```

![image](https://github.com/udayk01/network_f/assets/52235763/938cffb3-1d34-4f2e-bfdc-e8a55ac3dda2)

![image](https://github.com/udayk01/network_f/assets/52235763/04e8b6c3-886a-4033-a730-b0ba0fbaa13c)

Here, we can see that message is not visible due to the RSA encryption.

# Task 3

## Socket program to implement two-way communication between the client and sever with encryption.

```
2wayrsaserver.py

import socket
import rsa  # Make sure to have the rsa package installed

# Generating RSA key pairs for the server and client
public_key_server, private_key_server = rsa.newkeys(2048)
with open("public_server.pem", "wb") as f:
    f.write(public_key_server.save_pkcs1())

with open("private_server.pem", "wb") as f:
    f.write(private_key_server.save_pkcs1())

public_key_client, private_key_client = rsa.newkeys(2048)
with open("public_client.pem", "wb") as f:
    f.write(public_key_client.save_pkcs1())

with open("private_client.pem", "wb") as f:
    f.write(private_key_client.save_pkcs1())

# Create a socket for the server
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server's IP address and port
host = '0.0.0.0'  # 0.0.0.0 binds to all available network interfaces
port = 12345

# Bind the socket to the address and port
server_socket.bind((host, port))

# Listen for incoming connections
server_socket.listen()

print(f"Server listening on {host}:{port}")

# Accept a connection from a client
client_socket, client_address = server_socket.accept()
print(f"Accepted connection from {client_address}")

while True:
    # Receive data from the client
    client_data = client_socket.recv(1024)
    
    # Load the server's private key
    with open("private_server.pem", "rb") as f:
        private_key_server = rsa.PrivateKey.load_pkcs1(f.read())
    
    # Decrypt the client's data using the server's private key
    plain_text = rsa.decrypt(client_data, private_key_server)
    
    if not client_data:
        break

    # Print the received data from the client
    print(f"Client: {plain_text.decode('utf-8')}")

    # Send a response to the client
    server_response = input("Server: ")
    
    # Check if the server wants to exit
    srv_msg = server_response
    if srv_msg == 'exit':
        server_socket.close()
        exit()
    
    # Load the client's public key
    with open("public_client.pem", "rb") as f:
        public_key_client = rsa.PublicKey.load_pkcs1(f.read())
    
    # Encrypt the server's response using the client's public key
    msg_to_client = rsa.encrypt(server_response.encode('utf-8'), public_key_client)
    client_socket.send(msg_to_client)

# Close the client and server sockets
client_socket.close()
server_socket.close()
```
```
2wayrsaclient.py

import socket
import rsa

# Create a socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Define the server's IP address and port
host = '127.0.0.1'  # Change this to the server's IP address
port = 12345

# Connect to the server
client_socket.connect((host, port))

while True:
    # Send a message to the server
    client_message = input("Client: ")
    msg = client_message

    # Load the server's public key from 'public_server.pem'
    with open("public_server.pem", "rb") as f:
        public_key_server_data = f.read()
        public_key_server = rsa.PublicKey.load_pkcs1(public_key_server_data)

    # Encrypt the message using the server's public key
    message = rsa.encrypt(client_message.encode('utf-8'), public_key_server)
    client_socket.send(message)

    if msg == 'exit':
        exit()

    # Receive the response from the server
    with open("private_client.pem", "rb") as f:
        private_key_client_data = f.read()
        private_key_client = rsa.PrivateKey.load_pkcs1(private_key_client_data)
    server_response = client_socket.recv(1024)
    plain_text = rsa.decrypt(server_response, private_key_client)
    print(f"Server: {plain_text.decode('utf-8')}")

# Close the client socket
client_socket.close()
```
![image](https://github.com/udayk01/network_f/assets/52235763/d3781ac2-1376-45fb-9ce3-bba2a467c1f4)

![image](https://github.com/udayk01/network_f/assets/52235763/9a79a2d6-de60-48df-adb8-4864568c9629)

# Task 4

## To implement the concept that show in the figure given below using socket programming and creating a chat room for client1 and client2 where server is the key distributer.

![image](https://github.com/udayk01/network_f/assets/52235763/7e45c5e1-0ebf-43c9-a02d-9a43a5167b17)

```
admin.py

import socket
import threading
import rsa

# Generating the public key and the private key
public_key, private_key = rsa.newkeys(1024)
# Save the public key in a file
with open("public.pem", "wb") as f:
    f.write(public_key.save_pkcs1("PEM"))
# Save the private key in a file
with open("private.pem", "wb") as f:
    f.write(private_key.save_pkcs1("PEM"))

# Define the server host and port
HOST = '0.0.0.0'  # Listen on all available network interfaces
PORT = 12345

# Create a socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to the host and port
server_socket.bind((HOST, PORT))

# Listen for incoming connections
server_socket.listen(2)  # Allow up to 2 clients to connect

# List to hold client connections
client_connections = []

def handle_client(client_socket):
    while True:
        try:
            # Receive a message from the client
            message = client_socket.recv(1024)
            if not message:
                break

            # Load the server's private key for decryption
            with open("private.pem", "rb") as f:
                private_key = rsa.PrivateKey.load_pkcs1(f.read())
            # Decrypt the received message
            plain_text = rsa.decrypt(message, private_key)
            # Decode the decrypted message from bytes to a string
            plain_text = plain_text.decode('utf-8')

            if plain_text == 'exit':
                break

            # Broadcast the message to all connected clients
            for connection in client_connections:
                if connection != client_socket:
                    # Load the recipient's public key for encryption
                    with open("public.pem", "rb") as f:
                        public_key = rsa.PublicKey.load_pkcs1(f.read())
                    # Encrypt the message for the recipient
                    plain_text = rsa.encrypt(plain_text.encode(), public_key)
                    # Send the encrypted message to the recipient
                    connection.send(plain_text)
        except ConnectionResetError:
            break

    # Remove the disconnected client from the list
    client_connections.remove(client_socket)
    client_socket.close()

while True:
    print("Server is listening for incoming connections...")
    # Accept a connection from a client
    client_socket, client_address = server_socket.accept()
    print(f"Accepted connection from {client_address}")
    client_connections.append(client_socket)

    # Create a new thread to handle the client
    client_thread = threading.Thread(target=handle_client, args=(client_socket,))
    client_thread.start()
```
Same code for both the clients

```
cilent.py

import socket
import threading
import rsa

# Define the server host and port
HOST = '10.0.2.15'  #server's IP address
PORT = 12345

# Function to receive and display messages from the server
def receive_messages(client_socket):
    while True:
        try:
            # Receive a message from the server
            message = client_socket.recv(1024)
            with open("private.pem", "rb") as f:
                private_key = rsa.PrivateKey.load_pkcs1(f.read())
            # Decrypt the received message using the client's private key
            plain_text = rsa.decrypt(message, private_key)
            if plain_text == 'exit':
                break
            print("\n")
            print(f"Received: {plain_text.decode()}")
        except ConnectionResetError:
            print("Disconnected from the server.")
            break

# Create a socket for the client
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to the server using the defined host and port
client_socket.connect((HOST, PORT))

# Start a thread to receive and display messages from the server
receive_thread = threading.Thread(target=receive_messages, args=(client_socket,))
receive_thread.start()

# Send messages to the server
while True:
    with open("public.pem", "rb") as f:
        public_key = rsa.PublicKey.load_pkcs1(f.read())
    # Read a message from the user
    message = input("Enter the message to send: ")
    if message == 'exit':
        break
    else:
        # Encrypt the message using the server's public key and send it
        message = rsa.encrypt(message.encode(), public_key)
        client_socket.send(message)
```
![image](https://github.com/udayk01/network_f/assets/52235763/ffaa6dbe-5767-4d6c-9e66-0beb0b3191d6)

![image](https://github.com/udayk01/network_f/assets/52235763/c0d1474b-f71f-4887-b290-e6691c5bff9a)



