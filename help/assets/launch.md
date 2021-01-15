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
source-git-commit: 0560eb8e3c127964920827609a9982acf07b515f
workflow-type: tm+mt
source-wordcount: '6596'
ht-degree: 94%

---


# Integrieren von Dynamic Media-Viewern mit Adobe Analytics und Adobe Launch {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Worum geht es bei der Integration von Dynamic Media-Viewern mit Adobe Analytics und Adobe Launch? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

Mit der Erweiterung für *Dynamic Media-Viewer* für Adobe Launch und der neuen Dynamic Media-Viewer-Version 5.13 können Kunden von Dynamic Media, Adobe Analytics und Adobe Launch Ereignisse und Daten verwenden, die für die Dynamic Media-Viewer in ihrer Adobe Launch-Konfiguration spezifisch sind.

Diese Integration sorgt dafür, dass Sie die Nutzung von Dynamic Media-Viewern auf Ihrer Website mit Adobe Analytics verfolgen können. Gleichzeitig können Sie die von den Viewern angezeigten Ereignisse und Daten mit jeder anderen Launch-Erweiterung von Adobe oder einem anderen Drittanbieter verwenden.

Weitere Informationen zu Erweiterungen finden Sie unter [Adobe-Erweiterung](https://experienceleague.adobe.com/docs/launch/using/extensions-ref/overview.html#adobe-extension) im Experience Platform Launch-Benutzerhandbuch.

**Zielgruppe dieser Dokumentation:** Site-Administratoren, Entwickler, die auf der AEM-Plattform entwickeln, und Betriebsexperten.

### Einschränkungen der Integration {#limitations-of-the-integration}

* Die Adobe Launch-Integration für Dynamic Media-Viewer funktioniert nicht im AEM-Autorenmodus. Sie können keine Verfolgung einer WCM-Seite anzeigen, bis diese veröffentlicht wurde.
* Die Adobe Launch-Integration für Dynamic Media-Viewer wird im Popup-Betriebsmodus, bei dem die Viewer-URL über die Schaltfläche „URL“ auf der Seite „Asset-Details“ abgerufen wird, nicht unterstützt.
* Die Adobe Launch-Integration kann nicht gleichzeitig mit der Analytics-Integration älterer Viewer verwendet werden (mit dem Parameter `config2=`).
* Die Unterstützung für die Videoverfolgung ist auf die &quot;Core-Wiedergabe&quot;-Verfolgung beschränkt, wie unter [Tracking-Übersicht](https://experienceleague.adobe.com/docs/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html#player-events) beschrieben. Insbesondere wird die Verfolgung von QoS, Anzeigen, Kapiteln/Segmenten oder Fehlern nicht unterstützt.
* Die Konfiguration der Speicherdauer für Datenelemente wird bei Datenelementen, die die Erweiterung *Dynamic Media-Viewer* verwenden, nicht unterstützt. Die Speicherdauer muss auf **[!UICONTROL Ohne]** eingestellt sein.

### Anwendungsbeispiele für die Integration {#use-cases-for-the-integration}

Das primäre Anwendungsbeispiel für die Integration mit Adobe Launch sind Kunden, die sowohl AEM Assets als auch AEM Sites verwenden. In solchen Fällen können Sie eine Standardintegration zwischen Ihrem AEM-Autorenknoten und Adobe Launch einrichten und dann Ihre Sites-Instanz mit der Adobe Launch-Eigenschaft verknüpfen. Danach verfolgt jede Dynamic Media-WCM-Komponente, die einer Sites-Seite hinzugefügt wird, Daten und Ereignisse von Viewern.

Siehe [Informationen zum Verfolgen von Dynamic Media-Viewern in AEM Sites](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersinAEMSites).

Ein sekundäres Anwendungsbeispiel, das die Integration unterstützt, sind Kunden, die nur AEM Assets oder Dynamic Media Classic verwenden. In solchen Fällen können Sie den Einbettungs-Code für Ihren Viewer abrufen und der Web-Seite hinzufügen. Rufen Sie dann die Produktions-URL der Adobe Launch-Bibliothek aus Adobe Launch ab und fügen Sie sie manuell zum Web-Seiten-Code hinzu.

Siehe [Informationen zum Verfolgen von Dynamic Media-Viewern mit Einbettungs-Code](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode).

## Funktionsweise der Daten- und Ereignisverfolgung in der Integration {#how-data-and-event-tracking-works-in-the-integration}

Die Integration nutzt zwei separate und unabhängige Typen der Verfolgung von Dynamic Media-Viewern: *Adobe Analytics* und *Adobe Analytics for Audio and Video*.

### Informationen zum Tracking mit Adobe Analytics {#about-tracking-using-adobe-analytics}

Mit Adobe Analytics können Sie Aktionen verfolgen, die vom Endbenutzer bei der Interaktion mit Dynamic Media-Viewern auf Ihrer Website ausgeführt werden. Mit Adobe Analytics können Sie außerdem Viewer-spezifische Daten verfolgen. Beispielsweise können Sie Ladeereignisse der Ansicht zusammen mit dem Asset-Namen, vorgenommenen Zoom-Aktionen, Videowiedergabeaktionen usw. verfolgen und aufzeichnen.

In Adobe Launch arbeiten die Konzepte *Datenelemente* und *Regeln* zusammen, um die Adobe Analytics-Verfolgung zu erlauben.

#### Informationen zu Datenelementen in Adobe Launch {#about-data-elements-in-adobe-launch}

Ein Datenelement in Adobe Launch ist eine benannte Eigenschaft, deren Wert entweder statisch definiert ist oder basierend auf dem Status einer Web-Seite bzw. von Media-Viewer-Daten dynamisch berechnet wird.

Optionen, die für eine Datenelementdefinition verfügbar sind, hängen von der Liste der Erweiterungen ab, die in der Adobe Launch-Eigenschaft installiert sind. Die Erweiterung „Core“ ist vorinstalliert und in jeder Konfiguration standardmäßig verfügbar. Mit dieser Erweiterung „Core“ können Sie ein Datenelement definieren, dessen Wert aus Cookies, JavaScript-Code, Abfragezeichenfolgen und vielen anderen Quellen stammen kann.

Für das Tracking mit Adobe Analytics müssen mehrere zusätzliche Erweiterungen installiert werden, wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions) beschrieben. Die Erweiterung „Dynamic Media-Viewer“ bietet die Möglichkeit, ein Datenelement zu definieren, dessen Wert ein Argument des Dynamic Media-Viewer-Ereignisses ist. Beispielsweise können Sie auf den Viewer-Typ oder den Asset-Namen, der vom Viewer beim Laden gemeldet wird, auf den Zoom-Faktor, der beim Zoomen durch Endbenutzer gemeldet wird, und vieles mehr verweisen.

Die Erweiterung „Dynamic Media-Viewer“ sorgt dafür, dass die Werte der Datenelemente automatisch auf dem neuesten Stand sind.

Nachdem Sie ein Datenelement definiert haben, können Sie es an anderen Stellen der Adobe Launch-Benutzeroberfläche verwenden. Nutzen Sie dazu das Widget zur Auswahl von Datenelementen. Insbesondere wird von der Aktion „Variablen festlegen“ der Adobe Analytics-Erweiterung in Regel auf Datenelemente verwiesen, die für die Verfolgung von Dynamic Media-Viewern definiert werden (siehe unten).

Weitere Informationen dazu finden Sie unter [Datenelemente](https://experienceleague.adobe.com/docs/launch/using/reference/manage-resources/data-elements.html#reference) im Experience Platform Launch-Benutzerhandbuch.

#### Regeln in Adobe Launch {#about-rules-in-adobe-launch}

Eine Regel in Adobe Launch ist eine agnostische Konfiguration, die drei Bereiche definiert, aus denen eine Regel besteht: *Ereignisse*, *Bedingungen* und *Aktionen*:

* *Ereignisse*: (wenn) teilen Adobe Launch mit, wann eine Regel ausgelöst werden soll.
* *Bedingungen*: (wenn) teilen Adobe Launch mit, welche zusätzlichen Einschränkungen beim Auslösen einer Regel zulässig oder nicht zulässig sind.
* *Aktionen*: (dann) teilen Adobe Launch mit, was zu tun ist, wenn eine Regel ausgelöst wird.

Die im Abschnitt „Ereignisse“, „Bedingungen“ und „Aktionen“ verfügbaren Optionen hängen von den Erweiterungen ab, die in der Adobe Launch-Eigenschaft installiert sind. Die Erweiterung *Core* ist vorinstalliert und in jeder Konfiguration standardmäßig verfügbar. Die Erweiterung bietet verschiedene Optionen für Ereignisse, wie zum Beispiel grundlegende Aktionen auf der Browser-Ebene, inklusive Fokuswechsel, Tastendruck, Formularübermittlung usw. Sie enthält zudem Optionen für Bedingungen, wie z. B. Cookie-Wert, Browser-Typ und mehr. Für Aktionen steht nur die Option „Benutzerspezifischer Code“ zur Verfügung.

Für das Tracking mit Adobe Analytics müssen mehrere zusätzliche Erweiterungen installiert werden, wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions) beschrieben. Insbesondere gilt:

* Die Erweiterung „Dynamic Media-Viewer“ erweitert die Liste der unterstützten Ereignisse auf Ereignisse, die für Dynamic Media-Viewer spezifisch sind, z. B. Laden des Viewers, Austauschen von Assets, Vergrößern und Abspielen von Videos.
* Die Adobe Analytics-Erweiterung erweitert die Liste der unterstützten Aktionen um zwei Aktionen, die zum Senden von Daten an Tracking-Server erforderlich sind: *Variablen festlegen* und *Beacon senden*.

Bei der Verfolgung von Dynamic Media-Viewern ist es möglich, einen der folgenden Typen zu verwenden:

* Ereignisse aus der Erweiterung „Dynamic Media-Viewer“, der Core-Erweiterung oder einer anderen Erweiterung.
* Bedingungen in der Regeldefinition. Alternativ können Sie den Bedingungsbereich leer lassen.

Im Abschnitt „Aktionen“ müssen Sie über die Aktion *Variablen festlegen* verfügen. Diese Aktion teilt Adobe Analytics mit, wie Tracking-Variablen mit Daten ausgefüllt werden. Gleichzeitig sendet die Aktion *Variablen festlegen* nichts an den Tracking-Server.

Auf die Aktion *Variablen festlegen* muss eine Aktion vom Typ *Beacon senden* folgen. Mit der Aktion *Beacon senden* werden tatsächlich Daten an den Analytics-Tracking-Server gesendet. Beide Aktionen (*Variablen festlegen* und *Beacon senden*) kommen aus der Adobe Analytics-Erweiterung.

Weitere Informationen finden Sie unter [Regeln](https://experienceleague.adobe.com/docs/launch/using/reference/manage-resources/rules.html#reference) im Experience Platform Launch-Benutzerhandbuch.

#### Beispielkonfiguration {#sample-configuration}

Die folgende Beispielkonfiguration in Adobe Launch zeigt, wie sich ein Asset-Name beim Laden des Viewers verfolgen lässt.

1. Definieren Sie auf der Registerkarte **[!UICONTROL Datenelemente]** ein Datenelement `AssetName`, das auf den `asset`-Parameter des `LOAD`-Ereignisses in der Erweiterung „Dynamic Media-Viewer“ verweist.

   ![image2019-11](assets/image2019-11.png)

1. Definieren Sie auf der Registerkarte **[!UICONTROL Regeln]** eine Regel für *TrackAssetOnLoad*.

   In dieser Regel verwendet das Feld **[!UICONTROL Ereignis]** das **[!UICONTROL LOAD]**-Ereignis aus der Erweiterung „Dynamic Media-Viewer“.

   ![image2019-22](assets/image2019-22.png)

1. Die Aktionskonfiguration umfasst zwei Aktionstypen aus der Adobe Analytics-Erweiterung:

   *Variablen festlegen*, wodurch eine Analytics-Variable Ihrer Wahl dem Wert des Datenelements `AssetName` zugeordnet wird;

   *Beacon senden*, wodurch Tracking-Daten an Adobe Analytics gesendet werden.

   ![image2019-3](assets/image2019-3.png)

1. Die daraus resultierende Regelkonfiguration sieht wie folgt aus:

   ![image2019-4](assets/image2019-4.png)

### Informationen zu Adobe Analytics for Audio and Video {#about-adobe-analytics-for-audio-and-video}

Wenn für die Verwendung von Adobe Analytics for Audio and Video ein Experience Cloud-Konto abonniert wird, reicht es, in den Einstellungen der Erweiterung *Dynamic Media-Viewer* das Video-Tracking zu aktivieren. Videometriken werden so in Adobe Analytics verfügbar. Video-Tracking ist auf die Erweiterung „Adobe Media Analytics for Audio and Video“ angewiesen.

Siehe [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions).

Derzeit ist die Unterstützung für Video-Tracking auf das Tracking „Core-Wiedergabe“ beschränkt, wie in der [Tracking-Übersicht](https://experienceleague.adobe.com/docs/media-analytics/using/sdk-implement/track-av-playback/track-core-overview.html#player-events) beschrieben. Insbesondere wird die Verfolgung von QoS, Anzeigen, Kapiteln/Segmenten oder Fehlern nicht unterstützt.

## Verwenden der Erweiterung „Dynamic Media-Viewer“ {#using-the-dynamic-media-viewers-extension}

Wie unter [Anwendungsbeispiele für die Integration](#use-cases-for-the-integration) erwähnt, ist es möglich, Dynamic Media-Viewer sowohl mit der neuen Adobe Launch-Integration in AEM Sites als auch mithilfe von Einbettungs-Code zu verfolgen.

### Verfolgen von Dynamic Media-Viewern in AEM Sites {#tracking-dynamic-media-viewers-in-aem-sites}

Zur Verfolgung von Dynamic Media-Viewern in AEM Sites müssen alle Schritte ausgeführt werden, die im Abschnitt [Konfigurieren aller Integrationselemente](#configuring-all-the-integration-pieces) aufgeführt sind. Insbesondere müssen Sie die IMS-Konfiguration und die Adobe Launch Cloud-Konfiguration erstellen.

Nach ordnungsgemäßer Konfiguration verfolgt jeder Dynamic Media-Viewer, den Sie einer Sites-Seite mithilfe einer von Dynamic Media unterstützten WCM-Komponente hinzufügen, automatisch Daten für Adobe Analytics oder Adobe Analytics for Video oder beides.

<!-- To be reviewed and updated although this is found live in the AEMaaCS version:
See [Adding Dynamic Media Assets to Pages using Adobe Sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).
-->

### Verfolgen von Dynamic Media-Viewern mit Einbettungs-Code {#tracking-dynamic-media-viewers-using-embed-code}

Kunden, die kein AEM Sites verwenden oder Dynamic Media-Viewer in Web-Seiten außerhalb von AEM Sites einbetten (oder beides), können weiter die Adobe Launch-Integration nutzen.

Sie müssen die Konfigurationsschritte im Abschnitt [Konfigurieren von Adobe Analytics](#configuring-adobe-analytics-for-the-integration) und [Konfigurieren von Adobe Launch](#configuring-adobe-launch-for-the-integration) ausführen. AEM-bezogene Konfigurationsschritte sind jedoch nicht erforderlich.

Nach der ordnungsgemäßen Konfiguration können Sie mit einem Dynamic Media-Viewer Adobe Launch-Unterstützung zu einer Web-Seite hinzufügen.

Weitere Informationen zur Verwendung des Einbettungs-Codes für die Adobe Launch-Bibliothek finden Sie unter [Einbettungs-Code für Launch hinzufügen](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-websites-with-launch/configure-launch/launch-add-embed.html#configure-launch).

<!-- To be reviewed and updated although this is found live in the AEMaaCS version:
See [Embedding the Video or Image Viewer on a Web Page](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) to learn more about how to use the embed code feature of AEM Dynamic Media.
-->

**So verfolgen Sie Dynamic Media-Viewer mit Einbettungs-Code**:

1. Verwenden Sie eine Web-Seite, die bereit zum Einbetten eines Dynamic Media-Viewers ist.
1. Rufen Sie den Einbettungs-Code für die Adobe Launch-Bibliothek ab, indem Sie sich zunächst bei Adobe Launch anmelden (siehe [Konfigurieren von Adobe Launch](#configuring-adobe-launch-for-the-integration)).
1. Klicken Sie auf **[!UICONTROL Eigenschaften]** und dann auf die Registerkarte **[!UICONTROL Umgebungen]**.
1. Wählen Sie die für die Umgebung der Web-Seite relevante Umgebungsebene aus. Klicken Sie dann in der Spalte **[!UICONTROL Installieren]** auf das Kontrollkästchen.
1. Kopieren Sie im Dialogfeld **[!UICONTROL Web-Installationsanweisungen]** den vollständigen Einbettungs-Code der Adobe Launch-Bibliothek zusammen mit den zugehörigen `<script/>`-Tags.

## Referenzhandbuch für die Erweiterung „Dynamic Media-Viewer“ {#reference-guide-for-the-dynamic-media-viewers-extension}

### Über die Konfiguration der Dynamic Media-Viewer {#about-the-dynamic-media-viewers-configuration}

Die Erweiterung „Dynamic Media-Viewer“ wird automatisch in die Adobe Launch-Bibliothek integriert, wenn alle folgenden Bedingungen erfüllt sind:

* Das globale Objekt (`_satellite`) der Adobe Launch-Bibliothek befindet sich auf der Seite.
* Die Erweiterungsfunktion für „Dynamic Media-Viewer“ `_dmviewers_v001()` ist für `_satellite` definiert.

* Der Viewer-Parameter `config2=` wurde nicht angegeben. Das bedeutet, dass der Viewer keine ältere Analytics-Integration verwendet.

Darüber hinaus gibt es eine Option, um die Adobe Launch-Integration im Viewer explizit zu deaktivieren, indem in der Viewer-Konfiguration der Parameter `launch=0` angegeben wird. Der Standardwert dieses Parameters ist `1`.

### Konfigurieren der Erweiterung „Dynamic Media-Viewer“ {#configuring-the-dynamic-media-viewers-extension}

Die einzige Konfigurationsoption für die Erweiterung „Dynamic Media-Viewer“ ist **[!UICONTROL Adobe Media Analytics for Audio and Video aktivieren]**.

Wenn Sie diese Option aktivieren und die Erweiterung Adobe Media Analytics for Audio and Video installiert sowie ordnungsgemäß konfiguriert haben, werden Videowiedegabemetriken an die Lösung Adobe Analytics for Audio and Video gesendet. Durch Deaktivieren dieser Option wird das Video-Tracking deaktiviert.

Wenn Sie diese Option aktivieren, *ohne* die Erweiterung Adobe Media Analytics for Audio and Video installiert zu haben, hat diese Option keine Auswirkungen.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Datenelemente in der Erweiterung „Dynamic Media-Viewer“ {#about-data-elements-in-the-dynamic-media-viewers-extension}

Der einzige Datenelementtyp, den die Erweiterung „Dynamic Media-Viewer“ bietet, ist **[!UICONTROL Viewer-Ereignis]** aus der Dropdown-Liste **[!UICONTROL Datenelementtyp]**.

Wenn diese Option aktiviert ist, rendert der Datenelement-Editor ein Formular mit zwei Feldern:

* **[!UICONTROL Ereignisdatentyp DM-Viewer]** – eine Dropdown-Liste, die alle Viewer-Ereignisse identifiziert, die von der Erweiterung „Dynamic Media-Viewer“ unterstützt werden und Argumente sowie ein spezielles **[!UICONTROL COMMON]**-Element aufweisen. Ein **[!UICONTROL COMMON]**-Element stellt eine Liste von Ereignisparametern dar, die allen von den Viewern gesendeten Ereignistypen gemein sind.
* **[!UICONTROL Tracking-Parameter]** – ein Argument des ausgewählten Dynamic Media-Viewer-Ereignisses.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Eine Liste der unterstützten Ereignisse nach Viewer-Typ finden Sie im [Dynamic Media-Viewer-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html#viewers-aem-assets-dmc). Konsultieren Sie den Abschnitt zum gewünschten Viewer und klicken Sie auf den Unterabschnitt „Support für Tracking mit Adobe Analytics“. Derzeit sind Ereignisargumente im Referenzhandbuch für Dynamic Media-Viewer nicht dokumentiert.

Betrachten wir nun den Lebenszyklus des *Datenelements* von „Dynamic Media-Viewer“. Der Wert dieses Datenelements wird ausgefüllt, nachdem das entsprechende Dynamic Media-Viewers-Ereignis auf der Seite eintritt. Wenn das Datenelement beispielsweise auf das **[!UICONTROL LOAD]**-Ereignis und dessen „asset“-Argument verweist, erhält der Wert dieses Datenelements gültige Daten, sobald der Viewer das LOAD-Ereignis zum ersten Mal ausführt. Wenn das Datenelement auf das **[!UICONTROL ZOOM]**-Ereignis und das zugehörige „scale“-Argument verweist, bleibt der Wert dieses Datenelements leer, bis der Viewer zum ersten Mal ein **[!UICONTROL ZOOM]**-Ereignis sendet.

Gleichermaßen werden die Werte von Datenelementen automatisch aktualisiert, wenn der Viewer ein entsprechendes Ereignis auf der Seite sendet. Der Wert wird auch dann aktualisiert, wenn das betreffende Ereignis nicht in der Regelkonfiguration angegeben ist. Wenn das Datenelement **[!UICONTROL ZoomScale]** beispielsweise für den „scale“-Parameter des ZOOM-Ereignisses definiert ist, die einzige in der Regelkonfiguration vorhandene Regel jedoch vom **[!UICONTROL LOAD]**-Ereignis ausgelöst wird, wird der Wert von **[!UICONTROL ZoomScale]** dennoch jedes Mal aktualisiert, wenn ein Benutzer im Viewer den Zoom verwendet.

Jeder Dynamic Media-Viewer verfügt auf der Web-Seite über eine eindeutige Kennung. Das Datenelement verfolgt den Wert selbst und auch den Viewer, der den Wert ausgefüllt hat. Das bedeutet, dass bei mehreren Viewern auf derselben Seite und einem Datenelement **[!UICONTROL AssetName]**, das auf das **[!UICONTROL LOAD]**-Ereignis und das „asset“-Argument verweist, das Datenelement **[!UICONTROL AssetName]** eine Sammlung von Asset-Namen pflegt, die den einzelnen auf der Seite geladenen Viewern zugeordnet sind.

Der jeweilige vom Datenelement zurückgegebene Wert hängt vom Kontext ab. Wenn das Datenelement in einer Regel angefordert wird, die durch ein Dynamic Media-Viewer-Ereignis ausgelöst wurde, wird der Datenelementwert für den Viewer zurückgegeben, der die Regel initiiert hat. Wenn das Datenelement in einer Regel angefordert wird, die durch ein Ereignis aus einer anderen Adobe Launch-Erweiterung ausgelöst wurde, ist der Wert des Datenelements der Wert des Viewers, der dieses Datenelement als letzter aktualisiert hat.

**Betrachten Sie die folgende Beispieleinrichtung**:

* eine Web-Seite mit zwei Dynamic Media-Zoom-Viewern; wir werden sie als *Viewer1* und *Viewer2* bezeichnen.

* Das Datenelement **[!UICONTROL ZoomScale]** verweist auf das **[!UICONTROL ZOOM]**-Ereignis und das zugehörige „scale“-Argument.
* **[!UICONTROL TrackPan]**-Regel mit folgenden Eigenschaften:

   * Verwendet das Dynamic Media-Viewer-Ereignis **[!UICONTROL PAN]** als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]**-Datenelements an Adobe Analytics.

* **[!UICONTROL TrackKey]**-Regel mit folgenden Eigenschaften:

   * Verwendet das Tastendruckereignis der Adobe Launch-Core-Erweiterung als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]**-Datenelements an Adobe Analytics.

Nehmen wir nun an, dass der Endbenutzer die Web-Seite mit beiden Viewern lädt. In *Viewer1* zoomt er auf eine Skalierung von 50 %. In *Viewer2* zoomt er dann auf eine Skalierung von 25 %. In *viewer1* schwenken sie das Bild herum und wählen schließlich eine Taste auf der Tastatur aus.

Die Aktivitäten des Endbenutzers führen dazu, dass die folgenden beiden Tracking-Aufrufe an Adobe Analytics gesendet werden:

* Der erste Aufruf erfolgt, weil die **[!UICONTROL TrackPan]**-Regel ausgelöst wird, wenn der Benutzer in *Viewer1* schwenkt. Dieser Aufruf sendet 50 % als Wert des **[!UICONTROL ZoomScale]**-Datenelements, da das Datenelement weiß, dass die Regel von *Viewer1* ausgelöst wird, und den entsprechenden Skalierungswert abruft.
* Der zweite Aufruf erfolgt, weil die **[!UICONTROL TrackKey]**-Regel ausgelöst wird, wenn der Benutzer eine Taste auf der Tastatur drückt. Bei diesem Aufruf werden 25 % als Wert des **[!UICONTROL ZoomScale]**-Datenelements gesendet, da die Regel nicht vom Viewer ausgelöst wurde. Daher gibt das Datenelement den aktuellsten Wert zurück.

Das oben aufgestellte Beispiel wirkt sich auch auf die Lebensdauer des Datenelementwerts aus. Der Wert des vom Dynamic Media-Viewer verwalteten Datenelements wird im Code der Adobe Launch-Bibliothek gespeichert, selbst wenn der Viewer selbst auf der Web-Seite beendet wird. Wenn es also eine Regel gibt, die von einer Nicht-Dynamic Media-Viewer-Erweiterung ausgelöst wird und auf ein solches Datenelement verweist, gibt das Datenelement den letzten bekannten Wert zurück, selbst wenn der Viewer auf der Web-Seite nicht mehr vorhanden ist.

In jedem Fall werden Werte von Datenelementen, die von Dynamic Media-Viewern gesteuert werden, nicht im lokalen Speicher oder auf dem Server gespeichert. Sie werden stattdessen nur in der Client-seitigen Adobe Launch-Bibliothek gespeichert. Die Werte solcher Datenelemente verschwinden, wenn die Web-Seite neu geladen wird.

Im Allgemeinen unterstützt der Datenelement-Editor eine [Festlegung der Speicherdauer](https://experienceleague.adobe.com/docs/launch/using/reference/manage-resources/data-elements.html?lang=en#create-a-data-element). Datenelemente, die die Erweiterung „Dynamic Media-Viewer“ verwenden, unterstützen jedoch als Speicherdauer nur die Option **[!UICONTROL Ohne]**. Das Festlegen eines anderen Werts ist in der Benutzeroberfläche möglich, in diesem Fall wird jedoch das Verhalten des Datenelements nicht definiert. Die Erweiterung verwaltet den Wert des Datenelements selbst: das Datenelement, das den Wert des Viewer-Ereignisarguments während des gesamten Lebenszyklus des Viewers beibehält.

### Über Regeln in der Erweiterung „Dynamic Media-Viewer“ {#about-rules-in-the-dynamic-media-viewers-extension}

Im Regeleditor werden mit der Erweiterung neue Konfigurationsoptionen für den Ereigniseditor hinzugefügt. Darüber hinaus gibt es eine Option zum manuellen Verweisen auf Ereignisparameter im Aktionseditor als schnelle Alternative zur Nutzung vorkonfigurierter Datenelemente.

#### Über den Ereigniseditor {#about-the-events-editor}

Im Ereigniseditor wird mit der Erweiterung „Dynamic Media-Viewer“ ein neuer **[!UICONTROL Ereignistyp]** namens **[!UICONTROL Viewer-Ereignis]** hinzugefügt.

Wenn diese Option aktiviert ist, rendert der Ereigniseditor die Dropdown-Liste **[!UICONTROL Dynamic Media-Viewer-Ereignisse]** und listet alle verfügbaren Ereignisse auf, die von Dynamic Media-Viewern unterstützt werden.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### Über den Aktionseditor {#about-the-actions-editor}

Mit der Erweiterung „Dynamic Media-Viewer“ können Sie Ereignisparameter von Dynamic Media-Viewern verwenden, um im Editor „Variablen festlegen“ der Adobe Analytics-Erweiterung Analysevariablen zuzuordnen.

Die einfachste Methode dazu besteht darin, den folgenden zweistufigen Vorgang durchzuführen:

* Definieren Sie zunächst ein oder mehrere Datenelemente, wobei jedes Datenelement einen Parameter eines Dynamic Media-Viewer-Ereignisses darstellt.
* Klicken Sie dann im Editor „Variablen festlegen“ der Adobe Analytics-Erweiterung auf das Symbol für die Datenelementauswahl (drei gestapelte Festplatten), um das Dialogfeld „Datenelement auswählen“ zu öffnen; wählen Sie dann ein Datenelement aus.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Es ist jedoch möglich, einen anderen Ansatz zu verwenden und die Erstellung von Datenelementen zu umgehen. Sie können auch direkt aus einem Dynamic Media-Viewer-Ereignis auf ein Argument verweisen, indem Sie den vollständig qualifizierten Namen des Ereignisarguments in das Eingabefeld **[!UICONTROL Wert]** der Analytics-Variablenzuweisung eingeben, umgeben von Prozentzeichen (%). Beispiel:

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

Beachten Sie, dass es einen wichtigen Unterschied zwischen der Verwendung von Datenelementen und dem direkten Verweis auf ein Ereignisargument gibt. Bei Datenelementen spielt es keine Rolle, welches Ereignis die Aktion „Variablen festlegen“ auslöst. Das Ereignis, das die Regel auslöst, muss nicht mit dem Dynamic Media-Viewer in Zusammenhang stehen (wie ein Mausklick auf die Web-Seite aus der Core-Erweiterung). Bei Verwendung eines direkten Argumentverweises muss jedoch sichergestellt werden, dass das Ereignis, das die Regel auslöst, dem Ereignisargument entspricht, auf das es verweist.

Wenn Sie beispielsweise auf `%event.detail.dm.LOAD.asset%` verweisen, wird der richtige Asset-Name zurückgegeben, wenn die Regel durch das **[!UICONTROL LOAD]**-Ereignis der Dynamic Media-Viewer-Erweiterung ausgelöst wird. Bei jedem anderen Ereignis wird jedoch ein leerer Wert zurückgegeben.

In der folgenden Tabelle sind die Dynamic Media-Viewer-Ereignisse sowie die unterstützten Argumente aufgeführt:

<table>
 <tbody>
  <tr>
   <td>Name des Viewer-Ereignisses</td>
   <td>Argumentverweis</td>
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

**Voraussetzungen**

Wenn Sie es noch nicht getan haben, empfiehlt Adobe, vor diesem Abschnitt die gesamte Dokumentation sorgfältig zu prüfen, damit Sie die komplette Integration verstehen.

In diesem Abschnitt werden die Konfigurationsschritte erläutert, die zur Integration von Dynamic Media-Viewern mit Adobe Analytics und Adobe Analytics for Audio and Video erforderlich sind. Zwar kann die Erweiterung „Dynamic Media-Viewer“ in Adobe Launch auch für andere Zwecke verwendet werden, doch werden solche Szenarien in dieser Dokumentation nicht behandelt.

Sie werden die Integration in folgenden Adobe-Produkten konfigurieren:

* Adobe Analytics – Sie konfigurieren Tracking-Variablen und Berichte.
* Adobe Launch – Sie definieren eine Eigenschaft, eine oder mehrere Regeln und ein oder mehrere Datenelemente, um das Viewer-Tracking zu ermöglichen.

Wenn diese Integrationslösung mit AEM Sites verwendet wird, muss außerdem die folgende Konfiguration durchgeführt werden:

* [!DNL Adobe I/O] Konsole - Die Integration wird für den Adobe-Start erstellt.
* AEM-Autorenknoten – IMS-Konfiguration und Adobe Launch-Cloud-Konfiguration.

Vergewissern Sie sich, dass Sie bei der Konfiguration Zugriff auf eine Firma in Adobe Experience Cloud haben, für die Adobe Analytics und Adobe Launch bereits aktiviert sind.

## Konfigurieren von Adobe Analytics für die Integration {#configuring-adobe-analytics-for-the-integration}

Nach der Konfiguration von Adobe Analytics wird Folgendes für die Integration eingerichtet:

* Eine Report Suite ist vorhanden und ausgewählt.
* Analytics-Variablen stehen zum Empfang von Verfolgungsdaten zur Verfügung.
* Es gibt Berichte zur Anzeige der in Adobe Analytics erfassten Daten.

Siehe auch [Analytics-Implementierungshandbuch](https://experienceleague.adobe.com/docs/analytics/implementation/home.html).

**So konfigurieren Sie Adobe Analytics für die Integration**:

1. Beginnen Sie, indem Sie über die Experience Cloud-[Startseite](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/) auf Adobe Analytics zugreifen. Klicken Sie in der Menüleiste auf das Symbol „Lösungen“ (eine Tabelle mit drei mal drei Punkten) oben rechts auf der Seite und klicken Sie dann auf **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   Wählen Sie jetzt eine Report Suite aus.

### Auswählen einer Report Suite {#selecting-a-report-suite}

1. Wählen Sie rechts oben auf der Seite „Adobe Analytics“ rechts neben dem Feld **[!UICONTROL Berichte durchsuchen]** die gewünschte Report Suite aus der Dropdown-Liste. Wenn mehrere Report Suites verfügbar sind und Sie nicht sicher sind, welche verwendet werden soll, wenden Sie sich an Ihren Adobe Analytics-Administrator, um sich bei der Auswahl der zu verwendenden Report Suite helfen zu lassen.

   In der folgenden Abbildung hat ein Benutzer eine Report Suite mit dem Namen *DynamicMediaViewersExtensionDoc* erstellt und aus der Dropdown-Liste ausgewählt. Der Name der Report Suite dient nur zur Veranschaulichung. Der Name der Report Suite, die Sie letztendlich auswählen, wird anders lauten.

   Wenn keine Report Suite verfügbar ist, müssen Sie oder Ihr Adobe Analytics-Administrator eine erstellen, bevor Sie mit der Konfiguration fortfahren können.

   Siehe [Berichte und Report Suites](https://experienceleague.adobe.com/docs/analytics/admin/manage-report-suites/report-suites-admin.html#manage-report-suites) und [Report Suite erstellen](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/create-report-suite.html#admin-console).

   In Adobe Analytics werden Report Suites unter **[!UICONTROL Admin > Report Suites]** verwaltet.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   Nun richten Sie Adobe Analytics-Variablen ein.

### Einrichten von Adobe Analytics-Variablen {#setting-up-adobe-analytics-variables}

1. Sie bestimmen jetzt eine oder mehrere Adobe Analytics-Variablen, die Sie zur Verfolgung des Verhaltens von Dynamic Media-Viewern auf der Web-Seite verwenden möchten.

   Es lassen sich beliebige Variablentypen verwenden, die von Adobe Analytics unterstützt werden. Die Entscheidung über den Variablentyp (z. B. Custom Traffic [props] und Konversion [eVar]) sollte von spezifischen Anforderungen Ihrer Analytics-Implementierung abhängen.

   Siehe [Übersicht über props und eVars](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html#vars).

   Für die Zwecke dieser Dokumentation wird nur eine Variable „Custom Traffic (props)“ verwendet, da diese in einem Analytics-Bericht innerhalb weniger Minuten nach dem Ausführen einer Aktion auf einer Web-Seite verfügbar ist.

   Um eine neue Custom Traffic-Variable zu aktivieren, klicken Sie in Adobe Analytics in der Symbolleiste auf **[!UICONTROL Admin > Report Suites]**.

1. Wählen Sie auf der Seite **[!UICONTROL Report Suite Manager]** den gewünschten Bericht aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Einstellungen bearbeiten > Traffic > Traffic-Variablen]**.
1. Hier wählen Sie eine nicht verwendete Variable, geben ihr einen beschreibenden Namen (**[!UICONTROL Viewer-Asset (prop 30)]**) und setzen das Kombinationsfeld in der Spalte „Aktiviert“ auf „Aktiviert“.

   Der folgende Screenshot ist ein Beispiel für eine Custom Traffic-Variable ( **[!UICONTROL prop30]**) zur Verfolgung eines vom Viewer verwendeten Asset-Namens:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Klicken Sie unten in der Variablenliste auf **[!UICONTROL Speichern]**.

### Einrichten eines Berichts {#setting-up-a-report}

1. Im Allgemeinen wird die Einrichtung eines Berichts in Adobe Analytics von den jeweiligen Projektanforderungen bestimmt. Die Einrichtung detaillierter Berichte ist daher für diese Integration nicht relevant.

   Es ist ausreichend zu wissen, dass Custom Traffic-Berichte automatisch in Adobe Analytics verfügbar werden, nachdem Sie unter **[Einrichten von Adobe Analytics-Variablen](#setting-up-adobe-analytics-variables)** Custom Traffic-Variablen eingerichtet haben.

   Beispielsweise ist der Bericht für **[!UICONTROL Viewer-Asset (prop 30)]** im Menü „Berichte“ unter **[!UICONTROL Custom Traffic > Custom Traffic 21-30 > Viewer-Asset (prop 30)]** verfügbar.

   Beim Aufrufen dieses Berichts direkt nach der Erstellung von **[!UICONTROL Viewer-Asset (prop 30)]** werden keine Daten angezeigt; das ist an diesem Punkt der Integration zu erwarten.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Konfigurieren von Adobe Launch für die Integration {#configuring-adobe-launch-for-the-integration}

Nachdem Sie Adobe Launch konfiguriert haben, werden für die Integration folgende Schritte vorgenommen:

* Erstellung einer neuen Eigenschaft, um alle Konfigurationen zusammenzuhalten.
* Installation und Einrichtung von Erweiterungen. Der Client-seitige Code aller in der Eigenschaft installierten Erweiterungen wird in einer Bibliothek kompiliert. Diese Bibliothek wird später von der Web-Seite verwendet.
* Konfiguration von Datenelementen und Regeln. Diese Konfiguration bestimmt darüber, welche Daten von den Dynamic Media-Viewern erfasst werden, wann die Tracking-Logik ausgelöst wird und wohin die Daten des Viewers in Adobe Analytics gesendet werden.
* Veröffentlichen der Bibliothek.

**So konfigurieren Sie Adobe Launch für die Integration**:

1. Beginnen Sie, indem Sie über die Experience Cloud-[Startseite](https://exc-home.experiencecloud.adobe.com/exc-home/home.html#/) auf Adobe Launch zugreifen. Klicken Sie in der Menüleiste auf das Symbol „Lösungen“ (eine Tabelle mit drei mal drei Punkten) oben rechts auf der Seite und klicken Sie dann auf **[!UICONTROL Launch]**.

   Alternativ können Sie [Launch direkt öffnen](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Erstellen einer Eigenschaft in Adobe Launch {#creating-a-property-in-adobe-launch}

Bei einer Eigenschaft in Adobe Launch handelt es sich um eine benannte Konfiguration, die alle Ihre Einstellungen zusammenhält. Es wird eine Bibliothek der Konfigurationseinstellungen erstellt und in verschiedenen Umgebungsebenen (Entwicklung, Staging und Produktion) veröffentlicht.

Siehe auch [Eine Starteigenschaft erstellen](https://experienceleague.adobe.com/docs/launch-learn/implementing-in-mobile-android-apps-with-launch/configure-launch/launch-create-a-property.html#configure-launch).

1. Klicken Sie in Adobe Launch auf **[!UICONTROL Neue Eigenschaft]**.
1. Geben Sie im Dialogfeld **[!UICONTROL Eigenschaft erstellen]** im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein, z. B. den Titel Ihrer Website. Beispiel: `DynamicMediaViewersProp.`
1. Geben Sie im Feld **[!UICONTROL Domänen]** die Domäne Ihrer Website ein.
1. Aktivieren Sie in der Dropdown-Liste **[!UICONTROL Erweiterte Optionen]** die Option **[!UICONTROL Für die Erweiterungsentwicklung konfigurieren (kann später nicht geändert werden)]**, falls die zu verwendende Erweiterung - in diesem Fall *Dynamic Media Viewers* - noch nicht veröffentlicht wird.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   Klicken Sie auf die neu erstellte Eigenschaft und fahren Sie dann mit der *Installation und Einrichtung von Erweiterungen* fort.

### Installation und Einrichtung von Erweiterungen {#installing-and-setup-of-extensions}

Alle verfügbaren Erweiterungen in Adobe Launch werden unter **[!UICONTROL Erweiterungen > Katalog]** aufgeführt.

Um eine Erweiterung zu installieren, klicken Sie auf **[!UICONTROL Installieren]**. Führen Sie bei Bedarf eine einmalige Erweiterungskonfiguration durch und klicken Sie dann auf **[!UICONTROL Speichern]**.

Wenn erforderlich, müssen die folgenden Erweiterungen installiert und konfiguriert werden:

* (Erforderlich) *Experience Cloud-ID-Dienst *Erweiterung

Es ist keine zusätzliche Konfiguration erforderlich; akzeptieren Sie die vorgeschlagenen Werte. Wenn Sie fertig sind, klicken Sie auf **[!UICONTROL Speichern]**.

Siehe [Experience Cloud ID Service-Erweiterung](https://experienceleague.adobe.com/docs/launch/using/extensions-ref/adobe-extension/id-service-extension/overview.html#extensions-ref).

* (Erforderlich) *Adobe Analytics*-Erweiterung

Um diese Erweiterung zu konfigurieren, benötigen Sie zunächst die Report Suite-ID aus Adobe Analytics, die Sie unter **[!UICONTROL Admin > Report Suite]** unter der Spaltenüberschrift **[!UICONTROL Report Suite-ID]** finden können.

(Die Report Suite-ID der Report Suite **[!UICONTROL DynamicMediaViewersExtensionDoc]** wird in den folgenden Screenshots nur zu Demonstrationszwecken verwendet. Diese ID wurde unter [Auswählen einer Report Suite](#selecting-a-report-suite) zuvor erstellt und eingesetzt.)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Geben Sie auf der Seite „Erweiterung installieren“ die Report Suite-ID in das Feld **[!UICONTROL Report Suites Entwicklung]**, das Feld **[!UICONTROL Report Suites Staging]** und das Feld **[!UICONTROL Report Suites Produktion]** ein.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Konfigurieren Sie das folgende Element nur, wenn Sie Video-Tracking verwenden möchten:*

Erweitern Sie auf der Seite **[!UICONTROL Erweiterung installieren]** den Eintrag **[!UICONTROL Allgemein]** und geben Sie dann den Tracking-Server an. Der Tracking-Server folgt der Vorlage `<trackingNamespace>.sc.omtrdc.net`, wobei `<trackingNamespace>` die in der Bereitstellungs-E-Mail abgerufene Information darstellt.

Klicken Sie auf **[!UICONTROL Speichern]**.

Siehe [Adobe Analytics-Erweiterung](https://experienceleague.adobe.com/docs/launch/using/extensions-ref/adobe-extension/analytics-extension/overview.html#extensions-ref).

* (Optional) nur erforderlich, wenn Videoverfolgung erforderlich ist) *Adobe Medienanalyse für Audio und Video*

Füllen Sie das Feld für den Tracking-Server aus. Der Tracking-Server für die Erweiterung *Adobe Media Analytics for Audio and Video* unterscheidet sich von dem für Adobe Analytics verwendeten Tracking-Server. Er folgt der Vorlage `<trackingNamespace>.hb.omtrdc.net`, wobei `<trackingNamespace>` die Information aus der Bereitstellungs-E-Mail darstellt.

Alle anderen Felder sind optional.

Siehe [Erweiterung Adobe Media Analytics for Audio and Video](https://experienceleague.adobe.com/docs/launch/using/extensions-ref/adobe-extension/media-analytics-extension/overview.html#extensions-ref).

* (Erforderlich) Erweiterung *Dynamic Media-Viewer*

Wählen Sie **[!UICONTROL Adobe Analytics for Video aktivieren]**, um das Video-Heartbeat-Tracking zu aktivieren (einzuschalten).

Beachten Sie, dass die Erweiterung *Dynamic Media Viewers* zum Zeitpunkt des Schreibens nur verfügbar ist, wenn die Adobe Launch-Eigenschaft für die Entwicklung erstellt wurde.

Siehe [Erstellen einer Eigenschaft in Adobe Launch](#creating-a-property-in-adobe-launch).

Nachdem die Erweiterungen installiert und eingerichtet wurden, werden im Bereich „Erweiterungen“ > „Installiert“ mindestens die folgenden fünf Erweiterungen aufgeführt (vier, wenn Sie kein Video-Tracking nutzen).

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Einrichten von Datenelementen und Regeln {#setting-up-data-elements-and-rules}

Erstellen Sie in Adobe Launch Datenelemente und Regeln, die zur Verfolgung von Dynamic Media-Viewern erforderlich sind.

Eine Übersicht über die Verfolgung mit Adobe Launch finden Sie unter [Funktionsweise der Daten- und Ereignisverfolgung in der Integration](#how-data-and-event-tracking-works-in-the-integration).

Unter [Beispielkonfiguration](#sample-configuration) finden Sie eine Beispielkonfiguration in Adobe Launch, die zeigt, wie ein Asset-Name beim Laden des Viewers verfolgt wird.

Detaillierte Informationen zu den Funktionen der Erweiterung finden Sie unter [Konfigurieren der Erweiterung „Dynamic Media-Viewer“](#configuring-the-dynamic-media-viewers-extension).

### Veröffentlichen einer Bibliothek {#publishing-a-library}

Um Änderungen an der Adobe Launch-Konfiguration vorzunehmen (einschließlich eingerichteter Eigenschaften, Erweiterungen, Regeln und Datenelemente), müssen Sie diese Änderungen *veröffentlichen*.** Die Veröffentlichung in Adobe Launch erfolgt über die Registerkarte „Publishing“ unter der Eigenschaftskonfiguration.

Adobe Launch kann über mehrere Entwicklungsumgebungen, eine Staging-Umgebung und eine Produktionsumgebung verfügen. Standardmäßig verweist die Adobe Launch-Cloud-Konfiguration in AEM den AEM-Autorenknoten auf die Staging-Umgebung von Adobe Launch und den AEM-Veröffentlichungsknoten auf die Produktionsumgebung von Adobe Launch. Dies bedeutet, dass mit den AEM-Standardeinstellungen die Adobe Launch-Bibliothek in der Staging-Umgebung veröffentlicht werden muss, damit sie im AEM-Autorenknoten verwendet werden kann, und dann in der Produktionsumgebung veröffentlicht werden muss, damit sie im AEM-Veröffentlichungsknoten genutzt werden kann.

Weitere Informationen zu Adobe Launch-Umgebungen finden Sie unter [Umgebungen](https://experienceleague.adobe.com/docs/launch/using/reference/publish/environments/environments.html#environment-types).

Das Veröffentlichen einer Bibliothek umfasst die folgenden zwei Schritte:

* Hinzufügen und Erstellen einer neuen Bibliothek, indem alle erforderlichen Änderungen (neue und Aktualisierungen) in die Bibliothek aufgenommen werden.
* Verschieben der Bibliothek durch die verschiedenen Umgebungsebenen (von „Entwicklung“ über „Staging“ zu „Produktion“)

#### Hinzufügen und Erstellen einer neuen Bibliothek {#adding-and-building-a-new-library}

1. Wenn Sie die Registerkarte „Publishing“ in Adobe Launch zum ersten Mal öffnen, ist die Bibliotheksliste leer.

   Klicken Sie in der linken Spalte auf **[!UICONTROL Neue Bibliothek hinzufügen]**.

   ![image2019-7-15_14-43-17](assets/image2019-7-15_14-43-17.png)

1. Geben Sie auf der Seite „Neue Bibliothek erstellen“ im Feld **[!UICONTROL Name]** einen beschreibenden Namen für die neue Bibliothek ein. Beispiel:

   *DynamicMediaViewersLib*

   Wählen Sie in der Dropdown-Liste „Umgebung“ die Umgebungsebene aus. Zunächst steht nur die Entwicklungsebene zur Auswahl zur Verfügung. Klicken Sie unten links auf der Seite auf **[!UICONTROL Alle geänderten Ressourcen hinzufügen]**.

   ![image2019-7-15_14-49-41](assets/image2019-7-15_14-49-41.png)

1. Klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Für Entwicklung speichern und erstellen]**.

   In wenigen Minuten ist die Bibliothek erstellt und einsatzbereit.

   ![image2019-7-15_15-3-34](assets/image2019-7-15_15-3-34.png)

   >[!NOTE]
   >
   >Wenn Sie das nächste Mal Änderungen an Ihrer Adobe Launch-Konfiguration vornehmen, wechseln Sie zur Registerkarte **[!UICONTROL Publishing]** unter der Konfiguration **[!UICONTROL Eigenschaft]** und klicken Sie dann auf Ihre zuvor erstellte Bibliothek.
   >
   >
   >Klicken Sie im Bildschirm zur Bibliotheksveröffentlichung auf **[!UICONTROL Alle geänderten Ressourcen hinzufügen]** und klicken Sie dann auf **[!UICONTROL Für Entwicklung speichern und erstellen]**.

#### Verschieben einer Bibliothek durch Umgebungsebenen {#moving-a-library-up-through-environment-levels}

1. Nachdem Sie eine neue Bibliothek hinzugefügt haben, befindet sich diese zunächst in der Entwicklungsumgebung. Um sie auf die Ebene der Staging-Umgebung (was der Spalte „Gesendet“ entspricht) zu verschieben, klicken Sie im Dropdown-Menü der Bibliothek auf **[!UICONTROL Zur Genehmigung senden]**.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Senden]**.

   Nachdem die Bibliothek in die Spalte „Gesendet“ verschoben wurde, klicken Sie im Dropdown-Menü der Bibliothek auf **[!UICONTROL Für Staging erstellen]**.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Gehen Sie ähnlich vor, um die Bibliothek aus der Staging-Umgebung in die Produktionsumgebung (Spalte „Veröffentlicht“) zu verschieben.

   Klicken Sie zunächst im Dropdown-Menü auf **[!UICONTROL Veröffentlichung genehmigen]**.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Klicken Sie im Dropdown-Menü auf **[!UICONTROL Für Produktion erstellen und veröffentlichen]**.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Weitere Informationen zum Veröffentlichungsverfahren in Adobe Launch finden Sie unter [Veröffentlichung](https://experienceleague.adobe.com/docs/launch/using/reference/publish/overview.html#reference).

## Konfigurieren von Adobe Experience Manager für die Integration {#configuring-adobe-experience-manager-for-the-integration}

Voraussetzungen:

* AEM führt sowohl die Autoren- als auch die Veröffentlichungsinstanz aus.
* AEM Autorenknoten wird im Dynamic Media - Scene7-Ausführungsmodus (dynamicmedia_s7) eingerichtet
* WCM-Komponenten für Dynamic Media sind in AEM Sites aktiviert.

Die AEM-Konfiguration besteht aus den folgenden zwei Hauptschritten:

* Konfiguration von AEM IMS.
* Konfiguration von Adobe Launch Cloud.

### Konfigurieren von AEM IMS {#configuring-aem-ims}

1. Klicken Sie im AEM-Autorenknoten auf das Symbol „Tools“ (Hammer) und dann auf **[!UICONTROL Sicherheit > Adobe IMS-Konfigurationen]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Klicken Sie auf der Seite „Adobe IMC-Konfigurationen“ links oben auf **[!UICONTROL Erstellen]**.
1. Klicken Sie auf der Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** auf **[!UICONTROL Adobe Launch]**.
1. Aktivieren Sie **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie dann in das Textfeld einen beliebigen aussagekräftigen Wert für das Zertifikat ein. Beispiel: *AdobeLaunchIMSCert*. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**.

   Die folgende Informationsmeldung wird angezeigt:

   *Um ein gültiges Zugriffs-Token abzurufen, muss der öffentliche Schlüssel des neuen Zertifikats zum technischen Konto in Adobe I/O hinzugefügt werden*.

   Klicken Sie auf **[!UICONTROL OK]**, um das Dialogfeld „Informationen“ zu schließen.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Klicken Sie auf **[!UICONTROL Öffentlichen Schlüssel herunterladen]**, um eine öffentliche Schlüsseldatei (*.crt) auf Ihr lokales System herunterzuladen.

   >[!NOTE]
   >
   >Lassen Sie ***jetzt*** die Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** geöffnet; schließen Sie die Seite ***nicht*** und klicken Sie nicht auf ***Weiter***. Sie werden später in den Schritten noch zu dieser Seite zurückkehren.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. Navigieren Sie in einer neuen Browserregisterkarte zum Ordner [[!DNL Adobe I/O] Console](https://console.adobe.io/integrations).

1. Klicken Sie auf der Seite **[!UICONTROL Adobe I/O Console-Integrationen]** rechts oben auf **[!UICONTROL Neue Integration]**.
1. Vergewissern Sie sich, dass im Dialogfeld **[!UICONTROL Neue Integration erstellen]** die Optionsschaltfläche **[!UICONTROL Zugriff auf API]** ausgewählt ist, und klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Aktivieren Sie auf der zweiten Seite von **[!UICONTROL Neue Integration erstellen]** die Optionsschaltfläche **[!UICONTROL Experience Platform Launch-API]**. Klicken Sie in der rechten unteren Ecke der Seite auf **[!UICONTROL Weiter]**.

   ![2019-07-25_13-13-54](assets/2019-07-25_13-13-54.png)

1. Gehen Sie auf der dritten Seite von **[!UICONTROL Neue Integration erstellen]** wie folgt vor:

   * Geben Sie im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein. Beispielsweise *DynamicMediaViewersIO*.

   * Geben Sie im Feld **[!UICONTROL Beschreibung]** eine Beschreibung für die Integration ein.

   * Laden Sie im Bereich **[!UICONTROL Zertifikate mit öffentlichem Schlüssel]** Ihre öffentliche Schlüsseldatei (*.crt) hoch, die Sie zuvor in diesen Schritten heruntergeladen haben.

   * Wählen Sie unter der Überschrift **[!UICONTROL Rolle für Experience Platform Launch-API auswählen]** die Option **[!UICONTROL Admin]**.

   * Wählen Sie unter der Überschrift **[!UICONTROL Ein oder mehrere Produktprofile für die Experience Platform Launch-API auswählen]** das Produktprofil **[!UICONTROL Launch – &lt;Name_Ihrer_Firma>]**.

   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Klicken Sie auf **[!UICONTROL Integration erstellen]**.
1. Klicken Sie auf der Seite **[!UICONTROL Integration erstellt]** auf **[!UICONTROL Weiter zu Integrationsdetails]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Eine Integrationsdetailseite wird angezeigt, **** ähnlich der folgenden:

   >[!NOTE]
   >
   >***Lassen Sie die Seite mit Integrationsdetails geöffnet***. In wenigen Augenblicken benötigen Sie verschiedene Informationen aus den Registerkarten **[!UICONTROL Übersicht]** und **[!UICONTROL JWT]**.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Integrationsdetails angezeigt.

1. Kehren Sie zur Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** zurück, die Sie zuvor offen gelassen haben. Klicken Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Weiter]**, um die Seite **[!UICONTROL Konto]** im Fenster **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** zu öffnen.

   Wenn Sie die Seite zuvor versehentlich geschlossen haben, kehren Sie zum AEM-Autorenknoten zurück und klicken Sie auf **[!UICONTROL Tools > Sicherheit > Adobe IMS-Konfigurationen]**. Klicken Sie auf **[!UICONTROL Erstellen]**. Wählen Sie in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** die Option **[!UICONTROL Adobe Launch]**. Wählen Sie in der Dropdown-Liste **[!UICONTROL Zertifikat]** den Namen des zuvor erstellten Zertifikats aus.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Technische Kontokonfiguration für Adobe IMS – Zertifikatsseite.

1. Die Seite **[!UICONTROL Konto]** enthält fünf Felder, in denen Sie Informationen aus der Seite „Integrationsdetails“ (vorheriger Schritt) ausfüllen müssen.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Technische Kontokonfiguration für Adobe IMS – Kontoseite.

1. Füllen Sie auf der Seite **[!UICONTROL Konto]** die folgenden Felder aus:

   * **[!UICONTROL Titel]**: Geben Sie einen beschreibenden Kontonamen ein.
   * **[!UICONTROL Autorisierungs-Server]**: Kehren Sie zur Seite mit den Integrationsdetails zurück, die Sie zuvor geöffnet haben. Klicken Sie auf die Registerkarte **[!UICONTROL JWT]**. Kopieren Sie den Servernamen - ohne Pfad - wie unten hervorgehoben.

(Der Beispiel-Server-Name dient nur zu Veranschaulichungszwecken.)   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie den Namen in das entsprechende Feld ein.
Beispiel: `https://ims-na1.adobelogin.com/`(Der Beispiel-Server-Name dient nur zu Veranschaulichungszwecken.)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Seite mit Integrationsdetails - Registerkarte „JWT“

1. **[!UICONTROL API-Schlüssel]**: Kehren Sie zur Seite „Integrationsdetails“ zurück. Klicken Sie auf die Registerkarte **[!UICONTROL Übersicht]** und dann rechts neben dem Feld **[!UICONTROL API-Schlüssel (Client-ID)]** auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie den Schlüssel in das entsprechende Feld ****ein.

   ![2019-07-25_14-35-333](assets/2019-07-25_14-35-333.png)

   Integrationsdetails angezeigt.

1. **[!UICONTROL Client-Geheimnis]**: Kehren Sie zur Seite „Integrationsdetails“ zurück. Klicken Sie auf der Registerkarte **[!UICONTROL Übersicht]** auf **[!UICONTROL Client-Geheimnis abrufen]**. Klicken Sie rechts neben dem Feld **[!UICONTROL Client-Geheimnis]** auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Schlüssel in das entsprechende Feld ein.

1. **[!UICONTROL Payload]**: Kehren Sie zur Seite „Integrationsdetails“ zurück. Kopieren Sie auf der Registerkarte **[!UICONTROL JWT]** im Feld „JWT-Payload“ den gesamten JSON-Objekt-Code.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie den Code in das entsprechende Feld ein.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Seite mit Integrationsdetails – Registerkarte „JWT“

   Die Kontoseite mit allen ausgefüllten Feldern sieht wie folgt aus:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. Tippen Sie oben rechts neben **[!UICONTROL Konto]** auf **[!UICONTROL Erstellen]**.

   Wenn AEM IMS konfiguriert ist, befindet sich jetzt unter **[!UICONTROL Adobe IMS-Konfigurationen]** ein neues IMS-Konto.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Konfigurieren von Adobe Launch Cloud für die Integration {#configuring-adobe-launch-cloud-for-the-integration}

1. Klicken Sie im AEM-Autorenknoten in der oberen linken Ecke auf das Symbol „Tools“ (Hammer) und dann auf **[!UICONTROL Cloud Services > Adobe Launch-Konfigurationen]**.

   ![26.07.2019_12-10-38](assets/2019-07-26_12-10-38.png)

1. Wählen Sie auf der Seite **[!UICONTROL Adobe Launch-Konfigurationen]** im linken Bereich eine AEM-Site aus, auf die Sie Ihre Adobe Launch-Konfiguration anwenden möchten.

   Die Site **[!UICONTROL We.Retail]** ist im folgenden Screenshot nur zur Veranschaulichung ausgewählt.

   ![26.07.2019_12-20-06](assets/2019-07-26_12-20-06.png)

1. Klicken Sie links oben auf der Seite auf **[!UICONTROL Erstellen]**.
1. Füllen Sie auf der Seite **[!UICONTROL Allgemein]** (1/3 Seiten) des Fensters **[!UICONTROL Adobe Launch-Konfiguration erstellen]** die folgenden Felder aus:

   * **[!UICONTROL Titel]** – Geben Sie einen beschreibenden Konfigurationsnamen ein. Beispiel: `We.Retail Launch cloud configuration`.

   * **[!UICONTROL Zugewiesene Adobe IMS-Konfiguration]** – Wählen Sie die IMS-Konfiguration, die Sie zuvor unter [Konfigurieren von AEM IMS](#configuring-aem-ims) erstellt haben.

   * **[!UICONTROL Firma]** – Wählen Sie aus der Dropdown-Liste **[!UICONTROL Firma]** Ihre Experience Cloud-Firma aus. Die Liste wird automatisch ausgefüllt.

   * **[!UICONTROL Eigenschaft]** – Wählen Sie in der Dropdown-Liste „Eigenschaft“ die zuvor erstellte Adobe Launch-Eigenschaft aus. Die Liste wird automatisch ausgefüllt.
   Nachdem Sie alle Felder ausgefüllt haben, sieht Ihre Seite **[!UICONTROL Allgemein]** wie folgt aus:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Klicken Sie links oben auf **[!UICONTROL Weiter]**.
1. Füllen Sie auf der Seite **[!UICONTROL Staging]** (2/3 Seiten) des Fensters **[!UICONTROL Adobe Launch-Konfiguration erstellen]** das folgende Feld aus:

   Überprüfen Sie im Feld **[!UICONTROL URI der Bibliothek]** den Speicherort der Staging-Version Ihrer Adobe Launch-Bibliothek. AEM füllt dieses Feld automatisch aus.

   Nur zu Veranschaulichungszwecken werden in diesem Schritt Adobe Launch-Bibliotheken verwendet, die in Adobe CDN bereitgestellt werden.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der automatisch ausgefüllte Bibliotheks-URI (Uniform Resource Identifier) nicht fehlerhaft ist. Korrigieren Sie ihn ggf. so, dass der URI einen protokollrelativen URI darstellt. Das heißt, er beginnt mit einem doppelten Schrägstrich.
   >
   >
   >Beispiel: `//assets.adobetm.com/launch-xxxx`.

   Ihre **[!UICONTROL Staging]**-Seite sollte in etwa wie folgt aussehen: Beachten Sie, dass die Optionen **[!UICONTROL Archiv]** und **[!UICONTROL Bibliothek asynchron laden]** hier ***nicht*** festgelegt sind:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Weiter]**.
1. Korrigieren Sie auf der Seite **[!UICONTROL Produktion]** (3/3 Seiten) des Fensters **[!UICONTROL Adobe Launch-Konfiguration erstellen]** bei Bedarf den automatisch ausgefüllten Produktions-URI ähnlich wie auf der vorherigen **[!UICONTROL Staging]**-Seite.
1. Klicken Sie in der rechten oberen Ecke auf **[!UICONTROL Erstellen]**.

   Ihre neue Adobe Launch Cloud-Konfiguration wird jetzt erstellt und neben Ihrer Website aufgelistet, ähnlich dem folgenden Beispiel:

1. Wählen Sie Ihre neue Adobe Launch Cloud-Konfiguration aus (bei Auswahl wird links neben dem Konfigurationstitel ein Häkchen angezeigt). Klicken Sie in der Symbolleiste auf **[!UICONTROL Veröffentlichen]**.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

Derzeit unterstützt der AEM-Autorenknoten nicht die Integration von Dynamic Media-Viewern mit Adobe Launch.

Sie wird jedoch im AEM-Veröffentlichungsknoten unterstützt. Unter Verwendung der Standardeinstellungen der Adobe Launch Cloud-Konfiguration nutzt der AEM-Veröffentlichungsknoten die Produktionsumgebung von Adobe Launch. Daher müssen Adobe Launch-Bibliotheksaktualisierungen jedes Mal beim Test von der Entwicklungsumgebung in die Produktionsumgebung verschoben werden.

Sie können diese Beschränkung umgehen, indem Sie die Entwicklungs- oder Staging-URL der Adobe Launch-Bibliothek in der oben stehenden Adobe Launch Cloud-Konfiguration für den AEM-Veröffentlichungsknoten angeben. Dadurch verwendet der AEM-Veröffentlichungsknoten die Entwicklungs- oder Staging-Version der Adobe Launch-Bibliothek.

Weitere Informationen zum Einrichten der Adobe Launch Cloud-Konfiguration finden Sie unter [AEM mit Adobe Launch über integrieren [!DNL Adobe I/O].](https://helpx.adobe.com/de/experience-manager/using/aem_launch_adobeio_integration.html)
