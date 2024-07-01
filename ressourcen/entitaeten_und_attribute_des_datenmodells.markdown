---
layout: digi-kunst-docs
title: Entitäten und Attribute des Datenmodells
order: 2.2
---

## Zentrale Entitäten: Projekt und Ereignis

Die Aufgabe von Digi-Kunst ist es, die multimedialen künstlerischen Inhalte der Kunst- und Musikhochschulen des Landes NRW zu erschließen und zu sichern. Hauptsächlich sind das künstlerische Werke, aber auch viele Dinge, die sich nicht wirklich als Werk beschreiben lassen, wie z. B. Aufzeichnungen von Vorträgen. Deshalb benutzt Digi-Kunst.nrw als zentrale Verzeichnungseinheit den Begriff **Projekt**. Dies erlaubt eine größere Flexibilität und ermöglicht es, die ganze Bandbreite der künstlerischen Aktivitäten an den Hochschulen zu erfassen.

Ein Datensatz zu einem Projekt enthält in der Regel einen Titel und die Beschreibung eines Projekts. Hier wird es kategorisiert und verschlagwortet, es wird die einliefernde Hochschule und ggf. deren Organisationseinheit erfasst.

Als zweite zentrale Einheit bilden **Ereignisse** die historische Entwicklung eines Projekts ab:

* Es gibt viele [Typen von Ereignissen]({{ site.baseurl}}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/ereignistypen): Mit dem Ereignis der geistigen Schöpfung oder der Herstellung entsteht überhaupt erst ein Kunstwerk, später gibt es dann oft weitere Ereignisse wie Aufführung, Ausstellung oder Filmpremiere.
* Ereignisse haben in der Regel einen Beginn und ein Ende und finden an bestimmten Orten statt.
* Ereignisse werden von verschiedenen Akteur:innen durch- oder aufgeführt, wodurch sich rechtliche Ansprüche ableiten können.
* Bei manchen Ereignissen wird bestimmte Software und Equipment verwendet.
* Bei manchen Ereignissen entstehen bestimmte Physische Objekte oder werden verwendet.
* Ereignisse manifestieren sich oder werden dokumentiert in Digitalen Objekten (Dateien).
* Manche Digitale Objekte entstehen durch die Retrodigitalisierung eines Informationsträgers.

All diese Informationen sind ausschließlich über Ereignisse mit einem Projekt verknüpft. 

Ein Projekt kann beliebig viele Ereignisse beinhalten, und dasselbe Ereignis kann in beliebig vielen Projekten auftauchen.

<pre class="mermaid">
flowchart LR;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann mehrere Ereignisse haben</span> -->Ereignis
    Ereignis-- <span style="background-color: #f4effc">Dasselbe Ereignis kann in mehreren Projekten vorkommen</span> -->Projekt
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Ereignis fill:#90EE90, stroke:#000000;
</pre>


----

## Projekt: Titel & Alternative Titel

Ein Projekt muss einen bevorzugten Titel und kann – bei Bedarf – einen bevorzugten Untertitel haben. Diese bevorzugten Titel werden prominent in Anzeige und Suche angezeigt und sollten den gewünschten Haupt- und/oder Originaltitel des Projekts wiedergeben. Zudem müssen bevorzugter Titel und bevorzugter Untertitel eine Sprachauszeichnung erhalten. Für die Sprachauszeichnungen wird die Norm [ISO639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php) verwendet.

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">hat</span>  --> Bevorzugter_Titel[Bevorzugter Titel]
    Projekt-- <span style="background-color: #f4effc">hat bei Bedarf</span> --> Bevorzugter_Untertitel[Bevorzugter Untertitel]
    Bevorzugter_Titel-- <span style="background-color: #f4effc">hat</span>  --> Sprachauszeichnung
    Bevorzugter_Untertitel-- <span style="background-color: #f4effc">hat</span> --> Sprachauszeichnung
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Bevorzugter_Titel fill:#FFFFE0, stroke:#000000;
    style Bevorzugter_Untertitel fill:#FFFFE0, stroke:#000000;
</pre>


Zusätzlich können noch beliebig viele alternative Titel angelegt werden. Es ist häufig der Fall, dass Kunstwerke nicht nur unter einem Namen bekannt sind oder geführt werden, sondern im Laufe ihrer Historie oft mehrere Titel haben. Dies ist auch notwendig, wenn der Originaltitel nicht das lateinische Alphabet verwendet sondern beispielsweise kyrillische Schrift oder chinesische Zeichen. 

----

## Projekt: Projektkategorien

Projektkategorien geben die Kunstgattung oder das Genre eines Projekts an. Dafür verwenden wir eine selbst erstellte Taxonomie, in der die Kategorien in einem hierarchischen Kontext abgebildet werden. Beispiel: Für ein Projekt wurde die Projektkategorie „Industrial Design“ vergeben. In unserem System taucht diese Projektkategorie dann wie folgt auf:

<a href="{{ site.baseurl }}/assets/images/Beispiel_Breadcrumb_Projektkategorien.png"><img src="{{ site.baseurl }}/assets/images/Beispiel_Breadcrumb_Projektkategorien.png" class="center-image" style="width: 400px;"/></a>

Alle drei Kategorien werden dem Projekt zugeordnet, so dass sich dieses dann auch z. B. unter dem Begriff "Angewandte Kunst" wiederfindet. Zusätzlich sind die Kategorien mit Synonymen angereichert, um eine noch bessere Auffindbarkeit zu gewährleisten.

Es können beliebig viele Kategorien zu einem Projekt vergeben werden, was es ermöglicht, auch Projekte zu beschreiben, die nicht eindeutig in nur eine Kategorie fallen. Einen Überblick, mit welchen Kategorien Digi-Kunst.nrw gestartet ist, lässt sich in der Liste unserer [Projektkategorien]({{ site.baseurl }}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/projektkategorien) finden. 

