---
title: Erstellen und Verwenden von Designs
description: Sie können Designs verwenden, um ein adaptives Formular oder eine interaktive Kommunikation zu stilisieren und eine visuelle Identität bereitzustellen. Sie können ein Design für eine beliebige Anzahl adaptiver Formulare oder interaktiver Kommunikation freigeben.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop, interactive-communications
content-strategy: max-2018
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 93c360a8-a9d9-4c4b-b7e2-2c44eaf4604c
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '6086'
ht-degree: 83%

---

# Erstellen und Verwenden von Designs {#creating-and-using-themes}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/themes.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Einführung {#introduction}

Sie können Designs erstellen und anwenden, um ein adaptives Formular oder eine interaktive Kommunikation zu stilisieren. Zu einem Design gehören Stildetails für die Komponenten und Bedienfelder. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten wider. Design werden unabhängig voneinander verwaltet, ohne dass auf ein adaptives Formular oder interaktive Kommunikation verwiesen wird.

Sie haben folgende Möglichkeiten:

* Erstellen von Designs
* Ein vorhandenes Design bearbeiten und kopieren
* Herunterladen und Hochladen eines vorhandenen Designs auf den AEM Forms-Server
* Verwalten von Abhängigkeiten für ein Design

## Erstellen, Herunterladen und Hochladen eines Designs {#creating-downloading-or-uploading-a-theme}

Mit AEM Forms können Sie Designs erstellen, herunterladen und hochladen. Ein Design wird wie andere Assets erstellt, z. B. Formulare, Dokumente und Briefe. Das Design wird als separate Entität mit Meta-Eigenschaften wie Formularen gespeichert. Designs, die eine separate Entität sind, ermöglichen die Wiederverwendung in mehreren adaptiven Formularen und interaktiver Kommunikation. Sie können ein Design auch in eine andere Instanz von AEM Forms verschieben und wiederverwenden.

### Erstellen von Designs {#creating-a-theme}

Führen Sie die folgenden Schritte aus, um ein Design zu erstellen:

1. Klicken Sie auf **Adobe Experience Manager**, klicken Sie auf **Formulare** und dann auf **Designs**.

1. Klicken Sie auf der Seite „Designs“ auf **Erstellen > Design**.
Ein Assistent zum Erstellen eines Designs wird gestartet.

1. Geben Sie auf der Registerkarte „Einfach“ im Assistenten „Design erstellen“ **Titel** und **Name** des Designs ein. Dies sind Pflichtfelder.

1. Auf der Registerkarte „Erweitert“ sind zwei Felder enthalten:

   * **Clientlib-Speicherort**: Speicherort im Repository, in dem die Clientlibs für das Design gespeichert sind.

   * **Clientlib-Kategorie**: Bietet ein Textfeld zur Eingabe des gewünschten Clientlib-Kategorienamen für das Design.

1. Klicken Sie auf **Erstellen** und anschließend auf **Bearbeiten**, um das Design im Design-Editor zu öffnen, oder klicken Sie auf **Fertig**, um zur Seite mit den Designs zurückzukehren.

### Download eines Designs {#downloading-a-theme}

Sie können Designs als ZIP-Datei exportieren und in anderen Projekten oder AEM-Instanzen verwenden. Herunterladen von Designs

1. Klicken Sie auf **Adobe Experience Manager**, klicken Sie auf **Formulare** und dann auf **Designs**.

1. Wählen Sie in der Designs-Seite **ein Design aus** und klicken Sie auf **Herunterladen**. Ein Dialogfeld mit den Details des Designs wird angezeigt.

1. Klicken Sie auf **Herunterladen**. Das Design wird als eine zip.-Datei heruntergeladen.

>[!NOTE]
>
>Wenn Sie ein Design herunterladen, dem ein adaptives Formular zugeordnet ist und das zugehörige adaptive Formular auf einer benutzerdefinierten Vorlage basiert, laden Sie auch die benutzerdefinierte Vorlage herunter. Wenn Sie das heruntergeladene Design und adaptive Formular auf einen AEM Forms-Server hochladen, laden Sie die zugehörige benutzerdefinierte Vorlage auch hoch.

### Hochladen eines Designs {#uploading-a-theme}

Sie können erstellte Designs mit Stilvorgaben für Ihr Projekt verwenden. Sie können Design-Pakete importieren, die von anderen erstellt werden, indem Sie sie in Ihr Projekt hochladen.

Hochladen von Designs

1. Klicken Sie auf **Adobe Experience Manager**, klicken Sie auf **Formulare** und dann auf **Designs**.

1. Auf der Seite „Designs“ klicken Sie auf **Erstellen > Datei-Upload**.
1. In der Eingabeaufforderung zu „Datei-Upload“ suchen Sie ein Design-Paket auf Ihrem Computer, wählen es aus und klicken auf **Hochladen**.
Das hochgeladene Design ist auf der Seite „Designs“ verfügbar.

## Metadaten eines Designs {#metadata-of-a-theme}

Liste der Metaeigenschaften eines Designs (auf der Eigenschaftenseite eines Designs).

