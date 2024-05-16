---
title: Adobe Experience Manager (AEM) Desktop-App für AEM Forms
description: Adobe Experience Manager (AEM) Desktop-App für AEM Forms
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: manage
noindex: true
role: Admin,User
exl-id: b87e07b1-4a19-4888-bad0-c0f5327b9ad3
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '468'
ht-degree: 100%

---

# Adobe Experience Manager (AEM) Desktop-App für AEM Forms {#aem-desktop-app-for-aem-forms}

Mit der AEM Desktop-App können Sie das Assets-Repository von Adobe Experience Manager (AEM) und Binärdateien für AEM Forms einem Netzwerkverzeichnis in Ihrem System zuordnen. Sie können die synchronisierten Assets und Binärdateien in einem Datei-Explorer anzeigen und verschiedene Apps verwenden, um die Dateien nach Bedarf zu bearbeiten. Neben der Ansicht der Dateien können Sie auch die Binärdateien erstellen, hochladen und löschen. Sie können Dateien auch direkt aus der Software öffnen, bearbeiten und speichern. Sie können beispielsweise eine XDP-Datei direkt im Designer öffnen und bearbeiten. Die Änderungen, die Sie lokal an den Assets vornehmen, spiegeln sich im AEM Assets-Repository und in der Benutzeroberfläche von AEM Forms wider.

Sie können die App von einer AEM-Instanz herunterladen. Ausführliche Informationen zum Herunterladen der App finden Sie in den [Versionshinweisen zur AEM Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=de).

## AEM Forms-Assets, die in der AEM Desktop-App unterstützt werden {#aem-forms-assets-supported-in-aem-desktop-app}

Mithilfe der App können Sie AEM Forms-Binärdateien des folgenden Typs synchronisieren: Formularvorlagen (.xdp), PDF-Formulare (.pdf), Dokumente (.pdf), Bilder, XML-Schema (.xsd), Stilvorlagen (.xfs). Die App listet alle anderen Dateien (nicht unterstützte Dateien) als 0-Byte-Dateien auf. Durch das Auflisten nicht unterstützter Dateien als 0-Byte-Dateien wird sichergestellt, dass die Benutzenden wissen, dass andere auf dem AEM Forms-Server verfügbare Assets vorhanden sind.

>[!NOTE]
>
>Ein Dateiname darf nur alphanumerische Zeichen, Bindestriche oder Unterstriche enthalten.

## Aktivieren von AEM Forms für die AEM Desktop-App {#enable-aem-forms-for-aem-desktop-app}

Die AEM-Desktop-App verwendet das WebDAV-Protokoll unter Microsoft® Windows und SMB1 unter macOS X, um eine Verbindung zu einem AEM Forms-Server herzustellen. Standardmäßig ist der AEM Forms-Server nicht zum Synchronisieren von Binärdateien und anderen Assets mit einem WebDAV- oder SMB-Client aktiviert. Führen Sie die folgenden Schritte aus, damit Sie AEM Forms für die AEM-Desktop-App aktivieren können:

1. Melden Sie sich bei AEM Forms als Administrator an.
1. Klicken Sie in der Authoring-Instanz auf ![adobeexperiencemanager](assets/adobeexperiencemanager.png) **[!UICONTROL Adobe Experience Manager > Tools]** ![Hammer](assets/hammer.png) **[!UICONTROL Implementierung > Vorgänge > Web-Konsole]**. Die Webkonsole wird in einem neuen Fenster geöffnet.
1. Suchen Sie im Fenster der Web-Konsole die Option **[!UICONTROL FormsManager AddOn Configuration]** und öffnen Sie sie.
1. Deaktivieren Sie im Dialogfeld „FormsManager AddOn Configuration“ das Kontrollkästchen **[!UICONTROL Asynchronously Sync Resources]** und klicken Sie auf **[!UICONTROL Speichern]**.
1. Starten Sie den AEM Forms-Server neu. Nach dem Neustart ist der AEM Forms-Server in der Lage, Inhalte zu akzeptieren und mit der AEM-Desktop-App freizugeben.
1. Öffnen Sie die App und stellen Sie eine Verbindung mit dem AEM Forms-Server her.

   >[!NOTE]
   >
   > Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

   Wird die Verbindung erfolgreich hergestellt, füllt die App die Ordner `content/dam` und `content/dam/formsanddocuments`. Neben dem Verschieben von Dateien aus obigen Ordnern in lokale Ordner und umgekehrt können Sie mit der App auch Inhalte zwischen automatisch befüllten Ordnern verschieben.
