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
source-git-commit: 283802809d665cd979e2f1a4fa969b6ddc491ed6
workflow-type: tm+mt
source-wordcount: '5487'
ht-degree: 21%

---


# Integrieren in Dynamic Media Classic (Scene7){#integrating-with-dynamic-media-classic-scene}

[Adobe Dynamic Media ](https://help.adobe.com/en_US/scene7/using/WS26AB0D9A-F51C-464e-88C8-580A5A82F810.html) Classicis ist eine gehostete Lösung zum Verwalten, Erweitern, Veröffentlichen und Bereitstellen von Rich-Media-Assets für Web-, Mobil-, E-Mail- und Internetanzeigen und Drucken.

Um Dynamic Media Classic verwenden zu können, müssen Sie die Cloud-Konfiguration so konfigurieren, dass Dynamic Media Classic und AEM Assets miteinander interagieren können. In diesem Dokument wird beschrieben, wie Sie AEM und Dynamic Media Classic konfigurieren.

Informationen zur Verwendung aller Komponenten von Dynamic Media Classic auf einer Seite und zum Arbeiten mit Videos finden Sie unter [Verwenden von Dynamic Media Classic](../assets/scene7.md).

>[!NOTE]
>
>* Die DHTML-Viewer-Plattform von Dynamic Media Classic hat am 31. Januar 2014 offiziell das Ende des Lebenszyklus erreicht. Weitere Informationen finden Sie in den [FAQ zur Einstellung von DHTML-Viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Bevor Sie Dynamic Media Classic für die Verwendung mit AEM konfigurieren, lesen Sie [Best Practices](#best-practices-for-integrating-scene-with-aem) für die Integration von Dynamic Media Classic in AEM.
>* Wenn Sie Dynamic Media Classic mit einer benutzerdefinierten Proxykonfiguration verwenden, müssen Sie sowohl HTTP Client-Proxykonfigurationen konfigurieren, da einige Funktionen von AEM die 3.x-APIs und einige andere die 4.x-APIs verwenden. 3.x ist mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert und 4.x mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.

>



## AEM/Dynamic Media Classic-Integration versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

AEM Benutzer haben die Wahl zwischen zwei Lösungen, um mit dynamischen Medien zu arbeiten: Integrieren Sie entweder Ihre Instanz von AEM in Dynamic Media Classic oder verwenden Sie die Dynamic Media-Lösung, die in AEM integriert ist.

Verwenden Sie die folgenden Kriterien, um zu bestimmen, welche Lösung ausgewählt werden soll:

* Wenn Sie ein **vorhandener**-Kunde von Dynamic Media Classic sind, dessen Rich-Media-Assets zu Veröffentlichungs- und Versand-Zwecken in Dynamic Media Classic gespeichert sind, Sie diese Assets jedoch mit WCM-Authoring und/oder AEM Assets für die Verwaltung integrieren möchten, verwenden Sie die in diesem Dokument beschriebene Punkt-zu-Punkt-Integration [AEM/Dynamic Media Classic.](#aem-scene-point-to-point-integration)

* Wenn Sie AEM-**Neukunde** sind und Rich-Media-Bereitstellung benötigen, wählen Sie die [Option „Dynamic Media“](#aem-dynamic-media) aus. Diese Option ist am sinnvollsten, wenn Sie über kein vorhandenes S7-Konto verfügen und wenn Sie nicht über viele im System gespeicherte Assets verfügen.

* In bestimmten Fällen möchten Sie vielleicht beide Lösungen verwenden. Das [Dual-use-Szenario](/help/sites-administering/scene7.md#dual-use-scenario) beschreibt dieses Szenario.

### AEM/Dynamic Media Classic Point-to-Point-Integration {#aem-scene-point-to-point-integration}

Wenn Sie in dieser Lösung mit Assets arbeiten, nutzen Sie eine der folgenden Vorgehensweisen:

* Hochladen von Assets direkt auf Dynamic Media Classic und anschließenden Zugriff über den Inhaltsbrowser **Dynamic Media Classic** zum Erstellen von Seiten oder
* Hochladen auf AEM Assets und anschließendes Aktivieren der automatischen Veröffentlichung auf Dynamic Media Classic Sie greifen über den Inhaltsbrowser **Assets** zum Erstellen von Seiten zu.

Die Komponenten, die Sie für diese Integration verwenden, befinden sich im Komponentenbereich **Dynamischer Medienklassiker** im Designmodus.](/help/sites-authoring/author-environment-tools.md#page-modes)[

### AEM Dynamic Media {#aem-dynamic-media}

AEM Dynamic Media ist die Vereinheitlichung der Funktionen von Dynamic Media Classic direkt innerhalb der AEM Plattform.

Wenn Sie innerhalb dieser Lösung mit Assets arbeiten, befolgen Sie diesen Workflow:

1. Laden Sie Assets mit einzelnen Bildern und Videos direkt in AEM hoch.
1. Kodieren Sie Videos direkt in AEM.
1. Erstellen Sie bildbasierte Sets direkt in AEM.
1. Fügen Sie Bildern und Videos bei Bedarf interaktive Elemente hinzu.

Die von Ihnen für Dynamic Media verwendeten Komponenten befinden sich im Komponentenbereich **[!UICONTROL Dynamic Media]** im [Designmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Sie umfassen Folgendes:

* **[!UICONTROL Dynamic Media]** – Die Komponente **[!UICONTROL Dynamic Media]** ist intelligent. In Abhängigkeit davon, ob Sie ein Bild oder Video hinzufügen, haben Sie verschiedene Optionen. Die Komponente unterstützt Bildvorgaben, bildbasierte Viewer wie Bild-Sets sowie Rotations-Sets, Sets für gemischte Medien und Videos. Zudem ist der Viewer dynamisch. Die Größe des Bildschirms ändert sich demnach automatisch auf Grundlage der Bildschirmgröße. Bei allen Viewern handelt es sich um HTML5-Viewer.

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
    <td>Hochladen von Assets zu AEM und Verwenden AEM Komponente für dynamische Medien, um Assets auf Siteseiten zu erstellen</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td>Off</td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Im Handel und sind neu bei Sites und dynamischen Medien</td>
    <td>Laden Sie nicht produktspezifische Assets zur Verwaltung und zum Versand in AEM hoch. Laden Sie PRODUKT-Assets in Dynamic Media Classic hoch und verwenden Sie den Browser für dynamische Medien-Classic-Inhalte in AEM und Komponente, um Produktdetailseiten auf Sites zu erstellen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Neu bei Assets und dynamischen Medien</td>
    <td>Assets auf AEM Assets hochladen und veröffentlichten URL-/Einbettungscode aus dynamischen Medien verwenden</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Aus</td>
    <td>Aus</td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Neu bei dynamischen Medien und Vorlagen</td>
    <td>Verwenden Sie dynamische Medien für Bildbearbeitung und Video. Erstellen Sie Bildvorlagen in Dynamic Media Classic und verwenden Sie die Inhaltssuche für Dynamic Media Classic, um Vorlagen in Seiten mit Sites einzuschließen.</td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Ein</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Ein vorhandener Kunde von Dynamic Media Classic und neu bei Sites</td>
    <td>Hochladen von Assets in Dynamic Media Classic und Verwenden AEM Browser für dynamische Medien-Classic-Inhalte, um Assets auf Seiten von Sites zu suchen und zu erstellen</td>
    <td>Aus</td>
    <td>Aus</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td>Aus</td>
    </tr>
    <tr>
    <td>Ein vorhandener Kunde von Dynamic Media Classic, der neu bei Sites und Assets ist</td>
    <td>Laden Sie Assets zu DAM hoch und veröffentlichen Sie sie automatisch zum Versand auf Dynamic Media Classic. Verwenden Sie AEM Browser für dynamische Medien-Classic-Inhalte, um Assets auf Sites-Seiten zu suchen und zu erstellen.</td>
    <td>Aus</td>
    <td>Aus</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Ein</a></td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    <tr>
    <td>Bestehender Kunde von Dynamic Media Classic und neuer Kunde von Assets</td>
    <td><p>Laden Sie Assets hoch und verwenden Sie dynamische Medien, um Darstellungen zum Herunterladen/Freigeben zu generieren. Veröffentlichen Sie AEM Assets automatisch zum Versand in Dynamic Media Classic.</p> <p><strong>Wichtig: Die Verarbeitung und Darstellung von </strong> Incurs-Duplikaten, die in AEM generiert wurden, werden nicht mit Dynamic Media Classic synchronisiert.</p> </td>
    <td><p>Ein</p> <p>(Siehe Schritt 3)</p> </td>
    <td>Aus</td>
    <td>Aus</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Ein</a></p> <p>(Siehe Schritt 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (Optional) (siehe Verwendungsfalltabelle) - Richten Sie die [Konfiguration der dynamischen Medien-Cloud](/help/assets/config-dynamic.md) ein und [aktivieren Sie den Server für dynamische Medien](/help/assets/config-dynamic.md).
1. (Optional) (siehe Verwendungsfalltabelle) - Wenn Sie die Option &quot;Automatisches Hochladen von Assets zu Dynamisch Media Classic&quot;aktivieren, müssen Sie Folgendes hinzufügen:

   1. Richten Sie den automatischen Upload auf Dynamic Media Classic ein.
   1. hinzufügen Sie den Schritt **Hochladen von dynamischen Medien in Classic** nach allen Schritten des Arbeitsablaufs für dynamische Medien *am Ende* **Dam-Update-Asset**-Arbeitsablauf ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Optional) Schränken Sie das Hochladen von Dynamischen Medien-Classic-Assets nach MIME-Typ in [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl) ein. Asset-MIME-Typen, die nicht in dieser Liste enthalten sind, werden nicht auf den Dynamic Media Classic-Server hochgeladen.
   1. (Optional) Richten Sie Videos in der Konfiguration von Dynamic Media Classic ein. Sie können die Videokodierung für entweder dynamische Medien und Dynamic Media Classic gleichzeitig aktivieren. Dynamische Darstellungen werden für die lokale Vorschau und Wiedergabe in AEM Instanz verwendet, während Videodarstellungen von Dynamic Media Classic auf Servern von Dynamic Media Classic generiert und gespeichert werden. Wenden Sie beim Einrichten von Videokodierungsdiensten für dynamische Medien und Dynamic Media Classic ein [Videoverarbeitung-Profil](/help/assets/video-profiles.md) auf den Asset-Ordner von Dynamic Media Classic an.
   1. (Optional) [Sichere Vorschau in Dynamic Media Classic konfigurieren](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beschränkungen {#limitations}

Wenn Sie sowohl dynamische Medien als auch klassische Medien aktiviert haben, gelten folgende Einschränkungen:

* Das manuelle Hochladen auf Dynamic Media Classic durch Auswahl eines Assets und Ziehen auf eine Komponente des Typs Dynamic Media Classic auf einer AEM funktioniert nicht.
* Obwohl synchronisierte Assets mit AEM-Dynamic Media Classic beim Bearbeiten des Assets automatisch auf &quot;Dynamisch Media Classic&quot;aktualisiert werden, löst eine Rollback-Aktion keinen neuen Upload aus. Daher wird die neueste Version von Dynamisch Media Classic nicht unmittelbar nach einem Rollback abgerufen. Als Ausweichlösung eignet sich die erneute Bearbeitung, sobald das Rollback abgeschlossen ist.
* Wenn Sie für einen Anwendungsfall dynamische Medien und für einen anderen Anwendungsfall die Integration von Dynamic Media Classic verwenden müssen, damit die dynamischen Medien-Assets nicht mit dem Dynamischen Media Classic-System interagieren, wenden Sie die Konfiguration von Dynamic Media Classic nicht auf den Ordner &quot;Dynamische Medien&quot;oder die dynamische Medienkonfiguration (Verarbeitungs-Profil) auf einen Dynamischen Media Classic-Ordner an.

## Best Practices für die Integration von Dynamic Media Classic mit AEM {#best-practices-for-integrating-scene-with-aem}

Bei der Integration von Dynamic Media Classic mit AEM gibt es einige wichtige Best Practices, die in den folgenden Bereichen beachtet werden müssen:

* Testen Ihrer Integration
* Hochladen von Assets direkt von Dynamic Media Classic empfohlen für bestimmte Szenarien

Siehe [bekannte Beschränkungen](#known-limitations-and-design-implications).

### Testen Ihrer Integration {#test-driving-your-integration}

Adobe empfiehlt, dass Sie die Integration testen, indem Sie den Stammordner nur auf einen Unterordner und nicht auf eine ganze Firma verweisen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto der Firma &quot;Dynamische Medien - Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets und kann zum Absturz Ihres Systems führen).

### Hochladen von Assets aus AEM Assets im Vergleich zu Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

Sie können Assets entweder mit der Funktion &quot;Assets&quot;(Digital Asset Management) oder über den Inhaltsbrowser &quot;Dynamic Media Classic&quot;AEM direkt hochladen. Was davon Sie verwenden, hängt von den folgenden Faktoren ab:

* Die von AEM Assets noch nicht unterstützten Asset-Typen für Dynamic Media Classic müssen direkt von Dynamic Media Classic über den Inhaltsbrowser Dynamic Media Classic, z. B. Bildvorlagen, zu einer AEM Website hinzugefügt werden.
* Bei Asset-Typen, die von AEM Assets und Dynamic Media Classic unterstützt werden, hängt die Entscheidung, wie sie hochgeladen werden, von Folgendem ab:

   * Wo sich die Assets heute befinden UND
   * Wie wichtig ihre Verwaltung in einem gemeinsamen Repository ist

Wenn sich die Assets bereits in Dynamic Media Classic befinden und ihre Verwaltung in einem gemeinsamen Repository nicht so wichtig ist, wäre es ein unnötiger Umweg, sie nur nach AEM Assets zu exportieren, um sie für den Versand wieder mit Dynamic Media Classic zu synchronisieren. Andernfalls ist es empfehlenswert, Assets nur zum Versand in einem Repository zu belassen und mit Dynamic Media Classic zu synchronisieren.

## Konfigurieren der Integration von Dynamic Media Classic {#configuring-scene-integration}

Sie können AEM so konfigurieren, dass Assets in Dynamic Media Classic hochgeladen werden. Assets aus einem CQ-Zielgruppen-Ordner können (automatisch oder manuell) von AEM in ein Konto für die Firma von Dynamic Media Classic hochgeladen werden.

>[!NOTE]
>
>Adobe empfiehlt, nur den angegebenen Ordner &quot;Zielgruppe&quot;zum Importieren von Dynamischen Medien-Classic-Assets zu verwenden. Digitale Assets, die sich außerhalb des Ordners &quot;Zielgruppe&quot;befinden, können nur in Dynamisch Media Classic-Komponenten auf Seiten verwendet werden, auf denen die Konfiguration für Dynamische Medien Classic aktiviert wurde. Darüber hinaus werden sie in einem Ad-hoc-Ordner in Dynamic Media Classic abgelegt. Der Ad-hoc-Ordner wird nicht mit AEM synchronisiert (Assets können jedoch im Inhaltsbrowser von Dynamic Media Classic gefunden werden).

Um die Integration von Dynamic Media Classic in AEM zu konfigurieren, müssen Sie die folgenden Schritte ausführen:

1. [Definieren einer Cloud-Konfiguration](#creating-a-cloud-configuration-for-scene) : Definiert die Zuordnung zwischen einem Ordner &quot;Dynamic Media Classic&quot;und einem Ordner &quot;Assets&quot;. Sie müssen diesen Schritt auch dann ausführen, wenn Sie nur eine einseitige Synchronisierung (AEM Assets zu Dynamic Media Classic) wünschen.
1. [Aktivieren Sie den  **Adobe CQ s7dam Dam Listener**](#enabling-the-adobe-cq-scene-dam-listener) - Fertig in der   OSGiconsole.
1. Wenn AEM Assets automatisch in Dynamic Media Classic hochgeladen werden sollen, müssen Sie diese Option aktivieren und dem Arbeitsablauf [!UICONTROL DAM Update Asset] den Eintrag Dynamic Media Classic hinzufügen. Außerdem können Sie manuell Assets hochladen.
1. Hinzufügen von Komponenten aus Dynamic Media Classic zum Sidekick. Auf diese Weise können Benutzer auf ihren AEM Komponenten von Dynamic Media Classic verwenden.
1. [Ordnen Sie die Konfiguration der Seite in AEM](#enabling-scene-for-wcm)  zu. Dieser Schritt ist erforderlich, um alle Video-Vorgaben, die Sie in Dynamic Media Classic erstellt haben, Ansicht. Es ist auch erforderlich, wenn Sie ein Asset von außerhalb des Ordners &quot;CQ-Zielgruppe&quot;in &quot;Dynamic Media Classic&quot;veröffentlichen müssen.

In diesem Abschnitt wird die Durchführung all dieser Schritte behandelt und es werden wichtige Beschränkungen aufgeführt.

### Funktionsweise der Synchronisierung zwischen Dynamic Media Classic und AEM Assets {#how-synchronization-between-scene-and-aem-assets-works}

Beim Einrichten der Synchronisierung mit AEM Assets und Dynamic Media Classic ist Folgendes wichtig:

#### Hochladen auf Dynamic Media Classic von AEM Assets {#uploading-to-scene-from-aem-assets}

* Es gibt einen bestimmten Synchronisierungsordner in AEM für Dynamic Media Classic-Uploads.
* Uploads in Dynamic Media Classic können automatisiert werden, wenn die digitalen Assets in dem angegebenen Synchronisierungsordner abgelegt werden.
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
   <td>Pro Firma können Sie in AEM nur einen bestimmten Ordner für Dynamic Media Classic-Uploads verwenden. Sie können mehrere Konfigurationen erstellen, wenn Sie Zugriff auf mehr als ein Firma-Konto in Dynamic Media Classic benötigen.</td>
  </tr>
  <tr>
   <td>Ordnerstruktur</td>
   <td>Wenn Sie einen synchronisierten Ordner mit Assets löschen, werden alle Remote-Assets von Dynamic Media Classic gelöscht, der Ordner bleibt jedoch erhalten.</td>
  </tr>
  <tr>
   <td>Ad-hoc-Ordner</td>
   <td>Assets, die sich außerhalb des Ordners "Zielgruppe"befinden und manuell in den WCM-Ordner "Dynamic Media Classic"hochgeladen werden, werden unter "Dynamic Media Classic"automatisch in einen separaten Ad-hoc-Ordner abgelegt. Dies wird in der Cloud-Konfiguration in AEM konfiguriert.</td>
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
   <td>Achten Sie bei der Synchronisierung zwischen AEM und Dynamic Media Classic darauf, die Benutzeroberfläche auf Änderungen der Ansicht zu aktualisieren. </td>
  </tr>
  <tr>
   <td>Videominiaturen</td>
   <td>Wenn Sie ein Video zur Kodierung über Dynamic Media Classic auf AEM Assets hochladen, kann es abhängig von der Videoverarbeitung einige Zeit dauern, bis die Videominiaturen und kodierten Videos in AEM Assets verfügbar sind.</td>
  </tr>
  <tr>
   <td>Zielgruppen-Unterordner</td>
   <td><p>Wenn Sie Unterordner im Ordner "Zielgruppe"verwenden, stellen Sie sicher, dass Sie entweder eindeutige Namen für jedes Asset verwenden (unabhängig vom Speicherort) oder dass Sie "Dynamic Media Classic"(im Bereich "Einstellungen") konfigurieren, um Assets unabhängig vom Speicherort nicht zu überschreiben.</p> <p>Andernfalls werden Assets mit demselben Namen, die in einen Unterordner der Zielgruppe "Dynamische Medien - Klassische Medien"hochgeladen werden, hochgeladen, der gleichnamige Asset im Ordner "Zielgruppe"wird jedoch gelöscht. </p> </td>
  </tr>
 </tbody>
</table>

### Konfigurieren von Servern für dynamische Medien - Classic {#configuring-scene-servers}

Wenn Sie AEM hinter einem Proxy ausführen oder spezielle Firewall-Einstellungen haben, müssen Sie die Hosts der verschiedenen Regionen explizit aktivieren. Server werden im Inhalt in `/etc/cloudservices/scene7/endpoints` verwaltet und können nach Bedarf angepasst werden. Tippen Sie auf eine URL und bearbeiten Sie die URL bei Bedarf. In früheren Versionen von AEM waren diese Werte hartkodiert.

Wenn Sie zu `/etc/cloudservices/scene7/endpoints.html` navigieren, werden die Server aufgelistet (und können sie bearbeiten, indem Sie auf die URL klicken):

![chlimage_1-296](assets/chlimage_1-296.png)

### Erstellen einer Cloud-Konfiguration für Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Eine Cloud-Konfiguration definiert die Zuordnung zwischen einem Ordner &quot;Dynamic Media Classic&quot;und einem AEM Assets-Ordner. Es muss konfiguriert werden, um AEM Assets mit Dynamic Media Classic zu synchronisieren. Unter Funktionsweise der Synchronisierung finden Sie weitere Informationen.

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto der Firma &quot;Dynamische Medien - Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

>[!NOTE]
>
>Sie können über mehrere Konfigurationen verfügen: Eine Cloud-Konfiguration stellt einen Benutzer in einer Firma von Dynamic Media Classic dar. Wenn Sie auf andere Firmen oder Benutzer von Dynamic Media Classic zugreifen möchten, müssen Sie mehrere Konfigurationen erstellen.

So konfigurieren Sie AEM für das Veröffentlichen von Assets in Dynamic Media Classic:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, um auf die Adobe Dynamic Media Classic zuzugreifen.

1. Tippen Sie auf **[!UICONTROL Jetzt konfigurieren.]**

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** und optional im Feld **[!UICONTROL Name]** die entsprechenden Informationen ein. Tippen Sie auf **[!UICONTROL Erstellen.]**

   >[!NOTE]
   >
   >Beim Erstellen zusätzlicher Konfigurationen wird das Feld **[!UICONTROL Übergeordnete Konfiguration]** angezeigt.
   >
   >Ändern Sie **nicht** die übergeordnete Konfiguration. Das Ändern der übergeordneten Konfiguration kann zum Scheitern der Integration führen.

1. Geben Sie die E-Mail-Adresse, das Kennwort und den Bereich Ihres Kontos für Dynamic Media Classic ein und tippen Sie auf **[!UICONTROL Verbindung zu Dynamic Media Classic herstellen.]** Sie sind mit dem Dynamic Media Classic-Server verbunden und das Dialogfeld wird mit weiteren Optionen erweitert.

1. Geben Sie den Namen **[!UICONTROL Firma]** und **[!UICONTROL Stammpfad]** ein (dies ist der veröffentlichte Servername zusammen mit jedem Pfad, den Sie angeben möchten; Wenn Sie den Namen des veröffentlichten Servers nicht kennen, gehen Sie in Dynamic Media Classic zu **[!UICONTROL Einstellungen > Anwendungseinstellungen.]**)

   >[!NOTE]
   >
   >Der Stammpfad von Dynamic Media Classic ist der Ordner &quot;Dynamic Media Classic&quot;, mit dem eine Verbindung hergestellt AEM. Es kann auf einen spezifischen Ordner eingegrenzt werden.

   >[!CAUTION]
   >
   >Je nach der Größe des Ordners &quot;Dynamic Media Classic&quot;kann es lange dauern, einen Stammordner zu importieren. Darüber hinaus könnten die Daten aus Dynamic Media Classic die AEM Datenspeicherung überschreiten. Stellen Sie sicher, dass Sie in den richtigen Ordner importieren. Der Import einer zu großen Menge von Daten kann zur Unterbrechung Ihres Systems führen.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Klicken Sie auf **[!UICONTROL OK.]** AEM speichert Ihre Konfiguration.

>[!NOTE]
>
>Wenn Sie eine erneute Verbindung herstellen:
>
>* Wenn Sie beim Veröffentlichen wieder eine Verbindung zu Dynamic Media Classic herstellen, müssen Sie das Kennwort beim Veröffentlichen zurücksetzen, sonst funktioniert die erneute Verbindung nicht. Bei der Autoreninstanz stellt dies kein Problem dar.
>* Wenn Sie Werte wie Region und Firma ändern, müssen Sie die Verbindung zu Dynamic Media Classic wiederherstellen. Wenn Konfigurationsoptionen geändert, aber nicht gespeichert wurden, zeigt AEM fälschlicherweise nach wie vor an, dass die Konfiguration gültig ist. Achten Sie darauf, eine erneute Verbindung herzustellen.

>



### Aktivieren des Adobe CQ Dynamic Media Classic Dam Listener {#enabling-the-adobe-cq-scene-dam-listener}

Sie müssen den Adobe CQ Dynamic Media Classic Dam Listener aktivieren, der standardmäßig deaktiviert ist.

So aktivieren Sie ihn:

1. Tippen Sie auf das Symbol [!UICONTROL Tools] und navigieren Sie dann zu **[!UICONTROL Vorgänge > Web-Konsole.]** Die Web-Konsole wird geöffnet.
1. Navigieren Sie zu **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktiviert]**.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Tippen Sie auf **[!UICONTROL Speichern.]**

### Hinzufügen eines konfigurierbaren Timeouts zum Arbeitsablauf für das Hochladen dynamischer Medien - Classic {#adding-configurable-timeout-to-scene-upload-workflow}

Wenn eine AEM-Instanz so konfiguriert wird, dass die Videokodierung durch Dynamic Media Classic (Scene7) abgewickelt wird, gibt es standardmäßig ein 35-minütiges Timeout zu jedem Upload-Auftrag. Um Videokodierungsaufträge mit potenziell längerer Dauer zu ermöglichen, können Sie diese Einstellung konfigurieren:

1. Navigieren Sie zu **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Ändern Sie die Zahl wie gewünscht im Feld **[!UICONTROL Zeitüberschreitung bei aktiven Aufträgen]**. Jede positive Zahl wird binnen Sekunden mit der Maßeinheit akzeptiert. Standardmäßig ist dies auf 2100 festgelegt.

   >[!NOTE]
   >
   >Best Practice: Bei den meisten Assets dauert das Übernehmen höchstens einige Minuten (beispielsweise bei Bildern). Doch in bestimmten Fällen – beispielsweise bei größeren Videos – sollte der Timeout-Wert auf 7200 Sekunden (2 Stunden) erhöht werden, um eine lange Verarbeitungszeit zu ermöglichen. Andernfalls wird dieser Upload-Auftrag für Dynamic Media Classic in den JCR-Metadaten als **[!UICONTROL UploadFehlgeschlagen]** markiert.

1. Tippen Sie auf **[!UICONTROL Speichern.]**

### Automatisches Hochladen von AEM Assets {#autouploading-from-aem-assets}

Ab AEM 6.3.2 ist AEM Assets jetzt für Sie konfiguriert, sodass alle digitalen Assets, die Sie in den Digital Asset Manager hochladen, automatisch auf Dynamic Media Classic aktualisiert werden, wenn sich die Assets in einem CQ-Zielgruppen-Ordner befinden.

Wenn ein Asset in AEM Assets hinzugefügt wird, wird es automatisch hochgeladen und auf Dynamic Media Classic veröffentlicht.

>[!NOTE]
>
>Die maximale Dateigröße für das automatische Hochladen von AEM Assets auf Dynamic Media Classic beträgt 500 MB.

So wird das automatische Hochladen von AEM Assets konfiguriert:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**. Tippen Sie dann unter der Überschrift &quot;Dynamische Medien&quot;unter Verfügbare Konfigurationen auf **[!UICONTROL dms7 (Dynamische Medien]**)
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert]**, aktivieren Sie das Kontrollkästchen **[!UICONTROL Automatisches Hochladen aktivieren]** und tippen Sie dann auf **[!UICONTROL OK.]** Sie müssen jetzt den DAM-Asset-Workflow so konfigurieren, dass auch Hochladen in Dynamic Media Classic einbezogen wird.

   >[!NOTE]
   >
   >Informationen zum Übertragen von Assets in einen unveröffentlichten Zustand nach Dynamic Media Classic finden Sie unter [Konfigurieren des Status (veröffentlicht/unveröffentlicht) von Assets, die an Dynamic Media Classic gesendet werden.](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene)

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Navigieren Sie zurück zur AEM Begrüßungsseite und tippen Sie auf **[!UICONTROL Workflows.]** Doppelklicken Sie auf den Workflow **DAM-Update-Asset**, um ihn zu öffnen.
1. Navigieren Sie im Sidekick zu den Komponenten **[!UICONTROL Workflow]** und wählen Sie **[!UICONTROL Dynamic Media Classic.]** Ziehen Sie  **[!UICONTROL Dynamic Media]** Classic in den Workflow und tippen Sie auf  **[!UICONTROL Speichern.]** Assets, die im Ordner &quot;Zielgruppe&quot;zu AEM Assets hinzugefügt wurden, werden automatisch zu Dynamic Media Classic hochgeladen.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wenn Assets nach der Automatisierung hinzugefügt und nicht im Ordner &quot;CQ-Zielgruppe&quot;abgelegt werden, werden sie nicht in Dynamic Media Classic hochgeladen.
   >* AEM bettet alle Metadaten wie XMP ein, bevor sie in Dynamic Media Classic hochgeladen werden, sodass alle Eigenschaften auf dem Metadaten-Knoten in Dynamic Media Classic XMP verfügbar sind.


### Konfigurieren des Status (veröffentlicht/unveröffentlicht) von Assets, die an Dynamic Media Classic {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene} gesendet werden

Wenn Sie Assets von AEM Assets zu Dynamic Media Classic verschieben, können Sie sie entweder automatisch veröffentlichen (Standardverhalten) oder in einem unveröffentlichten Zustand zu Dynamic Media Classic verschieben.

Möglicherweise möchten Sie Assets nicht sofort in Dynamic Media Classic veröffentlichen, wenn Sie sie in einer Staging-Umgebung testen möchten, bevor sie live geschaltet werden. Sie können AEM mit der Secure Test-Umgebung von Dynamic Media Classic verwenden, um Assets in einem unveröffentlichten Zustand direkt von Assets in Dynamic Media Classic zu übertragen.

Dynamic Media Classic-Assets bleiben über eine sichere Vorschau verfügbar. Nur wenn Assets in AEM veröffentlicht werden, werden die Assets von Dynamic Media Classic auch in der Produktion live geschaltet.

Wenn Sie Assets sofort veröffentlichen möchten, wenn Sie sie zu Dynamic Media Classic verschieben, müssen Sie keine Optionen konfigurieren. Dies ist das Standardverhalten.

Wenn Sie jedoch nicht möchten, dass Assets, die automatisch an Dynamic Media Classic gesendet werden, automatisch veröffentlicht werden, wird in diesem Abschnitt beschrieben, wie AEM und Dynamic Media Classic dazu konfiguriert werden.

#### Voraussetzungen für das Weiterleiten von Assets an nicht veröffentlichte dynamische Medien-Classic {#prerequisites-to-push-assets-to-scene-unpublished}

Bevor Sie Assets an Dynamic Media Classic senden können, ohne sie zu veröffentlichen, müssen Sie Folgendes einrichten:

1. [Verwenden Sie die Admin Console, um einen Supportfall zu erstellen.](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) In Ihrem Support-Fall fordern Sie die Aktivierung der sicheren Vorschau für Ihr Dynamic Media Classic-Konto an.
1. Befolgen Sie die Anweisungen zum Einrichten der sicheren Vorschau für Ihr Konto bei Dynamic Media Classic.](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html)[

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

### Festlegen des Status von Assets, die als unveröffentlicht ({#setting-the-state-of-assets-pushed-to-scene-as-unpublished}) an Dynamic Media Classic gesendet werden

>[!NOTE]
>
>Wenn ein Benutzer das Asset in AEM veröffentlicht, aktiviert es automatisch das S7-Asset in der Produktion/im Live-Asset (das Asset befindet sich dann nicht mehr in der sicheren Vorschau/im unveröffentlichten Status).

So legen Sie den Status der Assets fest, die an Dynamic Media Classic als unveröffentlicht gesendet werden:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Wählen Sie im Dropdownmenü **[!UICONTROL Sichere Ansicht aktivieren]** die Option **[!UICONTROL Bei AEM-Aktivierung für Veröffentlichungen]**, um Assets ohne Veröffentlichung in Dynamic Media Classic zu verschieben. (Standardmäßig ist dieser Wert auf **[!UICONTROL Sofort]** festgelegt, wobei die Elemente von Dynamic Media Classic sofort veröffentlicht werden.)

   Weitere Informationen zum Testen von Assets, bevor sie veröffentlicht werden, finden Sie in der [Dokumentation zu Dynamic Media Classic](https://help.adobe.com/en_US/scene7/using/WSd968ca97bf00cf72-5eeee3a113268dc80f5-8000.html).

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Tippen Sie auf **[!UICONTROL OK]**.

Die Aktivierung der sicheren Ansicht bedeutet, dass Ihre Assets unveröffentlicht auf den sicheren Vorschauserver gepusht werden.

Sie können dies überprüfen, indem Sie zu einer Komponente für dynamische Medien-Classic auf einer Seite in AEM navigieren und auf **[!UICONTROL Bearbeiten tippen.]** Der sichere Vorschauserver ist in der URL des Assets aufgeführt. Nach der Veröffentlichung in AEM wird die Serverdomäne im Dateiverweis von der Vorschau-URL zur Produktions-URL aktualisiert.

### Aktivieren von Dynamic Media Classic für WCM {#enabling-scene-for-wcm}

Die Aktivierung von Dynamic Media Classic für WCM ist aus zwei Gründen erforderlich:

* Zum Aktivieren der Dropdown-Liste der universellen Videoprofile für die Seitenbearbeitung. Andernfalls ist die Dropdown-Liste **[!UICONTROL Universelle Video-Vorgabe]** leer und kann nicht eingestellt werden.
* Wenn sich ein digitales Asset nicht im Ordner &quot;Zielgruppe&quot;befindet, können Sie das Asset in &quot;Dynamic Media Classic&quot;hochladen, wenn Sie für diese Seite in den Seiteneigenschaften &quot;Dynamic Media Classic&quot;aktivieren und das Asset per Drag &amp; Drop auf eine Komponente von Dynamic Media Classic ziehen. Es gelten die normalen Vererbungsregeln (die untergeordneten Seiten übernehmen also die Konfiguration von der übergeordneten Seite).

Beachten Sie beim Aktivieren von Dynamic Media Classic für den WCM, dass wie bei anderen Konfigurationen Vererbungsregeln gelten. Sie können Dynamic Media Classic für WCM entweder in der touchoptimierten oder in der klassischen Benutzeroberfläche aktivieren.

#### Aktivieren von Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der touchoptimierten Benutzeroberfläche:

1. Tippen Sie auf das AEM-Symbol und navigieren Sie zu **[!UICONTROL Sites]** und dann zur Stamm-Seite Ihrer Website (nicht sprachspezifisch).

1. Wählen Sie in der Symbolleiste das Symbol [!UICONTROL settings] und tippen Sie auf **[!UICONTROL Eigenschaften öffnen.]**

1. Tippen Sie auf **[!UICONTROL Cloud Services]** und dann auf **[!UICONTROL Hinzufügen Configuration]** und wählen Sie **[!UICONTROL Dynamic Media Classic.]**
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK.]**

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen zur Verwendung in AEM mit der Videokomponente Dynamic Media Classic auf dieser Seite und untergeordneten Seiten zur Verfügung.

#### Aktivieren von Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche {#enabling-scene-for-wcm-in-the-classic-user-interface}

So aktivieren Sie Dynamic Media Classic für WCM in der klassischen Benutzeroberfläche:

1. Tippen Sie in AEM auf **[!UICONTROL Websites]** und navigieren Sie zur Stammseite Ihrer Website (nicht sprachspezifisch).

1. Tippen Sie im Sidekick auf das Symbol **[!UICONTROL Seite]** und dann auf **[!UICONTROL Seiteneigenschaften.]**

1. Tippen Sie auf **[!UICONTROL Cloud Services > Hinzufügen > Dynamic Media Classic.]**
1. Wählen Sie in der Dropdown-Liste **[!UICONTROL Adobe Dynamic Media Classic]** die gewünschte Konfiguration aus und tippen Sie auf **[!UICONTROL OK.]**

   Video-Vorgaben aus dieser Konfiguration von Dynamic Media Classic stehen zur Verwendung in AEM mit der Videokomponente Dynamic Media Classic auf dieser Seite und untergeordneten Seiten zur Verfügung.

### Konfigurieren einer Standardkonfiguration {#configuring-a-default-configuration}

Wenn Sie mehrere Konfigurationen für dynamische Medien Classic haben, können Sie eine davon als Standard für den Content-Browser von Dynamic Media Classic angeben.

Es kann jeweils nur eine Konfiguration von Dynamic Media Classic als Standard markiert werden. Bei der Standardkonfiguration handelt es sich um die Firmen-Assets, die standardmäßig im Content Browser für dynamische Medien und Klassische Inhalte angezeigt werden.

Sie können die Standardkonfiguration wie folgt konfigurieren:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Konfiguration zu öffnen.

1. Aktivieren Sie auf der Registerkarte **[!UICONTROL Allgemein]** das Kontrollkästchen **[!UICONTROL Standardkonfiguration]**, um dies zur standardmäßigen Firma und zum Stammpfad zu machen, die im Content Browser von Dynamic Media Classic angezeigt werden.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Wenn es nur eine Konfiguration gibt, hat die Auswahl des Kontrollkästchens **[!UICONTROL Standardkonfiguration]** keinerlei Wirkung.

### Konfigurieren des Ad-hoc-Ordners  {#configuring-the-ad-hoc-folder}

Sie können den Ordner konfigurieren, in den Assets in Dynamic Media Classic hochgeladen werden, wenn sich das Asset nicht im Ordner &quot;CQ-Zielgruppe&quot;befindet. Siehe Veröffentlichen von Assets von außerhalb des Ordners &quot;CQ-Zielgruppe&quot;.

Sie können den Ad-hoc-Ordner wie folgt konfigurieren:

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Bereitstellung > Cloud Services]**, tippen Sie auf **[!UICONTROL Dynamic Media Classic]** und wählen Sie Ihre Konfiguration in Dynamic Media Classic aus.
1. Tippen Sie auf **[!UICONTROL Bearbeiten]**, um die Konfiguration zu öffnen.

1. Tippen Sie auf die Registerkarte **[!UICONTROL Erweitert.]** Im Feld **[!UICONTROL Ad-hoc-Ordner]** können Sie den **Ad-hoc**-Ordner verändern. Standardmäßig handelt es sich um **Firmenname/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Konfigurieren der universellen Vorgaben {#configuring-universal-presets}

Informationen zur Konfiguration der universellen Vorgaben für die Videokomponente finden Sie unter [Video](/help/assets/s7-video.md).

## Aktivieren der Unterstützung für den Upload-Auftragsparameter für MIME-Typen &quot;Assets/Dynamic Media Classic&quot;{#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

Sie können konfigurierbare Parameter für Upload-Aufträge für Dynamic Media Classic aktivieren, die durch die Synchronisierung von Digital Asset Manager/Dynamic Media Classic-Assets ausgelöst werden.

Insbesondere konfigurieren Sie hier das vom MIME-Typ akzeptierte Dateiformat im Bereich „OSGi“ (Open Service Gateway initiator) des Bedienfelds der Web-Konsolen-Konfiguration. Anschließend können Sie die einzelnen Parameter für Upload-Aufträge anpassen, die für jeden MIME-Typ in JCR (Java Content Repository) verwendet werden.

**MIME-Typen-basierte Assets können Sie wie folgt konfigurieren:**

1. Tippen Sie auf das Symbol AEM und navigieren Sie zu **[!UICONTROL Tools > Vorgänge > Web-Konsole.]**
1. Klicken Sie im Bedienfeld &quot;Adobe Experience Manager Web Console Configuration&quot;im Menü **[!UICONTROL OSGi]** auf **[!UICONTROL Configuration.]**
1. Suchen Sie in der Spalte &quot;Name&quot;nach **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME-Typ Service]** und tippen Sie darauf, um die Konfiguration zu bearbeiten.
1. Tippen Sie im Bereich &quot;MIME-Typzuordnung&quot;auf ein beliebiges Pluszeichen (+), um einen MIME-Typ hinzuzufügen.

   Siehe [Unterstützte MIME-Typen](/help/assets/assets-formats.md#supported-mime-types).

1. Geben Sie in das Textfeld den neuen MIME-Typnamen ein.

   Geben Sie beispielsweise ein `<file_extension>=<mime_type>` wie in `EPS=application/postscript` ODER `PSD=image/vnd.adobe.photoshop` ein.

1. Tippen Sie in der rechten unteren Ecke des Konfigurationsfensters auf **[!UICONTROL Speichern.]**
1. Kehren Sie über die linke Leiste zu AEM zurück und tippen Sie auf „CRXDE Lite“.
1. Navigieren Sie auf der Seite &quot;CRXDE Lite&quot;in der linken Leiste zu `/etc/cloudservices/scene7/<environment>` (ersetzen Sie `<environment>` durch den tatsächlichen Namen).
1. Erweitern Sie `<environment>` (ersetzen Sie `<environment>` für den tatsächlichen Namen), um den Knoten `mimeTypes` anzuzeigen.
1. Tippen Sie auf den soeben hinzugefügten mimeType.

   Beispiel: `mimeTypes > application_postscript` ODER `mimeTypes > image_vnd.adobe.photoshop`.

1. Tippen Sie auf der rechten Seite der CRXDE Lite auf die Registerkarte **[!UICONTROL Properties]**.
1. Geben Sie im Wertefeld **[!UICONTROL jobParam]** einen Parameter für den Upload-Auftrag für Dynamic Media Classic an.

   Beispiel: `psprocess="rasterize"&psresolution=120`. 

   Weitere Upload-Auftragsparameter finden Sie unter [Adobe Dynamic Media Classic Image Production System API](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/image-production-api/c-overview.html).

   >[!NOTE]
   >
   >Wenn Sie PSD-Extraktionen hochladen und als Vorlagen mit Ebenendateien verarbeiten möchten, geben Sie im Wertefeld **[!UICONTROL jobParam]** Folgendes ein:
   >
   >`process=MaintainLayers&createTemplate=true`
   >
   >Vergewissern Sie sich, dass die PSD-Datei über &quot;Ebenen&quot;verfügt. Wenn es sich um ausschließlich ein Bild oder um ein Bild mit Maske handelt, wird es als Bild verarbeitet, da keine Ebenen verarbeitet werden können.

1. Tippen Sie oben links auf der Seite &quot;CRXDE Lite&quot;auf **[!UICONTROL Alle speichern.]**

## Fehlerbehebung bei der Integration von Dynamic Media Classic und AEM {#troubleshooting-scene-and-aem-integration}

Wenn Sie Probleme bei der Integration von AEM mit Dynamic Media Classic haben, finden Sie in den folgenden Szenarien Lösungen.

**Wenn die Veröffentlichung digitaler Assets in Dynamic Media Classic fehlschlägt:**

* Überprüfen Sie, ob sich das hochzuladende Asset im Ordner **[!UICONTROL CQ-Zielgruppe]** befindet (Sie geben diesen Ordner in der Cloud-Konfiguration von Dynamic Media Classic an).
* Falls nicht, müssen Sie die Cloud-Konfiguration in den **[!UICONTROL Seiteneigenschaften]** zu dieser Seite konfigurieren, um das Hochladen in den Ordner **[!UICONTROL CQ adhoc]** zu ermöglichen.

* Überprüfen Sie die Protokolle auf etwaige Informationen.

**Wenn Ihre Videovorgaben nicht angezeigt werden:**

* Stellen Sie sicher, dass Sie die Cloud-Konfiguration dieser Seite durch die **[!UICONTROL Seiteneigenschaften konfiguriert haben.]** Video-Vorgaben stehen in der Videokomponente &quot;Dynamic Media Classic&quot;zur Verfügung.

**Wenn Ihre Video-Assets nicht in AEM wiedergegeben werden:**

* Stellen Sie sicher, dass Sie die richtige Videokomponente verwendet haben. Die Videokomponente &quot;Dynamic Media Classic&quot;unterscheidet sich von der zugrunde liegenden Videokomponente. Siehe [Foundation Video Component versus Dynamic Media Classic Video Component](/help/assets/s7-video.md).

**Wenn neue oder geänderte Assets in AEM nicht automatisch in Dynamic Media Classic hochgeladen werden:**

* Stellen Sie sicher, dass sich die Assets im CQ-Zielordner befinden. Nur Assets, die sich im CQ-Zielordner befinden, werden automatisch aktualisiert (vorausgesetzt, Sie haben AEM Assets für das automatische Hochladen von Assets konfiguriert).
* Vergewissern Sie sich, dass Sie die Konfiguration der Cloud Services für &quot;Automatisches Hochladen aktivieren&quot;konfiguriert haben und dass Sie den DAM-Asset-Workflow aktualisiert und gespeichert haben, um das Hochladen von Dynamischen Medien in Classic einzuschließen.
* Führen Sie beim Hochladen eines Bildes in einen Unterordner des Ordners &quot;Dynamic Media Classic Zielgruppe&quot;einen der folgenden Schritte aus:

   * Stellen Sie sicher, dass die Namen aller Assets unabhängig von ihrem Speicherort eindeutig sind. Andernfalls wird das Asset im Hauptzielordner gelöscht und es verbleibt nur das Asset im Unterordner.
   * Ändern Sie, wie Dynamic Media Classic Assets im Bereich &quot;Einstellungen&quot;des Kontos &quot;Dynamic Media Classic&quot;überschreibt. Legen Sie für Dynamic Media Classic nicht fest, dass Assets unabhängig vom Speicherort überschrieben werden, wenn Sie Assets mit demselben Namen in Unterordnern verwenden.

**Wenn Ihre gelöschten Assets oder Ordner nicht zwischen Dynamic Media Classic und AEM synchronisiert werden:**

* In AEM Assets gelöschte Assets und Ordner werden weiterhin im synchronisierten Ordner in Dynamic Media Classic angezeigt. Sie müssen Sie manuell löschen.

**Wenn der Video-Upload fehlschlägt**

* Wenn Ihr Video-Upload fehlschlägt und Sie Video über die Integration von Dynamic Media Classic mit AEM kodieren, finden Sie weitere Informationen unter [Hinzufügen eines konfigurierbaren Timeouts zum Workflow für das Hochladen dynamischer Medien in Classic](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Das Importieren von Assets aus einem vorhandenen Konto der Firma &quot;Dynamische Medien - Classic&quot;kann lange dauern, bis sie in AEM angezeigt werden. Stellen Sie sicher, dass Sie einen Ordner in Dynamic Media Classic festlegen, der nicht über zu viele Assets verfügt (der Stammordner enthält beispielsweise häufig zu viele Assets).
>
>Wenn Sie einen Testlauf der Integration durchführen möchten, sollte der Stammordner möglichst nur auf einen Unterordner verweisen statt auf das ganze Unternehmen.

