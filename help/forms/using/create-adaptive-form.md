---
title: '„Tutorial: Erstellen eines adaptiven Formulars“'
description: Lernen Sie, ein adaptives Formular zu erstellen, zu gestalten und in der Vorschau anzuzeigen.  Informieren Sie sich auch über das Konfigurieren von Sendeaktionen.
feature: Adaptive Forms
exl-id: c0a2adcd-528a-41af-99b5-d8b423cd6605
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '1314'
ht-degree: 100%

---

# Schulung: Erstellen eines adaptiven Formulars {#do-not-publish-tutorial-create-an-adaptive-form}

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Dieses Tutorial ist ein Teil der Serie [Erstellen Ihres ersten adaptives Formulars](/help/forms/using/create-your-first-adaptive-form.md). Es wird empfohlen, die Serie in chronologischer Reihenfolge zu durchlaufen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, durchzuführen und zu demonstrieren.

## Über das Tutorial {#about-the-tutorial}

Adaptive Formulare sind Formulare der neuen Generation, die dynamisch und responsiv sind. Sie können adaptive Formulare verwenden, um ein personalisiertes Benutzererlebnis zu schaffen. Außerdem können Sie adaptive Formulare mit [!DNL Adobe Analytics] für Nutzungsstatistiken und mit [!DNL Adobe Campaign] für das Kampagnen-Management integrieren. Weitere Informationen zu den Funktionen adaptiver Formulare finden Sie unter [Einführung in das Bearbeiten adaptiver Formulare](/help/forms/using/introduction-forms-authoring.md).

Es ist einfacher, Formulare zu erstellen und zu verwalten, wenn ein ordnungsgemäßer Prozess eingehalten wird. In diesem Artikel lernen Sie Folgendes: 

