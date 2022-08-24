---
title: Hinzufügen von Search&Promote-Funktionen zu Ihrer Seite
seo-title: Adding Search&Promote Features To Your Page
description: Wenn Sie Search&Promote-Funktionen in Ihre Seite integrieren, können Sie mit den Search&Promote-Komponenten Funktionen, wie die Keyword-Suche, eine erweiterte Suchfunktion auf der Seite mit den Suchergebnissen sowie Banner, zu Ihren Seiten hinzufügen.
seo-description: Integrating Search&Promote capabilities in your web site, you can use the Search&Promote components to add features to your pages such as keyword search, search results page search refinement, and banners.
uuid: 8cd3c143-cb0b-4eb0-931d-9d447ea3c950
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 968b9131-ccdf-4856-b504-bc1a44974980
docset: aem65
exl-id: cf5849c7-1c6a-46d8-9cc4-f1f20a507a0c
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 74%

---

# Hinzufügen von Search&amp;Promote-Funktionen zu Ihrer Seite{#adding-search-promote-features-to-your-page}

Um Search&amp;Promote-Funktionen in Ihre Website zu integrieren, verwenden Sie die Search&amp;Promote-Komponenten zum Hinzufügen der folgenden Funktionen zu Ihren Seiten:

* Keyword-Suche
* Seite mit Suchergebnissen
* Präzisierung der Suche
* Banner

Sie können Search&amp;Promote-Funktionen nur verwenden, wenn sie von Ihrem Adobe Experience Manager-Administrator aktiviert wurden. Siehe [Integration mit Adobe Search&amp;Promote](/help/sites-administering/search-and-promote.md).

Facetten werden auf dem Search&amp;Promote-Server konfiguriert, genau wie die von jeder Komponente bereitgestellten Informationen. Die folgende Tabelle enthält eine kurze Beschreibung der einzelnen Komponenten. Die nachfolgenden Abschnitte enthalten ausführliche Informationen zu deren Verwendung.

<table>
 <tbody>
  <tr>
   <th>Search&amp;Promote-Komponente</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Banner</td>
   <td>Anzeige von Bannerwerbung. Banner werden auf Grundlage der Daten ausgewählt, die von Search&amp;Promote erfasst werden.<br /> </td>
  </tr>
  <tr>
   <td>Breadcrumb</td>
   <td>Zeigt den Suchbegriff und die Reihenfolge der Filter an, die der Benutzer auf Suchergebnisse angewendet hat.</td>
  </tr>
  <tr>
   <td>Facette als Kontrollkästchen-Liste</td>
   <td>Eine Liste mit Kontrollkästchen zur Auswahl von Facetten für das Filtern von Suchergebnissen.</td>
  </tr>
  <tr>
   <td>Facette als Dropdown</td>
   <td>Eine Dropdown-Liste mit Facetten zum Filtern von Suchergebnissen.</td>
  </tr>
  <tr>
   <td>Facette als Link-Liste</td>
   <td>Eine Liste der Facetten-Links für das Filtern von Suchergebnissen.</td>
  </tr>
  <tr>
   <td>Seitenumbruch</td>
   <td>Steuerelemente für die Navigation durch die Seiten von Suchergebnissen.</td>
  </tr>
  <tr>
   <td>Ergebnisse</td>
   <td>Zeigt die Ergebnisse einer Suche nach Begriffen an.</td>
  </tr>
  <tr>
   <td>Suchen</td>
   <td>Fügt ein Suchfeld in die Seite ein.</td>
  </tr>
 </tbody>
</table>

## Suchergebnisseite erstellen {#creating-the-search-results-page}

Verwenden Sie die WCM-Websites-Konsole, um eine Seite für die Anzeige von Suchergebnissen zu erstellen. Die Suchergebnisse aus einer beliebigen Suchkomponente können auf dieser Seite angezeigt werden, sofern für sie dieselben Search&amp;Promote-Services verwendet werden.

Die Komponenten, die es Benutzern ermöglichen, Suchergebnisse zu überprüfen, sind „Ergebnisse“ und „Seitenumbruch“. Die Komponente **[!UICONTROL Ergebnisse]** weist weder im Bearbeitungs- noch im Designmodus konfigurierbare Eigenschaften auf. Die Komponente „Ergebnisse“ listet lediglich Suchergebnisse auf, die Links zu anderen Seiten enthalten, und zeigt die Anzahl der Ergebnisse für jeden Suchbegriff an.

![srchresultscomp](assets/srchresultscomp.png)

