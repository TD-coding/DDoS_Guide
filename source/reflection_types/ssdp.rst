SSDP Reflection Attack with Amplification
=========================================
The Simple Service Discovery Protocol (SSDP) is commonly used for the discovery of Universal Plug and Play (UPnP) devices. UPnP is a series of networking protocols that allows networking devices to discover and connect with one another, without user intervention. Using SSDP, Simple Object Access Protocol (SOAP) is used to deliver control messages to UPnP devices. A SSDP reflection attack occurs when an attacker spoofs the victim’s IP address and sends crafted SOAP requests to open UPnP devices on the Internet. These devices then send their responses to that victim IP address. Depending on how the attacker crafted the request, the response could be amplified by a factor of 30 from a single request.

When an attacker spoofs a victim’s IP address and sends crafted SOAP requests over SSDP to a large number of public UPnP devices, the amplified responses are sent back to the victim, eventually resulting in the consumption of all available bandwidth.

Recommendations
---------------

* To identify if an SSDP Reflection Attack with Amplification is occurring, investigate network logs and look for inbound source port 1900/UDP (SSDP) traffic from a large number of source IP addresses.

* Once an attack is identified, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* Along with remediating inbound attacks, take the following preventative measures to ensure that your UPnP devices are not used to attack others.

  * If you are unsure if any devices on your network could be employed in an attack, follow the instructions available at `OpenSSDP <http://openssdpproject.org/>`_ to check.

  * It is also recommended to block outbound port 1900/UDP traffic at your border routers, and restrict UPnP to the internal network if required.