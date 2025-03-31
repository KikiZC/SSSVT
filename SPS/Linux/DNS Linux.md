## Základní konfigurace
Balíček: bind9

1)      Nastavit pevnou ip - nmtui

2)      V /etc/named.conf:

zde si definujeme adresu serveru
```bash
listen-on port 53 { 50.20.30.1; };
```
zde si definujeme ze které sítě se můžeme ptát, popř. any => můžeme se ptát odkudkoliv
```bash
allow-query { 50.20.30.0/24; any; }
```
poté si dole nadefinujeme svoje zóny
```bash
zone "jdeto.sps" IN {
	type master;
	file "dopred";
}
```
```bash
zone "30.20.50.in-addr.arpa" IN {
	type master;
	file "zpet";
}
```

4)      Ve /var/named si zkopírujeme named.localhost a přejmenujeme na jmeno které jsme napsali ve 3)

5)      **POZOR zde je třeba nastavit práva k souboru na 0777**

6)    	konfigurační soubor zóny

dopředná:
```bash
$TTL 1D
@	IN	SOA jdeto.sps. admin.jdeto.sps. (
							1		; serial
							1D		; refresh
							1H		; retry
							1W		; expire							
							3H)		; minimum
		NS	jdeto.sps.
		A	50.20.30.1
ano		A	50.20.30.2
www		CNAME	jdeto.sps.
```
zpětná:
```bash
$TTL 1D
@	IN	SOA 30.20.50.in-addr.arpa admin.jdeto.sps. (
							1		; serial
							1D		; refresh
							1H		; retry
							1W		; expire							
							3H)		; minimum
		NS	jdeto.sps.
		PTR	jdeto.sps.
2		PTR ano.jdeto.sps.
```

7)      Otevřeme si resolv.conf, zde nastavíme nameserver na nas DNS
```bash
nameserver 50.20.30.1
```
**Po rebootu je třeba tento soubor upravit znovu**

## Konfigurace sekundárního serveru
- při přidání záznamu do zóny je nutno změnit serial
```bash
	1		; serial
```
- v opačném případě se zóna znovu nepřenese a sekundární server nebude znát nové záznamy
### Na sekundáru
1)      Nastavit pevnou ip - nmtui

2)      V /etc/named.conf:

zde si definujeme adresu serveru
```bash
listen-on port 53 { 50.20.30.1; };
```
zde si definujeme ze které sítě se můžeme ptát, popř. any => můžeme se ptát odkudkoliv
```bash
allow-query { 50.20.30.0/24; any; }
```
poté si dole nadefinujeme svoje zóny
```bash
zone "jdeto.sps" IN {
	type slave;
	masters { 50.20.30.1; };
	file "slaves/dopred";
}
```
```bash
zone "30.20.50.in-addr.arpa" IN {
	type slave;
	masters { 50.20.30.1; };
	file "slaves/zpet";
}
```

### Na primárním
3)      V /etc/named.conf:

upravíme definici zóny
```bash
zone "jdeto.sps" IN {
	type master;
	file "dopred";
	allow-transfer { 50.20.30.2; };
	notify yes;
}
```
```bash
zone "30.20.50.in-addr.arpa" IN {
	type master;
	file "zpet";
	allow-transfer { 50.20.30.2; };
	notify yes;
}
```

při více adresách stačí přidat se středníkem další
```bash
allow-transfer { 50.20.30.2; 50.20.30.3; };
```
### Na obou
1)      Vypneme firewall:

	systemctl stop firewalld.service
	
2)      zařídíme aby se znovu nezapínal po restartu

	systemctl disable firewalld.service
	
3)      Postupně restartujeme službu named:
	
	První na primárním
	`systemctl restart named.service`
	
	Poté na sekundárním
	`systemctl restart named.service`

3)      Nakonec příkazem `nslookup` ověříme funkčnost