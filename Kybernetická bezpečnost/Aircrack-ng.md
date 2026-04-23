`airmon-ng` = zapne monitor mode, nastavi sitovku spravne

`airodump-ng` = vypise vsechny site 
`-w` = vypisuje do souboru vse vcetne handshake
`--bssid <MAC>` = nastavit jen specifickou wifi



Beacons = kolikrat jsme prijali packety o tom ze tam sit je
ESSID = jmeno site

jsou tam dve tabulky
ta spodni jsou clienti, kteri se chteji nebo jsou pripojini

### Postup:
Stop `NetworkManager` = vypne `nm` aby mohli pouzivat jiní
`airmon-ng` = vypise sitovky
`airmon start <vybrana sitovka>` = zapne tu sitovku pro pouziti
znovu `airmon-ng` = vypise znovu, protoze se zmenilo jmeno sitovky
`airmon-ng <sitovka>` = ted se to spusti a jsou videt tabulky

### vraceni zpet
`start NetworkManager`
`airmong stop <sitovka>` = odpoji se od sitovky aby mohla byt pouzita `nm`
