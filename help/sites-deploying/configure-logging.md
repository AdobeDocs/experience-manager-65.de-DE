---
title: Protokollierung
description: Erfahren Sie, wie Sie globale Parameter für den zentralen Protokollierungs-Service konfigurieren, bestimmte Einstellungen für einzelne Services festlegen oder eine Datenprotokollierung anfordern können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: b32001a1-0078-43f6-89d6-781d6d2e9c94
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 91%

---

# Protokollierung{#logging}

Mit AEM können Sie Folgendes konfigurieren:

* globale Parameter für den zentralen Protokollierungsdienst
* Anfragedatenprotokollierung; eine spezielle Protokollierungskonfiguration für Anfrageinformationen
* spezifische Einstellungen für die einzelnen Dienste, z. B. eine einzelne Protokolldatei und ein bestimmtes Format für die Protokollmeldungen

Hierbei handelt es sich jeweils um [OSGi-Konfigurationen](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Die Protokollierung in AEM basiert auf Sling-Prinzipien. Weitere Informationen finden Sie unter [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

## Globale Protokollierung {#global-logging}

Die Konfiguration [Apache Sling Logging Configuration](/help/sites-deploying/osgi-configuration-settings.md) dient zum Konfigurieren des Rootloggers. Dabei werden die globalen Einstellungen für die Protokollierung in AEM definiert:

* Protokollierungsebene
* Speicherort der zentralen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen

>[!NOTE]
>
>In diesem [Knowledgebase-Artikel](https://helpx.adobe.com/de/experience-manager/kb/HowToRotateRequestAndAccessLog.html) wird das Rotieren von request.log- und access.log-Dateien erläutert.

## Logger und Writer für einzelne Dienste {#loggers-and-writers-for-individual-services}

Neben den globalen Protokollierungseinstellungen können Sie in AEM bestimmte Einstellungen für einzelne Dienste konfigurieren:

* Bestimmte Protokollierungsstufe
* Speicherort der jeweiligen Protokolldatei
* Anzahl der aufzubewahrenden Versionen
* Versionsrotation; entweder maximale Größe oder Zeitintervall
* Format zum Schreiben der Protokollmeldungen
* Logger (OSGi-Dienst, der die Protokollmeldungen bereitstellt)

So können Sie die Protokollmeldungen für einen einzelnen Dienst in einer separaten Datei kanalisieren. Dies kann insbesondere beim Entwickeln oder Testen nützlich sein, etwa wenn Sie für einen bestimmten Dienst auf eine höhere Protokollierungsstufe angewiesen sind.

AEM geht wie folgt vor, um Protokollmeldungen in eine Datei zu schreiben:

1. Ein **OSGi-Dienst** (Logger) schreibt eine Protokollmeldung.
1. Ein **Logging Logger** (Protokollierungs-Logger) formatiert diese Meldung gemäß Ihren Angaben.
1. Ein **Logging Writer** (Protokollierungs-Writer) schreibt all diese Meldungen in die von Ihnen definierte physische Datei.

Diese Elemente sind über die folgenden Parameter mit den entsprechenden Elementen verknüpft:

* **Logger (Logging Logger)**

  Hiermit werden der Dienst bzw. die Dienste zum Generieren der Meldungen definiert.

* **Protokolldatei (Logging Logger)**

  Definieren Sie die physische Datei zum Speichern der Protokollmeldungen.

  Auf diese Weise werden Logging Logger und Logging Writer miteinander verknüpft. Der Wert muss für die herzustellende Verbindung mit den Parametern in der Logging-Writer-Konfiguration übereinstimmen.

* **Protokolldatei (Logging Writer)**

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

Diese können bei Bedarf angepasst werden, obwohl die Standardkonfiguration für die meisten Installationen geeignet ist.

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

1. Erstellen einer Instanz der Factory-Konfiguration [Apache Sling Logging Logger-Konfiguration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an.
   1. Geben Sie den Logger an.
   1. Konfigurieren Sie ggf. die anderen Parameter.

1. Erstellen einer Instanz der Factory-Konfiguration [Apache Sling Logging Writer-Konfiguration](/help/sites-deploying/osgi-configuration-settings.md).

   1. Geben Sie die Protokolldatei an – diese muss mit der Angabe für den Logger übereinstimmen.
   1. Konfigurieren Sie ggf. die anderen Parameter.

>[!NOTE]
>
>Unter bestimmten Bedingungen empfiehlt sich die Erstellung einer [benutzerdefinierten Protokolldatei](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).
