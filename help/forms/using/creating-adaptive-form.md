---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit  [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind Responsive-HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells, einer XFA-Formularvorlage und eines XML- oder JSON-Schemas.
feature: Adaptive Forms
role: User, Developer
level: Beginner
exl-id: 2c25a8b7-73f7-40fb-a303-9446a708c8eb
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '1923'
ht-degree: 54%

---

# Erstellen eines adaptiven Formulars {#creating-an-adaptive-form}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Erstellen eines adaptiven Formulars {#strong-create-an-adaptive-form-strong}

Führen Sie die folgenden Schritte aus, um ein adaptives Formular zu erstellen.

1. Zugreifen auf die [!DNL Experience Manager Forms]-Autoreninstanz unter `https://'[server]:[port]'/<custom-context-if-any>.`

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein.

   Nachdem Sie angemeldet sind, wählen Sie links oben die Option **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**.

   >[!NOTE]
   >
   >Bei einer Standardinstallation lautet der Benutzername `admin` und das Kennwort `admin`.

1. Auswählen **[!UICONTROL Erstellen]** und wählen **[!UICONTROL Adaptives Formular]**.
1. Eine Option zum Auswählen einer Vorlage wird angezeigt. Weitere Informationen zu Vorlagen finden Sie unter [Adaptive Formularvorlagen](creating-adaptive-form.md#p-adaptive-form-templates-p). Wählen Sie eine Vorlage aus, um sie auszuwählen, und wählen Sie Weiter aus.
1. Die Option „Eigenschaften hinzufügen“ wird angezeigt. Geben Sie die Werte für die folgenden Eigenschaftenfelder an. Die Felder „Titel“ und „Name“ sind obligatorisch.

   * **[!UICONTROL Titel:]** Gibt den Anzeigenamen des Formulars an. Der Titel erleichtert Ihnen die Identifizierung des Formulars in der Benutzeroberfläche von [!DNL Experience Manager Forms].
   * **[!UICONTROL Name:]** Gibt den Namen des Formulars an. Im Repository wird ein Knoten mit dem angegebenen Namen erstellt. Wenn Sie mit der Eingabe des Titels beginnen, wird automatisch ein Wert für das Feld „Name“ vorgeschlagen. Sie können den vorgeschlagenen Wert gegebenenfalls ändern. Im Feld „Name“ dürfen nur alphanumerische Zeichen, Bindestriche und Unterstriche eingegeben werden. Alle ungültigen Eingaben werden durch Bindestriche ersetzt.
   * **[!UICONTROL Beschreibung:]** Gibt detaillierte Informationen zum Formular an.
   * **[!UICONTROL Tags:]** Gibt Tags an, die eine eindeutige Identifizierung des adaptiven Formulars ermöglichen. Tags erleichtern die Suche nach dem Formular. Um die Tags zu erstellen, geben Sie neue Tag-Namen in das Feld **[!UICONTROL Tags]** ein.

1. Sie können ein adaptives Formular erstellen, das auf den folgenden Formularmodellen basiert:

   * [Formulardatenmodell](#fdm)
   * [XFA-Formularvorlage ](#create-an-adaptive-form-based-on-an-xfa-form-template)
   * [XML- oder JSON-Schema](#create-an-adaptive-form-based-on-xml-or-json-schema)
   * Keine oder ohne Formularmodell

   Sie können diese auf der Registerkarte **[!UICONTROL Formularmodell]** konfigurieren. Sie befindet sich auf der Seite **[!UICONTROL Eigenschaften hinzufügen]**. Standardmäßig ist das ausgewählte Formularmodell **[!UICONTROL Keines]**.

1. Wählen Sie **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

   Sobald Sie alle Eigenschaften angegeben haben, klicken Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

   Sobald Sie alle Eigenschaften angegeben haben, klicken Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

1. Auswählen **[!UICONTROL Öffnen]** , um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet und zeigt die in der Vorlage verfügbaren Inhalte an. Er zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltbrowsers]** in der Seitenleiste die Formularelemente angezeigt, die in der zugeordneten XFA-Formularvorlage, dem XML-Schema oder JSON-Schema vorhanden sind. Sie können diese Elemente auch per Drag &amp; Drop verschieben, um Ihr adaptives Formular zu erstellen.

   Informationen zur Authoring-Oberfläche für adaptive Formulare und zu verfügbaren Komponenten finden Sie unter [Einführung in das Authoring adaptiver Formulare](introduction-forms-authoring.md).

   >[!NOTE]
   >
   >Lassen Sie Popup-Fenster in Ihrem Browser zu, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen.

## Erstellen eines adaptiven Formulars basierend auf einem Formulardatenmodell {#fdm}

Durch die [[!DNL Experience Manager Forms] Datenintegration](data-integration.md) können Sie mehrere Datenquellen integrieren, ihre Entitäten und Services zusammenführen und so ein Formulardatenmodell erstellen. Dabei handelt es sich um eine Erweiterung des JSON-Schemas. Sie können ein Formulardatenmodell verwenden, um ein adaptives Formular zu erstellen. Die in einem Formulardatenmodell konfigurierten Entitäten oder Datenmodellobjekte sind als Datenmodellobjekte für die Formularbearbeitung verfügbar. Sie sind an die jeweiligen Datenquellen gebunden und werden verwendet, um ein Formular vorauszufüllen und die übermittelten Daten zurück in die entsprechenden Datenquellen zu schreiben. Sie können auch Services aufrufen, die in einem Formulardatenmodell mit Regeln für adaptive Formulare konfiguriert sind.

So verwenden Sie ein Formulardatenmodell zum Erstellen eines adaptiven Formulars:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Auswählen aus]**.

   ![Create-af-1-1](assets/create-af-1-1.png)

1. Zum Erweitern auswählen **[!UICONTROL Formulardatenmodell auswählen]**. Alle verfügbaren Formulardatenmodelle werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![Create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>Sie können das Formulardatenmodell für ein adaptives Formular auch ändern. Anweisungen hierfür finden Sie unter [Bearbeiten von Formularmodelleigenschaften eines adaptiven Formulars](#edit-form-model).

## Erstellen eines adaptiven Formulars basierend auf einer XFA-Formularvorlage {#create-an-adaptive-form-based-on-an-xfa-form-template}

Sie können Ihre XFA-Formularvorlagen erneut verwenden, um adaptive Formulare zu erstellen. Laden Sie zu diesem Zweck eine XFA-Formularvorlage hoch und verknüpfen Sie sie mit einem adaptiven Formular. Die Elemente der Formularvorlage (XFA-Formular) werden zum Zeitpunkt des Authoring adaptiver Formulare zur Verwendung in der Inhaltssuche bereitgestellt. Sie können die Formularvorlagenelemente per Drag &amp; Drop aus der Inhaltssuche in das Formular ziehen.

<!-- >>[!NOTE]
>
>[Upload the XFA Form Template](get-xdp-pdf-documents-aem.md) to AEM Forms before you start creating an adaptive form based on the form template.

Do the following to use an XFA form template as form model for your adaptive form:

1. On the **[!UICONTROL Add Properties]** page, open the **[!UICONTROL Form Model]** tab.
1. In the Form Model tab, from the drop-down list, select **[!UICONTROL Form Templates]**. All the form templates that are uploaded to the repository via AEM Forms UI are listed for selection. Select a template from the list.

   ![Associate XFA Form Template with an Adaptive Form](assets/form_model_xfa_associate.png)
**Figure:** *Selecting a form template*

   >[!NOTE]
   >
   >You can also change the form template for an adaptive form. For detailed steps, see [Edit Form Model properties of an adaptive form](#edit-form-model). -->

## Erstellen eines adaptiven Formulars basierend auf einem XML- oder JSON-Schema {#create-an-adaptive-form-based-on-xml-or-json-schema}

XML- und JSON-Schemas stellen die Struktur dar, in der Daten vom Back-End-System in Ihrer Organisation produziert oder genutzt werden. Sie können ein Schema mit einem adaptiven Formular verknüpfen und dem adaptiven Formular mithilfe der Elemente aus dem Schema dynamische Inhalte hinzufügen. Die Elemente des Schemas stehen auf der Registerkarte „Datenmodellobjekt“ des Inhalts-Browsers für das Erstellen von adaptiven Formularen zur Verfügung. Sie können die Schemaelemente zum Erstellen des Formulars ziehen und ablegen.

In den folgenden Dokumenten erfahren Sie, wie Sie ein XML- oder JSON-Schema für das Authoring adaptiver Formulare entwerfen.

* [Adaptive Formulare mithilfe des XML-Schemas erstellen](adaptive-form-xml-schema-form-model.md)
* [Erstellen adaptiver Formulare mithilfe eines JSON-Schemas](adaptive-form-json-schema-form-model.md)

Führen Sie folgende Schritte aus, um ein XML- oder JSON-Schema als Formularmodell für ein adaptives Formular zu verwenden:

1. Im **[!UICONTROL Eigenschaften hinzufügen]** Schritt der Seite zur Erstellung eines adaptiven Formulars, wählen Sie auf der **[!UICONTROL Formularmodell]** Registerkarte.
1. Wählen Sie auf der Registerkarte „Formularmodell“ **[!UICONTROL Schema]** aus dem Dropdown-Feld **[!UICONTROL Auswählen]**.

1. Auswählen **[!UICONTROL Schema auswählen]** und führen Sie einen der folgenden Schritte aus:

   * **[!UICONTROL Hochladen von der Festplatte]** - Wählen Sie diese Option aus und wählen Sie Schema-Definition hochladen , um ein XML-Schema oder JSON-Schema aus Ihrem Dateisystem zu durchsuchen und hochzuladen. Die hochgeladene Schemadatei befindet sich im Formular und ist für andere adaptive Formulare nicht zugänglich.
   * **[!UICONTROL Im Repository suchen]** - Wählen Sie diese Option aus der Liste der Schemadefinitionsdateien, die im Repository verfügbar sind. Wählen Sie die XML- oder JSON-Schemadatei als Formularmodell aus. Das ausgewählte Schema wird dem Formular per Verweis zugeordnet und kann für andere adaptive Formulare verwendet werden.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass der Dateiname des JSON-Schemas mit **.schema.json**. Beispiel: mySchema.schema.json

   ![Auswählen eines XML- oder JSON-Schemas](assets/upload-schema.png)
   **Abbildung:** *Auswählen eines XML- oder JSON-Schemas*

1. (Nur für XML-Schema) Nachdem Sie ein XML-Schema ausgewählt oder hochgeladen haben, geben Sie ein Stammelement der ausgewählten XSD-Datei an, das mit dem adaptiven Formular zugeordnet werden soll.

   ![Auswählen eines XSD-Stammelements](assets/xsd-root-element.png)
   **Abbildung:** *XSD-Stammelement auswählen*

>[!NOTE]
>
>Sie können das Schema für ein adaptives Formular ändern. Anweisungen hierfür finden Sie unter [Bearbeiten von Formularmodelleigenschaften eines adaptiven Formulars](#edit-form-model).

## Adaptive Formularvorlagen {#adaptive-form-templates}

Eine Vorlage bietet eine Grundstruktur für adaptive Formulare und definiert deren Erscheinungsbild (Layouts und Stile). Es enthält vorformatierte Komponenten, die bestimmte Eigenschaften und Inhaltsstruktur enthalten. <!-- Out of the box, AEM Forms provides some adaptive form templates. To get the complete template package including advanced templates, you need to install the AEM Forms add-on package. For more information, see [Installing AEM Forms add-on package](installing-configuring-aem-forms-osgi.md).-->

Darüber hinaus können Sie mit dem Vorlagen-Editor eigene Vorlagen erstellen. Weitere Informationen zum Arbeiten mit Vorlagen finden Sie unter [Adaptive Formularvorlagen](template-editor.md).

>[!NOTE]
>
>Wenn Sie ein adaptives Formular öffnen, das mit der erweiterten Vorlage zur Bearbeitung erstellt wurde, wird eine Fehlermeldung angezeigt. Die erweiterte Vorlage verfügt über eine Signaturschritt-Komponente und Adobe Sign ist dafür standardmäßig aktiviert. Erstellen und wählen Sie eine [Adobe Sign-Cloud-Konfiguration](adobe-sign-integration-adaptive-forms.md) und [Signierer konfigurieren](working-with-adobe-sign.md#addsignerstoanadaptiveform) um den Fehler zu beheben.

## Formularmodelleigenschaften eines adaptiven Formulars bearbeiten {#edit-form-model}

Adaptive Formulare werden ohne Formularmodell (unter Verwendung der Option &quot;Keine&quot;für Formularmodell) oder mit einem Formularmodell wie einer Formularvorlage, einem XML-Schema oder einem JSON-Schema oder einem Formulardatenmodell erstellt. Sie können das Formularmodell für ein adaptives Formular von &quot;Ohne&quot;in ein anderes Formularmodell ändern. Für adaptive Formulare, die auf einem Formularmodell basieren, können Sie eine andere Formularvorlage, ein XML-Schema, ein JSON-Schema oder ein Formulardatenmodell für dasselbe Formularmodell auswählen. Sie können jedoch nicht zwischen Formularmodellen wechseln.

1. Wählen Sie das adaptive Formular aus und wählen Sie die **Eigenschaften** Symbol.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie eine der folgenden Vorgehensweisen.

   * Wenn das adaptive Formular ohne Formularmodell vorliegt, können Sie ein anderes Formularmodell auswählen und dementsprechend eine Formularvorlage, ein XML- oder JSON-Schema oder ein Formulardatenmodell auswählen.
   * Wenn das adaptive Formular auf einem Formularmodell basiert, können Sie eine andere Formularvorlage, ein XML- oder JSON-Schema oder ein Formulardatenmodell für dasselbe Formularmodell auswählen.

1. Auswählen **[!UICONTROL Speichern]** , um die Eigenschaften zu speichern.

## Adaptives Formular automatisch speichern {#auto-save-an-adaptive-form}

Standardmäßig werden die Inhalte eines adaptiven Formulars in einer Benutzeraktion gespeichert, z. B. durch Drücken der Schaltfläche &quot;Speichern&quot;. Sie können auch ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem Zeitintervall automatisch gespeichert wird. Die Option &quot;Automatisches Speichern&quot;ist in folgenden Bereichen hilfreich:

* Automatisches Speichern des Inhalts für anonyme und angemeldete Benutzer
* Inhalt eines Formulars ohne oder mit minimalem Benutzereingriff speichern
* Speichern von Inhalt eines Formulars basierend auf einem Benutzerereignis starten
* Wiederholtes Speichern des Formularinhalts nach einem bestimmten Zeitintervall

### Automatisches Speichern für ein adaptives Formular aktivieren {#enable-auto-save-for-an-adaptive-form}

Die Option „Automatisches Speichern“ ist standardmäßig nicht aktiviert. Sie können die Option „Automatisches Speichern“ über die Registerkarte „Automatisches Speichern“ eines adaptiven Formulars aktivieren. Die Registerkarte „Automatisches Speichern“ bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt &quot;Automatisches Speichern&quot;in den Eigenschaften zuzugreifen, wählen Sie eine Komponente aus und klicken Sie dann auf ![Feldebene](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und wählen Sie ![cmppr](assets/cmppr.png).
1. Im **[!UICONTROL Automatisches Speichern]** Abschnitt, **[!UICONTROL Aktivieren]** die Option &quot;Automatisches Speichern&quot;.
1. Im **[!UICONTROL Adaptives Formularereignis]** geben Sie 1 oder TRUE an, um das Formular automatisch zu speichern, wenn es in den Browser geladen wird. Sie können auch einen bedingten Ausdruck für ein Ereignis angeben, das, wenn es ausgelöst wird und &quot;true&quot;zurückgibt, mit dem Speichern des Formularinhalts beginnt.
1. Geben Sie den Trigger an. Das automatische Speichern wird basierend auf Ihrer Konfiguration ausgelöst. Ihre Optionen sind:

   * **[!UICONTROL Zeitbasiert:]** Wählen Sie diese Option, um den Inhalt anhand eines bestimmtes Zeitintervalls zu speichern.
   * **[!UICONTROL Ereignisbasiert:]** Wählen Sie diese Option, um den Inhalt beim Auslösen eines Ereignisses zu speichern.

   Wenn Sie einen Trigger auswählen, ist das Feld &quot;Strategiekonfiguration&quot;aktiviert. Das Feld &quot;Strategiekonfiguration&quot;ermöglicht Folgendes:

   * ein Zeitintervall angeben, wenn Sie **[!UICONTROL Zeitbasiert]** für den Auslöser wählen.
   * Den Namen des Ereignisses angeben, wenn Sie **[!UICONTROL Ereignisbasiert]** für den Auslöser wählen.

   <!-- You can also create and add your own custom strategy to the list. For details, see [Implement a custom strategy to autosave the forms](auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p). -->

1. (Nur zeitbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um die Optionen für das zeitbasierte automatische Speichern zu konfigurieren.

   1. Im **[!UICONTROL Automatisches Speichern in diesem Intervall]** Legen Sie das Zeitintervall in Sekunden fest. Das Formular wird wiederholt gespeichert, nachdem die im Intervallfeld angegebene Anzahl von Sekunden abgelaufen ist.

1. (Nur ereignisbasiertes automatisches Speichern) Führen Sie die folgenden Schritte aus, um Optionen für ereignisbasiertes automatisches Speichern zu konfigurieren.

   1. Geben Sie im Feld **[!UICONTROL Automatisch nach diesem Ereignis speichern]** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis an. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **[!UICONTROL Automatisches Speichern für anonyme Benutzer aktivieren]** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Service zu konfigurieren, navigieren Sie zur Adobe Experience Manager Web Console-Konfiguration unter `https://'[server]:[port]'system/console/configMgr` und bearbeiten Sie den **[!UICONTROL allgemeinen Forms-Konfigurations-Service]**, um die Option **[!UICONTROL Alle Benutzer]** im Feld **[!UICONTROL Zulassen]** auszuwählen und die Konfiguration zu speichern. 
