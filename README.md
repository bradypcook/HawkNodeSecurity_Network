# HawkNodeSecurity Network

<p align="center">
  <a href="#overview">Overview</a>
  •
  <a href="#upcoming-features">Upcoming Features</a>
  •
  <a href="#documentation-menu">Documentation Menu</a>
</p>


# Overview

I created a Campus Area Network (CAN) for a hypothetical company (HawkNode Security), where I implemented typical industry practices while designing and configuring the network.

I wanted to do this project to demonstrate my ability to practically set up and configure enterprise networks that I have previously learned while studying for my CCNA.



# Upcoming Features

Here's what's coming in the future (Phase 2 -- Date TBD):

<ul>
<li>Improved addressing between router links (/31) </li>
<li>Access Control Lists </li>
<li>ASA Firewall Devices </li>
<li>NAT (Network Address Translation)</li>
<li>Port Security (for switches) </li>
<li>Restructured branches </li>
<li>FTP instead of TFTP </li>
<li>Email network </li>
<li>Interface Descriptions </li>
<li>and more!! </li>
</ul>


# Documentation Menu

<p align="center">
  <a href="#Network Design/Topology">Network Design/Topology</a>
  •
  <a href="#Router IP Addresses">Router IP Addresses</a>
  •
  <a href="#Host Device IP Addressing">Host Device IP Addressing</a>
   •
  <a href="#WiFi Networks">WiFi Networks</a>
  •
  <a href="#VLAN Information">VLAN Information</a>
  •
  <a href="#Etherchannel Information">Etherchannel Information</a>
  •
  <a href="#Passwords & Security">Passwords & Security</a>
</p>

*A PDF version of the documentation can also be found at the link below:
https://docs.google.com/document/d/1-Vc9t8vtXoVSt0ADlW3ko_1DJ-e-SblX3i97_mBOnME/edit?usp=sharing 


# Network Design/Topology

<img src="https://bradypcook.github.io/hns_logo_addr.png" alt="HawkNode Security Network Toplogy">

The network is set up in a ring configuration, with 2 external links to other branch campuses and 1 internal link to the campus itself. I would rather use a mesh topology; however, the Cisco 2911 routers only offer 3 physical Ethernet ports.

<table aria-describedby="desc">
    <caption id="desc">Network Interfaces &amp; OSPF Summary</caption>
    <thead>
      <tr>
        <th scope="col">Device Name</th>
        <th scope="col">Interface</th>
        <th scope="col">IP Address</th>
        <th scope="col">OSPF Info (Process, Area)</th>
        <th scope="col">Router ID</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Device Name">DC-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">1.1.1.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">1.1.1.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">DC-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">2.2.2.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">DC-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">ATL-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">1.1.1.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">3.3.3.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">ATL-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">3.3.3.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">ATL-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">AUS-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">4.4.4.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">4.4.4.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">AUS-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">3.3.3.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">AUS-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">LA-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">4.4.4.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">5.5.5.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">LA-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">5.5.5.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">LA-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">SLC-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">7.7.7.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">7.7.7.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">SLC-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">5.5.5.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">SLC-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">SEA-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address" class="mono">7.7.7.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID" class="mono">8.8.8.1</td>
      </tr>
      <tr>
        <td data-label="Device Name">SEA-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">8.8.8.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">SEA-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">MIN-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">MIN-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">8.8.8.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">MIN-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address" class="mono">9.9.9.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">NYC-RT</td>
        <td data-label="Interface" class="mono">G0/0</td>
        <td data-label="IP Address">See Network Map</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,1)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">NYC-RT</td>
        <td data-label="Interface" class="mono">G0/1</td>
        <td data-label="IP Address" class="mono">2.2.2.1/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
      <tr>
        <td data-label="Device Name">NYC-RT</td>
        <td data-label="Interface" class="mono">G0/2</td>
        <td data-label="IP Address" class="mono">9.9.9.2/24</td>
        <td data-label="OSPF Info (Process, Area)" class="mono">(1,0)</td>
        <td data-label="Router ID"></td>
      </tr>
    </tbody>
  </table>

# Router IP Addresses

# Host Device IP Addressing

# WiFi Networks

# VLAN Information

# Router IP Addresses

# Etherchannel Information

# Passwords & Security


