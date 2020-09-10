<center>
<h1>Computer Networks</h1>
</center>

**Question 1:** What is computer network? 

**Answer:** A computer network is a group of computers that use a set of common communication protocols over digital interconnections for the purpose of sharing resources located on or provided by the network nodes.
 
**Question 2:** What is a protocol? 

**Answer:** A communication protocol is a system of rules that allow two or more entities of a communications system to transmit information via any kind of variation of a physical quantity. The protocol defines the rules, syntax, semantics and synchronization of communication and possible error recovery methods.
 
**Question 3:** What is OSI Model?

**Answer:** The Open Systems Interconnection (OSI) model is a conceptual model created by the International Organization for Standardization which enables diverse communication systems to communicate using standard protocols. In plain English, the OSI provides a standard for different computer systems to be able to communicate with each other.

There are 7 OSI layers
- **Application Layer:** At the very top of the OSI Reference Model stack of layers, we find Application layer which is implemented by the network applications. These applications produce the data, which has to be transferred over the network. This layer also serves as a window for the application services to access the network and for displaying the received information to the user.
    - Example: Application – Browsers, Skype Messenger etc.
    - Describes the application over which the data is transmitted at application level like HTTP, HTTPS, SSH etc.
- **Presentation Layer:** The data from the application layer is extracted here and manipulated as per the required format to transmit over the network.
    - **Translation:**  For example, ASCII to EBCDIC
    - **Encryption:** Presenetation layer is responsible for encrypting the data.
    - **Compression:** Presenetation layer is responsible for compressing the number of bits to be tranmitted over network.
- **Session Layer:** In computer science and networking in particular, a session is a temporary and interactive information interchange between two or more communicating devices, or between a computer and user. This layer is responsible for establishment of connection, maintenance of sessions, authentication and also ensures security.
    - **Session Handling**: Session establishment, maintenance and termination happens here
    - **Synchronization:** This layer allows a process to add checkpoints which are considered as synchronization points into the data. These synchronization point help to identify the error so that the data is re-synchronized properly, and ends of the messages are not cut prematurely and data loss is avoided.
    - **Dialog Controller:** The session layer allows two systems to start communication with each other in half-duplex or full-duplex.
- **Transport Layer:** Transport layer provides services to application layer and takes services from network layer. The data in the transport layer is referred to as **Segments**.
    - **Segmentation and Reassembly:** This layer accepts the message from the (session) layer , breaks the message into smaller units . Each of the segment produced has a header associated with it. The transport layer at the destination station reassembles the message.
    - **Service Point Addressing:** In order to deliver the message to correct process, transport layer header includes a type of address called service **point address** or **port address**. Thus by specifying this address, transport layer makes sure that the message is delivered to the correct process.
    - **Sets Connection Type:** Adds if TCP or UDP connection.
- **Network Layer:** Network layer works for the transmission of data from one host to the other located in different networks. It also takes care of packet routing i.e. selection of the shortest path to transmit the packet, from the number of routes available. The sender & receiver’s IP address are placed in the header by the network layer.
    - **Routing:** The network layer protocols determine which route is suitable from source to destination. This function of network layer is known as routing.
    - **Logical Addressing**: In order to identify each device on inter-network uniquely, network layer defines an addressing scheme. The sender & receiver’s IP address are placed in the header by network layer. Such an address distinguishes each device uniquely and universally.
- **Data Link Layer:** The data link layer is responsible for the node to node delivery of the message. The main function of this layer is to make sure data transfer is error-free from one node to another, over the physical layer. When a packet arrives in a network, it is the responsibility of DLL to transmit it to the Host using its MAC address.
    - **Framing:** Framing is a function of the data link layer. It provides a way for a sender to transmit a set of bits that are meaningful to the receiver. This can be accomplished by attaching special bit patterns to the beginning and end of the frame.
    - **Physical addressing:** After creating frames, Data link layer adds physical addresses (MAC address) of sender and/or receiver in the header of each frame.
    - **Error control:** Data link layer provides the mechanism of error control in which it detects and retransmits damaged or lost frames
    - **Flow Control:** The data rate must be constant on both sides else the data may get corrupted thus , flow control coordinates that amount of data that can be sent before receiving acknowledgement.
    - **Access control:** When a single communication channel is shared by multiple devices, MAC sub-layer of data link layer helps to determine which device has control over the channel at a given time.
