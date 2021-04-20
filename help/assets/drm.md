---
title: Digital Rights Management der Vermögenswerte
description: Erfahren Sie, wie Sie den Asset-Ablaufstatus und Informationen für lizenzierte Assets in  [!DNL Experience Manager]  verwalten.
contentOwner: AG
role: Business Practitioner, Administrator
feature: DRM,Asset Management
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '1404'
ht-degree: 79%

---


# Digital Rights Management für Assets {#digital-rights-management-in-assets}

Digitale Assets sind oftmals mit einer Lizenz verbunden, in der die Bedingungen und die Nutzungsdauer festgelegt sind. Da [!DNL Adobe Experience Manager Assets] vollständig mit der [!DNL Experience Manager]-Plattform integriert ist, können Sie Asset-Ablaufinformationen und -Status effizient verwalten. Sie können Lizenzinformationen mit Assets verknüpfen.

## Asset-Ablauf {#asset-expiration}

Der Asset-Ablauf ist eine effektive Möglichkeit zum Durchsetzen von Lizenzanforderungen für Assets. Wenn ein veröffentlichtes Asset abläuft, wird seine Veröffentlichung aufgehoben und damit die Möglichkeit einer Lizenzverletzung unterbunden. Ein Benutzer ohne Administratorrechte kann ein abgelaufenes Asset weder bearbeiten, kopieren, verschieben, veröffentlichen noch herunterladen.

Sie können den Ablaufstatus eines Assets in der Konsole [!DNL Assets] sowohl in der Ansicht &quot;card&quot;als auch in der  &quot;Liste&quot;Ansicht haben.

![expired_Flag_Liste](assets/expired_flag_list.png)

*Abbildung: In der Ansicht &quot;Liste&quot;wird in der Spalte &quot;  Status&quot;das   Abgelaufene Banner angezeigt.*

Sie können den Ablaufstatus eines Assets in der linken Leiste unter [!UICONTROL Zeitschiene] Ansicht werden.

![chlimage_1-144](assets/chlimage_1-144.png)

>[!NOTE]
>
>Das Ablaufdatum eines Assets wird für Benutzer in verschiedenen Zeitzonen unterschiedlich angezeigt.

Sie können den Ablaufstatus von Assets auch in der Leiste **[!UICONTROL References]** Ansicht werden. Hier werden der Asset-Ablaufstatus und die Beziehungen zwischen ebenenübergreifenden Assets und referenzierten Teil-Assets, Sammlungen und Projekten verwaltet.

1. Navigieren Sie zu dem Asset, für das Sie referenzierende Web-Seiten und ebenenübergreifende Assets anzeigen möchten.
1. Wählen Sie das Asset aus und öffnen Sie **[!UICONTROL References]** in der linken Leiste. Bei abgelaufenen Assets zeigt die Leiste [!UICONTROL References] den Ablaufstatus **[!UICONTROL Asset abgelaufen]** oben an.

   ![chlimage_1-147](assets/chlimage_1-147.png)

   Wenn das Asset abgelaufene Teilassets enthält, zeigt die Leiste [!UICONTROL References] den Status **[!UICONTROL Asset hat abgelaufene Unterelemente]** an.

   ![chlimage_1-148](assets/chlimage_1-148.png)

### Suchen nach abgelaufenen Assets {#search-expired-assets}

Sie können im Suchfeld nach abgelaufenen Assets einschließlich abgelaufener Teil-Assets suchen.

1. Klicken Sie in der [!DNL Assets]-Konsole in der Symbolleiste auf **[!UICONTROL Suchen]**, um das Omnisearch-Feld anzuzeigen.

1. Wählen Sie bei in das Omnisearch-Feld gesetztem Cursor die Eingabetaste `Enter` aus, um die Seite mit den Suchergebnissen anzuzeigen.
1. Öffnen Sie das Suchfeld in der linken Leiste. Klicken Sie auf die Option **[!UICONTROL Ablaufstatus]**, um sie zu erweitern.

   ![chlimage_1-152](assets/chlimage_1-152.png)

