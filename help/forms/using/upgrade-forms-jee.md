---
title: Aktualisierung auf AEM 6.5 Forms
seo-title: Upgrade to AEM 6.5 Forms
description: Sie können direkt von AEM 6.1 Forms, AEM 6.2 Forms und LiveCycle ES4 SP1 auf AEM 6.3 Forms aktualisieren.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 722e75a0-bcb3-465e-bb74-ea94a3b99fd3
source-git-commit: 37d2c70bff770d13b8094c5959e488f5531aef55
workflow-type: ht
source-wordcount: '375'
ht-degree: 100%

---

# Aktualisierung auf AEM 6.5 Forms auf JEE {#upgrade-to-aem-forms-jee}

AEM 6.5.12.0 Forms on JEE bietet zwei Arten von Installationsprogrammen: Vollständiges Installationsprogramm und Patch-Installationsprogramm.

**Vollständiges Installationsprogramm**: Sie können das [Vollinstallationsprogramm für AEM 6.5.12.0 on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) verwenden, um neue AEM Forms-Instanzen einzurichten oder Aktualisierungen von AEM 6.3 Forms on JEE, AEM 6.4 on JEE und eine nicht ersetzende Aktualisierung von AEM 6.5.x.x Forms on JEE auf AEM 6.5.12.0 Forms on JEE durchzuführen.

**Patch-Installationsprogramm**: Das [Patch-Installationsprogramm für AEM 6.5.12.0 on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) ist für Kundinnen und Kunden bestimmt, die bereits eine Version AEM 6.5.x.x verwenden. Mit dem Patch-Installationsprogramm können Sie eine Aktualisierung auf die neueste Version von AEM Forms durchführen.

Die folgende Tabelle zeigt Szenarien für die Verwendung des Installationsprogramms für vollständige Installationen und Patches.

![](assets/full-and-patch-installer.png)

Gehen Sie wie folgt vor, um mit dem vollständigen Installationsprogramm ein Upgrade von AEM 6.3 Forms on JEE oder AEM 6.4 Forms on JEE auf AEM 6.5.12.0 Forms on JEE durchzuführen:

1. Laden Sie das Installationsprogramm für AEM 6.5 Forms on JEE von der [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) herunter. Sie benötigen einen gültigen Wartungs- und Supportvertrag, um das Installationsprogramm zu verwenden.
1. Lesen Sie das Dokument [Checkliste für die Aktualisierung und Planung](https://www.adobe.com/go/learn_aemforms_upgrade_checklist_65_de), um sich über die Überprüfungen zu informieren, die für eine erfolgreiche Aktualisierung ausgeführt werden müssen.
1. Lesen Sie das Dokument [Vorbereiten auf die Aktualisierung auf AEM Forms](https://www.adobe.com/go/learn_aemforms_prepareupgrade_65_de), um zu erfahren, wie Sie die Aufgaben durchführen, die sicherstellen, dass die Aktualisierung richtig und nur mit minimalem Serverausfall verläuft.
1. Wählen Sie je nach vorhandener Umgebung und Anwendungsserver eines der folgenden Dokumente und befolgen Sie die Anweisungen.

   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for JBoss ](https://www.adobe.com/go/learn_aemforms_upgradeJBoss_65_de)
   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for WebSphere](https://www.adobe.com/go/learn_aemforms_upgradeWebSphere_65_de)
   * [Upgrade von AEM 6.3 oder AEM 6.4 Forms auf AEM 6.5 Forms for JBoss Turnkey](https://www.adobe.com/go/learn_aemforms_upgradeTurnkey_65_de)

Die direkte Aktualisierung von LiveCycle ES2, Live Cycle ES3, AEM 6.0 Forms, AEM 6.1 Forms oder AEM 6.2 Forms auf AEM 6.5 Forms ist nicht verfügbar. Sie können eine Zwischenaktualisierung auf eine oder mehrere Versionen von LiveCycle oder AEM Forms durchführen und dann auf AEM 6.5 Forms aktualisieren. Eine Liste der Zwischenversionen und entsprechenden Aktualisierungsanweisungen finden Sie unter [Auswählen eines Aktualisierungspfads](upgrade.md).
