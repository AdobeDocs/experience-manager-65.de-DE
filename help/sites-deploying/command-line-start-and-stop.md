---
title: Start und Stopp über die Befehlszeile
seo-title: Start und Stopp über die Befehlszeile
description: Hier erfahren Sie, wie Sie AEM über die Befehlszeile starten und anhalten können.
seo-description: Hier erfahren Sie, wie Sie AEM über die Befehlszeile starten und anhalten können.
uuid: 585f071c-2286-4a2c-af07-404bf298cba8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 9333ff84-f624-4cfa-a9e4-c5e3882171ff
exl-id: 21041b55-240c-487d-9d79-c54c877f4e1e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 93%

---

# Start und Stopp über die Befehlszeile{#command-line-start-and-stop}

## Adobe Experience Manager über die Befehlszeile starten {#starting-adobe-experience-manager-from-the-command-line}

Das Skript `start` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl die Unix- als auch die Windows-Version wird bereitgestellt. Das Skript startet die im Verzeichnis *&lt;cq-installation>* installierte Instanz.

Diese beiden Versionen unterstützen eine Liste von Umgebungsvariablen, die zum Starten und Optimieren der AEM-Instanz verwendet werden können.

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
   <td>Durch Komma(s) getrennte Ausführungsmodi<br /> </td>
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
>Beachten Sie, dass einige Ausführungsmodi, wie „author“ und „publish“, vor dem ersten Starten von AEM eingerichtet werden müssen und im Nachhinein nicht mehr geändert werden können. Lesen Sie vor dem Einrichten einer AEM-Instanz, die in der Produktion verwendet werden soll, die [Dokumentation für die Ausführungsmodi](/help/sites-deploying/configure-runmodes.md), um weitere Informationen zu erhalten.

### „start.bat“-Skriptbeispiel für Windows-Plattform  {#windows-platform-start-bat-script-example}

```shell
SET CQ_PORT=1234 & ./start.bat
```

### „start“-Skriptbeispiel für Unix-Plattform{#unix-platform-start-script-example}

```shell
CQ_PORT=1234 ./start
```

>[!NOTE]
>
>Über das Skript „start“ wird der im Ordner *the &lt;cq-installation>/app* installierte AEM-Schnellstart gestartet.

## Anhalten von Adobe Experience Manager {#stopping-adobe-experience-manager}

Führen Sie zum Anhalten von AEM eine der folgenden Aktionen aus:

* In Abhängigkeit der von Ihnen verwendeten Plattform:

   * Drücken Sie **Strg + C**, um den Server herunterzufahren, wenn Sie AEM über ein Skript oder die Befehlszeile gestartet haben.
   * Wenn Sie das Skript „start“ unter UNIX verwendet haben, müssen Sie das Skript „stop“ zum Anhalten von AEM verwenden.

* Wenn Sie AEM durch Doppelklicken auf die JAR-Datei gestartet haben, klicken Sie im Startfenster auf die Schaltfläche **Ein** (die Schaltfläche ändert sich in **Aus**), um den Server herunterzufahren.

   ![chlimage_1-63](assets/chlimage_1-63.png)

## Adobe Experience Manager über die Befehlszeile anhalten {#stopping-adobe-experience-manager-from-the-command-line}

Das Skript `stop` befindet sich im Verzeichnis *&lt;cq-installation>/bin*. Sowohl die Unix- als auch die Windows-Version wird bereitgestellt. Das Skript hält die im Verzeichnis *&lt;cq-installation>* installierte aktive Instanz an.

### „stop“-Skriptbeispiel für Unix-Plattform{#unix-platform-stop-script-example}

```shell
./stop
```

### „stop.bat“-Skriptbeispiel für Windows-Plattform{#windows-platform-stop-bat-script-example}

```shell
./stop.bat
```

Wenn Sie das Repository einfach vorkonfigurieren möchten (ohne seine Position zu verändern), gehen Sie folgendermaßen vor:

* `repository.xml` am erforderlichen Speicherort extrahieren

* Aktualisieren Sie `repository.xml` nach Bedarf

* `bootstrap.properties` erstellen und `repository.config` definieren

Zur Erinnerung: Führen Sie diese Aktionen vor der tatsächlichen Installation aus.
