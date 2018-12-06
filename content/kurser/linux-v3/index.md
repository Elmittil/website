---
title: linux (v3)

author:
    - lew
    - mos
revision:
    "2018-12-21": (G, mos) Inför skapandet av linux v3, nytt namn, syfte, förkunskaper och kurskod.
    "2017-12-21": (F, mos) Genomgången inför vt18.
    "2017-12-18": (E, mos) Bort varningstext.
    "2016-12-16": (D, mos) Förberedelse inför linux-v2.
    "2016-09-09": (C, mos) Bytte till rätt kursnamn.
    "2015-08-03": (B, mos) Klar med texter för kursmomenten.
    "2015-03-02": (A, mos) Första revisionen inför kursstart HT2015.
...
Kursen linux (v3)
==================================

Kursen **Operativsystemet Linux och virtualiseringstekniker**, a.k.a. *linux*, och syftet med kursen är att studenten ska lära sig operativsystemet Linux och dess beståndsdelar såsom processer, filsystemet och terminalen. Kursens fokusområden ligger även i operativsystemets uppbyggnad, programhantering och serverhantering samt att programmera i språket bash. Studenten ska även lära sig skapa virtualiseringstekniker såsom VirtualBox och Docker.

<!--more-->

[WARNING]

**Kursutveckling pågår**

Kursen ges hösten 2019 läsperiod 1.

[/WARNING]

Kursen har två fokus, dels att lära ut grunder och beståndsdelar i operativsystemet Linux och dels att lära ut programmering med JavaScript och Node.js i en Linux-miljö. Kursen är för de som skall jobba med webbprogrammering.

Kursen börjar med att du installerar en egen version av Linux. Därefter lär du dig de grundläggande koncepten i Linux såsom terminalen, filsystemet, process-begreppet och att installera tjänster och programvaror och servrar. Du skriver skript-program i programspråket BASH och via praktiska övningar lär du dig mer om grunderna i Linux.

Samtidigt bygger du upp en utvecklingsmiljö för JavaScript och Node.js. Du utforskar Node.js API och via praktiska övningar programmerar du JavaScript-servrar och tjänster som sedan körs i din Linux-miljö.

I slutet av kursen får du visa dina färdigheter i ett praktiskt programmeringsprojekt.



