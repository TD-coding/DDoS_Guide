Microsoft SQL Reflection Attack with Amplification
==================================================

Microsoft (MS) Structured Query Language (SQL) is a popular application used to manage relational databases. Database servers using MS SQL are sometimes left on external IP addresses so that they can be accessed remotely over the Internet. A MS SQL reflection attack occurs when an attacker spoofs the target's IP address and then sends crafted requests to public-facing MS SQL servers using the MS SQL Server Resolution Protocol (MC-SQLR), which listens on port 1434/UDP. The response from the database server contains information about the database instances running on the server as well as how to connect to each one. Depending on the configuration of the database server, and the number of database instances on the server, the response to the client request could be amplified by a factor of 25 for a single request.

Attackers can send scripted MC-SQLR requests, spoofing the target's IP address, to a large number of public-facing MS SQL servers. The amplified responses are sent back to the target, possibly resulting in the consumption of all of the target's available bandwidth.

Recommendations
---------------

* To identify if a MS SQL Reflection Attack with Amplification is occurring, investigate network logs and look for inbound source port 1434/UDP (MC-SQLR) traffic from a large number of source IP addresses. In some instances, it may be possible to identify a particular payload signature.

* If you identify an attack, try to leverage your upstream provider in order for them to mitigate the activity before it reaches your network.

* If possible, block inbound connections to port 1434/UDP or filter connections to allow only trusted IP addresses.

* Along with mitigating inbound attacks, take the following steps to prevent your MS SQL server from being used as a reflector in attacks against others:

  * Use ingress and egress filters on firewalls to block SQL server ports. Port 1434/UDP should be open only if there is an identified need for the service. If the port is open, it is recommended that traffic be filtered to allow only trusted IP addresses.

  * SQL servers that have only one database instance running do not need to run MS-SQLR. If you are running only one database instance, disable MS-SQLR.

As of Microsoft SQL Server 2008 the feature is disabled by default. However, earlier versions require administrators to disable this service manually. If you are running an older version of the software and there is not a need for MS-SQLR, disable it. If it is determined that MS-SQLR is needed, consider adding an additional layer of security, such as requiring authentication via SSH or VPN, in front of the service.