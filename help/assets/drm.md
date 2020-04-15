---
title: Digital Rights Management in Assets
description: Erfahren Sie, wie Sie den Asset-Ablaufstatus und Informationen für lizenzierte Assets in AEM verwalten.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Digital Rights Management for digital assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da Adobe Experience Manager (AEM) Assets vollständig mit der AEM-Plattform integriert ist, können Sie Asset-Ablaufinformationen und -Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus für ein Asset in der Asset-Konsole sowohl in den Ansichten &quot;Karte&quot;als auch &quot;Liste&quot;Ansicht haben.

![expired_flag_card](assets/expired_flag_card.png)

*Abbildung: In der Ansicht der Karte zeigt ein Flag auf einem abgelaufenen Asset an*

**Listenansicht**

![expired_Flag_Liste](assets/expired_flag_list.png)

*Abbildung: In der Ansicht &quot;Liste&quot;wird in der Spalte &quot;[!UICONTROL Status]&quot;das Banner &quot;[!UICONTROL Abgelaufen]&quot;angezeigt.*

Sie können den Ablaufstatus eines Assets in der Timeline einsehen. Wählen Sie das Asset und danach im GlobalNav-Menü die Option „Timeline“ aus.

![chlimage_1-144](assets/chlimage_1-144.png)

You can also view the expiration status of assets in the **[!UICONTROL References]** rail. Hier werden der Asset-Ablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Teil-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Web-Seiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset und das Experience Manager-Logo aus.

1. Wählen Sie im Menü **[!UICONTROL Verweise]** aus.

   ![chlimage_1-146](assets/chlimage_1-146.png)

   Für abgelaufene Assets zeigt die Leiste „Verweise“ im oberen Bereich den Ablaufstatus **[!UICONTROL Asset ist abgelaufen]** an.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Sofern das Asset abgelaufene Teil-Assets aufweist, zeigt die Leiste „Verweise“ den Status **[!UICONTROL Asset enthält abgelaufene Teil-Assets]** an.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Suchen nach abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Teil-Assets suchen.

1. In the Assets console, click the **[!UICONTROL Search]** in the toolbar to display the Omnisearch box.

1. Klicken Sie mit dem Cursor in das Feld Omniture Search (Suchergebnis) auf die Eingabetaste, um die Seite Search Results (Suchergebnisse) anzuzeigen.

   ![chlimage_1-150](assets/chlimage_1-150.png)

1. Klicken Sie auf das Experience Manager-Logo, um das Suchfeld anzuzeigen.

   ![chlimage_1-151](assets/chlimage_1-151.png)

1. Click the **[!UICONTROL Expiry Status]** option to expand it.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Wählen Sie **[!UICONTROL Abgelaufen]** aus. Die abgelaufenen Assets werden in den Suchergebnissen angezeigt.

   ![chlimage_1-153](assets/chlimage_1-153.png)

Bei Auswahl der Option **Abgelaufen** zeigt die Konsole „Assets“ nur die abgelaufenen Assets und Teil-Assets an, auf die von ebenenübergreifenden Assets verwiesen wird. Die ebenenübergreifenden Assets, die auf abgelaufene Unter-Assets verweisen, werden nicht sofort nach Ablauf eines Unter-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem AEM Assets bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Unter-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planerzyklus liegt, erkennt der Planer das Asset als abgelaufenes Asset, wenn es das nächste Mal aufgeführt wird, und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass der Planer abgelaufene Assets im aktuellen Zyklus erkennt, untersucht der Planer diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

Damit die Konsole „Assets“ die verweisenden ebenenübergreifenden Assets neben den abgelaufenen Teil-Assets anzeigt, konfigurieren Sie in AEM Configuration Manager einen Workflow für **Adobe CQ DAM-Ablaufbenachrichtigungen**.

1. Öffnen Sie AEM Configuration Manager.
1. Wählen Sie **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigung]** aus. Standardmäßig wird **[!UICONTROL Zeitbasierter Planer]** ausgewählt, womit ein Auftrag geplant wird, der zu einem bestimmten Zeitpunkt prüft, ob ein Asset abgelaufene Teil-Assets aufweist. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Teil-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

   ![chlimage_1-154](assets/chlimage_1-154.png)

