---
title: "Uppgift: EShop CRUD (kmom07)" 
description: "Uppgift att implementera databasen eshop."
revision:
    "2026-02-27": "(A) Första utgåvan."
sidebar:
    order: 0070
---

Denna uppgift görs som en del av kmom07. Du jobbar vidare på den databasmodell som du skapade i kmom04-06.

Du skall färdigställa schemat databasen för eshop och börja jobba med den. Första steget, när schemat är på plats, är att fylla databasen med innehåll och implementera CRUD (Create Read Update Delete) mot vissa av tabellerna i databasen med hjälp av ett terminalprogram i CSharp.

Denna uppgiften är också en del av det kommande projektet i kmom10, så den koden du skriver här är egentligen en del av det examinerande kmom10.



:::danger
Kursmomentet är ännu ej redigerat, informationen är inte korrekt.
:::



## Förutsättning

Du har din databasmodell klar för din eshop och du har SQL-kod för att skapa tabeller och vyer.



## Krav - CSharp

Utför följande krav.

1. Skapa ett CSharp projekt i katalogen `kmom/07/Eshop`. Följ samma struktur som du gjort i kmom04-06.

1. Dela upp koden i klasser. Organisera din kod så att den är DRY. Refaktorisera när det behövs.

1. Koden skall passera `roslynator analyze` enligt Roslyn.



## Krav - Innehåll i databasens tabeller

Utför följande krav.

1. Skapa underkatalogen `sql` där du placerar din `setup.sql` som innehåller SQL-kod för att skapa databasen `eshop` tillsammans med tabeller och vyer i databasen. Det är fritt fram att justera SQL-koden som skapar schemat, även om det inte följer din ursprungliga ER-modell. Se framåt och gör bättre efterhand som du lär dig mer om din databas.

1. Skapa filen `insert.sql` där du placerar SQL-kod som fyller databasens tabeller med innehåll.

    1. Vilka tabeller?

    1. Om du väljer att göra `LOAD DATA INFILE` med hjälp av csv-filer så skall csv-filerna placeras i samma katalog och sökvägar skall vara relativa.

1. Skapa filen `proc.sql` där du placerar SQL-kod som skapar lagrade procedurer, triggers och funktioner.

1. Skapa filen `eshop.puml` där du placerar en uppdaterad version av din databasmodell i PlantUML format. Denna skall vara uppdaterad och spegla den databas du har skapat. För att göra det enkelt, prova att ge koden i `setup.sql` till din Ai-kompis och fråga om den kan generera ett ER-diagram i PlantUML format utifrån det. Det kan den ofta göra, för denna delen av uppgiften är det ok att använda Ai på det viset.



## Krav - En menydriven applikation

Ditt terminalprogram skall byggas på samma sätt som du gjort i kmom04-06 med samma typ av meny.

Följande är de menyvalen som skall stödjas.

```text
$ dotnet run
items <search>        - Show (or filter) all products that are in the marketplace
                      - or in the inventory, combine into one single report, one
                      - output table.
log <limit> <search>  - Show (or limit, filter) all entries in the log.
```

Funktioner?



## Avslutningsvis

Glöm inte kontrollera att lintern passerar.

Fundera på om din kod är DRY eller om det finns delar som du kan förbättra.
