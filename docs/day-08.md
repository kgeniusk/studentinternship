# Tag 8

## Speichern der Anleitungen in Elasticsearch


### Index

Lasst uns einen Elasticsearch-Index erstellen. Bestimme einen Namen, den die zu speichernden Daten gut repräsentieren.

```
PUT ...
```

### Analyzer

Der Elasticsearch-Analyzer zerlegt den Text in Token. Führe den folgenden Befehle aus und vergleiche die Ergebnisse.

with default analyser
```
GET _analyze?pretty
{
  "text": "Anpassung der Bearbeitungsmasken im Lead-Prozess",
}
```

with german analyser
```
GET _analyze?pretty
{
  "text": "Anpassung der Bearbeitungsmasken im Lead-Prozess",
  "analyzer": "german"
}
```

### Mapping

Lasst uns nun unserem Index ein Mapping hinzufügen. Ein Mapping ist wie ein Schema in MySQL. Es definiert die Felder, die das Dokument unterstützt. Wir definieren jedes Feld in einem Elasticsearch-Mapping mit einem Namen und einem Typ.

Elasticsearch definiert zwei verschiedene String-Datentypen: 

- text: die Werte werden für die Volltextsuche indiziert
- keyword: die Werte werden nur für exakte Übereinstimmungen verwenden

#### Welche Felder brauchen wir?

Denke darüber nach, welche Felder wir für das Speichern der Anleitungen brauchen.

Beispiel:
- heading 1
- heading 2
- heading 3
- Content
- Link

Nun füge ein Mapping in den index hinzu.

```
PUT index_name/...
{
  "...": {
    "heading1": {
      "type": "text",
      "analyzer": "german"
    },
    "heading2": {
      "type": "text",
      "analyzer": "german"
    },
    "content": {
      "type": "text",
      "analyzer": "german"
    },
    ...
  }
}
```

Prüfe, ob das Mapping richtig hinzugefügt ist.

```
GET index_name/...
```


### Document

Nun können wir die Anleitungen in Elasticsearch speichern.

```
POST index_name/...
{
    "heading1": "title",
    "heading2": "subtitle",
    ...
}
```

Zeige Anzahl der Dokumente.

```
GET mydocs/...
```

Zeige alle Daten, die du gespeichert hast.

```
GET mydocs/...
{
  "query": {
    "...": {}
  }
}
```

### Volltextsuche

Wie sieht eine Query aus, die einen bestimmten Begriff in allen Feldern sucht?

```
GET index_name/...
{
  "query": {
    "...": {
      "...": [
        {
          "match": {
            "heading1": "search_keyword"
          }
        },
        {
          "match": {
            "heading2": "search_keyword"
          }
        }
      ]
    }
  }
}
```

## Ausführen von Querys in Python

### Vorbereitung

```powershell
# im Verzeichnis workspace
mkdir elastic_client
cd elastic_client
python -m venv venv
venv\scripts\activate
pip install elasticsearch
```

### Programm

Erstelle eine neue Datei namens "main.py" und Kopiere den folgenden Code.

```python
from datetime import datetime
from elasticsearch import Elasticsearch
from config import CERT_FINGERPRINT, ELASTIC_PASSWORD, ELASTIC_USER, ELASTIC_HOST

es = Elasticsearch(
    hosts=ELASTIC_HOST,
    ssl_assert_fingerprint=CERT_FINGERPRINT,
    basic_auth=(ELASTIC_USER, ELASTIC_PASSWORD),
)

index_name = "test-index"

resp = es.indices.put_mapping(index=index_name, properties={
    "author": {
        "type": "text"
    },
    "text": {
        "type": "text"
    }
})
print(resp)

doc = {
    'author': 'kimchy',
    'author': 'Elasticsearch: cool. bonsai cool.',
    'timestamp': datetime.now(),
}

resp = es.index(index=index_name, id=1, document=doc)
print(resp['result'])

resp = es.get(index=index_name, id=1)
print(resp['_source'])

es.indices.refresh(index=index_name)

resp = es.search(index=index_name, query={"match_all": {}})
print("Got %d Hits:" % resp['hits']['total']['value'])
for hit in resp['hits']['hits']:
    print("%(timestamp)s %(author)s: %(text)s" % hit["_source"])
```

Erstelle eine andere Datei namens "config.py". Inhalt für die "config.py" hast du schon über Teams bekommen.

```python
ELASTIC_HOST = ''
ELASTIC_USER = ''
ELASTIC_PASSWORD = ''
CERT_FINGERPRINT = ''
```

Führe das Programm aus.

```powershell
python main.py
```

## Ausführen von Querys in Java

Wenn du noch Zeit hast, versuche es auch in Java.
