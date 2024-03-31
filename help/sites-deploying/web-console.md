---
title: Web-Konsole in Adobe Experience Manager
description: Erfahren Sie, wie Sie die Web-Konsole von Adobe Experience Manager (AEM) verwenden.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
feature: Configuring
exl-id: 9acbf61f-73a8-4998-9421-dd933f30ac8a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 100%

---

# Web-Konsole{#web-console}

Die Web-Konsole in Adobe Experience Manager (AEM) basiert auf der [Apache Felix Web Management Console](https://felix.apache.org/documentation/subprojects/apache-felix-web-console.html). Apache Felix ist ein Gemeinschaftsprojekt zur Implementierung der OSGi R4-Dienstplattform, die das OSGi-Framework und Standarddienste umfasst.

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
>Siehe [OSGi-Konfiguration mit der Web-Konsole](/help/sites-deploying/configuring-osgi.md) für weitere Informationen.

Auf die Registerkarte **Konfiguration** kann unter anderem wie folgt zugegriffen werden:

* über das Dropdown-Menü:

  **OSGi >**

* Die URL; Beispiel:

  `http://localhost:4502/system/console/configMgr`

Eine Liste der Konfigurationen wird angezeigt:

![screen_shot_2012-02-15at52308pm](assets/screen_shot_2012-02-15at52308pm.png)

Es gibt zwei Arten von Konfigurationen, die in den Dropdown-Listen auf diesem Bildschirm verfügbar sind:

* **Konfigurationen**
Hier können Sie die vorhandenen Konfigurationen aktualisieren. Diese weisen eine persistente Identität (PID) auf und können Folgendes sein:

   * Standard und integraler Bestandteil von AEM – diese sind erforderlich. Durch Löschen werden die Werte auf die Standardeinstellungen zurückgesetzt.
   * Instanzen, die von Werkskonfigurationen erstellt wurden – diese Instanzen werden von Benutzenden erstellt. Durch Löschen wird die Instanz entfernt.

* **Werkskonfigurationen**
Hier können Sie eine Instanz des erforderlichen Funktionsobjekts erstellen.

  Diese wird einer persistenten Identität zugewiesen und dann in der Dropdown-Liste mit den Konfigurationen aufgeführt.

Bei Auswahl eines Eintrags aus den Listen werden die Parameter für die Konfiguration angezeigt:

![chlimage_1-21](assets/chlimage_1-21a.png)

Die Parameter können dann ggf. aktualisiert werden und Sie können unter folgenden Optionen wählen:

* **Speichern**

  Speichert die vorgenommenen Änderungen.

  Für eine Werkskonfiguration wird hierdurch eine Instanz mit einer persistenten Identität erstellt. Die neue Instanz wird dann unter „Konfigurationen“ aufgelistet.

* **Zurücksetzen**

  Setzt die auf dem Bildschirm gezeigten Parameter auf die zuletzt gespeicherten zurück.

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

Eine Liste mit Paketen wird angezeigt:

![screen_shot_2012-02-15at44740pm](assets/screen_shot_2012-02-15at44740pm.png)

Auf dieser Registerkarte stehen folgende Optionen zur Verfügung:

* **Installieren oder aktualisieren**

  Hiermit können Sie nach der Datei mit Ihrem Bundle **suchen** und festlegen, ob dieses sofort **gestartet** werden soll, und mit welcher **Startebene**.

* **Neu laden**

  Aktualisiert die angezeigte Liste.

* **Pakete aktualisieren**

  Diese Option prüft die Verweise aller Pakete und aktualisiert sie ggf.

  So werden möglicherweise nach einer Aktualisierung sowohl die alte als auch die neue Version aufgrund vorheriger Verweise weiter ausgeführt. Diese Option prüft und transferiert alle Verweise auf die neue Version, sodass die alte Version beendet werden kann.

* **Starten**

  Startet ein Bundle gemäß der angegebenen Startebene.

* **Anhalten**

  Stoppt das Bundle.

* **Deinstallieren**

  Deinstalliert das Bundle vom System.

* **Status anzeigen**

  Die Liste gibt den Status des Pakets an. Klicken Sie auf den Namen eines bestimmten Pakets, um weitere Informationen anzuzeigen.

>[!NOTE]
>
>Nach dem **Update** empfiehlt Adobe, die Aktion **Pakete aktualisieren** durchzuführen.

## Komponenten {#components}

Auf der Registerkarte **Komponenten** können Sie die verschiedenen Komponenten aktivieren und/oder deaktivieren. Sie können mit einer der beiden folgenden Methoden auf die Registerkarte zugreifen:

* über das Dropdown-Menü:

  **Main >**

* Die URL; Beispiel:

  `http://localhost:4502/system/console/components`

Eine Liste der Komponenten wird angezeigt. Eine Reihe von Symbolen steht zur Verfügung, mit denen Sie die Komponenten aktivieren, deaktivieren oder ggf. Konfigurationsdetails für eine bestimmte Komponente öffnen können.

![screen_shot_2012-02-15at52144pm](assets/screen_shot_2012-02-15at52144pm.png)

Klicken Sie auf den Namen einer bestimmten Komponente, um weitere Informationen zu deren Status anzuzeigen. Hier können Sie die Komponente auch aktivieren, deaktivieren oder neu laden.

![chlimage_1-22](assets/chlimage_1-22a.png)

>[!NOTE]
>
>Das Aktivieren oder Deaktivieren einer Komponente gilt nur, bis AEM/CRX neu gestartet wird.
>
>Der Startstatus wird innerhalb des Komponentendeskriptors definiert, der während der Entwicklung generiert und zum Zeitpunkt der Paketerstellung im Paket gespeichert wird.
