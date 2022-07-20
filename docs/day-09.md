# Tag 9

## Suche als Webanwendung programmieren


### Web-Framework (Web Application Framework)

Ein Web-Framework ist für die Unterstützung der Entwicklung von Anwendungen für das World Wide Web (WWW) ausgelegt. 
Dabei wird mehrfach benutzter Programmcode wiederverwendet, wodurch eine schnelle Entwicklung von dynamischen Webseiten, 
Webservices oder Webanwendungen unterstützt wird. 

Natürlich kann man jede Form von Webanwendungen von Grund auf neu programmieren. 
Dies ist hinsichtlich der damit verbundenen wiederholten Aufwendung und der sich daraus ergebenden Risiken nicht sinnvoll. 

Dahingehend bietet sich die Nutzung eines Frameworks an:
- Dieses stellt Dienste wie Datenbankverbindungen, Seitentemplates (z.B. automatisch generierte Admin-Oberflächen), 
Caching-Verfahren oder Internationalisierung als fertige Module zur Verfügung, 
die dem jeweiligen Anwendungsfall entsprechend eingesetzt werden können.
- Ein weiterer Vorteil ist die Generierung sauberer Quelltexte, 
hierbei wird besonderer Wert gelegt auf die Trennung von Präsentation, 
Logik und Inhalt nach dem Prinzip des Model-View-Controller(MVC). 
- Weitere typische Prinzipien für die Entwicklung mit Frameworks sind "Dont´t Repeat Yourself" (DRY), 
Rapid Application Development (RAD) und Keep It Small and Simple (KISS).


### Vielfalt der Web-Frameworks

Es gibt sehr viele Web-Frameworks. Jedes Web-Framework hat seine Stärke und Schwäche.

- [Liste von Web-Frameworks](https://de.wikipedia.org/wiki/Liste_von_Webframeworks)

Lese den folgenden Artikel.

- [10 Best Web-Frameworks](https://hackr.io/blog/web-development-frameworks)

In Java Welt ist "Spring" bzw. "Spring boot" das meist verwendete Web-Framework. 
In Python Welt werden "Django" oder "Flask" häufig benutzt.


### Flask

Wir möchten Flask für unser Projekt nutzen. Flask ist ein leichtgewichtiges Python-Web-Framework. 
Es wurde entwickelt, um den Einstieg schnell und einfach zu machen, mit der Fähigkeit, komplexe Anwendungen zu skalieren.

Man kann eine einfache Hello-World-App mit wenigen Zeilen erstellen.

- [Link zu Flask Webseite](https://palletsprojects.com/p/flask/)

Hier ist ein Tutorial für Flask. Hier wird ein Blog erstellt.
Schau dir die folgenden Videos an und programmiere es mit.

- [Flask Tutorial Part 1](https://www.youtube.com/watch?v=MwZwr5Tvyxo)
- [Flask Tutorial Part 2](https://www.youtube.com/watch?v=QnDWIZuWYW0)


### HTMX

Für eine dynamische Webseite braucht man sehr viel javascript-Codes zu schreiben.
Es gibt Tools, die uns diese Arbeit erleichtern.
"htmx" ist ein solches Tool, das man schnell erlernen kann.

- [Link zu htmx Webseite](https://htmx.org/)

### Ein einfaches Beispiel mit htmx

Erstelle eine html Datei namens "index.html" und kopiere den folgenden Inhalt.

```html
<html lang="en">

<head>
    <script src="https://unpkg.com/htmx.org@1.8.0" integrity="sha384-cZuAZ+ZbwkNRnrKi05G/fjBX+azI9DNOkNYysZ0I/X5ZFgsmMiBXgDZof30F5ofc" crossorigin="anonymous"></script>    
</head>

<body>

    <button hx-get="clicked.html"
        hx-trigger="click"
        hx-target="#click-result"
        hx-swap="outerHTML">Klick mich!
    </button>

    <div id="click-result">
    </div>

</body>

</html>
```

Erstelle eine andere html Datei namens "clicked.html" und kopiere den folgenden Inhalt.

```html
Du hast mich geklickt!
```

Für unser Projekt brauchen wir "Active Search" Funktion von htmx.

- [Active Search in htmx](https://htmx.org/examples/active-search/)

### Packen wir alles zusammen

Nutze "Flask" und "htmx", um eine einfache Suche zu implementieren.

- In Flask brauchst du zwei Routen
  - "/": Web-Seite mit einem Suchfeld. Beim Tippen wird eine Post-Anfrage an "/search" geschickt 
  - "/search": Diese Route empfängt eine Postanfrage mit dem Suchbegriff und gibt das Suchergebnis in Elasticsearch zurück
- In der html-Datei unter der Route "/" solltest du ein Suchfeld mithilfe von "htmx - active search" implementieren 