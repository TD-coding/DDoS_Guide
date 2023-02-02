DNS Reflection Attack with Amplification
========================================
A Domain Name System (DNS) Reflection attack occurs when the attacker manipulates the DNS system to send an overwhelming amount of traffic to the target. DNS servers resolve IP addresses to domain names allowing the average Internet user to type an easily remembered domain name into their Internet browser, rather than remembering the IP addresses of websites. A DNS Reflection attack occurs when an attacker spoofs the victim's IP address and sends DNS name lookup requests to public DNS servers. The DNS server then sends the response to the target server, and the size of the response depends on the options specified by the attacker in their name lookup request. To get the maximum amplification, the attacker can use the word “ANY” in their request, which returns all known information about a DNS zone to a single request. When an attacker spoofs a target's IP address and sends DNS lookup requests to a large number of public DNS servers, the amplified responses are sent back to the target and will eventually result in the consumption of all available bandwidth.

Recommendations
---------------

* To identify if a DNS Reflection Attack with Amplification is occurring, investigate network logs and look for inbound DNS query responses with no matching DNS query requests.

  * DNS queries are normal and are themselves not indicative of an attack.

* If you identify an attack, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* Along with remediating inbound attacks, disable DNS recursion, if possible, by following the guidelines provided by your DNS server vendor (BIND, Microsoft, etc.). In doing so, this ensures that your DNS servers are not used to attack others.

  * Instructions for disabling recursion can also be found at `Team Cymru <http://www.team-cymru.org/Services/Resolvers/instructions.html>`_

  * To discover if any of your public DNS servers may be used to attack others, use the free test at openresolverproject.org. 