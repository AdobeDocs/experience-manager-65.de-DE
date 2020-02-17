---
title: Fehlerbehebung in Dynamic Media – Scene7-Modus
description: Fehlerbehebung in Dynamic Media im Ausführungsmodus „Scene7“.
uuid: 77e04ccf-33dc-4d2f-8950-318d4b008f74
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 0d48c031-d3ee-4143-b739-a79ba28fd63a
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Fehlerbehebung in Dynamic Media – Scene7-Modus{#troubleshooting-dynamic-media-scene-mode}

Das folgende Dokument beschreibt das Beheben von Fehlern mit Dynamic Media im Ausführungsmodus **dynamicmedia_scene7**.

## Setup und Konfiguration {#setup-and-configuration}

Stellen Sie sicher, dass Dynamic Media korrekt eingerichtet wurde, indem Sie folgende Schritte ausführen:

* Start up command contains the `-r dynamicmedia_scene7` runmode argument.
* Alle Cumulative Fix Packs für AEM 6.4 wurden *vor* den verfügbaren Feature Packs für Dynamic Media installiert.
* Das optionale Feature Pack 18912 wurde installiert.

   Dieses optionale Feature Pack bietet FTP-Unterstützung und Hilfe bei der Migration von Assets aus Dynamic Media Classic (Scene7) in Dynamic Media.

* Navigieren Sie zur Cloud Services-Benutzeroberfläche und vergewissern Sie sich, dass das angegebene Konto unter **[!UICONTROL Verfügbare Konfigurationen]** aufgeführt wird.
* Ensure that the `Dynamic Media Asset Activation (scene7)` replication agent is enabled.

   Diesen Replizierungsagent finden Sie unter „Agenten für Autor“.

## Allgemein (alle Assets) {#general-all-assets}

Die folgenden allgemeinen Tipps und Tricks gelten für alle Assets.

### Asset-Synchronisierungsstatuseigenschaften {#asset-synchronization-status-properties}

Anhand der folgenden Asset-Eigenschaften können Sie in CRXDE Lite prüfen, ob Assets erfolgreich zwischen AEM und Dynamic Media synchronisiert wurden:

| **Eigenschaft** | **Beispiel** | **Beschreibung** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Allgemeiner Indikator dafür, dass der Knoten mit Dynamic Media verknüpft ist. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** - oder Fehlertext | Status des Hochladens der Assets in Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Muss angegeben werden, um URLs zu Remote-Assets von Dynamic Media zu generieren. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **Erfolg** oder **fehlgeschlagen:`<error text>`** | Synchronisierungsstatus für Sets (Rotationssets, Bildsets usw.), Bildvorgaben, Viewer-Vorgaben oder Imagemap-Updates für ein Asset oder Bilder, die bearbeitet wurden. |

### Protokollierung der Synchronisierung {#synchronization-logging}

Synchronization errors and issues are logged in `error.log` (AEM server directory `/crx-quickstart/logs/`). Sufficient logging is available to determine the root cause of most issues, however you can increase the logging to DEBUG on the `com.adobe.cq.dam.ips` package through the Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) to gather more information.

### Verschieben, Kopieren, Löschen {#move-copy-delete}

Führen Sie folgende Schritte aus, bevor Sie einen Verschiebe-, Kopier- oder Löschvorgang ausführen:

* Überprüfen Sie bei Bildern und Videos, ob ein `<object_node>/jcr:content/metadata/dam:scene7ID` Wert vorhanden ist, bevor Sie Vorgänge zum Verschieben, Kopieren oder Löschen durchführen.
* For image and viewer presets, confirm that an `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` value exists before performing move, copy, or delete operations.
* Wenn der obige Metadatenwert fehlt, müssen Sie Assets erneut hochladen, bevor Sie Verschiebe-, Kopier- oder Löschvorgänge ausführen.

### Versionskontrolle {#version-control}

Wenn Sie ein vorhandenes Dynamic Media-Asset (gleicher Name und Speicherort) ersetzen, können Sie beide Assets beibehalten oder eine Version ersetzen/erstellen.

* Durch Beibehalten beider Werte wird ein neues Asset mit einem eindeutigen Namen für die URL des veröffentlichten Assets erstellt. Beispiel: `image.jpg` das ursprüngliche Asset und `image1.jpg` das neu hochgeladene Asset.

* Das Erstellen einer Version wird im Scene7-Modus von Dynamic Media nicht unterstützt. Die neue Version ersetzt das vorhandene Asset in der Bereitstellung.

## Bilder und Sets {#images-and-sets}

