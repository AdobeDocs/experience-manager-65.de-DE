---
title: Versionshinweise zu AEM Communities
description: Spezifische Versionshinweise zu Adobe Experience Manager 6.5. Communities
uuid: 1b436959-581c-4b34-b2df-cccc5727da59
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: c3505807-1550-491a-8619-e87839afca4f
docset: aem65
translation-type: tm+mt
source-git-commit: 57bad4e74b2dfd9e389643bfe58ef25564c5c545

---


# AEM Communities Versionshinweise{#aem-communities-release-notes}

Im Folgenden werden die an AEM Communities seit Version 6.4 durchgeführten Verbesserungen beschrieben. Ausführlichere Informationen zu den neuen Funktionen finden Sie im [AEM 6.5 Communities-Benutzerhandbuch](https://helpx.adobe.com/experience-manager/6-4/communities/user-guide.html).

Informationen dazu, wie Sie die neueste Version erhalten, finden Sie in der Dokumentation unter dem Abschnitt zur [Bereitstellung von Communities](https://helpx.adobe.com/in/experience-manager/6-4/help/communities/deploy-communities.html#LatestReleases).

## Wichtige Verbesserungen {#major-enhancements}

### Verbesserte Community-Aktivierung {#enhancements-to-community-engagement}

**@Erwähnungen unterstützen** AEM Communities ermöglicht es registrierten Benutzern nun, andere registrierte Mitglieder zu taggen (zu erwähnen), um ihre Aufmerksamkeit zu erhalten, in &quot;Benutzergenerierte Inhalte&quot;. Die getaggten (erwähnten) Mitglieder werden dann benachrichtigt, und zwar mit einem Deep-Link zu den entsprechenden anwendergenerierten Inhalten. Die Anwender können allerdings Web- und E-Mail-Benachrichtigungen deaktivieren/aktivieren.

![@Mentions-Unterstützung](assets/at-mentions.png)

Community-Anwender müssen nicht nach ihrem Vornamen, Nachnamen oder Anwendernamen suchen, um festzustellen, ob sich jemand an sie gewendet hat oder ein anderer ihre Hilfe braucht. Außerdem können UGC-Autoren Antwort von bestimmten registrierten Anwendern anfordern, die am besten dazu geeignet sind, ein Problem zu lösen und Feedback zu geben.

Die Community-Administratoren müssen **Erwähnung aktivieren **auf Community-Komponenten aktivieren, damit registrierte Benutzer die Funktionalität auf diesen Komponenten verwenden können.

**Gruppennachrichten**

Registrierte Community-Mitglieder können nun eine einzige E-Mail verfassen und diese direkt per Massenversand an Gruppen senden, anstatt dieselbe Nachricht einzeln an die jeweiligen Gruppenmitglieder verschicken zu müssen. To allow [group messaging](/help/communities/configure-messaging.md), enable both the instances of [Messaging Operations Service](/help/communities/messaging.md#group-messaging).

![Gruppennachricht](assets/group-messaging.png)

### Verbesserte Massenmoderation {#enhancements-to-bulk-moderation}

Benutzerdefinierte Filter in der Massenmoderation

[Benutzerdefinierte Filter](/help/communities/moderation.md#custom-filters) können jetzt entwickelt und der Benutzeroberfläche für die Massenmoderation hinzugefügt werden.

Ein in [Github](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) vorhandenes [Beispielprojekt](https://github.com/Adobe-Marketing-Cloud/aem-communities-extensions/tree/master/aem-communities-moderation-filter) zeigt das Filtern nach Tags. Dieses Projekt kann als Grundlage zum Entwickeln analoger benutzerdefinierter Filter verwendet werden.

![Benutzerdefinierte Filter](assets/custom-tag-filter.png)

**Listenansicht bei Massenmoderation**

Eine neue Listenansicht mit verbesserter UI wurde im Bereich für Massenmoderation bereitgestellt, um Einträge zu anwendergenerierten Inhalten anzuzeigen.

![Massenmoderation in der Listenansicht](assets/list-view-moderation.png)

### Verbesserte Site- und Gruppenverwaltung {#enhancements-to-site-and-group-management}

**Autorseitige Site- und Gruppenadministratoren**

Communities ermöglicht ab AEM 6.5 das dezentrale Verwalten (und Managen) verschiedener Community-Sites und Gruppen/verschachtelter Gruppen. Organisationen, die mehrere Community-Sites und verschachtelte Gruppen hosten, können nun beim Erstellen der Site (Gruppe) autorseitig Mitglieder für Administratorrollen auswählen.

![Site-Administrator](assets/site-admin.png)

Site-Administratoren können eine Gruppe auf jeder Hierarchieebene erstellen und zu Standardadministratoren werden. Diese Administratoren können später von anderen Gruppenadministratoren entfernt werden. Gruppenadministratoren können ihre Gruppe G1 verwalten und eine unter G1 verschachtelte Untergruppe erstellen.

### Verbesserte Aktivierung {#enhancements-to-enablement}

**SCORM 2017.1-Unterstützung**

The enablement functionality of AEM 6.5 Communities support Shareable Content Object Reference Model [(SCORM) 2017.1](https://rusticisoftware.com/blog/scorm-engine-2017-released/) engine.

**Unterstützung der Tastaturnavigation für Aktivierungskomponenten**Komponenten für die Aktivierung (z. B. Kataloge und Kurswiedergabe, Zuweisungen, Dateibibliothek) in AEM Communities unterstützen die Tastaturnavigation für eine verbesserte Zugänglichkeit.

### Weitere Verbesserungen {#other-enhancements}

* **Unterstützung für Solr 7**AEM 6.5 Communities unterstützt Apache Solr 7.0 Version der Suchplattform beim Einrichten von MSRP und DSRP.
