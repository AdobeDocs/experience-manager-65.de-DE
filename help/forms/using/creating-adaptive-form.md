---
title: Erstellen eines adaptiven Formulars
description: Erfahren Sie, wie Sie ein adaptives Formular mit [!DNL Experience Manager Forms] erstellen können. Adaptive Formulare sind Responsive-HTML5-Formulare, mit denen die Informationserfassung und -verarbeitung optimiert wird. Vertiefen Sie Ihre Kenntnisse über die Erstellung adaptiver Formulare auf der Grundlage eines Formulardatenmodells, einer XFA-Formularvorlage und eines XML- oder JSON-Schemas.
role: User, Developer
level: Beginner
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
exl-id: 2c25a8b7-73f7-40fb-a303-9446a708c8eb
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1984'
ht-degree: 100%

---

# Erstellen eines adaptiven Formulars {#creating-an-adaptive-form}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

## Erstellen eines adaptiven Formulars {#strong-create-an-adaptive-form-strong}

Gehen Sie wie folgt vor, um ein adaptives Formular zu erstellen.

1. Zugreifen auf die [!DNL Experience Manager Forms]-Autoreninstanz unter `https://'[server]:[port]'/<custom-context-if-any>.`

1. Geben Sie Ihre Anmeldedaten auf der Experience Manager-Anmeldeseite ein.

   Wenn Sie sich angemeldet haben, tippen Sie in der linken oberen Ecke auf **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Formulare]** > **[!UICONTROL Formulare und Dokumente]**.

   >[!NOTE]
   >
   >Bei einer Standardinstallation lautet der Benutzername `admin` und das Kennwort `admin`.