Falls Sie Probleme mit Bildern und Sets haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Kein Zugriff auf Schaltfläche „URL kopieren“/„Code einbetten“ in der Asset-Detailansicht</td>
   <td>
    <ol>
     <li><p>Öffnen Sie CRX/DE:</p>
      <ul>
       <li>Überprüfen Sie, ob die Vorgabe in der JCR- <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> Definition definiert ist. Achtung: Dieser Pfad trifft zu, wenn Sie ein Upgrade von AEM 6.x auf 6.4 durchgeführt und sich gegen die Migration entschieden haben. Andernfalls ist der Ort <code>/conf/global/settings/dam/dm/presets/viewer</code>der Ort.</li>
       <li>Check to make sure that the asset in the JCR has <code>dam:scene7FileStatus</code><strong> </strong>under Metadata shows as <code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Aktualisieren Sie die Seite/navigieren Sie zu einer anderen Seite und kehren Sie dann zurück (Seitenleisten-JSPs müssen neu kompiliert werden).</p> <p>Wenn dies das Problem nicht behebt:</p>
    <ul>
     <li>Veröffentlichen Sie das Asset.</li>
     <li>Laden Sie das Asset erneut hoch und veröffentlichen Sie es.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Asset-Wähler im Set-Editor hängt sich beim Laden auf</td>
   <td><p>Bekanntes Problem, das in 6.4 behoben wird</p> </td>
   <td><p>Schließen Sie den Wähler und öffnen Sie ihn erneut.</p> </td>
  </tr>
  <tr>
   <td>Schaltfläche <strong>Auswählen</strong> ist nicht aktiv, nachdem ein Asset beim Bearbeiten eines Sets ausgewählt wurde</td>
   <td><p> </p> <p>Bekanntes Problem, das in 6.4 behoben wird</p> <p> </p> </td>
   <td><p>Klicken Sie im Asset-Wähler zuerst auf einen anderen Ordner und kehren Sie dann zurück, um das Asset auszuwählen.</p> </td>
  </tr>
  <tr>
   <td>Karussell-Hotspot verschiebt sich nach dem Wechsel zwischen Folien</td>
   <td><p>Prüfen Sie, ob alle Folien dieselbe Größe haben.</p> </td>
   <td><p>Verwenden Sie für das Karussell nur Bilder derselben Größe.</p> </td>
  </tr>
  <tr>
   <td>Bild wird im Viewer für dynamische Medien nicht als Vorschau angezeigt</td>
   <td><p>Check that the asset contains <code>dam:scene7File</code> in the Metadata properties (CRXDE Lite)</p> </td>
   <td><p>Überprüfen Sie, ob alle Elemente verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Hochgeladenes Asset wird nicht im Asset-Wähler angezeigt</td>
   <td><p>Check asset has property <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Überprüfen Sie, ob alle Elemente verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Banner wird in der Kartenansicht als <strong>Neu</strong> angezeigt, wenn das Asset noch nicht gestartet wurde</td>
   <td>Check asset <code>jcr:content</code> &gt; <code>dam:assetState</code> = if <code>unprocessed</code> it was not picked up by the workflow.</td>
   <td>Warten Sie, bis das Asset vom Workflow abgeholt wurde.</td>
  </tr>
  <tr>
   <td>Bilder oder Sets zeigen weder Viewer-URL noch eingebetteten Code an</td>
   <td>Prüfen Sie, ob die Viewer-Vorgabe veröffentlicht wurde.</td>
   <td><p>Go to <strong>Tools</strong> &gt; <strong>Assets</strong> &gt; <strong>Viewer Presets</strong> and publish the viewer preset.</p> </td>
  </tr>
 </tbody>
</table>

## Video {#video}

