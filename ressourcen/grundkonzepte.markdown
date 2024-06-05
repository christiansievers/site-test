---
layout: digi-kunst-docs
title: Grundkonzepte
order: 2.1
---

Hier finden Sie einen Überblick über die Grundkonzepte von Digi-Kunst.nrw.

----

## Das Datenmodell von Digi-Kunst.nrw

Das Datenmodell definiert, wie die heterogenen Rohinformationen der unterschiedlichen Einliefernden in ein logisches Verhältnis gebracht und integriert werden, und in welchen Entitäten (Tabellen) und Attributen (Feldern) die einzelnen Metadaten erfasst und verfügbar gemacht werden. Dieses Diagramm zeigt in vereinfachter Form, wie sich die Entitäten (Tabellen) und Attribute (Felder) zueinander verhalten:

[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2024-04-24_datenmodellierung_vereinfacht.pdf]({{ site.baseurl}}/assets/documents/2024-04-24_datenmodellierung_vereinfacht.pdf) (20,3 KB)  

| **Projekt**  | Im Zentrum steht das Projekt, meistens ein künstlerisches Werk. Es sind aber auch z. B. Aufzeichnungen von Veranstaltungen erfassbar. Das Projekt hat einen oder mehrere Titel, es lässt sich kategorisieren und inhaltlich beschreiben. |
| **Organisationseinheit** | Projekte entstehen üblicherweise aus dem Zusammenhang eines Studiengangs oder einer Hochschuleinrichtung. Diese erfassen wir in der Entität Organisationseinheit |
| **Ereignis** | Die wichtigste Entität nach dem Projekt sind die Ereignisse. Hier führen wir die meisten mit dem Projekt verbundenen Informationen zusammen. Ereignisse sind gekennzeichnet durch einen Zeitraum und ggf. einen Ort. Hier findet sich eine Liste der verschiedenen Ereignistypen, die bei der Erfassung benutzt werden können.|
| **Akteur:innen** | Personen werden in der Entität Akteur:innen erfasst. In Ereignissen haben Akteur:innen eine oder mehrere *Rollen*. |
|**Digitlales Objekt** | Dateien oder Digitale Objekte sind an Ereignisse angeschlossen. Sie sind entweder durch Retrodigitalisierung aus physischen Medien entstanden, oder sie sind born digital. Sie können inhaltlich beschrieben und typisiert werden, und eine Vielzahl von technischen Metadaten, die sich je nach Datei- und Medientyp stark unterscheiden können, wird automatisch ausgelesen. |
| **Lizenz** | Digitalen Objekten kann eine Lizenz zur Veröffentlichung zugewiesen werden. Es ist möglich, auf Wunsch alle oder nur einzelne digitale Objekte eines Projekts (bzw. eines Ereignisses) zu veröffentlichen. Nicht veröffentlichte digitale Objekte bleiben für die Öffentlichkeit unzugänglich und werden nur in die Langzeitverfügbarkeit-Sicherung des hbz gegeben. |
| **Weitere Entitäten** | Weitere optionale Entitäten sind *physisches Objekt*, verwendetes *Equipment und Software* und *Informationsträger* – siehe Diagramm. |

Eine detailiertere Einführung in das Datenmodell finden sie [hier]({{ site.baseurl}}/dokumentation/datenmodell).

----

## Videos zum Datenmodell

### 1: Die Grundlagen

<video width="100%" controls>
    <source src="{{ site.baseurl}}/assets/documents/2024-04_datenmodellierung_1_grundlagen.mp4" type="video/mp4">
</video>

### 2: Verzeichnung eines einfachen Projekts

<video width="100%" controls>
    <source src="{{ site.baseurl}}/assets/documents/2024-04_datenmodellierung_2_einfaches_beispiel.mp4" type="video/mp4">
</video>

----

## Standards

Durch die Verwendung öffentlicher Systematiken, Vokabulare und Normdaten gewährleisten wir die Anschlussfähigkeit von Semantic Web- und Linked Open Data Anwendungen. 

Die in Digi-Kunst.nrw erfassten Informationen werden, wie im Bericht des Vorprojekts erwähnt, in Metadatenaustauschformaten wie LIDO und MARC21 abgerufen werden können. Große Portale wie die [Deutsche Digitale Bibliothek (DDB)](https://www.deutsche-digitale-bibliothek.de/) und [Europeana](https://www.europeana.eu/) können sie harvesten und aggregieren und damit damit die Archivalien der Hochschulen in ihren Suchmasken durchsuch- und auffindbar machen.

Digi-Kunst.nrw arbeitet nach den FAIR-Prinzipien, d.h. alle veröffentlichen Metadaten sind durchsuchbar, zugänglich, interoperabel, wiederverwendbar (findable, accessible, interoperable, reusable).

Durch die Nutzung von Rosetta als Langzeitverfügbarkeits-Lösung gewährleisten wir die Konformität mit dem OAIS-Standard-Referenzmodell für digitale Langzeitarchive.

---- 

## Weiterführende Lektüre zur Langzeitverfügbarkeit

  * Nicht alle Dateitypen sind langzeitstabil. Hier findet sich eine Übersicht der LZV.nrw-Initiative zu [gängigen Dateiformaten und deren Langzeitstabilität](https://www.lzv.nrw/dateiformate/). Die orangefarbene Schaltfläche blendet alle nicht-langzeitstabilen Dateiformate aus. 
  * Die (englischsprachige) NDSA [Levels of Digital Preservation Matrix](https://osf.io/3na96) gibt weiterführende Informationen zu den [hier aufgeführten]() grundlegenden Schritten zum Sichern digitaler Inhalte.
  * [nestor](https://www.langzeitarchivierung.de/Webs/nestor/DE/Publikationen/publikationen_node.html) bündelt deutschlandweit Wissen zum Thema Langzeitverfügbarkeit und veröffentlicht auf ihrer Webseite Ratgeber und Hinweise.
  * Weitere sehr gute und umfangreiche (englischsprachige) Ressourcen sind [Implement digital preservation](https://www.dpconline.org/digipres/implement-digipres) und
  * [Novice to Know-How: Online Digital Preservation Training](https://www.dpconline.org/digipres/prof-development/n2kh-online-training) der Digital Preservation Coalition.

