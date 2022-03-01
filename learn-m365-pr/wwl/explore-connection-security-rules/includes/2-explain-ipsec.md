You can use IPsec to ensure confidentiality, integrity, and authentication in data transport across channels that are not secure. Though its original purpose was to secure traffic across public networks, many organizations have chosen to implement IPsec to address perceived weaknesses in their own private networks that might be susceptible to exploitation.

If you implement IPsec properly, it provides a private channel for sending and exchanging potentially sensitive or vulnerable data, whether it is email, FTP traffic, news feeds, partner and supply-chain data, medical records, or any other type of TCP/IP-based data.

### IPsec

 -  Offers mutual authentication both before and during communications.
 -  Forces both parties to identify themselves during the communication process.
 -  Enables confidentiality through IP traffic encryption and digital-packet authentication.

#### IPsec modes

IPsec has two modes:

 -  **Encapsulating security payload (ESP)**. This mode encrypts data using one of several available algorithms.
 -  **Authentication Header (AH)**. This mode signs traffic, but does not encrypt it.

#### Providing IP traffic integrity by rejecting modified packets

ESP and AH verify the integrity of all IP traffic. If a packet has been modified, the digital signature will not match, and IPsec will discard the packet. ESP in the tunnel mode encrypts the source and destination addresses as part of the payload. In the tunnel mode, ESP adds a new IP header to the packet that specifies the tunnel endpoints’ source and destination addresses. ESP can make use of Data Encryption Standard (DES), Triple Data Encryption Standard (3DES), and Advanced Encryption Standard (AES) encryption algorithms in Windows Server and Windows client. As a best practice, you should avoid using DES unless clients cannot support the stronger encryption that AES or 3DES offer.

#### Providing protection from replay attacks

ESP and AH use sequence numbers. As a result, any packets that hackers attempt to capture for later replay use numbers that are out of sequence. Using sequenced numbers ensures that an attacker cannot reuse or replay captured data to establish a session or gain information. Using sequenced numbers also protects against attempts to intercept a message and use it to access resources, possibly months later.

### Connection security rules

You can protect a network with two types of isolation:

 -  **Server isolation**. You can isolate a server by configuring specific servers to require an IPsec policy before accepting authenticated communications from other computers. For example, you might configure a database server to accept connections only from a web application server.
 -  **Domain isolation**. You can isolate a domain by using Active Directory domain membership to ensure that computers that are domain members accept only authenticated and secured communications from other domain-member computers. The isolated network consists only of that domain’s member computers, and domain isolation uses an IPsec policy to protect traffic between domain members, including all client and server computers.
