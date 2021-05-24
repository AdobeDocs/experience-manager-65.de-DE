---
title: AEM-Entwicklung – Richtlinien und Best Practices
seo-title: AEM-Entwicklung – Richtlinien und Best Practices
description: Richtlinien und Best Practices für das Entwickeln mit AEM
seo-description: Richtlinien und Best Practices für das Entwickeln mit AEM
uuid: a67de085-4441-4a1d-bec3-2f27892a67ff
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: b4cf0ffc-973a-473b-80c8-7f530d111435
exl-id: 8eef7e4d-a6f2-4b87-a995-0761447283c6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1105'
ht-degree: 87%

---

# AEM-Entwicklung – Richtlinien und Best Practices{#aem-development-guidelines-and-best-practices}

## Richtlinien für die Verwendung von Vorlagen und Komponenten {#guidelines-for-using-templates-and-components}

AEM-Komponenten und -vorlagen sind sehr effiziente Tools. Entwickler können sie zum Bereitstellen von Websites für Geschäftsbenutzer, Editoren und Administratoren verwenden. Dabei sind Funktionen verfügbar, mit denen sie Websites an die sich ändernden Geschäftsanforderungen anpassen können (Inhaltsagilität), ohne das einheitliche Layout der Sites zu ändern (Markenschutz).

Eine typische Herausforderung für die für eine oder mehrere Websites (z. B. in einer Zweigniederlassung eines globalen Unternehmens) verantwortliche Person ist die Einführung einer neuen Art von Inhaltspräsentation auf den Websites.

Angenommen, eine Newslisten-Seite, die Auszüge aus bereits veröffentlichten Artikeln enthält, muss zu den Websites hinzugefügt werden. Die Seite soll das gleiche Design und die gleiche Struktur wie der Rest der Website haben.

Es wird empfohlen, wie folgt an diese Herausforderung heranzugehen:

* Verwenden Sie eine vorhandene Vorlage wieder, um einen neuen Seitentyp zu erstellen. Die Vorlage definiert grob die Seitenstruktur (Navigation, Elemente, Fenster usw.), die vom Design (CSS, Grafiken) weiter verfeinert wird.
* Verwenden Sie das Absatzsystem (parsys/iparsys) auf den neuen Seiten.
* Definieren Sie Zugriffsberechtigungen für den Designmodus der Absatzsysteme, damit diese nur von berechtigten Personen (normalerweise der Administrator) geändert werden können.
* Definieren Sie die Komponenten, die im angegebenen Absatzsystem zulässig sind, damit Editoren die erforderlichen Komponenten auf der Seite einfügen können. In unserem Fall könnte es sich um eine Listenkomponente handeln, die eine Unterstruktur von Seiten durchlaufen und die Informationen nach vordefinierten Regeln extrahieren kann.
* Editoren fügen die zulässigen Komponenten auf den Seiten, für die sie zuständig sind, hinzu und konfigurieren diese, um die angeforderte Funktionalität (Informationen) für das Unternehmen bereitzustellen.

Das Beispiel zeigt, wie es dieser Ansatz den beitragsleistenden Benutzern und Administratoren der Website ermöglicht, schnell auf Geschäftsanforderungen zu reagieren, ohne das Entwicklungsteam einbeziehen zu müssen. Andere Methoden, wie das Erstellen einer neuen Vorlage, sind in der Regel kostenintensiv. Außerdem sind dafür ein Änderungsmanagementprozess und die Beteiligung des Entwicklungsteams erforderlich. Dadurch wird der gesamte Prozess wesentlich länger und teurer.

Entwickler von AEM-basierten Systemen sollten daher Folgendes verwenden:

* Vorlagen und gesteuerten Zugriff auf das Absatzsystemdesign, um Einheitlichkeit und Markenschutz zu gewährleisten
* Absatzsystem mit Konfigurationsoptionen für maximale Flexibilität

Die folgenden allgemeinen Regeln für Entwickler sind in der Mehrzahl gängiger Projekte sinnvoll:

* Beschränken Sie die Anzahl der Vorlagen auf die Anzahl der grundlegend abweichenden Seitenstrukturen auf den Websites.
* Gestalten Sie die benutzerspezifischen Komponenten ausreichend flexibel und konfigurierbar.
* Nutzen Sie die Leistung und Flexibilität des AEM-Absatzsystems (d. h. die parsys- und iparsys-Komponenten) so optimal wie möglich.

### Anpassen von Komponenten und anderen Elementen  {#customizing-components-and-other-elements}

Wenn Sie eigene Komponenten erstellen oder eine vorhandene Komponente anpassen, ist es häufig am einfachsten (und sichersten), vorhandene Definitionen wiederzuverwenden. Dies gilt auch für andere Elemente in AEM, zum Beispiel für Fehler-Handler.

Kopieren Sie dazu die vorhandene Definition und überlagern Sie sie, wie nachfolgend beschrieben: Anders ausgedrückt: Kopieren Sie die Definition von `/libs` in `/apps/<your-project>`. Diese neue Definition in `/apps` kann entsprechend Ihren Anforderungen aktualisiert werden.

>[!NOTE]
>
>Einzelheiten finden Sie unter [Verwenden von Überlagerungen](/help/sites-developing/overlays.md).

Beispiel:

* [Anpassen einer Komponente](/help/sites-developing/components.md)

   Dazu gehörte das Überlagern einer Komponentendefinition:

   * Erstellen Sie einen neuen Komponentenordner in `/apps/<website-name>/components/<MyComponent>`, indem Sie eine vorhandene Komponente kopieren:

      * Um beispielsweise die Textkomponente anzupassen, kopieren Sie diese

         * von `/libs/foundation/components/text`
         * in `/apps/myProject/components/text`

