---
title: Integrieren [!DNL Assets] mit [!DNL InDesign Server]
description: Erfahren Sie, wie Sie  [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe InDesign Server] integrieren.
contentOwner: AG
role: Administrator
feature: Publishing
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 37%

---


# [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server} integrieren

[!DNL Adobe Experience Manager Assets] den:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist eine [!DNL Experience Manager]-Instanz, die mit einem Proxy-Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, und andere [!DNL Experience Manager]-Instanzen, um die Ergebnisse zu liefern.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.
Diese können eine Vielzahl von Aufgaben abdecken; zum Beispiel mit einem [!DNL InDesign Server] zur Verarbeitung von Dateien.

Um Dateien vollständig in [!DNL Experience Manager Assets] hochzuladen, die Sie mit [!DNL Adobe InDesign] erstellt haben, wird ein Proxy verwendet. Dabei wird ein Proxy-Worker verwendet, um mit dem [!DNL Adobe InDesign Server] zu kommunizieren, wobei [Skripte](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) ausgeführt werden, um Metadaten zu extrahieren und verschiedene Darstellungen für [!DNL Experience Manager Assets] zu generieren. Der Proxy-Worker aktiviert die bidirektionale Kommunikation zwischen den Instanzen [!DNL InDesign Server] und [!DNL Experience Manager] in einer Cloud-Konfiguration.

