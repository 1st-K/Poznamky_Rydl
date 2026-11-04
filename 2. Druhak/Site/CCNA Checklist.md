# 1 Network fundamentals
## 1.1 Network components
- [ ] **Router** - co dela, routing mezi sitemi
- [ ] **Layer 2 switch** - switching podle MAC
- [ ] **Layer 3 switch** - switching + routing
- [ ] **Layer 3 switch** — switching + routing
- [ ] **Next-generation firewall** — základní funkce
- [ ] **IPS** — Intrusion Prevention System
- [ ] **Access Point** — role AP
- [ ] **Controllers** — zejména WLC / network controller
- [ ] **Endpoints** — počítače, telefony, tiskárny atd.
- [ ] **Servers** — role serverů
- [ ] **PoE** — Power over Ethernet

## 1.2 Network topologies/architectures
- [ ] **WAN**
- [ ] **Two-tier architecture**
- [ ] **Three-tier architecture**
- [ ] **Spine-leaf architecture**
- [ ] **SOHO**
- [ ] **On-premises vs cloud**

## 1.3 Physical interfaces and cabling
- [ ] **Copper Ethernet**
- [ ] **Single-mode fiber**
- [ ] **Multimode fiber**
- [ ] **Ethernet shared media**
- [ ] **Point-to-point connection**
- [ ] **Rozdíl mezi single-mode a multimode**
- [ ] **Kdy použít copper/fiber**
- [ ] **Základní Ethernet konektory/transceivery**

## 1.4 Interface/cable issues
- [ ] **Speed**
- [ ] **Duplex**
- [ ] **Duplex mismatch**
- [ ] **Collisions**
- [ ] **Interface errors**
- [ ] **Jak poznat problém přes** `show interfaces`
- [ ] **Jak souvisí half/full duplex s collisions**

## 1.5 TCP vs UDP
- [ ] **TCP**
- [ ] **UDP**
- [ ] **TCP reliability**
- [ ] **TCP acknowledgements**
- [ ] **TCP retransmission**
- [ ] **TCP ordering**
- [ ] **TCP flow/congestion control**
- [ ] **UDP bez reliability/retransmission**
- [ ] **Umět vysvětlit, *proč* aplikace používá TCP vs UDP**

## 1.6 IPv4 addressing and subnetting
- [ ] **IPv4 adresa**
- [ ] **Subnet mask**
- [ ] **CIDR** `/24`, `/16`, `/30`, ...
- [ ] **Výpočet network address**
- [ ] **Výpočet broadcast address**
- [ ] **Výpočet usable host range**
- [ ] **Počet hostů v subnetu**
- [ ] **Počet subnetů**
- [ ] **Subnetování podle počtu hostů**
- [ ] **VLSM**
- [ ] **Převody masky ↔ prefix**
- [ ] **Binary subnetting**
- [ ] **Praktické subnetting úlohy bez kalkulačky**
- [ ] **Konfigurace IPv4 na routeru**
- [ ] **Ověření pomocí** `show ip interface brief`

## 1.7 Private IPv4
- [ ] `10.0.0.0/8`
- [ ] `172.16.0.0/12`
- [ ] `192.168.0.0/16`
- [ ] **Private vs public IPv4**
- [ ] **Proč existují private adresy**
- [ ] **Jak souvisí private IPv4 s NAT**

## 1.8 IPv6
- [ ] **IPv6 syntax**
- [ ] **IPv6 prefix**
- [ ] **IPv6 interface address**
- [ ] **Konfigurace IPv6 na interface**
- [ ] `show ipv6 interface`
- [ ] **IPv6 subnet/prefix basics**
- [ ] **IPv6 default gateway**

## 1.9 IPv6 address types
- [ ] **Global Unicast**
- [ ] **Unique Local**
- [ ] **Link-Local**
- [ ] **Multicast**
- [ ] **Anycast**
- [ ] **Modified EUI-64**
- [ ] **Rozpoznat typ IPv6 adresy podle prefixu**

## 1.10 Client IP parameters
**Umět zjistit konfiguraci na:**
- [ ] **Windows**
- [ ] **macOS**
- [ ] **Linux**
- [ ] **IP address**
- [ ] **Subnet mask/prefix**
- [ ] **Default gateway**
- [ ] **DNS server**
- [ ] **DHCP**
- [ ] **IPv6 informace**

