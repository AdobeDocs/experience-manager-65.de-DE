---
title: '[!DNL Assets]-Startseiten-Erlebnis'
description: Personalisieren Sie die [!DNL Experience Manager Assets]-Startseite, um Benutzenden ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.
contentOwner: AG
feature: Asset Management
role: Admin, User
exl-id: 042bd959-256a-4794-a34d-0848a6b8840d
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: 7d2b2ec8-499c-5434-9ffd-9218cd71f683
    internal-label: Asset Management
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 96%
---
# [!DNL Adobe Experience Manager Assets]-Startseiten-Erlebnis {#aem-assets-home-page-experience}

Personalisieren Sie die [!DNL Adobe Experience Manager Assets]-Startseite, um Benutzenden ein ansprechendes Erlebnis auf dem Willkommensbildschirm zu bieten, einschließlich einer Übersicht der letzten Aktivitäten rund um Assets.

Die [!DNL Assets]-Startseite bietet ein ansprechendes und personalisiertes Willkommenserlebnis, einschließlich einer Übersicht der letzten Aktivitäten, wie z. B. kürzlich angezeigte oder hochgeladene Assets.

Die [!DNL Assets]-Startseite ist standardmäßig deaktiviert. Gehen Sie wie folgt vor, um sie zu aktivieren:

1. Öffnen Sie [!DNL Experience Manager] Configuration Manager `https://[aem_server]:[port]/system/console/configMgr`.
1. Öffnen Sie den Dienst **[!UICONTROL Day CQ DAM Event Recorder]**.
1. Wählen Sie **[!UICONTROL Diesen Dienst aktivieren]** aus, um die Aktivitätsaufzeichnung zu aktivieren.

   ![chlimage_1-250](assets/chlimage_1-250.png)

1. Wählen Sie aus der Liste **[!UICONTROL Ereignistypen]** die Ereignisse aus, die aufgezeichnet werden sollen, und speichern Sie die Änderungen.

   >[!CAUTION]
   >
   >Die Aktivierung der Optionen „Angezeigte Assets“, „Angezeigte Projekte“ und „Angezeigte Sammlungen“ erhöht die Anzahl der aufgezeichneten Ereignisse erheblich.

1. Öffnen Sie den Dienst **[!UICONTROL DAM Assets-Startseitenfunktion-Flag]** von Configuration Manager aus `https://[aem_server]:[port]/system/console/configMgr`.
1. Wählen Sie die Option `isEnabled.name` aus, um die [!DNL Assets]-Startseitenfunktion zu aktivieren. Speichern Sie die Änderungen.

   ![chlimage_1-251](assets/chlimage_1-251.png)

1. Öffnen Sie das Dialogfeld **[!UICONTROL Benutzereinstellungen]** und wählen Sie **[!UICONTROL Assets-Startseite aktivieren]** aus. Speichern Sie die Änderungen.

   ![Asset-Startseite im Dialogfeld „Benutzereinstellungen“ aktivieren](assets/Annotation-color.png)

Nach der Aktivierung der [!DNL Assets]-Startseite navigieren Sie entweder über die Navigationsseite oder direkt über die URL `https://[aem_server]:[port]/aem/assetshome.html/content/dam` zur [!DNL Assets]-Benutzeroberfläche.

![Erlebnis-Link auf der Assets-Benutzeroberfläche konfigurieren](assets/config-experience-link.png)

Klicken Sie auf **[!UICONTROL Hier klicken, um Ihr Erlebnis zu konfigurieren]**, um Ihren Benutzernamen, Ihr Hintergrundbild und Ihr Profilbild hinzuzufügen.

Die [!DNL Assets]-Startseite enthält die folgenden Abschnitte:

* Begrüßungsabschnitt
* Widget-Abschnitt

**Begrüßungsabschnitt**

Wenn Ihr Profil vorhanden ist, wird im Begrüßungsabschnitt eine Begrüßungsnachricht für Sie angezeigt. Darüber hinaus werden Ihr Profilbild und ein Begrüßungsbild angezeigt (wenn bereits konfiguriert).

Wenn Ihr Profil unvollständig ist, zeigt der Begrüßungsabschnitt eine generische Begrüßungsnachricht und einen Platzhalter für Ihr Profilbild an.

**Widget-Abschnitt**

Dieser Abschnitt wird unter dem Begrüßungsabschnitt angezeigt und bietet vorkonfigurierte Widgets unter den folgenden Abschnitten:

* Aktivität
* Aktuell
* Entdecken

**Aktivität**: Unter diesem Abschnitt zeigt das Widget **[!UICONTROL Meine Aktivität]** die aktuellsten Aktivitäten an, die angemeldete Personen mit Assets durchgeführt haben (einschließlich Assets ohne Ausgabedarstellungen), z. B. Asset-Uploads, -Downloads, Asset-Erstellung, Bearbeitungen, Kommentare, Anmerkungen und Freigaben.

**Aktuell**: Das Widget **[!UICONTROL Vor kurzem angezeigt]** unter diesem Abschnitt zeigt vor kurzem durch angemeldete Benutzende aufgerufene Entitäten an, z. B. Ordner, Sammlungen und Projekte.

**Entdecken**: Das Widget **[!UICONTROL Neu]** unter diesem Abschnitt zeigt die Assets und Ausgabedarstellungen an, die zuletzt in die [!DNL Assets]-Bereitstellung hochgeladen wurden.

Um das Löschen von Benutzeraktivitätsdaten zu aktivieren, aktivieren Sie den **[!UICONTROL DAM Event Purge-Dienst]** vom Configuration Manager aus. Nachdem Sie diesen Dienst aktiviert haben, werden die Aktivitäten der angemeldeten Person, die eine bestimmte Anzahl überschreiten, vom System gelöscht.

Der Begrüßungsbildschirm enthält einfache Navigationshilfen, z. B. Symbole in der Symbolleiste für das Zugreifen auf Ordner, Sammlungen und Kataloge.

>[!NOTE]
>
>Die Dienste [!UICONTROL Day CQ DAM Event Recorder] und [!UICONTROL DAM Event Purge] erhöhen die Zahl der JCR-Schreibvorgänge und die Suchindizierung, was die Last auf dem [!DNL Experience Manager]-Server erheblich erhöht. Die zusätzliche Last auf dem [!DNL Experience Manager]-Server kann dessen Leistung beeinträchtigen.

>[!CAUTION]
>
>Das Erfassen, Filtern und Bereinigen von Benutzeraktivitäten für die [!DNL Assets]-Startseite erfordert einen gewissen Mehraufwand. Daher sollten Admins die Homepage für Zielbenutzerinnen und -benutzer effektiv konfigurieren.
>
>Adobe empfiehlt Administratoren und Benutzern, die mit großen Datenmengen arbeiten, die Verwendung der Asset-Homepage-Funktion zu vermeiden, um einen Anstieg der Benutzeraktivitäten zu verhindern. Außerdem können Admins Aufzeichnungsaktivitäten von bestimmten Benutzenden unterbinden, indem sie den [!UICONTROL Day CQ DAM Event Recorder] vom [!UICONTROL Configuration Manager] aus konfigurieren.
>
>Wenn Sie die Funktion verwenden, empfiehlt Adobe, dass Sie die Bereinigungsfrequenz auf der Grundlage der Serverlast planen.
