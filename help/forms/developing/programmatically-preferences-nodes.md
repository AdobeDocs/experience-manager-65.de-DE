---
title: Programmgesteuerte Verwaltung der PreferencesNodes
seo-title: Programmgesteuerte Verwaltung der PreferencesNodes
description: Verwenden Sie die Voreinstellungs-Manager-Dienst-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
seo-description: Verwenden Sie die Voreinstellungs-Manager-Dienst-API (Java), um die Voreinstellungsknoten programmgesteuert zu verwalten.
uuid: f0cb117a-a6cc-4ca5-8511-b3bc9f6738e9
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9d4dba7f-49d8-4112-bc8a-04dafc99a936
role: Developer
exl-id: 108eb249-879b-4e4f-b431-8118b8656e62
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Programmgesteuerte Verwaltung der Voreinstellungsknoten {#programmatically-managing-the-preferencesnodes}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

In diesem Thema wird beschrieben, wie Sie die Voreinstellungs-Manager-Dienst-API (Java) verwenden können, um die Voreinstellungsknoten programmgesteuert zu verwalten.

Sie können die Konfigurationseinstellungen über die Administrator-Benutzeroberfläche manuell ändern. Um die Optionen zu ändern, navigieren Sie zu `Home>Settings>User Management> Configuration>Manual Configuration`. Importieren Sie `config.xml`, nachdem Sie die Änderungen vorgenommen haben. Sie werden feststellen, dass alle Änderungen außer den Änderungen am Knoten `/Adobe/Adobe Experience Manager Forms/Config/UM persist` verloren gehen. Die Vorschau von User Management Import und Export unterstützt keine Änderung der Konfigurationseinstellungen für andere Komponenten. Jetzt können diese Änderungen mit `PreferencesManagerServiceClient` APIs vorgenommen werden.

**Zusammenfassung der** SchritteFühren Sie die folgenden Schritte aus, um die Voreinstellungsknoten programmgesteuert zu verwalten:

1. Projektdateien einschließen.
1. Erstellen eines PreferencesManagerService-Clients
1. Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines PreferencesManagerService-Clients**

Bevor Sie einen User Management PreferencesManagerService-Vorgang programmgesteuert ausführen können, müssen Sie einen PreferencesManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein PreferencesManagerServiceClient -Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie dann die Voreinstellungs-Manager-Vorgänge aufrufen. Mit dem Dienst-Client können Sie Berechtigungen lesen und festlegen.
