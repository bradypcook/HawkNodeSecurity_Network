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
  <a href="#network-designtopology">Network Design/Topology</a>
  •
  <a href="#router-ip-addresses">Router IP Addresses</a>
  •
  <a href="#host-device-ip-addressing">Host Device IP Addressing</a>
   •
  <a href="#wifi-networks">WiFi Networks</a>
  •
  <a href="#vlan-information">VLAN Information</a>
  •
  <a href="#etherchannel-information">Etherchannel Information</a>
  •
  <a href="#passwords--security">Passwords & Security</a>
</p>

*A PDF version of the documentation can also be found at the link below:
https://docs.google.com/document/d/1-Vc9t8vtXoVSt0ADlW3ko_1DJ-e-SblX3i97_mBOnME/edit?usp=sharing 


# Network Design/Topology

<img src="https://bradypcook.github.io/hns_logo_addr.png" alt="HawkNode Security Network Toplogy">

The network is set up in a ring configuration, with 2 external links to other branch campuses and 1 internal link to the campus itself. I would rather use a mesh topology; however, the Cisco 2911 routers only offer 3 physical Ethernet ports.

# Router IP Addresses

<table aria-describedby="desc">
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

# Host Device IP Addressing

As shown above on the map, the IP Addressing follows a scheme where each campus branch has its own host portion of the IP; so for example the Austin branch has an IP of X.X.X.3, where the last bit makes up the portion that the hosts use (except for the NYC office, which has X.X.0.0). In terms of the network portion of the address, each VLAN has its own network portion (i.e. Floor1 has a network address of 1X.1X.1X.X and IOT-Devices has a network address of 7X.7X.7X.X)

The following networks are correlated to the following VLANs:

<table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">VLAN Name</th>
        <th scope="col">Network IP Address</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="VLAN Name">Floor1</td>
        <td data-label="Network IP Address" class="mono">1X.1X.1X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor2</td>
        <td data-label="Network IP Address" class="mono">2X.2X.2X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor3</td>
        <td data-label="Network IP Address" class="mono">3X.3X.3X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor4</td>
        <td data-label="Network IP Address" class="mono">4X.4X.4X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor5</td>
        <td data-label="Network IP Address" class="mono">5X.5X.5X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Wireless-Devices</td>
        <td data-label="Network IP Address" class="mono">6X.6X.6X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">IOT-Devices</td>
        <td data-label="Network IP Address" class="mono">7X.7X.7X.X</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Management</td>
        <td data-label="Network IP Address" class="mono">10X.10X.10X.X</td>
      </tr>
    </tbody>
  </table>


  Additionally, the addressing information for the company servers is below (NOTE: Static IPs are configured for the servers to prevent DHCP issues)

  <table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">Server Name</th>
        <th scope="col">IP Address</th>
        <th scope="col">Subnet Mask</th>
        <th scope="col">Default Gateway</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Server Name">Web-Server</td>
        <td data-label="IP Address" class="mono">23.23.23.2</td>
        <td data-label="Subnet Mask" class="mono">255.255.255.0</td>
        <td data-label="Default Gateway" class="mono">23.23.23.1</td>
      </tr>
      <tr>
        <td data-label="Server Name">File-Server</td>
        <td data-label="IP Address" class="mono">23.23.23.3</td>
        <td data-label="Subnet Mask" class="mono">255.255.255.0</td>
        <td data-label="Default Gateway" class="mono">23.23.23.1</td>
      </tr>
      <tr>
        <td data-label="Server Name">Backup_Server_1</td>
        <td data-label="IP Address" class="mono">20.20.0.1</td>
        <td data-label="Subnet Mask" class="mono">255.255.0.0</td>
        <td data-label="Default Gateway" class="mono">20.20.20.1</td>
      </tr>
      <tr>
        <td data-label="Server Name">Backup_Server_2</td>
        <td data-label="IP Address" class="mono">24.24.24.2</td>
        <td data-label="Subnet Mask" class="mono">255.255.255.0</td>
        <td data-label="Default Gateway" class="mono">24.24.24.1</td>
      </tr>
    </tbody>
  </table>

# WiFi Networks

All WiFi networks have a randomly generated password, signal strength of 250 meters, use AES encryption, and have a naming scheme with the following: [BRANCH]-HNS

