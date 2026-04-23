zapnout jako v [[Aircrack-ng]]
`airodump-ng <sitovka>`
`--essid <nazev site>` = jen jedna sit
 `wifite --nodeuths` odpoji klienta a pak zjisti asi heslo 


client pripojit = je treba ho odpojit abychom mohli videt 
zjistit capture a prevest do formatu ktere hashcat zvladne `.hccapx` (.cap to hashcat)

`airodump -w <slozka> --essid <nazev site> -c <Chanel>`
Pak je treba to prevest z `.cap` na neco pro hashcat 
pak to nechat hashcat prechroustat 