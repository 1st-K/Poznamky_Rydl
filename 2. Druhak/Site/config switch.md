jsou tri vrstvy konfigurace 
1. 
2. enable - zapnes psani
3. config term - zapnes confikofigurovani 

`banner *uvnitr je text* `




``interface  g0/1`` - vcházim na config g0/1
``ip add 192.168.0.1 255.255.255.0``  - pridani ip adresy na rozhrani, maska musi byt takhle vypsana
``no shutdown`` - nevypinat - pridani ip adresy na rozhrani, maska musi byt takhle 
`reload` - restart
`erase` - smaze konfiguraci
`show running-config` - ukaze bezici configuraci