Jede Projektkategorie enthält mindestens auch noch den Link zu einem Begriff aus der [Wikidata](https://www.wikidata.org/w/index.php?title=Wikidata:Main_Page&uselang=de), oft sogar ein ganzes Set von Links zu großen kontrollierten Vokabularen: dem Vokabular der Deutschen Nationalbibliothek, dem Vokabular des Getty Art & Architecture Thesaurus und dem Vokabular des Filmportals.de.

----

## Projekt: Schlagwörter

Die Verzeichnung der Schlagwörter erfolgt über [Wikidata](https://www.wikidata.org/). Dadurch wird die Anbindung an Semantic Web- und Linked Open Data Anwendungen gewährleistet. Damit ein Schlagwort in unser System geladen werden kann, benötigt es mindestens einen deutschen oder englischen Wikidata-Eintrag mit zugehöriger Beschreibung, die automatisch ausgelesen werden. Synonyme werden, falls vorhanden, ebenfalls abgerufen, um zusätzlich die Erschließung der erfassten Inhalte zu verbessern. 

Dieses System der Verschlagwortung über Wikidata findet überall dort Verwendung, wo Schlagwort-ähnliche Einträge gemacht werden können. Neben dem Projekt sind dies Physisches Objekt, Digitales Objekt und Informationsträger.

<a href="{{ site.baseurl }}/assets/images/schlagwort_auslesen.png"><img src="{{ site.baseurl }}/assets/images/schlagwort_auslesen.png" class="center-image" style="margin-top: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>
<a href="{{ site.baseurl }}/assets/images/ausgelesenes_schlagwort.png"><img src="{{ site.baseurl }}/assets/images/ausgelesenes_schlagwort.png" class="center-image" style="margin-bottom: 8%; border: 1px solid black;"/></a>

----

## Projekt: Einliefernde Hochschule und Organisationseinheiten

Ein Projekt muss einer einliefernden Hochschule zugeordnet werden. Zu einer Einliefernden Hochschule können beliebig viele Projekte gehören. Die Einliefernde Hochschule gibt an, welche der Konsortialhochschulen rechtlich für die Behandlung des Projektes verantwortlich ist. Neben ihrem offiziellen deutschen Namen und ihrem englischen Namen haben die einzelnen einliefernden Hochschulen zusätzlich einen Wikidata-Link und einen GND-Link, durch den sie im Internet identifizierbar sind.

| Deutscher Name | Englischer Name | Wikidata-Link | GND-Link |
| ------------- | ------------- | ------------- | ------------- |
| Folkwang Universität der Künste | Folkwang University of the Arts | [https://www.wikidata.org/entity/Q521612](https://www.wikidata.org/entity/Q521612) | [https://d-nb.info/gnd/16159133-4](https://d-nb.info/gnd/16159133-4) |
| Hochschule für Musik Detmold | Hochschule für Musik Detmold | [https://www.wikidata.org/entity/Q317855](https://www.wikidata.org/entity/Q317855) | [https://d-nb.info/gnd/5073685-1](https://d-nb.info/gnd/5073685-1) |
| Hochschule für Musik und Tanz Köln | Hochschule für Musik und Tanz Köln | [https://www.wikidata.org/entity/Q55021](https://www.wikidata.org/entity/Q55021) | [https://d-nb.info/gnd/6525138-6](https://d-nb.info/gnd/6525138-6) |
| Kunsthochschule für Medien Köln | Academy of Media Arts Cologne | [https://www.wikidata.org/entity/Q827038](https://www.wikidata.org/entity/Q827038) | [https://d-nb.info/gnd/2128885-9](https://d-nb.info/gnd/2128885-9) |
| Robert Schumann Hochschule Düsseldorf | Robert Schumann Hochschule Düsseldorf | [https://www.wikidata.org/entity/Q315238](https://www.wikidata.org/entity/Q315238) | [https://d-nb.info/gnd/5082177-5](https://d-nb.info/gnd/5082177-5) |

Abgesehen von diesem rechtlichen Rahmen kann angegeben werden, aus welcher Organisationseinheit innerhalb der Hochschule ein Projekt stammt. Das kann beispielsweise ein Studiengang sein, ein Forschungsinstitut oder zum Beispiel ein Archiv.

<pre class="mermaid">
flowchart LR;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt gehört zu einer\n Einliefernden Hochschule</span>  --> Einliefernde_Hochschule[Einliefernde Hochschule]
    Einliefernde_Hochschule-- <span style="background-color: #f4effc">Zu einer Einliefernden Hochschule können beliebig\n viele Projekte gehören</span>  --> Projekt
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann zu einer oder\n mehreren Organisationseinheiten gehören</span>  --> Organisationseinheit
    Organisationseinheit-- <span style="background-color: #f4effc">Zu einer Organisationseinheit können beliebig\n viele Projekte gehören</span>  --> Projekt
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Einliefernde_Hochschule fill:#FFFFE0, stroke:#000000;
    style Organisationseinheit fill:#FFFFE0, stroke:#000000;
</pre>

----



## Projekt: Beschreibungen & Kommentare

Ein Projekt muss mindestens eine und kann beliebig viele Beschreibungen haben. Deswegen ist das Feld „Beschreibung“ in unserer Datenmodell-Tabelle mit der Kardinalität „1-u[nendlich“ gekennzeichnet. Die Beschreibung ist meistens ein von dem/der Autor:in des Projekts verfasster Text, kann aber auch von Dritten verfasst worden sein. Ähnlich wie Titel haben Beschreibungen eine Sprachauszeichnung. Beschreibungen können innerhalb eines Projekts nach ihrer Wertigkeit sortiert werden.

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann mehrere Beschreibungen haben \n Zum Export benötigt es mindestens eine</span>  -->Beschreibung
    Beschreibung-- <span style="background-color: #f4effc">hat</span> --> Sprachauszeichnung
    Beschreibung-- <span style="background-color: #f4effc">hat</span> --> Sortierungsnummer
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Beschreibung fill:#FFFFE0, stroke:#000000;
</pre>

Ebenso ist es möglich, einen Kommentar zum Projekt anzugeben. Wenn der deutsche Kommentar verwendet wurde, muss auch eine Übersetzung auf Englisch angegeben werden, und umgekehrt.

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">kann einen Deutschen Kommentar haben</span>  ---> Deutscher_Kommentar[Deutscher Kommentar]
    Projekt-- <span style="background-color: #f4effc">kann einen Englischen Kommentar haben</span>  --> Englischer_Kommentar[Englischer Kommentar]
    Deutscher_Kommentar-- <span style="background-color: #f4effc">ist Pflicht wenn benutzt</span> ---> Englischer_Kommentar
    Englischer_Kommentar-- <span style="background-color: #f4effc">ist Pflicht wenn benutzt</span> ---> Deutscher_Kommentar
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Deutscher_Kommentar fill:#FFFFE0, stroke:#000000;
    style Englischer_Kommentar fill:#FFFFE0, stroke:#000000;
</pre>

----

## Projekt: Projektart

Ein Projekt muss zu mindestens einer und kann zu mehreren [Projektarten]({{ site.baseurl}}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/projektarten) gehören. Die Projektart bezeichnet den Typ des Projekts im akademischen oder administrativen Kontext. 

----

## Projekt: Identifikatoren und Normdaten

Ein Projekt bekommt automatisch eine Digi-Kunst-ID. Diese setzt sich zusammen aus:

* Der Kennzeichnung „Digi-Kunst“
* Einer automatischen Nummer, die zählt, das wievielte Projekt es insgesamt in unserem System ist
* Einem dreistelligen Identifikator für die einliefernde Hochschule: **FUK** für die Folkwang Universität der Künste, **DET** für die Hochschule für Musik Detmold, **HMT** für die Hochschule für Musik und Tanz Köln, **KHM** für die Kunsthochschule für Medien Köln und **RSH** für die Robert Schumann Hochschule Düsseldorf.
* Einer weiteren automatischen Nummer, die zählt, das wievielte Projekt von der entsprechenden Hochschule in unserem System ist.

Eine vollständige Signatur könnte also wie folgt aussehen: **Digi-Kunst-9876-KHM-5432**.

Des Weiteren werden auch Einlieferer-interne Signaturen bei uns erfasst, ebenso wie Werkverzeichnisnummern.

Zusätzlich können zu einem Projekt beliebig viele Normdaten-Links angegeben werden, wie z. B. zu Karlheinz Stockhausens „Gesang der Jünglinge“: [https://d-nb.info/gnd/300322518](https://d-nb.info/gnd/300322518).

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">hat</span>  ---> Digi-Kunst-ID
    Projekt-- <span style="background-color: #f4effc">kann, wenn vorhanden, ein oder mehrere haben</span> --> Werkverzeichnisnummer
    Projekt-- <span style="background-color: #f4effc">kann, wenn vorhanden, ein oder mehrere haben</span> ---> Normdaten-Link
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Digi-Kunst-ID fill:#FFFFE0, stroke:#000000;
    style Werkverzeichnisnummer fill:#FFFFE0, stroke:#000000;
    style Normdaten-Link fill:#FFFFE0, stroke:#000000;
</pre>

----

## Projekt: Projekteigenschaften und Inhaltwarnungen

In den Projekteigenschaften können fachspezifische Angaben gemacht werden, etwa die Tonart eines Musikstücks oder die Dauer eines Films. Ein Projekt kann beliebig viele fachspezifische Angaben haben.

Zu einem Projekt kann eine projektspezifische, einmalig verwendbare Inhaltswarnung gegeben werden. Andere, bereits im Voraus angelegte Inhaltswarnungen können in anderen Projekten immer wieder Verwendung finden.

----

## Projekt: Nutzungsrechte

Damit eine einliefernde Hochschule die Digitalen Objekte eines Projekts in die Langzeitverfügbarkeit überführen, es öffentlich zugänglich machen und es gegebenenfalls an andere Portale für Kultur und Wissen weitergeben kann, benötigt sie dafür die Nutzungsrechte von den Rechteinhaber:innen. 

Diese können auf zweierlei Arten eingeholt werden:

* Zum einen kann bereits ein Nutzungsvertrag zwischen den Rechteinhaber:innen und der Hochschule bestehen, mit welchem bereits verschiedene Erhaltungsschritte erlaubt sind. Zum Beispiel kann es sein, dass die Archivierung eines Projekts bereits Bestandteil einer vorherigen Vereinbarung war. In diesen Fällen ist zu klären, ob Digi-Kunst.nrw bereits verschiedene Arbeitsschritte ausführen darf, beispielsweise die Projekte zu verzeichnen und die Dateien in die Langzeitverfügbarkeit zu überführen.
* Zum anderen kann über Digi-Kunst.nrw ein neuer Lizenzvertrag geschlossen werden, falls noch keiner vorliegt oder der bereits bestehende Lizenzvertrag erweitert werden soll. Digi-Kunst.nrw stellt dafür eine speziell für diesen Zweck erstellte Modularlizenz zur Verfügung. Details hierzu finden sich auf der Seite [Lizenzen]({{ site.baseurl }}/ressourcen/lizenzen).

Es ist möglich, auf Wunsch alle oder nur einzelne Digitale Objekte eines Projekts (bzw. eines Ereignisses) zu veröffentlichen. Nicht veröffentlichte Digitale Objekte bleiben für die Öffentlichkeit unzugänglich und werden nur in die Langzeitverfügbarkeit-Sicherung des hbz gegeben. Die Metadaten (Titel, Beschreibung, Akteur:innen, usw.) werden, sofern sie keine durch die DSGVO geschützten, persönlichen Informationen beinhalten, frei veröffentlicht.

<pre class="mermaid">
flowchart TB;
    Projekt_Urheberrechtsstatus{Ist das Projekt urheberrechtlich\n und/oder leistungsschutzrechtlich geschützt?}-- <span style="background-color: #f4effc">nein</span>  --> Projekt_eingeliefert[Das Projekt kann ohne Lizenzvereinbarung\n bei Digi-Kunst.nrw eingeliefert werden]
    Projekt_Urheberrechtsstatus-- <span style="background-color: #f4effc">ja</span>  ---> Lizenzvertrag_benötigt[Es wird eine Lizenzvereinbarung benötigt]
    Lizenzvertrag_benötigt --> Besteht_Lizenzvertrag{Besteht bereits ein Lizenzvertrag zwischen\n der Hochschule und dem/der Lizenzgeber:in?}
    Besteht_Lizenzvertrag-- <span style="background-color: #f4effc">ja</span>  --> Rechte_werden_geprüft[Es wird geprüft, welche Erhaltungsschritte\n bei Digi-Kunst.nrw bereits durchgeführt werden können]
    Besteht_Lizenzvertrag-- <span style="background-color: #f4effc">nein</span>  --> Neuer_Lizenzvertrag[Es kann ein neuer Lizenzvertrag via Digi-Kunst.nrw geschlossen werden]
    Rechte_werden_geprüft-- <span style="background-color: #f4effc">zusätzlich</span>  --> Neuer_Lizenzvertrag[Es kann ein neuer Lizenzvertrag via Digi-Kunst.nrw geschlossen werden]
</pre>

Außerdem gibt es noch einige Sonderfälle, die im Einzelfall geprüft werden müssen. So kann es sein, dass ein Werk verwaist ist, es also auch nach vorheriger Recherche nicht mehr seinen zugehörigen Urheber:innen zugeordnet werden kann. In diesem Fall kann eine europäische Sonderregelung gelten, bei der die zugehörigen Dateien öffentlich zugänglich gemacht werden könnten.


----

## Ereignis: Ereignistypen

Ereignisse können ebenso kategorisiert werden wie Projekte. Ein Ereignis kann ein Ankauf sein, eine musikalische Komposition, eine Ursendung oder ein Rundgang. Eine Übersicht über die Ereignistypen, die den Grundstock von Digi-Kunst.nrw bilden, finden Sie in der Liste unserer [Ereignistypen]({{ site.baseurl }}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/ereignistypen). Ein Ereignistyp hat mindestens einen Wikidata-Link und kann zusätzlich einen GND-Link, einen AAT-Link und einen Link zu einem Ereignis aus der LIDO-Terminologie haben.

<pre class="mermaid">
flowchart LR;
    Ereignis-- <span style="background-color: #f4effc">hat einen</span> --> Ereignistyp
    Ereignistyp-- <span style="background-color: #f4effc">hat</span> --> Wikidata-Link
    Ereignistyp-- <span style="background-color: #f4effc">kann zusätzlich haben</span> --> GND-Link
    Ereignistyp-- <span style="background-color: #f4effc">kann zusätzlich haben</span> --> AAT-Link
    Ereignistyp-- <span style="background-color: #f4effc">kann zusätzlich haben</span> --> LIDO-Terminologie-Link
    Ereignistyp-- <span style="background-color: #f4effc">kann zusätzlich haben</span> --> Synonyme
    style Ereignis fill:#90EE90, stroke:#000000;
    style Ereignistyp fill:#90EE90, stroke:#000000;
</pre>

----

## Ereignis: Zeitraumangaben

Ein Ereignis kann einen Beginn oder ein Ende haben. Es muss aber mindestens eine dieser beiden Angaben vorhanden sein. Sowohl der Ereignisbeginn als auch das Ereignisende können geschätzt sein. Zeitangaben speichern wir nach der Norm [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).

<pre class="mermaid">
flowchart TB;
    Ereignis-- <span style="background-color: #f4effc">hat (mindestens)\n kann bei Bedarf geschätzt sein</span> ---> Ereignisbeginn
    Ereignis-- <span style="background-color: #f4effc">hat (mindestens)\n kann bei Bedarf geschätzt sein</span> --> Ereignisende
    style Ereignis fill:#90EE90, stroke:#000000;
    style Ereignisbeginn fill:#90EE90, stroke:#000000;
    style Ereignisende fill:#90EE90, stroke:#000000;
</pre>

| Ereignisbeginn in ISO 8601 | Ereignisende in ISO 8601 | Ereigniszeitraum | Technischer Ereigniszeitraum |
| ------------- | ------------- | ------------- |
|2022| 2023 | 2022–2023 | 01.01.2022, 0:00 Uhr–31.12.2023, 23:59 Uhr |
| 2022-02 | 2023-03 | Februar 2023–März 2023 | 01.02.2022, 0:00 Uhr–31.03.2023, 23:59 Uhr |
| 2022-02-02 | 2023-03-03 | 02.02.2022–03.03.2023 | 02.02-2022, 0:00 Uhr–03.03.2023, 23:59 Uhr |
| 2022-02-02T12:12 | 2023-03-02T13:13 | 02.02.2022, 12:12 Uhr–03.03.2023, 13:13 Uhr | 02.02.2022, 12:12 Uhr–03.03.2023, 13:13 Uhr |

----

## Ereignis: Orte
Ein Ereignis kann an mehreren Orten stattgefunden haben. Orte laden wir, ebenso wie Schlagwörter, aus der Wikidata. Bei Orten wird aber im Hintergrund eine komplexere Abfrage gestellt, die mit der Abfragesprache SPARQL ausgeführt wird. SPARQL-Anfragen werden im Grunde wie Sätze formuliert: Finde alle „Orte“ „die übergeordnet sind“ „zum eingegebenen Ort“. Unsere Ort-Abfrage ist somit in der Lage, einen eingegebenen Ort direkt in seinen geografischen Kontext zu setzen. Es muss nur die Wikidata-ID eingegeben werden und das System übernimmt diese Einordnung. Bei uns werden Orte auf 6 Ebenen erfasst. Diese sind: **Kontinent** > **Land** > **Region** > **Stadt** > **Genauer Ort** > **Interner Ort**.

<a href="{{ site.baseurl }}/assets/images/wikidata_ort.png"><img src="{{ site.baseurl }}/assets/images/wikidata_ort.png" class="center-image" style="margin-top: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>

<a href="{{ site.baseurl }}/assets/images/adm_ort_angelegt.png"><img src="{{ site.baseurl }}/assets/images/adm_ort_angelegt.png" class="center-image" style="margin-bottom: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>

----

## Ereignis: Akteur:innen, Rollen und Rechteangaben

Personen, Gruppen oder Körperschaften können Akteur:innen sein. Die folgende Tabelle, zeigt, welche Attribute dazu angelegt werden können.

<pre class="mermaid">
flowchart LR;
    Ereignis-- <span style="background-color: #f4effc">Ein Ereignis kann mehrere Akteur:innen haben</span> --> AkteurIn[Akteur:in]
    AkteurIn-- <span style="background-color: #f4effc">Dieselbe Akteur:in kann an mehreren Ereignissen beteiligt sein</span> --> Ereignis
    style Ereignis fill:#90EE90, stroke:#000000;
    style AkteurIn fill:#F0F8FF, stroke:#000000;
</pre>

| Deutscher Feldname | Englischer Feldname | Kardinalität | Bemerkung |
| ------------- | ------------- | ------------- |
| Deutscher Name | German Name | 1 | Automatisch der englische Name, wenn nur dieser angegeben wurde |
| Englischer Name | English Name | 1 | Automatisch der deutsche Name, wenn nur dieser angegeben wurde |
| Alternativer Name | Alternative Name | 0-u | Beliebig viele Varianten des Namens, u. a. auch der Name in der Herkunftssprache |
| Nicht-öffentlicher Name | Non-public Name | 0-u | Ein Name, der nicht veröffentlicht werden soll, aber für die Langzeitverfügbarkeit oder Team-intern von Bedeutung ist |
| Nicht-öffentlicher Name (Erläuterung)| Non-public Name (Reason) | [1-u] | Eine Begründung, warum der Name nicht öffentlich stehen soll |
| Vorangestellter Titel | Preceding Title | 0-1 | Z. B. "Prof.", "Dr.phil.", "Dr. Dr.", etc.. |
| Nachgestellter Titel | Following Title | 0-1 | Z. B. "PhD" |
| Geschlecht | Gender | 0-1 | Entweder *männlich*, *weiblich* oder *divers*. Bei Gruppen und Körperschaften bleibt dieses Feld leer |
| Frühestes Geburtsdatum | Earliest Birth Date | 0-1 | Das früheste bekannte Geburtsdatum in ISO 8601|
| Spätestes Geburtsdatum | Latest Birth Date | 0-1 | Das späteste bekannte Geburtsdatum in ISO 8601 |
| Frühestes Sterbedatum | Earliest Death Date | 0-1 | Das früheste bekannte Sterbedatum in ISO 8601 |
| Spätestes Sterbedatum | Latest Death Date | 0-1 | Das späteste bekannte Sterbedatum in ISO 8601 |
| Wirkungsbeginn | Begin of Activity | 0-1 | Für Gruppen und Körperschaften deren Wirkungsbeginn in ISO 8601 |
| Wirkungsende | Enf of Activity | 0-1 | Für Gruppen und Körperschaften deren Wirkungsende in ISO 8601 |
| Geburtsort | Place of Birth | 0-1 | Ein Geburtsort aus der Entität Orte |
| Sterbeort | Place of Death | 0-1 | Ein Sterbeort aus der Entität Orte |
| Wirkungsort | Place of Activity | 0-u | Ein oder mehrere Wirkungsorte |
| Gründungsort | Place of Activity | 0-u | Für Gruppen und Körperschaften deren Gründungsorte |
| Auflösungsort | Place of Activity | 0-u | Für Gruppen und Körperschaften deren Auflösungsorte |
| Deutsche Kurzbiografie | German Short Biography | 0-1 | Die deutsche Kurzbiografie der Person, Gruppe oder Körperschaft |
| Englische Kurzbiografie | English Short Biography | 0-1 | Die englische Kurzbiografie der Person, Gruppe oder Körperschaft |
| Deutscher Kommentar | German Commentary | 0-1 | Ein deutscher Kommentar |
| Englischer Kommentar | English Commentary | [1] | Ein entsprechender englischer Kommentar |
| Interner Kommentar | Internal Commentary | 0-1 | Ein Team-interner Kommentar |           
| Beruf und Tätigkeit | Profession and Activity | 0-u | Ein oder mehrere feste Rollen aus der entsprechenden Entität (s. u.)|
| OrcID | OrcID | 0-1 | Ein Orcid-Identifier der Person |
| GND-Link | GND Link | 0-1 | Link zu einem GND-Normdatensatz zur Akteur:in |
| VIAF-Link | VIAF Link | 0-1 | Link zu einem VIAF-Normdatensatz zur Akteur:in |
| LCCN-Link | LCCN Link | 0-1 | Link zu einem Normdatensatz zur Akteur:in in der Library of Congress |
| Wikidata-Link | Wikidata Link | 0-1 | Link zu einem Wikidata-Satz zur Akteur:in |
| Andere Normdaten | Other Authority Files | 0-u | Weitere Normdatenlinks |
| Link zur Webseite der Akteur:in | Link to Actor Page | 0-u | Links zu externen Webseiten der Akteur:innen |
| Kontakt (E-Mail) | Contact (E-Mail) | 0-u | Ein oder mehrere mögliche Kontaktemails. Diese werden nicht mit in die Langzeitverfügbarkeit überführt |
| Kontakt (Telefon) | Contact (Phone) | 0-u | Ein oder mehrere mögliche Telefonkontakte. Diese werden nicht mit in die Langzeitverfügbarkeit überführt |
| Kontakt (Postanschrift) | Contact (Postal Address) | 0-1 | Eine mögliche Postanschrift. Diese wird nicht mit in die Langzeitverfügbarkeit überführt |

Innerhalb eines Ereignisses kann ein:e Akteur:in mehrere Rollen haben. Eine Rolle hat einen deutschen und einen englischen Namen und einen Wikidata-Link. Zusätzlich können Rollen auch einen rollenspezifischen GND-Link und einen „Getty Art and Architecture Thesaurus“-Link haben. Zur besseren Auffindbarkeit von Akteur:innen kann eine Rolle auch noch mit deutschen und englischen Synonymen angereichert werden. Eine Übersicht, welche Rollen verwendbar sind, finden sie in der [Rollen-Taxonomie]({{ site.baseurl }}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/rollen).

<pre class="mermaid">
flowchart TB;
    AkteurIn[Akteur:in]-- <span style="background-color: #f4effc">hat ein oder mehrere</span> ---> Rolle
    Rolle-- <span style="background-color: #f4effc">im</span> ---> Ereignis
    style Ereignis fill:#90EE90, stroke:#000000;
    style AkteurIn fill:#F0F8FF, stroke:#000000;
</pre>

Die beiden Felder „steuert 'ist Urheberin'“ und „steuert 'besitzt Leistungsschutzrechte'“ finden sich, ähnlich wie „Rolle“   zwischen Akteur:in und Ereignis. Ein/eine Akteur:in in in einem Ereignis Urheber:in sein, im nächsten nicht, in einem anderen kann ein:e Akteur:in Leistungsschutzrechte besitzen, im anderen nicht. Zusammen mit einer Rolle ist eine Vorauswahl gespeichert, ob ein:e Akteur:in wahrscheinlich solche Rechte besitzt. Ist eine Akteurin beispielsweise „Komponist:in“ in einem Ereignis, dann ist sie mit großer Wahrscheinlichkeit auch „Urheber:in“ des Projekts. Ist ein Akteur „Produzent“ eines Films, besitzt er wahrscheinlich Leistungssschutzrechte. Letztlich bestimmt aber die eingebende Person, ob diese Vorauswahl zutrifft oder nicht. 

Zusätzlich kann angegeben werden, ob nur vermutet wird, dass ein:e Akteur:in in einem Ereignis mitgewirkt hat. Für diesen Fall gibt es das Feld „Ungesicherte Zuschreibung“.

----

## Ereignis: Equipment & Software

In einem Ereignis können verschiedene Arten von Equipment & Software zum Einsatz kommen. Zum Beispiel könnte man auf diese Weise beschreiben, welches Equipment oder welche Software zur Herstellung verwendet wurden. Die Liste der [Equipmentarten]({{ site.baseurl}}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/equipmentarten) erlaubt die Kategorisierung von Einträgen in der Tabelle Equipment und Software.

| Deutsche Feldbezeichnung | Englische Feldbezeichnung | Verweist auf Entität | Kardinalität | Notizen/Definition/Referenz |
| ------------- | ------------- | ------------- | ------------- |
| Deutsche (Produkt-) Bezeichnung | German (Product) Name |  |  1 | Handelsname, z.B. Hasselblad X, Photoshop CS6, Numark 402, InkJet 7800 |
| Englische (Produkt-) Bezeichnung | English (Product) Name |  |   1| Es kann vorkommen, dass Produkte in der englischen Welt und deutschen anders heißen. Der Regelfall wird aber sein, dass in beiden Bezeichnungsfeldern dasselbe steht. |
| Hersteller | Producer |  | 0-1 | Freitext |
| Equipmentart | Equipment Type | Equimentart | 1 | Auswahlliste , z.b. Mikrofon, Mischpult, Verstärker, Filmkamera, Fotokamera, Videokamera, 3D-Scanner, 3D-Drucker, SBC, Software, Zubehör (allgemein), Audiorecorder, Licht, Aufnahmegerät (allgemein) |
| Deutsche Beschreibung	 | German Description |  | 0-1	| Freitext |
| Englische Beschreibung	 | English Description |  | 0-1	| Freitext |
| Normdatei	 | Authority File |  | 0-u	| Wikidata-ID |

----

## Ereignis: Physische Objekte

Die Entität „Physische Objekte“ beschreibt körperliche Bestandteile und Materialien, die Teil eines Projekts sind, z. B. ihre Beschaffenheit oder welche Technik zur Herstellung verwendet wurde.

In einem Ereignis können beliebig viele Physische Objekte beschrieben werden. Dasselbe Physische Objekt kann in vielen Projekten vorkommen.

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
|Deutsche Bezeichnung | German Name | 1 | Automatisch der englische Name, wenn nur dieser angegeben wurde |
| Englische Bezeichnung	| English Name | 1 | Automatisch der englische Name, wenn nur dieser angegeben wurde |
| Externe Inventar-Signaturnummer | External Inventory Number | 0-u | Eine oder mehrere Signaturen |
| Aufbewahrungsort | Depository | 0-1 | Ein Ort aus der Orte-Entität |
| Besitzer:in | Owner | 0-u | Ein oder mehrere Akteur:innen aus der Akteur:in-Entität |
| Eigentümer:in | Legal Rights Holder | 0-u | Ein oder mehrere Akteur:innen aus der Akteur:in-Entität |
| Provenienz | Provenance | 0-1 | Ein Freitextfeld zur Provenienzbeschreibung |
| Deutsche Beschreibung | German Description | 0-1 | Eine Beschreibung im Freitext. Pflicht, wenn die englische Beschreibung angegeben wurde |
| Englische Beschreibung | English Description | [1] | Eine Beschreibung im Freitext. Pflicht, wenn die deutsche Beschreibung angegeben wurde |
| Deutscher Kommentar | German Commentary | 0-1 | Ein deutscher Kommentar. Pflicht, wenn der englische Kommentar angegeben wurde |
| Englischer Kommentar |English Commentary | [1] | Ein deutscher Kommentar. Pflicht, wenn der deutsche Kommentar angegeben wurde |
| Klassifizierendes Schlagwort | Classification Keyword to Physical Object | 0-u | Ein oder mehrere Schlagworte aus der Schlagwort-Entität, die Objekte bezeichnen, z. B. „Stuhl“, „Bühne“, „Sockel“, etc. |
| Materialschlagwort | Material Keyword | 0-u | Ein oder mehrere Schlagworte aus einer separaten Entität, um Materialien zu bezeichnen, z. B. „Polyurethan“, „Sand“, „Wachs“, „Kabel“ |
| Maße	| Measurements | 0-1 | Ein Freitextfeld, in das Maße eingetragen werden können |		
| Erhaltungszustand (deutsch) | Conservation State (German) | 0-1 | Eine deutsche Beschreibung des Erhaltungszustands des Objekts. Pflicht, wenn das entsprechende englische Feld benutzt wurde |
| Erhaltungszustand (englisch) | Conservation State (English) | [1] | Eine englische Beschreibung des Erhaltungszustands des Objekts. Pflicht, wenn das entsprechende deutsche Feld benutzt wurde |

----

## Ereignis: Informationsträger

Informationsträger sind materielle Datenträger oder Trägermedien, die digitalisiert wurden oder eine andere Rolle im Ereignis spielen, wie z. B. eine Schallplatte, eine Diskette, ein Tonband oder eine Festplatte. Informationsträger werden durch [die Informationsträgertypen]({{ site.baseurl }}/technische-dokumentation/kontrollierte-vokabulare-und-taxonomien/informationstraegertypen) kategorisiert. Zu einem Informationsträger können die folgenden Informationen erfasst werden:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| Deutsche (Produkt-) Bezeichnung | German (Product-) Name | 0-1 | Der deutsche Name oder die Bezeichnung des Informationsträgers, z. B. „BASF C-90“, „SONY KSP-20“, „Hi8 ME 120“, etc. |
| Englische (Produkt-) Bezeichnung | English (Product-) Name | 0-1 | Der englische Name oder die Bezeichnung des Informationsträgers |			
| Label (Handelsmarke) | Label | 0-1 | Eine Handelsmarke |			
| Informationsträgertyp	| Information Storage Media Type | 1 | Eine Auswahl aus der Informationsträgertyp-Taxonomie |
| Produkt-ID-Typ | Product ID Type | 0-u | Eine Auswahl aus der Entität "Nummernart". Z. B. "Bestellnummer", "ISBN", "Seriennummer" oder "Matritzennummer" |
| Produkt-ID-Wert | Product ID Value | [1] | Zu jeder Auswahl ein dazugehöriger Wert |
| Externe Inventar-Signaturnummer | External Inventory Number | 1-u | Eine Pflichtangabe, die den Informationsträger beim Einlieferer identifiziert. Bei Bedarf können es auch mehrere Nummern sein | 
| Besitzer:in                  | Owner                        | 0-u | Metadaten werden nicht veröffentlicht und gehen ausschließlich in die Langzeitverfügbarkeit/Rosetta                                                                       |
| Eigentümer:in                | Legal Rights Holder          | 0-u | Freitext-Feld z.b. "von 1950-1990 Frau Meyer, ab 1990 Herr Schulze" (Metadaten werden nicht veröffentlicht und gehen ausschließlich in die Langzeitverfügbarkeit/Rosetta) |
| Provenienz                   | Provenance                   | 0-1 | Freitext-Feld z.b. "von 1950-1990 Frau Meyer, ab 1990 Herr Schulze" (Metadaten werden nicht veröffentlicht und gehen ausschließlich in die Langzeitverfügbarkeit/Rosetta) |
| Deutsche Beschreibung        | German Description           | 0-1 | Freitext|
| Englische Beschreibung       | English Description          | 0-1 | Freitext|
| Deutscher Kommentar          | German Commentary            | 0-1 | Freitext|
| Englischer Kommentar         | English Commentary           | 0-1 | Freitext|
| Interner Kommentar           | Internal Commentary          | 0-1 | Freitext|
| Maße                         | Measurements                 | 0-1 | Freitext|
| Materialschlagwort           | Material Keyword             | 0-u | Verzeichnung über Schlagwort-Entität|
| Erhaltungszustand (deutsch)  | Conservation State (German)  | 0-1 | z.B. im Original vorhanden, zerstört, verschollen                                                                                                                         |
| Erhaltungszustand (englisch) | Conservation State (English) | 0-1 ||
| Aufbewahrungsort | Depository | 0-1 | Ein Ort aus der Orte-Entität. Der derzeitige oder letztbekannte Aufbewahrungsort |
| Informationsträgereigenschaft | Information Storage Medium Property | 0-u | Eine Auswahl aus der Entität "Informationsträgereigenschaft", z. B. „Bildfrequenz“, „Abspielgeschwindigkeit“ oder „Tonformat“ |									
| Informationsträgereigenschaft-Wert | Information Storage Medium Property Value | [1] | Zu jeder Auswahl ein dazugehöriger Wert |
| Normdatei | Authority File | 0-u | Ein Normdatenlink zum Informationsträger |								
| Kompilation | Compilation | 0/1 | Eine Angabe, ob der Informationsträger mehrere Projekte enthält. Entweder "ja", "nein" oder "keine Aussage" |
| Kompilationstitel | Compilation Title | [0-1] | Der Name dieser Kompilation |
| Kompilations-Reihennummer | Compilation Series Number | [0-1] | Die entsprechende Reihennummer |									
| Originalsprache | Original Language | 0-u | Eine oder mehrere ISO 639-Sprachen |
| Sprachfassung | Language Version | 0-u | Eine oder mehrere ISO 639-Sprachen  |
| Untertitelsprache | Subtitle Language | 0-u | Eine oder mehrere ISO 639-Sprachen  |	

----

## Ereignis: Digitale Objekte

Digi-Kunst.nrw definiert ein Digitales Objekt als eine Datei oder ein Dateibündel sowie zugehörige inhaltliche Beschreibung und technische Metadaten. Ein Ereignis kann beliebig viele Digitale Objekte enthalten, und ein Digitales Objekt kann in beliebig vielen Ereignissen auftauchen. Bereits beim Upload werden zentrale Metadaten zur Datei erfasst:

  * **Wie ist die Datei entstanden?** Ist sie „born digital“ oder ein Retrodigitalisat?
  * **Zu welchem Medientyp gehört die Datei?** 3D, Audio, Bild, Code, Text oder Video?
  * **Optional: Was ist ein Schlagwort, das den Inhalt der Datei beschreibt?** Aus was für einem Objekt besteht die Datei, bzw. was „ist“ die Datei: ein Poster, ein Trailer, eine Ausstellungsansicht, ein Musikkanal?
  * **Handelt es sich bei der Datei um ein Dateipaket oder nicht?**
  * **Bei Code: Welche Systemvoraussetzungen sind notwendig, damit das Programm ausgeführt werden kann?**
  * **Erhaltungstyp** Worum handelt es sich bei der Datei in einem langzeitarchivarischen Sinn? Um einen "Preservation Master" (ein Original oder eine nach bestimmten Richtlinien hergestellte Kopie), um einen "Modified Master" (meist eine bereits langzeitstabile Kopie, von der besser Nutzerformate erstellt werden können) oder um eine "Derivative Copy" (ein Nutzerformat)?
  * **Die wievielte Nutzerkopie dieser Datei ist es?**
  * **Welchen Urheberrechts- und Lizenzstatus hat die Datei?** Neben unseren eigenen Lizenzen können den Dateien auch die Lizenzen von Creative Commons verliehen werden. Weitere Informationen zu den Auswahlmöglichkeiten erhalten sie auf der Seite [**Lizenzen**]({{ site.baseurl }}/ressourcen/lizenzen/)
  * **Soll die Datei öffentlich angezeigt werden oder nicht?**
  * Zudem wird **automatisch ausgelesen, wie groß die Datei ist, zu welchem Dateityp sie gehört und wann sie zuletzt verändert wurde**.

Dies sind die Pflichtangaben, um ein Digitales Objekt erfassen zu können: 

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| Digi-Kunst Signatur bzw. ID | Digi-Kunst Call Number / ID | 1 | Ein eindeutiger Identifikator der Datei |	
| Dateiname | File Name | 1 | Der automatisch ausgelesene Dateiname der Datei |
| Dateigröße | File Size | 1 | Die automatisch ausgelesene Dateigröße der Datei |
| MIME Type | MIME Type | 1 | Der automatisch ausgelesene Dateityp der Datei |
| Datei-Änderungsdatum | File Modification Date	| 1 | Das automatisch ausgelesene letzte Änderungsdatum der Datei |
| Dateipfad | File Path | 1 | Der Dateipfad der Datei im Digi-Kunst.nrw-Erfassungsportal |
| Entstehung | Genesis | 1 | Eine Auswahl zwischen "born digital" oder "Retrodigitalisat" |
| Medientyp | Media Type | 1 | Eine Auswahl zwischen "3D", "Audio", "Bild", "Code", "Text" oder "Video" |
| Objekttyp | Object Type | 0-1 | Ein Schlagwort aus der Wikidata, z. B. "Poster", "Trailer" oder "Kanal" |
| Dateipaket | File Package | 0/1 | Entweder keine Auswahl oder "ja" |
| Systemvoraussetzungen	| System Requirements | [1 für "Code"] | Pflicht wenn für eine Datei der Medientyp "Code" ausgewählt wurde |
| Erhaltungstyp | Preservation Type | 1 | Entweder "Preservation Master", "Modified Master" oder "Derivative Copy (Nutzerformat)" |
| Derivatkopie-Nummer | Derivative Copy Number | [1 wenn "Derivative Copy (Nutzerformat)] | Bei einer Nutzerkopie muss angegeben werden, um die wievielte Kopie es sich handelt. |		
| Lizenzstatus | License State | 1 | Der Lizenzstatus einer Datei aus der Entität "Digitales-Objekt-Lizenz". Einer Lizenz ist auch immer ein Urheberrechtsstatus zugeordnet | 
| Anzeigestatus	| Display State | 1 | Regelt, ob die Datei ohne vorherige Anmeldung später frei angezeigt werden wird |
| KHM-Internetfreigabestufe | KHM Internet Clearance Level | 0-1 | Ein Sonderfeld für KHM-Dateien, das angibt, ob die entsprechende Datei bereits schon auf der Seite des KHM-Archivs öffentlich angezeigt wird |

Neben diesen Pflichtangaben gibt es noch eine Reihe von optionalen, deskriptiven Feldern:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| Deutsche inhaltliche Beschreibung | German Description | 0-1 | |
| Englische inhaltliche Beschreibung | English Description | [1] | |
| Deutscher Kommentar | German Commentary | 0-1 | |
| Englischer Kommentar | English Commentary | [1] | |
| Interner Kommentar | Internal Commentary | 0-1 | |
| Wesentliche Eigenschaften (deutsch) | Significant Properties (German) | 0-1 | |
| Wesentliche Eigenschaften (englisch) | Significant Properties (English) | [1] | |
| Bildbeschreibung (deutsch) | Image Description (German) | 0-1 | | 
| Bildbeschreibung (englisch) | Image Description (English) | 0-1 | |
| Originalsprache | Original Language | 0-u | |
| Sprachfassung | Language Version | 0-u | |
| Untertitelsprache | Subtitle Language | 0-u | |
| Tonmischfassung | Dubbing Version | 0-1 | |
| Tonformat | Sound Format | 0-1 | |
| DCP-Art | DCP Type | 0-1 | |
| Projekt-Kompilation | Project Compilation | 0/1 | |
| Teil einer Serie | Part of a Series | 0/1 | |
| wird im Loop abgespielt | plays in Loop | 0/1 | |
| EQ | EQ | 0-1 | |



Mit folgenden Programmen wird außerdem eine Vielzahl von technischen Metadaten der Datei ausgelesen. Hierzu verwendet unser System:

  * [JHOVE](https://jhove.openpreservation.org/) – ursprünglich entwickelt von [JSTOR](https://www.jstor.org/) und der [Harvard University Library](https://library.harvard.edu/); derzeit in Kooperation weiterentwickelt von der [Open Preservation Foundation](https://openpreservation.org/)
  * [DROID](https://www.nationalarchives.gov.uk/information-management/manage-information/preserving-digital-records/droid/) von [The UK National Archives](https://www.nationalarchives.gov.uk/)
  * [MediaInfo](https://mediaarea.net/de/MediaInfo) von [MediaArea](https://mediaarea.net/)
  * [ExifTool](https://exiftool.org/) von Phil Harvey

Der Output dieser Tools wird in Gänze gespeichert. Einige Informationen aus diesem technischen Metadaten werden zusätzlich herausgezogen und in eigenen Feldern angezeigt:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| JHOVE-Dateistatus | JHOVE Status | 1 | Eine Information, die anzeigt, ob eine Datei valide und/oder wohlgeformt ist |							
| DROID-PUID | PUID | 1 | Eine aus DROID automatisch ausgelesene ID, die eine Datei in der [PRONOM-Datenbank](https://www.nationalarchives.gov.uk/PRONOM/) von [The National Archives](https://www.nationalarchives.gov.uk/) identifiziert. |							
| DROID-PUID-Link | PUID Link | 1 | Ein daraus erzeugter Link, z. B.: [https://www.nationalarchives.gov.uk/PRONOM/fmt/134](https://www.nationalarchives.gov.uk/PRONOM/fmt/134)
| Prüfsumme | Hash/Checksum | 1 | Eine von DROID erzeugte Prüfsumme der Datei (SHA512) |									
| Dateityp (kurz) | File Type (short) | 1 | Der kurze Name des Dateityps |
| Dateityp (lang) | File Type (long) | 1 | Der ausgeschriebene Name des Dateityps |
| Dateifamilie | File Family | 1 | Die jeweilige Dateifamilie |
| MediaInfo-Format | MediaInfo-Format | 0-1 | Ein oder mehrere MediaInfo „track types“ (General, Audio, Video, Text, Other) |
| Technische Dauer | Technical Duration	| 0-1 | Für Video- und Audiodateien |								


----

## Selbstreferentielle Verknüpfungen

Projekte, Ereignisse und Akteur:innen können jeweils rekursiv verknüpft werden, z. B. ein Projekt kann Teil eines anderen Projekts sein, oder einzelne Akteur:innen sind Mitglied einer Künstler:innengruppe, die ebenfalls als Akteur:in angelegt ist.

Diese Art von Verbindungen ist immer reziprok. Das heißt, wenn eine Verbindung hergestellt wurde, wird immer die passende Gegenverbindung mit angelegt. Ein Beispiel: Würde man bei C. P. E. Bach die Verbindung "hat Vater" = "Johann Sebastian Bach" herstellen, so würde bei Letzterem automatisch folgendes angelegt werden: "ist Vater von" = "C. P. E. Bach". 

<pre class="mermaid">
flowchart LR;
    Projekt<-- <span style="background-color: #f4effc">kann in Verbindung stehen zu</span> ---> Projekt
    Ereignis<-- <span style="background-color: #f4effc">kann in Verbindung stehen zu</span> ---> Ereignis
    AkteurIn[Akteur:in]<-- <span style="background-color: #f4effc">kann in Verbindung stehen zu</span> ---> AkteurIn
    style AkteurIn fill:#F0F8FF, stroke:#000000;
    style AkteurIn fill:#F0F8FF, stroke:#000000;
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Ereignis fill:#90EE90, stroke:#000000;
</pre>

Die folgenden Listen zeigen, welche Verbindungen angelegt werden können.

### Projekt

| Ausgewählte Verbindung | Gegenstück |
| ------------- | ------------- |
| hat Bezug zu | hat Bezug zu |
| hat Teil | ist Teil von |
| ist Teil von | hat Teil |
| basiert auf | ist vorbereitend für |
| ist vorbereitend für | basiert auf |
| hat Kopie | ist Kopie von |
| ist Kopie von | hat Kopie |
| hat Exemplar | ist Exemplar von |
| ist Exemplar von | ist Exemplar |
| dokumentiert | ist dokumentiert von |
| ist dokumentiert von | dokumentiert | 

### Ereignis

| Ausgewählte Verbindung | Gegenstück |
| ------------- | ------------- |
| hat Bezug zu |hat Bezug zu |
| ist Teil von | hat Teil |
| hat Teil | ist Teil von |
| ist ähnlich zu | ist ähnlich zu |

### Akteur:in

| Persönliche Beziehungen ||
| Ausgewählte Verbindung   | Gegenstück |
| ------------- | ------------- |
| ist verwandt mit | ist verwandt mit |
| ist Urgroßmutter von | hat Urgroßmutter |
| hat Urgroßmutter | ist Urgroßmutter von |
| ist Urgroßvater von | hat Urgroßvater |
| hat Urgroßvater | ist Urgroßvater von |
| ist Großmutter von | hat Großmutter |
| hat Großmutter | ist Großmutter von |
| ist Großvater von | hat Großvater |
| hat Großvater | ist Großvater von |
| ist Mutter von  | hat Mutter |
| hat Mutter | ist Mutter von  |
| ist Vater von | hat Vater |
| hat Vater | ist Vater von |
| ist Schwester von | hat Schwester |
| hat Schwester | ist Schwester von |
| ist Bruder von | hat Bruder |
| hat Bruder | ist Bruder von |
| ist Tante von | hat Tante |
| hat Tante | ist Tante von |
| ist Onkel von | hat Onkel |
| hat Onkel | ist Onkel von |
| ist Großtante von | hat Großtante |
| hat Großtante | ist Großtante von |
| ist Großonkel von | hat Großonkel |
| hat Großonkel | ist Großonkel von |
| ist Cousine von | hat Cousine	|
| hat Cousine | ist Cousine von |
| ist Cousin von | hat Cousin |
| hat Cousin | ist Cousin von |
| ist Nichte von | hat Nichte |
| hat Nichte | ist Nichte von |
| ist Neffe von | hat Neffe |
| hat Neffe | ist Neffe von |
| ist Schwägerin von | hat Schwägerin |
| hat Schwägerin | ist Schwägerin von |
| ist Schwager von | hat Schwager |
| hat Schwager | ist Schwager von |
| ist Schwiegermutter von | hat Schwiegermutter |
| hat Schwiegermutter | ist Schwiegermutter von |
| ist Schwiegervater von | hat Schwiegervater |
| hat Schwiegervater | ist Schwiegervater von |
| ist verheiratet mit | ist verheiratet mit |
| ist Lebenspartner:in von | ist Lebenspartner:in von |
| ist Trauzeug:in von | hat Trauzeug:in |
| hat Trauzeug:in | ist Trauzeug:in von |


| Professionelle Beziehungen ||
| Ausgewählte Verbindung   | Gegenstück |
| ------------- | ------------- |
| in Zusammenarbeit mit | in Zusammenarbeit mit |
| ist (Firmen-)Besitzer:in von | hat (Firmen-)Besitzer:in |
| hat (Firmen-)Besitzer:in | ist (Firmen-)Besitzer:in von |
| ist Mitarbeiter:in von | hat Mitarbeiter:in |
| hat Mitarbeiter:in | ist Mitarbeiter:in von |
| ist Assistent:in von | hat Assistent:in |
| hat Assistent:in | ist Assistent:in von |
| ist Direktor:in von | hat Direktor:in |
| hat Direktor:in | ist Direktor:in von |
| ist Gründer:in von | hat Gründer:in |
| hat Gründer:in | ist Gründer:in von |
| ist Lehrer:in von | hat Lehrer:in |
| hat Lehrer:in | ist Lehrer:in von |
| ist künstlerische:r Leiter:in von | hat künstlerische:r Leiter:in |
| hat künstlerische:r Leiter:in | ist künstlerische:r Leiter:in von |
| hat Meisterschüler:in | ist Meisterschüler:in von |
| ist Meisterschüler:in von | hat Meisterschüler:in |
| ist Kolleg:in von | hat Kolleg:in |
| hat Kolleg:in | ist Kolleg:in von |
| ist Mitglied von | hat Mitglied |
| hat Mitglied | ist Mitglied von |
| ist Vorgängerin von | hat Vorgänger:in |
| hat Vorgänger:in | ist Vorgängerin von |
| ist Präsident:in von | hat Präsident:in |
| hat Präsident:in | ist Präsident:in von |
| ist Schriftführer:in von | hat Schriftführer:in |
| hat Schriftführer:in | ist Schriftführer:in von |
| ist Teil von | hat Teil |
| hat Teil | ist Teil von |
| ist zugehörig zu | ist zugehörig zu |

----

## Sammlungen

Über Sammlungen können Zusammengehörigkeiten bei den einliefernden Institutionen erfasst werden, bzw. eine gemeinsame Provenienz. Beispiele: Tonträger aus dem Bandarchiv der HfMT Köln, Fotografien aus dem Fotoarchiv der Folkwang Universität der Künste, Equipment aus dem Technikarchiv der Kunsthochschule für Medien Köln, aber auch Veranstaltungen aus einer Reihe, etc.


<pre class="mermaid">
flowchart LR;
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Projekt
    Projekt-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Ereignis
    Ereignis-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Equipment_Software[Equipment und Software]
    Equipment_Software-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Physisches_Objekt[Physisches Objekt]
    Physisches_Objekt-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Informationsträger
    Informationsträger-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    Sammlung-- <span style="background-color: #f4effc">enthält beliebig viele</span> ---> Digitales_Objekt[Digitales Objekt]
    Digitales_Objekt-- <span style="background-color: #f4effc">kann auftauchen in beliebig vielen</span> --->Sammlung
    style Sammlung fill:#90EE90, stroke:#000000;
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Ereignis fill:#90EE90, stroke:#000000;
</pre>