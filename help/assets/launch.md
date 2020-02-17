---
title: Integrieren von Dynamic Media-Viewern mit Adobe Analytics und Adobe Launch
description: Mit der Erweiterung für Dynamic Media-Viewer für Adobe Launch und der Dynamic Media-Viewer-Version 5.13 können Kunden von Dynamic Media, Adobe Analytics und Adobe Launch Ereignisse und Daten verwenden, die für die Dynamic Media-Viewer in ihrer Adobe Launch-Konfiguration spezifisch sind.
uuid: d218ee1c-cd2c-40c3-a3d4-b95719ae8e98
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: f4051767-182e-4cfd-9dfc-8f516378e0b6
docset: aem65
translation-type: tm+mt
source-git-commit: 0595d89409e0ca21f771be5c55c3ec9548a8449f

---


# Integrieren von Dynamic Media-Viewern mit Adobe Analytics und Adobe Launch {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Was ist die Integration von Dynamic Media Viewern mit Adobe Analytics und Adobe Launch? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

The new *Dynamic Media Viewers* extension for Adobe Launch, along with the recent release of Dynamic Media Viewers 5.13, lets customers of Dynamic Media, Adobe Analytics, and Adobe Launch to use events and data specific for the Dynamic Media Viewers in their Adobe Launch configuration.

Diese Integration bedeutet, dass Sie die Nutzung von Dynamic Media Viewern auf Ihrer Website mit Adobe Analytics verfolgen können. Gleichzeitig können Sie die von den Viewern angezeigten Ereignisse und Daten mit jeder anderen Launch-Erweiterung von Adobe oder einem Drittanbieter verwenden.

Weitere Informationen zu Erweiterungen finden Sie unter [Adobe Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/overview.html) im Experience Platform Launch-Benutzerhandbuch.

**** Zielgruppe dieser Dokumentation: Site-Administratoren, Entwickler auf der AEM-Plattform und diejenigen im Betrieb.

### Einschränkungen der Integration {#limitations-of-the-integration}

* Die Adobe Launch-Integration für Dynamic Media-Viewer funktioniert nicht im AEM-Autorenknoten. Sie können keine Verfolgung von einer WCM-Seite sehen, bis sie veröffentlicht wurde.
* Die Adobe Launch-Integration für Dynamic Media-Viewer wird nicht für den Popup-Betriebsmodus unterstützt, bei dem die Viewer-URL über die Schaltfläche &quot;URL&quot;auf der Seite &quot;Asset-Details&quot;abgerufen wird.
* Die Adobe Launch-Integration kann nicht gleichzeitig mit der Analytics-Integration älterer Viewer verwendet werden (als `config2=` Parameter).
* Die Unterstützung für die Videoverfolgung ist auf die Core-Wiedergabe-Verfolgung beschränkt, wie unter Übersicht über die [Verfolgung](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html)beschrieben. Insbesondere werden die Nachverfolgung von QoS-, Anzeigen-, Kapitel-/Segmenten- oder Fehlermeldungen nicht unterstützt.
* Die Konfiguration der Speicherdauer für Datenelemente wird für Datenelemente, die die Erweiterung *Dynamische Medien-Viewer* verwenden, nicht unterstützt. Die Speicherdauer muss auf **[!UICONTROL Keine]** eingestellt sein.

### Anwendungsfälle für die Integration {#use-cases-for-the-integration}

Der primäre Anwendungsfall für die Integration mit Adobe Launch sind Kunden, die sowohl AEM Assets als auch AEM Sites verwenden. In solchen Fällen können Sie eine Standardintegration zwischen Ihrem AEM-Autorenknoten und Adobe Launch einrichten und dann Ihre Sites-Instanz mit der Adobe Launch-Eigenschaft verknüpfen. Danach verfolgt jede zu einer Siteseite hinzugefügte dynamische Medien-WCM-Komponente Daten und Ereignisse von Viewern.

Siehe [Informationen zum Verfolgen von Viewern für dynamische Medien in AEM-Sites](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersinAEMSites).

Ein sekundärer Anwendungsfall, den die Integration unterstützt, sind Kunden, die nur AEM Assets oder Dynamic Media Classic verwenden. In solchen Fällen können Sie den Einbettungscode für Ihren Viewer abrufen und ihn der Website-Seite hinzufügen. Rufen Sie dann die Produktions-URL der Adobe Launch-Bibliothek von Adobe Launch ab und fügen Sie sie manuell zum Webseitencode hinzu.

Siehe [Informationen zum Verfolgen von Viewern für dynamische Medien mit Einbettungscode](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode).

## Funktionsweise der Daten- und Ereignisverfolgung in der Integration {#how-data-and-event-tracking-works-in-the-integration}

Die Integration nutzt zwei separate und unabhängige Typen der Verfolgung dynamischer Medien-Viewer: *Adobe Analytics* und *Adobe Analytics für Audio und Video*.

### Informationen zur Verfolgung mit Adobe Analytics {#about-tracking-using-adobe-analytics}

Mit Adobe Analytics können Sie Aktionen verfolgen, die vom Endbenutzer bei der Interaktion mit dynamischen Medien-Viewern auf Ihrer Website ausgeführt werden. Mit Adobe Analytics können Sie außerdem Viewer-spezifische Daten verfolgen. Beispielsweise können Sie Ladereignisse der Ansicht zusammen mit dem Asset-Namen, eingetretene Zoomaktionen, Videowiedergabeaktionen usw. verfolgen und aufzeichnen.

In Adobe Launch arbeiten die Konzepte der *Datenelemente* und *Regeln* zusammen, um die Adobe Analytics-Verfolgung zu aktivieren.

#### Info zu Datenelementen in Adobe Launch {#about-data-elements-in-adobe-launch}

Ein Datenelement in Adobe Launch ist eine benannte Eigenschaft, deren Wert entweder statisch definiert oder basierend auf dem Status einer Webseite oder dynamischer Medien-Viewer-Daten dynamisch berechnet wird.

Optionen, die für eine Datenelementdefinition verfügbar sind, hängen von der Liste der Erweiterungen ab, die in der Adobe Launch-Eigenschaft installiert sind. Die Erweiterung &quot;Core&quot;ist vorinstalliert und ist in jeder Konfiguration standardmäßig verfügbar. Mit dieser &quot;Core&quot;-Erweiterung können Sie ein Datenelement definieren, das aus Cookies, JavaScript-Code, Abfragezeichenfolge und vielen anderen Quellen stammt.

Zur Verfolgung von Adobe Analytics müssen mehrere zusätzliche Erweiterungen installiert werden, wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions)beschrieben. Die Erweiterung &quot;Dynamic Media Viewer&quot;bietet die Möglichkeit, ein Datenelement zu definieren, das ein Argument des Ereignisses &quot;Dynamischer Viewer&quot;ist. Beispielsweise können Sie auf den Viewer-Typ oder den Asset-Namen verweisen, der vom Viewer beim Laden gemeldet wird, auf den Zoomgrad, der beim Zoomen des Endbenutzers gemeldet wird, und vieles mehr.

Die Erweiterung des dynamischen Media Viewers hält die Werte seiner Datenelemente automatisch auf dem neuesten Stand.

Nachdem Sie es definiert haben, kann ein Datenelement an anderen Stellen der Adobe Launch-Benutzeroberfläche mit dem Widget zur Auswahl von Datenelementen verwendet werden. Insbesondere wird auf Datenelemente, die für die Verfolgung von Dynamischen Medien-Viewern definiert wurden, in der Regel unter Aktion &quot;Variablen festlegen&quot;der Adobe Analytics-Erweiterung verwiesen (siehe unten).

Weitere Informationen finden Sie unter [Datenelemente](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html) im Experience Platform Launch-Benutzerhandbuch.

#### Regeln in Adobe Launch {#about-rules-in-adobe-launch}

Eine Regel in Adobe Launch ist eine agnostische Konfiguration, die drei Bereiche definiert, aus denen eine Regel besteht: *Ereignisse*, *Bedingungen* und *Aktionen*:

* *Ereignisse* (falls) teilen Adobe Launch mit, wann eine Regel ausgelöst werden soll.
* *Bedingungen* (falls) teilen Adobe Launch mit, welche zusätzlichen Einschränkungen beim Auslösen einer Regel zulässig oder nicht zulässig sind.
* *Aktionen* (dann) teilen Adobe Launch mit, was zu tun ist, wenn eine Regel ausgelöst wird.

