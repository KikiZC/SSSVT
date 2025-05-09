Tento dokument obsahuje kompletní seznam příkazů z CCNA: Introduction to Networks. Seznam je rozdělen do několika sekcí pro snadnější orientaci. Každá sekce pokrývá specifické kategorie příkazů, jako je konfigurace zařízení, správa sítí, diagnostika nebo bezpečnost. Pokud budete mít další otázky k příkazům, neváhejte se zeptat!
## Základní příkazy pro navigaci v CLI:

`enable` – Přechod do privilegovaného režimu (privileged EXEC mode).

`disable` – Návrat do uživatelského režimu (user EXEC mode).

`exit` – Ukončení aktuálního režimu nebo relace.

`logout` – Odhlášení z relace.

`show` – Zobrazení různých informací o zařízení.

- Příklad: `show running-config`, `show ip interface brief`.

## Příkazy pro zobrazení informací:

`show version` – Zobrazení verze IOS a základních informací o zařízení.

`show running-config` – Zobrazení aktuální konfigurace v paměti RAM.

`show startup-config` – Zobrazení uložené konfigurace v paměti NVRAM.

`show ip interface brief` – Zobrazení přehledu IP konfigurací na všech rozhraních.

`show interfaces` – Podrobné informace o rozhraních.

`show mac address-table` – Zobrazení MAC adresní tabulky na switchi.

`show vlan brief` – Přehled konfigurace VLAN na switchi.

`show cdp neighbors` – Zobrazení sousedních zařízení pomocí CDP.

`show arp` – Zobrazení ARP tabulky.

## Příkazy pro konfiguraci zařízení:

`configure terminal` – Vstup do globálního konfiguračního režimu.

`hostname <název>` – Nastavení názvu zařízení.

`interface <rozhraní>` – Vstup do konfiguračního režimu konkrétního rozhraní.

- Příklad: `interface gigabitEthernet 0/0`.

`ip address <IP-adresa> <maska>` – Nastavení IP adresy a masky na rozhraní.

`no shutdown` – Aktivace rozhraní.

`shutdown` – Deaktivace rozhraní.

`description <text>` – Přidání popisu k rozhraní.

`line console 0` – Konfigurace přístupu přes konzoli.

`password <heslo>` – Nastavení hesla.

`login` – Povolení ověřování heslem.

`line vty 0 4` – Konfigurace přístupu přes Telnet nebo SSH.

`service password-encryption` – Šifrování hesel v konfiguraci.

`banner motd <zpráva>` – Nastavení zprávy dne (Message of the Day).

## Příkazy pro správu směrování:

`ip route <cílová-síť> <maska> <next-hop>` – Statická směrovací tabulka.

`router rip` – Aktivace RIP protokolu.

`network <síť>` – Přidání sítě do RIP protokolu.

`version 2` – Nastavení RIP verze 2.

## Příkazy pro správu VLAN a trunků:

`vlan <číslo>` – Vytvoření VLAN.

`name <název>` – Pojmenování VLAN.

`interface vlan <číslo>` – Vstup do VLAN rozhraní.

`switchport mode access` – Nastavení přístupového režimu na portu.

`switchport mode trunk` – Nastavení trunkového režimu na portu.

`switchport access vlan <číslo>` – Přiřazení portu k VLAN.

## Diagnostické příkazy:

`ping <IP-adresa>` – Test konektivity.

`traceroute <IP-adresa>` – Sledování cesty k cílové IP adrese.

`debug` – Zapnutí ladění (např. `debug ip icmp`).

`undebug all` nebo `no debug all` – Vypnutí všech ladících zpráv.

## Další užitečné příkazy:

`write memory` nebo `copy running-config startup-config` – Uložení konfigurace.

`erase startup-config` – Vymazání uložené konfigurace.

`reload` – Restartování zařízení.

##  Rozšířené příkazy pro správu zařízení:

### Globální konfigurace:

`clock set <HH:MM:SS> <day> <month> <year>` – Nastavení systémového času.

`ip domain-name <domain>` – Nastavení doménového jména zařízení.

`username <name> privilege <level> password <password>` – Vytvoření uživatele s heslem.

`crypto key generate rsa` – Vygenerování klíče RSA pro SSH.

`ip ssh version 2` – Aktivace SSH verze 2.

`logging synchronous` – Synchronizace systémových zpráv v CLI.

### Telnet a SSH:

`transport input ssh` – Povolení SSH na VTY linkách.

`transport input telnet` – Povolení Telnetu na VTY linkách.

`exec-timeout <min>` – Nastavení času, po kterém se relace odhlásí.

### Správa flash paměti a konfigurace:

`dir` – Zobrazení obsahu flash paměti.

`delete <file>` – Smazání souboru z paměti.

`copy <source> <destination>` – Kopírování souborů (např. `copy tftp startup-config`).

## Rozšířené příkazy pro zobrazení informací:

`show flash` – Zobrazení obsahu flash paměti.

`show protocols` – Zobrazení protokolů na zařízení.

`show ip route` – Zobrazení směrovací tabulky.

`show port-security` – Zobrazení konfigurace portové bezpečnosti.

`show spanning-tree` – Informace o protokolu STP (Spanning Tree Protocol).

`show interfaces status` – Přehled stavu všech rozhraní.

`show running-config | include <text>` – Filtrování výstupu konfigurace.

`show logging` – Zobrazení systémových zpráv.

`show users` – Informace o aktuálně přihlášených uživatelích.

## Diagnostika a troubleshooting:

### Ladění (debug):

`debug ip rip` – Ladění RIP protokolu.

`debug ip routing` – Ladění směrování.

`debug spanning-tree` – Ladění protokolu STP.

### Pokročilé diagnostické příkazy:

`ping <IP-address> repeat <count>` – Opakovaný ping pro lepší diagnostiku.

`telnet <IP-address>` – Otestování připojení přes Telnet.

`clear ip arp` – Vymazání ARP tabulky.

`clear mac address-table dynamic` – Vymazání dynamické MAC tabulky.

## Bezpečnostní příkazy:

### Portová bezpečnost (Switch):

`switchport port-security` – Aktivace portové bezpečnosti.

`switchport port-security maximum <number>` – Nastavení maximálního počtu MAC adres.

`switchport port-security violation <action>` – Nastavení akce při porušení (shutdown, restrict, protect).

`switchport port-security mac-address <MAC>` – Přiřazení statické MAC adresy.

### ACL (Access Control List):

`access-list <number> permit <IP>` – Povolení IP adresy v ACL.

`access-list <number> deny <IP>` – Zakázání IP adresy v ACL.

`ip access-group <number> in/out` – Aplikace ACL na rozhraní.

`ip access-list standard/extended <name>` – Vytvoření pojmenované ACL.

## Směrovací protokoly:

### OSPF:

`router ospf <process-id>` – Aktivace OSPF.

`network <IP> <wildcard-mask> area <area-id>` – Přidání sítě do OSPF.

`passive-interface <interface>` – Nastavení pasivního rozhraní.

### EIGRP:

`router eigrp <AS-number>` – Aktivace EIGRP.

`network <IP> <wildcard-mask>` – Přidání sítě do EIGRP.

`no auto-summary` – Deaktivace automatické sumarizace.

## Spanning Tree Protocol (STP):

`spanning-tree vlan <vlan-id> priority <value>` – Nastavení priority STP.

`spanning-tree mode rapid-pvst` – Aktivace protokolu Rapid-PVST.