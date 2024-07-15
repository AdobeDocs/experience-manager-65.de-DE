---
title: Integration von  [!DNL Assets]  mit  [!DNL InDesign Server]
description: Erfahren Sie mehr über die Integration von  [!DNL Adobe Experience Manager Assets]  mit  [!DNL Adobe InDesign Server].
contentOwner: AG
role: Admin
feature: Publishing
exl-id: 5ba020a3-c36c-402b-a11b-d6b0426b03bf
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 100%

---

# Integration von [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] verwendet:

* Einen Proxy für den Lastenausgleich bei der Verarbeitung bestimmter Aufgaben. Ein Proxy ist eine [!DNL Experience Manager]-Instanz, die mit einem Proxy Worker kommuniziert, um eine bestimmte Aufgabe zu erfüllen, sowie mit anderen [!DNL Experience Manager]-Instanzen, um das Ergebnis bereitzustellen.
* Einen Proxy Worker zum Definieren und Verwalten einer bestimmten Aufgabe.
Diese Aufgaben können unterschiedlichster Art sein, beispielsweise die Nutzung von [!DNL InDesign Server] zur Verarbeitung von Dateien.

Um Dateien, die Sie mit [!DNL Adobe InDesign] erstellt haben, vollständig in [!DNL Experience Manager Assets] zu laden, wird ein Proxy verwendet. Dieser verwendet einen Proxy Worker für die Kommunikation mit dem [!DNL Adobe InDesign Server], auf dem [Skripte](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) ausgeführt werden, um Metadaten zu extrahieren und verschiedene Ausgabedarstellungen für [!DNL Experience Manager Assets] zu generieren. Der Proxy Worker ermöglicht die bidirektionale Kommunikation zwischen [!DNL InDesign Server]-Instanzen und den [!DNL Experience Manager]-Instanzen in einer Cloud-Konfiguration.

