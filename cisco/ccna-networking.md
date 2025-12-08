# CCNA Networking

<details>
<summary><h2>Introduction to Networking</h2></summary>

### Introduction to TCP/IP Networking
| OSI Model | 4 Layer RFC 1122 TCP/IP Model | 5 Layer TCP/IP Model | Protocol Data Unit (PDU) | Example | Equipment operating | Domain |
|-----------|-------------------------------|----------------------|--------------------------|---------|---------------------|--------|
| Application | Application                 | Application          |                          | HTTP    |                     |        |
| Presentation | Application                | Application          |                          | HTTP    |                     |        | 
| Session    | Application                  | Application          |                          | HTTP    |                     |        |
| Transport  | Transport                    | Transport            | Segment                  | TCP, UDP | Router w/ NAT      |        |
| Network    | Internet                     | Network              | Packet                   | IP       | Router             | Subnet |
| Data-Link  | Network Access | Data-Link | Frame | Ethernet, 802.11 | Switch | Broadcast domain |
| Physical   | Network Access | Physical  | Bit/symbol | UTP, single/multimode fiber | Hub | Collision domain | 

##### TCP/IP Model (5 Layers):
  - Application Layer: Provides services and interface between software running on PC and network. (Protocols: HTTP, POP3, SMTP)
  - Transport Layer: Provides services to application layer by error-recovery to ensure guaranteed delivery. (Protocols: TCP, UDP)
    - Same-layer interaction: 2 computers use protocol that defines a header that communicates what each computer wants to do
    - Adjacent-layer interaction: Lower layer provides service to layer above
  - Network-layer: Defines routing so that routers can forward packets of data to correct destination (Protocols: IP)
  - Data-link layer: Protocols and rules that control use of physical media
  - Physical layers: Defines cabling and energy that flow over cables

##### Data Encapsulation Terminology
<img width="496" height="230" alt="image" src="https://github.com/user-attachments/assets/de8e7482-b76a-4e83-b8eb-6642b93c7d9d" /> <br />
1. Create and encapsulate the application data with any required application layer headers. For example, the HTTP OK message can be returned in an HTTP header, followed by part of the contents of a web page.
2. Encapsulate the data supplied by the application layer inside a transport layer header. For end-user applications, a TCP or UDP header is typically used.
3. Encapsulate the data supplied by the transport layer inside a network layer (IP) header. IP defines the IP addresses that uniquely identify each computer.
4. Encapsulate the data supplied by the network layer inside a data-link layer header and trailer. This layer uses both a header and a trailer.
5. Transmit the bits. The physical layer encodes a signal onto the medium to transmit the frame.

##### Names of TCP/IP Messages
<img width="366" height="81" alt="image" src="https://github.com/user-attachments/assets/63dc732e-ca26-4bf7-9552-defc6c8a1d76" /> <br />
- Segment > Transport
- Packet > Network
- Frame > Data-link (LH = Link header, LT = Link trailer)





#### Fundamentals of Ethernet LANs

#### Fundamentals of WANs and IP Routing

  
</details>


<details>
<summary><h2>Implementing Ethernet LANs</h2></summary>

  
</details>


<details>
<summary><h2>Implementing VLANs and STP</h2></summary>

  
</details>


<details>
<summary><h2>IPv4 Addressing</h2></summary>

  
</details>


<details>
<summary><h2>IPv4 Routing</h2></summary>

  
</details>

<details>
<summary><h2>OSPF</h2></summary>

  
</details>

<details>
<summary><h2>IP Version 6</h2></summary>

  
</details>

<details>
<summary><h2>Wireless LANs</h2></summary>

  
</details>
