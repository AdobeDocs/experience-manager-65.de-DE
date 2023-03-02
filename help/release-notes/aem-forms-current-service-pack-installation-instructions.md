---
title: Installationsanweisungen für AEM Forms Patch für AEM Forms
description: Installationsanweisungen für das AEM Forms Service Pack für die OSGi- und JEE-Umgebung
exl-id: ae4c7e9d-9af8-4288-a6f9-e3bcbe7d153d
source-git-commit: b15581701aaff72db2fc0030b0062d2f12150d8f
workflow-type: tm+mt
source-wordcount: '1726'
ht-degree: 49%

---

# Installationsanweisungen für das Forms Service Pack AEM 6.5 {#aem-form-patch-installation-instructions}

## Versionsinformationen

| Produkt | Adobe Experience Manager 6.5 Forms |
|---|---|
| Version | 6.5.16.0 |
| Typ | Service Pack-Version |
| Datum | 2. März 2023 |
| Download-URL | [Neueste AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) |

>[!NOTE]
>
>Aktuelle Informationen anzeigen [Versionshinweise zum AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de) für eine vollständige Liste der behobenen Probleme.

## Was ist in Experience Manager Forms 6.5 enthalten?

Das Adobe Experience Manager (AEM) Forms Service Pack enthält neue und aktualisierte Funktionen, wie wichtige von Kunden angeforderte Verbesserungen, Leistungs-, Stabilitäts- und Sicherheitsverbesserungen. AEM Forms veröffentlicht Service Packs in regelmäßigen Abständen, um die neuesten Funktionen und Verbesserungen bereitzustellen. Wählen Sie je nach Stapel einen der folgenden Pfade zum Herunterladen und Installieren des Service Packs in Ihrer Umgebung aus:

* [Herunterladen und Installieren des Service Packs in einer AEM Form on JEE-Umgebung](#download-and-install-for-jee-service-pack)
* [Herunterladen und Installieren des Service Packs auf einem AEM Formular in der OSGi-Umgebung](#download-and-install-for-osgi-service-pack)

>[!NOTE]
>
> Adobe veröffentlicht jedes 6. Service Pack ein vollständiges Installationsprogramm. AEM 6.5 Forms Service Pack 12 (6.5.12.0) auf JEE war das letzte vollständige Installationsprogramm. Das vollständige Installationsprogramm unterstützt neue Plattformen, während das Installationsprogramm für das reguläre Service Pack neue Funktionen, behobene Fehler und allgemeine Verbesserungen enthält. Wenn Sie eine Neuinstallation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms on JEE-Umgebung planen, empfiehlt Adobe die Verwendung des Vollinstallationsprogramms für AEM 6.5.12.0 Forms on JEE vom 03. März 2022 anstelle des AEM 6.5 Forms-Installationsprogramms vom 08. April 2019. Nachdem Sie das vollständige Installationsprogramm verwendet haben, installieren Sie das neueste Service Pack.

## Herunterladen und Installieren des Service Packs in einer AEM Form on JEE-Umgebung {#download-and-install-for-jee-service-pack}

![JEE-Installation](/help/forms/using/assets/jeeinstallation.png)

+++1. Erstellen Sie eine Sicherungskopie Ihrer bestehenden Umgebung:

1. Sichern Sie Ihre [CRX-Repository, Datenbankschema und GDS (Globaler Dokumentenspeicher)](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).
1. Sichern Sie das &lt;*AEM_forms_root* Ordner >/deploy .

>[!NOTE]
>
> Bevor Sie das AEM Service Pack-Installationsprogramm ausführen, stellen Sie sicher, dass Sie über Schreibzugriffsberechtigungen für AEM Installationsverzeichnis verfügen.

+++

+++2.Laden Sie die erforderliche Software herunter:

* [AEM Forms on JEE Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)
* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de)
* [Forms-Add-on-Paket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)
* [Fragment-Servlet](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Forg.apache.felix.http.servlet-api-1.2.0_fragment_full.jar)

+++

+++3. Installieren Sie das AEM Forms on JEE Service Pack:

1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie die **Installationsprogramm für AEM Forms on JEE Service Pack** auf Ihrer Festplatte:

   * **Windows**
Navigieren Sie zum entsprechenden Ordner auf dem Installationsdatenträger oder dem Ordner auf der Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die 
`aemforms65_cfp_install.exe` file.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`
   * **Linux®**
Navigieren Sie zum entsprechenden Verzeichnis, von einer Shell aus und geben Sie 
`./aem65_cfp_install.bin`

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Hierdurch wird das Installieren des Assistenten gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm **Installationsordner auswählen** sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Service Pack-Zusammenfassungsinformationen und klicken Sie auf **[!UICONTROL Nächste]**.
1. Lesen Sie die Informationen zur „Zusammenfassung vor der Installation“ und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.
1. **[Nur für Windows]:** Führen Sie einen der folgenden Schritte aus:

   * Sie können entweder die Option **Configuration Manager starten** deaktivieren, bevor Sie auf **[!UICONTROL Fertig]** klicken. Führen Sie **Configuration Manager** durch Verwendung der Datei **ConfigurationManager.bat** in `[aem-forms root]\configurationManager\bin` aus.

   * Oder deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Navigieren Sie vor der Ausführung von **Configuration Manager** mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** zum Verzeichnis *`<AEMForms_Install_Dir>\configurationManager\bin`* und ersetzen Sie die Dateien [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) und [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax).

      >[!NOTE]
      >
      >* Aktualisieren oder Ersetzen der **ConfigurationManager.bat** hilft Ihnen dabei, das manuelle Aktualisieren der .lax-Dateien zu vermeiden.


1. **[Nur für Unix-basierte]:** Die **Configuration Manager starten** ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager sofort zu starten. Um **Configuration Manager** erst später zu starten, deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Sie können **Configuration Manager** später mit dem entsprechenden Skript im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten.

1. Wählen Sie je nach Anwendungsserver eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms für JBoss®](https://www.adobe.com/go/learn_aemforms_installJBoss_65_de)
   * [Installieren und Bereitstellen von AEM Forms für WebSphere®](https://www.adobe.com/go/learn_aemforms_installWebSphere_65_de)
   * [Installieren und Bereitstellen von AEM Forms für WebLogic](https://www.adobe.com/go/learn_aemforms_installWebLogic_65_de)
   * [Installieren und Bereitstellen von AEM für JBoss®-Cluster](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-jboss.pdf)
   * [Installieren und Bereitstellen von AEM Forms für WebSphere® Cluster](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-websphere.pdf)
   * [Installieren und Bereitstellen von AEM Forms für WebLogic Cluster](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/install-cluster-weblogic.pdf)


>[!NOTE]
>
> Nach der Installation des AEM Forms on JEE Service Packs müssen Sie das Forms Add-On-Paket aus `crx-repository\install` vor dem Neustart des Anwendungsservers. Laden Sie das neueste Add-On-Paket für Forms aus dem [Software Distribution-Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

+++

+++4. Servlet-Fragment installieren

>[!NOTE]
>
> * Falls Sie ein Upgrade von **AEM Service Pack 6.5.15.0**, ist es nicht erforderlich, die **Servlet-Fragment**. Wenn Sie von einer Version aktualisieren, die älter ist als **AEM Service Pack 6.5.15.0** müssen Sie die **Servlet-Fragment**.
> * Die Installation der **Servlet-Fragment** für alle Anwendungsserver mit Ausnahme der Anwendungsserver **JBoss® EAP 7.4.0**.



So laden Sie das Servlet-Fragment herunter und installieren es:

1. Wenn Sie das Fragment nicht heruntergeladen haben, laden Sie es von herunter [Softwareverteilung](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).

1. Starten Sie den Anwendungsserver, warten Sie, bis sich die Protokolle stabilisieren, und überprüfen Sie den Bundle-Status.

1. Öffnen Sie Webkonsole-Bundles. Die Standard-URL ist `http://[Server]:[Port]/system/console/bundles`.

1. Klicken Sie auf Installieren/Aktualisieren. Wählen Sie das heruntergeladene Fragment aus, `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`. Klicken Sie auf **Installieren** oder **Aktualisieren**. Warten Sie, bis sich der Anwendungsserver stabilisiert hat

1. Beenden Sie den Anwendungsserver.

+++

+++5. Installieren Sie AEM Service Pack

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.
1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.
1. Laden Sie das Service Pack von [Software Distribution](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->
1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie automatisch installieren können [!DNL ExperienceManager] Service Pack.<!--       UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist.
Das Paket wird automatisch installiert.

* Verwenden Sie die [HTTP-API von Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

   >[!NOTE]
   >
   >Experience Manager Service Pack unterstützt nicht die Installation von Bootstraps. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (spversion)` unter [!UICONTROL Installierte Produkte] an.<!-- UPDATE FOR EACH NEW RELEASE -->
1. Alle OSGi-Bundles sind entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** in der OSGi-Konsole (Webkonsole verwenden: `/system/console/bundles`).
1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.14 oder höher (WebConsole verwenden: `/system/console/     bundles`).

+++

+++6. Installieren AEM Experience Manager Forms-Add-On-Paket

1. Stellen Sie sicher, dass Sie die [!DNL Experience Manager] Service Pack.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-on-Paket wie unter [Installieren des AEM Forms-Add-on-Pakets](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) beschrieben.
1. Wenn Sie in Experience Manager 6.5 Forms Briefe verwenden, installieren Sie das [neueste AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

+++

## Herunterladen und Installieren des Service Packs auf einem AEM Formular in der OSGi-Umgebung {#download-and-install-for-osgi-service-pack}

![OSGi-Installationsschritte](/help/forms/using/assets/osgiinstallation.png)


+++1. Erstellen Sie eine Sicherungskopie Ihrer bestehenden Umgebung:

1. Sichern Sie Ihre [CRX-Repository und Datenbankschema](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html).

>[!NOTE]
>
> Wenn Sie das AEM Forms Service Pack für eine relationale Datenbank installieren, ist es erforderlich, eine Sicherung des DB_schema durchzuführen.

+++

+++2.Laden Sie die erforderliche Software herunter:

* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de)
* [Forms-Add-on-Paket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)

+++

+++3. Installieren Sie AEM Service Pack

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.
1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.
1. Laden Sie das Service Pack von [Software Distribution](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter. <!-- UPDATE FOR EACH NEW RELEASE -->
1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie automatisch installieren können [!DNL Experience Manager] Service Pack.<!--  UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

   >[!NOTE]
   >
   >Experience Manager Service Pack unterstützt nicht die Installation von Bootstraps. <!-- UPDATE FOR EACH NEW RELEASE -->

**Validierung der Installation**

Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (spversion)` unter [!UICONTROL Installierte Produkte] an. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

   1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.14 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`).

+++

+++4. Installieren AEM Experience Manager Forms-Add-On-Paket

1. Stellen Sie sicher, dass Sie die [!DNL Experience Manager] Service Pack.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-on-Paket wie unter [Installieren des AEM Forms-Add-on-Pakets](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) beschrieben.
1. Wenn Sie in Experience Manager 6.5 Forms Briefe verwenden, installieren Sie das [neueste AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

+++

## Fehlerbehebung

* Wenn **Dialogfeld &quot;Package Manager UI&quot;** während der Installation des Service Packs beendet wird, warten Sie, bis sich die Fehlerprotokolle stabilisieren, bevor Sie auf die Bereitstellung zugreifen. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungs-Bundles, bevor Sie sicherstellen, dass die Installationen erfolgreich sind. In der Regel tritt dieses Problem im Safari-Browser auf, kann aber gelegentlich auch in jedem Browser auftreten.

* Überprüfen Sie die Überwachungsprotokolle (error.log), sobald die Installation für eine Aktivität abgeschlossen ist. Warten Sie einige Minuten, bis keine Aktivität in den Protokollen vorhanden ist. Starten Sie die AEM-Instanz neu.

* Für den Fall, dass Sie **service-unavailable error** nach der Installation des AEM Forms 6.5.15.0 Service Packs, [Servlet-Fragment und -Bundle installieren](/help/forms/using/aem-service-pack-installation-solution.md) , um den Fehler zu beheben.