## 1.11 Wireless principles
- [ ] **Wi-Fi základní princip**
- [ ] **SSID**
- [ ] **RF — radio frequency**
- [ ] **Wi-Fi channels**
- [ ] **Non-overlapping channels**
- [ ] **2.4 GHz vs 5 GHz**
- [ ] **Interference**
- [ ] **Wireless encryption**
- [ ] **AP vs wireless controller**

## 1.12 Virtualization
- [ ] **Server virtualization**
- [ ] **VM**
- [ ] **Hypervisor**
- [ ] **Containers**
- [ ] **Rozdíl VM vs container**
- [ ] **VRF — Virtual Routing and Forwarding**
- [ ] **Proč VRF umožňuje oddělené routing tables**

## 1.13 Switching concepts
- [ ] **MAC address**
- [ ] **Switch**
- [ ] **Frame**
- [ ] **MAC address table**
- [ ] **MAC learning**
- [ ] **MAC aging**
- [ ] **Frame switching**
- [ ] **Frame flooding**
- [ ] **Unknown unicast**
- [ ] **Broadcast**
- [ ] **Jak switch zjistí, kam frame poslat**

---
# 2 Network Access

## 2.1 VLANs
- [ ] **VLAN
- [ ] **VLAN ID
- [ ] **Access port
- [ ] `switchport mode access`
- [ ] `switchport access vlan`
- [ ] **VLAN creation**
- [ ] **VLAN name**
- [ ] **VLAN across multiple switches**
- [ ] **Voice VLAN**
- [ ] **Default VLAN**
- [ ] **Inter-VLAN connectivity**
- [ ] **SVI**
- [ ] **VLAN ↔ subnet relationship**
### IOS
- [ ] `vlan 10`
- [ ] `name STUDENTS`
- [ ] `switchport mode access`
- [ ] `switchport access vlan 10`
- [ ] `interface vlan 10`
- [ ] `ip address ...`
- [ ] `show vlan brief`

## 2.2 Trunks
- [ ] **Trunk**
- [ ] `switchport mode trunk`
- [ ] **802.1Q**
- [ ] **Allowed VLANs**
- [ ] `show interfaces trunk`
- [ ] **Native VLAN**
- [ ] **Native VLAN mismatch**
- [ ] **Proč trunk přenáší více VLAN**
- [ ] **Jak switch pozná VLAN z 802.1Q tagu**

## 2.3 Layer 2 discovery
- [ ] **CDP**
- [ ] **LLDP**
- [ ] **Rozdíl CDP vs LLDP**
- [ ] **Konfigurace CDP**
- [ ] **Konfigurace LLDP**
- [ ] **Ověření sousedů**
- [ ] `show cdp neighbors`
- [ ] `show lldp neighbors`

## 2.4 EtherChannel / LACP
- [ ] **EtherChannel**
- [ ] **Proč se používá**
- [ ] **LACP**
- [ ] **Link aggregation**
- [ ] **Layer 2 EtherChannel**
- [ ] **Layer 3 EtherChannel**
- [ ] **Port-channel**
- [ ] **Konfigurace LACP**
- [ ] **Ověření EtherChannel**
- [ ] **Co se stane, když mají členové různé konfigurace**

## 2.5 Rapid PVST+
- [ ]  **Proč vzniká Layer 2 loop**
- [ ]  **Spanning Tree Protocol**
- [ ]  **Rapid PVST+**
- [ ]  **Root bridge**
- [ ]  **Root bridge election**
- [ ]  **Root port**
- [ ]  **Designated port**
- [ ]  **Alternate port**
- [ ]  **Port roles**
- [ ]  **Port states**
- [ ]  **Root bridge priority**
- [ ]  **Primary root**
- [ ]  **Secondary root**
- [ ]  **BPDU**
- [ ]  **PortFast**
- [ ]  **BPDU Guard**
- [ ]  **BPDU Filter**
- [ ]  **Root Guard**
- [ ]  **Loop Guard**
- [ ]  **Proč PortFast není pro běžný switch-to-switch link**
- [ ]  **Jak STP zabrání smyčce**

## 2.6 Wireless architecture
- [ ] **Autonomous AP**
- [ ] **Lightweight AP**
- [ ] **WLC**
- [ ] **AP modes**
- [ ] **Cisco wireless architecture**
- [ ] **AP ↔ switch**
- [ ] **WLC ↔ switch**
- [ ] **Access/trunk vztah**
- [ ] **LAG**

## 2.7 WLAN physical infrastructure
- [ ]  **AP připojený do access portu**
- [ ]  **AP připojený do trunku**
- [ ]  **WLC connectivity**
- [ ]  **LAG**
- [ ]  **VLANs pro WLAN**
- [ ]  **Jak se klient dostane z Wi-Fi přes AP do switch infrastruktury**

