HTTP GET Flood
==============

An HTTP GET Flood occurs when an attacker, or attackers, generate a significant number of continuous HTTP GET requests for a target website in an attempt to consume enough resources to make the server unavailable for legitimate users. In this case, the attacking IP addresses never wait for a response from the target server, despite the server attempting to respond to all incoming requests. This results in connections being left open on the web server. A large enough number of incoming HTTP GET requests to the target web server eventually exhausts all available server resources and results in a successful DDoS attack.

Recommendations
---------------

* To identify an HTTP GET Flood, investigate network logs and look for a large number of inbound traffic from a significant number of source IP addresses with a destination port of 80 and a protocol of TCP. The packet data should also begin with “GET”. We recommend using either Tcpdump or Wireshark.

  * HTTP GET requests are normal and are not on their own indicative of malicious activity. Look for a large number of identical GET requests coming from a large number of sources over a short period. The same source IP addresses should re-send the same GET requests rapidly.

* If you identify an attack, leverage a DDoS mitigation service provider for the best results in mitigating this activity.

* It is difficult to set up proactive security measures to block against this attack, as legitimate traffic is used to carry it out. Often, rate based protections are not sufficient to block this attack, and the source IP addresses of the attack are part of a large botnet, so blocking every source IP is not efficient and may include legitimate users.

* One solution that may help mitigate this type of attack is to use a Web Application Firewall (WAF). HTTP Floods often exhibit trends that a correctly configured WAF filters and blocks without blocking legitimate access to the web server.

.. note::
    **HTTP GET Flood Variation: HTTP POST Flood**
   
    Another HTTP Flood incorporates the use of the HTTP POST request instead of GET. This attack works because it forces the web server to allocate more resources in response to each inbound request. A large number of these requests could tie up enough server resources as to deny legitimate users access to the web server
