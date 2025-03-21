Slouží k překladu doménových jmen na IP adresy a naopak. Skládá se z dopředné a zpětné zóny.

## Autoritativní vs neautoritativní server

Autoritativní – v mojí síti, ručím za záznamy, správce své zóny

Neautoritativní – spravuji dns pro někoho, záznamy z jiné sítě – neručím za záznamy

## Primární vs sekundární server

Sekundární – rozložení zátěže, záloha v případě výpadku primáru, nelze měnit záznamy

Primární – data o zóně, slouží k editaci a změnám

## Dopředná vs zpětná zóna

Dopředná přiřazuje JMÉNO k IP

Zpětná přiřazuje IP ke JMÉNU

Sériové číslo v souboru zóny je kvůli synchronizaci se sekundárním serverem, ten se pouze podívá, zda je jeho sériové číslo stejné, není-li načte znovu zónu

S každou změnou zóny se MUSÍ změnit sériové číslo zóny, přes gui se mění samo

## Forwardovací server

Když to nezná, pošle to dál

Kam, to má nastaveno

Nemá svoje vlastní zóny

## Cachovací server

Funguje, jako forwardovací

Ale pamatuje si záznamy, pozor – Musí umět zapomínat (Alzheimer)

Poprvé to nezná, takže se zeptá dalšího a zapíše si při cestě zpět

Při dalším dotazu se podívá do cache a odpoví+