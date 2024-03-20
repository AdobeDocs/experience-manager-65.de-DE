---
title: AEM-Entwicklung – Richtlinien und Best Practices
description: Richtlinien und Best Practices für das Entwickeln mit AEM
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 94%

---

# AEM-Entwicklung – Richtlinien und Best Practices{#aem-development-guidelines-and-best-practices}

## Richtlinien für die Verwendung von Vorlagen und Komponenten {#guidelines-for-using-templates-and-components}

Adobe Experience Manager(AEM)-Komponenten und -Vorlagen beinhalten ein leistungsstarkes Toolkit. Sie können von Entwickelnden verwendet werden, um Menschen, die eine Website geschäftlich nutzen, bearbeiten oder verwalten, die Möglichkeit zu geben, ihre Website an die sich ändernden Geschäftsanforderungen anzupassen (Content-Agilität). All dies erfolgt unter Beibehaltung des einheitlichen Layouts der Sites (Markenschutz).

Eine typische Herausforderung für eine Person, die für eine Website oder eine Reihe von Websites verantwortlich ist (z. B. in einer Zweigstelle eines globalen Unternehmens), besteht darin, eine neue Art der Präsentation von Inhalten auf ihren Websites einzuführen.

Angenommen, eine Newslisten-Seite, die Auszüge aus bereits veröffentlichten Artikeln enthält, muss zu den Websites hinzugefügt werden. Die Seite soll das gleiche Design und die gleiche Struktur wie der Rest der Website haben.

Es wird empfohlen, wie folgt an eine solche Herausforderung heranzugehen:

* Verwenden Sie eine vorhandene Vorlage erneut, damit Sie einen Seitentyp erstellen können. Die Vorlage definiert grob die Seitenstruktur (Navigationselemente, Bedienfelder usw.), die im Rahmen des jeweiligen Designs (CSS, Grafiken) weiter verfeinert wird.
* Verwenden Sie das Absatzsystem (parsys/iparsys) auf den neuen Seiten.
* Definieren Sie Zugriffsberechtigungen für den Design-Modus der Absatzsysteme, damit diese nur von berechtigten Personen (normalerweise der Administrator) geändert werden können.
* Definieren Sie die Komponenten, die im angegebenen Absatzsystem zulässig sind, damit beim Bearbeiten die erforderlichen Komponenten auf der Seite platziert werden können. In diesem Fall könnte es sich um eine Listenkomponente handeln, die eine Unterstruktur von Seiten durchlaufen und die Informationen nach vordefinierten Regeln extrahieren kann.
* Bearbeiterinnen und Bearbeiter fügen die zulässigen Komponenten auf den Seiten, für die sie zuständig sind, hinzu und konfigurieren diese, um die angeforderte Funktionalität (Informationen) für das Unternehmen bereitzustellen.

Das Beispiel zeigt, wie dieser Ansatz die mitwirkenden Benutzenden und Admins der Website in die Lage versetzt, schnell auf Geschäftsanforderungen zu reagieren, ohne das Entwicklungsteam einbeziehen zu müssen. Alternative Methoden, wie etwa das Erstellen einer Vorlage, sind in der Regel kostenintensiv. Außerdem setzt dies einen Änderungs-Management-Prozess und die Beteiligung des Entwicklungs-Teams voraus. Dadurch wird der gesamte Prozess länger und teurer.

Entwickelnde von AEM-basierten Systemen sollten daher Folgendes verwenden:

* Vorlagen und Zugriffssteuerung für das Absatzsystem-Design, um Einheitlichkeit und Markenschutz sicherzustellen
* ein Absatzsystem mit Konfigurationsoptionen, um maximale Flexibilität zu erreichen

Die folgenden allgemeinen Regeln für Entwickelnde sind bei den meisten gängigen Projekten sinnvoll:

* Beschränken Sie die Anzahl der Vorlagen auf die Anzahl der grundverschiedenen Seitenstrukturen auf den Websites.
* Gestalten Sie die benutzerspezifischen Komponenten ausreichend flexibel und konfigurierbar.
* Nutzen Sie die Leistung und Flexibilität des AEM-Absatzsystems (d. h. der parsys- und iparsys-Komponenten) so optimal wie möglich.

### Anpassen von Komponenten und anderen Elementen {#customizing-components-and-other-elements}

Wenn Sie eigene Komponenten erstellen oder eine vorhandene Komponente anpassen, ist es häufig am einfachsten (und sichersten), vorhandene Definitionen wiederzuverwenden. Die gleichen Prinzipien gelten auch für andere Elemente in AEM, z. B. den Fehler-Handler.

Kopieren Sie dazu die vorhandene Definition und überlagern Sie sie, wie nachfolgend beschrieben: Mit anderen Worten, kopieren Sie die Definition von `/libs` zu `/apps/<your-project>`. Sie können die neue Definition in `/apps` Anforderungen entsprechend aktualisieren.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Verwenden von Überlagerungen](/help/sites-developing/overlays.md).

Beispiel:

* [Anpassen einer Komponente](/help/sites-developing/components.md)

  Dazu gehörte das Überlagern einer Komponentendefinition:

   * Erstellen Sie durch Kopieren einer vorhandenen Komponente einen neuen Komponentenordner unter `/apps/<website-name>/components/<MyComponent>`:

      * Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

         * von `/libs/foundation/components/text`
         * nach `/apps/myProject/components/text`

