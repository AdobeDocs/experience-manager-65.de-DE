---
title: Start und Stopp über die Befehlszeile
description: Erfahren Sie, wie Sie Adobe Experience Manager über die Befehlszeile starten und stoppen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 21041b55-240c-487d-9d79-c54c877f4e1e
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 39%

---

# Start und Stopp über die Befehlszeile{#command-line-start-and-stop}

## Starten von Adobe Experience Manager über die Befehlszeile {#starting-adobe-experience-manager-from-the-command-line}

Das Skript `start` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Es werden sowohl UNIX®- als auch Windows-Versionen bereitgestellt. Das Skript startet die in installierte Instanz *&lt;cq-installation>* Verzeichnis.

Diese beiden Versionen unterstützen eine Liste von Umgebungsvariablen, die zum Starten und Optimieren der Adobe Experience Manager (AEM)-Instanz verwendet werden können.

<table>
 <tbody>
  <tr>
   <td><strong>Umgebungsvariable </strong></td>
   <td><strong>Beschreibung </strong></td>
  </tr>
  <tr>
   <td>CQ_PORT</td>
   <td>Für „stop“- und „status“-Skripts verwendeter TCP-Port<br /> </td>
  </tr>
  <tr>
   <td>CQ_HOST</td>
   <td>Hostname<br /> </td>
  </tr>
  <tr>
   <td>CQ_INTERFACE</td>
   <td>Schnittstelle, an der dieser Server lauschen sollte<br /> </td>
  </tr>
  <tr>
   <td>CQ_RUNMODE</td>
   <td>Durch Kommas getrennte Ausführungsmodi<br /> </td>
  </tr>
  <tr>
   <td>CQ_JARFILE</td>
   <td>Name der JAR-Datei<br /> </td>
  </tr>
  <tr>
   <td>CQ_USE_JAAS</td>
   <td>Verwendung von JAAS (wenn „true“ vorliegt)<br /> </td>
  </tr>
  <tr>
   <td>CQ_JAAS_CONFIG</td>
   <td>Pfad der JAAS-Konfiguration<br /> </td>
  </tr>
  <tr>
   <td>CQ_JVM_OPTS</td>
   <td>JVM-Standardoptionen<br /> </td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>Einige Ausführungsmodi, darunter Autor und Veröffentlichung, müssen vor dem ersten Starten von AEM festgelegt werden und können danach nicht mehr geändert werden. Bevor Sie eine AEM-Instanz einrichten, die in der Produktion verwendet wird, lesen Sie Folgendes [Dokumentation zu Ausführungsmodi](/help/sites-deploying/configure-runmodes.md) für Details.

### Beispiel für ein Windows-Plattformstart.bat-Skript {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Beispiel für ein UNIX®-Startskript {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Über das Skript „start“ wird der im Ordner *the &lt;cq-installation>/app* installierte AEM-Schnellstart gestartet.

## Adobe Experience Manager stoppen {#stopping-adobe-experience-manager}

Führen Sie einen der folgenden Schritte aus, um AEM zu stoppen:

* Je nach verwendeter Plattform:

   * Drücken Sie **Strg + C**, um den Server herunterzufahren, wenn Sie AEM über ein Skript oder die Befehlszeile gestartet haben.
   * Wenn Sie das Startskript unter UNIX® verwendet haben, müssen Sie das Stopp-Skript verwenden, um AEM zu stoppen.

* Wenn Sie AEM durch Doppelklicken auf die JAR-Datei gestartet haben, klicken Sie auf die Schaltfläche **am** auf dem Startfenster (die Schaltfläche ändert sich dann in **AUS**), um den Server herunterzufahren.

  ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager über die Befehlszeile anhalten {#stopping-adobe-experience-manager-from-the-command-line}

Das Skript `stop` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Es werden sowohl UNIX®- als auch Windows-Versionen bereitgestellt. Das Skript hält die im Verzeichnis *&lt;cq-installation>* installierte aktive Instanz an.

### Beispiel für ein UNIX®-Plattformstoppskript {#unix-platform-stop-script-example}

```shell
./stop
```

### Windows-Plattform, Skriptbeispiel für stop.bat {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Wenn Sie nur das Repository vorkonfigurieren möchten (ohne es zu verschieben), müssen Sie nur:

* Extrahieren `repository.xml` An den erforderlichen Speicherort

* `repository.xml` nach Bedarf aktualisieren

* `bootstrap.properties` erstellen und `repository.config` definieren

Zur Erinnerung: Führen Sie diese Aktionen vor der tatsächlichen Installation aus.
