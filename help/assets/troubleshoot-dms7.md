---
title: Konfigurieren des Dynamic Media-Scene7-Modus
description: Erfahren Sie, wie Sie Setup, Konfiguration und allgemeine Probleme in Dynamic Media beheben können, wenn dieses im Scene7-Modus ausgeführt wird.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: d4507059-a54d-4dc9-a263-e55dfa27eeb1
feature: Troubleshooting
mini-toc-levels: 3
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1393'
ht-degree: 100%

---

# Fehlerbehebung bei Dynamic Media – Scene7-Modus{#troubleshooting-dynamic-media-scene-mode}

Das folgende Dokument beschreibt das Beheben von Fehlern mit Dynamic Media im Ausführungsmodus **dynamicmedia_scene7**.

## Einrichtung und Konfiguration {#setup-and-configuration}

Stellen Sie sicher, dass Dynamic Media korrekt eingerichtet wurde, indem Sie folgende Schritte ausführen:

* Der Befehl „Start“ enthält das `-r dynamicmedia_scene7`-Ausführungsmodus-Argument.
* Alle Cumulative Fix Packs (CFPs) für Adobe Experience Manager 6.4 wurden *vor* den verfügbaren Feature Packs für Dynamic Media installiert.
* Das optionale Feature Pack 18912 wurde installiert.

  Dieses optionale Feature Pack bietet FTP-Unterstützung und Hilfe bei der Migration von Assets aus Dynamic Media Classic nach Dynamic Media.

* Navigieren Sie zur Cloud Services-Benutzeroberfläche und vergewissern Sie sich, dass das angegebene Konto unter **[!UICONTROL Verfügbare Konfigurationen]** aufgeführt wird.
* Stellen Sie sicher, dass der `Dynamic Media Asset Activation (scene7)`-Replikationsagent aktiviert ist.

  Diesen Replikationsagent finden Sie unter „Agenten für Autor“.

## Allgemein (alle Assets) {#general-all-assets}

Die folgenden allgemeinen Tipps und Tricks gelten für alle Assets.

### Asset-Synchronisierungsstatuseigenschaften {#asset-synchronization-status-properties}

Anhand der folgenden Asset-Eigenschaften können Sie in CRXDE Lite prüfen, ob Assets erfolgreich zwischen Experience Manager und Dynamic Media synchronisiert wurden:

| **Eigenschaft** | **Beispiel** | **Beschreibung** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a\|364266`** | Allgemeiner Indikator dafür, dass der Knoten mit Dynamic Media verknüpft ist. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** oder Fehlertext | Status des Hochladens der Assets in Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Muss ausgefüllt werden, um URLs zu Remote-Assets von Dynamic Media zu generieren. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **Erfolg** oder **fehlgeschlagen:`<error text>`** | Synchronisierungsstatus für Sets (Rotationssets, Bildsets usw.), Bildvorgaben, Viewer-Vorgaben oder Imagemap-Updates für ein Asset oder Bilder, die bearbeitet wurden. |

### Protokollierung der Synchronisierung {#synchronization-logging}

Synchronisierungsfehler und -probleme werden in der Datei `error.log` (Experience Manager-Server-Verzeichnis `/crx-quickstart/logs/`) protokolliert. Anhand der protokollierten Informationen lassen sich die Hauptursachen der meisten Probleme ermitteln. Sie können die Protokollierung aber auch im Paket `com.adobe.cq.dam.ips` über die Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) auf DEBUG heraufsetzen, um mehr Informationen zu erfassen.

### Verschieben, Kopieren, Löschen {#move-copy-delete}

Führen Sie folgende Schritte aus, bevor Sie einen Verschiebe-, Kopier- oder Löschvorgang ausführen:

* Prüfen Sie für Bilder und Videos, ob der Wert `<object_node>/jcr:content/metadata/dam:scene7ID` vorhanden ist, bevor Sie Verschiebe-, Kopier- oder Löschvorgänge ausführen.
* Prüfen Sie für Bild- und Viewer-Vorgaben, ob der Wert `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` vorhanden ist, bevor Sie Verschiebe-, Kopier- oder Löschvorgänge ausführen.
* Wenn der obige Metadatenwert fehlt, müssen Sie Assets erneut hochladen, bevor Sie Verschiebe-, Kopier- oder Löschvorgänge ausführen.

### Versionskontrolle {#version-control}

Wenn Sie ein vorhandenes Dynamic Media-Asset (gleicher Name und Speicherort) ersetzen, können Sie beide Assets beibehalten oder eine Version ersetzen/erstellen.

* Wenn Sie beide beibehalten, wird ein neues Asset mit einem eindeutigen Namen für die veröffentlichte Asset-URL erstellt. Beispiel: `image.jpg` ist das ursprüngliche Asset und `image1.jpg` ist das neu hochgeladene Asset.

* Das Erstellen einer Version wird im Scene7-Modus von Dynamic Media nicht unterstützt. Die neue Version ersetzt das vorhandene Asset in der Bereitstellung.

## Bilder und Sets {#images-and-sets}

Falls Sie Probleme mit Bildern und Sets haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Vorgehensweise beim Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Kein Zugriff auf Schaltfläche „URL kopieren“/„Code einbetten“ in der Asset-Detailansicht</td>
   <td>
    <ol>
     <li><p>Öffnen Sie CRX/DE:</p>
      <ul>
       <li>Überprüfen Sie, ob die Vorgabe im JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> definiert ist. Dieser Speicherort trifft zu, wenn Sie ein Upgrade von Experience Manager 6.x auf 6.4 durchgeführt und sich gegen die Migration entschieden haben. Andernfalls ist der Speicherort <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Überprüfen Sie, ob das Asset im JCR unter „Metadaten“ für <code>dam:scene7FileStatus</code><strong> </strong>den Wert <code>PublishComplete</code> aufweist.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Aktualisieren Sie die Seite/gehen Sie zu einer anderen Seite und kehren Sie dann zurück (Seitenleisten-JSPs müssen neu kompiliert werden).</p> <p>Wenn dies das Problem nicht behebt:</p>
    <ul>
     <li>Veröffentlichen Sie das Asset.</li>
     <li>Laden Sie das Asset erneut hoch und veröffentlichen Sie es.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Asset-Auswahl im Set-Editor bleibt beim permanenten Laden hängen</td>
   <td><p>Bekanntes Problem, das in 6.4 behoben wird</p> </td>
   <td><p>Schließen Sie die Auswahl und öffnen Sie sie erneut.</p> </td>
  </tr>
  <tr>
   <td>Schaltfläche <strong>Auswählen</strong> ist nicht aktiv, nachdem ein Asset beim Bearbeiten eines Sets ausgewählt wurde</td>
   <td><p> </p> <p>Bekanntes Problem, das in 6.4 behoben wird</p> <p> </p> </td>
   <td><p>Klicken Sie in der Asset-Auswahl zuerst auf einen anderen Ordner und kehren Sie dann zurück, um das Asset auszuwählen.</p> </td>
  </tr>
  <tr>
   <td>Karussell-Hotspot verschiebt sich nach dem Wechsel zwischen Folien</td>
   <td><p>Überprüfen Sie, ob alle Folien die gleiche Größe aufweisen.</p> </td>
   <td><p>Verwenden Sie nur Bilder mit der gleichen Größe für das Karussell.</p> </td>
  </tr>
  <tr>
   <td>Bild wird im Viewer für Dynamic Media nicht als Vorschau angezeigt</td>
   <td><p>Überprüfen Sie, ob das Asset <code>dam:scene7File</code> in den Metadateneigenschaften (CRXDE Lite) enthält.</p> </td>
   <td><p>Überprüfen Sie, ob alle Assets verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Hochgeladenes Asset wird nicht in der Asset-Auswahl angezeigt</td>
   <td><p>Überprüfen Sie, ob das Asset die Eigenschaft <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite) aufweist.</p> </td>
   <td><p>Überprüfen Sie, ob alle Assets verarbeitet wurden.</p> </td>
  </tr>
  <tr>
   <td>Banner wird in der Kartenansicht als <strong>Neu</strong> angezeigt, wenn die Verarbeitung des Assets noch nicht gestartet wurde</td>
   <td>Überprüfen Sie <code>jcr:content</code> &gt; <code>dam:assetState</code> für das Asset. Wenn <code>unprocessed</code>, dann wurde es nicht vom Workflow abgeholt</td>
   <td>Warten Sie, bis das Asset vom Workflow abgerufen wurde.</td>
  </tr>
  <tr>
   <td>Bilder oder Sets zeigen weder die Viewer-URL noch den eingebetteten Code an</td>
   <td>Überprüfen Sie, ob die Viewer-Vorgabe veröffentlicht wurde.</td>
   <td><p>Wechseln Sie zu <strong>Tools</strong> &gt; <strong>Assets</strong> &gt; <strong>Viewer-Vorgaben</strong> und veröffentlichen Sie die Viewer-Vorgabe.</p> </td>
  </tr>
 </tbody>
</table>

## Video {#video}

Falls Sie Probleme mit Videos haben, sehen Sie sich die folgende Anleitung zur Fehlerbehebung an.

<table>
 <tbody>
  <tr>
   <td><strong>Problem</strong></td>
   <td><strong>Vorgehensweise beim Debugging</strong></td>
   <td><strong>Lösung</strong></td>
  </tr>
  <tr>
   <td>Video kann nicht als Vorschau angezeigt werden</td>
   <td>
    <ul>
     <li>Überprüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist (falls nicht unterstütztes Dateiformat). Falls nicht unterstützt, wird nur ein Bild angezeigt.</li>
     <li>Das Videoprofil muss mehr als eine Kodierungsvorgabe enthalten, damit ein AVS-Set generiert werden kann (einzelne Kodierungen werden als Videoinhalt für MP4-Dateien behandelt; nicht unterstützte Dateien werden wie nicht verarbeitete Dateien behandelt).</li>
     <li>Überprüfen Sie anhand von <code>dam:scene7FileAvs</code> von <code>dam:scene7File</code> in den Metadaten, ob die Verarbeitung des Videos abgeschlossen wurde.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Weisen Sie dem Ordner ein Videoprofil zu.</li>
     <li>Bearbeiten Sie das Videoprofil so, dass es mehr als eine Kodierungsvorgabe enthält.</li>
     <li>Warten Sie, bis die Verarbeitung des Videos abgeschlossen ist.</li>
     <li>Stellen Sie sicher, dass der Workflow für die Dynamic Media-Videokodierung nicht ausgeführt wird, bevor Sie das Video erneut laden.<br /> </li>
     <li>Laden Sie das Video erneut hoch.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video ist nicht kodiert</td>
   <td>
    <ul>
     <li>Prüfen Sie, ob der Ausführungsmodus <code>dynamicmedia_scene7</code> ist.</li>
     <li>Überprüfen Sie, ob Dynamic Media Cloud Service konfiguriert ist.</li>
     <li>Prüfen Sie, ob dem Upload-Ordner ein Videoprofil zugeordnet ist.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Überprüfen Sie Ihre Experience Manager-Instanz mit <code>-r dynamicmedia_scene7</code></li>
     <li>Prüfen Sie, ob die Dynamic Media-Konfiguration unter Cloud Services ordnungsgemäß eingerichtet ist.</li>
     <li>Überprüfen Sie, ob der Ordner über ein Videoprofil verfügt. Überprüfen Sie außerdem das Videoprofil.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Die Videoverarbeitung dauert zu lange</td>
   <td><p>So prüfen Sie, ob die Videokodierung noch läuft oder ob ein Fehler aufgetreten ist:</p>
    <ul>
     <li>Überprüfen Sie den Videostatus <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
     <li>Überwachen Sie das Video in der Workflow-Konsole <code>https://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Registerkarten „Instanzen“, „Archiv“, „Fehler“.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Videoausgabedarstellung fehlt</td>
   <td><p>Wenn das Video hochgeladen wurde, aber keine kodierten Ausgabedarstellungen vorhanden sind:</p>
    <ul>
     <li>Prüfen Sie, ob dem Ordner ein Videoprofil zugewiesen ist.</li>
     <li>Prüfen Sie anhand von <code>dam:scene7FileAvs</code> in den Metadaten, ob die Verarbeitung des Videos abgeschlossen wurde.</li>
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

### Problem: Viewer-Vorgaben werden nicht veröffentlicht {#viewers-not-published}

**Vorgehensweise beim Debugging**

1. Wechseln Sie zur Diagnoseseite des Beispiel-Managers: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`.
1. Überwachen Sie die berechneten Werte. Bei ordnungsgemäßer Funktion sehen Sie Folgendes: `_DMSAMPLE status: 0 unsyced assets - activation not necessary _OOTB status: 0 unsyced assets - 0 unactivated assets`.

   >[!NOTE]
   >
   >Nach der Konfiguration der Dynamic Media-Cloud-Einstellungen kann es bis zu 10 Minuten dauern, bis die Assets im Viewer synchronisiert werden.

