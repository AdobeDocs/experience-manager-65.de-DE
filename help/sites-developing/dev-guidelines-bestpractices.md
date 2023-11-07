---
title: AEM-Entwicklung – Richtlinien und Best Practices
description: Leitlinien und Best Practices für die Entwicklung auf AEM
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '1084'
ht-degree: 21%

---

# AEM-Entwicklung – Richtlinien und Best Practices{#aem-development-guidelines-and-best-practices}

## Richtlinien für die Verwendung von Vorlagen und Komponenten {#guidelines-for-using-templates-and-components}

Adobe Experience Manager (AEM)-Komponenten und -Vorlagen verfügen über ein leistungsstarkes Toolkit. Sie können von Entwicklern verwendet werden, um Benutzern, Editoren und Administratoren von Websites die Möglichkeit zu geben, ihre Websites an die sich ändernden Geschäftsanforderungen anzupassen (Inhaltserstellung). All dies unter Beibehaltung des einheitlichen Layouts der Websites (Markenschutz).

Eine typische Herausforderung für eine Person, die für eine Website oder eine Reihe von Websites verantwortlich ist (z. B. in einer Zweigstelle eines globalen Unternehmens), besteht darin, eine neue Art der Präsentation von Inhalten auf ihren Websites einzuführen.

Angenommen, eine Newslisten-Seite, die Auszüge aus bereits veröffentlichten Artikeln enthält, muss zu den Websites hinzugefügt werden. Die Seite sollte dasselbe Design und dieselbe Struktur aufweisen wie der Rest der Website.

Die empfohlene Vorgehensweise bei einer solchen Herausforderung wäre:

* Verwenden Sie eine vorhandene Vorlage erneut, damit Sie einen Seitentyp erstellen können. Die Vorlage definiert grob die Seitenstruktur (Navigationselemente, Bedienfelder usw.), die durch ihr Design (CSS, Grafiken) weiter optimiert wird.
* Verwenden Sie das Absatzsystem (parsys/iparsys) auf den neuen Seiten.
* Definieren Sie Zugriffsberechtigungen für den Design-Modus der Absatzsysteme, damit diese nur von berechtigten Personen (normalerweise der Administrator) geändert werden können.
* Definieren Sie die im angegebenen Absatzsystem zulässigen Komponenten, damit Editoren die erforderlichen Komponenten dann auf der Seite platzieren können. In diesem Fall kann es sich um eine Listenkomponente handeln, die eine Unterstruktur von Seiten durchlaufen und die Informationen anhand vordefinierter Regeln extrahieren kann.
* Bearbeiter fügen die zulässigen Komponenten zu den Seiten hinzu, für die sie verantwortlich sind, und konfigurieren sie, um die angeforderte Funktionalität (Informationen) für das Unternehmen bereitzustellen.

Das Beispiel zeigt, wie es dieser Ansatz den beitragsleistenden Benutzern und Administratoren der Website ermöglicht, schnell auf Geschäftsanforderungen zu reagieren, ohne das Entwicklungsteam einbeziehen zu müssen. Alternative Methoden wie das Erstellen einer Vorlage sind in der Regel eine kostspielige Übung, die einen Change-Management-Prozess und die Einbeziehung des Entwicklungsteams erfordert. Dadurch wird der gesamte Prozess länger und kostspielig.

Die Entwickler AEM Systeme sollten daher Folgendes verwenden:

* Vorlagen und Zugriffskontrolle für die Konstruktion von Absatzsystemen für Einheitlichkeit und Markenschutz
* Absatzsystem einschließlich der Konfigurationsoptionen für Flexibilität.

Die folgenden allgemeinen Regeln für Entwickler sind in den meisten gängigen Projekten sinnvoll:

* Halten Sie die Anzahl der Vorlagen gering - so gering wie die Anzahl grundlegend unterschiedlicher Seitenstrukturen auf den Websites.
* Stellen Sie die erforderlichen Flexibilität und Konfigurationsfunktionen für Ihre benutzerdefinierten Komponenten bereit.
* Maximieren Sie die Nutzung der Leistung und Flexibilität des AEM Absatzsystems - der parsys- und iparsys-Komponenten.

### Anpassen von Komponenten und anderen Elementen {#customizing-components-and-other-elements}

Wenn Sie eigene Komponenten erstellen oder eine vorhandene Komponente anpassen, ist es häufig am einfachsten (und sichersten), vorhandene Definitionen wiederzuverwenden. Die gleichen Prinzipien gelten auch für andere Elemente in AEM, z. B. den Fehler-Handler.

Kopieren Sie dazu die vorhandene Definition und überlagern Sie sie, wie nachfolgend beschrieben: Mit anderen Worten, kopieren Sie die Definition von `/libs` zu `/apps/<your-project>`. Sie können die neue Definition in `/apps` Anforderungen entsprechend aktualisieren.

>[!NOTE]
>
>Siehe [Verwenden von Überlagerungen](/help/sites-developing/overlays.md) für weitere Details.

Beispiel:

* [Anpassen einer Komponente](/help/sites-developing/components.md)

  Dazu gehörte das Überlagern einer Komponentendefinition:

   * Erstellen Sie einen Komponentenordner in `/apps/<website-name>/components/<MyComponent>` durch Kopieren einer vorhandenen Komponente:

      * Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

         * von `/libs/foundation/components/text`
         * nach `/apps/myProject/components/text`

