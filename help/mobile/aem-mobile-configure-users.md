---
title: Konfigurieren von Benutzern und Benutzergruppen
description: Auf dieser Seite erfahren Sie mehr über die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen, um die Erstellung und Verwaltung Ihrer mobilen On-Demand-Services-App zu unterstützen.
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

In diesem Kapitel werden die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen beschrieben, um die Erstellung und Verwaltung Ihrer Mobile Apps zu unterstützen.

## AEM Mobile-Programmbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

### Inhaltsautoren von AEM Mobile-Programmen (app-author-Gruppe) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe app-author sind für das Authoring von AEM-Mobile-App-Inhalten, einschließlich Seiten, Text, Bildern und Videos, verantwortlich.

#### Gruppenkonfiguration - app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine Benutzergruppe mit dem Namen „app-authors“:

   Navigieren Sie zur Benutzer-Admin Console: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Klicken Sie in der Benutzergruppenkonsole auf die Schaltfläche &quot;+&quot;, um eine Gruppe zu erstellen.

   Legen Sie die ID dieser Gruppe auf „app-authors“ fest, um anzugeben, dass es sich um einen bestimmten Typ von Autorenbenutzergruppe handelt, der für das Authoring von Mobile Apps innerhalb von AEM spezifisch ist.

1. Mitglied zur Gruppe hinzufügen: Autoren

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nachdem Sie nun die Benutzergruppe app-authors erstellt haben, können Sie dieser neuen Gruppe über die Admin Console „Benutzer[ einzelne Team-Mitglieder ](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Mit dem folgenden können Sie zur Gruppe der Inhaltsautoren von AEM hinzufügen:

   (Lesen) weiter

   * /app
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### Gruppe der AEM Mobile-Programmadministratoren (Gruppe der App-Administratoren) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe app-admins können Programminhalte mit den gleichen Berechtigungen erstellen, die auch in app-authors **AND** enthalten sind. Darüber hinaus sind sie auch verantwortlich für:

* Staging, Veröffentlichen und Löschen von ContentSync-OTA-Aktualisierungen der Anwendung

>[!NOTE]
>
>Berechtigungen bestimmen die Verfügbarkeit einiger Benutzeraktionen im AEM App Command Center.
>
>Beachten Sie, dass einige Optionen für app-authors, die für app-admins verfügbar sind, nicht verfügbar sind.

### Gruppenkonfiguration - app-admins {#group-configuration-app-admins}

1. Erstellen Sie eine Gruppe mit dem Namen app-admins.
1. Fügen Sie die folgenden Gruppen zu Ihrer neuen Gruppe „app-admins“ hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-169](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >workflow-users sind erforderlich, um Remote-Build mit dem PhoneGap Build-Service durchzuführen

1. Navigieren Sie zur [Konsole Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloud-Services hinzu

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/mobileservices

1. Fügen Sie in derselben Berechtigungskonsole Berechtigungen zum Staging, Veröffentlichen und Löschen von App-Inhaltsaktualisierungen hinzu.

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/packages/mobileapp
   * (Lesen) unter /var/contentsync

   >[!NOTE]
   >
   >Die Paketreplikation wird verwendet, um App-Aktualisierungen von der Autoreninstanz in der Veröffentlichungsinstanz zu veröffentlichen.

   >[!CAUTION]
   >
   >Der Zugriff auf /var/contentsync wird vorkonfiguriert verweigert.
   >
   >Das Auslassen der Leseberechtigung kann dazu führen, dass leere Aktualisierungspakete erstellt und repliziert werden.

1. Fügen Sie dieser Gruppe nach Bedarf Mitglieder hinzu
1. So exportieren Sie Inhalte zum Hochladen

   * (Lesen) unter /etc/contentsync, um auf Exportvorlagen zuzugreifen
   * (Lesen) auf /var zum Durchlaufen des Pfads bei Lesevorgängen
   * (Lesen, Schreiben, Ändern, Löschen) unter /var/contentsync zum Schreiben, Lesen und Bereinigen von ContentSync zum Schreiben, Lesen und Bereinigen von zwischengespeicherten Exportinhalten

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Zuständigkeiten beim Erstellen einer AEM Mobile On-demand Services-App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM-Inhalten für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Authoring von AEM-Inhalten für die AEM Mobile On-demand Services-App](/help/mobile/mobile-apps-ondemand.md)