Krav på labbmiljö {#labb}
------------------------

I kursen installerar du en operativsystemet Linux på din egna maskin med virtualiseringssystemet VirtualBox. Du behöver ha en dator med minst 8GB internminne för att det skall fungera bra. Med mindre internminne tar det längre tid att genomföra övningarna och det kan kännas trögt.

Du kan också genomföra installationen på en annan dator, en äldre laptop till exempel. Eller så kan du använda dig av virtuella servrar som du installerar på egen hand.

Kort och gott, du skall installera en linux-server och du behöver ha en tillräckligt bra miljö för att det skall fungera utan bekymmer.



Förkunskaper {#forkunskaper}
------------------------

Det formella förkunskapskravet är:

> För tillträde till kursen krävs 22,5hp programmering, webbteknologier och databaser.



Innehåll {#innehall}
------------------------

Kursen omfattar följande områden:

* Installation av Linux och Linux som server. Paket och pakethantering 
* Installation av servrar likt webbserver, databas, PHP, sshd.
* Linux med terminal (bash), ssh, vim, och systemkommandon.
* Operativsystemets olika delar såsom filsystemet, processer och processhantering.
* Skriptprogrammering i bash
* JavaScript och Node.js.
* Programmering i Linux-nära miljö med JavaScript och Node.js - filsystem och processer.
* Felsökning och tekniker att debugga sitt program.
* Utvecklingsmiljö och verktyg för utveckling med JavaScript, Node.js i en Linux-miljö.



Mål {#mal}
------------------------



###Kunskap och förståelse {#kunskap}

Efter genomförd kurs skall studenten:

* påvisa grundläggande förståelse för operativsystemet Linux genom att skriftligen beskriva och sammanfatta erfarenheter och observationer från övningar och projekt.
* påvisa goda kunskaper i att använda JavaScript på serversidan tillsammans med Node.js och Linux genom att tillämpa dessa tekniker i praktiska övningar och projekt.



###Färdighet och förmåga {#fardighet}

Efter genomförd kurs skall studenten:

* självständigt utveckla, dokumentera och presentera ett projekt baserat på programmering med JavaScript, Node.js i en Linux-miljö.
* ha god praktisk förmåga att hantera de verktyg och miljöer som används vid utveckling och felsökning för JavaScript, Node.js i en Linux-miljö.



Kursmoment {#kursmoment}
------------------------

Kursen är uppdelad i kursmoment där varje kursmoment uppskattas till 20h studerande i form av programmering, undersökning, läsande, övningar, uppgifter, redovisning och eftertanke. Alla kursmoment skall redovisas och du samlar alla redovisningar i din me-sida.


###Kmom01: Linux som server. {#kmom01}

Det första kursmomentet går ut på att installera Debian/Linux och logga in på maskinen som en server, via SSH.

För att lyckas med det så behöver du bekanta dig med grunderna i terminalen och lära dig ett par av de viktigaste kommandona som utförs i terminalen.

[Instruktion till kursmoment 01](kurser/linux-v3/kmom01).



###Kmom02: Apache Virtual Hosts. {#kmom02}

Nu har vi en Linux-server. Låt oss installera ett par webbplatser på den. Det låter som en vettig syssla för en webbprogrammerare.

Ett bra sätt att installera många webbplatser på en och samma maskin är Apache Virtual Hosts och det är något vi skall bekanta oss med.

Samtidigt behöver vi bekanta oss med fler Unix-kommandon så vi känner oss hemma i terminalen, SSH och att jobba med Linux som en server.

[Instruktion till kursmoment 02](kurser/linux-v3/kmom02).



###Kmom03: Skript med Bash. {#kmom03}

Mycket handlar om att förenkla vardagen som programmerare genom att automatisera de processer och rutiner man utför. En hel del av det vi gör kan automatiseras via skript, till exempel bash-skript med kommandon. Men för att göra det behöver vi ha koll på hur man skapar skript och hur man programmerar i bash.

[Instruktion till kursmoment 03](kurser/linux-v3/kmom03).



###Kmom04: Server med Node.js. {#kmom04}

Nu har vi en Linux-server, en webbserver och vi kan grunderna i att bygga skript i bash. Låt oss nu kika på en annan sak, hur man bygger egna servrar i Linux med Node.js.

Så, vi behöver starta med att installera Node.js på servern och komma igång med hur Node.js fungerar. Vi kör på med några övningar och sedan ser vi hur man byggger upp en enkel webbserver, eller webbtjänst, med Node.js. Vi närmar oss ett gränsland där webbservern blir till en webbtjänst. Det blir tydligt i hur vi använder Node.js för att skapa kod som både hanterar webbservern som sådan och lägger till tjänster som utförs av javaScript-funktioner.

[Instruktion till kursmoment 04](kurser/linux-v3/kmom04).



###Kmom05: Webbtjänst med RESTful API. {#kmom05}

Nu har vi en Linux-server, en webbserver, vi kan grunderna i att bygga skript i bash och vi kan bygga servrar med Node.js. Låt oss fortsätta titta på serverprogrammering i Node.js och se hur en mer renodlad webbtjänst kan se ut och fungera.

Du kommer få en färdig server och ett RESTful API till servern. Din uppgift är att bygga en klient till servern, enligt en kravspecifikation. Så är upplägget. Låt se hur bra vingarna bär.

[Instruktion till kursmoment 05](kurser/linux-v3/kmom05).



###Kmom06: Klient och server. {#kmom06}

Du bygger vidare på dina kunskaper om webbtjänster och programmerar nu båden en klient och en server och ser hur koden fördelar sig mellan klient och server.

[Instruktion till kursmoment 06](kurser/linux-v3/kmom06).



###Kmom07/10: Projekt och examination {#kmom10}

Avslutningsvis gör du ett projekt enligt en specifikation. Projektet är det sista som du gör och tillsammans med alla redovisningar som finns på din me-sida så används detta som underlag för att examinera dig från kursen.

[Instruktion till kursmoment 10](kurser/linux-v3/kmom10).



Kurslitteratur {#litteratur}
----------------------------

[Måste jag skaffa kurslitteraturen](kurser/maste-jag-skaffa-kurslitteraturen)?



###Kurslitteratur {#kurslitteratur}

Som kurslitteratur har jag valt följande bok, tillsammans med ett antal artiklar som finns tillgängliga på nätet. 

Det finns läsanvisningar i samband med varje kursmoment.


* **[The Linux Command Line](kunskap/boken-the-linux-command-line)** -- William Shotts  
    En lättläst och trevlig bok med öppen licens som gör att boken finns tillgänglig fritt på bokens webbplats. Boken ger en bra introduktion till nybörjaren i Linux, systemkommandon och terminalen.

* **[Exploring ES6](kunskap/boken-exploring-es6)** -- Axel Rauschmayer  
    En bok om ES6 som förutsätter att man kan ES5.



###Referenslitteratur {#referenslitteratur}

Följande böcker har jag valt som referenslitteratur. De kan vara bra att ha tillhands och ger lite extra läsmöjligheter. De behövs inte för att klara kursen men vill du bemästra kursens område så är dessa böcker bra startpunkter.

* **[The Debian Administrator's Handbook, Debian Wheezy from Discovery to Mastery](kunskap/boken-the-debian-administrator-s-handbook)** -- Raphaël Hertzog, Roland Mas  
    En gedigen referensmanual för den som är allvarlig med att lära sig Linux.



###Övrig litteratur {#ovriglitteratur}

Det finns närliggande litteratur som är intressant för den som vill fördjupa sig i ämnet eller den som vill skaffa sig förkunskaper innan kursen.


* **[Speaking JavaScript: An In-Depth Guide for Programmers](kunskap/boken-speaking-javascript)** -- Axel Rauschmayer  
    En bok om att komma igång med JavaScript som programmeringsspråk. Fungerar för nya programmerare såväl som för de som redan kan ett eller ett par programmeringsspråk.

* **[JavaScript: The Good Parts](kunskap/boken-javascript-the-good-parts)** -- D. Crockford  
    En genomgång av JavaScript Core och hur man ska, och inte ska, skriva sin kod.

* **[JavaScript: The definitive Guide](kunskap/boken-javascript-the-definitive-guide)** -- D. Flanagan  
    En tegelsten, komplett med allt du vill veta om språket JavaScript med dess Core, DOM och eventhantering, inklusive en referens till olika funktioner. Perfekt för dig som verkligen vill JavaScript.



Läsanvisningar {#lasanvisning}
------------------------------

Här följer en sammanställning av de läsanvisningar till kurslitteraturen som ges i varje kursmoment.

| Kursmoment | Linux Command Line | Debian Handbook | Exploring ES6     |
|------------|--------------------|-----------------|-------------------|
| Kmom01     | 1, 2, 3, 4         | 1, 4            |                   |
| Kmom02     | Repetera 1-4       | 6, 7            |                   |
| Kmom03     | 6, 24              |                 |                   | 
| Kmom04     |                    |                 | 1, 2              |
| Kmom05     |                    |                 |                   | 
| Kmom06     |                    |                 |                   | 
| Kmom10     |                    |                 |                   |

Varje kursmoment kan ha fler läsanvisningar som nämns i respektive instruktion för kursmomentet. 



Lektionsplan och rekommenderad studieplan {#schema}
---------------------------------------------

Läser du kursen inom ramen för programmet Webbprogrammering (campus/distans) så finns det en [rekommenderad studieplan inom programmet](program/webbprogrammering/studieplan/termin2) samt en [lektionsplan](program/webbprogrammering/lektionsplan/lasperiod3).

Läser du kursen som en del i ett kurspaket så finns det en [studieplan som är kopplad till kurspaketet](webutv#studieplan).

<!--
För dig som studerar kursen som enskild kurs finns det en [rekommenderad studieplan](linux/studieplan) kopplad till de kurstillfällen som erbjuds.
-->

Vissa av kurstillfällena kan ha en lektionsplan som du får i samband med kursstart. Lektionsplanen visar de tillfällena som är schemalagda träffar.

Finns det en lektionsplan så finns ofta bokningar av salar gjorda i bokningsschemat.

Studieplan, eventuell lektionsplan och eventuellt schema finns tillgängligt via kurstillfället på ITs.

Läs mer om den [rekommenderade studieplanen](kurser/faq/rekommenderad-studieplan) och [lektionsplanen](kurser/faq/lektionsplan-och-schema).



Lärarstöd och handledning {#handledning}
----------------------------------------

Schemalagda labbtillfällen, hangouts samt forum och chatt de viktigaste källorna för handledning. Läs om [handledning och hjälp-till-självhjälp](kurser/faq/lararstod-och-handledning).



Ladok {#ladok}
------------------------

Enligt kursplanen finns ett antal ladokmoment och de är kopplade till kursens kursmoment enligt följande.

| Kursens moment  | Ladok moment enligt kursplan  | Betyg |
|-----------------|-------------------------------|-------|
| Kmom01 + kmom02 | Uppgift 1 á 2.5hp             | G-U   |
| Kmom03 + kmom04 | Uppgift 2 á 2.5hp             | G-U   |
| Kmom05 - kmom10 | Projekt á 2.5hp               | A-F   |

Den sista inlämningen bestämmer kursens slutbetyg vilket utfärdas när samtliga moment godkänts.

Läs mer om [rapportering av resultat](kurser/faq/resultatrapportering).



Betygsättning {#betyg}
------------------------

Det finns ett särskilt dokument som beskriver [hur bedömning och betygsättning sker](kurser/bedomning-och-betygsattning). 



Kursutvärdering och kursutveckling {#kursutvardering}
-----------------------------------------------------

Det finns ett särskilt dokument som beskriver hur arbetet med kursutvärderingar och kursutveckling sker. Det är oerhört viktigt för mig att du säger till vad du tycker om kurs och kursmaterial, du kan alltid hojta till i både forum, chatt eller mail.

Läs om hur [vi jobbar med kursutvärdering och kursutveckling](kurser/kursutvardering-och-kursutveckling).



Kursplan {#kursplan}
-----------------------------------------------------

Kursplanen är kursens formella dokument som fastställts av högskolan. När kursen utvärderas görs det mot kursplanen. I kursplanen kan du läsa om kursens klassificering, syfte, innehåll, mål, generella förmågor, lärande och undervisning, bedömning och examination, litteratur, mm.

Från och med hösten 2019 heter kursen "Operativsystemet Linux och virtualiseringstekniker". Du hittar [kursplanen genom att söka på kurskoden DV1611 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1611).

Fram till och med våren 2019 gick kursen under namnet "Programmera webbtjänster i Linux". Du hittar [kursplanen genom att söka på kurskoden DV1547 via BTH's hemsida](http://edu.bth.se/utbildning/utb_kursplaner.asp?KKurskod=DV1547).

Under våren 2019 fanns en kurskod DV1609 med justerade förkunskapskrav jämfört med DV1547. Men den kursen har inget kurstillfälle.



Tidigare utgåvor {#tidigare}
-----------------------------------------------------

Kursen [linux (v3)](kurser/linux-v3) bygger på kurskoden DV1611.

Kurserna [linux (v2)](kurser/linux-v2) och [linux (v1)](kurser/linux-v1) bygger på kurskoden DV1547.
