---
layout: digi-kunst-docs
title: Einführung in das Datenmodell
order: 2.1
---

Das Datenmodell definiert, wie die heterogenen Rohinformationen der unterschiedlichen Einliefernden in ein logisches Verhältnis gebracht und integriert werden, und in welchen Entitäten (Tabellen) und Attributen (Feldern) die Metadaten erfasst und verfügbar gemacht werden. Zusätzlich umfasst es Wertelisten und Taxonomien, die den Kern des kontrollierten Vokabulars bilden.

## Die wichtigsten Entitäten

| **Projekt**  | Im Zentrum steht das Projekt, meistens ein künstlerisches Werk. Es sind aber auch z. B. Aufzeichnungen von Veranstaltungen erfassbar. Das Projekt hat einen oder mehrere Titel, es lässt sich kategorisieren und inhaltlich beschreiben. |
| **Ereignis** | Die wichtigste Entität nach dem Projekt sind die Ereignisse. Hier führen wir die meisten mit dem Projekt verbundenen Informationen zusammen. Ereignisse sind gekennzeichnet durch einen Zeitraum und ggf. einen Ort. Hier findet sich eine Liste der verschiedenen Ereignistypen, die bei der Erfassung benutzt werden können. [TODO Link setzen]|
| **Akteur:innen** | Personen werden in der Entität Akteur:innen erfasst. In Ereignissen haben Akteur:innen eine oder mehrere *Rollen*. [TODO Link setzen]|
|**Digitales Objekt** | Digitale Objekte (Dateien) werden über Ereignisse verzeichnet. Sie sind entweder durch Retrodigitalisierung aus physischen Medien entstanden, oder sie sind born digital. Sie können inhaltlich beschrieben und typisiert werden, und eine Vielzahl von technischen Metadaten wird automatisch ausgelesen, die sich je nach Datei- und Medientyp stark unterscheiden können. |
| **Weitere Entitäten** | Weitere optionale Entitäten sind u.a. *physisches Objekt*, verwendetes *Equipment und Software* und *Informationsträger* – siehe Diagramm. |


Dieses Diagramm zeigt in vereinfachter Form, wie sich die Entitäten und Attribute zueinander verhalten:

[![vereinfachtes Diagramm zum Datenmodell]({{ site.baseurl }}/assets/images/2024-04-24_datenmodellierung_vereinfacht.png 'vereinfachtes Diagramm zum Datenmodell')]({{ site.baseurl }}/assets/images/2024-04-24_datenmodellierung_vereinfacht.png)

[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2024-04-24_datenmodellierung_vereinfacht.pdf]({{ site.baseurl}}/assets/documents/2024-04-24_datenmodellierung_vereinfacht.pdf) (20,3 KB)  

----

## Die Grundlagen des Datenmodells im Video
<video width="100%" controls>
    <source src="{{ site.baseurl}}/assets/documents/2024-04_datenmodellierung_1_grundlagen.mp4" type="video/mp4">
</video>

----

## Beispielhafte Verzeichnung eines einfachen Projekts

<video width="100%" controls>
    <source src="{{ site.baseurl}}/assets/documents/2024-04_datenmodellierung_2_einfaches_beispiel.mp4" type="video/mp4">
</video>


