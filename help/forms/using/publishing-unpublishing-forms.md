---
title: Veröffentlichung von Formularen und Dokumenten und Veröffentlichungen rückgängig machen
seo-title: Veröffentlichung von Formularen und Dokumenten und Veröffentlichungen rückgängig machen
description: Sie können das Veröffentlichen und Rückgängigmachen von Veröffentlichungen bei Formularen planen. Veröffentlichte Formulare werden auf der Veröffentlichungsinstanz repliziert.
seo-description: Sie können das Veröffentlichen und Rückgängigmachen von Veröffentlichungen bei Formularen planen. Veröffentlichte Formulare werden auf der Veröffentlichungsinstanz repliziert.
uuid: 0bad5608-b7a8-4599-81cc-2cd0a3dc7dd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
content-strategy: max-2018
discoiquuid: 32a7a50c-74f4-49bc-a0bd-a9ec142527cb
docset: aem65
translation-type: tm+mt
source-git-commit: f9ed171c188a4dfb71f12ae9c98105a4c1895542

---


# Veröffentlichung von Formularen und Dokumenten und Veröffentlichungen rückgängig machen{#publishing-and-unpublishing-forms-and-documents}

Mit AEM Forms können Sie Formulare mühelos erstellen, veröffentlichen und die Veröffentlichung rückgängig machen. Weitere Informationen zu AEM Forms finden Sie in [Einführung zum Verwalten von Formularen](../../forms/using/introduction-managing-forms.md).

Der AEM Forms-Server umfasst zwei Instanzen: die Autoren- und die Veröffentlichungsinstanz. Der Autoreninstanz dient dem Erstellen und Verwalten von Formular-Assets und -Ressourcen. Die Veröffentlichungsinstanz dient zur Aufbewahrung von Assets und zugehörigen Ressourcen, die für Endbenutzer verfügbar sind. Sie können XDP- und PDF-Formulare im Author-Modus importieren. Detaillierte Informationen finden Sie unter [XDP- und PDF-Dokumente in AEM Forms aufrufen](../../forms/using/get-xdp-pdf-documents-aem.md).

## Unterstützte Asset   {#supported-assets-nbsp}

AEM Forms unterstützt die folgenden Assettypen:

* Adaptive Formulare
* Adaptive Dokumente
* Adaptive Formularfragmente
* Designs
* Formularvorlagen (XFA-Formulare)
* PDF-Formulare
* Dokumente (reduzierte PDF-Dokumente)
* Formularsätze
* Ressourcen (Bilder, Schemas und Stylesheets)

Zunächst sind alle Assets nur in der Autoreninstanz verfügbar. Ein Administrator oder Formularautor kann außer den Ressourcen alle Assets veröffentlichen.

Wenn Sie ein Formular auswählen und veröffentlichen, werden die zugehörigen Assets und Ressourcen ebenfalls veröffentlicht. Allerdings werden abhängige Assets nicht veröffentlicht. Mit zugehörigen Assets und Ressourcen sind in diesem Zusammenhang Assets gemeint, die von einem veröffentlichten Asset genutzt werden oder auf die dieses verweist. Abhängige Assets sind Assets, die auf ein veröffentlichtes Asset verweisen.

Ihre adaptiven Formulare können möglicherweise einige Konfigurationen, Einstellungen und Anpassungen verwenden, die nicht automatisch veröffentlicht werden. Es wird empfohlen, dass Sie diese Ressourcen veröffentlichen oder aktivieren, bevor Sie ein adaptives Formular veröffentlichen.

* Bearbeitbare adaptive Formularvorlagen
* Cloud-Dienstkonfigurationen für Adobe Sign, Typekit, reCAPTCHA und Form Data-Modelle
* Andere Cloud-Dienstkonfigationen sind nur aktiviert, wenn der Benutzer über Administratorberechtigungen verfügt.
* Anpassungen. Dazu zählen (jedoch nicht ausschließlich):

   * Benutzerdefinierte Layouts
   * Benutzerdefiniertes Erscheinungsbild
   * CSS-Datei - als Eingabe im Dialogfeld Eigenschaften des adaptiven Formularcontainers genommen
   * Client-Bibliothekskategorie - als Eingabe im Dialogfeld Eigenschaften des adaptiven Formularcontainers genommen
   * Andere Client-Bibliothek, die als Teil der adaptiven Formularvorlage enthalten sein kann.
   * Entwurfspfade

