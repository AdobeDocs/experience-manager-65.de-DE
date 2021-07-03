---
title: '[!DNL Assets] Erlebnis der Homepage'
description: Personalisieren Sie die Startseite [!DNL Experience Manager Assets] für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der aktuellen Aktivitäten rund um Assets.
contentOwner: AG
feature: Entwicklertools, Asset Management
role: Admin, User
exl-id: 042bd959-256a-4794-a34d-0848a6b8840d
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 36%

---

# [!DNL Adobe Experience Manager Assets] Startseiten-Erlebnis {#aem-assets-home-page-experience}

Personalisieren Sie die Startseite [!DNL Adobe Experience Manager Assets] für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der aktuellen Aktivitäten rund um Assets.

[!DNL Assets] Die Startseite bietet ein umfangreiches und personalisiertes Begrüßungsbildschirm-Erlebnis, das eine Momentaufnahme der letzten Aktivitäten enthält, z. B. der kürzlich angezeigten oder hochgeladenen Assets.

Die Startseite [!DNL Assets] ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Öffnen Sie [!DNL Experience Manager] Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Event Recorder]** .
1. Wählen Sie **[!UICONTROL Aktivieren Sie diesen Dienst]**, um die Aktivitätsaufzeichnung zu aktivieren.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Wählen Sie in der Liste **[!UICONTROL Ereignistypen]** die Ereignisse aus, die aufgezeichnet werden sollen, und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie den Dienst **[!UICONTROL DAM Asset Home Page Feature Flag]** im Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Wählen Sie die Option `isEnabled.name` aus, um die Funktion [!DNL Assets] Startseite zu aktivieren. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie das Dialogfeld **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Asset-Homepage aktivieren]** aus. Speichern Sie die Änderungen.

   ![Asset-Homepage im Dialogfeld &quot;Benutzereinstellungen&quot;aktivieren](assets/Annotation-color.png)

Nachdem Sie die Startseite [!DNL Assets] aktiviert haben, navigieren Sie zur Benutzeroberfläche [!DNL Assets] entweder über die Navigationsseite oder greifen Sie direkt über die URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam` zu.

![Erlebnislink auf der Assets-Benutzeroberfläche konfigurieren](assets/config-experience-link.png)

Klicken Sie auf **[!UICONTROL Klicken Sie hier , um Ihren Erlebnislink]** zu konfigurieren und Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profilbild hinzuzufügen.

Die Homepage [!DNL Assets] enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt** 

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Darüber hinaus werden Ihr Profilbild und ein Willkommensbild angezeigt (sofern bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt** 

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet fertige Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das Widget  **[!UICONTROL Meine]** Aktivität die letzten Aktivitäten an, die der angemeldete Benutzer mit Assets ausgeführt hat (einschließlich Assets ohne Ausgabedarstellungen), z. B. Asset-Uploads, -Downloads, Asset-Erstellung, -Bearbeitungen, Kommentare, Anmerkungen und &quot;Teilen&quot;-Klicks.

**Zuletzt**: Das Widget  **[!UICONTROL Kürzlich]** angezeigte Anzeigen unter diesem Abschnitt zeigt kürzlich aufgerufene Entitäten, auf die der angemeldete Benutzer zugegriffen hat, einschließlich Ordnern, Sammlungen und Projekten.

**Discover**: Das  **** Neue Widget unter diesem Abschnitt zeigt die Assets und Ausgabedarstellungen an, die kürzlich in die  [!DNL Assets] Bereitstellung hochgeladen wurden.

Um die Bereinigung der Benutzeraktivitätsdaten zu aktivieren, aktivieren Sie den **[!UICONTROL DAM-Ereignisbereinigungsdienst]** in Configuration Manager. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Durch die Aktivierung der Dienste [!UICONTROL Day CQ DAM Event Recorder] und [!UICONTROL DAM Event Purge] werden die Schreibvorgänge in JCR und die Suchindizierung erhöht, wodurch die Last auf dem [!DNL Experience Manager]-Server deutlich erhöht wird. Die zusätzliche Belastung des [!DNL Experience Manager]-Servers kann sich auf seine Leistung auswirken.

>[!CAUTION]
>
>Die Erfassung, Filterung und Bereinigung von Benutzeraktivitäten, die für die [!DNL Assets]-Startseite erforderlich sind, verursachen einen Mehraufwand für die Leistung. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den [!UICONTROL Day CQ DAM Event Recorder][!UICONTROL  vom Configuration Manager aus konfigurieren].
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
