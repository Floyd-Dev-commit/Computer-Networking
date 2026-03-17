#1. DNS Query (Linux Terminal)
# Perform an iterative DNS query to trace the resolution of a domain
dig www.hdu.edu.cn +trace

#2. Socket Programming (Python)
UDP Client & Server
## Udp client
from socket import *
serverName = '127.0.0.1'
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_DGRAM)
message = input('input lowercase sentence:')
clientSocket.sendto(message.encode(), (serverName, serverPort))
modifiedMessage, serverAddress = clientSocket.recvfrom(2048)
print(modifiedMessage.decode())
clientSocket.close()

## Udp server
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_DGRAM)
serverSocket.bind(('', serverPort))
print("The server is ready to receive")
while True:
    message, clientAddress = serverSocket.recvfrom(2048)
    modifiedMessage = message.decode().upper()
    serverSocket.sendto(modifiedMessage.encode(), clientAddress)

## Tcp client
from socket import *
serverName = '127.0.0.1'
serverPort = 12000
clientSocket = socket(AF_INET, SOCK_STREAM)
clientSocket.connect((serverName, serverPort))
sentence = input('input lowercase sentence:')
clientSocket.send(sentence.encode())
modifiedMessage = clientSocket.recv(1024)
print('From Server:', modifiedMessage.decode())
clientSocket.close()

## Tcp server
from socket import *
serverPort = 12000
serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', serverPort))
serverSocket.listen(1)
while True:
    connectionSocket, addr = serverSocket.accept()
    sentence = connectionSocket.recv(1024).decode()
    capitalizedSentence = sentence.upper()
    connectionSocket.send(capitalizedSentence.encode())
    connectionSocket.close()

#3. Cicso Device Configuration (CLI)
! --- Switch/Router Basic Configuration ---
enable
configure terminal
hostname R1

! --- Interface Configuration ---
interface fastEthernet 0/0
ip address 192.168.1.1 255.255.255.0
speed 10
duplex half
no shutdown
exit

! --- System Information & Banner ---
banner motd &
This is R1. Enjoy it!&

! --- Verification & Saving ---
show ip route
show running-config
write memory

#VLAN & Trunk
! --- Switch 1 Configuration ---
vlan 10
name Engineering
exit
interface fastEthernet 0/1
switchport access vlan 10
exit
interface fastEthernet 0/24
switchport mode trunk  ! Set up trunk link between switches

#Inter-VLAN Routing via Router-on-a-Stick
! --- Router Sub-interface Configuration ---
interface fastEthernet 0/0.1
encapsulation dot1Q 10  ! Associate with VLAN 10
ip address 192.168.10.1 255.255.255.0
exit
interface fastEthernet 0/0.2
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0

#NAT (Static NAT)
ip nat inside source static 192.168.1.1 200.1.1.1
interface fa 0/0
ip nat inside
interface fa 0/1
ip nat outside

#NAT (Dynamic NAT)
ip nat pool test 200.1.1.2 200.1.1.10 netmask 255.255.255.0
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 pool test

#RIP & OSPF
router rip
version 2
network 192.168.1.0
network 10.0.0.0

#OSPF
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 10.1.1.0 0.0.0.255 area 0

#ACL
access-list 1 deny 192.168.1.0 0.0.0.255
access-list 1 permit any
interface fastEthernet 0/0
ip access-group 1 in