- **Physical Layer:** The lowest layer of the OSI reference model is the physical layer. It is responsible for the actual physical connection between the devices. The physical layer contains information in the form of bits.
    - **Bit synchronization:** The physical layer provides the synchronization of the bits by providing a clock. This clock controls both sender and receiver thus providing synchronization at bit level.
    - **Bitrate control:** The Physical layer also defines the transmission rate i.e. the number of bits sent per second.
    - **Physical topologies:** Physical layer specifies the way in which the different, devices/nodes are arranged in a network i.e. bus, star or mesh topolgy.
    - **Transmission mode:** Physical layer also defines the way in which the data flows between the two connected devices. The various transmission modes possible are: Simplex, half-duplex and full-duplex.

**Question 4:** Explain what is happening practically in OSI layer.

**Answer:** 
- Router here does not mean the one we see in home, they are actually combination of router and switch
- All layer other than physical layers are providing some logical calculations only
Here is my logic
- Application Layer, Presentation Layer and Session Layers are work of browser (or application) only that is why it is merged in TCP/IP model
- Transport Layer is also browser work which tell from which port it will read the data but is actually solving logic for OS-software connection and getting it ready in boxes (called segments) to be loaded on truck.
- Network Layer is actually solving logic for where data should go next (or which turn truck needs to take next). 
- Now Network Layer is just telling a logical or refferential address known as IP address so it makes it difficult to communicate with physical layer.
- Data Link Layer is like a friend who tells cab driver your correct address when you ask driver to go your home.
- Once Data Link Layer gives physical address, Physical layer drives the data physically.
- All this communication has happened between two routers only and happens multiple times so it reach its final destination.
 
**Question 5:** What is Access Point?

**Answer:** Access Point(AP) is a wireless LAN base station that can connect one or many wireless devices simultaneously to internet.
 
**Question 6:** What is Circuit Switching and Packet Switching?

**Answer:** 
- **Circuit Switching-** This switching happens in physical layer. What happens is that once connection is created, then data flows continuously. 
    - There is a dedicated path
    - Contiguous Flow is there
    - Data is always in an order
    - Less Efficiency
    - There is less delay
- **Packet Switching-** We send data in packets, as discussed for OSI layer. All logics happens as discussed in OSI or TCP/IP model.
    - There is a store and forward switching, data is stored and then forwarded so in case data is lost, then it can resend.
    - No order of packets
    - More efficiency
    - There is more delay as if resources are not free, then packet waits in queue.
 
**Question 7:** What is a firewall?

**Answer:**  
A firewall is a network security device that monitors incoming and outgoing network traffic and decides whether to allow or block specific traffic based on a defined set of security rules.

Firewalls have been a first line of defense in network security for over 25 years. They establish a barrier between secured and controlled internal networks that can be trusted and untrusted outside networks, such as the Internet. 

A firewall can be hardware, software, or both.

- **Host based Firewalls:** Host-based firewall is installed on each network node which controls each incoming and outgoing packet. It is a software application or suite of applications, comes as a part of the operating system. Host-based firewalls are needed because network firewalls cannot provide protection inside a trusted network. Host firewall protects each host from attacks and unauthorized access.

- **Network based Firewalls:** Network firewall function on network level. In other words, these firewalls filter all incoming and outgoing traffic across the network. It protects the internal network by filtering the traffic using rules defined on the firewall. A Network firewall might have two or more network interface cards (NICs). A network-based firewall is usually a dedicated system with proprietary software installed.
 
**Question 8:** What is the difference between private IP address and public IP address?

**Answer:**
|Key|Private|Public|
|:--:|:--:|:--:|
|Scope|	Private IP address scope is local to present network.|Public IP address scope is global.|
|Provider| Local Network Operator creates private IP addresses using network operating system. | ISP, Internet Service Provider controls the public IP address.|
|Cost|Private IP Addresses are free of cost.|Public IP Address comes with a cost.|
|Range|Limited|Anything other than Private range is available for public|

**Question 9:** What is a 3 way handshake?

**Answer:** It is how TCP establishes connection. 
- **Step 1 (SYN):** In the first step, client wants to establish a connection with server, so it sends a segment with SYN(Synchronize Sequence Number) which informs server that client is likely to start communication and with what sequence number it starts segments with
- **Step 2 (SYN + ACK):** Server responds to the client request with SYN-ACK signal bits set. Acknowledgement(ACK) signifies the response of segment it received and SYN signifies with what sequence number it is likely to start the segments with
- **Step 3 (ACK):** In the final part client acknowledges the response of server and they both establish a reliable connection with which they will start the actual data transfer

![3-Way handshake](https://i.ibb.co/yXTT6hC/TCP-connection-1.png)
