General Recommendations and Mitigation Strategies
=================================================
The following generic recommendations for DDoS mitigation, can reduce the impact of attempted DDoS attacks and enable a faster response when successful DDoS attacks occur.

* Establish and maintain effective partnerships with your upstream network service provider and know what assistance they may be able to provide you in the event of a DDoS attack. In the case of a DDoS attack, the faster a provider can implement traffic blocks and mitigation strategies at their level, the sooner your services will become available for legitimate users.

* Consider also establishing relationships with companies who offer DDoS mitigation services.

* If you are experiencing a DDoS attack, provide the attacking IP addresses to your upstream network service provider so they can implement restrictions at their level. Keep in mind that Reflection DDoS attacks typically originate from legitimate public servers. It is important to ascertain to whom an IP belongs to when examining network logs during an attack. Use tools such as the American Registry for Internet Numbers (ARIN) (https://www.arin.net) to look up the source IPs involved in the attack. Otherwise, you may block traffic from legitimate networks or servers.

* Enable firewall logging of accepted and denied traffic to determine where the DDoS may be originating.

* Define strict “TCP keepalive” and “maximum connection” on all perimeter devices, such as firewalls and proxy servers. This recommendation assists with keeping SYN Flood attacks from being successful.

* Consider port and packet size filtering by the upstream network service provider.

* Establish and regularly validate baseline traffic patterns (volume and type) for public-facing websites.

* Apply all vendor patches after appropriate testing

* Configure firewalls to block, as a minimum, inbound traffic sourced from IP addresses that are reserved (0/8), loopback (127/8), private (RFC 1918 blocks 10/8, 172.16/12, and (92.168/16), unassigned DHCP clients (169.254.0.0/16), multicast (224.0.0.0/4) and otherwise listed in RFC 5735. This configuration should also be requested at the ISP level.

* Tune public-facing server processes to allow the minimum amount of processes or connections necessary to effectively conduct business.

* Configure firewalls and intrusion detection/prevention devices to alarm on traffic anomalies.

* Configure firewalls only to accept traffic detailed in your organization’s security policy as required for business purposes.

* Consider setting up Out-of-Band access, Internet and telephony, to an incident management room to ensure connection in the event of a DDoS attack that disrupts normal connectivity.

.. NOTE::

    The MS-ISAC is the focal point for cyber threat prevention, protection, response and recovery for the nation's state, local, tribal, and territorial (SLTT) governments. 
    The MS-ISAC 24x7 cyber security operations center provides real-time network monitoring, early cyber threat warnings and advisories, vulnerability identification and mitigation and incident response. 
    For more information please visit http://msisac.cisecurity.org/