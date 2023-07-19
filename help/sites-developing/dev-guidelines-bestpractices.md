---
title: AEM-Entwicklung – Richtlinien und Best Practices
seo-title: AEM Development - Guidelines and Best Practices
description: Leitlinien und Best Practices für die Entwicklung auf AEM
seo-description: Guidelines and best practices for developing on AEM
uuid: a67de085-4441-4a1d-bec3-2f27892a67ff
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b4cf0ffc-973a-473b-80c8-7f530d111435
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '1093'
ht-degree: 38%

---

# AEM-Entwicklung – Richtlinien und Best Practices{#aem-development-guidelines-and-best-practices}

## Richtlinien für die Verwendung von Vorlagen und Komponenten {#guidelines-for-using-templates-and-components}

AEM Komponenten und Vorlagen bilden ein sehr leistungsstarkes Toolkit. Sie können von Entwicklern verwendet werden, um Website-Benutzern, Editoren und Administratoren die Möglichkeit zu geben, ihre Websites an die sich ändernden Geschäftsanforderungen anzupassen (Content-Agilität) und gleichzeitig das einheitliche Layout der Sites (Markenschutz) beizubehalten.

Eine typische Herausforderung für eine Person, die für eine Website oder eine Reihe von Websites verantwortlich ist (z. B. in einer Zweigstelle eines globalen Unternehmens), besteht darin, eine neue Art der Präsentation von Inhalten auf ihren Websites einzuführen.

Angenommen, eine Newslisten-Seite, die Auszüge aus bereits veröffentlichten Artikeln enthält, muss zu den Websites hinzugefügt werden. Die Seite sollte dasselbe Design und dieselbe Struktur aufweisen wie der Rest der Website.

Die empfohlene Vorgehensweise bei einer solchen Herausforderung wäre:

* Verwenden Sie eine vorhandene Vorlage erneut, um einen neuen Seitentyp zu erstellen. Die Vorlage definiert grob die Seitenstruktur (Navigationselemente, Bedienfelder usw.), die durch ihr Design (CSS, Grafiken) weiter optimiert wird.
* Verwenden Sie das Absatzsystem (parsys/iparsys) auf den neuen Seiten.
* Definieren Sie Zugriffsberechtigungen für den Design-Modus der Absatzsysteme, damit diese nur von berechtigten Personen (normalerweise der Administrator) geändert werden können.
* Definieren Sie die im angegebenen Absatzsystem zulässigen Komponenten, damit Editoren die erforderlichen Komponenten dann auf der Seite platzieren können. In unserem Fall kann es sich um eine Listenkomponente handeln, die eine Unterstruktur von Seiten durchlaufen und die Informationen anhand vordefinierter Regeln extrahieren kann.
* Bearbeiter fügen die zulässigen Komponenten auf den Seiten, für die sie verantwortlich sind, hinzu und konfigurieren sie, um die angeforderte Funktionalität (Informationen) für das Unternehmen bereitzustellen.

Das Beispiel zeigt, wie es dieser Ansatz den beitragsleistenden Benutzern und Administratoren der Website ermöglicht, schnell auf Geschäftsanforderungen zu reagieren, ohne das Entwicklungsteam einbeziehen zu müssen. Andere Methoden, wie das Erstellen einer neuen Vorlage, sind in der Regel kostenintensiv. Außerdem sind dafür ein Änderungsmanagementprozess und die Beteiligung des Entwicklungsteams erforderlich. Dadurch wird der gesamte Prozess viel länger und kostspielig.

Die Entwickler AEM Systeme sollten daher Folgendes verwenden:

* Vorlagen und Zugriffskontrolle für die Konstruktion von Absatzsystemen für Einheitlichkeit und Markenschutz
* Absatzsystem einschließlich der Konfigurationsoptionen für Flexibilität.

Die folgenden allgemeinen Regeln für Entwickler sind in den meisten gängigen Projekten sinnvoll:

* Halten Sie die Anzahl der Vorlagen gering - so gering wie die Anzahl grundlegend unterschiedlicher Seitenstrukturen auf den Websites.
* Stellen Sie die erforderlichen Flexibilität und Konfigurationsfunktionen für Ihre benutzerdefinierten Komponenten bereit.
* Maximieren Sie die Nutzung der Leistung und Flexibilität AEM Absatzsystems - der parsys- und iparsys-Komponenten.

### Anpassen von Komponenten und anderen Elementen {#customizing-components-and-other-elements}

Wenn Sie eigene Komponenten erstellen oder eine vorhandene Komponente anpassen, ist es häufig am einfachsten (und sichersten), vorhandene Definitionen wiederzuverwenden. Dies gilt auch für andere Elemente in AEM, zum Beispiel für Fehler-Handler.

Kopieren Sie dazu die vorhandene Definition und überlagern Sie sie, wie nachfolgend beschrieben: Mit anderen Worten, kopieren Sie die Definition von `/libs` zu `/apps/<your-project>`. Sie können die neue Definition in `/apps` Anforderungen entsprechend aktualisieren.

>[!NOTE]
>
>Siehe [Verwenden von Überlagerungen](/help/sites-developing/overlays.md) für weitere Details.

Beispiel:

