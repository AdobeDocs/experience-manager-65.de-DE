---
title: Konfigurieren des Dynamic Media-Hybridmodus
description: Erfahren Sie mehr über die Konfiguration des Dynamic Media-Hybridmodus.
mini-toc-levels: 3
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
legacypath: /content/docs/en/aem/6-0/administer/integration/dynamic-media/config-dynamic
role: User, Admin
exl-id: 5719d32c-4f19-47c1-bea9-8fd0bc8439ed
feature: Configuration,Hybrid Mode
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '7738'
ht-degree: 100%

---

# Konfigurieren des Dynamic Media-Hybridmodus {#configuring-dynamic-media-hybrid-mode}

>[!IMPORTANT]
>
>Ende der Unterstützung für Secure Socket Layer 2.0 und 3.0 und Transport Layer Security 1.0 und 1.1
>Ab dem 30. April 2024 wird Adobe Dynamic Media die Unterstützung für Folgendes einstellen:
>
>* SSL (Secure Socket Layer) 2.0
>* SSL 3.0
>* TLS (Transport Layer Security) 1.0 und 1.1
>* Die folgenden schwachen Verschlüsselungsverfahren in TLS 1.2:
> `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
> `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
> `TLS_RSA_WITH_AES_256_GCM_SHA384`
> `TLS_RSA_WITH_AES_256_CBC_SHA256`
> `TLS_RSA_WITH_AES_256_CBC_SHA`
> `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
> `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
> `TLS_RSA_WITH_AES_128_GCM_SHA256`
> `TLS_RSA_WITH_AES_128_CBC_SHA256`
> `TLS_RSA_WITH_AES_128_CBC_SHA`
> `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
> `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
> `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
> `TLS_RSA_WITH_SDES_EDE_CBC_SHA`
>
> Siehe auch [Einschränkungen bei Dynamic Media](/help/assets/limitations.md).

<!-- FOR ABOVE - CQDOC-19433 (original ticket)
and CQDOC-19792 (removed as per this ticket December 5, 2022) -->


Der Dynamic Media-Hybridmodus muss für die Verwendung aktiviert und konfiguriert werden. Je nach Anwendungsfall verfügt Dynamic Media über mehrere [unterstützte Konfigurationen](#supported-dynamic-media-configurations).

>[!NOTE]
>
>Wenn Sie Dynamic Media im Scene7-Modus konfigurieren und ausführen möchten, finden Sie weitere Informationen unter [Konfigurieren des Dynamic Media-Scene7-Modus](/help/assets/config-dms7.md).
>
>Wenn Sie Dynamic Media im Hybridmodus konfigurieren und ausführen möchten, folgen Sie den Anweisungen auf dieser Seite.

Informieren Sie sich über die Verwendung von [Videos](/help/assets/video.md) in Dynamic Media.

>[!NOTE]
>
>Wenn Sie Adobe Experience Manager für verschiedene Umgebungen wie Entwicklung, Staging und Produktion verwenden, konfigurieren Sie Dynamic Media Cloud Services für jede dieser Umgebungen.

>[!NOTE]
>
>Wenn Sie Probleme mit Ihrer Dynamic Media-Konfiguration haben, sehen Sie sich die für Dynamic Media spezifischen Protokolldateien an. Diese Dateien werden automatisch installiert, wenn Sie Dynamic Media aktivieren:
>
>* `s7access.log`
>* `ImageServing.log`
>
>Sie sind in [Überwachen und Verwalten der Experience Manager-Instanz](/help/sites-deploying/monitoring-and-maintaining.md) dokumentiert.

Die hybride Veröffentlichung und Bereitstellung ist eine Kernfunktion der Erweiterung Dynamic Media für Adobe Experience Manager. Per hybrider Veröffentlichung können Sie Dynamic Media-Assets, z. B. Bilder, Sätze und Videos, über die Cloud bereitstellen, anstatt über die Experience Manager-Veröffentlichungsknoten.

Andere Inhalte, z. B. Dynamic Media-Viewer, Seiten von Websites und statische Inhalte, werden weiterhin über die Experience Manager-Veröffentlichungsknoten bereitgestellt.

Wenn Sie Kunde von Dynamic Media sind, ist es erforderlich, dass Sie die hybride Bereitstellung als Bereitstellungsmechanismus für die gesamten Dynamic Media-Inhalte verwenden.

## Hybride Veröffentlichungsarchitektur für Videos {#hybrid-publishing-architecture-for-videos}

![chlimage_1-506](assets/chlimage_1-428.png)

## Hybride Veröffentlichungsarchitektur für Bilder {#hybrid-publishing-architecture-for-images}

![chlimage_1-507](assets/chlimage_1-507.png)

## Unterstützte Dynamic Media-Konfigurationen {#supported-dynamic-media-configurations}

In den folgenden Konfigurationsaufgaben werden die hier angegebenen Begriffe verwendet:

| **Begriff** | **Dynamic Media aktiviert** | **Beschreibung** |
|---|---|---|
| Experience Manager-Autorknoten | Weißes Häkchen in einem grünen Kreis | Der Autorknoten, den Sie On-Premise oder über Managed Services bereitstellen. |
| Experience Manager-Veröffentlichungsknoten | Weißes „X“ in einem roten Quadrat. | Der Veröffentlichungsknoten, den Sie On-Premise oder über Managed Services bereitstellen. |
| Image Service-Veröffentlichungsknoten | Weißes Häkchen in einem grünen Kreis. | Der Veröffentlichungsknoten, den Sie in von Adobe verwalteten Datenzentren ausführen. Bezieht sich auf die Bilddienst-URL. |

Sie können Dynamic Media nur für Bilder, nur für Video oder sowohl für Bilder als auch für Video implementieren. Die Schritte zum Konfigurieren von Dynamic Media für Ihr jeweiliges Szenario finden Sie in der folgenden Tabelle.

<table>
 <tbody>
  <tr>
   <td><strong>Szenario</strong></td>
   <td ><strong>Funktionsweise</strong></td>
   <td><strong>Konfigurationsschritte</strong></td>
  </tr>
  <tr>
   <td>NUR Bilder in Produktion bereitstellen</td>
   <td>Bilder werden über Server in den weltweiten Datenzentren von Adobe bereitgestellt und dann per CDN zwischengespeichert, um eine skalierbare Leistung und globale Reichweite zu erzielen.</td>
   <td>
    <ol>
     <li>Markieren Sie auf dem Experience Manager-<strong>Autor</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a>.</li>
     <li>Konfigurieren Sie die Bildbearbeitung unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li>
     <li><a href="#configuring-image-replication">Konfigurieren Sie die Bildreplikation</a>.</li>
     <li><a href="#replicating-catalog-settings">Replizieren Sie die Katalogeinstellungen</a>.</li>
     <li><a href="#replicating-viewer-presets">Replizieren Sie die Viewer-Vorgaben</a>.</li>
     <li><a href="#using-default-asset-filters-for-replication">Verwenden Sie die Asset-Standardfilter für die Replikation</a>.</li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Bild-Server-Einstellungen für Dynamic Media</a>.</li>
     <li><a href="#delivering-assets">Stellen Sie Assets bereit</a>.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>NUR Bilder in der Phase vor der Produktion bereitstellen (Entwicklung, QE, Staging usw.)</td>
   <td>Bilder werden über den Experience Manager-Veröffentlichungsknoten bereitgestellt. Da bei diesem Szenario nur minimaler Traffic anfällt, müssen keine Bilder für das Rechenzentrum von Adobe bereitgestellt werden. Und es ermöglicht eine sichere Vorschau von Inhalten vor dem Start der Produktion.</td>
   <td>
    <ol>
     <li>Markieren Sie auf dem Experience Manager-<strong>Autor</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a>.</li>
     <li>Markieren Sie auf dem Experience Manager-<strong>-Veröffentlichungs</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a>.</li>
     <li><a href="#replicating-viewer-presets">Replizieren Sie die Viewer-Vorgaben</a>.</li>
     <li>Richten Sie <a href="#setting-up-asset-filters-for-imaging-in-non-production-deployments">Asset-Filter für nicht für die Produktion bestimmte Bilder</a> ein.</li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Dynamic Media-Bildserver-Einstellungen.</a></li>
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>NUR Videos in allen Umgebungen bereitstellen (Produktion, Entwicklung, QE, Staging usw.)</td>
   <td>Videos werden vom CDN für skalierbare Leistung und eine globale Reichweite bereitgestellt und zwischengespeichert. Das Video-Posterbild (Miniaturansicht des Videos, das vor der Initiierung der Wiedergabe angezeigt wird) wird von der Experience Manager-Veröffentlichungsinstanz bereitgestellt.</td>
   <td>
    <ol>
     <li>Markieren Sie auf dem Experience Manager-<strong>Autor</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a>.</li>
     <li>Markieren Sie auf dem Exeperience Manager-<strong>Veröffentlichungs</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a> (über die Veröffentlichungsinstanz werden das Video-Posterbild und die Metadaten für die Videowiedergabe bereitgestellt).</li>
     <li>Konfigurieren Sie Videos unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li>
     <li><a href="#replicating-viewer-presets">Replizieren Sie die Viewer-Vorgaben</a>.</li>
     <li>Richten Sie <a href="#setting-up-asset-filters-for-video-only-deployments">Asset-Filter ausschließlich für Videos</a> ein.</li>
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li>
    </ol> </td>
  </tr>
  <tr>
   <td>Bilder UND Videos in Produktion bereitstellen</td>
   <td><p>Videos werden vom CDN für skalierbare Leistung und eine globale Reichweite bereitgestellt und zwischengespeichert. Bilder und Video-Posterbilder werden über Server in den weltweiten Datenzentren von Adobe bereitgestellt und dann per CDN zwischengespeichert, um eine skalierbare Leistung und globale Reichweite zu erzielen.</p> <p>Informationen zur Einrichtung für Bilder oder Videos in der Phase vor der Produktion finden Sie in den obigen Abschnitten. </p> </td>
   <td>
    <ol>
     <li>Markieren Sie auf dem Experience Manager-<strong>Autor</strong>-Knoten die Option <a href="#enabling-dynamic-media">Dynamic Media aktivieren</a>.</li>
     <li>Konfigurieren Sie Videos unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li>
     <li>Konfigurieren Sie die Bildbearbeitung unter <a href="#configuring-dynamic-media-cloud-services">Dynamic Media Cloud Services</a>.</li>
     <li><a href="#configuring-image-replication">Konfigurieren Sie die Bildreplikation</a>.</li>
     <li><a href="#replicating-catalog-settings">Replizieren Sie die Katalogeinstellungen</a>.</li>
     <li><a href="#replicating-viewer-presets">Replizieren Sie die Viewer-Vorgaben</a>.</li>
     <li><a href="#using-default-asset-filters-for-replication">Verwenden Sie Asset-Standardfilter für die Replikation.</a></li>
     <li><a href="#configuring-dynamic-media-image-server-settings">Konfigurieren Sie Dynamic Media-Bildserver-Einstellungen.</a></li>
     <li><a href="#delivering-assets">Stellen Sie Assets bereit.</a></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Aktivieren von Dynamic Media {#enabling-dynamic-media}

[Dynamic Media ist standardmäßig deaktiviert. ](https://business.adobe.com/de/products/experience-manager/assets/dynamic-media.html) Um die Funktionen von Dynamic Media nutzen zu können, müssen Sie Dynamic Media aktivieren, indem Sie den Ausführungsmodus `dynamicmedia` verwenden, wie Sie dies beispielsweise auch mit dem Ausführungsmodus `publish` durchführen. Prüfen Sie vor dem Aktivieren die [technischen Anforderungen](/help/sites-deploying/technical-requirements.md#requirements-for-aem-dynamic-media-add-on).

>[!NOTE]
>
>Durch das Aktivieren von Dynamic Media per Ausführungsmodus wird die Funktionalität in Experience Manager 6.1 und Experience Manager 6.0 für die Teile ersetzt, für die Sie Dynamic Media aktiviert haben, indem das Flag `dynamicMediaEnabled` auf **[!UICONTROL true]** festgelegt wird. Dieses Flag hat in Experience Manager 6.2 und höher keine Funktion. Außerdem ist es nicht erforderlich, den Schnellstartvorgang neu zu starten, um Dynamic Media zu aktivieren.

Durch die Aktivierung von Dynamic Media sind die Funktionen von Dynamic Media auf der Benutzeroberfläche verfügbar und jedes hochgeladene Bild-Asset erhält die Ausgabedarstellung *cqdam.pyramid.tiff*, die für die schnelle Bereitstellung der Ausgabedarstellungen von dynamischen Bildern verwendet wird. Diese PTIFF-Dateien haben erhebliche Vorteile, wie die folgenden:

* Die Möglichkeit, nur ein einzelnes Primärquellenbild zu verwalten und unendliche Ausgabedarstellungen ohne zusätzlichen Speicher sofort zu generieren.
* Die Möglichkeit zur Verwendung interaktiver Visualisierungen wie Zoom, Schwenken und Drehen.

Falls Sie Dynamic Media Classic in Experience Manager verwenden möchten, sollten Sie Dynamic Media nur aktivieren, wenn Sie ein [bestimmtes Szenario](/help/sites-administering/scene7.md#aem-scene-integration-versus-dynamic-media) nutzen. Dynamic Media ist deaktiviert, sofern Sie es nicht per Ausführungsmodus aktivieren.

Zum Aktivieren von Dynamic Media müssen Sie den Ausführungsmodus für Dynamic Media entweder über die Befehlszeile oder den Schnellstart-Dateinamen aktivieren.

**So aktivieren Sie Dynamic Media:**

1. In der Befehlszeile haben Sie nach dem Starten des Schnellstartvorgangs die folgenden Möglichkeiten:

   * Fügen Sie beim Starten der JAR-Datei am Ende der Befehlszeile `-r dynamicmedia` hinzu.

   ```shellsession {.line-numbers}
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.5.0.jar -r dynamicmedia
   ```

   Wenn Sie in s7delivery veröffentlichen, müssen Sie auch die folgenden trustStore-Argumente einbeziehen:

   ```shellsession {.line-numbers}
   -Djavax.net.ssl.trustStore=<absoluteFilePath>/customerTrustStoreFileName>
   
    -Djavax.net.ssl.trustStorePassword=<passwordForTrustStoreFile>
   ```

1. Fordern Sie `https://localhost:4502/is/image` an und stellen Sie sicher, dass der Bildserver ausgeführt wird.

   >[!NOTE]
   >
   >Informationen zur Behebung von Problemen mit Dynamic Media finden Sie in den folgenden Protokollen im Verzeichnis `crx-quickstart/logs/`:
   >
   >* ImageServer-&lt;PortId>-&lt;yyyy>&lt;mm>&lt;dd>.log – Das ImageServer-Protokoll enthält Statistiken und Analyseinformationen, die zum Analysieren des Verhaltens des internen ImageServer-Prozesses verwendet werden.
   >
   Beispiel für einen Image-Server-Protokolldateinamen: `ImageServer-57346-2020-07-25.log`
   >
   * s7access-&lt;yyyy>&lt;mm>&lt;dd>.log - Im s7access-Protokoll werden alle Anfragen aufgezeichnet, die über `/is/image` und `/is/content` an Dynamic Media gesendet werden.
   >
   Diese Protokolle werden nur verwendet, wenn Dynamic Media aktiviert ist. Sie sind nicht im Paket **Alles herunterladen** enthalten, das über die Seite `system/console/status-Bundlelist` generiert wird. Fügen Sie diese beiden Protokolle bei der Kontaktaufnahme mit dem Support an die Problembeschreibung an, wenn bei Ihnen ein Problem mit Dynamic Media besteht.