Die Komponente **[!UICONTROL Seitenumbruch]** ermöglicht Benutzern die Navigation durch mehrere Seiten mit Suchergebnissen. Benutzer können die Anzahl der Seiten einsehen, zur nächsten oder vorherigen Seite wechseln, eine zu öffnende Seite auswählen und alle Ergebnisse auf einer Seite zusammenfassen.

![srchpagination](assets/srchpagination.png)

Sie können die folgenden Komponenteneigenschaften im Bearbeitungsmodus konfigurieren, um das Verhalten zur Laufzeit zu steuern:

* Ausblenden einer einzelnen Ergebnisseite: Wählen Sie diese Option aus, wenn Sie die Seitennavigationssteuerelemente ausblenden möchten, wenn die Suche eine einzelne Ergebnisseite zurückgibt.
* Erste/Letzte ausblenden: Wählen Sie diese Option aus, wenn Sie verhindern möchten, dass Benutzer zur ersten oder letzten Ergebnisseite springen.
* Vorherige/Nächste ausblenden: Legt fest, ob Benutzer zu Ergebnisseiten relativ zur aktuellen Seite navigieren können.
* „Alle anzeigen“ ausblenden: Legt fest, ob Benutzer alle Suchergebnisse auf einer einzigen Seite zusammenfassen können. In der Regel erfolgt die Nutzung von Serverressourcen bei Daten mit Seitenaufteilung effizienter. Wählen Sie diese Option aus, wenn Sie die Übertragung großer Datensätze in einer Antwortnachricht verhindern möchten.

### Aktivieren der Filterung der Ergebnisse nach Facetten {#enabling-the-filtering-of-results-by-facets}

Sie können Benutzern die Filterung von Suchergebnissen durch Facetten ermöglichen. Die **[!UICONTROL Facette der Kontrollkästchen-Liste]**, **[!UICONTROL Dropdown-Facette]** und **[!UICONTROL Facette der Link-Liste]** -Komponenten ermöglichen es Benutzern, eine oder mehrere Facetten zum Filtern auszuwählen. Bei Verwendung dieser Komponenten sollten Sie auch die Komponente **Breadcrumbs** einschließen. Breadcrumbs zeigen die aktuell verwendeten Filter an.

Die **[!UICONTROL Facette der Kontrollkästchen-Liste]**, **[!UICONTROL Dropdown-Facette]** und **[!UICONTROL Facette der Link-Liste]** Komponenten verfügen jeweils über die folgenden Eigenschaften, die Sie in **Bearbeiten** mode:

* **Facettenname**: Der Name der zur Filterung verwendeten Facette.

Die Komponente **[!UICONTROL Facette als Kontrollkästchen-Liste]** zeigt eine Liste von Facetten an, die jeweils ein Kontrollkästchen aufweisen. Verwenden Sie **[!UICONTROL Facette als Kontrollkästchen-Liste]**, damit Benutzer eine Untergruppe von Ergebnissen anzeigen können, die Elemente aus mehreren Facetten enthalten. Beispielsweise ist die **Marken-Facette geeignet, da mehrere Marken dieselbe Art von Produkt anbieten.**

Ein Kontrollkästchen wird für jede Facette angezeigt, die mit einem Suchergebnis verbunden ist. Wenn ein Benutzer ein Kontrollkästchen aktiviert, wird die Seite mit einem aktualisierten Ergebnissatz neu geladen. Alle Kontrollkästchen verbleiben auf der Seite, damit Kunden jederzeit zur weiteren Filterung Facetten hinzufügen oder entfernen können:

![sandpcheckboxcomp](assets/sandpcheckboxcomp.png)

Die Komponente **[!UICONTROL Facette als Dropdown]** ermöglicht es Kunden, ein Facettenelement in einer Dropdown-Liste auszuwählen. Diese Komponente ist hilfreich, wenn Sie möchten, dass Kunden sich umgehend auf ein einzelnes Facettenelement konzentrieren können. Beispielsweise ist die Facette „Abteilung“ dafür geeignet, Kunden die Einschränkung von Produktsuchen nach Abteilung zu ermöglichen. John sucht *Jeans* und schränkt danach die Suche auf die Herrenabteilung ein.

Die Dropdown-Liste wird mit den Facetten gefüllt, die mit allen Suchergebnissen verbunden sind. Bei Auswahl eines Elements in der Dropdown-Liste wird die Seite mit einem aktualisierten Ergebnissatz neu geladen. Die Elemente in der Dropdown-Liste ändern sich nicht, sodass Kunden jederzeit zwischen verschiedenen Facetten wechseln können.

![SandpDropdown-Abteilung](assets/sandpdropdowndepartment.png)

