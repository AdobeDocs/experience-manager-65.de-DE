---
title: Digital Rights Management in Assets
description: Erfahren Sie, wie Sie den Assetablaufstatus und Informationen für lizenzierte Assets in AEM verwalten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Digital Rights Management für digitale Assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da Adobe Experience Manager (AEM) Assets vollständig in die AEM-Plattform integriert sind, können Sie Asset-Ablaufinformationen und Asset-Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus für ein Asset in der Assets-Konsole sowohl in der Karten- als auch in der Listenansicht anzeigen.

![expired_flag_card](assets/expired_flag_card.png)<br> *Abbildung: In der Kartenansicht zeigt ein Flag auf der Karte das abgelaufene Asset an.*

**Listenansicht**

![expired_flag_list](assets/expired_flag_list.png)*Abbildung: In der Listenansicht wird in der Spalte **[!UICONTROL Status]**das Banner **[!UICONTROL Abgelaufen]**angezeigt.*

Sie können den Ablaufstatus eines Assets in der Timeline einsehen. Wählen Sie das Asset und danach im GlobalNav-Menü die Option „Timeline“ aus.

![chlimage_1-144](assets/chlimage_1-144.png)

You can also view the expiration status of assets in the **[!UICONTROL References]** rail. Hier werden der Assetablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Unter-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Webseiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset und das Experience Manager-Logo aus.

1. Choose **[!UICONTROL References]** from the menu.

   ![chlimage_1-146](assets/chlimage_1-146.png)

   For expired assets, the References rail displays the expiry status **[!UICONTROL Asset is Expired]** at the top.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   If the asset has expired subassets, the References rail displays the status **[!UICONTROL Asset has Expired Sub-Assets]**.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Suchen von abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Unter-Assets suchen.

1. In the Assets console, click the **[!UICONTROL Search]** in the toolbar to display the Omnisearch box.

1. Klicken Sie mit dem Cursor in das Feld Omniture Search (Suchergebnis) auf die Eingabetaste, um die Seite Search Results (Suchergebnisse) anzuzeigen.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Klicken Sie auf das Experience Manager-Logo, um das Suchfeld anzuzeigen.

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Klicken/tippen Sie auf die Option **[!UICONTROL Gültigkeitsstatus]**, um sie zu erweitern.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die abgelaufenen Assets werden in den Suchergebnissen angezeigt.

   ![chlimage_1-153](assets/chlimage_1-153.png)

When you choose the **Expired** option, the Assets console only displays the expired assets and subassets that are referenced by compound assets. Die ebenenübergreifenden Assets, die auf abgelaufene Unter-Assets verweisen, werden nicht sofort nach Ablauf eines Unter-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem AEM Assets bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Unter-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planerzyklus liegt, erkennt der Planer das Asset als abgelaufenes Asset, wenn es das nächste Mal aufgeführt wird, und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass der Planer abgelaufene Assets im aktuellen Zyklus erkennt, untersucht der Planer diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

To enable the Assets console to display the referencing compound assets along with the expired subassets, configure an **Adobe CQ DAM Expiry Notification** workflow in AEM Configuration Manager.

1. Öffnen Sie AEM Configuration Manager.
1. Choose **[!UICONTROL Adobe CQ DAM Expiry Notification]**. By default, **[!UICONTROL Time based Scheduler]** is selected, which schedules a job to check at a specific time whether an asset has expired subassets. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Unter-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. To run the job periodically, clear the **[!UICONTROL Time Based Scheduler Rule]** field and modify the time in seconds in the **[!UICONTROL Periodic Scheduler]** field. Beispiel: Der Beispielausdruck &quot;0 0 0 &amp;ast; &amp;ast; ?&#39; löst den Auftrag um 00:00 Uhr aus.
1. Select **[!UICONTROL send email]** to receive emails when an asset expires.

   >[!NOTE]
   >
   >Nur der Ersteller eines Assets (die Person, die ein bestimmtes Asset in AEM Assets hochlädt) erhält eine E-Mail, wenn das Asset abläuft. Weitere Einzelheiten zur Konfiguration von E-Mail-Benachrichtigungen in AEM im Allgemeinen finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md).

