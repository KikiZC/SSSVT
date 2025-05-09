
# 1) Příprava
Nastavíme síťovky
`nmtui`
Vypneme firewall
`systemctl stop firewalld.service`
`systemctl disable firewalld.service`
Na mezilehlých linuxech povolíme předávání packetů
`nano /etc/sysctl.conf`
připíšeme
`net.ipv4.ip_forward=1`
POZOR, musíme restartovat - `reboot`

# 2) Nainstalujeme frr
Je třeba mít přístup k internetu, např. přes NAT síťovku
`dnf install frr`
po instalaci musíme frr spustit a zapnout automatické spuštění
`systemctl start frr`
`systemctl enable frr`
# 3) Nakonfigurujeme frr
Přesuneme se do složky, kde se konfiguruje frr
`cd /etc/frr`
Zapneme služby dle výběru v souboru `daemons`
``` bash
bgpd=no
ospfd=no
ospf6d=no
ripd=no
ripngd=no
isisd=no
pimd=no
pim6d=no
nhrpd=no
eigrpd=yes
sharpd=no
pbrd=no
bfdd=no
fabricd=no
vrrpd=no
pathd=no
```

V tomto návodu se budeme zabývat pouze konfigurací `rip` a `eigrp`

## RIP
Zapneme si službu `ripd` v souboru daemons
do `frr.conf` přidáme následující konfiguraci

``` bash
hostname L1
router rip
version 2
network 10.20.30.0/24
network 20.20.30.0/24
redistribute connected
```
network - sítě, kde bude `rip` hledat sousedy se kterými se synchronizovat
redistribute connected - znamená, že ostatním posílá cestu do sítí, které tento server vidí, bude důležité později

Samozřejmě sítě u klíčových slov `network` změníme na své sousední.

Tuto konfiguraci provedeme na všech.

Poté restartujeme službu frr
`systemctl restart frr.service`
případně celý systém
`reboot`

## EIGRP
Zapneme si službu `eigrpd` v souboru daemons
do `frr.conf` přidáme následující konfiguraci

``` bash
hostname L1
router eigrp 1
network 10.20.30.0/24
network 20.20.30.0/24
redistribute connected
no auto-summary
```
router eigrp - zde je nutné definovat "číslo zóny" v našem případě 1
network - sítě, kde bude `eigrp` hledat sousedy se kterými se synchronizovat
redistribute connected - znamená, že ostatním posílá cestu do sítí, které tento server vidí, bude důležité později

Samozřejmě sítě u klíčových slov `network` změníme na své sousední.

Tuto konfiguraci provedeme na všech.

Poté restartujeme službu frr
`systemctl restart frr.service`
případně celý systém
`reboot`


# 4) BONUS - kombinace
Představíme si situaci
``` ascii
+----------+     +---------+     +---------+     +---------+     +---------+
| Windows  | --> | Linux 1 | --> | Linux 2 | --> | Linux 3 | --> | Linux 4 |
+----------+     +---------+     +---------+     +---------+     +---------+
```

Zde je nutné použít na komunikaci mezi Windows a Linux 1 protokol `rip`
Avšak na komunikaci mezi všemi 4 linuxy používáme ze záhadných důvodů `eigrp`

Na windows máme nainstalovanou službu směrování a zapnutý protokol `rip` na interface, který vede k Linuxu 1

Na Linuxu 1 si musíme zapnout předávání packetů
`nano /etc/sysctl.conf`
připíšeme
`net.ipv4.ip_forward=1`
POZOR, musíme restartovat - `reboot`

Poté upravíme konfiguraci Linuxu 1 takto:
``` bash
hostname L1
router eigrp 1
network 100.20.30.0/24
network 30.20.30.0/24
redistribute connected
redistribute rip
no auto-summary

router rip
version 2
network 30.20.30.0/24
redistribute connected
redistribute eigrp
```
Zde právě využíváme potenciál příkazu `redistribute` k tomu, aby nejenom odesílal cesty do sítí, které zná, ale i šířil směrovací tabulku, kterou získal pomocí jiného protokolu.

Samozřejmě sítě u klíčových slov `network` změníme na své sousední.

Poté restartujeme službu frr
`systemctl restart frr.service`
případně celý systém
`reboot`