1. Wählen Sie **[!UICONTROL Abgelaufen]**. Nach dem Filtern der Suchergebnisse werden nur die abgelaufenen Assets angezeigt.

Bei Auswahl der Option **[!UICONTROL Abgelaufen]** zeigt die [!DNL Assets]-Konsole nur die abgelaufenen Assets und Teil-Assets an, auf die von ebenenübergreifenden Assets verwiesen wird. Die ebenenübergreifenden Assets, die auf abgelaufene Teil-Assets verweisen, werden nicht sofort nach Ablauf eines Teil-Assets angezeigt. Stattdessen werden sie angezeigt, nachdem [!DNL Experience Manager] bei der nächsten Ausführung des Planers erkennt, dass sie auf abgelaufene Teil-Assets verweisen.

Wenn Sie das Ablaufdatum eines veröffentlichten Assets in ein Datum ändern, das vor dem aktuellen Planungszyklus liegt, erkennt die Planung das Asset bei der nächsten Ausführung als abgelaufenes Asset und spiegelt dementsprechend seinen Status wider.

Wenn eine Störung oder ein Fehler verhindert, dass die Planung abgelaufene Assets im aktuellen Zyklus erkennt, untersucht die Planung diese Assets im nächsten Zyklus erneut und erkennt dann, dass sie abgelaufen sind.

Damit die [!DNL Assets]-Konsole die verweisenden ebenenübergreifenden Assets neben den abgelaufenen Teil-Assets anzeigt, konfigurieren Sie in [!DNL Experience Manager] Configuration Manager einen Workflow für **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigungen]**.

1. Öffnen Sie [!DNL Experience Manager] Configuration Manager.
1. Wählen Sie **[!UICONTROL Adobe CQ DAM-Ablaufbenachrichtigung]** aus. Standardmäßig wird **[!UICONTROL Zeitbasierter Planer]** ausgewählt, womit ein Auftrag geplant wird, der zu einem bestimmten Zeitpunkt prüft, ob ein Asset abgelaufene Teil-Assets aufweist. Nach Abschluss des Auftrags werden Assets mit abgelaufenen Teil-Assets und verwiesenen Assets in den Suchergebnissen als abgelaufen angezeigt.

1. Um den Auftrag regelmäßig auszuführen, löschen Sie das Feld **[!UICONTROL Regel für zeitbasierten Planer]** und ändern Sie die Dauer in Sekunden im Feld **[!UICONTROL Periodischer Planer]**. Der Beispielauftrag wird beispielsweise mit dem Ausdruck `0 0 0 &ast; &ast; ?` um 00 Uhr Trigger.
1. Wählen Sie **[!UICONTROL E-Mail senden]** aus, um bei Ablauf von Assets E-Mails zu erhalten.

   >[!NOTE]
   >
   >Wenn das Asset abläuft, erhält nur der Asset-Ersteller (die Person, die ein bestimmtes Asset auf [!DNL Assets] hochlädt) eine E-Mail. Weitere Informationen zum Konfigurieren von E-Mail-Benachrichtigungen auf der Ebene [!DNL Experience Manager] finden Sie unter [Konfigurieren der E-Mail-Benachrichtigung](/help/sites-administering/notification.md).

