je velka 32 bitu
je členěná na 4 časti 

net určuje 

#net_cast     | #host_cast 
`192.168.1.0`


#### #prefix
to /24 znamena 24 bitu
tim prefixem urcuju co je urcene netem (siti) a co je host cast

#### maska
255.255.255.0
prvni tri oktety jsou urcovane siti a zbytek host
rozdeluje na #host_cast a #net_cast
a je to podobne jak #prefix , vlastne to same 
#### sit 
nemuzu pouzit prvni a posledni (0 a 255)
0 je adresa site (je pouzivana routerem kdyz komunikuje mimo sit)
255 je broadcast 