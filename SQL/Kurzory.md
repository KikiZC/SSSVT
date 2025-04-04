- Kurzory prochází jednotlivé řádky výsledku dotazu a vykonává nad nimi operace
- Neskutečně pomalé, neefektivní

## Typy kurzorů
### Statický
Udělá si "snapshot" na začátku a pracuje s ním, nehledí na aktuální změny dat při běhu kurzoru
### Dynamický
Promítá i změny které proběhnou během běhu kurzoru


## Syntax
``` sql
DECLARE @OrderID INT, @Total MONEY;

DECLARE order_cursor CURSOR FOR
SELECT OrderID FROM Orders;

OPEN order_cursor;

FETCH NEXT FROM order_cursor INTO @OrderID

WHILE @@FETCH_STATUS = 0
BEGIN
	SELECT @Total = SUM(UnitPrice * Quantity * (1-Discount))
	FROM [Order Details]
	WHERE OrderID = @OrderID

	INSERT INTO OrderTotals(OrderID, Total)
	VALUES (@OrderID, @Total)

	FETCH NEXT FROM order_cursor INTO @OrderID
END

CLOSE order_cursor;
DEALLOCATE order_cursor;
```

1) Deklarujeme si proměnné se kterými budeme pracovat
2) Deklarujeme kurzor pro `SELECT` nad jehož daty bude pracovat
3) Načteme si první řádek pomocí `FETCH NEXT`
4) Postavíme `WHILE` cyklus, který zpracuje jeden řádek a na konci si načte další
5) Nakonec kurzor zavřeme a dealokujeme - tím se smaže a nelze znovu otevřít
- Podmínka `@@FETCH_STATUS = 0` bude pro VŠECHNY KURZORY STEJNÁ
- `WHILE` zde funguje spíš jako "Until" - běží DOKUD není jeho podmínka splněna