## Asset-Zustände {#asset-states}

Ein Asset kann über folgende Status verfügen:

* **Unveröffentlicht**: Ein Asset, das noch nie veröffentlicht wurde (dieser Status kann nur für Formular-Assets verwendet werden. Correspondence Management-Asset haben keine unveröffentlichten Status.)
* **Veröffentlicht**: Ein Asset, das veröffentlicht wurde und auf der Veröffentlichungsinstanz verfügbar ist
* **Geändert**: Ein Element, das nach seiner Veröffentlichung geändert wird

## Asset veröffentlichen {#publish-an-asset}

1. Melden Sie sich beim AEM Forms-Server an.
1. Verwenden Sie eines der folgenden Verfahren, um ein Asset auszuwählen und zu veröffentlichen.

   1. Bewegen Sie den Mauszeiger über ein Asset und tippen Sie auf **[!UICONTROL Veröffentlichen]** von ![aem6forms_globe](assets/aem6forms_globe.pngasset.png).
   1. Führen Sie einen der folgenden Schritte aus und tippen Sie dann auf „Veröffentlichen“:

      * If you are in the card view, tap **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png), and tap the asset. Das Asset wird ausgewählt.
      * Wenn Sie sich in der Listenansicht befinden, aktivieren Sie das Kontrollkästchen eines Assets. Das Asset wird ausgewählt.
      * Tippen Sie auf ein Asset, um dessen Details anzuzeigen.
      * Display an asset&#39;s properties by tapping View Properties ![viewproperties](assets/viewproperties.png).
      >[!NOTE]
      >
      >Wählen Sie nicht mehrere Assets aus. Das Veröffentlichen mehrerer Assets auf einmal wird nicht unterstützt.


1. Wenn der Veröffentlichungsprozess beginnt, wird ein Bestätigungsdialogfeld angezeigt, in dem alle zugehörigen Assets und Ressourcen aufgelistet sind. In the dialog box that contains related assets, tap **[!UICONTROL Publish]**. Das Asset wird veröffentlicht und das Dialogfeld zum Erfolg von Assets veröffentlichen wird angezeigt.

   >[!NOTE]
   >
   >Bei adaptiven Formularen wird neben den zugehörigen Assets auch der Seitenname des adaptiven Formulars angezeigt.

   ![Ein Bestätigungsdialogfeld mit allen zugehörigen Elementen und Ressourcen](assets/p4.png)

   Ein Bestätigungsdialogfeld mit allen zugehörigen Elementen und Ressourcen

   >[!NOTE]
   >
   >Forms Manager: Wenn der Benutzer nicht berechtigt ist, die aufgelisteten Assets zu veröffentlichen, ist die Veröffentlichungsaktion deaktiviert. Ein Asset, für das zusätzliche Berechtigungen erforderlich sind, wird rot angezeigt.

   Nachdem ein Asset veröffentlicht wurde, werden die Metadateneigenschaften des Assets in die Veröffentlichungsinstanz kopiert und der Status des Assets wird in „Veröffentlicht“ geändert. Der Status der abhängigen Assets, die veröffentlicht wurden, wird ebenfalls in „Veröffentlicht“ geändert.

   Nach dem Veröffentlichen eines Assets können Sie Forms Portal nutzen, um alle Assets auf einer Webseite anzuzeigen. Weitere Informationen finden Sie unter [Einführung in das Veröffentlichen von Formularen in einem Portal](../../forms/using/introduction-publishing-forms.md).

## Alle Correspondence Management-Assets veröffentlichen {#publish-all-the-correspondence-management-assets}

Mit AEM Forms können Sie alle Correspondence Management-Assets auf einem Server in ein und demselben Vorgang veröffentlichen. Die veröffentlichten Assets umfassen sämtliche Correspondence Management-Assets und ihre zugehörigen Abhängigkeiten.

