---
title: AEM Desktop-App für AEM Forms
seo-title: AEM Desktop-App für AEM Forms
description: AEM Desktop-App für AEM Forms
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 63%

---


# AEM desktop app for AEM Forms {#aem-desktop-app-for-aem-forms}

Mit AEM Desktop-App können Sie das Adobe Experience Manager (AEM) Assets-Repository und die AEM Forms-Binärdateien einem Netzwerkverzeichnis auf Ihrem System zuordnen. Sie können die synchronisierten Elemente und Binärdateien in einem Datei-Explorer anzeigen und die Dateien wie gewünscht mit einer Reihe von Apps bearbeiten. Dabei können Sie die Dateien nicht nur anzeigen, sondern auch Binärdateien erstellen, hochladen und löschen. Sie können Dateien auch direkt von der Software aus öffnen, bearbeiten und speichern. Sie können beispielsweise eine XDP-Datei direkt in Designer öffnen und bearbeiten. Die Änderungen, die Sie lokal an den Assets vornehmen, werden im AEM-Assets-Repository und in der AEM Forms-Benutzeroberfläche übernommen.

Sie können die App aus einer AEM-Instanz aus herunterladen. For detailed information about downloading the app, see [AEM desktop app Release Notes](https://helpx.adobe.com/experience-manager/desktop-app/release-notes.html).

## AEM Forms assets supported in AEM desktop app {#aem-forms-assets-supported-in-aem-desktop-app}

Mithilfe der App können Sie AEM Forms-Binärdateien der Typen Formatvorlage (.xdp), PDF-Formular (.pdf), Dokument (.pdf), Bilder, XML-Schema (.xsd) und Formatvorlage (.xfs) synchronisieren. Die App listet alle anderen Dateien (nicht unterstützte Dateien) als 0-Byte-Dateien auf. Durch die Anzeige nicht unterstützter Dateien als 0-Byte-Dateien wird der Benutzer darauf aufmerksam gemacht, dass andere Assets auf dem AEM Forms-Server vorhanden sind.

>[!NOTE]
>
>Ein Dateiname darf nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

## Enable AEM Forms for AEM desktop app {#enable-aem-forms-for-aem-desktop-app}

AEM Desktop-App verwendet das WebDAV-Protokoll unter Microsoft Windows und SMB1 unter Mac OS X, um eine Verbindung zu einem AEM Forms-Server herzustellen. Standardmäßig ist der AEM Forms-Server nicht zum Synchronisieren von Binärdateien und anderen Assets mit einem WebDAV- oder SMB-Client aktiviert. Führen Sie die folgenden Schritte aus, um AEM Forms für AEM Desktop-App zu aktivieren:

1. Melden Sie sich bei AEM Forms als Administrator an.
1. In the author instance, click ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![hammer](assets/hammer.png) **[!UICONTROL > Deployment > Operations > Web Console]**. Die Web-Konsole wird in einem neuen Fenster geöffnet.
1. Suchen Sie im Fenster der Web-Konsole die Option **[!UICONTROL FormsManager AddOn Configuration]** und öffnen Sie sie.
1. Deaktivieren Sie im Dialogfeld „FormsManager AddOn Configuration“ das Kontrollkästchen **[!UICONTROL Asynchronously Sync Resources]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Starten Sie den AEM Forms-Server neu. Nach dem Neustart ist der AEM Forms-Server für die Akzeptanz und Freigabe von Inhalten für AEM Desktop-App aktiviert.
1. Öffnen Sie die App und stellen Sie eine Verbindung zum AEM Forms-Server her.

   On successful connection, the app populates the `content/dam` and `content/dam/formsanddocuments` folders. Sie können mithilfe der App nicht nur Dateien aus den oben genannten Ordnern in lokale Ordner und umgekehrt, sondern auch Inhalte zwischen automatisch gefüllten Ordnern verschieben.

