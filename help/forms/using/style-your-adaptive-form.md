---
title: 'Adaptive Formulare gestalten '
seo-title: Style your adaptive form
description: 'Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, einzelne Komponenten formatieren und Webfonts in einem Design verwenden '
seo-description: Learn to create a custom theme, style individual components, and use web fonts in a theme
page-status-flag: de-activated
uuid: ffb2cc22-baaf-4525-a2e3-29f39271c670
topic-tags: introduction
discoiquuid: 655303a4-99bb-4ba3-9d50-a178f5edcf85
feature: Adaptive Forms
exl-id: 7742c3ca-1755-44c5-b70f-61309f09d1b8
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '2037'
ht-degree: 100%

---

# Adaptive Formulare gestalten {#do-not-publish-style-your-adaptive-form}

Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, einzelne Komponenten formatieren und Webfonts in einem Design verwenden

![](do-not-localize/08-style_your_adaptiveformmain.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

## Über die Schulung  {#about-the-tutorial}

Sie können Themen verwenden, um einem adaptiven Formular eine eindeutige Darstellung und einen einzigartigen Stil zu geben. Sie können Standarddesigns anwenden, die mit dem adaptiven Formulareditor bereitgestellt werden, oder eigene Designs erstellen. AEM [!DNL Forms] bietet einen [Design-Editor](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/themes.html) zum Erstellen benutzerdefinierter Designs. Ein einzelnes Design kann das gleiche Aussehen auf Mobilgeräten, Tablets oder Desktops bieten. Vorkenntnisse von CSS oder LESS sind nicht erforderlich, um den Designeditor zu verwenden, aber sie sind erwünscht.

Am Ende der Schulung lernen Sie Folgendes: 

* Wenden Sie ein Standarddesign auf ein adaptives Formular an
* Erstellen Sie mithilfe des Designeditors ein Design für das adaptive Formular
* Entwerfen Sie einzelne Komponenten
* Bonusabschnitt: Verwenden Sie Webfonts in einem benutzerdefinierten Design

Nach dem Abschließen des Lernprogramms sieht das Formular wie folgt aus:

![Formular mit einem benutzerdefinierten Thema](assets/styled-adaptive-form.png)

## Bevor Sie beginnen {#before-you-start}

Laden Sie die unten abgebildeten kopfzeilenartigen und Logo-Bilder auf Ihrem lokalen Computer herunter. Die Kopfzeile des adaptiven Formulars `shipping-address-add-update-form` verwendet die kopfzeilenartigen und Logo-Bilder. Das kopfzeilenartige Bild erscheint auf der rechten Seite der Kopfzeile.

[Datei abrufen](assets/header-style.png)

[Datei abrufen](assets/logo-1.png)

## Schritt 1: Wenden Sie ein Design auf Ihr adaptives Formular an {#step-apply-a-theme-to-your-adaptive-form}

Der Adaptive Forms Editor bietet mehrere Standarddesigns. Wenn Sie beabsichtigen, keinen benutzerdefinierten Stil für Ihr adaptives Formular zu verwenden, können Sie Ihre adaptiven Formulare auch mit einem Standarddesign veröffentlichen. Designs sind unabhängig von adaptiven Formularen. Sie können dasselbe Design auf mehrere adaptive Formulare anwenden. So wenden Sie ein Design auf ein adaptives Formular an:

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Öffnen Sie die Eigenschaften von **[!UICONTROL Adaptive Form - Container]**. Navigieren Sie im Eigenschaften-Browser zu **[!UICONTROL Standard]** > **[!UICONTROL Adaptives Formulardesign]**. Das Feld **[!UICONTROL Adaptives Formulardesign]** listet alle vordefinierten und benutzerdefinierten Designs auf. Standardmäßig wird das Canvas-Design angewendet.
1. Wählen Sie ein Design aus dem Feld **[!UICONTROL Adaptives Formulardesign]**. Zum Beispiel: **Umfragedesign**. Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um das ausgewählte Design anzuwenden.

   ![Adaptives Formular mit dem Standarddesign](assets/default-adaptive-form.png)

   **Abbildung:** *Adaptives Formular mit dem Standard-Design*

   ![Adaptives Formular mit dem Umfragedesign](assets/adaptive-form-with-survey-theme.png)

   **Abbildung:** *Adaptives Formular mit dem Umfragedesign*

## Schritt 2: Aktualisieren Sie Ihr adaptives Formular {#step-update-your-adaptive-form}

Das oben angezeigte Design erfordert Änderungen am Platzhaltertext und Logo des vorhandenen adaptiven Formulars. Führen Sie die folgenden Schritte aus, um die erforderlichen Änderungen vorzunehmen:

1. Ändern Sie das vorhandene Logo und den Text der Kopfzeile. Entfernen des Logos:

   1. Öffnen Sie das Formular im Formulareditor.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Tippen Sie auf das Logo-Bild in der Komponente [!UICONTROL Kopfzeile] und anschließend auf ![cmppr](assets/cmppr.png) **[!UICONTROL Eigenschaften]**. Tippen Sie in der Eigenschaft [!UICONTROL Bild] auf „X“, um das vorhandene Logo-Bild zu entfernen.
   1. Tippen Sie auf **[!UICONTROL Hochladen]**, wählen Sie „logo.png“ aus und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen.
   1. Tippen auf Kopfzeilentext, `We.Retail`, und anschließend auf ![aem_6_3_edit](assets/aem_6_3_edit.png) **[!UICONTROL Bearbeiten]**. Ändern des Kopfzeilentextes in `we retail`. Anwenden der Fettformatierung nur auf `we`in `we retail`.

      ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Entfernen Sie Titel und fügen Sie Platzhaltertext hinzu:

   1. Tippen Sie auf das Feld „Kunden-ID“ und anschließend auf ![cmppr](assets/cmppr.png) „Eigenschaften“.
   1. Kopieren Sie den Inhalt des Felds **[!UICONTROL Titel]** in das Feld **[!UICONTROL Platzhaltertext]**.
   1. Löschen Sie den Inhalt des Felds **[!UICONTROL Titel]** und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Wiederholen Sie die vorherigen drei Schritte für alle Textfelder, das numerische Feld und das E-Mail-Feld im Formular.

      ![updated-adaptive-form](assets/updated-adaptive-form.png)

## Schritt 3: Erstellen Sie ein benutzerdefiniertes Design für Ihr adaptives Formular {#step-create-a-custom-theme-for-your-adaptive-form}

Sie können den [Design-Editor](/help/forms/using/themes.md) verwenden, um benutzerdefinierte Designs zu erstellen. Der Design-Editoreditor ist ein leistungsstarker WYSIWYG-Editor. Es ist eine visuelle Methode, um CSS auf verschiedene Komponenten eines adaptiven Formulars anzuwenden. Es bietet bessere Steuerelemente, um Komponenten und Bereiche eines adaptiven Formulars zu gestalten.

Ein Design ist eine separate Entität wie adaptive Formulare. Es enthält Stile (CSS) für die Komponenten und Bereiche eines adaptiven Formulars. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, wird der angegebene Stil auf die entsprechenden Komponenten eines adaptiven Formulars angewendet.

In diesem Lernprogramm werden Kopf- und Fußzeilen, Text- und numerische Komponenten, Anhangskomponenten und Schaltflächen formatiert. Beginnen wir mit dem Erstellen eines Designs: 

### Erstellen von Designs {#create-a-theme}

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**. Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Tippen Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Design]**. Die Seite [!UICONTROL Design erstellen] mit den Feldern zum Erstellen eines Designs wird angezeigt. Die Felder **[!UICONTROL Titel]** und **[!UICONTROL Name]** sind obligatorisch.

   * **Titel:** Geben Sie einen Titel für das Design an. Zum Beispiel: **Globales Design.** Der Titel hilft Ihnen, das Design in der Liste der Designs zu identifizieren.
   * **Name**: Geben Sie den Namen des Designs an. Zum Beispiel: **Globales-Design.** Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Ungültige Eingaben werden durch Bindestriche ersetzt.

