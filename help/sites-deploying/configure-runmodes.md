---
title: Ausführungsmodi
seo-title: Ausführungsmodi
description: Hier erfahren Sie, wie Sie Ihre AEM-Instanz mithilfe von Ausführungsmodi an einen bestimmten Verwendungszweck anpassen.
seo-description: Hier erfahren Sie, wie Sie Ihre AEM-Instanz mithilfe von Ausführungsmodi an einen bestimmten Verwendungszweck anpassen.
uuid: 8a0c6e5c-4fae-43e2-b745-eee58f346ceb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 12329e26-40bc-4c94-bc60-6d9cbd01345f
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 83%

---


# Ausführungsmodi{#run-modes}

Mithilfe von Ausführungsmodi können Sie Ihre AEM-Instanz an einen bestimmten Zweck anpassen, z. B. Inhaltserstellung, Veröffentlichung, Test, Entwicklung oder Intranet.

Sie haben folgende Möglichkeiten:

* [Gruppen von Konfigurationsparametern für jeden Ausführungsmodus definieren](#defining-configuration-properties-for-a-run-mode)

   Ein Grundbestand an Konfigurationsparametern wird auf alle Ausführungsmodi angewendet. Sie können dann zusätzliche Parameter entsprechend den Anforderungen Ihrer spezifischen Umgebung einstellen. Diese werden nach Bedarf angewendet.

* [Zusätzliche Bundles definieren, die für einen bestimmten Modus installiert werden](#defining-additional-bundles-to-be-installed-for-a-run-mode)

Sämtliche Einstellungen und Definitionen werden im selben Repository gespeichert und durch die Auswahl des **Ausführungsmodus** aktiviert.

## Installations-Ausführungsmodi {#installation-run-modes}

Installations- (oder fixe) Ausführungsmodi werden während der Installation verwendet und bleiben für die gesamte Dauer der Instanz gleich. Sie können nicht geändert werden. 

Installations-Ausführungsmodi sind vordefiniert:

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

Jeweils zwei Paare von Ausführungsmodi schließen einander gegenseitig aus. Sie können beispielsweise:

* entweder `author` oder `publish` definieren, nicht beide gleichzeitig

* `author` entweder mit `samplecontent` oder `nosamplecontent` kombinieren (aber nicht mit beiden)

>[!CAUTION]
>
>Wenn Sie einen der obigen Ausführungsmodi verwenden (author, publish, samplecontent, nosamplecontent), wird der während der Installation verwendete Wert für den Ausführungsmodus während der *gesamten Lebensdauer* dieser Installation beibehalten.
>
>Sie können diesen Wert für diese Ausführungsmodi nach der Installation *nicht mehr* ändern.

## Ausführungsmodi anpassen {#customized-run-modes}

Sie können auch Ihre eigenen, benutzerdefinierten Ausführungsmodi erstellen. Diese können beispielsweise folgendermaßen kombiniert werden:

* `author` + `development`

* `publish` +  `test`

* `publish` + `test` + `golive`

* `publish` +  `intranet`

* nach Bedarf ...

Benutzerdefinierte Ausführungsmodi können auch bei jedem Start ausgewählt werden. 

## Verwenden von samplecontent und nosamplecontent {#using-samplecontent-and-nosamplecontent}

Mit diesen Modi können Sie die Verwendung von Beispielinhalten steuern. Beispielinhalte werden definiert, bevor der Schnellstart erstellt wird. Sie können Pakete, Konfigurationen usw. enthalten:

* Mit dem Ausführungsmodus `samplecontent` wird dieser Inhalt installiert (Standardmodus). 

* Mit dem Modus `nosamplecontent` wird der Beispielinhalt nicht installiert.

Der nosamplecontent-Ausführungsmodus ist für Produktionsinstallationen bestimmt.

## Definieren von Konfigurationseigenschaften für einen Ausführungsmodus  {#defining-configuration-properties-for-a-run-mode}

Die Werte der Konfigurationseigenschaften, die für einen bestimmten Ausführungsmodus verwendet werden, können im Repository gespeichert werden.

Der Ausführungsmodus ist durch ein Suffix im Ordnernamen gekennzeichnet. Dadurch können Sie alle Konfigurationen in einem einzigen Repository speichern. Beispiel:

* `config`

   Gilt für alle Ausführungsmodi

* `config.author`

   Wird für den Autorenmodus verwendet

* `config.publish`

   Wird für den Veröffentlichungsmodus verwendet

* `config.<run-mode>`

   Wird für die den entsprechenden Ausführungsmodus verwendet. z. B. config

Siehe [OSGi-Konfiguration im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) für weitere Informationen zum Definieren der einzelnen Konfigurationsknoten in diesen Ordnern und zum Erstellen von Konfigurationen für Kombinationen aus mehreren Ausführungsmodi.

>[!NOTE]
>
>Für [Installations-Ausführungsmodi](#installation-run-modes) (z. B. author) kann der Ausführungsmodus nach der Installation nicht mehr geändert werden. Doch Änderungen an einzelnen Konfigurationseigenschaften werden bei einem Neustart wirksam.

## Definieren von zusätzlichen für einen Ausführungsmodus zu installierenden Bundles  {#defining-additional-bundles-to-be-installed-for-a-run-mode}

Zusätzliche Bundles, die für einen bestimmten Ausführungsmodus installiert werden sollen, können ebenfalls angegeben werden. Für diese Definitionen werden Installationsordner zum Speichern der Pakete verwendet. Auch hier ist der Ausführungsmodus durch ein Präfix gekennzeichnet:

* `install.author`
* `install.publish`

Diese Ordner sich vom Typ `nt:folder` und sollten das entsprechende Bundle enthalten.

## Starten von CQ mit einem bestimmten Ausführungsmodus {#starting-cq-with-a-specific-run-mode}

Wenn Sie Konfigurationen für mehrere Ausführungsmodi definiert haben, müssen Sie festlegen, welcher beim Start verwendet werden soll. Zur Spezifizierung des Ausführungsmodus gibt es mehrere Möglichkeiten. Gehen Sie nach dieser Reihenfolge vor:

1. [ `sling.properties` Datei an](#using-the-sling-properties-file)
1. [ `-r` option](#using-the-r-option)
1. [Systemeigenschaften (`-D`)](#using-a-system-property-in-the-start-script)

1. [Erkennung von Dateinamen](#filename-detection-renaming-the-jar-file) 

Wenn Sie einen Anwendungsserver verwenden, können Sie auch [den Ausführungsmodus in web.xml](#defining-the-run-mode-in-web-xml-with-application-server) definieren.

### Verwenden der sling.properties-Datei {#using-the-sling-properties-file}

Mit der Datei `sling.properties` können Sie den erforderlichen Ausführungsmodus definieren:

1. Bearbeiten Sie die Konfigurationsdatei:

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. hinzufügen die folgenden Eigenschaften; das folgende Beispiel ist für den Autor bestimmt:

   `sling.run.modes=author`

### Verwenden der -r-Option {#using-the-r-option}

Ein benutzerdefinierter Ausführungsmodus kann beim Starten des Schnellstarts mit der Option `-r` aktiviert werden. Verwenden Sie beispielsweise den folgenden Befehl, um eine AEM Instanz mit dem Ausführungsmodus zu starten, für die &quot;dev&quot;festgelegt ist. &quot;

```shell
java -jar cq-56-p4545.jar -r dev
```

### Verwenden einer Systemeigenschaft im Startskript {#using-a-system-property-in-the-start-script}

Mit einer Systemeigenschaft im Startskript kann der Ausführungsmodus spezifiziert werden.

* Verwenden Sie beispielsweise Folgendes, um eine Instanz als Produktions-Veröffentlichungsinstanz in den USA zu starten:

   `-Dsling.run.modes=publish,prod,us`

### Erkennen von Dateinamen – Umbenennen der JAR-Datei {#filename-detection-renaming-the-jar-file}

Die folgenden beiden Installationslaufmodi können vor der Installation durch Umbenennen der JAR-Datei für die Installation aktiviert werden:

* publish
* author

Die JAR-Datei muss diese Benennungskonvention verwenden:

`cq5-<run-mode>-p<port-number>`

Beispielsweise können Sie den Ausführungsmodus `publish` festlegen, indem Sie die JAR-Datei folgendermaßen benennen:

`cq5-publish-p4503`

### Definieren des Ausführungsmodus in web.xml (mit Anwendungsserver) {#defining-the-run-mode-in-web-xml-with-application-server}

Wenn Sie einen Anwendungsserver verwenden, können Sie auch die Eigenschaft:

`sling.run.modes`

in der Datei:

`WEB-INF/web.xml`

Dies ist die `war`-Datei von AEM. Sie sollte vor der Bereitstellung aktualisiert werden.

Weitere Informationen dazu finden Sie unter [Installieren von AEM mit einem Anwendungsserver](/help/sites-deploying/application-server-install.md).
