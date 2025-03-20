trigger je prvek v SQL databázích která sleduje tabulku a při provedení nastavené akce tak spustí blok kódu 

- speciální tryp uložené procedury   
- spouští se při určité události  
  - Upadte  
  - Insert  
  - delete  
  
**poznámka trigger je vždy transakce**  
  
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