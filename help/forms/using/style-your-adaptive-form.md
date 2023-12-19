---
title: Gestalten eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, individuelle Komponenten gestalten und Web Fonts in einem Design verwenden.
topic-tags: introduction
feature: Adaptive Forms
exl-id: 7742c3ca-1755-44c5-b70f-61309f09d1b8
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '1982'
ht-degree: 84%

---

# Gestalten eines adaptiven Formulars {#do-not-publish-style-your-adaptive-form}

Erfahren Sie, wie Sie ein benutzerdefiniertes Design erstellen, individuelle Komponenten gestalten und Web Fonts in einem Design verwenden.

![hero-image](do-not-localize/08-style_your_adaptiveformmain.png)

Dieses Tutorial ist ein Teil der Serie [Erstellen Ihres ersten adaptives Formulars](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Adobe empfiehlt, der Reihe chronologisch zu folgen, um den gesamten Anwendungsfall des Tutorials zu verstehen, auszuführen und praktisch zu erleben.

## Über das Tutorial  {#about-the-tutorial}

Mithilfe von Designs können Sie ein adaptives Formular mit einem unverwechselbaren Erscheinungsbild und Stil versehen. Sie haben die Möglichkeit, im adaptiven Formulareditor vorkonfigurierte Designs anzuwenden oder eigene benutzerdefinierte Designs zu erstellen. AEM [!DNL Forms] bietet einen [Design-Editor](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/themes.html) zum Erstellen benutzerdefinierter Designs. Über ein einziges Design kann ein und dasselbe adaptive Formular verschiedene Erscheinungsbilder erhalten, je nachdem, ob es auf einem Mobilgerät, Tablet oder Desktop geöffnet wird. CSS- oder LESS-Vorkenntnisse sind für die Nutzung des Design-Editors zwar nicht erforderlich, aber wünschenswert.

Am Ende des Tutorials sollten Sie zu Folgendem in der Lage sein:

* Anwenden eines vorkonfigurierten Designs auf ein adaptives Formular
* Erstellen eines Designs für ein adaptives Formular mit dem Design-Editor
* Gestalten einzelner Komponenten
* Bonusabschnitt: Verwenden von Web Fonts in einem benutzerdefinierten Design

Ihr Formular sollte nach Abschluss des Tutorials etwa wie folgt aussehen:

![Formular mit einem benutzerdefinierten Thema](assets/styled-adaptive-form.png)

## Bevor Sie beginnen {#before-you-start}

Laden Sie die unten bereitgestellten Header-Stile und Logobilder auf Ihren lokalen Computer herunter. Die Kopfzeile des adaptiven Formulars `shipping-address-add-update-form` verwendet die kopfzeilenartigen und Logo-Bilder. Das kopfzeilenartige Bild erscheint auf der rechten Seite der Kopfzeile.

[Datei abrufen](assets/header-style.png)

[Datei abrufen](assets/logo-1.png)

## Schritt 1: Anwenden eines Designs auf Ihr adaptives Formular {#step-apply-a-theme-to-your-adaptive-form}

Der Editor für adaptive Formulare bietet mehrere vorkonfigurierte Designs. Wenn Sie keinen benutzerdefinierten Stil für Ihr adaptives Formular verwenden möchten, können Sie Ihre adaptiven Formulare auch mit einem der vorkonfigurierten Designs veröffentlichen. Designs sind unabhängig von adaptiven Formularen. Sie können dasselbe Design auf mehrere adaptive Formulare anwenden.

**So wenden Sie ein Design auf Ihr adaptives Formular an:**

1. Öffnen Sie das adaptive Formular zum Bearbeiten.

   [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

1. Öffnen Sie die Eigenschaften des **[!UICONTROL Containers für adaptive Formulare]**. Navigieren Sie im Eigenschaften-Browser zu **[!UICONTROL Allgemein]** > **[!UICONTROL Adaptives Formulardesign]**. Das Feld **[!UICONTROL Adaptives Formulardesign]** listet alle vordefinierten und benutzerdefinierten Designs auf. Standardmäßig wird das Canvas-Design angewendet.
1. Wählen Sie ein Design aus dem Feld **[!UICONTROL Adaptives Formulardesign]** aus, z. B. für **Umfragen**. Auswählen ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) damit Sie das ausgewählte Design anwenden können.

   ![Adaptives Formular mit dem Standarddesign](assets/default-adaptive-form.png)

   **Abbildung:** *Adaptives Formular mit dem Standard-Design*

   ![Adaptives Formular mit dem Umfragedesign](assets/adaptive-form-with-survey-theme.png)

   **Abbildung:** *Adaptives Formular mit dem Umfragedesign*

## Schritt 2: Aktualisieren Ihres adaptiven Formulars {#step-update-your-adaptive-form}

Das oben angezeigte Design erfordert Änderungen am Platzhaltertext und Logo des vorhandenen adaptiven Formulars.

**So aktualisieren Sie Ihr adaptives Formular:**

1. Ändern Sie das vorhandene Logo und den Text in der Kopfzeile. So entfernen Sie das Logo:

   1. Öffnen Sie das Formular im Formulareditor.

      [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html)

   1. Logobild im [!UICONTROL header] Komponente und wählen Sie ![cmppr](assets/cmppr.png) **[!UICONTROL properties]**. Im [!UICONTROL image] -Eigenschaft, wählen Sie X aus, um das vorhandene Logo-Bild zu entfernen.
   1. Auswählen **[!UICONTROL hochladen]**, wählen Sie logo.png und dann ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) , um die Änderungen zu speichern. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen.
   1. Kopfzeilentext auswählen, `We.Retail`und wählen Sie ![aem_6_3_edit](assets/aem_6_3_edit.png) **[!UICONTROL edit]**. Ändern des Kopfzeilentextes in `we retail`. Anwenden der Fettformatierung nur auf `we`in `we retail`.

      ![we-retail-logo-text](assets/we-retail-logo-text.png)

