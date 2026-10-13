---
title: Starten und Anhalten von Diensten
description: Erfahren Sie, wie Sie die Dienste starten und stoppen, die mit AEM Forms-Modulen und dem Anwendungsserver und der Datenbank verknüpft sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 55bf5196-22c6-4286-8c92-ff44d81dde49
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 100%
---
# Starten und Anhalten von Diensten {#starting-and-stopping-services}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Es gibt zwei Arten von Diensten, die Teil von AEM Formularen sind:

* Dienste, die den AEM Forms-Anwendungs-Server und die Datenbank steuern.
* Services, die AEM Forms-Module steuern

## Starten oder Stoppen von Diensten, denen AEM Forms-Module zugeordnet sind {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM Forms-Module (z. B. Forms, Rights Management, Output) arbeiten als Dienste. Manchmal müssen die Dienste für diese AEM Forms-Module gestoppt und neu gestartet werden. Beispielsweise müssen Sie einen AEM Forms-Dienst stoppen und wieder neu starten, nachdem Sie Einstellungen des Dienstes geändert haben.

>[!NOTE]
>
> Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

1. Klicken Sie in der Administration-Console auf **Services** > **Programme und Services** > **Service-Verwaltung**.
1. Wählen Sie auf der Seite „Dienstverwaltung“ das Kontrollkästchen neben dem zu stoppenden oder startenden Dienst aus und klicken Sie auf „Beenden“ bzw. „Starten“.

## Starten und Stoppen von Diensten für den Anwendungs-Server und die Datenbank {#start-or-stop-services-for-the-application-server-and-database}

Eine vollständige Implementierung von AEM Forms umfasst einen Anwendungs-Server und Datenbankdienste:

* *`[application server]`* für AEM Forms
* *`[database]`* für AEM Forms

Unter Windows sind diese Services über **Verwaltung** > **Dienste** zugänglich. Wenn Sie z. B. AEM Forms unter JBoss mit der Turnkey-Methode installiert haben, stehen auf Ihrem System die folgenden Dienste zur Verfügung:

* JBoss für Adobe Experience Manager Forms
* MySQL für Adobe Experience Manager Forms

Sie können diese Dienste starten bzw. stoppen, indem Sie sie in der Liste im Bereich „Dienste“ auswählen und anschließend auf die entsprechende Aktionsschaltfläche klicken.

Unter UNIX® oder Linux geben Sie folgenden Text an einer Befehlszeile ein, wobei *`[service name]`* der Name des zu überprüfenden Services ist:

```java
     ps -A | grep [service name]
```
