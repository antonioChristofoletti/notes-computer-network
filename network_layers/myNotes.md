# Networks

## OSI (Open System Interconnection) Model

- Reference Model;
- Came from ISO;
- Define rules and advices for the connection works fine in any type of device or network.
- All the steps was broken in abstract layers that have responsabilities and works, improving 

### Layers

##### 1.Application

- Softwares, protocols to send email, file and so on;
- Protocols: HTTP, FTP.

##### 2.Apresensation

- Convert data from the application layer to session;
- Responsable for compression and cryptography;
- Protocols: TLS.

##### 3.Session

- Communication between two processes in each side;
- Protocols: SIP, NETBIOS.

##### 4.Transport

- Detect erros from the bellow layers;
- Control the data flow: when send the data, send again, error receiving something....;
- Protocols: TCP/UDP.

##### 5.Network

- Responsable by the data route;
- Device addressing;
- Routing protocols IP;
- Protocols: IP, ICMP, NAT, ARP.


###### IP (Internet Protocol)

- Define a identification in a network (Just once device per IP);
- 32 bits, 4 billions of combinations;
- It has 4 octet:

00000000.00000000.00000000.00000000

Each octet has 255 possibilities.

- Reserved IPs, just for internal use:
    - 10.0.0.1    until 10.255.255.255  - Class A;
    - 172.16.0.0  until 172.31.255.255  - Class B;
    - 192.168.0.0 until 192.168.255.255 - Class C.

- The first and the last IPs from a network are not used
    - The first is used by the network, it represents the network itself;
    - The last is used for broadcast, It is used by the hosts to send data to all the hosts in the same network.

- Submask
    - Define which part of the IP represent the network and the hosts.

##### 6.Data Link

- Detect errors from Physical layer;
- Control the data flow among the devices;
- Technologies: Ethernet, Wifi.

##### 7.Physical

- Responsable for the send and receive the data in the real world through cables, electromagnetic wave and light;
- This layer has no idea of the data, just know that is necessary send bits (0/1) in some way.

##### Layers Communication

The data goes from a layers to another, every time that reach a new one It happens a encapsulation/enencapsulate. If the data is arriving is an enencapsulate, otherwise, It is an encapsulation.

This way there is a huge decoupling. Each layer can put or remove data related to its layer, but never edit data from a previous layer.

Example:

PCI = Protocol Control Information
SDU = Server Data Unit
PDU = Process Data Unit

Layer 1 - Send PDU
Layer 2 - Get a SDU, Create a PCI and send a PCI + SDU
Layer 3 - Get a SDU, Create a PCI and send a PCI + SDU
Layer 4 - Get a SDU, Create a PCI and send a PCI + SDU

Obs.: Each layer produce a PDU, however, the next layers see it as a SDU, then create its own control data, encapsulate the received SDU inside of its PCI.