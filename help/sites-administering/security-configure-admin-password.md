---
title: Konfigurieren des Administratorkennworts bei der Installation
description: Erfahren Sie, wie Sie das Administratorkennwort bei der Adobe Experience Manager-Installation ändern.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: b55ff9d5-8139-4ecf-ba09-5cf88207c5c4
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 5%

---

# Konfigurieren des Administratorkennworts bei der Installation{#configure-the-admin-password-on-installation}

## Übersicht {#overview}

Seit Version 6.3 ermöglicht Adobe Experience Manager (AEM) das Festlegen des Administratorkennworts über die Befehlszeile bei der Installation einer neuen Instanz.

Bei früheren Versionen von AEM musste das Kennwort für das Administratorkonto zusammen mit dem Kennwort für verschiedene andere Konsolen nach der Installation geändert werden.

Diese Funktion bietet die Möglichkeit, während der Installation einer AEM-Instanz ein neues Administratorkennwort für das Repository und die Servlet-Engine festzulegen, sodass die manuelle Ausführung später entfällt.

>[!CAUTION]
>
>Die Felix-Konsole, für die das Kennwort manuell geändert werden muss, wird von der Funktion nicht erfasst. Weitere Informationen finden Sie in der entsprechenden [Abschnitt &quot;Sicherheitscheckliste&quot;](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Wie benutze ich es? {#how-do-i-use-it}

Diese Funktion wird automatisch Trigger, wenn Sie AEM über die Befehlszeile installieren möchten, anstatt auf die JAR-Datei in einem Dateisystem-Explorer zu doppelklicken.

Die allgemeine Syntax für die Ausführung einer AEM-Instanz über die Befehlszeile lautet:

```shell
java -jar aem6.3.jar
```

Nachdem Sie die Instanz über die Befehlszeile ausgeführt haben, erhalten Sie die Möglichkeit, das Administratorkennwort während des Installationsprozesses zu ändern:

![chlimage_1-116](assets/chlimage_1-116a.png)

>[!NOTE]
>
>Die Aufforderung zur Änderung des Administratorkennworts wird nur während der Installation einer neuen AEM angezeigt.

## Verwenden des Flag -nointeractive {#using-the-nointeractive-flag}

Sie können das Kennwort auch in einer Eigenschaftendatei angeben. Dies geschieht mithilfe der `-nointeractive` Markierung kombiniert mit `-Dadmin.password.file` Systemeigenschaft.

Beispiel:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Das Kennwort in der `passwordfile.properties` -Datei muss das folgende Format aufweisen:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Wenn Sie einfach die `-nointeractive` -Parameter ohne die `-Dadmin.password.file` -Systemeigenschaft verwenden AEM das standardmäßige Administratorkennwort, ohne Sie dazu aufzufordern, es zu ändern. Dies entspricht im Wesentlichen dem Verhalten früherer Versionen. Dieser nicht interaktive Modus kann für automatisierte Installationen mit der Befehlszeile in einem Installationsskript verwendet werden.
