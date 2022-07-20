# Tag 10

## Suchebegriff hervorheben

Es gibt zwei Möglichkeiten:

1. Das aktuelle Ergebnis direkt bearbeiten und Suchbegriff mit einem html tag umklammern
2. Elasticsearch highlighting funktion nutzen

### Elasticsearch Highlighting

[Elasticsearch Highlighting](https://www.elastic.co/guide/en/elasticsearch/reference/current/highlighting.html)

### Lade die Änderung von Github herunter

```powershell
# in deinem "search"-Verzeichnis
git pull git@github.com:kgeniusk/esclient.git
```

Das geänderte Programm nutzt "highlight" data anstatt "_source" data.
Dies verursacht ein Problem. Wie können wir es lösen?

## Sortierung der Suchergebnisse

Sortiere die Suchergebnisse nach "score"

## Verbesserungen

Denke darüber nach, welche Verbesserungen wir für unser Suchprogramm vornehmen kann.