Mit der Komponente **[!UICONTROL Facette als Link-Liste]** können Kunden ihren Fokus immer stärker auf Elemente beschränken, die unter mehreren Facettenmitgliedern bzw. Facetten kategorisiert sind.

Facettenmitglieder werden als Liste von Links angezeigt. Der Text eines Links entspricht dem Namen des jeweiligen Facettenmitglieds, das mit den aktuellen Suchergebnissen verbunden ist. Wenn ein Kunde auf einen solchen Link klickt, wird die Seite neu geladen und eine Untergruppe der Suchergebnisse wird angezeigt. Die Liste der Links wird entsprechend aktualisiert, sodass der Fokus noch weiter eingeschränkt werden kann.

![Sandplinklistcomp](assets/sandplinklistcomp.png)

Die Links in der Liste ändern sich auch, wenn ein Search&amp;Promote aus einem anderen Komponententyp angewendet wird. Durch die Verwendung von Filterkomponenten mehrerer Typen sind effektive Filterkombinationen möglich.

Die Komponente **[!UICONTROL Breadcrumbs]** ermöglicht es Kunden, die aktuell auf Suchergebnisse angewendeten Filter in der Reihenfolge, in der sie angewendet wurden, einzusehen. Kunden können auf die Elemente im Breadcrumb klicken, um die entsprechende Filterkombination wiederherzustellen.

![sandpbreadcrumbcomp](assets/sandpbreadcrumbcomp.png)

Sie können die folgenden Eigenschaften für Breadcrumbs im Bearbeitungsmodus konfigurieren, um das Erscheinungsbild der Komponente anzupassen:

* Trennzeichen: Definieren Sie das Zeichen oder die Zeichenfolge für die Verwendung als Trennzeichen zwischen den einzelnen Breadcrumbs. Die **[!UICONTROL Trennzeichen]** -Feld akzeptiert eine beliebige Zeichenfolge als Eingabe. Die Standardeinstellung ist: „>“ (ohne die Anführungszeichen)
* Nachfolgende Trennzeichen: Definieren Sie ein Zeichen oder eine Zeichenfolge für die Anzeige am Ende der Breadcrumbs. Die **[!UICONTROL Nachfolgende Trennzeichen]** -Feld akzeptiert eine beliebige Zeichenfolge als Eingabe. Die Standardeinstellung für dieses Feld ist &#42;blank&#42; (d. h. am Ende der Breadcrumb-Linie wird nichts angezeigt)

### Suchfelder hinzufügen {#adding-search-boxes}

Die **[!UICONTROL Suche]** -Komponente können Kunden Suchbegriffe suchen. Hinzufügen **[!UICONTROL Suche]** Komponenten zu jeder Seite hinzufügen, auf der Sie Zugriff auf die Suche gewähren möchten.

Konfigurieren Sie die folgenden Eigenschaften im Bearbeitungsmodus, damit Sie das Laufzeitverhalten steuern können:

* Pfad zur Ergebnisseite: Der Pfad zu der Seite, auf der die Suchergebnisse anzeigt werden.
* „Automatisch auffüllen“ aktivieren: Wählen Sie diese Option aus, um Vorschläge für Suchbegriffe anzuzeigen, wenn der Kunde mit der Eingabe im Suchfeld beginnt.

![sandpsearchcomp](assets/sandpsearchcomp.png)

### Hinzufügen von Bannern {#adding-banners}

Die **[!UICONTROL Banner]** -Komponente zeigt Banneranzeigen entsprechend den Search&amp;Promote des Kunden an. Logik auf dem Search&amp;Replace-Server ermittelt, welches Banner angezeigt wird. Beispielsweise könnte bei einer Suche nach Jeans ein Banner angezeigt werden, das mit Mode zu tun hat. Durch Filtern auf die Herrenabteilung könnte die Auswahl des Banners noch weiter verfeinert werden.

Die **[!UICONTROL Banner]** -Komponente bietet eine konfigurierbare Eigenschaft mit dem Namen Bannerbereich. Klicken Sie im Bearbeitungsmodus auf einen der Eigenschaftswerte, um die Darstellungsweise des Banners festzulegen. Der Search&amp;Promote-Service legt die Liste der Werte fest, aus denen Sie auswählen können.

### Beispiel für Search&amp;Promote-Suchseite {#example-search-promote-search-page}

Das folgende Diagramm zeigt die Komponenten, die zu einer Seite hinzugefügt werden, um die unten aufgeführte vollfunktionsfähige Search&amp;Promote-Ergebnisseite zu erstellen.

![1328213789109](assets/1328213789109.png) ![Sandpage-Beispiel](assets/sandppageexample.png)
