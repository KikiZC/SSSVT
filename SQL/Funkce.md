Funkce je prvek v SQL který umožnuje spouštět část kódu, příjmat vstup od uživatele, a vracet proměnou podle naších potřeb 
- neumí provádět komplikovanější operace 
- používá se spíše pro výpočet abyhom nemusely psát vzorečky v dotazech furt dokola\

rozdělujeme na
1. skalární - vrací jedno číslo, string, atd. 
2. tabulkové - vrací tabulku

základní syntaxe:
```SQL
CREATE OR ALTER FUNCTION dbo.[název funkce] (@[název promněné] [datový typ] @[název proměné] [datový typ] ...)
RETURNS [co vrací za datový typ nebo tabulka]
AS BEGIN
RETURN [kód který nakonci vrací proměnou]
END
```
