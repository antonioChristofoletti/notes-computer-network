# Networks

## OSI (Open System Interconnection) Model

- Reference Model;
- Came from ISO;
- Define rules and advices for the connection works fine in any type of device or network.
- All the steps was broken in abstract layers that have responsabilities and works, improving 

### Layers

##### 1.Application

- Used by network applicaton.
- Protocols to send email, file and so on;
- Protocols: HTTP, HTTPS, FTP, POP3, SMTP, DHCP.

###### DHCP (Dynamic Host Configuration Protocol)

Protocol that can be used in a network in order to give network informations for a host machine that wants to be part of the network.

This protocol generally involve a DHCP Server and DHCP client, the server domains the informations and give them to the client connect. There are applications running on both of the machines that send and receive information related to this protocol.

###### DNS (Domain Name System)

- Protocol used to convert the domain name to an IP.
- Distributed service around the world;
- Allow to keep more than 1 web service in the same host;
- Allow to change the server related to the web service. If the server A goes down, just change the DNS to a server B, everything keep working.
- It also provides others information:
    - MX (Mail Exchange): What is the responsible server for receive the emails from a domain;
    - NS (Name Service): What is the responsible DNS server for the domain;
    - How long the given IP is gonna be valid.

- DNS Reverse: Reverse process, try to find a domain name for an IP.

##### Types

DNS Authoritative: Servers responsable in keeping a group of domains name, There are responsable for them and also authorization, giving information or even checking the information as truthful.

DNS Resolver/Cache: It finds the IP for a name for a large network, also keep the searched IP in cache, increasing speed

##### Servers

Hierarchical:
    - 13 root services;
        - IANA foundation manage these servers;
    - TLD(Top Level Domain): mil, edu, com, org, net, gov, br, pt, us,jp....
    - It could be a site with sub domain names, examples:
        - subdomain1.domain.com.br;
        - subdomain2.domain.com.br;
        - subdomain3.domain.com.br;
        - g1.globo.com.br

Each country has a specific Top Level Domain: br, uk, jp, ch.
    - CGI manage the .br in Brazil;
        - registro.br allows registry names for .br.

##### 2.Apresensation

- Responsable for translate, compression and cryptography;
- Protocols: TLS, SSL

##### 3.Session

- Manage Communication between the two processes in each side;
- Responsable by authentication, authorization, track of requested data to download/send.

- Protocols: SIP, NETBIOS.

##### 4.Transport

- Segmentation, divide the information, each segment has a sequence number and port.
- Flow Control, how much data it is gonna be send/receive, speed.
- Error Control: Checksum algorithm.
- Protocols:
    - TCP (Transmisson Control Protocol)
        - Connection-oriented Transmission
        - feedback, no so fast.
    - UDP (User Datagram Protocol)
        - Connectionless Transmission
        - no feedback, faster.
- Encapsulate the content into a Segment.

##### 5.Network

- Logical Addresing: Reach the correct destination
    - IPv4/IPv6
- Path determination: Find the best route to delivery the package.
- Routing: Recognize and transmite the package to the correct network or machine.
- Protocols: IP, ICMP, NAT, ARP.
- Encapsulate the content to a Packet.


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
    - It was different representitation:
        base_ip/24 or 255.255.255.0
    - It is possible define a best submask in order to fullfil the demand, example:
        400 machines -> /23 or 255.255.128.0    or 11111111.11111111.10000000.00000000
        200 machines -> /24 or 255.255.255.0    or 11111111.11111111.10000000.00000000
        100 machines -> /25 or 255.255.255.128  or 11111111.11111111.11111111.10000000
    - Tips
        - Convert from 2 digitals number to IP format, just power the digits by the quantity of numbers in the right, the sum all of them, example:
            - /23 -> 10000000 -> 1 power 7 = 128 -> 255.255.128.0
        - The opposite situation, just discover how many times the number needs to be powered until reach 255. Example:
            - 255.255.128.0 -> 128 = 2^7, so 2^8 = 256, then It was taken only 1 bit from the third octet -> /23

##### 6.Data Link

- Physical Addresing: - MAC

- Access the media:

    - Depending of the media, Data Link layer is gonna put different information in the head and tail of the frame in order to send the data correctly thourgh the media(wireless, sitellite link, wire cable)\

    - Example:
        PC1 -> fiber -> tower transmission -> satellite link -> tower transmission -> fiber -> PC2
        - Control the data flow among the devices:
            - Check the media channel before, during and after, avoid collisions and improve the quality.

- Detect errors from Physical layer:
    - Use information in the frame's tail to check the data quality.

- Encapsulate the content to a Frame.
    - Frame: MAC1, MAC2,  (IP1 IP2, Segment) = Data Packet, Tail

- Technologies: Ethernet, Wifi.

##### 7.Physical

- Responsable for the send and receive the data in the real world through cables, electromagnetic wave and light;
- This layer has no idea of the data, just know that is necessary send bits (0/1) in some way, get the frame, convert to binary and then convert the bits to signals.
- duplex, half-duplex, full-duplex.
- Technologies: Ethernet, Wifi.

 
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

## Cool Links

- https://www.youtube.com/watch?v=HLziLmaYsO0&ab_channel=RealPars;
- https://www.youtube.com/watch?v=vv4y_uOneC0&ab_channel=TechTerms.