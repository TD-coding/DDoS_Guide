.. Test_Page documentation master file, created by
   sphinx-quickstart on Wed Feb  1 07:41:27 2023.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Guide to DDoS Attacks 
=====================================

.. WARNING::
   This is a testing page. This guide is under active development and should not be considered an authoritative source.

This Multi-State Information Sharing and Analysis Center (MS-ISAC) document is a guide to aid
partners in their remediation efforts of Distributed Denial of Service (DDoS) attacks. This guide
is not inclusive of all DDoS attack types and references only the types of attacks partners of the
MS-ISAC have reported experiencing.


.. toctree::
   :maxdepth: 1
   :caption: Introduction

   README

.. toctree::
   :maxdepth: 1
   :caption: Standard DDoS Attack Types

   standard_types/syn
   standard_types/udp
   standard_types/smb
   standard_types/icmp
   standard_types/http

.. toctree::
   :maxdepth: 1
   :caption: Reflection DDoS Attack Types

   reflection_types/ntp
   reflection_types/dns
   reflection_types/cdlap
   reflection_types/wordpress
   reflection_types/ssdp
   reflection_types/microsoft

.. toctree::
   :maxdepth: 1
   :caption: Recommendations

   recommendations/recommendations