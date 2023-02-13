---
title: Veröffentlichen von Formularen und Dokumenten und Rückgängigmachen von Veröffentlichungen
seo-title: Publishing and unpublishing forms and documents
description: Sie können das Veröffentlichen und Rückgängigmachen von Veröffentlichungen bei Formularen planen. Veröffentlichte Formulare werden auf der Veröffentlichungsinstanz repliziert.
seo-description: You can schedule publishing and unpublishing of forms. Published forms are replicated on the publish instance.
uuid: 0bad5608-b7a8-4599-81cc-2cd0a3dc7dd5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
content-strategy: max-2018
discoiquuid: 32a7a50c-74f4-49bc-a0bd-a9ec142527cb
docset: aem65
exl-id: f26c4268-7885-4e61-a258-219d98288548
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1413'
ht-degree: 100%

---

# Veröffentlichung von Formularen und Dokumenten und Rückgängigmachen von Veröffentlichungen{#publishing-and-unpublishing-forms-and-documents}

Mit AEM Forms können Sie Formulare mühelos erstellen, veröffentlichen und die Veröffentlichung rückgängig machen. Weitere Informationen zu AEM Forms finden Sie in [Einführung zum Verwalten von Formularen](../../forms/using/introduction-managing-forms.md).

Der AEM Forms-Server umfasst zwei Instanzen: die Autoren- und die Veröffentlichungsinstanz. Der Autoreninstanz dient dem Erstellen und Verwalten von Formular-Assets und -Ressourcen. Die Veröffentlichungsinstanz dient zur Aufbewahrung von Assets und zugehörigen Ressourcen, die für Endbenutzer verfügbar sind. Sie können XDP- und PDF-Formulare im Author-Modus importieren. Detaillierte Informationen finden Sie unter [XDP- und PDF-Dokumente in AEM Forms aufrufen](../../forms/using/get-xdp-pdf-documents-aem.md).

## Unterstützte Assets  {#supported-assets-nbsp}

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
* Andere Cloud-Service-Konfigurationen sind nur aktiviert, wenn der Benutzer über Administratorberechtigungen verfügt.
* Anpassungen. Dazu zählen (jedoch nicht ausschließlich):

   * Benutzerdefinierte Layouts
   * Benutzerdefiniertes Erscheinungsbild
   * CSS-Datei – als Eingabe im Dialogfeld „Container-Eigenschaften für adaptive Formulare“
   * Client-Bibliothekskategorie – als Eingabe im Dialogfeld „Container-Eigenschaften für adaptive Formulare“
   * Andere Client-Bibliothek, die als Teil der adaptiven Formularvorlage enthalten sein kann.
   * Entwurfspfade

## Asset-Status {#asset-states}

Ein Asset kann über folgende Status verfügen:

* **Unveröffentlicht**: Ein Asset, das noch nie veröffentlicht wurde (dieser Status kann nur für Formular-Assets verwendet werden. Correspondence Management-Asset haben keine unveröffentlichten Status.)
* **Veröffentlicht**: Ein Asset, das veröffentlicht wurde und auf der Veröffentlichungsinstanz verfügbar ist
* **Geändert**: Ein Asset, das nach seiner Veröffentlichung geändert wird

## Asset veröffentlichen {#publish-an-asset}

1. Melden Sie sich beim AEM Forms-Server an.
1. Verwenden Sie eines der folgenden Verfahren, um ein Asset auszuwählen und zu veröffentlichen.

   1. Bewegen Sie den Mauszeiger über ein Asset und tippen Sie auf **[!UICONTROL Veröffentlichen]** ![aem6forms_globe](assets/aem6forms_globe.pngasset.png).
   1. Führen Sie einen der folgenden Schritte aus und tippen Sie dann auf „Veröffentlichen“:

      * Wenn Sie sich in der Kartenansicht befinden, tippen Sie auf **[!UICONTROL Auswahl eingeben]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png) und dann auf das Asset. Das Asset wird ausgewählt.
      * Wenn Sie sich in der Listenansicht befinden, aktivieren Sie das Kontrollkästchen eines Assets. Das Asset wird ausgewählt.
      * Tippen Sie auf ein Asset, um dessen Details anzuzeigen.
      * Zeigen Sie die Eigenschaften eines Assets an, indem Sie auf „Eigenschaften anzeigen“ ![viewproperties](assets/viewproperties.png) tippen.

      >[!NOTE]
      >
      >Wählen Sie nicht mehrere Assets aus. Das gleichzeitige Veröffentlichen mehrerer Assets wird nicht unterstützt.


