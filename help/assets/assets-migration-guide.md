---
title: Migrieren von Assets zu Adobe Experience Manager-Assets als Massen
description: Beschreibt, wie Sie Assets in AEM einfügen, Metadaten anwenden, Ausgabeformate erstellen und diese aktivieren können, um Instanzen zu veröffentlichen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0ff23556444fcb161b0adf744bb72fdc50322d92

---


# Massenmigrieren von Assets {#assets-migration-guide}

Beim Migrieren von Assets nach AEM sind verschiedene Schritte zu berücksichtigen. Die Extrahierung von Assets und Metadaten aus ihrem aktuellen Speicherort geht über den Rahmen dieses Dokuments hinaus, da es zwischen den verschiedenen Implementierungen große Abweichungen gibt. In diesem Dokument wird jedoch beschrieben, wie diese Assets in AEM übernommen, ihre Metadaten angewendet, Wiedergaben generiert und für Veröffentlichungsinstanzen aktiviert werden können.

## Voraussetzungen {#prerequisites}

Before actually performing any of the steps in this methodology, please review and implement the guidance in [Assets performance tuning tips](performance-tuning-guidelines.md). Viele dieser Schritte, etwa die Konfiguration einer maximalen Anzahl gleichzeitiger Aufträge, führt zu einer deutlich höheren Stabilität und Leistung der Server unter Last. Andere Schritte wie die Konfiguration eines Dateidatenspeichers erweisen sich als wesentlich schwieriger, nachdem Assets in das System geladen wurden.

