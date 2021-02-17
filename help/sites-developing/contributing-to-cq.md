---
title: Beitragen zu AEM
seo-title: Beitragen zu AEM
description: AEM wird nach den bewährten Vorgehensweisen entwickelt, die häufig in großen Open-Source-Projekten praktiziert werden
seo-description: AEM wird nach den bewährten Vorgehensweisen entwickelt, die häufig in großen Open-Source-Projekten praktiziert werden
uuid: ffef60ae-8a9a-4c4b-8cbd-3cd72792a42e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: f52402df-f6dc-4c62-82bc-cbce489b2b74
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '2726'
ht-degree: 67%

---


# Beitragen zu AEM{#contributing-to-aem}

## Entwicklungsmethodik {#development-methodology}

AEM wird nach bewährten Vorgehensweisen entwickelt, die häufig in großen Open-Source-Projekten praktiziert werden. Viele Kernelemente im Technologie-Stack von AEM werden tatsächlich als aktive Open-Source-Projekte wie Sling und Jackrabbit verwaltet, die Teil der Apache Software Foundation sind. Ein wichtiger Aspekt der Idee von AEM besteht darin, dass Sie ermutigt werden, die verfügbaren Mailinglisten und Onlineforen für direkt Interaktion mit dem Entwicklungsteam zu nutzen.

Wenn Sie zu Komponenten von AEM beitragen, sollten Sie sich mit AEM genauso vertraut machen wie mit einem Open-Source-Projekt und mit dem vorhandenen Kernteam kommunizieren, als würden Sie zu einem solchen Projekt beitragen.

## Erforderliche Erfahrung {#required-experience}

Das HyperText Transfer Protocol (HTTP) spielt bei allem, was wir tun, eine zentrale Rolle. Bevor Sie also zu AEM beitragen, sollten Sie über ein tiefgehendes Verständnis von HTTP verfügen, idealerweise in dem Maße, dass Sie Ihre eigene Java-Implementierung eines Multithread-HTTP-Servers mit Thread-Pooling schreiben könnten. Sie sollten auch das HTTP/1.1-Keep-Alive-Verhalten verstehen und über eingehende Kenntnisse der server/clientseitigen Interaktionen mit JavaScript verfügen, insbesondere über den asynchronen Interaktionsstil, der von AJAX repräsentiert wird.

Da Seitendynamik und interaktiver Inhalt der Schlüssel zum WM-Erlebnis sind, ist es wichtig, dass Sie das Dokumentobjektmodell und sein Potenzial für programmatische Manipulation als Reaktion auf Ereignisse möglichst gut verstehen. Sie sollten zum Beispiel Kenntnisse über Echtzeit-DOM-Manipulation und Drag-and-Drop-Verhalten über mehrere Browser-Dokumente haben (z. B. mit iframes).

Auf der höchsten Ebene sollten Sie über ein solides Verständnis folgender Themen verfügen:

