Potřebujeme:
	- cíl - adresu sítě
	- masku cíle
	- rozhraní, kterým odchází ode mě
	- bránu
	- metriku - v linuxu nepovinná

## Nastavení na mezilehlých linuxech
- do `/etc/sysctl.conf` dopíšeme na nový řádek: `net.ipv4.ip_forward=1`
- potom je nutné rebootovat systém
- případně lze v terminálu spustit příkaz: `sysctl -w net.ipv4.ip_forward=1`
- tímto se povolí přeposílání paketů, které nejsou jeho

## Dočasná route
`ip route add 100.20.30.0/24 via 100.20.30.2 dev ens33`
u některých distribucí je potřeba definovat zvlášť masku sítě
`ip route add 100.20.30.0 netmask 255.255.255.0 via 100.20.30.2 dev ens33`

## Trvalá route
v konfiguráku síťovky, která bude sloužit jako odchozí tzn. např. `/etc/NetworkManager/system-connections/ens33.nmconnection`

připíšeme do oddílu ipv4
`route1=200.20.30.0/24,200.20.30.1,1`
případně route2, route3 atd.
- první parametr je cíl s maskou, druhý je brána, třetí je metrika(nepovinná)

- případně lze k nastavení použít GUI `nmtui`