Führen Sie nun die folgenden Schritte aus, um sämtliche Correspondence Management-Assets auf dem Server zu veröffentlichen:

1. Melden Sie sich beim AEM Forms-Server an.
1. Tippen Sie auf **Adobe Experience Manager** in der Menüleiste für globale Navigation.
1. Tap ![tools](assets/tools.png), and then tap **Forms**.
1. Tap **Publish Correspondence Management Assets**.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   Die Seite &quot;Alle Correspondence Management-Assets veröffentlichen&quot;wird angezeigt und enthält Informationen zum letzten Versuch, Correspondence Management-Assets zu veröffentlichen.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. Tap **Publish** and, in the confirm message, tap **OK**.

   Nachdem ein Stapelvorgang abgeschlossen ist, können Sie die Details der letzten Ausführung anzeigen. Unter anderem werden Informationen zu Administrator-Anmeldedaten angezeigt und ob die Stapelausführung erfolgreich war.

   >[!NOTE]
   >
   >Nachdem der Veröffentlichungsvorgang ausgelöst wurde, kann er nicht abgebrochen werden. Erstellen, löschen, ändern oder veröffentlichen Sie während des Veröffentlichungsvorgangs keine Assets oder starten Sie den Vorgang &quot;Alle Correspondence Management-Assets exportieren&quot;.

## Formulare und Dokumente veröffentlichen und Veröffentlichung rückgängig machen {#automate-publishing-and-unpublishing-for-forms-amp-documents}

Mit AEM Forms können Sie die Veröffentlichung von Formularen und Dokumenten und die Rückgängigmachung dieses Vorgangs planen. Sie können den Zeitplan im Metadaten-Editor angeben. For more information about managing form metadata, see [Managing form metadata.](../../forms/using/manage-form-metadata.md)

Führen Sie folgende Schritte aus, um das Datum und die Uhrzeit für die Veröffentlichung bzw. das Rückgängigmachen der Veröffentlichung bei Formular- und Dokument-Assets zu planen:

1. Select an asset and tap **[!UICONTROL View Properties]**. Die Seite mit den Metadateneigenschaften wird geöffnet.
1. Tippen Sie auf der Seite &quot;Metadateneigenschaften&quot;auf **[!UICONTROL Erweitert]** und dann auf **[!UICONTROL Bearbeiten]** der Datei &quot; ![illustratorcc_penciltool_cur_edit_2_17](assets/illustratorcc_penciltool_cur_edit_2_17.png)&quot;.
1. Wählen Sie in den Feldern **[!UICONTROL Veröffentlichungszeit]** und **[!UICONTROL Zeit für Rückgängigmachen der Veröffentlichung]** das Datum und die Uhrzeit aus.\
   Tippen Sie auf **[!UICONTROL Fertig]** ![aem6forms_check](assets/aem6forms_check.png).

## Rückgängigmachen der Veröffentlichung eines Assets {#unpublish-an-asset}

1. Select an asset that is published and tap **[!UICONTROL Unpublish]** ![unpublish](assets/unpublish.png).
1. Verwenden Sie eines der folgenden Verfahren, um ein Asset auszuwählen und seine Veröffentlichung rückgängig zu machen.

   1. Move the pointer over an asset and tap **[!UICONTROL Unpublish]** ![unpublish](assets/unpublish.png).
   1. Führen Sie einen der folgenden Schritte aus und tippen Sie dann auf „Veröffentlichung aufheben“:

      * If you are in the card view, tap **[!UICONTROL Enter Selection]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png), and tap the asset. Das Asset wird ausgewählt.

      * If you are in the list view, hover over an asset and tap ![selectassetcheckmark](assets/selectassetcheckmark.png) . Das Asset wird ausgewählt.

      * Tippen Sie auf ein Asset, um dessen Details anzuzeigen.
      * Display an asset&#39;s properties by tapping View Properties ![viewproperties](assets/viewproperties.png).

