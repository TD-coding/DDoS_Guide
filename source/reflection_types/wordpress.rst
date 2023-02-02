Wordpress Pingback Reflection Attack with Amplification
=======================================================

WordPress is a popular Content Management System (CMS) that is used to develop and maintain websites and blogs. A function of WordPress sites is called the Pingback feature, which is used to notify other WordPress websites that you have put a link to their website on your site. Sites using WordPress automate this process, and maintain automated lists linking back to sites that link to them. These “pingbacks” are sent as Hypertext Transfer Protocol (HTTP) POST requests to the /xmlrpc.php page, which is used by WordPress to carry out the pingback process. By default, this feature downloads the entire web page that contains the link that triggered the pingback process. An attacker can locate any number of WordPress websites and then send pingback requests to each of them with the URL of the target website, resulting in each of those WordPress websites sending requests to the target server requesting the download of the web page. A large number of requests to download the web page can eventually overload the target web server.

Recommendations
---------------

* To identify a WordPress Pingback Reflection attack with Amplification, investigate your network logs and look for a large number of inbound TCP traffic over port 80 from a large number of sources. The traffic appears as HTTP GET requests for random values such as “?5454545=6767676”. This request bypasses the cache and forces a full-page reload for every packet.

* If you identify an attack, try to leverage your upstream network service provider in order for them to mitigate the activity before it reaches your network.

* At the time of this writing, there is no way to prevent this inbound traffic as on its own it is normal web traffic. However, there is a way to ensure that your WordPress websites are not used to attack others. To do this, WordPress offers a tool that is available for download that disables the pingback feature of XMLRPC. Download the tool at using this `link <http://wordpress.org/plugins/disable-xml-rpc-pingback/>`_

  * Alternatively, you can create a plugin for the website that adds a filter that manually disables the pingback function of XMLRPC. An example of this plugin can be found `here <https://isc.sans.edu/forums/diary/Wordpress+Pingback+DDoS+Attacks/17801>`_  