## 2.8 Device management access
- [ ] **Console**
- [ ] **Telnet**
- [ ] **SSH**
- [ ] **HTTP management**
- [ ] **HTTPS management**
- [ ] **Local authentication**
- [ ] **TACACS+**
- [ ] **RADIUS**
- [ ] **Cloud-managed devices**
- [ ] **Vysvětlit rozdíl mezi authentication / authorization**
- [ ] **Bezpečný remote management přes SSH**

## 2.9 Wireless GUI
- [ ] **WLAN creation**
- [ ] **SSID configuration**
- [ ] **Security settings**
- [ ] **WPA2 PSK**
- [ ] **QoS profiles**
- [ ] **Advanced WLAN settings**
- [ ] **Základní orientace ve WLC GUI**

---
# 3 IP Connectivity

## 3.1 Routing table
- [ ] **Routing table**
- [ ] `show ip route`
- [ ] **Routing protocol code**
- [ ] **Prefix**
- [ ] **Network mask**
- [ ] **Next hop**
- [ ] **Administrative distance**
- [ ] **Metric**
- [ ] **Gateway of last resort**
- [ ] **Connected route**
- [ ] **Local route**
- [ ] **Static route**
- [ ] **OSPF route**

## 3.2 Forwarding decision
- [ ] **Jak router vybírá route**
- [ ] **Longest Prefix Match**
- [ ] **Administrative Distance**
- [ ] **Routing protocol metric**
- [ ] **Co když existuje více cest**
- [ ] **Proč**`/24` **může vyhrát nad** `/16`
- [ ] **Jak router najde next-hop/interface**

## 3.3 Static routing
- [ ] **Default route**
- [ ] **Network route**
- [ ] **Host route** `/32`
- [ ] **Floating static route**
- [ ] **IPv4 static route**
- [ ] **IPv6 static route**
- [ ] **Verify static routes**
- [ ] **Next-hop vs exit-interface**
- [ ] **Administrative distance u floating static**

## 3.4 OSPFv2
- [ ] **Co je OSPF**
- [ ] **Link-state routing**
- [ ] **OSPFv2**
- [ ] **Single-area OSPF**
- [ ] **Area 0**
- [ ] **Neighbor adjacency**
- [ ] **OSPF neighbors**
- [ ] **Router ID**
- [ ] **OSPF network types**
- [ ] **Point-to-point**
- [ ] **Broadcast**
- [ ] **DR**
- [ ] **BDR**
- [ ] **DR/BDR election**
- [ ] **OSPF metric / cost**
- [ ] **OSPF route**
- [ ] **Passive interface**
- [ ] **OSPF verification**
- [ ] **Základní konfigurace OSPF**

## 3.5 First-hop redundancy
- [ ]  **Co je FHRP**
- [ ]  **Proč existuje**
- [ ]  **Virtuální gateway**
- [ ]  **Redundantní default gateway**
- [ ]  **HSRP — alespoň princip**
- [ ]  **VRRP — alespoň princip**
- [ ]  **GLBP — alespoň vědět, co to je**

---

# 4 IP Services

## 4.1 NAT
- [ ] **NAT**
- [ ] **Inside source NAT**
- [ ] **Static NAT**
- [ ] **NAT pool**
- [ ] **Dynamic NAT**
- [ ] **PAT / NAT overload**
- [ ] **Inside local**
- [ ] **Inside global**
- [ ] **Outside local/global — alespoň koncept**
- [ ] **Konfigurace static NAT**
- [ ] **Konfigurace dynamic NAT**
- [ ] **Konfigurace PAT**
- [ ] **Ověření NAT**

## 4.2 NTP
- [ ] **Co je NTP**
- [ ] **Proč potřebujeme synchronizovaný čas**
- [ ] **NTP client**
- [ ] **NTP server**
- [ ] **Konfigurace NTP**
- [ ] **Ověření NTP**

## 4.3 DHCP + DNS
- [ ] **DHCP**
- [ ] **DHCP pool**
- [ ] **Network**
- [ ] **Default router**
- [ ] **DNS server**
- [ ] **DHCP client**
- [ ] **DHCP relay**
- [ ] `ip helper-address`
- [ ] **DNS**
- [ ] **DNS records**
- [ ] **DNS resolution**
- [ ] **DHCP DORA**

## 4.4 SNMP
- [ ] **Co je SNMP**
- [ ] **Monitoring network devices**
- [ ] **SNMP manager**
- [ ] **SNMP agent**
- [ ] **SNMP polling**
- [ ] **SNMP traps**
- [ ] **Základní rozdíl SNMPv2c vs SNMPv3**

