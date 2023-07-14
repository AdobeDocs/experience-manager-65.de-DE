---
title: Beitragen zu AEM
description: AEM wird nach bewährten Methoden entwickelt, die häufig in großen Open-Source-Projekten eingesetzt werden
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 43fb4fa3-269a-4635-b055-4b7d787da21f
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '2672'
ht-degree: 48%

---

# Beitragen zu AEM{#contributing-to-aem}

## Entwicklungsmethode {#development-methodology}

AEM werden nach bewährten Methoden entwickelt, die in großen Open-Source-Projekten häufig eingesetzt werden. Viele Kernelemente in AEM Technologie-Stack werden tatsächlich als aktive Open-Source-Projekte wie Sling und Jackrabbit gepflegt, die zur Apache Software Foundation beigetragen haben. Ein wichtiger Aspekt dieses Geistes, der in AEM vorhanden ist, ist, dass Sie dazu ermutigt werden, die verfügbaren Mailinglisten und Online-Foren für direkte Interaktionen mit dem Entwicklungsteam zu nutzen.

Wenn Sie zu Komponenten von AEM beitragen, machen Sie sich mit AEM vertraut, wie Sie es bei der Mitarbeit an einem Open-Source-Projekt tun würden, und kommunizieren Sie mit dem vorhandenen Kernteam so, wie Sie es gerne tun würden, wenn Sie zu einem solchen Projekt beitragen möchten.

## Erforderliches Erlebnis {#required-experience}

Das HyperText Transfer Protocol (HTTP) ist für alles, was wir tun, von zentraler Bedeutung. Bevor Sie zu AEM beitragen, sollten Sie daher über ein tiefes Verständnis von HTTP verfügen, idealerweise in dem Maße, in dem Sie Ihre eigene Java™-Implementierung eines mehrprozessgestützten HTTP-Servers mit Thread-Pooling schreiben können. Sie sollten auch das HTTP/1.1-Keep-Alive-Verhalten verstehen und über eingehende Kenntnisse der Server-/Client-seitigen Interaktionen mit JavaScript verfügen, insbesondere über den asynchronen Interaktionsstil, der von AJAX repräsentiert wird.

Da Seitendynamik und interaktiver Inhalt der Schlüssel zum WM-Erlebnis sind, ist es wichtig, dass Sie das Dokumentobjektmodell und sein Potenzial für programmatische Manipulation als Reaktion auf Ereignisse möglichst gut verstehen. Sie sollten beispielsweise Kenntnisse über die Echtzeit-DOM-Manipulation und das Drag-and-Drop-Verhalten über mehrere Browser-Dokumente haben (z. B. über iframes).

Auf höchster Ebene sollten Sie über ein solides Verständnis von Folgendem verfügen:

* das [HTTP/1.1 Protokoll](https://www.ietf.org/rfc/rfc2616.txt)
* HTML (vorzugsweise [HTML5](https://html.spec.whatwg.org/))
* Cascading Style Sheets
* Extensible Markup Language (XML)
* Asynchrone JavaScript- und XML-Designmuster (AJAX)
* JavaScript-Objektnotation (JSON)
* Dokumentobjektmodell
* Stateful- und stateless-Interaktionen
* [Einheitliche Ressourcen-IDs](https://www.ietf.org/rfc/rfc2396.txt)
* Browsercookies
* und andere moderne Konzepte zur Web-Entwicklung

Der Technologiestapel von Adobe Experience Manager basiert auf dem [Apache Felix](https://felix.apache.org/documentation/index.html) OSGi-Container mit dem [Apache Sling](https://sling.apache.org/index.html) Web-Framework und bettet ein Java™ Content Repository ein ([JCR](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html)) basierend auf [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/jcr-api.html). Machen Sie sich mit diesen einzelnen Projekten und anderen Open-Source-Komponenten (z. B. Apache Lucene) vertraut, die in dem Bereich verwendet werden, in dem Sie beitragen möchten.

## Stammeswissen {#tribal-knowledge}

Bestimmte Konzepte und Leitprinzipien sind tief in der früheren Day-Kultur verwurzelt. In diesem Abschnitt werden einige der &quot;tief in die DNA eingebetteten&quot;Probleme aufgelistet, die Sie kennen sollten.

### Alles ist Inhalt {#everything-is-content}

Der Inhalt umfasst nicht nur alle Daten, die die Webanwendung speichert. Der Programmcode, die Bibliotheken, Skripte, Vorlagen, HTML, CSS, Bilder und Artefakte aller Art, alles und alles wird im Content Repository persistiert und über Package Manager und Package Share in Form von Paketen importiert/exportiert.

### Davids Modell {#david-s-model}

Die Art und Weise, wie Inhalte in einem Java™ Content Repository modelliert werden sollen, erfordert eine völlig andere Denkweise als die gängige Praxis in der Software-Industrie für die Datenmodellierung in der relationalen Welt. Eine Pflichtlektüre für jeden Neuling im Content-Management mit der JCR-Methode ist [David&#39;s Model: A guide for content modeling](https://wiki.apache.org/jackrabbit/DavidsModel).

### RESTfulness {#restfulness}

Der REST-Ansatz ist tief verwurzelt in dem, was wir tun. Dies bedeutet unter anderem, stateful Interaktionen zu vermeiden und zu bedenken, dass URIs endgültige Adressen für Inhalte und Dienste sind.

REST (REpresentational State Transfer) bezeichnet den Software-Architekturstil, auf dem das World Wide Web basiert. Es beschreibt die Schlüsselelemente, die das Web zum Funktionieren bringen, und bietet somit eine Reihe von Prinzipien für die Gestaltung webbasierter Software. Bei der Entwicklung einer API, die über das Internet verwendet werden soll, ist es daher sinnvoll, diese „Best Practices“ einzuhalten.

Da REST die Leitphilosophie für so viel von dem, was wir tun, bietet, sollten Sie es für wichtig halten, sich mit den Grundsätzen des RESTful-Designs vertraut zu machen. Ein guter Ausgangspunkt ist mit [Roy Fielding&#39;s Dissertation](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).

### Sling-Anforderungsauflösung {#sling-request-resolution}

Ein wesentlicher Aspekt zum Verständnis von AEM ist, wie eingehende Anforderungen sich auf das Inhalts- und Anwendungsverhalten beziehen, wie Inhalte im Content-Repository strukturiert sind und wo AEM nach der Anwendungslogik sucht, um die Anforderung zu bearbeiten. Informationen zum Apache [Sling-URL-Dekomposition](https://sling.apache.org/documentation/the-sling-engine/url-decomposition.html) und wie sie den REST-Architekturstil und seine statuslosen, zwischenspeicherbaren und überlagerten Systemeinschränkungen durchsetzt.

Die wichtigsten Aspekte bei der Anforderungsauflösung von Apache Sling sind, wie Anforderungen primär einer bestimmten Ressource im Content Repository zugeordnet werden, wie zusätzliche Eigenschaften der Anforderung zusammen mit den Eigenschaften dieser Inhaltsobjekte bestimmen, welcher Anwendungscode zum Rendern des Inhalts aufgerufen wird und wie Code in /apps den Code in /libs überschreibt.

### Schnellstart {#quickstart}

Kein Schritt drei: zum Installieren und Ausführen lädt man einfach die Schnellstart-JAR-Datei herunter und doppelklickt darauf. Es gibt keinen dritten Schritt. Für jede zusätzliche optionale Funktion sollte nur die Installation des entsprechenden Pakets über Package Share erforderlich sein.

Kleine Schnellstart-Größe: halten Sie die Größe der Schnellstart-JAR-Datei auf ein Minimum begrenzt. Nutzen Sie Bibliotheken intelligent und optimiert und verschieben Sie optionale Funktionen in Package Share.

Schnellere Startzeit: Wenn Sie eine Änderung vornehmen, die sich auf die Startzeit auswirken könnte, stellen Sie sicher, dass sie kürzer und nicht länger wird.

### Arithmetisches Mittel {#lean-and-mean}

Wir bevorzugen Code und Projekte, die leicht, klein, schnell und elegant sind. &quot;Gut genug&quot;ist nicht gut genug.

Wiederverwendung von Code: Unsere OSGi-basierte Produktarchitektur und die Philosophie &quot;Alles ist Inhalt&quot; bedeutet, dass wir ungewöhnlich gute Möglichkeiten zur Wiederverwendung von Code und Artefakten haben. Wir versuchen, diese Tatsache, wann immer möglich, zu nutzen, um die Funktionen schlank und mittelschwer zu halten.

Lose Kopplung: Wir bevorzugen lose gekoppelte Interaktionen gegenüber engen Abhängigkeiten und „unerwünschter Intimität“. Eine lockere Kopplung ermöglicht auch eine stärkere Wiederverwendung von Code.

### Das Demo nicht unterbrechen {#don-t-break-the-demo}

Machen Sie sich mit Demo-Skripten und Produktfunktionen vertraut, die am häufigsten in Demos angezeigt werden. Beachten Sie, dass nichts, was Sie tun, jemals die Funktion &quot;Demo-Skript&quot;beschädigen sollte. Das Kernprodukt sollte auch während der Entwicklung immer demo-fähig sein.

### Design für Zuverlässigkeit {#design-for-reliability}

Wir bemühen uns, Features in Fail-Soft-Art zu entwerfen und zu kodieren, sodass (zum Beispiel) ein Problem mit einem einzelnen DOM-Element nicht dazu führt, dass eine ganze Seite nicht gerendert wird. Mit anderen Worten: Machen Sie Dinge, die tödlich sein sollten, tödlich. Macht alles andere überlebensfähig. Machen Sie das Produkt &quot;verzeihend&quot;.

### Abnorm ist der neue Normalzustand {#abnormal-is-the-new-normal}

Verlassen Sie sich nicht auf Shutdown-Hooks, sorgen Sie für eine Bereinigung beim Start. Abnormale Beendigung ist normale Beendigung.

`shutdown == kill -9 == power outage`

### Seien Sie bereit für elastisches Clustering {#be-ready-for-elastic-clustering}

Seien Sie immer bereit für elastisches Clustering; immer davon ausgehen, dass es Clustering gibt. Im Allgemeinen bedeutet die Einhaltung aller im Inhalts-Repository vorhandenen Elemente die integrierte Clustering-Unterstützung.

### Entwerfen Sie für Abwärtskompatibilität {#design-for-backward-compatibility}

Nichts, was Sie tun, sollte den alten Code eines Kunden zerstören. Nur `/libs` sollte Produkt-Code enthalten, der während eines Upgrades aktualisiert werden kann. Die `/apps` -Abschnitt des Repositorys Projektcode ist und die `/etc` enthält benutzerdefinierte Konfigurationen, die beibehalten werden müssen. Im Allgemeinen sollten Sie nichts in `/apps`, `/content`und `/home`. Nach einer Aktualisierung sollten alter Projektcode, Konfigurationen und Inhalt weiterhin so funktionieren, wie es vor der Aktualisierung der Fall war.

Durch die Konzeption für die Abwärtskompatibilität wird außerdem sichergestellt, dass das Upgrade-Erlebnis der Einfachheit der ersten Installation entspricht. Einfaches Beenden von AEM, Ersetzen der Schnellstart-JAR-Datei und erneutes Starten von AEM sollte ausreichen. Mit einer schnell wachsenden Installationsbasis stellt die Effizienz der Aktualisierung einen immer größeren Vorteil dar.

Bestehende APIs können und sollten als veraltet markiert werden, wenn eine neuere, bessere Funktionalität diese ersetzt, alle APIs, die in einer früheren 5.x-Version veröffentlicht wurden, müssen weiterhin funktionsfähig bleiben, da sie möglicherweise in benutzerdefiniertem Anwendungs-Code verwendet werden. Solche APIs sollten nicht entfernt werden.

Die Abwärtskompatibilität sollte auch in Bezug auf die allgemeine Konsistenz der Inhaltsstruktur und des Benutzererlebnisses berücksichtigt werden.

## Grundlegende Konzepte {#core-concepts}

**Autoreninstanz** - Aus Sicherheits-, Governance- und anderen Gründen unterteilt eine Produktions-Site normalerweise Instanzen von AEM in Autoren- und Veröffentlichungsinstanzen. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM-Instanzen.

**Caching, Frying und Baking**: Traditionell sind die Konzepte des Baking oder Frying eine wichtige Unterscheidung zwischen verschiedenen Web Content-Managementsystemen. Im CMS-Jargon bezieht sich &quot;Backen&quot;auf das Konzept der Datenübergabe an statische Dateien zur Veröffentlichungszeit, während &quot;Frittieren&quot;auf das Konzept der Datenverarbeitung zur endgültigen Präsentation zur Anforderungszeit (d. h. gerade rechtzeitig) verweist.

**Clustering und Lastenausgleich** - Um die Verfügbarkeit zu erhöhen und die Leistung einer Produktionsumgebung zu verbessern, ist es üblich, mehrere Autoren- und/oder Veröffentlichungsinstanzen (in Clustern) zu kombinieren, indem sie sie entweder verschiedenen Benutzergruppen zur Verfügung gestellt oder durch Lastenausgleich hinter einer Dispatcher-Konfiguration bereitgestellt werden.

Es ist auch möglich, mehrere Instanzen des Content-Repositorys zu einer JCR-Lösung mit *hoher Verfügbarkeit* zu kombinieren, die dann in Ihre AEM-Lösung integriert werden kann, um den Schutz vor Hardware- und Softwarefehlern zu maximieren. Weitere Informationen finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter).

**Komponente**: In AEM ist eine Komponente ein Objekttyp, dessen Instanzen in der Regel durch Ziehen und Ablegen z. B. im Sidekick erstellt werden können. So enthalten beispielsweise mit AEM ausgelieferte Standardkomponenten die Komponenten Text, Titel, Tag Cloud, Karussell, Bild und Liste, die alle zur Laufzeit über den Sidekick verfügbar sind.

**Content Finder (Inhaltssuche)**: Im Authoring-Modus ist der Content Finder ein spezieller Fensterbereich (Rahmen) auf der linken Seite der Seite, der je nach der oben ausgewählten Registerkarte Listen mit Bildern, Dokumenten, Flash-Assets, Seiten, Absätzen oder Repository-Ressourcen anzeigt, die Sie per Drag-and-Drop aus dem Content Finder auf die Seite ziehen können, an der Sie gerade arbeiten (rechts).

**Digitale Assets**: In AEM sind digitale Assets (in der Regel) Bilder und Rich-Media-Dateien. Weitere Informationen finden Sie unter Arbeiten mit digitalen Assets in DAM.

**Dispatcher** - Der Dispatcher ist sowohl ein Caching- als auch ein Lastenausgleichswerkzeug und bietet bestimmte Sicherheitsgarantien.

**ExtJS-Widgets**: Die meisten Elemente der Benutzeroberfläche in AEM verwenden ExtJS, eine in JavaScript geschriebene Widget-Bibliothek von Drittanbietern. ExtJS bietet leistungsstarke, anpassbare Benutzeroberflächen-Widgets und ein gut konzipiertes und erweiterbares Komponentenmodell.

**JCR, Java™ Content Repository** - Die Java™ Content Repository-Spezifikation (JSR-283) bietet sowohl ein abstraktes Datenmodell als auch eine Anwendungsprogrammierschnittstelle zur Realisierung eines massiv skalierbaren NoSQL-Datenrepository, das Funktionen eines Dateisystems und einer Objektdatenbank kombiniert. Obwohl Sie JSR-283 nicht vollständig verstehen müssen, sollten Sie sich die Zeit nehmen, sich mit den grundlegenden Funktionen von JCR und dem zugrunde liegenden Datenmodell vertraut zu machen, da JCR die &quot;Alles ist Inhalt&quot;-Philosophie von AEM ermöglicht.

Im Wesentlichen ist JCR ein System von Knoten und Eigenschaften, in dem Knoten von anderen Knoten erben können und der gesamte Inhalt als *Eigenschaftswerte* gespeichert wird. Beachten Sie, dass JCR neben der normalen Vererbung ein Konzept von &quot;Mixin&quot;-Knoten ermöglicht, das die Modellierung der mehrfachen Vererbung ermöglicht.

JCR verfügt über mehrere vordefinierte Knotentypen und Eigenschaftstypen, aber im Allgemeinen ist das Typisierungssystem flexibel. Eine der Stärken von JCR besteht darin, dass es sowohl strukturierte als auch unstrukturierte Inhalte mit gleicher Leichtigkeit speichert/verwaltet. Das heißt, JCR kann sehr strukturierte Daten aufnehmen, kann aber auch beliebige dynamische Datenstrukturen ohne Schemaeinschränkungen aufnehmen.

Die JavaDoc für die Java™-API von JCR lautet [here](https://jackrabbit.apache.org/jcr/jcr-api.html).

Bevor Sie versuchen, die JavaDoc- oder die JCR-Spezifikation selbst zu lesen, sollten Sie sich diese [High-Level-Erklärung](/help/sites-developing/the-basics.md#java-content-repository) von JCR ansehen, die von Adobe Experience Services implementiert wird.

**Multi-Site Manager (MSM)**: Die MSM-Funktion von AEM unterstützt Kunden bei der Bearbeitung mehrsprachiger und multinationaler Inhalte und ermöglicht es ihnen, zentralisiertes Branding mit lokalisierten Inhalten in Einklang zu bringen.

**OSGi** - OSGi ist die dienstbasierte Laufzeittechnologie, die die Grundlage für die modularisierte Java™-Entwicklung in AEM bietet. Es ist ein Framework, das nicht nur eine hochdynamische (und sichere) Classloading- und Execution-Umgebung für Coderessourcen (bekannt als Bundle) bietet, sondern auch volle Kontrolle über die Sichtbarkeit und den Lebenszyklus der verschiedenen Services, die von Bundles bereitgestellt werden. Eine Service-Registrierung stellt ein Kooperationsmodell für Bundles bereit, das Lebenszyklusdynamik (und Versionsanforderungen) berücksichtigt. OSGi löst viele der Probleme, die die Anwendungsserver lösen sollten, tut dies jedoch auf einfache, hochdynamische Weise, was es beispielsweise ermöglicht, Dienste heiß bereitzustellen (sodass der neue Code sofort verfügbar ist, ohne den Server neu zu starten).

**Parsys, Absatzsystem**: Das Absatzsystem (parsys) ist eine zusammengesetzte Komponente, die es Autoren ermöglicht, einer Seite Komponenten verschiedener Typen hinzuzufügen, und die andere Absatzkomponenten enthält. Jeder Absatztyp wird als eine Komponente dargestellt. Das Absatzsystem selbst ist auch eine Komponente, die die anderen Absatzkomponenten enthält.

**Mikrokernel** Jeder Arbeitsbereich im Repository kann separat konfiguriert werden, um seine Daten über einen bestimmten Mikrokernel zu speichern (eine Klasse, die das Lesen und Schreiben der Daten verwaltet). Ebenso kann der Repository-weite Versionsspeicher unabhängig für die Verwendung eines bestimmten Mikrokernels konfiguriert werden. Es stehen verschiedene Mikrokernels zur Verfügung, die Daten in verschiedenen Dateiformaten oder relationalen Datenbanken speichern können. (Beispielsweise gibt es Persistenzmanager für MongoDB, DB2® oder Oracle) Der Standard-Mikrokernel für AEM ist TarMK (siehe weiter unten).

**Veröffentlichungsinstanz**: Aus Gründen der Sicherheit, der Governance und aus anderen Gründen unterteilt eine Produktions-Website typischerweise Instanzen von AEM in Autoren- und Veröffentlichungsinstanzen. Weitere Informationen zur Bereitstellungsarchitektur (einschließlich Autoren-/Veröffentlichungsinstanzen) finden Sie in der Dokumentation zu AEM-Instanzen.

**Schnellstart**: Im Gegensatz zu vielen anderen Programmen installieren Sie AEM mithilfe einer einzelnen selbstextrahierenden JAR-Schnellstart-Datei. Wenn Sie zum ersten Mal auf die JAR-Datei doppelklicken, wird alles, was Sie benötigen, automatisch installiert. Die Schnellstart-JAR enthält alle für das CRX-Repository erforderlichen Dateien (einschließlich Verwaltungseinrichtungen), virtuelle Repository-Dienste, Index- und Suchdienste, Workflow-Services, Sicherheit und einen Webserver sowie die CQ Servlet Engine (CQSE) und alle AEM-Dienste. Es sind keine weiteren Dateien zu installieren: Der Schnellstart ist eigenständig.

Wenn Sie den Schnellstart zum ersten Mal starten, wird im Hintergrund ein ganzes JCR-kompatibles Repository erstellt, was einige Minuten dauern kann. Nach diesem ersten Start sind nachfolgende Startups viel schneller, da die Repository-Infrastruktur bereits eingerichtet wurde.

Viele Startoptionen (z. B. die Nummer des aktiven Ports und ob die fragliche AEM-Instanz eine Veröffentlichungsinstanz oder eine Autoreninstanz sein soll und vieles mehr) können durch entsprechendes Umbenennen der Schnellstart-Datei gesteuert werden. Um eine Liste der diesbezüglichen Optionen anzuzeigen, führen Sie die JAR mit &quot;-help&quot;in der Befehlszeile aus:

```shell
java -jar <quickstartfilename>.jar -help
```

**Replikationsagenten** - Replikationsagenten sind von zentraler Bedeutung für AEM als Mechanismus zum Veröffentlichen (Aktivieren) von Inhalten von einem Autor in einer Veröffentlichungsumgebung. Inhalt aus dem Dispatcher-Cache leeren; vom Benutzer generierte Inhalte (z. B. Formulareingaben) aus der Veröffentlichungsumgebung in die Autorenumgebung zurückgeben.

**Strukturvorlage**: Eine Strukturvorlage dient zur Erstellung eines Formulars (einer Struktur), dessen Felder die gewünschte Seitenstruktur bilden. Anhand dieses Formulars können Sie ganz einfach auf dieser Struktur basierende Seiten erstellen.

**Segmentierung**: Besucher von Websites haben unterschiedliche Interessen und Ziele, wenn sie eine Website besuchen. Die Ziele der Besucher zu verstehen und ihre Erwartungen zu erfüllen, ist eine wichtige Erfolgsvoraussetzung für das Online-Marketing. Die Segmentierung hilft dabei, die Details eines Besuchers zu analysieren und zu charakterisieren.

**Sidekick**: Der Sidekick ist ein palettenartiges schwebendes Fenster, das auf der bearbeitbaren Seite erscheint, von dem aus neue Komponenten gezogen und Aktionen für die Seite ausgeführt werden können.

**Site Catalyst**: SiteCatalyst bietet Marketern einen Ort, an dem sie integrierte Daten aus allen Online-Initiativen über mehrere Marketing-Kanäle messen, analysieren und optimieren können. Sie können mit Adobe SiteCatalyst Daten von AEM Sites analysieren.

**Tar-Speicher (TarMK)**: TarMK ist das standardmäßige Persistenzsystem in AEM. Obwohl AEM für die Verwendung eines anderen Persistenzsystems konfiguriert werden können (z. B. MongoDB), bietet TarMK gewisse Vorteile, da es leistungsoptimiert für typische JCR-Anwendungsfälle ist (daher schnell), ein branchenübliches Datenformat verwendet und schnell und einfach gesichert werden kann.

**Vorlage**: In AEM gibt eine Vorlage einen bestimmten Seitentyp an. Sie definiert die Struktur einer Seite (während sie normalerweise auch ein Miniaturbild und verschiedene Eigenschaften angibt). Sie können beispielsweise separate Vorlagen für Produktseiten, Sitemaps und Kontaktinformationen verwenden.

**Workflow**: Das AEM-Workflow-System ermöglicht die Erstellung von automatisierten Prozessen mit Seiten oder Assets.