1. Wählen Sie **[!UICONTROL Erstellen]** und dann **[!UICONTROL Adaptives Formular]** aus. 
1. Eine Option zum Auswählen einer Vorlage wird angezeigt. Weitere Informationen zu Vorlagen finden Sie unter [Adaptive Formularvorlagen](creating-adaptive-form.md#p-adaptive-form-templates-p). Wählen Sie eine Vorlage und dann „Weiter“ aus.
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

   Sie können diese auf der Registerkarte **[!UICONTROL Formularmodell]** konfigurieren. Sie befindet sich auf der Seite **[!UICONTROL Eigenschaften hinzufügen]**. Standardmäßig ist das Formularmodell **[!UICONTROL Keine]** ausgewählt.

1. Wählen Sie **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

   Sobald Sie alle Eigenschaften angegeben haben, klicken Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

   Sobald Sie alle Eigenschaften angegeben haben, klicken Sie auf **[!UICONTROL Erstellen]**. Ein adaptives Formular wird erstellt und es wird ein Dialogfeld zum Öffnen des Formulars zur Bearbeitung angezeigt.

1. Wählen Sie **[!UICONTROL Öffnen]** aus, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen. Das Formular wird zur Bearbeitung geöffnet und zeigt den Inhalt an, der in der Vorlage verfügbar ist. Er zeigt auch die Seitenleiste an, um das neu erstellte Formular entsprechend den Anforderungen anzupassen.

   Je nach Typ des adaptiven Formulars werden auf der Registerkarte **[!UICONTROL Datenmodellobjekte]** des **[!UICONTROL Inhaltbrowsers]** in der Seitenleiste die Formularelemente angezeigt, die in der zugeordneten XFA-Formularvorlage, dem XML-Schema oder JSON-Schema vorhanden sind. Sie können diese Elemente auch per Drag &amp; Drop in das adaptiven Formular ziehen.

   Informationen zur Authoring-Oberfläche für adaptive Formulare und zu verfügbaren Komponenten finden Sie unter [Einführung in das Authoring adaptiver Formulare](introduction-forms-authoring.md).

   >[!NOTE]
   >
   >Lassen Sie Popup-Fenster in Ihrem Browser zu, um das neu erstellte Formular in einer neuen Registerkarte zu öffnen.

## Erstellen eines adaptiven Formulars basierend auf einem Formulardatenmodell {#fdm}

Durch die [[!DNL Experience Manager Forms] Datenintegration](data-integration.md) können Sie mehrere Datenquellen integrieren, ihre Entitäten und Services zusammenführen und so ein Formulardatenmodell erstellen. Dabei handelt es sich um eine Erweiterung des JSON-Schemas. Sie können ein Formulardatenmodell verwenden, um ein adaptives Formular zu erstellen. Die Entitäten oder Datenmodellobjekte, die in einem Formulardatenmodell konfiguriert sind, sind als Datenmodellobjekte für die Formularerstellung verfügbar. Sie sind an die jeweiligen Datenquellen gebunden und werden verwendet, um ein Formular vorauszufüllen und die übermittelten Daten zurück in die entsprechenden Datenquellen zu schreiben. Sie können auch Services aufrufen, die in einem Formulardatenmodell mit Regeln für adaptive Formulare konfiguriert sind.

So verwenden Sie ein Formulardatenmodell zum Erstellen eines adaptiven Formulars:

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Bildschirm „Eigenschaften hinzufügen“ **[!UICONTROL Formulardatenmodell]** aus der Dropdownliste **[!UICONTROL Auswählen aus]**.

   ![Create-af-1-1](assets/create-af-1-1.png)

1. Wählen Sie zum Erweitern **[!UICONTROL Formulardatenmodell auswählen]** aus. Alle verfügbaren Formulardatenmodelle werden aufgelistet.

   Wählen Sie ein Formulardatenmodell aus.

   ![Create-af-2-1](assets/create-af-2-1.png)

>[!NOTE]
>
>Sie können das Formulardatenmodell für ein adaptives Formular auch ändern. Anweisungen hierfür finden Sie unter [Bearbeiten von Formularmodelleigenschaften eines adaptiven Formulars](#edit-form-model).

## Erstellen eines adaptiven Formulars anhand einer XFA-Formularvorlage {#create-an-adaptive-form-based-on-an-xfa-form-template}

Sie können Ihre XFA-Formularvorlagen wiederverwenden, um adaptive Formulare zu erstellen. Dazu müssen Sie eine XFA-Formularvorlage hochladen und mit einem adaptiven Formular verknüpfen. Die Elemente der Formularvorlage (XFA-Formular) sind dann zum Zeitpunkt der Erstellung adaptiver Formulare für die Verwendung in der Inhaltssuche verfügbar. Aus der Inhaltssuche können Sie per Drag &amp; Drop Formularvorlagenelemente in das Formular ziehen.

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

In den folgenden Dokumenten erfahren Sie, wie Sie ein XML- oder JSON-Schema für die Erstellung adaptiver Formulare entwickeln.

* [Adaptive Formulare mithilfe des XML-Schemas erstellen](adaptive-form-xml-schema-form-model.md)
* [Erstellen adaptiver Formulare mithilfe eines JSON-Schemas](adaptive-form-json-schema-form-model.md)

Führen Sie folgende Schritte aus, um ein XML- oder JSON-Schema als Formularmodell für ein adaptives Formular zu verwenden:

1. Wählen Sie auf der Seite zum Erstellen adaptiver Formulare beim Schritt **[!UICONTROL Eigenschaften hinzufügen]** die Registerkarte **[!UICONTROL Formularmodell]** aus.
1. Wählen Sie auf der Registerkarte „Formularmodell“ aus dem Dropdown-Feld **[!UICONTROL Auswählen]** die Option **[!UICONTROL Schema]**.

1. Wählen Sie **[!UICONTROL Schema auswählen]** und führen Sie einen der folgenden Schritte aus:

   * **[!UICONTROL Von Datenträger hochladen]** – Wählen Sie diese Option und dann „Schemadefinition hochladen“ aus, um ein XML- oder JSON-Schema in Ihrem Dateisystem zu suchen und hochzuladen. Die hochgeladene Schemadatei befindet sich innerhalb des Formulars und ist für andere adaptive Formulare nicht zugänglich.
   * **[!UICONTROL Im Repository suchen]** – Wählen Sie diese Option, um eine Auswahl aus der Liste der im Repository verfügbaren Schemadefinitionsdateien zu treffen. Wählen Sie die XML- oder JSON-Schemadatei als Formularmodell aus. Das ausgewählte Schema wird dem Formular per Verweis zugeordnet und kann für andere adaptive Formulare verwendet werden.

   >[!CAUTION]
   >
   >Stellen Sie sicher, dass der Dateiname des JSON-Schemas mit **.schema.json** endet, z. B. „meinSchema.schema.json“.

   ![Auswählen eines XML- oder JSON-Schemas](assets/upload-schema.png)
   **Abbildung:** *Auswählen eines XML- oder JSON-Schemas*

1. (Nur für XML-Schema) Nachdem Sie ein XML-Schema ausgewählt oder hochgeladen haben, geben Sie ein Stammelement der ausgewählten XSD-Datei an, das mit dem adaptiven Formular zugeordnet werden soll.

   ![Auswählen eines XSD-Stammelements](assets/xsd-root-element.png)
   **Abbildung:** *XSD-Stammelement auswählen*

>[!NOTE]
>
>Sie können das Schema für ein adaptives Formular ändern. Anweisungen hierfür finden Sie unter [Bearbeiten von Formularmodelleigenschaften eines adaptiven Formulars](#edit-form-model).

## Adaptive Formularvorlagen {#adaptive-form-templates}

Eine Vorlage bietet eine Grundstruktur für adaptive Formulare und definiert deren Erscheinungsbild (Layouts und Stile). Es enthält vorformatierte Komponenten, einschließlich bestimmter Eigenschaften und einer Struktur für Inhalte. <!-- Out of the box, AEM Forms provides some adaptive form templates. To get the complete template package including advanced templates, you need to install the AEM Forms add-on package. For more information, see [Installing AEM Forms add-on package](installing-configuring-aem-forms-osgi.md).-->

Darüber hinaus können Sie den Vorlageneditor verwenden, um eigene Vorlagen zu erstellen. Weitere Informationen zum Verwenden von Vorlagen finden Sie unter [Adaptive Formularvorlagen](template-editor.md).

>[!NOTE]
>
>Wenn Sie ein mit einer erweiterten Vorlage erstelltes adaptives Formular zur Bearbeitung öffnen, wird eine Fehlermeldung angezeigt. Die erweiterte Vorlage verfügt über eine Komponente für den Unterschriftsschritt, für die Adobe Sign standardmäßig aktiviert ist. Um den Fehler zu beheben, erstellen Sie eine [Adobe Sign-Cloud-Konfiguration](adobe-sign-integration-adaptive-forms.md), wählen Sie diese aus und [konfigurieren Sie eine unterschreibende Person](working-with-adobe-sign.md#addsignerstoanadaptiveform).

## Bearbeiten von Formularmodelleigenschaften eines adaptiven Formulars {#edit-form-model}

Adaptive Formulare werden entweder ohne Formularmodell erstellt (mithilfe der Option „Keine“ für Formularmodelle) oder mithilfe eines Formularmodells wie einer Formularvorlage, eines XML- bzw. JSON-Schemas oder eines Formulardatenmodells. Sie können das Formularmodell für ein adaptives Formular von der Option „Keine“ zu einem anderen Formularmodell ändern. Sie können für ein adaptives Formular, das auf einem Formularmodell basiert, eine andere Formularvorlage bzw. ein anderes XML-Schema, JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell wählen. Sie können jedoch nicht zwischen Formularmodellen wechseln.

1. Wählen Sie das adaptive Formular und dann das Symbol **Eigenschaften** aus.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie eine der folgenden Vorgehensweisen.

   * Wenn das adaptive Formular nicht auf einem Formularmodell basiert, können Sie ein Formularmodell und eine entsprechende Formularvorlage, ein XML- oder JSON-Schema oder ein Formulardatenmodell auswählen.
   * Wenn das adaptive Formular auf einem Formularmodell basiert, können Sie eine andere Formularvorlage bzw. ein anderes XML-Schema, JSON-Schema oder Formulardatenmodell für dasselbe Formularmodell wählen.

1. Wählen Sie **[!UICONTROL Speichern]** aus, um die Eigenschaften zu speichern.

## Automatisches Speichern eines adaptiven Formulars {#auto-save-an-adaptive-form}

Standardmäßig werden die Inhalte eines adaptiven Formulars bei einer Benutzeraktion wie einem Klick auf die Schaltfläche „Speichern“ gespeichert. Sie können auch ein adaptives Formular so konfigurieren, dass Inhalt basierend auf einem Ereignis oder einem Zeitintervall automatisch gespeichert wird. Die Option „Automatische Speicherung“ ist bei folgenden Aufgaben hilfreich:

* Automatisches Speichern der Inhalte für anonyme und angemeldete Benutzende
* Speichern der Inhalte eines Formulars ohne oder mit minimalem Benutzereingriff
* Speichern der Inhalte eines Formulars basierend auf einem Benutzerereignis
* Wiederholtes Speichern der Formularinhalte nach einem angegebenen Zeitintervall

### Aktivieren der Option „Automatische Speicherung“ für ein adaptives Formular {#enable-auto-save-for-an-adaptive-form}

Die Option „Automatisches Speichern“ ist standardmäßig nicht aktiviert. Sie können die Option „Automatisches Speichern“ über die Registerkarte „Automatisches Speichern“ eines adaptiven Formulars aktivieren. Die Registerkarte „Automatisches Speichern“ bietet mehrere weitere Konfigurationsoptionen. Führen Sie zum Aktivieren und Konfigurieren der Option „Automatisches Speichern“ für ein adaptives Formular folgende Schritte durch: 

1. Um auf den Abschnitt für das automatische Speichern in den Eigenschaften zuzugreifen, wählen Sie eine Komponente und dann ![field-level](assets/field-level.png) > **[!UICONTROL Container für adaptive Formulare]** und anschließend ![cmppr](assets/cmppr.png).
1. **[!UICONTROL Aktivieren]** Sie im Abschnitt **[!UICONTROL Automatische Speicherung]** die Option zum automatischen Speichern.
1. Geben Sie im Feld **[!UICONTROL Ereignis für adaptives Formular]** den Wert „1“ oder „TRUE“ ein, um das Formular automatisch speichern zu lassen, wenn das Formular im Browser geladen wird. Sie können außerdem einen bedingten Ausdruck für ein Ereignis angeben, bei dem, wenn es ausgelöst wird, der Status „true“ zurückgegeben und der Inhalt des Formulars gespeichert wird.
1. Geben Sie den Auslöser an. Die automatische Speicherung wird gemäß Ihrer Konfiguration ausgelöst. Ihre Optionen sind:

   * **[!UICONTROL Zeitbasiert:]** Wählen Sie diese Option, um den Inhalt anhand eines bestimmtes Zeitintervalls zu speichern.
   * **[!UICONTROL Ereignisbasiert:]** Wählen Sie diese Option, um den Inhalt beim Auslösen eines Ereignisses zu speichern.

   Wenn Sie einen Auslöser auswählen, wird das Feld „Strategiekonfiguration“ aktiviert. Mithilfe des Felds „Strategiekonfiguration“ können Sie:

   * ein Zeitintervall angeben, wenn Sie **[!UICONTROL Zeitbasiert]** für den Auslöser wählen.
   * Den Namen des Ereignisses angeben, wenn Sie **[!UICONTROL Ereignisbasiert]** für den Auslöser wählen.

   <!-- You can also create and add your own custom strategy to the list. For details, see [Implement a custom strategy to autosave the forms](auto-save-an-adaptive-form.md#p-implement-a-custom-strategy-to-enable-autosave-for-adaptive-forms-p). -->

1. (Nur zeitbasierte automatische Speicherung) Führen Sie die folgenden Schritte aus, um Optionen für die zeitbasierte automatische Speicherung zu konfigurieren.

   1. Geben Sie im Feld **[!UICONTROL Automatisches Speichern für das Intervall]** das Zeitintervall in Sekunden an. Das Formular wird wiederholt gespeichert, nachdem die im Intervallfeld angegebene Anzahl an Sekunden überschritten wird.

1. (Nur ereignisbasierte automatische Speicherung) Führen Sie die folgenden Schritte aus, um Optionen für die ereignisbasierte automatische Speicherung zu konfigurieren.

   1. Geben Sie im Feld **[!UICONTROL Automatisch nach diesem Ereignis speichern]** ein [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html)-Ereignis an. Das Formular wird immer dann gespeichert, wenn der Ausdruck „TRUE“ ergibt.

1. (Optional) Um den Inhalt automatisch für anonyme Benutzer zu speichern, wählen Sie die Option **[!UICONTROL Automatisches Speichern für anonyme Benutzer aktivieren]** und klicken Sie auf **[!UICONTROL OK]**.

   >[!NOTE]
   >
   >Damit die Option zum automatischen Speichern für anonyme Benutzer funktioniert, stellen Sie sicher, dass Sie den allgemeinen Forms-Konfigurationsdienst so konfiguriert ist, dass alle Benutzer Formulare in der Vorschau anzeigen, überprüfen und zu signieren können.
   >
   >Um den Service zu konfigurieren, navigieren Sie zur Adobe Experience Manager Web Console-Konfiguration unter `https://'[server]:[port]'system/console/configMgr` und bearbeiten Sie den **[!UICONTROL allgemeinen Forms-Konfigurations-Service]**, um die Option **[!UICONTROL Alle Benutzer]** im Feld **[!UICONTROL Zulassen]** auszuwählen und die Konfiguration zu speichern. 


## Wie erfolgt das Umbenennen eines adaptiven AEM-Formulars? {#rename-an-AEM-Adaptive-Form}

Führen Sie zum Umbenennen eines adaptiven Formulars die folgenden Schritte aus:

1. Wählen Sie ein adaptives Formular in Ihrer AEM Forms-Benutzeroberfläche aus.
1. Klicken Sie auf **Eigenschaften** in der oberen Leiste.

   ![Eigenschaften](/help/forms/using/assets/rename-form-properties.png)

1. Ändern Sie den Formularnamen auf der Registerkarte **Titel**, wie in der Abbildung unten dargestellt.
1. Klicken Sie auf **Speichern und schließen**.

   ![Umbenennen eines adaptiven AEM-Formulars](/help/forms/using/assets/rename-form-title.png)