1. Geben Sie im Feld **[!UICONTROL Vorabbenachrichtigung in Sekunden]** den Zeitpunkt in Sekunden vor dem Ablauf eines Assets an, zu dem Sie über den bevorstehenden Ablauf benachrichtigt werden möchten. Asset-Ersteller erhalten vor Ablauf des Assets eine Meldung, die Sie darüber informiert, dass das Asset nach der angegebenen Zeit abläuft. Nachdem das Asset abgelaufen ist, erhalten Sie eine weitere Benachrichtigung, die den Ablauf bestätigt. Außerdem werden die abgelaufenen Assets deaktiviert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Asset-Zustände {#asset-states}

Die [!DNL Assets]-Konsole kann verschiedene Status für Assets anzeigen. Abhängig vom aktuellen Status eines bestimmten Assets zeigt die zugehörige Kartenansicht eine Beschreibung des Zustands an, z. B. „Abgelaufen“, „Veröffentlicht“, „Genehmigt“, „Abgelehnt“ usw.

1. Wählen Sie in der [!DNL Assets]-Benutzeroberfläche ein Asset aus.
1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichen]**. Wenn **Veröffentlichen** in der Symbolleiste nicht angezeigt wird, klicken Sie auf **[!UICONTROL Mehr]** in der Symbolleiste und suchen Sie die Option **[!UICONTROL Veröffentlichen]** ![Veröffentlichen](assets/do-not-localize/publish-globe.png).
1. Wählen Sie im Menü **[!UICONTROL Veröffentlichen]** aus und schließen Sie danach das Bestätigungsdialogfeld.
1. Beenden Sie den Auswahlmodus. Der Veröffentlichungsstatus des Assets wird in der Kartenansicht im unteren Bereich der Miniaturansicht des Assets angezeigt. In der Listenansicht zeigt die Spalte „Veröffentlicht“ die Zeit an, zu der das Asset veröffentlicht wurde.

   ![chlimage_1-157](assets/chlimage_1-157.png)

1. Um die Seite mit den Asset-Details anzuzeigen, wählen Sie in der [!DNL Assets]-Oberfläche ein Asset aus und klicken Sie auf **[!UICONTROL Eigenschaften]** ![Eigenschaften der Ansicht](assets/do-not-localize/info-circle-icon.png).

1. Geben Sie auf der Registerkarte [!UICONTROL Erweitert] ein Ablaufdatum für das Asset im Feld **[!UICONTROL Ablaufdatum]** an.

   ![Asset-Ablaufdatum und -Uhrzeit im Feld &quot;Abgelaufen&quot;](assets/asset-properties-advanced-tab.png)

   *Abbildung:  [!UICONTROL Registerkarte &quot;] Erweitert&quot;auf der Seite &quot;Asset-  Eigenschaften&quot;, um den Asset-Ablauf festzulegen.*

1. Klicken Sie auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL Schließen]**, um die Asset-Konsole anzuzeigen.
1. Der Veröffentlichungsstatus des Assets weist in der Kartenansicht im unteren Bereich der Miniaturansicht darauf hin, dass das Asset abgelaufen ist. In der Listenansicht wird der Status des Assets als **[!UICONTROL Abgelaufen]** angegeben.

   ![chlimage_1-160](assets/chlimage_1-160.png)

1. Wählen Sie in der [!DNL Assets]-Konsole einen Ordner aus und erstellen Sie eine Prüfungsaufgabe für den Ordner.
1. Prüfen und bestätigen Sie das Asset in der Prüfungsaufgabe (bzw. lehnen Sie es ab) und klicken Sie auf **[!UICONTROL Fertig]**.
1. Navigieren Sie zu dem Ordner, für den Sie die Prüfungsaufgabe erstellt haben. Der Status des Assets, das Sie bestätigt oder abgelehnt haben, wird unten in der Kartenansicht angezeigt. In der Listenansicht werden Bestätigungs- und Ablaufstatus in entsprechenden Spalten angezeigt.

   ![chlimage_1-161](assets/chlimage_1-161.png)

1. Um nach Assets basierend auf ihrem Status zu suchen, klicken Sie auf **[!UICONTROL Suche]** ![Suchoption](assets/do-not-localize/search_icon.png), um die Omniture Suchleiste anzuzeigen.
1. Wählen Sie die Eingabetaste `Return` aus und klicken Sie auf [!DNL Experience Manager], um das Suchbedienfeld anzuzeigen.
1. Klicken Sie im Suchbedienfeld auf **[!UICONTROL Veröffentlichungsstatus]** und wählen Sie **[!UICONTROL Veröffentlicht]** aus, um in [!DNL Assets] nach veröffentlichten Assets zu suchen.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Klicken Sie auf **[!UICONTROL Genehmigungsstatus]** und danach auf die entsprechende Option, um nach bestätigten oder abgelehnten Assets zu suchen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

