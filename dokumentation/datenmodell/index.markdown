---
layout: digi-kunst-docs
title: Datenmodell
order: 3.1
---

Das Datenmodell ist in vielfältiger Hinsicht die fachliche wie technische Grundlage für Digi-Kunst.nrw:

* Es bestimmt die Form, nach der wir unsere Daten strukturieren und einheitlich speichern.
* Es zeigt an, wie und welchem Verhältnis (in welcher Kardinalität) die verschiedenen Teile dieses Modells miteinander verknüpft sind.
* Es umfasst Wertelisten und Taxonomien, die den Kern Kern unseres kontrollierten Vokabulars bilden.

Unser Datenmodell ist in einer ständigen Entwicklung, weswegen es von vom gesamten Team kollaborativ gepflegt wird.

----

## Zentrale Entitäten
Um einen besseren Einstieg in unser System zu ermöglichen, soll der Blick zunächst auf die für uns ganz zentralen Bausteine unseres Systems gerichtet werden. Diese Bausteine eines Datenmodells nennen sich Entitäten. Der Begriff leitet sich vom lateinischen Wort für „Ding“ ab. Entitäten bieten dementsprechend jeweils einen Rahmen, dass in ihnen genau eine Art von Ding verzeichnet werden kann. Diese Entitäten haben dann wiederum verschiedene Eigenschaften, sogenannte Attribute.

Die zwei zentralsten Entitäten in unserem System sind **Projekte** und **Ereignisse**.

Ein Projekt ist die zentrale Verzeichnungseinheit von Digi-Kunst.nrw. Es enthält in der Regel die Daten über ein Kunstwerk: ein Musikstück, ein Film, ein Designobjekt, ein Buch, eine digitale Animation, eine Performance, ein Theaterstück oder eine Installation – eben über etwas aus dem gesamten künstlerischen Spektrum. Das Konzept Projekt ist bei uns aber bewusst weiter gefasst und bietet die Möglichkeit, auch andere im Hochschulkontext entstandene Dinge dort zu verzeichnen: das Video eines künstlerischen Vortrags oder ein Dokument zu einer Meisterklasse.

Die zweite zentrale Einheit sind Ereignisse. Ereignisse bilden die historische Entwicklung eines Projekts ab:

* Ereignisse sind von verschiedenster Art. Einem Kunstwerk geht beispielsweise eine geistige Schöpfung voraus, es wird hergestellt, es wird auf Festivals aufgeführt, es wird durch ein Feuer zerstört.
* Ereignisse haben in der Regel ein Beginn und ein Ende.
* Ereignisse finden an bestimmten Orten statt.
* Es wurde von verschiedenen Personen, Gruppen oder Institutionen gemacht und performed, womit bestimmte rechtliche Ansprüche verbunden sind.
* Es wurde verschiedenste Software und Equipment dabei verwendet.
* Bei diesen Ereignissen sind bestimmte physische Objekte entstanden.
* Es ist manifestiert oder dokumentiert in den Dateien, die wir in die Langzeitverfügbarkeit überführen.
* Diese Dateien entspringen einem Informationsträger.

All diese Dinge werden bei uns in einem Ereignis gebündelt. Ein Projekt kann mit beliebig vielen Ereignissen verknüpft sein, dasselbe Ereignis kann in beliebig vielen Projekten auftauchen.

<pre class="mermaid">
flowchart LR;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann mehrere Ereignisse haben</span> -->Ereignis
    Ereignis-- <span style="background-color: #f4effc">Dasselbe Ereignis kann in mehreren Projekten vorkommen</span> -->Projekt
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Ereignis fill:#90EE90, stroke:#000000;
</pre>

Ausgehend von diesen beiden Entitäten lässt sich bereits das vollständige Datenmodell von Digi-Kunst.nrw erläutern.

----

## Projekt: Titel & Alternative Titel