### Bei Installation von Experience Manager über einen anderen Port oder Kontextpfad ... {#if-you-installed-aem-to-a-different-port-or-context-path}

Wenn Sie [Experience Manager auf einem Anwendungsserver](/help/sites-deploying/application-server-install.md) bereitstellen und Dynamic Media aktiviert haben, müssen Sie die **Self-Domain** im Externalizer konfigurieren. Andernfalls funktioniert die Generierung von Miniaturansichten für Dynamic Media-Assets nicht richtig.

Falls Sie den Schnellstart für einen anderen Port oder Kontextpfad ausführen, müssen Sie die **Self-Domain** ebenfalls ändern.

Wenn Dynamic Media aktiviert ist, werden die statischen Miniaturansicht-Ausgabedarstellungen für Bild-Assets mit Dynamic Media generiert. Damit die Generierung von Miniaturansichten für Dynamic Media richtig funktioniert, muss Experience Manager eine URL-Anfrage an sich selbst senden und sowohl die Portnummer als auch den Kontextpfad kennen.

In Experience Manager:

* Die **Self-Domain** im [Externalizer](/help/sites-developing/externalizer.md) wird verwendet, um sowohl die Portnummer als auch den Kontextpfad abzurufen.
* Wenn die **Self-Domain** konfiguriert ist, werden die Port-Nummer und der Kontextpfad über den Jetty-HTTP-Service abgerufen.

In einer Experience Manager QuickStart WAR-Bereitstellung können die Portnummer und der Kontextpfad nicht abgeleitet werden, daher müssen Sie eine **Self-Domain** konfigurieren. Weitere Informationen zur Konfiguration der [Self-domain](/help/sites-developing/externalizer.md) finden Sie in der **Dokumentation zum Externalizer**.

>[!NOTE]
>
Bei einer [eigenständigen Bereitstellung von Experience Manager Quickstart](/help/sites-deploying/deploy.md) muss in der Regel keine **Self-Domain** konfiguriert werden, da die Portnummer und der Kontextpfad automatisch konfiguriert werden können. Wenn jedoch alle Netzwerkschnittstellen deaktiviert sind, müssen Sie die **Self-Domain** konfigurieren.

## Deaktivieren von Dynamic Media  {#disabling-dynamic-media}

Dynamic Media ist standardmäßig deaktiviert. Wenn Sie Dynamic Media jedoch bereits aktiviert haben, können Sie es später deaktivieren.

Um Dynamic Media nach dem Aktivieren wieder zu deaktivieren, müssen Sie das Ausführungsmodus-Flag `-r dynamicmedia` entfernen.

**So deaktivieren Sie Dynamic Media:**

1. In der Befehlszeile haben Sie nach dem Starten des Schnellstartvorgangs die beiden folgenden Möglichkeiten:

   * Fügen Sie beim Starten der JAR-Datei der Befehlszeile nicht `-r dynamicmedia` hinzu.

   ```shellsession {.line-numbers}
   java -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.5.0.jar
   ```

1. Fragen Sie `https://localhost:4502/is/image` an. Sie erhalten eine Nachricht, dass Dynamic Media deaktiviert wurde.

   >[!NOTE]
   >
   Wenn der Dynamic Media-Ausführungsmodus deaktiviert wurde, wird der Workflow-Schritt zum Generieren der Ausgabedarstellungsformats `cqdam.pyramid.tiff` automatisch übersprungen. Hierbei werden auch die Unterstützung der dynamischen Ausgabedarstellungen und andere Dynamic Media-Funktionen deaktiviert.
   >
   Achtung: Wenn Sie den Dynamic Media-Ausführungsmodus nach der Konfiguration des Experience Manager-Servers deaktivieren, sind alle mit diesem Ausführungsmodus hochgeladenen Assets ungültig.

## (Optional) Migration von Dynamic Media-Vorgaben und -Konfigurationen von 6.3 zu 6.5 ohne Ausfallzeit {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Wenn Sie ein Upgrade von Experience Manager – Dynamic Media von 6.3 auf 6.5 durchführen (was jetzt die Möglichkeit bietet, Bereitstellungen ohne Ausfallzeiten zu erreichen), müssen Sie den folgenden curl-Befehl ausführen. Der Befehl migriert alle Vorgaben und Konfigurationen aus `/etc` nach `/conf` in CRXDE Lite.

>[!NOTE]
>
Wenn Sie Ihre Experience Manager-Instanz im Kompatibilitätsmodus ausführen, d. h. wenn das Kompatibilitätspaket installiert ist, müssen Sie diese Befehle nicht ausführen.

Bei allen Upgrades – mit oder ohne Kompatibilitätspaket – können Sie die standardmäßig in Dynamic Media vorhandenen Viewer-Vorgaben kopieren, indem Sie unter Linux® den folgenden curl-Befehl ausführen:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

Führen Sie zum Migrieren der von Ihren erstellten benutzerdefinierten Vorgaben und Konfigurationen von `/etc` nach `/conf` unter Linux den folgenden curl-Befehl aus:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

## Konfigurieren Sie die Bildreplikation {#configuring-image-replication}

Im Rahmen der Bereitstellung von Dynamic Media-Bildern werden Bild-Assets, z. B. Video-Miniaturansichten, über die Experience Manager-Autoreninstanz veröffentlicht und über den On-Demand-Replikationsdienst von Adobe (Replikationsservice-URL) repliziert. Die Assets werden dann über den Service für die On-Demand-Bildbereitstellung (Bildservice-URL) bereitgestellt.

Gehen Sie folgendermaßen vor:

1. [Einrichten der Authentifizierung](#setting-up-authentication)
1. [Konfigurieren des Replikationsagenten](#configuring-the-replication-agent)

Der Replikationsagent veröffentlicht Dynamic Media-Assets, z. B. Bilder, Videometadaten und Sätze, für den von Adobe gehosteten Bilddienst. Der Replikationsagent ist nicht standardmäßig aktiviert.

Nachdem Sie den Replikationsagenten konfiguriert haben, müssen Sie [überprüfen und testen, ob die Einrichtung erfolgreich war](#validating-the-replication-agent-for-dynamic-media). In diesem Abschnitt werden die entsprechenden Vorgehensweisen beschrieben.

>[!NOTE]
>
Die standardmäßige Speicherbegrenzung für die PTIFF-Erstellung beträgt für alle Workflows 3 GB. Beispielsweise können Sie ein Bild verarbeiten, für das 3 GB Speicher erforderlich sind, während andere Workflows angehalten werden. Sie können auch zehn Bilder parallel verarbeiten, die jeweils 300 MB Speicher erfordern.
>
Die Speicherbegrenzung ist konfigurierbar und sollte zur Verfügbarkeit der Systemressourcen und zur Art und Weise der Verarbeitung von Bildinhalten passen. Falls Sie über viele sehr große Assets verfügen und im System ausreichend Speicher vorhanden ist, können Sie diese Begrenzung erhöhen, um sicherzustellen, dass die Bilder parallel verarbeitet werden.
>
Ein Bild, das mehr als die maximale Speicherkapazität benötigt, wird abgelehnt.
>
Navigieren Sie zum Ändern der Speicherbegrenzung für die PTIFF-Erstellung zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]** > **[!UICONTROL Adobe CQ Scene7 PTiffManager]** und ändern Sie den Wert **[!UICONTROL maxMemory]**.

### Einrichten der Authentifizierung {#setting-up-authentication}

Richten Sie die Replikationsauthentifizierung auf der Autoreninstanz ein, damit Sie Bilder für den Dynamic Media-Bildbereitstellungsdienst replizieren können. Sie erhalten zunächst einen KeyStore und speichern ihn dann unter dem Benutzer **[!UICONTROL dynamic-media-replication]** und konfigurieren ihn. Der Admin in Ihrem Unternehmen sollte während des Bereitstellungsprozesses eine Begrüßungs-E-Mail mit der KeyStore-Datei und den erforderlichen Anmelddaten erhalten haben. Wenn Sie nicht über diese Informationen verfügen, wenden Sie sich an den Kunden-Support von Adobe.

**Gehen Sie wie folgt vor, um die Authentifizierung einzurichten:**

1. Wenden Sie sich an den Kunden-Support von Adobe, um Ihre KeyStore-Datei und Ihr Kennwort anzufordern, falls Sie diese noch nicht haben. Diese Informationen sind ein notwendiger Teil der Bereitstellung. Die Schlüssel werden Ihrem Konto zugeordnet.

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.

1. Gehen Sie auf der Seite „Benutzerverwaltung“ zum Benutzer **[!UICONTROL dynamic-media-replication]** und klicken Sie dann darauf, um ihn zu öffnen.

   ![dm-replication](assets/dm-replication.png)

1. Klicken Sie auf der Seite „Benutzereinstellungen für dynamic-media-replication bearbeiten“ auf die Registerkarte **[!UICONTROL KeyStore]** und dann auf **[!UICONTROL KeyStore erstellen]**.

   ![dm-replication-keystore](assets/dm-replication-keystore.png)

1. Geben Sie im Dialogfeld **[!UICONTROL Zugangskennwort für KeyStore festlegen]** ein Kennwort ein und bestätigen Sie es.

   >[!NOTE]
   >
   Denken Sie an das Kennwort, da Sie es später, wenn Sie den Replikationsagenten konfigurieren, erneut eingeben müssen.

   ![chlimage_1-508](assets/chlimage_1-508.png)

1. Erweitern Sie auf der Seite **[!UICONTROL Benutzereinstellungen für dynamic-media-replication bearbeiten]** den Bereich **Privaten Schlüssel aus KeyStore-Datei hinzufügen** und fügen Sie Folgendes ein (siehe folgende Abbildungen):

   * Geben Sie im Feld **[!UICONTROL Neuer Alias]** den Namen eines Alias ein, den Sie später in der Replikationskonfiguration verwenden. Sie könnten beispielsweise `replication` als Alias verwenden.
   * Wählen Sie die **[!UICONTROL KeyStore-Datei]** aus. Gehen Sie zu der KeyStore-Datei, die Sie von Adobe erhalten haben, wählen Sie sie aus und klicken Sie dann auf **[!UICONTROL Öffnen]**.
   * Geben Sie im Feld **[!UICONTROL Kennwort für KeyStore-Datei]** das Kennwort für die KeyStore-Datei ein. Dies ist **nicht** das KeyStore-Kennwort, das Sie in Schritt 5 erstellt haben, sondern das Kennwort für die KeyStore-Datei, das Sie in der Begrüßungs-E-Mail von Adobe während der Bereitstellung erhalten haben. Wenden Sie sich an dien Kunden-Support von Adobe, um Ihr Kennwort zu erhalten (falls noch nicht vorhanden).
   * Geben Sie im Feld **[!UICONTROL Kennwort für privaten Schlüssel]** das Kennwort für den privaten Schlüssel ein (dies kann dasselbe Kennwort für den privaten Schlüssel wie im vorherigen Schritt sein). Das Kennwort für den privaten Schlüssel ist in der Begrüßungs-E-Mail von Adobe enthalten, die während der Bereitstellung an Sie gesendet wird. Nehmen Sie Kontakt mit dem Kunden-Support von Adobe auf, falls Sie kein Kennwort für den privaten Schlüssel erhalten haben.
   * Geben Sie in das Feld **[!UICONTROL Alias für privaten Schlüssel]** den Alias für den privaten Schlüssel ein. Beispiel: `*companyname*-alias`. Der Alias für den privaten Schlüssel ist in der Begrüßungs-E-Mail von Adobe enthalten, die während der Bereitstellung an Sie gesendet wird. Nehmen Sie Kontakt mit dem Kunden-Support von Adobe auf, falls Sie keinen Alias für den privaten Schlüssel erhalten haben.

   ![edit_settings_fordynamic-media-replication2](assets/edit_settings_fordynamic-media-replication2.png)

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**, um Ihre Änderungen für diesen Benutzer zu speichern.

   Als Nächstes müssen Sie den [Replikationsagenten konfigurieren](#configuring-the-replication-agent).

### Konfigurieren des Replikationsagenten {#configuring-the-replication-agent}

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** > **[!UICONTROL Agenten für Autor]**.
1. Klicken Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Hybride Bildreplikation für Dynamic Media (s7delivery)]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Wählen Sie die Registerkarte **[!UICONTROL Einstellungen]** aus und geben Sie Folgendes ein:

   * **[!UICONTROL Aktiviert]**: Markieren Sie dieses Kontrollkästchen, um den Replikationsagenten zu aktivieren.
   * **[!UICONTROL Region]**: Legen Sie die passende Region fest: Nordamerika, Europa oder Asien.
   * **[!UICONTROL Mandanten-ID]**: Dieser Wert ist der Name Ihres Unternehmens bzw. Mandanten, von dem der Replikationsdienst veröffentlicht wird. Dieser Wert ist die Mandanten-ID aus der Begrüßungs-E-Mail von Adobe, die Sie während der Bereitstellung erhalten haben. Wenn Sie nicht über diese Informationen verfügen, wenden Sie sich an den Kunden-Support von Adobe.
   * **[!UICONTROL KeyStore-Alias]**: Dieser Wert entspricht dem Wert unter **Neuer Alias**, der beim Generieren des Schlüssels unter [Einrichten der Authentifizierung](#setting-up-authentication) festgelegt wurde (z. B. `replication`). (Siehe Schritt 7 unter [Einrichten der Authentifizierung](#setting-up-authentication).)
   * **[!UICONTROL KeyStore-Kennwort]**: Dies ist das KeyStore-Kennwort, das erstellt wurde, als Sie auf **[!UICONTROL KeyStore erstellen]** geklickt bzw. getippt haben. Dieses Kennwort wird nicht von Adobe bereitgestellt. Siehe Schritt 5 von [Einrichten der Authentifizierung](#setting-up-authentication).

   In der folgenden Abbildung ist der Replikationsagent mit Beispieldaten dargestellt:

   ![chlimage_1-509](assets/chlimage_1-509.png)

1. Klicken Sie auf **[!UICONTROL OK]**.

### Validieren des Replikationsagenten für Dynamic Media {#validating-the-replication-agent-for-dynamic-media}

Gehen Sie wie folgt vor, um den Replikationsagenten für Dynamic Media zu validieren:

Klicken Sie auf **[!UICONTROL Verbindung testen]**. Die Beispielausgabe lautet wie folgt:

```shell
11.03.2016 10:57:55 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
11.03.2016 10:57:55 - * Auth User: replication-receiver
11.03.2016 10:57:55 - * HTTP Version: 1.1
11.03.2016 10:57:55 - * Using OAuth 2.0 Authorization Grants
11.03.2016 10:57:55 - * OAuth 2.0 User: dynamic-media-replication
11.03.2016 10:57:55 - * OAuth 2.0 Token: '*****' initialized
11.03.2016 10:57:55 - Publishing: POST[https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=xfpuu-6613]
11.03.2016 10:57:55 - Publish response: OK[]
11.03.2016 10:57:55 - Transfer succeeded in 141 ms for ReplicationAction{type=TEST, path[0]='/content/dam', time=1457722675402, userId='admin', revision='null'}
-------------------------------------------------------------------------------------------------------------------------------
Replication test succeeded
```

>[!NOTE]
>
Sie können die Überprüfung auch durchführen, indem Sie einen der folgenden Schritte ausführen:
>
* Überprüfen Sie die Replikationsprotokolle, um sicherzustellen, dass das Asset repliziert wurde.
* Veröffentlichen Sie ein Bild. Wählen Sie das Bild aus und klicken Sie im Dropdown-Menü auf **[!UICONTROL Viewer]**. Wählen Sie dann eine Viewer-Vorgabe aus. Klicken Sie auf **[!UICONTROL URL]**. Um sicherzustellen, dass das Bild angezeigt wird, kopieren Sie den URL-Pfad und fügen Sie ihn in den Browser ein.
>

### Fehlerbehebung bei der Authentifizierung {#troubleshooting-authentication}

Hier sind einige Probleme, die beim Einrichten der Authentifizierung auftreten können. Es werden dazugehörige Lösungen angegeben. Achten Sie darauf, dass die Replikation eingerichtet wurde, bevor Sie diese Angaben prüfen.

#### Problem: HTTP-Status-Code 401 mit der Meldung „Authorization Required“ (Autorisierung erforderlich) {#problem-http-status-code-with-message-authorization-required}

Dieses Problem kann auftreten, wenn der KeyStore für den Benutzer `dynamic-media-replication` nicht eingerichtet wurde.

```shell
Replication test to s7delivery:https://s7bern.macromedia.com:8580/is-publish/
17.06.2016 18:54:43 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}
17.06.2016 18:54:43 - * Auth User: replication-receiver
17.06.2016 18:54:43 - * HTTP Version: 1.1
17.06.2016 18:54:43 - * Using OAuth 2.0 Authorization Grants
17.06.2016 18:54:43 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 18:54:43 - No OAuth token available. OAuth not initialized
17.06.2016 18:54:43 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 18:54:43 - Publishing: POST[https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough]
17.06.2016 18:54:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309, userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
17.06.2016 18:54:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466214883309,
 userId='admin', revision='null'}. java.io.IOException: Failed to execute request
'https://<localhost>:8580/is-publish//publish-receiver?Cmd=Test&RootId=brough':
 Server returned status code 401 with message: Authorization required.
```

**Lösung:**
Vergewissern Sie sich, dass der `KeyStore` für den Benutzer **dynamic-media-replication** gespeichert wurde und ihm das richtige Kennwort mitgeteilt wurde.

#### Problem: Schlüssel kann nicht entschlüsselt werden – Daten können nicht entschlüsselt werden {#problem-could-not-decrypt-key-could-not-decrypt-data}

```xml
Replication test to s7delivery:https://<localhost>:8580/is-publish/
17.06.2016 19:00:16 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}
17.06.2016 19:00:16 - * Auth User: replication-receiver
17.06.2016 19:00:16 - * HTTP Version: 1.1
17.06.2016 19:00:16 - * Using OAuth 2.0 Authorization Grants
17.06.2016 19:00:16 - * OAuth 2.0 User: dynamic-media-replication
17.06.2016 19:00:16 - No OAuth token available. OAuth not initialized
17.06.2016 19:00:16 - * Using Client Auth SSL alias - replication-alias *
17.06.2016 19:00:16 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1466215216662, userId='admin', revision='null'}. java.lang.SecurityException: java.security.UnrecoverableKeyException: Could not decrypt key: Could not decrypt data.
```

**Lösung:**
Überprüfen Sie das Kennwort. Das im Replikationsagenten gespeicherte Kennwort entspricht nicht dem Kennwort, das zur Keystore-Erstellung verwendet wurde.

#### Problem: InvalidAlgorithmParameterException {#problem-invalidalgorithmparameterexception}

Dieses Problem wird durch einen Konfigurationsfehler in Ihrer Experience Manager-Autoreninstanz verursacht. Für den Java™-Prozess des Autors wird nicht das richtige `javax.net.ssl.trustStore`-Element verwendet. Dieser Fehler ist im Replikationsprotokoll zu sehen:

```shell
14.04.2016 09:37:43 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
14.04.2016 09:37:43 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1460651862089, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://<localhost>:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx2': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
```

Oder im Fehlerprotokoll:

```shell
07.25.2019 12:00:59.893 *ERROR* [sling-threadpool-db2763bb-bc50-4bb5-bb64-10a09f432712-(apache-sling-job-thread-pool)-90-com_day_cq_replication_job_s7delivery(com/day/cq/replication/job/s7delivery)] com.day.cq.replication.Agent.s7delivery.queue Error during processing of replication.

java.io.IOException: Failed to execute request 'https://replicate-na.assetsadobe.com:8580/is-publish/publish-receiver?Cmd=Test&RootId=rbrough-osx': java.lang.RuntimeException: Unexpected error: java.security.InvalidAlgorithmParameterException: the trustAnchors parameter must be non-empty
        at com.scene7.is.catalog.service.publish.atomic.PublishingServiceHttp.executePost(PublishingServiceHttp.scala:195)
```

**Lösung:**
Vergewissern Sie sich, dass die Systemeigenschaft `-Djavax.net.ssl.trustStore=` für den Java™-Prozess in der Experience Manager-Autoreninstanz auf einen gültigen TrustStore festgelegt ist.

#### Problem: KeyStore ist entweder nicht eingerichtet oder nicht initialisiert {#problem-keystore-is-either-not-set-up-or-it-is-not-initialized}

Dieses Problem kann durch einen Hotfix oder dadurch verursacht werden, dass der dynamic-media-user oder KeyStore-Knoten durch ein Feature Pack überschrieben wurde.

Beispiel für Replikationsprotokoll:

```shell
Replication test to s7delivery:https://replicate-na.assetsadobe.com/is-publish
02.08.2016 14:37:44 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}
02.08.2016 14:37:44 - * Auth User: replication-receiver
02.08.2016 14:37:44 - * HTTP Version: 1.1
02.08.2016 14:37:44 - * Using OAuth 2.0 Authorization Grants
02.08.2016 14:37:44 - * OAuth 2.0 User: dynamic-media-replication
02.08.2016 14:37:44 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470173864834, userId='admin', revision='null'}. com.adobe.granite.keystore.KeyStoreNotInitialisedException: Uninitialised key store for user dynamic-media-replication
```

**Lösung:**

1. Gehen Sie zur User Management-Seite:
   `localhost:4502/libs/granite/security/content/useradmin.html`
1. Gehen Sie auf der Seite „User Management“ zum Benutzer `dynamic-media-replication` und klicken Sie auf ihn, um ihn zu öffnen.
1. Wählen Sie die Registerkarte **[!UICONTROL KeyStore]** aus. Wenn die Schaltfläche **[!UICONTROL KeyStore erstellen]** angezeigt wird, müssen Sie die Schritte zum [Einrichten der Authentifizierung](#setting-up-authentication) wiederholen.
1. Wenn Sie die KeyStore-Einrichtung wiederholen mussten, müssen Sie möglicherweise auch das [Konfigurieren des Replikationsagenten](/help/assets/config-dynamic.md#configuring-the-replication-agent) wiederholen.

   Konfigurieren Sie den s7delivery-Replikationsagenten neu.
   `localhost:4502/etc/replication/agents.author/s7delivery.html`

1. Klicken Sie auf **[!UICONTROL Verbindung testen]**, um zu überprüfen, ob die Konfiguration gültig ist.

#### Problem: Für den Veröffentlichungsagenten wird SSL anstelle von OAuth verwendet {#problem-publish-agent-is-using-ssl-instead-of-oauth}

Dieses Problem kann durch einen Hotfix, ein nicht korrekt installiertes Feature Pack oder Überschreiben der Einstellungen verursacht werden.

Beispiel für Replikationsprotokoll:

```shell
01.08.2016 18:42:59 - Transferring content for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}
01.08.2016 18:42:59 - * Auth User: replication-receiver
01.08.2016 18:42:59 - * HTTP Version: 1.1
01.08.2016 18:42:59 - * Using Client Auth SSL alias - replication-receiver *
01.08.2016 18:42:59 - Publishing: POST[https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=altayerstaging]
01.08.2016 18:42:59 - Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
01.08.2016 18:42:59 - Error while replicating: com.day.cq.replication.ReplicationException: Transfer failed for ReplicationAction{type=TEST, path[0]='/content/dam', time=1470073379634, userId='admin', revision='null'}. java.io.IOException: Failed to execute request 'https://replicate-eu.assetsadobe2.com:443/is-publish/publish-receiver?Cmd=Test&RootId=rbroughstaging': Server returned status code 401 with message: Authorization required.
```

**Lösung:**

1. Gehen Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.

   `localhost:4502/crx/de/index.jsp`

1. Navigieren Sie zum s7delivery-Replikationsagenten-Knoten.
   `localhost:4502/crx/de/index.jsp#/etc/replication/agents.author/s7delivery/jcr:content`

1. Fügen Sie diese Einstellung dem Replikationsagenten hinzu (boolescher Wert mit der Einstellung **[!UICONTROL True]**):

   `enableOauth=true`

1. Klicken Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Alle speichern]**.

### Testen Sie die Konfiguration {#testing-your-configuration}

Adobe empfiehlt, für die Konfiguration einen umfassenden Test durchzuführen.

Achten Sie darauf, dass Sie vor Beginn dieses Tests Folgendes durchgeführt haben:

* Hinzugefügte Bildvorgaben.
* Abschließen der **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]** unter „Cloud-Services“. Die Bilddienst-URL ist für diesen Test nicht erforderlich.

**Gehen Sie wie folgt vor, um die Konfiguration zu testen:**

1. Laden Sie ein Bild-Asset hoch. (Gehen Sie in Assets zu **[!UICONTROL Erstellen]** > **[!UICONTROL Dateien]** und wählen Sie die Datei aus.)
1. Warten Sie, bis der Workflow abgeschlossen ist.
1. Veröffentlichen Sie das Bild-Asset.  (Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Quick Publish]**.)
1. Gehen Sie zu den Ausgabedarstellungen für dieses Bild, indem Sie das Bild öffnen und auf **[!UICONTROL Ausgabedarstellungen]** klicken bzw. tippen.

   ![chlimage_1-510](assets/chlimage_1-510.png)

1. Wählen Sie eine beliebige dynamische Ausgabedarstellung aus.
1. Um die URL für dieses Asset zu erhalten, klicken Sie auf **[!UICONTROL URL]**.
1. Navigieren Sie zur ausgewählten URL und überprüfen Sie, ob sich das Bild wie erwartet verhält.

Eine andere Möglichkeit zum Testen der Bereitstellung Ihrer Assets besteht darin, „req=exists“ an die URL anzufügen.

## Konfigurieren von Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Der Dynamic Media-Cloud Service unterstützt u. a. die hybride Veröffentlichung und Bereitstellung von Bildern und Videos, Videoanalysen und Videokodierung.

Im Rahmen der Konfiguration müssen Sie eine Registrierungs-ID, Videodienst-URL, Bilddienst-URL und Replikationsdienst-URL eingeben und die Authentifizierung einrichten. Diese Informationen wurden Ihnen im Rahmen der Kontobereitstellung per E-Mail zugeschickt. Falls Sie diese Informationen nicht erhalten haben, können Sie sich an Ihren Adobe Experience Manager-Admin oder den Kunden-Support von Adobe wenden.

>[!NOTE]
>
Stellen Sie vor dem Einrichten des Dynamic Media Cloud Service sicher, dass Sie Ihre Veröffentlichungsinstanz eingerichtet haben. Außerdem müssen Sie die Replikation einrichten, bevor Sie Dynamic Media Cloud Service konfigurieren.

**So konfigurieren Sie Dynamic Media Cloud Services:**

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media-Konfiguration (vor 6.3)]**.
1. Wählen Sie auf der Browser-Seite für die Dynamic Media-Konfiguration im Bedienfeld links **[!UICONTROL global]** und klicken Sie dann auf **[!UICONTROL Erstellen]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Dynamic Media-Konfiguration erstellen]** im Feld „Titel“ einen Titel ein.
1. Wenn Sie Dynamic Media für Video konfigurieren,

   * Geben Sie im Feld **[!UICONTROL Registrierungs-ID]** Ihre Registrierungs-ID ein.
   * Geben Sie im Feld **[!UICONTROL Videodienst-URL]** die Videodienst-URL für das Dynamic Media Gateway ein.

1. Geben Sie beim Konfigurieren von Dynamic Media für die Bilddarstellung im Dialogfeld **[!UICONTROL Bilddienst-URL]** die Bilddienst-URL für das Dynamic Media Gateway ein.
1. Klicken Sie auf **[!UICONTROL Speichern]**, um zur Browser-Seite für die Dynamic Media-Konfiguration zurückzukehren.
1. Um auf die globale Navigationskonsole zuzugreifen, klicken Sie auf das Experience Manager-Logo.

## Konfigurieren von Videoberichten {#configuring-video-reporting}

Mit dem Hybridmodus von Dynamic Media können Sie Videoberichte für mehrere Installationen von Experience Manager konfigurieren.

**Verwendung:** Beim Konfigurieren der Dynamic Media-Konfiguration (vor 6.3) werden Funktionen gestartet, darunter auch Videoberichte. Die Konfiguration erstellt eine Report Suite in einem regionalen Analytics-Unternehmen Wenn Sie mehrere Author-Knoten konfigurieren, erstellen Sie für jeden davon eine separate Report Suite. Das führt zu inkonsistenten Berichtsdaten in den einzelnen Installationen. Wenn jeder Author-Knoten auf denselben Hybrid-Veröffentlichungs-Server verweist, ändert die letzte Author-Installation die zielseitige Report Suite für alle Video-Berichte. Dieses Problem führt zur Überlastung des Analysesystems mit zu vielen Report Suites.

**Erste Schritte:** Konfigurieren Sie Video-Berichte, indem Sie die drei folgenden Schritte ausführen.

1. Erstellen Sie nach dem Konfigurieren der Dynamic Media-Konfiguration (vor 6.3) ein Vorgabenpaket für die Video-Analyse auf dem ersten Author-Knoten. Diese Aufgabe ist wichtig, da sie einer neuen Konfiguration die weitere Verwendung derselben Report Suite ermöglicht.
1. Installieren Sie das Vorgabenpaket für die Videoanalyse auf ***neuen*** Autorknoten, ***bevor*** Sie die Dynamic Media-Konfiguration (vor 6.3) konfigurieren.
1. Überprüfen und debuggen Sie die Paketinstallation.

### Erstellen eines Vorgabenpakets für Videoanalysen nach der Konfiguration des ersten Autorknotens {#creating-a-video-analytics-preset-package-after-configuring-the-first-author-node}

Wenn Sie diese Aufgabe abgeschlossen haben, erhalten Sie eine Paketdatei, die die Vorgaben für Videoanalysen enthält. Diese Vorgaben enthalten eine Report Suite, den Tracking-Server, den Tracking-Namespace und die Experience Cloud-Organisations-ID (falls verfügbar).

1. Konfigurieren Sie, falls noch nicht geschehen, die Dynamic Media-Konfiguration (vor 6.3).
1. (Optional) Zeigen Sie die Report Suite-ID an und kopieren Sie diese (Sie benötigen Zugriff auf das JCR). Eine Report Suite-ID ist nicht erforderlich, vereinfacht jedoch die Überprüfung.
1. Erstellen Sie ein Paket mit Package Manager.
1. Bearbeiten Sie das Paket so, dass es einen Filter enthält.

   In Experience Manager: `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

1. Erstellen Sie das Paket.
1. Laden Sie das Vorgabenpaket für die Video-Analyse herunter oder geben Sie es zum Teilen mit künftigen neuen Author-Knoten frei.

### Installieren des Vorgabenpakets für Videoanalysen vor dem Konfigurieren weiterer Autorknoten {#installing-the-video-analytics-preset-package-before-you-configure-additional-author-nodes}

Schließen Sie diese Aufgabe ab, ***bevor*** Sie die Dynamic Media-Konfiguration (vor 6.3) konfigurieren. Andernfalls wird eine weitere nicht verwendete Report Suite erstellt. Darüber hinaus wird die Datenerfassung nicht optimiert, obwohl die Videoberichte weiterhin korrekt ausgeführt werden.

Stellen Sie sicher, dass der Zugriff auf das Vorgabenpaket für die Videoanalyse auf dem ersten Autorknoten möglich ist.

1. Laden Sie das zuvor erstellte Vorgabenpaket für Videoanalysen in Package Manager hoch.
1. Installieren Sie das Vorgabenpaket für die Video-Analyse.
1. Konfigurieren Sie die Dynamic Media-Konfiguration (vor 6.3).

### Überprüfen und debuggen Sie die Paketinstallation {#verifying-and-debugging-the-package-installation}

1. Führen Sie einen der folgenden Schritte aus, um die Paketinstallation zu überprüfen und bei Bedarf zu debuggen:

   * **Überprüfen der Vorgabe für die Videoanalyse über das JCR** Zum Überprüfen der Vorgabe für die Videoanalyse über das JCR benötigen Sie Zugriff auf CRXDE Lite.

     Experience Manager: Navigieren Sie in CRXDE Lite zu `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata`

     Wie in `https://localhost:4502/crx/de/index.jsp#/conf/global/settings/dam/dm/presets/analytics/jcr%3Acontent/userdata`

     Wenn Sie im Autorknoten keinen Zugriff auf CRXDE Lite haben, können Sie die Vorgabe über den Veröffentlichungsserver überprüfen.

   * **Überprüfen der Vorgabe für Videoanalysen über den Bildserver**

     Sie können die Vorgabe für Videoanalysen direkt überprüfen, indem Sie eine Bildserver-Anfrage „req=userdata“ erstellen.
Um beispielsweise die Analytics-Vorgabe im Autorknoten anzuzeigen, können Sie die folgende Anfrage stellen:

     `https://localhost:4502/is/image/conf/global/settings/dam/dm/presets/analytics?req=userdata`

     Um die Vorgabe auf Veröffentlichungsservern zu überprüfen, können Sie eine ähnliche direkte Anfrage an den Veröffentlichungsserver richten. Die Antworten sind auf dem Autor- und Veröffentlichungsknoten identisch. Die Antwort sieht ähnlich wie die folgende aus:

     ```
     marketingCloudOrgId=0FC4E86B573F99CC7F000101
      reportSuite=aemaem6397618-2018-05-23
      trackingNamespace=aemvideodal
      trackingServer=aemvideodal.d2.sc.omtrdc.net
     ```

   * **Überprüfen Sie die Vorgabe für Videoanalysen über das Tool für Videoberichte in Experience Manager**
Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Videoberichte]**

     `https://localhost:4502/mnt/overlay/dam/gui/content/s7dam/videoreports/videoreport.html`

     Wenn die folgende Fehlermeldung angezeigt wird, ist die Report Suite zwar verfügbar, aber nicht ausgefüllt. Dieser Fehler ist korrekt und erwünscht, wenn es sich um eine Neuinstallation handelt, bevor das System Daten erfasst hat.

   ![screen_shot_2018-05-23at52254pm](assets/screen_shot_2018-05-23at52254pm.png)

   Laden Sie zum Generieren von Berichtsdaten ein Video hoch und veröffentlichen Sie es. Verwenden Sie **[!UICONTROL URL kopieren]** und lassen Sie das Video mindestens einmal laufen.

   Es kann bis zu 12 Stunden dauern, bevor die Berichtsdaten aus der Verwendung in Video-Viewer geladen werden.

   Wenn ein Fehler vorliegt und die Report Suite nicht ordnungsgemäß festlegt wurde, wird der folgende Warnhinweis angezeigt.

   ![screen_shot_2018-05-23at52612pm](assets/screen_shot_2018-05-23at52612pm.png)

   Dieser Fehler wird auch angezeigt, wenn Videoberichte ausgeführt wird, bevor Sie die Dynamic Media-Konfiguration (vor 6.3) konfigurieren.

