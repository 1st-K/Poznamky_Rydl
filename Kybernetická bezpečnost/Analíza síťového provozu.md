#### Wireshark:
používá se na traking packetů

#### Tcpdump

###### `[options]` - parametry programu, které můžete použít k upravení chování programu

- `-i <interface>` - zvolí síťové hrozhraní, na kterém chcete zachytávat síťový provoz (např. `eth0`, `wlan0` nebo `any` pro zachytávání na všech dostupných rozhraních)
- `-s <size>` - nastaví maximální velikost zachytávaných paketů v bajtech (standardně **68**, pro zachytávání celých paketů je vhodné nastavit velikost na **65535** nebo taktéž **0**)
- `-w <file>` - uloží záznam provozu do souboru `<file>`
- `-n` - nepřekládá názvy hostů na IP adresy (např. `google.com` -> `8.8.8.8`)
- `-nn` - nepřekládá názvy hostů na IP adresy a nepřekládá čísla portů na služby (např. `22` -> `ssh`)
- `-c <count>` - počet zachycených paketů (defaultně **-1**, tedy neomezeně)
- `-A` - zobrazí obsah paketů v ASCII formátu
- `-X` - zobrazí obsah paketů v hexadecimálním formátu
- `-v` - zobrazí více informací o zachytávaných paketech
- `-vv` - zobrazí ještě více informací o zachytávaných paketech
- `-vvv` - zobrazí ještě ještě více informací o zachytávaných paketech


###### `[expression]` - podmínka, která musí být splněna, aby byl paket zachycen a zobrazen:

- `host <host>` - zachytává pouze pakety, kde cíl nebo zdroj je `<host>`
- `port <port>` - zachytává pouze pakety, které jsou určeny pro port `<port>`
- `src <host>` - zachytává pouze pakety, které pocházejí z hostu `<host>`
- `dst <host>` - zachytává pouze pakety, které jsou určeny pro host `<host>`
- `src port <port>` - zachytává pouze pakety, které pocházejí z portu `<port>`
- `dst port <port>` - zachytává pouze pakety, které jsou určeny pro port `<port>`
- `tcp` - zachytává pouze pakety, které jsou typu TCP
- `udp` - zachytává pouze pakety, které jsou typu UDP
- `icmp` - zachytává pouze pakety, které jsou typu ICMP
- `ip` - zachytává pouze pakety, které jsou typu IP
- `ether` - zachytává pouze pakety, které jsou typu Ethernet
- `net <network>` - zachytává pouze pakety, které jsou určeny pro síť `<network>`

expression můžete kombinovat pomocí logických operátorů:

- `and` - `&&`
- `or` - `||`
- `not` - `!`
- `(` a `)` - závorky pro určení pořadí vyhodnocování