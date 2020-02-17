---
title: Integrieren in Dynamic Media Classic (Scene7)
seo-title: Integrieren in Dynamic Media Classic (Scene7)
description: Erfahren Sie, wie Sie AEM mit Dynamic Media Classic integrieren.
seo-description: Erfahren Sie, wie Sie AEM mit Dynamic Media Classic integrieren.
uuid: b014d643-1cc1-47f3-a79c-7f6f9e45637a
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: f55e68c3-3309-4400-bef9-fd3afa6e2b5f
translation-type: tm+mt
source-git-commit: e9c64d214456eed8e0adb29edd60c2350b852a67

---


# Integrieren in Dynamic Media Classic (Scene7){#integrating-with-dynamic-media-classic-scene}

[Adobe Dynamic Media Classic](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und Drucken.

Um Dynamic Media Classic verwenden zu können, müssen Sie die Cloud-Konfiguration so konfigurieren, dass Dynamic Media Classic und AEM Assets miteinander interagieren können. In diesem Dokument wird die Konfiguration von AEM und Dynamic Media Classic beschrieben.

Informationen zur Verwendung aller Komponenten von Dynamic Media Classic auf einer Seite und zum Arbeiten mit Videos finden Sie unter [Verwenden von Dynamic Media Classic](../assets/scene7.md).

>[!NOTE]
>
>* Die DHTML-Viewer-Plattform von Dynamic Media Classic hat am 31. Januar 2014 offiziell das Ende des Lebenszyklus erreicht. Weitere Informationen finden Sie in den [FAQ zur Einstellung von DHTML-Viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Bevor Sie Dynamic Media Classic für die Verwendung mit AEM konfigurieren, lesen Sie die [Best Practices](#best-practices-for-integrating-scene-with-aem) für die Integration von Dynamic Media Classic in AEM.
>* Wenn Sie Dynamic Media Classic mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie sowohl HTTP Client-Proxykonfigurationen konfigurieren, da einige Funktionen von AEM die 3.x-APIs und andere die 4.x-APIs verwenden. 3.x is configured with [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) and 4.x is configured with [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator).
>



## AEM/Dynamic Media Classic-Integration versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

AEM-Benutzer haben die Wahl zwischen zwei Lösungen, um mit dynamischen Medien zu arbeiten: Integrieren Sie entweder die Instanz von AEM mit Dynamic Media Classic oder verwenden Sie die in AEM integrierte Lösung für dynamische Medien.

Verwenden Sie die folgenden Kriterien, um zu bestimmen, welche Lösung ausgewählt werden soll:

* If you are an **existing** Dynamic Media Classic customer whose rich media assets reside in Dynamic Media Classic for publishing and delivery, but you want to integrate those assets with Sites (WCM) authoring and/or AEM Assets for management, then use the [AEM/Dynamic Media Classic point-to-point integration](#aem-scene-point-to-point-integration) described in this document.

* Wenn Sie AEM-**Neukunde** sind und Rich-Media-Bereitstellung benötigen, wählen Sie die [Option „Dynamic Media“](#aem-dynamic-media) aus. Diese Option ist am sinnvollsten, wenn Sie über kein vorhandenes S7-Konto verfügen und wenn Sie nicht über viele im System gespeicherte Assets verfügen.

* In bestimmten Fällen möchten Sie vielleicht beide Lösungen verwenden. The [dual-use scenario](/help/sites-administering/scene7.md#dual-use-scenario) describes that scenario.

### AEM/Dynamic Media Classic-Point-to-Point-Integration {#aem-scene-point-to-point-integration}

Wenn Sie in dieser Lösung mit Assets arbeiten, nutzen Sie eine der folgenden Vorgehensweisen:

* Hochladen von Assets direkt auf Dynamic Media Classic und anschließenden Zugriff über den Browser für **Dynamic Media Classic** -Inhalte zum Erstellen von Seiten oder
* Upload to AEM Assets and then enable automatic publishing to Dynamic Media Classic; you access via **Assets** content browser for page authoring

The components you use for this integration are found in the **Dynamic Media Classic** component area in [Design mode.](/help/sites-authoring/author-environment-tools.md#page-modes)

### AEM Dynamic Media {#aem-dynamic-media}

AEM Dynamic Media ist die Vereinigung der Funktionen von Dynamic Media Classic direkt innerhalb der AEM-Plattform.

Wenn Sie innerhalb dieser Lösung mit Assets arbeiten, befolgen Sie diesen Workflow:

1. Laden Sie Assets mit einzelnen Bildern und Videos direkt in AEM hoch.
1. Kodieren Sie Videos direkt in AEM.
1. Erstellen Sie bildbasierte Sets direkt in AEM.
1. Fügen Sie Bildern und Videos bei Bedarf interaktive Elemente hinzu.

Die von Ihnen für Dynamic Media verwendeten Komponenten befinden sich im Komponentenbereich **[!UICONTROL Dynamic Media]** im [Designmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Sie umfassen Folgendes:

* **[!UICONTROL Dynamic Media]** – Die Komponente **[!UICONTROL Dynamic Media]** ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, gemischte Mediensets und Videos. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

* **[!UICONTROL Interaktive Medien]** - Die Komponente für **[!UICONTROL interaktive Medien]** ist für Assets wie Karussell-Banner, interaktive Bilder und interaktive Videos bestimmt, die interaktive Elemente wie Hotspots oder Imagemaps enthalten. Die Komponente ist intelligent – je nachdem, ob Sie ein Bild oder Video hinzufügen, werden Ihnen unterschiedliche Optionen zur Verfügung gestellt. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

### Szenario einer Doppelnutzung {#dual-use-scenario}

Standardmäßig können Sie die Integrationsfunktionen von AEM für dynamische Medien und Dynamic Media Classic gleichzeitig verwenden. Die folgende Tabelle mit Anwendungsfällen beschreibt, wann Sie bestimmte Bereiche ein- und ausschalten.

So verwenden Sie dynamische Medien und Dynamic Media Classic gleichzeitig:

1. Konfigurieren Sie [Dynamic Media Classic](#creating-a-cloud-configuration-for-scene) in Cloud-Diensten.
1. Befolgen Sie die Anleitungen, die auf Ihr jeweiliges Nutzungsszenario zutreffen:

   <table>
    <tbody>
    <tr>
    <td> </td>
    <td> </td>
    <td><strong>Dynamic Media</strong></td>
    <td> </td>
    <td><strong>Dynamic Media Classic-Integration</strong></td>
    <td> </td>
    </tr>
    <tr>
    <td><strong>Wenn Sie sind ...</strong></td>
    <td><strong>Verwendungsfallarbeitsablauf</strong></td>
    <td><strong>Imaging/Video</strong></td>
    <td><strong>Komponente „Dynamische Medien“</strong></td>
    <td><strong>S7 Content Browser und Komponenten</strong></td>
    <td><strong>Automatisches Hochladen von Assets auf S7</strong></td>
    </tr>
    <tr>
    <td>Neu bei Sites und dynamischen Medien</td>
    <td>Hochladen von Assets in AEM und Verwenden der AEM Dynamic Media-Komponente zum Erstellen von Assets auf Siteseiten</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td>Off</td>
    <td>Off</td>
    </tr>
    <tr>
    <td>Im Handel und sind neu bei Sites und dynamischen Medien</td>
    <td>Hochladen von Nicht-Produkt-Assets zu AEM zur Verwaltung und Bereitstellung Laden Sie PRODUKT-Assets in Dynamic Media Classic hoch und verwenden Sie den Browser für dynamische Medien-Classic-Inhalte in AEM und einer Komponente, um Produktdetailseiten auf Sites zu erstellen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Off</td>
    </tr>
    <tr>
    <td>Neu bei Assets und dynamischen Medien</td>
    <td>Hochladen von Assets in AEM Assets und Verwenden von veröffentlichtem URL-/Einbettungscode aus dynamischen Medien</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Off</td>
    <td>Off</td>
    <td>Off</td>
    </tr>
    <tr>
    <td>Neu bei dynamischen Medien und Vorlagen</td>
    <td>Verwenden Sie dynamische Medien für Bildbearbeitung und Video. Erstellen Sie Bildvorlagen in Dynamic Media Classic und verwenden Sie die Inhaltssuche für Dynamic Media Classic, um Vorlagen in Seiten mit Sites einzuschließen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Off</td>
    </tr>
    <tr>
    <td>Ein vorhandener Kunde von Dynamic Media Classic und neu bei Sites</td>
    <td>Hochladen von Assets in Dynamic Media Classic und Verwenden des AEM Dynamic Media Classic-Inhaltsbrowsers, um Assets auf Siteseiten zu suchen und zu erstellen</td>
    <td>Off</td>
    <td>Off</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Off</td>
    </tr>
    <tr>
    <td>Ein vorhandener Kunde von Dynamic Media Classic, der neu bei Sites und Assets ist</td>
    <td>Laden Sie Assets zu DAM hoch und veröffentlichen Sie sie automatisch zur Bereitstellung auf Dynamic Media Classic. Verwenden Sie den AEM Dynamic Media Classic-Inhaltsbrowser, um Assets auf Siteseiten zu suchen und zu erstellen.</td>
    <td>Off</td>
    <td>Off</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    <tr>
    <td>Bestehender Kunde von Dynamic Media Classic und neuer Kunde von Assets</td>
    <td><p>Laden Sie Assets auf AEM hoch und verwenden Sie dynamische Medien, um Darstellungen zum Herunterladen/Freigeben zu generieren. Veröffentlichen Sie AEM-Assets automatisch für die Bereitstellung in Dynamic Media Classic.</p> <p><strong></strong> Wichtig: Incurs duplicate processing and renditions created in AEM will not be synchronisation to Dynamic Media Classic</p> </td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Off</td>
    <td>Off</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (Optional; see use case table) - Set up the [Dynamic Media cloud configuration](/help/assets/config-dynamic.md) and [enable the Dynamic Media server](/help/assets/config-dynamic.md).
1. (Optional) (siehe Verwendungsfalltabelle) - Wenn Sie die Option &quot;Automatisches Hochladen von Assets zu Dynamisch Media Classic&quot;aktivieren, müssen Sie Folgendes hinzufügen:

   1. Richten Sie den automatischen Upload auf Dynamic Media Classic ein.
   1. Fügen Sie den Schritt zum Hochladen **von** Dynamischen Medien in Classic nach allen Schritten des Arbeitsablaufs für dynamische Medien *am Ende* des Arbeitsablaufs für **DAM-Aktualisierung von Assets** hinzu ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Optional) Restrict Dynamic Media Classic asset upload by MIME type in [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl). Asset-MIME-Typen, die nicht in dieser Liste aufgeführt sind, werden nicht auf den Dynamic Media Classic-Server hochgeladen.
   1. (Optional) Richten Sie Videos in der Konfiguration von Dynamic Media Classic ein. Sie können die Videokodierung für entweder dynamische Medien und Dynamic Media Classic gleichzeitig aktivieren. Dynamische Darstellungen werden für die lokale Vorschau und Wiedergabe in der AEM-Instanz verwendet, während Videodarstellungen von Dynamischer Media Classic auf Servern von Dynamic Media Classic generiert und gespeichert werden. When setting up video encoding services for both Dynamic Media and Dynamic Media Classic, apply a [video processing profile](/help/assets/video-profiles.md) to the Dynamic Media Classic asset folder.
   1. (Optional) Sichere Vorschau in Dynamic Media Classic [konfigurieren](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beschränkungen {#limitations}

Wenn Sie sowohl dynamische Medien als auch klassische Medien aktiviert haben, gelten folgende Einschränkungen:

* Das manuelle Hochladen auf Dynamic Media Classic durch Auswahl eines Assets und Ziehen auf eine Komponente des Typs Dynamic Media Classic auf einer AEM-Seite funktioniert nicht.
* Obwohl synchronisierte Assets mit AEM-Dynamic Media Classic automatisch auf Dynamic Media Classic aktualisiert werden, wenn das Asset in Assets bearbeitet wird, löst eine Rollback-Aktion keinen neuen Upload aus. Daher erhält Dynamic Media Classic nicht die neueste Version unmittelbar nach einem Rollback. Als Ausweichlösung eignet sich die erneute Bearbeitung, sobald das Rollback abgeschlossen ist.
* Wenn Sie dynamische Medien für einen Verwendungsfall und die Integration von Dynamic Media Classic für einen anderen Anwendungsfall verwenden müssen, damit die dynamischen Medien-Assets nicht mit dem System Dynamic Media Classic interagieren, wenden Sie die Konfiguration von Dynamic Media Classic nicht auf den Ordner &quot;Dynamic Media&quot;oder die Konfiguration von dynamischen Medien (Verarbeitungsprofil) auf einen Ordner von Dynamic Media Classic an.

## Best Practices für die Integration von Dynamic Media Classic mit AEM {#best-practices-for-integrating-scene-with-aem}

Bei der Integration von Dynamic Media Classic mit AEM gibt es einige wichtige Best Practices, die in den folgenden Bereichen beachtet werden müssen:

* Testen Ihrer Integration
* Hochladen von Assets direkt von Dynamic Media Classic empfohlen für bestimmte Szenarien

Siehe [bekannte Einschränkungen](#known-limitations-and-design-implications).

### Testen Ihrer Integration {#test-driving-your-integration}

Adobe empfiehlt, dass Sie Ihre Integration testen und testen, indem Sie den Stammordner nur auf einen Unterordner und nicht auf ein ganzes Unternehmen verweisen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto des Unternehmens &quot;Dynamic Media Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets und kann zum Absturz Ihres Systems führen).

### Hochladen von Assets aus AEM Assets im Vergleich zu Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

Sie können Assets entweder mit der Funktion &quot;Assets&quot;(Digital Asset Management) oder durch direkten Zugriff auf &quot;Dynamic Media Classic&quot;in AEM über den Content Browser &quot;Dynamic Media Classic&quot;hochladen. Was davon Sie verwenden, hängt von den folgenden Faktoren ab:

* Die von AEM Assets noch nicht unterstützten Asset-Typen von Dynamic Media Classic müssen direkt von Dynamic Media Classic über den Content Browser von Dynamic Media Classic, z. B. Bildvorlagen, zu einer AEM-Website hinzugefügt werden.
* Bei Asset-Typen, die von AEM Assets und Dynamic Media Classic unterstützt werden, hängt die Entscheidung, wie sie hochgeladen werden, von Folgendem ab:

   * Wo sich die Assets heute befinden UND
   * Wie wichtig ihre Verwaltung in einem gemeinsamen Repository ist

Wenn sich die Assets bereits in Dynamic Media Classic befinden und ihre Verwaltung in einem gemeinsamen Repository nicht so wichtig ist, wäre der Export in AEM Assets nur zur Synchronisierung mit Dynamic Media Classic für die Bereitstellung ein unnötiger Roundtrip. Andernfalls ist es empfehlenswert, Assets nur zur Bereitstellung in einem einzigen Repository zu speichern und mit Dynamic Media Classic zu synchronisieren.

## Configuring Dynamic Media Classic integration {#configuring-scene-integration}

Sie können AEM so konfigurieren, dass Assets in Dynamic Media Classic hochgeladen werden. Assets aus einem CQ-Zielordner können (automatisch oder manuell) von AEM in ein Unternehmenskonto von Dynamic Media Classic hochgeladen werden.

>[!NOTE]
>
>Adobe empfiehlt, nur den festgelegten Zielordner zum Importieren von Dynamischen Medien-Classic-Assets zu verwenden. Digitale Assets, die sich außerhalb des Zielordners befinden, können nur in Komponenten von Dynamic Media Classic auf Seiten verwendet werden, auf denen die Konfiguration von Dynamic Media Classic aktiviert wurde. Darüber hinaus werden sie in einem Ad-hoc-Ordner in Dynamic Media Classic abgelegt. Der Ad-hoc-Ordner wird nicht mit AEM synchronisiert (Assets können jedoch im Inhaltsbrowser von Dynamic Media Classic gefunden werden).

Um die Integration von Dynamic Media Classic in AEM zu konfigurieren, müssen Sie die folgenden Schritte ausführen:

1. [Cloud-Konfiguration](#creating-a-cloud-configuration-for-scene) definieren - Definiert die Zuordnung zwischen einem Ordner &quot;Dynamic Media Classic&quot;und einem Ordner &quot;Assets&quot;. Sie müssen diesen Schritt auch dann ausführen, wenn Sie nur eine einmalige Synchronisierung (AEM Assets to Dynamic Media Classic) wünschen.
1. [Aktivieren Sie **Adobe CQ s7dam Dam Listener **](#enabling-the-adobe-cq-scene-dam-listener)- Fertig in der[!UICONTROL OSGi]-Konsole.
1. Wenn Sie möchten, dass AEM-Assets automatisch in Dynamic Media Classic hochgeladen werden, müssen Sie diese Option aktivieren und dem DAM-Arbeitsablauf zum Aktualisieren von Assets hinzufügen. Außerdem können Sie manuell Assets hochladen.
1. Hinzufügen von Komponenten aus Dynamic Media Classic zum Sidekick. Auf diese Weise können die Benutzer auf ihren AEM-Seiten Dynamic Media Classic-Komponenten verwenden.
1. [Ordnen Sie die Konfiguration der Seite in AEM](#enabling-scene-for-wcm) zu - Dieser Schritt ist erforderlich, um alle Video-Vorgaben anzuzeigen, die Sie in Dynamic Media Classic erstellt haben. Es ist auch erforderlich, wenn Sie ein Asset von außerhalb des CQ-Zielordners in Dynamic Media Classic veröffentlichen müssen.

In diesem Abschnitt wird die Durchführung all dieser Schritte behandelt und es werden wichtige Beschränkungen aufgeführt.

### Funktionsweise der Synchronisierung zwischen Dynamic Media Classic und AEM Assets {#how-synchronization-between-scene-and-aem-assets-works}

Beim Einrichten der Synchronisierung von AEM Assets und Dynamic Media Classic ist Folgendes wichtig:

#### Hochladen von AEM-Assets zu Dynamic Media Classic {#uploading-to-scene-from-aem-assets}

* In AEM für Dynamic Media Classic-Uploads ist ein bestimmter Synchronisierungsordner vorhanden.
* Uploads in Dynamic Media Classic können automatisiert werden, wenn die digitalen Assets in dem angegebenen Synchronisierungsordner abgelegt werden.
* Die Ordner- und Unterordnerstruktur in AEM wird in Dynamic Media Classic repliziert.

>[!NOTE]
>
>AEM bettet alle Metadaten als XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadaten-Knoten in Dynamic Media Classic als XMP verfügbar sind.

#### Bekannte Beschränkungen und Designimplikationen {#known-limitations-and-design-implications}

Bei der Synchronisierung zwischen AEM Assets und Dynamic Media Classic gibt es derzeit die folgenden Einschränkungen/Auswirkungen auf das Design:

<table>
 <tbody>
  <tr>
   <td><strong>Implikation von Einschränkungen/Design</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Ein angegebener Synchronisierungs-(Ziel-)Ordner</td>
   <td>Pro Unternehmen kann in AEM nur ein bestimmter Ordner für Dynamic Media Classic-Uploads verwendet werden. Sie können mehrere Konfigurationen erstellen, wenn Sie Zugriff auf mehr als ein Unternehmenskonto in Dynamic Media Classic benötigen.</td>
  </tr>
  <tr>
   <td>Ordnerstruktur</td>
   <td>Wenn Sie einen synchronisierten Ordner mit Assets löschen, werden alle Remote-Assets von Dynamic Media Classic gelöscht, der Ordner bleibt jedoch erhalten.</td>
  </tr>
  <tr>
   <td>Ad-hoc-Ordner</td>
   <td>Assets, die sich außerhalb des Zielordners befinden und manuell in den WCM-Ordner "Dynamic Media Classic"hochgeladen werden, werden automatisch in einen separaten Ad-hoc-Ordner unter "Dynamic Media Classic"verschoben. Dies wird in der Cloud-Konfiguration in AEM konfiguriert.</td>
  </tr>
  <tr>
   <td>Gemischte Medien</td>
   <td>Gemischte Mediensets werden in AEM angezeigt, obwohl sie in AEM nicht unterstützt werden.</td>
  </tr>
  <tr>
   <td>PDFs </td>
   <td>Generierte PDFs aus E-Katalogen in Dynamic Media Classic werden in den CQ-Zielordner importiert.</td>
  </tr>
  <tr>
   <td>Aktualisieren der Benutzeroberfläche</td>
   <td>Stellen Sie bei der Synchronisierung zwischen AEM und Dynamic Media Classic sicher, dass Sie die Benutzeroberfläche aktualisieren, um die Änderungen anzuzeigen. </td>
  </tr>
  <tr>
   <td>Videominiaturen</td>
   <td>Wenn Sie ein Video zur Kodierung über Dynamic Media Classic in AEM Assets hochladen, kann es abhängig von der Videoverarbeitung einige Zeit dauern, bis die Video-Miniaturansichten und kodierten Videos in AEM Assets verfügbar sind.</td>
  </tr>
  <tr>
   <td>Zielunterordner</td>
   <td><p>Wenn Sie Unterordner im Zielordner verwenden, stellen Sie sicher, dass Sie entweder eindeutige Namen für jedes Asset verwenden (unabhängig vom Speicherort) oder dass Sie Dynamic Media Classic (im Bereich "Einstellungen") so konfigurieren, dass Assets nicht unabhängig vom Speicherort überschrieben werden.</p> <p>Andernfalls werden Assets mit demselben Namen, die in einen Target-Unterordner von Dynamic Media Classic hochgeladen werden, hochgeladen, der gleichnamige Asset im Zielordner wird jedoch gelöscht. </p> </td>
  </tr>
 </tbody>
</table>

### Configuring Dynamic Media Classic servers {#configuring-scene-servers}

Wenn Sie AEM hinter einem Proxy ausführen oder besondere Firewall-Einstellungen haben, müssen Sie möglicherweise die Hosts der verschiedenen Regionen explizit aktivieren. Servers are managed in content in `/etc/cloudservices/scene7/endpoints` and can be customized as required. Tippen Sie auf eine URL und bearbeiten Sie die URL bei Bedarf. In früheren Versionen von AEM waren diese Werte hartkodiert.

If you navigate to `/etc/cloudservices/scene7/endpoints.html`, you see the servers listed (and can edit them by clicking on the URL):

![chlimage_1-296](assets/chlimage_1-296.png)

### Erstellen einer Cloud-Konfiguration für Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Eine Cloud-Konfiguration definiert die Zuordnung zwischen einem Ordner &quot;Dynamic Media Classic&quot;und einem Ordner &quot;AEM Assets&quot;. Es muss konfiguriert werden, um AEM Assets mit Dynamic Media Classic zu synchronisieren. Unter Funktionsweise der Synchronisierung finden Sie weitere Informationen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto des Unternehmens &quot;Dynamic Media Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

>[!NOTE]
>
>Sie können über mehrere Konfigurationen verfügen: Eine Cloud-Konfiguration stellt einen Benutzer in einem Unternehmen von Dynamic Media Classic dar. Wenn Sie auf andere Unternehmen oder Benutzer von Dynamic Media Classic zugreifen möchten, müssen Sie mehrere Konfigurationen erstellen.

So konfigurieren Sie AEM für das Veröffentlichen von Assets in Dynamic Media Classic:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud-Services]** , um auf Adobe Dynamic Media Classic zuzugreifen.

1. Tippen Sie auf Jetzt **[!UICONTROL konfigurieren]**.

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** und optional im Feld **[!UICONTROL Name]** die entsprechenden Informationen ein. Tippen Sie auf **[!UICONTROL Erstellen]**.

   >[!NOTE]
   >
   >Beim Erstellen zusätzlicher Konfigurationen wird das Feld **[!UICONTROL Übergeordnete Konfiguration]** angezeigt.
   >
   >Ändern Sie **nicht** die übergeordnete Konfiguration. Das Ändern der übergeordneten Konfiguration kann zum Scheitern der Integration führen.

1. Geben Sie die E-Mail-Adresse, das Kennwort und die Region Ihres Kontos für Dynamic Media Classic ein und tippen Sie auf **[!UICONTROL Verbindung zu Dynamic Media Classic]** herstellen. Sie sind mit dem Dynamic Media Classic-Server verbunden und das Dialogfeld wird mit weiteren Optionen erweitert.

1. Enter the **[!UICONTROL Company]** name and **[!UICONTROL Root Path]** (this is the published server name together with any path you want to specify; if you do not know the published server name, in Dynamic Media Classic, go to **[!UICONTROL Setup > Application Setup]**.)

   >[!NOTE]
   >
   >Der Stammpfad von Dynamic Media Classic ist der Ordner &quot;Dynamic Media Classic&quot;, mit dem AEM eine Verbindung herstellt. Es kann auf einen spezifischen Ordner eingegrenzt werden.

   >[!CAUTION]
   >
   >Je nach der Größe des Ordners &quot;Dynamic Media Classic&quot;kann es lange dauern, einen Stammordner zu importieren. Darüber hinaus können die Daten von Dynamic Media Classic den AEM-Speicher überschreiten. Stellen Sie sicher, dass Sie in den richtigen Ordner importieren. Der Import einer zu großen Menge von Daten kann zur Unterbrechung Ihres Systems führen.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Klicken Sie auf **[!UICONTROL OK]**. AEM speichert Ihre Konfiguration.

>[!NOTE]
>
>Wenn Sie eine erneute Verbindung herstellen:
>
>* Wenn Sie beim Veröffentlichen wieder eine Verbindung zu Dynamic Media Classic herstellen, müssen Sie das Kennwort beim Veröffentlichen zurücksetzen, sonst funktioniert die erneute Verbindung nicht. Bei der Autoreninstanz stellt dies kein Problem dar.
>* Wenn Sie Werte wie Region, Firmenname ändern, müssen Sie die Verbindung zu Dynamic Media Classic wiederherstellen. Wenn Konfigurationsoptionen geändert, aber nicht gespeichert wurden, zeigt AEM fälschlicherweise nach wie vor an, dass die Konfiguration gültig ist. Achten Sie darauf, eine erneute Verbindung herzustellen.
>



### Aktivieren des Adobe CQ Dynamic Media Classic Dam Listener {#enabling-the-adobe-cq-scene-dam-listener}

Sie müssen den Adobe CQ Dynamic Media Classic Dam Listener aktivieren, der standardmäßig deaktiviert ist.

So aktivieren Sie ihn:

1. Tap the [!UICONTROL Tools] icon, then navigate to **[!UICONTROL Operations > Web Console]**. Die Web-Konsole wird geöffnet.
1. Navigate to **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** and select the **[!UICONTROL Enabled]** check box.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### Hinzufügen eines konfigurierbaren Timeouts zum Workflow für das Hochladen von Dynamischen Medien mit Classic {#adding-configurable-timeout-to-scene-upload-workflow}

Wenn eine AEM-Instanz so konfiguriert wird, dass die Videokodierung durch Dynamic Media Classic (Scene7) abgewickelt wird, gibt es standardmäßig ein 35-minütiges Timeout zu jedem Upload-Auftrag. Um Videokodierungsaufträge mit potenziell längerer Dauer zu ermöglichen, können Sie diese Einstellung konfigurieren:

1. Navigate to **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Ändern Sie die Zahl wie gewünscht im Feld **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]**. Jede positive Zahl wird binnen Sekunden mit der Maßeinheit akzeptiert. Standardmäßig ist dies auf 2100 festgelegt.

   >[!NOTE]
   >
   >Best Practice: Bei den meisten Assets dauert das Übernehmen höchstens einige Minuten (beispielsweise bei Bildern). Doch in bestimmten Fällen – beispielsweise bei größeren Videos – sollte der Timeout-Wert auf 7200 Sekunden (2 Stunden) erhöht werden, um eine lange Verarbeitungszeit zu ermöglichen. Otherwise, this Dynamic Media Classic upload job is marked as **[!UICONTROL UploadFailed]** in the JCR metadata.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### Automatisches Hochladen von AEM Assets {#autouploading-from-aem-assets}

Ab AEM 6.3.2 sind AEM Assets jetzt für Sie konfiguriert, sodass alle digitalen Assets, die Sie in den Digital Asset Manager hochladen, automatisch auf Dynamic Media Classic aktualisiert werden, wenn sich die Assets in einem CQ-Zielordner befinden.

Wenn ein Asset zu AEM Assets hinzugefügt wird, wird es automatisch hochgeladen und auf Dynamic Media Classic veröffentlicht.

>[!NOTE]
>
>Die maximale Dateigröße für das automatische Hochladen von AEM Assets zu Dynamic Media Classic beträgt 500 MB.

So wird das automatische Hochladen von AEM Assets konfiguriert:

1. Tap the AEM icon and navigate to **[!UICONTROL Deployment > Cloud Services]** then, under the Dynamic Media heading, under Available Configurations, tap **[!UICONTROL dms7 (Dynamic Media]**)
1. Tap the **[!UICONTROL Advanced]** tab, select the **[!UICONTROL Enable Automatic Upload]** check box, then tap **[!UICONTROL OK]**. Sie müssen jetzt den DAM-Asset-Workflow so konfigurieren, dass auch Hochladen in Dynamic Media Classic einbezogen wird.

   >[!NOTE]
   >
   >See [Configuring the state (published/unpublished) of assets pushed to Dynamic Media Classic](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) for information on pushing assets to Dynamic Media Classic in an unpublished state.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Navigate back to the AEM welcome page and tap **[!UICONTROL Workflows]**. Doppelklicken Sie auf den Workflow **DAM-Update-Asset**, um ihn zu öffnen.
1. In the sidekick, navigate to the **[!UICONTROL Workflow]** components, and select **[!UICONTROL Dynamic Media Classic]**. Ziehen Sie **[!UICONTROL Dynamic Media Classic]** in den Workflow und tippen Sie auf **[!UICONTROL Speichern]**. Assets, die AEM Assets im Zielordner hinzugefügt wurden, werden automatisch in Dynamic Media Classic hochgeladen.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wenn Assets nach der Automatisierung hinzugefügt und nicht im CQ-Zielordner abgelegt werden, werden sie nicht in Dynamic Media Classic hochgeladen.
   >* AEM bettet alle Metadaten als XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadaten-Knoten in Dynamic Media Classic als XMP verfügbar sind.


### Konfigurieren des Status (veröffentlicht/unveröffentlicht) von Assets, die in Dynamic Media Classic gesendet werden {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Wenn Sie Assets von AEM Assets zu Dynamic Media Classic verschieben, können Sie sie entweder automatisch veröffentlichen (Standardverhalten) oder sie in einem unveröffentlichten Zustand zu Dynamic Media Classic verschieben.

Möglicherweise möchten Sie Assets nicht sofort in Dynamic Media Classic veröffentlichen, wenn Sie sie in einer Staging-Umgebung testen möchten, bevor sie live geschaltet werden. Sie können AEM mit der Secure Test-Umgebung von Dynamic Media Classic verwenden, um Assets in einem unveröffentlichten Zustand direkt von Assets in Dynamic Media Classic zu übertragen.

Dynamic Media Classic-Assets bleiben über eine sichere Vorschau verfügbar. Nur wenn Assets in AEM veröffentlicht werden, werden die dynamischen Medien-Classic-Assets auch in der Produktion live geschaltet.

Wenn Sie Assets sofort veröffentlichen möchten, wenn Sie sie zu Dynamic Media Classic verschieben, müssen Sie keine Optionen konfigurieren. Dies ist das Standardverhalten.

Wenn Sie jedoch nicht möchten, dass Assets, die an Dynamic Media Classic gesendet werden, automatisch veröffentlicht werden, wird in diesem Abschnitt beschrieben, wie Sie AEM und Dynamic Media Classic dazu konfigurieren.

#### Voraussetzungen für das unveröffentlichte Senden von Assets an Dynamic Media Classic {#prerequisites-to-push-assets-to-scene-unpublished}

Bevor Sie Assets an Dynamic Media Classic senden können, ohne sie zu veröffentlichen, müssen Sie Folgendes einrichten:

1. Wenden Sie sich an den Kundendienst von Dynamic Media Classic (s7support@adobe.com), um eine sichere Vorschau für Ihr Konto bei Dynamic Media Classic zu aktivieren.
1. Follow directions to [setup secure preview for your Dynamic Media Classic account.](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html)

Dies sind dieselben Schritte, die Sie ausführen würden, um eine sichere Testeinrichtung in Dynamic Media Classic zu erstellen.

>[!NOTE]
>
>If your installation environment is a Unix 64-bit operating system, see [https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) regarding additional configuration options you need to set.

#### Bekannte Beschränkungen für das Pushen von Assets im nicht veröffentlichten Status  {#known-limitations-for-pushing-assets-in-unpublished-state}

Beachten Sie die folgenden Beschränkungen, wenn Sie diese Funktion verwenden:

* Die Versionskontrolle wird nicht unterstützt.
* Wenn ein Asset bereits in AEM veröffentlicht ist und eine Folgeversion erstellt wurde, wird diese neue Version sofort veröffentlicht und tatsächlich in der Produktion eingesetzt. Die Veröffentlichung zusammen mit der Aktivierung funktioniert nur bei der ersten Veröffentlichung eines Assets.

>[!NOTE]
>
>If you want to publish assets instantly, best practice is to keep **[!UICONTROL Enable Secure Preview]** set to **[!UICONTROL Immediately]** and use the **[!UICONTROL Enable Automatic Upload]** feature.

### Festlegen des Status von Assets, die als unveröffentlicht an Dynamic Media Classic gesendet werden {#setting-the-state-of-assets-pushed-to-scene-as-unpublished}

>[!NOTE]
>
>Wenn ein Benutzer das Asset in AEM veröffentlicht, aktiviert es automatisch das S7-Asset in der Produktion/im Live-Asset (das Asset befindet sich dann nicht mehr in der sicheren Vorschau/im unveröffentlichten Status).

So legen Sie den Status der Assets fest, die an Dynamic Media Classic als unveröffentlicht gesendet werden:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud-Dienste]**, tippen Sie auf **[!UICONTROL Dynamische Medien Classic]** und wählen Sie Ihre Konfiguration in Dynamisch Media Classic aus.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** In the **[!UICONTROL Enable Secure View]** drop-down menu, select **[!UICONTROL Upon AEM Publish Activation]** to push assets to Dynamic Media Classic without publishing. (By default, this value is set to **[!UICONTROL Immediately]**, where Dynamic Media Classic assets are published immediately.)

   See [Dynamic Media Classic documentation](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html) for more information on testing assets before making them public.

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

Die Aktivierung der sicheren Ansicht bedeutet, dass Ihre Assets unveröffentlicht auf den sicheren Vorschauserver gepusht werden.

You can check this by navigating to a Dynamic Media Classic component on a page in AEM and tapping **[!UICONTROL Edit]**. Der sichere Vorschauserver ist in der URL des Assets aufgeführt. Nach der Veröffentlichung in AEM wird die Serverdomäne im Dateiverweis von der Vorschau-URL zur Produktions-URL aktualisiert.

### Aktivieren von Dynamic Media Classic für WCM {#enabling-scene-for-wcm}

Die Aktivierung von Dynamic Media Classic für WCM ist aus zwei Gründen erforderlich:

* Zum Aktivieren der Dropdown-Liste der universellen Videoprofile für die Seitenbearbeitung. Without this, the **[!UICONTROL Universal Video Preset]** drop-down is empty and cannot be set.
* Wenn sich ein digitales Asset nicht im Zielordner befindet, können Sie das Asset in Dynamic Media Classic hochladen, wenn Sie für diese Seite in den Seiteneigenschaften die Option &quot;Dynamischer Medienklassiker&quot;aktivieren, und das Asset per Drag &amp; Drop in eine Komponente von Dynamic Media Classic ziehen. Es gelten die normalen Vererbungsregeln (die untergeordneten Seiten übernehmen also die Konfiguration von der übergeordneten Seite).

Beachten Sie beim Aktivieren von Dynamic Media Classic für den WCM, dass wie bei anderen Konfigurationen Vererbungsregeln gelten. Sie können Dynamic Media Classic für WCM in der touchoptimierten oder klassischen Benutzeroberfläche aktivieren.

#### Aktivieren von Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche:

1. Tap the AEM icon and navigate to **[!UICONTROL Sites]** and then the root page of your web site (not language specific).

1. In the toolbar, select the [!UICONTROL settings] icon and tap **[!UICONTROL Open Properties]**.

1. Tippen Sie auf **[!UICONTROL Cloud-Dienste]** und dann auf Konfiguration **** hinzufügen und wählen Sie **[!UICONTROL Dynamische Medien klassisch]**.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und klicken Sie auf **[!UICONTROL OK]**.

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen für die Verwendung in AEM mit der Videokomponente Dynamic Media Classic auf dieser Seite und untergeordneten Seiten zur Verfügung.

#### Aktivieren von Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche {#enabling-scene-for-wcm-in-the-classic-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche:

1. In AEM, tap **[!UICONTROL Websites]** and navigate to the root page of your web site (not language specific).

1. In the sidekick, tap the **[!UICONTROL Page]** icon and tap **[!UICONTROL Page Properties]**.

1. Tippen Sie auf **[!UICONTROL Cloud-Dienste > Dienste hinzufügen > Dynamischer Medienklassiker]**.
1. Wählen Sie in der Dropdownliste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und klicken Sie auf **[!UICONTROL OK]**.

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen für die Verwendung in AEM mit der Videokomponente Dynamic Media Classic auf dieser Seite und untergeordneten Seiten zur Verfügung.

### Konfigurieren einer Standardkonfiguration {#configuring-a-default-configuration}

Wenn Sie mehrere Konfigurationen für dynamische Medien Classic haben, können Sie eine davon als Standard für den Content-Browser von Dynamic Media Classic angeben.

Es kann jeweils nur eine Konfiguration von Dynamic Media Classic als Standard markiert werden. Die Standardkonfiguration sind die Unternehmensassets, die standardmäßig im Content Browser von Dynamic Media Classic angezeigt werden.

Sie können die Standardkonfiguration wie folgt konfigurieren:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud-Dienste]**, tippen Sie auf **[!UICONTROL Dynamische Medien Classic]** und wählen Sie Ihre Konfiguration in Dynamisch Media Classic aus.
1. Tap **[!UICONTROL Edit]** to open the configuration.

1. In the **[!UICONTROL General]** tab, select the **[!UICONTROL Default Configuration]** check box to make this the default company and root path that appears in the Dynamic Media Classic content browser.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Wenn es nur eine Konfiguration gibt, hat die Auswahl des Kontrollkästchens **[!UICONTROL Standardkonfiguration]** keinerlei Wirkung.

### Konfigurieren des Ad-hoc-Ordners {#configuring-the-ad-hoc-folder}

Sie können den Ordner konfigurieren, in den Assets in Dynamic Media Classic hochgeladen werden, wenn sich das Asset nicht im CQ-Zielordner befindet. Siehe Veröffentlichen von Assets von außerhalb des CQ-Zielordners.

Sie können den Ad-hoc-Ordner wie folgt konfigurieren:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud-Dienste]**, tippen Sie auf **[!UICONTROL Dynamische Medien Classic]** und wählen Sie Ihre Konfiguration in Dynamisch Media Classic aus.
1. Tap **[!UICONTROL Edit]** to open the configuration.

1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Im Feld **[!UICONTROL Ad-hoc-Ordner]** können Sie den **Ad-hoc**-Ordner verändern. Standardmäßig handelt es sich um **Firmenname/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Konfigurieren der universellen Vorgaben {#configuring-universal-presets}

Informationen zur Konfiguration der universellen Vorgaben für die Videokomponente finden Sie unter [Video](/help/assets/s7-video.md).

## Unterstützung von MIME-typbasierten Assets/Dynamic Media Classic-Upload-Auftragsparametern {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

Sie können konfigurierbare Parameter für Upload-Aufträge für Dynamic Media Classic aktivieren, die durch die Synchronisierung von Digital Asset Manager/Dynamic Media Classic-Assets ausgelöst werden.

Insbesondere konfigurieren Sie hier das vom MIME-Typ akzeptierte Dateiformat im Bereich „OSGi“ (Open Service Gateway initiator) des Bedienfelds der Web-Konsolen-Konfiguration. Anschließend können Sie die einzelnen Parameter für Upload-Aufträge anpassen, die für jeden MIME-Typ in JCR (Java Content Repository) verwendet werden.

**MIME-Typen-basierte Assets können Sie wie folgt konfigurieren:**

1. Tap the AEM icon and navigate to **[!UICONTROL Tools > Operations > Web Console]**.
1. In the Adobe Experience Manager Web Console Configuration panel, on the **[!UICONTROL OSGi]** menu, tap **[!UICONTROL Configuration]**.
1. Under the Name column, find and tap **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]** to edit the configuration.
1. Tippen Sie im Bereich &quot;MIME-Typzuordnung&quot;auf ein beliebiges Pluszeichen (+), um einen MIME-Typ hinzuzufügen.

   See [Supported MIME types](/help/assets/assets-formats.md#supported-mime-types).

1. Geben Sie in das Textfeld den neuen MIME-Typnamen ein.

   Sie würden beispielsweise eine `<file_extension>=<mime_type>` wie in `EPS=application/postscript` OR eingeben `PSD=image/vnd.adobe.photoshop`.

1. In the lower-right corner of the configuration window, tap **[!UICONTROL Save]**.
1. Kehren Sie über die linke Leiste zu AEM zurück und tippen Sie auf „CRXDE Lite“.
1. On the CRXDE Lite page, in the left rail, navigate to `/etc/cloudservices/scene7/<environment>` (substitute `<environment>` for the actual name).
1. Expand `<environment>` (substitute `<environment>` for the actual name) to reveal the `mimeTypes` node.
1. Tippen Sie auf den soeben hinzugefügten mimeType.

   For example, `mimeTypes > application_postscript` OR `mimeTypes > image_vnd.adobe.photoshop`.

1. On the right side of the CRXDE Lite page, tap the **[!UICONTROL Properties]** tab.
1. Specify a Dynamic Media Classic upload job parameter in the **[!UICONTROL jobParam]** value field.

   Beispiel, `psprocess="rasterize"&psresolution=120` .

   See the [Adobe Dynamic Media Classic Image Production System API](https://marketing.adobe.com/resources/help/en_US/s7/ips_api/) for additional upload job parameters you can use.

   >[!NOTE]
   >
   >Wenn Sie PSD-Dateien hochladen und sie als Vorlagen mit Ebenenextrahierungen verarbeiten möchten, geben Sie Folgendes in das **[!UICONTROL Wertefeld jobParam]** ein:
   >
   >`process=MaintainLayers&createTemplate=true`
   >
   >Vergewissern Sie sich, dass die PSD-Datei über &quot;Ebenen&quot;verfügt. Wenn es sich um ausschließlich ein Bild oder um ein Bild mit Maske handelt, wird es als Bild verarbeitet, da keine Ebenen verarbeitet werden können.

1. In the upper-left corner of the CRXDE Lite page, tap **[!UICONTROL Save All]**.

## Fehlerbehebung bei der Integration von Dynamic Media Classic und AEM {#troubleshooting-scene-and-aem-integration}

Wenn Sie Probleme bei der Integration von AEM mit Dynamic Media Classic haben, finden Sie in den folgenden Szenarien Lösungen.

**Wenn die Veröffentlichung digitaler Assets in Dynamic Media Classic fehlschlägt:**

* Überprüfen Sie, ob sich das hochzuladende Asset im **[!UICONTROL CQ-Zielordner]** befindet (Sie geben diesen Ordner in der Cloud-Konfiguration von Dynamic Media Classic an).
* Falls nicht, müssen Sie die Cloud-Konfiguration in den **[!UICONTROL Seiteneigenschaften]** zu dieser Seite konfigurieren, um das Hochladen in den Ordner **[!UICONTROL CQ adhoc]** zu ermöglichen.

* Überprüfen Sie die Protokolle auf etwaige Informationen.

**Wenn Ihre Videovorgaben nicht angezeigt werden:**

* Stellen Sie sicher, dass Sie die Cloud-Konfiguration dieser Seite durch die **[!UICONTROL Seiteneigenschaften]** konfiguriert haben. Video-Vorgaben stehen in der Videokomponente &quot;Dynamic Media Classic&quot;zur Verfügung.

**Wenn Ihre Video-Assets nicht in AEM wiedergegeben werden:**

* Stellen Sie sicher, dass Sie die richtige Videokomponente verwendet haben. Die Videokomponente &quot;Dynamic Media Classic&quot;unterscheidet sich von der zugrunde liegenden Videokomponente. Siehe [Foundation Video Component versus Dynamic Media Classic Video Component](/help/assets/s7-video.md).

**Wenn neue oder geänderte Assets in AEM nicht automatisch in Dynamic Media Classic hochgeladen werden:**

* Stellen Sie sicher, dass sich die Assets im CQ-Zielordner befinden. Nur Assets, die sich im CQ-Zielordner befinden, werden automatisch aktualisiert (vorausgesetzt, Sie haben AEM Assets für das automatische Hochladen von Assets konfiguriert).
* Vergewissern Sie sich, dass Sie die Cloud-Services-Konfiguration so konfiguriert haben, dass das automatische Hochladen aktiviert wird, und dass Sie den DAM-Asset-Workflow aktualisiert und gespeichert haben, damit das Hochladen von Dynamischem Media Classic mit einbezogen wird.
* Führen Sie beim Hochladen eines Bildes in einen Unterordner des Zielordners von Dynamic Media Classic einen der folgenden Schritte aus:

   * Stellen Sie sicher, dass die Namen aller Assets unabhängig von ihrem Speicherort eindeutig sind. Andernfalls wird das Asset im Hauptzielordner gelöscht und es verbleibt nur das Asset im Unterordner.
   * Ändern Sie, wie Dynamic Media Classic Assets im Bereich &quot;Einstellungen&quot;des Kontos &quot;Dynamic Media Classic&quot;überschreibt. Legen Sie für Dynamic Media Classic nicht fest, dass Assets unabhängig vom Speicherort überschrieben werden, wenn Sie Assets mit demselben Namen in Unterordnern verwenden.

**Wenn Ihre gelöschten Assets oder Ordner nicht zwischen Dynamic Media Classic und AEM synchronisiert werden:**

* In AEM Assets gelöschte Assets und Ordner werden weiterhin im synchronisierten Ordner in Dynamic Media Classic angezeigt. Sie müssen Sie manuell löschen.

**Wenn der Video-Upload fehlschlägt**

* If your video upload fails and you are using AEM to encode video through the Dynamic Media Classic integration, see [Adding configurable timeout to Dynamic Media Classic Upload workflow](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto des Unternehmens &quot;Dynamic Media Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

