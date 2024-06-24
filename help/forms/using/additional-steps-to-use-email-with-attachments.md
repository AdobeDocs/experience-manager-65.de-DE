---
title: Zusätzliche Schritte zum Abrufen von E-Mails mit Anhängen
description: Erfahren Sie, wie Sie den Fehler beheben können, wenn Sie keine E-Mail mit Anhängen für AEM Forms auf JEE-Plattformen abrufen können.
exl-id: 0d0713fb-d95a-4a95-91ef-9cdaea30e343
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 100%

---

# E-Mail mit Anhängen für AEM Forms kann auf JEE-Plattformen nicht abgerufen werden{#unable-to-get-email-with-attachments}

Das Problem betrifft die folgende Version:

* Experience Manager 6.5 Forms

## Problem {#issue}

Benutzenden sind nicht in der Lage, Vorgänge wie „PDF per E-Mail versenden“ oder „Anhänge einfügen“ mit der Konfiguration „Übermittlung“ durchzuführen.

## Lösung {#solution}

1. Laden Sie JAR als [java.mail-1.0.jar](/help/forms/using/java.mail-1.0.jar) herunter und entpacken Sie die heruntergeladene JAR-Datei, um die Manifestdatei zu erhalten.

1. Verwenden Sie die in Schritt 1 erhaltene Manifestdatei `java.mail-1.0.jar`, um eine benutzerdefinierte JAR-Datei mit einer Bezeichnung wie etwa `java.mail-1.5.jar` zu erstellen.

1. Öffnen Sie die Manifestdatei und ersetzen Sie alle Vorkommen von `1.5.0` durch `1.5.6` und `Bundle-Version: 1.0` durch `Bundle-Version:1.5`

1. Erstellen Sie eine benutzerdefinierte JAR-Datei (`java.mail-1.5.jar`) im Ordner `C:\Adobe\Adobe_Experience_Manager_Forms\java\jdk\bin` mit folgendem Befehl:
   `jar -cfm java.mail-1.5.jar manifest.mf`

   Im obigen Befehl ist *manifest.mf* der Name der Manifestdatei und *java.mail-1.5.jar* ist der Name der Datei, die nach der Ausführung des obigen Befehls erstellt wird.

1. Laden Sie [javax.mail-1.5.6.redhat-1.jar](https://mvnrepository.com/artifact/com.sun.mail/javax.mail/1.5.6.redhat-1) herunter.

1. Navigieren Sie zu `http://<server name>:<port>/lc/system/console/bundles` und löschen Sie das Bundle mit dem Namen `JavaMail API (com.sun.mail.javax.mail) version 1.6.2`.

1. Installieren Sie `java.mail-1.5.jar` aus Schritt 3. Dieser Schritt startet die Sling-Eigenschaften der JEE-Bereitstellung neu. Warten Sie, bis die installierten Bundles unter `http://<server name>:<port>/lc/system/console/bundles` den Status **Aktiv** anzeigen.

   >Falls der Status immer noch **InActive** ist, starten Sie **JBoss®** über die **Dienste-Konsole** neu.


1. Installieren Sie die Datei `javax.mail-1.5.6.redhat-1.jar`, die Sie in Schritt 5 heruntergeladen haben.

1. Stoppen Sie **JBoss®** über die **Services-Konsole** und fügen Sie die folgenden Eigenschaften an die Datei **Sling.properties** an:
   * `org.osgi.framework.system.packages.extra=javax.activation; version\=1.2.0`
   * `sling.bootdelegation.activation=javax.activation.*`

1. Starten Sie **JBoss®** neu.

>[!NOTE]
>
> Es wird empfohlen, den Tastaturbefehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.
