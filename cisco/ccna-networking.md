# CCNA Networking

> Credits to CCNA 200-301 Volume 1 and 2 Official Cert Guide by Wendell Odom, CCIE No. 1624 Emeritus, year 2020

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

##### OSI Networking Model and Terminology
- Layer 5-7 of OSI model = Layer 5 TCP/IP model
- OSI does not use frame/packet/segment for messages, instead it uses Protocol Data Unit (PDU). Uses LxPDU refers to PDU at referenced layer <br />
  <img width="496" height="212" alt="image" src="https://github.com/user-attachments/assets/2be42308-9693-4114-9fc6-6744ec34ea35" />


### Fundamentals of Ethernet LANs
- Ethernet refers to a family of LAN standards that define physical and data-link layers of the world's most popular wired LAN technology
- Wired LAN -> switch, Wireless LAN -> access point (AP)
- Types of Ethernet:
  | Speed | Common Name | Informal IEEE Standard Name | Formal IEEE Standard Name | Cable Type, Maximum Length |
  |-------|-------------|-----------------------------|---------------------------|--------------------|
  | 10 Mbps | Ethernet  | 10BASE-T                    | 802.3                     | Copper, 100 m      |
  | 100 Mbps | Fast Ethernet | 100BASE-T              | 802.3u                    | Copper, 100 m      |
  | 1000 Mbps | Gigabit Ethernet | 1000BASE-LX        | 802.3z                    | Fiber, 5000 m      |
  | 1000 Mbps | Gigabit Ethernet | 1000BASE-L         | 802.3ab                   | Copper, 100 m      |
  | 10 Gbps   | 10 Gig Ethernet  | 10GBASE-T          | 802.3an                   | Copper, 100 m      |


##### Building Physical Ethernet LANs with UTP
- Ethernet sends data over UTP cables, but uses electricity that flows over wires
- To send data, 2 devices follow the same rules called an encoding scheme (like 2 people talk using the same language)
- In an actual UTP cable, the wires will be twisted together, instead of being parallel. The twisting prevents crosstalk from EMI
- Straight-Through Cable Pinout:
  - 10BASE-T and 100BASE-T use 2 pairs of wires in a UTP cable, one for each direction <br />
    - <img width="534" height="263" alt="image" src="https://github.com/user-attachments/assets/d856a0f7-78d5-40a0-a3b4-6bf754c5fdd4" />
    - As a rule, Ethernet NIC transmitters use the pair connected to pins 1 and 2, NIC receivers use the pair at pins 3 and 6
    - LAN switches, do the opposite: LAN receivers use pair at pins 1 and 2, LAN transmitters use wire pair at pins 3 and 6 <br />
      <img width="573" height="211" alt="image" src="https://github.com/user-attachments/assets/1a25476f-0d4b-46e1-a14f-850ea25afa31" /> <br />
      <img width="640" height="146" alt="image" src="https://github.com/user-attachments/assets/c3592642-ac08-4d48-a8d7-daecd067bfb5" />
  - 1000BASE-T (Gigabit Ethernet) differs from 10BASE-T and 100BASE-T in terms of cabling and pinouts
    - Requires 4 wire pairs and uses advanced electronics that allow both ends to transmit and receive simultaneously on each wire pair
    - Has same pinouts for 2 pairs as the 10BASE-T and 100BASE-T standards, and adds a pair at pins 4 5 7 8 <br />
      <img width="537" height="263" alt="image" src="https://github.com/user-attachments/assets/66fb1ddc-e7f9-4f7a-8254-a83495e2690f" />


##### Building Physical Ethernet LANs with Fiber
- 3 outer layers (outer jacket, strengthener, buffer) of the cable protect the interior, while inner cladding and core works together to allow transmission of light <br />
  <img width="501" height="236" alt="image" src="https://github.com/user-attachments/assets/4bd24599-d0bf-4072-a489-38b762b00059" />
  - Multimode Fiber with Internal Reflection <br />
    <img width="553" height="139" alt="image" src="https://github.com/user-attachments/assets/f0ef5532-98f1-481c-9f2e-8a24827ec05d" />
  - Single-Mode Fiber with Laser Transmitter (core diameter is 1/5 of multimode cables) <br />
    <img width="556" height="135" alt="image" src="https://github.com/user-attachments/assets/60a3f9b7-c85e-4e88-b96b-f3c8d5116bf3" /> <br />
<img width="634" height="199" alt="image" src="https://github.com/user-attachments/assets/1b83c6ad-eb96-428e-98a2-7a428eb8c2f6" />

##### Sending Data in Ethernet Networks
- Ethernet Data-Link Protocols
  - Ethernet Frame Format: Header + Encapsulated Data + Trailer <br />
    <img width="534" height="84" alt="image" src="https://github.com/user-attachments/assets/f2fd4e9c-adb2-4bc4-b11f-982317a8e993" />
  - <img width="640" height="366" alt="image" src="https://github.com/user-attachments/assets/4ce44776-0785-4a84-9458-ee794249d60c" />
