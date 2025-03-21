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