Die im Abschnitt &quot;Ereignisse&quot;, &quot;Bedingungen&quot;und &quot;Aktionen&quot;verfügbaren Optionen hängen von den Erweiterungen ab, die in der Adobe Launch-Eigenschaft installiert sind. Die *Core* Extension ist vorinstalliert und ist in jeder Konfiguration standardmäßig verfügbar. Die Erweiterung bietet mehrere Optionen für Ereignisse, wie zum Beispiel grundlegende Aktionen auf Browserebene, die Fokusänderung, Tastendruck, Formularübermittlung usw. umfassen. Es enthält auch Optionen für Bedingungen, wie z. B. Cookie-Wert, Browsertyp und mehr. Für Aktionen steht nur die Option Benutzerdefinierter Code zur Verfügung.

Für die Adobe Analytics-Verfolgung müssen mehrere zusätzliche Erweiterungen installiert werden, wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions)beschrieben. Insbesondere:

* Die Erweiterung &quot;Dynamische Medien-Viewer&quot;erweitert die Liste der unterstützten Ereignisse auf Ereignisse, die für Dynamische Medien-Viewer spezifisch sind, z. B. Laden des Viewers, Austauschen von Assets, Vergrößern und Abspielen von Videos.
* Die Adobe Analytics-Erweiterung erweitert die Liste der unterstützten Aktionen um zwei Aktionen, die zum Senden von Daten an Tracking-Server erforderlich sind: Variablen *einstellen* und Beacon *senden*.

Zur Verfolgung von Viewern für dynamische Medien ist es möglich, einen der folgenden Typen zu verwenden:

* Ereignisse aus der Erweiterung &quot;Dynamic Media Viewer&quot;, der Core-Erweiterung oder einer anderen Erweiterung.
* Bedingungen in der Regeldefinition. Oder Sie können den Bedingungsbereich leer lassen.

Im Abschnitt Aktionen müssen Sie über die Aktion *Variablen* festlegen verfügen. Diese Aktion teilt Adobe Analytics mit, wie Verfolgungsvariablen mit Daten aufgefüllt werden. Gleichzeitig sendet die Aktion *&quot;Variablen* festlegen&quot;nichts an den Tracking-Server.

Auf die Aktion *&quot;Variablen* festlegen&quot;muss eine *Beacon* -Aktion folgen. Die Aktion *Beacon* senden sendet Daten tatsächlich an den Analytics-Tracking-Server. Beide Aktionen, *&quot;Variablen* festlegen&quot;und &quot;Beacon *senden&quot;*, stammen aus der Adobe Analytics-Erweiterung.

Weitere Informationen finden Sie unter [Regeln](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/rules.html) im Benutzerhandbuch zum Starten der Erlebnisplattform.

#### Beispielkonfiguration {#sample-configuration}

Die folgende Beispielkonfiguration in Adobe Launch zeigt, wie ein Asset-Name beim Laden des Viewers verfolgt wird.

1. Definieren Sie auf der Registerkarte &quot; **[!UICONTROL Datenelemente]** &quot;ein Datenelement, `AssetName` das auf den `asset` Parameter des `LOAD` Ereignisses in der Erweiterung &quot;Dynamische Medienansichten&quot;verweist.

   ![image2019-11](assets/image2019-11.png)

1. Definieren Sie auf der Registerkarte **[!UICONTROL Regeln]** eine Regel *TrackAssetOnLoad*.

   In dieser Regel verwendet das Feld &quot; **[!UICONTROL Ereignis]** &quot;das **[!UICONTROL LOAD]** -Ereignis aus der Erweiterung &quot;Dynamic Media Viewer&quot;.

   ![image2019-22](assets/image2019-22.png)

1. Die Aktionskonfiguration umfasst zwei Aktionstypen aus der Adobe Analytics-Erweiterung:

   *Legen Sie Variablen* fest, die eine Analytics-Variable Ihrer Wahl dem Wert des `AssetName` Datenelements zuordnen.

   *Beacon* senden, der Verfolgungsinformationen an Adobe Analytics sendet.

   ![image2019-3](assets/image2019-3.png)

1. Die resultierende Regelkonfiguration sieht wie folgt aus:

   ![image2019-4](assets/image2019-4.png)

### Info zu Adobe Analytics für Audio und Video {#about-adobe-analytics-for-audio-and-video}

Wenn ein Experience Cloud-Konto für die Verwendung von Adobe Analytics für Audio und Video abonniert wird, reicht es aus, die Videoverfolgung in den Erweiterungseinstellungen für *Dynamic Media-Viewer* zu aktivieren. Videometriken werden in Adobe Analytics verfügbar. Die Videoverfolgung hängt von der Adobe Media Analytics for Audio and Video Extension ab.

Siehe [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions).

