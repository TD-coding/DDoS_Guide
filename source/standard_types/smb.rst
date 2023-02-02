SMBLoris
========

A Server Message Block (SMB) SMBLoris attack is an application-level DDoS attack that occurs when a cyber threat actor opens multiple SMB connections to a device, maliciously consuming memory with minimal attack cost. SMB is a remote access protocol used for providing shared access to files, printers, and various communications between devices over port 445. All versions of SMB are vulnerable to SMBLoris, because the vulnerability lies in the way SMB packets are processed and the memory is allocated. Windows and Samba software devices are both susceptible to the attack.

A connection made with a single IPv4 or IPv6 address impacts up to 8GB of memory if an actor sends the attack over both IPv4 and IPv6, which allows for one computer to cause 16GB of memory to be consumed while utilizing only 512 MB of its own memory. Eventually the targeted computer cannot allocate any more memory and forces the Windows computer to become unresponsive, which results in the computer needing to be manually rebooted. If this attack occurs against a Linux device with Samba, the device is forced into its configured Out of Memory (OOM) behavior.

Recommendations
---------------

* To block a remote SMBLoris attack from occurring, configure the border firewall to block all ingress traffic over ports 445 and 139.

* To block an internal SMBLoris attack from occurring, set an artificial rate limit for the number of connections local devices can have open.