* das [HTTP/1.1 Protokoll](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (vorzugsweise [HTML5](https://dev.w3.org/html5/spec/Overview.html))
* Cascading Style Sheets (CSS)
* Extensible Markup Language (XML)
* Entwurfsmuster für Asynchronous JavaScript and XML (AJAX)
* JavaScript Object Notation (JSON)
* Document Object Model
* Stateful und Stateless-Interaktionen
* [Uniform Resource Identifiers](https://www.ietf.org/rfc/rfc2396.txt)
* Browser-Cookies
* und andere moderne Web-Entwicklungskonzepte

Der Technologiestapel von Adobe Experience Manager basiert auf dem Container [Apache Felix](https://felix.apache.org/) OSGI mit dem Webframework [Apache Sling](https://sling.apache.org/site/index.html) und bettet ein Java Content Repository ([JCR](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/index.html)) ein, das auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr-api.html) basiert. Sie sollten sich mit diesen einzelnen Projekten sowie mit anderen Open Source-Komponenten (z. B. Apache Lucene) vertraut machen, die in dem Bereich verwendet werden, in dem Sie Beiträge leisten möchten.

## Tribal-Kenntnisse {#tribal-knowledge}

Bestimmte Konzepte und Leitprinzipien sind tief in der früheren Day-Kultur verwurzelt. In diesem Abschnitt werden einige der „tief in die DNA eingebetteten“ Probleme aufgeführt, die Sie beachten sollten.

### Alles ist Inhalt {#everything-is-content}

Der Inhalt umfasst nicht nur alle Daten, die die Webanwendung speichert. Der Programm-Code, Bibliotheken, Skripten, Vorlagen, HTML, CSS, Bilder und Artefakte aller Art bleiben im Content Repository erhalten und werden über Package Manager und Package Share in Form von Paketen importiert/exportiert.

### Davids Modell {#david-s-model}

Die Art und Weise, wie Inhalte in einem Java Content Repository modelliert werden sollen, erfordert eine völlig andere Art zu denken als das, was in der Softwarebranche für die Datenmodellierung in der relationalen Welt üblich ist. Eine Pflichtlektüre für jeden Neuling im Content-Management mit der JCR-Methode ist [David&#39;s Model: A guide for content modeling](https://wiki.apache.org/jackrabbit/DavidsModel).

### RESTfulness {#restfulness}

Der REST-Ansatz ist tief verwurzelt in dem, was wir tun. Dies bedeutet unter anderem, statusbehaftete Interaktionen zu vermeiden und zu berücksichtigen, dass URIs endgültige Adressen für Inhalte und Dienste sind.

REST (REpresentational State Transfer) bezeichnet den Software-Architekturstil, auf dem das World Wide Web basiert. Es beschreibt die Schlüsselelemente, die das Web zum Funktionieren bringen, und bietet somit eine Reihe von Prinzipien für die Gestaltung webbasierter Software. Bei der Entwicklung einer API, die über das Internet verwendet werden soll, ist es daher sinnvoll, diese Best Practices einzuhalten.

Da REST die Leitphilosophie ist, die hinter so viel von dem steckt, was wir tun, sollten Sie es für wichtig halten, sich in den Grundsätzen des RESTful Designs auskennen zu können. Ein guter Ausgangspunkt ist [Roy Fieldings Dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Sling Anfrageauflösung {#sling-request-resolution}

Ein wesentlicher Aspekt zum Verständnis von AEM ist, wie eingehende Anforderungen sich auf das Inhalts- und Anwendungsverhalten beziehen, wie Inhalte im Content-Repository strukturiert sind und wo AEM nach der Anwendungslogik sucht, um die Anforderung zu bearbeiten. Erfahren Sie mehr über die Apache [Sling URL-Dekomposition](https://sling.apache.org/site/url-decomposition.html) und die Art und Weise, wie sie den REST-Architekturstil und seine statusfreien, cachefähigen und geschichteten Systemeinschränkungen erzwingt.

Schwerpunkte der Apache Sling-Anfrageauflösung sind, wie Anfragen hauptsächlich auf eine bestimmte Ressource im Content Repository abgebildet werden, wie zusätzliche Eigenschaften der Anfrage zusammen mit Eigenschaften dieser Inhaltsobjekte bestimmen, welcher Anwendungscode zum Rendern des Inhalts aufgerufen wird. und wie der Code in /apps den Code in /libs überschreibt.

### Schnellstart {#quickstart}

Kein Schritt drei: zum Installieren und Ausführen lädt man einfach die Schnellstart-JAR-Datei herunter und doppelklickt darauf. Es gibt keinen Schritt drei. Jede zusätzliche optionale Funktionalität erfordert nichts weiter als die Installation des entsprechenden Pakets von Package Share.

Kleine Schnellstart-Größe: halten Sie die Größe der Schnellstart-JAR-Datei auf ein Minimum begrenzt. Intelligente, optimierte Verwendung von Bibliotheken, wobei optionale Funktionen zur Paketfreigabe verschoben werden.

Schnellere Startzeit: wenn Sie eine Änderung vornehmen, die sich auf die Startzeit auswirken könnte, stellen Sie sicher, dass sie kürzer wird, nicht länger.

### Rank und schlank  {#lean-and-mean}

Wir bevorzugen Code und Projekte, die leicht, klein, schnell und elegant sind. „Gut genug“ ist nicht gut genug.

Wiederverwendung von Code: Unsere OSGi-basierte Produktarchitektur und die Philosophie „Alles ist Inhalt“ bedeuten, dass wir außergewöhnlich gute Möglichkeiten für die Wiederverwendung von Code und Artefakten haben. Wir versuchen, diese Tatsache wann immer möglich zu nutzen, um Features „rank und schlank“ zu halten.

Lose Kopplung: Wir bevorzugen lose gekoppelte Interaktionen gegenüber engen Abhängigkeiten und „unerwünschter Intimität“. Lose Kopplung ermöglicht auch mehr Code-Wiederverwendung.

### Zerstören Sie die Demo nicht  {#don-t-break-the-demo}

Machen Sie sich mit Demo-Skripten und Produktfunktionen vertraut, die in Demos am häufigsten angezeigt werden. Verstehen Sie, dass nichts, was Sie tun, jemals eine „Demo-Skript“ -Funktion zerstören sollte. Das Kernprodukt sollte immer demofähig sein, auch während der Entwicklung.

### Design für Zuverlässigkeit  {#design-for-reliability}

Wir bemühen uns, Features in Fail-Soft-Art zu entwerfen und zu kodieren, sodass (zum Beispiel) ein Problem mit einem einzelnen DOM-Element nicht dazu führt, dass eine ganze Seite nicht gerendert wird. Mit anderen Worten: Machen Sie Dinge, die tödlich sein sollten, tödlich. Machen Sie alles andere überlebensfähig. Machen Sie das Produkt „nachsichtig“.

### Abnormal ist das neue normal  {#abnormal-is-the-new-normal}

Verlassen Sie sich nicht auf Shutdown-Hooks, sorgen Sie für eine Bereinigung beim Start. Abnormale Beendigung ist normale Beendigung.

`shutdown == kill -9 == power outage`

### Seien Sie bereit für elastisches Clustering {#be-ready-for-elastic-clustering}

Seien Sie immer bereit für elastische Clustering, nehmen Sie immer an, dass es Clustering. Im Allgemeinen bedeutet das Einhalten von allem, was im Content-Repository enthalten ist, eine integrierte Clusterunterstützung.

### Entwerfen Sie für Abwärtskompatibilität {#design-for-backward-compatibility}

Nichts, was Sie tun, sollte den alten Code eines Kunden zerstören. Verwenden Sie nur `/libs`, um Produktcode zu enthalten, der während einer Aktualisierung aktualisiert werden kann. Der Abschnitt `/apps` des Repositorys ist Projektcode und der Abschnitt `/etc` enthält benutzerdefinierte Konfigurationen, die beibehalten werden müssen. Überschreiben Sie im Allgemeinen nichts in `/apps`, `/content` und `/home`. Nach einer Aktualisierung sollten alter Projektcode, Konfigurationen und Inhalt weiterhin wie vor der Aktualisierung funktionieren.

Wenn Sie für Abwärtskompatibilität entwickeln, stellen Sie außerdem sicher, dass das Upgrade-Erlebnis mit der Einfachheit der Erstinstallation übereinstimmt. Einfaches Beenden von AEM, Ersetzen der Quickstart-JAR-Datei und erneutes Starten von AEM sollten ausreichen. Mit einer schnell wachsenden Installationsbasis wird die Upgrade-Effizienz ein zunehmend wichtigerer Vorteil sein.

Bestehende APIs können und sollten als veraltet markiert werden, wenn eine neuere, bessere Funktionalität diese ersetzt, alle APIs, die in einer früheren 5.x-Version veröffentlicht wurden, müssen weiterhin funktionsfähig bleiben, da sie möglicherweise in benutzerdefiniertem Anwendungscode verwendet werden. Keine dieser APIs sollte entfernt werden.

Abwärtskompatibilität sollte auch im Hinblick auf die allgemeine Konsistenz der Inhaltsstruktur und Benutzererfahrung berücksichtigt werden.

## Grundlegende Konzepte {#core-concepts}

**Autoreninstanz** : Aus Sicherheitsgründen, aus Verwaltungsgründen und aus anderen Gründen unterteilt eine Produktionssite Instanzen von AEM in Instanzen im Autoren- und Veröffentlichungsmodus. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM Instanzen.

**Zwischenspeicherung, Braten und Backen**  - Traditionell unterscheiden sich die Konzepte von Backen und Braten in den verschiedenen Web-Content-Management-Systemen. Im CMS-Jargon bezieht sich &quot;Backen&quot;auf das Konzept der Datenbindung an statische Dateien zur Veröffentlichungszeit, während &quot;Braten&quot;auf das Konzept der Verarbeitung von Daten zur endgültigen Präsentation zur Anforderungszeit (d.h. gerade rechtzeitig) verweist.

**Clustering und Lastenausgleich** : Zur Verbesserung der Verfügbarkeit und der Leistung einer Produktions-Umgebung ist es üblich, mehrere Autor- und/oder Veröffentlichungsinstanzen (in Clustern) zu kombinieren, indem sie entweder verschiedenen Benutzergruppen zur Verfügung gestellt werden oder indem sie hinter einer Dispatcher-Konfiguration einen Lastenausgleich vornehmen.

Es ist auch möglich, mehrere Instanzen des Inhalts-Repositorys zu kombinieren, um eine *hochverfügbare* JCR-Lösung zu erstellen, die dann in Ihre AEM-Lösung integriert werden kann, um den Schutz vor Hardware- und Softwareausfällen zu maximieren. Weitere Informationen finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter).

**Komponente** : In AEM ist eine Komponente ein Objekttyp, dessen Instanzen im Allgemeinen durch Ziehen und Ablegen aus dem Sidekick erstellt werden können. So enthalten beispielsweise mit AEM ausgelieferte Standardkomponenten die Komponenten Text, Titel, Tag Cloud, Karussell, Bild und Liste, die alle zur Laufzeit über den Sidekick verfügbar sind.

**Content Finder**  - Im Authoring-Modus ist die Inhaltssuche ein spezielles Bedienfeld (Frame) auf der linken Seite der Seite, das je nach der Registerkarte, die Sie oben auswählen, Listen von Bildern, Dokumenten, Flashs, Assets, Seiten, Absätzen oder Repository-Ressourcen anzeigt, die Sie per Drag &amp; Drop aus der Inhaltssuche auf die Seite ziehen können, an der Sie gerade arbeiten (rechts).

**Digitale Assets**  - In AEM sind digitale Assets (in der Regel) Bilder und Rich-Media-Dateien. Weitere Informationen finden Sie unter Arbeiten mit digitalen Assets in DAM.

**Dispatcher**  - Der Dispatcher ist sowohl ein Cache- und Lastenausgleichswerkzeug, als auch bietet bestimmte Sicherheitsgarantien.

**ExtJS-Widgets**  - Die meisten Elemente der Benutzeroberfläche in AEM verwenden ExtJS, eine Widget-Bibliothek eines Drittanbieters, die in JavaScript geschrieben ist. ExtJS bietet leistungsstarke, anpassbare UI-Widgets und ein gut gestaltetes und erweiterbares Komponentenmodell.

**JCR, Java Content Repository**  - Die Java Content Repository-Spezifikation (JSR-283) bietet sowohl ein abstraktes Datenmodell als auch eine Anwendungsprogrammierschnittstelle zur Realisierung eines massiv skalierbaren NoSQL-Datenrepository, das Funktionen eines Dateisystems und einer Objektdatenbank kombiniert. Obwohl Sie JSR-283 nicht umfassend verstehen müssen, sollten Sie sich die Zeit nehmen, sich mit den grundlegenden Funktionen von JCR und dem zugrunde liegenden Datenmodell vertraut zu machen, da JCR die „Alles ist Inhalt“-Philosophie von AEM ermöglicht.

Im Wesentlichen ist JCR ein System von Knoten und Eigenschaften, in dem Knoten von anderen Knoten erben können und der gesamte Inhalt als *Eigenschaftswerte* gespeichert wird. Beachten Sie, dass JCR zusätzlich zur normalen Vererbung ein Konzept von „Mixin“-Knoten ermöglicht, das die Modellierung von Mehrfachvererbung ermöglicht.

JCR verfügt über eine Reihe vordefinierter Knotentypen und Eigenschaftstypen, aber im Allgemeinen ist das Typisierungssystem ziemlich flexibel und tatsächlich besteht eine der Stärken von JCR darin, dass sowohl strukturierter als auch unstrukturierter Inhalt mit Leichtigkeit gespeichert/verwaltet werden kann. Das heißt, JCR kann stark strukturierte Daten aufnehmen, aber es kann auch beliebige dynamische Datenstrukturen ohne Schemaeinschränkungen aufnehmen.

Die JavaDoc für die JCR-Java-API finden Sie [hier](http://jackrabbit.apache.org/jcr/jcr-api.html).

Bevor Sie versuchen, die JavaDoc- oder die JCR-Spezifikation selbst zu lesen, sollten Sie sich diese [High-Level-Erklärung](/help/sites-developing/the-basics.md#java-content-repository) von JCR ansehen, die von Adobe Experience Services implementiert wird.

**Multi-Site-Manager (MSM)**  - Die MSM-Funktion von AEM unterstützt Kunden bei der Verwaltung mehrsprachiger und multinationaler Inhalte, sodass sie zentralisiertes Branding mit lokalisierten Inhalten in Einklang bringen können.

**OSGi** - OSGi ist die dienstbasierte Laufzeittechnologie, die die Grundlage für die modulare Java-Entwicklung in AEM bietet. Es ist ein Framework, das nicht nur eine hochdynamische (und sichere) Classloading- und Execution-Umgebung für Coderessourcen (bekannt als Bundle) bietet, sondern auch volle Kontrolle über die Sichtbarkeit und den Lebenszyklus der verschiedenen Services, die von Bundles bereitgestellt werden. Eine Service-Registrierung stellt ein Kooperationsmodell für Bundles bereit, das Lebenszyklusdynamik (und Versionsanforderungen) berücksichtigt. OSGi löst viele der Probleme, die von Anwendungsservern gelöst werden sollten, jedoch auf leichte und hochdynamische Weise. So können beispielsweise Dienste schnell bereitgestellt werden (der neue Code wird sofort verfügbar, ohne den Server neu zu starten).

**Parsys, Absatzsystem**  - Das Absatzsystem (parsys) ist eine zusammengesetzte Komponente, mit der Autoren Komponenten unterschiedlicher Typen zu einer Seite hinzufügen können und die andere Absatzkomponenten enthalten. Jeder Absatztyp wird als eine Komponente dargestellt. Das Absatzsystem selbst ist auch eine Komponente, die die anderen enthält.

**Microkernel**  - Jeder Arbeitsbereich im Repository kann separat konfiguriert werden, um seine Daten über einen bestimmten Microkernel zu speichern (eine Klasse, die das Lesen und Schreiben der Daten verwaltet). Ebenso kann der Repository-weite Versionsspeicher unabhängig für die Verwendung eines bestimmten Mikrokernels konfiguriert werden. Eine Reihe verschiedener Mikrokernel sind verfügbar, die Daten in einer Vielzahl von Dateiformaten oder relationalen Datenbanken speichern können. (Zum Beispiel gibt es Persistence Manager für MongoDB, DB2 oder Oracle). Der Standard-Microkernel für AEM ist TarMK (siehe weiter unten).

**Instanz**  im Veröffentlichungsmodus: Aus Sicherheitsgründen, zur Verwaltung und aus anderen Gründen unterteilt eine Produktions-Site Instanzen von AEM in Instanzen im Autoren- und Veröffentlichungsmodus. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM Instanzen.

**Quickstart**  - Im Gegensatz zu vielen anderen Programmen installieren Sie AEM mit einer einzigen, selbstextrahierenden JAR-Datei. Wenn Sie zum ersten Mal auf die JAR-Datei doppelklicken, wird alles, was Sie benötigen, automatisch installiert. Die Schnellstart-JAR enthält alle für das CRX-Repository erforderlichen Dateien (einschließlich Verwaltungseinrichtungen), virtuelle Repository-Dienste, Index- und Suchdienste, Workflow-Services, Sicherheit und einen Webserver sowie die CQ Servlet Engine (CQSE) und alle AEM-Dienste. Es sind keine weiteren Dateien zu installieren: Der Schnellstart ist eigenständig.

Wenn Sie den Schnellstart zum ersten Mal starten, wird im Hintergrund ein ganzes JCR-kompatibles Repository erstellt, was einige Minuten dauern kann. Nach diesem ersten Start sind nachfolgende Startvorgänge viel schneller, da die Repository-Infrastruktur bereits angelegt wurde.

Viele Startoptionen (z. B. die Nummer des aktiven Ports und ob die fragliche AEM-Instanz eine Veröffentlichungsinstanz oder eine Autoreninstanz sein soll und vieles mehr) können durch entsprechendes Umbenennen der Schnellstart-Datei gesteuert werden. Um eine Liste diesbezüglicher Optionen anzuzeigen, führen Sie das JAR mit „-help“ in der Befehlszeile aus:

```shell
java -jar <quickstartfilename>.jar -help
```

**Replizierungsagenten** : Replizierungsagenten sind von zentraler Bedeutung für AEM als Mechanismus zur Veröffentlichung (Aktivierung) von Inhalten von einem Autor zu einer Umgebung zur Veröffentlichung. Inhalte aus dem Dispatcher-Cache löschen; vom Benutzer generierte Inhalte (z. B. Formulareingaben) aus der Umgebung &quot;Veröffentlichen&quot;in die Umgebung &quot;Autor&quot;zurückgeben.

**Gerüst**  - Mit dem Gerüst können Sie ein Formular (ein Gerüst) mit Feldern erstellen, die die gewünschte Struktur für Ihre Seiten widerspiegeln. Anschließend können Sie mit diesem Formular auf einfache Weise Seiten erstellen, die auf dieser Struktur basieren.

**Segmentierung** : Site-Besucher haben unterschiedliche Interessen und Ziele, wenn sie zu einer Site gelangen. Die Ziele der Besucher zu verstehen und ihre Erwartungen zu erfüllen, ist eine wichtige Erfolgsvoraussetzung für das Online-Marketing. Die Segmentierung hilft dabei, die Details eines Besuchers zu analysieren und zu charakterisieren.

**Sidekick**  - Der Sidekick ist ein palettenähnliches schwebendes Fenster, das auf der bearbeitbaren Seite angezeigt wird und aus dem neue Komponenten gezogen werden können und Aktionen ausgeführt werden können, die für die Seite gelten.

**SiteCatalyst**  - SiteCatalyst bietet Marketingexperten eine zentrale Stelle zur Messung, Analyse und Optimierung integrierter Daten aus allen Onlineinitiativen über mehrere Marketing-Kanal hinweg. Sie können mit Adobe SiteCatalyst Daten von AEM Sites analysieren.

**Tar Datenspeicherung (TarMK)**  - TarMK ist das Standardpersistenzsystem in AEM. Obwohl AEM für die Verwendung eines anderen Persistenzsystems (z. B. MongoDB) konfiguriert werden kann, hat TarMK gewisse Vorteile, da es für typische JCR-Anwendungsfälle leistungsoptimiert ist (also sehr schnell), ein Industriestandard-Datenformat verwendet kann schnell und einfach gesichert werden kann.

**Vorlage** : In AEM gibt eine Vorlage einen bestimmten Seitentyp an. Sie definiert die Struktur einer Seite (während sie normalerweise auch ein Miniaturbild und verschiedene Eigenschaften angibt). Beispielsweise könnten Sie unterschiedliche Vorlagen für Produktseiten, Sitemaps und Kontaktangaben verwenden.

**Workflow**  - Das AEM Workflow-System ermöglicht die Erstellung automatisierter Prozesse, die Seiten oder Assets beinhalten.
