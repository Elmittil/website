---
author: 
    - aar
    - lew
revision:
    "2018-12-12": (C, aar) La till session.
    "2018-11-26": (B, aar) Skrev om handler koden till en klass.
    "2017-12-01": (A, lew) First version for v2.
category:
    - oopython
...
Flask, POST och GET
===================================

[FIGURE src=/image/oopython/kmom02/topimage-art1.png?w=c5 class="right"]

Vi ska titta närmare på hur man kan jobba med POST och GET i Flask. Målet är att vi ska med hjälp av ett formulär, en tabell, GET och POST, presentera innehåll i vår Flask-applikation. Vi behöver även blanda in Session för att spara data mellan requests på studentservern.

<!--more-->  

Intro {#intro}
-------------------------------
När vi hämtar en webbsida används HTTP-metoden GET. Det man skickar hamnar då synligt i adressfältet, tex: `http://localhost:5000?id=2&car=volvo`.

Vill vi däremot inte att datan, eller informationen vi skickar, ska synas, så kan vi använda metoden POST. POST kan bland annat inte bokmärkas, cachas eller sparas i historiken till skillnad från GET-metoden. POST-data skickas i headern, så den är ej synlig i URL:en.  

[Läs mer om POST och GET](http://www.w3schools.com/tags/ref_httpmethods.asp).

Vi ska som sagt gå igenom båda två och se hur de kan användas tillsammans med Python och Flask. Vill du hänga med och koda själv redan nu kan du skapa filerna som används i artikeln:

[FIGURE src=/image/oopython/kmom02/tree_flask2.png]



Förutsättning {#pre}
-------------------------------

Du har läst delen om GET och POST i guiden "[Php på 20 steg](kunskap/kom-i-gang-med-php-pa-20-steg#globals)" eller vet vad det innebär.  
Du har läst artikeln om "[Flask med Jinja2](kunskap/flask-med-jinja2)".  
<!-- Du har läst artikeln om "[Klassrelationer](kunskap/klass-relationer)".   -->



Struktur {#struktur}
-------------------------------

Innan vi kommer igång med koden kan det vara bra att tänka igenom vad det är man vill åstadkomma. Det minskar risken att hamna snett och behöva kasta kod och göra om. Målet är en sida som kan lägga till en person, en *employee*, i en lista, som i sin tur visas upp i en tabell. Tabellen ska uppdateras automatiskt och vi blandar inte in någon databas, utan vi lämnar koden med några personer hårdkodade. Till detta skapar vi en klass, `Employee`. Vi ska hantera GET och POST i routen och agera korrekt beroende på hur vi skickar en request till routen. När vi klickar på länken i navbaren görs ett GET-request och när vi postar formuläret kan vi använda POST. Vi kan med fördel i detta fallet använda samma route, kallad "company" i artikeln. Vi vill även undvika lösa funktioner i app.py så vi skapar en klass, *Handler*, som får sköta mappningen mellan app.py och Employee objekten.

En vattentät plan är på plats så vi börjar kika på koden.



Visa anställda {#show}
-------------------------------

VI börjar med att snabbt gå igenom app.py som påminner om hur den såg ut i förra kmom:et. Om Något fortfarande är oklart gå tillbaka och läs "[Flask med Jinja2](kunskap/flask-med-jinja2)".

```python
#!/usr/bin/env python3
from flask import Flask, render_template, request, session

app = Flask(__name__)

@app.route("/")
def main():
    """ Main route """
    return render_template("index.html")

```
Vi kikar lite snappt på `index.html` också. Kolla i "[Flask med Jinja2](kunskap/flask-med-jinja2)" för innehållet i header.html, footer.html och style.css.

```
{% include 'header.html' %}

<div class="container">
    <div class="page-header">
        <h1>Visa anställda.</h1>
    </div>
</div>

{% include 'footer.html' %}
```

Okej, nu har vi grunden och går vidare med att skapa Employee klassen.



###employee.py {#emplyee-py}

Vi skapar en simple klass för att hålla data om anställda.

```python
#!/usr/bin/env python3
"""
Class file for Employee
"""
import random

class Employee():
    """
    Class for Employee
    """

    def __init__(self, firstname, lastname, salary):
        """
        init method
        """
        self.firstname = firstname
        self.lastname = lastname
        self.salary = salary
        self.id = random.sample(range(10), 4)

    def get_salary(self):
        """
        Returns the salary
        """
        return self.salary

    def get_id(self):
        """
        Returns the employement id
        """
        return "".join(map(str, self.id))

    def get_name(self):
        """
        Returns name
        """
        return self.firstname + " " + self.lastname
```

Nästa steg blir att skapa Handler klassen så vi kan använda Employee i på hemsidan 



###handler.py {#handler-py}

Handler klassen ska vara bryggan mellan app.py och Employee objekten. Vi börjar med en lista som innehåller alla skapade objekt och en metod som skapar några hårdkodade Employee objekt. 

```python
#!/usr/bin/env python3
"""
Handler file
"""

from employee import Employee

class Handler():
    def __init__(self):
        self.people = []
        self.add_predefined_employees()

    def get_people(self):
        return self.people

    def add_predefined_employees(self):
        emil = Employee("Emil", "Folino", 30000)
        mikael = Employee("Mikael", "Roos", 31000)
        kenneth = Employee("Kenneth", "Lewenhagen", 75000)
        andreas = Employee("Andreas", "Arnesson", 12000)

        self.people.append(emil)
        self.people.append(mikael)
        self.people.append(kenneth)
        self.people.append(andreas)
```

Nu har vi två klasser som vi kan skapa objekt av för att spara data och jobba med den. Innan vi bygger ihop det i app.py skapar vi html koden för att visa upp de anställda.



###templates/tables {#templates-tables}

Vi ska utnyttja Jinja2's funktionalitet för att hantera mallar och skapa mallar, *templates*, för tabellen och formuläret. Som du såg i början av artikeln så har vi mapparna templates/forms och templates/tables.

Vi hoppar in i mappen templates/tables/ och tittar på `show_employees.html`.

Vi skapar en tabell och använder Jinja för att skapa en loop och lägga till varje employee i tabellen.
Här skapar vi en tabell och i `<tbody>` där magin händer, använder vi en [for-loop](http://jinja.pocoo.org/docs/2.10/templates/#for) med hjälp av Jinja som går igenom den en lista med Employee objekt och lägger till dem i tabellen. Detta betyder att vi i app.py måste skicka med en lista med Employee objekt till `render_template()` metoden.

```
<table class="table">
    <thead>
        <tr>
            <th>Name</th>
            <th>Id</th>
            <th>Salary</th>
        </tr>
    </thead>
<tbody>
    {% for person in people %}
    <tr>
        <td>{{ person.get_name() }}</td>
        <td>{{ person.get_id() }}</td>
        <td>{{ person.get_salary() }}</td>
    </tr>
    {% endfor %}
</tbody>
</table>
```

Vi passar även på att inkludera tabellen i index.html 

```
{% include 'header.html' %}

<div class="container">
    <div class="page-header">
        <h1>Visa anställda</h1>
    </div>
    <div class="row">
        <div class="col-md-3 col-md-offset-1">
            <h3>Employed</h3>
            {% include 'tables/show_employees.html' %}
        </div>
    </div>
</div>

{% include 'footer.html' %}

```

När vi kallar på `{% include ... %}` letar Jinja2 automatiskt i mappen templates/. Vi kan på detta sättet separera koden och inkludera formulär, tabeller och övrig html-kod. För att få en snygg layout använder vi Bootstrap's färdiga klasser. Klassen `row` gör sitt bästa för att innehållet ska hamna på en rad. Klassen `col-md-3` tar upp 3 kolumner av 12. Klassen `col-md-offset-1` puttar elementet 1 kolumn åt höger.

Sista steget blir att importera Handler i app.py och skicka med alla Employee objekt till `render_template()`.

```python
# app.py
...

@app.route("/")
def main():
    """ Main route """
    return render_template("index.html", people=handler.get_people())

...
```

Kolla att det fungerar, starta servern och gå till `http://localhost:5000` i webbläsaren.

[FIGURE src=/image/oopython/kmom02/show_employees.png caption="Visa alla anställda."]



Lägg till nya anställda {#add}
-------------------------------

Nästa steg är att kunna lägga till fler anställda. Vi gör det med ett formulär som skickar ett POST request. Börja med att lägga till ett menyval i navbaren för `company.html` i `header.html`, samt en route som returnerar i app.py som returnerar rätt sida.

```python
# app.py
...

@app.route("/company")
def company():
    """ Company route """

    return render_template("company.html")

...
```

Vi går vidare med att lägga till kod i company.html.



###company.html {#company.html}

Vi bygger upp company.html påliknande sätt som index.html. Vi skapar en egen mall för formuläret och bara importera det i company.html. Då blir index.html och company.html väldigt lika varandra.

```html
{% include 'header.html' %}
<div class="container">
    <div class="page-header">
        <h1>Lägg till anställda</h1>
    </div>
    <div class="row">
        <div class="col-md-3 col-md-offset-1">
            <h3>Add employee</h3>
            {% include 'forms/add_employee.html' %}
        </div>
    </div>
</div>
{% include 'footer.html' %}
```



###templates/forms {#templates-forms}

Mallen för formuläret, templates/forms/add_employee.html, ser ut på följande sätt:

```html
<form role="form" method="POST" action="{{ url_for('company') }}">
    <div class="form-group">
        <label for="firstname">First name: </label>
        <input type="text" name="firstname" class="form-control" />
    </div>
    <div class="form-group">
        <label for="lastname">Last name: </label>
        <input type="text" name="lastname" class="form-control" />
    </div>
    <div class="form-group">
        <label for="salary">Salary: </label>
        <input type="text" name="salary" class="form-control" />
    </div>
    <button type="submit" class="btn btn-default">Lägg till</button>
</form>
```

Vi sätter metoden till POST och action till den sökvägen vi vill skicka formuläret när vi gör submit. Attributet `name` är även här namnet vi når formulärets data med när vi tar hand om det.



###app.py {#app-py}

Vi behöver modulen `request` så vi importerar den överst i filen:  
```
from flask import Flask, render_template, request
```
Nu återstår bara att hantera det inskickade formuläret. Det kan vi göra i routen för company.html:

```python
@app.route("/company", methods=["POST", "GET"])
def company():
    """ Company route """

    if request.method == "POST":
        handler.add_employee(request.form)

    return render_template("company.html", people=handler.get_people())
```

Här talar vi om att det är helt i sin ordning att ta sig hit via både POST och GET. Med modulen `request` kan vi se hur användaren har tagit sig in i routen med `request.method`. Om requesten är GET behöver vi inte göra något, då ska bara sidan renderas. Om det däremot är POST betyder det att det är formuläret som skickats och det behöver vi ta hand om. Här ser vi att routen använder filen *handler*. Den importeras högst upp i app.py och tanken är att den ska vara en form av controller, eller hanterare, mellan klassen och app.py. Sist så skickar vi med listan till company.html och låter tabellen ta hand om den för utskrift.

###handler.py {#handler-py}

Handler klassen ska vara bryggan mellan app.py och Employee objekten. Vi börjar med en lista som innehåller alla skapade objekt och en metod som skapar några hårdkodade Employee objekt. 

```python
#!/usr/bin/env python3
"""
Handler file
"""

from employee import Employee

class Handler():
    def __init__(self):
        self.people = []
        self.add_predefined_employees()

    def add_employee(self, form):
        self.people.append(
            Employee(
                form["firstname"],
                form["lastname"],
                form["salary"]
        ))

    def get_people(self):
        return self.people

    def add_predefined_employees(self):
        emil = Employee("Pelle", "Scriptsson", 30000)
        mikael = Employee("Mikael", "Roos", 31000)
        kenneth = Employee("Kenneth", "Lewenhagen", 75000)
        andreas = Employee("Andreas", "Arnesson", 12000)

        self.people.append(emil)
        self.people.append(mikael)
        self.people.append(kenneth)
        self.people.append(andreas)
```



Avslutningsvis {#avslutning}
------------------------------

Det var det hela. Smidigt och strukturerat. Prova gärna att lägga till fler personer i tabellen.