- Ethernet addressing aka Media Access Control (MAC) addresses = 6-byte-long = 48-bit-long binary numbers
  - MAC are usually listed as 12-digit hexadecimal numbers (Cisco devices usually add periods to the number for easier readability; ex: 0000.0C12.3456)
  - Most MAC addresses represent a single NIC or other Ethernet port, so these addresses are often called a unicast Ethernet address
  - Sending data to a destination unicast MAC address only works if all MAC addresses are unique. To solve this, manufacturers must ask IEEE to assign a universally unique 3-byte code called the organisationally unique identifier (OUI) <br />
    <img width="490" height="174" alt="image" src="https://github.com/user-attachments/assets/8d7ca9a5-fa99-43f3-b17c-a5d7e4d806d0" />
  - Broadcast address: Has a value of FFFF.FFFF.FFFF. Frames sent to this address should be sent to all devices on the LAN.
  - Multicast address: Frames sent to this address will be forwarded to multiple recipient devices
- Error Detection with Frame Check Sequence (FCS): Sender uses complex math formula to the frame before sending and stores the result in the FCS field. Receiver uses same math formula and compares with sender's results
- Error detection is not error recovery. Errored frames are discarded, while TCP recovers lost data by sending again
- Modern Ethernet LANs uses full duplex: Device sends and receives at same time
- Older LAN hubs used half duplex: Device alternates between sending and receiving
- Half-duplex devices face collision errors of electrical signals <br />
  <img width="471" height="106" alt="image" src="https://github.com/user-attachments/assets/80cd2b49-0b29-40e6-80a7-b0e794db9693" />
- That's why Carrier Sense Multiple Access with Collision Detection (CSMA/CD) algorithm is used. CSMA/CD allows only 1 device to successfully send a frame at any point in time


### Fundamentals of WANs and IP Routing
- WAN technologies define the physical (L1) standards and data-link (L2) protocols used for long distance communication
- Leased-Line WANs:
  - Internetwork uses a router connected to each LAN with a WAN link between routers. Crooked line between routers commonly hides physical details of the line <br />
    <img width="614" height="109" alt="image" src="https://github.com/user-attachments/assets/c1cbb97f-c1e4-4222-805c-c17491e05df0" />
  - 2 most popular data-link layer protocols for leased lines: High-Level Data Link Control (HDLC) and Point-to-Point Protocol (PPP). All control the correct delivery of data over a physical link
  - HDLC: Less work than Ethernet because of simple point-to-point topology of a leased line (HDLC frame from 1 router can only go to the other end of the link) <br />
    <img width="643" height="294" alt="image" src="https://github.com/user-attachments/assets/3da2d16b-466e-4654-98bd-07153b299657" /> <br />
    ISO standard HDLC does not have a Type field. Cisco routers use a Ciso-proprietary variation of HDLC that adds a Type field: <br />
    <img width="332" height="123" alt="image" src="https://github.com/user-attachments/assets/8a1de958-f5a4-43c6-a8d6-64bbe01d9d83" />

##### Ethernet as a WAN Technology:
- Many WAN service providers (SP) use the model: <br />
  <img width="594" height="207" alt="image" src="https://github.com/user-attachments/assets/ddd80f11-042f-4264-8987-18e7c8b5b55c" />
- Ethernet WAN logically behaves like a point-to-point connection between 2 routers, and physically behaves as if a physical fiber Ethernet link existed between 2 routers
- Ethernet over MPLS (EoMPLS): Multiprotocol Label Switching used for creating Ethernet service for customer
- EoMPLS acting like a simple Ethernet link between 2 routers: <br />
  <img width="608" height="122" alt="image" src="https://github.com/user-attachments/assets/4c5fb43b-044f-4cf2-bb14-97c158611513" />
- EoMPLS link uses Ethernet for L1 and L2 functions. <br />
  <img width="606" height="199" alt="image" src="https://github.com/user-attachments/assets/d7b51728-fe5c-4b2a-badc-b238031d7017" />

##### IP Routing
- Only concerns itself with the logical details of delivering data, not the physical details
- <img width="608" height="393" alt="image" src="https://github.com/user-attachments/assets/c2d87c58-9041-4306-b209-efd41a44dbff" /> <br />
  - A: Network layer decides 150.150.4.10 is not in local IP subnet, so PC1 needs to send packet to R1
  - B: R1 compares received packet's destination address (150.150.4.10) to its routing table and finds entry for subnet 150.150.4.0. R1 encapsulates IP packet and forwards it to next-hop router R2
  - C: R2 repeats the same general process as R1 when R2 receives the HDLC frame
  - D: Like R1 and R2, R3 checks the FCS, discard old data-link header and trailer and matches its own route for destination's subnet
- Because routers build new data-link headers and trailers, and because new headers contain data-link addresses, PCs and routers need to decide what data-link addresses to use. Address Resolution Protocol (ARP) is used to dynamically learn the data-link address of an IP host connected to a LAN
- 



  
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
