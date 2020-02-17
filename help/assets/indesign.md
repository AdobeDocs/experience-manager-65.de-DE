---
title: Integration von AEM Assets mit Adobe InDesign Server
description: Erfahren Sie, wie Sie AEM Assets in Adobe InDesign Server integrieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 07c1a4102539ba4678c55dee3a4882101e39864f

---


# Integration von AEM Assets mit Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets nutzt:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist eine AEM-Instanz, die mit einem Proxy Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, sowie mit anderen AEM-Instanzen, um das Ergebnis bereitzustellen.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.
Diese Aufgaben können unterschiedlichster Art sein, beispielsweise die Nutzung von InDesign Server zur Verarbeitung von Dateien.

Um Dateien, die Sie mit Adobe InDesign erstellt haben, vollständig in AEM Assets zu laden, wird ein Proxy verwendet. Dieser verwendet einen Proxy Worker für die Kommunikation mit Adobe InDesign Server, wo [Skripte](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) ausgeführt werden, um Metadaten zu extrahieren und verschiedene Ausgabeformate für AEM Assets zu generieren. Der Proxy Worker ermöglicht die bidirektionale Kommunikation zwischen InDesign Server und den AEM-Instanzen in einer Cloud-Konfiguration.

>[!NOTE]
>
>Adobe InDesign wird in Form von zwei Produkten angeboten:
>
>* [InDesign](https://www.adobe.com/products/indesign.html)
   >  Damit können Sie Seitenlayouts für den Druck bzw. die digitale Distribution entwerfen.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)
   >  Diese Engine ermöglicht die programmgesteuerte automatisierte Erstellung von Dokumenten, die auf denen basieren, die Sie mit InDesign entworfen haben. Die Engine fungiert als Dienst, der eine Schnittstelle seiner [ExtendScript](https://www.adobe.com/devnet/scripting.html)-Engine bereitstellt.
   >  Die Skripten werden in ExtendScript geschrieben, was JavaScript ähnlich ist. For information about InDesign scripts see [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).


## How the extraction works {#how-the-extraction-works}

Der Adobe InDesign Server kann mit AEM Assets integriert werden, sodass mit InDesign erstellte INDD-Dateien hochgeladen, Darstellungen generiert, alle Medien extrahiert (z. B. Video) und als Assets gespeichert werden können:

>[!NOTE]
>
>Frühere Versionen von AEM konnten XMP und die Miniaturansicht extrahieren, während jetzt alle Medien extrahiert werden können.

1. Laden Sie Ihre INDD-Datei auf AEM Assets hoch.
1. Ein Framework sendet Befehlsskripte via SOAP (Simple Object Access Protocol) an InDesign Server.
Dieses Befehlsskript führt folgende Aktionen aus:

   * Rufen Sie die INDD-Datei ab.
   * Führt InDesign Server-Befehle aus:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.
   * Veröffentlicht die resultierenden Dateien wieder in AEM Assets.
   >[!NOTE]
   >
   >IDML ist ein XML-basiertes Format, das den gesamten Inhalt der InDesign-Datei rendert. It is stored as an compressed package using [ZIP](https://www.techterms.com/definition/zip) compression. Weitere Informationen finden Sie unter [InDesign Interchange Formats INX und IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&seqNum=8).

   >[!CAUTION]
   >
   >Wenn der InDesign-Server nicht installiert oder nicht konfiguriert ist, können Sie dennoch eine INDD-Datei in AEM hochladen. Die erzeugten Darstellungen sind jedoch auf PNG und JPEG beschränkt. Sie können keine HTML-, IDML- oder Seitendarstellungen erstellen.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in AEM Assets gespeichert.
   * Alle Ausgabeformate werden in AEM Assets im Asset selbst gespeichert.

## Integrate the InDesign Server with AEM {#integrating-the-indesign-server-with-aem}

Um den InDesign-Server für die Verwendung mit AEM Assets und nach der Konfiguration des Proxys zu integrieren, müssen Sie:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Falls erforderlich, [konfigurieren Sie den AEM Assets-Workflow](#configuring-the-aem-assets-workflow).
Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.
1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installieren Sie InDesign Server {#installing-the-indesign-server}

Um InDesign Server für die Verwendung mit AEM zu installieren und zu starten, gehen Sie wie folgt vor:

1. Laden Sie Adobe InDesign Server herunter und installieren ihn.

1. Bei Bedarf können Sie die Konfiguration Ihrer InDesign Server-Instanz anpassen.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configure the AEM Assets workflow {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **[!UICONTROL DAM Update Asset]**, that has several process steps specifically for InDesign:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten](#page-extraction)

Dieser Workflow wird mit Standardwerten konfiguriert, die für Ihr Setup in den verschiedenen Autoreninstanzen angepasst werden können. (Dies ist ein Standard-Workflow. Deshalb finden Sie weitere Information unter [Bearbeiten eines Workflows](/help/sites-developing/workflows-models.md#configuring-a-workflow-step).) Wenn Sie die Standardwerte (einschließlich SOAP-Port) verwenden, ist keine Konfiguration erforderlich.

Nach Abschluss des Setups löst das Hochladen von InDesign-Dateien in AEM Assets (mithilfe einer der üblichen Methoden) den Workflow für die Verarbeitung des Assets und Vorbereitung der verschiedenen Ausgabeformate aus. Test your configuration by uploading an INDD file into AEM Assets to confirm that you see the different renditions created by IDS under `<*your_asset*>.indd/Renditions`

#### Media extraction {#media-extraction}

Dieser Schritt steuert die Extraktion von Medien aus der INDD-Datei.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Medien]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek**: Dies ist eine einfache HTTP get/post-Methodenbibliothek, die von den anderen Skripten benötigt wird.

* **Skripten** erweitern: Hier können Sie verschiedene Skriptkombinationen angeben. If you want your own scripts to be executed on the InDesign Server, save the scripts at `/apps/settings/dam/indesign/scripts`.

Weitere Informationen zu InDesign-Skripten finden Sie in der [InDesign-Entwicklerdokumentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)

>[!CAUTION]
>
>Ändern Sie nicht die ExtendScript-Bibliothek. Diese Bibliothek bietet die HTTP-Funktionen, die für die Kommunikation mit Sling erforderlich sind. Diese Einstellung legt die Bibliothek fest, die zur Verwendung an InDesign Server gesendet werden soll.

Das Skript `ThumbnailExport.jsx`, das vom Workflow-Schritt „Extrahierung von Medien“ ausgeführt wird, generiert eine Miniaturansicht im JPG-Format. Diese Darstellung wird vom Arbeitsablaufschritt &quot;Prozessminiaturen&quot;verwendet, um die für AEM erforderlichen statischen Darstellungen zu generieren.

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Voreinstellungen nicht entfernen, da sie für die AEM Assets-Benutzeroberfläche erforderlich sind. Abschließend entfernt der Workflow-Schritt „Bildvorschau-Wiedergabe löschen“ die JPG-Miniaturansicht, da sie nicht mehr benötigt wird.

#### Page extraction {#page-extraction}

Dabei wird eine AEM-Seite aus den extrahierten Elementen erstellt. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungshandlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Seiten]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Seitenextrahierungs-Handler**: Wählen Sie in der Popup-Liste den zu verwendenden Handler aus. Ein Extrahierungshandler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API). In einer standardmäßigen AEM-Installation ist folgende Option verfügbar:
   * IDML Export Extraction Handle: Operates on the `IDML` rendition generated in the MediaExtract step.

* **Seitenname**: Geben Sie den Namen an, den Sie der resultierenden Seite zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel**: Geben Sie den Titel an, den Sie der resultierenden Seite zuweisen möchten.

* **Seitenstammpfad**: Der Pfad zum Stammverzeichnis der resultierenden Seite. Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage**: Die Vorlage, die beim Generieren der resultierenden Seite verwendet wird.

* **Seitendesign**: Der Seitenentwurf, der beim Generieren der resultierenden Seite verwendet wird.

### Configure the proxy worker for InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole im linken Bereich den Eintrag **[!UICONTROL Cloud-Service-Konfigurationen]**. Anschließend erweitern Sie den Eintrag **[!UICONTROL Cloud-Proxy-Konfiguration]**.

1. Doppelklicken Sie auf den **[!UICONTROL IDS-Worker]**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-Pool** Die SOAP-Endpunkte, die mit InDesign Server kommunizieren sollen. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf OK.

### Configure Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Wenn InDesign Server und AEM auf unterschiedlichen Hosts ausgeführt werden oder eine bzw. beide Anwendungen nicht die Standardanschlüsse nutzen, konfigurieren Sie in [!UICONTROL Day CQ Link Externalizer] den Host, Port und Inhaltspfad für InDesign Server.

1. Access the Web Console at `https://[aem_server]:[port]/system/console/configMgr`.
1. Locate the configuration **[!UICONTROL Day CQ Link Externalizer]**, and tap **[!UICONTROL Edit]** to open it.
1. Geben Sie den Hostnamen und Kontextpfad für InDesign Server an und klicken Sie auf **Speichern**.

   ![chlimage_1-97](assets/chlimage_1-290.png)

### Aktivieren der parallelen Auftragsverarbeitung für InDesign-Server {#enabling-parallel-job-processing-for-indesign-server-s}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren. Legen Sie die maximale Anzahl paralleler Aufträge fest (`x`), die ein InDesign-Server verarbeiten kann:

* On a single multiprocessor machine, the maximum number of parallel jobs (`x`) that an InDesign Server can process is one less than the number of processors running IDS.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie von der Gesamtanzahl der verfügbaren Prozessoren (auf allen Computern) die Gesamtanzahl der Computer abziehen.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **[!UICONTROL Konfigurationen]** der Felix-Konsole. Beispiel: `https://[aem_server]:[port]/system/console/configMgr`.

1. Wählen Sie die IDS-Verarbeitungsschlange unter `Apache Sling Job Queue Configuration`.

1. Satz:

   * **Typ** - `Parallel`
   * **Maximale Anzahl paralleler Aufträge** - `<*x*>` (wie oben berechnet)

1. Speichern Sie diese Änderungen.
1. Aktivieren Sie das `enable.multisession.name` Kontrollkästchen unter &quot;Konfiguration&quot;, um die Unterstützung für mehrere Sitzungen für Adobe CS6 und höher zu aktivieren `com.day.cq.dam.ids.impl.IDSJobProcessor.name` .
1. Create a [pool of `x` IDS workers by adding SOAP endpoints to the IDS Worker configuration](#configuring-the-proxy-worker-for-indesign-server).

   Wenn mehrere Computer InDesign Server ausführen, fügen Sie SOAP-Endpunkte (Anzahl der Prozessoren pro Computer -1) für jeden Computer hinzu.

   >[!NOTE]
   >
   >Sie können IDS-Worker per Blacklist sperren, wenn Sie mit einem Worker-Pool arbeiten.
   >
   >
   >To do so, enable the **[!UICONTROL enable.retry.name]** checkbox, under the `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuration, which enables IDS job retrials.
   >
   >
   >Also, under the `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuration, set a positive value for `max.errors.to.blacklist` parameter which determines number of job retrials before barring an IDS from the job handlers list.
   >
   >
   >Standardmäßig wird der IDS-Worker nach einer konfigurierbaren Zeit (retry.interval.to.whitelist.name) in Minuten erneut validiert. Wenn der Worker online gefunden wird, wird er aus der Blacklist entfernt..

## Unterstützung für InDesign Server 10.0 oder höher aktivieren {#enabling-support-for-indesign-server-or-later}

Führen Sie für InDesign Server 10.0 oder höher die folgenden Schritte durch, um Unterstützung für Mehrfachsitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager über Ihre AEM Assets-Instanz `https://[aem_server]:[port]/system/console/configMgr`.
1. Edit the configuration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Select the **[!UICONTROL ids.cc.enable]** option, and click **[!UICONTROL Save]**.

>[!NOTE]
>
>Verwenden Sie für die Integration von InDesign Server in AEM Assets einen Mehrkernprozessor, da die für die Integration notwendige Funktion „Sitzungsunterstützung“ auf Einzelkernsystemen nicht unterstützt wird.

## Konfigurieren von AEM-Anmeldeinformationen {#configure-aem-credentials}

Sie können die Standardberechtigung des Administrators (Benutzername und Kennwort) für den Zugriff auf den InDesign-Server von Ihrer AEM-Instanz aus ändern, ohne die Integration mit dem InDesign-Server zu unterbrechen.

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie in diesem Dialogfeld den neuen Benutzernamen und das Kennwort ein.
1. Speichern Sie die Anmeldedaten.

>[!MORELIKETHIS]
>
>* [Info zu Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)

