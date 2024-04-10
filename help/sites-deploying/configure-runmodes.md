---
title: Ausführungsmodi
description: Erfahren Sie, wie Sie Ihre AEM-Instanz mithilfe von Ausführungsmodi für bestimmte Zwecke anpassen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Administering
exl-id: 6d03cb1d-500e-4a23-80e5-347a43dff30e
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 100%

---

# Ausführungsmodi{#run-modes}

Mit Ausführungsmodi können Sie Ihre AEM-Instanz auf einen bestimmten Zweck ausrichten, z. B. Author oder Publish, Test, Entwicklung, Intranet usw.

Sie haben folgende Möglichkeiten:

* [Kollektionen von Konfigurationsparametern für jeden Ausführungsmodus definieren](#defining-configuration-properties-for-a-run-mode).

  Ein Grundbestand an Konfigurationsparametern wird auf alle Ausführungsmodi angewendet. Sie können dann zusätzliche Parameter entsprechend den Anforderungen Ihrer spezifischen Umgebung einstellen. Diese werden nach Bedarf angewendet.

* [Definieren von zusätzlichen Bundles, die für einen bestimmten Modus installiert werden sollen](#defining-additional-bundles-to-be-installed-for-a-run-mode).

Sämtliche Einstellungen und Definitionen werden im selben Repository gespeichert und durch die Auswahl des **Ausführungsmodus** aktiviert.

## Installations-Ausführungsmodi {#installation-run-modes}

Installations- (oder fixe) Ausführungsmodi werden während der Installation verwendet und bleiben für die gesamte Dauer der Instanz gleich. Sie können nicht geändert werden.

Installations-Ausführungsmodi sind vordefiniert:

* `author`
* `publish`
* `samplecontent`
* `nosamplecontent`

Jeweils zwei Paare von Ausführungsmodi schließen einander gegenseitig aus. Sie können beispielsweise:

* entweder `author` oder `publish` definieren, aber nicht beide gleichzeitig;

* `author` mit `samplecontent` oder `nosamplecontent` (aber nicht beiden) kombinieren.

>[!CAUTION]
>
>Bei Verwendung eines der oben genannten Ausführungsmodi (author, publish, samplecontent, nosamplecontent) definiert der während der Installation verwendete Wert den Ausführungsmodus für die *gesamte Lebensdauer* der Installation.
>
>Bei diesen Ausführungsmodi können Sie diese Werte nach der Installation *nicht* ändern.

## Benutzerdefinierte Ausführungsmodi {#customized-run-modes}

Sie können auch eigene, benutzerdefinierte Ausführungsmodi erstellen. Diese können kombiniert werden, um Szenarien abzudecken, wie z. B.:

* `author` + `development`

* `publish` + `test`

* `publish` + `test` + `golive`

* `publish` + `intranet`

* nach Bedarf ...

Benutzerdefinierte Ausführungsmodi können auch bei jedem Start ausgewählt werden.

## Verwenden von samplecontent und nosamplecontent {#using-samplecontent-and-nosamplecontent}

Mit diesen Modi können Sie die Verwendung von Beispielinhalten steuern. Der Beispielinhalt wird vor der Erstellung des Schnellstarts definiert und kann Pakete, Konfigurationen usw. umfassen:

* Mit dem Ausführungsmodus `samplecontent` wird dieser Inhalt installiert (Standardmodus). 

* Mit dem Modus `nosamplecontent` wird der Beispielinhalt nicht installiert.

Der Ausführungsmodus nosamplecontent wurde für Produktionsinstallationen entwickelt.

## Definieren von Konfigurationseigenschaften für einen Ausführungsmodus {#defining-configuration-properties-for-a-run-mode}

Eine Sammlung von Werten für Konfigurationseigenschaften, die für einen bestimmten Ausführungsmodus verwendet werden, kann im Repository gespeichert werden.

Der Ausführungsmodus wird durch ein Suffix nach dem Ordnernamen angegeben. Auf diese Weise können Sie alle Konfigurationen in einem Repository speichern. Beispiel:

* `config`

  Wird für alle Ausführungsmodi verwendet

* `config.author`

  Wird für den author-Ausführungsmodus verwendet

* `config.publish`

  Wird für den publish-Ausführungsmodus verwendet

* `config.<run-mode>`

  Wird für die den entsprechenden Ausführungsmodus verwendet. z. B. config

Siehe [OSGi-Konfiguration im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) für weitere Informationen zum Definieren der einzelnen Konfigurationsknoten in diesen Ordnern und zum Erstellen von Konfigurationen für Kombinationen aus mehreren Ausführungsmodi.

>[!NOTE]
>
>Für [Ausführungsmodi der Installation](#installation-run-modes) (beispielsweise author) kann der Ausführungsmodus nach der Installation nicht mehr geändert werden. Änderungen an den einzelnen Konfigurationseigenschaften werden jedoch bei einem Neustart wirksam.

## Definieren von zusätzlichen Bundles, die für einen Ausführungsmodus installiert werden sollen {#defining-additional-bundles-to-be-installed-for-a-run-mode}

Zusätzliche Bundles, die für einen bestimmten Ausführungsmodus installiert werden sollen, können ebenfalls angegeben werden. Für diese Definitionen werden Installationsordner verwendet, die die Bundles enthalten. Auch hier ist der Ausführungsmodus durch ein Präfix gekennzeichnet:

* `install.author`
* `install.publish`

Diese Ordner sich vom Typ `nt:folder` und sollten das entsprechende Bundle enthalten.

## Starten von CQ mit einem bestimmten Ausführungsmodus {#starting-cq-with-a-specific-run-mode}

Wenn Sie Konfigurationen für mehrere Ausführungsmodi definiert haben, müssen Sie definieren, welcher beim Start verwendet werden soll. Es gibt mehrere Methoden, um festzulegen, welcher Ausführungsmodus verwendet werden soll. Die Reihenfolge der Auflösung lautet:

1. [Systemeigenschaften (](#using-a-system-property-in-the-start-script)
1. [](#using-the-sling-properties-file)
1. [](#using-the-r-option)
1. [Erkennung von Dateinamen ](#filename-detection-renaming-the-jar-file)

Wenn Sie einen Anwendungsserver verwenden, können Sie auch [den Ausführungsmodus in web.xml](#defining-the-run-mode-in-web-xml-with-application-server) definieren.

### Verwenden der sling.properties-Datei {#using-the-sling-properties-file}

Mit der Datei `sling.properties` können Sie den erforderlichen Ausführungsmodus definieren:

1. Bearbeiten Sie die Konfigurationsdatei:

   `<cq-installation-dir>/crx-quickstart/conf/sling.properties`

1. Fügen Sie die folgenden Eigenschaften hinzu; dies ist ein Beispiel für „author“:

   `sling.run.modes=author`

### Verwenden der -r-Option {#using-the-r-option}

Beim Ausführen des Schnellstarts können Sie mit der `-r`-Option einen benutzerdefinierten Ausführungsmodus aktivieren. Beispielsweise können Sie folgenden Befehl verwenden, um eine AEM-Instanz mit dem dev-Ausführungsmodus zu starten. ``

```shell
java -jar cq-56-p4545.jar -r dev
```

### Verwenden einer Systemeigenschaft im Startskript {#using-a-system-property-in-the-start-script}

Mit einer Systemeigenschaft im Startskript kann der Ausführungsmodus spezifiziert werden.

* Beispielsweise können Sie Folgendes verwenden, um eine Instanz als Produktionsveröffentlichungsinstanz zu starten, die sich in den USA befindet:

  `-Dsling.run.modes=publish,prod,us`

### Erkennen von Dateinamen – Umbenennen der JAR-Datei {#filename-detection-renaming-the-jar-file}

Die folgenden beiden Installations-Ausführungsmodi können durch die Umbenennung der Installations-JAR-Datei vor der Installation aktiviert werden:

* publish
* author

Die JAR-Datei muss die Namenskonvention verwenden:

`cq5-<run-mode>-p<port-number>`

Beispielsweise können Sie den Ausführungsmodus `publish` festlegen, indem Sie die JAR-Datei folgendermaßen benennen:

`cq5-publish-p4503`

### Definieren des Ausführungsmodus in web.xml (mit Anwendungs-Server) {#defining-the-run-mode-in-web-xml-with-application-server}

Wenn Sie einen Anwendungs-Server verwenden, können Sie auch die Eigenschaft konfigurieren:

`sling.run.modes`

in der Datei:

`WEB-INF/web.xml`

Dies ist die `war`-Datei von AEM. Sie sollte vor der Bereitstellung aktualisiert werden.

Weitere Informationen dazu finden Sie unter [Installieren von AEM mit einem Anwendungsserver](/help/sites-deploying/application-server-install.md).
