---
title: Entwicklungs-Tools
description: Zur Entwicklung Ihrer JCR-, Apache Sling- oder Adobe Experience Manager-Anwendungen stehen mehrere Toolsets zur Verfügung.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 97310ed5-f8fb-416c-8a66-68f652abeaa0
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 34%

---

# Entwicklungs-Tools{#development-tools}

Um Ihre JCR-, Apache Sling- oder Adobe Experience Manager-Anwendungen (AEM) zu entwickeln, sind die folgenden Toolsets verfügbar:

* Ein Set mit [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) und WebDAV. CRXDE Lite ist in CRX/AEM integriert und ermöglicht es Ihnen, gängige Entwicklungstätigkeiten im Browser vorzunehmen. Mit CRXDE Lite können Sie Dateien (wie .jsp und .java), Ordner, Vorlagen, Komponenten, Dialogfelder, Knoten, Eigenschaften und Bundles erstellen und bearbeiten, während Sie die Protokollierung und Integration mit SVN durchführen.

  CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den CRX-/AEM-Server haben, wenn Sie eine Anwendung entwickeln, indem Sie die vordefinierten Komponenten und Java™-Bundles erweitern oder ändern oder wenn Sie keinen dedizierten Debugger, keine Codevervollständigung und keine Syntaxhervorhebung benötigen.

* ein Satz bestehend aus:
   * Eine integrierte Entwicklungsumgebung. Beispiel: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) oder [IntelliJ](/help/sites-developing/ht-intellij.md).
   * Ein Build-Tool. Beispiel: [Apache Maven](/help/sites-developing/ht-projects-maven.md).
   * FileVault, das von Adobe entwickelt wurde, um ein Repository einem Dateisystem zuzuordnen, einem Versionskontrollsystem. Beispiel: Subversion.
   * Ein Fehlerverfolgungssystem. Beispiel: Jira.
   * Ein zentrales Abhängigkeitsmanagementsystem. Beispiel: Apache Archiva.
   * Und ein System zur Automatisierung von Builds. Beispiel: Apache Continuum.

  Mit diesem Setup können Sie Ihre Anwendung (Inhalt, Code, Konfiguration) vollständig in jede Entwicklungsumgebung und jeden Entwicklungsprozess integrieren. Die Verknüpfung zwischen den verschiedenen Elementen ist die Dateisystemdarstellung des Repositorys über FileVault, da alle zuvor erwähnten Entwicklungstools mit Dateien funktionieren können.

## Erweiterungen für integrierte Entwicklungsumgebungen {#extensions-for-integrated-development-environments}

Adobe hat die folgenden Erweiterungen veröffentlicht:

* [AEM Eclipse-Erweiterung](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets-Erweiterung](/help/sites-developing/aem-brackets.md)

### Sonstige Instrumente {#other-tools}

AEM mit anderen Werkzeugen, die die Entwicklung erleichtern:

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
