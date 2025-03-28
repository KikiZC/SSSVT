Tento manuál ti ukáže, jak správně přidávat zápisky do repozitáře, aby se vše udržovalo **přehledné** a **organizované**.

## 🔹 **1️⃣ Stáhni nejnovější změny před začátkem práce**

Předtím, než začneš psát nové zápisky, si stáhni všechny **nové změny** od ostatních.

1. **Otevři GitHub Desktop**
    
2. Klikni na **Fetch origin** – tím zjistíš, jestli jsou nové změny
    
3. Pokud jsou, klikni na **Pull origin** – tím si je stáhneš
    

💡 **Proč je to důležité?**  
Aby se nestalo, že budeš pracovat se starou verzí a pak vzniknou konflikty!

---

## 🔹 **2️⃣ Vytvoř si vlastní větev (branch)**

Každou úpravu dělej ve **vlastní větvi**, aby hlavní větev zůstala stabilní.

1. V **GitHub Desktop** klikni na **Current branch**
    
2. Klikni na **New branch**
    
3. Pojmenuj větev podle toho, co děláš (např. `CJ-zapisky-10-04`)
    
4. Klikni na **Create branch**
    

💡 **Proč používat vlastní větev?**

- Umožní ti to dělat změny bez ovlivnění hlavní větve
    
- Zabrání chybám a konfliktům
    

---

## 🔹 **3️⃣ Přidej nebo uprav zápisky v Obsidianu**

1. **Otevři Obsidian**
    
2. **Najdi správnou složku** podle předmětu
    
3. **Přidej nový Markdown (.md) soubor** nebo uprav existující
    
4. **Ulož změny** (Obsidian to dělá automaticky)
    
---

## 🔹 **4️⃣ Commitni změny do své větve**

1. Otevři **GitHub Desktop**
    
2. Uvidíš změněné soubory (oranžově označené)
    
3. **Napiš popis změny** (např. "Doplněny zápisky z CJ 10.4.")
    
4. Klikni na **Commit to [název_tvé_větve]**
    

💡 **Co napsat do commit message?**

- **Dobrý popis:** `"Přidány zápisky z matematiky - derivace"`
    
- **Špatný popis:** `"update"` nebo `"změna"` (příliš obecné)
    

---

## 🔹 **5️⃣ Pushni změny na GitHub**

Aby se tvoje změny dostaly na server, musíš je **pushnout**.

1. Po commitu klikni na **Push origin**
    
2. Změny se nahrají na GitHub
    

💡 **Kdy pushovat?**  
Kdykoliv dokončíš nějakou část práce, aby se nic neztratilo.

---

## 🔹 **6️⃣ Pošli Pull Request (PR) na schválení**

Až budeš mít hotové zápisky, musíš požádat o jejich schválení.

1. Na **GitHub Desktop** klikni na **Create Pull Request**
    
2. Otevře se stránka GitHubu ve webovém prohlížeči
    
3. **Vyplň název PR** (např. `"Zápisky z CJ - 10.4."`)
    
4. **Popiš, co jsi změnil**
    
5. **Klikni na "Create Pull Request"**
    

💡 **Co se stane dál?**

- Učitelé nebo spolužáci, co mají daný předmět na starost, zkontrolují zápisky
    
- Pokud je vše v pořádku, schválí to
    
- Až to všichni schválí, může se změna sloučit do hlavní větve
    

---

## 🔹 **7️⃣ Sloučení Pull Requestu a aktualizace**

**Pokud již tak neučinil někdo jiný z reviewerů**
1. Klikni na **Merge Pull Request** na GitHubu
    
2. Klikni na **Delete Branch** (starou větev už nepotřebuješ)
    
3. V **GitHub Desktop** přepni zpět na hlavní větev (`main`)
    
4. Klikni na **Fetch origin** a **Pull origin**, aby sis stáhl všechny změny

**Pokud již tak učinil někdo jiný z reviewerů**
- Přeskoč první krok s **Merge Pull Request** a jdi rovnou na druhý

💡 **Až to uděláš, můžeš začít s novými zápisky!**

---

## 🔹 **Shrnutí celého procesu**

1. **Stáhni nejnovější změny** (`Pull origin`)
    
2. **Vytvoř novou větev** (`New branch`)
    
3. **Přidej nebo uprav zápisky** v Obsidianu
    
4. **Commitni změny** v GitHub Desktopu
    
5. **Pushni změny** (`Push origin`)
    
6. **Vytvoř Pull Request** na GitHubu
    
7. **Počkej na schválení a sloučení**
    
8. **Stáhni si nejnovější verzi (`Pull origin`) a smaž starou větev**