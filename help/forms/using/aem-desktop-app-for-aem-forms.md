---
title: AEM Desktop-App für AEM Forms
seo-title: AEM desktop app for AEM Forms
description: AEM Desktop-App für AEM Forms
uuid: 99e0f2fb-8623-45bb-8e2e-5c5d6f482366
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
discoiquuid: c30332b6-e012-442d-8e84-28832c116c7b
noindex: true
role: Admin
exl-id: b87e07b1-4a19-4888-bad0-c0f5327b9ad3
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 55%

---

# AEM Desktop-App für AEM Forms {#aem-desktop-app-for-aem-forms}

Mit der AEM Desktop-App können Sie das Assets-Repository von Adobe Experience Manager (AEM) und Binärdateien für AEM Forms einem Netzwerkverzeichnis in Ihrem System zuordnen. Sie können die synchronisierten Assets und Binärdateien in einem Datei-Explorer anzeigen und verschiedene Apps verwenden, um die Dateien nach Bedarf zu bearbeiten. Neben der Ansicht der Dateien können Sie auch die Binärdateien erstellen, hochladen und löschen. Sie können Dateien auch direkt aus der Software öffnen, bearbeiten und speichern. Sie können beispielsweise eine XDP-Datei direkt in Designer öffnen und bearbeiten. Die Änderungen, die Sie lokal an den Assets vornehmen, spiegeln sich im AEM Assets-Repository und in der AEM Forms-Benutzeroberfläche wider.

Sie können die App von einer AEM-Instanz herunterladen. Ausführliche Informationen zum Herunterladen der App finden Sie in den [Versionshinweisen zur AEM Desktop-App](https://helpx.adobe.com/de/experience-manager/desktop-app/release-notes.html).

## AEM Forms-Assets, die in der AEM Desktop-App unterstützt werden {#aem-forms-assets-supported-in-aem-desktop-app}

Sie können das Programm zum Synchronisieren von AEM Forms-Binärdateien des folgenden Typs verwenden: Formularvorlagen (.xdp), PDF-Formular (.pdf), Dokument (.pdf), Bilder, XML-Schema (.xsd), Stylesheets (.xfs). Das Programm listet alle anderen Dateien (nicht unterstützte Dateien) als 0-Byte-Dateien auf. Durch das Auflisten nicht unterstützter Dateien als 0-Byte-Dateien wird sichergestellt, dass der Benutzer weiß, dass andere auf dem AEM Forms-Server verfügbare Assets vorhanden sind.

>[!NOTE]
>
>Dateinamen dürfen nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

## Aktivieren von AEM Forms für die AEM Desktop-App {#enable-aem-forms-for-aem-desktop-app}

Die AEM Desktop-App verwendet das WebDAV-Protokoll unter Microsoft Windows und SMB1 unter Mac OS X, um eine Verbindung zu einem AEM Forms-Server herzustellen. Standardmäßig ist der AEM Forms-Server nicht zum Synchronisieren von Binärdateien und anderen Assets mit einem WebDAV- oder SMB-Client aktiviert. Führen Sie die folgenden Schritte aus, um AEM Forms für die AEM Desktop-App zu aktivieren:

1. Melden Sie sich bei AEM Forms als Administrator an.
1. Klicken Sie in der Authoring-Instanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![Hammer](assets/hammer.png) **[!UICONTROL Implementierung > Vorgänge > Web-Konsole]**. Die Webkonsole wird in einem neuen Fenster geöffnet.
1. Suchen Sie im Fenster der Web-Konsole die Option **[!UICONTROL FormsManager AddOn Configuration]** und öffnen Sie sie.
1. Deaktivieren Sie im Dialogfeld „FormsManager AddOn Configuration“ das Kontrollkästchen **[!UICONTROL Asynchronously Sync Resources]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Starten Sie den AEM Forms-Server neu. Nach dem Neustart kann der AEM Forms-Server Inhalte von der AEM Desktop-App akzeptieren und mit ihr austauschen.
1. Öffnen Sie die App und stellen Sie eine Verbindung zum AEM Forms-Server her.

   Wird die Verbindung erfolgreich hergestellt, füllt die App die Ordner `content/dam` und `content/dam/formsanddocuments`. Sie können das Programm zusammen mit dem Verschieben von Dateien aus den oben genannten Ordnern in lokale Ordner und umgekehrt verwenden, um Inhalte zwischen automatisch ausgefüllten Ordnern zu verschieben.
