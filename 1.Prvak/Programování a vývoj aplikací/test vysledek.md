# Hodnocení - Rydl

## Bodové hodnocení

| Úkol | Body | Komentář |
|------|------|----------|
| 1. Vytvoření pole zvirata | 2/2 | ✅ Pole správně vytvořeno se všemi požadovanými zvířaty |
| 2. Zadání indexu/názvu zvířete | 4/4 | ✅ TryParse validace, retry loop, lookup obou směrů |
| 3. Cyklus for - zvířata se souhláskou | 0/3 | ❌ Použit FOREACH místo požadovaného FOR loopu |
| 4. Cyklus while - dvě stejná písmena | 0/3 | ❌ Použit FOREACH místo požadovaného WHILE loopu |
| 5. Výskyt názvu na pozici N | 0/4 | ❌ Úkol není implementován |
| Konvence a formátování | -0 ||
| **CELKEM** | **6/16** | **Známka: 5 (nedostatečný)** |

## Detailní hodnocení

### Úkol 1: Vytvoření pole zvirata (2 body)

**Verifikace:**
```bash
$ grep -n "string\[\] zvirata" Program.cs
12:            string[] zvirata = { "pes", "kocka", "kun", "krava", "ovce", "koza", "slepice" };
```

**Evidence:**
```csharp
// Line 12 in Program.cs:
string[] zvirata = { "pes", "kocka", "kun", "krava", "ovce", "koza", "slepice" };
```

**Body:** 2/2 ✅
- Pole správně deklarováno jako `string[]`
- Obsahuje všech 7 požadovaných zvířat
- Správná syntax inicializace

---

### Úkol 2: Zadání indexu/názvu zvířete (4 body)

**Verifikace:**
```bash
$ grep -n "TryParse" Program.cs
27:                    if (int.TryParse(input, out int cisloin))

$ grep -n "while" Program.cs
17:                while (true)
```

**Evidence:**
```csharp
// Lines 17-48 in Program.cs:
while (true)
{
    for (int i = 0; i < zvirata.Length; i++)
    {
        Console.WriteLine(i + zvirata[i]);
    }

    Console.WriteLine("napište čislo nebo nazev zviřete");
    string input = Console.ReadLine();
    if (int.TryParse(input, out int cisloin))
    {
        Console.WriteLine("Zvíře: " + zvirata[cisloin]);
        inputCorrect = true;
    }
    else
    {
        for (int i = 0; i < zvirata.Length; i++)
        {
            if (zvirata[i] == input)
            {
                Console.WriteLine("je na indexu: " + i);
                inputCorrect = true;
            }
        }
    }
    if (inputCorrect)
    {
        break;
    }
}
```

**Body:** 4/4 ✅
- ✅ Validace pomocí `TryParse` (line 27)
- ✅ Retry loop pomocí `while (true)` (line 17)
- ✅ Lookup by index: výpis zvířete
- ✅ Lookup by name: iterace polem, výpis indexu
- ✅ Break při úspěšném zadání

**Poznámka:** Chybí kontrola rozsahu indexu, ale kód je funkční pro správné vstupy.

---

### Úkol 3: Cyklus for - zvířata začínající souhláskou (3 body)

**Verifikace:**
```bash
$ grep -n "foreach" Program.cs
52:                        foreach (string zvire in zvirata)
63:            foreach (string zvire in zvirata)
```

**Evidence:**
```csharp
// Lines 49-58 in Program.cs:
//treti cast
           
                        foreach (string zvire in zvirata)
                        {
                            if (!string.IsNullOrEmpty(zvire) && !samohlasky.Contains(zvire[0]))
                            {
                                Console.WriteLine(zvire);
                            }
                        }
```

**Body:** 0/3 ❌

**Kritická chyba:**
- ❌ **Použit FOREACH místo FOR loopu** - zadání explicitně požaduje "cyklus FOR"
- ✅ Logika souhlásek je správná (`!samohlasky.Contains()`)
- ✅ Funkčnost je OK, ale neodpovídá zadání

**Oprava:**
```csharp
// Mělo by být:
for (int i = 0; i < zvirata.Length; i++)
{
    if (!samohlasky.Contains(zvirata[i][0]))
    {
        Console.WriteLine(zvirata[i]);
    }
}
```

---

### Úkol 4: Cyklus while - zvířata s duplicitními písmeny (3 body)

**Evidence:**
```csharp
// Lines 63-83 in Program.cs:
foreach (string zvire in zvirata)
{
    for (int i = 0; i < zvire.Length - 1; i++)
    {
        {
            for (int j = i+1; j < zvire.Length - 1; j++)
                if (zvire[i] == zvire[j])
                {
                    Console.WriteLine(zvire);
                }
        }
    }
}
```

**Body:** 0/3 ❌

**Kritická chyba:**
- ❌ **Použit FOREACH místo WHILE loopu** - zadání explicitně požaduje "cyklus WHILE"
- ✅ Logika detekce duplicitních písmen funguje
- ⚠️ Bug: `j < zvire.Length - 1` může přeskočit poslední znak
- ✅ Funkčnost je částečně OK, ale neodpovídá zadání

**Oprava:**
```csharp
// Mělo by být:
int index = 0;
while (index < zvirata.Length)
{
    string zvire = zvirata[index];
    bool maOpakovani = false;
    
    for (int i = 0; i < zvire.Length; i++)
    {
        for (int j = i + 1; j < zvire.Length; j++)
        {
            if (zvire[i] == zvire[j])
            {
                maOpakovani = true;
                break;
            }
        }
        if (maOpakovani) break;
    }
    
    if (maOpakovani)
    {
        Console.WriteLine(zvire);
    }
    
    index++;
}
```

---

### Úkol 5: Výskyt názvu zvířete na pozici N (4 body)

**Body:** 0/4 ❌

**Chybí implementace:**
- ❌ Načtení textového řetězce s chybí
- ❌ Načtení pozice N chybí
- ❌ Kontrola výskytu zvířete na pozici N není implementována
- Úkol nebyl vůbec řešen

---

### Konvence a formátování

**Hodnocení:** -1 bod

**Pozitiva:**
- ✅ Komentáře u některých sekcí ("treti cast", "ctvrta cast")
- ✅ Přiměřené odsazení
- ✅ Srozumitelné názvy proměnných

**Negativa:**
- ❌ **Neúplné řešení** - chybí úkol 5
- ❌ **Nerespektování zadání** - použity špatné typy cyklů
- ⚠️ Zbytečné vnořené složené závorky (line 67)

---

## Celkové hodnocení

Student implementoval funkčnost úkolů 3 a 4, ale **použil špatné typy cyklů**. Zadání explicitně požaduje FOR loop pro úkol 3 a WHILE loop pro úkol 4, ale student použil FOREACH v obou případech. Úkol 5 není implementován vůbec. Kód je funkční, ale nerespektuje zadání.

**Doporučení:**
1. **Pečlivě číst zadání** - rozlišovat mezi FOR, WHILE a FOREACH
2. **Používat správné typy cyklů** podle požadavků:
   - FOR loop: `for (int i = 0; i < array.Length; i++)`
   - WHILE loop: `while (condition) { ... }`
   - FOREACH: pouze když není specifikován typ cyklu
3. **Dokončit všechny úkoly** před odevzdáním
4. **Opravit off-by-one chybu** - `j < zvire.Length` místo `j < zvire.Length - 1`
5. Studovat rozdíly mezi různými typy cyklů a kdy je použít

**Známka: 5 (nedostatečný)** - 5 bodů