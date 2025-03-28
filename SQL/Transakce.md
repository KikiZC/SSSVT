Transakce je prvek v SQL který nám umožnuje dělat operace které při případě že by došlo ke chybě spadnou a celé se ukončí a nedostanou se nám do databáze chybná nebo nesprávná data
- většinou ukládáme do [[Procedura|procedury]]
- mají dvě možnosti "žití" v tzv:. Catch, Try bloku 
- řídí se takzvaným [[ACID]] principem 

základní syntaxe 

```SQL
BEGIN TRANSACTION
BEGIN TRY
	[kód procedůry]
	COMMIT TRANSACTION
END TRY
BEGIN CATCH
	[kód když dojde k problému v prvním bloku]
	ROLLBACK TRANSACTION
END CATCH
```