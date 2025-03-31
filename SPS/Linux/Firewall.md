= zeď která chrání:
- Mojí síť proti venku
- Venek proti mé síti

## Typy firewallu:
- Softwarový
- Hardwarový
	- Mimo server nebo stanici, stejně tam ale běží software

## Typy filtru ve firewallu:
### Paketový filtr
- řídí se tabulkou pravidel
- lze formou:
	- **Povolení** - povolí průchod
	- **Zakázání** - zakáže průchod 
	- **Zahození** - zahodí paket
- poslední pravidlo nelze smazat (u Kerio FW)
- pravidlo obsahuje:
	- *název* - pojmenování pravidla
	- *zdroj* - síťovka, adresa, síť, ...
	- *cíl* - síťovka, adresa, síť, ...
	- *protokol* - TCP, UDP
	- *odkdy do kdy* - určuje čas aplikace pravidla
	- *co dělat* - Povolit, Zakázat, Zahodit
- rychlý, nezpomaluje tak moc, levnější
- **Výhody**:
	- rychlost úprav
- **Nevýhody**:
	- těžké nastavování restriktivního přístupu

### Aplikační filtr
- na aplikační vrstvě
- nezajímá se o paket, ale o obsah paketu
- **Nevýhody**:
	- pomalejší
	- náročnější na zpracování
	- dražší
- **Výhody**:
	- větší bezpečnost
	- lepší pravidla

## Speciální
### Dynamický paketový filtr
- Čeká a pustí pouze odpověď na mojí otázku
- Př: ping -> vrátí se mi a projde v pohodě, protože jsem se zeptal a toto je jen odpověď


## DMZ
= demilitarizovaná zóna
Nachází se zde věci, které chceme vidět i zvenku i zevnitř
Na začátku DMZ je lehčí Firewall a vevnitř poté druhý
![[DMZ 2 FW.PNG]]

Lze i s jedním FW
- udělám jakoby odbočku z FW do DMZ
 ![[DMZ 1 FW.PNG]]



