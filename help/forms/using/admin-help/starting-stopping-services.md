---
title: Dienste starten und beenden
seo-title: Dienste starten und beenden
description: Erfahren Sie, wie Sie die Dienste starten und stoppen, die mit AEM-Forms-Modulen und dem Anwendungsserver und der Datenbank verknüpft sind.
seo-description: Erfahren Sie, wie Sie die Dienste starten und stoppen, die mit AEM-Forms-Modulen und dem Anwendungsserver und der Datenbank verknüpft sind.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Dienste starten und beenden {#starting-and-stopping-services}

Es gibt zwei Arten von Diensten, die Bestandteil von AEM Forms sind:

* Dienste zum Steuern von AEM Forms-Anwendungsserver und -Datenbank.
* Dienste, die AEM Forms-Module steuern

## Dienste starten oder beenden, denen AEM Forms-Module zugeordnet sind {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM Forms-Module (z. B. Forms, Rights Management, Output) arbeiten als Dienste. Manchmal müssen die Dienste für diese AEM Forms-Module beendet und neu gestartet werden. Beispielsweise müssen Sie einen AEM Forms-Dienst beenden und wieder neu starten, nachdem Sie Einstellungen des Dienstes geändert haben.

1. In administration console click **Services** > **Applications and Services** > **Service Management**.
1. Aktivieren Sie auf der Seite „Dienstverwaltung“ das Kontrollkästchen neben dem zu beendenden oder startenden Dienst und klicken Sie auf „Beenden“ bzw. „Starten“.

## Dienste für den Anwendungsserver und die Datenbank starten und beenden {#start-or-stop-services-for-the-application-server-and-database}

Eine vollständige Implementierung von AEM Forms umfasst einen Anwendungsserver und Datenbankdienste:

* *`[application server]`* für AEM Forms
* *`[database]`* für AEM Forms

On Windows, these services are accessible through the **Administrative Tools** > **Services panel**. Wenn Sie z. B. AEM Forms unter JBoss mit der Turnkey-Methode installiert haben, stehen auf Ihrem System die folgenden Dienste zur Verfügung:

* JBoss für Adobe Experience Manager Forms
* MySQL für Adobe Experience Manager Forms

Sie können Sie diese Dienste starten bzw. beenden, indem Sie sie in der Liste im Bereich „Dienste“ auswählen und anschließend auf die entsprechende Aktionsschaltfläche klicken.

On UNIX® or Linux, enter the following text from a command line, where *`[service name]`* is the name of the service you are verifying:

```as3
     ps -A | grep [service name]
```

