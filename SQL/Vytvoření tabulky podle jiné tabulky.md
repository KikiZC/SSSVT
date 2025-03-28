Někdy je potřeba vytvořit kopii tabulky jako archiv a jen přidat datum jako rezdělení

### Postup
0. Vysvětlivky:
- **Tabulka** = název tabulky co chceme vytvořit
- **Kopírák** = tabulka kterou chceme zkopírovat
- **Sloupec** = název nového sloupce v tabulce

1. Začnu podmínkou, abych nepřemazal archiv kdyby již existoval
```sql
IF NOT EXISTS (SELECT * FROM sys.tables WHERE name = 'Tabulka')
```

2. Zkopíruji informace z tabulky
```sql
SELECT * INTO [Tabulka] FROM [Kopírák] WHERE 1 = 0
```

3. Přidáme sloupec s datumem
```sql
ALTER TABLE [Tabulka] ADD [Sloupec] DATETIME DEFAULT GETDATE()
```

4. Celý kód:
```sql
IF NOT EXISTS (SELECT * FROM sys.tables WHERE name = 'Název tabulky')
BEGIN
	SELECT * INTO [Tabulka] FROM [Kopírák] WHERE 1 = 0

	ALTER TABLE [Tabulka] ADD [Sloupec] DATETIME DEFAULT GETDATE()
END
GO
```