---
title: Konfigurieren von Benutzern und Benutzergruppen
description: Auf dieser Seite erfahren Sie mehr über die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung der Erstellung und Verwaltung Ihrer mobilen Apps.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
exl-id: 9f814204-8cd4-4ba9-9e25-3ff1b25c1955
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 5%

---

# Konfigurieren von Benutzern und Benutzergruppen {#configure-your-users-and-user-groups}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

In diesem Kapitel werden die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung der Erstellung und Verwaltung Ihrer Apps beschrieben.

## AEM Mobile-Anwendungsbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

Um das Berechtigungsmodell für AEM Apps zu organisieren und zu verwalten, sind die folgenden beiden Gruppen verfügbar:

* App-Administratoren für App-Administratoren
* app-authors für App-Autoren

### AEM Mobile Application Content Authors (Gruppe &quot;app-author&quot;) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe &quot;App-Autor&quot;sind für das Authoring AEM Inhalte mobiler Anwendungen verantwortlich, einschließlich Seiten, Text, Bildern und Videos.

#### Gruppenkonfiguration - app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine Benutzergruppe mit dem Namen &quot;app-authors&quot;:

   Navigieren Sie zur Admin Console Benutzer : [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Wählen Sie in der Benutzergruppenkonsole die Schaltfläche &quot;+&quot;, um eine Gruppe zu erstellen.

   Setzen Sie die ID dieser Gruppe auf &quot;app-authors&quot;, um anzugeben, dass es sich um einen bestimmten Typ von Autoren-Benutzergruppe handelt, die für das Authoring von Mobile Apps in AEM spezifisch ist.

1. Mitglied zur Gruppe hinzufügen: Autoren

   ![chlimage_1-18](assets/chlimage_1-18.png)

   App-Autoren zur Gruppe Autoren hinzufügen

1. Nachdem Sie die Benutzergruppe &quot;app-authors&quot;erstellt haben, können Sie dieser neuen Gruppe einzelne Teammitglieder über die [Admin Console des Benutzers](http://localhost:4502/libs/granite/security/content/useradmin.md).

   ![chlimage_1-19](assets/chlimage_1-19.png)

   Benutzergruppen bearbeiten

1. Navigieren Sie zum [Berechtigungskonsole](http://localhost:4502/useradmin) und Berechtigungen zum Verwalten von Cloud Services hinzufügen

   * (Lesen) unter /etc/cloudservices

   >[!NOTE]
   >
   >App-Autoren erweitern die standardmäßige Gruppe &quot;content-authors&quot;(Autoren) von AEM, sodass sie die Möglichkeit erben, Inhalte unter /content/phonegap zu erstellen

### AEM Mobile-Gruppe &quot;Anwendungsadministratoren&quot;(Gruppe &quot;app-admins&quot;) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe &quot;app-admins&quot;können Anwendungsinhalte mit denselben Berechtigungen erstellen, die auch für App-Autoren vorhanden sind **UND** Darüber hinaus sind folgende Aufgaben zuständig:

* Konfigurieren von PhoneGap Build und Adobe Mobile Services Cloud Services in AEM
* Staging, Veröffentlichen und Löschen von OTA-Aktualisierungen für die Inhaltssynchronisierung

>[!NOTE]
>
>Berechtigungen bestimmen die Verfügbarkeit einiger Benutzeraktionen im AEM App Command Center.
>
>Beachten Sie, dass einige Optionen nicht für App-Autoren verfügbar sind, die für App-Administratoren verfügbar sind.

#### Gruppenkonfiguration - App-Administratoren {#group-configuration-app-admins}

1. Erstellen Sie eine Gruppe namens &quot;app-admins&quot;.
1. Fügen Sie Ihrer neuen Gruppe &quot;app-admins&quot;die folgenden Gruppen hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Navigieren Sie zum [Berechtigungskonsole](http://localhost:4502/useradmin) und Berechtigungen zum Verwalten von Cloud Services hinzufügen

   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/mobileservices
   * (Lesen, Ändern, Erstellen, Löschen, Replizieren) unter /etc/cloudservices/phonegap-build

1. Fügen Sie in derselben Berechtigungskonsole Berechtigungen zum Staging, Veröffentlichen und Löschen von App-Inhaltsaktualisierungen hinzu

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

## Berechtigungen für Dashboard-Kacheln {#dashboard-tile-permissions}

Dashboard-Kacheln können je nach den Berechtigungen des Benutzers unterschiedliche Aktionen anzeigen. Im Folgenden wird beschrieben, welche Aktionen für die einzelnen Kacheln verfügbar sind.

Zusätzlich zu diesen Berechtigungen kann eine Aktion auch je nach Konfiguration der aktuellen App ein-/ausgeblendet werden. Es hat beispielsweise keinen Zweck, die Aktion &quot;Remote Build&quot;anzuzeigen, wenn der App keine PhoneGap-Cloud-Konfiguration zugewiesen wurde. Diese sind unten unter &quot;**Konfigurationsbedingung**&quot;.

### App-Kachel verwalten {#manage-app-tile}

Die Kachel verfügt derzeit über keine Aktionen, für die Berechtigungen erforderlich sind. Die Detailseite für die Anwendung weist jedoch die folgenden Aktionen auf:

* *Bearbeiten* für app-author und app-admin (UI-Trigger - jcr:write - für /content/phonegap/{suffix})
* *Herunterladen* für app-author und app-admin (UI-Trigger - unter /content/phonegap/{suffix})

Die folgende Abbildung zeigt die Download- und Bearbeitungsoptionen für eine App:

![chlimage_1-21](assets/chlimage_1-21.png)
