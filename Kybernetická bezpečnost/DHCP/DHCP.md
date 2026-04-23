kdyz se pripoji nove zarizeni tak posele **discover**
DHCP posle **offer**
client posle **request**
posledni je **ACK**
#### offer 
*soucasti toho je:*
**IP
Maska
GW
DNS
NTP**

#### request
posle zpet vsechny udaje zda jsou spravne
potvrzeni pro server 

#### ACK
kontrola pro klienta
vse je spravne a zapsano v tabulkach 

### **DHCP tabulka:**

je to rezervovani ip adresy na urcity cas
po uplinuti casu se pokusi obnovit, pokud se zarizeni neozve zaznam je smazan

| MAC | IP       | lease time (s) |
| --- | -------- | -------------- |
| x   | 10.0.0.1 | 120            |
