---
title: Migrieren von Assets [!DNL Adobe Experience Manager Assets] zusammen.
description: Describes how to bring assets into [!DNL Adobe Experience Manager], apply metadata, generate renditions, and activate them to publish instances.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '1800'
ht-degree: 66%

---


# Massenmigrieren von Assets {#assets-migration-guide}

When migrating assets into [!DNL Adobe Experience Manager], there are several steps to consider. Extracting assets and metadata out of their current home is outside the scope of this document as it varies widely between implementations, but this document describes how to bring these assets into [!DNL Experience Manager], apply their metadata, generate renditions, and activate them to publish instances.

## Voraussetzungen {#prerequisites}

Before actually performing any of the steps in this methodology, please review and implement the guidance in [Assets performance tuning tips](performance-tuning-guidelines.md). Viele dieser Schritte, etwa die Konfiguration einer maximalen Anzahl gleichzeitiger Aufträge, führt zu einer deutlich höheren Stabilität und Leistung der Server unter Last. Andere Schritte wie die Konfiguration eines Dateidatenspeichers erweisen sich als wesentlich schwieriger, nachdem Assets in das System geladen wurden.

>[!NOTE]
>
>The following asset migration tools are not part of [!DNL Experience Manager] and are not supported by Adobe:
>
>* Tag Maker von ACS AEM-Tools
>* CSV Asset Importer von ACS AEM-Tools
>* Bulk Workflow Manager von ACS Commons
>* Fast Action Manager von ACS Commons
>* Synthetic Workflow
>
>
Hierbei handelt es sich um eine Open-Source-Software. Sie wird mit der [Apache v2-Lizenz](https://adobe-consulting-services.github.io/pages/license.html) abgedeckt. Um eine Frage zu stellen oder ein Problem zu melden, besuchen Sie den Bereich für die entsprechenden [GitHub-Probleme für ACS AEM-Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) und [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrate to [!DNL Experience Manager] {#migrating-to-aem}

Migrating assets to [!DNL Experience Manager] requires several steps and should be viewed as a phased process. Die Migrationsphasen lauten wie folgt:

1. Workflows deaktivieren
1. Laden von Tags.
1. Aufnehmen von Assets.
1. Verarbeiten von Wiedergaben
1. Aktivieren von Assets.
1. Workflows aktivieren

![chlimage_1-223](assets/chlimage_1-223.png)

### Disable workflows {#disabling-workflows}

Before starting your migration, disable your launchers for the [!UICONTROL DAM Update Asset] workflow. Am besten nehmen Sie zunächst alle Assets in das System auf und führen dann die Workflows stapelweise aus. Wenn Ihr System bereits „live“ ist, während die Migration durchgeführt wird, können Sie diese Aktivitäten so planen, dass sie außerhalb der Arbeitszeiten ausgeführt werden.

### Laden von Tags {#loading-tags}

Womöglich verfügen Sie bereits über eine Tag-Taxonomie für Ihre Bilder. While tools like the CSV Asset Importer and [!DNL Experience Manager] support for metadata profiles can automate the process of applying tags to assets, the tags need to be loaded into the system. Mit [Tag Maker von ACS AEM-Tools](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) können Sie Tags mithilfe einer in das System geladenen Microsoft Excel-Tabelle auffüllen.

### Aufnehmen von Assets {#ingesting-assets}

Leistung und Stabilität sind wichtige Faktoren bei der Aufnahme von Assets in das System. Da Sie eine große Datenmenge in das System laden, sollten Sie eine möglichst optimale Systemleistung sicherstellen, um den erforderlichen Zeitaufwand zu minimieren und eine Überlastung des Systems zu vermeiden, die zu einem Systemabsturz führen kann. Dies gilt insbesondere für Systeme, die bereits produktiv eingesetzt werden.

Es gibt zwei Herangehensweisen zum Laden von Assets in das System: ein Push-basierter Ansatz mit HTTP oder ein Pull-basierter Ansatz mit JCR-APIs.

#### Senden über HTTP {#pushing-through-http}

Das Managed Services-Team von Adobe lädt Daten mit einem Tool namens Glutton in Kundenumgebungen. Glutton is a small Java application that loads all assets from one directory into another directory on an [!DNL Experience Manager] instance. Statt Glutton können Sie auch Tools wie Perl-Skripts zum Posten der Assets in das Repository verwenden.

Der Push-basierte Ansatz mit HTTP hat zwei wesentliche Nachteile:

1. Die Assets müssen über HTTP an den Server übertragen werden. Dies ist mit einem gewissen (zeitlichen) Mehraufwand verbunden, sodass die Migration länger dauert.
1. Wenn Tags und benutzerdefinierte Metadaten auf die Assets angewendet werden müssen, erfordert dieser Ansatz einen zweiten benutzerdefinierten Prozess, der zum Anwenden dieser Metadaten auf die Assets durchgeführt werden muss (nach dem Asset-Import).

Der andere Ansatz zur Aufnahme von Assets sieht einen Pull der Assets aus dem lokalen Dateisystem vor. Kann jedoch kein externes Laufwerk bzw. keine Netzwerkfreigabe an den Server angebunden werden, um den Pull-basierten Ansatz durchzuführen, sollten die Assets am besten über HTTP gepostet werden.

#### Fetch from the local filesystem {#pulling-from-the-local-filesystem}

[CSV Asset Importer von ACS AEM-Tools](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) ruft Assets aus dem Dateisystem sowie Asset-Metadaten aus einer CSV-Datei zwecks Asset-Import ab. Die Experience Manager Asset Manager-API wird verwendet, um die Assets in das System zu importieren und die konfigurierten Metadateneigenschaften anzuwenden. Im Idealfall werden die Assets über eine Netzwerkdateibereitstellung oder über ein externes Laufwerk auf dem Server bereitgestellt.

Da Assets nicht über ein Netzwerk übertragen werden müssen, verbessert sich die Gesamtleistung erheblich, sodass diese Methode allgemein als effizienteste Möglichkeit zum Laden von Assets in das Repository gilt. Des Weiteren unterstützt das Tool auch die Aufnahme von Metadaten. Daher können Sie alle Assets und Metadaten in einem einzigen Schritt importieren und müssen keinen zusätzlichen zweiten Schritt zum Anwenden der Metadaten durch ein separates Tool erstellen.

### Verarbeiten von Wiedergaben {#processing-renditions}

After you load the assets into the system, you need to process them through the [!UICONTROL DAM Update Asset] workflow to extract metadata and generate renditions. Before performing this step, you need to duplicate and modify the [!UICONTROL DAM Update Asset] workflow to fit your needs. The out-of-the-box workflow contains many steps that may not necessary for you, such as Scene7 PTIFF generation or [!DNL InDesign Server] integration.

Wenn Sie den Workflow den Anforderungen entsprechend konfiguriert haben, stehen Ihnen zwei Optionen zur Ausführung zur Verfügung:

1. Die einfachste Herangehensweise bietet [Bulk Workflow Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Mit diesem Tool können Sie eine Abfrage ausführen und die Ergebnisse der Abfrage durch einen Workflow verarbeiten. Darüber hinaus gibt es auch Optionen zum Festlegen von Stapelgrößen.
1. Sie können [Fast Action Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) zusammen mit [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html) verwenden. While this approach is much more involved, it lets you remove the overhead of the [!DNL Experience Manager] workflow engine while optimizing the use of server resources. Darüber hinaus steigert der Fast Action Manager die Leistung durch die dynamische Überwachung der Serverressourcen und die Einschränkung der Systemlast. Beispielskripte wurden auf der Seite mit den ACS Commons-Funktionen bereitgestellt.

### Aktivieren von Assets {#activating-assets}

Bei Bereitstellungen mit einer Veröffentlichungsstufe müssen Sie die Assets für die Veröffentlichungsfarm aktivieren. Zwar empfiehlt Adobe die Ausführung von mehr als einer Veröffentlichungsinstanz, dennoch ist es am effizientesten, alle Assets in einer Veröffentlichungsinstanz zu replizieren und dann diese Instanz zu klonen. Wird eine große Anzahl von Assets nach Auslösen einer Strukturaktivierung aktiviert, müssen Sie ggf. eingreifen. Deshalb: Beim Auslösen von Aktivierungen werden Elemente zu den Sling-Aufträgen/Ereignisschlangen hinzugefügt. Bei einer Warteschlangengröße von mehr als ca. 40.000 Elementen wird die Verarbeitung deutlich langsamer. Wenn die Größe dieser Warteschlange die Zahl von 100.000 Elementen übersteigt, wird die Systemstabilität beeinträchtigt.

Um hier Abhilfe zu schaffen, können Sie [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) für die Asset-Verwaltung einsetzen. Dies funktioniert ohne Sling-Warteschlangen und sorgt für weniger Mehraufwand, während der Workload gedrosselt wird, um eine Überlastung des Servers zu vermeiden. Ein Beispiel für die Verwendung von FAM zur Replikationsverwaltung finden Sie auf der Dokumentationsseite für die Funktion.

Zu weiteren Optionen zum Übertragen von Assets in die Veröffentlichungsfarm gehören u. a. [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) und [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), die als Tools mit Jackrabbit bereitgestellt werden. Another option is to use an open-sourced tool for your [!DNL Experience Manager] infrastructure called [Grabbit](https://github.com/TWCable/grabbit), which claims to have faster performance than vlt.

Jeder dieser Ansätze ist dahingehend eingeschränkt, dass die Assets in der Autoreninstanz nicht als aktiviert angezeigt werden. Um diese Assets mit dem korrekten Aktivierungsstatus zu kennzeichnen, müssen Sie ein Skript ausführen, damit die Assets als aktiviert markiert werden.

>[!NOTE]
>
>Adobe bietet weder Wartung noch Unterstützung für Grabbit.

### Clone Publish {#cloning-publish}

Nach Aktivierung der Assets können Sie Ihre Veröffentlichungsinstanz klonen, um die zur Bereitstellung benötigte Anzahl an Kopien zu erstellen. Einen Server zu klonen, ist ein relativ unkomplizierter Vorgang. Dabei müssen jedoch einige wichtige Schritte berücksichtigt werden. So klonen Sie eine Veröffentlichungsinstanz:

1. Sichern Sie die Quellinstanz und den Datenspeicher.
1. Stellen Sie die Sicherung der Instanz und des Datenspeichers am Zielspeicherort wieder her. Die folgenden Schritte beziehen sich allesamt auf diese neue Instanz.
1. Führen Sie unter `crx-quickstart/launchpad/felix` eine Dateisystemsuche nach `sling.id` durch. Löschen Sie diese Datei.
1. Suchen und löschen Sie etwaig vorhandene `repository-XXX`-Dateien im Stammverzeichnis.
1. Bearbeiten Sie `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`, um auf den Speicherort des Datenspeichers in der neuen Umgebung zu zeigen.
1. Starten Sie die Umgebung.
1. Aktualisieren Sie die Konfiguration aller Replikationsagenten auf Autorseite so, dass auf die korrekten Veröffentlichungsinstanzen verwiesen wird, bzw. die Agenten „Dispatcher leeren“ der neuen Instanz so, dass auf die korrekten Dispatcher für die neue Umgebung verwiesen wird.

### Enable workflows {#enabling-workflows}

Once we have completed migration, the launchers for the [!UICONTROL DAM Update Asset] workflows should be re-enabled to support rendition generation and metadata extraction for ongoing day-to-day system usage.

## Migrieren zwischen [!DNL Experience Manager] Bereitstellungen {#migrating-between-aem-instances}

While not nearly as common, sometimes you need to migrate large amounts of data from one [!DNL Experience Manager] instance to another; for example, when you perform an [!DNL Experience Manager] upgrade, upgrade your hardware, or migrate to a new datacenter, such as with an AMS migration.

In diesem Fall sind die Assets schon mit Metadaten aufgefüllt und Wiedergaben sind bereits generiert. Sie können sich einfach darauf konzentrieren, Assets zwischen Instanzen zu verschieben. When migrating between [!DNL Experience Manager] instances, you perform the following steps:

1. Disable workflows: Because you are migrating renditions along with our assets, you want to disable the workflow launchers for [!UICONTROL DAM Update Asset] workflow.

1. Migrate tags: Because you already have tags loaded in the source [!DNL Experience Manager] instance, you can build them in a content package and install the package on the target instance.

1. Migrate assets: There are two tools that are recommended for moving assets from one [!DNL Experience Manager] instance to another:

   * **Vault Remote Copy** oder vlt rcp ermöglicht die Verwendung von vlt über ein Netzwerk. Nach Angabe eines Quell- und Zielverzeichnisses lädt vlt alle Repositorydaten von einer Instanz herunter und lädt diese in die andere Instanz. Die Dokumentation zum vlt rcp-Tool finden Sie unter [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** ist ein Open-Source-Tool zur Synchronisierung von Inhalten, das von Time Warner Cable für ihre [!DNL Experience Manager] Implementierung entwickelt wurde. Durch die Nutzung kontinuierlicher Datenströme weist das Tool im Vergleich zu vlt rcp eine geringere Latenz auf. Darüber hinaus soll es zwei- bis zehnmal schneller sein als vlt rcp. Grabbit unterstützt zudem die alleinige Synchronisierung von Delta-Inhalten, sodass Änderungen nach erfolgreich abgeschlossener Erstmigration synchronisiert werden.

1. Activate assets: Follow the instructions for [activating assets](#activating-assets) documented for the initial migration to [!DNL Experience Manager].

1. Veröffentlichung klonen: Wie bei einer neuen Migration ist das Laden einer einzelnen Veröffentlichungsinstanz und das Klonen effizienter als das Aktivieren des Inhalts auf beiden Knoten. Siehe [Klonen von Veröffentlichungsinstanzen](#cloning-publish).

1. Enable workflows: After you have completed migration, re-enable the launchers for the [!UICONTROL DAM Update Asset] workflow to support rendition generation and metadata extraction for ongoing day-to-day system usage.