>[!NOTE]
>
>[!DNL Adobe InDesign] gibt es als zwei separate Angebote. Das [Adobe InDesign](https://www.adobe.com/de/products/indesign.html)-Desktop-Programm, das zum Entwerfen von Seiten-Layouts für den Druck und die digitale Distribution verwendet wird. [Adobe InDesign Server](https://www.adobe.com/de/products/indesignserver.html) ermöglicht die programmgesteuerte automatisierte Erstellung von Dokumenten, die auf denen basieren, die Sie mit [!DNL InDesign] entworfen haben. Es fungiert als Dienst, der eine Schnittstelle zu seiner [ExtendScript](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)-Engine bietet. Die Skripte werden in [!DNL ExtendScript] geschrieben, das [!DNL JavaScript] ähnelt. Weitere Informationen zu [!DNL InDesign]-Skripten finden Sie unter [https://www.adobe.com/devnet/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## So funktioniert die Extraktion {#how-the-extraction-works}

Der [!DNL Adobe InDesign Server] kann mit [!DNL Experience Manager Assets] integriert werden, sodass in [!DNL InDesign] erstellte Dateien (.indd) hochgeladen, Ausgabedarstellungen generiert sowie alle Medien (z. B. Video) extrahiert und als Assets gespeichert werden können:

>[!NOTE]
>
>Frühere Versionen von [!DNL Experience Manager] konnten XMP und die Miniaturansicht extrahieren, während jetzt alle Medien extrahiert werden können.

1. Laden Sie Ihre INDD-Dateien in [!DNL Experience Manager Assets] hoch.
1. Ein Framework sendet Befehlsskripte via SOAP (Simple Object Access Protocol) an [!DNL InDesign Server].
Dieses Befehlsskript führt folgende Aktionen aus:

   * Ruft die INDD-Datei ab.
   * Führt [!DNL InDesign Server]-Befehle aus:

      * Struktur, Text und alle Mediendateien werden extrahiert.
      * PDF- und JPG-Ausgabeformate werden generiert.
      * HTML- und IDML-Ausgabeformate werden generiert.

   * Veröffentlicht die resultierenden Dateien wieder in [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML ist ein XML-basiertes Format, das alle Inhalte der [!DNL InDesign]-Datei aufbereitet. Es wird als komprimiertes Paket mit [ZIP](https://www.techterms.com/definition/zip)-Komprimierung gespeichert. Weitere Informationen finden Sie unter [InDesign Interchange Formats INX and IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).

   >[!CAUTION]
   >
   >Wenn der [!DNL InDesign Server] nicht installiert oder konfiguriert ist, können Sie trotzdem eine INDD-Datei in [!DNL Experience Manager] hochladen. Die erzeugten Ausgabedarstellungen sind jedoch auf PNG und JPEG beschränkt. Sie können keine HTML-, IDML- oder Seitenausgabeformate generieren.

1. Nach der Extraktion und Ausgabegenerierung:

   * Die Struktur wird auf einer `cq:Page` repliziert (Ausgabetyp).
   * Der extrahierte Text und die Dateien werden in [!DNL Experience Manager Assets] gespeichert. 
   * Alle Ausgabedarstellungen werden in [!DNL Experience Manager Assets] im Asset selbst gespeichert.

## Integration von [!DNL InDesign Server] mit Experience Manager {#integrating-the-indesign-server-with-aem}

Um [!DNL InDesign Server] für die Verwendung mit [!DNL Experience Manager Assets] zu integrieren und nach der Konfiguration des Proxys müssen Sie folgende Schritte durchführen:

1. [Installieren Sie InDesign Server](#installing-the-indesign-server).
1. Falls erforderlich, [konfigurieren Sie den Experience Manager Assets-Workflow](#configuring-the-aem-assets-workflow).
Dies ist nur dann notwendig, wenn die Standardwerte für Ihre Instanz nicht geeignet sind.
1. Konfigurieren Sie einen [Proxy Worker für InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installieren von [!DNL InDesign Server] {#installing-the-indesign-server}

Um den [!DNL InDesign Server] für die Verwendung mit [!DNL Experience Manager] zu installieren und zu starten, gehen Sie wie folgt vor:

1. Laden Sie den [!DNL InDesign Server] herunter und Sie installieren ihn.

1. Bei Bedarf können Sie die Konfiguration Ihrer [!DNL InDesign Server]-Instanz anpassen.

1. Starten Sie den Server über die Befehlszeile:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Dadurch wird der Server mit dem SOAP-Plug-in gestartet, das Port 8080 abhört. Alle Protokollmeldungen und Ausgaben werden direkt im Befehlsfenster angezeigt.

   >[!NOTE]
   >
   >Wenn Sie die Ausgabemeldungen in einer Datei speichern möchten, müssen Sie dazu eine Umleitung verwenden, z. B. unter Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Konfigurieren des [!DNL Experience Manager Assets]-Workflows {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager Assets] verfügt über den vorkonfigurierten Workflow **[!UICONTROL DAM-Update-Asset]**, der mehrere Prozessschritte speziell für [!DNL InDesign] umfasst:

* [Extrahierung von Medien](#media-extraction)
* [Extrahierung von Seiten  ](#page-extraction)

Dieser Workflow wird mit Standardwerten konfiguriert, die für Ihr Setup in den verschiedenen Autoreninstanzen angepasst werden können. (Dies ist ein Standard-Workflow. Deshalb finden Sie weitere Information unter [Bearbeiten eines Workflows](/help/sites-developing/workflows-models.md#configuring-a-workflow-step).) Wenn Sie die Standardwerte (einschließlich SOAP-Port) verwenden, ist keine Konfiguration erforderlich.

Nach Abschluss des Setups löst das Hochladen von [!DNL InDesign]-Dateien in [!DNL Experience Manager Assets] (mithilfe einer der üblichen Methoden) den Workflow für die Verarbeitung des Assets und Vorbereitung der verschiedenen Ausgabedarstellungen aus. Testen Sie Ihre Konfiguration, indem Sie eine INDD-Datei in [!DNL Experience Manager Assets] hochladen und auf diese Weise überprüfen, ob IDS verschiedene Ausgabedarstellungen unter `<*your_asset*>.indd/Renditions` erstellt.

#### Extrahierung von Medien {#media-extraction}

Dieser Schritt steuert die Extrahierung von Medien aus der INDD-Datei.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Medien]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![Argumente und Skriptpfade zum Extrahieren von Medien](assets/media_extraction_arguments_scripts.png)

Argumente und Skriptpfade zum Extrahieren von Medien

* **ExtendScript-Bibliothek**: Dies ist eine einfache HTTP-GET/POST-Methodenbibliothek, die von anderen Skripten benötigt wird.

* **Skripte erweitern**: Hier können Sie unterschiedliche Skriptkombinationen angeben. Wenn Ihre eigenen Skripte auf [!DNL InDesign Server] ausgeführt werden sollen, speichern Sie die Skripte unter `/apps/settings/dam/indesign/scripts`.

<!-- TBD: Hiding this link since ADC is not available anymore. 
For information about [!DNL Adobe InDesign] scripts, see [InDesign developer documentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
-->

>[!CAUTION]
>
>Ändern Sie nicht die ExtendScript-Bibliothek. Diese Bibliothek bietet die HTTP-Funktionen, die für die Kommunikation mit Sling erforderlich sind. Diese Einstellung legt die Bibliothek fest, die zur Verwendung an [!DNL InDesign Server] gesendet werden soll.

Das Skript `ThumbnailExport.jsx`, das vom Workflow-Schritt „Extrahierung von Medien“ ausgeführt wird, generiert eine Miniaturansicht im JPG-Format. Diese Ausgabedarstellung wird vom Workflow-Schritt „Miniaturansichten verarbeiten“ dazu verwendet, die für [!DNL Experience Manager] erforderlichen statischen Ausgabedarstellungen zu rendern.

Sie können den Workflow-Schritt „Miniaturansichten verarbeiten“ so konfigurieren, dass statische Darstellungen in verschiedenen Größen generiert werden. Stellen Sie sicher, dass Sie die Voreinstellungen nicht entfernen, da sie für die Benutzeroberfläche von [!DNL Experience Manager Assets] erforderlich sind. Abschließend entfernt der Workflow-Schritt „Bildvorschau-Wiedergabe löschen“ die JPG-Miniaturansicht, da sie nicht mehr benötigt wird.

#### Extrahierung von Seiten {#page-extraction}

Dabei wird eine [!DNL Experience Manager]-Seite aus den extrahierten Elementen erstellt. Das Extrahieren von Daten aus einem Ausgabeformat (aktuell HTML oder IDML) erfolgt mithilfe eines Extrahierungs-Handlers. Diese Daten werden verwendet, um eine Seite mit PageBuilder zu erstellen.

Anpassungen können Sie im Schritt **[!UICONTROL Extrahierung von Seiten]** auf der Registerkarte **[!UICONTROL Argumente]** vornehmen.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Handler zur Extrahierung von Seite**: Wählen Sie in der Dropdown-Liste den zu verwendenden Handler aus. Ein Extrahierungs-Handler arbeitet mit einem bestimmten Ausgabeformat, das mit einem entsprechenden `RenditionPicker` ausgewählt wird (siehe `ExtractionHandler`-API). Bei einer standardmäßigen [!DNL Experience Manager]-Installation sind folgende Optionen verfügbar:
   * IDML-Export-Extrahierungs-Handler: Bearbeitet die `IDML`-Ausgabedarstellung, die im Schritt „MediaExtract“ generiert wurde.

* **Seitenname**: Geben Sie den Namen an, den Sie der resultierenden Datei zuweisen möchten. Wenn Sie das Feld leer lassen, wird als Name „Seite“ gewählt (oder eine Ableitung, falls „Seite“ bereits vorhanden ist).

* **Seitentitel**: Geben Sie den Titel an, den Sie der resultierenden Datei zuweisen möchten.

* **Stammverzeichnis der Seite**: Der Pfad zum Stammverzeichnis der resultierenden Datei. Wenn Sie das Feld leer lassen, wird der Knoten mit den Ausgabeformaten des Assets verwendet.

* **Seitenvorlage**: Die zu verwendende Vorlage für das Generieren der resultierenden Seite.

* **Seiten-Design**: Das zu verwendende Seiten-Design für das Generieren der resultierenden Seite.

### Konfigurieren des Proxy Workers für [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Der Worker befindet sich in der Proxy-Instanz.

1. Erweitern Sie in der Tools-Konsole die Option **[!UICONTROL Cloud Service-Konfigurationen]** im linken Bereich. Anschließend erweitern Sie den Eintrag **[!UICONTROL Cloud-Proxy-Konfiguration]**.

1. Doppelklicken Sie auf den **[!UICONTROL IDS-Worker]**, um ihn für die Konfiguration zu öffnen.

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um das Konfigurationsdialogfeld zu öffnen und die erforderlichen Einstellungen vorzunehmen:

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-Pool**
Die SOAP-Endpunkte, die mit dem [!DNL InDesign Server] kommunizieren sollen. Sie können Elemente nach Bedarf hinzufügen, entfernen und ordnen.

1. Klicken Sie zum Speichern auf „OK“.

### Konfigurieren von Day CQ Link Externalizer {#configuring-day-cq-link-externalizer}

Wenn [!DNL InDesign Server] und [!DNL Experience Manager] auf unterschiedlichen Hosts laufen und eine bzw. beide Anwendungen nicht die Standardanschlüsse nutzen, konfigurieren Sie in [!UICONTROL Day CQ Link Externalizer] den Host-Namen, Anschluss und Inhaltspfad für den [!DNL InDesign Server].

1. Rufen Sie die Web-Konsole unter `https://[aem_server]:[port]/system/console/configMgr` auf.
1. Suchen Sie die Konfiguration **[!UICONTROL Day CQ Link Externalizer]**. Klicken Sie auf **[!UICONTROL Bearbeiten]**, um sie zu öffnen.
1. Mithilfe der Einstellungen von Link Externalizer können Sie absolute URLs für die [!DNL Experience Manager]-Bereitstellung und für den [!DNL InDesign Server] erstellen. Geben Sie im Feld **[!UICONTROL Domains]** den Host-Namen für den [!DNL Adobe InDesign Server] an. Klicken Sie auf **Speichern**.

   Verwenden Sie in absoluten URLs `localhost` als Host-Namen für Ihre lokale (Autoren-)Instanz und Host-Namen oder IP-Adresse für die Veröffentlichungsinstanz, wie in der folgenden Abbildung dargestellt.

   ![Einstellung für Link Externalizer](assets/link-externalizer-config.png)

### Aktivieren der parallelen Auftragsverarbeitung für [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server}

Sie können jetzt die parallele Auftragsverarbeitung für IDS aktivieren. Bestimmen Sie die maximale Anzahl paralleler Aufträge (`x`), die ein [!DNL InDesign Server] verarbeiten kann:

* Auf einem einzelnen Mehrprozessor-Computer ist die Anzahl der parallelen Aufträge (`x`), die ein [!DNL InDesign Server] verarbeiten kann, um eins kleiner als die Anzahl der Prozessoren, die IDS ausführen.
* Wenn Sie IDS auf mehreren Computern ausführen, müssen Sie die Gesamtanzahl der verfügbaren Prozessoren (d. h. auf allen Computern) zählen und dann die Gesamtanzahl der Maschinen subtrahieren.

So konfigurieren Sie die Anzahl der parallelen IDS-Aufträge:

1. Öffnen Sie die Registerkarte **[!UICONTROL Konfigurationen]** der Felix-Konsole. Zum Beispiel: `https://[aem_server]:[port]/system/console/configMgr`.

1. Wählen Sie die IDS-Verarbeitungsschlange unter `Apache Sling Job Queue Configuration`.

1. Satz:

   * **Typ** - `Parallel`
   * **Maximal parallel ausführbare Aufträge** –`<*x*>` (Berechnung siehe oben)

1. Speichern Sie diese Änderungen.
1. Um die Unterstützung für mehrere Sitzungen für Adobe CS6 und höher zu aktivieren, aktivieren Sie das Kontrollkästchen `enable.multisession.name` unter der Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Erstellen Sie einen [Pool von`x` IDS-Workern, indem Sie SOAP-Endpunkte zur IDS-Worker-Konfiguration](#configuring-the-proxy-worker-for-indesign-server) hinzufügen.

   Wenn mehrere Computer [!DNL InDesign Server] ausführen, fügen Sie SOAP-Endpunkte (Anzahl der Prozessoren pro Computer -1) für jeden Computer hinzu.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wenn Sie mit einem Pool von Workern arbeiten, können Sie die Blockierungsliste von IDS-Workern aktivieren.
>
>Aktivieren Sie dazu das Kontrollkästchen **[!UICONTROL enable.retry.name]** unter der Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, um Wiederholungen von IDS-Aufträgen zu ermöglichen.
>
>Legen Sie in der Konfiguration `com.day.cq.dam.ids.impl.IDSPoolImpl.name` außerdem einen positiven Wert für den Parameter `max.errors.to.blacklist` fest, der die Anzahl der Auftragswiederholungen steuert, bevor ein IDS aus der Auftrags-Handler-Liste ausgeschlossen wird.
>
>Standardmäßig wird der IDS-Worker nach einer konfigurierbaren Zeit (`retry.interval.to.whitelist.name`) in Minuten erneut validiert. Wenn der Worker online gefunden wird, wird er aus der Blockierungsliste entfernt.

## Aktivieren der Unterstützung für [!DNL InDesign Server] 10.0 oder höher {#enabling-support-for-indesign-server-or-later}

Führen Sie für [!DNL InDesign Server] 10.0 oder höher die folgenden Schritte durch, um Unterstützung für Mehrfachsitzungen zu aktivieren.

1. Öffnen Sie Configuration Manager über Ihre [!DNL Experience Manager Assets]-Instanz `https://[aem_server]:[port]/system/console/configMgr`.
1. Bearbeiten Sie die Konfiguration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Aktivieren Sie die Option **[!UICONTROL ids.cc.enable]** und klicken Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>Verwenden Sie für die Integration von [!DNL InDesign Server] mit [!DNL Experience Manager Assets] einen Mehrkernprozessor, da die für die Integration notwendige Funktion „Sitzungsunterstützung“ auf Einzelkernsystemen nicht unterstützt wird.

## Konfigurieren der [!DNL Experience Manager]-Anmeldeinformationen {#configure-aem-credentials}

Sie können die standardmäßigen Admin-Anmeldeinformationen (Benutzername und Passwort) für den Zugriff auf den [!DNL InDesign Server] in Ihrer [!DNL Experience Manager]-Bereitstellung ändern, ohne die Integration mit dem [!DNL InDesign Server] aufzuheben.

1. Wechseln zu `/etc/cloudservices/proxy.html`.
1. Geben Sie im Dialogfeld den neuen Benutzernamen und das neue Passwort an.
1. Speichern Sie die Anmeldeinformationen. 

>[!MORELIKETHIS]
>
>* [Über Adobe InDesign Server](https://www.adobe.com/de/products/indesignserver/faq.html)
