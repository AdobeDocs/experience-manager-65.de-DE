---
title: Konfigurieren des Administratorkennworts bei der Installation
seo-title: Configure the Admin Password on Installation
description: Hier erfahren Sie, wie Sie das Administratorkennwort bei der AEM-Installation ändern.
seo-description: Learn how to change the Admin Password on AEM Installation.
uuid: 06da9890-ed63-4fb6-88d5-fd0e16bc4ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 00806e6e-3578-4caa-bafa-064f200a871f
exl-id: b55ff9d5-8139-4ecf-ba09-5cf88207c5c4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '305'
ht-degree: 100%

---

# Konfigurieren des Administratorkennworts bei der Installation{#configure-the-admin-password-on-installation}

## Übersicht {#overview}

Ab Version 6.3 kann bei der Installation einer neuen AEM-Instanz das Administratorkennwort über die Befehlszeile festgelegt werden.

In älteren Versionen von AEM musste das Kennwort für das Administratorkonto zusammen mit dem Kennwort für diverse andere Konsolen nach der Installation geändert werden.

Dieses Feature ermöglicht es, ein neues Administratorkennwort für das Repository und das Servlet-Modul während der Installation einer AEM-Instanz hinzuzufügen, sodass dieser Schritt nicht mehr manuell im Nachhinein ausgeführt werden muss.

>[!CAUTION]
>
>Beachten Sie, dass die Felix-Konsole von diesem Feature ausgenommen ist und das Kennwort für diese Konsole manuell geändert werden muss. Weitere Informationen finden Sie im entsprechenden [Abschnitt der Sicherheits-Checkliste](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Verwendung {#how-do-i-use-it}

Dieses Feature wird automatisch ausgelöst, wenn Sie AEM über die Befehlszeile installieren (anstatt in einem Dateisystem-Explorer auf die JAR-Datei doppelzuklicken).

Allgemeine Syntax zum Ausführen einer AEM-Instanz über die Befehlszeile:

```shell
java -jar aem6.3.jar
```

Wenn Sie die Instanz über die Befehlszeile ausführen, haben Sie während des Installationsprozesses die Möglichkeit, das Administratorkennwort zu ändern:

![chlimage_1-116](assets/chlimage_1-116a.png)

>[!NOTE]
>
>Die Aufforderung zum Ändern des Administratorkennworts wird nur während der Installation einer neuen AEM-Instanz angezeigt.

## Verwenden des Flags „-nointeractive“ {#using-the-nointeractive-flag}

Das Kennwort kann auch über eine Eigenschaftendatei angegeben werden. Dies geschieht mithilfe der `-nointeractive`-Markierung kombiniert mit der Systemeigenschaft `-Dadmin.password.file`.

Beispiel:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Das Kennwort in der Datei `passwordfile.properties` muss im folgenden Format angegeben werden:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Wenn Sie den Parameter `-nointeractive`- ohne die Systemeigenschaft `-Dadmin.password.file` verwenden, verwendet AEM das standardmäßige Administratorkennwort und fordert Sie nicht zur Änderung des Kennworts auf, was im Wesentlichen dem Verhalten älterer Versionen entspricht. Dieser nicht interaktive Modus kann für automatische Installationen unter Verwendung der Befehlszeile in einem Installationsskript verwendet werden.