1. Falls weiterhin nicht aktivierte Assets vorhanden sind, klicken Sie auf eine der Schaltflächen **Alle nicht aktivierten Assets auflisten**, um die Details anzuzeigen.

**Lösung**

1. Navigieren Sie in den Admin Tools zur Liste der Viewer-Vorgaben: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`
1. Wählen Sie alle Viewer-Vorgaben aus und klicken Sie auf **Veröffentlichen**.
1. Navigieren Sie zurück zum Beispiel-Manager und prüfen Sie, ob die Anzahl der nicht aktivierten Assets jetzt mit null angegeben wird.

### Problem: Für das Bildmaterial der Viewer-Vorgabe wird für eine Vorschau in den Asset-Details oder für „URL kopieren“/„Code einbetten“ der Fehler 404 zurückgegeben {#viewer-preset-404}

**Vorgehensweise beim Debugging**

Gehen Sie in CRXDE Lite wie folgt vor:

1. Navigieren Sie zum `<sync-folder>/_CSS/_OOTB`-Ordner im Synchronisierungsordner für Dynamic Media (z. B. `/content/dam/_CSS/_OOTB`).
1. Suchen Sie den Metadaten-Knoten des problematischen Assets (z. B. `<sync-folder>/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/`).
1. Prüfen Sie, ob die Eigenschaften `dam:scene7*` vorhanden sind. Wenn das Asset erfolgreich synchronisiert und veröffentlicht wurde, sehen Sie, dass für `dam:scene7FileStatus` der Wert **PublishComplete** festgelegt ist.
1. Versuchen Sie, das Bildmaterial direkt aus Dynamic Media anzufragen, indem Sie die Werte der folgenden Eigenschaften und Zeichenfolgen verketten:

   * `dam:scene7Domain`
   * `"is/content"`
   * `dam:scene7Folder`
   * `<asset-name>`
Beispiel: `https://<server>/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png`

