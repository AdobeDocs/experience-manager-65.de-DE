---
title: Anwenden von Regeln in adaptiven Formularfelder
seo-title: Apply rules to adaptive form fields
description: Erstellen Sie Regeln, um einem adaptiven Formular Interaktivität, Geschäftslogik und intelligente Validierungen hinzuzufügen.
seo-description: Create rules to add interactivity, business logic, and smart validations to an adaptive form.
page-status-flag: de-activated
uuid: 60f142aa-81ca-4333-8614-85a01e23e917
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 982eddba-2350-40e7-8a42-db02d28cf133
exl-id: 0202ca65-21ef-4477-b704-7b52314a7d7b
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 55%

---

# Schulung: Wenden Sie Regeln auf adaptive Formularfelder an {#tutorial-apply-rules-to-adaptive-form-fields}

![06-apply-rules-to-adaptive-form_main](assets/06-apply-rules-to-adaptive-form_main.png)

Dieses Tutorial ist ein Teil der Serie [Erstellen Ihres ersten adaptives Formulars](/help/forms/using/create-your-first-adaptive-form.md). Adobe empfiehlt, der Reihe in chronologischer Abfolge zu folgen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, auszuführen und zu demonstrieren.

## Über das Tutorial {#about-the-tutorial}

Sie können Regeln verwenden, um einem adaptiven Formular Interaktivität, Geschäftslogik und intelligente Validierungen hinzuzufügen. Adaptive Formulare verfügen über einen integrierten Regeleditor. Der Regeleditor bietet eine Drag-and-Drop-Funktion, ähnlich wie bei geführten Touren. Die Drag &amp; Drop-Methode ist die schnellste und einfachste Methode zum Erstellen von Regeln. Der Regeleditor bietet außerdem ein Codefenster für Benutzer, die ihre Kodierungsfähigkeiten testen oder die Regeln auf die nächste Stufe bringen möchten.

Weitere Informationen zum Regeleditor finden Sie unter [Regeleditor für adaptive Forms](/help/forms/using/rule-editor.md).

Am Ende der Schulung lernen Sie Regeln zu erstellen, um Folgendes zu tun: 

* Rufen Sie einen Formulardatenmodelldienst auf, um Daten aus der Datenbank abzurufen
* Aufrufen eines Formulardatenmodelldienstes, um Daten zur Datenbank hinzuzufügen
* Ausführen einer Validierungsprüfung und Anzeigen von Fehlermeldungen

Interaktive GIF-Bilder am Ende jedes Abschnitts der Schulung helfen Ihnen dabei, die Funktionalität des Formulars, das Sie gerade erstellen, schnell zu lernen und zu validieren. 

## Schritt 1: Abrufen eines Kundendatensatzes aus der Datenbank {#retrieve-customer-record}

Sie haben ein Formulardatenmodell anhand der folgenden Schritte erstellt: [Formulardatenmodell erstellen](/help/forms/using/create-form-data-model.md) Artikel. Jetzt können Sie mit dem Regeleditor die Forms-Datenmodelldienste aufrufen, um Informationen abzurufen und zur Datenbank hinzuzufügen.

Jedem Kunden wird eine eindeutige Kunden-ID-Nummer zugewiesen, mit der relevante Kundendaten in einer Datenbank identifiziert werden können. Im folgenden Verfahren wird die Kunden-ID verwendet, um Informationen aus der Datenbank abzurufen:

1. Öffnen Sie Ihr adaptives Formular zum Bearbeiten.

   [http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html](http://localhost:4502/editor.html/content/forms/af/change-billing-shipping-address.html)

1. Tippen Sie auf das Feld **[!UICONTROL Kunden-ID]** und tippen Sie auf das Symbol **[!UICONTROL Regeln bearbeiten]**. Das Fenster „Regeleditor“ wird geöffnet.
1. Tippen Sie auf **[!UICONTROL + Erstellen]** -Symbol, um eine Regel hinzuzufügen. Dadurch wird der Visual Editor geöffnet.

   Im visuellen Editor ist die Anweisung **[!UICONTROL WHEN]** standardmäßig ausgewählt. Darüber hinaus wird das Formularobjekt (in diesem Fall **[!UICONTROL Kunden-ID]**), von dem aus Sie den Regeleditor gestartet haben, in der **[!UICONTROL WHEN]**-Anweisung angegeben.

1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL wurde geändert]**.

   ![whencustomeridischanged](assets/whencustomeridischanged.png)

