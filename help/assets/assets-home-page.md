---
title: Adobe Experience Manager Assets Startseite Experience
description: Personalisieren Sie die Experience Manager Assets-Startseite, um eine umfassende Bildschirmdarstellung zu erhalten, einschließlich einer Momentaufnahme der letzten Aktivitäten um Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 678e91699523c22a7048bd7b344fa539b849ae8b
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 35%

---


# Adobe Experience Manager Assets Startseite Experience {#aem-assets-home-page-experience}

Personalisieren Sie die Adobe Experience Manager Assets-Startseite, um eine umfassende Bildschirmdarstellung zu erhalten, einschließlich einer Momentaufnahme der letzten Aktivitäten um Assets.

Die Assets-Startseite bietet eine umfassende und personalisierte Benutzeroberfläche für den Begrüßungsbildschirm, die eine Momentaufnahme der letzten Aktivitäten enthält, z. B. Assets, die kürzlich angezeigt oder hochgeladen wurden.

Die Startseite &quot;Assets&quot;ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Öffnen Sie Experience Manager Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ DAM Event Recorder]** service.
1. Select the **[!UICONTROL Enable this service]** to enable activity recording.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. From the **[!UICONTROL Event Types]** list, select the events to be recorded and save the changes.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Open the **[!UICONTROL DAM Asset Home Page Feature Flag]** service from Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Select the `isEnabled.name` option to enable the Assets Home page feature. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Open the **[!UICONTROL User Preferences]** dialog, and select **[!UICONTROL Enable Assets Home Page]**. Speichern Sie die Änderungen.

   ![Aktivieren der Asset-Startseite im Dialogfeld &quot;Benutzereinstellungen&quot;](assets/Annotation-color.png)

After enabling the Assets Home page, navigate to the Assets user interface either from the Navigation page or access it directly from the URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam`.

![Erlebnislink auf der Benutzeroberfläche &quot;Assets&quot;konfigurieren](assets/config-experience-link.png)

Click the **[!UICONTROL Click here to configure your experience link]** to add your username, background image, and profile image.

Die Assets-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt** 

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Außerdem werden Ihr Profil und ein Begrüßungsbild angezeigt (falls bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt** 

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet fertige Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das Widget &quot; **[!UICONTROL Meine Aktivität]** &quot;aktuelle Aktivitäten an, die der angemeldete Benutzer mit Assets (einschließlich Assets ohne Ausgabeformate) durchgeführt hat, z. B. Asset-Uploads, Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und &quot;Teilen&quot;-Klicks.

**Zuletzt**: Das **[!UICONTROL kürzlich angezeigte]** Widget unter diesem Abschnitt zeigt kürzlich aufgerufene Entitäten des angemeldeten Benutzers an, einschließlich Ordner, Sammlungen und Projekte.

**Discover**: Das **[!UICONTROL neue]** Widget unter diesem Abschnitt zeigt die Assets und Darstellungen an, die kürzlich in die Asset-Bereitstellung hochgeladen wurden.

To enable purging of user activity data, enable the **[!UICONTROL DAM Event Purge Service]** from Configuration Manager. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Enabling the [!UICONTROL Day CQ DAM Event Recorder] and [!UICONTROL DAM Event Purge] services increases write operations to JCR and search indexing, which significantly increases the load on the Experience Manager server. Die zusätzliche Belastung des Experience Manager-Servers kann sich auf seine Leistung auswirken.

>[!CAUTION]
>
>Das Erfassen, Filtern und Bereinigen der für die Asset-Startseite erforderlichen Aktivitäten führt zu einem Leistungsaufwand. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den [!UICONTROL Day CQ DAM Event Recorder][!UICONTROL  vom Configuration Manager aus konfigurieren].
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