1. Um den Auftrag regelmäßig auszuführen, löschen Sie das Feld **[!UICONTROL Regel für zeitbasierten Planer]** und ändern Sie die Dauer in Sekunden im Feld **[!UICONTROL Periodischer Planer]**. Beispiel: Der Beispielausdruck „0 0 0 &amp;ast; &amp;ast; ?“ löst den Auftrag um 00:00 Uhr aus.
1. Wählen Sie **[!UICONTROL E-Mail senden]** aus, um bei Ablauf von Assets E-Mails zu erhalten.

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

1. Click **[!UICONTROL Publish]** from the toolbar. If you don&#39;t see **Publish** on the toolbar, click **[!UICONTROL More]** on the toolbar and locate **[!UICONTROL Publish]** option.

   ![chlimage_1-156](assets/chlimage_1-156.png)

1. Wählen Sie im Menü **[!UICONTROL Veröffentlichen]** aus und schließen Sie danach das Bestätigungsdialogfeld.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. In the Assets interface, select an asset and click **[!UICONTROL Properties]** to display its asset details page.

   ![chlimage_1-158](assets/chlimage_1-158.png)

1. In the Advanced tab, set an expiration date for the asset from the **[!UICONTROL Expires]** field.

   ![Asset-Ablaufdatum und -Uhrzeit im Feld &quot;Abgelaufen&quot;](assets/asset-properties-advanced-tab.png)


   *Abbildung: Erweiterte Registerkarte in Asset-Eigenschaften zum Festlegen des Asset-Ablaufs*

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**, um die Konsole „Assets“ anzuzeigen.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In der Listenansicht wird der Status des Assets als **[!UICONTROL Abgelaufen]** angegeben.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Wählen Sie in der Konsole „Assets“ einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Prüfen und bestätigen Sie das Asset in der Prüfungsaufgabe (bzw. lehnen Sie es ab) und klicken Sie auf **[!UICONTROL Fertig]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden Bestätigungs- und Ablaufstatus in entsprechenden Spalten angezeigt.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. To search for assets based on their status, click **[!UICONTROL Search]** to display the Omnisearch bar.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Drücken Sie die Eingabetaste und klicken Sie dann auf **[!UICONTROL GlobalNav]** , um das Suchfeld anzuzeigen.
1. In the Search panel, click **[!UICONTROL Publish Status]** and select **[!UICONTROL Published]** to search for published assets in AEM Assets.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Click **[!UICONTROL Approval Status]** and click the appropriate option to search for approved or rejected assets.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Um nach Assets auf Grundlage ihres Ablaufstatus zu suchen, wählen Sie im Suchfeld **[!UICONTROL Gültigkeitsstatus]** und danach die entsprechende Option aus.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe bestätigt wurden und noch nicht abgelaufen sind, indem Sie die entsprechenden Optionen in den Suchfacetten auswählen.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management in Assets {#digital-rights-management-in-assets-1}

Diese Funktion erzwingt die Annahme der Lizenzvereinbarung, bevor Sie ein lizenziertes Asset aus Adobe Experience Manager Assets herunterladen können.

If you select a protected asset and click **[!UICONTROL Download]**, you are redirected to a license page where you accept the license agreement. Wenn Sie die Lizenzvereinbarung nicht annehmen, wird die Schaltfläche **[!UICONTROL Herunterladen]** deaktiviert.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* The asset metadata property `xmpRights:WebStatement` points to the path of the page that contains the license agreement for the asset.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um nicht formatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>Der Speicherort `/etc/dam/drm/licenses`, der in den früheren Versionen von AEM zum Speichern von Lizenzen verwendet wurde, wird nicht mehr unterstützt.
>
>If you create or modify licence pages, or port them from previous AEM releases, Adobe recommends that you store them under `/apps/settings/dam/drm/licenses` or `/conf/&ast;/settings/dam/drm/licenses`.

### Herunterladen von DRM-geschützten Assets {#downloading-drm-assets}

1. In the Card view, select the assets you want to download and click **[!UICONTROL Download]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im Lizenzfenster **[!UICONTROL Zustimmen]**. Möglicherweise erscheint ein Häkchen neben dem Asset, für das Sie die Lizenzvereinbarung angenommen haben. Klicken Sie auf die Schaltfläche **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Die Schaltfläche **[!UICONTROL Herunterladen]** ist nur dann verfügbar, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch nicht geschützte Assets enthält, erscheinen nur die geschützten Assets im linken Bereich und die Schaltfläche **[!UICONTROL Herunterladen]** ist für den Download der nicht geschützten Assets verfügbar. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig annehmen, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. In the dialog, click **[!UICONTROL Download]** to download the asset or its renditions.
