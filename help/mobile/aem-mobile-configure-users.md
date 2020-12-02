---
title: Konfigurieren von Benutzern und Benutzergruppen
seo-title: Konfigurieren von Benutzern und Benutzergruppen
description: Folgen Sie dieser Seite, um die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen On-Demand-Dienste-App zu verstehen.
seo-description: Folgen Sie dieser Seite, um die Benutzerrollen und die Konfiguration Ihrer Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen On-Demand-Dienste-App zu verstehen.
uuid: 461e1725-41dd-4883-92b9-a7e175660401
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: administering-on-demand-services-app
discoiquuid: c3c73e67-7f85-4308-b4cd-1b42d4f3f2d9
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 51%

---


# Konfigurieren von Benutzern und Benutzergruppen {#configure-your-users-and-user-groups}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein frameworkbasiertes clientseitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

In diesem Kapitel werden die Benutzerrollen und die Konfiguration der Benutzer und Gruppen zur Unterstützung des Authoring und der Verwaltung Ihrer mobilen Apps beschrieben.

## AEM Mobile-Anwendungsbenutzer und Gruppenverwaltung {#aem-mobile-application-users-and-group-administration}

### AEM Mobile Application Content Authors (App-Autorengruppe) {#aem-mobile-application-content-authors-app-author-group}

Mitglieder der Gruppe &quot;App-Autor&quot;sind für das Authoring AEM Inhalte mobiler Anwendungen zuständig, einschließlich Seiten, Text, Bilder und Videos.

#### Gruppenkonfiguration: app-authors {#group-configuration-app-authors}

1. Erstellen Sie eine neue Benutzergruppe mit dem Namen „app-authors“:

   Navigieren Sie zur Admin Console &quot;Benutzer&quot;: [http://localhost:4502/libs/granite/security/content/groupadmin.html](http://localhost:4502/libs/granite/security/content/groupadmin.html)

   Wählen Sie in der Benutzergruppenkonsole das Plussymbol, um die Gruppe zu erstellen.

   Legen Sie die ID dieser Gruppe auf „app-authors“ fest, um anzugeben, dass diese Autorenbenutzergruppe spezifisch für mobile Anwendungen in AEM ist.

1. Hinzufügen von Mitgliedern zur Gruppe: Autoren

   ![chlimage_1-167](assets/chlimage_1-167.png)

1. Nachdem Sie die Benutzergruppe „app-authors“ erstellt haben, können Sie ihr über die [Benutzer-Admin](http://localhost:4502/libs/granite/security/content/useradmin.md)-Konsole Teammitglieder hinzufügen.

   ![chlimage_1-168](assets/chlimage_1-168.png)

1. Im Folgenden können Sie AEM Inhaltsautorengruppe hinzufügen:

   (Lesen) am

   * /App
   * /etc/clientlibs
   * /etc/designs
   * /etc/cloudservices/dps2015

### AEM Mobile Application Administrators Group (app-admins group) {#aem-mobile-application-administrators-group-app-admins-group}

Mitglieder der Gruppe &quot;app-admins&quot; können Anwendungsinhalte mit den gleichen Berechtigungen erstellen, die auch bei den App-Autoren **UND** vorhanden sind. Außerdem sind auch für Folgendes zuständig:

* Staffeln, Veröffentlichen und Löschen von OTA-Anwendungsaktualisierungen über die Inhaltssynchronisierung

>[!NOTE]
>
>Welche Benutzeraktionen in der AEM Apps-Befehlszentrale verfügbar sind, hängt von den jeweiligen Berechtigungen an.
>
>Sie werden feststellen, dass einige Optionen nicht für „app-authors“, jedoch für „app-admins“ zur Verfügung stehen.

### Gruppenkonfiguration: app-admins {#group-configuration-app-admins}

1. Erstellen Sie eine neue Gruppe mit dem Namen „app-admins“:
1. Fügen Sie die folgenden Gruppen Ihrer neuen Gruppe „app-admins“ hinzu:

   * content-authors
   * workflow-users

   ![chlimage_1-169](assets/chlimage_1-169.png)

   >[!NOTE]
   >
   >Nur Mitglieder der Gruppe „workflow-users“ können die Aktion „Remote-Build“ für den PhoneGap Build-Dienst ausführen.

1. Navigieren Sie zur Konsole [Berechtigungen](http://localhost:4502/useradmin) und fügen Sie Berechtigungen zum Verwalten von Cloudservices hinzu.

   * (Lesen, Verändern, Erstellen, Löschen, Replizieren) für „/etc/cloudservices/mobileservices“

1. Fügen Sie ebenfalls in der Berechtigungskonsole Berechtigungen zum Staffeln, Veröffentlichen und Löschen von Anwendungsinhaltsaktualisierungen hinzu:

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
1. So exportieren Sie Inhalte oder laden

   * (Lesen) unter /etc/contentsync, um auf Exportvorlagen zuzugreifen
   * (Gelesen) unter /var zu für Pfad-Traversal bei Lesevorgängen
   * (Lesen, Schreiben, Ändern, Löschen) unter /var/contentsync zum Schreiben, Lesen und Bereinigen von ContentSynchronisieren von zwischengespeicherten Exportinhalten

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu den beiden anderen Rollen und Verantwortlichkeiten beim Erstellen einer AEM Mobile On-demand Services-App finden Sie in den folgenden Ressourcen:

* [Entwickeln von AEM für AEM Mobile On-demand Services](/help/mobile/aem-mobile-on-demand.md)
* [Authoring AEM Inhalte für AEM Mobile On-demand Services-Apps](/help/mobile/mobile-apps-ondemand.md)
