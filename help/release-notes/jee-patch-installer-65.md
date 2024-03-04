---
title: AEM Forms JEE-Patch-Installationsprogramm
description: Erfahren Sie, wie Sie mit dem AEM Forms JEE Patch-Installationsprogramm Probleme in AEM 6.5 Forms-Komponenten beheben können.
content-type: reference
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
hide: true
hidefromtoc: true
source-git-commit: 947f45e043c2ce1b683212f70157d1e9a08e1941
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 100%

---

# AEM Forms JEE-Patch-Installationsprogramm {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Kontaktieren Sie den Support](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home?lang=de#support), um weitere Informationen oder den Patch zu erhalten.

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
Navigieren Sie zu dem entsprechenden Verzeichnis auf dem Installationsmedium oder dem Ordner auf Ihrer Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die Datei „aemforms65_cfp_install.exe“.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux**:
Wechseln Sie in den entsprechenden Ordner und geben Sie an einer Eingabeaufforderung Folgendes ein:`./aem65_cfp_install.bin`

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Dadurch wird ein Installationsassistent gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm **Installationsordner auswählen** sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Zusammenfassung der Schnellkorrektur und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen in der Zusammenfassung vor der Installation und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.

1. **[Nur für Windows]:** Gehen Sie wie folgt vor:
   * Sie können entweder die Option **Configuration Manager starten** deaktivieren, bevor Sie auf **[!UICONTROL Fertig]** klicken. Führen Sie **Configuration Manager** durch Verwendung der Datei **ConfigurationManager.bat** in `[aem-forms root]\configurationManager\bin` aus.

   * Oder deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Navigieren Sie vor der Ausführung von **Configuration Manager** mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** zu *`<AEMForms_Install_Dir>\configurationManager\bin`* und ersetzen Sie **ConfigurationManager.lax** und **ConfigurationManager_IPV6.lax** durch die neuesten Dateien [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) und [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) und ersetzen Sie in diesen beiden Dateien **axis-1.4.1.1.jar** überall durch **axis-1.4.1.2.jar**.

   >[!NOTE]
   >
   >Indem Sie die Datei **ConfigurationManager.bat** verwenden, müssen Sie die Namen der .lax-Dateien nicht manuell aktualisieren.
   >

1. **[Nur auf Unix-Basis]:**

   * Das Kontrollkästchen **Configuration Manager starten** ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager sofort zu starten. Um **Configuration Manager** erst später zu starten, deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Sie können **Configuration Manager** später mit dem entsprechenden Skript im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten.

1. Wählen Sie je nach Anwendungs-Server eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms for JBoss®](https://www.adobe.com/go/learn_aemforms_installJBoss_65_de)
   * [Installieren und Bereitstellen von AEM Forms für WebSphere®](https://www.adobe.com/go/learn_aemforms_installWebSphere_65_de)

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
> Es wird empfohlen, den Befehl „Strg + C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mithilfe alternativer Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

## Betroffene Module {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE

[Support kontaktieren](https://experienceleague.adobe.com/?support-solution=General&amp;support-tab=home?lang=de#support)
