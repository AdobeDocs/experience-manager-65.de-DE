---
title: Integrieren in Dynamic Media Classic
description: Erfahren Sie, wie Sie Adobe Experience Manager mit Dynamic Media Classic integrieren.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
translation-type: tm+mt
source-git-commit: 4333cfde433d00ddc4cb013b31fe52956791da46
workflow-type: tm+mt
source-wordcount: '5452'
ht-degree: 21%

---


# Integrieren in Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und -drucke.

Um Dynamic Media Classic verwenden zu können, müssen Sie die Cloud-Konfiguration so konfigurieren, dass Dynamic Media Classic und AEM Assets miteinander interagieren können. In diesem Dokument wird die Konfiguration von AEM und Dynamic Media Classic beschrieben.

Informationen zur Verwendung aller Dynamic Media Classic-Komponenten auf einer Seite und zum Arbeiten mit Videos finden Sie unter [Verwenden von Dynamic Media Classic](../assets/scene7.md).

>[!NOTE]
>
>* Die DHTML-Viewer-Plattform von Dynamic Media Classic hat am 31. Januar 2014 offiziell das Ende des Lebenszyklus erreicht. Weitere Informationen finden Sie in den [FAQ zur Einstellung von DHTML-Viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Bevor Sie Dynamic Media Classic für die Verwendung mit AEM konfigurieren, lesen Sie [Best Practices](#best-practices-for-integrating-scene-with-aem) für die Integration von Dynamic Media Classic mit AEM.
>* Wenn Sie Dynamic Media Classic mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie sowohl HTTP Client-Proxykonfigurationen konfigurieren, da einige Funktionen von AEM die 3.x-APIs und einige andere die 4.x-APIs verwenden. 3.x ist mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert und 4.x mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.

>



## AEM/Dynamic Media Classic Integration versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

AEM Benutzer haben die Wahl zwischen zwei Lösungen, um mit dynamischen Medien zu arbeiten: Integrieren Sie entweder Ihre AEM in Dynamic Media Classic oder verwenden Sie die Dynamic Media-Lösung, die in AEM integriert ist.

Verwenden Sie die folgenden Kriterien, um zu bestimmen, welche Lösung ausgewählt werden soll:

* Wenn Sie ein **bestehender** Dynamic Media Classic-Kunde sind, dessen Rich-Media-Assets in Dynamic Media Classic für Veröffentlichung und Versand gespeichert sind, diese Assets jedoch mit WCM-Authoring und/oder AEM Assets für die Verwaltung integrieren möchten, verwenden Sie die in diesem Dokument beschriebene Punkt-zu-Punkt-Integration [AEM/Dynamic Media Classic.](#aem-scene-point-to-point-integration)

* Wenn Sie AEM-**Neukunde** sind und Rich-Media-Bereitstellung benötigen, wählen Sie die [Option „Dynamic Media“](#aem-dynamic-media) aus. Diese Option ist am sinnvollsten, wenn Sie über kein vorhandenes S7-Konto verfügen und wenn Sie nicht über viele im System gespeicherte Assets verfügen.

* In bestimmten Fällen möchten Sie vielleicht beide Lösungen verwenden. Das [Dual-use-Szenario](/help/sites-administering/scene7.md#dual-use-scenario) beschreibt dieses Szenario.

### AEM/Dynamic Media Classic Punkt-zu-Punkt-Integration {#aem-scene-point-to-point-integration}

Wenn Sie in dieser Lösung mit Assets arbeiten, nutzen Sie eine der folgenden Vorgehensweisen:

* Laden Sie Assets direkt in Dynamic Media Classic hoch und greifen Sie dann über den Inhaltsbrowser **Dynamic Media Classic** zum Erstellen von Seiten oder
* Hochladen auf AEM Assets und anschließendes Aktivieren der automatischen Veröffentlichung auf Dynamic Media Classic Sie greifen über den Inhaltsbrowser **Assets** zum Erstellen von Seiten zu.

Die für diese Integration verwendeten Komponenten befinden sich im Komponentenbereich **Dynamic Media Classic** im Designmodus.](/help/sites-authoring/author-environment-tools.md#page-modes)[

### AEM Dynamic Media {#aem-dynamic-media}

AEM Dynamic Media ist die Vereinigung von Dynamic Media Classic Funktionen direkt innerhalb der AEM Plattform.

Wenn Sie innerhalb dieser Lösung mit Assets arbeiten, befolgen Sie diesen Workflow:

1. Laden Sie Assets mit einzelnen Bildern und Videos direkt in AEM hoch.
1. Kodieren Sie Videos direkt in AEM.
1. Erstellen Sie bildbasierte Sets direkt in AEM.
1. Fügen Sie Bildern und Videos bei Bedarf interaktive Elemente hinzu.

Die von Ihnen für Dynamic Media verwendeten Komponenten befinden sich im Komponentenbereich **[!UICONTROL Dynamic Media]** im [Designmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Sie umfassen Folgendes:

* **[!UICONTROL Dynamic Media]** – Die Komponente **[!UICONTROL Dynamic Media]** ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bildsets sowie Rotationssets, Sets für gemischte Medien und Videos. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

* **[!UICONTROL Interaktive Medien]** - Die Komponente für **[!UICONTROL interaktive Medien]** ist für Assets wie Karussell-Banner, interaktive Bilder und interaktive Videos bestimmt, die interaktive Elemente wie Hotspots oder Imagemaps enthalten. Die Komponente ist intelligent – je nachdem, ob Sie ein Bild oder Video hinzufügen, werden Ihnen unterschiedliche Optionen zur Verfügung gestellt. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

### Szenario einer Doppelnutzung {#dual-use-scenario}

Standardmäßig können Sie die Integrationsfunktionen von Dynamic Media und Dynamic Media Classic von AEM gleichzeitig verwenden. Die folgende Tabelle mit Anwendungsfällen beschreibt, wann Sie bestimmte Bereiche ein- und ausschalten.

So verwenden Sie Dynamic Media und Dynamic Media Classic gleichzeitig:

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
    <td>Neu bei Websites und Dynamic Media</td>
    <td>Hochladen von Assets in AEM und Verwenden AEM Dynamic Media-Komponente zum Erstellen von Assets auf Siteseiten</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td>Off</td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Im Einzelhandel und sind neu bei Sites und Dynamic Media</td>
    <td>Laden Sie nicht produktspezifische Assets zur Verwaltung und zum Versand in AEM hoch. Laden Sie PRODUKT-Assets in Dynamic Media Classic hoch und verwenden Sie den Dynamic Media Classic-Inhaltsbrowser in AEM und Komponente, um Produktdetailseiten auf Sites zu erstellen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Neu bei Assets und Dynamic Media</td>
    <td>Assets auf AEM Assets hochladen und veröffentlichten URL-/Einbettungscode von Dynamic Media verwenden</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Aus</td>
    <td>Aus</td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Neu bei Dynamic Media und Planung</td>
    <td>Verwenden Sie Dynamic Media für Bildbearbeitung und Video. Erstellen Sie Bildvorlagen in Dynamic Media Classic und verwenden Sie Dynamic Media Classic Content Finder, um Vorlagen in Sites-Seiten einzuschließen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Ein bestehender Dynamic Media Classic-Kunde und neu bei Sites</td>
    <td>Hochladen von Assets in Dynamic Media Classic und Verwenden AEM Dynamic Media Classic-Inhaltsbrowsers, um Assets auf Siteseiten zu suchen und zu erstellen</td>
    <td>Aus</td>
    <td>Aus</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Ein bestehender Dynamic Media Classic-Kunde, der neu bei Sites und Assets ist</td>
    <td>Laden Sie Assets zu DAM hoch und veröffentlichen Sie sie automatisch zum Versand in Dynamic Media Classic. Verwenden Sie AEM Dynamic Media Classic-Inhaltsbrowser, um Assets auf Siteseiten zu suchen und zu erstellen.</td>
    <td>Aus</td>
    <td>Aus</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    <tr>
    <td>Bestehender Dynamic Media Classic-Kunde und neuer Asset-Kunde</td>
    <td><p>Laden Sie Assets auf AEM hoch und verwenden Sie Dynamic Media, um Darstellungen zum Herunterladen/Freigeben zu generieren. Veröffentlichen Sie AEM Assets automatisch für den Versand in Dynamic Media Classic.</p> <p><strong>Wichtig: Die Verarbeitung von </strong> Incurs-Duplikaten und die in AEM generierten Darstellungen werden nicht mit Dynamic Media Classic synchronisiert.</p> </td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Aus</td>
    <td>Aus</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (Optional) (siehe Verwendungsfalltabelle) - Richten Sie die [Dynamic Media Cloud-Konfiguration](/help/assets/config-dynamic.md) ein und [aktivieren Sie den Dynamic Media-Server](/help/assets/config-dynamic.md).
1. (Optional) (siehe Verwendungsfalltabelle) - Wenn Sie die Option &quot;Automatisches Hochladen von Assets zu Dynamic Media Classic&quot;aktivieren, müssen Sie Folgendes hinzufügen:

   1. Richten Sie den automatischen Upload auf Dynamic Media Classic ein.
   1. hinzufügen Sie den Schritt **Dynamic Media Classic-Upload** nach allen Dynamic Media-Workflow-Schritten *am Ende* **Dam-Update-Asset**-Arbeitsablauf ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Optional) Schränken Sie das Hochladen von Dynamic Media Classic-Assets nach MIME-Typ in [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl) ein. Asset-MIME-Typen, die nicht in dieser Liste enthalten sind, werden nicht auf den Dynamic Media Classic-Server hochgeladen.
   1. (Optional) Richten Sie Video in der Dynamic Media Classic-Konfiguration ein. Sie können die Videokodierung für Dynamic Media und Dynamic Media Classic gleichzeitig aktivieren. Dynamische Darstellungen werden für die lokale Vorschau und Wiedergabe in AEM Instanz verwendet, während Dynamic Media Classic-Videodarstellungen auf Dynamic Media Classic-Servern generiert und gespeichert werden. Wenden Sie beim Einrichten von Videokodierungsdiensten für Dynamic Media und Dynamic Media Classic ein [Videoverarbeitung-Profil](/help/assets/video-profiles.md) auf den Asset-Ordner von Dynamic Media Classic an.
   1. (Optional) [Sichere Vorschau in Dynamic Media Classic konfigurieren](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beschränkungen {#limitations}

Wenn Sie sowohl Dynamic Media Classic als auch Dynamic Media aktiviert haben, gelten folgende Einschränkungen:

* Das manuelle Hochladen in Dynamic Media Classic durch Auswahl eines Assets und Ziehen in eine Dynamic Media Classic-Komponente auf einer AEM funktioniert nicht.
* Obwohl synchronisierte Assets mit AEM-Dynamic Media Classic automatisch auf Dynamic Media Classic aktualisiert werden, wenn das Asset in Assets bearbeitet wird, wird bei einer Rollback-Aktion kein neuer Upload Trigger. Daher würde Dynamic Media Classic die neueste Version nicht unmittelbar nach einem Rollback erhalten. Als Ausweichlösung eignet sich die erneute Bearbeitung, sobald das Rollback abgeschlossen ist.
* Wenn Sie Dynamic Media für einen Anwendungsfall und die Dynamic Media Classic-Integration für einen anderen Anwendungsfall verwenden müssen, damit die Dynamic Media-Assets nicht mit dem Dynamic Media Classic-System interagieren, wenden Sie die Dynamic Media Classic-Konfiguration nicht auf den Dynamic Media-Ordner oder die Dynamic Media-Konfiguration (Verarbeitungs-Profil) auf einen Dynamic Media Classic-Ordner an.

## Best Practices für die Integration von Dynamic Media Classic mit AEM {#best-practices-for-integrating-scene-with-aem}

Bei der Integration von Dynamic Media Classic mit AEM gibt es einige wichtige Best Practices, die in den folgenden Bereichen zu beachten sind:

* Testen Ihrer Integration
* Hochladen von Assets direkt von Dynamic Media Classic empfohlen für bestimmte Szenarien

Siehe [bekannte Beschränkungen](#known-limitations-and-design-implications).

### Testen Ihrer Integration {#test-driving-your-integration}

Adobe empfiehlt, dass Sie die Integration testen, indem Sie den Stammordner nur auf einen Unterordner und nicht auf eine ganze Firma verweisen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem bestehenden Dynamic Media Classic-Firmen-Konto kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets und kann zum Systemabsturz führen).

### Hochladen von Assets aus AEM Assets im Vergleich zu Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

Sie können Assets entweder mit der Funktion &quot;Assets&quot;(Digital Asset Management) oder über den Dynamic Media Classic-Inhaltsbrowser direkt in AEM hochladen. Was davon Sie verwenden, hängt von den folgenden Faktoren ab:

* Dynamic Media Classic-Asset-Typen, die AEM Assets noch nicht unterstützt, müssen direkt über den Content-Browser von Dynamic Media Classic einer AEM Website von Dynamic Media Classic hinzugefügt werden, z. B. Bildvorlagen.
* Bei Asset-Typen, die von AEM Assets und Dynamic Media Classic unterstützt werden, hängt die Entscheidung, wie sie hochgeladen werden, von Folgendem ab:

   * Wo sich die Assets heute befinden UND
   * Wie wichtig ihre Verwaltung in einem gemeinsamen Repository ist

Wenn sich die Assets bereits in Dynamic Media Classic befinden und sie in einem gemeinsamen Repository verwaltet werden, ist es nicht so wichtig, sie nach AEM Assets zu exportieren, nur um sie für den Versand wieder mit Dynamic Media Classic zu synchronisieren. Andernfalls ist es empfehlenswert, Assets nur zum Versand in einem einzigen Repository zu speichern und mit Dynamic Media Classic zu synchronisieren.

## Konfigurieren der Dynamic Media Classic-Integration {#configuring-scene-integration}

Sie können AEM so konfigurieren, dass Assets nach Dynamic Media Classic hochgeladen werden. Assets aus einem CQ-Zielgruppen-Ordner können (automatisch oder manuell) von AEM in ein Dynamic Media Classic-Firmen-Konto hochgeladen werden.

>[!NOTE]
>
>Adobe empfiehlt, nur den angegebenen Ordner &quot;Zielgruppe&quot;zum Importieren von Dynamic Media Classic-Assets zu verwenden. Digitale Assets, die sich außerhalb des Ordners &quot;Zielgruppe&quot;befinden, können nur in Dynamic Media Classic-Komponenten auf Seiten verwendet werden, auf denen die Dynamic Media Classic-Konfiguration aktiviert wurde. Darüber hinaus werden sie in einem Ad-hoc-Ordner in Dynamic Media Classic abgelegt. Der Ad-hoc-Ordner wird nicht mit AEM synchronisiert (Assets können jedoch im Content Browser von Dynamic Media Classic gefunden werden).

Um Dynamic Media Classic für die Integration mit AEM zu konfigurieren, müssen Sie die folgenden Schritte ausführen:

1. [Definieren einer Cloud-Konfiguration](#creating-a-cloud-configuration-for-scene) : Definiert die Zuordnung zwischen einem Dynamic Media Classic-Ordner und einem Asset-Ordner. Sie müssen diesen Schritt auch dann ausführen, wenn Sie nur eine einseitige Synchronisierung (AEM Assets bis Dynamic Media Classic) wünschen.
1. [Aktivieren Sie den  **Adobe CQ s7dam Dam Listener**](#enabling-the-adobe-cq-scene-dam-listener) - Fertig in der   OSGiconsole.
1. Wenn AEM Assets automatisch in Dynamic Media Classic hochgeladen werden sollen, müssen Sie diese Option aktivieren und Dynamic Media Classic zum Arbeitsablauf [!UICONTROL DAM Update Asset] hinzufügen. Außerdem können Sie manuell Assets hochladen.
1. Hinzufügen von Dynamic Media Classic-Komponenten zum Sidekick. Auf diese Weise können die Benutzer Dynamic Media Classic-Komponenten auf ihren AEM verwenden.
1. [Ordnen Sie die Konfiguration der Seite in AEM](#enabling-scene-for-wcm)  zu. Dieser Schritt ist erforderlich, um alle Video-Vorgaben, die Sie in Dynamic Media Classic erstellt haben, Ansicht. Es ist auch erforderlich, wenn Sie ein Asset von außerhalb des Ordners &quot;CQ-Zielgruppe&quot;in Dynamic Media Classic veröffentlichen müssen.

In diesem Abschnitt wird die Durchführung all dieser Schritte behandelt und es werden wichtige Beschränkungen aufgeführt.

### Funktionsweise der Synchronisierung zwischen Dynamic Media Classic und AEM Assets {#how-synchronization-between-scene-and-aem-assets-works}

Beim Einrichten der Synchronisierung von AEM Assets und Dynamic Media Classic ist Folgendes wichtig:

#### Hochladen auf Dynamic Media Classic von AEM Assets {#uploading-to-scene-from-aem-assets}

* Es gibt einen bestimmten Synchronisierungsordner in AEM für Dynamic Media Classic-Uploads.
* Uploads in Dynamic Media Classic können automatisiert werden, wenn die digitalen Assets im angegebenen Synchronisierungsordner abgelegt werden.
* Die Ordner- und Unterordnerstruktur in AEM wird in Dynamic Media Classic repliziert.

>[!NOTE]
>
>AEM bettet alle Metadaten wie XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadaten-Knoten in Dynamic Media Classic XMP verfügbar sind.

#### Bekannte Beschränkungen und Designimplikationen {#known-limitations-and-design-implications}

Die Synchronisierung zwischen AEM Assets und Dynamic Media Classic hat derzeit folgende Einschränkungen/Auswirkungen auf das Design:

<table>
 <tbody>
  <tr>
   <td><strong>Implikation von Einschränkungen/Entwürfen</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Ein angegebener Synchronisierungsordner (Zielgruppe)</td>
   <td>Für Dynamic Media Classic-Uploads kann in AEM nur ein bestimmter Ordner pro Firma festgelegt werden. Sie können mehrere Konfigurationen erstellen, wenn Sie Zugriff auf mehr als ein Firma-Konto in Dynamic Media Classic benötigen.</td>
  </tr>
  <tr>
   <td>Ordnerstruktur</td>
   <td>Wenn Sie einen synchronisierten Ordner mit Assets löschen, werden alle Remote-Assets von Dynamic Media Classic gelöscht, der Ordner bleibt jedoch erhalten.</td>
  </tr>
  <tr>
   <td>Ad-hoc-Ordner</td>
   <td>Assets, die sich außerhalb des Ordners "Zielgruppe"befinden und manuell in Dynamic Media Classic in WCM hochgeladen werden, werden in Dynamic Media Classic automatisch in einem separaten Ad-hoc-Ordner abgelegt. Dies wird in der Cloud-Konfiguration in AEM konfiguriert.</td>
  </tr>
  <tr>
   <td>Gemischte Medien</td>
   <td>Gemischte Mediensets werden in AEM angezeigt, obwohl sie in AEM nicht unterstützt werden.</td>
  </tr>
  <tr>
   <td>PDFs </td>
   <td>Generierte PDFs aus E-Katalogen in Dynamic Media Classic werden in den Ordner "CQ-Zielgruppe"importiert.</td>
  </tr>
  <tr>
   <td>Aktualisieren der Benutzeroberfläche</td>
   <td>Stellen Sie bei der Synchronisierung zwischen AEM und Dynamic Media Classic sicher, dass Sie die Benutzeroberfläche aktualisieren, um Änderungen an der Ansicht vorzunehmen. </td>
  </tr>
  <tr>
   <td>Videominiaturen</td>
   <td>Wenn Sie ein Video zur Kodierung über Dynamic Media Classic nach AEM Assets hochladen, kann es abhängig von der Videoverarbeitung einige Zeit dauern, bis die Videominiaturen und kodierten Videos in AEM Assets verfügbar sind.</td>
  </tr>
  <tr>
   <td>Zielgruppen-Unterordner</td>
   <td><p>Wenn Sie Unterordner im Ordner "Zielgruppe"verwenden, stellen Sie sicher, dass Sie für jedes Asset entweder eindeutige Namen verwenden (unabhängig vom Speicherort) oder Dynamic Media Classic (im Bereich "Einstellungen") konfigurieren, um Assets unabhängig vom Speicherort nicht zu überschreiben.</p> <p>Andernfalls werden Assets mit demselben Namen, die in einen Unterordner der Dynamic Media Classic-Zielgruppe hochgeladen werden, hochgeladen, der gleichnamige Asset im Ordner "Zielgruppe"wird jedoch gelöscht. </p> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media Classic-Server {#configuring-scene-servers} konfigurieren

Wenn Sie AEM hinter einem Proxy ausführen oder spezielle Firewall-Einstellungen haben, müssen Sie die Hosts der verschiedenen Regionen explizit aktivieren. Server werden im Inhalt in `/etc/cloudservices/scene7/endpoints` verwaltet und können nach Bedarf angepasst werden. Tippen Sie auf eine URL und bearbeiten Sie die URL bei Bedarf. In früheren Versionen von AEM waren diese Werte hartkodiert.

Wenn Sie zu `/etc/cloudservices/scene7/endpoints.html` navigieren, werden die Server aufgelistet (und können sie bearbeiten, indem Sie auf die URL klicken):

![chlimage_1-296](assets/chlimage_1-296.png)

### Erstellen einer Cloud-Konfiguration für Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Eine Cloud-Konfiguration definiert die Zuordnung zwischen einem Dynamic Media Classic-Ordner und einem AEM Assets-Ordner. Es muss konfiguriert werden, um AEM Assets mit Dynamic Media Classic zu synchronisieren. Unter Funktionsweise der Synchronisierung finden Sie weitere Informationen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem bestehenden Dynamic Media Classic-Firmen-Konto kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

>[!NOTE]
>
>Sie können über mehrere Konfigurationen verfügen: Eine Cloud-Konfiguration stellt einen Benutzer in einer Dynamic Media Classic-Firma dar. Wenn Sie auf andere Dynamic Media Classic-Firmen oder -Benutzer zugreifen möchten, müssen Sie mehrere Konfigurationen erstellen.

So konfigurieren Sie AEM, um Assets in Dynamic Media Classic veröffentlichen zu können:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, um auf die Adobe Dynamic Media Classic zuzugreifen.

1. Tippen Sie auf **[!UICONTROL Jetzt konfigurieren.]**

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** und optional im Feld **[!UICONTROL Name]** die entsprechenden Informationen ein. Tippen Sie auf **[!UICONTROL Erstellen.]**

   >[!NOTE]
   >
   >Beim Erstellen zusätzlicher Konfigurationen wird das Feld **[!UICONTROL Übergeordnete Konfiguration]** angezeigt.
   >
   >Ändern Sie **nicht** die übergeordnete Konfiguration. Das Ändern der übergeordneten Konfiguration kann zum Scheitern der Integration führen.

1. Geben Sie die E-Mail-Adresse, das Kennwort und die Region Ihres Dynamic Media Classic-Kontos ein und tippen Sie auf **[!UICONTROL Mit Dynamic Media Classic verbinden.]** Sie sind mit dem Dynamic Media Classic-Server verbunden und das Dialogfeld wird mit weiteren Optionen erweitert.

1. Geben Sie den Namen **[!UICONTROL Firma]** und **[!UICONTROL Stammpfad]** ein (dies ist der veröffentlichte Servername zusammen mit jedem Pfad, den Sie angeben möchten; Wenn Sie den Namen des veröffentlichten Servers nicht kennen, gehen Sie in Dynamic Media Classic zu **[!UICONTROL Einstellungen > Anwendungseinstellungen.]**)

   >[!NOTE]
   >
   >Der Dynamic Media Classic-Stammordner ist der Dynamic Media Classic-Ordner, mit dem eine Verbindung hergestellt AEM. Es kann auf einen spezifischen Ordner eingegrenzt werden.

   >[!CAUTION]
   >
   >Je nach Größe des Dynamic Media Classic-Ordners kann es lange dauern, einen Stammordner zu importieren. Darüber hinaus könnten Dynamic Media Classic-Daten die AEM Datenspeicherung überschreiten. Stellen Sie sicher, dass Sie in den richtigen Ordner importieren. Der Import einer zu großen Menge von Daten kann zur Unterbrechung Ihres Systems führen.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Klicken Sie auf **[!UICONTROL OK.]** AEM speichert Ihre Konfiguration.

>[!NOTE]
>
>Wenn Sie eine erneute Verbindung herstellen:
>
>* Wenn Sie beim Veröffentlichen eine Verbindung zu Dynamic Media Classic herstellen, müssen Sie das Kennwort ggf. beim Veröffentlichen zurücksetzen. Andernfalls funktioniert die erneute Verbindung nicht. Bei der Autoreninstanz stellt dies kein Problem dar.
>* Wenn Sie Werte wie Region und Firma ändern, müssen Sie die Verbindung zu Dynamic Media Classic wiederherstellen. Wenn Konfigurationsoptionen geändert, aber nicht gespeichert wurden, zeigt AEM fälschlicherweise nach wie vor an, dass die Konfiguration gültig ist. Achten Sie darauf, eine erneute Verbindung herzustellen.

>



### Aktivieren des Adobe CQ Dynamic Media Classic Dam Listener {#enabling-the-adobe-cq-scene-dam-listener}

Sie müssen den Adobe CQ Dynamic Media Classic Dam Listener aktivieren, der standardmäßig deaktiviert ist.

So aktivieren Sie ihn:

1. Tippen Sie auf das Symbol [!UICONTROL Tools] und navigieren Sie dann zu **[!UICONTROL Vorgänge > Web-Konsole.]** Die Web-Konsole wird geöffnet.
1. Navigieren Sie zu **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]**.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Tippen Sie auf **[!UICONTROL Speichern.]**

### Hinzufügen eines konfigurierbaren Timeouts zum Dynamic Media Classic Upload-Arbeitsablauf {#adding-configurable-timeout-to-scene-upload-workflow}

Wenn eine AEM-Instanz für die Videokodierung über Dynamic Media Classic konfiguriert ist, gibt es für jeden Upload-Auftrag standardmäßig einen 35-Minuten-Timeout. Um Videokodierungsaufträge mit potenziell längerer Dauer zu ermöglichen, können Sie diese Einstellung konfigurieren:

1. Navigieren Sie zu **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Ändern Sie die Zahl wie gewünscht im Feld **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]**. Jede positive Zahl wird binnen Sekunden mit der Maßeinheit akzeptiert. Standardmäßig ist dies auf 2100 festgelegt.

   >[!NOTE]
   >
   >Best Practice: Bei den meisten Assets dauert das Übernehmen höchstens einige Minuten (beispielsweise bei Bildern). Doch in bestimmten Fällen – beispielsweise bei größeren Videos – sollte der Timeout-Wert auf 7200 Sekunden (2 Stunden) erhöht werden, um eine lange Verarbeitungszeit zu ermöglichen. Andernfalls wird dieser Dynamic Media Classic-Upload-Auftrag in den JCR-Metadaten als **[!UICONTROL UploadFehlgeschlagen]** markiert.

1. Tippen Sie auf **[!UICONTROL Speichern]**.

### Automatisches Hochladen von AEM Assets {#autouploading-from-aem-assets}

Ab AEM 6.3.2 ist AEM Assets jetzt für Sie konfiguriert, sodass alle digitalen Assets, die Sie in den Digital Asset Manager hochladen, automatisch auf Dynamic Media Classic aktualisiert werden, wenn sich die Assets in einem Ordner mit der CQ-Zielgruppe befinden.

Wenn ein Asset in AEM Assets hinzugefügt wird, wird es automatisch hochgeladen und in Dynamic Media Classic veröffentlicht.

>[!NOTE]
>
>Die maximale Dateigröße für das automatische Hochladen von AEM Assets nach Dynamic Media Classic beträgt 500 MB.

So wird das automatische Hochladen von AEM Assets konfiguriert:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**. Tippen Sie dann unter der Überschrift Dynamic Media unter Verfügbare Konfigurationen auf **[!UICONTROL dms7 (Dynamic Media]**)
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert]**, aktivieren Sie das Kontrollkästchen **[!UICONTROL Automatisches Hochladen aktivieren]** und tippen Sie dann auf **[!UICONTROL OK.]** Sie müssen jetzt den DAM Asset-Workflow so konfigurieren, dass auch Hochladen in Dynamic Media Classic möglich ist.

   >[!NOTE]
   >
   >Informationen zum Übertragen von Assets in einen unveröffentlichten Zustand nach Dynamic Media Classic finden Sie unter [Konfigurieren des Status (veröffentlicht/unveröffentlicht) von Assets, die an Dynamic Media Classic](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) gesendet werden.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Navigieren Sie zurück zur AEM Begrüßungsseite und tippen Sie auf **[!UICONTROL Workflows.]** Doppelklicken Sie auf den Workflow **DAM-Update-Asset**, um ihn zu öffnen.
1. Navigieren Sie im Sidekick zu den Komponenten **[!UICONTROL Workflow]** und wählen Sie **[!UICONTROL Dynamic Media Classic.]** Ziehen Sie  **[!UICONTROL Dynamic Media]** Classic in den Workflow und tippen Sie auf  **[!UICONTROL Speichern.]** Assets, die im Ordner &quot;Zielgruppe&quot;zu AEM Assets hinzugefügt wurden, werden automatisch in Dynamic Media Classic hochgeladen.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wenn Assets nach der Automatisierung hinzugefügt und nicht im Ordner &quot;CQ-Zielgruppe&quot;abgelegt werden, werden sie nicht in Dynamic Media Classic hochgeladen.
   >* AEM bettet alle Metadaten wie XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadaten-Knoten in Dynamic Media Classic XMP verfügbar sind.


### Konfigurieren des Status (veröffentlicht/unveröffentlicht) der in Dynamic Media Classic {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene} übertragenen Assets

Wenn Sie Assets von AEM Assets nach Dynamic Media Classic verschieben, können Sie sie entweder automatisch veröffentlichen (Standardverhalten) oder in einem unveröffentlichten Zustand nach Dynamic Media Classic verschieben.

Möglicherweise möchten Sie Assets nicht sofort in Dynamic Media Classic veröffentlichen, wenn Sie sie in einer Staging-Umgebung testen möchten, bevor sie live geschaltet werden. Sie können AEM mit der Secure Test-Umgebung von Dynamic Media Classic verwenden, um Assets in einem unveröffentlichten Zustand direkt von Assets in Dynamic Media Classic zu verschieben.

Dynamic Media Classic Assets bleiben über eine sichere Vorschau verfügbar. Nur wenn Assets in AEM veröffentlicht werden, werden die Dynamic Media Classic-Assets auch in der Produktion live geschaltet.

Wenn Sie Assets sofort veröffentlichen möchten, wenn Sie sie in Dynamic Media Classic verschieben, müssen Sie keine Optionen konfigurieren. Dies ist das Standardverhalten.

Wenn Sie jedoch nicht möchten, dass Assets, die zur automatischen Veröffentlichung an Dynamic Media Classic gesendet werden, automatisch veröffentlicht werden, wird in diesem Abschnitt beschrieben, wie AEM und Dynamic Media Classic dazu konfiguriert werden.

#### Voraussetzungen für das Hochladen von Assets in nicht veröffentlichte Dynamic Media Classic {#prerequisites-to-push-assets-to-scene-unpublished}

Bevor Sie Assets in Dynamic Media Classic verschieben können, ohne sie zu veröffentlichen, müssen Sie Folgendes einrichten:

1. [Verwenden Sie die Admin Console, um einen Support-Fall zu erstellen.](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) In Ihrem Support-Fall fordern Sie die Aktivierung der sicheren Vorschau für Ihr Dynamic Media Classic-Konto an.
1. Folgen Sie den Anweisungen zum Einrichten der sicheren Vorschau für Ihr Dynamic Media Classic-Konto.](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html)[

Dies sind dieselben Schritte, die Sie ausführen würden, um eine sichere Testeinrichtung in Dynamic Media Classic zu erstellen.

>[!NOTE]
>
>Wenn es sich bei Ihrer Umgebung um ein Unix 64-Bit-Betriebssystem handelt, finden Sie weitere Konfigurationsoptionen, die Sie festlegen müssen, unter [https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

#### Bekannte Beschränkungen für das Pushen von Assets im nicht veröffentlichten Status  {#known-limitations-for-pushing-assets-in-unpublished-state}

Beachten Sie die folgenden Beschränkungen, wenn Sie diese Funktion verwenden:

* Die Versionskontrolle wird nicht unterstützt.
* Wenn ein Asset bereits in AEM veröffentlicht ist und eine Folgeversion erstellt wurde, wird diese neue Version sofort veröffentlicht und tatsächlich in der Produktion eingesetzt. Die Veröffentlichung zusammen mit der Aktivierung funktioniert nur bei der ersten Veröffentlichung eines Assets.

>[!NOTE]
>
>Wenn Sie Assets sofort veröffentlichen möchten, sollten Sie die Option **[!UICONTROL Sichere Vorschau aktivieren]** auf **[!UICONTROL Sofort]** setzen und die Funktion **[!UICONTROL Automatisches Hochladen aktivieren]** verwenden.

### Festlegen des Status der in Dynamic Media Classic als unveröffentlicht {#setting-the-state-of-assets-pushed-to-scene-as-unpublished} veröffentlichten Assets

>[!NOTE]
>
>Wenn ein Benutzer das Asset in AEM veröffentlicht, aktiviert es automatisch das S7-Asset in der Produktion/im Live-Asset (das Asset befindet sich dann nicht mehr in der sicheren Vorschau/im unveröffentlichten Status).

So legen Sie den Status der an Dynamic Media Classic gesendeten Assets als unveröffentlicht fest:

1. Tippen Sie auf das Symbol &quot;AEM&quot;, navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Wählen Sie im Dropdownmenü **[!UICONTROL Sichere Ansicht aktivieren]** die Option **[!UICONTROL Bei AEM-Aktivierung für Veröffentlichungen]**, um Assets ohne Veröffentlichung in Dynamic Media Classic zu verschieben. (Standardmäßig ist dieser Wert auf **[!UICONTROL Sofort]** festgelegt, wobei Dynamic Media Classic-Assets sofort veröffentlicht werden.)

   Weitere Informationen zum Testen von Assets, bevor sie veröffentlicht werden, finden Sie in der [Dynamic Media Classic-Dokumentation](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html).

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

Die Aktivierung der sicheren Ansicht bedeutet, dass Ihre Assets unveröffentlicht auf den sicheren Vorschauserver gepusht werden.

Sie können dies überprüfen, indem Sie zu einer Dynamic Media Classic-Komponente auf einer Seite in AEM navigieren und auf **[!UICONTROL Bearbeiten tippen.]** Der sichere Vorschauserver ist in der URL des Assets aufgeführt. Nach der Veröffentlichung in AEM wird die Serverdomäne im Dateiverweis von der Vorschau-URL zur Produktions-URL aktualisiert.

### Aktivieren von Dynamic Media Classic für WCM {#enabling-scene-for-wcm}

Die Aktivierung von Dynamic Media Classic für WCM ist aus zwei Gründen erforderlich:

* Zum Aktivieren der Dropdown-Liste der universellen Videoprofile für die Seitenbearbeitung. Andernfalls ist die Dropdown-Liste **[!UICONTROL Universelle Video-Vorgabe]** leer und kann nicht eingestellt werden.
* Wenn sich ein digitales Asset nicht im Ordner &quot;Zielgruppe&quot;befindet, können Sie das Asset nach Dynamic Media Classic hochladen, wenn Sie Dynamic Media Classic für diese Seite in den Seiteneigenschaften aktivieren und das Asset per Drag &amp; Drop in einer Dynamic Media Classic-Komponente ablegen. Es gelten die normalen Vererbungsregeln (die untergeordneten Seiten übernehmen also die Konfiguration von der übergeordneten Seite).

Beachten Sie beim Aktivieren von Dynamic Media Classic für den WCM, dass wie bei anderen Konfigurationen Vererbungsregeln gelten. Sie können Dynamic Media Classic für WCM in der touchoptimierten oder klassischen Benutzeroberfläche aktivieren.

#### Aktivieren von Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Sites]** und dann zur Stamm-Seite Ihrer Website (nicht sprachspezifisch).

1. Wählen Sie in der Symbolleiste das Symbol [!UICONTROL settings] und tippen Sie auf **[!UICONTROL Eigenschaften öffnen.]**

1. Tippen Sie auf **[!UICONTROL Cloud Services]** und dann auf **[!UICONTROL Hinzufügen Configuration]** und wählen Sie **[!UICONTROL Dynamic Media Classic.]**
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK.]**

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen zur Verwendung in AEM mit der Dynamic Media Classic-Videokomponente auf dieser Seite und den untergeordneten Seiten zur Verfügung.

#### Aktivieren von Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche {#enabling-scene-for-wcm-in-the-classic-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche:

1. Tippen Sie in AEM auf **[!UICONTROL Websites]** und navigieren Sie zur Stammseite Ihrer Website (nicht sprachspezifisch).

1. Tippen Sie im Sidekick auf das Symbol **[!UICONTROL Seite]** und dann auf **[!UICONTROL Seiteneigenschaften.]**

1. Tippen Sie auf **[!UICONTROL Cloud Services > Hinzufügen > Dynamic Media Classic.]**
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK.]**

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen zur Verwendung in AEM mit der Dynamic Media Classic-Videokomponente auf dieser Seite und den untergeordneten Seiten zur Verfügung.

### Konfigurieren einer Standardkonfiguration {#configuring-a-default-configuration}

Wenn Sie mehrere Dynamic Media Classic-Konfigurationen haben, können Sie eine davon als Standard für den Dynamic Media Classic-Inhaltsbrowser angeben.

Es kann jeweils nur eine Dynamic Media Classic-Konfiguration als Standard markiert werden. Die Standardkonfiguration ist die Firma der Assets, die standardmäßig im Dynamic Media Classic Content Browser angezeigt werden.

Sie können die Standardkonfiguration wie folgt konfigurieren:

1. Tippen Sie auf das Symbol &quot;AEM&quot;, navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Konfiguration zu öffnen.

1. Aktivieren Sie auf der Registerkarte **[!UICONTROL Allgemein]** das Kontrollkästchen **[!UICONTROL Standardkonfiguration]**, um dies zur standardmäßigen Firma und zum Stammpfad zu machen, die im Content-Browser von Dynamic Media Classic angezeigt werden.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Wenn es nur eine Konfiguration gibt, hat die Auswahl des Kontrollkästchens **[!UICONTROL Standardkonfiguration]** keinerlei Wirkung.

### Konfigurieren des Ad-hoc-Ordners  {#configuring-the-ad-hoc-folder}

Sie können den Ordner konfigurieren, in den Assets in Dynamic Media Classic hochgeladen werden, wenn sich das Asset nicht im Ordner &quot;CQ-Zielgruppe&quot;befindet. Siehe Veröffentlichen von Assets von außerhalb des Ordners &quot;CQ-Zielgruppe&quot;.

Sie können den Ad-hoc-Ordner wie folgt konfigurieren:

1. Tippen Sie auf das Symbol &quot;AEM&quot;, navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Konfiguration zu öffnen.

1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Im Feld **[!UICONTROL Ad-hoc-Ordner]** können Sie den **Ad-hoc**-Ordner verändern. Standardmäßig handelt es sich um **Firmenname/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Konfigurieren der universellen Vorgaben {#configuring-universal-presets}

Informationen zur Konfiguration der universellen Vorgaben für die Videokomponente finden Sie unter [Video](/help/assets/s7-video.md).

## Aktivieren der Unterstützung für MIME-typbasierte Assets/Dynamic Media Classic Upload-Auftragsparameter {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

Sie können konfigurierbare Parameter für Dynamic Media Classic-Upload-Aufträge aktivieren, die durch die Synchronisierung von Digital Asset Manager/Dynamic Media Classic-Assets ausgelöst werden.

Insbesondere konfigurieren Sie hier das vom MIME-Typ akzeptierte Dateiformat im Bereich „OSGi“ (Open Service Gateway initiator) des Bedienfelds der Web-Konsolen-Konfiguration. Anschließend können Sie die einzelnen Parameter für Upload-Aufträge anpassen, die für jeden MIME-Typ in JCR (Java Content Repository) verwendet werden.

**MIME-Typen-basierte Assets können Sie wie folgt konfigurieren:**

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Tools > Vorgänge > Web-Konsole.]**
1. Klicken Sie im Bedienfeld &quot;Adobe Experience Manager Web Console Configuration&quot;im Menü **[!UICONTROL OSGi]** auf **[!UICONTROL Configuration.]**
1. Suchen Sie in der Spalte &quot;Name&quot;nach und tippen Sie auf **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]**, um die Konfiguration zu bearbeiten.
1. Tippen Sie im Bereich &quot;MIME-Typzuordnung&quot;auf ein beliebiges Pluszeichen (+), um einen MIME-Typ hinzuzufügen.

   Siehe [Unterstützte MIME-Typen](/help/assets/assets-formats.md#supported-mime-types).

1. Geben Sie in das Textfeld den neuen MIME-Typnamen ein.

   Geben Sie beispielsweise ein `<file_extension>=<mime_type>` wie in `EPS=application/postscript` ODER `PSD=image/vnd.adobe.photoshop` ein.

1. Tippen Sie in der rechten unteren Ecke des Konfigurationsfensters auf **[!UICONTROL Speichern.]**
1. Kehren Sie über die linke Leiste zu AEM zurück und tippen Sie auf „CRXDE Lite“.
1. Navigieren Sie auf der Seite &quot;CRXDE Lite&quot;in der linken Leiste zu `/etc/cloudservices/scene7/<environment>` (ersetzen Sie `<environment>` für den tatsächlichen Namen).
1. Erweitern Sie `<environment>` (ersetzen Sie `<environment>` für den tatsächlichen Namen), um den Knoten `mimeTypes` anzuzeigen.
1. Tippen Sie auf den soeben hinzugefügten mimeType.

   Beispiel: `mimeTypes > application_postscript` ODER `mimeTypes > image_vnd.adobe.photoshop`.

1. Tippen Sie auf der rechten Seite der CRXDE Lite auf die Registerkarte **[!UICONTROL Properties]**.
1. Geben Sie im Wertefeld **[!UICONTROL jobParam]** einen Dynamic Media Classic-Upload-Auftragsparameter an.

   Beispiel: `psprocess="rasterize"&psresolution=120`.

   Weitere Upload-Auftragsparameter, die Sie verwenden können, finden Sie unter [Adobe Dynamic Media Classic Image Production System API](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html).

   >[!NOTE]
   >
   >Wenn Sie PSD-Extraktionen hochladen und als Vorlagen mit Ebenendateien verarbeiten möchten, geben Sie im Wertefeld **[!UICONTROL jobParam]** Folgendes ein:
   >
   >`process=MaintainLayers&createTemplate=true`
   >
   >Vergewissern Sie sich, dass die PSD-Datei über &quot;Ebenen&quot;verfügt. Wenn es sich um ausschließlich ein Bild oder um ein Bild mit Maske handelt, wird es als Bild verarbeitet, da keine Ebenen verarbeitet werden können.

1. Tippen Sie oben links auf der Seite &quot;CRXDE Lite&quot;auf **[!UICONTROL Alle speichern.]**

## Fehlerbehebung bei der Integration von Dynamic Media Classic und AEM {#troubleshooting-scene-and-aem-integration}

Wenn Sie Probleme bei der Integration von AEM mit Dynamic Media Classic haben, finden Sie in den folgenden Lösungsszenarien weitere Informationen.

**Wenn die Veröffentlichung digitaler Assets in Dynamic Media Classic fehlschlägt:**

* Vergewissern Sie sich, dass sich das hochzuladende Asset im Ordner **[!UICONTROL CQ-Zielgruppe]** befindet (Sie geben diesen Ordner in der Dynamic Media Classic-Cloud-Konfiguration an).
* Falls nicht, müssen Sie die Cloud-Konfiguration in den **[!UICONTROL Seiteneigenschaften]** zu dieser Seite konfigurieren, um das Hochladen in den Ordner **[!UICONTROL CQ adhoc]** zu ermöglichen.

* Überprüfen Sie die Protokolle auf etwaige Informationen.

**Wenn Ihre Videovorgaben nicht angezeigt werden:**

* Stellen Sie sicher, dass Sie die Cloud-Konfiguration dieser Seite durch die **[!UICONTROL Seiteneigenschaften konfiguriert haben.]** Video-Vorgaben stehen in der Dynamic Media Classic-Videokomponente zur Verfügung.

**Wenn Ihre Video-Assets nicht in AEM wiedergegeben werden:**

* Stellen Sie sicher, dass Sie die richtige Videokomponente verwendet haben. Die Videokomponente von Dynamic Media Classic unterscheidet sich von der Video-Komponente der Grundlage. Siehe [Foundation Video Component versus Dynamic Media Classic Video Component](/help/assets/s7-video.md).

**Wenn neue oder geänderte Assets in AEM nicht automatisch in Dynamic Media Classic hochgeladen werden:**

* Stellen Sie sicher, dass sich die Assets im CQ-Zielordner befinden. Nur Assets, die sich im CQ-Zielordner befinden, werden automatisch aktualisiert (vorausgesetzt, Sie haben AEM Assets für das automatische Hochladen von Assets konfiguriert).
* Vergewissern Sie sich, dass Sie die Konfiguration der Cloud Services für &quot;Automatisches Hochladen aktivieren&quot;konfiguriert haben und dass Sie den DAM-Asset-Workflow aktualisiert und gespeichert haben, um Dynamic Media Classic-Uploads einzuschließen.
* Führen Sie beim Hochladen eines Bildes in einen Unterordner des Ordners &quot;Dynamic Media Classic Zielgruppe&quot;einen der folgenden Schritte aus:

   * Stellen Sie sicher, dass die Namen aller Assets unabhängig von ihrem Speicherort eindeutig sind. Andernfalls wird das Asset im Hauptzielordner gelöscht und es verbleibt nur das Asset im Unterordner.
   * Ändern Sie, wie Dynamic Media Classic Assets im Bereich &quot;Einstellungen&quot;des Dynamic Media Classic-Kontos überschreibt. Legen Sie Dynamic Media Classic nicht so fest, dass Assets unabhängig vom Speicherort überschrieben werden, wenn Sie Assets mit demselben Namen in Unterordnern verwenden.

**Wenn Ihre gelöschten Assets oder Ordner nicht zwischen Dynamic Media Classic und AEM synchronisiert werden:**

* In AEM Assets gelöschte Assets und Ordner werden weiterhin im synchronisierten Ordner in Dynamic Media Classic angezeigt. Sie müssen Sie manuell löschen.

**Wenn der Video-Upload fehlschlägt**

* Wenn Ihr Video-Upload fehlschlägt und Sie Video über die Dynamic Media Classic-Integration kodieren AEM, finden Sie weitere Informationen unter [Hinzufügen eines konfigurierbaren Timeouts zum Dynamic Media Classic Upload-Arbeitsablauf](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Das Importieren von Assets aus einem bestehenden Dynamic Media Classic-Firmen-Konto kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