### Fehlerbehebung bei der Konfiguration von Videoberichten {#troubleshooting-the-video-reporting-configuration}

* Während der Installation kommt es bei Verbindungen mit dem Analytics-API-Server manchmal zu Timeouts. Bei der Installation wird 20-mal versucht, die Verbindung wiederherzustellen. In diesem Fall werden in der Protokolldatei mehrere Fehler aufgezeichnet. Suchen Sie nach `SiteCatalystReportService`.
* Wird das Vorgabenpaket für die Analyse nicht vorab installiert, wird möglicherweise eine neue Report Suite erstellt.
* Beim Aktualisieren von Experience Manager 6.3 auf Experience Manager 6.4 oder Experience Manager 6.4.1 und dem anschließenden Durchführen der Dynamic Media-Konfiguration (vor 6.3) wird weiterhin eine Report Suite erstellt. Dieses Problem ist bekannt und wird in Experience Manager 6.4.2 behoben.

### Informationen zur Vorgabe für Videoanalysen {#about-the-video-analytics-preset}

Die Vorgabe für Videoanalysen wird auch als Analysevorgabe bezeichnet und ist in Dynamic Media neben den Viewer-Vorgaben gespeichert. Sie entspricht im Grunde einer Viewer-Vorgabe, enthält jedoch auch Informationen zum Konfigurieren von AppMeasurement- und Video Heartbeat-Berichten.

