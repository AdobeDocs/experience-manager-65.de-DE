---
title: Protokollierung
seo-title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
seo-description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungsdienst konfigurieren, bestimmte Einstellungen für einzelne Dienste festlegen oder eine Datenprotokollierung anfordern können.
uuid: 8c9e3628-2f2c-445d-9706-5c7725b85fe2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 5aa69b10-2cd0-4d34-8104-8c3b88405926
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '689'
ht-degree: 93%

---


# Protokollierung{#logging}

Mit AEM können Sie Folgendes konfigurieren:

* Globale Parameter für den zentralen Protokollierungsdienst
* Anforderung einer Datenprotokollierung; eine spezielle Protokollierungskonfiguration zum Anfordern von Informationen
* Spezifische Einstellungen für die einzelnen Dienste; zum Beispiel eine einzelne Protokolldatei und ein bestimmtes Format für die Protokollmeldungen

Hierbei handelt es sich jeweils um [OSGi-Konfigurationen](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Die Protokollierung in AEM basiert auf Sling-Prinzipien. Weitere Informationen finden Sie unter [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

## Globale Protokollierung {#global-logging}

Die Konfiguration [Apache Sling Logging Configuration](/help/sites-deploying/osgi-configuration-settings.md) dient zum Konfigurieren des Root-Loggers. Dabei werden die globalen Einstellungen für die Protokollierung in AEM definiert:

* Protokollierungsstufe
* Speicherort der zentralen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen

>[!NOTE]
>
>In diesem [Knowledgebase-Artikel](https://helpx.adobe.com/experience-manager/kb/HowToRotateRequestAndAccessLog.html) wird das Rotieren von request.log- und access.log-Dateien erläutert.

## Logger und Writer für einzelne Dienste {#loggers-and-writers-for-individual-services}

Neben den globalen Protokollierungseinstellungen können Sie in AEM bestimmte Einstellungen für einzelne Dienste konfigurieren:

* Bestimmte Protokollierungsstufe
* Speicherort der jeweiligen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen
* Logger (OSGi-Dienst, der die Protokollmeldungen bereitstellt)

So können Sie die Protokollmeldungen für einen einzelnen Dienst in eine separate Datei leiten. Dies kann insbesondere beim Entwickeln oder Testen nützlich sein, etwa wenn Sie für einen bestimmten Dienst auf eine höhere Protokollierungsstufe angewiesen sind.

AEM geht wie folgt vor, um Protokollmeldungen in eine Datei zu schreiben:

1. Ein **OSGi-Dienst** (Logger) schreibt eine Protokollmeldung.
1. Ein **Logging Logger** (Protokollierungslogger) formatiert diese Meldung gemäß Ihren Angaben.
1. Ein **Logging Writer** (Protokollierungswriter) schreibt all diese Meldungen in die von Ihnen definierte physische Datei.

Diese Elemente sind über die folgenden Parameter mit den entsprechenden Elementen verknüpft:

* **Logger (Logging Logger)**

   Hiermit werden der Dienst bzw. die Dienste zum Generieren der Meldungen definiert.

* **Protokolldatei (Protokollprotokollierung)**

   Definieren Sie die physische Datei zum Speichern der Protokollmeldungen.

   Auf diese Weise werden Logging Logger und Logging Writer miteinander verknüpft. Der Wert muss für die herzustellende Verbindung mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen.

* **Protokolldatei (Protokollautor)**

   Definieren Sie die physische Datei, in die die Protokollmeldungen geschrieben werden.

   Der Wert muss mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen. Andernfalls erfolgt kein Abgleich. Liegt keine Übereinstimmung vor, wird ein impliziter Writer mit der Standardkonfiguration (tägliche Protokollrotation) erstellt.

### Standard-Logger und -Writer {#standard-loggers-and-writers}

Bestimmte Logger und Writer sind in einer standardmäßigen AEM-Installation bereits enthalten.

Das erste Paar ist ein Sonderfall, da sowohl `request.log`- als auch `access.log`-Dateien gesteuert werden:

* Der Logger:

   * Apache Sling Customizable Request Data Logger

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Schreibt Meldungen zum Anforderungsinhalt in die Datei `request.log`.

* Ist verknüpft mit:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Schreibt Meldungen in `request.log` oder `access.log`.

Eine Anpassung ist hier ggf. möglich, obwohl die Standardkonfiguration für die meisten Installationen geeignet ist.

Die anderen Paare folgen der Standardkonfiguration:

* Der Logger:

   * Apache Sling Logging Logger-Konfiguration

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Schreibt `Information`-Meldungen in `logs/error.log`.

* Ist mit dem folgenden Writer verknüpft:

   * Apache Sling Logging Write-Konfiguration

      (org.apache.sling.commons.log.LogManager.factory.writer)

* Der Logger:

   * Apache Sling Logging Logger-Konfiguration (org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schreibt `Warning`-Meldungen in `../logs/error.log` für den `org.apache.pdfbox`-Dienst.

* Ist nicht mit einem bestimmten Writer verknüpft, sodass ein impliziter Writer mit Standardkonfiguration (tägliche Protokollrotation) verwendet wird.

### Erstellen eigener Logger und Writer {#creating-your-own-loggers-and-writers}

Sie können ein eigenes Logger-/Writer-Paar definieren:

1. Erstellen Sie eine neue Instanz der Werkskonfiguration [Apache Sling Logging Logger Configuration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an.
   1. Geben Sie den Logger an.
   1. Konfigurieren Sie die anderen Parameter nach Bedarf.

1. Erstellen Sie eine neue Instanz der Werkskonfiguration [Apache Sling Logging Writer Configuration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an – diese muss mit der Angabe für den Logger übereinstimmen.
   1. Konfigurieren Sie die anderen Parameter nach Bedarf.

>[!NOTE]
>
>Unter bestimmten Bedingungen empfiehlt sich die Erstellung einer [benutzerdefinierten Protokolldatei](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).