1. Wenn der Veröffentlichungsprozess beginnt, wird ein Bestätigungsdialogfeld angezeigt, in dem alle zugehörigen Assets und Ressourcen aufgelistet sind. Tippen Sie im Dialogfeld, das das zugehörige Asset enthält, auf **[!UICONTROL Veröffentlichen]**. Das Asset wird veröffentlicht, und das Dialogfeld über das erfolgreiche Veröffentlichen des Assets wird angezeigt.

   >[!NOTE]
   >
   >Bei adaptiven Formularen wird neben den zugehörigen Assets auch der Seitenname des adaptiven Formulars angezeigt.

   ![Bestätigungsdialogfeld mit allen zugehörigen Elementen und Ressourcen](assets/p4.png)

   Bestätigungsdialogfeld mit allen zugehörigen Elementen und Ressourcen

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
1. Tippen Sie auf ![Werkzeuge](assets/tools.png) und dann auf **Formulare**.
1. Tippen Sie auf **Correspondence Management Assets veröffentlichen**.

   ![publish-cmp-assets](assets/publish-cmp-assets.png)

   Die Seite „Alle Correspondence Management Assets veröffentlichen“ erscheint und zeigt Informationen zur letzten Ausführung des Prozesses „Correspondence Management Assets veröffentlichen“ an.

   ![publish-last-run-details](assets/publish-last-run-details.png)

1. Tippen Sie auf **Veröffentlichen** und anschließend in der Bestätigungsmeldung auf **OK**.

   Nachdem ein Stapelvorgang abgeschlossen ist, können Sie die Details der letzten Ausführung anzeigen. Unter anderem werden Informationen zu Administrator-Anmeldedaten angezeigt und ob die Stapelausführung erfolgreich war.

   >[!NOTE]
   >
   >Nachdem der Veröffentlichungsvorgang ausgelöst wurde, kann er nicht abgebrochen werden. Zudem sollten Sie darauf achten, während der Ausführung des Vorgangs „Veröffentlichen“ keine Assets zu erstellen, zu löschen, zu modifizieren oder zu veröffentlichen und nicht den Vorgang „Alle Correspondence Management-Elemente exportieren“ zu starten.

## Formulare und Dokumente veröffentlichen und die Veröffentlichung rückgängig machen {#automate-publishing-and-unpublishing-for-forms-amp-documents}

Mit AEM Forms können Sie die Veröffentlichung von Formularen und Dokumenten und die Rückgängigmachung dieses Vorgangs planen. Sie können den Zeitplan im Metadaten-Editor angeben. Weitere Informationen zum Verwalten von Formularmetadaten finden Sie unter [Verwalten von Formularmetadaten](../../forms/using/manage-form-metadata.md).

Führen Sie folgende Schritte aus, um das Datum und die Uhrzeit für die Veröffentlichung bzw. das Rückgängigmachen der Veröffentlichung von Formular- und Dokument-Assets zu planen:

1. Wählen Sie ein Asset aus und tippen Sie auf **[!UICONTROL Eigenschaften anzeigen]**. Die Seite mit den Metadateneigenschaften wird geöffnet.
1. Tippen Sie auf der Seite „Metadateneigenschaften“ auf **[!UICONTROL Erweitert]** und dann auf **[!UICONTROL Bearbeiten]** ![illustratorcc_penciltool_cur_edit_2_17](assets/illustratorcc_penciltool_cur_edit_2_17.png).
1. Wählen Sie in den Feldern **[!UICONTROL Veröffentlichungszeit]** und **[!UICONTROL Zeit für Rückgängigmachen der Veröffentlichung]** das Datum und die Uhrzeit aus.\
   Tippen Sie auf **[!UICONTROL Fertig]** ![aem6forms_check](assets/aem6forms_check.png).

## Die Veröffentlichung eines Assets rückgängig machen {#unpublish-an-asset}

1. Wählen Sie ein veröffentlichtes Asset aus und tippen Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]** ![unpublish](assets/unpublish.png).
1. Verwenden Sie eines der folgenden Verfahren, um ein Asset auszuwählen und seine Veröffentlichung rückgängig zu machen.

   1. Bewegen Sie den Mauszeiger über ein Asset und klicken Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]** ![unpublish](assets/unpublish.png).
   1. Führen Sie einen der folgenden Schritte aus und tippen Sie dann auf „Veröffentlichung rückgängig machen“:

      * Wenn Sie sich in der Kartenansicht befinden, tippen Sie auf **[!UICONTROL Auswahl eingeben]** ![aem6forms_check-circle](assets/aem6forms_check-circle.png) und dann auf das Asset. Das Asset wird ausgewählt.

      * Wenn Sie sich in der Listenansicht befinden, halten Sie den Mauszeiger über ein Asset und tippen Sie auf ![selectassetcheckmark](assets/selectassetcheckmark.png). Das Asset wird ausgewählt.

      * Tippen Sie auf ein Asset, um dessen Details anzuzeigen.
      * Zeigen Sie die Eigenschaften eines Assets an, indem Sie auf „Eigenschaften anzeigen“ ![viewproperties](assets/viewproperties.png) tippen.