1. Wenn Sie der Prozess zum Rückgängigmachen der Veröffentlichung startet, wird ein Bestätigungsdialogfeld angezeigt. Tap **[!UICONTROL Unpublish]**.

   >[!NOTE]
   >
   >Es wird nur die Veröffentlichung des ausgewählten Assets rückgängig gemacht, Assets, die ihm untergeordnet sind oder auf dieses verweisen, bleiben veröffentlicht.

## Stellen Sie ein Asset oder einen Brief auf die zuvor veröffentlichte Version wieder her {#revert-an-asset-or-letter-to-the-previously-published-version}

Jedes Mal, wenn Sie ein Asset oder einen Brief veröffentlichen, nachdem Sie sie bearbeitet haben, wird eine Version des Assets oder Briefs erstellt. Sie können ein Asset oder einen Brief auf eine zuvor veröffentlichten Version wiederherstellen. Möglicherweise müssen Sie dies tun, wenn die aktuelle Version des Assets oder des Dokuments fehlschlägt.

>[!NOTE]
>
>Setzen Sie einen Brief nicht auf einen zuletzt veröffentlichten Status zurück, wenn ein abhängiges Asset, das in diesem veröffentlichten Brief verwendet wird, aus dem System gelöscht wird.

1. Select an asset and tap **[!UICONTROL Revert to Previously Published Version]** ![reverttopreviouslypublishedversion](assets/reverttopreviouslypublishedversion.png).
1. Bevor das Asset wiederhergestellt wird, wird ein Bestätigungsdialogfeld angezeigt. Tap **[!UICONTROL Revert]**.

   Das Asset bzw. der Brief wird auf seine zuvor veröffentlichte Version zurückgesetzt.

## Löschwn eines Assets {#delete-an-asset}

>[!NOTE]
>
>Wenn Sie ein Asset löschen, wird es aus der Veröffentlichungsinstanz entfernt. Das Löschen von Elementen entfernt den Versionsverlauf mit Ausnahme der Basisversion.

1. Select an asset and tap **[!UICONTROL Delete]** ![delete](assets/delete.png).

   >[!NOTE]
   >
   >The Delete option is also available when you display asset details by tapping an asset or you display an asset&#39;s properties by tapping View Properties ![viewproperties](assets/viewproperties.png).

1. Bevor das Asset gelöscht wird, wird ein Bestätigungsdialogfeld angezeigt. Tippen Sie auf **[!UICONTROL Löschen]**. 

   >[!NOTE]
   >
   >Nur das ausgewählte Asset wird gelöscht, nicht jedoch die von ihm abhängigen Assets. To check references of an asset, tap ![references](assets/references.png) and then select an asset.
   >
   >
   >Wenn Sie versuchen, ein Asset zu löschen, das einem anderen Asset untergeordnet ist, kann es nicht gelöscht werden. Um ein solches Asset löschen, entfernen Sie seine Verweise aus anderen Asset und wiederholen Sie den Vorgang.

## Geschützte adaptive Formulare {#protected-adaptive-forms}

Sie können die Authentifizierung für den Zugriff auf Formulare aktivieren, für die Sie ausgewählten Benutzern Zugriff gewähren möchten. Wenn Sie die Authentifizierung für Ihre Formulare aktivieren, sehen Benutzer einen Anmeldebildschirm, bevor sie auf sie zugreifen können. Nur Benutzer, deren Anmeldeinformationen über die entsprechende Autorisierung verfügen, erhalten Zugriff auf die Formulare.

Authentifizierung für Ihre Formulare aktivieren

1. Öffnen Sie in Ihrem Browser configMgr in der Veröffentlichungsinstanz.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Klicken Sie auf der Seite „Adobe Experience Manager Web Console-Konfigurationen“ auf **Apache Sling-Authentifizierungsdienst**, um diesen zu konfigurieren.
1. Fügen Sie im daraufhin angezeigten Dialogfeld „Authentifizierungsdienst“ mithilfe der Schaltfläche **+** die gewünschten Pfade hinzu.\
   Wenn Sie einen Pfad hinzufügen, wird der Authentifizierungsdienst für Formulare unterdiesem Pfad aktiviert.