<table>
 <tbody>
  <tr>
   <th><p><strong>ID</strong></p> <p> </p> </th>
   <th><strong>Name</strong></th>
   <th><strong>Kann bearbeitet werden</strong></th>
   <th><strong>Beschreibung der Eigenschaft</strong></th>
  </tr>
  <tr>
   <td>1.</td>
   <td>Titel</td>
   <td>Ja</td>
   <td>Anzeigename des Designs.</td>
  </tr>
  <tr>
   <td>2.</td>
   <td>Beschreibung</td>
   <td>Ja</td>
   <td>Beschreibung des Designs.</td>
  </tr>
  <tr>
   <td>3.</td>
   <td>Typ</td>
   <td>Nein</td>
   <td>
    <ul>
     <li>Asset-Typ.</li>
     <li>Wert ist immer „Design“.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>4.</td>
   <td>Erstellt</td>
   <td>Nein</td>
   <td>Datum der Designerstellung</td>
  </tr>
  <tr>
   <td>5.</td>
   <td>Name des Autors oder der Autorin</td>
   <td>Ja</td>
   <td>Autor oder Autorin des Designs. Wird zum Zeitpunkt der Design-Erstellung berechnet.</td>
  </tr>
  <tr>
   <td>6.</td>
   <td>Datum der letzten Änderung</td>
   <td>Nein</td>
   <td>Datum der letzten Änderung des Designs.</td>
  </tr>
  <tr>
   <td>7.</td>
   <td>Status</td>
   <td>Nein</td>
   <td>Status des Designs (Geändert/Veröffentlicht).</td>
  </tr>
  <tr>
   <td>8.</td>
   <td>Einschaltzeit für Veröffentlichung</td>
   <td>Ja</td>
   <td>Zeitpunkt der automatischen Veröffentlichung des Designs.</td>
  </tr>
  <tr>
   <td>9.</td>
   <td>Ausschaltzeit für Veröffentlichung</td>
   <td>Ja</td>
   <td>Zeitpunkt, zu dem die Veröffentlichung des Designs automatisch aufgehoben wird.</td>
  </tr>
  <tr>
   <td>10.</td>
   <td>Tags</td>
   <td>Ja</td>
   <td>Eine Beschriftung am Design zur Kennzeichnung, um die Suche zu erleichtern.</td>
  </tr>
  <tr>
   <td>11.</td>
   <td>Verweise</td>
   <td>Links</td>
   <td>
    <ul>
     <li>Enthält einen Abschnitt „Verweis von“. Listet Formulare auf, die das Design verwenden.</li>
     <li>Da das Design nicht auf ein anderes Asset verweist, gibt es keinen Abschnitt "Verweise".</li>
    </ul> </td>
  </tr>
  <tr>
   <td>12.</td>
   <td>Clientlib-Speicherort</td>
   <td>Ja</td>
   <td>
    <ul>
     <li>Der benutzerdefinierte Repository-Pfad innerhalb von "/etc", in dem die clientlibs, die diesem Design entsprechen, gespeichert werden.</li>
     <li>Standardwert - "/etc/clientlibs/fd/themes"+ relativer Pfad des Design-Assets.</li>
     <li>Wenn der Speicherort nicht vorhanden ist, wird die Ordnerhierarchie automatisch generiert.</li>
     <li>Wenn dieser Wert geändert wird, wird die clientlib-Knotenstruktur an den neuen eingegebenen Speicherort verschoben.<br /> <em><strong>Hinweis:</strong> Wenn Sie den standardmäßigen clientlib-Speicherort ändern, weisen Sie im CRXDE-Repository die <code>crx:replicate</code>, <code>rep:write</code>, <code>rep:glob:*</code>, <code>rep:itemNames::</code> <code>js.txt</code>, <code>jcr:read</code> nach <code>forms-users</code> und <code>crx:replicate</code>, <code>jcr:read</code> nach <code>fd-service</code> am neuen Speicherort. Fügen Sie außerdem eine weitere ACL hinzu, indem Sie <code>deny jcr:addChildNodes</code> für <code>forms-user</code></em> hinzufügen</li>
    </ul> </td>
  </tr>
  <tr>
   <td>13.</td>
   <td>Clientlib-Kategoriename</td>
   <td>Ja</td>
   <td>
    <ul>
     <li>Der benutzerdefinierte clientlib-Kategoriename für dieses Design.</li>
     <li>Wenn der Name bereits von einem anderen vorhandenen Design verwendet wird, wird ein Fehler angezeigt.</li>
     <li>Standardwert - berechnet mithilfe des Designspeicherorts.</li>
     <li>Wenn dieser Wert geändert wird, wird der Kategoriename auf dem entsprechenden clientlib-Knoten aktualisiert. Das Aktualisieren des Clientlib-Kategorienamen in den JSP-Dateien ist nicht erforderlich, da der clientlib-Kategoriename als Referenz verwendet wird.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Informationen zum Design-Editor {#about-the-theme-editor}

AEM Forms ist mit dem Design-Editor ausgestattet. Dabei handelt es sich um eine benutzerfreundliche Benutzeroberfläche für Geschäftskunden und Web-Designer/Entwickler mit Funktionen zur einfachen Festlegung der Formatierung für verschiedene Elemente für adaptive Formulare und interaktive Kommunikation. Wenn Sie ein Design erstellen, wird es als separate Entität wie Formulare, interaktive Kommunikation, Briefe, Dokumentfragmente und Datenwörterbücher gespeichert.

Mit dem Design-Editor können Sie Stile der in einem Design formatierten Komponenten anpassen. Sie können anpassen, wie ein Formular oder eine interaktive Kommunikation auf einem Gerät aussieht.

Der Design-Editor ist in zwei Bereiche unterteilt:

* **Arbeitsfläche** – Wird auf der rechten Seite angezeigt. Es wird ein Beispiel für ein adaptives Formular oder eine interaktive Kommunikation angezeigt, in dem alle Stiländerungen sofort übernommen werden. Sie können Objekte auch direkt auf der Arbeitsfläche auswählen, um die damit verknüpften Stile anzuzeigen und diese Stile zu bearbeiten. Ein Lineal für die Geräteauflösung an der Oberseite steuert die Arbeitsfläche. Wenn Sie einen Auflösungshaltepunkt aus dem Lineal auswählen, wird die Vorschau des Beispielformulars oder der interaktiven Kommunikation für die jeweilige Auflösung angezeigt. Die Arbeitsfläche wird im Detail weiter [unten](../../forms/using/themes.md#using-canvas) beschrieben.

* **Seitenleiste** – Wird auf der linken Seite angezeigt. Sie umfasst die folgenden Elemente:

   * **Selektor:** Zeigt die für die Formatierung ausgewählte Komponente und die Eigenschaften, die Sie gestalten können, an. Der Selektor stellt alle Komponenten eines bestimmten Typs dar. Wenn Sie eine Textfeldkomponente in einem Design für die Formatierung auswählen, übernehmen alle Textfelder in Ihrem Formular oder in der interaktiven Kommunikation den Stil. Mit Selektoren können Sie eine generische Komponente oder eine bestimmte Komponente für die Gestaltung auswählen. Beispielsweise ist eine Feldkomponente eine allgemeine Komponente, und ein Textfeld ist eine spezielle Komponente.

     **Formatierung allgemeiner Komponenten:**
Ein Feld kann ein numerisches Feld wie Alter oder ein Textfeld wie Adresse sein.
Wenn Sie einen Stil für ein Feld definieren, werden alle Felder wie Alter, Name, Adresse entsprechend formatiert.

     **Formatierung einer spezifischen Komponente**: Eine spezifische Komponente wirkt sich auf die Objekte der betreffenden Kategorie aus. Wenn Sie im Design für die Komponente „Numerisches Feld“ einen Stil definieren, wird der Stil nur auf das numerische Feldobjekt angewendet.

     Beispiel: Ein Textfeld wie Adresse ist länger und ein numerisches Feld wie Alter ist kürzer. Sie können ein numerisches Feld auswählen, seine Länge verringern und auf das Formular anwenden. Die Breite aller numerischen Felder wird in Ihrem Formular verringert.

     Wenn Sie alle Feldkomponenten mit einer bestimmten Hintergrundfarbe anpassen, übernehmen alle Felder in Ihrem Formular, wie Alter, Name und Adresse, die Hintergrundfarbe. Wenn Sie ein numerisches Feld wie Alter auswählen und seine Breite verringern, wird die Breite aller numerischer Felder, wie Alter, Anzahl der Personen in einer Familie, verringert. Die Breite von Textfeldern wird nicht geändert.

   * **Status:** Hier können Sie die Stile eines Objekts mit einem bestimmten Status anpassen. Beispielsweise können Sie festlegen, wie ein Objekt mit dem Status „Standard“, „Fokus“, „Deaktiviert“, „Mausberührung“ oder „Fehler“ aussieht.
   * **Eigenschaftenkategorien:** Formatierungseigenschaften sind in verschiedene Kategorien unterteilt. Beispiel: Abmessung und Position, Text, Hintergrund, Rahmen und Effekte. Unter jeder Kategorie geben Sie Informationen zur Formatierung an. Unter „Hintergrund“ können Sie z. B. „Hintergrundfarbe“ sowie „Bild und Verlauf“ angeben.

   * **Erweitert:** Hier können Sie einem Objekt benutzerdefiniertes CSS hinzufügen, womit im Falle einer Überschneidung die durch visuelle Steuerelemente definierten Eigenschaften überschrieben werden.

   * **CSS anzeigen**: Ermöglicht das Anzeigen von CSS für die ausgewählte Komponente

  Zusätzlich befindet sich unten in der Seitenleiste ein Pfeil. Wenn Sie auf den Pfeil klicken, erhalten Sie zwei zusätzliche Optionen: **Erfolg simulieren** und **Fehler simulieren.** Diese Optionen werden zusammen mit den oben beschriebenen Optionen [nachfolgend](../../forms/using/themes.md#using-rail) detailliert erläutert.

[![Design-Editor mit hervorgehobener Leiste und Arbeitsfläche.](assets/themes.png)](assets/themes-1.png) **A.** Seitenleiste **B.** Arbeitsfläche

### Formatieren von Komponenten {#styling-components}

Sie können ein Design in mehreren Formularen und interaktiver Kommunikation verwenden, wodurch die Formatierung der Formularkomponenten importiert wird, die Sie im Design angegeben haben. Sie können mehrere Komponenten formatieren, z. B. Titel, Beschreibungen, Bereiche, Felder, Symbole und Textfelder. Verwenden Sie Widgets zum Konfigurieren von Komponenteneigenschaften in einem Design. Vorkenntnisse im Umgang mit CSS oder LESS sind nicht erforderlich, aber wünschenswert, obwohl Sie im Abschnitt „CSS-Überschreibung“ CSS-Code schreiben oder benutzerdefinierte Selektoren bereitstellen können. Der Abschnitt „CSS-Überschreibung“ wird angezeigt, wenn Sie eine Komponente in der Seitenleiste auswählen.

![Formatierbare Komponenten in der Seitenleiste](assets/stylable-components.png)

Optionen in der Seitenleiste, mit denen Sie verschiedene Komponenten auswählen und gestalten können.

Wenn Sie auf die Schaltfläche „Bearbeiten“ für eine Komponente in der Seitenleiste klicken, wird die Komponente auf der Arbeitsfläche ausgewählt, und Sie können die Komponente mithilfe der Optionen in der Seitenleiste formatieren.

Bestimmte Komponenten, wie Textfelder, numerische Felder, Optionsfelder und Kontrollkästchen, werden unter allgemeinen Komponenten, wie „Feld“, kategorisiert. Angenommen, Sie möchten die Formatierung von Optionsfeldern anpassen. Um Optionsfelder für die Formatierung auszuwählen, wählen Sie **Feld > Widget > Optionsfeld**.

Klicks **ALLE erweitern** in der Seitenleiste, um kategorisierte Komponenten, die nicht im Voraus sichtbar sind, anzuzeigen, auszuwählen und zu formatieren.

### Formatieren von Bereichslayouts {#styling-panel-layouts-br}

Designs in AEM Forms unterstützen den Stil von Elementen im Layout von Bereichen in Ihren Formularen in der interaktiven Kommunikation. Die Gestaltung von Elementen in standardmäßigen Layouts und benutzerdefinierten Layouts wird unterstützt.

Zu den standardmäßigen Bedienfeldern gehören:

* Registerkarten links
* Registerkarten oben
* Akkordeon
* Responsiv
* Assistent
* Layout für Mobilgeräte

   * Bedienfeldnamen in der Kopfzeile
   * Ohne Bedienfeldnamen in der Kopfzeile

Die Selektoren variieren je nach Layout.
Die Formatierung benutzerdefinierter Layouts im Design-Editor umfasst Folgendes:

* Definieren der Komponenten für ein Layout, das formatiert werden kann, und der CSS-Selektoren für die eindeutige Identifizierung dieser Komponenten
* Definieren der CSS-Eigenschaften, die auf diese Komponenten angewendet werden können
* Definieren der Formatierung für diese Komponenten interaktiv über die Benutzeroberfläche

### Unterschiedliche Stile für unterschiedliche Bildschirmgrößen {#different-styles-for-different-screen-sizes-br}

Layouts für Desktop- und Mobilgeräte können leicht oder völlig unterschiedliche Stile aufweisen. Bei Mobilgeräten verwenden Tablets und Smartphones ähnliche Layouts, mit Ausnahme der Komponentengrößen.

Verwenden Sie Design-Editor-Haltepunkte, um alternative Stile für verschiedene Bildschirmgrößen zu definieren. Sie können ein Basisgerät oder eine Auflösung auswählen, mit dem bzw. der Sie mit der Erstellung des Designs beginnen. Die Stilvarianten für andere Auflösungen werden automatisch generiert. Sie können die Gestaltung für alle Auflösungen explizit ändern.

>[!NOTE]
>
>Das Design wird zuerst mit einem Formular oder einer interaktiven Kommunikation erstellt und dann auf verschiedene Formulare oder interaktive Kommunikation angewendet. Die Haltepunkte, die bei der Designerstellung verwendet werden, können sich von dem Formular oder der interaktiven Kommunikation unterscheiden, auf die das Design angewandt wird. Die CSS-Medienabfragen basieren auf dem Formular oder der interaktiven Kommunikation, das/die bei der Erstellung des Designs verwendet wird, und nicht auf dem Formular oder der interaktiven Kommunikation, auf das/die das Design angewandt wird.

### Kontextänderungen der Formatierungseigenschaften in der Seitenleiste bei der Auswahl der Objekte {#styling-properties-context-changes-in-sidebar-on-selecting-objects}

Wenn Sie eine Komponente auf der Arbeitsfläche auswählen, werden ihre Stileigenschaften in der Seitenleiste angezeigt. Wählen Sie den Objekttyp und seinen Status aus und geben Sie dann dessen Stil vor.

### Kürzlich verwendete Stile im Design-Editor {#recently-used-styles-in-theme-editor}

Der Design-Editor speichert bis zu 10 Stile, die auf eine Komponente angewendet werden. Die im Cache gespeicherten Stile können für andere Komponenten eines Designs verwendet werden. Kürzlich verwendete Stile stehen direkt unter der ausgewählten Komponente in der Seitenleiste in Form eines Listenfelds zur Auswahl. Zunächst ist die Liste der kürzlich verwendeten Stile leer.

![asset-library](assets/asset-library.png)

Während Sie eine Komponente gestalten, werden die Stile zwischengespeichert und im Listenfeld aufgelistet. In diesem Beispiel wird die Beschriftung des Textfelds so gestaltet, dass die Schriftgröße und -farbe geändert wird. Sie können ähnliche Schritte zum Auswählen eines Bildes oder zum Ändern der Farben ausführen, um eine Komponente zu gestalten. Beobachten Sie, wie der Stil zwischengespeichert und im Listenfeld aufgeführt wird, wenn die Gestaltung für Feldtitel geändert wird.

![Schrifttyp zwischengespeichert für eine Komponente, die für andere verfügbar ist](assets/font-style-cached.png)

In diesem Beispiel wird der Stil für die Feldbeschriftung geändert, und wenn Responsive-Bedienfeldbeschreibung für den Stil ausgewählt ist, wird ein Listeneintrag in der Asset-Bibliothek hinzugefügt. Der Eintrag in der Asset-Bibliothek kann verwendet werden, um den Stil für die Responsive-Bedienfeldbeschreibung zu ändern.

Wenn ein Stil in der Asset-Bibliothek hinzugefügt wird, steht er für andere Designs und im [Stil-Modus](../../forms/using/inline-style-adaptive-forms.md) des Formular-Editors oder in der Editor-Benutzeroberfläche der interaktiven Kommunikation zur Verfügung. Wenn Sie den Stilmodus des Formular-Editors verwenden, um den Stilmodus des Formular-Editors oder der interaktiven Kommunikations-Editor-Benutzeroberfläche zum Gestalten einer Komponente zu verwenden, wird der Stil ebenfalls zwischengespeichert und steht in den Designs zur Verfügung.

Mit der Plus-Schaltfläche in der Asset-Bibliothek können Sie den Stil dauerhaft mit einem angegebenen Namen speichern. Mit der Plus-Schaltfläche wird der Stil gespeichert, auch wenn Sie nicht in der Seitenleiste auf die Schaltfläche „Speichern“ klicken, um den Stil auf eine Komponente anzuwenden. Die Plus-Schaltfläche zum Speichern eines Stils für die spätere Verwendung ist im Stilmodus nicht verfügbar.

![Bereitstellen eines benutzerdefinierten Stilnamens für die Asset-Bibliothek](assets/custom-style-name.png)

Wenn Sie einen benutzerdefinierten Namen für einen Stil angeben, ist der Stil an ein Design gebunden und nicht mehr für andere Designs verfügbar. So löschen Sie einen gespeicherten Stil:

1. Klicken Sie in der Symbolleiste der Arbeitsfläche auf **Themenoptionen** ![Themenoptionen](assets/theme-options.png) > **Stile verwalten**.
1. Wählen Sie im Dialogfeld „Stile verwalten“ einen gespeicherten Stil aus und klicken Sie auf **Löschen**.

   ![Löschen eines gespeicherten Stils](assets/manage-styles.png)

### Live-Vorschau, Speichern und Verwerfen von Änderungen {#live-preview-save-and-discard-changes}

Änderungen, die an der Formatierung vorgenommen wurden, werden sofort in dem Formular oder in der interaktiven Kommunikation auf der Arbeitsfläche widergespiegelt. Mit der Live-Vorschau können Sie die Auswirkungen des Stils interaktiv definieren und anzeigen. Wenn Sie die Gestaltung einer Komponente ändern, wird die Schaltfläche **Fertig** in der Seitenleiste aktiviert. Um Änderungen beizubehalten, verwenden Sie die Schaltfläche **Fertig**.

>[!NOTE]
>
>Wenn ein ungültiges Zeichen in ein Feld eingegeben wird, wird die Farbe der Feldgrenze in Rot geändert und in der oberen linken Ecke des Bildschirms wird eine Fehlermeldung angezeigt. Wenn Sie z. B. Alphabetzeichen in ein Textfeld eingeben, das numerische Zeichen als Eingabe akzeptiert, wird die Rahmenbegrenzung des Eingabefelds rot. Sie können ein solches Design nicht speichern, ohne den oben angezeigten Fehler zu beheben.

### Design mit einem anderen adaptiven Formular oder interaktiver Kommunikation {#theme-with-another-adaptive-form-or-interactive-communication}

Wenn Sie ein Design erstellen, wird es mit einem Formular erstellt, das im Lieferumfang des Design-Editors enthalten ist. In diesem Formular geben Sie die Gestaltung der Komponenten an. Anstelle des Formulars, das mit dem Design-Editor versendet wird, können Sie ein Formular oder eine interaktive Kommunikation Ihrer Wahl auswählen, um die Formatierung vorzugeben, und die Ergebnisse in der Vorschau anzeigen.

So ersetzen Sie das aktuelle Formular oder die interaktive Kommunikation auf der Arbeitsfläche des Design-Editors:

1. Klicken Sie im Bereich „Design-Editor“ auf **Themenoptionen** ![Themenoptionen](assets/theme-options.png) > **Konfigurieren**.

1. Wählen Sie auf der Registerkarte „Allgemein“ ein Formular oder eine interaktive Kommunikation für das Feld **Adaptives Formular/Dokument** aus.

### Wiederholen/Rückgängigmachen {#redo-undo}

Sie können unerwünschte versehentliche Änderungen rückgängig machen oder wiederherstellen. Verwenden Sie die Schaltflächen „Wiederholen“/„Rückgängig“ auf der Arbeitsfläche.

![Wiederholen und Rückgängigmachen von Aktionen](assets/redo_undo_new.png)

Schaltflächen zum Rückgängigmachen/Wiederherstellen auf der Arbeitsfläche

Die Schaltflächen „Wiederholen“/„Rückgängig“ werden angezeigt, wenn Sie eine Komponente im Design-Editor formatieren.

## Verwenden des Design-Editors {#using-the-theme-editor}

Mit dem Design-Editor können Sie ein Design bearbeiten, das Sie erstellt oder hochgeladen haben. Navigieren Sie zu **Formulare und Dokumente > Designs**, wählen Sie ein Design aus und öffnen Sie es. Das Design wird im Design-Editor geöffnet.

Wie bereits erwähnt, besteht der Design-Editor aus zwei Bereichen: Seitenleiste und Arbeitsfläche.
![theme-editor](assets/theme-editor.png)

Anpassen der Gestaltung für den Erfolgsstatus der Komponente Widget „Textfeld“ im Design-Editor. Die Komponente wird auf der Arbeitsfläche ausgewählt und ihr Status wird in der Seitenleiste ausgewählt. Die in der Seitenleiste verfügbaren Stiloptionen werden verwendet, um das Erscheinungsbild einer Komponente anzupassen.

### Verwenden der Arbeitsfläche {#using-canvas}

Das Design wird entweder mit dem nativen Formular oder mit einem Formular oder einer interaktiven Kommunikation Ihrer Wahl erstellt. Die Arbeitsfläche zeigt die Vorschau des Formulars oder der interaktiven Kommunikation an, die zum Erstellen des Designs mit den im Design festgelegten Anpassungen verwendet wird. Das Lineal über dem Formular wird verwendet, um das Layout entsprechend der Größe der Anzeige auf Ihrem Gerät zu bestimmen.

In der Symbolleiste der Arbeitsflächen sehen Sie Folgendes:

* **Seitliches Bedienfeld ein/aus** ![Seitenleiste ein/aus](assets/toggle-side-panel.png): Hiermit können Sie die Seitenleiste ein- oder ausblenden.
* **Themenoptionen** ![Themenoptionen](assets/theme-options.png): Bietet drei Optionen.

   * Konfigurieren: Bietet Optionen zum Auswählen des Vorschauformulars oder der interaktiven Kommunikation, der Basis-Clientlib und der Adobe Fonts-Konfiguration.
   * Design-CSS anzeigen: Erzeugt CSS für das ausgewählte Design.
   * Stile verwalten: Bietet Optionen zum Verwalten von Text- und Bildstilen.
   * Hilfe: Zeigt eine Einführung in den Design-Editor mit Abbildungen an.

* **Emulator** ![Lineal](assets/ruler.png): Emuliert das Erscheinungsbild des Designs für verschiedene Displaygrößen. Eine Displaygröße wird im Emulator als Haltepunkt behandelt. Sie können einen Breakpoint auswählen und einen Stil dafür festlegen. Zwei solche Haltepunkte sind beispielsweise „Desktop“ und „Tablet“. Sie können unterschiedliche Formate für jeden Haltepunkt angeben.

Wenn Sie eine Komponente auf der Arbeitsfläche auswählen, wird die Komponenten-Symbolleiste darüber angezeigt. Über die Komponenten-Symbolleiste können Sie Komponenten auswählen oder zu allgemeinen Komponenten wechseln. Sie wählen beispielsweise ein numerisches Textfeld in einem Bedienfeld aus. Die folgenden Optionen werden in der Komponenten-Symbolleiste angezeigt:

* **Widget „Numerisches Feld“**: Ermöglicht Ihnen die Auswahl der Komponente, um ihr Erscheinungsbild in der Seitenleiste anzupassen.
* **Widget „Feld“**: Ermöglicht die Auswahl der allgemeinen Komponente für die Gestaltung. In diesem Beispiel werden alle Texteingabekomponenten (Textfeld/numerisches Feld/numerische Schritte/Datumseingabe) für die Formatierung ausgewählt.

* ![field-level](assets/field-level.png): Hiermit können Sie zur allgemeinen Komponente für die Formatierung wechseln. Wenn Sie „Numerisches Feld“ und dann dieses Symbol auswählen, wird die Feldkomponente ausgewählt. Wenn Sie „Feldkomponente“ und dann dieses Symbol auswählen, wird das Bedienfeld ausgewählt. Wenn Sie mehrfach zur Auswahl auf dieses Symbol tippen, wählen Sie das Formularlayout für die Formatierung aus.

>[!NOTE]
>
>Die in der Komponenten-Symbolleiste verfügbaren Optionen variieren je nach ausgewählter Komponente.

![Komponenten-Symbolleiste](assets/overlay.png)

Komponentensymbolleiste im numerischen Feld auf der Arbeitsfläche

### Verwenden der Seitenleiste {#using-rail}

Die Seitenleiste im Design-Editor bietet Optionen zum Anpassen von Stilen für Komponenten in einem Design und zum Verwenden von Selektoren. Mit Selektoren können Sie eine Gruppe von Komponenten oder einzelne Komponenten auswählen und in der Seitenleiste nach Selektoren suchen. Sie können Selektoren für benutzerdefinierte Komponenten schreiben.

Wenn Sie eine Komponente auf der Arbeitsfläche oder Selektoren in der Seitenleiste auswählen, werden in der Seitenleiste alle Optionen angezeigt, mit denen Sie die zugehörigen Stile anpassen können.
Im Folgenden sehen Sie die Optionen, die in der Seitenleiste angezeigt werden, wenn Sie eine Komponente auswählen:

* Status
* Eigenschaftenblatt
* Fehler/Erfolg simulieren

#### Status {#state}

Ein Status ist ein Indikator für die Benutzerinteraktion mit einer Komponente. Wenn ein Benutzer beispielsweise fehlerhafte Daten in ein Textfeld eingibt, ändert sich der Status des Textfelds in einen Fehlerstatus. Mit dem Design-Editor können Sie die spezifische Formatierung für einen bestimmten Status angeben.

Die Optionen für die Anpassung der Statusstile variieren je nach Komponente.

#### Eigenschaftenblatt {#property-sheet}

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Verwendung</strong></td>
  </tr>
  <tr>
   <td><p>Abmessungen und Position</p> </td>
   <td><p>Ermöglicht die Gestaltung von Ausrichtung, Größe, Positionierung und Platzierung von Komponenten im Design. </p> <p>Ihre Optionen sind Anzeigeeinstellung, Auffüllung, Rand, Breite, Höhe und Z-Indexposition.</p> <p>Im Layout-Modus können Sie die Breite von Komponenten auch über eine einfache Drag-and-Drop-Schnittstelle definieren. Weitere Informationen finden Sie unter <a href="../../forms/using/resize-using-layout-mode.md">Verwenden des Layout-Modus zum Ändern der Größe von Komponenten</a>.</p> </td>
  </tr>
  <tr>
   <td><p>Text</p> </td>
   <td><p>Ermöglicht die Anpassung der Textstile in der Komponente des Designs.</p> <p>Sie möchten beispielsweise das Aussehen des in das Textfeld eingegebenen Texts ändern.</p> <p>Ihre Optionen sind: Schriftfamilie, Gewichtung, Farbe, Größe, Zeilenhöhe, Textausrichtung, Zeichenabstand, Texteinzug, Unterstrichen, Kursiv, Texttransformation, vertikale Ausrichtung, Grundlinie und Richtung. </p> </td>
  </tr>
  <tr>
   <td><p>Hintergrund </p> </td>
   <td><p>Hiermit können Sie den Hintergrund der Komponente mit einem Bild oder einer Farbe füllen. </p> </td>
  </tr>
  <tr>
   <td><p>Rahmen</p> </td>
   <td><p>Hier können Sie festlegen, wie der Rahmen Ihrer Komponente aussieht. Sie möchten zum Beispiel, dass das Textfeld einen tiefroten, dicken Rand mit einer gepunkteten Linie hat. </p> <p>Ihre Optionen sind: Breite, Stil, Radius und Farbe des Rahmens.</p> </td>
  </tr>
  <tr>
   <td><p>Effekte</p> </td>
   <td><p>Hiermit können Sie bestimmte Effekte zu den Komponenten hinzufügen, zum Beispiel: Deckkraft, Übergangsmodus und Schatten. </p> </td>
  </tr>
  <tr>
   <td><p>Erweitert</p> </td>
   <td><p>Hiermit können Sie Folgendes hinzufügen:</p>
    <ul>
     <li>Eigenschaften für die Pseudo-Elemente <code>::before</code> und <code>::after</code> zum Hinzufügen von Inhalten nach oder vor dem Standardinhalt im Selektor und deren Formatierung.<br /> Siehe <a href="https://www.w3schools.com/css/css_pseudo_elements.asp" target="_blank">CSS-Pseudo-Elemente</a>.</li>
     <li>Benutzerdefinierter CSS-Code inline zu einer Komponente und schreiben benutzerdefinierte Selektoren. </li>
    </ul> <p>Wenn Sie benutzerdefinierten CSS-Code hinzufügen, überschreibt dieser die Anpassungen, die Sie mithilfe der Optionen in der Seitenleiste hinzugefügt haben. </p> </td>
  </tr>
 </tbody>
</table>

#### Fehler/Erfolg simulieren {#simulate-error-success}

Die Optionen „Fehler simulieren“ und „Erfolg simulieren“ sind am unteren Rand der Seitenleiste verfügbar. Sie können sie mithilfe eines Pfeils zum Anzeigen/Ausblenden sehen, der am Ende der Seitenleiste sichtbar ist. Mit dem Design-Editor können Sie verschiedene Status einer Komponente gestalten.

Fügen Sie beispielsweise Ihrem Formular ein numerisches Feld hinzu und legen Sie seine Formatierung im Design-Editor fest. Sobald ein Benutzer einen alphanumerischen Wert im Feld eingibt, soll sich die Hintergrundfarbe des Textfelds ändern. Wählen Sie das numerische Feld im Thema aus und verwenden Sie die Statusoption in der Seitenleiste. Wählen Sie in der Seitenleiste den Status „Fehler“ und ändern Sie die Hintergrundfarbe zu Rot. Um das Verhalten in der Vorschau anzuzeigen, können Sie die Option „Fehler simulieren“ verwenden, die in der Seitenleiste verfügbar ist. Die Optionen „Fehler simulieren“ und „Erfolg simulieren“ werden hier genauer beschrieben:

* **Erfolg simulieren**:
Hier können Sie sehen, wie eine Komponente aussieht, wenn Sie die Formatierung für den Erfolgsstatus festlegen. Beispiel: In einem Formular legen Kunden Kennwörter fest. Benutzer können Kennwörter gemäß Richtlinien festlegen, die Sie erstellen. Wenn Benutzende ein Passwort eingeben, das allen von Ihnen angegebenen Richtlinien entspricht, wird das Textfeld grün. Wenn das Textfeld grün wird, zeigt es damit den Erfolgsstatus an. Sie können die Formatierung für eine Komponente im Erfolgsstatus festlegen und das Erscheinungsbild mit der Option „Erfolg simulieren“ simulieren.

* **Fehler simulieren**:
Hier können Sie sehen, wie eine Komponente aussieht, wenn Sie die Formatierung für den Fehlerstatus festlegen. Beispiel: In einem Formular legen Kunden Kennwörter fest. Benutzer können Kennwörter gemäß Richtlinien festlegen, die Sie erstellen. Wenn Benutzende ein Passwort eingeben, das nicht allen von Ihnen angegebenen Richtlinien entspricht, wird das Textfeld rot. Wenn das Textfeld rot wird, zeigt es damit den Fehlerstatus an. Sie können die Gestaltung für eine Komponente mit Fehlerstatus festlegen und ihr Erscheinungsbild mit der Option „Fehler simulieren“ simulieren.

### Formatieren einer Komponente {#styling-a-component}

Beispiel: In Ihrem Formular gibt es zwei Arten von Textfeldern: In das eine lassen sich nur numerische und in das andere nur alphanumerische Werte eingeben. Sie können die Gestaltung für das Textfeld anpassen, das nur numerische Werte akzeptiert (ein numerisches Feld).

Führen Sie die folgenden Schritte aus, um die Formatierung für eine bestimmte Komponente anzupassen (in diesem Beispiel ein numerisches Feld):

1. Wählen Sie im Design-Editor das numerische Feld auf der Arbeitsfläche aus.
1. Wenn Sie das numerische Feld auswählen, wird die Komponenten-Symbolleiste mit drei Optionen angezeigt:

   * **Widget „Numerisches Feld“**
   * **Feld-Widget** ![Feldebene](assets/field-level.png)

1. Wählen Sie **Widget „Numerisches Feld“**.
1. Der Titel der Seitenleiste ändert sich zu „Widget ‚Numerisches Feld‘“, und sie enthält die Optionen zum Anpassen des Erscheinungsbildes.
Ändern Sie mit der Option **Abmessung und Position** in der Seitenleiste die Größe der Komponente. Stellen Sie sicher, dass der Status **Standard** lautet.

Wählen Sie in der Komponenten-Symbolleiste statt **Widget „Numerisches Feld“** die Option **Widget „Feld“** und führen Sie die oben genannten Schritte durch. Wenn Sie Abmessungen für die Option **Widget „Feld“** auswählen, haben alle Textfelder mit Ausnahme des numerischen Felds die gleiche Größe.

### Formatieren von Feldern für einen bestimmten Status {#styling-fields-given-state}

Mit der Komponenten-Symbolleiste können Sie auch die Gestaltung von Komponenten für die verschiedenen Status festlegen. Wenn eine Komponente beispielsweise deaktiviert ist, besitzt sie den Status „deaktiviert“. Die allgemein verwendeten Status einer Komponente, die Sie im Design-Editor gestalten können, sind: „Standard“, „Fokus“, „Deaktiviert“, „Fehler“ und „Mausbewegung“. Sie können eine Komponente auf der Arbeitsfläche auswählen und die Option „Status“ in der Seitenleiste verwenden, um ihr Erscheinungsbild individuell anzupassen.

Führen Sie die folgenden Schritte aus, um die Formatierung für eine Komponente mit einem bestimmten Status anzupassen:

1. Wählen Sie eine Komponente auf der Arbeitsfläche aus und wählen Sie die entsprechende Option in der Komponenten-Symbolleiste.
In der Seitenleiste werden die Optionen zum Anpassen der Formatierung für die Komponente angezeigt.
1. Wählen Sie in der Seitenleiste einen Status aus. Beispielsweise den Status „Fehler“.
1. Verwenden Sie Optionen wie **Rahmen, Hintergrund** in der Seitenleiste, um das Erscheinungsbild der Komponente anzupassen.
1. Durch Auswahl der Option **Fehler simulieren** am unteren Rand der Seitenleiste können Sie während der Bearbeitung sehen, wie die Formatierung aussieht.

Wenn Sie die Gestaltung einer Komponente anpassen, nachdem Sie ihren Status angegeben haben, wird die Anpassung für die Komponente nur für den angegebenen Status angezeigt. Angenommen, Sie passen die Formatierung für die Komponente an, wenn der Status „Mausbewegung“ festgelegt ist. Die Anpassung wird für die Komponente angezeigt, wenn Sie den Mauszeiger im wiedergegebenen Formular oder in der interaktiven Kommunikation, auf die Sie das Design anwenden, über die Komponente bewegen.

Um das Verhalten von anderen Statuszuständen als „Fehler“ und „Erfolg“ zu simulieren, verwenden Sie den Vorschaumodus. Um den Vorschaumodus zu aktivieren, klicken Sie in der Symbolleiste der Seite auf **Vorschau**.

### Formatieren von Layouts für kleinere Displays {#styling-layouts-for-smaller-displays}

Verwenden Sie das Lineal auf der Arbeitsfläche, um Haltepunkte für Geräte mit kleineren Displays auszuwählen. Klicken Sie auf der Arbeitsfläche auf „Emulator“ ![Lineal](assets/ruler.png), um Lineal und Haltepunkte anzuzeigen. Mithilfe der Haltepunkte können Sie ein Formular oder eine interaktive Kommunikation für Anzeigegrößen mehrerer Geräte, wie Smartphones und Tablets, in einer Vorschau anzeigen. Der Design-Editor unterstützt verschiedene Displaygrößen.

So formatieren Sie Komponenten für verschiedene Haltepunkte:

1. Wählen Sie auf der Arbeitsfläche einen Haltepunkt über dem Lineal aus.
Ein Haltepunkt steht für ein Mobilgerät und dessen Displaygröße.
1. Verwenden Sie die Seitenleiste, um die Formatierung von Formular- oder interaktiven Kommunikationskomponenten im Design für die ausgewählte Anzeigegröße anzupassen.
1. Stellen Sie sicher, dass die Anpassung gespeichert wird.

Sie können Formular- oder interaktive Kommunikationskomponenten für mehrere Geräte gestalten. Formular- und interaktive Kommunikationskomponenten für Desktops und Mobilgeräte können unterschiedliche Stile aufweisen.

### Verwenden von Webschriften in einem Design {#using-web-fonts-in-a-theme}

Sie können jetzt die Schriftarten, die in einem Webservice verfügbar sind, in einem adaptiven Formular oder in interaktiver Kommunikation verwenden. Standardmäßig ist [Adobe Fonts](https://fonts.adobe.com/), der Adobe-Service für Web-Schriftarten, als Konfiguration verfügbar. Um Adobe Fonts zu verwenden, erstellen Sie ein Kit, fügen Schriftarten hinzu und beziehen die Kit-ID von [Adobe Fonts](https://fonts.adobe.com/).

Führen Sie die folgenden Schritte aus, um Adobe Fonts in AEM zu konfigurieren:

1. Klicken Sie in der Autoreninstanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png)Adobe Experience Manager > Tools ![hammer](assets/hammer.png) > Bereitstellung > Cloud Services.
1. Navigieren Sie auf der Seite **Cloud Services** zur Option **Adobe Fonts** und öffnen Sie sie. Öffnen Sie den Konfigurationsordner und klicken Sie auf **Erstellen**.
1. Im **Konfiguration erstellen** Dialogfeld geben Sie einen Titel für die Konfiguration an und klicken Sie auf **Erstellen**.

   Daraufhin werden Sie zur Seite „Konfiguration“ geleitet.

1. Geben Sie im Dialogfeld „Komponente bearbeiten“, das angezeigt wird, Ihre Kit-ID ein und klicken Sie auf **OK**.

Führen Sie die folgenden Schritte aus, um ein Design so zu konfigurieren, dass es die Adobe Fonts-Konfiguration verwendet:

1. Öffnen Sie in der Author-Instanz im Design-Editor ein Design.
1. Navigieren Sie im Design-Editor zu **Themenoptionen** ![Themenoptionen](assets/theme-options.png) > **Konfigurieren**.
1. Wählen Sie im Feld **Adobe Fonts-Konfiguration** ein Kit aus und klicken Sie auf **Speichern**.

   Jetzt können Sie sehen, dass die Schriftarten in der Schriftfamilieneigenschaft des Designs hinzugefügt werden.

### Auflisten und Auswählen von Schriftarten im Design-Editor {#listing-and-selecting-fonts-in-theme-editor}

Sie können den Designkonfigurationsdienst verwenden, um dem Design-Editor weitere Schriftarten hinzuzufügen. Führen Sie die folgenden Schritte aus, um Schriftarten hinzuzufügen:

1. Melden Sie sich mit Administratorrechten bei AEM Web Console an. Die URL der AEM-Web-Konsole lautet `https://'[server]:[port]'/system/console/configMgr`.
1. Öffnen Sie den **Adaptiven Formulardesignkonfigurationsdienst**.

   ![theme-config](assets/theme-config.png)

1. Klicken Sie auf +, geben Sie den Namen der Schriftart an und klicken Sie auf **Speichern**. Die Schrift wird hinzugefügt und ist im Design-Editor verfügbar.

#### Auswahl der Schriften im Designeditor {#selecting-fonts-in-theme-editor}

Verwenden Sie die Schaltfläche „+“, um eine Schriftart hinzuzufügen. Wenn Sie eine Schriftart hinzufügen, wird sie in der Seitenleiste aufgeführt.

![Eine neue Schrift wird im Design-Editor aufgeführt](assets/theme-font.png)

Zusätzlich zur Option für die Design-Konfiguration können Sie Ihre Schriftart auch aus dem Design-Editor selbst hinzufügen. Geben Sie die Schriftart, die Sie verwenden möchten, in das Feld für die Schriftfamilie unter der Seitenleiste ein und drücken Sie die Eingabetaste auf der Tastatur.

![Eingeben und Auswahl der Schrift im Designeditor](assets/font-selection.png)

Wenn Sie eine Schriftart auswählen, wird sie unter der Schriftfamilienliste hinzugefügt. Sie können die Option „Maske“ im Design-Editor verwenden, um die aufgelisteten Schriftarten zu deaktivieren oder zu aktivieren.

![multi-fonts](assets/multi-fonts.jpg)

Sie können die Komponentenschriftänderung sehen.

Das Schriftfamilienfeld unterstützt mehrere Schriftarten. Wenn Sie eine Schriftart eingeben, sucht der Browser danach und wendet sie auf die ausgewählte Komponente an. Wenn der Browser eine Schriftart nicht finden kann, sucht er in der Familie nach einer Schriftart neben ihr. Sie können mit der Eingabe der gewünschten Schriftart beginnen. Wenn Sie die Schriftart, die Sie verwenden möchten, nicht finden, können Sie eine generische Schriftart in die Familie eingeben und sie verwenden.

#### Maskieren von Stilen, die im Designeditor angewendet wurden {#mask-styles-applied-in-theme-editor}

Sie können die Stile maskieren, die in einem Design angewendet wurden. In der Seitenleiste im Design-Editor steht das Symbol ![Maskieren ein/aus](assets/toggle_eye.png) zur Verfügung, mit dem Sie einen angewendeten Stil deaktivieren können. Wenn Sie beispielsweise die Dimensionen einer Komponente in einem Formular oder in einer interaktiven Kommunikation ändern, können Sie die Maskenschaltfläche links von einer Eigenschaft verwenden, um sie zu deaktivieren. Wenn Sie ein Design speichern, bleiben die gewählten Maskierungsoptionen erhalten.

![In der Seitenleiste des Design-Editors verfügbare Maskierungsoption](assets/mask-styles.png)

Das folgende Beispiel zeigt maskierte und nicht maskierte Stile in einem Design.

![Maskierte und nicht maskierte Stile](assets/mask2.png)

## Anwenden eines Designs auf ein Formular oder eine interaktive Kommunikation {#applying-a-theme-to-a-form-or-interactive-communication-br}

So wenden Sie ein Design auf ein adaptives Formular an:

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und klicken Sie dann auf **Öffnen**.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und klicken Sie anschließend zuerst auf ![Feld-Ebene](assets/field-level.png) > **Container für ein adaptives Formular** und dann auf ![cmppr](assets/cmppr.png).

   Sie können die Eigenschaften Ihres Formulars in der Seitenleiste bearbeiten.

1. Klicken Sie in der Seitenleiste auf **Formatierung**.
1. Wählen Sie im Dropdown-Menü **Adaptives Formulardesign** ein Design aus und klicken Sie auf **Fertig** ![Häkchen-Schaltfläche](assets/check-button.png).

So wenden Sie ein Design auf eine interaktive Kommunikation an:

1. Öffnen Sie Ihre interaktive Kommunikation im Bearbeitungsmodus. Um eine interaktive Kommunikation im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und klicken Sie auf **Öffnen**.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, klicken Sie auf ![field-level](assets/field-level.png) > **Dokumenten-Container** und dann auf ![cmppr](assets/cmppr.png).

   Sie können die Eigenschaften Ihres Formulars in der Seitenleiste bearbeiten.

1. Wählen Sie in der Seitenleiste unter **Basic** Ihr Thema aus der Dropdown-Liste **Design** aus und klicken Sie auf **Fertig** ![check-button](assets/check-button.png)

### Ändern des Designs eines Formulars zur Laufzeit {#change-theme-of-a-form-at-runtime}

Ein Design versieht verschiedene Komponenten eines Formulars mit Stilen. Mit der `themeOverride`-Eigenschaft können Sie das Design eines Formulars dynamisch ändern. Eine typische URL eines Formulars lautet:

`https://<server>:<port>/content/forms/af/test.html`

Mit dem Parameter „themeOverride“ können Sie ein Design zur Laufzeit anwenden.

`https://<server>:<port>/content/forms/af/test.html?themeOverride=/content/dam/formsanddocuments-themes/simpleEnrollmentTheme`

Mit der Option `themeOverride` können Sie einen Pfad zu einem Design angeben. Damit wird das Design des Formulars geändert und das Formular mit aktualisierten Stilen aktualisiert.

## Kreieren eines bestimmten Erscheinungsbildes mithilfe von Designs {#specific-af-appearance}

AEM Forms stellt neben dem standardmäßigen Arbeitsflächen-Design auch viele andere Designs zur Verfügung. Wenn Sie Ihr Formular oder Ihre interaktive Kommunikation mit anderen Designs zusammen mit zusätzlichen Änderungen entwerfen möchten, kopieren Sie das Design aus dem Ordner &quot;Designbibliothek&quot;. Fügen Sie die kopierten Designs aus dem Design-Bibliotheks-Ordner ein und bearbeiten Sie das kopierte Design entsprechend den gewünschten Änderungen.

Gehen Sie wie folgt vor, um ein Design zu kopieren:

1. Navigieren Sie in der Author-Instanz zu **Adobe Experience Manager > Formulare > Designs**.
1. Öffnen Sie den Ordner für die Designbibliothek.
1. Fahren Sie im Ordner für die Design-Bibliothek mit dem Mauszeiger über das entsprechende vordefinierte Design und wählen Sie **Kopieren** aus.
1. Fügen Sie das kopierte Design aus dem Design-Bibliotheks-Ordner ein.
1. Passen Sie das kopierte Design an.

Nachdem Sie das Design angepasst haben, wenden Sie es auf Ihr Formular oder Ihre interaktive Kommunikation an.

>[!NOTE]
>
>Ändern Sie nicht die Designs, die im Design-Bibliotheks-Ordner verfügbar sind. Dieser Ordner enthält System-Designs. Alle Änderungen, die Sie an diesen Designs vorgenommen haben, werden bei der Installation einer neueren Version oder eines Hotfix von AEM Forms überschrieben.

## Auswirkungen auf andere Anwendungsfälle adaptiver Formulare {#impact-on-other-adaptive-form-use-cases}

* **Formular veröffentlichen/Veröffentlichung aufheben:** Beim Veröffentlichen eines Formulars wird das angewendete Design ebenfalls veröffentlicht (wenn es nicht bereits veröffentlicht ist).
* **Formular importieren/exportieren:** Beim Importieren oder Exportieren eines Formulars wird das zugehörige Design ebenfalls automatisch importiert oder exportiert.
* **Verweise eines Formulars:** Der Abschnitt „Verweist“ in den Formularverweisen enthält einen zusätzlichen Eintrag für das Design.
* **Zeit der letzten Änderung eines Formulars:** Wird aktualisiert, wenn das zugehörige Design geändert wird.
* **A/B-Tests**: Sie können in A/B-Tests verschiedene Designs auf zwei Versionen des Formulars anwenden. Die Informationen der beiden Designs werden einzeln in den beiden Guide-Containern gespeichert.

## CSS-Generierungssequenz {#css-generation-sequence}

Wenn Sie „CSS anzeigen“ wählen, sammelt der Design-Editor alle Gestaltungs-Informationen und erstellt eine CSS-Datei. Sie erfasst Informationen in der folgenden Reihenfolge:

1. In der zugrunde liegenden Client-Bibliothek des Designs definierte Stile.
1. Benutzerdefinierter Stil, der mithilfe der Eigenschaften in der Seitenleiste angegeben wird.
1. Mithilfe der Option zur CSS-Überschreibung angegebene CSS-Stile

Beispielsweise ist die Hintergrundfarbe eines Textfelds in der Basis-Client-Bibliothek blau. Über die Eigenschaften in der Seitenleiste können Sie die Farbe in Rosa ändern. Wenn Sie die CSS-Datei generieren, sehen Sie die Hintergrundfarbe des Textfelds als Rosa. Nachdem Sie die Hintergrundfarbe mithilfe der Eigenschaften geändert haben, ändert ein anderer Autor oder eine andere Autorin die Hintergrundfarbe des Textfelds mithilfe der CSS-Überschreibungsoption in Weiß. Beim Generieren des CSS wird Weiß als Hintergrundfarbe festgelegt.

## Debugging von Stilen {#debugging-styles}

Wenn Sie im Design-Editor Stile für Komponenten angeben, wird wie oben beschrieben ein CSS generiert. Wenn Sie eine generische Komponente gestalten, werden auch mehrere darin enthaltene Komponenten gestaltet. Wenn Sie beispielsweise ein Feld formatieren, werden das Textfeld und die Beschriftung darin ebenfalls formatiert. Wenn Sie das Textfeld innerhalb des Felds formatieren, wird eigens für dieses Textfeld CSS generiert. Damit Sie das für das Feld und die Komponente erstellte CSS debuggen können, bietet Design-Editor Optionen, mit denen Sie CSS anzeigen können.

Zum Anzeigen der generierten CSS-Datei stehen die folgenden Optionen zur Verfügung:

* Option **CSS anzeigen** in der Seitenleiste: Wenn Sie eine Komponente im Design auswählen, wird die Option „CSS anzeigen“ in der Seitenleiste angezeigt. Sie ermöglicht die Anzeige des generierten CSS, einschließlich CSS für die Pseudo-Elemente `::before` und `::after`.
* Option **Design-CSS anzeigen** in der Symbolleiste der Arbeitsfläche: Klicken Sie in der Symbolleiste der Arbeitsfläche auf ![Themenoptionen](assets/theme-options.png) > **Design-CSS anzeigen**. Daraufhin wird das gesamte Design-CSS angezeigt, das anhand der von Ihnen im Design-Editor definierten Eigenschaften generiert wurde.

## Fehlerbehebung, Empfehlungen und optimale Verfahren {#troubleshooting-recommendations-and-best-practices}

* **Vermeiden von Assets aus einem anderen Design**

  Bei der Bearbeitung von Designs können Sie Assets (etwa Bilder) aus anderen Designs durchsuchen und hinzufügen. Angenommen, Sie bearbeiten den Hintergrund einer Seite. Wenn Sie beispielsweise **Seite** ![Bearbeiten-Schaltfläche](assets/edit-button.png) > **Hintergrund** > **Hinzufügen** > **Bild** auswählen, wird ein Dialogfeld angezeigt, in dem Sie Bilder aus anderen Designs suchen und hinzufügen können.

* Es können Probleme im aktuellen Design auftreten, wenn ein Asset aus einem anderen Design hinzugefügt und dieses andere Design später verschoben oder gelöscht wird. Wir empfehlen daher, keine Assets aus anderen Designs zu suchen und hinzuzufügen.
* **Verwenden der Basis-Clientlib, des Design-Editors und der Inline-Formatierung**

   * **Basis-Clientlib**:

     Die Basis-Client-Bibliothek enthält Formatierungsinformationen. Um die Informationen zur Formatierung in Client-seitigen Bibliotheken in Designs zu verwenden.

      1. Navigieren Sie zu **Experience Manager > Formulare > Designs**.
      1. Wählen Sie in der Themenseite ein Thema aus und klicken Sie auf **Eigenschaften anzeigen**.
      1. Klicken Sie auf der sich öffnenden Eigenschaftsseite auf **Erweitert**.
      1. Suchen Sie auf der Registerkarte Erweitert im Feld Clientlib-Speicherort die Client-Bibliothek, die Sie verwenden möchten, und wählen Sie sie aus.
      1. Klicken Sie auf **Speichern**.

     Der Stil, den Sie in der Client-Bibliothek angeben, wird in das Design importiert, das ihn verwendet. Beispielsweise geben Sie die Formatierung für das Textfeld, das numerische Feld und den Wechsel in die Client-Bibliothek an. Wenn Sie Ihre Client-Bibliothek in das Design importieren, wird die Formatierung für das Textfeld, das numerische Feld und den Schalter importiert. Sie können dann andere Komponenten mithilfe des Design-Editors formatieren.
Sie können auch ein Design erstellen, Kopien davon anfertigen und dann die in den kopierten Designs enthaltenen Stile für ähnliche Anwendungsfälle abändern.
Siehe [Kreieren eines bestimmten Looks mithilfe von Designs](#specific-af-appearance)

   * **Themen-Editor:**

     Mit dem Design-Editor können Sie Designs erstellen, um ein Formular oder eine interaktive Kommunikation zu gestalten. Sie können auch die Gestaltung von Komponenten in einem Design festlegen, die die Konsistenz von Looks in mehreren Formularen oder interaktiven Kommunikationen, die Sie gestalten, gewährleisten. Es wird empfohlen, Formatierungsinformationen in einem Design anzugeben und dann das Design auf ein Formular anzuwenden.

   * **Inline-Stil**:

     Sie können Komponenten mithilfe des Formatierungsmodus im Multikanal-Editor für das Formular oder die interaktive Kommunikation gestalten, wenn Sie mit einem Formular arbeiten. Wenn der Formatierungsmodus verwendet wird, um die Formularkomponentenformatierung zu ändern, wird die Formatierung, die im Design angegeben ist, überschrieben. Wenn Sie die Formatierung für bestimmte Komponenten eines bestimmten Formulars ändern möchten, lesen Sie [Inline-Formatierung von Komponenten](../../forms/using/inline-style-adaptive-forms.md).

* **Verwenden Client-seitiger Bibliotheken**

  Wenn Sie Client-Bibliotheken erstellen möchten, um Formatierungsinformationen zu importieren, finden Sie weitere Informationen unter [Verwenden von Client-seitigen Bibliotheken](/help/sites-developing/clientlibs.md). Nachdem Sie eine Client-Bibliothek erstellt haben, können Sie sie in das Design mithilfe der oben genannten Schritte importieren.

* **Ändern der Layout-Breite des Container-Bereichs**

  Es wird nicht empfohlen, die Layout-Breite des Container-Bereichs zu ändern. Wenn Sie die Breite eines Container-Bereichs angeben, wird er statisch und passt sich nicht mehr an unterschiedliche Displays an.

* **Verwendung des Formular- oder Design-Editors für die Arbeit mit Kopf- und Fußzeile**

  Verwenden Sie den Design-Editor, wenn Sie Kopf- und Fußzeilen mit Formatierungsoptionen wie Schriftschnitt, Hintergrund und Transparenz formatieren möchten.
Wenn Sie Informationen wie ein Logo, einen Firmennamen in der Kopfzeile und Copyright-Informationen in der Fußzeile angeben möchten, verwenden Sie dazu die im Formular-Editor verfügbaren Optionen.