1. Geben Sie im Feld **[!UICONTROL Vorabbenachrichtigung in Sekunden]** den Zeitpunkt in Sekunden vor dem Ablauf eines Assets an, zu dem Sie über den bevorstehenden Ablauf benachrichtigt werden möchten. Wenn Sie ein Administrator oder der Ersteller des Assets sind, werden Sie vor Ablauf des Assets darüber informiert, dass das Asset nach dem angegebenen Zeitraum ablaufen wird.

   Nachdem das Asset abgelaufen ist, erhalten Sie eine weitere Benachrichtigung, die den Ablauf bestätigt. Außerdem werden die abgelaufenen Assets deaktiviert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Asset-Zustände {#asset-states}

Die Konsole „Assets“ in Adobe Experience Manager (AEM) Assets kann verschiedene Zustände für Assets anzeigen. Abhängig vom aktuellen Zustand eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der Assets-Benutzeroberfläche ein Asset aus.

   ![chlimage_1-155](assets/chlimage_1-155.png)

1. Tippen Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichen]** . Wenn die Symbolleiste keine **Veröffentlichung** enthält, tippen Sie in der Symbolleiste auf **[!UICONTROL Mehr]** und suchen Sie die Option &quot; **[!UICONTROL Veröffentlichen]** &quot;.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Choose **[!UICONTROL Publish]** from the menu, and then close the confirmation dialog.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. In the Assets UI, select an asset and tap **[!UICONTROL Properties]** to display its asset details page.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. In the Advanced tab, and set an expiration date for the asset from the **[!UICONTROL Expires]** field under.

   ![chlimage_1-159](assets/chlimage_1-159.png)

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL Close]** to display the Asset console.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In the list view, the status of the asset is displayed as **[!UICONTROL Expired]**.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Wählen Sie in der Konsole „Assets“ einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Review and approve/reject the assets in the review task and click **[!UICONTROL Complete]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden die Status der Genehmigung und des Ablaufs in den entsprechenden Spalten angezeigt.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Um nach Assets basierend auf ihrem Status zu suchen, tippen Sie auf **[!UICONTROL Suchen]** , um die Suchleiste anzuzeigen.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Drücken Sie die Eingabetaste und tippen Sie dann auf **[!UICONTROL GlobalNav]** , um das Suchfeld anzuzeigen.
1. In the Search panel, tap/click **[!UICONTROL Publish Status]** and select **[!UICONTROL Published]** to search for published assets in AEM Assets.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Tap/click **[!UICONTROL Approval Status]** and click the appropriate option to search for approved or rejected assets.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. To search for assets based on their expiration status, select **[!UICONTROL Expiry Status]** in the Search panel and choose the appropriate option.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe bestätigt wurden und noch nicht abgelaufen sind, indem Sie die entsprechenden Optionen in den Suchfacetten auswählen.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management in Assets {#digital-rights-management-in-assets-1}

Diese Funktion setzt die Annahme der Lizenzvereinbarung zwingend voraus. Erst nach diesem Schritt können lizenzierte Assets von Adobe Experience Manager (AEM) Assets heruntergeladen werden.

If you select a protected asset and tap **[!UICONTROL Download]**, you are redirected to a license page where you accept the license agreement. Wenn Sie die Lizenzvereinbarung nicht annehmen, wird die Schaltfläche **[!UICONTROL Herunterladen]** deaktiviert.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der CQ-Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um nicht formatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>The location `/etc/dam/drm/licenses` used for storing licenses in earlier releases of AEM is deprecated.
>
>If you create or modify licence pages, or port them from previous AEM releases, Adobe recommends that you store them under `/apps/settings/dam/drm/licenses` or `/conf/&ast;/settings/dam/drm/licenses`.

### Herunterladen von DRM-geschützten Assets {#downloading-drm-assets}

1. In the Card view, select the assets you want to download and click **[!UICONTROL Download]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie von der Liste herunterladen möchten.
1. Wählen Sie im Lizenzfenster **[!UICONTROL Zustimmen]**. Möglicherweise erscheint ein Häkchen neben dem Asset, für das Sie die Lizenzvereinbarung angenommen haben. Tap/click the **[!UICONTROL Download]** button.

   >[!NOTE]
   >
   >The **[!UICONTROL Download]** button is enabled only when you choose to agree to the license agreement for a protected asset. However, if your selection comprises both protected and unprotected assets, only the protected assets are listed in the left pane and the **[!UICONTROL Download]** button is enabled to download the unprotected assets. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig annehmen, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. In the dialog, tap/click **[!UICONTROL Download]** to download the asset or its renditions.
