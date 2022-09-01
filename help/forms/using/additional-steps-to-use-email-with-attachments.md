---
title: 'Zusätzliche Schritte zum Abrufen der E-Mail mit Anhang '
description: 'Zusätzliche Schritte zum Abrufen der E-Mail mit Anhang   '
source-git-commit: 9ee8e79777b89fbf4d6e5b5fd1dbb1ef3bc9ad5d
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# E-Mail mit Anhängen für AEM Forms on JEE-Plattformen kann nicht abgerufen werden{#unable-to-get-email-with-attachments}

Das Problem tritt bei der folgenden Version auf:
* Experience Manager 6.5 Forms

## Problem {#issue}

Der Benutzer kann keine Vorgänge wie PDF per E-Mail senden oder Anhänge mit Sendekonfiguration einschließen.

## Lösung {#solution}

1. JAR als herunterladen [java.mail-1.0.jar](/help/forms/using/java.mail-1.0.jar) und entpacken Sie die heruntergeladene JAR-Datei, um die Manifestdatei zu erhalten.

1. Verwenden Sie die Manifestdatei von `java.mail-1.0.jar` Wird aus Schritt 1 abgerufen, um eine neue benutzerdefinierte JAR-Datei zu erstellen, z. B. `java.mail-1.5.jar`.

1. Öffnen Sie die Manifestdatei und ersetzen Sie alle Vorkommen von `1.5.0` mit `1.5.6` und `Bundle-Version: 1.0` mit `Bundle-Version:1.5`

1. Erstellen Sie eine neue benutzerdefinierte JAR (`java.mail-1.5.jar`) mithilfe des folgenden Befehls in `C:\Adobe\Adobe_Experience_Manager_Forms\java\jdk\bin` Ordner als:
   `jar -cfm java.mail-1.5.jar manifest.mf`

   Im obigen Befehl *manifest.mf* ist der Name der Manifestdatei und *java.mail-1.5.jar* ist der Name der Datei, die nach der Ausführung des obigen Befehls erstellt wird.

1. Download [javax.mail-1.5.6.redhat-1.jar](https://mvnrepository.com/artifact/com.sun.mail/javax.mail/1.5.6.redhat-1).

1. Navigieren Sie zu `http://<server name>:<port>/lc/system/console/bundles`und löschen Sie das Bundle mit einem Namen als `JavaMail API (com.sun.mail.javax.mail) version 1.6.2`.

1. Installieren `java.mail-1.5.jar` gewonnen aus Schritt 3.  In diesem Schritt werden die Sling-Eigenschaften der JEE-Bereitstellung neu gestartet. Warten Sie auf die installierten Bundles unter `http://<server name>:<port>/lc/system/console/bundles` Status anzeigen als **Aktiv**.

   >Hinweis: Wenn der Status weiterhin **InActive**, Neustart   **JBoss** von **Dienstkonsole**.


1. Installieren `javax.mail-1.5.6.redhat-1.jar`-Datei heruntergeladen haben, die mit Schritt 5 heruntergeladen wurde.

1. Anhalten **JBoss** von **Dienstkonsole** und hängen Sie die folgenden Eigenschaften an **Sling.properties** Datei:
   * `org.osgi.framework.system.packages.extra=javax.activation; version\=1.2.0`
   * `sling.bootdelegation.activation=javax.activation.*`

1. Neu starten **JBoss**.