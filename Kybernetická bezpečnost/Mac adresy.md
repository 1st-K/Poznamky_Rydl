**NIC** - Network Interface Card, **Síťová karta**


#### MAC adresa
data link layer
každá karta má vlastní MAC adresu jako unikátní identifikátor 
MAC = Media Access Control address

### Hlavičky linkové vrstvy (Data Link Layer Headers)

V rámci zapouzdření dat (packet encapsulation) se na linkové vrstvě přidávají do rámce (frame) **headery** (hlavičky), které obsahují důležité informace pro správný přenos dat v rámci lokální sítě. Mezi tyto informace patří například:

- **Zdrojová MAC adresa (Source MAC Address)** – MAC adresa odesílajícího zařízení
- **Cílová MAC adresa (Destination MAC Address)** – MAC adresa přijímajícího zařízení
- **Typ protokolu (Type)** – určuje, jaký protokol je použit v následující vrstvě (například IPv4 – vysvětlíme si v dalších úlohách)
- **Délka rámce** - někdy místo typu protokolu je zde uvedena délka rámce
- **Frame Check Sequence (FCS)** – kontrolní součet pro detekci chyb v rámci. Můžete si to představit jako "otisk prstu" rámce, který pomáhá zjistit, zda nedošlo k poškození dat během přenosu. Pokud "otisk" dat v rámci neodpovídá tomuto kontrolnímu součtu, rámec je považován za poškozený a je zahozen.

Dále se zde taky provádí kontrola již zmíněného "otisku prstu" rámce, aby se zajistilo, že data nebyla poškozena během přenosu. Kontroluje se tady rovněž délka rámce, aby se zajistilo, že rámec není příliš krátký nebo příliš dlouhý (rámce mají definovanou minimální a maximální délku, pokud rámec nesplňuje tyto požadavky, je zahozen).

![[Pasted image 20260317202938.png]]


### Formát MAC adresy

**Hexadecimální soustava:** V klasické desítkové soustavě pracujeme s číslicemi od 0 do 9. V hexadecimální soustavě (zkráceně hex) se k těmto číslicím přidávají ještě písmena A, B, C, D, E a F, které reprezentují hodnoty 10 až 15. Takže pokud bychom chtěli zapsat číslo 13 v hexadecimální soustavě, zapsali bychom ho jako D. Nebo například číslo 255 bychom zapsali jako FF (15*16 + 15 = 255).

MAC adresa je tvořena **48 bity** (12 hexadecimálních číslic), které jsou obvykle zapisovány ve formátu **šesti dvojic oddělených dvojtečkami**. Například:

```
CC:46:D6:3C:4D:5E
```

- První tři dvojice MAC adresy (v tomto případě `CC:46:D6`) **identifikují výrobce** dané síťové karty – tzv. **OUI** (Organizationally Unique Identifier).

- Poslední tři dvojice (`3C:4D:5E`) by měly být **unikátní pro každou síťovou kartu** daného výrobce.


Když se tedy znovu podíváme na příkladovou MAC adresu výše, můžeme ve veřejně dostupných databázích pomocí její OUI zjistit, kdo je výrobcem příslušné síťové karty; například:

```
CC:46:D6 - Cisco 
00:04:23 - Intel Corporation
10:93:E9 - Apple, Inc.
00:0C:42 - MikroTik (RouterBoard)
08:00:27 - VirtualBox (Pcs Systemtechnik GmbH - Oracle Corporation)
00:05:69 - VMware, Inc.
```

### Účel MAC adresy
MAC adresa slouží jako **unikátní identifikátor zařízení v rámci lokální sítě** na první vrstvě TCP/IP modelu (linková vrstva). Pokud bude váš počítač komunikovat s jiným počítačem, udělá to následovně:

1. Váš počítač připraví data, která chce odeslat.
2. Váš počítač zjistí MAC adresu dalšího počítače v síti, přes který chce data odeslat.
3. Váše síťová karta zabalí data do **rámce** (frame), kde napíše **zdrojovou MAC adresu** (vaše síťová karta) a **cílovou MAC adresu** (síťová karta následujícího počítače).
4. Síťová karta **převede rámec** na signály a **odešle** je po fyzickém médiu.
5. Síťová karta cílového počítače **přijme signály**, převede je zpět na rámec a zkontroluje cílovou MAC adresu. Pokud se shoduje s její vlastní MAC adresou, zpracuje data uvnitř rámce.

Tento proces se opakuje na každém počítači po cestě, dokud data nedorazí ke svému cíli, kde se poté zpracují a odešle se odpověď zpět stejným způsobem.

![[Pasted image 20260317203226.png]]

#### Jak poznat, která MAC adresa je která?
To, že se jedná o unicast, multicast nebo broadcast MAC adresu poznáme z tzv. **LSB** (Least Significant Bit) **prvního oktetu** (první dvojice hexadecimálních číslic) MAC adresy. U **unicast MAC adres** je tento bit nastaven na **0**, zatímco u **multicast MAC adres** je tento bit nastaven na **1**. V případě **broadcast MAC adresy** jsou **všechny bity** nastaveny na **1**.

> **LSB je nejméně významný bit**, který se nachází na nejnižší pozici v binárním zápisu čísla (úplně vpravo). Kdybychom si vzali například číslo 129, jeho binární zápis je 10000001, kde jeho LSB je poslední 1 (1000000**1**). Least Significant Bit se mu říká proto, že má nejmenší váhu při určování hodnoty celého čísla a **jeho změna má nejmenší dopad na celkovou hodnotu čísla** (pokud změníme LSB z 1 na 0, hodnota čísla se změní pouze o 1).