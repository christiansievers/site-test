---
layout: digi-kunst-docs
title: Infrastruktur
order: 3.3
---

Digi-Kunst.nrw hat gleich mehrere [zentrale Ziele]({{ site.baseurl }}). Damit diese teils sehr vielfätigen Aufgaben zusammen gelingen können, durchlaufen die Informationen und Dateien, die an den Hochschulen vorliegen, gleich eine ganze Reihe von Stationen, bis sie zur Langzeiterhaltung und für die künstlerische, wissenschaftliche wie öffentliche Nutzung aufbereitet sind.

----

## Strukturdiagramm

Dieses Strukturdiagramm veranschaulicht den logischen Aufbau der derzeitigen Projektinfrastruktur und zeigt die Zusammenhänge von Systemkomponenten, Nutzer:innen, angebundenen Diensten und externen Institutionen.

[![Digi-Kunst-Organigramm Stand Mai 2024]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png 'Das Strukturdiagramm veranschaulicht den logischen Aufbau der intendierten Projektinfrastruktur')]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png)

[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2023-08-04_Strukturdiagramm.pdf]({{site.baseurl }}/assets/documents/2023-08-04_Strukturdiagramm.pdf) (50 KB)

In den folgenden Abschnitten werden die zentralen Einheiten dieses Modells kurz erklärt und ihre zentralen Funktionsweisen beschrieben.

----

## Erfassungs-Backend

Im Erfassungs-Backend können neue [Projekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#zentrale-entitäten-projekt-und-ereignis) angelegt sowie bereits bestehende Projekte verwaltet werden. Das Erfassungs-Backend steht allen einliefernden Personen zur Verfügung. Das sind, neben der [Projektleitung]({{ site.baseurl }}/projektstruktur/team.html#gesamtprojektleitung) und [Mediendokumentar:innen]({{ site.baseurl }}/projektstruktur/team.html#mediendokumentarinnen), zunächst ausgewählte Personen an den Hochschulen. In Zukunft soll dieses Backend aber, via [Shibboleth](https://www.shibboleth.net/), auch für Lehrende und Student:innen zugänglich sein.

----

## Admin-Backend

Das Admin-Backend umfasst die Verwaltung bestimmter kontrollierter Vokabulare und Taxonomien sowie die Verwaltung von zuweisbaren Rechte- und Lizenzangaben, die auf Projekte und [Digitale Objekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#ereignis-digitale-objekte) im Erfassungs-Backend angewendet werden können. Zudem können vom Admin-Portal aus alle zentralen Arbeitsschritte zur Überführung in die Langzeitverfügbarkeit geplant und durchgeführt werden. Der Zugriff auf das Admin-Backend ist, je nachdem, was dort verwaltet werden muss, auf die Projektleitung und/oder die Mediendokumentar:innen beschränkt.

----

## Staging-Speicher

Die hochgeladenen Dateien werden dann zunächst auf einem Staging-Speicher gespeichert. Dabei wird darauf geachtet, dass die Dateien auch vollständig hochgeladen wurden. Dort angekommen, werden die Dateien mit einer Prüfsumme versehen, sodass spätere Änderungen an ihnen nachvollziehbar sind. Ebenso werden eine Reihe technsicher Informationen aus ihnen ausgelesen. Die ausgelesen Daten werden dann gemeinsam mit den im Erfassungs-Backend eingegebenen Dateien in einer [relationalen Datenbank](https://www.ibm.com/de-de/topics/relational-databases) gespeichert. Damit einzelne Datensätze in- und außerhalb von Digi-Kunst.nrw identifizierbar sind, werden sie mit [Handles](https://www.handle.net/) versehen. Es ist vorgesehen, auch noch weitere digitale Identifikatoren vergeben zu können, zum Beispiel [DOIs](https://www.doi.org/). Sind alle Dateien und Informationen vollständig vorhanden, kann ein Paket erzeugt werden, das für die Langzeitverfügbarkeit geeignet ist. Dieses Paket wird dann an das Web- und Arbeitsrepositorium weitergeleitet.

----

## Arbeits- und Webrepositorium & KA3

Das Arbeits- und Webrepositorium ist der zentrale Knotenpunkt, an dem alle Daten und Dateien, die bei Digi-Kunst.nrw erfasst werden, zusammenlaufen und von dem sie aus auch wieder weiterverarbeitet werden können. Damit dieser Workload gestemmt und gesteuert werden kann, benutzt Digi-Kunst.nrw das von Christoph Stollwerk speziell für die Archivierung von audio-visuellen Kulturarchivalien entwickelte Repositoriumssystem [KA3](https://ka3.uni-koeln.de/). KA3 ermöglicht es, dass diese Daten nicht nur für einen Zweck, sondern vielfältig und austauschfähig verwendet werden können. So ist dieses Repositorium zum einen Quelle für die öffentliche Webseite, zum anderen bietet es eine Schnittstelle zu den Strukturen der Langzeitverfügbarkeit im [Hochschulbibliothekszentrum](https://www.hbz-nrw.de/).

----

## Speicher der Langzeitverfügbarkeit NRW

Das erstellte Daten-Paket enthält alle nötigen Informationen, die zur Langzeiterhaltung der Dateien benötigt werden. Entsprechend kann es von KA3 and den Speicher der [Landesinitiative Langzeitverfügbarkeit](https://www.lzv.nrw/) gesendet werden. Digi-Kunst.nrw ist in dieser Funktion also ein sogenannter „SIP-Produzent“ für die Hochschulen, wenn man das Portal in den Lanzeitarchivierungsprozess nach dem Referenzmodell [OAIS](https://www.forschungsdaten.org/index.php/OAI) einordnen möchte. Die LZV sichert dann die digitalen Originale (sogenannte „Preservation Master-Dateien“). Das funktioniert sogar bei Dateien, die beispielsweise verschlüsselt, beschädigt, oder keinem Dateiformat mehr zuzuordnen sind. Hier wird dann der Bitstream aus Nullen und Einsen gespeichert. Zu den Dateien werden aber in jedem Fall ebenfalls die dazugehörigen Metadaten archiviert.

----

## Rosetta-Backend

Über das [Rosetta-Backend](https://www.lzv.nrw/ueber-lzv/wie-funktioniert-lzv), welches von der Landesinitiative Langzeitverfügbarkeit bereitgestellt wird, kann die Hochschule die Erhaltungsmaßnahmen ihrer digitalen Daten planen und durchführen. Bei Bedarf können die dort eingelieferten Daten auch wieder exportiert werden. Es gilt aber hierbei die Regelungen unserer Partnerinstitution zu beachten.
 
----

## Dissimination-Frontend

Das Dissimination-Frontend ist unsere öffentliche Webseite. Von hier aus können die Meta- und Mediendaten von Digi-Kunst.nrw durchsucht und angesehen werden. Nicht jedem/jeder Urser:in stehen dabei allerdings alle Mediendaten zur Verfügung. Manche sind erst nach einem Log-In mit [Shibboleth](https://www.shibboleth.net/) und/oder nach vorheriger Anfrage einsehbar. Die Metadaten sind jedoch (sofern möglich) frei verfügbar und können gleich in mehreren Formaten heruntergeladen und weiterverwendet werden. Auch können die Datensätze sicher über die angelegten Identifier zitiert werden. Zudem ist immer ersichtlich, wann der Datensatz zuletzt geändert wurde, sodass auch der/die Endnutzer:in stets einen Überblick über alle gesicherten Versionen hat.
