ACID je souhrn základních principů/pravidel pro transakce v SQL

**Atomicity (Atomicita)** – Transakce musí být buď provedena celá, nebo vůbec. Pokud se některá část nezdaří, musí být zrušeny všechny změny.

**Consistency (Konzistence)** – Transakce musí splňovat standardy aby šla spustit na úplně cizí databázi z minimálními úpravami 

**Isolation (Izolace)** – v databazy transakce na sebe nesmí mýt žádný vliv 

**Durability (Trvalost)** – Jakmile je transakce potvrzena (COMMIT), její změny musí být trvale uloženy i v případě výpadku systému.