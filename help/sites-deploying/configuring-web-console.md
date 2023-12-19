---
title: Web-Konsole in AEM
description: Erfahren Sie, wie Sie die Web-Konsole in Adobe Experience Manager (AEM) verwenden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
exl-id: bdfeaf85-e832-40c1-8769-7d027cdb021e
source-git-commit: c7c32130a3257c14c98b52f9db31d80587d7993a
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 68%

---

# Web-Konsole{#web-console}

Die Web-Konsole in Adobe Experience Manager (AEM) basiert auf dem [Apache Felix Web Management Console](https://felix.apache.org/documentation/subprojects/apache-felix-web-console.html). Apache Felix ist ein Gemeinschaftsprojekt zur Implementierung der OSGi R4-Dienstplattform, die das OSGi-Framework und Standarddienste umfasst.

>[!NOTE]
>
>In der Web-Konsole beziehen sich alle Beschreibungen, in denen Standardeinstellungen erwähnt werden, auf die Sling-Standardeinstellungen.
>
>Für AEM gelten eigene Standardeinstellungen, sodass sich die festgelegten Standardeinstellungen möglicherweise von denen der Konsole unterscheiden.

Die Web-Konsole bietet eine Auswahl von Registerkarten zur Verwaltung der OSGi-Bundles, darunter:

* [Konfiguration](#configuration): wird zum Konfigurieren der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zum Konfigurieren der AEM-Systemparameter.
* [Bundles](#bundles): wird für die Installation von Bundles verwendet
* [Komponenten](#components): dient zur Kontrolle der Status der für AEM erforderlichen Komponenten

Alle vorgenommenen Änderungen werden sofort auf das laufende System angewendet. Es ist kein Neustart erforderlich.

Der Zugriff auf die Konsole ist über `../system/console` möglich, z. B.:

`http://localhost:4502/system/console/components`

## Konfiguration {#configuration}

Die Registerkarte **Konfiguration** wird zur Konfiguration der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zur Konfiguration der AEM-Systemparameter.

>[!NOTE]
>
>Siehe [OSGi-Konfiguration mit der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) für weitere Informationen.

Auf die Registerkarte **Konfiguration** kann unter anderem wie folgt zugegriffen werden:

* über das Dropdown-Menü:

  **OSGi >**

* Die URL; Beispiel:

  `http://localhost:4502/system/console/configMgr`

Eine Liste der Konfigurationen wird angezeigt:

![screen_shot_2012-02-15at52308pm-1](assets/screen_shot_2012-02-15at52308pm-1.png)

In den Dropdown-Listen auf diesem Bildschirm stehen zwei Arten von Konfigurationen zur Verfügung:

* **Konfigurationen**

  Hier können Sie die vorhandenen Konfigurationen aktualisieren. Diese weisen eine persistente Identität (PID) auf und können Folgendes sein:

   * Standard und integraler Bestandteil von AEM – diese sind erforderlich. Durch Löschen werden die Werte auf die Standardeinstellungen zurückgesetzt.
   * Instanzen, die von Werkskonfigurationen erstellt wurden – diese Instanzen werden von Benutzenden erstellt. Durch Löschen wird die Instanz entfernt.

* **Werkskonfigurationen**

  Erstellen Sie eine Instanz des erforderlichen Funktionsobjekts.

  Diese wird einer persistenten Identität zugewiesen und dann in der Dropdown-Liste Konfigurationen aufgeführt.

Wenn Sie einen Eintrag aus der Liste auswählen, werden die Parameter für diese Konfiguration angezeigt:

![chlimage_1-61](assets/chlimage_1-61.png)

Die Parameter können dann ggf. aktualisiert werden und Sie können unter folgenden Optionen wählen:

* **Speichern**

  Speichert die vorgenommenen Änderungen.

  Bei einer Factory-Konfiguration wird dadurch eine Instanz mit einer beständigen Identität erstellt. Die neue Instanz wird unter Konfigurationen aufgeführt.

* **Zurücksetzen**

  Setzen Sie die auf dem Bildschirm angezeigten Parameter auf die zuletzt gespeicherten zurück.

* **Löschen**

  Löscht die aktuelle Konfiguration. Bei einer Standardinstanz werden die Parameter auf die Standardeinstellungen zurückgesetzt. Wenn sie über eine Werkskonfiguration erstellt wurde, wird die spezifische Instanz gelöscht.

* **Bindung aufheben**

  Hebt die Bindung zwischen der aktuellen Konfiguration und dem Bundle auf.

* **Abbrechen**

  Verwirft alle aktuellen Änderungen.

## Bundles {#bundles}

Die Registerkarte **Bundles** stellt den Mechanismus zum Installieren der für AEM erforderlichen OSGi-Pakete dar. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* über das Dropdown-Menü:

  **OSGi >**

* Die URL; Beispiel:

  `http://localhost:4502/system/console/bundles`

Eine Liste von Bundles wird angezeigt:

![screen_shot_2012-02-15at44740pm-1](assets/screen_shot_2012-02-15at44740pm-1.png)

Auf dieser Registerkarte stehen folgende Optionen zur Verfügung:

* **Installieren oder aktualisieren**

  Hiermit können Sie nach der Datei mit Ihrem Bundle **suchen** und festlegen, ob dieses sofort **gestartet** werden soll, und mit welcher **Startebene**.

* **Neu laden**

  Aktualisiert die angezeigte Liste.

* **Pakete aktualisieren**

  Dadurch werden die Referenzen aller Pakete überprüft und bei Bedarf aktualisiert.

   So werden möglicherweise nach einer Aktualisierung die alte und die neue Version aufgrund vorheriger Verweise weiter ausgeführt, Mit dieser Option werden alle Verweise auf die neue Version überprüft und verschoben, sodass die alte Version angehalten werden kann.

* **Starten**

  Startet ein Bundle gemäß der angegebenen Startebene.

* **Anhalten**

  Stoppt das Bundle.

* **Deinstallieren**

  Deinstalliert das Bundle vom System.

* **Status anzeigen**

  Die Liste gibt den Status des Bundles an. Durch Klicken auf den Namen eines bestimmten Bundles werden weitere Informationen angezeigt.

>[!NOTE]
>
>Nachher **Aktualisieren** empfiehlt Adobe, dass Sie eine **Aktualisieren von Paketen**.

## Komponenten {#components}

Auf der Registerkarte **Komponenten** können Sie die verschiedenen Komponenten aktivieren und/oder deaktivieren. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* über das Dropdown-Menü:

  **Main >**

* Die URL; Beispiel:

  `http://localhost:4502/system/console/components`

Eine Liste von Komponenten wird angezeigt. Eine Reihe von Symbolen steht zur Verfügung, mit denen Sie die Komponenten aktivieren, deaktivieren oder ggf. Konfigurationsdetails für eine bestimmte Komponente öffnen können.

![screen_shot_2012-02-15at52144pm-1](assets/screen_shot_2012-02-15at52144pm-1.png)

Wenn Sie auf den Namen einer bestimmten Komponente klicken, werden weitere Informationen zum Status angezeigt. Hier können Sie die Komponente auch aktivieren, deaktivieren oder neu laden.

![chlimage_1-62](assets/chlimage_1-62.png)

>[!NOTE]
>
>Die Aktivierung oder Deaktivierung einer Komponente gilt nur, bis AEM/CRX neu gestartet wird.
>
>Der Startstatus wird innerhalb des Komponentendeskriptors definiert, der während der Entwicklung generiert und zum Zeitpunkt der Bundle-Erstellung im Bundle gespeichert wird.
