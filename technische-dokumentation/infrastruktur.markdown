---
layout: digi-kunst-docs
title: Infrastruktur
order: 3.3
---

## Strukturdiagramm
Dieses Strukturdiagramm veranschaulicht den logischen Aufbau der derzeitigen Projektinfrastruktur und zeigt die Zusammenhänge von Systemkomponenten, Nutzer:innen, angebundenen Diensten und externen Institutionen.

[![Digi-Kunst-Organigramm Stand Mai 2024]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png 'Das Strukturdiagramm veranschaulicht den logischen Aufbau der intendierten Projektinfrastruktur')]({{ site.baseurl }}/assets/images/2023-08-04_Strukturdiagramm.png)

[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2023-08-04_Strukturdiagramm.pdf]({{site.baseurl }}/assets/documents/2023-08-04_Strukturdiagramm.pdf) (50 KB)

In den folgenden Abschnitte werden die zentralen Einheiten dieses Modells kurz beschrieben.

----

## Erfassungsportal

Das Erfassungsportal besteht aus dem Erfassungs-Backend und dem Admin-Backend. Im Erfassungs-Backend kann man neue [Projekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#zentrale-entitäten-projekt-und-ereignis) angelegen sowie bereits bestehende Projekte verwalten. Das Erfassungs-Backend steht allen einliefernden Personen zur Verfügung. Das sind, neben der [Projektleitung]({{ site.baseurl }}/projektstruktur/team.html#gesamtprojektleitung) und unseren [Mediendokumentar:innen]({{ site.baseurl }}/projektstruktur/team.html#mediendokumentarinnen), zunächst ausgewählte Personen an den Hochschulen. In Zukunft soll dieses Backend aber, via [Shibboleth](https://www.shibboleth.net/), auch für Lehrende und Student:innen zugänglich sein. Das Admin-Backend umfasst die Verwaltung kontrollierter Vokabulare und Taxonomien sowie die Verwaltung von verfügbaren Rechte- und Lizenzangaben, die auf Projekte und [Digitale Objekte]({{ site.baseurl }}/ressourcen/entitaeten_und_attribute_des_datenmodells.html#ereignis-digitale-objekte) angewendet werden können. Dieser Zugriff ist, je nach Verwaltungseinheit, auf die Projektleitung und/oder die Mediendokumentar:innen beschränkt.

----

## Staging-Server

Die eingegeben Daten und hochgeladenen Dateien werden dann zunächst auf einem Staging-Server gespeichert. Dabei achtet der Server darauf, dass die hochgeladenen Dateien auch vollständig sind. Auf dem Server angekommen, werden die Dateien mit einer Prüfsumme versehen, sodass spätere Änderungen an ihnen nachvollziehbar sind, und eine Reihe technsicher Informationen aus ihnen ausgelesen. Beides, die manuell eingegeben und die ausgelesen Daten, werden gemeinsam in einer [relationalen Datenbank](https://www.ibm.com/de-de/topics/relational-databases) gespeichert. Damit einzelne Datensätze in- und außerhalb von Digi-Kunst.nrw identifizierbar sind, verwenden wir sogenannte [Handles](https://www.handle.net/). Es ist aber vorgesehen, auch noch weitere digitale Identifikatoren vergeben zu können, zum Beispiel [DOIs](https://www.doi.org/). Sind alle Dateien und Informationen vollständig vorhanden, wird über eine Metadatenschnitstelle ein Paket erzeugt, das für die Langzeitverfügbarkeit geeignet ist. Dieses Paket wird dann an das Arbeits- und Webrepositorium KA3 weitergeleitet.

----

## Arbeits- und Webrepositorium KA3

----

## Rosetta-Backend

