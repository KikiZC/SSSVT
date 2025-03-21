Procedura je prvek v SQL která umožnuje přidání uživatelského vstupu (proměnách), a poté s nimi pracovat.\
procedůra ukládá kód bloku který se do DB uloží a jde znovu zpustit klidně i z jinými parametry 
- nevrací žádný datový typ
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

