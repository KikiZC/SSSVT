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
- `WHILE` zde funguje spíš jako "Until" - běží DOKUD není jeho podmínka splněna
- Podmínka `@@FETCH_STATUS = 0` bude pro VŠECHNY KURZORY STEJNÁ

## Postup vytvoření
#### 1) Deklarujeme si proměnné se kterými budeme pracovat
```sql
DECLARE @Prom1 INT, @Prom2 NVARCHAR(255);
```
- například
	```sql
	DECLARE @CustomerID NCHAR(5), @OrderCount INT;
	```

#### 2) Deklarujeme kurzor pro `SELECT` nad jehož daty bude pracovat
```sql
DECLARE <Název kurzoru>_cursor CURSOR FOR
SELECT <Něco> FROM <Odkud>
```
- například
	```sql
	DECLARE VIP_Customers_cursor CURSOR FOR
	SELECT CustomerID FROM Customers
	```

#### 3) Otevřeme kurzor
```sql
OPEN <Název kurzoru>
```
- například
	```sql
	OPEN VIP_Customers_cursor
	```

#### 4) Načteme si první řádek pomocí `FETCH NEXT`
```sql
FETCH NEXT FROM <Název kurzoru> INTO <Název jedné z promněnných>
```
- například
	```sql
	FETCH NEXT FROM VIP_Customers_cursor INTO @CustomerID
	```

#### 5) Postavíme `WHILE` cyklus, který zpracuje jeden řádek a na konci si načte další
```sql
WHILE @@FETCH_STATUS = 0
BEGIN
	<nějaká práce s tímto řádkem>
	
	FETCH NEXT FROM <Název kurzoru> INTO <Název jedné z promněnných>
END
```
- například
	```sql
	WHILE @@FETCH_STATUS = 0
	BEGIN
		SELECT @OrderCount = COUNT(*) 
			FROM Orders
			WHERE CustomerID = @CustomerID
	
		IF @OrderCount > 10
		BEGIN
			INSERT INTO VIPCustomers
			VALUES (@CustomerID, @OrderCount)
		END
		
		FETCH NEXT FROM VIP_Customers_cursor INTO @CustomerID
	END
	```
	- V prvním kroku spočítám počet objednávek každého zákazníka
	- Ve druhém kontroluji zdali jich má více než 10 a pokud ano, tak ho zapíši do tabulky VIP zákazníků

#### 6) Nakonec kurzor zavřeme a dealokujeme - tím se smaže a nelze ho znovu otevřít
```sql
CLOSE <Název kurzoru>
DEALLOCATE <Název kurzoru>
```
- například
	```sql
	CLOSE VIP_Customers_cursor
	DEALLOCATE VIP_Customers_cursor
	```

## Shrnutí postupu
V každém kurzoru musí být vždy nějaké proměnné ([[Kurzory#1) Deklarujeme si proměnné se kterými budeme pracovat|Krok 1]]), a vždy se musí deklarovat ([[Kurzory#2) Deklarujeme kurzor pro `SELECT` nad jehož daty bude pracovat|Krok 2]]).
Kurzor se musí vždy otevřít a zavřít (například jak tomu je s BEGIN a END)([[Kurzory#3) Otevřeme kurzor|Krok 3]] a [[Kurzory#6) Nakonec kurzor zavřeme a dealokujeme - tím se smaže a nelze ho znovu otevřít|Krok 6]]).
A nakonec každý kurzor musí mít posunutí na další záznam ([[Kurzory#4) Načteme si první řádek pomocí `FETCH NEXT`|Krok 4]]) a smyčku která projde všechny záznamy ([[Kurzory#5) Postavíme `WHILE` cyklus, který zpracuje jeden řádek a na konci si načte další|Krok 5]])

### Celkový výstupní kód
```sql
DECLARE @Prom1 INT, @Prom2 NVARCHAR(255); -- Krok 1

DECLARE <Název kurzoru>_cursor CURSOR FOR -- Krok 2
SELECT <Něco> FROM <Odkud>

OPEN <Název kurzoru> -- Krok 3

FETCH NEXT FROM <Název kurzoru> INTO <Název jedné z promněnných> -- Krok 4

WHILE @@FETCH_STATUS = 0 -- Krok 5
BEGIN
	<nějaká práce s tímto řádkem>
	
	FETCH NEXT FROM <Název kurzoru> INTO <Název jedné z promněnných>
END

CLOSE <Název kurzoru> -- Krok 6
DEALLOCATE <Název kurzoru>
```