---
title: Start und Stopp über die Befehlszeile
description: Erfahren Sie, wie Sie Adobe Experience Manager über die Befehlszeile starten und stoppen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
exl-id: 21041b55-240c-487d-9d79-c54c877f4e1e
source-git-commit: e068cee192c0837f1473802143e0793674d400e8
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 40%

---

# Start und Stopp über die Befehlszeile{#command-line-start-and-stop}

## Starten von Adobe Experience Manager über die Befehlszeile {#starting-adobe-experience-manager-from-the-command-line}

Das Skript `start` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl UNIX®- als auch Windows-Versionen werden bereitgestellt. Das Skript startet die in *&lt;cq-installation>* Verzeichnis.

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
>Einige Ausführungsmodi, darunter Autoren- und Veröffentlichungsmodus, müssen vor dem ersten Start der AEM festgelegt werden und können danach nicht mehr geändert werden. Bevor Sie eine AEM-Instanz einrichten, die in der Produktion verwendet wird, lesen Sie [Dokumentation zu Ausführungsmodi](/help/sites-deploying/configure-runmodes.md) für Details.

### Skriptbeispiel für Windows-Plattform start.bat {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### Beispiel für ein Startskript der UNIX®-Plattform {#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Über das Skript „start“ wird der im Ordner *the &lt;cq-installation>/app* installierte AEM-Schnellstart gestartet.

## Beenden von Adobe Experience Manager {#stopping-adobe-experience-manager}

Um AEM zu beenden, führen Sie einen der folgenden Schritte aus:

* Abhängig von der verwendeten Plattform:

   * Drücken Sie **Strg + C**, um den Server herunterzufahren, wenn Sie AEM über ein Skript oder die Befehlszeile gestartet haben.
   * Wenn Sie das Startskript unter UNIX® verwendet haben, müssen Sie das Stopp-Skript verwenden, um AEM anzuhalten.

* Wenn Sie AEM durch Doppelklicken auf die JAR-Datei gestartet haben, klicken Sie auf die **on** Schaltfläche im Startfenster (die Schaltfläche ändert sich in **Aus**), um den Server herunterzufahren.

  ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager über die Befehlszeile anhalten {#stopping-adobe-experience-manager-from-the-command-line}

Das Skript `stop` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl UNIX®- als auch Windows-Versionen werden bereitgestellt. Das Skript hält die im Verzeichnis *&lt;cq-installation>* installierte aktive Instanz an.

### Beispiel eines Stoppskripts für die UNIX®-Plattform {#unix-platform-stop-script-example}

```shell
./stop
```

### Skriptbeispiel für das Windows-Plattform-stop.bat {#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Wenn Sie das Repository nur vorkonfigurieren möchten (ohne es neu zu lokalisieren), müssen Sie nur:

* Extract `repository.xml` an den gewünschten Ort

* `repository.xml` nach Bedarf aktualisieren

* `bootstrap.properties` erstellen und `repository.config` definieren

Zur Erinnerung: Führen Sie diese Aktionen vor der tatsächlichen Installation aus.
