=kryptografie

=nauka o metodách utajování smyslu zpráv převodem do podoby, která je čitelná pouze se speciální znalostí

Míra neuspořádatelnosti = míra entropie

## Symetrické šifrování

Máme jeden klíč, kterým šifrujeme i dešifrujeme

### Výhoda

Jednoduchost

Výpočetní výkon

### Nevýhoda

Nutnost sdílení klíče (resp. Domluvit se předem na klíči)

Metody: DES, Triple DES, AES

  

## Asymetrické šifrování

### Dva klíče

Public a Private

Generují se současně

Jsou matematicky závislé, ale z public nejde získat private

Public pouze šifruje

Private pouze dešifruje

Nelze pomocí public zpětně rozšifrovat data

Jakmile jsou data zašifrována pomocí public, jediná možnost dešifrování je pomocí private key

Dnes se používá metoda RSA, která využívá prvočísla

Další metody: Diffie-Hellmanova výměna klíčů, ElGamal

## Digitální podpis

=speciální druh podpisu, který je zajištěn certifikátem