Die Vorgabe umfasst die folgenden Eigenschaften:

* `reportSuite`
* `trackingServer`
* `trackingNamespace`
* `marketingCloudOrgId` (in älteren Experience Manager-Versionen nicht vorhanden)

Diese Vorgabe wird in Experience Manager 6.4 und neueren Versionen unter `/conf/global/settings/dam/dm/presets/analytics/jcr:content/userdata` gespeichert.

## Replizieren von Katalogeinstellungen {#replicating-catalog-settings}

Veröffentlichen Sie Ihre eigenen Standardeinstellungen für den Katalog im Rahmen der Einrichtung per JCR. Gehen Sie wie folgt vor, um die Katalogeinstellungen zu replizieren:

1. Führen Sie in einem Terminal-Fenster folgenden Befehl aus:

   `curl -u admin:admin localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

1. Navigieren Sie in Experience Manager zum folgenden CRXDE Lite-Speicherort (Administratorrechte erforderlich):

   `https://<*server*>:<*port*>/crx/de/index.jsp#/conf/global/settings/dam/dm/imageserver/`

1. Wählen Sie die Registerkarte **[!UICONTROL Replikation]** aus.
1. Klicken Sie auf **[!UICONTROL Replizieren]**.

## Replizieren von Viewer-Vorgaben {#replicating-viewer-presets}

