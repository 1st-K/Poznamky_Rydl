## Základní konfigurace

- Router> enable - přistoupení do privilegovaného uživatelského módu
- Router#configure terminal – přistoupení do globálního konfiguračního módu
- Router(config)#hostname <nazev routeru> – nastavení jména zařízení v síti
- Router(config)#enable password/secret <heslo> – nastavení hesla pro přístup do privilegovaného uživatelského módu (heslo pro enable)
- Router(config)#banner motd <*zprava*>- nastavení úvodní zprávy při vstupu do zařízení

## Nastavení hesla pro consoli

- Router(config)#line console 0 – přistoupení do konfigurace console
- Router(config-line)#password x – nastavení hesla pro consoli
- Router(config-line)#login – potvrzení hesla a zapnutí jeho ověřování (bez „login“ příkazu se heslo nebude na consoli požadovat)

## Nastavení hesla pro vzdálený přístup(telnet)

- Router(config)#line vty 0 4 – přistoupení do konfigurace virtuálního terminálu
- Router(config-line)#password x – nastavení hesla pro vzdálený přístup
- Router(config-line)#login -potvrzení hesla a zapnutí jeho ověřování

  
  

## Nastavení IP adresy na routeru

- Router(config)#interface g0/0 (přistoupení na daný port routeru)
- Router(config-if)#ip address 192.168.0.1 255.255.255.0 (nastavení adresy s maskou)
- Router(config-if)#no shutdown (zapnutí vypnutého portu, ze začátku je vždy potřeba port nahodit)

## Nastavení IP adresy na switchi
- Switch(config)#interface vlan1 (přistoupení do konfigurace vlanu 1, který na switchi v základním rozpoložení zahrnuje všechny porty dohromady)
- Switch(config-if)#ip add 192.168.0.2 255.255.255.0
- Switch(config-if)#no shutdown


Ctrl + Shift + 6 – přerušení NS Lookupu

Nezapomeňte, že určité příkazy fungují jenom v daném konfiguračním prostředí, například „hostname jméno“ nelze použít nikde jinde než v configure terminal a „enable“ zase nebude fungovat nikde jinde než v základním uživatelském módu. Dejte si proto vždy pozor, kam příkazy píšete!