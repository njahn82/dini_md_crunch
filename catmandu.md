# Harvesting von Metadaten

## Tools

## Use cases

### Alle Daten des Repositories

```bash
$ catmandu convert OAI --.....\
  to YAML >uni-bi.ym
```

#### Harvest records
$ catmandu convert OAI --url http://myrepo.org/oai
$ catmandu convert OAI --url http://myrepo.org/oai --metadataPrefix didl --handler raw

#### Harvest repository description
$ catmandu convert OAI --url http://myrepo.org/oai --identify 1

#### Harvest identifiers
$ catmandu convert OAI --url http://myrepo.org/oai --listIdentifiers 1

#### Harvest sets
$ catmandu convert OAI --url http://myrepo.org/oai --listSets 1

#### Harvest metadataFormats
$ catmandu convert OAI --url http://myrepo.org/oai --listMetadataFormats 1

#### Harvest one record
$ catmandu convert OAI --url http://myrepo.org/oai --getRecord 1 --identifier oai:myrepo:1234



#### Harvesting von aktuellen Open-Access-Publikationen

```bash
$ catmandu convert OAI --url https://pub.uni-bielefeld.de/oai --listRecords 1 \
  --set open_access --from 2018-10-01 to YAML \
  --fix "reject any_match(_status, deleted)" >data/openaccess.yml
```


```bash

```

```bash
```

```bash
```

```bash
```



## Weitere Infos

- http://journal.code4lib.org/articles/7818

- [Catmandu Cheatsheet](http://librecat.org/assets/catmandu_cheat_sheet.pdf)