Ein Projekt muss einen bevorzugten Titel und kann – bei Bedarf – einen bevorzugten Untertitel haben. Diese bevorzugten Titel werden prominent in Anzeige und Suche angezeigt und sollten den gewünschten Haupt- und/oder Originaltitel des Projekts wiedergeben. Zudem muss ein bevorzugter Titel eine Sprachauszeichnung erhalten. Der bevorzugte Untertitel benötigt ebenfalls eine Sprachauszeichnung, sofern er angegeben wird. Die Sprachauszeichnungen selber verwenden ein genormtes Sprachenset nach der Norm [ISO639-2](https://www.loc.gov/standards/iso639-2/php/code_list.php).

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


Zusätzlich können noch beliebig viele alternative Titel-Sets angelegt werden. Es ist häufig der Fall, dass gerade Kunstwerke nicht nur unter einem Namen bekannt sind oder geführt werden, sondern im Laufe ihrer Historie oft mehrere Titel haben. Im Besonderen ist dies auch notwendig, wenn der Originaltitel nicht in latinisierten Buchstaben geschrieben ist, sondern beispielsweise in kyrillischer Schrift oder chinesischen Zeichen. In einem alternativen Titel-Set kann auch bloß ein alternativer Untertitel samt Sprachauszeichnung angegeben werden. Ein alternatives Titel-Set ist allerdings nur dann valide, wenn es mindestens einen alternativen Titel oder alternativen Untertitel samt seiner Sprachauszeichnung enthält.

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann mehrere alternative Titel-Sets haben\n Das Set muss entweder einen alternativen Titel oder Untertitel haben</span> --> Alternatives_Titel-Set[Alternatives Titel-Set]
    Alternatives_Titel-Set-- <span style="background-color: #f4effc">hat bei Bedarf</span>  --> Alternativer_Titel[Alternativer Titel]
    Alternatives_Titel-Set-- <span style="background-color: #f4effc">hat bei Bedarf</span>  --> Alternativer_Untertitel[Alternativer Untertitel]
    Alternativer_Titel-- <span style="background-color: #f4effc">hat</span>  --> Sprachauszeichnung
    Alternativer_Untertitel-- <span style="background-color: #f4effc">hat</span> --> Sprachauszeichnung
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Alternatives_Titel-Set fill:#FFFFE0, stroke:#000000;
    style Alternativer_Titel fill:#FFFFE0, stroke:#000000;
    style Alternativer_Untertitel fill:#FFFFE0, stroke:#000000;
</pre>

----

## Projekt: Beschreibungen & Kommentare

Ein Projekt kann mehrere Beschreibungen haben. Damit es später jedoch in die Langzeitverfügbarkeit überführt werden kann, muss mindestens eine Beschreibung vor diesem Export vorhanden sein. Deswegen ist das Feld „Beschreibung“ in unserer Datenmodell-Tabelle mit der Kardinalität „1-u[nendlich]“ gekennzeichnet. Die Beschreibung ist meistens ein von dem/der Autor:in des Werkes verfasster Text, kann aber auch von jemandem Dritten verfasst worden sein. Ähnlich wie Titel haben Beschreibungen eine Sprachauszeichnung. Beschreibungen können nach Belieben innerhalb eines Projekts sortiert werden.

<pre class="mermaid">
flowchart TB;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt kann mehrere Berschreibungen haben \n Zum Export benötigt es mindestens eine</span>  -->Beschreibung
    Beschreibung-- <span style="background-color: #f4effc">hat</span> --> Sprachauszeichnung
    Beschreibung-- <span style="background-color: #f4effc">hat</span> --> Sortierungsnummer
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Beschreibung fill:#FFFFE0, stroke:#000000;
</pre>

Ebenso ist es möglich, einen Kommentar zum Projekt anzugeben. Wenn der deutsche Kommentar verwendet wurde, muss auch eine Übersetzung auf Englisch angegeben werden – und umgekehrt.

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

## Projekt: Projaktarten, Projektkategorien und Schlagwörter

Die Kategorisierung und die Verschlagwortung eines Projekts sind wesentliche Teile der sogenannten Sacherschließung. Diese ermöglicht es, dass auch in Zukunft die bei uns gespeicherten Projekte wiedergefunden werden können.

Ein Projekt muss zu mindestens einer Projektart gehören, kann aber auch zu mehreren Projektarten zugewiesen werden. Die Projektart gibt an, um was es sich bei einem Projekt in einem akademischen oder administrativen Sinn handelt. Eine erste Auswahl gibt die folgende Liste, sie kann aber bei Bedarf im Erfassungsbackend erweitert werden.

<pre class="mermaid">
flowchart LR;
    Projekt-- <span style="background-color: #f4effc">Ein Projekt muss zu einer Projektart gehören\n Es kann bei Bedarf mehreren zugewiesen werden </span>  -->Projektart
    Projektart-- <span style="background-color: #f4effc">Die selbe Projektart kann beliebig viele Projekte erfassen</span> --> Projekt
    style Projekt fill:#FFFFE0, stroke:#000000;
    style Projektart fill:#FFFFE0, stroke:#000000;
</pre>

| Deutscher Name der Projektart | Englischer Name der Projektart | Wikidata-Link |
| ------------- | ------------- | ------------- |
| Bachelorarbeit | Bachelor Thesis | [https://www.wikidata.org/entity/Q798134](https://www.wikidata.org/entity/Q798134) |
| Diplomprojekt | Diploma Project | [https://www.wikidata.org/entity/Q30749496](https://www.wikidata.org/entity/Q30749496) |
| Forschungsprojekt | Research Project | [https://www.wikidata.org/entity/Q1298668](https://www.wikidata.org/entity/Q1298668) |
| Autonomes Projekt | Autonomous Project | [https://www.wikidata.org/entity/Q124535359](https://www.wikidata.org/entity/Q124535359) |
| Masterarbeit | Master Thesis | [https://www.wikidata.org/entity/Q1907875](https://www.wikidata.org/entity/Q1907875) |
| Projekt 1 (KHM) | Project 1 (KHM) | [https://www.wikidata.org/entity/Q123692929](https://www.wikidata.org/entity/Q123692929) |
| Projekt 2 (KHM) | Project 2 (KHM) | [https://www.wikidata.org/entity/Q123692947](https://www.wikidata.org/entity/Q123692947) |
| Sammlungsobjekt | Collection Item | [https://www.wikidata.org/entity/Q106815942](https://www.wikidata.org/entity/Q106815942) |
| Studentisches Projekt | Student Project | [https://www.wikidata.org/entity/Q30032131](https://www.wikidata.org/entity/Q30032131) |
| Veranstaltung	| Event | [https://www.wikidata.org/entity/Q1656682](https://www.wikidata.org/entity/Q1656682) |
| Vordiplom | Vordiplom | [https://www.wikidata.org/entity/Q1227202](https://www.wikidata.org/entity/Q1656682) |

Projektkategorien geben die Kunstgattung, das Gebiet oder das Genre eines Projekts an. Dafür verwenden wir keine einfache Liste, sondern eine sogenannte Taxonomie (griechisch für „Ordnung“), in der die Kategorien stets in einem gewissen Kontext abgebildet werden. Am besten lässt sich das an einem Beispiel erklären. Für ein Projekt wurde die Projektkategorie „Industrial Design“ vergeben. In unserem System taucht diese Projektkategorie dann wie folgt auf:

<a href="/assets/images/Beispiel_Breadcrumb_Projektkategorien.png"><img src="/assets/images/Beispiel_Breadcrumb_Projektkategorien.png" class="center-image" style="width: 400px;"/></a>

Alle drei Kategorisierungen werden dann zu dem entsprechenden Projekt gespeichert. Man kann dieses dann also auch unter dem Begriff "Angewandte Kunst" wiederfinden. Zsätzlich sind die Kategorien mit Synonymen angereichert, sodass eine noch bessere Auffindbarkeit gewährleistet wird. 

Es können beliebig viele Kategorien zu einem Projekt vergeben werden, sodass auch Projekte beschrieben werden können, die in mehr als eine Kategorie fallen. Einen Überblick, mit welchen Digi-Kunst.nrw gestartet ist, lässt sich in unserem [Projektkategorien-Grundset](projektkategorien-grundset) finden. 

Jede Projektkategorie enthält mindestens auch noch den Link zu einem Begriff des kontrollierten Vokabulars der [Wikidata](https://www.wikidata.org/w/index.php?title=Wikidata:Main_Page&uselang=de). „Kontrolliert“ wird ein Vokabular dann genannt, wenn für eine Sache (ein Konzept) jeweils nur ein einziger Eintrag existiert; es also keine „Teekesselchen“ gibt, die für Unklarheiten in einem System sorgen könnten. Außerdem ist die Kategorie damit besser im Internet identifizierbar und austauschfähig. Oft enthält eine Projektkategorie ein ganzes Set von Links zu großen kontrollierten Vokabularen: dem Vokabular der Deutschen Nationalbibliothek, dem Vokabular des Getty Art & Architecture Thesaurus und dem Vokabular des Filmportals.de.

Die Schlagwörter, mit denen Digi-Kunst.nrw arbeitet, stammen aus der [Wikidata](https://www.wikidata.org/w/index.php?title=Wikidata:Main_Page&uselang=de). Die Informationen können direkt von dort aus nach Digi-Kunst.nrw importiert werden. Diese Methode hat den Vorteil, dass das Schlagwortvokabular von Digi-Kust.nrw stetig erweitert und verbessert werden kann. Damit ein Schlagwort allerdings in unser System geladen werden kann, benötigt es mindestens einen deutschen und englischen Eintrag mit zugehöriger Beschreibung auf der Wikidata. Ebenso werden – falls sie vorhanden sind – Synonyme, die auf der Wikidata stehen, ebenfalls mitgeladen, um die weiter die Auffindbarkeit der Projekte zu gewährleisten.

<a href="/assets/images/schlagwort_auslesen.png"><img src="/assets/images/schlagwort_auslesen.png" class="center-image" style="margin-top: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>
<a href="/assets/images/ausgelesenes_schlagwort.png"><img src="/assets/images/ausgelesenes_schlagwort.png" class="center-image" style="margin-bottom: 8%; border: 1px solid black;"/></a>

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


Abgesehen von diesem rechtlichen Rahmen kann angegeben werden, aus welcher Organisationseinheit innerhalb der Hochschule ein Projekt stammt: das kann beispielsweise ein Studiengang sein, ein Forschungsinstitut oder zum Beispiel ein Archiv.

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

## Projekt: Identifikatoren und Normdaten

Ein Projekt bekommt automatisch eine Digi-Kunst-ID. Diese setzt sich zusammen aus:

* Der Kennzeichnung „Digi-Kunst“
* Einer automatischen Nummer, die zählt, das wievielte Projekt es insgesamt in unserem System ist
* Einem dreistelligen Identifikator für die einliefernde Hochschule: **FUK** für die Folkwang Universität der Künste, **DET** für die Hochschule für Musik Detmold, **HMT** für die Hochschule für Musik und Tanz Köln, **KHM** für die Kunsthochschule für Medien Köln und **RSH** für die Robert Schumann Hochschule Düsseldorf.
* Einer weiteren automatischen Nummer, die zählt, das wievielte Projekt von der entsprechenden Hochschule in unserem System ist.

Eine vollständige Signatur könnte also wie folgt aussehen: **Digi-Kunst-9876-KHM-5432**.

Des Weiteren können auch weitere Signaturen beim Einlieferer bei uns eingetragen werden, ebenso wie Werkverzeichnisnumern.

Zusätzlich können zu einem Projekt auch beliebig viele Normdaten-Links angegeben werden. Das sind Verweise auf Datensätze, in denen das Projekt genormt beschrieben wird, wie hier z. B. Karlheinz Stockhausens „Gesang der Jünglinge“: [https://d-nb.info/gnd/300322518](https://d-nb.info/gnd/300322518).

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

## Projekt: Fachspezifische Angaben und Inhaltwarnungen

Je nach Fachrichtung, können fachspezifische Angaben gemacht werden, etwa die Tonart eines Musikstücks oder die Dauer eines Films. Über eine eigene Entität können diese fachspezifischen Felder angelegt werden. Ein Projekt kann beliebig viele fachspezifischen Angaben haben, die Angaben sind auf alle Projekte anwendbar.

Zudem kann zu dem Projekt eine projektspezifische Inhaltswarnung gegeben werden, bereits vorangelegte Inhaltswarnungen können in anderen Projekten immer wieder verwendung finden.

----

## Projekt: Nutzungsrechtangaben

Damit eine einliefernde Hochschule ein Projekt in die Langzeitverfügbarkeit überführen, es öffentlich zugänglich machen und es gegebenenfalls an andere Portale für Kultur und Wissen weitergeben kann, benötigt sie in der Regel bestimmte Nutzungsrechte von den Urheber:innen und Leistungsschutzrechtsinhaber:innen. 

Digi-Kunst.nrw erfasst dafür zunächst bestimmte Rechte für das Projekt. Das kann auf zweierlei Arten passieren:

* Zum einen kann bereits ein Nutzungsvertrag zwischen den Rechteinhaber:innen und der Hochschule bestehen, mit welchem bereits verschiedene Erhaltungsschritte erlaubt sind. Zum Beispiel kann es sein, dass die Archivierung eines Projekts bereits Bestandteil einer vorherigen Vereinbarung war. In diesen Fällen ist zu klären, ob Digi-Kunst.nrw bereits verschiedene Arbeitsschritte ausführen darf, beispielsweise die Projekte zu verzeichnen und die Dateien in die Langzeitverfügbarkeit zu überführen.
* Zum anderen kann über Digi-Kunst.nrw ein neuer Lizenzvertrag geschlossen werden, falls noch keiner vorliegt oder der bereits bestehende Lizenzvertrag erweitert werden soll. Digi-Kunst.nrw stellt dafür eine speziell für diesen Zweck erstellte Modularlizenz zur Verfügung. Details hierzu finden sich auf der Seite [**Lizenzen**](/ressourcen/lizenzen/).

<pre class="mermaid">
flowchart TB;
    Projekt_Urheberrechtsstatus{Ist das Projekt urheberrechtlich\n und/oder leistungsschutzrechtlich geschützt?}-- <span style="background-color: #f4effc">nein</span>  --> Projekt_eingeliefert[Das Projekt kann ohne Lizenzvereinbarung\n bei Digi-Kunst.nrw eingeliefert werden]
    Projekt_Urheberrechtsstatus-- <span style="background-color: #f4effc">ja</span>  ---> Lizenzvertrag_benötigt[Es wird eine Lizenzvereinbarung benötigt]
    Lizenzvertrag_benötigt --> Besteht_Lizenzvertrag{Besteht bereits ein Lizenzvertrag zwischen\n der Hochschule und dem/der Lizenzgeber:in?}
    Besteht_Lizenzvertrag-- <span style="background-color: #f4effc">ja</span>  --> Rechte_werden_geprüft[Es wird geprüft, welche Erhaltungsschritte\n bei Digi-Kunst.nrw bereits durchgeführt werden können]
    Besteht_Lizenzvertrag-- <span style="background-color: #f4effc">nein</span>  --> Neuer_Lizenzvertrag[Es kann ein neuer Lizenzvertrag via Digi-Kunst.nrw geschlossen werden]
    Rechte_werden_geprüft-- <span style="background-color: #f4effc">zusätzlich</span>  --> Neuer_Lizenzvertrag[Es kann ein neuer Lizenzvertrag via Digi-Kunst.nrw geschlossen werden]
</pre>

Außerdem gibt es noch einige Sonderfälle, die im Einzelfall geprüft werden müssen. So kann es sein, dass ein Werk verwaist seien kann, es also auch nach vorheriger Recherche nicht mehr seinen zugehörigen Urheber:innen zugeordnet werden kann. In diesem Fall würde z. B. eine europäische Sonderregelung gelten, bei der die zugehörigen Dateien öffentlich zugänglich gemacht werden könnten.

----

## Ereignis: Ereignistypen

Ereignisse können ebenso kategorisiert werden wie Projekte. Ein Ereignis kann ein Ankauf sein, eine musikalische Komposition, eine Ursendung oder ein Rundgang. Ein Ereignis muss daher eine Zuordnung haben, zu welchem Ereigsnistyp es gehört. Eine Übersicht über die Ereignistypen, die den Grundstock von Digi-Kunst.nrw bilden, finden Sie in unserem [**Ereignistypen-Grundset**](ereignistypen-grundset). Ein Ereignistyp hat mindestens einen Wikidata-Link und kann zusätzlich einen GND-Link, einen AAT-Link und einen Link zu einem Ereignis aus der LIDO-Terminologie haben.

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
Ein Ereignis kann an mehreren Orten stattgefunden haben. Orte laden wir, ebenso wie Schlagwörter, aus der Wikidata. Bei Orten wird aber im Hintergrund eine komplexere Abfrage gestellt, die mit der Abfragesprache SPARQL ausgeführt wird. SPARQL-Anfragen werden im Grunde wie Sätze formuliert: Finde alle „Orte“ „die übergeordnet sind“ „zum eingegebenen Ort“. Unsere Ort-Abfrage ist somit in der Lage, einen eingegebenen Ort direkt in seinen geografischen Kontext zu setzen. Es muss nur die Wikidata-ID eingegeben werden und das System übernimmt diese Einordnung. Bei uns werden Orte auf 6 Ebenen erfasst. Diese sind: **Kontinent** > **Land** > **Staat/Region/Bundesland** > **Stadt** > **Genauer Ort** > **Interner Ort**.

<a href="/assets/images/wikidata_ort.png"><img src="/assets/images/wikidata_ort.png" class="center-image" style="margin-top: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>

<a href="/assets/images/adm_ort_importieren.png"><img src="/assets/images/adm_ort_importieren.png" class="center-image-small" style="margin-bottom: 8%;"/></a>

<a href="/assets/images/adm_ort_angelegt.png"><img src="/assets/images/adm_ort_angelegt.png" class="center-image" style="margin-bottom: 8%; margin-bottom: 8%; border: 1px solid black;"/></a>

----

## Ereignis: Akteur:innen, Rollen und Rechteangaben

Einem Ereignis können alle beteiligten Akteur:innen zugewiesen werden. Derselbe/dieselbe Akteur:in kann in allen benötigten Ereignissen vorkommen. Akteur:innen sind Personen, Gruppen oder Körperschaften. Akteur:innen können innerhalb des Digi-Kunst.nrw-Erfassungsbackends angelegt werden. Eine Übersicht, welche angaben dazu innerhalb des Systems gemacht werden können, findet sich in der folgenden Tabelle.

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
| Kontakt (E-Mail) | Contact (E-Mail) | 0-u | Ein oder mehrere mögliche Kontaktemails. Diese werden gelöscht, wenn sie nicht mehr benötigt werden |
| Kontakt (Telefon) | Contact (Phone) | 0-u | Ein oder mehrere mögliche Telefonkontakte. Diese werden gelöscht, wenn sie nicht mehr benötigt werden |
| Kontakt (Postanschrift) | Contact (Postal Address) | 0-1 | Eine mögliche Postanschrift. Diese wird gelöscht, wenn sie nicht mehr benötigt wird |

Innerhalb eines Projekts kann ein/eine Akteur:in mehrere Rollen haben. Dieselbe Rolle kann auf unterschiedliche Akteur:innen angewendet werden. Rollen stammen bei uns aus einer eigenen Entität. Eine Rolle hat einen deutschen und einen englischen Namen und einen Wikidata-Link. Zusätzlich können Rollen auch einen rollenspezifischen „Gemeinsame Normdatei“-Link und einen „Getty Art and Architecture Thesaurus“-Link haben. Zur besseren Auffindbarkeit von Akteur:innen kann eine Rolle auch noch mit deutschen und englischen Synonymen angereichert werden. Eine Übersicht, mit welchen Rollen Digi-Kunst.nrw gestartet ist, finden sie in unserem [**Rollen-Grundset**](/dokumentation/datenmodell/rollen-grundset).

<pre class="mermaid">
flowchart TB;
    AkteurIn[Akteur:in]-- <span style="background-color: #f4effc">hat ein oder mehrere</span> ---> Rolle
    Rolle-- <span style="background-color: #f4effc">im</span> ---> Ereignis
    style Ereignis fill:#90EE90, stroke:#000000;
    style AkteurIn fill:#F0F8FF, stroke:#000000;
</pre>

Ganz speziell in der Entität Rolle sind die beiden Felder „steuert 'ist Urheberin'“ und „steuert 'besitzt Leistungsschutzrechte'“. Das sind zwei Felder, die wir, ebenso zwischen Akteur:in und Ereignis finden können. Ein/eine Akteur:in in in einem Ereignis Urheber:in sein, im nächsten nicht, in einem anderen kann der/die Akteur:in Leistungsschutzrechte besitzen, im anderen nicht. Diese Information wird hier auch erfasst. Eine Rolle ist nun in der Lage, dass sie eine Vorauswahl treffen kann, wenn ein/eine Akteur:in mit einem Ereignis verbunden wird. Ist der/die besagte Akteur:in beispielsweise „Komponist:in“ in einem Ereignis, dann ist sie mit großer Wahrscheinlichkeit auch „Urheber:in“ des bei uns gespeicherten Projekts. Letztlich bestimmt muss aber die eingebende Person bestimmen, ob diese Eingabe wirklich korrekt ist oder nicht. Außerdem kann angegeben werden, ob nur vermutet wird, das ein/eine Akteur:in in einem Ereignis mitgewirkt hat. Für diesen Fall gibt es das Feld „Ungesicherte Zuschreibung“.

----

## Ereignis: Equipment & Software

In einem Ereignis kann verschiedenes Equipment & Software zum Einsatz kommen. Ein Equipment-Teil und eine Software kann in vielen Ereignissen vorkommen. Equipment ist von verschiedener Art. Einen Beispielfundus an Equipmentarten findet man wie folgt in unserem Datenmodell.


[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2024-05-equipmentarten-grundset.xlsx](/assets/documents/2024-05-equipmentarten-grundset.xlsx) (13,5 KB)  
[<svg class="download-icon" xmlns="http://www.w3.org/2000/svg" height="24" viewBox="0 -960 960 960" width="24"><path d="M480-320 280-520l56-58 104 104v-326h80v326l104-104 56 58-200 200ZM240-160q-33 0-56.5-23.5T160-240v-120h80v120h480v-120h80v120q0 33-23.5 56.5T720-160H240Z"/></svg> 2024-05-equipmentarten-grundset.pdf](/assets/documents/2024-05-equipmentarten-grundset.pdf) (59 KB)

| Deutscher Name der Equipmentart | Englischer Name der Equipmentart | Wikidata-Link | GND-Link | AAT-Link |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| 3D-Drucker | 3D-Printer | [https://www.wikidata.org/entity/Q3834994](https://www.wikidata.org/entity/Q3834994) | [https://d-nb.info/gnd/1051019354](https://d-nb.info/gnd/1051019354) | [https://vocab.getty.edu/aat/300391466](https://vocab.getty.edu/aat/300391466) |
| 3D-Scanner | 3D Scanner | [https://www.wikidata.org/entity/Q1775257](https://www.wikidata.org/entity/Q1775257) |[https://d-nb.info/gnd/7704418-6](https://d-nb.info/gnd/7704418-6) | |
| Abtastnadel | Phonograph Needle | [https://www.wikidata.org/entity/Q10923110](https://www.wikidata.org/entity/Q10923110) | | [https://vocab.getty.edu/aat/300374973](https://vocab.getty.edu/aat/300374973) |
| Archéophone | Archéophone | [https://www.wikidata.org/entity/Q2860627](https://www.wikidata.org/entity/Q2860627) | | |
| Beamer | Video Projector | [https://www.wikidata.org/entity/Q275568](https://www.wikidata.org/entity/Q275568) |[https://d-nb.info/gnd/4726555-3](https://d-nb.info/gnd/4726555-3) | |	
| Drucker | Printer | [https://www.wikidata.org/entity/Q82](https://www.wikidata.org/entity/Q82) | [https://d-nb.info/gnd/4013091-5](https://d-nb.info/gnd/4013091-5) | [https://vocab.getty.edu/aat/300024535](https://vocab.getty.edu/aat/300024535) |
| Flachbildscanner | Flatbed Scanner | [https://www.wikidata.org/entity/Q82744](https://www.wikidata.org/entity/Q82744) | | |
| Fotokamera | Photographic Camera | [https://www.wikidata.org/entity/Q15328](https://www.wikidata.org/entity/Q15328) | [https://d-nb.info/gnd/4045869-6](https://d-nb.info/gnd/4045869-6) | [https://vocab.getty.edu/aat/300022636](https://vocab.getty.edu/aat/300022636) |
| Fräse | Milling Machine | [https://www.wikidata.org/entity/Q623106](https://www.wikidata.org/entity/Q623106) | | [https://vocab.getty.edu/aat/300024721](https://vocab.getty.edu/aat/300024721) |
| Lautsprecher | Loudspeaker | [https://www.wikidata.org/entity/Q570](https://www.wikidata.org/entity/Q570) | |[https://vocab.getty.edu/aat/300250653](https://vocab.getty.edu/aat/300250653)
| Mikrofon | Microphone | [https://www.wikidata.org/entity/Q46384](https://www.wikidata.org/entity/Q46384) | [https://d-nb.info/gnd/4139330-2](https://d-nb.info/gnd/4139330-2) | [https://vocab.getty.edu/aat/300266322](https://vocab.getty.edu/aat/300266322) |
| Mischpult | Mixer | [https://www.wikidata.org/entity/Q654117](https://www.wikidata.org/entity/Q654117) | [https://d-nb.info/gnd/4039545-5](https://d-nb.info/gnd/4039545-5) | [https://vocab.getty.edu/aat/300420468](https://vocab.getty.edu/aat/300420468) |
| Musikinstrument | Musical Instrument | [https://www.wikidata.org/entity/Q34379](https://www.wikidata.org/entity/Q34379) | [https://d-nb.info/gnd/4040851-6](https://d-nb.info/gnd/4040851-6) |  [https://vocab.getty.edu/aat/300041620](https://vocab.getty.edu/aat/300041620) |
| Plug-In | Plug-In | [https://www.wikidata.org/entity/Q184148](https://www.wikidata.org/entity/Q184148) | [https://d-nb.info/gnd/4753748-6](https://d-nb.info/gnd/4753748-6) | |
| Samplebibliothek | Sample Library | [https://www.wikidata.org/entity/Q7410139](https://www.wikidata.org/entity/Q7410139) | | |
| Schallplattenspieler | Record Player | [https://www.wikidata.org/entity/Q17591720](https://www.wikidata.org/entity/Q17591720) | [https://d-nb.info/gnd/4174890-6](https://d-nb.info/gnd/4174890-6) | [https://vocab.getty.edu/aat/300310108](https://vocab.getty.edu/aat/300310108) |
| Server | Server | [https://www.wikidata.org/entity/Q44127](https://www.wikidata.org/entity/Q44127) | [https://d-nb.info/gnd/4209324-7](https://d-nb.info/gnd/4209324-7) | [https://vocab.getty.edu/aat/300266043](https://vocab.getty.edu/aat/300266043) |
| Software | Software | [https://www.wikidata.org/entity/Q7397](https://www.wikidata.org/entity/Q7397) | [https://d-nb.info/gnd/4055382-6](https://d-nb.info/gnd/4055382-6) | [https://vocab.getty.edu/aat/300028566](https://vocab.getty.edu/aat/300028566) |
| Tonabnehmer | Pickup | [https://www.wikidata.org/entity/Q572648](https://www.wikidata.org/entity/Q572648) | [https://d-nb.info/gnd/4185653-3](https://d-nb.info/gnd/4185653-3) | [https://vocab.getty.edu/aat/300421687](https://vocab.getty.edu/aat/300421687) |
| Videokamera | Video Camera | [https://www.wikidata.org/entity/Q313614](https://www.wikidata.org/entity/Q313614) | [https://d-nb.info/gnd/4136080-1](https://d-nb.info/gnd/4136080-1) | [https://vocab.getty.edu/aat/300263898](https://vocab.getty.edu/aat/300263898) |
| Vorstufe | Preamp | [https://www.wikidata.org/entity/Q399804](https://www.wikidata.org/entity/Q399804) | [https://d-nb.info/gnd/4454584-8](https://d-nb.info/gnd/4454584-8) | |
| VR-Headset | VR Headset | [https://www.wikidata.org/entity/Q19600329](https://www.wikidata.org/entity/Q19600329) | | |
| Wandler | Transducer | [https://www.wikidata.org/entity/Q215928](https://www.wikidata.org/entity/Q215928) | [https://d-nb.info/gnd/4064541-1](https://d-nb.info/gnd/4064541-1) | [https://vocab.getty.edu/aat/300264909](https://vocab.getty.edu/aat/300264909) |

----

## Ereignis: Physische Objekte

Nicht alle Projekte, die wir in unserem System erfassen, sind in ihrem Ursprung ganz oder teilweise “born digital”. “Born digital” werden digitale Repräsentation eines Kunstwerk oder einer Dokumentation dann bezeichnet, wenn innerhalb der Herstellung eines Kunstwerks oder einer Dokumentation das Geschehene entweder direkt aufgezeichnet oder gleich auf einem Computer, einem Tablet, einem mobilen Telefon oder Smartphone hergestellt wird.

In einem Ereignis können beliebig viele physische Objekte beschrieben werden. Dasselbe physische Objekt kann in vielen Projekten vorkommen.

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
|Deutsche Bezeichnung | German Name | 1 | Automatisch der englische Name, wenn nur dieser angegeben wurde |
| Englische Bezeichnung	| English Name | 1 | Automatisch der englische Name, wenn nur dieser angegeben wurde |
| Externe Inventar-Signaturnummer | External Inventory Number | 0-u | Bei Bedarf eine oder mehrere Signaturen |
| Aufbewahrungsort | Depository | 0-1 | Bei Bedarf ein Ort aus der Orte-Entität |
| Besitzer:in | Owner | 0-u | Bei Bedarf ein oder mehrere Akteur:innen aus der Akteur:in-Entität |
| Eigentümer:in | Legal Rights Holder | 0-u | Bei Bedarf ein oder mehrere Akteur:innen aus der Akteur:in-Entität |
| Provenienz | Provenance | 0-1 | Ein Freitextfeld zur Provenienzbeschreibung |
| Deutsche Beschreibung | German Description | 0-1 | Eine Beschreibung im Freitext. Pflicht, wenn die englische Beschreibung angegeben wurde |
| Englische Beschreibung | English Description | [1] | Eine Beschreibung im Freitext. Pflicht, wenn die deutsche Beschreibung angegeben wurde |
| Deutscher Kommentar | German Commentary | 0-1 | Ein deutscher Kommentar. Pflicht, wenn der englische Kommentar angegeben wurde |
| Englischer Kommentar |English Commentary | [1] | Ein deutscher Kommentar. Pflicht, wenn der deutsche Kommentar angegeben wurde |
| Klassifizierendes Schlagwort | Classification Keyword to Physical Object | 0-u | Ein oder mehrere Schlagworte aus der Schlagwort-Entität |
| Materialschlagwort | Material Keyword | 0-u | Ein oder mehrere Schlagworte aus einer separaten Entität, die Schlagworte aus der Wikidata lädt |
| Maße	| Measurements | 0-1 | Ein Freitextfeld, in das Maße eingetragen werden können |		
| Erhaltungszustand (deutsch) | Conservation State (German) | 0-1 | Eine deutsche Beschreibung des Erhaltungszustand des Objekts. Pflicht, wenn das entsprechende englische Feld benutzt wurde |
| Erhaltungszustand (englisch) | Conservation State (English) | [1] | Eine englische Beschreibung des Erhaltungszustand des Objekts. Pflicht, wenn das entsprechende deutsche Feld benutzt wurde |

----

## Ereignis: Informationsträger

Informationsträger sind eine besondere Form von physischen Objekten, weswegen wir sie auch eigenständig führen. Dabei handelt es sich um die Trägermedien, die Grundlage oder Speicher für die bei uns gesichertenen Informationen oder Dateien sind. Das kann z. B. sein: eine Schallplatte, eine Diskette, eine Festplatte oder ähnliches. Wir nennen diese Eigenschaft, zu welcher Art ein Informationsträger gehört, Informationsträgertyp. Die [**Taxonomie der Informationsträgertypen**](/dokumentation/datenmodell/informationstraegertypen-grundset) kann bei Bedarf im Erfassungsportal erweitert werden. Neben den Felder, die auch das Physische Objekt besitzt, können bei einem Informationsträger die folgenden Informationen eingegeben werden:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| Deutsche (Produkt-) Bezeichnung | German (Product-) Name | 0-1 | Der deutsche Name des Informationsträgers |
| Englische (Produkt-) Bezeichnung | English (Product-) Name | 0-1 | Der englische Name des Informationsträgers |			
| Label (Handelsmarke) | Label | 0-1 | Eine Handelsmarke |									
| Informationsträgertyp	| Information Storage Media Type | 1 | Eine Auswahl aus der Informationsträgertyp-Taxonomie |
| Produkt-ID-Typ | Product ID Type | 0-u | Eine Auswahl aus der Entität "Nummernart". Z. B. "Bestellnummer", "ISBN", "Seriennummer" oder "Matritzennummer" |
| Produkt-ID-Wert | Product ID Value | [1] | Zu jeder Auswahl ein dazugehöriger Wert |
| Externe Inventar-Signaturnummer | External Inventory Number | 1-u | Eine Pflichtangabe, die den Informationsträger beim Einlieferer identifiziert. Bei Bedarf können es auch mehrere Nummern sein | 
| Aufbewahrungsort | Depository | 0-1 | Ein Ort aus der Orte-Entität. Der derzeitige oder letztbekannte Aufbewahrungsort |
| Informationsträgereigenschaft | Information Storage Medium Property | 0-u | Eine Auswahl aus der Entität "Informationsträgereigenschaft". Z. B. "Bildfrequenz" oder "Abspielgeschwindigkeit" |									
| Informationsträgereigenschaft-Wert | Information Storage Medium Property Value | [1] | Zu jeder Auswahl ein dazugehöriger Wert |
| Normdatei | Authority File | 0-u | Ein zugehöriger Normdatenlink zum Informationsträger |								
| Kompilation | Compilation | 0/1 | Eine Angabe, ob der Informationsträger mehrere Projekte enthält. Entweder "ja", "nein" oder "keine Aussage" |
| Kompilationstitel | Compilation Title | [0-1] | Der Name dieser Kompilation |
| Kompilations-Reihennummer | Compilation Series Number | [0-1] | Die entsprechende Reihennummer |									
| Originalsprache | Original Language | 0-u | Eine oder mehrere ISO 639-Sprachen |
| Sprachfassung | Language Version | 0-u | Eine oder mehrere ISO 639-Sprachen  |
| Untertitelsprache | Subtitle Language | 0-u | Eine oder mehrere ISO 639-Sprachen  |	

----

## Ereignis: Digitale Objekte

Digi-Kunst.nrw definiert ein Digitales Objekt als eine Datei sowie ihre zugehörige inhaltliche Beschreibung und ihre technischen Metadaten. Ein Ereignis kann beliebig viele Digitale Objekte enthalten, ein Digitales Objekt kann in beliebig vielen Ereignissen auftauchen. Bereits beim Upload werden zentrale Metadaten zur Datei gleich erfasst:

  * **Wie ist die Datei entstanden?** Ist sie "born digital" oder ein Retrodigitalisat, also erst später digitalisiert worden?
  * **Zu welchem Medientyp gehört die Datei?** 3D, Audio, Bild, Code, Text oder Video?
  * **Optional: Was ist ein Schlagwort, das den Inhalt der Datei beschreibt?** Was für ein Objekt ist in der Datei abgebildet: ein Poster, ein Trailer, ein Musikkanal?
  * **Handelt es sich bei der Datei um ein Dateipaket oder nicht?**
  * **Bei Code: Welche Systemvorraussetzungen sind notwendig, damit das Programm ausgeführt werden kann?**
  * **Worum handelt es sich bei der Datei in einem langzeitarchivarischen Sinn?** Um einen "Preservation Master" (ein Original oder eine nach bestimmten Richtlinien hergestellte Kopie), um einen "Modified Master" (meist eine bereits langzeitstabile Kopie, von der besser Abzüge gemacht werden können) oder um eine "Derivative Copy" (um ein Nutzerformat, dass keinen archivarischen Zweck erfüllt)?
  * **Die wievielte Nutzerkopie dieser Datei ist es?**
  * **Welchen Urheberrechts- und Lizenzstatus hat die Datei?** Neben unseren eigenen Lizenzen können auf die Dateien auch die Lizenzen von Creative Commons vergeben werden. Weiter Informationen zu den Auswahlmöglichkeiten erhalten sie auf der Seite [**Lizenzen**](/ressourcen/lizenzen/)
  * **Soll die Datei öffentlich angezeigt werden oder nicht?**
  * Zudem wird **automatisch ausgelesen, wie groß die Datei ist, zu welchem Dateityp sie gehört und wann sie zuletzt verändert wurde**.

Entsprechend sind die Plichtangaben um ein Digitales Objekt in das System hochladen zu können, sind bereits mit der Beantwortung dieser Fragen erfüllt. Die zugehörigen Spezifikationen lauten wie folgt:

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
| Objekttyp | Object Type | 0-1 | Ein Schlagwort aus der wikidata. Z. B. "Poster", "Trailer" oder "Kanal" |
| Dateipaket | File Package | 0/1 | Entweder keine Auswahl oder "ja" |
| Systemvoraussetzungen	| System Requirements | [1 für "Code"] | Pflicht wenn für eine Datei der Medientyp "Code" ausgewählt wurde |
| Erhaltungstyp | Preservation Type | 1 | Entweder "Preservation Master", "Modified Master" oder "Derivative Copy (Nutzerformat)" |
| Derivatkopie-Nummer | Derivative Copy Number | [1 wenn "Derivative Copy (Nutzerformat)] | Bei einer Nutzerkopie muss angegeben werden, um die viewielte Kopie es sich von einer Master-Datei handelt. |		
| Lizenzstatus | License State | 1 | Der Lizenzstatus einer Datei aus der Entität "Digitales-Objekt-Lizenz". Einer Lizenz ist auch immer ein Urheberrechtsstatus zugeordnet | 
| Anzeigestatus	| Display State | 1 | Ein Status der regelt, ob die Datei ohne vorherige Anmeldung später frei angezeigt werden wird |
| KHM-Internetfreigabestufe | KHM Internet Clearance Level | 0-1 | Ein Sonderfeld für KHM-Dateien, ob die entsprechende Datei bereits schon auf der Seite des KHM-Archivs öffentlich angezeigt wird oder nicht |

Neben diesen Pflichangaben gibt es noch eine Reihe von deskriptiven Feldern, die optional verwendet werden können, dazu gehören:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| Deutsche inhaltliche Beschreibung | German Description | 0-1 | |
| Englische inhaltliche Beschreibung | English Description | [1] |
| Deutscher Kommentar | German Commentary | 0-1 | |
| Englischer Kommentar | English Commentary | [1] | |
| Interner Kommentar | Internal Commentary | 0-1 | |
| Wesentliche Eigenschaften (deutsch) | Significant Properties (German) | 0-1 | |
| Wesentliche Eigenschaften (englisch) | Significant Properties (English) | [1] | |
| Bildbeschreibung (deutsch) | Image Description (German) | 0-1 |
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

  * [**JHOVE**](https://jhove.openpreservation.org/) – ursprünglich entwickelt von [JSTOR](https://www.jstor.org/) und der [Harvard University Library](https://library.harvard.edu/); derzeit in Kooperation weiterentwickelt von der [Open Preservation Foundation](https://openpreservation.org/)
  * [**DROID**](https://www.nationalarchives.gov.uk/information-management/manage-information/preserving-digital-records/droid/) – von [The National Archives](https://www.nationalarchives.gov.uk/)
  * [**MediaInfo**](https://mediaarea.net/de/MediaInfo)  – entwickelt von der "Open Source"-Software-Firma [MediaArea](https://mediaarea.net/)
  * [**ExifTool**](https://exiftool.org/) – von Phil Harvey

Einige Informationen aus diesem technischen Metadaten werden dabei besonders prominent in eigenen Feldern angezeigt. Diese sind:

| Deutscher Feldname | Englischer Feldname | Kardinalität | Kommentar |
| ------------- | ------------- | ------------- | ------------- |
| JHOVE-Dateistatus | JHOVE Status | 1 | Ein Status, der automatisch aus JHOVE ausgelesen wird und anzeigt, ob eine Datei valide und/oder wohlgeformt ist |							
| DROID-PUID | PUID | 1 | Eine aus DROID automatisch ausgelesene ID, die eine Datei in der [PRONOM-Datenbank](https://www.nationalarchives.gov.uk/PRONOM/) von [The National Archives]([https://www.nationalarchives.gov.uk/) identifiziert. |							
| DROID-PUID-Link | PUID Link | 1 | Ein daraus erzeugter Link, z. B.: [https://www.nationalarchives.gov.uk/PRONOM/fmt/134](https://www.nationalarchives.gov.uk/PRONOM/fmt/134)
| Prüfsumme | Hash/Checksum | 1 | Eine von DROID erzeugte Prüfsumme der Datei |									
| Dateityp (kurz) | File Type (short) | 1 | Der kurze Name des Dateityps |
| Dateityp (lang) | File Type (long) | 1 | Der ausgeschriebene Name des Dateityps |
| Dateifamilie | File Family | 1 | Die jeweilige Dateifamilie |
| Technische Dauer | Technical Duration	| 0-1 |Für Video- und Audiodateien |								


----

## Selbstbezügliche Entitäten

Projekte, Ereignisse und Akteur:innen können jeweils außerdem untereinander verknüpft werden. Dazu haben wir verschiedene reziproke Verbindungen angelegt. Das heißt, wenn eine Verbindung ausgewählt worden ist, wird immer die passende Gegenverbindung mitangelegt. Dies lässt sich an einem Beispiel illustrieren. Würde man bei C. P. E. Bach die Verbindung "hat Vater" "Johann Sebastian Bach" anlegen, so würde bei Letzterem automatisch folgendes angelegt werden: "ist Vater von" "C. P. E. Bach". Aus den folgenden Listen kann jeweils entnommen werden, welche Verbindung als Gegenstück angelegt wird.

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

### Projekt

| Ausgewählte Verbindung | Gegenstück |
| ------------- | ------------- |
| hat Bezug zu | hat Bezug zu |
|hat Teil | ist Teil von |
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

Sammlung ist die große Container-Entität von Digi-Kunst.nrw, die eine Vielzahl der bereits kennengelernten Entitäten bündeln kann. Denn neben eigenen deskriptiven Feldern, wie der deutsche und der englische Name der Sammlung, einer englischen und deutschen Beschreibung und der Auswahl einer Sammlungsart (z. B. "Reihe" oder "Objekt-Sammlung"), dient eine Sammlung dazu, Projekte, Ereignisse, Equipment & Software, Physische Objekte, Informationsträger und Digitale Objekte in einem größeren Kontext zusammenzufassen. Diese können wiederum in beliebig vielen Sammlungen auftauchen. Die Zusammenfassung in Sammlungen kann nach räumlichen, thematischen, zeitlichen Aspekten oder nach weiteren fachlichen Kriterien erfolgen.

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