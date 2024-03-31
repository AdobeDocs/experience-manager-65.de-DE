---
title: Migrieren von Assets in großen Mengen
description: Beschreibt, wie Sie Assets in  [!DNL Adobe Experience Manager] einfügen, Metadaten anwenden, Ausgabedarstellungen erstellen und diese aktivieren können, um Instanzen zu veröffentlichen.
contentOwner: AG
role: Architect, Admin
feature: Migration,Renditions,Asset Management
exl-id: 184f1645-894a-43c1-85f5-8e0d2d77aa73
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1739'
ht-degree: 100%

---

# Massenmigrierung von Assets {#assets-migration-guide}

Beim Migrieren von Assets nach [!DNL Adobe Experience Manager] sind verschiedene Schritte zu berücksichtigen. Das Extrahieren von Assets und Metadaten aus ihrem aktuellen Speicherort würde den Rahmen dieses Dokuments sprengen, da es zwischen den verschiedenen Implementierungen große Abweichungen gibt. In diesem Dokument wird jedoch beschrieben, wie diese Assets in [!DNL Experience Manager] übernommen, Metadaten zugewiesen, Ausgabedarstellungen generiert und für Veröffentlichungsinstanzen aktiviert werden.

## Voraussetzungen {#prerequisites}

Bevor Sie einen Schritt dieser Methodik tatsächlich ausführen, lesen Sie sich die Anleitungen in den [Tipps zur Assets-Leistungsoptimierung](performance-tuning-guidelines.md) durch und setzen Sie diese um. Viele der Schritte, z. B. die Konfiguration der maximalen Anzahl gleichzeitiger Aufträge, verbessern die Stabilität und Leistung des Servers unter Last erheblich.  Andere Schritte, wie das Konfigurieren eines Dateidatenspeichers, sind nach dem Laden des Systems mit Assets viel schwieriger durchzuführen.

