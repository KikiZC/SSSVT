- postupně ukazuje na jednotlivé řádky   
- prochází jednotlivé vybrané záznamy (For Each cyklus)  
- týkají se hlavně SELECTU  
  
### typy kurzorů  
- statický (pracuje z daty tak jak jsou při začátku dotazu)  
- dynamický (když se data při běhu změní změní se i output)  
  
## základní syntaxe   
  
### deklarace  
````SQL  
DECLARE [název]_curozor CURSOR FOR  
SELECT [jaký řádek platí] FROM [pro jaké tabulku platí]  
````  
### později musíme otevřít  
````SQL  
OPEN [název]_curozor  
````  
### zavolat si řádek a ukláda do proměné   
````SQL  
FETCH NEXT FROM [název]_curozor INTO @[název proměné]  
````  
pozn:. řádek se "uloží" do dané proměnné 
### while ciklus   
````SQL  
WHILE [podmínka]  
BEGIN  
[co se má provést(práce z daním řádkem)]
END 
````  
pozn:. cyklus běží dokud podmínka není true\  
### zavolat další řádek  
````SQL  
FETCH NEXT FROM [název]_curozor INTO @[název proměné]  
````  
### po skončení cyklu je potřeba kurzor ukončit a vyčistit z paměti  
````SQL  
CLOSE [název]_curozor  
DEALLOCATE [název]_curozor  
````  
  