1. Tippen Sie auf **[!UICONTROL Erstellen]**. Ein Design wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt. Tippen Sie auf **[!UICONTROL Öffnen]**, um das neu erstellte Design in einer neuen Registerkarte zu öffnen. Design wird im Design-Editor geöffnet. Zum Festlegen des Designs verwendet der Design-Editor ein adaptives Standardformular, das im Lieferumfang von AEM [!DNL Forms] enthalten ist.

   Informationen zur Verwendung der Benutzeroberfläche des Design-Editors finden Sie unter [Informationen zum Design-Editor](/help/forms/using/themes.md#aboutthethemeeditor).

1. Tippen Sie auf **[!UICONTROL Designoptionen]** ![theme-options](assets/theme-options.png) > **[!UICONTROL Konfigurieren]**. Wählen Sie im Feld **[!UICONTROL Vorschauformular]** das adaptive Formular **shipping-address-add-update-form** und tippen Sie zunächst auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), dann auf **[!UICONTROL Speichern]**. Jetzt ist der Design-Editor konfiguriert, um Ihr eigenes adaptives Formular anstelle des adaptiven Standardformulars zu benutzen. Tippen Sie auf **[!UICONTROL Abbrechen]**, um zum Design-Editor zurückzukehren.

   ![custom-theme](assets/custom-theme.png)

   **Abbildung:** *Design-Editor mit dem adaptiven Formular „shipping-address-add-update-form“*

   ![create-a-theme](assets/create-a-theme.png)

   **Abbildung:** *Adaptives Formular mit dem Standardformular*

