---
author: mos
category: labbmiljo
revision:
  "2016-03-07": (C, mos) Ändrade paketnamn på Debian till python3-pip.
  "2014-09-17": (A, mos) Första utgåvan för python kursen.
updated: "2016-04-07 22:46:00"
created: "2014-09-17 13:10:18"
...
Python pakethantering med PIP
==================================

Python har många inbyggda moduler men det finns många fler externa moduler som kan användas. PIP är ett verktyg för att installera sådana externa moduler. Det är en pakethanterare för Pythons externa moduler.

Denna artikel beskriver kortfattat hur du jobbar med PIP och hur du installerar `pip3` för Python 3.

<!--more-->


Om PIP {#pip}
--------------------------------------

PIP är en pakethanterare för python moduler. Du kan läsa om [PIP på deras webbplats](https://pip.pypa.io/en/latest/). 

Som ett exempel på hur det kan se ut när en referens görs till att du *"kan installera modulen med pip"* så kikar vi på [installationsbeskrivningen för Python-modulen `requests`](http://docs.python-requests.org/en/latest/user/install/#install).

Så här står det där.

```bash
pip install requests
```

Nåväl, först behöver vi installera PIP.



Installera PIP för Python 3 {#installera}
--------------------------------------

På webbplatsen finns det instruktioner [hur man installerar PIP](https://pip.pypa.io/en/latest/installing.html#install-pip) generellt sätt. 

Jag vill dock använda PIP tillsammans med Python 3 så det blir lite annorlunda.



###Installera i Windows och Cygwin {#cygwin}

I Cygwin installerar `pip3` jag enligt beskrivningen på PIPs webbplats. Bortsett från att jag använder `pyton3` istället för `python`.

```bash
# Ladda ned installationsfilen
wget https://bootstrap.pypa.io/get-pip.py

# Använd python3 för att installera pip
python3 get-pip.py
```



###Installera i MacOS {#mac}

Jag installerade `python3` med pakethanteraren Brew. Då fick jag också med pakethanteraren `pip3`.



###Installera i Linux {#linux}

För att installera `pip3` i Debian Linux gör jag så här.

```bash
apt-get install python3-pip
```



Använd PIP {#pip}
--------------------------------------



###Vilken version har jag? {#pip1}

Nu kan du köra kommandot `pip3`. Skriv `pip3 --version` för att se vilken version du har och för att dubbelkolla att pip är kopplad mot Python 3.

```bash
pip3 --version
```

Vi kör python 3 och därför använder vi `pip3` som kommando.



###Installera moduler {#pip2}

När du har installerat PIP kan du installera moduler. I exemplet installeras Python-modulen `request`.

```bash
pip3 install requests
```


###Hantera installerade moduler {#pip3}

Du kan kolla upp vilken version du har av en viss modul.

```bash
pip3 show requests
```



Virtual environment {#venv}
--------------------------------------

När man använder pip som vi gjort ovanför installeras paket globalt vilket bl.a. innebär att om vi har flera olika Python projekt på datorn måste alla dem använda samma version av ett paket. Proj1 kan inte använda requests 1.3 medan proj2 använder requests 2.3 utan requests kan bara installeras en gång och då används den överallt.

Lösningen på detta är [Virtual environment](https://docs.python.org/3/tutorial/venv.html) även kallat **venv**. Venv är ett sätt att isolera paket från övriga paket installerade på resten av ett system. Detta gör att vi kan installera paket för specifika projekt utan att det krockar med globala installationer eller andra projekts installationer.

Jag använder paketen från kursen OOPython som exempel. Vi har lagt in kommandon i dbwebb-cli för att förenkla arbetet med venv i kurserna, jag kommer visa hur man gör både med dbwebb-cli och utan.



###Skapa virtuell miljö{#venv_install}

För att skapa en virtuell mijljö behöver man bestämma var man vill placera den. Vi har som standard att lägga den i roten för ett projekt. Sen använder vi modulen `venv` som ska följa med när man installerar Python3.

```bash
# Stå i roten av ditt projekt
python3 -m venv .venv
```

Om man inte har `venv` installerat på Linux kan man få upp följande meddelande:
```bash
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt-get install python3-venv
```
Och gör man som det står och installerar det sen kör man kommandot igen.

Nu har vi skapat en ny mapp som heter `.venv` och det har lagts till en mängd filer och mappar i den.

[FIGURE src=/image/oopython/venv_dir.png caption="Mapp struktur i .venv."]



Avslutningsvis {#avslutning}
--------------------------------------

Kika på hemsidan för PIP för att lära dig fler kommandon om själva pakethanteraren.

Har du frågor kring PIP så finns det en särskild [forumtråd kopplad till denna artikeln](t/2725).




