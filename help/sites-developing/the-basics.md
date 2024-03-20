---
title: Grundlegende AEM-Konzepte
description: Ein Überblick über die grundlegenden Konzepte der Adobe Experience Manager (AEM)-Struktur und der damit verbundenen Entwicklung, einschließlich Informationen zu JCR, Sling, OSGi, Dispatcher, Workflows und MSM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: f6f32290-422e-4037-89d8-d9f414332e8e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3251'
ht-degree: 73%

---

# Grundlegende AEM-Konzepte {#aem-core-concepts}

>[!NOTE]
>
>Bevor Sie sich mit den Kernkonzepten von Adobe Experience Manager (AEM) befassen, empfiehlt Adobe, das WKND-Tutorial im Abschnitt [Erste Schritte bei der Entwicklung von AEM Sites](/help/sites-developing/getting-started.md) Dokument. Es enthält einen Überblick über den AEM Entwicklungsprozess und eine Einführung in die Kernkonzepte.

## Voraussetzungen für die Entwicklung in AEM {#prerequisites-for-developing-on-aem}

Sie benötigen die folgenden Fähigkeiten zur Entwicklung auf Basis von AEM:

* Grundlegende Kenntnisse der Web-Anwendungstechniken, einschließlich:

   * Anfrage-Antwort-Zyklus (XMLHttpRequest/XMLHttpResponse)
   * HTML
   * CSS
   * JavaScript

* Kenntnisse des Experience Servers (CRX) einschließlich des Content Explorers
* Für die Entwicklung in der klassischen Benutzeroberfläche sind grundlegende Kenntnisse von JSP (JavaServer Pages) einschließlich der Fähigkeit, einfache JSP-Beispiele zu verstehen und zu modifizieren, erforderlich.

Es wird außerdem empfohlen, dass Sie die [Richtlinien und Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md) lesen und befolgen.

## Java™ Content-Repository {#java-content-repository}

Der Java™ Content-Repository-Standard (JCR) [JSR 283](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/index.html) legt eine hersteller- und implementierungsunabhängige Methode für den bidirektionalen Zugriff auf Inhalte auf einer granularen Ebene in einem Content-Repository fest.

Die Leitung der Spezifikation liegt bei Adobe Research (Schweiz) AG.

Das [JCR API 2.0](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/index.html)-Paket, javax.jcr.&amp;ast; wird für den direkten Zugriff und die Bearbeitung von Repository-Inhalten verwendet.

## Experience Server (CRX) und Jackrabbit {#experience-server-crx-and-jackrabbit}

Der Experience Server stellt die Experience Services bereit, auf denen AEM basiert und die zum Erstellen benutzerdefinierter Anwendungen verwendet werden können. Außerdem wird das Content-Repository auf Basis von Jackrabbit eingebettet.

[Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) ist eine vollständig konforme Open-Source-Implementierung der JCR-API 2.0.

## Sling-Anfrageverarbeitung {#sling-request-processing}

### Einführung in Sling {#introduction-to-sling}

