Tým: Dan Rýdl 
Datum: 2026-03-23
Místo: Smíchovská SPŠ
Zadavatel: Pan učitel Vacek
Scope:
```
Připojení na vzdálený server
Vyzkoušet připojení na server na adrese 179.5.5.5 na root pomocí klice 
Kopírování klíče na server
Nainstalování a konfigurace OpenSSH
Nastavení přihlašování pomocí klíče

Konfigurace podle podmínek:
- Ať server běží na portu 9815
- Maximální počet pokusů na přihlášení musí být 4
- Na server se bude dát přihlásit pouze na uživatele root a ukol4
- Na uživatele root se půjde přihlásit pouze soukromým klíčem, ne heslem (samotné klíče na serveru nastavovat nemusíte)


```

Postupoval jsem podle zadání a vše šlo hladce


Postup:
Připojení na vzdálený server pomocí hesla které bylo přiřazeno
(příkazy jsou psané mezi * *)
#### Flag 1:
```
Připojení na vzdalený server na adrese 179.5.5.5 na root pomocí klíče
*cat flag*
flag jsem zadal jako výstup

```
#### Flag 2:
```
Kopírování ssh klíče na vzdalený server
*ssh-copy-id -i /tmp/keys-to-setup/id_ed25519.pub ukol2@179.5.5.6*
```
#### Flag 3:
```
Připojení na vzdalený server
*ls -a*
nic to nevypsalo
*mkdir .ssh*
*cd .ssh*
*echo "ssh-ed25519 AAAAC3N....setup-key" > authorized_keys*
*sudo service ssh start*
```
Flag