1. Entfernen Sie Titel und fügen Sie Platzhaltertext hinzu:

   1. Wählen Sie das Feld Kunden-ID aus und wählen Sie ![cmppr](assets/cmppr.png) Eigenschaften.
   1. Kopieren Sie den Inhalt des Felds **[!UICONTROL Titel]** in das Feld **[!UICONTROL Platzhaltertext]**.
   1. Löschen Sie den Inhalt der **[!UICONTROL Titel]** Feld und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
   1. Wiederholen Sie die vorherigen drei Schritte für alle Textfelder, das numerische Feld und das E-Mail-Feld im Formular.

      ![updated-adaptive-form](assets/updated-adaptive-form.png)

## Schritt 3: Erstellen eines benutzerdefinierten Designs für Ihr adaptives Formular {#step-create-a-custom-theme-for-your-adaptive-form}

Sie können den [Design-Editor](/help/forms/using/themes.md) verwenden, um benutzerdefinierte Designs zu erstellen. Der Design-Editor ist ein leistungsstarker WYSIWYG-Editor. Er bietet eine visuelle Methode, um CSS auf verschiedene Komponenten eines adaptiven Formulars anzuwenden. Der Editor stellt genauere Steuerelemente zum Gestalten von Komponenten und Panels eines adaptiven Formulars bereit.

Ein Design ist eine separate Entität, so wie adaptive Formulare. Es enthält Stile (CSS) für die Komponenten und Panels eines adaptiven Formulars. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie ein Design anwenden, wird der angegebene Stil auf die entsprechenden Komponenten eines adaptiven Formulars angewendet.

Im Rahmen dieses Tutorials gestalten Sie Kopf- und Fußzeilen, Text- und numerische Komponenten, Anhangskomponenten sowie Schaltflächen. Erstellen wir zunächst ein Design.