>[!NOTE]
>
>[!DNL Adobe InDesign] wird als zwei separate Angebote angeboten. [Adobe ](https://www.adobe.com/de/products/indesign.html) InDesign-Desktop-App, die zum Entwerfen von Seitenlayouts für die Druck- und digitale Verteilung verwendet wird. [Mit Adobe InDesign ](https://www.adobe.com/de/products/indesignserver.html) Server können Sie automatisierte Dokumente programmgesteuert erstellen, basierend auf dem, was Sie mit erstellt haben  [!DNL InDesign]. Es dient als Dienst, der eine Schnittstelle zu seiner [ExtendScript](https://www.adobe.com/devnet/scripting.html)-Engine anbietet. Die Skripte werden in [!DNL ExtendScript] geschrieben, was [!DNL JavaScript] ähnlich ist. Weitere Informationen zu [!DNL InDesign]-Skripten finden Sie unter [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Funktionsweise der Extraktion {#how-the-extraction-works}

Das [!DNL Adobe InDesign Server] kann mit [!DNL Experience Manager Assets] integriert werden, sodass mit [!DNL InDesign] erstellte INDD-Dateien hochgeladen, Darstellungen generiert, alle Medien extrahiert (z. B. Video) und als Assets gespeichert werden können:

>[!NOTE]
>
>Frühere Versionen von [!DNL Experience Manager] konnten XMP und die Miniaturansicht extrahieren, jetzt können alle Medien extrahiert werden.

1. Laden Sie Ihre INDD-Datei auf [!DNL Experience Manager Assets] hoch.
1. Ein Framework sendet Befehlsskripte über SOAP (Simple Object Access Protocol) an das [!DNL InDesign Server].
Dieses Befehlsskript führt folgende Aktionen aus:

   * Ruft die INDD-Datei ab.
   * Führen Sie die Befehle [!DNL InDesign Server] aus:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.
   * Posten Sie die resultierenden Dateien zurück zu [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML ist ein XML-basiertes Format, das den gesamten Inhalt der Datei [!DNL InDesign] rendert. Es wird als komprimiertes Paket unter Verwendung der Komprimierung [ZIP](https://www.techterms.com/definition/zip) gespeichert. Weitere Informationen finden Sie unter [InDesign Interchange Formats INX und IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).

   >[!CAUTION]
   >
   >Wenn [!DNL InDesign Server] nicht installiert oder nicht konfiguriert ist, können Sie dennoch eine INDD-Datei in [!DNL Experience Manager] hochladen. Allerdings sind die generierten Ausgabeformate auf PNG und JPEG beschränkt und Sie können keine HTML- oder IDML-Dateien sowie keine Seitenausgabe generieren.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in [!DNL Experience Manager Assets] gespeichert.
   * Alle Darstellungen werden in [!DNL Experience Manager Assets] im Asset gespeichert.

## [!DNL InDesign Server] mit Experience Manager {#integrating-the-indesign-server-with-aem} integrieren

Um [!DNL InDesign Server] für die Verwendung mit [!DNL Experience Manager Assets] und nach der Konfiguration Ihres Proxys zu integrieren, müssen Sie:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Konfigurieren Sie ggf. den Experience Manager Assets Workflow](#configuring-the-aem-assets-workflow).
[
Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.
1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### [!DNL InDesign Server] {#installing-the-indesign-server} installieren

So installieren und Beginn von [!DNL InDesign Server] für die Verwendung mit [!DNL Experience Manager]:

1. Laden Sie [!DNL InDesign Server] herunter und installieren Sie es.

1. Bei Bedarf können Sie die Konfiguration der [!DNL InDesign Server]-Instanz anpassen.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### [!DNL Experience Manager Assets]-Arbeitsablauf {#configuring-the-aem-assets-workflow} konfigurieren

[!DNL Experience Manager Assets] verfügt über einen vorkonfigurierten Workflow  **[!UICONTROL DAM Update Asset]**, der mehrere Prozessschritte speziell für  [!DNL InDesign]folgende Aufgaben umfasst:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten  ](#page-extraction)

Dieser Workflow wird mit Standardwerten konfiguriert, die für Ihr Setup in den verschiedenen Autoreninstanzen angepasst werden können. (Dies ist ein Standard-Workflow. Deshalb finden Sie weitere Information unter [Bearbeiten eines Workflows](/help/sites-developing/workflows-models.md#configuring-a-workflow-step).) Wenn Sie die Standardwerte (einschließlich SOAP-Port) verwenden, ist keine Konfiguration erforderlich.

Nach dem Setup wird beim Hochladen von [!DNL InDesign]-Dateien in [!DNL Experience Manager Assets] (mit einer der üblichen Methoden) der Arbeitsablauf zum Verarbeiten des Assets und Vorbereiten der verschiedenen Darstellungen Trigger. Testen Sie Ihre Konfiguration, indem Sie eine INDD-Datei in [!DNL Experience Manager Assets] hochladen, um sicherzustellen, dass Sie die verschiedenen Darstellungen sehen, die von IDS unter `<*your_asset*>.indd/Renditions` erstellt wurden.

#### Media-Extraktion {#media-extraction}

Dieser Schritt steuert die Extrahierung von Medien aus der INDD-Datei.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Medien]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek**: Dies ist eine einfache HTTP get/post-Methodenbibliothek, die von den anderen Skripten benötigt wird.

* **Skripten** erweitern: Hier können Sie verschiedene Skriptkombinationen angeben. Wenn Sie möchten, dass Ihre eigenen Skripten auf dem [!DNL InDesign Server] ausgeführt werden, speichern Sie die Skripte unter `/apps/settings/dam/indesign/scripts`.

Weitere Informationen zu [!DNL Adobe InDesign]-Skripten finden Sie in der [InDesign-Entwicklerdokumentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)

>[!CAUTION]
>
>Ändern Sie nicht die ExtendScript-Bibliothek. Diese Bibliothek bietet die HTTP-Funktionen, die für die Kommunikation mit Sling erforderlich sind. Diese Einstellung gibt die Bibliothek an, die zur Verwendung an das [!DNL InDesign Server] gesendet werden soll.

Das vom Workflow-Schritt für die Media-Extraktion ausgeführte `ThumbnailExport.jsx`-Skript generiert eine Miniaturansicht im JPG-Format. Diese Darstellung wird vom Arbeitsablaufschritt &quot;Prozessminiaturen&quot;verwendet, um die für [!DNL Experience Manager] erforderlichen statischen Darstellungen zu generieren.

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Standardwerte nicht entfernen, da sie für die [!DNL Experience Manager Assets]-Schnittstelle erforderlich sind. Im Arbeitsablauf zum Löschen der Bildwiedergabe wird die JPG-Miniaturdarstellung entfernt, da sie nicht mehr benötigt wird.

#### Extraktion der Seite {#page-extraction}

Dadurch wird eine [!DNL Experience Manager]-Seite aus den extrahierten Elementen erstellt. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungshandlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Seiten]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Seiten-Extraktionen-Handler**: Wählen Sie in der Popup-Liste den zu verwendenden Handler aus. Ein Extrahierungs-Handler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API). Bei einer Standardinstallation von [!DNL Experience Manager] ist Folgendes verfügbar:
   * IDML Export Extraktion Handle: Wird für die im MediaExtract-Schritt generierte Darstellung `IDML` ausgeführt.

* **Seitenname**: Geben Sie den Namen an, den Sie der resultierenden Seite zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel**: Geben Sie den Titel an, den Sie der resultierenden Seite zuweisen möchten.

* **Seitenstammpfad**: Der Pfad zum Stammverzeichnis der resultierenden Seite. Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage**: Die Vorlage, die beim Generieren der resultierenden Seite verwendet wird.

* **Seitendesign**: Der Seitenentwurf, der beim Generieren der resultierenden Seite verwendet wird.

### Proxy-Worker für [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server} konfigurieren

>[!NOTE]
>
>Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole im linken Bereich den Eintrag **[!UICONTROL Cloud-Service-Konfigurationen]**. Anschließend erweitern Sie den Eintrag **[!UICONTROL Cloud-Proxy-Konfiguration]**.

1. Doppelklicken Sie auf den **[!UICONTROL IDS-Worker]**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS**
PoolDer/die SOAP-Endpunkt/e, der/die für die Kommunikation mit dem  [!DNL InDesign Server]Pool verwendet werden soll/werden. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf „OK“.

### Day CQ Link Externalizer {#configuring-day-cq-link-externalizer} konfigurieren

Wenn sich [!DNL InDesign Server] und [!DNL Experience Manager] auf verschiedenen Hosts befinden oder eine oder beide Anwendungen nicht an Standardanschlüssen funktionieren, konfigurieren Sie [!UICONTROL Day CQ Link Externalizer], um Hostnamen, Anschluss und Inhaltspfad für [!DNL InDesign Server] festzulegen.

1. Rufen Sie die Web-Konsole unter `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Suchen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]**. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um zu öffnen.
1. Mithilfe der Einstellungen für Link-Externalisierer können Sie absolute URLs für die [!DNL Experience Manager]-Bereitstellung und für [!DNL InDesign Server] erstellen. Verwenden Sie das Feld **[!UICONTROL Domänen]**, um den Hostnamen und den Kontextpfad für [!DNL Adobe InDesign Server] anzugeben. Klicken Sie auf **Speichern**.

   ![Einstellung für Link-Externalisierer](assets/link-externalizer-config.png)

### Aktivieren der parallelen Auftragsverarbeitung für [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren. Legen Sie die maximale Anzahl paralleler Aufträge (`x`) fest, die ein [!DNL InDesign Server] verarbeiten kann:

* Auf einem einzelnen Multiprozessorcomputer ist die maximale Anzahl paralleler Aufträge (`x`), die ein [!DNL InDesign Server] verarbeiten kann, eine weniger als die Anzahl der Prozessoren, die IDS ausführen.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie von der Gesamtanzahl der verfügbaren Prozessoren (auf allen Computern) die Gesamtanzahl der Computer abziehen.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **[!UICONTROL Konfigurationen]** der Felix-Konsole. Beispiel:   `https://[aem_server]:[port]/system/console/configMgr`.

1. Wählen Sie die IDS-Verarbeitungsschlange unter `Apache Sling Job Queue Configuration`.

1. Satz:

   * **Typ** - `Parallel`
   * **Maximal parallel ausführbare Aufträge** –`<*x*>` (Berechnung siehe oben)

1. Speichern Sie diese Änderungen.
1. Aktivieren Sie das Kontrollkästchen `enable.multisession.name` unter `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, um die Multisession-Unterstützung für Adobe CS6 und höher zu aktivieren.
1. Erstellen Sie einen [Pool von`x` IDS-Workern, indem Sie SOAP-Endpunkte zur IDS-Worker-Konfiguration](#configuring-the-proxy-worker-for-indesign-server) hinzufügen.

   Wenn mehrere Computer mit [!DNL InDesign Server] ausgeführt werden, fügen Sie für jeden Computer SOAP-Endpunkte (Anzahl der Prozessoren pro Computer -1) hinzu.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wenn Sie mit einem Pool von Mitarbeitern arbeiten, können Sie die Blockierungsliste von IDS-Mitarbeitern aktivieren.
>
>Aktivieren Sie dazu das Kontrollkästchen **[!UICONTROL enable.retry.name]** unter der `com.day.cq.dam.ids.impl.IDSJobProcessor.name`-Konfiguration, mit der die IDS-Auftragsneuversuchen aktiviert werden.
>
>Legen Sie außerdem unter der Konfiguration `com.day.cq.dam.ids.impl.IDSPoolImpl.name` einen positiven Wert für `max.errors.to.blacklist` fest, der die Anzahl der Auftragswiederholungen bestimmt, bevor ein IDS aus der Liste der Auftragshandler ausgeschlossen wird.
>
>Standardmäßig wird der IDS-Mitarbeiter nach der konfigurierbaren (`retry.interval.to.whitelist.name`) Zeit in Minuten erneut überprüft. Wenn der Worker online gefunden wird, wird er aus der Blockierungsliste entfernt.

## Unterstützung für [!DNL InDesign Server] 10.0 oder höher {#enabling-support-for-indesign-server-or-later} aktivieren

Führen Sie für [!DNL InDesign Server] 10.0 oder höher die folgenden Schritte aus, um die Unterstützung für mehrere Sitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager von der [!DNL Experience Manager Assets]-Instanz `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Aktivieren Sie die Option **[!UICONTROL ids.cc.enable]** und klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Für die Integration von [!DNL InDesign Server] mit [!DNL Experience Manager Assets] verwenden Sie einen Multicore-Prozessor, da die für die Integration erforderliche Sitzungsunterstützungsfunktion auf einzelnen Core-Systemen nicht unterstützt wird.

## Konfigurieren Sie [!DNL Experience Manager]-Berechtigungen {#configure-aem-credentials}

Sie können die Standardanmeldeinformationen des Administrators (Benutzername und Kennwort) für den Zugriff auf [!DNL InDesign Server] aus Ihrer [!DNL Experience Manager]-Bereitstellung ändern, ohne die Integration mit [!DNL InDesign Server] zu unterbrechen.

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie in diesem Dialogfeld den neuen Benutzernamen und das Kennwort ein.
1. Speichern Sie die Anmeldedaten.

>[!MORELIKETHIS]
>
>* [Info zu Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)

