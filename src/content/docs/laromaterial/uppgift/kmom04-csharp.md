---
title: "Uppgift: CSharp bank (kmom04)" 
description: "Uppgift att skapa ett bank-liknande program i CSharp som använder sig av transaktioner."
revision:
    "2026-02-08": "(A) Första utgåvan."
sidebar:
    order: 0040
---

Denna uppgift görs som en del av kmom04.



## Förutsättning

Du behöver ha jobbat igenom övningen "Transaktioner i databas" och du behöver veta hur man använder transaktioner i ett CSharp program.



## Krav - CSharp

Utför följande krav.

1. Skapa ett CSharp projekt i katalogen `kmom/04/Bank`.

1. Dela upp koden i klasser.

1. Bygg en liknande meny-hantering som du jobbade med i förra uppgiften.

1. Du bör organisera din kod så att den är DRY (Do not repeat yourself).

1. Koden skall passera `roslynator analyze` enligt Roslyn.



## Krav - Databas

Utför följande krav.

1. Skapa katalogen `kmom/04/Bank/sql`.

1. Skapa filen `setup.sql` där du skapar en databas som du döper till "bank" på samma sätt som du skapade en databas i övningen för transaktioner. Glöm inte att lägga till collations.

1. I filen `setup.sql` lägger du till SQL DDL för att skapa de tabeller som behövs.

1. I filen `setup.sql` fyller du tabellerna med innehåll.

1. Försäkra dig om att SQL-koden i `setup.sql` kan köras minst två gånger efter varandra och producera exakt likadant schema i databasen och samma innehåll.

1. Din databas skall ha en tabell som heter `account` som representerar bankkonton. Varje konto har (minst) ett id och en balans.

1. Din databas skall ha en tabell som heter `customer` där kunden har (minst) ett namn och bor på en ort.

1. Ett konto tillhör en kund. En kund kan ha flera konton.

1. Din databas skall (minst) innehålla kunderna Adam och Eva. Adam skall ha ett konto med 10 bitcoin. Eva skall ha ett konto med 7 bitcoin och ett konto som innehåller 0 bitcoin.

1. Det skall finnas ett "hemligt konto" som ägs av den hemliga kunden som heter Doe. Detta hemliga kontot fylls på med 0.01 bitcoin varje gång som pengar flyttas mellan konton. Till exempel, om Adam flyttar 1.5 bitcoin till Eva så får Eva bara 1.49 bitcoin och 0.01 bitcoin hamnar på det hemliga kontot.

1. Använd PRIMARY KEY och FOREIGN KEY i dina tabeller.



## Krav - En menydriven applikation

Skapa en menydriven applikation C# som ser ut så här för användaren.

När programmet startas så skrivs meny ut. Du kan formattera utskriften av menyn efter dina egna tankar.

```text
$ dotnet run
menu, help, h      - Print out the menu.
customer <search>  - Show all customers or filter by <search>
account <search>   - Show all accounts (except the secret one) with the customers name
                   - or filter by <search>
move               - Move 1.5 bitcoin from Adam to Eva (do not forget the secret account)
move <amount> <from> <to>
                   - Move a flexible amount of bitcoin from one account to another account
                   - (do not forget the secret account)
swish <amount> <to>
                   - Add <amount> to the account <to>, do not forget to take 0.01 bitcoin 
                   - as a transaction fee and put inot the secret account. 
secret             - Show the balance of the secret account with the name of the owner of
                   - the account.
quit, q            - Quit the application

> 
```

Programmet väntar därefter på användarens inmatning. Om användaren skriver menu visas menytexten. Om användaren skriver quit eller q avslutas applikationen.

När man söker/filtrerar så skall det stödjas att man söker på kontonumret, kundens namn, kundens ort.

Bygg stöd för samtliga menyval ovan.

Det är okey om det blir mindre än 0 i balans på ett konto.



## Avslutningsvis

Glöm inte kontroller att lintern passerar.

Fundera på om din kod är DRY eller om det finns delar som du kan förbättra.
