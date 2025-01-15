---
title: Konfigurieren von Benutzern und Benutzergruppen
description: Auf dieser Seite erfahren Sie mehr über die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen, um die Erstellung und Verwaltung Ihrer Mobile Apps zu unterstützen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 9f814204-8cd4-4ba9-9e25-3ff1b25c1955
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 2%

---

# Konfigurieren von Benutzern und Benutzergruppen {#configure-your-users-and-user-groups}

{{ue-over-mobile}}

In diesem Kapitel werden die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen beschrieben, um die Erstellung und Verwaltung Ihrer Mobile Apps zu unterstützen.

## AEM Mobile-Programmbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

Um das Berechtigungsmodell für AEM-Apps zu organisieren und zu verwalten, sind die beiden folgenden Gruppen verfügbar:

* app-admins für App-Admins
* app-authors für App-Autoren

### Inhaltsautoren von AEM Mobile-Programmen (app-author-Gruppe) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe app-author sind für das Authoring von AEM-Mobile-App-Inhalten, einschließlich Seiten, Text, Bildern und Videos, verantwortlich.

#### Gruppenkonfiguration - app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine Benutzergruppe mit dem Namen „app-authors“:

   Navigieren Sie zur Benutzer-Admin Console: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Klicken Sie in der Benutzergruppenkonsole auf die Schaltfläche &quot;+&quot;, um eine Gruppe zu erstellen.

   Legen Sie die ID dieser Gruppe auf „app-authors“ fest, um anzugeben, dass es sich um einen bestimmten Typ von Autorenbenutzergruppe handelt, der für das Authoring von Mobile Apps innerhalb von AEM spezifisch ist.

1. Mitglied zur Gruppe hinzufügen: Autoren

   ![chlimage_1-18](assets/chlimage_1-18.png)

   Hinzufügen von app-authors zur Gruppe „Authors“

1. Nachdem Sie nun die Benutzergruppe app-authors erstellt haben, können Sie dieser neuen Gruppe über die Admin Console „Benutzer[ einzelne Team-Mitglieder ](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-19](assets/chlimage_1-19.png)

   Benutzergruppen bearbeiten

1. Navigieren Sie zur [Konsole Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloud-Services hinzu

   * (Lesen) unter /etc/cloudservices

   >[!NOTE]
   >
   >App-Autoren erweitern die standardmäßige Gruppe der Inhaltsautoren von AEM, sodass sie die Möglichkeit erben, Inhalte unter /content/phonegap zu erstellen

### Gruppe der AEM Mobile-Programmadministratoren (Gruppe der App-Administratoren) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe app-admins können Programminhalte mit den gleichen Berechtigungen erstellen, die auch in app-authors **AND** enthalten sind. Darüber hinaus sind sie auch verantwortlich für:

* Konfigurieren von PhoneGap Build- und Adobe-Mobile-Services-Cloud-Services in AEM
* Staging, Veröffentlichen und Löschen von OTA-Aktualisierungen zur Inhaltssynchronisierung der Anwendung

>[!NOTE]
>
>Berechtigungen bestimmen die Verfügbarkeit einiger Benutzeraktionen im AEM App Command Center.
>
>Beachten Sie, dass einige Optionen für app-authors, die für app-admins verfügbar sind, nicht verfügbar sind.

#### Gruppenkonfiguration - app-admins {#group-configuration-app-admins}

1. Erstellen Sie eine Gruppe mit dem Namen app-admins.
1. Fügen Sie die folgenden Gruppen zu Ihrer neuen Gruppe „app-admins“ hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Navigieren Sie zur [Konsole Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloud-Services hinzu

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/mobileservices
   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/phonegap-build

1. Fügen Sie in derselben Berechtigungskonsole Berechtigungen zum Staging, Veröffentlichen und Löschen von App-Inhaltsaktualisierungen hinzu

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

## Dashboard-Kachelberechtigungen {#dashboard-tile-permissions}

Dashboard-Kacheln können je nach den Berechtigungen, über die der Benutzer verfügt, unterschiedliche Aktionen anzeigen. Im Folgenden wird beschrieben, welche Aktionen für jede Kachel verfügbar sind.

Zusätzlich zu diesen Berechtigungen kann eine Aktion auch je nach Konfiguration der aktuellen App ein- oder ausgeblendet werden. Wenn der App beispielsweise keine PhoneGap-Cloud-Konfiguration zugewiesen wurde, hat es keinen Sinn, die Aktion „Remote-Build“ anzuzeigen. Diese sind unten unter den Abschnitten **Konfigurationsbedingung** aufgeführt.

### Programmkachel verwalten {#manage-app-tile}

Die Kachel verfügt derzeit über keine Aktionen, für die Berechtigungen erforderlich sind. Die Detailseite für die Anwendung enthält jedoch die folgenden Aktionen:

* *Bearbeiten* für app-author und app-admin (Benutzeroberflächen-Trigger - jcr:write - in /content/phonegap/{suffix})
* *Download* für app-author und app-admin (Benutzeroberflächen-Trigger - unter /content/phonegap/{suffix})

Die folgende Abbildung zeigt die Download- und Bearbeitungsoptionen für eine App:

![chlimage_1-21](assets/chlimage_1-21.png)
