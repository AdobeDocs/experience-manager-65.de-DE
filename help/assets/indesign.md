---
title: Integration von [!DNL Assets] mit [!DNL InDesign Server]
description: Informationen zur Integration [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe InDesign Server].
contentOwner: AG
role: Admin
feature: Publishing
exl-id: 5ba020a3-c36c-402b-a11b-d6b0426b03bf
source-git-commit: 67e145e250bbe386168ab2c0f8967f91aa9d8a36
workflow-type: tm+mt
source-wordcount: '1591'
ht-degree: 36%

---

# Integration von [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] den:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist [!DNL Experience Manager] -Instanz, die mit einem Proxy Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, und andere [!DNL Experience Manager] Instanzen, um die Ergebnisse bereitzustellen.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.
Diese können eine Vielzahl von Aufgaben abdecken; zum Beispiel mithilfe eines [!DNL InDesign Server] , um Dateien zu verarbeiten.

Zum vollständigen Hochladen von Dateien in [!DNL Experience Manager Assets] , die Sie mit [!DNL Adobe InDesign] ein Proxy verwendet wird. Dies verwendet einen Proxy Worker für die Kommunikation mit dem [!DNL Adobe InDesign Server], wobei [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) werden ausgeführt, um Metadaten zu extrahieren und verschiedene Ausgabeformate für [!DNL Experience Manager Assets]. Der Proxy Worker ermöglicht die bidirektionale Kommunikation zwischen der [!DNL InDesign Server] und [!DNL Experience Manager] Instanzen in einer Cloud-Konfiguration.

