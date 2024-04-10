---
title: Konfigurieren des Administratorkennworts bei der Installation
description: Erfahren Sie, wie Sie das Administratorkennwort bei der Adobe Experience Manager-Installation ändern.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: b55ff9d5-8139-4ecf-ba09-5cf88207c5c4
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 6%

---

# Konfigurieren des Administratorkennworts bei der Installation{#configure-the-admin-password-on-installation}

## Übersicht {#overview}

Seit Version 6.3 kann das Administratorkennwort in Adobe Experience Manager (AEM) bei der Installation einer neuen Instanz über die Befehlszeile festgelegt werden.

Bei früheren Versionen von AEM mussten das Passwort für das Admin-Konto sowie das Passwort für verschiedene andere Konsolen nach der Installation geändert werden.

Mit dieser Funktion können Sie während der Installation einer AEM-Instanz ein neues Administratorkennwort für das Repository und die Servlet-Engine festlegen, sodass Sie es anschließend nicht mehr manuell tun müssen.

>[!CAUTION]
>
>Die Funktion deckt nicht die Felix-Konsole ab, für die das Kennwort manuell geändert werden muss. Weitere Informationen finden Sie in den entsprechenden [Abschnitt „Sicherheitscheckliste“](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Wie verwende ich es? {#how-do-i-use-it}

Diese Funktion wird automatisch Trigger, wenn Sie AEM über die Befehlszeile installieren möchten, anstatt auf die JAR-Datei in einem Dateisystem-Explorer zu doppelklicken.

Die allgemeine Syntax zum Ausführen einer AEM-Instanz über die Befehlszeile lautet:

```shell
java -jar aem6.3.jar
```

Nachdem Sie die Instanz über die Befehlszeile ausgeführt haben, wird Ihnen die Option angezeigt, das Administratorkennwort während des Installationsprozesses zu ändern:

![chlimage_1-116](assets/chlimage_1-116a.png)

>[!NOTE]
>
>Die Aufforderung zur Änderung des Administratorkennworts wird nur während der Installation einer neuen AEM-Instanz angezeigt.

## Verwenden des Flags -nointeractive {#using-the-nointeractive-flag}

Sie können das Kennwort auch in einer Eigenschaftendatei angeben. Dies geschieht mithilfe der `-nointeractive` -Markierung kombiniert mit der `-Dadmin.password.file` Systemeigenschaft.

Beispiel:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Das Kennwort in der `passwordfile.properties` Die Datei muss im folgenden Format vorliegen:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Wenn Sie einfach die `-nointeractive` Parameter ohne `-Dadmin.password.file` Systemeigenschaft verwendet AEM das standardmäßige Administratorkennwort, ohne Sie aufzufordern, es zu ändern, was im Wesentlichen dem Verhalten älterer Versionen entspricht. Dieser nicht interaktive Modus kann für automatisierte Installationen mithilfe der Befehlszeile in einem Installationsskript verwendet werden.