**Lösung**

Wenn die Beispiel-Assets oder das Bildmaterial der Viewer-Vorgabe nicht synchronisiert oder veröffentlicht wurden, starten Sie den gesamten Kopier-/Synchronisierungsvorgang neu:

1. Gehen Sie zu CRXDE Lite.
1. Löschen Sie `<sync-folder>/_CSS/_OOTB`.
1. Navigieren Sie zum CRX Package Manager: `https://localhost:4502/crx/packmgr/`.
1. Suchen Sie das Viewer-Paket in der Liste; es beginnt mit `cq-dam-scene7-viewers-content`.
1. Wählen Sie **Neu installieren** aus.
1. Navigieren Sie zur Seite für die Dynamic Media-Konfiguration und klicken Sie auf „Bearbeiten“, um das Konfigurationsdialogfeld für Ihre Dynamic Media S7-Konfiguration zu öffnen.
1. Nehmen Sie keine Änderungen vor und klicken Sie auf **Speichern**.
Dadurch wird die Logik zum Erstellen und Synchronisieren von Beispiel-Assets, Viewer-Vorgabe-CSS und Bildmaterial erneut ausgelöst.

### Problem: Die Bildvorschau wird beim Bearbeiten von Viewer-Vorgaben nicht geladen {#image-preview-not-loading}

**Lösung**

1. Klicken Sie in Experience Manager auf das Adobe Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in der linken Leiste zum Ordner mit Beispielinhalten am folgenden Speicherort:

   `/content/dam/_DMSAMPLE`

1. Löschen Sie den Ordner `_DMSAMPLE`.
1. Navigieren Sie in der linken Leiste zum Ordner „Vorgaben“ am folgenden Speicherort:

   `/conf/global/settings/dam/dm/presets/viewer`

1. Löschen Sie den Ordner `viewer`.
1. Wählen Sie in der oberen linken Ecke der Seite „CRXDE Lite“ die Option **[!UICONTROL Alle speichern]** aus.
1. Klicken Sie links oben auf der Seite „CRXDE Lite“ auf das Symbol **Zurück zur Startseite**.
1. Erstellen Sie erneut eine [Dynamic Media-Konfiguration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
