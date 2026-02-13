---
title: "Uppgift: CSharp bank (kmom05)" 
description: "Uppgift att skapa ett bank-liknande program i CSharp som använder sig av transaktioner och lagrade procedurer."
revision:
    "2026-02-13": "(A) Första utgåvan."
sidebar:
    order: 0050
---

Denna uppgift görs som en del av kmom05.



## Förutsättning

Du behöver ha jobbat igenom övningen "Övning: Lagrade procedurer i databas" och du behöver veta hur man använder lagrade procedurer i ett CSharp program.



## Krav - CSharp

Utför följande krav.

1. Skapa ett CSharp projekt i katalogen `kmom/05/Bank` genom att kopiera ditt projekt från `kmom/04/Bank`.

1. Dela upp koden i klasser.

1. Bygg en liknande meny-hantering som du jobbade med i förra uppgiften.

1. Du bör organisera din kod så att den är DRY (Do not repeat yourself).

1. Koden skall passera `roslynator analyze` enligt Roslyn.



## Krav - Lagrade procedurer "flytta pengar"

Utför följande krav.

1. I katalogen `kmom/05/Bank/sql` skapar du filen `procedure_account.sql`.

1. Skapa lagrade procedurer för att flytta pengar mellan konton samt för att swisha till ett konto.

1. Uppdatera din CSharp-kod så att den använder sig av lagrade procedurer för att implementera (minst) följande kommandon.

```text
$ dotnet run
move            - Move 1.5 bitcoin from Adam to Eva (do not forget the secret account)
move <amount> <from> <to>
                - Move a flexible amount of bitcoin from one account to another account
                - (do not forget the secret account)
swish <amount> <to>
                - Add <amount> to the account <to>, do not forget to take 0.01 bitcoin 
                - as a transaction fee and put inot the secret account. 
```


## Krav - Nya tabeller

Utför följande krav.

1. I katalogen `kmom/05/Bank/sql` spara filen `setup_inventory.sql` där du lägger till ett antal tabeller till databasens schema. Du skall alltså jobba vidare med databasen "bank".

1. Din databas skall ha en tabell som heter `product` som är en produktkatalog över "produkter" eller "items" eller "saker" som finns i din bank. Tänk Gringotts bank, där fanns det en massa konstiga saker i bankvalven. I tabellen skall det finnas kolumner för id, name, description, base_price.

1. Lägg till INSERT för att lägga till minst 5 olika produkter i tabellen.

1. Din databas skall ha en tabell som heter `inventory` som är en fysisk representatio av en produkt som ägs av en customer. Kolumner i tabellen skall vara id, quantity, created_at, updated_at (TIMESTAMPS) samt FK customer_id och produkt_id. När en produkt finns i ett inventory så ägs den av en customer.

1. Lägg till INSERT för att lägga till minst 3 olika produkter till varje customer. Det skall finnas minst 2 customers.

1. Det skall finnas en tabell som heter `marketplace` som håller de produkter som är till salu. När en produkt blir tillgänglig så skall den placeras i tabellen marketplace tillsammans med ett pris. Nu är den tillgänglig så att produkten kan köpas av en customer.

1. När en customer köper en produkt så flyttas pengar från kunden till ett konto som ägs av marketplace. Av dessa pengar flyttas 0.01 pengar till det hemliga kontot.

1. När en customer säljer en produkt till marketplace så får customern pengar från marketplace (pengar flyttas i respektive account). Av dessa pengar flyttas direkt 0.01 peng till det hemliga kontot.

1. Det får inte bli noll på ett account. 

1. Skissa på ett ER-diagram i puml som visar hur dina tabeller är kopplade. Spara i filen `bank.puml`. 

1. I övrigt skall databasen fungera enligt kraven i kmom04 för uppgiften.

1. Använd PRIMARY KEY och FOREIGN KEY i dina tabeller.

1. All SQL-kod skall hanteras av lagrade procedurer.

1. Använd transaktioner där det behövs.

1. OPTIONAL Lägg till en ASCII art på  varje produkt för at göra det lite roligare och ge möjligheten att visa upp vilken produkt man har i sitt inventory. Tänk att det är en ny form av NTF.


## Krav - En menydriven applikation

Skapa en menydriven applikation C# som ser ut så här för användaren.

När programmet startas så skrivs meny ut. Du kan formattera utskriften av menyn efter dina egna tankar.

Ditt terminalprogram skall stödja samma menyval som anns som krav i terminalprogrammet i kmom04.

Följande är de nya menyvalen som skall stödjas.

```text
$ dotnet run
marketplace <search>
                - Show all products on the marketplace or filter by <search>
product <search>
                - Show all products in the product catalogue, or show only the 
                - one matching the search string. Make it possible to search all columns.
inventory <customerid>
                - Show all inventory, or show only the one for a specific customer 
                - id.
sell <customerid> <productid> <price>
                - Sell a product from the customers inventory to the marketplace for
                - the specified price.
buy <customerid> <productid>
                - Buy a product from the marketplace to the customers inventory.
market <productid> <price>
                - Add an existing product (from the product table) to the 
                - marketplace for the specified price.
```

Bygg stöd för samtliga menyval ovan.

Glöm inte att även samtliga menyvalen från kmom04 skall fungera, till exempel möjligheten att se account, customer och secret account.



## Avslutningsvis

Glöm inte kontroller att lintern passerar.

Fundera på om din kod är DRY eller om det finns delar som du kan förbättra.
