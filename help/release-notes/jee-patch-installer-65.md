---
title: AEM Forms JEE-Patch-Installationsprogramm
description: AEM Forms JEE-Patch-Installationsprogramm
uuid: 76662858-afca-4ba3-883b-9b9a61874f15
content-type: reference
discoiquuid: b0283feb-c3ec-4ef0-885c-46bc83a61e26
exl-id: 6b17472b-9226-4319-b305-4dba862d21af
source-git-commit: e3caa3e3067cf5e29cfcdf4286047eb346aefa23
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 69%

---

# AEM Forms JEE-Patch-Installationsprogramm {#aem-forms-jee-patch-installer}

>[!NOTE]
>
>[Kontaktieren Sie den Support](https://www.adobe.com/account/sign-in.supportportal.html), um weitere Informationen oder den Patch zu erhalten.

## Über das Patch-Installationsprogramm {#about-the-patch-installer}

Das AEM 6.5 Forms JEE Patch-Installationsprogramm enthält alle behobenen Probleme für alle Komponenten von AEM 6.5 Forms JEE, die bis zur Veröffentlichung dieses Patches verfügbar waren. Eine vollständige Liste der behobenen Probleme finden Sie in den [Versionshinweisen zum aktuellen Service Pack](release-notes.md).

## Voraussetzungen für die Installation des Patches {#prerequisites-to-installing-the-patch}

* AEM 6.5 Forms

## Installieren und Konfigurieren des Patches {#installing-and-configuring-the-patch}

1. Erstellen Sie eine Sicherungskopie des Ordners *aem-forms_root*. Das ist erforderlich, wenn Sie die Schnellkorrektur deinstallieren.
1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie die Archivdatei des Patch-Installationsprogramms auf Ihrer Festplatte.
1. Im Ordner mit dem Namen entsprechend des von Ihnen verwendeten Betriebssystems:

   * **Windows**


Wechseln Sie zu dem Ordner auf dem Installationsdatenträger oder auf der Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die Datei aemforms65_cfp_install.exe.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux**:
Wechseln Sie in den entsprechenden Ordner und geben Sie an einer Eingabeaufforderung Folgendes ein: 
`./aem65_cfp_install.bin`.

      * (Linux) `Linux/Disk1/InstData/NoVM`

   Hierdurch wird das Installieren des Assistenten gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Im **Installationsordner auswählen** überprüfen Sie, ob der angezeigte Standardspeicherort für Ihre bestehende Installation richtig ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]** zum Auswählen des alternativen Ordners, in dem AEM Formulare installiert sind, und klicken Sie auf **[!UICONTROL Nächste]**.
1. Lesen Sie die Schnellkorrekturzusammenfassung und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen zur „Zusammenfassung vor der Installation“ und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.

1. **[Nur für Windows]:** Führen Sie einen der folgenden Schritte aus:
   * Deaktivieren Sie entweder die **Configuration Manager starten** Option vor dem Klicken **[!UICONTROL Fertig]**. Ausführen **Configuration Manager** durch Verwendung von **ConfigurationManager.bat** Datei in `[aem-forms root]\configurationManager\bin`.

   * Oder deaktivieren Sie die **Configuration Manager starten** Option vor dem Klicken **[!UICONTROL Fertig]**. Vor der Ausführung **Configuration Manager** using **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe**, navigieren Sie zu *`<AEMForms_Install_Dir>\configurationManager\bin`* Verzeichnis und ersetzen [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) und [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax) Dateien.
   >[!NOTE]
   >Verwenden **ConfigurationManager.bat** hilft Ihnen dabei, die Namensänderung von .lax-Dateien manuell zu vermeiden.

1. **[Nur für Unix-basierte]:**

   * Die **Configuration Manager starten** ist standardmäßig aktiviert. Klicken **[!UICONTROL Fertig]** , um Configuration Manager sofort auszuführen oder **Configuration Manager** Heben Sie später die Auswahl der **Configuration Manager starten** Option vor dem Klicken **[!UICONTROL Fertig]**. Sie können **Configuration Manager** später mithilfe des entsprechenden Skripts in der `[AEM_forms_root]/configurationManager/bin` Verzeichnis.

1. Wählen Sie je nach Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms für JBoss](https://www.adobe.com/go/learn_aemforms_installJBoss_65_de) 
   * [Installieren und Bereitstellen von AEM Forms für WebSphere](https://www.adobe.com/go/learn_aemforms_installWebSphere_65_de)

1. (Nur JBoss) Löschen Sie nach der Installation des Patches und der Konfiguration des Servers die Ordner „tmp“ und „work“ des JBoss-Anwendungsservers.

## Konfigurationen nach der Bereitstellung {#post-deployment-configurations}

### SAML-Konfigurationen {#saml-configurations}

Wenn Sie die SAML-Authentifizierung konfiguriert hatten und Probleme mit großen IDP-Metadaten haben, führen Sie nach der Installation des Patches die folgenden Schritte aus:

1. Legen Sie die folgende Systemeigenschaft auf Ihrem Anwendungsserver fest:\
   `um.saml.enable.large.xml=true`
1. Starten Sie den Server neu.
1. Löschen Sie vorhandene SAML-Authentifizierungsanbieter und fügen Sie sie erneut für bestehende Domains hinzu, wie in den SAML-Einstellungen beschrieben.

## Betroffene Module {#impacted-modules}

* Document Services
* Document Security
* Foundation JEE

[Support kontaktieren](https://www.adobe.com/account/sign-in.supportportal.html)
