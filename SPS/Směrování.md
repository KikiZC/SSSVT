=rozhodování o dalším směru přenosu dat

### Adaptivní algoritmy

=dynamické směrování

Reagují na průběžné změny v síti

Windows server: každý max. 2 min na synchronizaci tabulek (tzn. 5 serverů – 10 min)

### Neadaptivní algoritmy

=statické směrování

Nereagují změny v síti

## Druhy směrování

### Centralizované

1 centrum

1 point of failure

Výjimečné použití

### Izolované

Neexistuje centrum

Každý router se rozhoduje sám

#### Záplavové

Používá se při autoconfiguraci switche

Zaručeno dodání packetu do cíle

Bohužel může přijít několikrát

Pošle je všude, KROMĚ odesílatele

#### Metoda horké brambory

Pošle packet do nejméně zatížené cesty

Klidně i zpátky

#### Metoda zpětného učení

Učí se z packetů, které se vrací

„Sem jsem to poslal a funguje to“

Musí umět zapomínat (kvůli aktualizaci)

### Distribuované

Neexistuje centrum

Rozhodují se směrovače, ale spolupracují spolu

Vyměňují si mezi sebou informace o topologii (protokoly RIP či OSPF)

Aktuálně používáme RIPv2

Druhy

#### Vector-distance routing

#### Link-state algoritmus

#### Hierarchické směrování

Pro velké sítě

Síť se rozdělí na menší části

Do každé části se vymezí pouze jeden bod