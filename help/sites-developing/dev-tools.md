---
title: Entwicklungs-Tools
description: Für die Entwicklung Ihrer JCR-, Apache Sling- oder Adobe Experience Manager-Anwendungen stehen mehrere Toolsets zur Verfügung.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 97310ed5-f8fb-416c-8a66-68f652abeaa0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 100%

---

# Entwicklungs-Tools{#development-tools}

Für die Entwicklung Ihrer JCR-, Apache Sling- oder Adobe Experience Manager (AEM)-Anwendungen stehen Ihnen die folgenden Toolsets zur Verfügung:

* Ein Set mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) und WebDAV. CRXDE Lite ist in CRX/AEM integriert und ermöglicht es Ihnen, gängige Entwicklungstätigkeiten im Browser vorzunehmen. Mit CRXDE Lite können Sie Dateien (wie .jsp und .java), Ordner, Vorlagen, Komponenten, Dialoge, Knoten, Eigenschaften und Bundles erstellen und bearbeiten, während gleichzeitig eine Protokollierung und Integration mit SVN erfolgt.

  CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den CRX/AEM-Server haben, wenn Sie zur Entwicklung einer Anwendung die vorkonfigurierten Komponenten und Java™-Bundles erweitern oder modifizieren oder wenn Sie keinen speziellen Debugger, keine Code-Vervollständigung und keine Syntaxhervorhebung benötigen.

* Ein Set, das Folgendes umfasst:
   * Eine integrierte Entwicklungsumgebung. Zum Beispiel [Eclipse](/help/sites-developing/howto-projects-eclipse.md) oder [IntelliJ](/help/sites-developing/ht-intellij.md).
   * Ein Build-Tool. Zum Beispiel [Apache Maven](/help/sites-developing/ht-projects-maven.md).
   * FileVault, das von Adobe entwickelt wurde, um ein Repository auf ein Dateisystem abzubilden, ein Versionskontrollsystem. Zum Beispiel Subversion.
   * Ein Bug-Tracker-System. Zum Beispiel Jira.
   * Ein zentrales System zur Verwaltung von Abhängigkeiten. Zum Beispiel Apache Archiva.
   * Und ein System zur Automatisierung von Builds. Zum Beispiel Apache Continuum.

  Mit diesem Setup können Sie Ihre Anwendung (Inhalt, Code, Konfiguration) vollständig in jede Entwicklungsumgebung und jeden Entwicklungsprozess integrieren. Das Bindeglied zwischen den verschiedenen Elementen ist die Darstellung des Dateisystems des Repositorys durch FileVault, da alle zuvor genannten Entwicklungswerkzeuge mit Dateien arbeiten können.

## Erweiterungen für integrierte Entwicklungsumgebungen {#extensions-for-integrated-development-environments}

Adobe hat die folgenden Erweiterungen veröffentlicht:

* [AEM Eclipse-Erweiterung](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets-Erweiterung](/help/sites-developing/aem-brackets.md)

### Weitere Tools {#other-tools}

AEM wird mit weiteren Tools ausgeliefert, die die Entwicklung erleichtern:

* [Dialogfeldeditor](/help/sites-developing/dialog-editor.md)
* [Verwalten von Wörterbüchern mithilfe des Übersetzers](/help/sites-developing/i18n-translator.md)
* [Verwalten von Paketen mithilfe von Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Entwickeln von AEM-Projekten mit Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Entwicklung von AEM-Projekten mit IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Vewenden des VLT-Tools](/help/sites-developing/ht-vlttool.md)
* [Verwendung des Proxy-Server-Tools](/help/sites-developing/ht-proxy-server.md)
* [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md)
* [AEM Repo Tool](/help/sites-developing/aem-repo-tool.md)

Tools, die die Erstellung neuer Projekte erleichtern:

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
* [AEM-Lazybones-Vorlagen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>Das folgende Tutorial kann für den Start eines neuen AEM-Projekts von Interesse sein:
>[Erste Schritte mit AEM Sites – Teil 1: Projekteinrichtung](https://helpx.adobe.com/de/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