Derzeit ist die Unterstützung für die Videoverfolgung auf die &quot;Core-Wiedergabe&quot;-Verfolgung beschränkt, wie in Übersicht über die [Verfolgung](https://docs.adobe.com/content/help/en/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html)beschrieben. Insbesondere werden die Nachverfolgung von QoS-, Anzeigen-, Kapitel-/Segmenten- oder Fehlermeldungen nicht unterstützt.

## Verwenden der Erweiterung &quot;Dynamic Media Viewer&quot; {#using-the-dynamic-media-viewers-extension}

Wie unter [Anwendungsfälle für die Integration](#use%20cases%20for%20the%20integration)erwähnt, ist es möglich, dynamische Medien-Viewer mit der neuen Adobe Launch-Integration in AEM-Sites und mithilfe von Einbettungscode zu verfolgen.

### Verfolgen von Viewern für dynamische Medien in AEM-Sites {#tracking-dynamic-media-viewers-in-aem-sites}

Zur Verfolgung von Viewern für dynamische Medien in AEM-Sites müssen alle Schritte ausgeführt werden, die im Abschnitt [Konfigurieren aller Integrationselemente](#configuring-all-the-integration-pieces) aufgeführt sind. Insbesondere müssen Sie die IMS-Konfiguration und die Adobe Launch Cloud-Konfiguration erstellen.

Nach ordnungsgemäßer Konfiguration verfolgt jeder Viewer für dynamische Medien, den Sie einer Seite &quot;Sites&quot;mithilfe einer von dynamischen Medien unterstützten WCM-Komponente hinzufügen, automatisch Daten in Adobe Analytics oder Adobe Analytics für Video oder beides.

Siehe [Hinzufügen dynamischer Medienelemente zu Seiten mithilfe von Adobe-Sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).

### Verfolgen von Viewern für dynamische Medien mit Einbettungscode {#tracking-dynamic-media-viewers-using-embed-code}

Kunden, die keine AEM-Sites verwenden oder Dynamic Media-Viewer in Webseiten außerhalb von AEM-Sites oder beides einbetten, können weiterhin die Adobe Launch-Integration verwenden.

Sie müssen die Konfigurationsschritte im Abschnitt [Konfigurieren von Adobe Analytics](#configuringadobeanalytics) und [Konfigurieren von Adobe Launch](#configuringadobelaunch) ausführen. AEM-bezogene Konfigurationsschritte sind jedoch nicht erforderlich.

Nach der richtigen Konfiguration können Sie Adobe Launch-Unterstützung zu einer Webseite mit einem Dynamic Media Viewer hinzufügen.

Weitere Informationen zur Verwendung des Einbettungscodes der Adobe Launch-Bibliothek finden Sie unter Einbettungscode[ ](https://docs.adobe.com/content/help/en/launch/using/implement/configure/implement-the-launch-install-code.html)hinzufügen.

Weitere Informationen zur Verwendung der Einbettungscode-Funktion von AEM Dynamic Media finden Sie unter [Einbetten des Video- oder Bild-Viewers auf einer Webseite](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) .

**So verfolgen Sie dynamische Medien-Viewer mit Einbettungscode**:

1. Verwenden Sie eine Webseite, die zum Einbetten eines Viewers für dynamische Medien bereit ist.
1. Rufen Sie den Einbettungscode für die Adobe Launch-Bibliothek ab, indem Sie sich zuerst bei Adobe Launch anmelden (siehe Adobe Launch [konfigurieren](#configuringadobelaunch)).
1. Klicken Sie auf **[!UICONTROL Eigenschaft]** und dann auf die Registerkarte **[!UICONTROL Umgebungen]** .
1. Nehmen Sie die für die Umgebung der Webseite relevante Umgebungsebene auf. Klicken Sie dann in der Spalte **[!UICONTROL Installieren]** auf das Kontrollkästchen.
1. **[!UICONTROL Kopieren Sie im Dialogfeld &quot;Webinstallationsanweisungen]** &quot;den vollständigen Einbettungscode der Adobe Launch-Bibliothek zusammen mit den zugehörigen `<script/>` -Tags.

## Referenzhandbuch für die Erweiterung &quot;Dynamic Media Viewer&quot; {#reference-guide-for-the-dynamic-media-viewers-extension}

### Konfiguration der Viewer für dynamische Medien {#about-the-dynamic-media-viewers-configuration}

Die Erweiterung für den dynamischen Media Viewer wird automatisch in die Adobe Launch-Bibliothek integriert, wenn alle folgenden Bedingungen erfüllt sind:

* Das globale Objekt ( `_satellite`) der Adobe Launch-Bibliothek befindet sich auf der Seite.
* Die Erweiterungsfunktion für dynamische Medien-Viewer `_dmviewers_v001()` ist für definiert `_satellite`.

* `config2=` Der Viewer-Parameter wurde nicht angegeben. Das bedeutet, dass der Viewer keine ältere Analytics-Integration verwendet.

Darüber hinaus gibt es eine Option, um die Adobe Launch-Integration im Viewer explizit zu deaktivieren, indem `launch=0` Parameter in der Viewer-Konfiguration angegeben werden. The default value of this parameter is `1`.

### Konfigurieren der Erweiterung &quot;Dynamic Media Viewer&quot; {#configuring-the-dynamic-media-viewers-extension}

Die einzige Konfigurationsoption für die Erweiterung &quot;Dynamische Medien-Viewer&quot;ist &quot;Adobe Media Analytics für Audio und Video **[!UICONTROL aktivieren&quot;]**.

Wenn Sie diese Option aktivieren (aktivieren oder aktivieren) und wenn die Adobe Media Analytics for Audio and Video-Erweiterung installiert und ordnungsgemäß konfiguriert ist, werden die Videoverspielungsmetriken an die Adobe Analytics for Audio and Video-Lösung gesendet. Durch Deaktivieren dieser Option wird die Videoverfolgung deaktiviert.

Wenn Sie diese Option aktivieren, *ohne* die Adobe Media Analytics for Audio and Video Extension installiert zu haben, hat diese Option keine Auswirkungen.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Datenelemente in der Erweiterung &quot;Dynamic Media Viewer&quot; {#about-data-elements-in-the-dynamic-media-viewers-extension}

Der einzige Datenelementtyp, den die Erweiterung &quot;Dynamische Medien-Viewer&quot;bietet, ist das **[!UICONTROL Viewer-Ereignis]** aus der Dropdownliste &quot; **[!UICONTROL Datenelementtyp]** &quot;.

Wenn diese Option aktiviert ist, rendert der Datenelement-Editor ein Formular mit zwei Feldern:

* **[!UICONTROL DM-Viewer-Ereignistyp]** - eine Dropdown-Liste, die alle Viewer-Ereignisse identifiziert, die von der Erweiterung &quot;Dynamic Media Viewer&quot;unterstützt werden und Argumente sowie ein spezielles **[!UICONTROL COMMON]** -Element enthalten. Ein **[!UICONTROL COMMON]** -Element stellt eine Liste von Ereignisparametern dar, die für alle vom Viewer gesendeten Ereignistypen gelten.
* **[!UICONTROL Tracking-Parameter]** - ein Argument des ausgewählten Dynamic Media-Viewer-Ereignisses.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Eine Liste der unterstützten Ereignisse nach Viewer-Typ finden Sie im Referenzhandbuch[ zu ](https://marketing.adobe.com/resources/help/en_US/s7/viewers_ref/c_html5_s7_aem_asset_viewers.html)Dynamischen Medien-Viewern. Rufen Sie den Abschnitt zu einem bestimmten Viewer auf und klicken Sie dann auf Support für Adobe Analytics-Tracking-Unterabschnitt. Derzeit dokumentiert das Referenzhandbuch für dynamische Medien-Viewer keine Ereignisargumente.

Betrachten wir nun den Lebenszyklus des *Datenelements*&quot;Dynamic Media Viewer&quot;. Der Wert dieses Datenelements wird aufgefüllt, nachdem das entsprechende Ereignis des dynamischen Medien-Viewers auf der Seite eintritt. Wenn das Datenelement beispielsweise auf das **[!UICONTROL LOAD]** -Ereignis und dessen &quot;asset&quot;-Argument verweist, erhält der Wert dieses Datenelements gültige Daten, nachdem der Viewer das LOAD-Ereignis zum ersten Mal ausführt. Wenn das Datenelement auf das **[!UICONTROL ZOOM]** -Ereignis und das zugehörige &quot;scale&quot;-Argument verweist, bleibt der Wert dieses Datenelements leer, bis der Viewer ein **[!UICONTROL ZOOM]** -Ereignis zum ersten Mal sendet.

Gleichermaßen werden die Werte von Datenelementen automatisch aktualisiert, wenn der Viewer ein entsprechendes Ereignis auf der Seite sendet. Die Wertaktualisierung erfolgt auch dann, wenn das betreffende Ereignis nicht in der Regelkonfiguration angegeben ist. Wenn beispielsweise für den Parameter &quot;scale&quot;des ZOOM-Ereignisses der Parameter &quot;Data Element **[!UICONTROL ZoomScale]** &quot;definiert ist, die einzige in der Regelkonfiguration vorhandene Regel jedoch vom **[!UICONTROL LOAD]** -Ereignis ausgelöst wird, wird der Wert von &quot; **[!UICONTROL ZoomScale]** &quot;immer noch aktualisiert, wenn ein Benutzer im Viewer Zoom ausführt.

Jeder Viewer für dynamische Medien verfügt über eine eindeutige Kennung auf der Webseite. Das Datenelement verfolgt den Wert selbst und den Viewer, der den Wert ausgefüllt hat. Das bedeutet, dass bei mehreren Viewern auf derselben Seite, die ein **[!UICONTROL AssetName]** -Datenelement enthalten, das auf das **[!UICONTROL LOAD]** -Ereignis und das &quot;Asset&quot;-Argument verweist, das **[!UICONTROL AssetName]** -Datenelement eine Sammlung von Asset-Namen beibehält, die mit jedem auf der Seite geladenen Viewer verknüpft sind.

Der genaue vom Datenelement zurückgegebene Wert hängt vom Kontext ab. Wenn das Datenelement in einer Regel angefordert wird, die durch ein Ereignis des Viewers für dynamische Medien ausgelöst wurde, wird der Datenelementwert für den Viewer zurückgegeben, der die Regel initiiert hat. Wenn das Datenelement in einer Regel angefordert wird, die durch ein Ereignis aus einer anderen Adobe Launch-Erweiterung ausgelöst wurde, dann ist der Wert des Datenelements der Wert des Viewers, der als letzter dieses Datenelement aktualisiert hat.

**Betrachten Sie die folgenden Beispielsätze**:

* eine Webseite mit zwei Dynamischen Medien-Zoom-Viewern; werden sie als *Viewer1* und *Viewer2* bezeichnet.

* **[!UICONTROL Das ZoomScale]** -Datenelement verweist auf das **[!UICONTROL ZOOM]** -Ereignis und das zugehörige &quot;scale&quot;-Argument.
* **[!UICONTROL TrackPan]** -Regel mit folgenden Eigenschaften:

   * Verwendet das **[!UICONTROL PAN]** -Ereignis des dynamischen Media Viewers als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]** -Datenelements an Adobe Analytics.

* 
   * **[!UICONTROL TrackKey]** -Regel mit folgenden Eigenschaften:

   * Verwendet das Tastenpressereignis der Core Adobe Launch Extension als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]** -Datenelements an Adobe Analytics.

Nehmen Sie jetzt an, dass der Endbenutzer die Webseite mit den beiden Viewern lädt. In *Viewer1* wird der Skalierungsgrad auf 50 % heranzoomen. In *Viewer2* zoomen sie dann auf die Skala von 25 %. In *Viewer1* schwenken sie das Bild herum und drücken schließlich eine Taste auf der Tastatur.

Die Aktivität des Endbenutzers führt dazu, dass die folgenden zwei Verfolgungsaufrufe an Adobe Analytics gesendet werden:

* Der erste Aufruf erfolgt, weil die **[!UICONTROL TrackPan]** -Regel ausgelöst wird, wenn sich der Benutzer in *viewer1* verschiebt. Dieser Aufruf sendet 50 % als Wert des **[!UICONTROL ZoomScale]** -Datenelements, da das Datenelement weiß, dass die Regel von *viewer1* ausgelöst wird, und den entsprechenden Skalierungswert abrufen.
* Der zweite Aufruf erfolgt, weil die **[!UICONTROL TrackKey]** -Regel ausgelöst wird, wenn der Benutzer eine Taste auf der Tastatur drückt. Bei diesem Aufruf werden 25 % als Wert des **[!UICONTROL ZoomScale]** -Datenelements gesendet, da die Regel nicht vom Viewer ausgelöst wurde. Daher gibt das Datenelement den aktuellsten Wert zurück.

Das oben aufgestellte Beispiel wirkt sich auch auf die Lebensdauer des Datenelementwerts aus. Der Wert des vom Dynamic Media Viewer verwalteten Datenelements wird im Adobe Launch-Bibliothekscode gespeichert, auch wenn der Viewer selbst auf der Webseite abgelegt wird. Wenn es also eine Regel gibt, die von einer nicht dynamischen Media Viewer-Erweiterung ausgelöst wird und auf ein solches Datenelement verweist, gibt das Datenelement den letzten bekannten Wert zurück, selbst wenn der Viewer nicht mehr auf der Webseite vorhanden ist.

In jedem Fall werden Werte von Datenelementen, die von dynamischen Medienansichten gesteuert werden, nicht im lokalen Speicher oder auf dem Server gespeichert. Sie werden stattdessen nur in der clientseitigen Adobe Launch-Bibliothek gespeichert. Die Werte dieser Datenelemente verschwinden, wenn die Webseite neu geladen wird.

Im Allgemeinen unterstützt der Datenelement-Editor die Auswahl der [Speicherdauer](https://docs.adobe.com/content/help/en/launch/using/reference/manage-resources/data-elements.html#create-a-data-element). Datenelemente, die die Erweiterung &quot;Dynamische Medien-Viewer&quot;verwenden, unterstützen jedoch nur die Option für die Speicherdauer **[!UICONTROL Keine]**. Das Festlegen eines anderen Werts ist in der Benutzeroberfläche möglich, in diesem Fall wird jedoch das Verhalten des Datenelements nicht definiert. Die Erweiterung verwaltet den Wert des Datenelements selbst: das Datenelement, das den Wert des Viewer-Ereignisargument während des gesamten Lebenszyklus des Viewers beibehält.

### Regeln in der Erweiterung &quot;Dynamic Media Viewer&quot; {#about-rules-in-the-dynamic-media-viewers-extension}

Im Regeleditor werden mit der Erweiterung neue Konfigurationsoptionen für den Ereigniseditor hinzugefügt. Darüber hinaus bietet die Funktion eine Option zum manuellen Verweisen auf Ereignisparameter im Action-Editor als Kurzoption, anstatt vorkonfigurierte Datenelemente zu verwenden.

#### Informationen zum Ereigniseditor {#about-the-events-editor}

Im Ereigniseditor wird mit der Erweiterung &quot;Dynamische Medien-Viewer&quot;ein neuer **[!UICONTROL Ereignistyp]** namens **[!UICONTROL Viewer-Ereignis]** hinzugefügt.

Wenn diese Option aktiviert ist, rendert der Ereigniseditor die Dropdown- **[!UICONTROL Ereignisse]** des dynamischen Media Viewers und listet alle verfügbaren Ereignisse auf, die von Viewern für dynamische Medien unterstützt werden.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### Informationen zum Aktionseditor {#about-the-actions-editor}

Mit der Erweiterung &quot;Dynamische Medien-Viewer&quot;können Sie Ereignisparameter von Dynamischen Medien-Viewern verwenden, um Analytics-Variablen im Editor &quot;Variablen festlegen&quot;der Adobe Analytics-Erweiterung zuzuordnen.

Die einfachste Methode hierfür besteht darin, den folgenden zweistufigen Vorgang abzuschließen:

* Definieren Sie zunächst ein oder mehrere Datenelemente, bei denen jedes Datenelement einen Parameter eines dynamischen Media Viewer-Ereignisses darstellt.
* Klicken Sie schließlich im Editor &quot;Variablen festlegen&quot;der Adobe Analytics-Erweiterung auf das Symbol für die Datenelement-Auswahl (drei gestapelte Festplatten), um das Dialogfeld &quot;Datenelement auswählen&quot;zu öffnen, und wählen Sie dann ein Datenelement aus.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Es ist jedoch möglich, einen alternativen Ansatz zu verwenden und die Erstellung von Datenelementen zu umgehen. Sie können direkt auf ein Argument aus einem Dynamic Media Viewer-Ereignis verweisen, indem Sie den vollständig qualifizierten Namen des Ereignisarguments in das **[!UICONTROL Werteingabefeld]** der Analytics-Variablenzuweisung eingeben, umgeben von Prozentzeichen (%). Beispiel:

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

Beachten Sie, dass es einen wichtigen Unterschied zwischen der Verwendung von Datenelementen und der Referenz zu direkten Ereignissen gibt. Bei Datenelementen spielt es keine Rolle, welches Ereignis die Aktion &quot;Variablen festlegen&quot;auslöst. Das Ereignis, das die Regel auslöst, kann nicht mit dem dynamischen Viewer in Zusammenhang stehen (wie ein Mausklick auf die Webseite aus der Core-Erweiterung). Bei Verwendung eines direkten Argumentverweises muss jedoch sichergestellt werden, dass das Ereignis, das die Regel auslöst, dem Ereignisargument entspricht, auf das sie verweist.

Wenn Sie beispielsweise auf &quot;Verweisen&quot;verweisen, `%event.detail.dm.LOAD.asset%` wird der richtige Asset-Name zurückgegeben, wenn die Regel durch das **[!UICONTROL LOAD]** -Ereignis der Dynamischen Media Viewer-Erweiterung ausgelöst wird. Für jedes andere Ereignis wird jedoch ein leerer Wert zurückgegeben.

In der folgenden Tabelle sind die Ereignisse des dynamischen Media Viewers und die unterstützten Argumente aufgeführt:

<table>
 <tbody>
  <tr>
   <td>Name des Viewer-Ereignisses</td>
   <td>Argument</td>
  </tr>
  <tr>
   <td><code>COMMON</code></td>
   <td><code>%event.detail.dm.objID%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.compClass%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.instName%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.timeStamp%</code></td>
  </tr>
  <tr>
   <td><code>BANNER</code> </td>
   <td><code>%event.detail.dm.BANNER.asset%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.BANNER.label%</code></td>
  </tr>
  <tr>
   <td><code>HREF</code></td>
   <td><code>%event.detail.dm.HREF.rollover%</code></td>
  </tr>
  <tr>
   <td><code>ITEM</code></td>
   <td><code>%event.detail.dm.ITEM.rollover%</code></td>
  </tr>
  <tr>
   <td><code>LOAD</code></td>
   <td><code>%event.detail.dm.LOAD.applicationname%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.asset%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.company%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.sdkversion%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewertype%</code></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><code>%event.detail.dm.LOAD.viewerversion%</code></td>
  </tr>
  <tr>
   <td><code>METADATA</code></td>
   <td><code>%event.detail.dm.METADATA.length%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.METADATA.type%</code></td>
  </tr>
  <tr>
   <td><code>MILESTONE</code></td>
   <td><code>%event.detail.dm.MILESTONE.milestone%</code></td>
  </tr>
  <tr>
   <td><code>PAGE</code></td>
   <td><code>%event.detail.dm.PAGE.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.PAGE.label%</code></td>
  </tr>
  <tr>
   <td><code>PAUSE</code></td>
   <td><code>%event.detail.dm.PAUSE.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>PLAY</code></td>
   <td><code>%event.detail.dm.PLAY.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SPIN</code></td>
   <td><code>%event.detail.dm.SPIN.framenumber%</code></td>
  </tr>
  <tr>
   <td><code>STOP</code></td>
   <td><code>%event.detail.dm.STOP.timestamp%</code></td>
  </tr>
  <tr>
   <td><code>SWAP</code></td>
   <td><code>%event.detail.dm.SWAP.asset%</code></td>
  </tr>
  <tr>
   <td><code>SWATCH</code></td>
   <td><code>%event.detail.dm.SWATCH.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.SWATCH.label%</code></td>
  </tr>
  <tr>
   <td><code>TARG</code></td>
   <td><code>%event.detail.dm.TARG.frame%</code></td>
  </tr>
  <tr>
   <td> </td>
   <td><code>%event.detail.dm.TARG.label%</code></td>
  </tr>
  <tr>
   <td><code>ZOOM</code></td>
   <td><code>%event.detail.dm.ZOOM.scale%</code></td>
  </tr>
 </tbody>
</table>

## Konfigurieren aller Integrationselemente {#configuring-all-the-integration-pieces}

**BEVOR SIE BEGINNEN**

Wenn Sie dies noch nicht getan haben, empfiehlt Adobe, dass Sie die gesamte Dokumentation vor diesem Abschnitt gründlich überprüfen, damit Sie die vollständige Integration verstehen.

In diesem Abschnitt werden die Konfigurationsschritte erläutert, die zur Integration von Viewern für dynamische Medien in Adobe Analytics und Adobe Analytics für Audio und Video erforderlich sind. Obwohl die Erweiterung &quot;Dynamic Media Viewer&quot;für andere Zwecke in Adobe Launch verwendet werden kann, werden solche Szenarien in dieser Dokumentation nicht behandelt.

Sie konfigurieren die Integration in den folgenden Adobe-Produkten:

* Adobe Analytics - Sie konfigurieren Verfolgungsvariablen und Berichte.
* Adobe Launch - Sie definieren eine Eigenschaft, eine oder mehrere Regeln und ein oder mehrere Datenelemente, um die Viewer-Verfolgung zu aktivieren.

Wenn diese Integrationslösung mit AEM-Sites verwendet wird, muss außerdem die folgende Konfiguration durchgeführt werden:

* Adobe I/O Console - Integration für Adobe Launch erstellt.
* AEM-Autorenknoten - IMS-Konfiguration und Adobe Launch-Cloud-Konfiguration.

Vergewissern Sie sich, dass Sie im Rahmen der Konfiguration Zugriff auf ein Unternehmen in Adobe Experience Cloud haben, für das Adobe Analytics und Adobe Launch bereits aktiviert sind.

## Konfigurieren von Adobe Analytics für die Integration {#configuring-adobe-analytics-for-the-integration}

Nach der Konfiguration von Adobe Analytics wird Folgendes für die Integration eingerichtet:

* Eine Report Suite wurde eingerichtet und ausgewählt.
* Analytics-Variablen stehen zum Empfang von Verfolgungsdaten zur Verfügung.
* Berichte stehen zur Ansicht der erfassten Daten in Adobe Analytics zur Verfügung.

Siehe auch [Analytics-Implementierungshandbuch](https://docs.adobe.com/content/help/en/analytics/implementation/home.html).

**So konfigurieren Sie Adobe Analytics für die Integration**:

1. Starten Sie den Zugriff auf Adobe Analytics über die Experience Cloud- [Homepage](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/). Klicken Sie in der Menüleiste auf das Symbol Lösungen (eine Tabelle mit drei Punkten) oben rechts auf der Seite und klicken Sie dann auf **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   Jetzt wählen Sie eine Report Suite aus.

### Selecting a report suite {#selecting-a-report-suite}

1. Wählen Sie rechts oben auf der Seite &quot;Adobe Analytics&quot;rechts neben dem Feld &quot; **[!UICONTROL Suchberichte]** &quot;die richtige Report Suite aus der Dropdownliste. Wenn mehrere Report Suites verfügbar sind und Sie sich nicht sicher sind, welche verwendet werden soll, wenden Sie sich an Ihren Adobe Analytics-Administrator, der Ihnen bei der Auswahl der zu verwendenden Report Suite helfen kann.

   In unten stehender Abbildung hat ein Benutzer eine Report Suite mit dem Namen *DynamicMediaViewersExtensionDoc* erstellt und aus der Dropdownliste ausgewählt. Der Name der Report Suite dient nur zur Veranschaulichung. Der Name der Report Suite, die Sie letztendlich auswählen, unterscheidet sich.

   Wenn keine Report Suite verfügbar ist, müssen Sie oder Ihr Adobe Analytics-Administrator eine erstellen, bevor Sie mit der Konfiguration fortfahren können.

   Siehe [Berichte und Report Suites](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/ref-reports-report-suites.html) und [Erstellen einer Report Suite](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/create-report-suite.html).

   In Adobe Analytics werden Report Suites unter **[!UICONTROL Admin > Report Suites]** verwaltet.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   Sie richten jetzt Adobe Analytics-Variablen ein.

### Einrichten von Adobe Analytics-Variablen {#setting-up-adobe-analytics-variables}

1. Sie bestimmen jetzt eine oder mehrere Adobe Analytics-Variablen, die Sie zur Verfolgung des Verhaltens von dynamischen Medien-Viewern auf der Webseite verwenden möchten.

   Es ist möglich, alle Variablentypen zu verwenden, die von Adobe Analytics unterstützt werden. Die Entscheidung über den Variablentyp (z. B. Custom Traffic- [Props], Konversions- [eVar]) sollte von spezifischen Anforderungen Ihrer Analytics-Implementierung bestimmt werden.

   Siehe [Übersicht über Props und eVars](https://docs.adobe.com/content/help/en/analytics/implementation/analytics-basics/traffic-props-evars/props-evars.html).

   Für die Zwecke dieser Dokumentation wird nur eine Eigenschaftsvariable (Custom Traffic) verwendet, da sie in einem Analytics-Bericht innerhalb weniger Minuten nach dem Auftreten einer Aktion auf einer Webseite verfügbar ist.

   Um eine neue Custom Traffic-Variable zu aktivieren, klicken Sie in Adobe Analytics in der Symbolleiste auf **[!UICONTROL Admin > Report Suites]**.

1. Wählen Sie auf der Seite **[!UICONTROL Report Suite Manager]** den richtigen Bericht aus und klicken Sie dann auf der Symbolleiste auf Einstellungen **[!UICONTROL bearbeiten > Traffic > Traffic-Variablen]**.
1. Hier können Sie nicht verwendete Variablen aufrufen, ihr einen beschreibenden Namen geben ( **[!UICONTROL Viewer-Asset (prop 30)]**) und das Kombinationsfeld in der Spalte &quot;Aktiviert&quot;in &quot;Aktiviert&quot;ändern.

   Der folgende Screenshot ist ein Beispiel für eine Custom Traffic-Variable ( **[!UICONTROL prop30]**) zur Verfolgung eines vom Viewer verwendeten Asset-Namens:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Klicken Sie unten in der Variablenliste auf **[!UICONTROL Speichern]**.

### Setting up a report {#setting-up-a-report}

1. Im Allgemeinen wird die Einrichtung eines Berichts in Adobe Analytics von bestimmten Projektanforderungen bestimmt. Die Einrichtung detaillierter Berichte ist daher für diese Integration nicht relevant.

   Es ist jedoch ausreichend zu wissen, dass die Berichte zum benutzerdefinierten Traffic automatisch in Adobe Analytics verfügbar werden, nachdem Sie unter **[Einrichten von Adobe Analytics-Variablen](#setting-up-adobe-analytics-variables)**benutzerdefinierte Traffic-Variablen eingerichtet haben.

   Beispielsweise ist die Variable &quot;Bericht für **[!UICONTROL Viewer-Asset&quot;(prop 30)]** im Menü &quot;Berichte&quot;unter &quot; **[!UICONTROL Benutzerspezifischer Traffic&quot;> &quot;Benutzerspezifischer Traffic 21-30&quot;> &quot;Viewer-Asset&quot;(prop 30)]** verfügbar.

   Beim Besuch dieses Berichts direkt nach der Erstellung des **[!UICONTROL Viewer-Assets (prop 30)]** werden keine Daten angezeigt. zu diesem Zeitpunkt bei der Integration erwartet wird.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Konfigurieren von Adobe Launch für die Integration {#configuring-adobe-launch-for-the-integration}

Nachdem Sie Adobe Launch konfiguriert haben, wird für die Integration Folgendes eingerichtet:

* Die Erstellung einer neuen Eigenschaft, um alle Konfigurationen zusammenzuhalten.
* Installation und Einrichtung von Erweiterungen. Der clientseitige Code aller in der Eigenschaft installierten Erweiterungen wird in einer Bibliothek kompiliert. Diese Bibliothek wird später von der Webseite verwendet.
* Konfiguration von Datenelementen und Regeln. Diese Konfiguration definiert, welche Daten von den Viewern für dynamische Medien erfasst werden sollen, wann die Verfolgungslogik ausgelöst werden soll und wo die Daten des Viewers in Adobe Analytics gesendet werden sollen.
* Veröffentlichen der Bibliothek.

**Konfigurieren von Adobe Launch für die Integration**:

1. Starten Sie den Zugriff auf Adobe Launch über die Experience Cloud- [Homepage](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/). Klicken Sie in der Menüleiste auf das Symbol Lösungen (drei x drei Punkte) in der oberen rechten Ecke der Seite und dann auf **[!UICONTROL Starten]**.

   Sie können Adobe Launch auch direkt [öffnen](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Erstellen einer Eigenschaft in Adobe Launch {#creating-a-property-in-adobe-launch}

Bei einer Eigenschaft in Adobe Launch handelt es sich um eine benannte Konfiguration, die alle Einstellungen zusammenhält. Eine Bibliothek der Konfigurationseinstellungen wird erstellt und auf verschiedenen Umgebungsebenen (Entwicklung, Staging und Produktion) veröffentlicht.

Siehe auch Eigenschaft [erstellen](https://docs.adobe.com/content/help/en/launch/using/implement/configure/create-a-property.html).

1. Klicken Sie in Adobe Launch auf **[!UICONTROL Neue Eigenschaft]**.
1. Geben Sie im Dialogfeld Eigenschaft **** erstellen im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein, z. B. den Titel Ihrer Website. Beispiel: `DynamicMediaViewersProp.`
1. Geben Sie im Feld **[!UICONTROL Domänen]** die Domäne Ihrer Website ein.
1. Aktivieren Sie in der Dropdown-Liste &quot; **[!UICONTROL Erweiterte Optionen]** &quot;die Option &quot; **[!UICONTROL Konfigurieren für die Erweiterungsentwicklung&quot;(kann später nicht geändert werden)]** , falls die gewünschte Erweiterung - in diesem Fall *Dynamic Media Viewer*- noch nicht veröffentlicht ist.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Klicken Sie auf die neu erstellte Eigenschaft und fahren Sie dann mit der *Installation und Einrichtung von Erweiterungen* fort.

### Installieren und Einrichten von Erweiterungen {#installing-and-setup-of-extensions}

Alle verfügbaren Erweiterungen in Adobe Launch werden unter **[!UICONTROL Erweiterungen > Katalog]** aufgeführt.

Um eine Erweiterung zu installieren, klicken Sie auf **[!UICONTROL Installieren]**. Führen Sie bei Bedarf eine einmalige Erweiterungskonfiguration durch und klicken Sie dann auf **[!UICONTROL Speichern]**.

Erforderlichenfalls müssen die folgenden Erweiterungen installiert und konfiguriert werden:

* (Erforderlich) *Experience Cloud ID-Dienst *Erweiterung

Es ist keine zusätzliche Konfiguration erforderlich, akzeptieren Sie die vorgeschlagenen Werte. Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Speichern]**.

Siehe [Experience Cloud ID-Diensterweiterung](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/id-service-extension/overview.html).

* (Erforderlich) *Adobe Analytics* -Erweiterung

Um diese Erweiterung zu konfigurieren, benötigen Sie zunächst die Report Suite-ID in Adobe Analytics unter **[!UICONTROL Admin > Report Suite]** unter der Spaltenüberschrift **[!UICONTROL Report Suite-ID]** .

(Nur zu Demonstrationszwecken wird die Report Suite-ID der Report Suite **[!UICONTROL DynamicMediaViewersExtensionDoc]** Report Suite in den folgenden Screenshots verwendet. Diese ID wurde erstellt und bei der [Auswahl einer Report Suite](#selecting-a-report-suite) zuvor verwendet.)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Geben Sie auf der Seite &quot;Erweiterung installieren&quot;die Report Suite-ID in das Feld **[!UICONTROL Entwicklungs-Report Suites]** , das Feld **[!UICONTROL Staging Report Suites]** und das Feld **[!UICONTROL Produktions-Report Suites]** ein.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Konfigurieren Sie das folgende Element nur, wenn Sie die Videoverfolgung verwenden möchten:*

Erweitern Sie auf der Seite **[!UICONTROL Install Extension]** den Eintrag **[!UICONTROL General]** und geben Sie dann den Tracking-Server an. Der Tracking-Server folgt der Vorlage `<trackingNamespace>.sc.omtrdc.net`und `<trackingNamespace>` enthält die in der Bereitstellungs-E-Mail abgerufenen Informationen.

Klicken Sie auf **[!UICONTROL Speichern]**.

Siehe [Adobe Analytics Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/analytics-extension/overview.html).

* (Optional) nur erforderlich, wenn Videoverfolgung erforderlich ist) *Adobe Media Analytics für Audio- und Video* -Erweiterung

Füllen Sie das Feld für den Tracking-Server aus. Der Tracking-Server für die Erweiterung *Adobe Media Analytics für Audio und Video* unterscheidet sich von dem für Adobe Analytics verwendeten Tracking-Server. Es folgt der Vorlage `<trackingNamespace>.hb.omtrdc.net`und `<trackingNamespace>` enthält die Informationen aus der Bereitstellungs-E-Mail.

Alle anderen Felder sind optional.

Siehe [Adobe Media Analytics for Audio and Video Extension](https://docs.adobe.com/content/help/en/launch/using/extensions-ref/adobe-extension/media-analytics-extension/overview.html).

* (Erforderlich) Erweiterung *für Viewer* für dynamische Medien

Wählen Sie Adobe Analytics für Video **** aktivieren, um die Video Heartbeat-Verfolgung zu aktivieren (aktivieren).

Beachten Sie, dass zum Zeitpunkt der Erstellung die Erweiterung &quot; *Dynamic Media Viewer* &quot;nur verfügbar ist, wenn die Adobe Launch-Eigenschaft für die Entwicklung erstellt wurde.

Siehe [Erstellen einer Eigenschaft in Adobe Launch](#creating-a-property-in-adobe-launch).

Nachdem die Erweiterungen installiert und eingerichtet wurden, werden mindestens die folgenden fünf Erweiterungen (vier, wenn Sie kein Video verfolgen) im Bereich Erweiterungen > Installiert aufgeführt.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Einrichten von Datenelementen und Regeln {#setting-up-data-elements-and-rules}

Erstellen Sie in Adobe Launch Datenelemente und Regeln, die zur Verfolgung von Viewern für dynamische Medien erforderlich sind.

Eine Übersicht über die Verfolgung mit Adobe Launch finden Sie unter [Funktionsweise der Daten- und Ereignisverfolgung in der Integration](#how-data-and-event-tracking-works-in-the-integration) .

Unter [Beispielkonfiguration](#sample-configuration) finden Sie eine Beispielkonfiguration in Adobe Launch, die zeigt, wie ein Asset-Name beim Laden des Viewers verfolgt wird.

Detaillierte Informationen zu den Funktionen der Erweiterung finden Sie unter Dynamische Medien-Viewer [konfigurieren](#configuring-the-dynamic-media-viewers-extension) .

### Veröffentlichen einer Bibliothek {#publishing-a-library}

Um Änderungen an der Adobe Launch-Konfiguration vorzunehmen (einschließlich Eigenschaften, Erweiterungen, Regeln und Datenelemente einrichten), müssen Sie diese Änderungen *veröffentlichen* *.* Die Veröffentlichung in Adobe Launch erfolgt über die Registerkarte &quot;Veröffentlichen&quot;unter der Eigenschaftenkonfiguration.

Adobe Launch verfügt möglicherweise über mehrere Entwicklungsumgebungen, eine Staging-Umgebung und eine Produktionsumgebung. Standardmäßig verweist die Adobe Launch Cloud-Konfiguration in AEM den AEM-Autorenknoten auf die Stage-Umgebung von Adobe Launch und den AEM-Veröffentlichungsknoten auf die Produktionsumgebung von Adobe Launch. Diese Vorgehensweise bedeutet, dass mit den AEM-Standardeinstellungen die Adobe Launch-Bibliothek in der Staging-Umgebung veröffentlicht werden muss, damit sie in AEM-Autor verwendet werden kann, und sie dann in der Produktionsumgebung veröffentlichen muss, damit sie in AEM veröffentlicht werden kann.

Weitere Informationen zu Adobe Launch-Umgebungen finden Sie unter [Umgebungen](https://docs.adobe.com/content/help/en/launch/using/reference/publish/environments.html) .

Das Veröffentlichen einer Bibliothek umfasst die folgenden zwei Schritte:

* Hinzufügen und Erstellen einer neuen Bibliothek, indem alle erforderlichen Änderungen (neue und Aktualisierungen) in die Bibliothek aufgenommen werden.
* Verschieben der Bibliothek durch die verschiedenen Umgebungsebenen (von &quot;Entwicklung&quot;zu &quot;Staging&quot;und &quot;Produktion&quot;)

#### Hinzufügen und Erstellen einer neuen Bibliothek {#adding-and-building-a-new-library}

1. Wenn Sie die Registerkarte &quot;Veröffentlichung&quot;zum ersten Mal in Adobe Launch öffnen, ist die Bibliotheksliste leer.

   Klicken Sie in der linken Spalte auf Neue Bibliothek **[!UICONTROL hinzufügen]**.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. Geben Sie auf der Seite &quot;Neue Bibliothek erstellen&quot;im Feld &quot; **[!UICONTROL Name]** &quot;einen beschreibenden Namen für die neue Bibliothek ein. Beispiel:

   *DynamicMediaViewersLib*

   Wählen Sie in der Dropdownliste Umgebung die Umgebungsebene aus. Zunächst steht nur die Entwicklungsstufe zur Auswahl zur Verfügung. Klicken Sie unten links auf der Seite auf Alle geänderten Ressourcen **[!UICONTROL hinzufügen]**.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. Near the upper-right corner of the page, click **[!UICONTROL Save &amp; Build for Development]**.

   In wenigen Minuten wird die Bibliothek erstellt und einsatzbereit.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >Wenn Sie das nächste Mal Änderungen an Ihrer Adobe Launch-Konfiguration vornehmen, wechseln Sie zur Registerkarte **[!UICONTROL Veröffentlichung]** unter der Konfiguration **[!UICONTROL Eigenschaft]** und klicken Sie dann auf Ihre zuvor erstellte Bibliothek.
   >
   >
   >Klicken Sie im Anzeigebereich &quot;Bibliotheksveröffentlichung&quot;auf Alle geänderten Ressourcen **[!UICONTROL hinzufügen]** und klicken Sie dann auf **[!UICONTROL Speichern &amp; Erstellen für Entwicklung]**.

#### Verschieben einer Bibliothek durch Umgebungsebenen {#moving-a-library-up-through-environment-levels}

1. Nachdem eine neue Bibliothek hinzugefügt wurde, befindet sie sich zunächst in der Entwicklungsumgebung. Um sie auf die Ebene der Staging-Umgebung (die der Spalte &quot;Gesendet&quot;entspricht) zu verschieben, klicken Sie im Dropdown-Menü der Bibliothek auf **[!UICONTROL Zur Genehmigung]**&#x200B;übermitteln.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Senden]**.

   Nachdem die Bibliothek in die Spalte &quot;Gesendet&quot;verschoben wurde, klicken Sie im Dropdown-Menü der Bibliothek auf &quot; **[!UICONTROL Für Staging]** erstellen&quot;.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Führen Sie einen ähnlichen Vorgang aus, um die Bibliothek aus der Staging-Umgebung in die Produktionsumgebung zu verschieben (die Spalte &quot;Veröffentlicht&quot;).

   Klicken Sie zunächst im Dropdown-Menü auf **[!UICONTROL Genehmigung für Veröffentlichung]**.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Klicken Sie im Dropdownmenü auf **[!UICONTROL Erstellen und Veröffentlichen in Produktion]**.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Weitere Informationen zum Veröffentlichungsprozess in Adobe Launch finden Sie unter [Veröffentlichen](https://docs.adobe.com/content/help/en/launch/using/reference/publish/overview.html) .

## Konfigurieren von Adobe Experience Manager für die Integration {#configuring-adobe-experience-manager-for-the-integration}

Voraussetzungen:

* AEM führt die Autoren- und die Veröffentlichungsinstanz aus.
* Der AEM-Autorenknoten wird im Modus &quot;Dynamische Medien - Scene7-Ausführung&quot;eingerichtet (dynamicmedia_s7)
* WCM-Komponenten für dynamische Medien sind in AEM-Sites aktiviert.

Die AEM-Konfiguration besteht aus den folgenden zwei Hauptschritten:

* Konfiguration von AEM IMS.
* Konfiguration von Adobe Launch Cloud.

### Konfigurieren von AEM IMS {#configuring-aem-ims}

1. Klicken Sie in AEM-Autor auf das Symbol Werkzeuge (Hammer) und dann auf **[!UICONTROL Sicherheit > Adobe IMS-Konfigurationen]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Klicken Sie auf der Seite &quot;Adobe IMC-Konfiguration&quot;links oben auf **[!UICONTROL Erstellen]**.
1. Klicken Sie auf der Seite **[!UICONTROL Adobe IMS Technical Account Configuration]** in der Dropdownliste **[!UICONTROL Cloud Solution]** auf **[!UICONTROL Adobe Launch]**.
1. Aktivieren Sie **[!UICONTROL Neues Zertifikat]** erstellen und geben Sie dann in das Textfeld einen beliebigen aussagekräftigen Wert für das Zertifikat ein. Beispiel: *AdobeLaunchIMSCert*. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**.

   Die folgende Infomeldung wird angezeigt:

   *Um ein gültiges Zugriffstoken abzurufen, muss der öffentliche Schlüssel des neuen Zertifikats dem technischen Konto auf Adobe I/O hinzugefügt werden!*.

   Click **[!UICONTROL OK]** to dismiss the Info dialog box.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Klicken Sie auf Öffentlichen Schlüssel **[!UICONTROL herunterladen]** , um eine öffentliche Schlüsseldatei (*.crt) auf Ihr lokales System herunterzuladen.

   >[!NOTE]
   >
   >Öffnen Sie ***jetzt*** die Seite &quot;Konfiguration **[!UICONTROL des technischen]** Adobe IMS-Kontos&quot;. Schließen Sie die Seite ***nicht*** und ***klicken Sie nicht*** auf Weiter. Sie kehren später in den Schritten zu dieser Seite zurück.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. Navigieren Sie auf einer neuen Browser-Registerkarte zur [Adobe-E/A-Konsole](https://console.adobe.io/integrations).

1. Klicken Sie auf der Seite &quot; **[!UICONTROL Adobe-E/A-Konsolenintegrationen]** &quot;rechts oben auf **[!UICONTROL Neue Integration]**.
1. Vergewissern Sie sich, dass im Dialogfeld &quot;Neue Integration **** erstellen&quot;das Optionsfeld &quot; **[!UICONTROL Zugriff auf eine API]** &quot;ausgewählt ist, und klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Aktivieren Sie auf der zweiten Seite &quot; **[!UICONTROL Neue Integration]** erstellen&quot;die Optionsschaltfläche &quot; **[!UICONTROL Experience Platform Launch API]** &quot;(Aktivieren). In the lower-right corner of the page, click **[!UICONTROL Continue]**.

   ![2019-07-25_13-13-54](assets/2019-07-25_13-13-54.png)

1. Gehen Sie auf der dritten Seite &quot; **[!UICONTROL Neue Integration]** erstellen&quot;wie folgt vor:

   * Geben Sie im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein. Beispielsweise *DynamicMediaViewersIO*.

   * Geben Sie im Feld **[!UICONTROL Beschreibung]** eine Beschreibung für die Integration ein.

   * Laden Sie im Bereich &quot; **[!UICONTROL Public-Key-Zertifikate]** &quot;Ihre öffentliche Schlüsseldatei (*.crt) hoch, die Sie zuvor in diesen Schritten heruntergeladen haben.

   * Wählen Sie unter der Überschrift Rolle für Experience Platform Launch API **** auswählen die Option **[!UICONTROL Admin]**.

   * Wählen Sie unter der Überschrift **[!UICONTROL Select one or more product profiles for Experience Platform Launch API]** das Produktprofil **[!UICONTROL Launch - &lt;your_company_name>]**.
   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Click **[!UICONTROL Create integration]**.
1. Klicken Sie auf der Seite **[!UICONTROL Integration erstellt]** auf **[!UICONTROL Weiter zu den Integrationsdetails]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Es wird eine Seite mit Integrationsdetails angezeigt, ****ähnlich der folgenden:

   >[!NOTE]
   >
   >***Lassen Sie die Seite*** Integrationsdetails geöffnet. In wenigen Augenblicken benötigen Sie verschiedene Informationen aus den Registerkarten **[!UICONTROL Übersicht]** und **[!UICONTROL JWT]** .

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Integrationsdetails angezeigt.

1. Kehren Sie zur Seite &quot;Konfiguration **[!UICONTROL des technischen]** Adobe IMS-Kontos&quot;zurück, die Sie zuvor geöffnet haben. Klicken Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Weiter]** , um die Seite &quot; **[!UICONTROL Konto]** &quot;im Fenster &quot;Technische Kontokonfiguration **[!UICONTROL von]** Adobe IMS&quot;zu öffnen.

   (Wenn Sie die Seite versehentlich zuvor geschlossen haben, kehren Sie zu AEM-Autor zurück und klicken Sie dann auf **[!UICONTROL Tools > Sicherheit > Adobe IMS-Konfigurationen]**. Klicken Sie auf **[!UICONTROL Erstellen]**. Wählen Sie in der Dropdownliste **[!UICONTROL Cloud-Lösung]** die Option **[!UICONTROL Adobe Launch]**. Wählen Sie in der Dropdownliste **[!UICONTROL Zertifikat]** den Namen des zuvor erstellten Zertifikats aus.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Technische Kontokonfiguration für Adobe IMS - Zertifikatsseite.

1. Die Seite &quot; **[!UICONTROL Konto]** &quot;enthält fünf Felder, in denen Sie Informationen aus der Seite &quot;Integrationsdetails&quot;des vorherigen Schritts ausfüllen müssen.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Technische Konfiguration des Adobe IMS-Kontos - Kontoseite.

1. Füllen Sie auf der Seite &quot; **[!UICONTROL Konto]** &quot;die folgenden Felder aus:

   * **[!UICONTROL Titel]** - Geben Sie einen beschreibenden Kontonamen ein.
   * **[!UICONTROL Autorisierungsserver]** : Kehren Sie zur Seite mit den Integrationsdetails zurück, die Sie zuvor geöffnet haben. Click the **[!UICONTROL JWT]** tab. Kopieren Sie den Servernamen - ohne Pfad - wie unten hervorgehoben.
   Kehren Sie zur Seite &quot; **[!UICONTROL Konto]** &quot;zurück und fügen Sie dann den Namen in das entsprechende Feld ein.
Beispiel: `https://ims-na1.adobelogin.com/`(Der Beispielservername dient nur zur Veranschaulichung)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Seite mit Integrationsdetails - Registerkarte &quot;JWT&quot;

1. **[!UICONTROL API-Schlüssel]** - Kehren Sie zur Seite Integrationsdetails zurück. Klicken Sie auf die Registerkarte **[!UICONTROL Übersicht]** und dann rechts neben dem Feld **[!UICONTROL API-Schlüssel (Client-ID)]** auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Schlüssel in das entsprechende ****Feld ein.

   ![2019-07-25_14-35-333](assets/2019-07-25_14-35-333.png)

   Integrationsdetails angezeigt.

1. **[!UICONTROL geheimer Clientschlüssel]**: Kehren Sie zur Seite &quot;Integrationsdetails&quot;zurück. Klicken Sie auf der Registerkarte &quot; **[!UICONTROL Übersicht]** &quot;auf **[!UICONTROL Clientgeheimnis abrufen]**. Klicken Sie rechts neben dem **[!UICONTROL geheimen]** Feld &quot;Client&quot;auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Schlüssel in das entsprechende Feld ein.

1. **[!UICONTROL Nutzlast]** - Kehren Sie zur Seite Integrationsdetails zurück. Kopieren Sie auf der Registerkarte **[!UICONTROL JWT]** im Feld JWT Payload den gesamten JSON-Objektcode.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Code in das entsprechende Feld ein.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Seite mit Integrationsdetails - Registerkarte &quot;JWT&quot;

   Die Kontoseite mit allen ausgefüllten Feldern sieht wie folgt aus:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. Near the upper-right corner of the **[!UICONTROL Account]** page, click **[!UICONTROL Create]**.

   Wenn AEM IMS konfiguriert ist, befindet sich jetzt ein neues IMSAaccount unter **[!UICONTROL Adobe IMS-Konfigurationen]**.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Adobe Launch Cloud für die Integration konfigurieren {#configuring-adobe-launch-cloud-for-the-integration}

1. Klicken Sie in AEM-Autor in der oberen linken Ecke auf das Symbol Werkzeuge (Hammer) und dann auf **[!UICONTROL Cloud Services > Adobe Launch Configurations]**.

   ![2019-07-26_12-10-38](assets/2019-07-26_12-10-38.png)

1. Wählen Sie auf der Seite &quot; **[!UICONTROL Adobe-Startkonfigurationen]** &quot;im linken Bereich eine AEM-Site aus, für die Sie Ihre Adobe-Startkonfiguration anwenden möchten.

   Nur zur Veranschaulichung wird die **[!UICONTROL We.Retail]** Site im folgenden Screenshot ausgewählt.

   ![2019-07-26_12-20-06](assets/2019-07-26_12-20-06.png)

1. Klicken Sie links oben auf der Seite auf **[!UICONTROL Erstellen]**.
1. Füllen Sie auf der Seite &quot; **[!UICONTROL Allgemein]** &quot;(1/3 Seiten) des Fensters &quot;Adobe Launch Configuration **** erstellen&quot;die folgenden Felder aus:

   * **[!UICONTROL Titel]** - Geben Sie einen beschreibenden Konfigurationstitel ein. Beispiel, `We.Retail Launch cloud configuration`.

   * **[!UICONTROL Zugeordnete Adobe IMS-Konfiguration]** - Wählen Sie die IMS-Konfiguration, die Sie zuvor unter [Konfigurieren von AEM IMS](#configuring-aem-ims)erstellt haben.

   * **[!UICONTROL Unternehmen]** - Wählen Sie aus der Dropdownliste **[!UICONTROL Unternehmen]** Ihr Experience Cloud-Unternehmen aus. Die Liste wird automatisch ausgefüllt.

   * **[!UICONTROL Eigenschaft]** : Wählen Sie in der Dropdownliste Eigenschaft die zuvor erstellte Adobe Launch-Eigenschaft aus. Die Liste wird automatisch ausgefüllt.
   Nachdem Sie alle Felder ausgefüllt haben, sieht Ihre **[!UICONTROL Allgemeine]** Seite wie folgt aus:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Klicken Sie links oben auf **[!UICONTROL Weiter]**.
1. Füllen Sie auf der Seite **[!UICONTROL Staging]** (2/3 Seiten) des Fensters Adobe Launch Configuration **** erstellen das folgende Feld aus:

   Überprüfen Sie im Feld **[!UICONTROL Bibliotheks-URI]** den Speicherort der Staging-Version Ihrer Adobe Launch-Bibliothek. AEM füllt dieses Feld automatisch aus.

   Nur zu Veranschaulichungszwecken werden in diesem Schritt Adobe Launch-Bibliotheken verwendet, die in Adobe CDN bereitgestellt werden.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der automatisch ausgefüllte Bibliotheks-URI (Uniform Resource Identifier) nicht fehlerhaft ist. Korrigieren Sie diese ggf. so, dass der URI einen protokollrelativen URI darstellt. Das heißt, es beginnt mit einem doppelten Schrägstrich.
   >
   >
   >Beispiel: `//assets.adobetm.com/launch-xxxx`.

   Ihre **[!UICONTROL Staging]** -Seite sollte wie folgt aussehen: Beachten Sie, dass die Optionen **[!UICONTROL Archiv]** und Bibliothek asynchron **[!UICONTROL laden]** nicht ****** festgelegt sind:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Weiter]**.
1. Korrigieren Sie auf der Seite &quot; **[!UICONTROL Produktion]** &quot;(3/3 Seiten) des Fensters &quot;Adobe Launch Configuration **[!UICONTROL erstellen&quot;bei Bedarf den automatisch ausgefüllten Produktions-URI, ähnlich wie auf der vorherigen]** Staging ****-Seite.
1. Klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Erstellen]**.

   Ihre neue Adobe Launch Cloud-Konfiguration wird jetzt erstellt und neben Ihrer Website aufgelistet, ähnlich dem folgenden Beispiel:

   ![]()

1. Wählen Sie Ihre neue Adobe Launch Cloud-Konfiguration aus (bei Auswahl wird links neben dem Konfigurationstitel ein Häkchen angezeigt). Klicken Sie in der Symbolleiste auf **[!UICONTROL Publish]**.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

Derzeit unterstützt AEM-Autor nicht die Integration von Dynamic Media Viewern mit Adobe Launch.

Sie wird jedoch vom AEM-Veröffentlichungsknoten unterstützt. Unter Verwendung der Standardeinstellungen der Adobe Launch Cloud-Konfiguration verwendet AEM-Veröffentlichung die Produktionsumgebung von Adobe Launch. Daher müssen Adobe Launch-Bibliotheksaktualisierungen während des Tests immer von der Entwicklungsumgebung in die Produktionsumgebung verschoben werden.

Sie können diese Einschränkung umgehen, indem Sie die Entwicklungs- oder Staging-URL der Adobe Launch-Bibliothek in der oben stehenden Adobe Launch Cloud-Konfiguration für AEM-Veröffentlichung angeben. Dadurch verwendet der AEM-Veröffentlichungsknoten die Entwicklungs- oder Staging-Version der Adobe Launch-Bibliothek.

Weitere Informationen zum Einrichten der Adobe Launch Cloud-Konfiguration finden Sie unter AEM mit Adobe Launch über Adobe I/O[ ](https://helpx.adobe.com/experience-manager/using/aem_launch_adobeio_integration.html)integrieren.