>[!NOTE]
>
>[!DNL Adobe InDesign] wird als zwei separate Angebote angeboten. [Adobe InDesign](https://www.adobe.com/de/products/indesign.html) -Desktop-Programm, das zum Entwerfen von Seitenlayouts für den Druck und die digitale Distribution verwendet wird. [Adobe InDesign Server](https://www.adobe.com/de/products/indesignserver.html) ermöglicht die programmgesteuerte Erstellung automatisierter Dokumente basierend auf dem, was Sie mit [!DNL InDesign]. Es fungiert als Dienst, der eine Schnittstelle zu seiner [ExtendScript](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) engine.Die Skripte werden in [!DNL ExtendScript], der [!DNL JavaScript]. Informationen zu [!DNL InDesign] Skripte siehe [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Funktionsweise der Extraktion {#how-the-extraction-works}

Die [!DNL Adobe InDesign Server] kann mit [!DNL Experience Manager Assets] sodass INDD-Dateien, die mit [!DNL InDesign] können hochgeladen, Ausgabeformate generiert, alle Medien extrahiert (z. B. Video) und als Assets gespeichert werden:

>[!NOTE]
>
>Frühere Versionen von [!DNL Experience Manager] konnte XMP und die Miniaturansicht extrahieren, jetzt können alle Medien extrahiert werden.

1. Laden Sie Ihre INDD-Datei in hoch. [!DNL Experience Manager Assets].
1. Ein Framework sendet Befehlsskripte an die [!DNL InDesign Server] über SOAP (Simple Object Access Protocol).
Dieses Befehlsskript führt folgende Aktionen aus:

   * Ruft die INDD-Datei ab.
   * Ausführen [!DNL InDesign Server] Befehle:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.
   * Posten Sie die resultierenden Dateien zurück in [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML ist ein XML-basiertes Format, das alle Inhalte der [!DNL InDesign] -Datei. Sie wird als komprimiertes Paket gespeichert, indem [ZIP](https://www.techterms.com/definition/zip) Komprimierung. Weitere Informationen finden Sie unter [InDesign Interchange Formats INX und IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).

   >[!CAUTION]
   >
   >Wenn die Variable [!DNL InDesign Server] nicht installiert oder nicht konfiguriert ist, können Sie dennoch eine INDD-Datei in [!DNL Experience Manager]. Allerdings sind die generierten Ausgabeformate auf PNG und JPEG beschränkt und Sie können keine HTML- oder IDML-Dateien sowie keine Seitenausgabe generieren.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in [!DNL Experience Manager Assets].
   * Alle Ausgabedarstellungen werden in [!DNL Experience Manager Assets]im Asset selbst.

## Integrieren Sie die [!DNL InDesign Server] mit Experience Manager {#integrating-the-indesign-server-with-aem}

So integrieren Sie die [!DNL InDesign Server] zur Verwendung mit [!DNL Experience Manager Assets] und nach der Konfiguration Ihres Proxys müssen Sie:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Falls erforderlich, [Konfigurieren des Experience Manager Assets-Workflows](#configuring-the-aem-assets-workflow).
Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.
1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installieren Sie die [!DNL InDesign Server] {#installing-the-indesign-server}

So installieren und starten Sie die [!DNL InDesign Server] zur Verwendung mit [!DNL Experience Manager]:

1. Laden Sie die [!DNL InDesign Server].

1. Bei Bedarf können Sie die Konfiguration Ihrer [!DNL InDesign Server] -Instanz.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Konfigurieren Sie die [!DNL Experience Manager Assets] Workflow {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager Assets] verfügt über einen vorkonfigurierten Workflow **[!UICONTROL DAM-Update-Asset]**, der mehrere Prozessschritte speziell für [!DNL InDesign]:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten  ](#page-extraction)

Dieser Workflow wird mit Standardwerten konfiguriert, die für Ihr Setup in den verschiedenen Autoreninstanzen angepasst werden können. (Dies ist ein Standard-Workflow. Deshalb finden Sie weitere Information unter [Bearbeiten eines Workflows](/help/sites-developing/workflows-models.md#configuring-a-workflow-step).) Wenn Sie die Standardwerte (einschließlich SOAP-Port) verwenden, ist keine Konfiguration erforderlich.

Nach dem Setup wird das [!DNL InDesign] Dateien in [!DNL Experience Manager Assets] (nach einer der üblichen Methoden) Trigger des Workflows, um das Asset zu verarbeiten und die verschiedenen Ausgabedarstellungen vorzubereiten. Testen Sie Ihre Konfiguration durch Hochladen einer INDD-Datei in [!DNL Experience Manager Assets] , um zu bestätigen, dass Sie die verschiedenen Ausgabedarstellungen sehen, die von IDS unter erstellt wurden. `<*your_asset*>.indd/Renditions`

#### Medienextraktion {#media-extraction}

Dieser Schritt steuert die Extrahierung von Medien aus der INDD-Datei.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Medien]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek**: Dies ist eine einfache HTTP-GET/Post-Methodenbibliothek, die von anderen Skripten benötigt wird.

* **Skripte erweitern**: Hier können Sie unterschiedliche Skriptkombinationen angeben. Wenn Sie möchten, dass Ihre eigenen Skripte auf der [!DNL InDesign Server]speichern Sie die Skripte unter `/apps/settings/dam/indesign/scripts`.

<!-- TBD: Hiding this link since ADC is not available anymore. 
For information about [!DNL Adobe InDesign] scripts, see [InDesign developer documentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
-->

>[!CAUTION]
>
>Ändern Sie nicht die ExtendScript-Bibliothek. Diese Bibliothek bietet die HTTP-Funktionen, die für die Kommunikation mit Sling erforderlich sind. Diese Einstellung gibt die Bibliothek an, die an die [!DNL InDesign Server] zur Verwendung dort.

Die `ThumbnailExport.jsx` Skript, das vom Workflow-Schritt &quot;Extrahierung von Medien&quot;ausgeführt wird, generiert eine Miniaturansicht im JPG-Format. Diese Ausgabedarstellung wird vom Workflow-Schritt &quot;Miniaturansichten verarbeiten&quot;verwendet, um die für [!DNL Experience Manager].

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Standardwerte nicht entfernen, da sie von der [!DNL Experience Manager Assets] -Schnittstelle. Schließlich entfernt der Workflow-Schritt Bildvorschau-Wiedergabe löschen die JPG-Miniaturansicht, da sie nicht mehr benötigt wird.

#### Seitenextraktion {#page-extraction}

Dadurch wird eine [!DNL Experience Manager] aus den extrahierten Elementen. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungshandlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Seiten]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Handler zur Seitenextrahierung**: Wählen Sie in der Popup-Liste den Handler aus, den Sie verwenden möchten. Ein Extrahierungs-Handler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API). In einem Standard [!DNL Experience Manager] -Installation ist Folgendes verfügbar:
   * IDML-Export-Extraktionshandbuch: Bearbeitet die `IDML` Ausgabedarstellung, die im Schritt MediaExtract generiert wurde.

* **Seitenname**: Geben Sie den Namen an, den Sie der resultierenden Seite zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel**: Geben Sie den Titel an, den Sie der resultierenden Seite zuweisen möchten.

* **Stammverzeichnis der Seite**: Der Pfad zum Stammverzeichnis der resultierenden Seite. Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage**: Die Vorlage, die beim Generieren der resultierenden Seite verwendet werden soll.

* **Seitendesign**: Der Seitenentwurf, der beim Generieren der resultierenden Seite verwendet werden soll.

### Proxy Worker konfigurieren für [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole im linken Bereich den Eintrag **[!UICONTROL Cloud-Service-Konfigurationen]**. Anschließend erweitern Sie den Eintrag **[!UICONTROL Cloud-Proxy-Konfiguration]**.

1. Doppelklicken Sie auf den **[!UICONTROL IDS-Worker]**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-Pool**
Die SOAP-Endpunkte, die für die Kommunikation mit der [!DNL InDesign Server]. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf „OK“.

### Konfigurieren von Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Wenn die Variable [!DNL InDesign Server] und [!DNL Experience Manager] sich auf verschiedenen Hosts befinden oder eine oder beide dieser Anwendungen nicht an Standardanschlüssen funktionieren, konfigurieren Sie [!UICONTROL Day CQ Link Externalizer] , um den Hostnamen, Port und Inhaltspfad für die [!DNL InDesign Server].

1. Zugriff auf die Webkonsole unter `https://[aem_server]:[port]/system/console/configMgr`.
1. Suchen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]**. Klicken **[!UICONTROL Bearbeiten]** zu öffnen.
1. Mithilfe der Einstellungen von Link Externalizer können Sie absolute URLs für die [!DNL Experience Manager] und für [!DNL InDesign Server]. Verwendung **[!UICONTROL Domänen]** -Feld zum Angeben des Hostnamens für [!DNL Adobe InDesign Server]. Klicken Sie auf **Speichern**.

   Verwenden Sie in absoluten URLs `localhost` als Hostnamen für Ihre lokale (Autoren-) Instanz und Hostname oder IP-Adresse für die Veröffentlichungsinstanz, wie in der folgenden Abbildung dargestellt.

   ![Externalizer-Einstellung für Link](assets/link-externalizer-config.png)

### Aktivieren der parallelen Auftragsverarbeitung für [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren. Bestimmen Sie die maximale Anzahl paralleler Aufträge (`x`) [!DNL InDesign Server] kann verarbeiten:

* Auf einem einzigen Multiprozessorcomputer wird die maximale Anzahl paralleler Aufträge (`x`), die [!DNL InDesign Server] kann verarbeiten ist eine weniger als die Anzahl der Prozessoren, die IDS ausführen.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie von der Gesamtanzahl der verfügbaren Prozessoren (auf allen Computern) die Gesamtanzahl der Computer abziehen.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **[!UICONTROL Konfigurationen]** der Felix-Konsole. Beispiel:   `https://[aem_server]:[port]/system/console/configMgr`.

1. Wählen Sie die IDS-Verarbeitungsschlange unter `Apache Sling Job Queue Configuration`.

1. Satz:

   * **Typ** - `Parallel`
   * **Maximal parallel ausführbare Aufträge** –`<*x*>` (Berechnung siehe oben)

1. Speichern Sie diese Änderungen.
1. Um die Unterstützung für mehrere Sitzungen für Adobe CS6 und höher zu aktivieren, überprüfen Sie `enable.multisession.name` Kontrollkästchen, unter `com.day.cq.dam.ids.impl.IDSJobProcessor.name` Konfiguration.
1. Erstellen Sie einen [Pool von`x` IDS-Workern, indem Sie SOAP-Endpunkte zur IDS-Worker-Konfiguration](#configuring-the-proxy-worker-for-indesign-server) hinzufügen.

   Wenn mehrere Computer ausgeführt werden [!DNL InDesign Server], fügen Sie SOAP-Endpunkte (Anzahl der Prozessoren pro Computer -1) für jeden Computer hinzu.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wenn Sie mit einem Pool von Mitarbeitern arbeiten, können Sie die Blockierungsliste von IDS-Arbeitern aktivieren.
>
>Aktivieren Sie dazu die **[!UICONTROL enable.retry.name]** Kontrollkästchen unter dem `com.day.cq.dam.ids.impl.IDSJobProcessor.name` -Konfiguration, die Wiederholungen von IDS-Aufträgen ermöglicht.
>
>Außerdem wird im `com.day.cq.dam.ids.impl.IDSPoolImpl.name` -Konfiguration festlegen, legen Sie einen positiven Wert für `max.errors.to.blacklist` -Parameter, der die Anzahl der Auftragswiederholungen bestimmt, bevor ein IDS aus der Auftrags-Handler-Liste ausgeschlossen wird.
>
>Standardmäßig nach dem konfigurierbaren (`retry.interval.to.whitelist.name`) Zeit in Minuten, in der der IDS-Worker erneut validiert wird. Wenn der Worker online gefunden wird, wird er aus der Blockierungsliste entfernt.

## Aktivieren der Unterstützung für [!DNL InDesign Server] 10.0 oder höher {#enabling-support-for-indesign-server-or-later}

Für [!DNL InDesign Server] Führen Sie die folgenden Schritte aus, um die Unterstützung für mehrere Sitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager über Ihre [!DNL Experience Manager Assets] instance `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Aktivieren Sie die Option **[!UICONTROL ids.cc.enable]** und klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Für [!DNL InDesign Server] Integration mit [!DNL Experience Manager Assets]verwenden Sie einen Multicore-Prozessor, da die für die Integration erforderliche Sitzungsunterstützungsfunktion auf einzelnen Kernsystemen nicht unterstützt wird.

## Konfigurieren [!DNL Experience Manager] Anmeldeinformationen {#configure-aem-credentials}

Sie können die standardmäßigen Administratorberechtigungen (Benutzername und Kennwort) für den Zugriff auf die [!DNL InDesign Server] von [!DNL Experience Manager] Implementierung ohne Unterbrechung der Integration mit der [!DNL InDesign Server].

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie in diesem Dialogfeld den neuen Benutzernamen und das Kennwort ein.
1. Speichern Sie die Anmeldedaten.

>[!MORELIKETHIS]
>
>* [Über Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)

