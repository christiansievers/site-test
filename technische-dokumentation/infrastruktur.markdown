---
layout: digi-kunst-docs
title: Infrastruktur
order: 3.3
---

## Strukturdiagramm
Dieses Strukturdiagramm veranschaulicht den logischen Aufbau der derzeitigen Projektinfrastruktur und zeigt die Zusammenhänge von Systemkomponenten, Nutzer:innen, angebundenen Diensten und externen Institutionen.

[![Digi-Kunst-Organigramm Stand Mai 2024]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png 'Das Strukturdiagramm veranschaulicht den logischen Aufbau der intendierten Projektinfrastruktur')]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png)

[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2023-08-04_Strukturdiagramm.pdf]({{site.baseurl }}/assets/documents/2023-08-04_Strukturdiagramm.pdf) (50 KB)

In den folgenden Abschnitten werden die zentralen Einheiten dieses Modells kurz erklärt und zentrale Funktionsweise beschrieben.

----

## Erfassungs-Backend

Im Erfassungs-Backend kann man neue [Projekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#zentrale-entitäten-projekt-und-ereignis) angelegen sowie bereits bestehende Projekte verwalten. Das Erfassungs-Backend steht allen einliefernden Personen zur Verfügung. Das sind, neben der [Projektleitung]({{ site.baseurl }}/projektstruktur/team.html#gesamtprojektleitung) und unseren [Mediendokumentar:innen]({{ site.baseurl }}/projektstruktur/team.html#mediendokumentarinnen), zunächst ausgewählte Personen an den Hochschulen. In Zukunft soll dieses Backend aber, via [Shibboleth](https://www.shibboleth.net/), auch für Lehrende und Student:innen zugänglich sein.

----

## Admin-Backend

Das Admin-Backend umfasst die Verwaltung bestimmter kontrollierter Vokabulare und Taxonomien sowie die Verwaltung von zuweisbaren Rechte- und Lizenzangaben, die auf Projekte und [Digitale Objekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#ereignis-digitale-objekte) im Erfassungsbackend angewendet werden können. Außerdem können vom Admin-Portal aus alle zentralen Arbeitsschritte zur Überführung in die Langzeitverfügbarkeit geplant und durchgeführt werden. Der Zugriff auf das Admin-Backend ist, je nachdem, was dort verwaltet werden muss, auf die Projektleitung und/oder die Mediendokumentar:innen beschränkt.

----

## Staging-Speicher

Die eingegeben Daten und hochgeladenen Dateien werden dann zunächst auf einem Staging-Speicher gespeichert. Dabei wird darauf geachtet, dass die Dateien auch vollständig hochgeladen werden. Auf diesem Speicher angekommen, werden die Dateien mit einer Prüfsumme versehen, sodass spätere Änderungen an ihnen nachvollziehbar sind. Ebenso wird eine Reihe technsicher Informationen aus ihnen ausgelesen. Beides, die manuell eingegeben und die ausgelesen Daten, werden dann gemeinsam in einer [relationalen Datenbank](https://www.ibm.com/de-de/topics/relational-databases) gespeichert. Damit einzelne Datensätze in- und außerhalb von Digi-Kunst.nrw identifizierbar sind, werden sie mit [Handles](https://www.handle.net/) versehen. Es ist vorgesehen, auch noch weitere digitale Identifikatoren vergeben zu können, zum Beispiel [DOIs](https://www.doi.org/). Sind alle Dateien und Informationen vollständig vorhanden, kann ein Paket erzeugt werden, das für die Langzeitverfügbarkeit geeignet ist. Dieses Paket wird dann an das Arbeits- und Webrepositorium KA3 weitergeleitet.

----

## Arbeits- und Webrepositorium KA3

----

## Speicher der Langzeitverfügbarkeit NRW

Zur Langzeitverfügbarkeit wird das erstellte Paket an den Speicher der [Landesinitiative Langzeitverfügbarkeit](https://www.lzv.nrw/) gesendet, die ein Teil des [Hochschulbibliothekszentrum des Landes Nordrhein-Westfalen](https://www.hbz-nrw.de/) ist. Digi-Kunst.nrw ist damit ein sogenannter „SIP-Produzent“ im Lanzeitarchivierungsprozess nach dem Referenzmodell [OAIS](https://www.forschungsdaten.org/index.php/OAI). Im minimalsten Fall kann aber auf jedefall der Bitstream erhalten werden, also eine Abfolge von von Nullen und Einsen, die sich in elektronischen Signalen eines Computer wiederspiegeln. Diese Methode kann jede Datei erhalten, selbst wenn die Datei beispielsweise verschlüsselt, beschädigt, oder kein Dateiformat mehr auszumachen ist.

----

## Rosetta-Backend

Über das [Rosetta-Backend](https://www.lzv.nrw/ueber-lzv/wie-funktioniert-lzv), welches von der Landesinitiative Langzeitverfügbarkeit bereitgestellt wird, kann die Hochschule die Erhaltungsmaßnahmen ihrer digitalen Daten planen und durchführen. Bei Bedarf können die dort eingelieferten Daten auch wieder exportiert werden.
 
----

## Dissiminations-Frontend

Das Dissiminations-Frontend ist unsere öffentliche Webseite. Von hier aus können die Meta- und Mediendaten von Digi-Kunst.nrw durchsucht und angesehen werden. Nicht jedem/jeder Urser:in stehen allerdings alle Mediendaten zur Verfügung. Manche Mediendaten sind erst nach einem Log-In mit [Shibboleth](https://www.shibboleth.net/) und/oder nach vorheriger Anfrage sichtbar. Über eine entsprechende Schnitstellen werden sich Metadaten in gleich mehreren Formaten herunterladen und weiterverwenden lassen. Ebenso können über die angelegten Identifier die Datensätze zitiert werden und es ist immer ersichtlich, wann der Datensatz zuletzt geändert wurde.