### Kopf- und Fußzeile gestalten {#style-header-and-footer}

Kopf- und Fußzeile bieten einem adaptiven Formular ein konsistentes und unverwechselbares Aussehen. Im Allgemeinen enthält die Kopfzeile das Logo und den Namen der Organisation. Die Fußzeile enthält Copyright-Informationen, die in allen Formularen einer Organisation identisch bleiben. So formatieren Sie Kopf- und Fußzeile des adaptiven Formulars „shipping-address-add-update-form adaptive form“:

1. Navigieren Sie im Bereich „Auswahl“ zur Option **[!UICONTROL Kopfzeile]** > **[!UICONTROL Text]**. Der Bereich „Auswahl“ befindet sich auf der linken Seite des Design-Editors. Wenn das Bedienfeld nicht sichtbar ist, tippen Sie auf ![toggle-side-panel](assets/toggle-side-panel.png) – „Seitliches Bedienfeld ein/aus“.

1. Legen Sie die folgenden Eigenschaften im Akkordeon **[!UICONTROL Text]** fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | Schriftfamilie | Arial |
   | Schriftfarbe | FFFFFF |
   | Schriftgrad | 54px |

1. Tippen Sie zunächst auf das [!UICONTROL Kopfzeilen]-Widget und dann auf **[!UICONTROL Kopfzeile]**. Die Optionen zum Formatieren des Kopfzeilen-Widgets werden auf der linken Seite angezeigt. Erweitern Sie das Akkordeon **[!UICONTROL Abmessungen und Position]**, legen Sie für die **[!UICONTROL Höhe]** `120px` fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Erweitern Sie das Akkordeon **[!UICONTROL Hintergrund]** des Kopfzeilen-Widgets und legen Sie für die **[!UICONTROL Hintergrundfarbe]** `F6921E.` fest.

   Bewegen Sie den Mauszeiger über **[!UICONTROL Bild und Verlauf]** > **[!UICONTROL + Hinzufügen]** und tippen Sie auf **[!UICONTROL Bild]**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | image | Laden Sie header-style.png hoch. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen. |
   | Position | Rechts unten |
   | Anordnung | Keine Wiederholung |

1. Tippen Sie im Design-Editor auf das Logo in der Kopfzeile und tippen Sie auf **[!UICONTROL Kopfzeilen-Logo]**. Erweitern Sie das Akkordeon „Abmessungen und Position“, legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Rand</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Rand</td> 
      <td> 
       <ul> 
        <li>Oben: 1.5rem</li> 
        <li>Unten: -35px</li> 
        <li>Links: 1rem<strong><br /> </strong></li> 
       </ul> <p><strong>Tipp:</strong> Tippen Sie auf das Link-Symbol<img src="assets/link.png">, um einen anderen Wert für jedes Feld zur Verfügung zu stellen.<br /> </p> </td> 
     </tr> 
     <tr> 
      <td>Höhe</td> 
      <td>4.75rem</td> 
     </tr> 
    </tbody> 
   </table>

