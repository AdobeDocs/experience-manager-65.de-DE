---
title: Programmgesteuertes Verwalten der PreferencesNodes
seo-title: Programmgesteuertes Verwalten der PreferencesNodes
description: 'null'
seo-description: 'null'
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Programmgesteuertes Verwalten der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

In diesem Thema wird beschrieben, wie Sie die Voreinstellungs-Nodes programmgesteuert mit der Voreinstellungen Manager Service API (Java) verwalten können.

Sie können die Konfigurationseinstellungen in der Benutzeroberfläche des Administrators manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Importieren Sie `config.xml` nach den Änderungen, Sie werden feststellen, dass alle Änderungen mit Ausnahme der am Knoten vorgenommenen Änderungen verloren gehen `/Adobe/Adobe Experience Manager Forms/Config/UM persist` . Die Vorschau von User Management Import und Export unterstützt keine Änderung der Konfigurationseinstellungen für andere Komponenten. Nun können diese Änderungen mithilfe von `PreferencesManagerServiceClient` APIs vorgenommen werden.

**Zusammenfassung der** SchritteSo verwalten Sie die Voreinstellungsknoten programmgesteuert:

1. Schließen Sie Projektdateien ein.
1. Erstellen eines PreferencesManagerService-Clients
1. Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines PreferencesManagerService-Clients**

Bevor Sie einen User Management PreferencesManagerService-Vorgang programmgesteuert durchführen können, müssen Sie einen PreferencesManagerService-Client erstellen. Mit der Java-API wird dies durch Erstellen eines PreferencesManagerServiceClient-Objekts erreicht.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Dienstclient erstellt haben, können Sie die Vorgänge im Voreinstellungen-Manager aufrufen. Der Dienstclient ermöglicht Ihnen das Lesen und Festlegen von Berechtigungen.
