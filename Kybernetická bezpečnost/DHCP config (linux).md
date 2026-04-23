nejprve budeme muset nainstalovat `isc-dhcp-server`

> *config v praxi v [[DHCP spoofing]].*

nasledne musime zjistit svoji IP: ```
``` bash
ip a
```

nyni jdeme konfigurovat:
``` bash
sudo nano /etc/default/isc-dhcp-server
```

zamerime se na `INTERFACESv4=""` a `INTERFACESv6=""`.

pokud budeme chtit nakonfigurovat DHCP server pro IPv4 na eth1, udelame
`INTERFACESv4="eth1"`nejprve budeme muset nainstalovat `isc-dhcp-server`
nasledne `ip a`

``` bash
sudo nano /etc/default/isc-dhcp-server
```

zamerime se na `INTERFACESv4=""` a `INTERFACESv6=""`.

napr. pokud budeme chtit nakonfigurovat DHCP server pro IPv4 na eth1, udelame
`INTERFACESv4="eth1"`

nasledne musime
``` bash
sudo nano /etc/dhcp/dhcpd.conf
```

na prvni radek napiseme `authoritative;`

dale nakonfigurujeme DNS servery

``` config
option domain-name-servers <primarni DNS>, <sekundarni DNS>;
```

jako posledni definujeme `default-lease-time` a `max-lease-time`

``` config
default-lease-time <SECONDS>; max-lease-time <SECONDS>;
```

tim jsme dokoncili globalni konfiguraci a nyni budeme konfigurovat podsite

``` config
subnet <subnet IP> netmask <subnet mask> {
	range <nejmensi IP> <nejvetsi IP>; # rozsah IP
	option routers 192.168.0.1;        # defaultni brana
}
```




[[pojmy]]