### Erstellen von Designs {#create-a-theme}

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Designs]**. Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments-themes).
1. Auswählen **[!UICONTROL Erstellen]** und wählen **[!UICONTROL Design]**. Die Seite [!UICONTROL Design erstellen] mit den Feldern zum Erstellen eines Designs wird angezeigt. Die Felder **[!UICONTROL Titel]** und **[!UICONTROL Name]** sind obligatorisch.

   * **Titel:** Geben Sie einen Titel für das Design an. Zum Beispiel: **Globales Design.** Der Titel hilft Ihnen, das Design in der Liste der Designs zu identifizieren.
   * **Name**: Geben Sie den Namen des Designs an. Beispiel: **Globales-Design.** Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.

1. Wählen Sie **[!UICONTROL Erstellen]**. Ein Design wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt. Auswählen **[!UICONTROL Öffnen]** , um das neu erstellte Design in einer neuen Registerkarte zu öffnen. Das Design wird im Design-Editor geöffnet. Zum Festlegen des Designs verwendet der Design-Editor ein sofort einsatzbereites adaptives Formular, das mit AEM [!DNL Forms] mitgeliefert wird.

   Informationen zur Verwendung der Benutzeroberfläche des Design-Editors finden Sie unter [Informationen zum Design-Editor](/help/forms/using/themes.md#aboutthethemeeditor).

1. Auswählen **[!UICONTROL Designoptionen]** ![theme-options](assets/theme-options.png) > **[!UICONTROL Konfigurieren]**. Im **[!UICONTROL Vorschau des Formulars]** ein, wählen Sie die **shipping-address-add-update-form** adaptives Formular, auswählen ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png)auswählen **[!UICONTROL Speichern]**. Jetzt ist der Design-Editor konfiguriert, um Ihr eigenes adaptives Formular anstelle des adaptiven Standardformulars zu benutzen. Auswählen **[!UICONTROL Abbrechen]** , um zum Design-Editor zurückzukehren.

   ![custom-theme](assets/custom-theme.png)

   **Abbildung:** *Design-Editor mit dem adaptiven Formular „shipping-address-add-update-form“*

   ![create-a-theme](assets/create-a-theme.png)

   **Abbildung:** *Adaptives Formular mit dem Standardformular*

### Gestalten einer Kopf- und Fußzeile {#style-header-and-footer}

Kopf- und Fußzeile bieten ein konsistentes und unverwechselbares Erscheinungsbild für ein adaptives Formular. Im Allgemeinen enthält die Kopfzeile das Logo und den Namen der Organisation, während die Fußzeile Copyright-Informationen enthält. Diese Angaben bleiben in unterschiedlichen Formularen einer Organisation identisch. So gestalten Sie die Kopf- und Fußzeile des adaptiven Formulars „shipping-address-add-update-form“:

1. Navigieren Sie zur Option **[!UICONTROL Kopfzeile]** > **[!UICONTROL Text]** im Bedienfeld „Selektoren“. Das Bedienfeld „Selektoren“ befindet sich auf der linken Seite des Design-Editors. Wenn das Bedienfeld nicht sichtbar ist, wählen Sie ![Umschalten des Seitenbereichs](assets/toggle-side-panel.png) Seitliches Bedienfeld ein/aus.

1. Legen Sie die folgenden Eigenschaften in der **[!UICONTROL Text]** Akkordeon und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | Schriftfamilie | Arial® |
   | Schriftfarbe | FFFFFF |
   | Schriftgrad | 54 px |