>[!NOTE]
>
>Die folgenden Asset-Migrationswerkzeuge sind nicht Bestandteil von AEM und werden von Adobe nicht unterstützt:
>
>* Tag Maker von ACS AEM-Tools
>* CSV Asset Importer von ACS AEM-Tools
>* Bulk Workflow Manager von ACS Commons
>* Fast Action Manager von ACS Commons
>* Synthetic Workflow
>
>
Diese Softwareprogramme sind von der [Apache v2-Lizenz](https://adobe-consulting-services.github.io/pages/license.html) abgedeckte Open-Source-Anwendungen. Wenn Sie Fragen haben oder ein Problem melden möchten, besuchen Sie die folgenden Webseiten: [GitHub-Probleme für ACS AEM-Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) und [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Zu AEM migrieren {#migrating-to-aem}

Die Migration von Assets nach AEM setzt die Ausführung verschiedener Schritte voraus und sollte als stufenweises Verfahren angesehen werden. Die Migrationsphasen lauten wie folgt:

1. Workflows deaktivieren
1. Tags laden
1. Assets aufnehmen
1. Wiedergaben verarbeiten
1. Assets aktivieren
1. Workflows aktivieren

![chlimage_1-223](assets/chlimage_1-223.png)

### Disable workflows {#disabling-workflows}

Deaktivieren Sie vor der Migration die Starter für den Workflow „DAM-Update-Asset“. Am besten nehmen Sie zunächst alle Assets in das System auf und führen dann die Workflows stapelweise aus. Wenn Ihr System bereits „live“ ist, während die Migration durchgeführt wird, können Sie diese Aktivitäten so planen, dass sie außerhalb der Arbeitszeiten ausgeführt werden.

### Load tags {#loading-tags}

Womöglich verfügen Sie bereits über eine Tag-Taxonomie für Ihre Bilder. Zwar kann die Anwendung von Tags auf Assets mit Tools wie CSV Asset Importer und durch die AEM-Unterstützung für Metadatenprofile automatisiert werden, die Tags müssen dazu aber in das System geladen werden. The [ACS AEM Tools Tag Maker](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) feature lets you populate tags by using a Microsoft Excel spreadsheet that is loaded into the system.

### Ingest assets {#ingesting-assets}

Leistung und Stabilität sind wichtige Faktoren bei der Aufnahme von Assets in das System. Da Sie eine große Datenmenge in das System laden, sollten Sie eine möglichst optimale Systemleistung sicherstellen, um den erforderlichen Zeitaufwand zu minimieren und eine Überlastung des Systems zu vermeiden, die zu einem Systemabsturz führen kann. Dies gilt insbesondere für Systeme, die bereits produktiv eingesetzt werden.

Es gibt zwei Herangehensweisen zum Laden von Assets in das System: ein Push-basierter Ansatz mit HTTP oder ein Pull-basierter Ansatz mit JCR-APIs.

#### Senden über HTTP {#pushing-through-http}

Das Managed Services-Team von Adobe lädt Daten mit einem Tool namens Glutton in Kundenumgebungen. Glutton ist eine kleine Java-Anwendung, die alle Assets von einem Verzeichnis in ein anderes Verzeichnis einer AEM-Instanz lädt. Statt Glutton können Sie auch Tools wie Perl-Skripts zum Posten der Assets in das Repository verwenden.

Der Ansatz, HTTPS zu durchdrücken, hat zwei Hauptvorteile:

1. Die Assets müssen über HTTP an den Server übertragen werden. Dies ist mit einem gewissen (zeitlichen) Mehraufwand verbunden, sodass die Migration länger dauert.
1. Wenn Tags und benutzerdefinierte Metadaten auf die Assets angewendet werden müssen, erfordert dieser Ansatz einen zweiten benutzerdefinierten Prozess, der zum Anwenden dieser Metadaten auf die Assets durchgeführt werden muss (nach dem Asset-Import).

Der andere Ansatz zur Aufnahme von Assets sieht einen Pull der Assets aus dem lokalen Dateisystem vor. Kann jedoch kein externes Laufwerk bzw. keine Netzwerkfreigabe an den Server angebunden werden, um den Pull-basierten Ansatz durchzuführen, sollten die Assets am besten über HTTP gepostet werden.

#### Fetch from the local filesystem {#pulling-from-the-local-filesystem}

The [ACS AEM Tools CSV Asset Importer](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) pulls assets from the filesystem and asset metadata from a CSV file for the asset import. Die AEM Asset Manager-API dient zum Importieren der Assets in das System und zum Anwenden der konfigurierten Metadateneigenschaften. Im Idealfall werden die Assets über eine Netzwerkdateibereitstellung oder über ein externes Laufwerk auf dem Server bereitgestellt.

Da Assets nicht über ein Netzwerk übertragen werden müssen, verbessert sich die Gesamtleistung erheblich, sodass diese Methode allgemein als effizienteste Möglichkeit zum Laden von Assets in das Repository gilt. Des Weiteren unterstützt das Tool auch die Aufnahme von Metadaten. Daher können Sie alle Assets und Metadaten in einem einzigen Schritt importieren und müssen keinen zusätzlichen zweiten Schritt zum Anwenden der Metadaten durch ein separates Tool erstellen.

### Process renditions {#processing-renditions}

Nachdem Sie die Assets in das System geladen haben, müssen Sie sie über den Workflow „DAM-Update-Asset“ verarbeiten, um Metadaten zu extrahieren und Wiedergaben zu generieren. Vor diesem Schritt müssen Sie den DAM-Update-Asset-Workflow duplizieren und an Ihre Anforderungen anpassen. Der standardmäßig verfügbare Workflow enthält möglicherweise eine Reihe von Schritten, die Sie nicht benötigen, so etwa die Scene7-PTIF-Generierung oder die InDesign Server-Integration.

Wenn Sie den Workflow den Anforderungen entsprechend konfiguriert haben, stehen Ihnen zwei Optionen zur Ausführung zur Verfügung:

1. The simplest approach is [ACS Commons’ Bulk Workflow Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Mit diesem Tool können Sie eine Abfrage ausführen und die Ergebnisse der Abfrage durch einen Workflow verarbeiten. Darüber hinaus gibt es auch Optionen zum Festlegen von Stapelgrößen.
1. You can use the [ACS Commons Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) in concert with [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html). Dieser Ansatz bedeutet zwar eine deutlich stärkere Einbindung, aber Sie können damit den Mehraufwand durch die AEM-Workflow-Engine beseitigen – bei gleichzeitiger Optimierung der Nutzung von Serverressourcen. Zusätzlich sorgt Fast Action Manager für eine weitere Leistungssteigerung durch die dynamische Überwachung von Serverressourcen und Drosselung der Last auf dem System. Beispielskripts sind auf der ACS Commons-Funktionsseite verfügbar.

### Activate assets {#activating-assets}

Bei Bereitstellungen mit einer Veröffentlichungsstufe müssen Sie die Assets für die Veröffentlichungsfarm aktivieren. Zwar empfiehlt Adobe die Ausführung von mehr als einer Veröffentlichungsinstanz, dennoch ist es am effizientesten, alle Assets in einer Veröffentlichungsinstanz zu replizieren und dann diese Instanz zu klonen. Wird eine große Anzahl von Assets nach Auslösen einer Strukturaktivierung aktiviert, müssen Sie ggf. eingreifen. Deshalb: Beim Auslösen von Aktivierungen werden Elemente zur Warteschlange für Sling-Aufträge/Ereignisse hinzugefügt. Bei einer Warteschlangengröße von mehr als ca. 40.000 Elementen wird die Verarbeitung deutlich langsamer. Wenn die Größe dieser Warteschlange die Zahl von 100.000 Elementen übersteigt, wird die Systemstabilität beeinträchtigt.

Um hier Abhilfe zu schaffen, können Sie [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) für die Asset-Verwaltung einsetzen. Dies funktioniert ohne Sling-Warteschlangen und sorgt für weniger Mehraufwand, während der Workload gedrosselt wird, um eine Überlastung des Servers zu vermeiden. Ein Beispiel für die Verwendung von FAM zur Replikationsverwaltung finden Sie auf der Dokumentationsseite für die Funktion.

Other options for getting assets to the publish farm include using [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) or [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), which are provided as tools as part of Jackrabbit. Another option is to use an open-sourced tool for your AEM infrastructure called [Grabbit](https://github.com/TWCable/grabbit), which claims to have faster performance than vlt.

Jeder dieser Ansätze ist dahingehend eingeschränkt, dass die Assets in der Autoreninstanz nicht als aktiviert angezeigt werden. Um diese Assets mit dem korrekten Aktivierungsstatus zu kennzeichnen, müssen Sie ein Skript ausführen, damit die Assets als aktiviert markiert werden.

>[!NOTE]
>
>Adobe bietet weder Wartung noch Unterstützung für Grabbit.

### Clone Publish {#cloning-publish}

Nach Aktivierung der Assets können Sie Ihre Veröffentlichungsinstanz klonen, um die zur Bereitstellung benötigte Anzahl an Kopien zu erstellen. Einen Server zu klonen, ist ein relativ unkomplizierter Vorgang. Dabei müssen jedoch einige wichtige Schritte berücksichtigt werden. So klonen Sie eine Veröffentlichungsinstanz:

1. Sichern Sie die Quellinstanz und den Datenspeicher.
1. Stellen Sie die Sicherung der Instanz und des Datenspeichers am Zielspeicherort wieder her. Die folgenden Schritte beziehen sich allesamt auf diese neue Instanz.
1. Perform a filesystem search under `crx-quickstart/launchpad/felix` for `sling.id`. Löschen Sie diese Datei.
1. Suchen und löschen Sie etwaig vorhandene `repository-XXX`-Dateien im Stammverzeichnis.
1. Bearbeiten `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config` bis zum Speicherort des Datenspeichers in der neuen Umgebung.
1. Starten Sie die Umgebung.
1. Aktualisieren Sie die Konfiguration aller Replikationsagenten auf Autorseite so, dass auf die korrekten Veröffentlichungsinstanzen verwiesen wird, bzw. die Agenten „Dispatcher leeren“ der neuen Instanz so, dass auf die korrekten Dispatcher für die neue Umgebung verwiesen wird.

### Enable workflows {#enabling-workflows}

Nach abgeschlossener Migration sollten die Starter für die Workflows „DAM-Update-Asset“ neu aktiviert werden, um die Wiedergabegenerierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.

## AEM-Bereitstellungen migrieren {#migrating-between-aem-instances}

Wenn es auch nicht so häufig vorkommt, müssen dennoch manchmal große Datenmengen zwischen AEM-Instanzen migriert werden, etwa wenn Sie ein AEM- bzw. Hardwareupgrade durchführen oder auf ein neues Rechenzentrum migrieren, wie bei der AMS-Migration.

In diesem Fall sind die Assets schon mit Metadaten aufgefüllt und Wiedergaben sind bereits generiert. Sie können sich einfach darauf konzentrieren, Assets zwischen Instanzen zu verschieben. Führen Sie beim Migrieren zwischen AEM-Instanzen die folgenden Schritte aus:

1. Arbeitsabläufe deaktivieren:Da Sie Darstellungen zusammen mit unseren Assets migrieren, sollten Sie die Workflow-Starter für DAM Update Asset deaktivieren.

1. Tags migrieren:Da Sie bereits Tags in der AEM-Quellinstanz geladen haben, können Sie sie in einem Inhaltspaket erstellen und das Paket auf der Zielinstanz installieren.

1. Assets migrieren:Es gibt zwei Tools, die zum Verschieben von Assets von einer AEM-Instanz in eine andere empfohlen werden:

   * **Vault Remote Copy** oder vlt rcp ermöglicht die Verwendung von vlt über ein Netzwerk. Nach Angabe eines Quell- und Zielverzeichnisses lädt vlt alle Repositorydaten von einer Instanz herunter und lädt diese in die andere Instanz. Vlt rcp is documented at [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** ist ein Open-Source-Tool zur Inhaltssynchronisierung, das von Time Warner Cable für die eigene AEM-Implementierung entwickelt wurde. Durch die Nutzung kontinuierlicher Datenströme weist das Tool im Vergleich zu vlt rcp eine geringere Latenz auf. Darüber hinaus soll es zwei- bis zehnmal schneller sein als vlt rcp. Grabbit unterstützt zudem die alleinige Synchronisierung von Delta-Inhalten, sodass Änderungen nach erfolgreich abgeschlossener Erstmigration synchronisiert werden.

1. Activate assets: Follow the instructions for [activating assets](#activating-assets) documented for the initial migration to AEM.

1. Veröffentlichung klonen:Wie bei einer neuen Migration ist das Laden einer einzelnen Veröffentlichungsinstanz und das Klonen effizienter als das Aktivieren des Inhalts auf beiden Knoten. Siehe [Klonen von Veröffentlichungsinstanzen](#cloning-publish).

1. Arbeitsabläufe aktivieren:Nachdem Sie die Migration abgeschlossen haben, aktivieren Sie die Starter für die DAM Update Asset-Workflows erneut, um die Generierung und Extraktion von Metadaten für die laufende Systemverwendung zu unterstützen.