* [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md#how-to-customize-pages-shown-by-the-error-handler)

   In diesem Fall wird ein Servlet überlagert:

   * Kopieren Sie im Repository das/die Standardskript(e):

      * von `/libs/sling/servlet/errorhandler/`
      * in `/apps/sling/servlet/errorhandler/`

>[!CAUTION]
>
>Sie dürfen **** keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Für die Konfiguration und andere Änderungen:
>
>1. Kopieren Sie das Element in `/libs` in `/apps`
>1. nimmt beliebige Änderungen in `/apps` vor


## Verwenden von JCR-Abfragen {#when-to-use-jcr-queries-and-when-not-to-use-them}

JCR-Abfragen sind sehr wirksam, wenn sie richtig eingesetzt werden. Sie sind besonders geeignet für:

* echte Benutzerabfragen, wie die Volltextsuche in Inhalten.
* die Suche nach strukturierten Inhalten in einem gesamten Repository.

   Stellen Sie in solchen Fällen sicher, dass Abfragen nur dann ausgeführt werden, wenn dies unbedingt erforderlich ist, z. B. bei der Aktivierung einer Komponente oder der Cache-Invalidierung (im Gegensatz zu Workflows-Schritten, Event Handlers, der Trigger bei Inhaltsänderungen, Filtern usw.).

JCR-Abfragen sollten nicht für reine Rendering-Anforderungen verwendet werden. Beispielsweise sind JCR-Abfragen nicht geeignet für

* das Rendern von Navigationselementen
* das Erstellen einer Übersicht über die „10 aktuellsten Nachrichten“
* Anzeigen der Anzahl der Inhaltselemente

Verwenden Sie für das Rendern von Inhalten anstelle einer JCR-Abfrage den Navigationszugriff auf die Inhaltsstruktur.

>[!NOTE]
>
>Beim Verwenden von [Query Builder](/help/sites-developing/querybuilder-api.md) verwenden Sie jedoch JCR-Abfragen, da Query Builder JCR-Abfragen im Hintergrund erzeugt.


## Sicherheitsüberlegungen {#security-considerations}

>[!NOTE]
>
>Es lohnt sich auch, auf die [Sicherheits-Checkliste](/help/sites-administering/security-checklist.md) zu verweisen.

### JCR- bzw. Repository-Sitzungen {#jcr-repository-sessions}

Verwenden Sie die Benutzersitzung und nicht die Administratorsitzung. Sie sollten also Folgendes verwenden:

```java
slingRequest.getResourceResolver().adaptTo(Session.class);
```

### Schutz vor Cross-Site Scripting (XSS)  {#protect-against-cross-site-scripting-xss}

Mit Cross-Site Scripting (XSS) können Angreifer Code in Webseiten einfügen, die von anderen Benutzern aufgerufen werden. Diese Sicherheitslücke kann von böswilligen Nutzern ausgenutzt werden, um die Zugriffssteuerung zu umgehen.

AEM filtert prinzipiell sämtliche vom Benutzer bereitgestellten Inhalte bei der Ausgabe. Bei Entwicklung und Tests hat das Vermeiden von XSS höchste Priorität.

Darüber hinaus kann eine Webanwendungs-Firewall, z. B. [mod_security für Apache](https://modsecurity.org), eine zuverlässige, zentrale Kontrolle über die Sicherheit der Bereitstellungsumgebung bieten und vor zuvor nicht erkannten Cross-Site-Scripting-Angriffen schützen.

>[!CAUTION]
>
>Der in AEM bereitgestellte Beispielcode alleine bietet keinen Schutz vor Angriffen dieser Art, sondern muss durch die Anforderungsfilterung der Firewall in der Web-Anwendung ergänzt werden.

Der XSS-API-Spickzettel enthält Informationen, die Sie für das Verwenden der XSS-API und Sichern einer AEM-Anwendung benötigen. Sie können diesen hier herunterladen:

Der XSSAPI-Spickzettel.

[Datei laden](assets/xss_cheat_sheet_2016.pdf)

### Sichere Kommunikation vertraulicher Informationen {#securing-communication-for-confidential-information}

Stellen Sie wie auch bei anderen Internetanwendungen sicher, dass bei der Übertragung vertraulicher Informationen

* Traffic durch SSL gesichert wird.
* HTTP POST verwendet wird, falls zutreffend.

Dies gilt für vertrauliche Systeminformationen (wie Konfiguration oder Administrationszugriff) und vertrauliche Benutzerinformationen (wie persönliche Daten).

## Spezifische Entwicklungsaufgaben  {#distinct-development-tasks}

### Anpassen von Fehlerseiten {#customizing-error-pages}

Fehlerseiten können in AEM angepasst werden. Dies ist ratsam, um zu vermeiden, dass die Instanz Sling-Ablaufverfolgungen zu internen Serverfehlern ausgibt.

Weitere Informationen finden Sie unter [Anpassen der vom Fehler-Handler angezeigten Seiten](/help/sites-developing/customizing-errorhandler-pages.md).

### Geöffnete Dateien im Java-Prozess  {#open-files-in-the-java-process}

Da AEM auf eine große Anzahl von Dateien zugreifen kann, wird empfohlen, die Anzahl [geöffneter Dateien für einen Java-Prozess](/help/sites-deploying/configuring.md#open-files-in-the-java-process) ausdrücklich für AEM zu konfigurieren.

Um das Problem gering zu halten, sollte bei der Entwicklung darauf geachtet werden, dass geöffnete Dateien so schnell wie irgend möglich richtig geschlossen werden.
