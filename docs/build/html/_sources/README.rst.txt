Introduction
============
A Denial of Service (DoS) attack is an attempt to make a system unavailable to the intended
user(s), such as preventing access to a website. A successful DoS attack consumes all
available network or system resources, usually resulting in a slowdown or server crash.
Whenever multiple sources are coordinating in the DoS attack, it becomes known as a DDoS
attack.
MS-ISAC regularly observes two methods of DDoS attacks: Standard and Reflection.
A Standard DDoS attack occurs when attackers send a substantial amount of malformed
network traffic directly to a target server or network. One of the ways an attacker can
accomplish this is by using a botnet to send the traffic. A botnet is a large number of victim
computers, or zombies, connected over the Internet, that communicate with each other and can
be controlled from a single location. When an attacker uses a botnet to perform the DDoS
attack, they send instructions to some or all of the zombie machines connected to that botnet,
thereby magnifying the size of their attack, making it originate from multiple networks and
possibly from multiple countries.

.. NOTE::
    Image goes here

A Reflection DDoS attack occurs when attackers spoof their IP address to pose as the intended
victim and then send legitimate requests to legitimate public-facing servers. The responses to
these requests are sent to the intended victim and originate from legitimate servers.
In addition to these methods, a technique used by attackers to increase the effectiveness of
their attack is called Amplification. Usually used in conjunction with Reflection attacks,
Amplification occurs when the response that is sent to the victim is larger than the request that
is sent from the attacker. The attacker is able to orchestrate this by requesting a large amount of
data from a third-party system. As the below drawing illustrates, this might occur when the attacker spoofs its IP address, pretending to be the victim, and requests all known data from a
public server. This results in the attacker sending a request that is small in size, but results in
the public server responding to the victim with a large amount of data.

.. NOTE::
    Image goes here

In addition to the use of botnets, some tools are freely available online that cyber threat actors
can use to perform DDoS attacks. Most of these tools were originally designed to be stress
testers and have since become open source tools used to conduct DDoS attacks by amateur
cyber threat actors. Popular examples of these tools include the Low Orbit Ion Cannon (LOIC)
and the High Orbit Ion Cannon (HOIC). These tools can be downloaded, installed, and utilized
by anyone who wishes to be a part of an ongoing DDoS attack. With the goal of consuming all
available bandwidth allocated to the target, the LOIC sends significant amounts of Transmission
Control Protocol (TCP) and User Datagram Protocol (UDP) traffic, while the HOIC specifically
sends HTTP traffic. Other examples of tools that can be used to perform DDoS activities include
Metasploit, Pyloris, and Slowloris.

.. NOTE::
    Image goes here

While the main purpose behind a DDoS attack is the malicious consumption of resources,
different attackers may use different techniques to generate the traffic necessary for an effective
DDoS. A lone actor with a botnet at their disposal may use that botnet to orchestrate the
attacks. However, botnets are also available for hire, with operators charging minimal fees for
short duration attacks. A group of actors working together may choose to use the same type of
free tool, rather than trying to gain access to a botnet. Attacks like these are usually less
successful, as it is difficult to coordinate enough attackers for the effect to be noticeable