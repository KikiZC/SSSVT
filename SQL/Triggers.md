trigger je prvek v SQL databázích která sleduje tabulku a při provedení nastavené akce tak spustí blok kódu 

- speciální typ uložené procedury   
- spouští se při určité události  
  - Update  
  - Insert  
  - Delete  
  
**poznámka trigger je vždy [[Transakce]]** 
  
Vytváříme   
```SQL  
CREATE OR ALTER TRIGGER TRG_[název triggeru]  
ON [tabulká kterou sleduje]  
AFTER [po jaké akci se bude spoštět]  
AS BEGIN  
END  
```  
  
### after trigger  
- spustí se po akci  
### insted of   
- spustí se místo akce  
  
### Systémové tabulky pro trigger  
- inserted   
  - Tabulka která obsahuje nově vložené řádky nebo upravené tádky   
- deleted  
  - Tabulka která obsahuje smazané řádky
