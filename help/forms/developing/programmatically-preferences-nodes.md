---
title: Programmgesteuertes Verwalten der PreferencesNodes
seo-title: Programmgesteuertes Verwalten der PreferencesNodes
description: Verwenden Sie die Voreinstellungen-Manager-Dienst-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
seo-description: Verwenden Sie die Voreinstellungen-Manager-Dienst-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Programmgesteuertes Verwalten der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

In diesem Thema wird beschrieben, wie Sie die Voreinstellungs-Nodes programmgesteuert mit der Voreinstellungen Manager Service API (Java) verwalten können.

Sie können die Konfigurationseinstellungen in der Benutzeroberfläche des Administrators manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Importieren Sie `config.xml`, nachdem Sie die Änderungen vorgenommen haben, werden Sie feststellen, dass alle Änderungen mit Ausnahme der an Knoten `/Adobe/Adobe Experience Manager Forms/Config/UM persist` vorgenommenen Änderungen verloren gehen. Die Vorschau von User Management Import und Export unterstützt keine Änderung der Konfigurationseinstellungen für andere Komponenten. Nun können diese Änderungen mit `PreferencesManagerServiceClient`-APIs vorgenommen werden.

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
