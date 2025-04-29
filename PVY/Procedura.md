Procedura je prvek v SQL která umožnuje přidání uživatelského vstupu (proměnných), a poté s nimi pracovat.
Procedura ukládá kód bloku který se do DB uloží a jde znovu zpustit klidně i s jinými parametry 
- nemusí vracet žádný datový typ, ale může
- umí `update, delete atd.`


základní syntaxe:

```SQL
CREATE OR ALTER PROCEDURE SP_[jméno procedůry]
@[jméno proměné] [datový typ],
@[jméno proměné] [datový typ]
...
AS BEGIN
[kód procedůry]
END
```