* [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

  In diesem Fall wird ein Servlet überlagert:

   * Kopieren Sie im Repository mindestens ein Standardskript:

      * von `/libs/sling/servlet/errorhandler/`
      * nach `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>**** Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` wird beim nächsten Upgrade Ihrer Instanz überschrieben (und kann auch überschrieben werden, wenn Sie einen Hotfix oder ein Feature Pack anwenden).
>
>Für die Konfiguration und andere Änderungen:
>
>1. Kopieren Sie das Element von `/libs` nach `/apps`
>1. Nehmen Sie Änderungen, falls erforderlich, in `/apps` vor.

## Verwendung von JCR-Abfragen und wann diese nicht verwendet werden sollen {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-Abfragen sind ein leistungsstarkes Werkzeug, wenn sie richtig eingesetzt werden. Sie eignen sich für:

* echte Endbenutzerabfragen, z. B. Volltextsuchen nach Inhalten.
* Fälle, in denen strukturierte Inhalte im gesamten Repository zu finden sind.

  Stellen Sie in solchen Fällen sicher, dass Abfragen nur bei Bedarf ausgeführt werden. Beispielsweise bei der Aktivierung von Komponenten oder der Cache-Invalidierung (im Gegensatz zu z. B. Workflow-Schritten, Ereignishandlern, die Trigger bei Inhaltsänderungen sind, und Filtern).

Verwenden Sie JCR-Abfragen nie für reine Rendering-Anforderungen. JCR-Abfragen eignen sich beispielsweise nicht für Folgendes:

* Rendering-Navigation
* Erstellen einer Übersicht über die 10 wichtigsten Neuigkeiten
* das Anzeigen der Anzahl von Inhaltselementen

Verwenden Sie zum Rendern von Inhalten den Navigationszugriff auf die Inhaltsstruktur, anstatt eine JCR-Abfrage durchzuführen.

>[!NOTE]
>
>Wenn Sie die [Query Builder](/help/sites-developing/querybuilder-api.md)verwenden Sie JCR-Abfragen, da Query Builder JCR-Abfragen im Hintergrund generiert.
>

## Sicherheitsüberlegungen {#security-considerations}

>[!NOTE]
>
>Es ist auch sinnvoll, die [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) zu Rate zu ziehen.

### JCR-Sitzungen (Repository) {#jcr-repository-sessions}

Verwenden Sie die Benutzersitzung, nicht die Verwaltungssitzung. Sie sollten also Folgendes verwenden:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Protect gegen Cross-Site Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Cross-Site Scripting (XSS) ermöglicht es Angreifern, Code in Webseiten einzufügen, die von anderen Benutzern angesehen werden. Diese Sicherheitslücke kann von böswilligen Webbenutzern ausgenutzt werden, um Zugriffskontrollen zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Die Prävention von XSS hat sowohl bei der Entwicklung als auch beim Testen höchste Priorität.

Außerdem eine Webanwendungs-Firewall, z. B. [mod_security für Apache](https://modsecurity.org), kann eine zuverlässige, zentrale Kontrolle über die Sicherheit der Bereitstellungsumgebung bieten und vor zuvor nicht erkannten Cross-Site-Scripting-Angriffen schützen.

>[!CAUTION]
>
>Der in AEM bereitgestellte Beispiel-Code alleine bietet keinen Schutz vor Angriffen dieser Art, sondern muss durch die Anforderungsfilterung der Firewall in der Web-Anwendung ergänzt werden.

Das XSS-API-Cheatsheet enthält Informationen, die Sie benötigen, um die XSS-API zu verwenden und eine AEM App sicherer zu machen. Sie können ihn hier herunterladen:

Das XSSAPI-Cheatsheet.

[Datei laden](assets/xss_cheat_sheet_2016.pdf)

### Sichere Kommunikation für vertrauliche Informationen {#securing-communication-for-confidential-information}

Stellen Sie wie bei jeder Internetanwendung sicher, dass beim Transport vertraulicher Informationen

* Datenverkehr über SSL gesichert
* HTTP-POST wird verwendet, falls zutreffend

Dies gilt für Informationen, die vertraulich für das System sind (z. B. Konfiguration oder administrativer Zugriff), sowie für vertrauliche Informationen für die Benutzer (wie ihre persönlichen Daten).

## Spezifische Entwicklungsaufgaben {#distinct-development-tasks}

### Anpassen von Fehlerseiten {#customizing-error-pages}

Fehlerseiten können für AEM angepasst werden. Dies ist ratsam, damit die Instanz keine Sling-Traces auf internen Server-Fehlern offenlegt.

Siehe [Anpassen der vom Fehler-Handler angezeigten Fehlerseiten](/help/sites-developing/customizing-errorhandler-pages.md) für ausführliche Informationen.

### Öffnen von Dateien im Java™-Prozess {#open-files-in-the-java-process}

Da AEM auf viele Dateien zugreifen kann, wird empfohlen, die Anzahl der [Dateien für einen Java™-Prozess öffnen](/help/sites-deploying/configuring.md#open-files-in-the-java-process) explizit für AEM konfiguriert werden.

Um dieses Problem zu minimieren, sollte die Entwicklung sicherstellen, dass geöffnete Dateien ordnungsgemäß geschlossen werden, wenn dies (sinnvoll) möglich ist.