* [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

  In diesem Fall wird ein Servlet überlagert:

   * Kopieren Sie im Repository ein oder mehrere Standardskripte:

      * von `/libs/sling/servlet/errorhandler/`
      * nach `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>Sie dürfen **keinerlei** Änderungen im Pfad `/libs` vornehmen.
>
>Der Grund dafür ist, dass der Inhalt von `/libs` überschrieben wird, wenn Sie Ihre Instanz das nächste Mal aktualisieren (und möglicherweise auch bei Anwendung eines Hotfix oder Feature Pack).
>
>Für die Konfiguration und andere Änderungen:
>
>1. Kopieren Sie das Element von `/libs` nach `/apps`
>1. Nehmen Sie Änderungen, falls erforderlich, in `/apps` vor.

## Wann sollte man JCR-Abfragen verwenden und wann nicht? {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-Abfragen sind sehr wirksam, wenn sie richtig eingesetzt werden. Sie sind geeignet für:

* echte Endbenutzerabfragen, z. B. die Volltextsuche nach Inhalten
* die Suche nach strukturierten Inhalten im gesamten Repository

  Stellen Sie in solchen Fällen sicher, dass Abfragen nur bei Bedarf ausgeführt werden, etwa bei der Aktivierung von Komponenten oder der Cache-Invalidierung (im Gegensatz zu z. B. Workflow-Schritten, Ereignis-Handlern, die bei Inhaltsänderungen ausgelöst werden, und Filtern).

Verwenden Sie JCR-Abfragen nie für reine Rendering-Anfragen. JCR-Abfragen sind beispielsweise nicht geeignet für:

* das Rendern von Navigationselementen
* das Erstellen einer Übersicht über die „10 neuesten Nachrichten“
* das Anzeigen der Anzahl von Inhaltselementen

Verwenden Sie für das Rendern von Inhalten anstelle einer JCR-Abfrage den Navigationszugriff auf die Inhaltsstruktur.

>[!NOTE]
>
>Wenn Sie den [Query Builder](/help/sites-developing/querybuilder-api.md) verwenden, nutzen Sie JCR-Abfragen, da der Query Builder JCR-Abfragen im Hintergrund erzeugt.
>

## Sicherheitsaspekte {#security-considerations}

>[!NOTE]
>
>Es ist auch sinnvoll, die [Sicherheitsprüfliste](/help/sites-administering/security-checklist.md) zu Rate zu ziehen.

### JCR- bzw. Repository-Sitzungen {#jcr-repository-sessions}

Verwenden Sie die Benutzersitzung und nicht die Administratorsitzung. Sie sollten also Folgendes verwenden:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Schützen vor Cross-Site-Scripting (XSS) {#protect-against-cross-site-scripting-xss}

Mit Cross-Site-Scripting (XSS) können Angreifer Code in Web-Seiten einfügen, die von anderen Benutzenden aufgerufen werden. Diese Sicherheitslücke kann von böswilligen Web-Benutzenden ausgenutzt werden, um die Zugriffssteuerung zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Bei Entwicklung und Tests hat das Vermeiden von XSS höchste Priorität.

Auch kann eine Firewall in der Web-Anwendung wie [mod_security für Apache](https://modsecurity.org) die Sicherheit der Bereitstellungsumgebung zuverlässig und zentral steuern und diese vor bisher unerkannten Cross-Site-Scripting-Angriffen schützen.

>[!CAUTION]
>
>Der in AEM bereitgestellte Beispiel-Code alleine bietet keinen Schutz vor Angriffen dieser Art, sondern muss durch die Anforderungsfilterung der Firewall in der Web-Anwendung ergänzt werden.

Der XSS-API-Spickzettel enthält Informationen, die Sie für das Verwenden der XSS-API und Schützen einer AEM-Anwendung benötigen. Sie können diesen hier herunterladen:

Der XSS-API-Spickzettel.

[Datei laden](assets/xss_cheat_sheet_2016.pdf)

### Sichere Kommunikation vertraulicher Informationen {#securing-communication-for-confidential-information}

Stellen Sie wie auch bei anderen Internet-Anwendungen sicher, dass bei der Übertragung vertraulicher Informationen

* Traffic durch SSL gesichert wird
* HTTP POST verwendet wird, falls anwendbar

Dies gilt für vertrauliche Systeminformationen (wie Konfiguration oder Administratorzugriff) und vertrauliche Benutzerinformationen (wie persönliche Daten).

## Spezifische Entwicklungsaufgaben {#distinct-development-tasks}

### Anpassen von Fehlerseiten {#customizing-error-pages}

Fehlerseiten können in AEM angepasst werden. Dies ist ratsam, um zu vermeiden, dass die Instanz Sling-Traces zu internen Server-Fehlern ausgibt.

Ausführliche Informationen finden Sie unter [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md).

### Geöffnete Dateien im Java™-Prozess {#open-files-in-the-java-process}

Da AEM auf viele Dateien zugreifen kann, wird empfohlen, die Anzahl [geöffneter Dateien für einen Java™-Prozess](/help/sites-deploying/configuring.md#open-files-in-the-java-process) ausdrücklich für AEM zu konfigurieren.

Um das Problem gering zu halten, sollte bei der Entwicklung darauf geachtet werden, dass geöffnete Dateien korrekt geschlossen werden, wenn (sinnvoll) möglich.
