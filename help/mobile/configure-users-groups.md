---
title: Konfigurieren von Benutzern und Benutzergruppen
seo-title: Konfigurieren von Benutzern und Benutzergruppen
description: Folgen Sie dieser Seite, um die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen Apps zu verstehen.
seo-description: Folgen Sie dieser Seite, um die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen Apps zu verstehen.
uuid: 55cea2b3-d7e6-4174-92b3-ee97e46b59c4
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 167f3bd9-7dbc-4e6b-9868-3ee53935641b
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 52%

---


# Konfigurieren von Benutzern und Benutzergruppen {#configure-your-users-and-user-groups}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

In diesem Kapitel werden die Benutzerrollen und die Konfiguration der Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung der mobilen Apps beschrieben.

## AEM Mobile-Anwendungsbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

Um das Berechtigungsmodell für AEM Apps zu organisieren und zu verwalten, stehen die folgenden zwei Gruppen zur Verfügung:

* app-admins für App-Administratoren
* app-authors for App Authors

### AEM Mobile Application Content Authors (App-Autorengruppe) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe &quot;App-Autor&quot;sind für das Authoring AEM Inhalte mobiler Anwendungen zuständig, einschließlich Seiten, Text, Bilder und Videos.

#### Gruppenkonfiguration: app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine neue Benutzergruppe mit dem Namen „app-authors“:

   Navigieren Sie zur Admin Console &quot;Benutzer&quot;: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Wählen Sie in der Benutzergruppenkonsole das Plussymbol, um die Gruppe zu erstellen.

   Legen Sie die ID dieser Gruppe auf „app-authors“ fest, um anzugeben, dass diese Autorenbenutzergruppe spezifisch für mobile Anwendungen in AEM ist.

1. Hinzufügen von Mitgliedern zur Gruppe: Autoren

   ![chlimage_1-18](assets/chlimage_1-18.png)

   hinzufügen von App-Autoren zur Autorengruppe

1. Nachdem Sie die Benutzergruppe „app-authors“ erstellt haben, können Sie ihr über die [Benutzer-Admin](http://localhost:4502/libs/granite/security/content/useradmin.md)-Konsole Teammitglieder hinzufügen.

   ![chlimage_1-19](assets/chlimage_1-19.png)

   Bearbeiten von Benutzergruppen

1. Navigieren Sie zur Konsole [Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloudservices hinzu.

   * (Lesen) unter /etc/cloudservices
   >[!NOTE]
   >
   >App-Autoren erweitern die Standard-Gruppe &quot;Inhaltautoren&quot;(Autoren) von AEM und erben so die Möglichkeit, Inhalte unter /content/phonegap zu erstellen

### AEM Mobile Application Administrators Group (app-admins group) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe &quot;app-admins&quot; können Anwendungsinhalte mit den gleichen Berechtigungen erstellen, die auch bei den App-Autoren **UND** vorhanden sind. Außerdem sind auch für Folgendes zuständig:

* Konfigurieren von PhoneGap Build- und Adobe Mobile Services-Cloud-Services in AEM
* Staging, Veröffentlichen und Löschen von Anwendungen Content Sync OTA-Updates

>[!NOTE]
>
>Welche Benutzeraktionen in der AEM Apps-Befehlszentrale verfügbar sind, hängt von den jeweiligen Berechtigungen an.
>
>Sie werden feststellen, dass einige Optionen nicht für „app-authors“, jedoch für „app-admins“ zur Verfügung stehen.

#### Gruppenkonfiguration: app-admins {#group-configuration-app-admins}

1. Erstellen Sie eine neue Gruppe mit dem Namen „app-admins“:
1. Fügen Sie die folgenden Gruppen Ihrer neuen Gruppe „app-admins“ hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-20](assets/chlimage_1-20.png)

1. Navigieren Sie zur Konsole [Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloudservices hinzu.

   * (Lesen, Verändern, Erstellen, Löschen, Replizieren) für „/etc/cloudservices/mobileservices“
   * (Lesen, Verändern, Erstellen, Löschen, Replizieren) für „/etc/cloudservices/phonegap-build“

1. Fügen Sie in derselben Berechtigungskonsole Aktualisierungen für App-Inhalte hinzu, veröffentlichen und löschen Sie sie

   * (Lesen, Verändern, Erstellen, Löschen, Replizieren) für „/etc/packages/mobileapp“
   * (Lesen) für „/var/contentsync“

   >[!NOTE]
   >
   >Die Paketreplikation wird verwendet, um Anwendungsaktualisierungen aus der Erstellungsinstanz in der Veröffentlichungsinstanz zu veröffentlichen.

   >[!CAUTION]
   >
   >Der Zugriff auf „/var/contentsync“ ist standardmäßig nicht möglich.
   >
   >Das Übergehen der Leseberechtigung, kann dazu führen, dass leere Aktualisierungspakete erstellt und repliziert werden.

1. Fügen Sie dieser Gruppe je nach Bedarf Mitglieder hinzu.

## Berechtigungen für die Dashboard-Kacheln  {#dashboard-tile-permissions}

Die Dashboard-Kacheln können je nach Berechtigungen des Benutzers verschiedene Aktionen enthalten. Im Folgenden werden die Aktionen beschrieben, die für die einzelnen Kacheln verfügbar sind.

Die Verfügbarkeit von Aktionen ist außerdem abhängig von der Konfiguration der aktuellen App. Beispielsweise ergibt die Aktion „Remote-Build“ keinen Sinn, wenn der App keine PhoneGap-Cloud-Konfiguration zugewiesen wurde. Diese werden in den Abschnitten &quot;**Konfigurationsbedingung**&quot;aufgelistet.

### Kachel „App verwalten“{#manage-app-tile}

Die Kachel enthält zurzeit keine Aktionen, für die Berechtigungen erforderlich sind, die Detailseite der Anwendung weist jedoch folgende Aktionen auf:

* ** Editor für app-author und app-admin (UI-Trigger - jcr:write - unter /content/phonegap/{suffix})
* *Herunterladen* für app-author und app-admin (UI-Trigger - unter /content/phonegap/{suffix})

Die folgende Abbildung zeigt die Optionen zum Herunterladen und Bearbeiten einer App:

![chlimage_1-21](assets/chlimage_1-21.png)

