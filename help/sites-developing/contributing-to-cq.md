---
title: Beitragen zu AEM
description: AEM wird nach den bewährten Vorgehensweisen entwickelt, die meist in großen Open-Source-Projekten praktiziert werden
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 43fb4fa3-269a-4635-b055-4b7d787da21f
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2635'
ht-degree: 98%

---

# Beitragen zu AEM{#contributing-to-aem}

## Entwicklungsmethodik {#development-methodology}

AEM wird nach bewährten Vorgehensweisen entwickelt, die meist in großen Open-Source-Projekten praktiziert werden. Viele Kernelemente im Technologie-Stack von AEM werden tatsächlich als aktive Open-Source-Projekte wie Sling und Jackrabbit verwaltet, die Teil der Apache Software Foundation sind. Ein wichtiger Aspekt des Ansatzes von AEM besteht darin, dass Sie ermutigt werden, die verfügbaren Mailing-Listen und Online-Foren für direkte Interaktionen mit dem Entwicklungs-Team zu nutzen.

Wenn Sie zu Komponenten von AEM beitragen, machen Sie sich mit AEM genauso vertraut wie mit einem Open-Source-Projekt und kommunizieren mit dem vorhandenen Kern-Team, als würden Sie zu einem solchen Projekt beitragen.

## Erforderliche Erfahrung {#required-experience}

Das HyperText Transfer Protocol (HTTP) spielt bei allem, was wir tun, eine zentrale Rolle. Bevor Sie also zu AEM beitragen, sollten Sie über ein tiefgehendes Verständnis von HTTP verfügen, idealerweise in dem Maße, dass Sie Ihre eigene Java™-Implementierung eines Multithread-HTTP-Servers mit Thread-Pooling schreiben können. Sie sollten auch das HTTP/1.1-Keep-Alive-Verhalten kennen und über eingehende Kenntnisse der Server-/Client-seitigen Interaktionen mit JavaScript verfügen, insbesondere über den asynchronen Interaktionsstil, der von AJAX repräsentiert wird.

Da Seitendynamik und interaktiver Inhalt der Schlüssel zum WM-Erlebnis sind, ist es wichtig, dass Sie über möglichst detaillierte Kenntnisse des Dokumentobjektmodells und seines Potenzials für die programmatische Bearbeitung als Reaktion auf Ereignisse verfügen. Sie sollten zum Beispiel Kenntnisse über Echtzeit-DOM-Manipulation und Drag-and-Drop-Verhalten über mehrere Browser-Dokumente haben (z. B. mit iframes).

Auf der höchsten Ebene sollten Sie über ein solides Verständnis folgender Themen verfügen:

