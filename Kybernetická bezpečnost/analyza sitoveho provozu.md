- umoznuji administratorum / spravcum site videt, co se deje v siti
- tato prace je velmi narocna a tak existuje nekolik nastroju, ktere ji mohou usnadnit

## wireshark
- **GUI**
- dvoji pouziti

### orientace
- nahore panel `Apply a display filter ... <Ctrl-/>`
- dale 3 hlavni casti
	1. ve vrchnim vidime zaznam sitove komunikace
		- jsou tam sloupce
			1. sloupec **No.**
				- cislo zachyceneho paketu (odshora dolu)
			2. sloupec **Time**
				- cas ve vterinach od zacatku scanovani
			3. sloupec **Source**
				- zdrojova adresa
			4. sloupec **Destination**
				- cilova adresa
			5. sloupec **Protokol**
				- zobrazuje protokol, ktery byl ke komunikaci pouzit
			6. sloupec **Length**
				- velikost paketu v bajtech
			7. sloupec **Info**
				- informace spajte s protokolem
	
	2. ve spodnim sloupci vlevo vidime detail vybraneho paketu z vrchniho sloupce
	3. ve spodnim sloupci vpravo vidime detail reprezentaci paketu v hexadecimalu


### filtrovani
`ip.addr == <IP address>` -> pouze pakety smerujici nebo odchazejici z/do `IP_address`
`ip.src == <IP address>` -> pouze pakety dochazejici z `<IP address>`
`ip.dst == <IP address>` -> pouze pakety smerujici do `<IP address>`
`tcp` -> pouze protokol `tcp`
`udp` -> pouze protokol `udp`
`tcp.port == <port>` -> pouze `tcp` pakety smerujici/odchazejici do/z `<port>`
`udp.port == <port>` -> pouze `udp` pakety smerujici/odchazejici do/z `<port>`
`icmp` -> pouze pakety typu `icmp`
`http` -> pouze pakety typu `http`
`ip` -> pouze pakety typu `ip`

#### operatory
`||` - OR
`&&` - AND
`!` - NOT
`()` - priority

priklad:
``` mathematica
ip.src == 192.168.0.1 && tcp
```

### scan site

``` bash
wireshark
```

necha te vybrat rozhrani (`eth0`, `wlan0`, `any`...), musis mit uzivatele v group wireshark (nejde se `sudo`)
``` bash
sudo usermod -aG wireshark ondra
```

### analyza souboru

``` bash
wireshark soubor.pcap
```

## tcpdump
- **CLI** (lze tedy pouzit i pres `SSH`)
- spoustet se `sudo`

### pouziti

``` bash
sudo tcpdump [options] [expression]
```

#### options
- upravuji chovani programu

`-i <interface>` -> zvoli sitove rozhrani
	`eth0` -> ethernet
	`wlan0` -> sit
	`any` -> vsechna rozhrani
`-s <size>` -> nastavi maximalni velikost zachytavani paketu v bajtech (doporucuje se `0`)
`-w <file>` -> ulozi zaznam do souboru
`-n` -> nepreklada domeny na IP adresy (zustane `google.com` a ne `8.8.8.8`)
`-nn` -> nepreklada ani domeny ani cisla portu na sluzby
`-c <count>` -> pocet zachycenych paketu (standardne 0)
`-A` -> zobrazi ASCII podobu paketu
`-X` -> zobrazi obsah paketu v hexadecimalni podobe
`-v` -> zobrazi vice informaci o paketach
`-vv` -> zobrazi jeste vice informaci
`-vvv` -> zobrazi jeste vice informaci

priklad:
```bash
sudo tcpdump -i any -w scan.pcap -nn -vvv -s 0 'tcp and port 80'
```

#### expression
- podminka, ktera musi byt splnena, aby se paket vypsal

`host <host>` -> jen pokud je cil/zdroj `<host>`
`port <port>` -> jen pokud to smeruje na `<port>`
`src <src>` -> jen pokud je odesilatel `<src>`
`dst <dst>` -> jen pokud je adresat `<dst>`
`src port <port>` -> jen pokud je odesilajici port `<port>`
`dst port <port>` -> jen pokud je port prijemce `<port>`
`tcp` -> jen pokud je `tcp`
`udp` -> jen pokud je `udp`
`icmp` -> jen pokud je `icmp`
`ip` -> jen pokud je typu `ip`
`ether` -> jen pokud je typu `ether`
`net <network>` -> jen pokud je urcene pro sit `<network>`

##### operatory

- `OR ||`
- `AND &&`
- `NOT !`
- `()` -> pro vyhodnoceni priorit

## termshark
- CLI `wireshark` (typu `btop`, graficke zobrazeni, ale kompletne v terminalu, funguje i v `ssh`)

[[network scan]]
[[utoky]]