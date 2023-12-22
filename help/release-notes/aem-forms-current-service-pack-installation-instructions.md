---
title: AEM Forms – Patch-Installationsanweisungen für AEM Forms
description: Installationsanweisungen für AEM Forms Service Pack für OSGi- und JEE-Umgebungen
exl-id: ae4c7e9d-9af8-4288-a6f9-e3bcbe7d153d
source-git-commit: 531eed9bb6d7792a6da0104b533a505738a64786
workflow-type: ht
source-wordcount: '1714'
ht-degree: 100%

---

# AEM 6.5 Forms Service Pack – Installationsanweisungen {#aem-form-patch-installation-instructions}

## Versionsinformationen

| Produkt | Adobe Experience Manager 6.5 Forms |
|---|---|
| Version | 6.5.19.0 (OSGi), 6.5.19.1 (JEE) |
| Typ | Service Pack-Version |
| Datum | 8. Dezember 2023 |
| Download-URL | [Neueste AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) |

>[!NOTE]
>
>Eine vollständige Liste der behobenen Probleme finden Sie in den aktuellen [AEM Service Pack Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de).

## Was ist in Experience Manager Forms 6.5 enthalten?

Das Service Pack für Adobe Experience Manager (AEM) Forms enthält neue und aktualisierte Funktionen, darunter wichtige kundenseitig geforderte Erweiterungen sowie Verbesserungen bei Leistung, Stabilität und Sicherheit. AEM Forms veröffentlicht in regelmäßigen Abständen Service Packs mit den neuesten Funktionen und Verbesserungen. Wählen Sie abhängig von Ihrem Technologie-Stack einen der folgenden Pfade, um das Service Pack herunterzuladen und in Ihrer Umgebung zu installieren:

* [Herunterladen und Installieren des Service Packs auf einer Umgebung von AEM Forms on JEE](#download-and-install-for-jee-service-pack)
* [Herunterladen und Installieren des Service Packs auf einer Umgebung von AEM Forms on OSGi](#download-and-install-for-osgi-service-pack)

>[!NOTE]
>
> * Adobe veröffentlicht mit jedem sechsten Service Pack ein vollständiges Installationsprogramm. AEM 6.5 Forms Service Pack 18 (6.5.18.0) ist das neueste vollständige Installationsprogramm für JEE. Das vollständige Installationsprogramm unterstützt neue Plattformen, während das reguläre Service Pack-Installationsprogramm neue Funktionen, Fehlerbehebungen und allgemeine Verbesserungen enthält. Wenn Sie eine Neuinstallation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms on JEE-Umgebung planen, empfiehlt Adobe die Verwendung des Vollinstallationsprogramms für AEM 6.5.18.0 Forms on JEE vom 31. August 2023 anstelle des AEM 6.5 Forms-Installationsprogramms vom 08. April 2019 oder des AEM 6.5.12.0 Forms-Installationsprogramms vom 03. März 2022. Nachdem Sie das vollständige Installationsprogramm verwendet haben, installieren Sie das neueste Service Pack.
> * Die im [AEM 6.5-Schnellstart](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de) verfügbaren AEM Forms-Funktionen, z. B. adaptive Formulare, dienen nur zu Kennenlern- und Evaluierungszwecken. Für die Verwendung in der Produktion ist es unerlässlich, eine gültige Lizenz für AEM Forms zu erwerben.

<!--

## Prerequisites {#prerequisites}

From AEM Service Pack 6.5.19.0 and onwards, XMLFM (XML output) will be available in 64-bit only, therefore you require the latest [Microsoft Visual C++ Redistributable (2015-2022) 64-bit](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170) to be installed on Windows Server prior to JEE or OSGi installation.

>[!NOTE]
> This prerequisite is required in addition to the already existing Microsoft Visual C++ Redistributable 32-bit.

-->

## Service Pack herunterladen und auf einer Umgebung von AEM Forms on JEE installieren {#download-and-install-for-jee-service-pack}

![JEE-Installation](/help/forms/using/assets/jeeinstallation.png)

+++1. Erstellen Sie ein Backup Ihrer bestehenden Umgebung

1. Sichern Sie Ihr [CRX-Repository, Datenbankschema und GDS (Global Document Storage)](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html?lang=de).
1. Sichern Sie den Ordner &lt;*AEM_forms_root*>/deploy.

>[!NOTE]
>
> Bevor Sie das AEM Service Pack-Installationsprogramm ausführen, vergewissern Sie sich, dass Sie über Schreibzugriffsrechte für das AEM-Installationsverzeichnis verfügen.

+++

+++2. Laden Sie die erforderliche Software herunter

* [AEM Forms on JEE Service Pack](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)
* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de)
* [Forms-Add-on-Paket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)
* [Fragment-Servlet](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Forg.apache.felix.http.servlet-api-1.2.0_fragment_full.jar)

+++

+++ 3. Installieren Sie Microsoft Visual C++ Redistributable Packages

* Laden Sie die [64-Bit-Version der Microsoft Visual C++ Redistributable Packages for Visual Studio 2015, 2017, 2019 und 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) auf den Computer herunter, auf dem AEM 6.5 Forms installiert ist, und installieren Sie sie.

>[!NOTE]
>
> Stellen Sie sicher, dass Sie das Redistributable installieren, auch wenn eine frühere Version bereits installiert ist, um die Verfügbarkeit der neuesten Version zu gewährleisten.

+++

+++3. Installieren Sie das AEM Forms on JEE Service Pack:

1. Stoppen Sie den Programm-Server.
1. Extrahieren Sie das **AEM Forms on JEE Service Pack-Installationsarchiv** auf Ihrer Festplatte:

   * **Windows**
Navigieren Sie zu dem entsprechenden Verzeichnis auf dem Installationsmedium oder dem Ordner auf Ihrer Festplatte, in den Sie das Installationsprogramm kopiert haben, und doppelklicken Sie auf die Datei `aemforms65_cfp_install.exe`.

      * (Windows 32-Bit) `Windows\Disk1\InstData\VM`
      * (Windows 64-Bit) `Windows_64Bit`\ `Disk1\InstData\VM`

   * **Linux®**
Navigieren Sie zum entsprechenden Ordner und geben Sie in einer Shell Folgendes ein`./aem65_cfp_install.bin`.

      * (Linux®) `Linux/Disk1/InstData/NoVM`

   Dadurch wird ein Installationsassistent gestartet, der Sie durch die Installation führt.

1. Klicken Sie im Begrüßungsbildschirm auf **[!UICONTROL Weiter]**.
1. Stellen Sie auf dem Bildschirm **Installationsordner auswählen** sicher, dass der Standardspeicherort, der angezeigt wird, für Ihre bestehende Installation korrekt ist, oder klicken Sie auf **[!UICONTROL Durchsuchen]**, um den alternativen Ordner auszuwählen, auf dem AEM Forms installiert ist, und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Zusammenfassung der Informationen zum Service Pack und klicken Sie auf **[!UICONTROL Weiter]**.
1. Lesen Sie die Informationen in der Zusammenfassung vor der Installation und klicken Sie auf **[!UICONTROL Installieren]**.
1. Wenn die Installation abgeschlossen ist, klicken Sie auf **[!UICONTROL Weiter]**, um die Schnellkorrektur-Updates auf Ihre installierten Dateien anzuwenden.
1. **[Nur für Windows]:** Führen Sie einen der folgenden Schritte aus:

   * Sie können entweder die Option **Configuration Manager starten** deaktivieren, bevor Sie auf **[!UICONTROL Fertig]** klicken. Führen Sie **Configuration Manager** durch Verwendung der Datei **ConfigurationManager.bat** in `[aem-forms root]\configurationManager\bin` aus.

   * Oder deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Navigieren Sie vor der Ausführung von **Configuration Manager** mit **ConfigurationManager.exe** oder **ConfigurationManager_IPv6.exe** zu *`<AEMForms_Install_Dir>\configurationManager\bin`* und ersetzen Sie **ConfigurationManager.lax** und **ConfigurationManager_IPV6.lax** durch die neuesten Dateien [ConfigurationManager.lax](/help/assets/ConfigurationManager.lax) und [ConfigurationManager_IPV6.lax](/help/assets/ConfigurationManager_IPv6.lax).

     >[!NOTE]
     >
     >* Wenn Sie die Datei **ConfigurationManager.bat** aktualisieren oder ersetzen, müssen Sie die .lax-Dateien nicht manuell aktualisieren.

1. **[Nur für Unix-basierte Systeme]:** Das Kontrollkästchen **Configuration Manager starten** ist standardmäßig aktiviert. Klicken Sie auf **[!UICONTROL Fertig]**, um Configuration Manager sofort zu starten. Um **Configuration Manager** erst später zu starten, deaktivieren Sie die Option **Configuration Manager starten**, bevor Sie auf **[!UICONTROL Fertig]** klicken. Sie können **Configuration Manager** später mit dem entsprechenden Skript im Verzeichnis `[AEM_forms_root]/configurationManager/bin` starten.

1. Wählen Sie je nach Anwendungs-Server eines der folgenden Dokumente aus und befolgen Sie die Anweisungen im Bereich *Konfigurieren und Bereitstellen von AEM Forms*.

   * [Installieren und Bereitstellen von AEM Forms for JBoss®](https://www.adobe.com/go/learn_aemforms_installJBoss_65_de)
   * [Installieren und Bereitstellen von AEM Forms für WebSphere®](https://www.adobe.com/go/learn_aemforms_installWebSphere_65_de)
   * [Installieren und Bereitstellen von AEM Forms for WebLogic](https://www.adobe.com/go/learn_aemforms_installWebLogic_65_de)
   * [Installieren und Bereitstellen von AEM Forms for JBoss® Cluster](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/install-cluster-jboss.pdf)
   * [Installieren und Bereitstellen von AEM Forms for WebSphere® Cluster](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/install-cluster-websphere.pdf)
   * [Installieren und Bereitstellen von AEM Forms for WebLogic Cluster](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/install-cluster-weblogic.pdf)


>[!NOTE]
>
> Nach der Installation von AEM Forms on JEE Service Pack müssen Sie das Add-On-Paket für Forms aus dem Ordner `crx-repository\install` entfernen, bevor Sie den Anwendungs-Server neu starten. Laden Sie das neueste Add-On-Paket für Forms vom [Software Distribution-Portal](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter.

+++

+++4. Installation des Servlet-Fragments (AEM Service Pack 6.5.14.0 oder früher)

>[!NOTE]
>
> * Wenn Sie ein Upgrade von **AEM Service Pack 6.5.15.0** durchführen, ist die Installation des **Servlet-Fragments** nicht erforderlich. Für die Versionen **AEM Service Pack 6.5.14.0** oder früher ist es zwingend erforderlich, das Servlet-Fragment zu installieren.
> * Die Installation des **Servlet-Fragments** ist obligatorisch für alle Anwendungs-Server, mit Ausnahme derer, die auf **JBoss® EAP 7.4.0** laufen.


So laden Sie das Servlet-Fragment herunter und installieren es:

1. Wenn Sie das Fragment nicht heruntergeladen haben, laden Sie es von [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) herunter.

1. Starten Sie den Anwendungs-Server, warten Sie, bis sich die Protokolle stabilisiert haben und überprüfen Sie den Bundle-Status.

1. Öffnen Sie Web-Konsole Bundles. Die Standard-URL ist `http://[Server]:[Port]/system/console/bundles`.

1. Klicken Sie auf „Installieren/Aktualisieren“. Wählen Sie das heruntergeladene Fragment aus, `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`. Klicken Sie auf **Installieren** oder **Aktualisieren**. Warten Sie, bis sich der Anwendungsserver stabilisiert hat

1. Stoppen Sie den Anwendungs-Server.

+++

+++5. Installieren des AEM Service Pack

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.
1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.
1. Laden Sie das Service Pack von [Software Distribution](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter.<!-- UPDATE FOR EACH NEW RELEASE -->
1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit denen Sie das Service Pack von [!DNL ExperienceManager] automatisch installieren können.<!--       UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist.
Das Paket wird automatisch installiert.

* Verwenden Sie die [HTTP-API von Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

  >[!NOTE]
  >
  >Das Service Pack von Experience Manager unterstützt keine Bootstrap-Installation. <!-- UPDATE FOR EACH NEW RELEASE -->

  **Validierung der Installation**

  Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

   1. Auf der Seite mit Produktinformationen (`/system/console/productinfo`) wird die aktualisierte Versionszeichenfolge `Adobe Experience Manager (spversion)` unter [!UICONTROL Installierte Produkte] angezeigt.<!-- UPDATE FOR EACH NEW RELEASE -->
   1. Alle OSGi-Bundles haben in der OSGi-Konsole entweder den Status **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (Verwenden Sie die Web-Konsole: `/system/console/bundles`).
   1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` ist Version 1.22.14 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`).

+++

+++6. Installieren des Add-On-Pakets zu AEM Experience Manager Forms

1. Stellen Sie sicher, dass Sie das [!DNL Experience Manager] Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-on-Paket wie unter [Installieren des AEM Forms-Add-on-Pakets](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) beschrieben.
1. Wenn Sie in Experience Manager 6.5 Forms Briefe verwenden, installieren Sie das [neueste AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

+++

## Herunterladen und Installieren des Service Packs in einer Umgebung von AEM Forms on OSGi {#download-and-install-for-osgi-service-pack}

![OSGi-Installationsschritte](/help/forms/using/assets/osgiinstallation.png)


+++1. Erstellen Sie ein Backup Ihrer bestehenden Umgebung

1. Sichern Sie Ihr [CRX-Repository und Datenbankschema](https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/aem-forms-backup-recovery/backing-aem-forms-data.html?lang=de).

>[!NOTE]
>
>Wenn Sie das AEM Forms Service Pack für eine relationale Datenbank installieren, müssen Sie unbedingt ein Backup von DB_schema erstellen.

+++

+++2. Laden Sie die erforderliche Software herunter

* [AEM Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/release-notes.html?lang=de)
* [Forms-Add-on-Paket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de)

+++

+++ 3. Installieren Sie Microsoft Visual C++ Redistributable Packages

* Laden Sie die [64-Bit-Version der Microsoft Visual C++ Redistributable Packages for Visual Studio 2015, 2017, 2019 und 2022](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) auf den Computer herunter, auf dem AEM 6.5 Forms installiert ist, und installieren Sie sie.

>[!NOTE]
>
>
>Stellen Sie sicher, dass Sie das Redistributable installieren, auch wenn eine frühere Version bereits installiert ist, um die Verfügbarkeit der neuesten Version zu gewährleisten.

+++

+++4. Installieren des AEM Service Pack

1. Starten Sie die Instanz vor der Installation neu, wenn sich die Instanz im Update-Modus befindet (wenn die Instanz von einer früheren Version aktualisiert wurde). Adobe empfiehlt einen Neustart, wenn die aktuelle Betriebszeit für eine Instanz hoch ist.
1. Erstellen Sie vor der Installation eine Momentaufnahme oder ein neues Backup Ihrer [!DNL Experience Manager]-Instanz.
1. Laden Sie das Service Pack von [Software Distribution](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) herunter.<!-- UPDATE FOR EACH NEW RELEASE -->
1. Öffnen Sie Package Manager und wählen Sie dann **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen. Weitere Informationen finden Sie unter [Package Manager](/help/sites-administering/package-manager.md).
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

**Automatische Installation**

Es gibt zwei verschiedene Methoden, mit der Sie das Service Pack von [!DNL Experience Manager] automatisch installieren können.<!--  UPDATE FOR EACH NEW RELEASE -->

* Platzieren Sie das Paket in den Ordner `../crx-quickstart/install`, wenn der Server online verfügbar ist. Das Paket wird automatisch installiert.
* Verwenden Sie die [HTTP-API von Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de). Verwenden Sie `cmd=install&recursive=true`, damit die verschachtelten Pakete installiert werden.

  >[!NOTE]
  >
  >Das Service Pack von Experience Manager unterstützt keine Bootstrap-installation. <!-- UPDATE FOR EACH NEW RELEASE -->

  **Validierung der Installation**

  Informationen zu den Plattformen, die für diese Version zertifiziert sind, finden Sie in den [technischen Anforderungen](/help/sites-deploying/technical-requirements.md).

   1. Die Seite mit den Produktinformationen (`/system/console/productinfo`) zeigt die aktualisierte Versionszeichenfolge `Adobe Experience Manager (spversion)` unter [!UICONTROL Installierte Produkte] an.<!-- UPDATE FOR EACH NEW RELEASE -->

   1. Alle OSGi-Bundles sind in der OSGi-Konsole entweder **[!UICONTROL AKTIV]** oder **[!UICONTROL FRAGMENT]** (zu verwendende Web-Konsole: `/system/console/bundles`).

      1. Das OSGi-Bundle `org.apache.jackrabbit.oak-core` hat die Version 1.22.14 oder höher (zu verwendende Web-Konsole: `/system/console/bundles`).

+++

+++4. Installieren des Adobe Experience Manager Forms (AEM)-Add-On-Pakets

1. Stellen Sie sicher, dass Sie das [!DNL Experience Manager] Service Pack installiert haben.
1. Wählen Sie unter den aufgeführten [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) das für Ihr Betriebssystem passende Forms-Add-on-Paket aus und laden Sie es herunter.
1. Installieren Sie das Forms-Add-on-Paket wie unter [Installieren des AEM Forms-Add-on-Pakets](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) beschrieben.
1. Wenn Sie in Experience Manager 6.5 Forms Briefe verwenden, installieren Sie das [neueste AEMFD-Kompatibilitätspaket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

+++

## Fehlerbehebung

* Wenn das **Dialogfeld auf der Package Manager-Oberfläche** während der Installation des Service Packs beendet wird, warten Sie, bis sich die Fehlerprotokolle stabilisiert haben, bevor Sie auf die Bereitstellung zugreifen. Warten Sie auf die spezifischen Protokolle im Zusammenhang mit der Deinstallation des Aktualisierungspakets, bevor Sie sich vergewissern, dass die Installationen erfolgreich waren. Dieses Problem tritt in der Regel im Safari-Browser auf, kann aber zeitweise auch in jedem anderen Browser auftreten.

* Überprüfen Sie die Überwachungsprotokolle (error.log) nach Abschluss der Installation auf Aktivitäten. Warten Sie ein paar Minuten, bis keine Aktivität in den Protokollen zu sehen ist. Starten Sie die AEM-Instanz neu.

* Falls Sie nach der Installation des neuesten Service Packs von AEM Forms 6.5.15.0 einen Fehler **Dienst nicht verfügbar** erhalten, [installieren Sie das Servlet-Fragment und -Paket](/help/forms/using/aem-service-pack-installation-solution.md), um den Fehler zu beheben.