Zum Bereitstellen *eines Assets mit einer Viewer-Vorgabe müssen Sie die Viewer-Vorgabe replizieren bzw. veröffentlichen*. (Alle Viewer-Vorgaben müssen aktiviert *und* repliziert werden, um die URL abzurufen oder Code für ein Asset einzubetten.)
Weitere Informationen finden Sie unter [Veröffentlichen von Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#publishing-viewer-presets).

>[!NOTE]
>
Standardmäßig zeigt das System mehrere Ausgabedarstellungen an, wenn Sie **[!UICONTROL Ausgabedarstellungen]** auswählen, und mehrere Viewer-Vorgaben, wenn Sie in der Detailansicht des Assets **[!UICONTROL Viewer]** auswählen. Sie können die angezeigte Anzahl erhöhen oder verringern. Siehe [Erhöhung der Anzahl angezeigter Bildvorgaben](/help/assets/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) oder [Erhöhung der Anzahl angezeigter Viewer-Vorgaben](/help/assets/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

## Filtern von Assets für die Replikation {#filtering-assets-for-replication}

Bei anderen als Dynamic Media-Bereitstellungen replizieren Sie *alle* Assets (sowohl Bilder als auch Videos) aus Ihrer Experience Manager-Autorenumgebung zum Experience Manager-Veröffentlichungsknoten. Dieser Workflow ist erforderlich, weil von den Experience Manager-Veröffentlichungs-Servern auch die Assets bereitgestellt werden.

Da Assets in Dynamic Media-Bereitstellungen über die Cloud bereitgestellt werden, ist es nicht erforderlich, dieselben Assets auf Experience Manager-Veröffentlichungsknoten zu replizieren. Bei einem Workflow für die „hybride Veröffentlichung“ dieser Art werden zusätzliche Speicherkosten und längere Verarbeitungsdauern für das Replizieren der Assets vermieden. Andere Inhalte, z. B. Dynamic Media-Viewer, Seiten von Websites und statische Inhalte, werden weiterhin über die Experience Manager-Veröffentlichungsknoten bereitgestellt.

Zusätzlich zu den Assets werden auch die folgenden anderen Elemente repliziert:

* Dynamic Media-Bereitstellungskonfiguration: `/conf/global/settings/dam/dm/imageserver/jcr:content`
* Bildvorgaben: `/conf/global/settings/dam/dm/presets/macros`
* Viewer-Vorgaben: `/conf/global/settings/dam/dm/presets/viewer`

Mit den Filtern können Sie Assets von der Replikation auf dem Experience Manager-Veröffentlichungsknoten *ausschließen*.

### Verwenden von Asset-Standardfiltern für die Replikation {#using-default-asset-filters-for-replication}

Wenn Sie Dynamic Media für die (1) Bildverarbeitung in der Produktion *oder* die (2) Bild- und Videoverarbeitung verwenden, können Sie die von Adobe bereitgestellten Standardfilter unverändert nutzen. Folgende Filter sind standardmäßig aktiviert:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>MIME-Typ</strong></td>
   <td><strong>Ausgabedarstellungen</strong></td>
  </tr>
  <tr>
   <td>Dynamic Media-Bildbereitstellung</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td>
   <td><p>Beginnt mit <strong>image/</strong></p> <p>Enthält <strong>application/</strong> und endet mit <strong>set</strong>.</p> </td>
   <td>Die vorkonfigurierten „filter-images“ (gilt für einzelne Bilder, einschließlich interaktiver Bilder) und „filter-sets“ (gilt für Rotationssets, Bildsets, gemischte Medien-Sets und Karussellsets) werden:
    <ul>
     <li>PTIFF-Bilder und Metadaten für die Replikation enthalten (Beliebige Ausgabedarstellung, die mit <strong>cqdam</strong> beginnt).</li>
     <li>Das Originalbild und statische Bildausgabefdarstellungen werden von der Replikation ausgeschlossen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media-Videobereitstellung</td>
   <td>filter-video</td>
   <td>Beginnt mit <strong>video/</strong></td>
   <td>Das vorkonfigurierte „filter-video“ wird:
    <ul>
     <li>Proxy-Videoausgabedarstellungen, Videominiatur-/Posterbild, Metadaten (sowohl bei übergeordneten Video- als auch Videoausgabedarstellungen) für die Replikation enthalten (Beliebige Ausgabedarstellung, die mit <strong>cqdam</strong> beginnt).</li>
     <li>Das Originalvideo und statische Miniaturausgabedarstellungen werden von der Replikation ausgeschlossen.<br /> <br /> <strong>Hinweis:</strong> Die Proxy-Videoausgabedarstellungen enthalten keine Binärdateien, sondern es handelt sich lediglich um Knoteneigenschaften. Dies hat daher keine Auswirkung auf die Repositorygröße des Herausgebers.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Integration von Dynamic Media Classic (Scene7)</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p>filter-video</p> </td>
   <td><p>Beginnt mit <strong>image/</strong></p> <p>Enthält <strong>application/</strong> und endet mit <strong>set</strong>.</p> <p>Beginnt mit <strong>video/</strong></p> </td>
   <td><p>Sie konfigurieren den Transport-URI so, dass er auf Ihren Experience Manager-Veröffentlichungsserver verweist, anstatt auf die Adobe Dynamic Media Cloud-Replikationsdienst-URL. Durch das Einrichten dieses Filters können Assets mit Dynamic Media Classic bereitgestellt werden, anstatt mit der Experience Manager-Veröffentlichungsinstanz.</p> <p>Die vorkonfigurierten „filter-images“, „filter-sets“ und „filter-video“ werden:</p>
    <ul>
     <li>PTIFF-Bilder, Proxy-Videoausgabedarstellungen und Metadaten für die Replikation enthalten. Da diese in JCR nicht vorhanden sind, werden keine Schritte ausgeführt (bei Durchführung der Experience Manager/Dynamic Media Classic-Integration).</li>
     <li>Das Originalbild, statische Bildausgabedarstellungen, das Originalvideo und statische Miniaturausgabedarstellungen werden aus der Replikation ausgeschlossen. Stattdessen stellt Dynamic Media Classic Bild- und Video-Assets bereit.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
Filter gelten für MIME-Typen und können nicht pfadspezifisch sein.

### Einrichten von Asset-Filtern nur für die Bereitstellung von Videos {#setting-up-asset-filters-for-video-only-deployments}

Wenn Sie Dynamic Media ausschließlich für Videos nutzen, können Sie mit diesen Schritten Asset-Filter für die Replikation einrichten:

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** > **[!UICONTROL Agenten für Autor]**.
1. klicken Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Standardagent (Veröffentlichen)]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Markieren Sie im Dialogfeld **[!UICONTROL Agenteneinstellungen]** auf der Registerkarte **[!UICONTROL Einstellungen]** die Option **[!UICONTROL Aktiviert]**, um den Agenten zu aktivieren.
1. Klicken Sie auf **[!UICONTROL OK]**.
1. Gehen Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`.
1. Suchen Sie nach **[!UICONTROL filter-video]**, klicken Sie mit der rechten Maustaste darauf und klicken Sie auf **[!UICONTROL Kopieren]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/publish`.
1. Suchen Sie nach `jcr:content`, klicken Sie mit der rechten Maustaste darauf und klicken Sie auf **[!UICONTROL Einfügen]**.

So wird für die Experience Manager-Veröffentlichungsinstanz eingerichtet, dass das Video-Posterbild sowie die für die Wiedergabe erforderlichen Videometadaten bereitgestellt werden, während das Video selbst vom Dynamic Media Cloud Service bereitgestellt wird. Mit dem Filter werden auch das Originalvideo und statische Miniaturausgabedarstellungen, die auf der Veröffentlichungsinstanz nicht benötigt werden, von der Replikation ausgeschlossen.

### Einrichten von Asset-Filtern für die Bildverarbeitung in produktionsfremden Bereitstellungen {#setting-up-asset-filters-for-imaging-in-non-production-deployments}

Wenn Sie Dynamic Media für die Bilddarstellung in Bereitstellungen außerhalb der Produktion nutzen, können Sie mit diesen Schritten Asset-Filter für die Replikation einrichten:

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** > **[!UICONTROL Agenten für Autor]**.
1. klicken Sie auf der Seite „Agenten für Autor“ auf **[!UICONTROL Standardagent (Veröffentlichen)]**.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Markieren Sie im Dialogfeld **[!UICONTROL Agenteneinstellungen]** auf der Registerkarte **[!UICONTROL Einstellungen]** die Option **[!UICONTROL Aktiviert]**, um den Agenten zu aktivieren.
1. Klicken Sie auf **[!UICONTROL OK]**.
1. Gehen Sie in Experience Manager zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`.

   ![image-2018-01-16-10-22-40-410](assets/image-2018-01-16-10-22-40-410.png)

1. Suchen Sie nach **[!UICONTROL filter-images]**, klicken Sie mit der rechten Maustaste darauf und klicken Sie auf **[!UICONTROL Kopieren]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/publish`.
1. Suchen Sie nach `jcr:content`, klicken Sie mit der rechten Maustaste darauf und gehen Sie dann zu **[!UICONTROL Erstellen]** > **[!UICONTROL Knoten erstellen]**. Geben Sie den Namen `damRenditionFilters` des Typs `nt:unstructured` ein.
1. Suchen Sie nach `damRenditionFilters`, klicken Sie mit der rechten Maustaste darauf und klicken Sie auf **[!UICONTROL Einfügen]**.

Mit diesen Schritten wird die Experience Manager-Veröffentlichungsinstanz so eingerichtet, dass sie die Bilder für Ihre produktionsfremde Umgebung bereitstellt. Mit dem Filter werden auch das Originalbild und statische Ausgabedarstellungen, die auf der Veröffentlichungsinstanz nicht benötigt werden, von der Replikation ausgeschlossen.

>[!NOTE]
>
Wenn es für eine Autoreninstanz viele verschiedene Filter gibt, muss jedem Agenten eine andere Benutzerin bzw. ein anderer Benutzer zugewiesen werden.  Der Granite-Code erzwingt, dass pro Person nur ein Filter angewendet wird.  Deswegen sollten Sie für jeden eingerichteten Filter einen anderen Benutzer einrichten.
>
Verwenden Sie mehr als einen Filter auf einem Server? Beispielsweise einen Filter für die zu veröffentlichende Replikation und einen zweiten Filter für s7delivery. Wenn dies der Fall ist, müssen Sie sicherstellen, dass diesen beiden Filtern im x-Knoten eine unterschiedliche userId zugewiesen ist. Wenn dies der Fall ist, müssen Sie sicherstellen, dass diesen beiden Filtern im `jcr:content`-Knoten eine unterschiedliche **userId** zugewiesen ist. Sehen Sie sich das folgende Bild an:

![image-2018-01-16-10-26-28-465](assets/image-2018-01-16-10-26-28-465.png)

### Anpassen von Asset-Filtern für die Replikation (optional) {#customizing-asset-filters-for-replication}

1. Klicken Sie in Experience Manager auf das Experience Manager-Logo, um auf die globale Navigationskonsole zuzugreifen, und dann auf **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.
1. Navigieren Sie in der Ordnerstruktur auf der linken Seite zu `/etc/replication/agents.author/dynamic_media_replication/jcr:content/damRenditionFilters`, um die Filter anzuzeigen.

   ![chlimage_1-511](assets/chlimage_1-511.png)

1. Zum Definieren des MIME-Typs für den Filter können Sie den MIME-Typ wie folgt ermitteln:

   Erweitern Sie in der linken Leiste `content > dam > <locate_your_asset> >  jcr:content > metadata` und suchen Sie dann in der Tabelle nach `dc:format`.

   Die folgende Grafik ist ein Beispiel für den Pfad eines Assets zu `dc:format`.

   ![chlimage_1-512](assets/chlimage_1-512.png)

   Beachten Sie Folgendes: Das `dc:format` für das Asset `Fiji Red.jpg` lautet `image/jpeg`.

   Damit dieser Filter für alle Bilder gilt, müssen Sie den Wert unabhängig vom Format auf `image/*` festlegen. Hierbei ist `*`* ein regulärer Ausdruck, der auf alle Bilder beliebigen Formats angewendet wird.

   Wenn der Filter nur für Bilder vom Typ JPEG gelten soll, geben Sie den Wert `image/jpeg` ein.

1. Definieren Sie, welche Ausgabedarstellungen Sie in die Replikation einbeziehen bzw. davon ausschließen möchten.

   Sie können die folgenden Zeichen verwenden, um einen Filtervorgang für die Replikation durchzuführen:

   | Zu verwendendes Zeichen | Filtern von Assets für die Replikation |
   | --- | --- |
   | `*` | Platzhalterzeichen |
   | `+` | Schließt Assets in die Replikation ein |
   | `-` | Schließt Assets aus der Replikation aus |

   Navigieren Sie zu `content/dam/<locate your asset>/jcr:content/renditions`.

   Die folgende Grafik ist ein Beispiel für die Ausgabedarstellungen eines Assets.

   ![chlimage_1-513](assets/chlimage_1-4.png)

   Wenn Sie unter Verwendung des obigen Beispiels nur PTIFF (Pyramid TIFF) replizieren möchten, geben Sie `+cqdam,*` ein, um alle Ausgabedarstellungen einzubeziehen, die mit `cqdam` beginnen. Im Beispiel lautet diese Ausgabedarstellung `cqdam.pyramid.tiff`.

   Wenn Sie nur das Original replizieren möchten, geben Sie `+original` ein.

## Konfigurieren der Einstellungen des Dynamic Media-Bild-Servers {#configuring-dynamic-media-image-server-settings}

Das Konfigurieren des Dynamic Media-Bild-Servers umfasst die Bearbeitung des Adobe CQ Scene7 ImageServer-Bundles und des Adobe CQ Scene7 PlatformServer-Bundles.

>[!NOTE]
>
Dynamic Media funktioniert vorkonfiguriert [nach der Aktivierung](#enabling-dynamic-media). Sie können für Ihre Installation optional aber eine Feineinstellung verwenden, indem Sie den Dynamic Media-Bildserver so konfigurieren, dass er bestimmte Spezifikationen oder Anforderungen erfüllt.

**Voraussetzung**: Stellen Sie *vor* dem Konfigurieren des Dynamic Media-Bildservers sicher, dass Ihre Windows®-VM eine Installation der Microsoft® Visual C++-Bibliotheken enthält. Diese Bibliotheken werden benötigt, um den Dynamic Media-Bildserver auszuführen. Sie können das [Microsoft® Visual C++ 2010 Redistributable Package (x64) hier herunterladen](https://www.microsoft.com/de-de/download/details.aspx?id=26999).

So konfigurieren Sie die Einstellungen für den Dynamic Media-Bildserver:

1. Klicken Sie in der oberen linken Ecke in Experience Manager auf **[!UICONTROL Adobe Experience Manager]**, um auf die Konsole für die globale Navigation zuzugreifen, und gehen Sie dann zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**.
1. Gehen Sie auf der Adobe Experience Manager-Seite für die Web-Konsolen-Konfiguration zu **[!UICONTROL OSGi]** > **[!UICONTROL Konfiguration]**, um alle Bundles aufzulisten, die in Experience Manager derzeit ausgeführt werden.

   Die Dynamic Media-Server für die Bereitstellung sind in der Liste unter den folgenden Namen angegeben:

   * `Adobe CQ Scene7 ImageServer`
   * `Adobe CQ Scene7 PlatformServer`

1. Klicken Sie in der Liste mit den Bundles rechts von Adobe CQ Scene7 ImageServer auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Legen Sie im Dialogfeld für Adobe CQ Scene7 ImageServer die folgenden Konfigurationswerte fest:

   >[!NOTE]
   >
   Für gewöhnlich ist keine Änderung der Standardwerte erforderlich. Falls Sie jedoch die Standardeinstellungen ändern, müssen Sie das Bundle neu starten, damit die Änderungen wirksam werden.

   | Eigenschaft | Standardwert | Beschreibung |
   | --- | --- | --- |
   | `TcpPort.name` | *`empty`* | Portnummer für die Kommunikation mit dem ImageServer-Prozess. Der freie Port wird standardmäßig automatisch erkannt. |
   | `AllowRemoteAccess.name` | *`empty`* | Der Remotezugriff auf den ImageServer-Prozess wird zugelassen bzw. nicht zugelassen. Bei „false“ lauscht der Bildserver nur über „localhost“.<br> In Externalizer-Standardeinstellungen, die auf den „localhost“ verweisen, muss die tatsächliche Domain oder IP-Adresse der jeweiligen VM-Instanz angegeben werden. Der Grund dafür ist, dass der „localhost“ auf das übergeordnete System der VM verweist.<br>Domains oder IP-Adressen für die VM müssen ggf. über einen Hostdateieintrag verfügen, damit die Auflösung selbst durchgeführt werden kann. |
   | `MaxRenderRgnPixels` | 16 MP | Maximale Größe in Megapixel, die gerendert wird. |
   | `MaxMessageSize` | 16 MB | Maximale Nachrichtengröße in MB, die bereitgestellt wird. |
   | `RandomAccessUrlTimeout` | 20 | Wert der maximalen Wartezeit in Sekunden, wie lange der Bildserver darauf warten soll, dass JCR auf eine Ranged-Tile-Anfrage reagiert. |
   | `WorkerThreads` | 10 | Anzahl der Workerthreads. |

1. Klicken Sie auf **[!UICONTROL Speichern]**.
1. Klicken Sie in der Liste mit den Bundles rechts von Adobe CQ Scene7 PlatformServer auf das Symbol **[!UICONTROL Bearbeiten]**.
1. Legen Sie im Dialogfeld für Adobe CQ Scene7 PlatformServer die folgenden Standardwerte fest:

   >[!NOTE]
   >
   Der Dynamic Media-Bildserver verwendet einen eigenen Datenträgercache für das Zwischenspeichern von Antworten. Der Experience Manager-HTTP-Cache und der Dispatcher können nicht genutzt werden, um Antworten vom Dynamic Media-Bild-Server zwischenzuspeichern.

   | Eigenschaft | Standardwert | Beschreibung |
   |---|---|---|
   | Cache enabled (Cache aktiviert) | Aktiviert | Gibt an, ob der Cache für Antworten aktiviert ist. |
   | Cache roots (Cache-Stämme) | cache | Mindestens ein Pfad zu Ordnern des Caches für Antworten. Relative Pfade werden für den internen s7imaging-Bundle-Ordner aufgelöst. |
   | Cache Max Size (Maximale Cache-Größe) | 200000000 | Gibt die maximale Größe des Caches für Antworten in Byte an. |
   | Cache Max Entries (Maximale Cache-Einträge) | 100000 | Gibt die maximale Anzahl von Einträgen an, die im Cache zulässig ist. |

### Standardeinstellungen des Manifests {#default-manifest-settings}

Mit dem Standardmanifest können Sie die Standardwerte konfigurieren, die zum Generieren der Antworten für die Dynamic Media-Bereitstellung verwendet werden. Sie können eine Feinabstimmung der Qualität (JPEG-Qualität, Auflösung, Modus für Resampling) und des Cachings (Ablauf) vornehmen und das Rendern von Bildern verhindern, die zu groß sind (defaultpix, defaultthumbpix, maxpix).

Der Speicherort der Standardmanifest-Konfiguration wird aus dem Standardwert für **[!UICONTROL Catalog root]** des **[!UICONTROL Adobe CQ Scene7 PlatformServer]**-Bundles übernommen. Standardmäßig befindet sich dieser Wert unter dem folgenden Pfad unter **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]**.

`/conf/global/settings/dam/dm/imageserver/`

![Konfigurieren des Bildservers in CRXDE Lite](assets/configimageservercrxdelite.png)

Sie können die Werte der Eigenschaften wie in der folgenden Tabelle beschrieben ändern, indem Sie neue Werte eingeben.

Wenn Sie Ihre Änderungen am Standardmanifest abgeschlossen haben, klicken Sie in der oberen linken Ecke der Seite auf **[!UICONTROL Alle speichern]**.

Klicken Sie unbedingt auf die Registerkarte **[!UICONTROL Zugriffssteuerung]** (rechts neben der Registerkarte „Eigenschaften“) und legen Sie die Zugriffssteuerungsrechte für die Benutzer „Alle“ und „dynamic-media-replication“ auf `jcr:read` fest.

![Konfigurieren des Bildservers in CRXDE Lite und Festlegen der Registerkarte „Zugriffssteuerung“](assets/configimageservercrxdeliteaccesscontroltab.png)

Tabelle mit Manifesteinstellungen und deren Standardwerte:

| Eigenschaft | Standardwert | Beschreibung |
| --- | --- | --- |
| `bkgcolor` | `FFFFFF` | Standard-Hintergrundfarbe. RGB-Wert, mit dem alle Bereiche des Antwortbildes gefüllt werden, die keine Bilddaten enthalten. Siehe auch [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `defaultpix` | `300,300` | Standard-Ansichtsgröße. Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe, falls bei der Anfrage die Größe nicht explizit durch die Werte „wid=“, „hei=“ oder „scl=“ festgelegt wird.<br>Wird als zwei ganze Zahlen angegeben (0 oder höher), die durch ein Komma getrennt sind. Breite und Höhe in Pixel. Einer oder beide Werte können auf 0 festgelegt werden, um die Einschränkung aufzuheben. Gilt nicht für verschachtelte oder eingebettete Anforderungen.<br>Siehe auch [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html?lang=de#image-serving-api) in der Image-Serving-API.<br>Normalerweise verwenden Sie aber eine Viewer-Vorgabe oder Bildvorgabe, um das Asset bereitzustellen. „defaultpix“ gilt nur für ein Asset, für das keine Viewer-Vorgabe oder Bildvorgabe verwendet wird. |
| `defaultthumbpix` | `100,100` | Standardgröße für Miniaturansichten. Wird anstelle von „attribute::DefaultPix“ für Anfragen von Miniaturen verwendet (`req=tmb`).<br>Der Server beschränkt die Größe der Antwortbilder auf diese Breite und Höhe. Diese Aktion ist „true“, wenn eine Anfrage einer Miniatur (`req=tmb`) die Größe nicht explizit angibt und die Anzeigegröße nicht explizit mithilfe von `wid=`, `hei=` oder `scl=` angibt.<br>Wird als zwei ganze Zahlen angegeben (0 oder höher), die durch ein Komma getrennt sind. Breite und Höhe in Pixel. Einer oder beide Werte können auf 0 festgelegt werden, um die Einschränkung aufzuheben.<br>Gilt nicht für verschachtelte oder eingebettete Anforderungen.<br>Siehe auch [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `expiration` | `36000000` | Standardeinstellung für die Gültigkeitsdauer des Client-Caches.  Bietet ein standardmäßiges Ablaufintervall für den Fall, dass ein bestimmter Katalogdatensatz keinen gültigen Wert für „catalog::Expiration“ (also den Ablauf des Katalogs) aufweist.<br>Reelle Zahl, 0 oder höher. Anzahl von Millisekunden bis zum Ablauf seit der Generierung der Daten.  Geben Sie „0“ an, wenn das Antwortbild immer sofort ablaufen soll. Hiermit wird das Client-Caching praktisch deaktiviert.  Dieser Wert ist standardmäßig auf zehn Stunden festgelegt. Dies bedeutet, dass es bei der Veröffentlichung eines neuen Bildes zehn Stunden dauert, bis das alte Bild aus dem Cache des Benutzers entfernt wird. Wenden Sie sich an den Kunden-Support, wenn der Cache früher geleert werden soll.<br>Siehe auch [Expiration](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html?lang=de) in der Image-Serving-API. |
| `jpegquality` | `80` | Standardattribute für JPEG-Verschlüsselung.  Legt die Standardattribute von JPEG-Antwortbildern fest.<br>Ganze Zahl und Flag, getrennt durch ein Komma. Der erste Wert liegt im Bereich 1 bis 100 und definiert die Qualität. Der zweite Wert kann „0“ für normales Verhalten oder „1“ sein, um anzugeben, dass die normalerweise von der JPEG-Kodierung genutzte RGB-Farbunterabtastung deaktiviert werden soll.<br>Siehe auch [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `maxpix` | `2000,2000` | Maximale Größe des Antwortbildes. Maximale Breite und Höhe des Antwortbildes, das an den Client zurückgegeben wird.<br>Der Server gibt einen Fehler zurück, wenn eine Anfrage zu einem Antwortbild führt, dessen Breite oder Höhe den Wert von „attribute::MaxPix“ übersteigt.<br>Siehe auch [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `resmode` | `SHARP2` | Standard-Resampling-Modus. Gibt die standardmäßigen Resampling- und Interpolationsattribute an, die für die Skalierung von Bilddaten verwendet werden sollen.<br>Wird verwendet, wenn `resMode=` in einer Anfrage nicht angegeben wird.<br>Zulässige Werte umfassen `BILIN`, `BICUB`oder `SHARP2`.<br>Enum. Festlegung auf Interpolationsmodus: 2 für `bilin`, 3 für `bicub` oder 4 für `sharp2`. Verwenden Sie `sharp2`, um bestmögliche Ergebnisse zu erzielen.<br>Siehe auch [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `resolution` | `72` | Standardobjektauflösung.  Bietet eine standardmäßige Objektauflösung, falls ein bestimmter Katalogdatensatz keinen gültigen Wert für „catalog::Resolution“ aufweist.<br>Reelle Zahl, größer als 0. Wird normalerweise als Pixel pro Zoll ausgedrückt, aber es können auch andere Einheiten verwendet werden, z. B. Pixel pro Meter.<br>Siehe auch [Resolution](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-resolution.html?lang=de#image-serving-api) in der Image-Serving-API. |
| `thumbnailtime` | `1%,11%,21%,31%,41%,51%,61%,71%,81%,91%` | Diese Werte stellen eine Momentaufnahme der Videowiedergabezeit dar und werden an [encoding.com](https://www.encoding.com/) übergeben. Weitere Informationen finden Sie unter [Informationen zu Videominiaturen](/help/assets/video.md#about-video-thumbnails-in-dynamic-media-hybrid-mode). |

## Konfigurieren des Farb-Managements für Dynamic Media {#configuring-dynamic-media-color-management}

Mit dem Farbmanagement von Dynamic Media können Sie die Farbe von Assets für die Vorschau korrigieren.

Bei der Farbkorrektur behalten aufgenommene Assets ihren Farbraum (RGB, CMYK, Grau) und das eingebettete Farbprofil in der generierten Pyramid TIFF-Ausgabedarstellung bei. Wenn Sie eine dynamische Ausgabedarstellung anfordern, wird die Bildfarbe gemäß dem Zielfarbraum korrigiert. Sie konfigurieren das Ausgabefarbprofil in JCR in den Veröffentlichungseinstellungen von Dynamic Media.

Das Farbmanagement der Adobe verwendet ICC (International Color Consortium)-Profile, ein vom ICC definiertes Format.

Sie können das Farbmanagement von Dynamic Media und Bildvorgaben konfigurieren, indem Sie eine CMYK-, RGB- oder Graustufen-Ausgabe verwenden. Siehe [Konfigurieren von Bildvorgaben](/help/assets/managing-image-presets.md).

Für komplexere Anwendungsfälle kann der Modifikator `icc=` für die manuelle Konfiguration verwendet werden, um explizit ein Ausgabefarbprofil auszuwählen:

* `icc` – [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html?lang=de](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-icc.html?lang=de)

* `iccEmbed` – [https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html?lang=de](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-iccembed.html?lang=de)

>[!NOTE]
>
Der Standardsatz der Farbprofile von Adobe ist nur verfügbar, wenn Sie das [Feature Pack 12445 von Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/featurepack/cq-6.3.0-featurepack-12445) installiert haben. Alle Feature Packs und Service Packs sind über [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) verfügbar. Das Feature Pack 12445 enthält die Farbprofile von Adobe.


### Installieren von Feature Pack 12445 {#installing-feature-pack}

Um die Dynamic Media-Farbmanagementfunktionen zu verwenden, installieren Sie das Feature Pack 12445.

**Gehen Sie wie folgt vor, um das Feature Pack 12445 zu installieren:**

1. Gehen Sie zu [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) und laden Sie `cq-6.3.0-featurepack-12445` herunter.

   Weitere Informationen zur Verwendung von Paketen in [!DNL Adobe Experience Manager] finden Sie unter [Arbeiten mit Paketen](/help/sites-administering/package-manager.md).

1. Installieren Sie das Feature Pack.

### Konfigurieren der Standardfarbprofile {#configuring-the-default-color-profiles}

Nach der Installation des Feature Pack müssen Sie die richtigen Standardfarbprofile konfigurieren, um die Farbkorrektur beim Anfragen von RGB- oder CMYK-Bilddaten zu ermöglichen.

**Gehen Sie wie folgt vor, um die Standardfarbprofile zu konfigurieren:**

1. Gehen sie in **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL CRXDE Lite]** zum Ordner `/conf/global/settings/dam/dm/imageserver/jcr:content`, der die Standardfarbprofile von Adobe enthält.

   ![chlimage_1-514](assets/chlimage_1-514.png)

1. Fügen Sie eine Farbkorrektureigenschaft hinzu, indem Sie zum unteren Rand der Registerkarte **[!UICONTROL Eigenschaften]** scrollen. Geben Sie den Eigenschaftsnamen, den Typ und den Wert manuell ein, wie in den folgenden Tabellen beschrieben. Klicken Sie nach dem Eingeben der Werte auf **[!UICONTROL Hinzufügen]** und dann auf **[!UICONTROL Alle speichern]**, um die Werte zu speichern.

   Die Farbkorrektureigenschaften werden in der Tabelle **Farbkorrektureigenschaften** beschrieben. Die Werte, die Sie den Farbkorrektureigenschaften zuweisen können, sind in der Tabelle **Farbprofil** angegeben.

   Fügen Sie beispielsweise unter **[!UICONTROL Name]** den Namen `iccprofilecmyk` hinzu, wählen Sie bei **[!UICONTROL Typ]** die Option `String` und fügen Sie `WebCoated` als **[!UICONTROL Wert]** ein. Klicken Sie anschließend auf **[!UICONTROL Hinzufügen]** und dann auf **[!UICONTROL Alle speichern]**, um die Werte zu speichern.

   ![chlimage_1-515](assets/chlimage_1-515.png)

   **Tabelle „Farbkorrektureigenschaften“**

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaft</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Standard</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html?lang=de">iccprofilergb</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen RGB-Profils.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html?lang=de">iccprofilecmyk</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen CMYK-Farbprofils.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html?lang=de">iccprofilegray</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen grauen Farbprofils.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcrgb.html?lang=de">iccprofilesrcrgb</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen RGB-Farbprofils, das für RGB-Bilder ohne eingebettetes Farbprofil verwendet wird.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrccmyk.html?lang=de">iccprofilesrccmyk</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen CMYK-Farbprofils, das für CMYK-Bilder ohne eingebettetes Farbprofil verwendet wird.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilesrcgray.html?lang=de">iccprofilesrcgray</a></td>
   <td>Zeichenfolge</td>
   <td>&lt;empty&gt;</td>
   <td>Name des standardmäßigen Farbprofils für Grau, das für CMYK-Bilder ohne eingebettetes Farbprofil verwendet wird.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccblackpointcompensation.html?lang=de">iccblackpointpayment</a></td>
   <td>Boolesch</td>
   <td>True</td>
   <td>Gibt an, ob während der Farbkorrektur eine Schwarzpunktkompensation erfolgt. Adobe empfiehlt, dass diese Einstellung aktiviert ist.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccdither.html?lang=de">iccdither</a></td>
   <td>Boolesch</td>
   <td>False</td>
   <td>Gibt an, ob die Fehlerdiffusion während der Farbkorrektur durchgeführt wird.</td>
  </tr>
  <tr>
   <td><a href="https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html?lang=de">iccrenderintent</a></td>
   <td>Zeichenfolge</td>
   <td>relative</td>
   <td><p>Gibt die Rendering-Absicht an. Zulässige Werte sind: <strong>wahrnehmungsorientiert, relativ, Sättigung, absolut. </strong><i></i>Adobe empfiehlt <strong>relativ</strong><i></i> als Standard.</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
Bei Eigenschaftsnamen wird zwischen Groß- und Kleinschreibung unterschieden. Es darf nur die Kleinschreibung verwendet werden.

**Tabelle „Farbprofile“**

Die folgenden Farbprofile werden installiert:

<table>
 <tbody>
  <tr>
   <th><p>Name</p> </th>
   <th><p>Farbraum</p> </th>
   <th><p>Beschreibung</p> </th>
  </tr>
  <tr>
   <td>Adobe RGB</td>
   <td>RGB</td>
   <td>Adobe RGB (1998)</td>
  </tr>
  <tr>
   <td>AppleRGB</td>
   <td>RGB</td>
   <td>Apple RGB</td>
  </tr>
  <tr>
   <td>CIERGB</td>
   <td>RGB</td>
   <td>CIE-RGB</td>
  </tr>
  <tr>
   <td>CoatedFogra27</td>
   <td>CMYK</td>
   <td>Coated FOGRA27 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>CoatedFogra39</td>
   <td>CMYK</td>
   <td>Coated FOGRA39 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>CoatedGraCol</td>
   <td>CMYK</td>
   <td>Coated GRACoL 2006 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>ColorMatchRGB</td>
   <td>RGB</td>
   <td>ColorMatch-RGB</td>
  </tr>
  <tr>
   <td>EuropeISOCoated</td>
   <td>CMYK</td>
   <td>Europe ISO Coated FOGRA27</td>
  </tr>
  <tr>
   <td>EuroscaleCoated</td>
   <td>CMYK</td>
   <td>Euro-Skala Coated v2</td>
  </tr>
  <tr>
   <td>EuroscaleUncoated</td>
   <td>CMYK</td>
   <td>Euro-Skala, Uncoated v2</td>
  </tr>
  <tr>
   <td>JapanColorCoated</td>
   <td>CMYK</td>
   <td>Japan Color 2001 Coated</td>
  </tr>
  <tr>
   <td>JapanColorNewspaper</td>
   <td>CMYK</td>
   <td>Japan Color 2002 Newspaper</td>
  </tr>
  <tr>
   <td>JapanColorUncoated</td>
   <td>CMYK</td>
   <td>Japan Color 2001 Uncoated</td>
  </tr>
  <tr>
   <td>JapanColorWebCoated</td>
   <td>CMYK</td>
   <td>Japan Color 2003 Web Coated</td>
  </tr>
  <tr>
   <td>JapanWebCoated</td>
   <td>CMYK</td>
   <td>Japan Web Coated (Ad)</td>
  </tr>
  <tr>
   <td>NewsprintSNAP2007</td>
   <td>CMYK</td>
   <td>US Newsprint (SNAP 2007)</td>
  </tr>
  <tr>
   <td>NTSC</td>
   <td>RGB</td>
   <td>NTSC (1953)</td>
  </tr>
  <tr>
   <td>PAL</td>
   <td>RGB</td>
   <td>PAL/SECAM</td>
  </tr>
  <tr>
   <td>ProPhoto</td>
   <td>RGB</td>
   <td>ProPhoto RGB</td>
  </tr>
  <tr>
   <td>PS4Default</td>
   <td>CMYK</td>
   <td>Photoshop 4 Standard CMYK</td>
  </tr>
  <tr>
   <td>PS5Default</td>
   <td>CMYK</td>
   <td>Photoshop 5 Standard CMYK</td>
  </tr>
  <tr>
   <td>SheetfedCoated</td>
   <td>CMYK</td>
   <td>U.S. Sheetfed Coated v2</td>
  </tr>
  <tr>
   <td>SheetfedUncoated</td>
   <td>CMYK</td>
   <td>U.S. Sheetfed Uncoated v2</td>
  </tr>
  <tr>
   <td>SMPTE</td>
   <td>RGB</td>
   <td>SMPTE-C</td>
  </tr>
  <tr>
   <td>sRGB</td>
   <td>RGB</td>
   <td>sRGB IEC61966-2.1</td>
  </tr>
  <tr>
   <td>UncoatedFogra29</td>
   <td>CMYK</td>
   <td>Uncoated FOGRA29 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>WebCoated</td>
   <td>CMYK</td>
   <td>U.S. Web Coated (SWOP) v2</td>
  </tr>
  <tr>
   <td>WebCoatedFogra28</td>
   <td>CMYK</td>
   <td>Web Coated FOGRA28 (ISO 12647-2:2004)</td>
  </tr>
  <tr>
   <td>WebCoatedGrade3</td>
   <td>CMYK</td>
   <td>Web Coated SWOP 2006 Grade 3 Paper</td>
  </tr>
  <tr>
   <td>WebCoatedGrade5</td>
   <td>CMYK</td>
   <td>Web Coated SWOP 2006 Grade 5 Paper</td>
  </tr>
  <tr>
   <td>WebUncoated</td>
   <td>CMYK</td>
   <td>U.S. Web Uncoated v2</td>
  </tr>
  <tr>
   <td>WideGamutRGB</td>
   <td>RGB</td>
   <td>Wide Gamut RGB</td>
  </tr>
 </tbody>
</table>

1. Klicken Sie auf **[!UICONTROL Alle speichern]**.

Sie können beispielsweise **[!UICONTROL iccprofilergb]** auf `sRGB` und **[!UICONTROL iccprofilecmyk]** auf **[!UICONTROL WebCoated]** festlegen.

Dies hat folgende Auswirkungen:

* Die Farbkorrektur für RGB- und CMYK-Bilder wird aktiviert.
* Für RGB-Bilder ohne Farbprofil wird angenommen, dass sie sich im Farbraum *sRGB* befinden.
* Für CMYK-Bilder ohne Farbprofil wird angenommen, dass sie sich im Farbraum *WebCoated* befinden.
* Für dynamische Ausgabedarstellungen, bei denen eine RGB-Ausgabe zurückgegeben wird, erfolgt dies im Farbraum * sRGB*.
* Für dynamische Ausgabedarstellungen, bei denen eine CMYK-Ausgabe zurückgegeben wird, erfolgt dies im Farbraum *WebCoated*.

## Bereitstellen von Assets {#delivering-assets}

Nachdem Sie alle obigen Aufgaben abgeschlossen haben, werden aktivierte Dynamic Media-Assets über den Bild- oder Videodienst bereitgestellt. In Experience Manager ist dies in einer **[!UICONTROL URL für „Bild kopieren“]**, **[!UICONTROL URL für „Viewer kopieren“]**, in **[!UICONTROL Code für die Viewer-Einbettung]** und in WCM möglich.

Siehe [Bereitstellen von Assets mit Dynamic Media](/help/assets/delivering-dynamic-media-assets.md).

<table>
 <tbody>
  <tr>
   <td><strong>Aktion</strong></td>
   <td><strong>Ergebnis</strong></td>
  </tr>
  <tr>
   <td>Kopieren einer Bild-URL</td>
   <td><p>Das Dialogfeld zum Kopieren einer URL zeigt eine URL ähnlich der folgenden an (URL dient nur zur Veranschaulichung):</p> <p><code>https://IMAGESERVICEPUBLISHNODE/is/image/content/dam/path/to/Image.jpg?$preset$</code></p> <p>Hier verweist <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Siehe auch <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Dynamic Media-Assets</a>.</p> </td>
  </tr>
  <tr>
   <td>Kopieren einer Viewer-URL</td>
   <td><p>Das Dialogfeld zum Kopieren einer URL zeigt eine URL ähnlich der folgenden an (URL dient nur zur Veranschaulichung):</p> <p><code>https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/BasicZoomViewer.html?asset=/content/dam/path/to/Image.jpg&amp;config=/conf/global/settings/dam/dm/presets/viewer/Zoom_dark&amp;serverUrl=https://IMAGESERVICEPUBLISHNODE/is/image/&amp;contentRoot=%2F</code></p> <p>Hier verweist <code>PUBLISHNODE</code> auf den regulären Veröffentlichungsknoten von Experience Manager und <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Siehe auch <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Dynamic Media-Assets</a>.</p> </td>
  </tr>
  <tr>
   <td>Kopieren von Einbettungs-Code eines Viewers</td>
   <td><p>Im Dialogfeld zum Einbetten von Code wird ein Codeschnipsel wie der folgende angezeigt (Codeschnipsel dient nur zur Veranschaulichung):</p> <p><code class="code">&lt;style type="text/css"&gt;
       #s7basiczoom_div.s7basiczoomviewer{
       width:100%;
       height:auto;
       }
       &lt;/style&gt;
       &lt;script
       type="text/javascript" src="https://PUBLISHNODE/etc/dam/viewers/s7viewers/html5/js/BasicZoomViewer.js"&gt;&lt;/script&gt;
       &lt;div id="s7basiczoom_div"&gt;&lt;/div&gt;
       &lt;script type="text/javascript"&gt;
       var s7basiczoomviewer = new s7viewers.BasicZoomViewer({
       "containerId" : "s7basiczoom_div",
       "params" : {
       "serverurl" : "https://IMAGESERVICEPUBLISHNODE/is/image/",
       "contenturl" : "https://PUBLISHNODE/",
       "config" : "/conf/global/settings/dam/dm/presets/viewer/Zoom_dark",
       "asset" : "/content/dam/path/to/Image.jpg" }
       }).init();
       &lt;/script&gt;</code></p> <p>Hier verweist <code>PUBLISHNODE</code> auf den regulären Veröffentlichungsknoten von Experience Manager und <code>IMAGESERVICEPUBLISHNODE</code> auf die Bilddienst-URL.</p> <p>Siehe auch <a href="/help/assets/delivering-dynamic-media-assets.md">Bereitstellen von Dynamic Media-Assets</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Komponenten von Dynamic Media und interaktiven Medien für WCM {#wcm-dynamic-media-and-interactive-media-components}

Auf WCM-Seiten mit Verweisen auf Komponenten von Dynamic Media und interaktiven Medien wird auf den Service für die Bereitstellung verwiesen.
