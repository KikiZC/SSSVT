## Postup
1)      Disky
2)      Slozeni do pole
3)      Zapsat do configu
4)      Soub. Sys. + mountovaci místo
5)      Fstab

## Příkazy

### Vytvoření
mdadm --create /dev/md5 --level=5 --raid-devices=3 /dev/sd[b-g]

--level - level raidu
--raid-devices - kolik disků se použije na raid, ostatní zůstanou jako spare
/dev/sd[b-g] - disky sdb, sdc, sdd...

### Uložení do configu
echo "DEVICES /dev/sd[b-g]" > /etc/mdadm.conf
mdadm --examine --scan --config=/etc/mdadm.conf >> /etc/mdadm.conf

## Postup
- Přidáme disky podle RAIDU
	- R1 = velikost jednoho disku
	- R0 = kapacita /* počet disků
	- R5 = kapacita /* (počet disků - 1)
- Složíme pole
	- Použijeme příkaz **mdadm** s parametry:
		- --create <název (/dev/md5)>
		- --level=<číslo raidu>
		- --raid-devices=<počet> <vypíši všechny>
	- Výsledný příkaz: `mdadm --create /dev/md5 --level=5 --raid-devices=7 /dev/sd[bcdefgh]`
	- Potvrdíme **Enterem**
	- Zkontrolujeme pomocí `mdadm --detail /dev/md5`
	- Zapíšeme do configu pomocí: `echo “DEVICE /dev/sd*[b-n]“ > /etc/mdadm.conf`
	- Přidáme zbytek: `a. mdadm --examine --scan >> /etc/mdadm.conf`
- Přidáme filesystem
	- Uděláme složku pomocí `mkdir /mnt/r5`
	- Přidáme filesystem:
		- `mkfs.<typ> <na jaký raid>`
		- př: `mkfs.ntfs /dev/md5`
- Přiděláme do složky
	- `mount <co> <kam>`
		- `mount /dev/md5 /mnt/r5`