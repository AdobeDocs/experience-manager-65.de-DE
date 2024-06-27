---
title: Aktualisierung auf AEM 6.5 Forms
description: Sie können direkt von AEM 6.3 Forms und AEM 6.4 Forms auf AEM 6.5 Forms aktualisieren.
content-type: reference
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin,User
exl-id: 2fc8abec-8ba6-40b7-bbb1-4288eeea7c86
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms Upgrade
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '364'
ht-degree: 100%

---

# Aktualisierung auf AEM 6.5 Forms {#upgrade-to-aem-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


AEM Forms 6.5 beinhaltet verschiedene neue Funktionen und Verbesserungen, die die Erstellung, Verwaltung und die Benutzererfahrung von Formularen und Korrespondenz weiter optimieren. Weitere Informationen über die neuen Funktionen und Verbesserungen von AEM 6.5 Forms finden Sie im Dokument [Übersicht über die neuen Funktionen](../../forms/using/whats-new.md).

Sie können Ihre vorhandene LiveCycle- oder AEM Forms-Installation aktualisieren, um neue Funktionen und Verbesserungen in AEM 6.5 Forms zu erhalten und gleichzeitig vorhandene Daten, Prozesse und Assets beizubehalten. Bei der Aktualisierung werden Metadaten und Status der Prozesse ebenfalls beibehalten. Sie können einen Aktualisierungspfad auswählen, um mit der Aktualisierung zu beginnen.

Das folgende Diagramm zeigt die verfügbaren Aktualisierungspfade für AEM Forms on OSGi:

![OSGi-Aktualisierungsablauf](do-not-localize/osgi-upgrade-path.png)

Sie können von hier aus eine direkte Aktualisierung durchführen:

* AEM 6.3 Forms on OSGi
* AEM 6.4 Forms on OSGi

Eine Multihop-Aktualisierung ist möglich von:

* AEM 6.0 Forms on OSGi
* AEM 6.1 Forms on OSGi
* AEM 6.2 Forms on OSGi

Das folgende Diagramm zeigt die verfügbaren Aktualisierungspfade für AEM Forms on JEE:

![JEE-Aktualisierung 6.5](do-not-localize/jee-upgrade-6-5.png)


Sie können von hier aus eine direkte Aktualisierung durchführen:

* AEM 6.3 Forms on JEE
* AEM 6.4 Forms on JEE
* AEM 6.5.x.x Forms on JEE

Eine Multihop-Aktualisierung ist möglich von:

* LiveCycle ES4 SP1
* AEM 6.0 Forms on JEE
* AEM 6.1 Forms on JEE
* AEM 6.2 Forms on JEE

AEM 6.5.18.0 Forms on JEE bietet zwei Arten von Installationsprogrammen: ein [Vollinstallationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) und ein [Patch-Installationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de).

**Vollinstallationsprogramm**: Sie können das Vollinstallationsprogramm verwenden, um neue AEM Forms-Instanzen einzurichten oder Upgrades von AEM 6.5.x.x Forms on JEE auf AEM 6.5.18.0 Forms on JEE durchzuführen.

**Patch-Installationsprogramm**: Das Patch-Installationsprogramm ist für Kundinnen und Kunden vorgesehen, die bereits AEM 6.5.x.x verwenden. Mit dem Patch-Installationsprogramm können Sie eine Aktualisierung auf die neueste Version von AEM Forms durchführen.

Die folgende Abbildung zeigt Szenarien für die Verwendung des vollständigen Installationsprogramms und des Patch-Installationsprogramms.

![Vollständiges Installationsprogramm und Patch-Installationsprogramm](/help/forms/using/assets/full-and-patch-installer.png)

Weitere Informationen zum Installieren des neuesten Service Pack für die JEE-Umgebung finden Sie in den [Installationsanweisungen für das AEM 6.5 Forms Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/aem-forms-current-service-pack-installation-instructions.html?lang=de).

<!--
[Work in Progress]

Migration involves moving only assets (PDF, XDP, images, adaptive forms, correspondence management assets) from one server to another - processes (LCA), settings, configurations, and a few other pieces of metadata are not migrated. Perform the following steps to migrate to AEM 6.3 Forms:

1. Set up a fresh environment of [AEM 6.3 Forms](https://adobe.com/go/learn_aemforms_documentation_63).
1. Move XDP or other compatible assets to the freshly set instance. For detailed instructions, see [Importing and exporting assets to AEM Forms](../../forms/using/import-export-forms-templates.md). [
   ](../../forms/using/import-export-forms-templates.md)
1. Build the required services, if any.

   For example, if you are using AEM Forms on JEE Document Services, changes are required in the code to use document services available in AEM Forms on OSGi.

1. Perform post-installation activities:

    * **Run Migration Utility**

      The migration utility makes the adaptive forms and correspondence management assets of earlier versions compatible with AEM 6.3 forms. You can download the utility from AEM Software Distribution. For step-by-step information to configure and use the migration utility, see [migration utility](../../forms/using/migration-utility.md) documentation.

    * **Reconfigure Adobe Sign**

      If you had Adobe Sign configured in the previous version of AEM Forms, then reconfigure Adobe Sign from AEM Cloud services. For more details, see [Integrate Adobe Sign with AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

      Moreover, AEM 6.3 Forms release has introduced many new Adobe Sign features. For step-by-step information to use Adobe Sign, see [Using Adobe Sign in an adaptive form](../../forms/using/working-with-adobe-sign.md).

    * **Reconfigure analytics and reports**

      In AEM 6.3 Forms, traffic variable for source and success event for impression are not available. So, when you upgrade to AEM 6.3 Forms, AEM Forms stops sending data to Adobe Analytics server and analytics reports for adaptive forms are not available. Moreover, AEM 6.3 Forms introduces traffic variable for the version of form analytics and success event for the amount of time spent on a field. So, reconfigure analytics and reports for your AEM Forms environment. For detailed steps, see [Configuring analytics and reports](../../forms/using/configure-analytics-forms-documents.md).

      Methods to calculate average fill time for forms and average read time for have changed. So, when you upgrade to AEM 6.3 forms, older data (data from previous AEM Forms release) for these metrics is available only in Adobe Analytics. It is not visible in AEM Forms analytics reports. For these metrics, AEM Forms analytics reports display data which is captured after performing the upgrade.
      
      -->


