UDP Flood
=========

A UDP Flood is very similar to a SYN Flood in that an attacker uses a botnet to send a significant amount of traffic to the target server. The difference is that this attack is much faster, and rather than attempting to exhaust server resources, it seeks to consume all of the available bandwidth on the server’s network link, thereby denying access to legitimate users. The attack works because a server that receives a UDP packet on a network port, such as 50555/UDP, checks for an application that is listening on that port. If nothing is listening on that port, it replies to the sender of the UDP packet with an Internet Control Message Protocol (ICMP) Destination Unreachable packet. During an attack, a large number of UDP packets arrive, each with various destination ports. This forces the server to process each one, and in most cases, respond to each one. This type of attack can quickly lead to the consumption of all available bandwidth.

Recommendations
---------------

* To identify a UDP Flood, investigate network logs and look for a large number of inbound UDP packets over irregular network ports coming from a large number of source IP addresses.

  * Many legitimate services use UDP for their network traffic. Common UDP ports are 53 (DNS), 88 (Kerberos), 137/138/445 (Windows), and 161 (SNMP). When investigating a DDoS attack, look for UDP traffic with high numbered network ports (1024+).

* If you identify an attack, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* To minimize the effect of UDP Flood attacks, define strict rules on your perimeter network devices, like firewalls, to allow only inbound traffic on ports that are required.