<table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">Network Name</th>
        <th scope="col">Password</th>
        <th scope="col">2.4 GHz Channel</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Network Name">LA-HNS</td>
        <td data-label="Password" class="mono">tiYLkcO0YnN07^</td>
        <td data-label="2.4 GHz Channel" class="mono">11</td>
      </tr>
      <tr>
        <td data-label="Network Name">SLC-HNS</td>
        <td data-label="Password" class="mono">AhdjtZW@!7pI3N</td>
        <td data-label="2.4 GHz Channel" class="mono">10</td>
      </tr>
      <tr>
        <td data-label="Network Name">Seattle-HNS</td>
        <td data-label="Password" class="mono">fLW%#4K9DTqMoJ</td>
        <td data-label="2.4 GHz Channel" class="mono">8</td>
      </tr>
      <tr>
        <td data-label="Network Name">MIN-HNS</td>
        <td data-label="Password" class="mono">Yf4#FNXe!OGyDm</td>
        <td data-label="2.4 GHz Channel" class="mono">7</td>
      </tr>
      <tr>
        <td data-label="Network Name">NYC-HNS</td>
        <td data-label="Password" class="mono">w%x@6oPh^G1@2S</td>
        <td data-label="2.4 GHz Channel" class="mono">6</td>
      </tr>
      <tr>
        <td data-label="Network Name">WashDC-HNS</td>
        <td data-label="Password" class="mono">jw5n$TS%802OT5</td>
        <td data-label="2.4 GHz Channel" class="mono">3</td>
      </tr>
      <tr>
        <td data-label="Network Name">Atlanta-HNS</td>
        <td data-label="Password" class="mono">cOjw7JNTR8o^CY</td>
        <td data-label="2.4 GHz Channel" class="mono">2</td>
      </tr>
      <tr>
        <td data-label="Network Name">Austin-HNS</td>
        <td data-label="Password" class="mono">7r53fAJH2%*cPr</td>
        <td data-label="2.4 GHz Channel" class="mono">1</td>
      </tr>
    </tbody>
  </table>

# VLAN Information

<table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">VLAN Name</th>
        <th scope="col">VLAN ID</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="VLAN Name">Floor1</td>
        <td data-label="VLAN ID" class="mono">10</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor2</td>
        <td data-label="VLAN ID" class="mono">20</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor3</td>
        <td data-label="VLAN ID" class="mono">30</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor4</td>
        <td data-label="VLAN ID" class="mono">40</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Floor5</td>
        <td data-label="VLAN ID" class="mono">50</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Native</td>
        <td data-label="VLAN ID" class="mono">55</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Wireless-Devices</td>
        <td data-label="VLAN ID" class="mono">60</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">IOT-Devices</td>
        <td data-label="VLAN ID" class="mono">70</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Voice-Traffic</td>
        <td data-label="VLAN ID" class="mono">75</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Management</td>
        <td data-label="VLAN ID" class="mono">100</td>
      </tr>
      <tr>
        <td data-label="VLAN Name">Non_Allocated_Ports</td>
        <td data-label="VLAN ID" class="mono">200</td>
      </tr>
    </tbody>
  </table>

# Etherchannel Information

All etherchannels are configured in PAgP (Cisco proprietary EtherChannel protocol)
**NOTE: Group Number 4 is only present in the LA branch
<table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">Interface Range</th>
        <th scope="col">Group Number</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Interface Range" class="mono">f0/1-3</td>
        <td data-label="Group Number" class="mono">1</td>
      </tr>
      <tr>
        <td data-label="Interface Range" class="mono">f0/4-6</td>
        <td data-label="Group Number" class="mono">2</td>
      </tr>
      <tr>
        <td data-label="Interface Range" class="mono">f0/7-9</td>
        <td data-label="Group Number" class="mono">3</td>
      </tr>
      <tr>
        <td data-label="Interface Range" class="mono">f0/10-12**</td>
        <td data-label="Group Number" class="mono">4**</td>
      </tr>
    </tbody>
  </table>

# Passwords & Security

Login Block (Router ONLY)
*All login blocks will be set for the following format:
 login block-for [180 seconds] attempts [3] within [60 seconds]

Network Address Translation (Router ONLY)
Configuration items TBD

Access Control Lists (Router ONLY)
Configuration items TBD

Switchport Security (Switch ONLY)
Configuration items TBD

