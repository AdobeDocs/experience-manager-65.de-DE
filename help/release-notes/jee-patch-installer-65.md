---
title: AEM Forms JEE-Patch-Installationsprogramm
description: Erfahren Sie, wie Sie mit dem AEM Forms JEE Patch-Installationsprogramm Probleme in AEM 6.5 Forms-Komponenten beheben können.
content-type: reference
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
hide: true
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 91%
---
# AEM Forms JEE-Patch-Installationsprogramm {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Kontaktieren Sie den Support](https://experienceleague.adobe.com/de?lang=de&support-solution=General&support-tab=home#support), um weitere Informationen oder den Patch zu erhalten.

## Über das Patch-Installationsprogramm {#about-the-patch-installer}

Das AEM 6.5 Forms JEE Patch-Installationsprogramm enthält alle behobenen Probleme für alle Komponenten von AEM 6.5 Forms JEE, die bis zur Veröffentlichung dieses Patches verfügbar waren. Eine vollständige Liste der behobenen Probleme finden Sie in den [Versionshinweisen zum aktuellen Service Pack](release-notes.md).

## Voraussetzungen für die Installation des Patches {#prerequisites-to-installing-the-patch}

* AEM 6.5 Forms

## Installieren und Konfigurieren des Patches {#installing-and-configuring-the-patch}

1. Erstellen Sie eine Sicherungskopie des Ordners &lt;*aem-forms_root*>/deploy. Das ist erforderlich, wenn Sie die Schnellkorrektur deinstallieren möchten.
1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie die Archivdatei des Patch-Installationsprogramms auf Ihrer Festplatte.
1. Im Ordner mit dem Namen entsprechend des von Ihnen verwendeten Betriebssystems:

   * **Windows**
     Navigieren Sie zu dem entsprechenden Verzeichnis auf dem Installationsmedium oder dem Ordner auf Ihrer Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die Datei aemforms65_cfp_install.exe.

     * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
     * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
     Navigieren Sie zum entsprechenden Verzeichnis und geben Sie an einer Eingabeaufforderung `./aem65_cfp_install.bin` ein.

     * (Linux®) `Linux/Disk1/InstData/NoVM`

   Dadurch wird ein Installationsassistent gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm **Installationsordner auswählen** sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Zusammenfassung der Schnellkorrektur und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen in der Zusammenfassung vor der Installation und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.

1. **[Nur für Windows]:** Gehen Sie wie folgt vor:
   * Sie können entweder die Option **Configuration Manager starten** deaktivieren, bevor Sie auf **[!UICONTROL Fertig]** klicken. Führen Sie **Configuration Manager** durch Verwendung der Datei **ConfigurationManager.bat** in `[aem-forms root]\configurationManager\bin` aus.

   * Oder deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Navigieren Sie vor der Ausführung von **Configuration Manager** mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** zum Verzeichnis *`<AEMForms_Install_Dir>\configurationManager\bin`*, ersetzen Sie **ConfigurationManager.lax** und **ConfigurationManager_IPV6.lax** durch die neuesten Versionen der Dateien [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) und [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) und ersetzen Sie in diesen beiden Dateien **axis-1.4.1.1.jar** überall durch **axis-1.4.1.2.jar**.

   >[!NOTE]
   >
   >Indem Sie die Datei **ConfigurationManager.bat** verwenden, müssen Sie die Namen der .lax-Dateien nicht manuell aktualisieren.
   >

1. **[Nur auf Unix-Basis]:**

   * Das Kontrollkästchen **Configuration Manager starten** ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager sofort zu starten. Um **Configuration Manager** erst später zu starten, deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Sie können **Configuration Manager** später mit dem entsprechenden Skript im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten.

1. Wählen Sie je nach Anwendungs-Server eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms for JBoss®](https://www.adobe.com/go/learn_aemforms_installJBoss_65_de)
   * [Installieren und Bereitstellen von AEM Forms for WebSphere®](https://www.adobe.com/go/learn_aemforms_installWebSphere_65_de)

1. (Nur JBoss®) Löschen Sie nach der Installation des Patches und der Konfiguration des Servers die Ordner „tmp“ und „work“ des JBoss®-Anwendungs-Servers.

## Konfigurationen nach der Bereitstellung {#post-deployment-configurations}

### SAML-Konfigurationen {#saml-configurations}

Wenn Sie die SAML-Authentifizierung konfiguriert haben und Probleme mit großen IDP-Metadaten haben, führen Sie nach der Installation des Patches die folgenden Schritte aus:

1. Legen Sie die folgende Systemeigenschaft auf Ihrem Anwendungsserver fest:\
   `um.saml.enable.large.xml=true`
1. Starten Sie den Server neu.
1. Löschen Sie vorhandene SAML-Authentifizierungsanbieter und fügen Sie sie erneut für bestehende Domains hinzu, wie in den SAML-Einstellungen beschrieben.

>[!NOTE]
>
> Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## Betroffene Module {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE

[Support kontaktieren](https://experienceleague.adobe.com/de?support-solution=General&support-tab=home&lang=de#support)
