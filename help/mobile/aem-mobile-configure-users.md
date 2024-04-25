---
title: Konfigurieren von Benutzern und Benutzergruppen
description: Auf dieser Seite erhalten Sie Informationen zu den Benutzerrollen und dazu, wie Sie Ihre Benutzer und Gruppen konfigurieren, um die Bearbeitung und Verwaltung Ihrer mobilen On-Demand-Dienste-App zu unterstützen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
exl-id: 58b7d1b9-a851-442a-9d02-212cad8abbed
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 6%

---

# Konfigurieren von Benutzern und Benutzergruppen {#configure-your-users-and-user-groups}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

In diesem Kapitel werden die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung der Erstellung und Verwaltung Ihrer Apps beschrieben.

## AEM Mobile-Anwendungsbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

### AEM Mobile Application Content Authors (Gruppe &quot;app-author&quot;) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe &quot;App-Autor&quot;sind für das Authoring AEM Inhalte mobiler Anwendungen verantwortlich, einschließlich Seiten, Text, Bildern und Videos.

#### Gruppenkonfiguration - app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine Benutzergruppe mit dem Namen &quot;app-authors&quot;:

   Navigieren Sie zur Admin Console Benutzer : [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Wählen Sie in der Benutzergruppenkonsole die Schaltfläche &quot;+&quot;, um eine Gruppe zu erstellen.

   Setzen Sie die ID dieser Gruppe auf &quot;app-authors&quot;, um anzugeben, dass es sich um einen bestimmten Typ von Autoren-Benutzergruppe handelt, die für das Authoring von Mobile Apps in AEM spezifisch ist.

1. Mitglied zur Gruppe hinzufügen: Autoren

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nachdem Sie die Benutzergruppe &quot;app-authors&quot;erstellt haben, können Sie dieser neuen Gruppe einzelne Teammitglieder über die [Admin Console des Benutzers](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Im Folgenden können Sie AEM Inhaltsautorengruppe hinzufügen:

   (Lesen Sie)

   * /app
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### AEM Mobile-Gruppe &quot;Anwendungsadministratoren&quot;(Gruppe &quot;app-admins&quot;) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe &quot;app-admins&quot;können Anwendungsinhalte mit denselben Berechtigungen erstellen, die auch für App-Autoren vorhanden sind **UND** Darüber hinaus sind folgende Aufgaben zuständig:

* Staging, Publishing und Deaktivieren der Anwendung ContentSync OTA-Aktualisierungen

>[!NOTE]
>
>Berechtigungen bestimmen die Verfügbarkeit einiger Benutzeraktionen im AEM App Command Center.
>
>Beachten Sie, dass einige Optionen nicht für App-Autoren verfügbar sind, die für App-Administratoren verfügbar sind.

### Gruppenkonfiguration - App-Administratoren {#group-configuration-app-admins}

1. Erstellen Sie eine Gruppe namens &quot;app-admins&quot;.
1. Fügen Sie Ihrer neuen Gruppe &quot;app-admins&quot;die folgenden Gruppen hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-169](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >workflow-users sind zum Remote-Build mit PhoneGap Build Service erforderlich

1. Navigieren Sie zum [Berechtigungskonsole](http://localhost:4502/useradmin) und Berechtigungen zum Verwalten von Cloud Services hinzufügen

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/mobileservices

1. Fügen Sie in derselben Berechtigungskonsole Berechtigungen zum Staging, Veröffentlichen und Löschen von App-Inhaltsaktualisierungen hinzu.

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/packages/mobileapp
   * (Lesen) unter /var/contentsync

   >[!NOTE]
   >
   >Paketreplikation wird verwendet, um App-Aktualisierungen von der Autoreninstanz zur Veröffentlichungsinstanz zu veröffentlichen.

   >[!CAUTION]
   >
   >Der Zugriff auf /var/contentsync wird standardmäßig verweigert.
   >
   >Wenn Sie die LESE-Berechtigung auslassen, kann dies dazu führen, dass leere Aktualisierungspakete erstellt und repliziert werden.

1. Mitglieder dieser Gruppe nach Bedarf hinzufügen
1. So exportieren Sie Inhalte oder laden sie hoch

   * (Lesen Sie unter /etc/contentsync für den Zugriff auf Exportvorlagen.)
   * (Lesen) auf /var zum Pfad traversal bei Lesevorgängen
   * (Lesen, Schreiben, Ändern, Löschen) unter /var/contentsync zum Schreiben, Lesen und Bereinigen zwischengespeicherter ContentSync-Exportinhalte

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten beim Erstellen einer AEM Mobile On-demand Services App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Inhaltserstellung AEM AEM Mobile On-demand Services App](/help/mobile/mobile-apps-ondemand.md)