1. Wählen Sie die [!UICONTROL header] Widget und auswählen **[!UICONTROL Kopfzeile]**. Die Optionen zum Formatieren des Kopfzeilen-Widgets werden auf der linken Seite angezeigt. Erweitern Sie die **[!UICONTROL Dimensionen und Position]** Akkordeon festlegen **[!UICONTROL Höhe]** nach `120px`und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).
1. Erweitern Sie das Akkordeon **[!UICONTROL Hintergrund]** des Kopfzeilen-Widgets und legen Sie für die **[!UICONTROL Hintergrundfarbe]** `F6921E.` fest.

   Bewegen **[!UICONTROL Bild und Verlauf]** > **[!UICONTROL + Hinzufügen]** auswählen **[!UICONTROL Bild]**. Legen Sie die folgenden Eigenschaften fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   | Eigenschaft | Wert |
   |---|---|
   | image | Laden Sie die Datei „header-style.png“ hoch. Das Bild wurde im Abschnitt [Bevor Sie beginnen](/help/forms/using/style-your-adaptive-form.md#before-you-start) heruntergeladen. |
   | Position | Rechts unten |
   | Kachelung | Keine Wiederholung |

1. Wählen Sie im Design-Editor das Logo in der Kopfzeile aus und wählen Sie **[!UICONTROL Kopfzeilenlogo]**. Erweitern Sie das Akkordeon Dimensionen &amp; Position , legen Sie die folgenden Eigenschaften fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
        <li>Oben: 1,5 rem</li> 
        <li>Unten: -35 px</li> 
        <li>Links: 1rem<strong><br /> </strong></li> 
       </ul> <p><strong>Tipp:</strong> Wählen Sie die <img src="assets/link.png"> Verknüpfungssymbol, um für jedes Feld einen anderen Wert bereitzustellen.<br /> </p> </td> 
     </tr> 
     <tr> 
      <td>Höhe</td> 
      <td>4.75 rem</td> 
     </tr> 
    </tbody> 
   </table>

1. Wählen Sie das Fußzeilen-Widget aus und wählen Sie **[!UICONTROL Fußzeile]**. Erweitern Sie die **[!UICONTROL Hintergrund]** Akkordeon festlegen **[!UICONTROL Hintergrundfarbe]** nach `F6921E`und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

### Gestalten der Datenerfassungskomponente und Anwenden eines Hintergrunds auf das adaptive Formular {#style-the-data-capture-component-and-apply-a-background-to-the-adaptive-form}

Sie können mehrere Komponenten in einem adaptiven Formular verwenden, um Daten zu erfassen,  zum Beispiel ein Textfeld und ein numerisches Feld. Sie können für alle Datenerfassungskomponenten einen identischen Stil bereitstellen oder jeder Komponente einen eigenen Stil zuweisen.  In diesem Lernprogramm wird ein identischer Stil auf numerische Felder (Kunden-ID, Postleitzahl) und Textfelder (Kunden-ID, Name, Lieferadresse, Status, E-Mail) angewendet. So gestalten Sie die Datenerfassungskomponenten:

1. Wählen Sie die **[!UICONTROL Kunden-ID]** und wählen Sie die **[!UICONTROL Feld-Widget]** -Option. Legen Sie die folgenden Eigenschaften fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
        <li>Oben: 7 px<br /> </li> 
        <li>Rechts: 7 px<br /> </li> 
        <li>Unten: 7 px<br /> </li> 
        <li>Links: 7 px<br /> </li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfamilie</td> 
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>939598<br /> </td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18 px</td> 
     </tr> 
     <tr> 
      <td>Dimensionen und Position</td> 
      <td>Breite</td> 
      <td>60%</td> 
     </tr> 
     <tr> 
      <td>Dimensionen und Position</td> 
      <td>Rand</td> 
      <td> 
       <ul> 
        <li>Links: 10 rem</li> 
       </ul> </td> 
     </tr> 
    </tbody> 
    </table>

1. Wählen Sie den leeren Bereich über dem **[!UICONTROL Kunden-ID]** Feld und wählen Sie **[!UICONTROL Container für responsives Bedienfeld]**. Legen Sie den **[!UICONTROL Hintergrund]** > **[!UICONTROL Hintergrundfarbe]** auf F1F2F2 fest. Auswählen ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

   ![Responsiver Panel-Container](do-not-localize/responsive-panel-container.png)

### Gestalten Sie die Schaltflächen {#style-the-buttons}

Sie können ein benutzerdefiniertes Design verwenden, um allen Schaltflächen des adaptiven Formulars einen identischen Stil zuzuweisen, bzw. einen [Inline-Stil](/help/forms/using/inline-style-adaptive-forms.md), um einen Stil einer bestimmten Schaltfläche zuzuweisen. So gestalten Sie die Schaltflächen:

1. Wählen Sie die **[!UICONTROL Einsenden]** und wählen Sie die **[!UICONTROL Schaltfläche]** -Option. Legen Sie die folgenden Eigenschaften fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

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
        <li>Oben: 7 px<br /> </li> 
        <li>Rechts: 7 px<br /> </li> 
        <li>Unten: 7 px<br /> </li> 
        <li>Links: 7 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Text<br /> </td> 
      <td>Schriftfamilie</td> 
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>FFFFFF</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18 px</td> 
     </tr> 
    </tbody> 
   </table>

1. [Wenden Sie das benutzerdefinierte Design](/help/forms/using/style-your-adaptive-form.md#step-apply-a-theme-to-your-adaptive-form) „Globales Design“ auf Ihr adaptives Formular an. Wenn der Stil das adaptive Formular nicht widerspiegelt, bereinigen Sie den Browser-Cache und versuchen Sie es erneut. 

   ![style-data-collection-components](assets/style-data-capture-components.png)

## Schritt 4: Gestalten einzelner Komponenten {#step-style-individual-components}

Einige Stile gelten nur für eine bestimmte Komponente. Diese Komponenten werden im Editor für adaptive Formulare formatiert.

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten. [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)
1. Wählen Sie in der oberen Leiste die Option **[!UICONTROL Stil]**.

   ![style-option](assets/style-option.png)

1. Wählen Sie die **[!UICONTROL Attach]** und wählen Sie die ![aem_6_3_edit](assets/aem_6_3_edit.png)Symbol. Stellen Sie die folgenden Eigenschaften im Akkordeon **[!UICONTROL Abmessungen und Position]** ein:

   | Eigenschaft | Wert |
   |---|---|
   | Fließkommazahl | Linksbündig |
   | Breite | 10% |

1. Wählen Sie die **[!UICONTROL Von Behörden anerkannter Adressnachweis]** und wählen Sie die ![aem_6_3_edit](assets/aem_6_3_edit.png)Symbol. Legen Sie die folgenden Eigenschaften fest:

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
      <td>Linksbündig</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Breite</td> 
      <td>73%</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Padding</td> 
      <td> 
       <ul> 
        <li>Links: 10 px</li> 
       </ul> </td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position</td> 
      <td>Höhe</td> 
      <td>40 px</td> 
     </tr> 
     <tr> 
      <td>Abmessungen und Position<br /> </td> 
      <td>Rand</td> 
      <td><br /> 
       <ul> 
        <li>Rechts: 2 rem</li> 
        <li>Links: 10 rem </li> 
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
      <td>1 px</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenstil</td> 
      <td>Durchgehend</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenfarbe</td> 
      <td>A7A9AC</td> 
     </tr> 
     <tr> 
      <td>Rahmen</td> 
      <td>Rahmenradius</td> 
      <td>7 px</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfamilie</td> 
      <td>Arial®</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftfarbe</td> 
      <td>BCBEC0</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Schriftgrad</td> 
      <td>18 px</td> 
     </tr> 
     <tr> 
      <td>Text</td> 
      <td>Zeilenhöhe</td> 
      <td>2</td> 
     </tr> 
     </tr> 
    </tbody> 
   </table>

1. Wählen Sie die **[!UICONTROL Einsenden]** und wählen Sie die ![aem_6_3_edit](assets/aem_6_3_edit.png) Symbol. Legen Sie die folgenden Eigenschaften fest:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Akkordeon</b></td> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Dimensionen und Position</td> 
      <td>Fließkommazahl</td> 
      <td>Rechtsbündig</td> 
     </tr> 
     <tr> 
      <td>Dimensionen und Position</td> 
      <td>Rand</td> 
      <td> 
       <ul> 
        <li>Oben: 5 rem</li> 
        <li>Rechts: 14 rem</li> 
        <li>Unten: 20 px</li> 
        <li>Links: 20 px<br /> </li> 
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

## Schritt 5: Bonusabschnitt: Verwenden von Web Fonts in einem benutzerdefinierten Design {#step-bonus-section-using-web-fonts-in-a-custom-theme}

Sie können verschiedene Schriftarten verwenden, um ein adaptives Formular zu entwerfen. Möglicherweise sind die Schriftarten, die zum Entwerfen des adaptiven Formulars verwendet werden, nicht auf allen Geräten vorhanden, auf denen das adaptive Formular angezeigt wird. Sie können einen Webfont-Dienst verwenden, um die benötigten Schriftarten auf dem Zielgerät bereitzustellen.

[!DNL Adobe Fonts] ist solch ein Webfont-Dienst. Sie können den Dienst mit adaptiven Formularen konfigurieren und verwenden. So verwenden Sie [!DNL Adobe Fonts] in einem adaptiven Formular:

>[!NOTE]
>
>![typekit-to-adobe-fonts](assets/typekit-to-adobe-fonts.png) [!DNL Typekit] heißt jetzt Adobe Fonts und ist in Creative Cloud- und anderen Abonnements enthalten. [Weitere Informationen](https://fonts.adobe.com/)

1. Erstellen Sie ein [Adobe Fonts](https://fonts.adobe.com/?ref=tk.com)-Konto, erstellen Sie ein Kit, fügen Sie dem Kit die Schriftart Myriad Pro hinzu, veröffentlichen Sie das Kit und erhalten Sie die Kit-ID. In einem adaptiven Formular muss [!DNL Adobe Fonts] (Web Fonts) verwendet werden.
1. Navigieren Sie auf dem AEM [!DNL Forms]-Server zu ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Werkzeuge]** ![hammer](assets/hammer.png) > **[!UICONTROL Adobe Fonts]**. Öffnen Sie jetzt einen Konfigurationsordner. Wenn bereits eine Konfiguration zur Verfügung steht, klicken Sie auf die Schaltfläche **[!UICONTROL Erstellen]**, um eine neue Instanz zu erstellen.

   Geben Sie im Dialogfeld „Konfiguration erstellen“ einen **Titel** für die Konfiguration an und klicken Sie auf **[!UICONTROL Erstellen]**. Daraufhin werden Sie zur Seite „Konfiguration“ geleitet. Geben Sie im Dialogfeld [!UICONTROL Komponente bearbeiten], das angezeigt wird, Ihre **Kit-ID** ein und klicken Sie auf **[!UICONTROL OK]**.

1. Konfigurieren Sie Ihr Design für die Verwendung der [!DNL Adobe Fonts]-Konfiguration. Öffnen Sie in der Autorinstanz ein Design im Design-Editor **[!UICONTROL Globales Design]**. Navigieren Sie im Design-Editor zu **[!UICONTROL Themenoptionen]** ![Themenoptionen](assets/theme-options.png) > **[!UICONTROL Konfigurieren]**. Wählen Sie im Feld **[!UICONTROL Adobe Fonts-Konfiguration]** ein Kit aus und klicken Sie auf **[!UICONTROL Speichern]**.

   Die zu **[!UICONTROL Adobe Fonts]** hinzugefügten Schriftarten stehen im **[!UICONTROL Text]**-Akkordeon aller Komponenten zur Auswahl.
