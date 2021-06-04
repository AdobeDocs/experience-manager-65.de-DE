---
title: AEM Forms JEE Patch Installationsprogramm
description: AEM Forms JEE Patch Installationsprogramm
uuid: 76662858-afca-4ba3-883b-9b9a61874f15
content-type: reference
discoiquuid: b0283feb-c3ec-4ef0-885c-46bc83a61e26
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
source-git-commit: ecac6269b5e12b847136f4af534016bc7b88bb2b
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 51%

---

# AEM Forms JEE Patch Installer {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Wenden Sie sich an ](https://www.adobe.com/account/sign-in.supportportal.html) den Support , um weitere Informationen zu erhalten oder den Patch zu erhalten.

## Über das Patch-Installationsprogramm {#about-the-patch-installer}

Das AEM 6.5 Forms JEE Patch-Installationsprogramm enthält alle behobenen Probleme für alle Komponenten von AEM 6.5 Forms JEE, die bis zur Veröffentlichung dieses Patches verfügbar sind. Eine vollständige Liste der behobenen Probleme finden Sie in den aktuellen Versionshinweisen zu [Service Pack](sp-release-notes.md) .

## Voraussetzungen für die Installation des Patches {#prerequisites-to-installing-the-patch}

* AEM 6.5 Forms

## Installieren und Konfigurieren des Patches {#installing-and-configuring-the-patch}

1. Erstellen Sie eine Sicherungskopie des Ordners *aem-forms_root*. Das ist erforderlich, wenn Sie die Schnellkorrektur deinstallieren.
1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie die Archivdatei des Patch-Installationsprogramms auf Ihrer Festplatte.
1. Im Ordner mit dem Namen entsprechend des von Ihnen verwendeten Betriebssystems:

   * **Windows**
Navigieren Sie zum entsprechenden Ordner auf dem Installationsdatenträger oder dem Ordner auf der Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die Datei aemforms65_cfp_install.exe.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * ****
LinuxNavigieren Sie zum entsprechenden Ordner und geben Sie an einer Eingabeaufforderung Folgendes ein: 
`./aem65_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`

   Hierdurch wird das Installieren des Assistenten gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm „Installationsordner auswählen“ sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Schnellkorrekturzusammenfassung und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen zur „Zusammenfassung vor der Installation“ und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.

1. Deaktivieren Sie die Option „LiveCycle Configuration Manager“ starten, bevor Sie auf „Fertig“ klicken. Bevor Sie Configuration Manager mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** ausführen, navigieren Sie zum Ordner *&lt;AEMForms_Install_Dir>\configurationManager\bin* und aktualisieren Sie die Dateien `ConfigurationManager.lax` und `ConfigurationManager_IPv6.lax` mit den folgenden Umbenennungsvorgängen:

   * `axis.jar` in `axis-1.4.1.1.jar`
   * `serializer-2.7.1.jar` in `serializer-2.7.2.jar`
   * `xalan-2.7.1.jar` in `xalan-2.7.2.jar`
   * `xercesImpl-2.9.1.jar` in `xercesImpl-2.12.0.jar`

1. Das Kontrollkästchen Configuration Manager starten ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager auszuführen.

1. Um Configuration Manager später auszuführen, deaktivieren Sie die Option Configuration Manager starten, bevor Sie auf Fertig klicken. Sie können Configuration Manager später mit dem entsprechenden Skript im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten.

1. Wählen Sie je nach Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms für JBoss](http://www.adobe.com/go/learn_aemforms_installJBoss_65) 
   * [Installieren und Bereitstellen von AEM Forms für WebSphere](http://www.adobe.com/go/learn_aemforms_installWebSphere_65)

1. (Nur JBoss) Löschen Sie nach der Installation des Patches und der Konfiguration des Servers die Ordner tmp und work des JBoss-Anwendungsservers.

## Konfigurationen nach der Bereitstellung {#post-deployment-configurations}

### SAML-Konfigurationen {#saml-configurations}

Wenn Sie die SAML-Authentifizierung konfiguriert haben und Probleme mit großen IDP-Metadaten haben, führen Sie nach der Installation des Patches die folgenden Schritte aus:

1. Legen Sie die folgende Systemeigenschaft auf Ihrem Anwendungsserver fest:\
   `um.saml.enable.large.xml=true`
1. Starten Sie den Server neu.
1. Löschen Sie vorhandene SAML-Authentifizierungsanbieter und fügen Sie sie erneut für bestehende Domänen hinzu, wie in den SAML-Einstellungen beschrieben.

## Betroffene Module {#impacted-modules}

* Document Services
* Dokumentensicherheit
* Foundation JEE

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