* [Erstellen Sie ein adaptives Formular, mit dem ein Kunde eine Versandadresse hinzufügen kann](/help/forms/using/create-adaptive-form.md#step-create-the-adaptive-form)

* [Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden](/help/forms/using/create-adaptive-form.md#step-add-header-and-footer)

* [Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt](/help/forms/using/create-adaptive-form.md#step-add-components-to-capture-and-display-information)
* [Anzeigen und Senden eines adaptiven Formulars in der Vorschau](/help/forms/using/create-adaptive-form.md)

Am Ende des Artikels haben Sie ein Formular, was so ähnlich wie Folgendes aussieht:\
[![Formularvorschau auf einem Mobilgerät](do-not-localize/form-preview-mobile.gif)](do-not-localize/form-preview-mobile.gif)

## Schritt 1: Adaptives Formular erstellen {#step-create-the-adaptive-form}

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**. Die Standard-URL lautet [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).
1. Wählen Sie **[!UICONTROL Erstellen]** und dann **[!UICONTROL Adaptives Formular]** aus. Eine Option zum Auswählen einer Vorlage wird angezeigt. Wählen Sie die **[!UICONTROL leere]** Vorlage und dann **[!UICONTROL Weiter]** aus.

1. Eine Option **[!UICONTROL Eigenschaften hinzufügen]** wird angezeigt. Die Felder **[!UICONTROL Titel]** und **[!UICONTROL Name]** sind obligatorisch.

   * **Titel:** Geben Sie `Add new or update shipping address` im Feld **[!UICONTROL Titel]** an. Das Feld „Titel“: Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von AEM [!DNL Forms].
   * **Name:** Geben Sie `shipping-address-add-update-form` in das Feld **[!UICONTROL Name]** ein. Das Feld „Name“ gibt den Namen des Formulars an.  Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.

1. Wählen Sie **[!UICONTROL Erstellen]**. Es wird ein adaptives Formular erstellt und ein Dialogfeld zum Öffnen der Formularbearbeitung angezeigt.
 Wählen Sie **[!UICONTROL Öffnen]** aus, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet.  Es zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Weitere Informationen zur Authoring-Oberfläche für adaptive Formulare und zu verfügbaren Komponenten finden Sie in der [Einführung in das Authoring adaptiver Formulare](/help/forms/using/creating-adaptive-form.md).

   ![Ein neu erstelltes adaptives Formular](assets/newly-created-adaptive-form.png)

## Schritt 2: Kopf- und Fußzeile hinzufügen {#step-add-header-and-footer}

AEM [!DNL Forms] bietet viele Komponenten zum Anzeigen von Informationen in einem adaptiven Formular. Kopfzeilen- und Fußzeilen-Komponenten sorgen für ein konsistentes Erscheinungsbild eines Formulars.  Eine Kopfzeile enthält normalerweise das Logo eines Unternehmens, den Titel des Formulars und eine Zusammenfassung.  Eine Fußzeile enthält meist Copyright-Informationen und Links zu anderen Seiten.

1. Wählen Sie ![toggle-side-panel](assets/toggle-side-panel.png) > ![treeexpandall](assets/treeexpandall.png) aus. Der Komponentenbrowser wird geöffnet. Ziehen Sie die Komponente **[!UICONTROL Kopfzeile]** aus dem Komponentenbrowser in das adaptive Formular.
1. Wählen Sie **[!UICONTROL Logo]** aus. Die Symbolleiste wird angezeigt.  Wählen Sie in der Symbolleiste ![aem_6_3_edit](assets/aem_6_3_edit.png) aus. Geben Sie **We.Retail** ein und wählen Sie anschließend ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.

1. Wählen Sie ein Bild aus. Die Symbolleiste wird angezeigt.  Wählen Sie ![cmppr](assets/cmppr.png) aus. Der Eigenschaften-Browser wird auf der linken Seite des Bildschirms geöffnet. **[!UICONTROL Suchen Sie]** das Logo und laden Sie es hoch. Wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus. Das Bild erscheint in der Kopfzeile.

   Sie können „Datei abrufen“ auswählen, um das in diesem Artikel verwendete Logo herunterzuladen, falls Sie keines haben.

[Datei laden](assets/logo.png)

1. Ziehen Sie die Komponente **[!UICONTROL Fußzeile]** aus ![treeexpandall](assets/treeexpandall.png) in das adaptive Formular. Nach diesem Schritt sieht das Formular wie folgt aus:

   ![adaptive-form-with-headers-and-footers](assets/adaptive-form-with-headers-and-footers.png)

## Schritt 3: Komponenten hinzufügen, um Informationen zu erfassen und anzuzeigen {#step-add-components-to-capture-and-display-information}

Komponenten sind Bausteine &#x200B;&#x200B;eines adaptiven Formulars. AEM [!DNL Forms] bietet viele Komponenten zum Erfassen und Anzeigen von Informationen in einem adaptiven Formular. Sie können die Komponenten von ![treeexpandall](assets/treeexpandall.png) in ein Formular ziehen. Informationen zu verfügbaren Komponenten und entsprechenden Funktionen finden Sie in [Einführung in die Bearbeitung von adaptiven Formularen](/help/forms/using/introduction-forms-authoring.md). 

1. Ziehen Sie die **[!UICONTROL numerische Feldkomponente]** in das adaptive Formular. Platzieren Sie sie vor der Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente. Ändern Sie den **[!UICONTROL Titel]** der Komponente in **`Customer ID`** und den **[!UICONTROL Elementnamen]** in **`customer_ID`**. Aktivieren Sie die Option **[!UICONTROL Erforderliches Feld]**, aktivieren Sie die Option **[!UICONTROL HTML5-Zahleneingabetyp verwenden]** und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.
1. Ziehen Sie drei Textfeldkomponenten in das adaptive Formular.  Platzieren Sie diese vor die Fußzeilenkomponente.  Legen Sie die folgenden Eigenschaften für diese Textfelder fest.:

   <table> 
    <tbody> 
     <tr> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Textfeld 1<br/></b></td> 
      <td><b>Textfeld 2<br/></b></td> 
      <td><b>Textfeld 3</b></td> 
     </tr> 
     <tr> 
      <td>Titel</td> 
      <td>Name<br /> </td> 
      <td>Lieferadresse</td> 
      <td>Status</td> 
     </tr> 
     <tr> 
      <td>Elementname</td> 
      <td>customer_Name<br /> </td> 
      <td>customer_Shipping_Address</td> 
      <td>customer_State</td> 
     </tr> 
     <tr> 
      <td>Erforderliches Feld</td> 
      <td>Aktiviert</td> 
      <td>Aktiviert</td> 
      <td>Aktiviert</td> 
     </tr> 
     <tr> 
      <td>Mehrere Zeilen zulassen<br /> </td> 
      <td>Deaktiviert</td> 
      <td>Aktiviert</td> 
      <td>Deaktiviert</td> 
     </tr> 
    </tbody> 
   </table>

1. Ziehen Sie eine **[!UICONTROL Numerisches Feld]**-Komponente vor die Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführten Werte fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.

   | Eigenschaft | Wert |
   |---|---|
   | Titel | Postleitzahl |
   | Elementname | customer_ZIPCode |
   | Maximale Anzahl von Ziffern | 6 |
   | Erforderliches Feld | Aktiviert |
   | Mustertyp anzeigen | Kein Muster |

1. Ziehen Sie eine **[!UICONTROL E-Mail]**-Komponente vor die Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführten Werte fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.

   | Eigenschaft | Wert |
   |---|---|
   | Titel | E-Mail |
   | Elementname | customer_Email |
   | Erforderliches Feld | Aktiviert |

1. Ziehen Sie eine **[!UICONTROL Dateianhang]**-Komponente vor die Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, legen Sie die in der folgenden Tabelle aufgeführten Werte fest und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.

   <table> 
    <tbody> 
     <tr> 
      <td><b>Eigenschaft</b></td> 
      <td><b>Wert</b></td> 
     </tr> 
     <tr> 
      <td>Titel</td> 
      <td>Von Behörden anerkannter Adressnachweis<br /> </td> 
     </tr> 
     <tr> 
      <td>Elementname</td> 
      <td>customer_Address_Proof</td> 
     </tr> 
     <tr> 
      <td>Erforderliches Feld</td> 
      <td>Aktiviert</td> 
     </tr> 
    </tbody> 
   </table>

1. Ziehen Sie eine **[!UICONTROL Sendeschaltfläche]**-Komponente in das adaptive Formular. Platzieren Sie sie vor der Fußzeilenkomponente. Öffnen Sie die Eigenschaften der Komponente, ändern Sie den Elementnamen in `address_addition_update_submit` und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus. Das Layout des Formulars ist vollständig und das Formular sieht wie folgt aus:

   ![adaptive-form-with-all-the-components](assets/adaptive-form-with-all-the-components.png)

## Schritt 4: Sendeaktion für das adaptive Formular konfigurieren {#step-configure-submit-action-for-the-adaptive-form}

Eine Sendeaktion wird ausgelöst, wenn Benutzende in einem adaptiven Formular auf die Schaltfläche „Absenden“ klicken.  Sie können eine Sendeaktion verwenden, um Formulardaten im lokalen Repository zu speichern, Formulardaten an einen REST-Endpunkt zu senden, Formulardaten als E-Mail zu senden und mehr. Adaptive Formulare bieten einige weitere vordefinierte Sendeaktionen. Ausführliche Informationen finden Sie unter [Konfigurieren der Sendeaktion](/help/forms/using/configuring-submit-actions.md).

Mit den folgenden Schritten können Sie die E-Mail-Sendeaktion und die Demo-Sendeaktion des Formulars konfigurieren:

1. Konfigurieren Sie den E-Mail-Server. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen.](/help/sites-administering/notification.md).


1. Wählen Sie im Inhalts-Browser **[!UICONTROL Formular-Container]** und dann ![cmppr](assets/cmppr.png) aus. Der Eigenschaften-Browser wird auf der linken Seite geöffnet.
1. Navigieren Sie zu **[!UICONTROL Übermittlung]** > **[!UICONTROL Übermittlungsaktion]**. Wählen Sie **[!UICONTROL E-Mail senden]**. Geben Sie die folgenden Werte an und wählen Sie ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) aus.

   | Eigenschaft | Wert |
   |--- |--- |
   | Von | `donotreply@weretail.com` |
   | To | `${customer_Email}` |
   | Betreff | Bestätigung: Sie haben die Lieferadresse auf der We.Retail-Website hinzugefügt. |
   | E-Mail-Vorlage | Hallo `${customer_Name}`, die folgende Adresse wurde als Lieferadresse für Ihr Konto hinzugefügt: <br>`${customer_Name}`, `${customer_Shipping_Address}`, `${customer_State}`, `${customer_ZIPCode}`<br> Mit freundlichen Grüßen, We.Retail |
   | Anhänge einfügen | Aktiviert |

   Ihr Formular ist fertig. Jetzt können Sie eine Vorschau des Formulars anzeigen und die Funktionalität testen. Wenn Sie den im Tutorial genannten Namen verwendet haben und das Formular auf dem Rechner mit dem AEM [!DNL Forms]-Server aufrufen, dann ist das Formular unter [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html) verfügbar.

## Schritt 5: Adaptives Formular in der Vorschau ansehen und senden {#step-preview-and-submit-the-adaptive-form}

Sie können die Option **[!UICONTROL Vorschau]** verwenden, um das Erscheinungsbild und Verhalten eines Formulars zu bewerten. Sie können ein Formular im Vorschaumodus absenden und auch die auf ein Formular angewendeten Validierungen überprüfen. Zum Beispiel, wenn ein Fehler angezeigt wird, weil ein Pflichtfeld leer gelassen wurde.

Adaptive Formulare bieten auch eine Option zum Emulieren von Erlebnissen eines Formulars für verschiedene Geräte. Beispiel: iPhone, iPad und Desktop. Sie können die beiden Optionen **[!UICONTROL Vorschau]** und **[!UICONTROL Emulator]**-![Lineal](assets/ruler.png) in Verbindung miteinander verwenden, um eine Vorschau eines Formulars für Geräte mit unterschiedlichen Bildschirmgrößen anzuzeigen.

1. Wählen Sie die Option **[!UICONTROL Vorschau]** auf der rechten Seite des Formulareditors aus. Das Formular wird im Bearbeitungsmodus geöffnet. Wenn Sie den Namen verwendet haben, der in der Schulung benutzt wird, dann lautet die Vorschau-URL des Formulars [http://localhost:4502/content/dam/formsanddocuments/shipping-address-add-update-form/jcr:content?wcmmode=disabled](http://localhost:4502/content/dam/formsanddocuments/shipping-address-addition-updation-form/jcr:content?wcmmode=disabled)
1. Verwenden Sie ![Lineal](assets/ruler.png), um zu sehen, wie das Formular auf verschiedenen Geräten aussieht.
1. Füllen Sie die Formularfelder aus und wählen Sie **[!UICONTROL Absenden]** aus. Das Formular wird abgesendet und Sie werden zur standardmäßigen **Dankeschön**-Seite weitergeleitet. Sie können auch eine benutzerdefinierte Dankeschön-Seite angeben. Einzelheiten finden Sie unter [Konfigurieren der Weiterleitungsseite](/help/forms/using/configuring-redirect-page.md).

Das adaptive Formular zum Hinzufügen einer Adresse ist fertig. Wenn Sie den im Tutorial genannten Namen verwendet haben und auf das Formular auf dem Computer zugreifen, auf dem der AEM Forms-Server ausgeführt wird, ist das Formular unter [http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html](http://localhost:4502/editor.html/content/forms/af/shipping-address-add-update-form.html) verfügbar.