* das [HTTP/1.1 Protokoll](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (vorzugsweise [HTML5](https://html.spec.whatwg.org/))
* Cascading Style Sheets (CSS)
* Extensible Markup Language (XML)
* Entwurfsmuster für Asynchronous JavaScript and XML (AJAX)
* JavaScript Object Notation (JSON)
* Document Object Model (DOM)
* Stateful und Stateless-Interaktionen
* [Uniform Resource Identifiers](https://www.ietf.org/rfc/rfc2396.txt)
* Browser-Cookies
* und andere moderne Web-Entwicklungskonzepte

Der Technologie-Stack von Adobe Experience Manager basiert auf dem [Apache Felix](https://felix.apache.org/documentation/index.html)-OSGI-Container mit dem [Apache Sling](https://sling.apache.org/index.html)-Web-Framework und bettet ein Java™ Content-Repository ([JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)) basierend auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/jcr-api.html) ein. Machen Sie sich mit diesen einzelnen Projekten sowie mit anderen Open Source-Komponenten (zum Beispiel Apache Lucene) vertraut, die in dem Bereich verwendet werden, in dem Sie Beiträge leisten möchten.

## Tribal-Kenntnisse {#tribal-knowledge}

Bestimmte Konzepte und Leitprinzipien sind tief in der früheren Day-Kultur verwurzelt. In diesem Abschnitt werden einige der „tief in die DNA eingebetteten“ Probleme aufgeführt, die Sie beachten sollten.

### Alles ist Inhalt {#everything-is-content}

Der Inhalt umfasst nicht nur alle Daten, die die Web-Anwendung speichert. Programm-Code, Bibliotheken, Skripte, Vorlagen, HTML, CSS, Bilder und Artefakte aller Art, alles und jedes wird im Content-Repository aufbewahrt und über Package Manager und Package Share in Form von Paketen importiert/exportiert.

### Davids Modell {#david-s-model}

Die Art und Weise, wie Inhalte in einem Java™ Content-Repository modelliert werden sollen, erfordert eine völlig andere Art zu denken als das, was in der Software-Branche für die Datenmodellierung in der relationalen Welt üblich ist. Eine Pflichtlektüre für jeden Neuling im Content-Management mit der JCR-Methode ist [David&#39;s Model: A guide for content modeling](https://wiki.apache.org/jackrabbit/DavidsModel).

### RESTfulness {#restfulness}

Der REST-Ansatz ist tief verwurzelt in dem, was wir tun. Dies bedeutet unter anderem, statusbehaftete Interaktionen zu vermeiden und zu berücksichtigen, dass URIs endgültige Adressen für Inhalte und Dienste sind.

REST (REpresentational State Transfer) bezeichnet den Software-Architekturstil, auf dem das World Wide Web basiert. Es beschreibt die Schlüsselelemente, die das Web zum Funktionieren bringen, und bietet somit eine Reihe von Prinzipien für die Gestaltung webbasierter Software. Bei der Entwicklung einer API, die über das Internet verwendet werden soll, ist es daher sinnvoll, diese „Best Practices“ einzuhalten.

Da REST die Leitphilosophie ist, die hinter so viel von dem steckt, was wir tun, sollten Sie es für wichtig erachten, sich in den Grundsätzen des RESTful-Designs auszukennen. Ein guter Ausgangspunkt ist [die Dissertation von Roy Fielding](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Auflösung von Sling-Anfragen {#sling-request-resolution}

Ein wesentlicher Aspekt zum Verständnis von AEM ist, wie eingehende Anforderungen sich auf das Inhalts- und Anwendungsverhalten beziehen, wie Inhalte im Content-Repository strukturiert sind und wo AEM nach der Anwendungslogik sucht, um die Anforderung zu bearbeiten. Erfahren Sie mehr über die Apache [Sling-URL-Dekomposition](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html) und die Art und Weise, wie sie den REST-Architekturstil und seine statusfreien, Cache-fähigen und geschichteten Systemeinschränkungen erzwingt.

Die wichtigsten Aspekte bei der Auflösung von Apache Sling-Anfragen sind, wie Anfragen primär einer bestimmten Ressource im Content-Repository zugeordnet werden, inwiefern zusätzliche Eigenschaften der Anfrage zusammen mit den Eigenschaften dieser Inhaltsobjekte bestimmen, welcher Anwendungs-Code zum Rendern des Inhalts aufgerufen wird und wie Code in „/apps“ den Code in „/libs“ überschreibt.

### Schnellstart {#quickstart}

Kein Schritt drei: zum Installieren und Ausführen lädt man einfach die Schnellstart-JAR-Datei herunter und doppelklickt darauf. Es gibt keinen Schritt drei.  Jede zusätzliche optionale Funktionalität erfordert nichts weiter als die Installation des entsprechenden Pakets von Package Share.

Kleine Schnellstart-Größe: halten Sie die Größe der Schnellstart-JAR-Datei auf ein Minimum begrenzt. Nutzen Sie Bibliotheken intelligent und optimiert und verschieben Sie optionale Funktionen auf Package Share.

Schnellere Startzeit: wenn Sie eine Änderung vornehmen, die sich auf die Startzeit auswirken könnte, stellen Sie sicher, dass sie kürzer wird, nicht länger.

### Rank und schlank {#lean-and-mean}

Wir bevorzugen Code und Projekte, die leicht, klein, schnell und elegant sind. „Gut genug“ ist nicht gut genug.

Wiederverwendung von Code: Unsere OSGi-basierte Produktarchitektur und die Philosophie „Alles ist Inhalt“ bedeuten, dass wir außergewöhnlich gute Möglichkeiten für die Wiederverwendung von Code und Artefakten haben. Wir versuchen, diese Tatsache wann immer möglich zu nutzen, um Features „rank und schlank“ zu halten.

Lose Kopplung: Wir bevorzugen lose gekoppelte Interaktionen gegenüber engen Abhängigkeiten und „unerwünschter Intimität“. Die lose Kopplung ermöglicht auch mehr Wiederverwendung von Code.

### Demo nicht unterbrechen {#don-t-break-the-demo}

Machen Sie sich mit Demo-Skripten und Produktfunktionen vertraut, die am häufigsten in Demos angezeigt werden. Verstehen Sie, dass nichts, was Sie tun, jemals eine „Demo-Skript“ -Funktion zerstören sollte. Das Kernprodukt sollte immer demofähig sein, auch während der Entwicklung.

### Design für Zuverlässigkeit {#design-for-reliability}

Wir bemühen uns, Funktionen auf Fail-Soft-Weise zu entwerfen und zu kodieren, sodass (z. B.) ein Problem mit einem einzelnen DOM-Element nicht dazu führt, dass eine ganze Seite nicht gerendert wird. Mit anderen Worten: Machen Sie Dinge, die tödlich sein sollten, tödlich. Machen Sie alles andere überlebensfähig.  Machen Sie das Produkt „nachsichtig“.

### Abnormal ist das neue Normal {#abnormal-is-the-new-normal}

Abhängig von den Shutdown-Hooks sollten Sie beim Start eine Bereinigung durchführen. Abnormale Beendigung ist normale Beendigung.

`shutdown == kill -9 == power outage`

### Seien Sie bereit für elastisches Clustering {#be-ready-for-elastic-clustering}

Seien Sie immer bereit für elastisches Clustering, gehen Sie immer davon aus, dass es Clustering gibt. Im Allgemeinen bedeutet das Einhalten von allem, was im Content-Repository enthalten ist, eine integrierte Cluster-Unterstützung.

### Entwerfen Sie für Abwärtskompatibilität {#design-for-backward-compatibility}

Nichts, was Sie tun, sollte den alten Code eines Kunden zerstören. Nur `/libs` sollte Produkt-Code enthalten, der während eines Upgrades aktualisiert werden kann. Der Abschnitt `/apps` des Repositorys ist Projekt-Code und der Abschnitt `/etc` enthält benutzerdefinierte Konfigurationen, die beibehalten werden müssen. Überschreiben Sie grundsätzlich nichts in `/apps`, `/content` und `/home`. Nach einem Upgrade sollten alter Projekt-Code, Konfigurationen und Inhalte weiterhin so funktionieren wie vor dem Upgrade.

Wenn Sie für Abwärtskompatibilität entwickeln, stellen Sie außerdem sicher, dass das Upgrade-Erlebnis genauso einfach ist wie das der Erstinstallation.  Einfaches Beenden von AEM, Ersetzen der Quickstart-JAR-Datei und erneutes Starten von AEM sollten ausreichen. Mit einer schnell wachsenden Installationsbasis wird die Effizienz von Upgrades ein zunehmend wichtiger Vorteil sein.

Bestehende APIs können und sollten als veraltet markiert werden, wenn eine neuere, bessere Funktionalität diese ersetzt, alle APIs, die in einer früheren 5.x-Version veröffentlicht wurden, müssen weiterhin funktionsfähig bleiben, da sie möglicherweise in benutzerdefiniertem Anwendungs-Code verwendet werden. Keine dieser APIs sollte entfernt werden.

Die Abwärtskompatibilität sollte auch in Bezug auf die allgemeine Konsistenz der Inhaltsstruktur und des Anwendererlebnisses berücksichtigt werden.

## Grundlegende Konzepte {#core-concepts}

**Autoreninstanz**: Aus Gründen der Sicherheit und der Governance, aber auch aus anderen Gründen unterteilt eine Produktions-Site typischerweise Instanzen von AEM in Autoren- und Veröffentlichungsinstanzen. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM-Instanzen.

**Caching, Frying und Baking**: Traditionell sind die Konzepte des Baking oder Frying eine wichtige Unterscheidung zwischen verschiedenen Web Content-Managementsystemen. Im CMS-Jargon bezieht sich „Baking“ auf das Konzept der Übertragung von Daten in statische Dateien zur Veröffentlichungszeit, während „Frying“ sich auf das Konzept der Verarbeitung von Daten für die endgültige Präsentation zum Zeitpunkt der Anfrage (d. h. gerade rechtzeitig) bezieht.

**Clustering und Lastenausgleich**: Um die Verfügbarkeit zu erhöhen und die Leistung einer Produktionsumgebung zu steigern, ist es üblich, mehrere Autoren- und/oder Veröffentlichungsinstanzen in Clustern zu kombinieren, indem sie entweder für verschiedene Benutzergruppen oder durch Lastenausgleich hinter einer Dispatcher-Konfiguration verfügbar gemacht werden.

Es ist auch möglich, mehrere Instanzen des Content-Repositorys zu einer JCR-Lösung mit *hoher Verfügbarkeit* zu kombinieren, die dann in Ihre AEM-Lösung integriert werden kann, um den Schutz vor Hardware- und Softwarefehlern zu maximieren. Weitere Informationen finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter).

**Komponente**: In AEM ist eine Komponente ein Objekttyp, dessen Instanzen in der Regel durch Ziehen und Ablegen z. B. im Sidekick erstellt werden können. So enthalten beispielsweise mit AEM ausgelieferte Standardkomponenten die Komponenten Text, Titel, Tag Cloud, Karussell, Bild und Liste, die alle zur Laufzeit über den Sidekick verfügbar sind.

**Content Finder (Inhaltssuche)**: Im Authoring-Modus ist der Content Finder ein spezieller Fensterbereich (Rahmen) auf der linken Seite der Seite, der je nach der oben ausgewählten Registerkarte Listen mit Bildern, Dokumenten, Flash-Assets, Seiten, Absätzen oder Repository-Ressourcen anzeigt, die Sie per Drag-and-Drop aus dem Content Finder auf die Seite ziehen können, an der Sie gerade arbeiten (rechts).

**Digitale Assets**: In AEM sind digitale Assets (in der Regel) Bilder und Rich-Media-Dateien. Weitere Informationen finden Sie unter Arbeiten mit digitalen Assets in DAM.

**Dispatcher**: Der Dispatcher ist sowohl ein Caching- als auch ein Lastenausgleichs-Tool und bietet bestimmte Sicherheitsmaßnahmen.

**ExtJS-Widgets**: Die meisten Elemente der Benutzeroberfläche in AEM verwenden ExtJS, eine in JavaScript geschriebene Widget-Bibliothek von Drittanbietern. ExtJS bietet leistungsstarke, anpassbare Benutzeroberflächen-Widgets und ein gut konzipiertes und erweiterbares Komponentenmodell.

**JCR (Java™ Content-Repository)**: Die Java™ Content-Repository-Spezifikation (JSR-283) bietet sowohl ein abstraktes Datenmodell als auch eine Anwendungsprogrammierschnittstelle zur Realisierung eines massiv skalierbaren NoSQL-Daten-Repositorys, das Merkmale eines Dateisystems und einer Objektdatenbank kombiniert. Auch wenn Sie JSR-283 nicht umfassend verstehen müssen, sollten Sie sich die Zeit nehmen, um sich mit den grundlegenden Funktionen von JCR und dem zugrunde liegenden Datenmodell vertraut zu machen, da JCR die „Alles ist Inhalt“-Philosophie von AEM ermöglicht.

Im Wesentlichen ist JCR ein System von Knoten und Eigenschaften, in dem Knoten von anderen Knoten erben können und der gesamte Inhalt als *Eigenschaftswerte* gespeichert wird. Beachten Sie, dass JCR zusätzlich zur normalen Vererbung ein Konzept von „Mixin“-Knoten ermöglicht, das die Modellierung von Mehrfachvererbung ermöglicht.

JCR verfügt über eine Reihe vordefinierter Knotentypen und Eigenschaftstypen, aber im Allgemeinen ist das Typisierungssystem ziemlich flexibel, und tatsächlich besteht eine der Stärken von JCR darin, dass sowohl strukturierte als auch unstrukturierte Inhalte mit Leichtigkeit gespeichert/verwaltet werden können. Das heißt, JCR kann stark strukturierte Daten aufnehmen, aber es kann auch beliebige dynamische Datenstrukturen ohne Schemaeinschränkungen aufnehmen.

Die JavaDoc für die JCR-Java™-API finden Sie [hier](https://jackrabbit.apache.org/jcr/jcr-api.html).

Bevor Sie versuchen, die JavaDoc- oder die JCR-Spezifikation selbst zu lesen, sollten Sie sich diese [High-Level-Erklärung](/help/sites-developing/the-basics.md#java-content-repository) von JCR ansehen, die von Adobe Experience Services implementiert wird.

**Multi-Site Manager (MSM)**: Die MSM-Funktion von AEM unterstützt Kunden bei der Bearbeitung mehrsprachiger und multinationaler Inhalte und ermöglicht es ihnen, zentralisiertes Branding mit lokalisierten Inhalten in Einklang zu bringen.

**OSGi**: OSGi ist die Service-basierte Runtime-Technologie, die die Basis für die modularisierte Java™-Entwicklung in AEM bietet. Es ist ein Framework, das nicht nur eine hochdynamische (und sichere) Classloading- und Execution-Umgebung für Coderessourcen (bekannt als Bundle) bietet, sondern auch volle Kontrolle über die Sichtbarkeit und den Lebenszyklus der verschiedenen Services, die von Bundles bereitgestellt werden. Eine Service-Registrierung stellt ein Kooperationsmodell für Bundles bereit, das Lebenszyklusdynamik (und Versionsanforderungen) berücksichtigt. OSGi löst viele der Probleme, die von Anwendungs-Servern gelöst werden sollten, jedoch auf leichte und hochdynamische Weise. So können beispielsweise Dienste direkt bereitgestellt werden (der neue Code wird sofort verfügbar, ohne den Server neu zu starten).

**Parsys, Absatzsystem**: Das Absatzsystem (parsys) ist eine zusammengesetzte Komponente, die es Autoren ermöglicht, einer Seite Komponenten verschiedener Typen hinzuzufügen, und die andere Absatzkomponenten enthält. Jeder Absatztyp wird als eine Komponente dargestellt. Das Absatzsystem selbst ist ebenfalls eine Komponente, die die anderen Absatzkomponenten enthält.

**Mikrokernel** Jeder Arbeitsbereich im Repository kann separat konfiguriert werden, um seine Daten über einen bestimmten Mikrokernel zu speichern (eine Klasse, die das Lesen und Schreiben der Daten verwaltet). Ebenso kann der Repository-weite Versionsspeicher unabhängig für die Verwendung eines bestimmten Mikrokernels konfiguriert werden. Eine Reihe verschiedener Mikro-Kernels sind verfügbar, die Daten in einer Vielzahl von Dateiformaten oder relationalen Datenbanken speichern können. (Zum Beispiel gibt es Persistence Manager für MongoDB, DB2® oder Oracle). Der Standard-Mikro-Kernel für AEM ist TarMK (siehe weiter unten).

**Veröffentlichungsinstanz**: Aus Gründen der Sicherheit, der Governance und aus anderen Gründen unterteilt eine Produktions-Website typischerweise Instanzen von AEM in Autoren- und Veröffentlichungsinstanzen. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM-Instanzen.

**Schnellstart**: Im Gegensatz zu vielen anderen Programmen installieren Sie AEM mithilfe einer einzelnen selbstextrahierenden JAR-Schnellstart-Datei. Wenn Sie zum ersten Mal auf die JAR-Datei doppelklicken, wird alles, was Sie benötigen, automatisch installiert. Die Schnellstart-JAR enthält alle für das CRX-Repository erforderlichen Dateien (einschließlich Verwaltungseinrichtungen), virtuelle Repository-Dienste, Index- und Suchdienste, Workflow-Services, Sicherheit und einen Webserver sowie die CQ Servlet Engine (CQSE) und alle AEM-Dienste. Es sind keine weiteren Dateien zu installieren: Der Schnellstart ist eigenständig.

Wenn Sie den Schnellstart zum ersten Mal starten, wird im Hintergrund ein ganzes JCR-kompatibles Repository erstellt, was einige Minuten dauern kann. Nach diesem ersten Start sind nachfolgende Startvorgänge wesentlich schneller, da die Repository-Infrastruktur bereits angelegt wurde.

Viele Startoptionen (z. B. die Nummer des aktiven Ports und ob die fragliche AEM-Instanz eine Veröffentlichungsinstanz oder eine Autoreninstanz sein soll und vieles mehr) können durch entsprechendes Umbenennen der Schnellstart-Datei gesteuert werden. Um eine Liste diesbezüglicher Optionen anzuzeigen, führen Sie die JAR-Datei mit „-help“ in der Befehlszeile aus:

```shell
java -jar <quickstartfilename>.jar -help
```

**Replikationsagenten**: Replikationsagenten sind für AEM als Mechanismus für Folgendes von zentraler Bedeutung: Veröffentlichen (Aktivieren) von Inhalten von einer Autoren- in eine Veröffentlichungsumgebung, Leeren des Inhalts aus dem Dispatcher-Cache und Zurückgeben der von Benutzenden generierten Inhalte (z. B. Formulareingabe) von der Veröffentlichungsumgebung an die Autorenumgebung.

**Strukturvorlage**: Eine Strukturvorlage dient zur Erstellung eines Formulars (einer Struktur), dessen Felder die gewünschte Seitenstruktur bilden. Anhand dieses Formulars können Sie ganz einfach auf dieser Struktur basierende Seiten erstellen.

**Segmentierung**: Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Website besuchen. Die Ziele der Besucher zu verstehen und ihre Erwartungen zu erfüllen, ist eine wichtige Erfolgsvoraussetzung für das Online-Marketing. Die Segmentierung hilft dabei, die Details eines Besuchers zu analysieren und zu charakterisieren.

**Sidekick**: Der Sidekick ist ein palettenartiges schwebendes Fenster, das auf der bearbeitbaren Seite erscheint, von dem aus neue Komponenten gezogen und Aktionen für die Seite ausgeführt werden können.

**Site Catalyst**: SiteCatalyst bietet Marketern einen Ort, an dem sie integrierte Daten aus allen Online-Initiativen über mehrere Marketing-Kanäle messen, analysieren und optimieren können. Sie können mit Adobe SiteCatalyst Daten von AEM Sites analysieren.

**Tar-Speicher (TarMK)**: TarMK ist das standardmäßige Persistenzsystem in AEM. Obwohl AEM für die Verwendung eines anderen Persistenzsystems (z. B. MongoDB) konfiguriert werden kann, hat TarMK gewisse Vorteile, da es für typische JCR-Anwendungsfälle leistungsoptimiert ist (also sehr schnell), ein Industriestandard-Datenformat verwendet und schnell und einfach gesichert werden kann.

**Vorlage**: In AEM gibt eine Vorlage einen bestimmten Seitentyp an. Sie definiert die Struktur einer Seite (während sie normalerweise auch ein Miniaturbild und verschiedene Eigenschaften angibt). Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden.

**Workflow**: Das AEM-Workflow-System ermöglicht die Erstellung von automatisierten Prozessen mit Seiten oder Assets.
