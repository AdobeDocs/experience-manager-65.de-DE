---
title: Starten und Anhalten von Diensten
description: Erfahren Sie, wie Sie die Dienste starten und stoppen, die mit AEM Forms-Modulen und dem Anwendungsserver und der Datenbank verknüpft sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 55bf5196-22c6-4286-8c92-ff44d81dde49
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 28%

---

# Starten und Anhalten von Diensten {#starting-and-stopping-services}

Es gibt zwei Arten von Diensten, die Teil AEM Formularen sind:

* Dienste, die den AEM forms-Anwendungsserver und die Datenbank steuern.
* Dienste, die AEM Formularmodule steuern

## Dienste starten oder beenden, die mit AEM Formularmodulen verknüpft sind {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM Formularmodule (z. B. Forms, Rights Management, Output) fungieren als Dienste. Manchmal müssen Sie die Dienste für diese AEM Formularmodule anhalten oder starten. Beispielsweise müssen Sie einen AEM Forms-Dienst beenden und neu starten, nachdem Sie eine Einstellung für den Dienst geändert haben.

1. Klicken Sie in der Administration-Console auf **Services** > **Programme und Services** > **Service-Verwaltung**.
1. Aktivieren Sie auf der Seite &quot;Dienstverwaltung&quot;das Kontrollkästchen neben dem Dienst, der angehalten oder gestartet werden soll, und klicken Sie auf &quot;Beenden&quot;oder &quot;Starten&quot;.

## Dienste für den Anwendungsserver und die Datenbank starten oder beenden {#start-or-stop-services-for-the-application-server-and-database}

Eine vollständige Implementierung AEM Formulars umfasst einen Anwendungsserver und Datenbankdienste:

* *`[application server]`* für AEM Forms
* *`[database]`* für AEM Forms

Unter Windows sind diese Services über **Verwaltung** > **Dienste** zugänglich. Wenn Sie beispielsweise AEM Formulare mithilfe der Turnkey-Methode auf JBoss installiert haben, sind die folgenden Dienste auf Ihrem System verfügbar:

* JBoss für Adobe Experience Manager forms
* MySQL für Adobe Experience Manager forms

Starten oder stoppen Sie diese Dienste, indem Sie sie in der Liste im Bedienfeld Dienste auswählen und dann auf die entsprechende Aktionsschaltfläche im Bedienfeld klicken.

Unter UNIX® oder Linux geben Sie folgenden Text an einer Befehlszeile ein, wobei *`[service name]`* der Name des zu überprüfenden Services ist:

```java
     ps -A | grep [service name]
```
