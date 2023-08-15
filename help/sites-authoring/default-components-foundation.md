---
title: Foundation-Komponenten
seo-title: Foundation Components
description: Foundation-Komponenten
seo-description: null
uuid: 3caf9123-ae58-4590-af2f-57ef076daf7f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: ea2a523e-8d26-4be4-822f-35f153e40308
docset: aem65
legacypath: /content/docs/en/aem/6-2/author/page-authoring/default-components/editmode
pagetitle: Foundation Components
exl-id: 278701f3-3f0c-45f4-90b7-c0e316a7da8a
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '7198'
ht-degree: 97%

---

# Foundation-Komponenten {#foundation-components}

>[!CAUTION]
>
>Die meisten Foundation-Komponenten sind in AEM 6.5 veraltet. Weitere Informationen finden Sie in den [Versionshinweisen](/help/release-notes/deprecated-removed-features.md).
>
>Adobe empfiehlt, in AEM-Projekten die moderneren und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden. Diese sind Teil des [Inhalts des Beispielprojekts We.Retail](/help/sites-developing/we-retail.md) und können von Ihren Admins [separat installiert und zu Entwicklungszwecken verwendet werden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/using.html?lang=de).
>
>Sie können die [AEM-Modernisierungs-Tool-Suite](https://opensource.adobe.com/aem-modernize-tools/) verwenden, um Ihre auf Foundation-Komponenten basierende Website für die Verwendung von Kernkomponenten umzugestalten.

Die Foundation-Komponenten wurden für die Verwendung beim Bearbeiten von Inhalten für eine Standardwebseite entworfen. Sie bilden eine Teilmenge der Komponenten, die vorkonfiguriert für eine Standardinstallation von AEM verfügbar sind.

Einige sind direkt im Komponenten-Browser verfügbar, viele andere stehen außerdem im [Design-Modus](/help/sites-authoring/default-components-designmode.md) (wenn die Seite auf einer statischen Vorlage basiert) bzw. beim [Bearbeiten der Vorlage](/help/sites-authoring/templates.md) (wenn die Seite auf einer bearbeitbaren Vorlage basiert) zur Verfügung.

Die Verwendung von Foundation-Komponenten wird unterstützt, sie wurden jedoch größtenteils eingestellt und durch Kernkomponenten ersetzt, die eine größere Erweiterbarkeit und Flexibilität bieten.

>[!NOTE]
>
>In diesem Abschnitt werden nur Komponenten behandelt, die vorkonfiguriert in einer AEM-Standardinstallation verfügbar sind.
>
>Je nach Ihrer Instanz verfügen Sie möglicherweise über benutzerdefinierte Komponenten, die explizit für Ihre Anforderungen entwickelt wurden. Diese benutzerdefinierten Komponenten haben möglicherweise sogar denselben Namen wie einige der hier behandelten Komponenten.

Die Komponenten sind im Seiteneditor auf dem seitlichen Bedienfeld der Registerkarte **Komponenten** verfügbar, wenn Sie eine [Seite bearbeiten](/help/sites-authoring/editing-content.md).

Sie können eine Komponente auswählen und an die gewünschte Stelle auf Ihrer Seite ziehen. Sie können sie dann bearbeiten, indem Sie Folgendes verwenden:

* [Eigenschaften konfigurieren](/help/sites-authoring/editing-page-properties.md)
* [Inhalt bearbeiten](/help/sites-authoring/editing-content.md)

* [Inhalt bearbeiten – Vollbildmodus](/help/sites-authoring/editing-content.md#edit-content-full-screen-mode)

Die Komponenten sind nach verschiedenen Kategorien (Komponentengruppen) sortiert. Diese umfassen:

* [Allgemein](#general): Enthält grundlegende Komponenten wie Text, Bilder, Tabellen und Diagramme.
* [Spalten](#columns): Enthält Komponenten, die für die Organisation des Inhalts-Layouts benötigt werden.
* [Formular](#formgroup): Enthält alle für das Erstellen eines Formulars benötigten Komponenten.

## Allgemein {#general}

Die allgemeinen Komponenten sind die grundlegenden Komponenten, die Sie zum Erstellen von Inhalten verwenden.

### Kontoelement {#account-item}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Sie können einen Link mit Titel und Beschreibung definieren.

![chlimage_1-88](assets/chlimage_1-88.png)

### Adaptives Bild {#adaptive-image}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Bild“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=de) zu verwenden.

Die Komponente der Adaptive Image Foundation erzeugt Bilder, die in das Fenster eingepasst werden, in dem die Webseite geöffnet wird. Um die Komponente zu verwenden, geben Sie eine Bildressource entweder im Dateisystem oder im DAM an. Wenn die Web-Seite geöffnet wird, lädt der Webbrowser eine Kopie des Bildes herunter, die so in der Größe angepasst wurde, dass sie in das aktuelle Fenster passt.

Die Größe des Fensters kann von den folgenden Eigenschaften abhängen:

* Geräte-Display: Auf Mobilgeräten werden Web-Seiten im Allgemeinen so angezeigt, dass das komplette Display ausgefüllt ist.
* Fenstergröße des Webbrowsers: Benutzerinnen und Benutzer von Laptop- und Desktop-Computern können die Größe von Webbrowser-Fenstern ändern.

Die Komponente erzeugt zum Beispiel ein kleines Bild, wenn die Webseite auf einem Mobiltelefon geöffnet wird, und ein mittelgroßes Bild, wenn sie auf einem Tablet geöffnet wird. Auf einem Laptop erzeugt die Komponente ein großes Bild, wenn die Seite in einem maximierten Webbrowser geöffnet wird. Wenn der Webbrowser so angepasst wird, dass er nur noch einen Teil des Bildschirms ausfüllt, passt die Komponente das Bild in der Größe an und aktualisiert die Ansicht.

#### Unterstützte Bildformate {#supported-image-formats}

Mit der Adaptive Image-Komponente können Sie Bilddateien mit den folgenden Dateinamenerweiterungen verwenden:

* .jpg
* .jpeg
* .png
* .gif &#42;&#42;

>[!CAUTION]
>
>Animierte GIF-Dateien werden in AEM für adaptive Ausgabedarstellungen nicht unterstützt.

#### Bildgrößen und -qualität {#images-sizes-and-quality}

In der folgenden Tabelle wird die Breite des Bildes aufgeführt, die für die jeweilige Anzeigebreite erzeugt wird. Die Höhe des erzeugten Bildes wird so berechnet, dass ein konstantes Seitenverhältnis erhalten bleibt und innerhalb des Bildrandes keine weißen Bereiche auftreten. Das Zuschneiden kann verwendet werden, um leere Bereiche zu vermeiden.

Wenn es sich bei dem Bild um ein JPEG-Bild handelt, kann die Anzeigegröße sich auch auf die JPEG-Qualität auswirken. Die folgenden JPEG-Qualitäten sind möglich:

* Niedrig (0,42)
* Mittel (0,82)
* Hoch (1,00)

| **Breitenbereich des Darstellungsfelds (Pixel)** | **Bildbreite (Pixel)** | **JPEG-Qualität** | **Zielgerätetyp** |
|---|---|---|---|
| Breite &lt;= 319 | 320 | niedrig |  |
| Breite = 320 | 320 | mittel | Mobiltelefon (Hochformat) |
| 320 &lt; Breite &lt; 481 | 480 | mittel | Mobiltelefon (Querformat) |
| 480 &lt; Breite &lt; 769 | 476 | hoch | Tablet (Hochformat) |
| 768 &lt; Breite &lt; 1025 | 620 | hoch | Tablet (Querformat) |
| Breite &lt;= 1025 | Vollbild (Originalgröße) | hoch | Desktop |

#### Eigenschaften {#properties}

Über das Dialogfeld können Sie Eigenschaften für Ihre Instanz der Komponente Adaptives Bild bearbeiten, von denen viele mit der Bildkomponente übereinstimmen, auf der sie basiert. Die Eigenschaften sind auf zwei Registerkarten verfügbar:

* **Bild**

   * **Bild**
Ziehen Sie ein Bild aus dem Content Finder oder klicken Sie, um ein Browserfenster zu öffnen, in dem Sie ein Bild laden können. Nachdem das Bild geladen wurde, können Sie es beschneiden, drehen oder löschen. Verwenden Sie den Regler unter dem Bild (und über den Schaltflächen „OK“ und „Abbrechen“), um das Bild ein- und auszuzoomen.

   * **Zuschneiden**
Beschneiden des Teils eines Bildes. Ziehen Sie den Rahmen, um das Bild zuzuschneiden.

   * **Drehen**
Klicken Sie mehrfach auf „Drehen“, bis das Bild in die gewünschte Ausrichtung gedreht ist.

   * **Entfernen**
Damit entfernen Sie das aktuelle Bild.

* **Erweitert**

   * **Titel**
Die Adaptive Image-Komponente nutzt diese Eigenschaft nicht.

   * **Alt-Text**
Der alternative Text für das Bild.

   * **Verknüpfung zu**
Die Adaptive Image-Komponente nutzt diese Eigenschaft nicht.

   * **Beschreibung**
Die Adaptive Image-Komponente nutzt diese Eigenschaft nicht.

#### Vergrößern der Adaptive Image-Komponente {#extending-the-adaptive-image-component}

Informationen zum Anpassen der Adaptive Image-Komponente finden Sie unter [Grundlegendes zur Adaptive Image-Komponente](/help/sites-developing/responsive.md#using-adaptive-images).

### Karussell {#carousel}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Karussell“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html?lang=de) zu verwenden.

Mit der Karussellkomponente können Sie Bilder anzeigen, die einzelnen Seiten zugeordnet sind:

* jeweils eines
* für eine kurze Zeit
* in einer von Ihnen festgelegten Reihenfolge
* mit einer von Ihnen festgelegten Zeitverzögerung

Durch klickbare Steuerelemente können Benutzerinnen und Benutzer bei Bedarf auch in Echtzeit durch die angezeigten Seiten navigieren. Wenn das derzeit sichtbare Seitenbild ausgewählt wird, gelangt man zu dieser Seite. Das heißt, das Karussell dient als Navigationssteuerung.

#### Eigenschaften {#properties-1}

Diese Eigenschaften sind auf zwei Registerkarten verfügbar:

* **Karussell**
Hier geben Sie an wie das Karussell arbeitet:

   * Abspielgeschwindigkeit
Die Zeit in Millisekunden bis zur Anzeige des nächsten Dias.
   * Übergangszeit
Die Zeit in Millisekunden für den Übergang zwischen zwei Folien.
   * Steuerelemente-Stil
Über ein Pulldown-Menü sind verschiedene Optionen verfügbar: z. B. Zurück-/Weiter-Schaltflächen, Schalter oben rechts.

* **Liste**

  Hier legen Sie fest, wie Seiten in Ihr Karussell aufgenommen werden:

   * **Erstellen einer Liste mittels**
Es gibt verschiedene Möglichkeiten, eine Seitenliste zu erstellen: untergeordnete Seiten, feste Liste, Suche oder erweiterte Suche (alle unten beschrieben).
Unabhängig von der gewählten Methode sollte jeder Seite, die Sie in Ihre Liste aufnehmen, bereits ein Bild zugeordnet sein. Dieses Bild wird im Karussell angezeigt. Wenn unter den Seiteneigenschaften dieser Seite kein Bild für eine bestimmte Seite vorhanden ist, sollten Sie ein Bild mit der Seite verknüpfen, bevor Sie beginnen. Andernfalls wird im Karussell eine größtenteils leere Seite angezeigt. Weitere Informationen finden Sie unter [Bearbeiten der Seiteneigenschaften](/help/sites-authoring/editing-page-properties.md).
Je nach ausgewähltem Element wird ein neues Panel angezeigt:

      * **Optionen für untergeordnete Seiten**

         * **Übergeordnete Seite**
Geben Sie den Pfad entweder manuell oder mithilfe der Auswahl an. Wenn Sie nichts angeben, wird die aktuelle Seite als übergeordnete Seite verwendet.

      * **Optionen für Liste fester Werte**

         * **Seiten**
Wählen Sie eine Liste mit Seiten aus. Fügen Sie mit `+` weitere Einträge hinzu und passen Sie mit den Schaltflächen nach oben und unten die Reihenfolge an.

      * **Optionen für die Suche**

         * **Starten in**
Geben Sie manuell oder über die Auswahl einen Startpfad ein.

         * **Suchabfrage**
Sie können eine Textsuchabfrage eingeben.

      * **Optionen für die erweiterte Suche**

         * **Querybuilder-Eigenschafts-Notation**
Geben Sie mit der Querybuilder-Eigenschafts-Notation eine Suchabfrage ein. Sie können beispielsweise „fulltext=Marketing“ eingeben, um alle Seiten, deren Inhalt das Wort „Marketing“ enthält, in Ihrem Karussell anzuzeigen.
Unter [QueryBuilder API](/help/sites-developing/querybuilder-api.md) finden Sie eine umfassende Übersicht über Abfrageausdrücke sowie weitere Beispiele.

   * **Sortierreihenfolge**
Wählen Sie `jcr:title`, `jcr:created`, `cq:lastModified` oder `cq:template` aus dem Dropdown-Menü aus.

   * **Limit**
Optional. Die maximale Anzahl von Elementen, die Sie im Karussell verwenden möchten.

>[!NOTE]
>
>Sie können eine benutzerdefinierte Karussellkomponente für Adobe Experience Manager erstellen, in der die im AEM DAM vorhandenen digitalen Assets angezeigt werden. Siehe [Erstellen benutzerdefinierter Karussellkomponenten für Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de).

### Diagramm {#chart}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Mit der Komponente „Diagramm“ können Sie ein Balken-, Linien- oder Tortendiagramm hinzufügen. AEM erstellt aus den von Ihnen bereitgestellten Daten ein Diagramm. Sie können Daten direkt in die Registerkarte „Daten“ eingeben oder eine Tabelle kopieren und einfügen.

* **Daten**

   * **Diagrammdaten**
Geben Sie die Diagrammdaten im CSV-Format ein; das CSV-Format (kommagetrennte Werte) verwendet ein Komma (,) als Feldtrennzeichen.

* **Erweitert**

   * **Diagrammtyp**
Wählen Sie ein Torten-, Linien- oder Balkendiagramm aus.

   * **Alternativtext**
Zeigt alternativen Text anstelle des Diagramms an.

   * **Breite**
Die Breite des Diagramms in Pixeln.

   * **Höhe**
Die Höhe des Diagramms in Pixeln.

Im Folgenden sehen Sie ein Beispiel für Diagrammdaten und das daraus resultierende Balkendiagramm:

![chlimage_1-89](assets/chlimage_1-89.png) ![dc_chart_use](assets/dc_chart_use.png)

>[!NOTE]
>
>Sie können eine benutzerdefinierte Diagrammsteuerung für AEM erstellen, in der Daten aus dem AEM JCR angezeigt werden. Weitere Informationen finden Sie unter [Anzeigen von Adobe Experience Manager-Daten in einem Diagramm](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=de).

### Inhaltsfragment {#content-fragment}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Inhaltsfragement“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) zu verwenden.

[Inhaltsfragmente](/help/sites-authoring/content-fragments.md) werden als seitenunabhängige Assets erstellt und verwaltet. Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden.

### Design-Import-Tool {#design-importer}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Mit dieser Komponente können Sie eine ZIP-Datei mit einem Design-Paket hochladen.

### Herunterladen {#download}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Über die Download-Komponente wird auf der ausgewählten Webseite ein Link erstellt, über den eine spezifische Datei heruntergeladen werden kann. Sie können ein Asset entweder aus dem Content Finder ziehen oder eine Datei hochladen.

* **Download**

   * **Beschreibung**
Eine kurze Beschreibung, die mit dem Download-Link angezeigt wird.

   * **Datei**
Die Datei, die auf der resultierenden Web-Seite heruntergeladen werden kann. Ziehen Sie ein Asset aus dem Content Finder oder wählen Sie den Bereich aus, damit Sie die Datei hochladen können, die Sie für den Downlowd verfügbar machen wollen.

Das folgende Beispiel zeigt die Download-Komponente in Geometrixx:

![dc_download_use](assets/dc_download_use.png)

### Extern {#external}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Die Komponente **Extern** ermöglicht es Ihnen, anhand von iframes externe Anwendungen in Ihre AEM-Seite einzubetten.

* **Extern**

   * **Zielanwendung**
Geben Sie die URL der zu integrierenden Web-Anwendung an, z. B.:

     ```
     https://en.wikipedia.org/wiki/Main_Page
     ```

   * **Parameter weiterleiten**
Aktivieren Sie das Kontrollkästchen für das Weiterleiten von Parametern an die Anwendung.

   * **Breite und Höhe**
Definieren der Größe des iframe

Die externe Anwendung wird in das Absatzsystem der AEM-Seite integriert. Beispiel: Wenn Sie als Zielanwendung `https://en.wikipedia.org/wiki/Main_Page` verwenden:

![chlimage_1-90](assets/chlimage_1-90.png)

>[!NOTE]
>
>Je nach Anwendungsfall stehen weitere Optionen zur Integration externer Anwendungen zur Verfügung, zum Beispiel die [Integration von Portlets](/help/sites-administering/aem-as-portal.md).

### Flash {#flash}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten zu verwenden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

Mithilfe der Flash-Komponente können Sie einen Flash-Film laden. Sie können ein Flash-Asset aus dem Content Finder auf die Komponente ziehen oder das Dialogfeld verwenden:

* **Flash**

   * **Flash-Movie**

     Die Flash-Film-Datei. Ziehen Sie ein Asset aus dem Content Finder oder klicken Sie, um ein Suchfenster zu öffnen.

   * **Größe**

     Die Abmessungen des Anzeigebereichs für den Film in Pixel.

* **Alternativbild**

  Ein alternatives Bild, das angezeigt werden soll.

* **Erweitert**

   * **Kontextmenü**

     Gibt an, ob das Kontextmenü ein- oder ausgeblendet werden soll.

   * **Fenstermodus**

     Darstellung des Fensters, z B. deckend, transparent oder als klares (einfarbiges) Fenster.

   * **Hintergrundfarbe**

     Eine aus dem Farbdiagramm ausgewählte Hintergrundfarbe.

   * **Minimum-Version**

     Die zum Abspielen des Films erforderliche Mindestversion von Adobe Flash Player. Der Standardwert lautet 9.0.0.

   * **Attribute**

     Alle weiteren erforderlichen Attribute.

### Bild {#image}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Bild“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=de) zu verwenden.

Die Komponente „Bild“ zeigt ein Bild und begleitenden Text gemäß den festgelegten Parametern an.

Sie können ein Bild hochladen und dieses anschließend bearbeiten und anpassen (beispielsweise zuschneiden, drehen oder Links/Titel/Text hinzufügen).

Sie können ein Bild entweder aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assets-browser) direkt auf die Komponente oder deren [Dialogfeld „Konfigurieren“](/help/sites-authoring/editing-content.md#component-edit-dialog) ziehen. Sie können ein Bild auch aus dem Dialogfeld „Konfigurieren“ hochladen. Dieses Dialogfeld steuert auch alle Definitionen und Bearbeitungen des Bildes:

![chlimage_1-91](assets/chlimage_1-91.png)

Nachdem das Bild hochgeladen wurde (und nicht vorher), können Sie es mittels [Direktbearbeitung](/help/sites-authoring/editing-content.md#edit-content) wie erforderlich zuschneiden und drehen:

![Symbolleiste für die Kontext-Bearbeitung](do-not-localize/chlimage_1-15.png)

>[!NOTE]
>
>Der integrierte Editor zeigt bei der Bearbeitung die Originalgröße und das Seitenverhältnis des Bildes an. Sie können auch die Höhe und die Breite festlegen. Alle in den Eigenschaften definierten Beschränkungen der Größe und des Seitenverhältnisses werden angewendet, sobald Sie Ihre Änderungen speichern.
>
>Je nach Ihrer Instanz können Mindest- und Höchstbeschränkungen auch durch das [Design der Seite](/help/sites-developing/designer.md) vorgegeben sein. Diese Einschränkungen werden während der Projektimplementierung entwickelt.

Im Vollbildbearbeitungsmodus stehen verschiedene zusätzliche Optionen zur Verfügung, beispielsweise Karte und Zoom:

![Vollbildbearbeitungsmodus – Karte und Zoom](do-not-localize/chlimage_1-16.png)

>[!NOTE]
>
>Der Upload-Fortschritt kann in Internet Explorer nicht verfolgt werden.
>
>Benutzerinnen und Benutzer von Internet Explorer müssen das Bild hochladen, auf **OK** klicken und anschließend das Bild erneut öffnen, um die hochgeladene Datei in der Vorschau zu sehen und Änderungen (z. B. Zuschneiden) vornehmen zu können.
>
>Weitere Informationen zu den von AEM verwendeten HTML5-Features finden Sie im Abschnitt [Zertifizierte Plattformen](/help/release-notes/release-notes.md#certifiedplatforms).

Wenn ein Bild geladen wird, können folgende Konfigurationen durchgeführt werden:

* **Zuweisen**

  Wählen Sie „Zuweisen“ aus, um ein Bild zuzuweisen. Sie legen fest, wie die Imagemap (Rechteck, Polygon usw.) erstellt werden soll, und geben an, worauf der Bereich verweisen soll.

* **Zuschneiden**

  Um einen Teil eines Bildes auszuschneiden, wählen Sie „Zuschneiden“ aus. Verwenden Sie die Maus, um das Bild zuzuschneiden.

* **Drehen**

  Wählen Sie „Drehen“ aus, um ein Bild zu drehen. Wiederholen Sie das Drehen so lange, bis das Bild die gewünschte Ausrichtung hat.

* **Entfernen**

  Damit entfernen Sie das aktuelle Bild.

* **Titel**

  Der Titel des Bildes.

* **Alt-Text**

  Ein alternativer Text, der beim Erstellen barrierefreier Inhalte verwendet wird.

* **Verknüpfung zu**

  Erstellt einen Link zu Assets oder anderen Seiten innerhalb Ihrer Website.

* **Beschreibung**

  Eine Beschreibung des Bildes.

* **Größe**

  Legt die Höhe und Breite des Bildes fest.

>[!NOTE]
>
>Einige Optionen sind nur im Vollbild-Bearbeitungsmodus verfügbar.

Das endgültige Bild (mit **Titel** und **Beschreibung**) sieht beispielsweise wie folgt aus:

![chlimage_1-92](assets/chlimage_1-92.png)

### Layout-Container {#layout-container}

Diese Komponente liefert ein Rasterabsatzsystem, mit dem Sie Komponenten in einem [responsiven Raster hinzufügen und positionieren können](/help/sites-authoring/responsive-layout.md). Sie können verschiedene Inhalts-Layouts definieren, die auf der Breite von Zielgeräten basieren, einschließlich einer Reihe von Smartphones, Tablets und Desktop-Geräten.

![chlimage_1-93](assets/chlimage_1-93.png)

>[!NOTE]
>
>Diese Komponente ist mit [HTML Template Language (HTL)](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de) implementiert.

### Liste {#list}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [ Kernkomponente „Liste“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html?lang=de) zu verwenden.

Mit der Komponente Liste können Sie Suchkriterien für die Anzeige einer Liste konfigurieren:

* **Liste**

   * **Liste erstellen mittels**

     Hier legen Sie fest, woher die Liste den Inhalt abruft. Es gibt verschiedene Methoden:

   * Je nach ausgewähltem Element wird ein neues Panel angezeigt:

      * **Optionen für untergeordnete Seiten**

         * **Untergeordnete Seite von** (Übergeordnete Seite)

           Geben Sie den Pfad entweder manuell oder mithilfe der Auswahl an. Wenn Sie nichts angeben, wird die aktuelle Seite als übergeordnete Seite verwendet.

      * **Optionen für Liste fester Werte**

         * **Seiten**

           Wählen Sie eine Liste mit Seiten aus. Fügen Sie mit + weitere Einträge hinzu und passen Sie mit den Schaltflächen nach oben und unten die Reihenfolge an.

      * **Optionen für die Suche**

         * Starten in

           Geben Sie einen Startpfad ein – manuell oder über die Auswahl.

         * Suchabfrage

           Sie können eine Klartext-Suchabfrage eingeben.

      * **Optionen für die erweiterte Suche**

         * **Querybuilder-Eigenschafts-Notation**

           Geben Sie mit der QueryBuilder-Eigenschaftsnotation eine Suchanfrage ein. Sie können beispielsweise „fulltext=Marketing“ eingeben, um alle Seiten, deren Inhalt das Wort „Marketing“ enthält, in Ihrem Karussell anzuzeigen.

           Unter [„QueryBuilder API“](/help/sites-developing/querybuilder-api.md) finden Sie eine umfassende Übersicht über Abfrageausdrücke sowie weitere Beispiele.

      * **Tags**

        Legen Sie die **übergeordnete Seite**, **Tags/Schlüsselwörter** sowie Ihre erforderlichen Übereinstimmungskriterien fest.

   * **Anzeigen als**

     Angabe, wie die Elemente aufgeführt werden sollen; umfasst Links, Teaser und Nachrichten.

   * **Sortieren nach**

     Gibt an, ob die Liste sortiert und nach welchen Kriterien sie sortiert sein soll. Sie können Kriterien eingeben oder aus der Dropdown-Liste auswählen.

   * **Beschränkung**

     Legen Sie die maximale Anzahl an Elementen fest, die in der Liste angezeigt werden sollen.

   * **Feed aktivieren**

     Gibt an, ob für die Liste ein RSS-Feed aktiviert werden soll.

   * **Paginieren nach**

     Hier können Sie die Anzahl der Listenelemente festlegen, die gleichzeitig angezeigt werden sollen. Bei einer Liste mit mehr Elementen als festgelegt wird ein Seitenumbruch durchgeführt, um die Liste in mehrere Gruppen aufzuteilen.

Das folgende Beispiel zeigt, wie eine **Listen-Komponente** eine Liste von untergeordneten Seiten anzeigen würde, wobei das Layout durch die benutzerdefinierten CSS-Definitionen eines Site-Designs gesteuert wird.

![dc_list_use](assets/dc_list_use.png)

### Anmeldung {#login}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten zu verwenden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

Stellt die Felder für den Benutzernamen und das Passwort bereit.

![chlimage_1-94](assets/chlimage_1-94.png)

Sie können Folgendes konfigurieren:

* Anmelden

   * Bereichsbeschriftung

     Einleitender Text für die Eingabefelder.

   * Benutzername-Beschriftung

     Text zur Beschriftung des Benutzernamenfelds.

   * Kennwortaufschrift

     Text zur Beschriftung des Kennwortfelds.

   * Beschriftung für Anmelde-Schaltfläche

     Text für die Anmelde-Schaltfläche.

   * Umleiten zu

     Sie können die Seite Ihrer Website angeben, die geöffnet wird, nachdem sich der Benutzer angemeldet hat.

* Bereits angemeldet

   * Schaltflächenbeschriftung fortsetzen

     Text, der angibt, dass die Benutzerin bzw. der Benutzer bereits angemeldet ist.

### Auftragsstatus {#order-status}

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente ohne umfassende Anpassungen auf Projektebene vorkonfiguriert funktioniert.

* **Titel**

   * **Titel**

     Geben Sie den Titeltext an, der angezeigt werden soll.

   * **Verknüpfung**

     
Geben Sie die Seite (das Produkt) an, für das der Auftragsstatus angezeigt werden soll.

   * **Typ/Größe**

     Wählen Sie aus der bereitgestellten Auswahl aus.

![chlimage_1-95](assets/chlimage_1-95.png)

### Verweis {#reference}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Inhaltsfragment“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=de) zu verwenden.

Mit der Komponente **Verweis** können Sie auf Text in einem anderen Teil einer AEM-basierten Website (innerhalb der aktuellen Instanz) verweisen. Der Inhalt des referenzierten Absatzes wird dann so angezeigt, als befände er sich auf der aktuellen Seite. Der Inhalt wird aktualisiert, wenn sich der Quellabsatz ändert (möglicherweise muss die Seite aktualisiert werden).

* **Absatzverweis**

   * **Verweis**

     Geben Sie den Pfad zu der Seite und den Absatz an, auf die bzw. den Sie verweisen möchten (einschließlich Inhalt).

Um den Pfad zu einem Absatz anzugeben, muss das folgende Suffix an den Pfad (zur Seite) angehängt werden:

`.../jcr:content/par/<paragraph-ID>`

Beispiel:

`/content/geometrixx-outdoors/en/equipment/biking/cajamara/jcr:content/par/similar-products`

Der Pfad kann auf einen bestimmten Absatz verweisen, aber er kann auch geändert werden, um ein ganzes PAR-System anzugeben. Sie können diesen Verweis vornehmen, indem Sie den Pfad mit folgendem Suffix versehen:

`/jcr:content/par`

Beispiel:

`/content/geometrixx-outdoors/en/equipment/biking/cajamara/jcr:content/par`

Nach der Konfiguration wird der Inhalt genau wie auf der Quellseite angezeigt. Dass es sich um einen Verweis handelt, sehen Sie erst, wenn Sie die Komponente zur Bearbeitung öffnen:

![chlimage_1-96](assets/chlimage_1-96.png)

### Suchen {#searching}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Schnellsuche“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/quick-search.html?lang=de) zu verwenden.

Die Komponente „Suche“ stellt für Ihre Seite eine Suchfunktion zur Verfügung.

Sie können Folgendes konfigurieren:

* Suchen

   * **Knotentypen**

     Wenn die Suche für den bestimmten Knotentyp zu restriktiv ist, führen Sie sie hier auf, beispielsweise `cq:Page`.

   * **Suchpfad**

     Geben Sie die Stammseite der Verzweigung an, die Sie suchen möchten.

   * **Text auf Such-Schaltfläche**

     Der auf der Suchschaltfläche tatsächlich angezeigte Name.

   * **Text für Statistiken**

     Der über den Suchergebnissen angezeigte Text.

   * **Text für Keine Ergebnisse**

     Wenn keine Ergebnisse vorliegen, wird der hier eingegebene Text angezeigt.

   * **Text für Rechtschreibprüfung**

     Wenn jemand einen ähnlichen Begriff eingibt, wird dieser Text vor dem Begriff angezeigt.
Wenn Sie zum Beispiel `Geometrixxe` eingeben, zeigt das System „Meinten Sie? Geometrixx“.

   * **Text für Ähnliche Seiten**

     Der Text, der für ähnliche Seiten neben dem Ergebnis angezeigt wird. Um Seiten mit ähnlichem Inhalt anzuzeigen, klicken Sie auf diesen Link.

   * **Text für Verwandte Suche**

     Der Text, der neben Suchen nach verwandten Begriffen und Themen angezeigt wird.

   * **Text für Such-Trends**

     Der Titel über den Suchbegriffen, die eine Benutzerin oder ein Benutzer eingibt.

   * **Beschriftung: Ergebnisseiten**

     Der Text, der am Ende dieser Liste mit Links zu anderen Ergebnisseiten angezeigt wird.

   * **Beschriftung: Vorherige**

     Der Name, der für den Link zu vorherigen Suchseiten angezeigt wird.

   * **Beschriftung: Weiter**

     Der Name, der für den Link zu nachfolgenden Suchseiten angezeigt wird.

Das folgende Beispiel zeigt die Suchkomponente, nachdem im Stammverzeichnis der Standardinstallation das Wort *`geometrixx`* gesucht wurde. Es zeigt außerdem die Paginierung der Ergebnisse:

![dc_search_use](assets/dc_search_use.png)

Das folgende Beispiel zeigt einen falsch geschriebenen und nicht verfügbaren Suchbegriff:

![dc_search_usenotfound](assets/dc_search_usenotfound.png)

### Sitemap {#sitemap}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die Kernkomponenten [Navigation](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/navigation.html?lang=de), [Sprachnavigation](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/language-navigation.html?lang=de) und [Breadcrumb](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/breadcrumb.html?lang=de) zu verwenden.

Eine automatische Sitemap-Auflistung, in der (bei Standardeinstellungen) alle Seiten (als aktive Links) in der aktuellen Website aufgeführt werden: Ein Auszug zeigt zum Beispiel:

![dc_sitemap_use](assets/dc_sitemap_use.png)

Bei Bedarf können Sie Folgendes konfigurieren:

* **Sitemap**

   * **Stammverzeichnis**

     Pfad, von dem aus die Auflistung beginnen soll.

### Bildschirmpräsentation {#slideshow}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Karussell“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/carousel.html?lang=de) zu verwenden.

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

Mit dieser Komponente können Sie eine Reihe von Bildern laden, die als Bildschirmpräsentation auf Ihrer Seite angezeigt werden. Sie können Bilder hinzufügen oder entfernen und jedem einen Titel zuweisen. Unter „Erweitert“ können Sie auch die Größe des Anzeigebereichs angeben.

Sie können Folgendes konfigurieren:

* **Folien**

   * **Neue Folie**

     Über die Schaltflächen **Hinzufügen** (und **Entfernen**) können Sie eine Auswahl von Folien festlegen.

   * **Titel**

     Geben Sie gegebenenfalls einen Titel an. Der Titel wird auf der entsprechenden Folie überlagert.

* **Erweitert**

   * **Größe**

     Geben Sie die Breite und die Höhe in Pixel an.

Die Bildschirmpräsentation-Komponente zeigt dann wiederholt der Reihe nach die einzelnen Folien für kurze Zeit an und blendet jeweils zur nächsten Folie über.

![dc_slideshow_use](assets/dc_slideshow_use.png)

### Tabelle {#table}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Text“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html?lang=de) zu verwenden.

>[!NOTE]
>
>Die Foundation-Komponente **Tabelle** basiert ebenso wie die Foundation-Komponente **[Text](#text)** auf dem [Rich-Text-Editor](/help/sites-authoring/rich-text-editor.md).

Die **Tabellenkomponente** ist für das Erstellen, Ausfüllen und Formatieren einer Tabelle schon vorkonfiguriert. Im Dialogfeld können Sie Ihre Tabelle konfigurieren und den Inhalt erstellen, entweder:

* von Grund auf
* oder indem Sie ein Arbeitsblatt oder eine Tabelle aus einem externen Editor (wie Excel, OpenOffice, Editor usw.) kopieren und einfügen.

Mit dem Inline-Editor können Sie grundlegende Änderungen am Inhalt vornehmen:

![dc_table](assets/dc_table.png)

Im Vollbildmodus können Sie das Tabellenlayout konfigurieren:

![chlimage_1-97](assets/chlimage_1-97.png)

Der folgende Screenshot zeigt ein Beispiel für den Einsatz der Tabellen-Komponente. Das Design wird durch das Site-spezifische CSS bestimmt:

![dc_table_use](assets/dc_table_use.png)

### Tag-Cloud {#tag-cloud}

Eine Tag-Cloud zeigt eine grafisch dargestellte Auswahl der Tags, die auf Inhalte auf Ihrer Website angewendet werden:

![dc_tagclouduse](assets/dc_tagclouduse.png)

Beim Konfigurieren der Tag-Cloud-Komponente können Sie Folgendes festlegen:

* **Tags für Anzeige**

  Ort, aus dem die anzuzeigenden Tags erfasst werden sollen. Wählen Sie dafür eine Seite, eine Seite mit allen untergeordneten Seiten oder alle Tags aus.

* **Seite**

  Wählen Sie die Seite aus, auf die verwiesen werden soll.

* **Keine Einschränkung bezüglich Tags**

  Ob die angezeigten Tags als Links fungieren sollen.

Weitere Informationen zum Anwenden von Tags finden Sie unter [Verwenden von Tags](/help/sites-authoring/tags.md).

### Text {#text}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Text“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html?lang=de) zu verwenden.

>[!NOTE]
>
>Die Foundation-Komponente **Text** basiert ebenso wie die Foundation-Komponente **Tabelle** auf dem [Rich-Text-Editor](/help/sites-authoring/rich-text-editor.md).

Mit der Textkomponente können Sie einen Textblock unter Verwendung eines WYSIWYG-Editors eingeben, dessen Funktionalität vom [Rich-Text-Editor](/help/sites-authoring/rich-text-editor.md) bereitgestellt wird. Über eine Auswahl von Symbolen können Sie Ihren Text formatieren, einschließlich Schriftmerkmale, Ausrichtung, Links, Listen und Einzügen.

![chlimage_1-98](assets/chlimage_1-98.png)

Wenn Sie das Dialogfeld **Konfigurieren** öffnen, können Sie auch Folgendes festlegen:

* **Abstand**
* **Textstil**

Der formatierte Text wird auf der Seite angezeigt. Das eigentliche Design hängt von der Site-CSS ab:

![dc_text_use](assets/dc_text_use.png)

Weitere Informationen zur Text-Komponente und den vom Rich-Text-Editor bereitgestellten Funktionen finden Sie auf der Seite zum [Rich-Text-Editor.](/help/sites-authoring/rich-text-editor.md) 

#### Kontext-Bearbeitung {#inplace-editing}

Zusätzlich zu der Bearbeitung in Dialogfeldern durch den Rich-Text-Editor bietet AEM noch die Möglichkeit einer [Bearbeitung im Kontext](/help/sites-authoring/editing-content.md), bei der Sie den Text direkt so bearbeiten, wie er im Layout der Seite erscheint.

### Text und Bild {#text-image}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die Kernkomponenten [Bild](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/image.html?lang=de) und [Text](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html?lang=de) zu verwenden.

Mit der Komponente „Text und Bild“ werden ein Textblock und ein Bild hinzugefügt. Sie können auch Text und Bilder separat hinzufügen und bearbeiten. Weitere Einzelheiten finden Sie bei den Komponenten [Text](#text) und [Bild](#image).

![chlimage_1-99](assets/chlimage_1-99.png)

Sie können Folgendes konfigurieren:

* **Komponentenstile** (**Stile**)

  Mit dieser Option können Sie das Bild rechts- oder linksbündig ausrichten. Standardmäßig wird das Bild **linksbündig** ausgerichtet.

* **Bildeigenschaften** (**Erweiterte Bildeigenschaften**)

  Hier können Sie Folgendes angeben:

   * **Bild-Asset**

     Laden Sie das gewünschte Bild hoch.

   * **Titel**

     Der Titel des Blocks, der durch Bewegen der Maus angezeigt wird.

   * **Alt-Text**

     Alternativer Text, der angezeigt wird, wenn das Bild nicht dargestellt werden kann. Wenn dies leer gelassen wird, wird der Titel verwendet.

   * **Verknüpfung zu**

     Geben Sie einen Zielpfad an.

   * **Beschreibung**

     Eine Beschreibung des Bildes.

   * **Größe**

     Legt die Höhe und Breite des Bildes fest.

Das folgende Beispiel zeigt eine Text-Bild-Komponente, die das Bild linksbündig anzeigt:

![dc_textimage_use](assets/dc_textimage_use.png)

### Titel {#title}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Titel“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/list.html?lang=de) zu verwenden.

Die Komponente „Titel“ kann Folgendes tun:

* Den Namen der aktuellen Seite anzeigen, indem Sie das Feld „Titel“ leer lassen.
* Einen Text anzeigen, den Sie im Feld „Titel“ angeben.

Sie können Folgendes konfigurieren:

* **Titel**

  Wenn Sie einen anderen Namen als den Seitentitel verwenden möchten, geben Sie ihn hier ein.

* **Verknüpfung**

  Die URI, wenn der Titel als Link fungieren soll.

* **Typ/Größe**

  Wählen Sie aus der Dropdown-Liste die Option „Klein“ oder „Groß“. „Klein“ wird als Bild generiert. „Groß“ wird als Text generiert.

Das folgende Beispiel zeigt die Anzeige einer Komponente **Titel**. Das Design wird durch das Site-spezifische CSS bestimmt.

![dc_title_use](assets/dc_title_use.png)

### Video  {#video}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Einbetten“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/embed.html?lang=de) zu verwenden.

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

Mit der **Video**-Komponente können Sie ein vordefiniertes, vorkonfiguriertes Videoelement auf Ihrer Seite platzieren.

Siehe auch [Konfigurieren Ihrer Videoprofile](/help/sites-administering/config-video.md#configuringvideoprofiles) zur Verwendung mit HTML5-Elementen.

Nachdem Sie eine Instanz der Komponente auf Ihrer Seite platziert haben, können Sie Folgendes konfigurieren:

* Video 

   * **Video-Asset**

     Video-Asset hochladen oder ablegen.

   * **Größe**

     Die systemeigene Größe des Videos (Breite x Höhe in Pixeln) wird in den Feldern neben der Größe angezeigt (siehe oben). Geben Sie hier manuell die Breite und Höhe ein, wenn Sie die systemeigenen Abmessungen des Videos überschreiben möchten. Durch Auswahl von **OK** wird der Dialog beendet.

>[!NOTE]
>
>Unterstützte Formate:
>
>* `.mp4`
>* `Ogg`
>* `FLV` (Flash-Video)

## Spalten {#columns}

Spalten sind ein Mechanismus zur Steuerung des Inhalts-Layouts in AEM. In einer Standardinstallation werden Komponenten zum Erstellen von zwei oder drei Spalten bereitgestellt.

Das folgende Beispiel zeigt die zwei verwendeten Spalten-Komponenten. Sie können die Platzhalter für neue Komponenten verwenden:

![dc_columncontroluse](assets/dc_columncontroluse.png)

### 2 Spalten {#columns-1}

Eine Spalten-Steuerungs-Komponente, die standardmäßig auf zwei gleiche Spalten eingestellt ist.

### 3 Spalten {#columns-2}

Eine Spalten-Steuerungs-Komponente, die standardmäßig auf drei gleiche Spalten eingestellt ist.

### Spalten-Steuerung {#column-control}

Mit der Komponente „Spalten-Steuerung“ können Benutzerinnen und Benutzer auswählen, wie der Inhalt im Hauptbereich der Web-Seite in mehrere Spalten aufgeteilt werden soll. Benutzerinnen und Benutzer können die Anzahl der erforderlichen Spalten aus einer vordefinierten Liste auswählen und dann Inhalte in jeder der Spalten erstellen, löschen oder verschieben.

* **Spalten-Steuerung**

   * **Spalten-Layout**

     Wählen Sie die Anzahl der Spalten aus, die gerendert werden sollen. Nach der Erstellung verfügt jede Spalte über einen eigenen Link, um Inhalte hinzuzufügen, indem Komponenten oder Assets dorthin gezogen werden.

## Formular {#form}

>[!CAUTION]
>
>Die Foundation-Komponente wird nicht mehr unterstützt. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Mit Formular-Komponenten können Sie Formulare erstellen, damit Besucher Eingaben vornehmen können. Formulare und Formularkomponenten können verwendet werden, um Informationen, einschließlich Benutzer-Feedback (z. B. ein Fragebogen zur Kundenzufriedenheit) und Benutzerinformationen (z. B. Benutzerregistrierung), zu erfassen.

>[!NOTE]
>
>Informationen zu AEM Forms finden Sie in der [AEM Forms-Hilfe](/help/forms/home.md).

Formulare bestehen aus mehreren verschiedenen Komponenten:

* **Formular**

  Die Formular-Komponente definiert den Beginn und das Ende eines neuen Formulars auf einer Seite. Andere Komponenten können dann zwischen diesen Elementen eingefügt werden, wie etwa Tabellen und Downloads.

* **Formularfelder und -elemente**

  Formularfelder und -elemente können etwa Textfelder, Optionsschaltflächen und Bilder umfassen. Der Benutzer führt oft eine Aktion in einem Formularfeld aus, z. B. Eingabe von Text. Weitere Informationen finden Sie unter den einzelnen Formularelementen.

* **Profilkomponenten**

  Profilkomponenten beziehen sich auf Besucherprofile, die für soziale Zusammenarbeit und andere Bereiche verwendet werden, für die eine Personalisierung erforderlich ist.

Im Folgenden finden Sie ein Beispielformular. Es setzt sich zusammen aus der **Formularkomponente** (Anfang und Ende) mit zwei **Formular**-**Textfeldern**, einem **allgemeinen** **Textfeld**, das für den Einführungstext verwendet wird, und einer **Senden**-Schaltfläche.

![dc_form](assets/dc_form.png)

>[!NOTE]
>
>Informationen zum Entwickeln und Anpassen Ihrer Formulare finden Sie auf der Seite zum [Entwickeln von Formularen](/help/sites-developing/developing-forms.md). Diese Möglichkeit umfasst u. a. das Hinzufügen von Aktionen, Einschränkungen, das Vorausfüllen von Feldern und die Verwendung von Skripten, um einen Dienst für eine Aktion aufzurufen.

### Gemeinsame Einstellungen für (viele) Formularkomponenten {#settings-common-to-many-form-components}

Obwohl jede Formularkomponente einen anderen Zweck hat, bestehen viele aus ähnlichen Optionen und Parametern.

Beim Konfigurieren einer jeden Formularkomponente sind die folgenden Registerkarten im Dialogfeld verfügbar:

* **Titel und Text**

  Hier müssen Sie grundlegende Informationen angeben, wie den Titel des Formulars und begleitenden Text. Gegebenenfalls können Sie auch andere Schlüsselinformationen definieren, z. B. ob das Feld mehrmals ausgewählt werden kann und welche Elemente ausgewählt werden können.

* **Anfangswerte**

  Hier können Sie einen Standardwert angeben.

* **Begrenzungen**

  Hier können Sie angeben, ob ein Feld erforderlich ist, und Beschränkungen für dieses Feld platzieren (z. B. ob nur numerische Werte zulässig sind).

* **Stile**

  Gibt die Größe und den Stil der Felder an.

>[!NOTE]
>
>Die angezeigten Felder können je nach Komponente sehr unterschiedlich sein.

Diese Registerkarten bieten die notwendigen Parameter. Die Registerkarten können vom jeweiligen Komponententyp abhängen und Folgendes umfassen:

* **Titel und Text**

   * **Elementname**

     Name des Formularelements. Gibt an, wo im Repository die Daten gespeichert werden.
Dieses Feld ist erforderlich und sollte nur die folgenden Zeichen enthalten:

      * alphanumerische Zeichen
      * `_ . / : -`

   * **Titel**

     Der Titel, der mit dem Feld angezeigt wird. Wenn das Feld leer gelassen wird, wird der Standardtitel angezeigt.

   * **Beschreibung**

     Bietet Ihnen die Möglichkeit, bei Bedarf weitere Informationen für die Benutzerin bzw. den Benutzer anzugeben. Auf dem Formular wird sie unter dem Feld in einer kleineren Schrift als der Titel angezeigt.

   * **Einblenden/ausblenden**

     Bestimmt, wann das Feld sichtbar ist.

* **Anfangswerte**

   * **Standardwert**

     Der Wert, der im Feld beim Öffnen des Formulars angezeigt wird. Das heißt, bevor die Benutzerin bzw. der Benutzer eine Eingabe vornimmt.

* **Begrenzungen**

   * **Erforderlich**

     Abhängig vom Typ der Formularkomponente, bietet jedoch eines oder mehrere Kontrollkästchen, die anzeigen, dass das entsprechende Feld oder bestimmte Teile des Felds erforderlich sind.

   * **Meldung: Erforderlich**

     Eine Meldung, die Benutzerinnen und Benutzer darüber informiert, dass dieses Feld erforderlich ist. Ein erforderliches Feld ist außerdem mit einem Sternchen gekennzeichnet.

   * **Beschränkung**

     Welche Beschränkungen für die Auswahl verfügbar sind, hängt vom Typ der Formularkomponente ab.

   * **Beschränkungsmeldung**

     Eine Meldung, die den Benutzer über erforderliche Eingaben informiert.

* **Stile**

   * **Größe**

     In Zeilen und Spalten.

   * **Breite**

     In Pixeln.

   * **CSS**

### Formular (Komponente) {#form-component}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formular-Container“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html?lang=de) zu verwenden.

Die Formular-Komponente definiert den Beginn und das Ende eines Formulars mithilfe der Elemente **Beginn des Formulars** und **Ende des Formulars**. Beginn und Ende werden immer gepaart, um sicherzustellen, dass das Formular korrekt definiert ist.

![dc_form-1](assets/dc_form-1.png)

Zwischen dem Start und dem Ende eines Formulars können Sie Formular-Komponenten hinzufügen, die die eigentlichen Eingabefelder für die Benutzer definieren.

>[!NOTE]
>
>Eine Formularkomponente, die zu den Foundation-Komponenten gehört, unterstützt nur die Verwendung anderer Formularkomponenten aus den Foundation-Komponenten (Schaltflächen, Text, ausgeblendet usw.). Die Verwendung von Formularkomponenten, die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind, innerhalb eines Foundation-Komponenten-Formulars (und umgekehrt) wird nicht unterstützt.

#### Beginn des Formulars {#start-of-form}

Diese Komponente definiert den Beginn eines neuen Formulars auf einer Seite. Sie können Folgendes konfigurieren:

* **Formular**

   * **Dankeseite**

     Die Seite, auf die verwiesen wird, um Besuchern für ihre Eingabe zu danken. Wenn dies leer gelassen wird, wird das Formular nach der Übermittlung erneut angezeigt.

   * **Workflow starten**

     Bestimmt, welcher Workflow ausgelöst wird, sobald ein Formular übermittelt wird.

* **Erweitert**

   * **Aktionstyp**

     Für ein Formular ist eine Aktion erforderlich. Die Aktion bestimmt den Vorgang, dessen Ausführung mit den vom Benutzer übermittelten Daten ausgelöst wird (ähnlich wie „action=“ in HTML). Teilweise erfordert dies eine entsprechende **Aktionskonfiguration**.
Einige Aktionstypen sind in einer Standard-AEM-Installation enthalten:

      * **Kontoabfrage**
      * **Inhalt erstellen**
      * **Lead erstellen**
      * **Konto erstellen und aktualisieren**
      * **E-Mail-Dienst: Abonnenten erstellen und zu Liste hinzufügen**
      * **E-Mail-Dienst: Abwesenheitsnachricht senden**
      * **E-Mail-Dienst: Benutzer von Liste entfernen**
      * **Community bearbeiten**
      * **Ressourcen bearbeiten**
      * **Workflow-gesteuerte Ressourcen bearbeiten**
      * **E-Mail**
      * **Details für platzierten Auftrag**
      * **Profilaktualisierung**
      * **Kennwort zurücksetzen**
      * **Kennwort festlegen**
      * **Inhalt speichern**

        Der standardmäßige Aktionstyp.

      * **Inhalt mit Uploads speichern**
      * **Bestellung übermitteln**
      * **Abonnenten löschen**
      * **Auftrag aktualisieren**

   * **Formular-ID**

     Mit der Formular-ID wird das Formular eindeutig gekennzeichnet. Verwenden Sie die Formular-ID, wenn sich mehrere Formulare auf einer Seite befinden. Achten Sie darauf, dass die Formulare unterschiedliche IDs haben.

   * **Ladepfad**

     Dies ist der Pfad zu den Knoteneigenschaften, mit denen vordefinierte Werte in die Formularfelder geladen werden.

     Dies ist ein optionales Feld, das den Pfad zu einem Knoten im Repository angibt. Wenn dieser Knoten Eigenschaften hat, die den Feldnamen entsprechen, werden die jeweiligen Felder im Formular vorab mit den Werten dieser Eigenschaften ausgefüllt. Wenn keine Übereinstimmung besteht, steht im Feld der Standardwert.

     Mit **Ladepfad** können Sie das Formular mit Werten in den erforderlichen Feldern vorab laden. Siehe den Beitrag zum [Vorabladen von Formularwerten](/help/sites-developing/developing-forms.md#preloading-form-values).

   * **Client-Validierung**

     Gibt an, ob für dieses Formular eine Client-Überprüfung erforderlich ist (eine Server-Überprüfung findet *immer* statt). Die Client-Validierung kann mit der Komponente **Formular-Captcha** erzielt werden.

   * **Validierungsressourcentyp**

     Hiermit wird der Ressourcentyp für die Formularvalidierung definiert, wenn Sie das gesamte Formular (anstelle von einzelnen Feldern) überprüfen möchten. Wenn Sie das gesamte Formular überprüfen, führen Sie auch eine der folgenden Aufgaben aus:

      * Ein Skript zur Client-Überprüfung:

        `/apps/<*myApp*>/form/<*myValidation*>/formclientvalidation.jsp`

      * Ein Skript zur Überprüfung auf der Server-Seite:

        `/apps/<*myApp*>/form/<*myValidation*>/formservervalidation.jsp`

   * **Aktionskonfiguration**

     Die in **Aktionskonfiguration** verfügbaren Optionen hängen vom ausgewählten **Aktionstyp** ab:

      * **Kontoabfrage**

         * **Konto erstellen (Seite)**

           Die Seite, die beim Erstellen eines Kontos verwendet wird.

      * **Inhalt erstellen**

         * Inhalts-Pfad

           Der Inhaltspfad zu Inhalten, die aus dem Formular ausgegeben werden. Geben Sie einen Pfad ein, der mit einem Schrägstrich (`/`) endet. Der Schrägstrich zeigt an, dass für jeden Formular-Port ein neuer Knoten unter dem angegebenen Verzeichnis erstellt wird. Beispiel:

           `/forms/feedback/`

         * **Typ**

           Wählen Sie den erforderlichen Typ aus.

         * **Formular**

           Geben Sie das Formular an.

         * **Rendern mit**

           Wählen Sie die gewünschte Option aus der Liste aus.

         * **Ressourcentyp**

           Wenn festgelegt, wird dies zu jedem Kommentar als `sling:resourceType` hinzugefügt.

         * **Ansichtselektor**

      * **Lead erstellen**

         * **Lead wird dieser Liste hinzugefügt**

           Geben Sie die gewünschte Lead-Liste an.

      * **Konto erstellen und aktualisieren**

         * **Anfangsgruppe**

           Gruppe, der neue Benutzerinnen und Benutzer zugewiesen werden sollen.

         * **Home**

           Seite, die nach erfolgreicher Anmeldung angezeigt werden soll.

         * **Pfad**

           Der Pfad (relativ), in dem das neue Konto erstellt und gespeichert wird.

         * **Daten anzeigen...**

           Klicken Sie auf diese Schaltfläche, um im Bulk Editor auf die Informationen zu den Formularergebnissen zuzugreifen. Von hier aus können Sie die Informationen in eine `.tsv`-Datei (durch Tabulatoren getrennt) exportieren, die Sie z. B. in einer Excel-Tabelle öffnen können.

      * **E-Mail**

         * **Von**

           Geben Sie die E-Mail-Adresse ein, von der die E-Mail stammen soll.

         * **Mailto**

           Geben Sie eine oder mehrere E-Mail-Adressen ein, an die das Formular gesendet wird.

         * **CC**

           Geben Sie eine oder mehrere E-Mail-Adressen in CC ein.

         * **BCC**

           Geben Sie eine oder mehrere E-Mail-Adressen in BCC ein.

         * **Betreff**

           Geben Sie einen Betreff für die E-Mail ein.

      * **Kennwort zurücksetzen**

         * **Passwort ändern (Seite)**

           Die Seite, die beim Ändern des Passworts verwendet wird.

      * **Inhalt speichern**

         * **Inhalts-Pfad**

           Der Inhaltspfad zu Inhalten, die aus dem Formular ausgegeben werden. Geben Sie einen Pfad ein, der mit einem Schrägstrich (`/`) endet. Der Schrägstrich zeigt an, dass für jeden Formular-Port ein neuer Knoten unter dem angegebenen Verzeichnis erstellt wird. Beispiel:
           `/forms/feedback/`

         * **Daten anzeigen...**

           Klicken Sie auf diese Schaltfläche, damit Sie auf die Informationen über Formularergebnisse im Bulk Editor zugreifen können. Von hier aus können Sie die Informationen in eine .tsv (tabulatorgetrennte) Datei exportieren (z. B. zur Verwendung in einer Excel-Tabelle).

      * **Inhalt mit Uploads speichern**

        Hat die gleichen Optionen wie **Inhalt speichern**.

      * **Abonnentin bzw. Abonnent abmelden**

         * **Lead wird aus dieser Liste gelöscht**

           Geben Sie die gewünschte Lead-Liste an.

#### Ende des Formulars {#end-of-form}

Markiert das Ende des Formulars. Sie können Folgendes konfigurieren:

* **Formular-Ende**

   * **Senden-Schaltfläche einblenden**

     Gibt an, ob eine Senden-Schaltfläche angezeigt werden soll.

   * **Senden-Name**

     Eine ID, die erforderlich ist, wenn Sie mehrere Senden-Schaltflächen in einem Formular verwenden.

   * **Senden-Titel**

     Der Name, der auf der Schaltfläche angezeigt wird, z. B. „Senden“ oder „Übermitteln“.

   * **Zurücksetzen-Schaltfläche einblenden**

     Wenn Sie das Kontrollkästchen aktivieren, wird die Schaltfläche „Zurücksetzen“ angezeigt.

   * **Titel zurücksetzen**

     Der Name, der auf der Schaltfläche zum Zurücksetzen angezeigt wird.

   * **Beschreibung**

     Informationen, die unter der Schaltfläche angezeigt werden.

### Kontoname {#account-name}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formulartext“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html?lang=de) zu verwenden.

Ermöglicht der Benutzerin bzw. dem Benutzer die Eingabe eines Kontonamens:

![dc_form_accountname](assets/dc_form_accountname.png)

### Adresse {#address}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formulartext“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html?lang=de) zu verwenden.

Hiermit kann ein Feld für internationale Adressen im folgenden Format hinzugefügt werden:

![dc_form_address_field](assets/dc_form_addressfield.png)

Die Komponente ist für den unmittelbaren Einsatz konfiguriert, Sie können die Konfiguration jedoch bei Bedarf ändern. Es können z. B. Beschränkungen für die einzelnen Elemente der Adresse hinzugefügt werden. Wenn Felder leer gelassen werden, werden Standardeinstellungen verwendet.

### Captcha {#captcha}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten zu verwenden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).

>[!CAUTION]
>
>Es wird nicht mehr erwartet, dass diese Komponente vorkonfiguriert und ohne umfassende Anpassungen auf Projektebene funktioniert.

Bei der Captcha-Komponente muss der Benutzer eine alphanumerische Zeichenfolge eingeben, die am Bildschirm angezeigt wird. Die Zeichenfolge ändert sich bei jeder Aktualisierung.

![dc_form_captcha](assets/dc_form_captcha.png)

Sie können verschiedene Parameter für diese Komponente konfigurieren, einschließlich einer Meldung, die angezeigt wird, wenn die Captcha-Zeichenfolge ungültig ist.

### Kontrollkästchen-Gruppe {#checkbox-group}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularoptionen“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html?lang=de) zu verwenden.

Mit einem Kontrollkästchen können Sie eine Liste mehrerer Kontrollkästchen erstellen, von denen mehrere gleichzeitig ausgewählt werden können.

![dc_form_checkboxgroupuse](assets/dc_form_checkboxgroupuse.png)

Sie können verschiedene Parameter angeben, darunter einen Titel, eine Beschreibung und einen Elementnamen. Mithilfe der Schaltflächen „+“ und „-“ können Sie Elemente hinzufügen oder entfernen und sie dann mit den Pfeilen nach oben/unten positionieren.

>[!NOTE]
>
>Mit **Element-Ladepfad** können Sie die Kontrollkästchengruppen-Liste vorab mit Werten laden.
>
>Siehe [Vorabladen von Formularfeldern mit mehreren Werten](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Kreditkartendetails {#credit-card-details}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Hier können Sie die Felder angeben, die für die Eingabe der Kreditkartendetails erforderlich sind. Sie können sie so konfigurieren, dass die akzeptierten Arten von Karten und die erforderlichen Informationen (z. B. Sicherheits-Code) angegeben werden.

![chlimage_1-100](assets/chlimage_1-100.png)

### Dropdown-Liste {#dropdown-list}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularoptionen“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html?lang=de) zu verwenden.

Eine Dropdown-Liste kann so konfiguriert werden, dass Sie eine Reihe von Werten zur Auswahl haben:

![dc_form_dropdownlistuse](assets/dc_form_dropdownlistuse.png)

Sie können einen Titel und Elemente angeben, die in der Liste angezeigt werden sollen. Mit den Schaltflächen „+“ und „-“ können Sie Listenelemente hinzufügen oder entfernen und sie dann mit den Nach-oben- und Nach-unten-Tasten positionieren. Sie können angeben, ob Benutzerinnen und Benutzer mehrere Elemente aus der Liste auswählen dürfen, sowie alle Elemente, die beim ersten Öffnen der Liste automatisch ausgewählt sein sollen (Anfangswerte).

>[!NOTE]
>
>Mit dem **Element-Ladepfad** können Sie die Dropdown-Liste vorab mit Werten laden.
>
>Siehe [Vorabladen von Formularfeldern mit mehreren Werten](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Datei-Upload {#file-upload}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Die Komponente „Datei-Upload“ bietet Benutzern die Möglichkeit, eine Datei auszuwählen und hochzuladen.

![dc_form_fileupload](assets/dc_form_fileupload.png)

>[!NOTE]
>
>Sie können eine individuelle Upload-Komponente erstellen, um Dateien in ein Sling Servlet hochzuladen. Weitere Informationen finden Sie unter [Hochladen von Dateien in Adobe Experience Manager](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-cloud-service-create-asset-servlet-for-uploading-small-files/td-p/404276).

### Ausgeblendetes Feld {#hidden-field}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formular ausgeblendet“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-hidden.html?lang=de) zu verwenden.

Ermöglicht das Erstellen eines ausgeblendeten Felds. Diese ausgeblendeten Felder können für verschiedene Zwecke verwendet werden. Dies ist beispielsweise der Fall, wenn Sie eine Aktion nach dem Senden des Formulars durchführen müssen oder wenn ausgeblendete Daten in der Nachbearbeitung erforderlich sind.

![dc_form_hidenfield](assets/dc_form_hiddenfield.png)

>[!NOTE]
>
>Sie können das Formular auch so anpassen, dass bestimmte Formular-Komponenten abhängig vom Wert anderer auf dem Formular befindlichen Felder ein- oder ausgeblendet werden. Das Ändern der Sichtbarkeit eines Formularfelds ist nützlich, wenn das Feld nur unter besonderen Bedingungen erforderlich ist.
>
>Siehe [Ein- und Ausblenden von Formularkomponenten](/help/sites-developing/developing-forms.md#showing-and-hiding-form-components).

### Bild-Schaltfläche {#image-button}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularschaltfläche“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html?lang=de) zu verwenden.

Mit einer Bild-Schaltfläche können Sie eine Schaltfläche mit Ihrem eigenen Bild und Text erstellen:

![dc_form_imagebutton](assets/dc_form_imagebutton.png)

### Bild-Upload {#image-upload}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Die Bild-Upload-Komponente bietet Benutzern die Möglichkeit, eine Bilddatei auszuwählen und hochzuladen.

![dc_form_imageupload](assets/dc_form_imageupload.png)

### Verknüpfungsfeld {#link-field}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Im Link-Feld können Benutzer eine URL angeben:

![dc_form_link](assets/dc_form_link.png)

Wird am häufigsten für das Kalenderereignisformular verwendet, wo es für das URL-/Link-Feld eines Ereignisses verwendet wird.

### Kennwortfeld {#password-field}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Ermöglicht der Benutzerin oder dem Benutzer die Eingabe ihres bzw. seines Passworts:

![dc_form_password](assets/dc_form_password.png)

### Kennwort zurücksetzen {#password-reset}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) zu verwenden.

Diese Komponente bietet Ihrer Benutzerin oder Ihrem Benutzer zwei Felder für:

* die Eingabe eines Passworts
* die wiederholte Eingabe des Passworts, um zu bestätigen, dass die Eingabe korrekt ist.

Bei den Standardeinstellungen wird die Komponente wie folgt angezeigt:

![dc_password_reset](assets/dc_password_reset.png)

### Optionsfeldgruppe {#radio-group}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularoptionen“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-options.html?lang=de) zu verwenden.

Eine Optionsfeldgruppe stellt Ihnen eine Liste mit einem oder mehreren Optionsfeldern zur Verfügung, von denen jeweils nur eines ausgewählt werden kann.

Sie können den Elementnamen zusammen mit einem Titel und einer Beschreibung angeben. Mithilfe der Schaltflächen „+“ und „-“ können Sie Elemente hinzufügen oder entfernen, sie mit den Pfeilen nach oben/unten positionieren und bei Bedarf einen Standardwert festlegen:

![dc_form_radiogroupuse](assets/dc_form_radiogroupuse.png)

>[!NOTE]
>
>Mit dem **Element-Ladepfad** können Sie die Optionsfeld-Gruppe vorab mit Werten laden.
>
>Siehe [Vorabladen von Formularfeldern mit mehreren Werten](/help/sites-developing/developing-forms.md#preloading-form-fields-with-multiple-values).

### Senden-Schaltfläche {#submit-button}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularschaltfläche“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html?lang=de) zu verwenden.

Mit dieser Komponente können Sie eine Senden-Schaltfläche mit dem Standardtext erstellen:

![dc_form_submitbutton](assets/dc_form_submitbutton.png)

Oder Sie können Ihren eigenen Text eingeben:

![dc_form_submit_buttonuse](assets/dc_form_submitbuttonuse.png)

### Feld „Tags“ {#tags-field}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponenten zu verwenden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de).

In diesem Feld können Sie Tags auswählen:

![dc_form_tags_use](assets/dc_form_tags_use.png)

Sie können auf der spezialisierten Registerkarte verschiedene Parameter festlegen, darunter auch die Namespaces:

* **Tag-Feld**

   * **Zugelassene Namespaces**

      * **Geometrixx Outdoors**
      * **Arbeitsablauf**
      * **Forum**
      * **Bildarchiv**
      * **Geometrixx Media**
      * **Standard-Tags**
      * **Marketing**
      * **Asset-Eigenschaften**
      * **Breite in Pixel**
      * **Popup-Größe**

### Textfeld {#text-field}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formulartext“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-text.html?lang=de) zu verwenden.

Das Standardtextfeld kann an die erforderliche Größe angepasst werden und kann den eigenen Lead in der Nachricht enthalten:

![dc_form_text](assets/dc_form_text.png)

### Workflow-Sende-Schaltfläche(n) {#workflow-submit-button-s}

>[!CAUTION]
>
>Diese Foundation-Komponente ist veraltet. Adobe empfiehlt, stattdessen die [Kernkomponente „Formularschaltfläche“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-button.html?lang=de) zu verwenden.

Damit können Sie eine Senden-Schaltfläche für die Verwendung in einem Workflow erstellen.

![chlimage_1-101](assets/chlimage_1-101.png)