## 4.5 Syslog
- [ ] **Co je Syslog**
- [ ] **Syslog server**
- [ ] **Syslog message**
- [ ] **Severity levels**
- [ ] **Facility**
- [ ] **Lokální logging**
- [ ] **Remote logging**

## 4.6 DHCP client + relay
- [ ] **Router jako DHCP client**
- [ ] **Switch/router jako DHCP relay**
- [ ] **`ip helper-address`**
- [ ] **DHCP server v jiné subnet/VLAN**
- [ ] **Jak DHCP broadcast překoná router**

## 4.7 QoS
- [ ]  **QoS**
- [ ]  **Classification**
- [ ]  **Marking**
- [ ]  **Queuing**
- [ ]  **Congestion**
- [ ]  **Policing**
- [ ]  **Shaping**
- [ ]  **PHB — Per-Hop Behavior**
- [ ]  **Proč QoS *nezvyšuje bandwidth*, ale řídí provoz**

## 4.8 SSH
- [ ] **SSH**
- [ ] **VTY**
- [ ] **Local username**
- [ ] `login local`
- [ ] `transport input ssh`
- [ ] `ip domain-name`
- [ ] **RSA keys**
- [ ] **SSH version**
- [ ] **Ověřit SSH konfiguraci**
- [ ] **Proč Telnet není vhodný pro bezpečnou správu**

## 4.9 TFTP / FTP
- [ ] **FTP**
- [ ] **FTP**
- [ ] **K čemu se používá TFTP**
- [ ] **IOS image transfer**
- [ ] **Config backup**
- [ ] **Config restore**
- [ ] **Rozdíl FTP vs TFTP**
- [ ] `copy ... tftp:`
- [ ] `copy ... ftp:`

---
# 5.0 Security Fundamentals
## 5.1 Security concepts
- [ ] **Threat**
- [ ] **Vulnerability**
- [ ] **Exploit**
- [ ] **Mitigation**
- [ ] **Malware**
- [ ] **Phishing**
- [ ] **DoS / DDoS**
- [ ] **Spoofing**
- [ ] **Social engineering**
- [ ] **Password attacks**
- [ ] **Network attacks**
- [ ] **Basic mitigation techniques**

## 5.2 Security program
- [ ] **User awareness**
- [ ] **Security training**
- [ ] **Physical access control**
- [ ] **Security policies**
- [ ] **Least privilege**
- [ ] **Incident awareness**

## 5.3 Device access control
- [ ] **Console password**
- [ ] **VTY password**
- [ ] `enable secret`
- [ ] **Local authentication**
- [ ] **Local username/password**
- [ ] `login local`
- [ ] **SSH authentication**
- [ ] **Secure management plane**

## 5.4 Password policies
- [ ] **Password complexity**
- [ ] **Password management**
- [ ] **Password alternatives**
- [ ] **MFA**
- [ ] **Certificates**
- [ ] **Biometrics**
- [ ] **Password rotation / policy concepts**

## 5.5 VPN
- [ ] **IPsec**
- [ ] **Remote-access VPN**
- [ ] **Site-to-site VPN**
- [ ] **VPN tunnel**
- [ ] **Encryption**
- [ ] **Authentication**
- [ ] **K čemu VPN slouží**
- [ ] **Rozdíl remote-access vs site-to-site**

## 5.6 ACL
- [ ] **ACL**
- [ ] **Standard ACL**
- [ ] **Extended ACL**
- [ ] **Permit**
- [ ] **Deny**
- [ ] **Implicit deny**
- [ ] **Source IP**
- [ ] **Destination IP**
- [ ] **Protocol**
- [ ] **Port**
- [ ] **Wildcard mask**
- [ ] **ACL placement**
- [ ] **Inbound**
- [ ] **Outbound**
- [ ] **Configure ACL**
- [ ] **Verify ACL**
- [ ] **Troubleshoot ACL**

## 5.7 Layer 2 security
- [ ] **DHCP Snooping**
- [ ] **Trusted port**
- [ ] **Untrusted port**
- [ ] **DHCP binding table**
- [ ] **Dynamic ARP Inspection**
- [ ] **ARP spoofing**
- [ ] **Port Security**
- [ ] **Sticky MAC**
- [ ] **Maximum MAC addresses**
- [ ] **Violation modes**
- [ ] **Ověření port security**

