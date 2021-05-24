---
title: Entwicklungstools
seo-title: Entwicklungstools
description: Für die Entwicklung Ihrer JCR-, Apache Sling- oder AEM-Anwendungen stehen Ihnen eine Reihe von Toolsets zur Verfügung.
seo-description: Für die Entwicklung Ihrer JCR-, Apache Sling- oder AEM-Anwendungen stehen Ihnen eine Reihe von Toolsets zur Verfügung.
uuid: 1bee3a52-5d76-4b0c-a222-a02e12ff3a43
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 76c570e5-46ed-46be-9864-4fe4a83f0caf
exl-id: 97310ed5-f8fb-416c-8a66-68f652abeaa0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 62%

---

# Entwicklungstools{#development-tools}

Für die Entwicklung Ihrer JCR-, Apache Sling- oder AEM-Anwendungen stehen die folgenden Toolsets zur Verfügung:

* einen Satz, der aus [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md) und WebDAV besteht. CRXDE Lite ist in CRX/AEM integriert und ermöglicht es Ihnen, gängige Entwicklungstätigkeiten im Browser vorzunehmen. Mit CRXDE Lite können Sie Dateien (etwa JSP- und JAVA-Dateien), Ordner, Vorlagen, Komponenten, Dialoge, Knoten, Eigenschaften und Pakete erstellen und bearbeiten, während eine Protokollierung und Integration mit SVN erfolgt.

   CRXDE Lite wird empfohlen, wenn Sie keinen direkten Zugriff auf den CRX-/AEM-Server haben, wenn Sie eine Anwendung entwickeln, indem Sie die vordefinierten Komponenten und Java-Bundles erweitern oder ändern oder wenn Sie keinen dedizierten Debugger, keine Codevervollständigung und keine Syntaxhervorhebung benötigen.

* eine Gruppe, die aus einer integrierten Entwicklungsumgebung besteht (z. B.: [Eclipse](/help/sites-developing/howto-projects-eclipse.md) oder [IntelliJ](/help/sites-developing/ht-intellij.md)), ein Build-Tool (z. B.: [Apache Maven](/help/sites-developing/ht-projects-maven.md)), FileVault, das von Adobe entwickelt wurde, um ein Repository einem Dateisystem zuzuordnen, einem Versionskontrollsystem (z. B.: Subversion), einem Fehlertracker-System (z. B.: Jira), ein zentrales Abhängigkeitsmanagementsystem (z. B.: Apache Archiva) und ein Automatisierungssystem für den Build (z. B.: Apache Continuum).

   Diese Ausstattung ermöglicht Ihnen, Ihre Anwendung (Inhalte, Code, Konfiguration) vollständig in beliebige Entwicklungsumgebungen und -prozesse zu integrieren. Die Verbindung zwischen den verschiedenen Elementen ist die Dateisystemdarstellung des Repositorys durch FileVault, da alle genannten Entwicklungstools mit Dateien umgehen können.

## Erweiterungen für integrierte Entwicklungsumgebungen {#extensions-for-integrated-development-environments}

Adobe hat die folgenden Erweiterungen veröffentlicht:

* [AEM Eclipse-Erweiterung](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets-Erweiterung](/help/sites-developing/aem-brackets.md)
* [AEM IntelliJ-Erweiterung](https://github.com/headwirecom/aem-ide-tooling-4-intellij/blob/master/documenation/AEM%20Tooling%20Plugin%20for%20IntelliJ%20IDEA.pdf) (von Headwire)

### Weitere Tools  {#other-tools}

AEM wird mit weiteren Tools für die Entwicklung bereitgestellt:

* [Dialogfeldeditor](/help/sites-developing/dialog-editor.md)
* [Verwalten von Wörterbüchern mithilfe des Übersetzers](/help/sites-developing/i18n-translator.md)
* [Verwalten von Paketen mithilfe von Maven](/help/sites-developing/vlt-mavenplugin.md)
* [Entwickeln von AEM-Projekten mit Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [Erstellen von AEM-Projekten mit Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Entwicklung von AEM-Projekten mit IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Vewenden des VLT-Tools](/help/sites-developing/ht-vlttool.md)
* [Verwendung des Proxyservertools](/help/sites-developing/ht-proxy-server.md)
* [AEM-Modernisierungs-Tools](/help/sites-developing/modernization-tools.md)
* [AEM Repo Tool](/help/sites-developing/aem-repo-tool.md)

Tools, die die Erstellung neuer Projekte erleichtern:

* [AEM-Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype)
* [AEM-Lazybones-Vorlagen](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>Das folgende Tutorial kann für den Start eines neuen AEM-Projekts von Interesse sein:
>[Erste Schritte mit AEM Sites Teil 1 - Projekt-Setup](https://helpx.adobe.com/de/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