1. Tippen Sie auf das Fußzeilen-Widget und tippen Sie auf **[!UICONTROL Fußzeile]**. Erweitern Sie das Akkordeon **[!UICONTROL Hintergrund]**, legen Sie für die **[!UICONTROL Hintergrundfarbe]** `F6921E` fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Formatieren Sie die Datenerfassungskomponente und wenden Sie einen Hintergrund auf das adaptive Formular an. {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

Sie können mehrere Komponenten in einem adaptiven Formular verwenden, um Daten zu erfassen. Zum Beispiel Textfeld und Zahlenfeld. Sie können für alle Datenerfassungskomponenten einen identischen Stil bereitstellen oder jeder Komponente einen eigenen Stil zuweisen. In diesem Lernprogramm wird ein identischer Stil auf numerische Felder (Kunden-ID, Postleitzahl) und Textfelder (Kunden-ID, Name, Lieferadresse, Status, E-Mail) angewendet. So gestalten Sie die Datenerfassungskomponenten:

1. Tippen Sie zunächst auf das Feld **[!UICONTROL Kunden-ID]** und dann auf die Option **[!UICONTROL Feld-Widget]**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Akkordeon</b></td> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenfarbe</td> 
      <td>A7A9AC</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenradius </td> 
      <td> 
       <ul> 
        <li>Oben: 7px<br /> </li> 
        <li>Rechts: 7px<br /> </li> 
        <li>Unten: 7px<br /> </li> 
        <li>Links: 7px<br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>939598<br /> </td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18px</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Breite</td> 
      <td>60%</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Rand</td> 
      <td> 
       <ul> 
        <li>Links: 10rem</li> 
       </ul> </td> 
     </tr> 
    </tbody> 
    </table>

1. Tippen Sie zunächst auf den leeren Bereich über dem Feld **[!UICONTROL Kunden-ID]** und dann auf **[!UICONTROL Responsive Bereichscontainer]**. Legen Sie den **[!UICONTROL Hintergrund]** > **[!UICONTROL Hintergrundfarbe]** auf F1F2F2 fest. Tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![](do-not-localize/responsive-panel-container.png)

### Gestalten Sie die Schaltflächen {#style-the-buttons}

Sie können ein benutzerdefiniertes Design verwenden, um allen Schaltflächen des adaptiven Formulars einen identischen Stil zuzuweisen, bzw. einen [Inline-Stil](/help/forms/using/inline-style-adaptive-forms.md), um einen Stil einer bestimmten Schaltfläche zuzuweisen. So gestalten Sie die Schaltflächen:

1. Tippen Sie auf **[!UICONTROL Senden]** und dann auf **[!UICONTROL Option]**. Legen Sie die folgenden Eigenschaften fest und tippen Sie auf ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   <table> 
    <tbody> 
     <tr> 
      <td><b>Akkordeon</b></td> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Hintergrund</td> 
      <td>Hintergrundfarbe</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rahmen<br /> </td> 
      <td>Rahmenfarbe</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenradius </td> 
      <td> 
       <ul> 
        <li>Oben: 7px<br /> </li> 
        <li>Rechts: 7px<br /> </li> 
        <li>Unten: 7px<br /> </li> 
        <li>Links: 7px </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Text<br /> </td> 
      <td>Schriftfamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18px</td> 
     </tr> 
    </tbody> 
   </table>

1. [Wenden Sie das benutzerdefinierte Design](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form), Globales Design, auf Ihr adaptives Formular an. Wenn der Stil das adaptive Formular nicht widerspiegelt, bereinigen Sie den Browser-Cache und versuchen Sie es erneut. 

   ![style-data-collection-components](assets/style-data-capture-components.png)

## Schritt 4: Gestalten Sie einzelne Komponenten {#step-style-individual-components}

Einige Stile gelten nur für eine bestimmte Komponente. Solche Komponenten werden im adaptiven Formulareditor gestaltet.

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Wählen Sie in der oberen Leiste die Option **[!UICONTROL Stil]**.

   ![style-option](assets/style-option.png)

1. Tippen Sie auf die Schaltfläche **[!UICONTROL Anhängen]** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Stellen Sie die folgenden Eigenschaften im Akkordeon **[!UICONTROL Abmessungen und Position]** ein:

   | Eigenschaft | Wert |
   |---|---|
   | Gleitkomma | Links |
   | Breite | 10% |

1. Tippen Sie auf die Option **[!UICONTROL Von Behörden anerkannter Adressnachweis]** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Legen Sie die folgenden Eigenschaften fest:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Akkordeon</b></td> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Gleitkomma</td> 
      <td>Links</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Breite</td> 
      <td>73%</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Erweiterte Umrandung</td> 
      <td> 
       <ul> 
        <li>Links: 10px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Höhe</td> 
      <td>40px</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position<br /> </td> 
      <td>Rand</td> 
      <td><br /> 
       <ul> 
        <li>Rechts: 2rem</li> 
        <li>Links: 10rem </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Hintergrund</td> 
      <td>Hintergrundfarbe</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenbreite</td> 
      <td>1px</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenstil</td> 
      <td>Durchgezogen</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenfarbe</td> 
      <td>A7A9AC</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenradius</td> 
      <td>7px</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfamilie</td> 
      <td>Arial</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>BCBEC0</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18px</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Zeilenhöhe</td> 
      <td>2</td> 
     </tr> 
     </tr> 
    </tbody> 
   </table>

1. Tippen Sie auf die Schaltfläche **[!UICONTROL Senden]** und dann auf das Symbol ![aem_6_3_edit](assets/aem_6_3_edit.png). Legen Sie die folgenden Eigenschaften fest:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Akkordeon</b></td> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Gleitkomma</td> 
      <td>Rechts</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Rand</td> 
      <td> 
       <ul> 
        <li>Oben: 5rem</li> 
        <li>Rechts: 14rem</li> 
        <li>Unten: 20px</li> 
        <li>Links: 20px<br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Hintergrund</td> 
      <td>Hintergrundfarbe</td> 
      <td>F6921E</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenfarbe</td> 
      <td>F6921E</td> 
     </tr> 
    </tbody> 
   </table>

   ![styled-adaptive-form-1](assets/styled-adaptive-form-1.png)

## Schritt 5: Bonusabschnitt: Verwenden von Webschriftarten in einem benutzerdefinierten Design {#step-bonus-section-using-web-fonts-in-a-custom-theme}

Sie können verschiedene Schriftarten verwenden, um ein adaptives Formular zu entwerfen. Alle Geräte, auf denen das adaptive Formular angezeigt wird, verfügen möglicherweise nicht über die zum Entwerfen des adaptiven Formulars verwendeten Schriftarten. Sie können einen Webfont-Dienst verwenden, um erforderliche Schriftarten auf dem Zielgerät bereitzustellen.

[!DNL Adobe Fonts] ist ein Webschriftartdienst. Sie können den Dienst mit adaptiven Formularen konfigurieren und verwenden. So verwenden Sie [!DNL Adobe Fonts] in einem adaptiven Formular:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) [!DNL Typekit] heißt jetzt Adobe Fonts und ist in Creative Cloud- und anderen Abonnements enthalten. [Weitere Informationen](https://fonts.adobe.com/)

1. Erstellen Sie ein [Adobe Fonts](https://typekit.com/)-Konto, erstellen Sie ein Kit, fügen Sie dem Kit die Schriftart Myriad Pro hinzu, veröffentlichen Sie das Kit und erhalten Sie die Kit-ID. Es ist erforderlich, [!DNL Adobe Fonts] (Webfonts) in einem adaptiven Formular zu verwenden.
1. Im AEM [!DNL Forms] Server, navigieren Sie zu ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Werkzeuge]** ![Hammer](assets/hammer.png) > **[!UICONTROL Adobe Fonts]**. Öffnen Sie jetzt einen Konfigurationsordner. Wenn eine Konfiguration bereits zur Verfügung steht, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**, um eine neue Instanz zu erstellen.

   Geben Sie im Dialogfeld „Konfiguration erstellen“ einen **Titel** für die Konfiguration an und klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin werden Sie zur Seite „Konfiguration“ geleitet. Geben Sie im Dialogfeld [!UICONTROL Komponente bearbeiten], das angezeigt wird, Ihre **Kit-ID** ein und klicken Sie auf **[!UICONTROL OK]**.

1. Konfigurieren Sie Ihr Design für die Verwendung der [!DNL Adobe Fonts]-Konfiguration. Öffnen Sie in der Autorinstanz ein Design im Design-Editor **[!UICONTROL Globales Design]**. Navigieren Sie im Design-Editor zu **[!UICONTROL Themenoptionen]** ![Themenoptionen](assets/theme-options.png) > **[!UICONTROL Konfigurieren]**. Wählen Sie im Feld **[!UICONTROL Adobe Fonts-Konfiguration]** ein Kit aus und klicken Sie auf **[!UICONTROL Speichern]**.

   Die zu **[!UICONTROL Adobe Fonts]** hinzugefügten Schriftarten stehen im **[!UICONTROL Text]**-Akkordeon aller Komponenten zur Auswahl.
