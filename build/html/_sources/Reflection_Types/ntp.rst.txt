NTP Reflection Attack with Amplification
========================================
A Network Time Protocol (NTP) reflection attack occurs when the attacker uses traffic from a legitimate NTP server to overwhelm the resources of the target. NTP is used to synchronize clocks on networked machines and runs over port 123/UDP. An obscure command, monlist, allows a requesting computer to receive information regarding the last 600 connections to the NTP server. An attacker can spoof the target's IP address and send a monlist command to request that the NTP server send a large amount of information to the target. These responses typically have a fixed packet size that can be identified across a large number of replies. Since the response from the NTP server is larger than the request sent from the attacker, the effect of the attack is amplified. When an attacker spoofs the target's IP address and then sends the monlist command to a large number of Internet-facing NTP servers, the amplified responses are sent back to the target. This eventually results in the consumption of all available bandwidth.

Recommendations
---------------
* To identify a NTP Reflection Attack with Amplification, investigate your network logs and look for inbound traffic with a source port of 123/UDP and a specific packet size.

* Once identified, try to leverage your upstream network service provider and provide them with the attacking IP addresses and the packet sizes used in the attack. Upstream providers have the ability to place a filter at their level that forces inbound NTP traffic, using the specific packet size that you are experiencing, to drop.

* Along with remediating inbound attacks, take the following preventative measures to ensure that your NTP servers are not used to attack others.

  * If you are unsure whether or not your NTP server is vulnerable to being utilized in an attack, follow the instructions available at OpenNTP: hxxp://openntpproject.org/.

  * Upgrade NTP servers to version 2.4.7 or later, which removes the monlist command entirely, or implement a version of NTP that does not utilize the monlist command, such as OpenNTPD.
  
  * If you are unable to upgrade your server, disable the monlist query feature by adding “disable monitor” to your ntp.conf file and restarting the NTP process.
  
  * Implement firewall rules that restrict unauthorized traffic to the NTP server.