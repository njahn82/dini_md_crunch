# Harvesting von OAI-Metadaten mit Catmandu

## Was ist Catmandu?

Catmandu - the data processing toolkit

"Catmandu is a command line tool to access and convert data 
from your digital library, research services or any other open data sets."

Siehe http://librecat.org/ für mehr Infos.

## Grundbegriffe OAI-Abfragen mit Catmandu

### Zeige Information zum Repository: `identify`

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --identify 1 to YAML
```

### Zeige vorhanden Formate: `listMetadataFormats`
```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --listMetadataFormats 1 to YAML
```

### Zeige Identifier: `listIdentifiers`

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --listIdentifiers 1 to YAML
```

### Zeige vorhandene Sets: `listSets`

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --listSets 1 to YAML
```

### Harvesting von Daten: `listRecords`

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai to YAML
```

*Achtung: Dieser Befehl harvestet alle Records des Repositories! Dies kann einige Minuten in Anspruch nehmen (ca. 6 min. bei PUB).*

a. In anderen Formaten

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --metadataPrefix rdf --handler raw to YAML
```

b. Einen einzigen Datensatz

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --getRecord 1 --identifier oai:pub.uni-bielefeld.de:1634091 to YAML
```

c. Aktuelle Open-Access-Publikationen

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai     
  --listRecords 1 \
  --set open_access --from 2018-10-01 to YAML \
  --fix "reject any_match(_status, deleted)" to YAML
```

## Datenanalyse

### Gesamtübersicht über die Werteverteilung

Zuerst werden die Daten in ein `Breaker`-Format, transformiert:  
```bash
$ catmandu convert YAML to Breaker <data/openaccess.yml >data/openaccess.breaker
```

Danach kommt die statistische Analyse:

```bash
$ catmandu breaker daten/openaccess.breaker
```

### Analyse einzelner Felder

a. Werte von `dc:rights`

```bash
$ catmandu convert YAML to CSV \
  --fix "move(rights.0, r); retain(r)" \
  < data/all.yml | sort | uniq
```

b. Werte von `dc:language`

```bash
$ catmandu convert YAML to CSV \
  --fix "move(language.0, l); retain(l)" \
  < data/all.yml | sort | uniq
```

## Weiterführende Informationen

- http://journal.code4lib.org/articles/7818

- [Catmandu Cheatsheet](http://librecat.org/assets/catmandu_cheat_sheet.pdf)