1. Im **[!UICONTROL THEN]** Anweisung, auswählen **[!UICONTROL Aufrufdienst]** aus dem **[!UICONTROL Aktion auswählen]** angezeigt.
1. Wählen Sie die **[!UICONTROL Versandadresse abrufen]** -Dienst von **[!UICONTROL Auswählen]** angezeigt.
1. Ziehen Sie das Feld **[!UICONTROL Kunden-ID]** per Drag-and-Drop von der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** im **[!UICONTROL INPUT]**-Bereich.

   ![dropobjectstoinputfield-retrieveData](assets/dropobjectstoinputfield-retrievedata.png)

1. Ziehen Sie das Feld **[!UICONTROL Kunden-ID, Name, Versandadresse, Bundesland und Postleitzahl]** per Drag-and-Drop von der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** im Bereich **[!UICONTROL OUTPUT]**.

   ![dropobjectstooutputfield-retrieveData](assets/dropobjectstooutputfield-retrievedata.png)

   Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern. Tippen Sie im Fenster des Regeleditors auf **[!UICONTROL Schließen]**.

1. Zeigen Sie das adaptive Formular in der Vorschau an. Geben Sie eine ID in die **[!UICONTROL Kunden-ID]** -Feld. Das Formular kann jetzt Kundendetails aus der Datenbank abrufen.

   ![retrieve-information](assets/retrieve-information.gif)

## Schritt 2: Hinzufügen der aktualisierten Kundenadresse zur Datenbank {#updated-customer-address}

Nachdem die Kundendetails aus der Datenbank abgerufen wurden, können Sie die Lieferadresse, den Bundesstaat und die Postleitzahl aktualisieren. Das folgende Verfahren ruft einen Formulardatenmodelldienst auf, um Kundeninformationen in der Datenbank zu aktualisieren:

1. Wählen Sie das Feld **[!UICONTROL Senden]** und tippen Sie auf das Symbol **[!UICONTROL Regeln bearbeiten]**. Das Fenster „Regeleditor“ wird geöffnet.
1. Wählen Sie die Regel **[!UICONTROL Senden - Klicken]** und tippen Sie auf das Symbol **[!UICONTROL Bearbeiten]**. Die Optionen zum Bearbeiten der Senden-Regel werden angezeigt.

   ![submit-rule](assets/submit-rule.png)

   In der WHEN-Option sind die Optionen **[!UICONTROL Senden]** und **[!UICONTROL wurde angeklickt]** bereits ausgewählt.

   ![submit-is-clicked](assets/submit-is-clicked.png)

1. Im **[!UICONTROL THEN]** Tippen Sie auf die **[!UICONTROL + Anweisung hinzufügen]** -Option. Auswählen **[!UICONTROL Aufrufdienst]** aus dem **[!UICONTROL Aktion auswählen]** angezeigt.
1. Wählen Sie die **[!UICONTROL Versandadresse aktualisieren]** -Dienst von **[!UICONTROL Auswählen]** angezeigt.

   ![update-shipping-address](assets/update-shipping-address.png)

   ![dropobjectstoinputfield-updatedata](assets/dropobjectstoinputfield-updatedata.png)

1. Ziehen Sie das Feld **[!UICONTROL Versandadresse, Bundesland und Postleitzahl]** aus der Registerkarte [!UICONTROL Formularobjekte] auf die entsprechende Tabellennameneigenschaft (z. B. customerdetails.shippingAddress) des Feldes **[!UICONTROL Objekt hier einfügen oder auswählen]** im Bereich **[!UICONTROL INPUT]**. Alle Felder mit dem Präfix „tablename“ (in diesem Anwendungsbeispiel das Feld „customerdetails“) dienen als Eingabedaten für den Aktualisierungsservice. Der gesamte Inhalt in diesen Feldern wird in der Datenquelle aktualisiert.

   >[!NOTE]
   >
   >Ziehen Sie die Felder **[!UICONTROL Name]** und **[!UICONTROL Kunden-ID]** nicht auf die entsprechende tablename.property (z. B. customerdetails.name). Der Name und die ID des Kunden sollten nicht versehentlich aktualisiert werden.

