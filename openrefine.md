Was ist OpenRefine?
===================

* „powerful tool for working with messy data": Bereinigung, (Format-)Transformation & Aggregation von Daten
* Source code & kollaborative Entwicklung via [GitHub](https://github.com/OpenRefine/OpenRefine) ([BSD-3-Clause-Lizenz](http://opensource.org/licenses/BSD-3-Clause))
* Aktuelle Version 3.1 ([Download](http://openrefine.org/download.html) für Windows, Mac OS, Linux)
* primär GUI-gestützt; diverse [Client libraries](https://github.com/OpenRefine/OpenRefine/wiki/Documentation-For-Developers#known-client-libraries-for-refine) zur Automatisierung von OpenRefine-Transformationen (z.B. Python, R, ruby)
* Kein Webservice! Desktop-Anwendung (Java-basiert): Bearbeitung im Browser (Aufruf via <http://127.0.0.1:3333/> oder <http://localhost:3333/>); Daten & Bearbeitungshistorie werden lokal gespeichert


Was kann OpenRefine?
====================

* Datenexploration: Filter & Facetten (verschiedene Datentypen), Clustering, Dubletten
* Transformation: auf Ebenen Zellen, Zeilen oder Spalten; Standardfunktionen (Zellen aufteilen oder verketten, Leerzeichen entfernen, Datentyp ändern, Groß-/Kleinschreibung ändern, ...); Mini-Skripte mit Google Refine Expression Language (GREL), Python/Jython oder Clojure
* History: Undo auch für ausgewählte (frühere) Schritte; kann exportiert werden, um gleiche Operationen auf andere Datensets anzuwenden
* Aggregation: mit Daten aus anderen OR-Projekten; Webschnittstellen abfragen + Daten parsen (JSON, XML, HTML); Reconciliation Services (z.B. Wikidata, GND via LOBID, VIAF) bzw. [Extensions](http://openrefine.org/download.html) (z.B. GoKB)
* Import: TSV, CSV, *SV, XLS(X), JSON, XML, RDF as XML, Google Data documents; andere Formate via OpenRefine Extensions
* Export: Standardformate (CSV, TSV, XLS(X), HTML table, ...); Templating z.B. für XML


Was kann OpenRefine nicht?
==========================

* Manuelles Editieren von Zellen möglich aber mühselig
* Manuelles Hinzufügen neuer Zeilen
* Statistische Auswertung oder Plotten (Diagramme, Grafiken) -- aber bestens geeignet für Vorbereitung der Daten für weitere Verwendung in Excel (Pivot) oder R, Python o.Ä.
* Rechteverwaltung für verschiedene Nutzer\*innen, die an gleichem Projekt arbeiten
* Performance Probleme bei sehr großen Datensets


Wie kann ich mehr über OpenRefine lernen?
=========================================

* Online Tutorials: u.a. [OR-Webseite](http://openrefine.org/documentation.html), [Recipies](https://github.com/OpenRefine/OpenRefine/wiki/Recipes) bzw. [Liste externer Tutorials](https://github.com/OpenRefine/OpenRefine/wiki/External-Resources) im [OpenRefine GitHub Wiki](https://github.com/OpenRefine/OpenRefine/wiki)
* Tutorials Bibliotheken/Kultureinrichtungen: [Library Carpentry OpenRefine](https://librarycarpentry.org/lc-open-refine/), Artikelreihe bei [HistHub](https://histhub.ch/cat/net/blog/openrefine/)
* Einführung: Ruben Verborgh, Max De Wilde (2013) [Using OpenRefine](http://www.packtpub.com/openrefine-guide-for-data-analysis-and-linking-dataset-to-the-web/book), ISBN 9781783289080
* Zahlreiche allgemeine Einführungen und Lösungsansätze für bestimmte Aufgaben auf [YouTube](https://www.youtube.com/results?search_query=openefine)


Anwendungsbeispiele
===================

* LIBREAS.Library Ideas: [Workflow](https://github.com/libreas/libreas.github.io/wiki/prepare-and-submit-DOAJ-metadata) zur Nachnutzung von OAI-DC-Metadaten und deren Aufbereitung als XML für Import in DOAJ
* Hamburg Open Science "Schaufenster": [Automated workflow for harvesting, transforming and indexing of metadata using metha, OpenRefine and Solr](https://github.com/subhh/HOS-MetadataTransformations)
* Galvan, Angela (2016) [Gathering IR Seed Data with OpenRefine and SHERPA/RoMEO](https://asgalvan.com/2016/04/27/gathering-ir-seed-data-with-openrefine-and-sherparomeo/)
* Steeg, Fabian; Pohl, Adrian (2018): [GND reconciliation for OpenRefine](http://blog.lobid.org/2018/08/27/openrefine.html)
* Harlow, Christina (2015): [Data Munging Tools in Preparation for RDF: Catmandu and LODRefine](https://journal.code4lib.org/articles/11013), Code4Lib Journal \#30

Beispiel Libreas
===================

* Ziel: Nachnutzung von OAI-DC-Metadaten und deren Aufbereitung als XML für Import in DOAJ
* Anleitung [Workflow](https://github.com/libreas/libreas.github.io/wiki/prepare-and-submit-DOAJ-metadata) im Libreas-Wiki
*  [edoc Collection \#34](
* Vorgehen am Beispiel für [Ausgabe 34](http://libreas.eu/ausgabe34/inhalt/):
  - edoc-Collection für Ausgabe aufrufen <https://edoc.hu-berlin.de/handle/18452/20305>
  - ListIdentifiers <https://edoc.hu-berlin.de/oai/request/?verb=ListIdentifiers&metadataPrefix=rdf&set=col_18452_20305> [view source](view-source:https://edoc.hu-berlin.de/oai/request/?verb=ListIdentifiers&metadataPrefix=rdf&set=col_18452_20305) - XML kopieren
  - neues Projekt in OpenRefine (via Clipboard) - XML einfügen - in Vorschau Bereich `<ListIdentifiers>` auswählen
  - Skript einlesen: via `Undo/Redo` [json für Bearbeitungsschritte 1.2–3.6](/openrefine-libreas/libreasworkflow_1.2-3.7.json) einfügen
  - (manuelle Nacharbeiten Schritt 3.8)
  - in Refine-Projekt: `Export` -> `Templating`
* [finale XML-Datei](/openrefine-libreas/libreas34_doaj.xml) für Import DOAJ