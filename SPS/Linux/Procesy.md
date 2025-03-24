=Něco probíhá

Identifikujeme je podle PID (Process ID)

Každý proces má svého rodiče

## Vytváří ho:

Uživatel, systém nebo jiný proces

## Typy

Systémové – vlastní je systém nebo root, systémové procesy se nazývají démoni

Uživatelské – vlastní je tzv. Efektivní uživatel tj. ten co ho spustil

Vláknové - používá je jádro OS

## Stavy procesu

Běžící - Running

Zastavený – Terminated – CTRL+C

Pozastavený – Sleeping – CTRL+Z

popř. Připravený - proces čeká na input tj. např. spuštění

## Spouštění souborů

Jednou, teď - ./

Jednou, někdy – at

Opakovaně – cron

### Příkaz at

Kdy – např. now+1min

at „kdy“ <enter>

co chci dělat

CTRL+D

### Cron

![crontab](cron.png)

1.       Každou celou hodinu a 3 min tzn. 13:03, 14:03….
2.       Každé 3 minuty tzn. 13:03,13:06