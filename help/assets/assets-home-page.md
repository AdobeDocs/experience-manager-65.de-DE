---
title: '"[!DNL Assets] Erlebnis der Homepage"'
description: Personalisieren Sie die [!DNL Experience Manager Assets] Startseite für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der letzten Aktivitäten rund um Assets.
contentOwner: AG
feature: Developer Tools, Asset Management
role: Admin, User
exl-id: 042bd959-256a-4794-a34d-0848a6b8840d
source-git-commit: e24316cb9495a552960ae0620e4198f10a08b691
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 36%

---

# [!DNL Adobe Experience Manager Assets] Startseiten-Erlebnis {#aem-assets-home-page-experience}

Personalisieren Sie die [!DNL Adobe Experience Manager Assets] Startseite für ein umfangreiches Begrüßungsbildschirm-Erlebnis, einschließlich einer Momentaufnahme der letzten Aktivitäten rund um Assets.

[!DNL Assets] Die Startseite bietet ein umfangreiches und personalisiertes Begrüßungsbildschirm-Erlebnis, das eine Momentaufnahme der letzten Aktivitäten enthält, z. B. der kürzlich angezeigten oder hochgeladenen Assets.

Die [!DNL Assets] Homepage ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Öffnen Sie [!DNL Experience Manager] Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie die **[!UICONTROL Day CQ DAM Event Recorder]** Dienst.
1. Wählen Sie die **[!UICONTROL Aktivieren dieses Dienstes]** zur Aktivierung der Aktivitätsaufzeichnung.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Aus dem **[!UICONTROL Ereignistypen]** , wählen Sie die Ereignisse aus, die aufgezeichnet werden sollen, und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie die **[!UICONTROL Feature Flag &quot;DAM Asset Home Page&quot;]** Dienst von Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Wählen Sie die `isEnabled.name` -Option zum Aktivieren der [!DNL Assets] Startseitenfunktion. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie die **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Asset-Homepage aktivieren]**. Speichern Sie die Änderungen.

   ![Asset-Homepage im Dialogfeld &quot;Benutzereinstellungen&quot;aktivieren](assets/Annotation-color.png)

Nach der Aktivierung der [!DNL Assets] Startseite, navigieren Sie zur [!DNL Assets] -Benutzeroberfläche entweder über die Navigationsseite oder direkt über die URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam`.

![Erlebnislink auf der Assets-Benutzeroberfläche konfigurieren](assets/config-experience-link.png)

Klicken Sie auf **[!UICONTROL Klicken Sie hier , um Ihren Erlebnislink zu konfigurieren.]** um Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profilbild hinzuzufügen.

Die [!DNL Assets] Die Startseite enthält die folgenden Abschnitte:

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

**Aktivität**: Unter diesem Abschnitt wird die **[!UICONTROL Meine Aktivität]** Widget zeigt die letzten Aktivitäten an, die der angemeldete Benutzer mit Assets ausgeführt hat (einschließlich Assets ohne Ausgabedarstellungen), z. B. Asset-Uploads, -Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und Teilen-Vorgänge.

**Zuletzt**: Die **[!UICONTROL Kürzlich angezeigt]** -Widget unter diesem Abschnitt zeigt die kürzlich vom angemeldeten Benutzer aufgerufenen Entitäten an, darunter Ordner, Sammlungen und Projekte.

**Discover**: Die **[!UICONTROL Neu]** Widget unter diesem Abschnitt zeigt die Assets und Ausgabedarstellungen an, die kürzlich in die [!DNL Assets] Implementierung.

Um die Bereinigung der Benutzeraktivitätsdaten zu ermöglichen, aktivieren Sie die **[!UICONTROL DAM-Ereignisbereinigungsdienst]** von Configuration Manager aus. Nachdem Sie den Dienst aktiviert haben, werden die Aktivitäten des angemeldeten Benutzers, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Aktivieren der [!UICONTROL Day CQ DAM Event Recorder] und [!UICONTROL DAM-Ereignisbereinigung] -Dienste erhöhen die Schreibvorgänge in JCR und die Suchindizierung, wodurch die Belastung für die [!DNL Experience Manager] Server. Die zusätzliche Belastung der [!DNL Experience Manager] -Server kann sich auf seine Leistung auswirken.

>[!CAUTION]
>
>Erfassen, Filtern und Bereinigen der für [!DNL Assets] Homepage bringt einen Mehraufwand für die Leistung mit sich. Daher sollten Administratoren die Homepage für Zielbenutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Administratoren Aufzeichnungsaktivitäten von bestimmten Benutzern unterbinden, indem sie den [!UICONTROL Day CQ DAM Event Recorder][!UICONTROL  vom Configuration Manager aus konfigurieren].
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
