SNY Flood
=========

A SYN Flood is one of the most common forms of DDoS attacks observed by the MS-ISAC. It occurs when an attacker sends a succession of TCP Synchronize (SYN) requests to the target in an attempt to consume enough resources to make the server unavailable for legitimate users. This works because a SYN request opens network communication between a prospective client and the target server. When the server receives a SYN request, it responds acknowledging the request and holds the communication open while it waits for the client to acknowledge the open connection. However, in a successful SYN Flood, the client acknowledgment never arrives, thus consuming the server's resources until the connection times out. A large number of incoming SYN requests to the target server exhausts all available server resources and results in a successful DDoS attack.

Recommendations
---------------

* To identify a SYN Flood, investigate network logs and locate the TCP SYN flag. Tcpdump or Wireshark may work for this purpose.

  * TCP SYN packets are normal and are not necessarily indicative of malicious activity. Instead look for a large number of SYN packets, from multiple sources, over a short duration.

* If you identify an attack, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* To help minimize the impact of successful SYN Flood attacks, define strict “TCP keepalive” and “maximum connection” rules on all perimeter devices, such as firewalls and proxy servers.

* On some firewall appliances, you can enable “SYN cookies” to help mitigate the effects of a SYN Flood. Enabling SYN cookies forces the firewall to validate the TCP connection between client and server before traffic is passed to the server. When attackers never send a final acknowledgment of the open connection, the firewall drops the connection.

.. note::
     **Slowloris Attacks**
     
     While Slowloris is a DoS tool that can be easily accessed by threat actors, the term Slowloris is also used to describe a type of DoS attack. Slowloris attacks attempt to establish multiple TCP connections on a target web server, and hold them open for as long as possible by sending partial requests, very similar to a SYN Flood.
     
     **Variation of SYN Flood: ESSYN/XSYN Flood**
     
     An ESSYN Flood, also known as an XSYN Flood, is an attack designed to target entities using stateful firewalls. The attack works when a large number of unique source IP  addresses all attempt to open connections with the target destination IP. Each new connection from a unique source IP creates a new entry in the firewall state table. The purpose of this attack is to create more unique connections then there is space for in the firewall’s state table. Once the table is full, the firewall will not accept any additional inbound connections, denying service to legitimate users attempting to access the destination IP.
     
     **Variation of SYN Flood: PSH Flood**
     
     A Push (PSH) Flood involves sending a large number of TCP packets with the PSH bit enabled. The purpose of a PSH packet is to bypass packet buffering, which allows for the efficient transfer of data by ensuring packets are filled to the maximum segment size when multiple packets are sent over a TCP connection. If the PSH bit is enabled, it indicates the packet should immediately be sent to the application. In normal circumstances, this does not present an issue, however when a significant number of PSH packets are sent to a target server, there is a potential to overload its resources, creating a DoS situation.