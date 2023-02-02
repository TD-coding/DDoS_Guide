ICMP Flood
==========

An ICMP Flood occurs when an attacker uses a botnet to send a large number of ICMP packets to a target server in an attempt to consume all available bandwidth and deny legitimate users access. This attack works when a large number of sources can send enough ICMP traffic to consume all available bandwidth of the target’s network.

An example of this could be the “ping” command. This command is primarily used to test network connectivity between two points on a network. However, it is possible to supply this command with different variables to make the ping larger in size and occur more often. By using these variables correctly, and with enough source machines initiating the traffic, it is possible to consume all of the available bandwidth.

Recommendations
---------------

* To identify an ICMP Flood, investigate network logs and look for a significant amount of inbound ICMP traffic from a large number of sources.

  * Depending on what tool you are using to investigate your logs, you can identify ICMP packets either by the protocol displayed in the graphical user interface, such as with WireShark. When analyzing ICMP traffic you will notice that no port information is available, as ICMP does not use network ports like TCP or UDP.

  * If you are using a tool that displays the network protocols as numbered values, ICMP is protocol 1.

  * There are also ICMP type and code fields that identify what ICMP traffic is being sent or received. For a complete list of these types and codes, please clikc `here <http://www.nthelp.com/icmp.html>`_

* If you identify an attack, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* To mitigate some of the damage of ICMP Flood attacks, block ICMP traffic at perimeter network devices such as routers Additionally, set a packet-per-second threshold for ICMP requests on perimeter routers. If the amount of inbound ICMP traffic exceeds this threshold, the excess traffic is ignored until the next second. Packet-per-second thresholds effectively keep your network from being overrun with ICMP traffic.

  * Note: The above step does not stop a determined ICMP Flood. If there is enough inbound traffic to exhaust the bandwidth between the upstream network provider and the perimeter device filtering ICMP, legitimate traffic may be dropped, or delayed to the point of a DOS. If this is the case, it is necessary to contact the upstream network service provider to have ICMP activity dropped at their level before it reaches your network link.

.. note::
   
   **ICMP Flood Variant Using Reflection: Smurf Attack**
   
   A Smurf attack is an alternate method of carrying out an ICMP Flood attack. In a Smurf attack, the attacker uses the target's IP address as their own, which is called spoofing, and then sends ICMP ping requests to the broadcast IP address of a public network on the Internet. The broadcast IP addresså of a network will send any traffic that it receives to all other IP addresses within its network. Therefore, when the ICMP ping request is received by the broadcast IP address, it is then forwarded on to all live computers on its network. Each of those computers think that these ping requests are coming from the target IP address and therefore send their responses to the target rather than back to the attacker. The result of this is a large number of unsolicited ICMP ping replies being sent to the target of the DDoS, resulting in the consumption of available bandwidth.