Falls Sie Probleme mit Videos haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Video kann nicht als Vorschau angezeigt werden</td>
   <td>
    <ul>
     <li>Prüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist (falls nicht unterstütztes Dateiformat). Falls nicht unterstützt, wird nur ein Bild angezeigt.</li>
     <li>Das Videoprofil muss mehr als eine Kodierungsvorgabe enthalten, damit ein AVS-Set generiert werden kann (einzelne Kodierungen werden als Videoinhalt für MP4-Dateien behandelt; nicht unterstützte Dateien werden wie nicht verarbeitete Dateien behandelt).</li>
     <li>Check that the video has finished processing by confirming <code>dam:scene7FileAvs</code> of <code>dam:scene7File</code> in metadata.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Weisen Sie dem Ordner ein Videoprofil zu.</li>
     <li>Bearbeiten Sie das Videoprofil, damit es mehr als eine Kodierungsvorgabe enthält.</li>
     <li>Warten Sie, bis die Verarbeitung des Videos abgeschlossen ist.</li>
     <li>Stellen Sie sicher, dass der Workflow für die Dynamic Media-Videokodierung nicht ausgeführt wird, bevor Sie das Video erneut laden.<br /> </li>
     <li>Laden Sie das Video erneut hoch.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video ist nicht kodiert</td>
   <td>
    <ul>
     <li>Check that the runmode is <code>dynamicmedia_scene7</code>.</li>
     <li>Prüfen Sie, ob der Dynamic Media-Cloud-Service konfiguriert ist.</li>
     <li>Prüfen Sie, ob dem Upload-Ordner ein Videoprofil zugeordnet ist.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Überprüfen Sie Ihre AEM-Instanz mit <code>-r dynamicmedia_scene7</code></li>
     <li>Prüfen Sie, ob die Dynamic Media-Konfiguration unter Cloud-Services ordnungsgemäß eingerichtet ist.</li>
     <li>Überprüfen Sie, ob der Ordner ein Videoprofil hat. Überprüfen Sie außerdem das Videoprofil.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Die Videoverarbeitung dauert zu lang</td>
   <td><p>So prüfen Sie, ob die Videokodierung noch läuft oder ob ein Fehler aufgetreten ist:</p>
    <ul>
     <li>Videostatus prüfen <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
     <li>Monitor the video from the workflow console <code>https://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Instances, Archive, Failures tabs.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Videoausgabeformat fehlt</td>
   <td><p>Wenn das Video hochgeladen wurde, aber keine kodierten Ausgabeformate vorhanden sind:</p>
    <ul>
     <li>Prüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist.</li>
     <li>Check that the video has finished processing by confirming <code>dam:scene7FileAvs</code> in metadata.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Weisen Sie dem Ordner ein Videoprofil zu.</li>
     <li>Warten Sie, bis die Verarbeitung des Videos abgeschlossen ist.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Viewer {#viewers}

Falls Sie Probleme mit einem Viewer haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Viewer-Vorgaben werden nicht veröffentlicht</td>
   <td><p>Gehen Sie zur Diagnoseseite des Stichprobenmanagers weiter: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>Überwachen Sie die berechneten Werte. Bei einem ordnungsmäßigen Betrieb wird Folgendes angezeigt:</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>Hinweis</strong>: Nach der Konfiguration der Dynamic Media-Cloud-Einstellungen kann es bis zu 10 Minuten dauern, bis die Assets im Viewer synchronisiert werden.</p> <p>Falls weiterhin nicht aktivierte Assets vorhanden sind, klicken Sie auf eine der Schaltflächen <strong>Alle nicht aktivierten Assets auflisten</strong>, um die Details anzuzeigen.</p> </td>
   <td>
    <ol>
     <li>Navigieren Sie in den Admin Tools zur Viewer-Vorgabenliste: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>Wählen Sie alle Viewer-Vorgaben aus und klicken Sie auf <strong>Veröffentlichen</strong>.</li>
     <li>Navigieren Sie zurück zum Beispiel-Manager und prüfen Sie, ob die Anzahl der nicht aktivierten Assets jetzt mit null angegeben wird.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Für das Bildmaterial der Viewer-Vorgabe wird für eine Vorschau in den Asset-Details oder für „URL kopieren“/„Code einbetten“ der Code 404 zurückgegeben</td>
   <td><p>Gehen Sie in CRXDE Lite wie folgt vor:</p>
    <ol>
     <li>Navigieren Sie zum <code>&lt;sync-folder&gt;/_CSS/_OOTB</code> Ordner im Synchronisierungsordner für dynamische Medien (z. B. <code>/content/dam/_CSS/_OOTB</code>),</li>
     <li>Suchen Sie den Metadaten-Knoten des problematischen Assets (z. B. <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>).</li>
     <li>Check for the presence of <code>dam:scene7*</code> properties. If the asset was successfully synced and published you see the <code>dam:scene7FileStatus</code> set is to <strong>PublishComplete</strong>.</li>
     <li>Versuchen Sie, das Bildmaterial direkt aus Dynamic Media anzufordern, indem Sie die Werte der folgenden Eigenschaften und Zeichenketten verketten.
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>Beispiel: <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>Wenn die Beispiel-Assets oder das Bildmaterial der Viewer-Vorgabe nicht synchronisiert oder veröffentlicht wurden, starten Sie den gesamten Kopier-/Synchronisierungsvorgang neu:</p>
    <ol>
     <li>Navigieren Sie zu CRXDE Lite.
      <ul>
       <li>Löschen <code>&lt;sync-folder&gt;/_CSS/_OOTB</code>.</li>
      </ul> </li>
     <li>Navigate to the CRX package manager: <code>https://localhost:4502/crx/packmgr/</code><a href="https://localhost:4502/crx/packmgr/"></a>
      <ol>
       <li>Suchen Sie das Viewer-Paket in der Liste (es beginnt mit <code>cq-dam-scene7-viewers-content</code>)</li>
       <li>Klicken Sie auf <strong>Neu installieren</strong>.</li>
      </ol> </li>
     <li>Navigieren Sie zur Seite für die Dynamic Media-Konfiguration und klicken Sie auf „Bearbeiten“, um das Konfigurationsdialogfeld für Ihre Dynamic Media S7-Konfiguration zu öffnen.
      <ul>
       <li>Nehmen Sie keine Änderungen vor und klicken Sie auf <strong>Speichern</strong>. Dadurch wird die Logik zum Erstellen und Synchronisieren von Beispiel-Assets, Viewer-Vorgabe-CSS und Bildmaterial erneut ausgelöst.<br />  </li>
      </ul> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