>[!NOTE]
>
>Die folgenden Tools zur Asset-Migration sind nicht Teil von [!DNL Experience Manager] und werden von Adobe nicht unterstützt: 
>
>* Tag Maker von ACS AEM-Tools
>* CSV Asset Importer von ACS AEM-Tools
>* Bulk Workflow Manager von ACS Commons
>* Fast Action Manager von ACS Commons
>* Synthetic Workflow
>
>Hierbei handelt es sich um eine Open-Source-Software. Sie wird mit der [Apache v2-Lizenz](https://adobe-consulting-services.github.io/pages/license.html) abgedeckt. Um eine Frage zu stellen oder ein Problem zu melden, besuchen Sie den Bereich für die entsprechenden [GitHub-Probleme für ACS AEM-Tools](https://github.com/Adobe-Consulting-Services/acs-aem-commons/issues) und [ACS AEM Commons](https://github.com/Adobe-Consulting-Services/acs-aem-tools/issues).

## Migrieren nach [!DNL Experience Manager] {#migrating-to-aem}

Die Migration von Assets nach [!DNL Experience Manager] erfolgt in mehreren Schritten und sollte als stufenweises Verfahren angesehen werden. Die Migrationsphasen lauten wie folgt:

1. Deaktivieren von Workflows.
1. Laden von Tags.
1. Aufnehmen von Assets.
1. Verarbeiten von Ausgabedarstellungen.
1. Aktivieren von Assets.
1. Aktivieren von Workflows.

![chlimage_1-223](assets/chlimage_1-223.png)

### Deaktivieren von Workflows {#disabling-workflows}

Deaktivieren Sie vor der Migration die Starter für den Workflow [!UICONTROL DAM-Update-Asset]. Optimalerweise führen Sie die Workflows nach der Aufnahme aller Assets im System in Stapeln aus. Wenn Sie während der Migration bereits aktiv sind, können Sie diese Aktivitäten so planen, dass sie außerhalb der Arbeitszeiten ausgeführt werden.

### Laden von Tags {#loading-tags}

Womöglich verfügen Sie bereits über eine Tag-Taxonomie für Ihre Bilder. Zwar kann die Anwendung von Tags auf Assets mit Tools wie CSV Asset Importer und durch [!DNL Experience Manager]-Unterstützung für Metadatenprofile automatisiert werden, die Tags müssen dazu aber in das System geladen werden. Mit [Tag Maker von ACS AEM-Tools](https://adobe-consulting-services.github.io/acs-aem-tools/features/tag-maker/index.html) können Sie Tags mithilfe einer in das System geladenen Microsoft Excel-Tabelle auffüllen.

### Aufnehmen von Assets {#ingesting-assets}

Bei der Aufnahme von Assets in das System sind Leistung und Stabilität von großer Bedeutung. Da Sie eine große Menge an Daten in das System laden, sollten Sie sicherstellen, dass das System gut funktioniert, um die erforderliche Zeit zu minimieren und eine Überlastung des Systems zu vermeiden, welche zu einem Systemabsturz führen kann, insbesondere bei Systemen, die bereits in Produktion sind.

Es gibt zwei Ansätze zum Laden der Assets in das System: einen Push-basierten Ansatz mit HTTP oder einen Pull-basierten Ansatz mit den JCR-APIs.

#### Senden über HTTP {#pushing-through-http}

Das Managed Services-Team von Adobe lädt Daten mit einem Tool namens Glutton in Kundenumgebungen. Glutton ist eine kleine Java-Anwendung, die alle Assets von einem Verzeichnis in ein anderes Verzeichnis einer [!DNL Experience Manager]-Bereitstellung lädt. Statt Glutton können Sie auch Tools wie Perl-Skripts zum Posten der Assets in das Repository verwenden.

Der Push-basierte Ansatz mit HTTP hat zwei wesentliche Nachteile:

1. Die Assets müssen über HTTP an den Server übertragen werden. Dies erfordert einen gewissen Mehraufwand und ist zeitaufwendig, wodurch die Dauer der Migration verlängert wird.
1. Wenn Sie über Tags und benutzerdefinierte Metadaten verfügen, die auf die Assets angewendet werden sollen, erfordert dieser Ansatz einen zweiten benutzerdefinierten Prozess, den Sie ausführen müssen, um diese Metadaten nach dem Import auf die Assets anzuwenden.

Der andere Ansatz bei der Aufnahme von Assets besteht darin, Assets aus dem lokalen Dateisystem abzurufen. Wenn Sie jedoch kein externes Laufwerk und keine Netzwerkfreigabe für einen Pull-basierten Ansatz auf dem Server bereitstellen können, ist die Veröffentlichung der Assets über HTTP die beste Option.

#### Abrufen aus dem lokalen Dateisystem {#pulling-from-the-local-filesystem}

[CSV Asset Importer von ACS AEM-Tools](https://adobe-consulting-services.github.io/acs-aem-tools/features/csv-asset-importer/index.html) ruft Assets aus dem Dateisystem sowie Asset-Metadaten aus einer CSV-Datei zwecks Asset-Import ab. Die Experience Manager Asset Manager-API dient zum Importieren der Assets in das System und zum Anwenden der konfigurierten Metadateneigenschaften. Idealerweise werden Assets über eine Netzwerkdateibereitstellung oder über ein externes Laufwerk auf dem Server bereitgestellt.

Da Assets nicht über ein Netzwerk übertragen werden müssen, verbessert sich die Gesamtleistung erheblich, und diese Methode wird im Allgemeinen als die effizienteste Methode zum Laden von Assets in das Repository betrachtet. Da das Tool die Metadatenaufnahme unterstützt, können Sie alle Assets und Metadaten in einem Schritt importieren, anstatt einen zweiten Schritt zu erstellen, um die Metadaten über ein separates Tool anzuwenden.

### Verarbeiten von Ausgabedarstellungen {#processing-renditions}

Nachdem Sie die Assets in das System geladen haben, müssen Sie sie über den Workflow [!UICONTROL DAM-Update-Asset] verarbeiten, um Metadaten zu extrahieren und Ausgabedarstellungen zu generieren. Vor diesem Schritt müssen Sie den Workflow [!UICONTROL DAM-Update-Asset] duplizieren und an Ihre Anforderungen anpassen. Der vorkonfigurierte Workflow enthält möglicherweise eine Reihe von Schritten, die Sie nicht benötigen, so etwa die Dynamic Media PTIFF-Generierung oder die [!DNL InDesign Server]-Integration.

Wenn Sie den Workflow den Anforderungen entsprechend konfiguriert haben, stehen Ihnen zwei Optionen zur Ausführung zur Verfügung:

1. Die einfachste Herangehensweise bietet [Bulk Workflow Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/bulk-workflow-manager.html). Mit diesem Tool können Sie eine Abfrage ausführen und die Ergebnisse der Abfrage mithilfe eines Workflows verarbeiten. Es gibt auch Optionen zum Festlegen von Batch-Größen.
1. Sie können [Fast Action Manager von ACS Commons](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) zusammen mit [Synthetic Workflows](https://adobe-consulting-services.github.io/acs-aem-commons/features/synthetic-workflow.html) verwenden. Dieser Ansatz erfordert zwar viel mehr Mitwirkung, Sie können jedoch den Verwaltungsaufwand für die [!DNL Experience Manager]-Workflow-Engine verringern und gleichzeitig die Verwendung von Server-Ressourcen optimieren. Darüber hinaus steigert der Fast Action Manager die Leistung durch die dynamische Überwachung der Serverressourcen und die Einschränkung der Systemlast. Beispielskripte wurden auf der Seite mit den ACS Commons-Funktionen bereitgestellt.

### Aktivieren von Assets {#activating-assets}

Bei Bereitstellungen mit einer Veröffentlichungsebene müssen Sie die Assets in der Veröffentlichungs-Farm aktivieren. Adobe empfiehlt zwar, mehr als eine Veröffentlichungsinstanz auszuführen, es ist jedoch am effizientesten, alle Assets in einer Veröffentlichungsinstanz zu replizieren und diese Instanz dann zu klonen. Wenn Sie eine große Anzahl von Assets aktivieren, müssen Sie nach dem Auslösen einer Strukturaktivierung möglicherweise eingreifen. Der Grund: Beim Auslösen von Aktivierungen werden Elemente der Sling-Auftrags-/Even-Warteschlange hinzugefügt. Wenn die Größe dieser Warteschlange etwa 40.000 Elemente überschreitet, verlangsamt sich die Verarbeitung drastisch. Wenn die Größe dieser Warteschlange 100.000 Elemente überschreitet, leidet die Systemstabilität.

Um dieses Problem zu umgehen, können Sie den [Fast Action Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/fast-action-manager.html) zur Verwaltung der Asset-Replikation einsetzen. Dies funktioniert ohne die Sling-Warteschlangen. So wird der Overhead verringert und gleichzeitig die Arbeitslast reduziert, sodass eine Server-Überlastung verhindert wird. Ein Beispiel für die Verwendung des FAM zur Verwaltung der Replikation finden Sie auf der Dokumentationsseite der Funktion.

Zu weiteren Optionen zum Übertragen von Assets in die Veröffentlichungsfarm gehören u. a. [vlt-rcp](https://jackrabbit.apache.org/filevault/rcp.html) und [oak-run](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run), die als Tools mit Jackrabbit bereitgestellt werden. Eine andere Möglichkeit ist zudem [Grabbit](https://github.com/TWCable/grabbit), ein Open-Source-Tool für Ihre [!DNL Experience Manager]-Infrastruktur, das schneller sein soll als vlt.

Bei jedem dieser Ansätze besteht der Nachteil darin, dass die Assets in der Autoreninstanz nicht als aktiviert angezeigt werden. Für die Kennzeichnung dieser Assets mit dem korrekten Aktivierungsstatus müssen Sie ein Skript ausführen, um die Assets als aktiviert zu markieren.

>[!NOTE]
>
>Adobe verwaltet oder unterstützt Grabbit nicht.

### Klonen der Veröffentlichungsinstanz {#cloning-publish}

Wenn die Assets aktiviert sind, können Sie Ihre Veröffentlichungsinstanz klonen, um so viele Kopien zu erstellen wie für die Bereitstellung erforderlich. Das Klonen eines Servers ist relativ einfach, es gibt jedoch einige wichtige Schritte, die zu berücksichtigen sind. So klonen Sie die Veröffentlichungsinstanz:

1. Sichern Sie die Quellinstanz und den Datenspeicher.
1. Stellen Sie die Sicherungskopie der Instanz und des Datenspeichers am Zielspeicherort wieder her. Die folgenden Schritte beziehen sich alle auf diese neue Instanz.
1. Führen Sie unter `crx-quickstart/launchpad/felix` eine Dateisystemsuche nach `sling.id` durch. Löschen Sie diese Datei.
1. Suchen und löschen Sie etwaig vorhandene `repository-XXX`-Dateien im Stammverzeichnis.
1. Bearbeiten Sie `crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config` und `crx-quickstart/launchpad/config/org/apache/jackrabbit/oak/plugins/blob/datastore/FileDataStore.config`, um auf den Speicherort des Datenspeichers in der neuen Umgebung zu zeigen.
1. Starten Sie die Umgebung.
1. Aktualisieren Sie die Konfiguration der Replikationsagenten auf den Autoreninstanzen, um auf die richtigen Veröffentlichungsinstanzen zu verweisen, oder die Dispatcher-Flush-Agenten auf der neuen Instanz, um auf die richtigen Dispatcher für die neue Umgebung zu verweisen.

### Aktivieren von Workflows {#enabling-workflows}

Nach abgeschlossener Migration sollten die Starter für die Workflows [!UICONTROL DAM-Update-Asset] neu aktiviert werden, um die Ausgabegenerierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.

## Migrieren zwischen zwei [!DNL Experience Manager]-Bereitstellungen {#migrating-between-aem-instances}

Wenn es auch nicht so häufig vorkommt, müssen dennoch manchmal große Datenmengen zwischen zwei [!DNL Experience Manager]-Bereitstellungen migriert werden, etwa wenn Sie ein [!DNL Experience Manager]- bzw. Hardware-Upgrade durchführen oder auf ein neues Rechenzentrum migrieren, wie bei der AMS-Migration.

In diesem Fall sind die Assets schon mit Metadaten aufgefüllt und Ausgabedarstellungen sind bereits generiert. Sie können sich einfach darauf konzentrieren, Assets von einer Instanz in eine andere zu verschieben. Führen Sie beim Migrieren zwischen zwei [!DNL Experience Manager]-Bereitstellungen die folgenden Schritte aus:

1. Deaktivieren von Workflows: Da Ausgabedarstellungen zusammen mit den Assets migriert werden, sollten Sie die Workflow-Starter für den Workflow [!UICONTROL DAM-Update-Asset] deaktivieren.

1. Migrieren von Tags: Da Sie bereits Tags in die [!DNL Experience Manager]-Quellbereitstellung geladen haben, können Sie diese in einem Inhaltspaket erstellen und das Paket in der Zielinstanz installieren.

1. Migrieren von Assets: Es werden zwei Tools zum Verschieben von Assets von einer [!DNL Experience Manager]-Bereitstellung zur anderen empfohlen:

   * Mit **Vault Remote Copy** (oder vlt rcp) können Sie vlt netzwerkübergreifend einsetzen. Nach Angabe eines Quell- und Zielverzeichnisses lädt vlt alle Repository-Daten von einer Instanz herunter und lädt diese in die andere Instanz. Die Dokumentation zum vlt rcp-Tool finden Sie unter [https://jackrabbit.apache.org/filevault/rcp.html](https://jackrabbit.apache.org/filevault/rcp.html)
   * **Grabbit** ist ein Open-Source-Tool zur Inhaltssynchronisierung, das von Time Warner Cable für die eigene [!DNL Experience Manager]-Implementierung entwickelt wurde. Da hier kontinuierliche Datenströme verwendet werden, ist die Latenz im Vergleich zu vlt rcp niedriger und zwei- bis zehnmal schneller. Grabbit unterstützt außerdem eine Synchronisierung nur von Delta-Inhalten, sodass Änderungen nach einem ersten kompletten Migrationsdurchlauf synchronisiert werden können.

1. Aktivieren von Assets: Befolgen Sie die Anweisungen zum [Aktivieren von Assets](#activating-assets) in der Dokumentation zur Erstmigration nach [!DNL Experience Manager].

1. Klonen der Veröffentlichungsinstanz: Wie bei einer neuen Migration ist es effizienter, eine einzelne Veröffentlichungsinstanz zu laden und zu klonen, als Inhalt auf beiden Knoten zu aktivieren. Siehe [Klonen von Veröffentlichungsinstanzen](#cloning-publish).

1. Aktivieren von Workflows: Aktivieren Sie nach abgeschlossener Migration die Starter für den Workflow [!UICONTROL DAM-Update-Asset] neu, um die Ausgabedarstellungs-Generierung und Metadatenextraktion für die laufende, tagtägliche Systemnutzung zu unterstützen.