* [Anpassen einer Komponente](/help/sites-developing/components.md)

  Dazu gehörte das Überlagern einer Komponentendefinition:

   * Erstellen Siedurch Kopieren einer vorhandenen Komponente einen neuen Komponentenordner in `/apps/<website-name>/components/<MyComponent>`:

      * Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

         * von `/libs/foundation/components/text`
         * nach `/apps/myProject/components/text`

* [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

  In diesem Fall wird ein Servlet überlagert:

   * Kopieren Sie im Repository das/die Standardskript(e):

      * von `/libs/sling/servlet/errorhandler/`
      * nach `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>Sie dürfen **keinerlei** Änderungen im Pfad `/libs` vornehmen.
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Für die Konfiguration und andere Änderungen:
>
>1. Kopieren Sie das Element von `/libs` nach `/apps`
>1. Nehmen Sie Änderungen, falls erforderlich, in `/apps` vor.

## Verwendung von JCR-Abfragen und wann diese nicht verwendet werden sollen {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-Abfragen sind ein leistungsstarkes Werkzeug, wenn sie richtig eingesetzt werden. Sie eignen sich für:

* echte Endbenutzerabfragen, z. B. Volltextsuchen nach Inhalten.
* Fälle, in denen strukturierte Inhalte im gesamten Repository gefunden werden müssen.

  Stellen Sie in solchen Fällen sicher, dass Abfragen nur dann ausgeführt werden, wenn dies unbedingt erforderlich ist, z. B. bei der Aktivierung einer Komponente oder der Cache-Invalidierung (im Gegensatz zu Workflows Steps, Event Handlers, die Trigger bei Inhaltsänderungen, Filtern usw.).

JCR-Abfragen sollten niemals für reine Rendering-Anfragen verwendet werden. JCR-Abfragen eignen sich beispielsweise nicht für

* Rendering-Navigation
* Erstellen einer Übersicht über die 10 wichtigsten Neuigkeiten
* das Anzeigen der Anzahl von Inhaltselementen

Verwenden Sie zum Rendern von Inhalten den Navigationszugriff auf die Inhaltsstruktur, anstatt eine JCR-Abfrage durchzuführen.

>[!NOTE]
>
>Wenn Sie [Query Builder](/help/sites-developing/querybuilder-api.md)verwenden Sie JCR-Abfragen, da Query Builder JCR-Abfragen im Hintergrund generiert.
>

## Sicherheitsaspekte {#security-considerations}

>[!NOTE]
>
>Es ist auch sinnvoll, die [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) zu Rate zu ziehen.

### JCR-Sitzungen (Repository) {#jcr-repository-sessions}

Sie sollten die Benutzersitzung und nicht die Verwaltungssitzung verwenden. Sie sollten also Folgendes verwenden:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Protect gegen Cross-Site Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Cross-Site Scripting (XSS) ermöglicht es Angreifern, Code in Webseiten einzufügen, die von anderen Benutzern angesehen werden. Diese Sicherheitslücke kann von böswilligen Webbenutzern ausgenutzt werden, um Zugriffskontrollen zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Die Prävention von XSS hat sowohl bei der Entwicklung als auch beim Testen höchste Priorität.

Zusätzlich kann eine Firewall in der Web-Anwendung wie [mod_security für Apache](https://modsecurity.org) die Sicherheit einer Bereitstellungsumgebung zuverlässig und zentral steuern und diese vor bisher unerkannten Cross-Site-Scripting-Angriffen schützen.

>[!CAUTION]
>
>Der in AEM bereitgestellte Beispiel-Code alleine bietet keinen Schutz vor Angriffen dieser Art, sondern muss durch die Anforderungsfilterung der Firewall in der Web-Anwendung ergänzt werden.

Der XSS-API-Spickzettel enthält Informationen, die Sie für das Verwenden der XSS-API und Sichern einer AEM-Anwendung benötigen. Sie können ihn hier herunterladen:

Das XSSAPI-Cheatsheet.

[Datei laden](assets/xss_cheat_sheet_2016.pdf)

### Sichere Kommunikation für vertrauliche Informationen {#securing-communication-for-confidential-information}

Stellen Sie wie bei jeder Internetanwendung sicher, dass beim Transport vertraulicher Informationen

* Traffic wird über SSL gesichert
* HTTP-POST wird verwendet, falls zutreffend

Dies gilt für vertrauliche Informationen des Systems (wie Konfiguration oder administrativer Zugriff) sowie vertrauliche Informationen für die Benutzer (wie ihre persönlichen Daten).

## Spezifische Entwicklungsaufgaben {#distinct-development-tasks}

### Anpassen von Fehlerseiten {#customizing-error-pages}

Fehlerseiten können für AEM angepasst werden. Dies ist ratsam, damit die Instanz keine Sling-Traces auf internen Server-Fehlern offenlegt.

Siehe [Anpassen der vom Fehler-Handler angezeigten Fehlerseiten](/help/sites-developing/customizing-errorhandler-pages.md) für ausführliche Informationen.

### Öffnen von Dateien im Java-Prozess {#open-files-in-the-java-process}

Da AEM auf eine große Anzahl von Dateien zugreifen kann, wird empfohlen, die Anzahl [geöffneter Dateien für einen Java-Prozess](/help/sites-deploying/configuring.md#open-files-in-the-java-process) ausdrücklich für AEM zu konfigurieren.

Um das Problem gering zu halten, sollte bei der Entwicklung darauf geachtet werden, dass geöffnete Dateien so schnell wie irgend möglich richtig geschlossen werden.
