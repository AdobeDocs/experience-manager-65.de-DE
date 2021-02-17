---
title: Web-Konsole
seo-title: Web-Konsole
description: Erfahren Sie, wie Sie die Web-Konsole in AEM verwenden.
seo-description: Erfahren Sie, wie Sie die Web-Konsole in AEM verwenden.
uuid: 047274ff-4d7d-4c7d-95be-06f363beae2e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: f934eb02-1f84-44f2-9f14-3f17250c9a90
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 71%

---


# Web-Konsole{#web-console}

Die Web-Konsole in AEM basiert auf der [Apache Felix Web Management Console](https://felix.apache.org/documentation/subprojects/apache-felix-web-console.html). Apache Felix ist ein gemeinschaftlich entwickeltes Framework zum Implementieren der OSGi R4 Service Platform, die das OSGi-Framework und die Standarddienste umfasst.

>[!NOTE]
>
>In der Web-Konsole beziehen sich alle Beschreibungen mit Standardeinstellungen auf Sling-Standardwerte.
>
>Für AEM gelten eigene Standardeinstellungen, sodass sich die festgelegten Standardeinstellungen möglicherweise von denen der Konsole unterscheiden.

Die Web-Konsole umfasst eine Reihe von Registerkarten für die Verwaltung der OSGi-Bundles, darunter:

* [Konfiguration:](#configuration) Dient zur Konfiguration der OSGi-Bundles und bildet deshalb den zugrunde liegenden Mechanismus für die Konfiguration der AEM-Systemparameter.
* [Bundles:](#bundles) Dient zum Installieren von Bundles.
* [Komponenten:](#components) Steuert den Status der für AEM erforderlichen Komponenten.

Alle vorgenommenen Änderungen werden sofort auf das laufende System angewendet. Ein Neustart ist nicht erforderlich.

Die Konsole kann von `../system/console` aus aufgerufen werden. Beispiel:

`http://localhost:4502/system/console/components`

## Konfiguration {#configuration}

Die Registerkarte **Konfiguration** dient zur Konfiguration der OSGi-Bundles und bildet deshalb den zugrunde liegenden Mechanismus für die Konfiguration der AEM-Systemparameter.

>[!NOTE]
>
>Weitere Einzelheiten finden Sie unter [OSGi-Konfiguration mit der Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console).

Sie können mit einer der beiden folgenden Methoden auf die Registerkarte **Konfiguration** zugreifen:

* Das Dropdown-Menü:

   **OSGi >**

* die URL; Beispiel:

   `http://localhost:4502/system/console/configMgr`

Eine Liste der Konfigurationen wird angezeigt:

![screen_shot_2012-02-15at52308pm-1](assets/screen_shot_2012-02-15at52308pm-1.png)

Es gibt zwei Arten von Konfigurationen, die in den Dropdown-Listen auf dem Bildschirm verfügbar sind:

* **Konfigurationen**

   Ermöglicht die Aktualisierung der vorhandenen Konfigurationen. Diese haben eine Persistent Identity (PID) und fallen in eine der beiden folgenden Kategorien:

   * Standardkonfigurationen, die ein integraler Bestandteil von AEM sind. Sie sind erforderlich, und die Werte werden beim Löschen auf die Standardeinstellungen zurückgesetzt.
   * Instanzen, die vom Benutzer auf Basis von Factory-Konfigurationen erstellt werden. Sie werden durch Löschen der Instanzen entfernt.

* **Factory-Konfigurationen**

   Ermöglicht das Erstellen einer Instanz des erforderlichen Funktionsobjekts.

   Diesem Objekt wird eine Persistent Identity (PID) zugewiesen und es wird dann in der Dropdown-Liste „Konfigurationen“ aufgeführt.

Bei Auswahl eines Eintrags aus den Listen werden die Parameter für die Konfiguration angezeigt:

![chlimage_1-61](assets/chlimage_1-61.png)

Die Parameter können dann ggf. aktualisiert werden und Sie können unter folgenden Optionen wählen:

* **Speichern**

   Speichern Sie die vorgenommenen Änderungen.

    Für eine Factory-Konfiguration wird hierdurch eine neue Instanz mit einer Persistent Identity erstellt. Die neue Instanz wird dann unter „Konfigurationen“ aufgelistet.

* **Zurücksetzen**

   Setzen Sie die auf dem Bildschirm angezeigten Parameter auf die zuletzt gespeicherten Parameter zurück.

* **Löschen**

   Löschen Sie die aktuelle Konfiguration. Bei einer Standardinstanz werden die Parameter auf die Standardeinstellungen zurückgesetzt. Basiert die Instanz auf einer Factory-Konfiguration, wird die spezifische Instanz gelöscht.

* **Unbind**

   Trennen Sie die Bindung der aktuellen Konfiguration vom Bundle.

* **Abbrechen**

   Alle aktuellen Änderungen abbrechen.

## Bundles {#bundles}

Die Registerkarte **Pakete** ist der Mechanismus zum Installieren der OSGi-Pakete, die für AEM erforderlich sind. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* Das Dropdown-Menü:

   **OSGi >**

* die URL; Beispiel:

   `http://localhost:4502/system/console/bundles`

Eine Liste mit Bundles wird angezeigt:

![screen_shot_2012-02-15at44740pm-1](assets/screen_shot_2012-02-15at44740pm-1.png)

Auf dieser Registerkarte stehen folgende Optionen zur Verfügung:

* **Installieren oder Aktualisieren**

   Sie können **Browse** suchen, um die Datei mit Ihrem Bundle zu suchen und anzugeben, ob **Beginn** sofort angezeigt werden soll und auf welcher **Beginn-Ebene**.

* **Neu laden**

   Aktualisiert die angezeigte Liste.

* **Pakete aktualisieren**

   Dadurch werden die Referenzen aller Pakete überprüft und nach Bedarf aktualisiert.

    So werden möglicherweise nach einer Aktualisierung die alte und die neue Version aufgrund vorheriger Verweise weiter ausgeführt, Diese Option prüft und transferiert alle Verweise auf die neue Version, sodass die alte Version beendet werden kann.

* **Anfang**

   Beginn eines Bundles entsprechend der angegebenen Beginn-Ebene.

* **Anhalten**

   Hält das Bundle an.

* **Deinstallieren**

   Deinstalliert das Bundle vom System.

* **den Status**

   Die Liste gibt den aktuellen Status des Bundles an. Klicken Sie auf den Namen eines Bundles mit weiteren Informationen.

>[!NOTE]
>
>Nach einer **Aktualisierung** wird empfohlen, die **Pakete zu aktualisieren**.

## Komponenten {#components}

Auf der Registerkarte **Komponenten** können Sie die verschiedenen Komponenten aktivieren und/oder deaktivieren. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* Das Dropdown-Menü:

   **Main >**

* die URL; Beispiel:

   `http://localhost:4502/system/console/components`

Eine Liste der Komponenten wird angezeigt. Eine Reihe von Symbolen steht zur Verfügung, mit denen Sie die Komponenten aktivieren, deaktivieren oder ggf. Konfigurationsdetails für eine bestimmte Komponente öffnen können.

![screen_shot_2012-02-15at52144pm-1](assets/screen_shot_2012-02-15at52144pm-1.png)

Klicken Sie auf den Namen einer bestimmten Komponente, um weitere Informationen zu deren Status anzuzeigen. Hier können Sie die Komponente auch aktivieren, deaktivieren oder neu laden.

![chlimage_1-62](assets/chlimage_1-62.png)

>[!NOTE]
>
>Das Aktivieren oder Deaktivieren einer Komponente gilt nur, bis AEM/CRX neu gestartet wird.
>
>Der Startstatus ist im Komponenten-Deskriptor definiert, der bei der Entwicklung generiert wird, und wird bei der Bundle-Erstellung im Bundle gespeichert.