Console/Enable Mode Passwords
*Follow this format: RoleAbbr-SiteDevice
*COMMENT: While I know these passwords aren’t as secure, they follow this format for configuration purposes (as it would be difficult to remember random passwords for the entire network) 

 <table aria-describedby="desc">
    <thead>
      <tr>
        <th scope="col">Console Mode Password</th>
        <th scope="col">Device Name</th>
        <th scope="col">Enable Mode Password</th>
      </tr>
    </thead>
    <tbody>
      <tr><td data-label="Console Mode Password">Con-NYCRT</td><td data-label="Device Name">NYC-RT</td><td data-label="Enable Mode Password">Enb-NYCRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-NYCS1</td><td data-label="Device Name">NYC-S1</td><td data-label="Enable Mode Password">Enb-NYCS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-NYCS2</td><td data-label="Device Name">NYC-S1</td><td data-label="Enable Mode Password">Enb-NYCS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-NYCS3</td><td data-label="Device Name">NYC-S3</td><td data-label="Enable Mode Password">Enb-NYCS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-NYCS4</td><td data-label="Device Name">NYC-S4</td><td data-label="Enable Mode Password">Enb-NYCS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-DCRT</td><td data-label="Device Name">DC-RT</td><td data-label="Enable Mode Password">Enb-DCRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-DCS1</td><td data-label="Device Name">DC-S1</td><td data-label="Enable Mode Password">Enb-DCS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-DCS2</td><td data-label="Device Name">DC-S2</td><td data-label="Enable Mode Password">Enb-DCS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-DCS3</td><td data-label="Device Name">DC-S3</td><td data-label="Enable Mode Password">Enb-DCS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-DCS4</td><td data-label="Device Name">DC-S4</td><td data-label="Enable Mode Password">Enb-DCS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-ATLRT</td><td data-label="Device Name">ATL-RT</td><td data-label="Enable Mode Password">Enb-ATLRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-ATLS1</td><td data-label="Device Name">ATL-S1</td><td data-label="Enable Mode Password">Enb-ATLS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-ATLS2</td><td data-label="Device Name">ATL-S2</td><td data-label="Enable Mode Password">Enb-ATLS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-ATLS3</td><td data-label="Device Name">ATL-S3</td><td data-label="Enable Mode Password">Enb-ATLS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-ATLS4</td><td data-label="Device Name">ATL-S4</td><td data-label="Enable Mode Password">Enb-ATLS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-AUSRT</td><td data-label="Device Name">AUS-RT</td><td data-label="Enable Mode Password">Enb-AUSRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-AUSS1</td><td data-label="Device Name">AUS-S1</td><td data-label="Enable Mode Password">Enb-AUSS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-AUSS2</td><td data-label="Device Name">AUS-S2</td><td data-label="Enable Mode Password">Enb-AUSS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-AUSS3</td><td data-label="Device Name">AUS-S3</td><td data-label="Enable Mode Password">Enb-AUSS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-AUSS4</td><td data-label="Device Name">AUS-S4</td><td data-label="Enable Mode Password">Enb-AUSS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-LART</td><td data-label="Device Name">LA-RT</td><td data-label="Enable Mode Password">Enb-LART</td></tr>
      <tr><td data-label="Console Mode Password">Con-LAS1</td><td data-label="Device Name">LA-S1</td><td data-label="Enable Mode Password">Enb-LAS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-LAS2</td><td data-label="Device Name">LA-S2</td><td data-label="Enable Mode Password">Enb-LAS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-LAS3</td><td data-label="Device Name">LA-S3</td><td data-label="Enable Mode Password">Enb-LAS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-LAS4</td><td data-label="Device Name">LA-S4</td><td data-label="Enable Mode Password">Enb-LAS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-LAS5</td><td data-label="Device Name">LA-S5</td><td data-label="Enable Mode Password">Enb-LAS5</td></tr>
      <tr><td data-label="Console Mode Password">Con-SLCRT</td><td data-label="Device Name">SLC-RT</td><td data-label="Enable Mode Password">Enb-SLCRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-SLCS1</td><td data-label="Device Name">SLC-S1</td><td data-label="Enable Mode Password">Enb-SLCS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-SLCS2</td><td data-label="Device Name">SLC-S2</td><td data-label="Enable Mode Password">Enb-SLCS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-SLCS3</td><td data-label="Device Name">SLC-S3</td><td data-label="Enable Mode Password">Enb-SLCS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-SLCS4</td><td data-label="Device Name">SLC-S4</td><td data-label="Enable Mode Password">Enb-SLCS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-SEART</td><td data-label="Device Name">SEA-RT</td><td data-label="Enable Mode Password">Enb-SEART</td></tr>
      <tr><td data-label="Console Mode Password">Con-SEAS1</td><td data-label="Device Name">SEA-S1</td><td data-label="Enable Mode Password">Enb-SEAS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-SEAS2</td><td data-label="Device Name">SEA-S2</td><td data-label="Enable Mode Password">Enb-SEAS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-SEAS3</td><td data-label="Device Name">SEA-S3</td><td data-label="Enable Mode Password">Enb-SEAS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-SEAS4</td><td data-label="Device Name">SEA-S4</td><td data-label="Enable Mode Password">Enb-SEAS4</td></tr>
      <tr><td data-label="Console Mode Password">Con-MINRT</td><td data-label="Device Name">MIN-RT</td><td data-label="Enable Mode Password">Enb-MINRT</td></tr>
      <tr><td data-label="Console Mode Password">Con-MINS1</td><td data-label="Device Name">MIN-S1</td><td data-label="Enable Mode Password">Enb-MINS1</td></tr>
      <tr><td data-label="Console Mode Password">Con-MINS2</td><td data-label="Device Name">MIN-S2</td><td data-label="Enable Mode Password">Enb-MINS2</td></tr>
      <tr><td data-label="Console Mode Password">Con-MINS3</td><td data-label="Device Name">MIN-S3</td><td data-label="Enable Mode Password">Enb-MINS3</td></tr>
      <tr><td data-label="Console Mode Password">Con-MINS4</td><td data-label="Device Name">MIN-S4</td><td data-label="Enable Mode Password">Enb-MINS4</td></tr>
    </tbody>
  </table>