AEM wird mithilfe von [Sling](https://sling.apache.org/index.html), ein Framework für Webanwendungen, das auf REST-Prinzipien basiert und eine einfache Entwicklung inhaltsorientierter Anwendungen ermöglicht. Sling verwendet ein JCR-Repository, z. B. Apache Jackrabbit oder, falls AEM vorhanden ist, das CRX Content Repository als Datenspeicher. Sling ist Teil der Apache Software Foundation – weitere Informationen finden Sie bei Apache.

Bei Verwendung von Sling ist der Typ des zu rendernden Inhalts nicht die erste Verarbeitungsüberlegung. Stattdessen ist die Hauptüberlegung, ob die URL zu einem Inhaltsobjekt aufgelöst wird, für das dann ein Skript gefunden werden kann, um das Rendering durchzuführen. Dies bietet Autorinnen und Autoren von Web-Inhalten eine hervorragende Unterstützung beim Erstellen von Seiten, die einfach an ihre Anforderungen angepasst werden können.

Die Vorteile dieser Flexibilität zeigen sich in Programmen mit einer großen Auswahl verschiedener Inhaltselemente oder wenn Sie Seiten benötigen, die einfach angepasst werden können. Insbesondere bei der Implementierung eines Web Content Management-Systems wie WCM in der AEM-Lösung.

Siehe [Entdecken Sie Sling in 15 Minuten](https://sling.apache.org/documentation/getting-started/discover-sling-in-15-minutes.html) für die ersten Schritte zur Entwicklung mit Sling.

Im folgenden Diagramm wird die Auflösung des Sling-Skripts erläutert. Es zeigt, wie Sie von einer HTTP-Anforderung zum Inhaltsknoten, vom Inhaltsknoten zum Ressourcentyp, vom Ressourcentyp zum Skript gelangen und welche Skriptvariablen verfügbar sind.

![Verstehen der Auflösung des Apache Sling-Skripts](assets/sling-cheatsheet-01.png)

Im folgenden Diagramm werden alle verborgenen, aber leistungsstarken Anforderungsparameter erläutert, die Sie beim Umgang mit dem SlingPostServlet verwenden können. Sie enthält den Standard-Handler für alle POST-Anforderungen, der Ihnen unzählige Möglichkeiten zum Erstellen, Ändern, Löschen, Kopieren und Verschieben von Knoten im Repository bietet.

![Verwenden des SlingPostServlet](assets/sling-cheatsheet-02.png)

### Sling ist inhaltszentriert {#sling-is-content-centric}

Sling ist *inhaltzentriert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anfrage auf den Inhalt in Form einer JCR-Ressource (eines Repository-Knotens) abgebildet wird:

* das erste Ziel ist die Ressource (JCR-Knoten), die den Inhalt enthält
* Zweitens befindet sich die Darstellung oder das Skript aus den Ressourceneigenschaften, die mit bestimmten Teilen der Anforderung kombiniert sind (z. B. Selektoren und/oder die Erweiterung).

### RESTful Sling {#restful-sling}

Aufgrund der inhaltsorientierten Philosophie implementiert Sling einen REST-orientierten Server und bietet damit ein neues Konzept für Webanwendungs-Frameworks. Die Vorteile:

* RESTful, nicht nur an der Oberfläche; Ressourcen und Darstellungen werden innerhalb des Servers korrekt modelliert
* entfernt ein oder mehrere Datenmodelle

   * zuvor war Folgendes erforderlich: URL-Struktur, Geschäftsobjekte, DB-Schema;
   * dies wird jetzt reduziert auf: URL = Ressource = JCR-Struktur

### URL-Zerlegung {#url-decomposition}

In Sling wird die Verarbeitung durch die URL der Benutzeranfrage gesteuert. Dies definiert den Inhalt, der von den entsprechenden Skripten angezeigt werden soll. Zu diesem Zweck werden Informationen aus der URL extrahiert.

Wenn Sie die folgende URL analysieren:

```xml
https://myhost/tools/spy.printable.a4.html/a/b?x=12
```

Sie lässt sich in ihre Bestandteile zerlegen:

| protocol | host | content path | selectors | Erweiterung |  | Suffix |  | params |
|---|---|---|---|---|---|---|---|---|
| https:// | Myhost  | tools/spy | .printable.a4. | html | / | a/b | ? | x=12 |

**protocol** – HTTP

**host** – Name der Website.

**content path** – Pfad, der den Inhalt angibt, der gerendert werden soll. Wird mit der -Erweiterung verwendet. In diesem Beispiel übersetzen sie in `tools/spy.html`.

**Selektoren** Wird für alternative Methoden zum Rendern des Inhalts verwendet, in diesem Beispiel eine druckerfreundliche Version im A4-Format.

**extension** – Inhaltsformat; gibt außerdem das Skript an, das zum Rendern verwendet werden soll.

**suffix** – kann verwendet werden, um zusätzliche Information anzugeben.

**params** Alle für dynamischen Inhalt erforderlichen Parameter.

#### Von URL zu Inhalt und Skripten {#from-url-to-content-and-scripts}

Unter Verwendung dieser Prinzipien:

* das Mapping verwendet den aus der Anfrage extrahierten Inhaltspfad, um die Ressource zu lokalisieren
* wenn die entsprechende Ressource gefunden wurde, wird der Sling-Ressourcentyp extrahiert und zum Suchen des Skripts verwendet, das zum Rendern des Inhalts verwendet werden soll

Die folgende Abbildung zeigt den verwendeten Mechanismus, der in den folgenden Abschnitten ausführlicher erläutert wird.

![chlimage_1-86](assets/chlimage_1-86a.png)

Mit Sling geben Sie an, welches Skript eine bestimmte Entität rendert (indem Sie die Eigenschaft `sling:resourceType` im JCR-Knoten festlegen). Dieser Mechanismus bietet mehr Freiheit als einer, in dem das Skript auf die Datenentitäten zugreift (wie es eine SQL-Anweisung in einem PHP-Skript tun würde), da eine Ressource mehrere Ausgabedarstellungen haben kann.

#### Zuordnen von Anfragen zu Ressourcen {#mapping-requests-to-resources}

Die Anfrage wird zerlegt und die notwendigen Informationen werden extrahiert. Das Repository wird nach der angeforderten Ressource (Inhaltsknoten) durchsucht:

* Zunächst prüft Sling, ob ein Knoten an der in der Anfrage angegebenen Position existiert; z. B. `../content/corporate/jobs/developer.html`
* Wird kein Knoten gefunden, dann wird die Erweiterung entfernt und die Suche wiederholt; z. B., `../content/corporate/jobs/developer`
* Wenn kein Knoten gefunden wird, gibt Sling den HTTP-Code 404 (Nicht gefunden) zurück.

Sling erlaubt auch anderen Elementen als JCR-Knoten, als Ressourcen zu fungieren, dies ist jedoch eine erweiterte Funktion.

### Auffinden des Skripts {#locating-the-script}

Wenn die entsprechende Ressource (Inhaltsknoten) gefunden wird, wird der **Sling-Ressourcentyp** extrahiert. Dies ist ein Pfad, der das Skript findet, das zum Rendern des Inhalts verwendet werden soll.

Der vom `sling:resourceType` angegebene Pfad kann wie folgt sein:

* absolut oder
* relativ zu einem Konfigurationsparameter

  Relative Pfade werden von Adobe empfohlen, da sie die Portabilität erhöhen.

Alle Sling-Skripte werden in Unterordnern von `/apps` oder `/libs`, die in dieser Reihenfolge durchsucht wird (siehe [Anpassen von Komponenten und anderen Elementen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

Einige andere zu beachtende Punkte sind:

* Wenn die Methode (GET, POST) erforderlich ist, wird sie in Großbuchstaben wie gemäß der HTTP-Spezifikation angegeben, z. B. jobs.POST.esp (siehe unten).
* Es werden verschiedene Skript-Engines unterstützt:

   * HTL (HTML-Vorlagensprache – das von Adobe Experience Manager bevorzugte und empfohlene Server-seitige Vorlagensystem für HTML): `.html`
   * ECMAScript (JavaScript)-Seiten (Server-seitige Ausführung): `.esp, .ecma`
   * Java™ Server-Seiten (Server-seitige Ausführung): `.jsp`
   * Java™ Servlet-Compiler (Server-seitige Ausführung): `.java`
   * JavaScript-Vorlagen (Client-seitige Ausführung): `.jst`

Die Liste der von der angegebenen Instanz von AEM unterstützten Skript-Engines wird in der Felix Management Console aufgeführt (`http://<host>:<port>/system/console/slingscripting`).

Darüber hinaus unterstützt Apache Sling die Integration mit anderen gängigen Skript-Engines (z. B. Groovy, JRuby, Freemarker) und bietet eine Möglichkeit zur Integration neuer Skript-Engines.

Unter Verwendung des obigen Beispiels, wenn der `sling:resourceType` `hr/jobs` lautet:

* GET/HEAD-Anfragen und URLs, die auf .HTML enden (Standardanfragetypen, Standardformat)

  Das Skript lautet „/apps/hr/jobs/jobs.esp“. Der letzte Abschnitt von „sling:resourceType“ bildet den Dateinamen.

* POST-Anfragen (alle Anfragetypen außer GET/HEAD, der Methodenname muss in Großbuchstaben angegeben werden)

  POST wird im Skriptnamen verwendet.

  Das Skript ist `/apps/hr/jobs/jobs.POST.esp`.

* URLs in anderen Formaten, die nicht auf .html enden

  Beispiel: `../content/corporate/jobs/developer.pdf`

  Das Skript ist `/apps/hr/jobs/jobs.pdf.esp`. Das Suffix wird zum Skriptnamen hinzugefügt.

* URLs mit Selektoren

  Selektoren können verwendet werden, um denselben Inhalt in einem alternativen Format anzuzeigen. Beispielsweise eine druckerfreundliche Version, einen RSS-Feed oder eine Zusammenfassung.

  Wenn Sie sich eine druckerfreundliche Version ansehen, in der der Selektor *print*, wie in `../content/corporate/jobs/developer.print.html`

  Das Skript ist `/apps/hr/jobs/jobs.print.esp`. Der Selektor wird zum Skriptnamen hinzugefügt.

* Wenn kein sling:resourceType definiert ist, dann:

   * Der Inhaltspfad wird verwendet, um nach einem geeigneten Skript zu suchen (wenn der pfadbasierte ResourceTypeProvider aktiv ist).

     Zum Beispiel würde das Skript für `../content/corporate/jobs/developer.html` eine Suche in `/apps/content/corporate/jobs/` erzeugen.

   * wird der primäre Knotentyp verwendet.

* Wenn kein Skript gefunden wird, wird das Standardskript verwendet.

  Die Standardausgabe wird als Nur-Text (.txt), HTML (.html) und JSON (.json) unterstützt, die alle die Eigenschaften des Knotens auflisten (entsprechend formatiert). Die Standardversion für die Erweiterung „.res“ oder für Anfragen ohne Anfrageerweiterung besteht darin, die Ressource (sofern möglich) zu spoolen.
* Für die HTTP-Fehlerbehandlung (Codes 403 oder 404) sucht Sling nach einem Skript in:

   * am Speicherort „/apps/sling/servlet/errorhandler“ für [angepasste Skripte](/help/sites-developing/customizing-errorhandler-pages.md)
   * oder am Speicherort der Standardskripte „/libs/sling/servlet/errorhandler/403.esp“ bzw. „404.esp“.

Wenn mehrere Skripte für eine bestimmte Anfrage gelten, wird das Skript mit der besten Übereinstimmung ausgewählt. Je genauer eine Übereinstimmung ist, desto besser ist sie. Mit anderen Worten: Je mehr Selektor-Treffer, desto besser, unabhängig von einer Übereinstimmung bei Anfrageerweiterung oder Methodenname.

Betrachten Sie beispielsweise eine Anfrage zum Zugriff auf die Ressource
`/content/corporate/jobs/developer.print.a4.html`
des Typs
`sling:resourceType="hr/jobs"`

Angenommen, Sie haben die folgende Liste von Skripten am richtigen Speicherort:

1. `GET.esp`
1. `jobs.esp`
1. `html.esp`
1. `print.esp`
1. `print.html.esp`
1. `print/a4.esp`
1. `print/a4/html.esp`
1. `print/a4.html.esp`

Dann wäre die Reihenfolge der Bevorzugung (8) - (7) - (6) - (5) - (4) - (3) - (2) - (1).

Zusätzlich zu den Ressourcentypen (primär definiert durch die Eigenschaft `sling:resourceType`) gibt es auch den Supertyp der Ressource. Dies wird durch die Variable `sling:resourceSuperType` -Eigenschaft. Diese Supertypen werden ebenfalls berücksichtigt, wenn Sie versuchen, ein Skript zu finden. Der Vorteil von Ressourcensupertypen besteht darin, dass sie eine Hierarchie von Ressourcen bilden können, wobei der Standard-Ressourcentyp `sling/servlet/default` (von den Standard-Servlets verwendet) effektiv der Stamm ist.

Der Ressourcensupertyp einer Ressource kann auf zwei Arten definiert werden:

* durch die Eigenschaft `sling:resourceSuperType` der Ressource.
* durch die Eigenschaft `sling:resourceSuperType` des Knotens, auf den der `sling:resourceType` zeigt.

Zum Beispiel:

* /

   * eine
   * b

      * sling:resourceSuperType = a

   * c

      * sling:resourceSuperType = b

   * x

      * sling:resourceType = c

   * y

      * sling:resourceType = c
      * sling:resourceSuperType = a

Die Typhierarchie von:

* `/x`
   * ist `[ c, b, a, <default>]`,
* während für `/y`
   * die Hierarchie `[ c, a, <default>]` lautet.

Grund hierfür ist, dass `/y` die Eigenschaft `sling:resourceSuperType` aufweist, während `/x` sie nicht aufweist und daher der Obertyp vom Ressourcentyp übernommen wird.

#### Sling-Skripte können nicht direkt aufgerufen werden {#sling-scripts-cannot-be-called-directly}

In Sling können Skripte nicht direkt aufgerufen werden, da dies das strikte Konzept eines REST-Servers beeinträchtigen würde. Es würden nämlich Ressourcen und Darstellungen vermischt werden.

Wenn Sie die Repräsentation (das Skript) direkt aufrufen, blenden Sie die Ressource in Ihrem Skript aus, sodass das Framework (Sling) nicht mehr davon weiß. Sie verlieren so bestimmte Funktionen:

* automatische Handhabung von HTTP-Methoden außer GET, einschließlich:

   * POST, PUT, DELETE, die mit einer Sling-Standardimplementierung behandelt werden
   * Das `POST.jsp`-Skript in Ihrem sling:resourceType-Speicherort

* Ihre Code-Architektur ist nicht mehr so sauber oder so klar strukturiert, wie sie es sein sollte. Dies ist besonders wichtig für die Entwicklung in großem Maßstab.

### Sling-API {#sling-api}

Hierbei wird das Sling-API-Paket „org.apache.sling“ verwendet.&amp;ast; und -Tag-Bibliotheken.

### Referenzieren von vorhandenen Elementen mithilfe von sling:include {#referencing-existing-elements-using-sling-include}

Eine letzte Überlegung ist die Notwendigkeit, auf vorhandene Elemente innerhalb der Skripte zu verweisen.

Komplexere Skripte (Aggregat-Skripte) müssen auf mehrere Ressourcen zugreifen (z. B. Navigation, Seitenleiste, Fußzeile, Elemente einer Liste) und dies durch Einbeziehung der *resource*.

Verwenden Sie dazu sling:include(&quot;/&lt;path>/&lt;resource>&quot;). Dies umfasst effektiv die Definition der referenzierten Ressource, wie in der folgenden Anweisung, die auf eine vorhandene Definition für das Rendern von Bildern verweist:

```xml
%><sling:include resourceType="geometrixx/components/image/img"/><%
```

## OSGI {#osgi}

OSGi definiert eine Architektur für die Entwicklung und Bereitstellung modularer Anwendungen und Bibliotheken (auch Dynamic Module System für Java™ genannt). Mit OSGi-Containern können Sie Ihre Anwendung in einzelne Module unterteilen (JAR-Dateien mit zusätzlichen Metainformationen und so genannten Bundles in der OSGi-Terminologie) und die Querabhängigkeiten zwischen ihnen verwalten mit:

* Services, die innerhalb des Containers implementiert sind
* ein Vertrag zwischen dem Container und Ihrer Anwendung

Diese Services und Verträge bieten eine Architektur, die es einzelnen Elementen ermöglicht, sich dynamisch für die Zusammenarbeit zu entdecken.

Ein OSGi-Framework bietet Ihnen dann dynamisches Laden/Entladen, Konfiguration und Steuerung dieser Bundles, ohne dass ein Neustart erforderlich ist.

>[!NOTE]
>
>Ausführliche Informationen zur OSGi-Technologie finden Sie auf der [OSGi-Website](https://www.osgi.org).
>
>Speziell die Seite mit grundlegenden Informationen beinhaltet eine Sammlung von Präsentationen und Tutorials.

Diese Architektur ermöglicht es Ihnen, Sling um anwendungsspezifische Module zu erweitern. Sling, und daher CQ5, verwendet die [Apache Felix](https://felix.apache.org/documentation/index.html)-Implementierung von OSGI (Open Services Gateway Initiative) und basiert auf der OSGi Service Platform Release 4 Version 4.2. Beides sind Sammlungen von OSGi-Bundles, die in einem OSGi-Framework ausgeführt werden.

Auf diese Weise können Sie die folgenden Aktionen für beliebige Pakete innerhalb Ihrer Installation durchführen:

* install
* Starten
* Stoppen
* Aktualisieren
* uninstall
* den Status anzeigen
* Greifen Sie auf detailliertere Informationen (z. B. symbolischen Namen, Version und Speicherort) zu den jeweiligen Bundles zu.

Siehe [die Web-Konsole](/help/sites-deploying/web-console.md), [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md), und [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) für weitere Informationen.

## Entwicklungsobjekte in der AEM-Umgebung {#development-objects-in-the-aem-environment}

Folgendes ist für die Entwicklung von Interesse:

**Element** Ein Element ist entweder ein Knoten oder eine Eigenschaft.

Detaillierte Informationen zum Bearbeiten von Item-Objekten finden Sie unter [Java™-Dokumente](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html) der Schnittstelle javax.jcr.Item

**Knoten (und ihre Eigenschaften)** Knoten und ihre Eigenschaften sind in der JCR API 2.0-Spezifikation (JSR 283) definiert. Sie speichern Inhalte, Objektdefinitionen, Rendering-Skripte und andere Daten.

Knoten definieren die Inhaltsstruktur, und ihre Eigenschaften speichern den tatsächlichen Inhalt und die Metadaten.

Inhaltsknoten steuern das Rendering. Sling ruft den Inhaltsknoten von der eingehenden Anfrage ab. Die Eigenschaft „sling:resourceType“ dieses Knotens verweist auf die zu verwendende Sling-Rendering-Komponente.

Ein Knoten, bei dem es sich um einen JCR-Namen handelt, wird in der Sling-Umgebung auch als Ressource bezeichnet.

Um beispielsweise die Eigenschaften des aktuellen Knotens abzurufen, können Sie den folgenden Code in Ihrem Skript verwenden:

`PropertyIterator properties = currentNode.getProperties();`

Der currentNode ist das aktuelle Knotenobjekt.

Weitere Informationen zum Bearbeiten von Knotenobjekten finden Sie unter [Java™-Dokumente](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html).

**Widget** In AEM werden sämtliche Benutzereingaben von Widgets verwaltet. Diese werden häufig verwendet, um die Bearbeitung eines Inhaltselements zu steuern.

Dialogfelder werden durch die Kombination von Widgets erstellt.

AEM wurde mit der ExtJS-Bibliothek von Widgets entwickelt.

**Dialog** Ein Dialogfeld ist eine spezielle Art von Widget.

Um Inhalte zu bearbeiten, verwendet AEM Dialogfelder, die vom Anwendungsentwickler definiert wurden. Diese kombinieren eine Reihe von Widgets, um der Benutzerin oder dem Benutzer alle Felder und Aktionen darzustellen, die zum Bearbeiten des zugehörigen Inhalts erforderlich sind.

Dialogfelder werden auch zur Bearbeitung von Metadaten und von verschiedenen Admin-Tools verwendet.

**Komponente** Eine Softwarekomponente ist ein Systemelement, das einen vordefinierten Dienst oder ein vordefiniertes Ereignis bietet und in der Lage ist, mit anderen Komponenten zu kommunizieren.

In AEM wird eine Komponente häufig zum Rendern des Inhalts einer Ressource verwendet. Wenn es sich bei der Ressource um eine Seite handelt, wird die Komponente, die sie rendert, als Komponente der obersten Ebene oder als Seitenkomponente bezeichnet. Eine Komponente muss jedoch weder Inhalte rendern noch mit einer bestimmten Ressource verknüpft sein. Beispielsweise zeigt eine Navigationskomponente Informationen über mehrere Ressourcen an.

Die Definition einer Komponente umfasst Folgendes:

* den Code, der zum Rendern des Inhalts verwendet wird
* ein Dialogfeld für die Benutzereingabe und die Konfiguration des resultierenden Inhalts.

**Vorlage** Eine Vorlage ist die Grundlage für einen bestimmten Seitentyp. Beim Erstellen einer Seite auf der Registerkarte Websites muss der Benutzer eine Vorlage auswählen. Die neue Seite wird dann durch Kopieren dieser Vorlage erstellt.

Eine Vorlage ist eine Hierarchie von Knoten, die dieselbe Struktur wie die zu erstellende Seite aufweist, jedoch keinen tatsächlichen Inhalt hat.

Sie definiert die Seitenkomponente, die zum Rendern der Seite verwendet wird, und den Standardinhalt (primären Top-Level-Inhalt). Der Inhalt definiert, wie er gerendert wird, da AEM inhaltsorientiert ist.

**Seitenkomponente (Komponente auf oberster Ebene)** Die Komponente, die zum Rendern der Seite verwendet werden soll.

**Seite** Eine Seite ist eine „Instanz“ einer Vorlage.

Eine Seite hat einen Hierarchieknoten vom Typ cq:Page und einen Inhaltsknoten vom Typ cq:PageContent. Die Eigenschaft „sling:resourceType“ des Inhaltsknotens verweist auf die Seitenkomponente, die zum Rendern der Seite verwendet wird.

Um beispielsweise den Namen der aktuellen Seite abzurufen, können Sie den folgenden Code in Ihrem Skript verwenden:

S`tring pageName = currentPage.getName();`

TcurrentPage ist das aktuelle Seitenobjekt. Weitere Informationen zum Bearbeiten von Seitenobjekten finden Sie unter [Java™-Dokumente](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/Page.html).

**Seiten-Manager** Der Seiten-Manager ist eine Schnittstelle, die Methoden für Vorgänge auf Seitenebene bereitstellt.

Um beispielsweise die übergeordnete Seite einer Ressource abzurufen, können Sie den folgenden Code in Ihrem Skript verwenden:

Page myPage = pageManager.getContainingPage(myResource);

pageManager ist das Seitenmanagerobjekt und myResource ein Ressourcenobjekt. Weitere Informationen zu den vom Seitenmanager bereitgestellten Methoden finden Sie unter [Java™-Dokumente](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/api/PageManager.html).

## Struktur innerhalb des Repositorys {#structure-within-the-repository}

Die folgende Liste gibt einen Überblick über die Struktur, die Sie im Repository sehen.

>[!CAUTION]
>
>Änderungen an dieser Struktur oder an den darin enthaltenen Dateien sollten sorgfältig vorgenommen werden.
>
>Es sind Änderungen bei der Entwicklung erforderlich, Sie sollten jedoch darauf achten, dass Sie die Auswirkungen von vorgenommenen Änderungen vollständig verstehen.

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen. Für die Konfiguration und andere Änderungen kopieren Sie das Element von `/libs` nach `/apps` und nehmen Sie alle Änderungen innerhalb von `/apps` vor.

* `/apps`

   Anwendungsbezogen; enthält für Ihre Website spezifische Komponentendefinitionen. Die von Ihnen entwickelten Komponenten können auf den Standardkomponenten basieren, die unter `/libs/foundation/components` verfügbar sind.

* `/content`

  Inhalt, der für Ihre Website erstellt wurde.

* `/etc`

* `/home`

  Benutzer- und Gruppeninformationen.

* `/libs`

   Bibliotheken und Definitionen, die zum Kern von AEM gehören. Die Unterordner in `/libs` die vordefinierten AEM Funktionen wie Suche oder Replikation darstellen. Inhalte in `/libs` sollten nicht geändert werden, da dies die Funktionsweise von AEM beeinflusst. Spezielle Funktionen für Ihre Website sollten unter `/apps` entwickelt werden (siehe [Anpassen von Komponenten und anderen Elementen](/help/sites-developing/dev-guidelines-bestpractices.md#customizing-components-and-other-elements)).

* `/tmp`

  Temporärer Arbeitsbereich.

* `/var`

   Dateien, die sich ändern und vom System aktualisiert werden; wie Audit-Logs, Statistiken, Event-Handling.

## Umgebungen {#environments}

Bei AEM besteht eine Produktionsumgebung häufig aus zwei verschiedenen Instanztypen: einem [Autoren- und Veröffentlichungsinstanzen](/help/sites-deploying/deploy.md#author-and-publish-installs).

## Der Dispatcher {#the-dispatcher}

Der Dispatcher ist das Tool von Adobe für Caching und/oder Lastenausgleich. Weitere Informationen finden Sie unter [Der Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de).

## FileVault (Quellüberarbeitungssystem) {#filevault-source-revision-system}

FileVault stellt Ihrem JCR-Repository Dateisystemzuordnung und Versionskontrolle zur Verfügung. Es kann verwendet werden, um AEM-Entwicklungsprojekte mit voller Unterstützung für das Speichern und Versionieren von Projekt-Code, Inhalten, Konfigurationen usw. in standardmäßigen Versionskontrollsystemen (z. B. Subversion) zu verwalten.

Ausführliche Informationen finden Sie in der Dokumentation zum [FileVault-Tool](/help/sites-developing/ht-vlttool.md).

## Workflows {#workflows}

Ihre Inhalte unterliegen oft organisatorischen Prozessen, einschließlich Schritten wie Genehmigung und Freigabe durch verschiedene Teilnehmer. Diese Prozesse können als Workflows, [die in AEM definiert und entwickelt wurden](/help/sites-developing/workflows-models.md), repräsentiert werden und anschließend wie erforderlich auf die [passenden Inhaltsseiten](/help/sites-administering/workflows.md) oder [digitale Assets](/help/assets/assets-workflow.md) angewendet werden.

Die Workflow-Engine wird verwendet, um die Implementierung Ihrer Workflows und deren anschließende Anwendung auf Ihre Inhalte zu verwalten.

## Verwaltung mehrerer Websites {#multi-site-management}

Multi-Site-Manager (MSM) ermöglicht es Ihnen, mehrere Websites mit gemeinsamen Inhalten problemlos zu verwalten. Mit MSM können Sie Beziehungen zwischen den Sites definieren, sodass Inhaltsänderungen auf einer Site automatisch auf anderen Sites repliziert werden.

Zum Beispiel werden Websites oft in mehreren Sprachen für internationale Zielgruppen bereitgestellt. Wenn die Anzahl der Sites in derselben Sprache niedrig ist (drei bis fünf), ist ein manueller Prozess für die Synchronisierung von Inhalten über Sites hinweg möglich. Wenn jedoch die Anzahl der Sites zunimmt oder mehrere Sprachen involviert sind, wird es effizienter, den Prozess zu automatisieren.

* Effiziente Verwaltung verschiedener Sprachversionen einer Website.
* So aktualisieren Sie automatisch eine oder mehrere Sites basierend auf einer Quell-Site:

   * Erzwingen Sie eine gemeinsame Basisstruktur und verwenden Sie gemeinsame Inhalte auf mehreren Sites.
   * Maximieren Sie den Einsatz der verfügbaren Ressourcen.
   * Pflegen Sie ein gemeinsames Look-and-Feel.
   * Konzentrieren Sie Ihre Anstrengungen auf die Verwaltung der Inhalte, die sich zwischen den Sites unterscheiden.

Weitere Informationen finden Sie unter [Multi-Site-Manager](/help/sites-administering/msm.md).