1. Um nach Assets auf Grundlage ihres Ablaufstatus zu suchen, wählen Sie im Suchfeld **[!UICONTROL Gültigkeitsstatus]** und danach die entsprechende Option aus.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Sie können auch auf Grundlage einer Kombination von Statusangaben mit verschiedenen Suchfacetten nach Assets suchen. Sie können beispielsweise nach veröffentlichten Assets suchen, die in einer Prüfungsaufgabe bestätigt wurden und noch nicht abgelaufen sind, indem Sie die entsprechenden Optionen in den Suchfacetten auswählen.

   ![chlimage_1-166](assets/chlimage_1-166.png)

## Digital Rights Management in [!DNL Assets] {#digital-rights-management-in-assets-1}

Diese Funktion setzt die Annahme der Lizenzvereinbarung zwingend voraus. Erst nach diesem Schritt können lizenzierte Assets von [!DNL Adobe Experience Manager Assets] heruntergeladen werden.

Wenn Sie ein geschütztes Asset auswählen und auf **[!UICONTROL Herunterladen]** klicken, werden Sie auf die Lizenzseite weitergeleitet, um die Lizenzvereinbarung anzunehmen. Wenn Sie die Lizenzvereinbarung nicht annehmen, steht die Option **[!UICONTROL Herunterladen]** nicht zur Verfügung.

Falls die Auswahl mehrere geschützte Assets enthält, wählen Sie jeweils eines aus, nehmen Sie die Lizenzvereinbarung an und fahren Sie mit dem Herunterladen des Assets fort.

Ein Asset gilt als geschützt, wenn eine der folgenden Bedingungen erfüllt ist:

* Die `xmpRights:WebStatement`-Metadateneigenschaft des Assets verweist auf den Pfad der Seite, die die Lizenzvereinbarung für das Asset enthält.
* Beim Wert der `adobe_dam:restrictions`-Metadateneigenschaft des Assets handelt es sich um unformatierten HTML-Code, der die Lizenzvereinbarung angibt.

>[!NOTE]
>
>Der Speicherort `/etc/dam/drm/licenses`, der in den früheren Versionen von [!DNL Experience Manager] zum Speichern von Lizenzen verwendet wurde, wird nicht mehr unterstützt.
>
>Wenn Sie Lizenzseiten erstellen oder bearbeiten bzw. aus früheren [!DNL Experience Manager]-Versionen portieren möchten, speichern Sie diese unter `/apps/settings/dam/drm/licenses` oder `/conf/&ast;/settings/dam/drm/licenses`.

### Herunterladen von DRM-geschützten Assets {#downloading-drm-assets}

1. Wählen Sie die gewünschten Assets in der Kartenansicht aus und klicken Sie auf **[!UICONTROL Herunterladen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Copyright-Management]** das Asset aus, das Sie herunterladen möchten.
1. Wählen Sie im [!UICONTROL Lizenzfenster] die Option **[!UICONTROL Zustimmen]** aus. Neben dem Asset erscheint ein Häkchen. Klicken Sie auf die Option **[!UICONTROL Herunterladen]**.

   >[!NOTE]
   >
   >Die Option **[!UICONTROL Herunterladen]** ist nur dann verfügbar, wenn Sie der Lizenzvereinbarung für ein geschütztes Asset zustimmen. Wenn Ihre Auswahl jedoch sowohl geschützte als auch ungeschützte Assets umfasst, werden nur die geschützten Assets im Bereich aufgelistet und die Option **[!UICONTROL Herunterladen]** ist aktiviert, um die ungeschützten Assets herunterzuladen. Sie können mehrere Lizenzvereinbarungen für verschiedene geschützte Assets gleichzeitig akzeptieren, indem Sie die Assets in der Liste auswählen und anschließend auf **[!UICONTROL Zustimmen]** klicken.

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Klicken Sie im Dialogfeld auf **[!UICONTROL Herunterladen]**, um das Asset oder seine Ausgabedarstellungen herunterzuladen.