1. Ziehen Sie das Feld **[!UICONTROL Kunden-ID]** per Drag-and-Drop von der Registerkarte [!UICONTROL Formularobjekte] in das Feld „ID“ im Feld **[!UICONTROL INPUT]**. Felder ohne vorangestellten Tabellennamen (in diesem Anwendungsbeispiel das Feld „customerdetails“) dienen als Suchparameter für den Aktualisierungsservice. Das Feld **[!UICONTROL ID]** in diesem Anwendungsfall identifiziert einen Datensatz in der Tabelle **customerdetails**.
1. Tippen Sie auf **[!UICONTROL Fertig]**, um die Regel zu speichern. Tippen Sie im Fenster des Regeleditors auf **[!UICONTROL Schließen]**.
1. Zeigen Sie das adaptive Formular in der Vorschau an. Rufen Sie Details zu einem Kunden ab, aktualisieren Sie die Lieferadresse und senden Sie das Formular. Wenn Sie die Details desselben Kunden erneut abrufen, wird die aktualisierte Versandadresse angezeigt.

## Schritt 3: (Abschnitt &quot;Bonus&quot;) Verwenden Sie den Code-Editor, um Überprüfungen auszuführen und Fehlermeldungen anzuzeigen. {#step-bonus-section-use-the-code-editor-to-run-validations-and-display-error-messages}

Sie sollten eine Validierung für das Formular durchführen, um sicherzustellen, dass die im Formular eingegebenen Daten korrekt sind und eine Fehlermeldung angezeigt wird, wenn falsche Daten vorliegen. Wenn beispielsweise eine nicht vorhandene Kunden-ID in das Formular eingegeben wird, sollte eine Fehlermeldung angezeigt werden.

Adaptive Formulare bieten mehrere Komponenten mit integrierten Validierungen, z. B. E-Mail und numerische Felder, die Sie für häufige Anwendungsfälle verwenden können. Verwenden Sie den Regeleditor für erweiterte Anwendungsfälle, um z. B. eine Fehlermeldung anzuzeigen, wenn die Datenbank null (0) Datensätze (keine Datensätze) zurückgibt. 

Das folgende Verfahren zeigt, wie eine Regel erstellt wird, um eine Fehlermeldung anzuzeigen, wenn die im Formular eingegebene Kunden-ID nicht in der Datenbank vorhanden ist. Die Regel bringt auch den Fokus auf das Feld **[!UICONTROL Kunden-ID]** und setzt es zurück. Die Regel verwendet [die dataIntegrationUtils-API des Formulardatenmodell-Services](/help/forms/using/invoke-form-data-model-services.md), um zu überprüfen, ob die Kunden-ID in der Datenbank vorhanden ist.

1. Tippen Sie auf das Feld **[!UICONTROL Kunden-ID]** und dann auf das Symbol `Edit Rules`. Das Fenster [!UICONTROL Regeleditor] wird geöffnet.
1. Tippen Sie auf **[!UICONTROL + Erstellen]** -Symbol, um eine Regel hinzuzufügen. Dadurch wird der Visual Editor geöffnet.

   Im visuellen Editor ist die Anweisung **[!UICONTROL WHEN]** standardmäßig ausgewählt. Darüber hinaus wird das Formularobjekt (in diesem Fall **[!UICONTROL Kunden-ID]**), von dem aus Sie den Regeleditor gestartet haben, in der **[!UICONTROL WHEN]**-Anweisung angegeben.

1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Status auswählen]** und wählen Sie **[!UICONTROL wurde geändert]**.

   ![whencustomeridischanged](assets/whencustomeridischanged.png)

   Im **[!UICONTROL THEN]** Anweisung, auswählen **[!UICONTROL Aufrufdienst]** aus dem **[!UICONTROL Aktion auswählen]** angezeigt.

1. Zwischen **[!UICONTROL Visual Editor]** nach **[!UICONTROL Code-Editor]**. Die Umschalttaste befindet sich rechts im Fenster. Der Code-Editor wird geöffnet und zeigt Code ähnlich dem folgenden an:

   ![code-editor](assets/code-editor.png)

1. Ersetzen Sie den Eingabevariablenabschnitt durch den folgenden Code:

   ```javascript
   var inputs = {
       "id" : this
   };
   ```

1. Ersetzen Sie den Abschnitt `guidelib.dataIntegrationUtils.executeOperation (operationInfo, inputs, outputs)` durch den folgenden Code:

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, function (result) {
     if (result) {
         result = JSON.parse(result);
       customer_Name.value = result.name;
       customer_Shipping_Address = result.shippingAddress;
     } else {
       if(window.confirm("Invalid Customer ID. Provide a valid customer ID")) {
             customer_Name.value = " ";
            guideBridge.setFocus(customer_ID);
       }
     }
   });
   ```

1. Zeigen Sie das adaptive Formular in der Vorschau an. Geben Sie eine falsche Kunden-ID ein. Eine Fehlermeldung wird angezeigt.

   ![display-validation-error](assets/display-validation-error.gif)