## 5.8 AAA
- [ ] **Authentication**
- [ ] **Authorization**
- [ ] **Accounting**
- [ ] **AAA**
- [ ] **Local authentication**
- [ ] **RADIUS**
- [ ] **TACACS+**
- [ ] **Základní rozdíl RADIUS vs TACACS+**

## 5.9 Wireless security
- [ ]  **WPA**
- [ ]  **WPA2**
- [ ]  **WPA3**
- [ ]  **PSK**
- [ ]  **Encryption**
- [ ]  **Personal vs Enterprise authentication** — základ

## 5.10 WLAN WPA2 PSK
- [ ] **Vytvořit WLAN**
- [ ] **SSID**
- [ ] **WPA2**
- [ ] **PSK**
- [ ] **Client connectivity**
- [ ] **Ověření konfigurace přes GUI**

---
# 6 Automation & Programmability

## 6.1 Automation
- [ ] **Co je network automation**
- [ ] **Proč automatizovat síť**
- [ ] **Manual configuration vs automation**
- [ ] **Repetitive tasks**
- [ ] **Configuration consistency**
- [ ] **Network management automation**

## 6.2 Traditional vs controller-based
- [ ] **Traditional network**
- [ ] **Controller-based network**
- [ ] **Centralized management**
- [ ] **Controller**
- [ ] **Device-level configuration vs centralized configuration**
- [ ] **Výhody/nevýhody**

## 6.3 SDN / controller architecture
- [ ] **Software-defined networking**
- [ ] **Underlay**
- [ ] **Overlay**
- [ ] **Fabric**
- [ ] **Control plane**
- [ ] **Data plane**
- [ ] **Separation of control/data plane**
- [ ] **Northbound API**
- [ ] **Southbound API**
- [ ] **Controller ↔ devices**

## 6.4 AI / ML
- [ ] **AI v network operations**
- [ ] **Predictive AI**
- [ ] **Generative AI**
- [ ] **Machine learning**
- [ ] **Jak může AI pomáhat network engineerovi**
- [ ] **Základní limity/risika AI v network operations**
## 6.5 REST APIs
- [ ] **REST API**
- [ ] **HTTP**
- [ ] **GET**
- [ ] **POST**
- [ ] **PUT**
- [ ] **PATCH**
- [ ] **DELETE**
- [ ] **CRUD**
- [ ] **Authentication**
- [ ] **API token**
- [ ] **Basic authentication**
- [ ] **JSON**
- [ ] **Data encoding**
- [ ] **Request**
- [ ] **Response**
- [ ] **HTTP status codes**

## 6.6 Configuration management
- [ ] **Configuration management**
- [ ] **Ansible**
- [ ] **Terraform**
- [ ] **Infrastructure as Code**
- [ ] **Declarative vs imperative approach — základ**
- [ ] **Proč se používají automation tools**
- [ ] **Rozdíl Ansible vs Terraform na konceptuální úrovni**

## 6.7 JSON
- [ ] **JSON object
- [ ] **JSON array**
- [ ] **Key**
- [ ] **Value**
- [ ] **String**
- [ ] **Number**
- [ ] **Boolean**
- [ ] `null`
- [ ] **Nested objects**
- [ ] **Nested arrays**
- [ ] **Číst JSON bez problémů**

---
# Priority
### Priorita 1 — musíš dostat do ruky
- [ ]  IPv4 subnetting
- [ ]  IPv6
- [ ]  Routing tables
- [ ]  Longest Prefix Match
- [ ]  Static routing
- [ ]  OSPF
- [ ]  STP / Rapid PVST+
- [ ]  EtherChannel / LACP
- [ ]  ACL
- [ ]  NAT/PAT
- [ ]  DHCP relay
- [ ]  SSH

### Priorita 2 — velmi důležité
- [ ]  Port Security
- [ ]  DHCP Snooping
- [ ]  Dynamic ARP Inspection
- [ ]  CDP / LLDP
- [ ]  Wireless
- [ ]  WLC
- [ ]  NTP
- [ ]  Syslog
- [ ]  SNMP
- [ ]  AAA / RADIUS / TACACS+
- [ ]  VPN
- [ ]  QoS

### Priorita 3 — menší, ale pořád v blueprintu
- [ ]  Spine-leaf
- [ ]  Two-tier / three-tier
- [ ]  VRF
- [ ]  Containers / virtualization
- [ ]  FHRP
- [ ]  PoE
- [ ]  TFTP/FTP
- [ ]  REST APIs
- [ ]  JSON
- [ ]  Ansible
- [ ]  Terraform
- [ ]  SDN
- [ ]  AI/ML