1. Wenn der Prozess zum Rückgängigmachen der Veröffentlichung startet, wird ein Bestätigungsdialogfeld angezeigt. Tippen Sie auf **[!UICONTROL Veröffentlichung rückgängig machen]**.

   >[!NOTE]
   >
   >Es wird nur die Veröffentlichung des ausgewählten Assets rückgängig gemacht, Assets, die ihm untergeordnet sind oder auf es verweisen, bleiben veröffentlicht.

## Die zuvor veröffentlichte Version eines Assets oder Briefes wiederherstellen {#revert-an-asset-or-letter-to-the-previously-published-version}

Jedes Mal, wenn Sie ein Asset oder einen Brief veröffentlichen, nachdem Sie sie bearbeitet haben, wird eine Version des Assets oder Briefs erstellt. Sie können ein Asset oder einen Brief auf eine zuvor veröffentlichte Version zurücksetzen. Möglicherweise müssen Sie dies tun, wenn die aktuelle Version des Assets oder des Dokuments fehlschlägt.

>[!NOTE]
>
>Setzen Sie einen Brief nicht auf einen zuletzt veröffentlichten Status zurück, wenn ein abhängiges Asset, das in diesem veröffentlichten Brief verwendet wird, aus dem System gelöscht wird.

1. Wählen Sie ein Asset aus und tippen Sie auf **[!UICONTROL Wiederherstellen der zuvor veröffentlichten Version]** ![reverttopreviouslypublishedversion](assets/reverttopreviouslypublishedversion.png).
1. Bevor das Asset wiederhergestellt wird, wird ein Bestätigungsdialogfeld angezeigt. Tippen Sie auf **[!UICONTROL Wiederherstellen]**.

   Das Asset bzw. der Brief wird auf seine zuvor veröffentlichte Version zurückgesetzt.

## Löschen eines Assets {#delete-an-asset}

>[!NOTE]
>
>Wenn Sie ein Asset löschen, wird es aus der Veröffentlichungsinstanz entfernt. Das Löschen von Elementen entfernt den Versionsverlauf mit Ausnahme der Basisversion.

1. Wählen Sie ein Asset aus und tippen Sie auf **[!UICONTROL Löschen]** ![delete](assets/delete.png).

   >[!NOTE]
   >
   >Die Option „Löschen“ ist auch dann verfügbar, wenn Sie auf ein Asset tippen, um seine Details anzuzeigen, oder durch Tippen auf „Eigenschaften anzeigen“ ![viewproperties](assets/viewproperties.png) seine Eigenschaften anzeigen.

1. Bevor das Asset gelöscht wird, wird ein Bestätigungsdialogfeld angezeigt. Tippen Sie auf **[!UICONTROL Löschen]**.

   >[!NOTE]
   >
   >Nur das ausgewählte Asset wird gelöscht, nicht jedoch die von ihm abhängigen Assets. Um die Verweise eines Assets zu prüfen, tippen Sie auf ![references](assets/references.png) und wählen Sie ein Asset aus.
   >
   >
   >Wenn Sie versuchen, ein Asset zu löschen, das einem anderen Asset untergeordnet ist, kann es nicht gelöscht werden. Um ein solches Asset löschen, entfernen Sie seine Verweise aus anderen Assets und wiederholen Sie den Vorgang.

## Geschützte adaptive Formulare {#protected-adaptive-forms}

Sie können die Authentifizierung für den Zugriff auf Formulare aktivieren, für die Sie ausgewählten Benutzern Zugriff gewähren möchten. Wenn Sie die Authentifizierung für Ihre Formulare aktivieren, sehen Benutzer einen Anmeldebildschirm, bevor sie auf sie zugreifen können. Nur Benutzer, deren Anmeldeinformationen über die entsprechende Autorisierung verfügen, erhalten Zugriff auf die Formulare.

Authentifizierung für Ihre Formulare aktivieren

1. Öffnen Sie in Ihrem Browser configMgr in der Veröffentlichungsinstanz.\
   URL: `https://<hostname>:<PublishPort>/system/console/configMgr`

1. Klicken Sie auf der Seite „Adobe Experience Manager Web Console-Konfigurationen“ auf **Apache Sling-Authentifizierungs-Service**, um diesen Service zu konfigurieren.
1. Fügen Sie im daraufhin angezeigten Dialogfeld „Apache Sling-Authentifizierungs-Service“ mithilfe der Schaltfläche **+** die gewünschten Pfade hinzu.\
   Wenn Sie einen Pfad hinzufügen, wird der Authentifizierungs-Service für Formulare unter diesem Pfad aktiviert.
