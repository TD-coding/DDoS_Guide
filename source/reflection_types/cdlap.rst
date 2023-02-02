CLDAP Reflection Attack with Amplification
==========================================

A Connection-less Lightweight Directory Access Protocol (CLDAP) Reflection Attack with Amplification occurs when an attacker sends a CLDAP request to an LDAP server, using a spoofed sender IP address. CLDAP is used to connect, search, and modify shared Internet directories. It runs over port 389/UDP.

A CLDAP Reflection attack occurs when a cyber threat actor spoofs the victim's IP address and sends a CLDAP query to multiple LDAP servers. The LDAP servers then send the requested data to the spoofed IP address. This unsolicited response is what results in a DDoS attack, as the victim's machine can't process an overabundance of LDAP/CLDAP data at the same time.

The amplification is due to the number of times a packet is enlarged while processed by the LDAP server. LDAP UDP protocol responses are much larger than the initial request with an amplification factor of 52, and can peak at up to a factor of 70.

.. note::
    **TCP LDAP Reflection Attack with Amplification Variant**
    
    The LDAP Reflection Attack with Amplification variant can be used over port 389/TCP. This attack has an amplification factor of 46, and can peak at up to a factor of 55.

Recommendations
---------------

* To identify a CLDAP Reflection Attack with Amplification, investigate your network logs and look for inbound traffic with a source port of 389/UDP.

* Once identified, try to leverage your upstream network service provider and provide them with the attacking IP addresses and the packet sizes used in the attack. Upstream providers have the ability to place a filter at their level.

* Create a DDoS protection plan.

* Along with remediating inbound attacks, take the following preventative measures to ensure that your servers are not used to attack others.

  * Implement ingress firewall rules that restrict unauthorized use of the LDAP server.
  
  * Auditing policies can be used to provide reporting of network services that are potentially exploitable as reflection attacks.

