konfigurační soubor - /etc/dhcp/dhcpd.conf

nastavíme si statickou IP adresu - nmtui

Zde definujeme rozsah na rozdávání
``` bash
subnet 10.20.30.0 netmask 255.255.255.0 {
	range 10.20.30.10 10.20.30.100;
	option routers 10.20.30.1;
	default-lease-time 600;
	max-lease-time 7200;
}
```
option routers = výchozí brána
default-lease-time = na jak dlouho zapůjčíme adresu v sekundách
max-lease-time = jak dlouho maximálně může být vypůjčena adresa
=> zapůjčí se na 10 min, po 10 min se znovu obnoví atd. dokud nedojde k max limitu - poté se adresa změní

``` bash
host fantasia {
	hardware ethernet E2:79:48:B1:F0:1F;
	fixed-address 10.20.30.50
}
```
Nyní pomocí příkazu `systemctl restart dhcpd.service`
nehodí-li chybu - 🎉🎉🎉🎉🎉🎉
vyhodí-li chybu, pomocí příkazu `systemctl status dhcpd.service` zjistíme, kde máme v configu chybu a tu opravíme