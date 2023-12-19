---
title: Integrieren von Dynamic Media Viewers mit Adobe Analytics und Experience Platform Tags
description: Erfahren Sie mehr über die Dynamic Media Viewers-Erweiterung für Experience Platform Tags und Dynamic Media Viewers 5.13. Sie ermöglicht es Kunden von Adobe Analytics und Experience Platform Tags, für Dynamic Media Viewers in ihrer Experience Platform Tags-Konfiguration spezifische Ereignisse und Daten zu verwenden.
mini-toc-levels: 3
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Viewers
role: User, Admin,Developer,Data Engineer,Data Architect
exl-id: 161dfe22-bc1c-4b60-8ab6-a19407a39e2e
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '6664'
ht-degree: 99%

---

# Integrieren von Dynamic Media Viewers mit Adobe Analytics und Experience Platform Tags {#integrating-dynamic-media-viewers-with-adobe-analytics-and-adobe-launch}

## Worum geht es bei der Integration von Dynamic Media Viewers mit Adobe Analytics und Experience Platform Tags? {#what-is-dynamic-media-viewers-integration-with-adobe-analytics-and-adobe-launch}

<!-- Leave this hidden path here; it points to the topic source from Sasha https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=~oufimtse&title=Dynamic+Media+Viewers+integration+with+Adobe+Launch -->

*Mit der Dynamic Media Viewers*-Erweiterung für Experience Platform Tags und Dynamic Media Viewers 5.13 können Adobe Analytics- und Experience Platform Tags-Kunden ihrer Experience Platform Tags-Konfiguration für Dynamic Media Viewers spezifische Ereignisse und Daten verwenden.

Diese Integration ermöglicht es Ihnen, die Nutzung von Dynamic Media Viewers auf Ihrer Website mit Adobe Analytics zu verfolgen. Gleichzeitig können Sie die von den Viewern angezeigten Ereignisse und Daten mit jeder anderen Experience Platform Tags-Erweiterung von Adobe oder einem Drittanbieter verwenden.

Weitere Informationen zu Erweiterungen von Adobe oder Drittanbieterern finden Sie unter [Adobe-Erweiterungen](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/overview.html?lang=de) im Benutzerhandbuch zu Experience Platform Tags.

**Dieses Thema richtet sich an:** Site-Admins, Entwicklerinnen und Entwickler für die Experience Platform und Anwendende.

### Einschränkungen der Integration {#limitations-of-the-integration}

* Die Experience Platform Tags-Integration für Dynamic Media Viewers funktioniert nicht im Experience Manager-Autorenmodus. Sie können kein Tracking für eine WCM-Seite anzeigen, bevor diese veröffentlicht wurde.
* Die Experience Platform Tags-Integration für Dynamic Media Viewer wird nicht im Popup-Betriebsmodus unterstützt, bei dem die Viewer-URL über die Schaltfläche „URL“ auf der Seite „Asset-Details“ abgerufen wird.
* Die Experience Platform Tags-Integration kann nicht gleichzeitig mit der Analytics-Integration älterer Viewer verwendet werden (mit dem Parameter `config2=`).
* Unterstützung für das Video-Tracking ist auf das Core-Wiedergabe-Tracking beschränkt, wie unter [Tracking-Übersicht](https://experienceleague.adobe.com/docs/media-analytics/using/tracking/track-core-overview.html?lang=de) beschrieben. Insbesondere wird die Verfolgung von QoS, Anzeigen, Kapiteln/Segmenten oder Fehlern nicht unterstützt.
* Die Konfiguration der Speicherdauer für Datenelemente wird bei Datenelementen, die die Erweiterung *Dynamic Media Viewers* verwenden, nicht unterstützt. Die Speicherdauer muss auf **[!UICONTROL Ohne]** eingestellt sein.

### Anwendungsbeispiele für die Integration {#use-cases-for-the-integration}

Der primäre Anwendungsfall für die Integration mit Experience Platform Tags sind Kunden, die sowohl Adobe Experience Manager Assets als auch Adobe Experience Manager Sites verwenden. In solchen Fällen können Sie eine Standardintegration zwischen dem Autorenknoten von Experience Manager und Experience Platform Tags einrichten und dann Ihre Sites-Instanz mit der Experience Platform Tags-Eigenschaft verknüpfen. Danach verfolgt jede Dynamic Media-WCM-Komponente, die einer Sites-Seite hinzugefügt wird, Daten und Ereignisse von Viewern.

Siehe [Tracking von Dynamic Media-Viewern in Experience Manager Sites](#tracking-dynamic-media-viewers-in-aem-sites).

Ein sekundäres Anwendungsbeispiel, das die Integration unterstützt, sind Kunden, die nur Experience Manager Assets oder Dynamic Media Classic verwenden. In solchen Fällen können Sie den Einbettungs-Code für Ihren Viewer abrufen und der Web-Seite hinzufügen. Rufen Sie dann die Produktions-URL der Experience Platform Tags-Bibliothek aus Experience Platform Tags ab und fügen Sie sie manuell zum Web-Seiten-Code hinzu.

Siehe [Tracking von Dynamic Media-Viewern mit Einbettungs-Code](#tracking-dynamic-media-viewers-using-embed-code).

<!-- Path on internal wiki [About tracking Dynamic Media viewers using embed code](https://wiki.corp.adobe.com/display/~oufimtse/Dynamic+Media+Viewers+integration+with+Adobe+Launch#DynamicMediaViewersintegrationwithAdobeLaunch-TrackingDynamicMediaViewersusingEmbedcode). -->

## Funktionsweise der Daten- und Ereignisverfolgung in der Integration {#how-data-and-event-tracking-works-in-the-integration}

Die Integration nutzt zwei separate und unabhängige Typen des Tracking von Dynamic Media Viewers: *Adobe Analytics* und *Adobe Analytics for Audio and Video*.

### Informationen zum Tracking mit Adobe Analytics  {#about-tracking-using-adobe-analytics}

Mit Adobe Analytics können Sie Aktionen verfolgen, die vom Endbenutzer bei der Interaktion mit Dynamic Media Viewers auf Ihrer Website ausgeführt werden. Mit Adobe Analytics können Sie außerdem Viewer-spezifische Daten verfolgen. Beispielsweise können Sie Ladeereignisse der Ansicht zusammen mit dem Asset-Namen, vorgenommenen Zoom-Aktionen und Videowiedergabeaktionen verfolgen und aufzeichnen.

In Experience Platform Tags arbeiten die Konzepte *Datenelemente* und *Regeln* zusammen, um das Adobe Analytics-Tracking zu erlauben.

#### Datenelemente in Experience Platform Tags {#about-data-elements-in-adobe-launch}

Ein Datenelement in Experience Platform Tags ist eine benannte Eigenschaft, deren Wert entweder statisch definiert ist oder basierend auf dem Status einer Web-Seite bzw. von Dynamic Media Viewers-Daten dynamisch berechnet wird.

Optionen, die für eine Datenelementdefinition verfügbar sind, hängen von der Liste der Erweiterungen ab, die in der Experience Platform Tags-Eigenschaft installiert sind. Die Erweiterung „Core“ ist vorinstalliert und in jeder Konfiguration standardmäßig verfügbar. Mit der Erweiterung „Core“ können Sie ein Datenelement definieren, dessen Wert aus Cookies, JavaScript-Code, Abfragezeichenfolgen und vielen anderen Quellen stammen kann.

Für das Tracking mit Adobe Analytics müssen mehrere zusätzliche Erweiterungen wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions) beschrieben installiert werden. Die Dynamic Media Viewers-Erweiterung bietet die Möglichkeit, ein Datenelement zu definieren, dessen Wert ein Argument des Dynamic Media Viewers-Ereignisses ist. Beispielsweise können Sie auf den Viewer-Typ oder den Asset-Namen, der vom Viewer beim Laden gemeldet wird, auf den Zoom-Faktor, der beim Zoomen durch Endbenutzer gemeldet wird, und vieles mehr verweisen.

Die Dynamic Media Viewers-Erweiterung sorgt dafür, dass die Werte der Datenelemente automatisch auf dem neuesten Stand sind.

Nachdem Sie ein Datenelement definiert haben, können Sie es an anderen Stellen der Experience Platform Tags-Benutzeroberfläche verwenden. Nutzen Sie dazu das Widget zur Auswahl von Datenelementen. Insbesondere wird von der Aktion „Variablen festlegen“ der Adobe Analytics-Erweiterung in der Regel auf Datenelemente verwiesen, die für das Tracking von Dynamic Media Viewers definiert werden (siehe unten).

Siehe [Datenelemente](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html?lang=de).

#### Info zu Regeln in Experience Platform Tags {#about-rules-in-adobe-launch}

Eine Regel in Experience Platform Tags ist eine agnostische Konfiguration, die drei Bereiche definiert, aus denen eine Regel besteht: *Ereignisse*, *Bedingungen* und *Aktionen*:

* *Ereignisse*: (wenn) teilen Experience Platform Tags mit, wann eine Regel ausgelöst werden soll.
* *Bedingungen*: (wenn) teilen Experience Platform Tags mit, welche zusätzlichen Einschränkungen beim Auslösen einer Regel zulässig oder nicht zulässig sind.
* *Aktionen*: (dann) teilen Experience Platform Tags mit, was zu tun ist, wenn eine Regel ausgelöst wird.

Die im Abschnitt „Ereignisse“, „Bedingungen“ und „Aktionen“ verfügbaren Optionen hängen von den Erweiterungen ab, die in der Experience Platform Tags-Eigenschaft installiert sind. Die Erweiterung *Core* ist vorinstalliert und in jeder Konfiguration standardmäßig verfügbar. Die Erweiterung bietet mehrere Optionen für Ereignisse, z. B. grundlegende Aktionen auf Browser-Ebene. Zu diesen Aktionen gehören Fokusänderung, Tastendruck und Formularübermittlung. Sie enthält zudem Optionen für Bedingungen, wie z. B. Cookie-Wert, Browser-Typ und mehr. Für Aktionen steht nur die Option „Benutzerspezifischer Code“ zur Verfügung.

Für das Tracking mit Adobe Analytics müssen mehrere zusätzliche Erweiterungen wie unter [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions) beschrieben installiert werden. Insbesondere gilt:

* Die Dynamic Media Viewers-Erweiterung erweitert die Liste der unterstützten Ereignisse auf Ereignisse, die für Dynamic Media Viewers spezifisch sind, z. B. Laden des Viewers, Austauschen von Assets, Vergrößern und Abspielen von Videos.
* Die Adobe Analytics-Erweiterung erweitert die Liste der unterstützten Aktionen um zwei Aktionen, die zum Senden von Daten an Tracking-Server erforderlich sind: *Variablen festlegen* und *Beacon senden*.

Beim Tracking von Dynamic Media-Viewern ist es möglich, einen der folgenden Typen zu verwenden:

* Ereignisse aus der Dynamic Media Viewers-Erweiterung, der Core-Erweiterung oder einer anderen Erweiterung.
* Bedingungen in der Regeldefinition. Alternativ können Sie den Bedingungsbereich leer lassen.

Im Abschnitt „Aktionen“ müssen Sie über die Aktion *Variablen festlegen* verfügen. Diese Aktion teilt Adobe Analytics mit, wie Tracking-Variablen mit Daten ausgefüllt werden. Gleichzeitig sendet die Aktion *Variablen festlegen* nichts an den Tracking-Server.

Auf die Aktion *Variablen festlegen* muss eine Aktion vom Typ *Beacon senden* folgen. Mit der Aktion *Beacon senden* werden tatsächlich Daten an den Analytics-Tracking-Server gesendet. Beide Aktionen (*Variablen festlegen* und *Beacon senden*) kommen aus der Adobe Analytics-Erweiterung.

Siehe [Regeln](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/rules.html?lang=de).

#### Beispielkonfiguration {#sample-configuration}

Die folgende Beispielkonfiguration in Experience Platform Tags zeigt, wie sich ein Asset-Name beim Laden des Viewers verfolgen lässt.

1. Definieren Sie auf der Registerkarte **[!UICONTROL Datenelemente]** ein Datenelement `AssetName`, das auf den `asset`-Parameter des `LOAD`-Ereignisses in der Dynamic Media Viewer-Erweiterung verweist.

   ![image2019-11](assets/image2019-11.png)

1. Definieren Sie auf der Registerkarte **[!UICONTROL Regeln]** eine Regel für *TrackAssetOnLoad*.

   In dieser Regel verwendet das Feld **[!UICONTROL Ereignis]** das **[!UICONTROL LOAD]**-Ereignis aus der Dynamic Media Viewers-Erweiterung-Erweiterung.

   ![image2019-22](assets/image2019-22.png)

1. Die Aktionskonfiguration umfasst zwei Aktionstypen aus der Adobe Analytics-Erweiterung:

   *Variablen festlegen*, wodurch eine Analytics-Variable Ihrer Wahl dem Wert des Datenelements `AssetName` zugeordnet wird;

   *Beacon senden*, wodurch Tracking-Daten an Adobe Analytics gesendet werden.

   ![image2019-3](assets/image2019-3.png)

1. Die daraus resultierende Regelkonfiguration sieht wie folgt aus:

   ![image2019-4](assets/image2019-4.png)

### Informationen zu Adobe Analytics for Audio and Video {#about-adobe-analytics-for-audio-and-video}

Wenn für die Verwendung von Adobe Analytics for Audio and Video ein Experience Cloud-Konto abonniert wird, reicht es, in den Einstellungen der Erweiterung *Dynamic Media Viewers* das Video-Tracking zu aktivieren. Videometriken werden so in Adobe Analytics verfügbar. Video-Tracking ist auf die Erweiterung „Adobe Media Analytics for Audio and Video“ angewiesen.

Siehe [Installation und Einrichtung von Erweiterungen](#installing-and-setup-of-extensions).

Derzeit ist die Unterstützung für Video-Tracking auf das Tracking „Core-Wiedergabe“ beschränkt, wie in der [Tracking-Übersicht](https://experienceleague.adobe.com/docs/media-analytics/using/tracking/track-core-overview.html?lang=de) beschrieben. Insbesondere wird die Verfolgung von QoS, Anzeigen, Kapiteln/Segmenten oder Fehlern nicht unterstützt.

## Verwenden der Dynamic Media Viewers-Erweiterung {#using-the-dynamic-media-viewers-extension}

Wie unter [Anwendungsbeispiele für die Integration](#use-cases-for-the-integration) erwähnt, ist es möglich, Dynamic Media Viewers sowohl mit der neuen Experience Platform Tags-Integration in Experience Manager Sites als auch mithilfe von Einbettungs-Code zu verfolgen.

### Tracking von Dynamic Media-Viewern in Experience Manager Sites {#tracking-dynamic-media-viewers-in-aem-sites}

Zum Tracking von Dynamic Media-Viewern in Experience Manager Sites müssen alle Schritte ausgeführt werden, die im Abschnitt [Konfigurieren aller Integrationselemente](#configuring-all-the-integration-pieces) aufgeführt sind. Insbesondere müssen Sie die IMS-Konfiguration und die Experience Platform Tags Cloud-Konfiguration erstellen.

Nach ordnungsgemäßer Konfiguration verfolgt jeder Dynamic Media-Viewer, den Sie einer Sites-Seite mithilfe einer von Dynamic Media unterstützten WCM-Komponente hinzufügen, automatisch Daten für Adobe Analytics oder Adobe Analytics for Video oder beides.

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Adding Dynamic Media Assets to Pages using Adobe Sites](https://helpx.adobe.com/experience-manager/6-5/help/assets/adding-dynamic-media-assets-to-pages.html).
-->

### Tracking von Dynamic Media-Viewern mit Einbettungs-Code {#tracking-dynamic-media-viewers-using-embed-code}

Kunden, die kein Experience Manager Sites verwenden oder Dynamic Media Viewers in Web-Seiten außerhalb von Experience Manager Sites einbetten (oder beides), können weiterhin die Experience Platform Tags-Integration nutzen.

Sie müssen die Konfigurationsschritte im Abschnitt [Konfigurieren von Adobe Analytics](#configuring-adobe-analytics-for-the-integration) und [Konfigurieren von Experience Platform Tags](#configuring-adobe-launch-for-the-integration) ausführen. Experience Manager-bezogene Konfigurationsschritte sind jedoch nicht erforderlich.

Nach der ordnungsgemäßen Konfiguration können Sie Experience Platform Tags-Unterstützung zu einer Website mit einem Dynamic Media-Viewer hinzufügen.

Weitere Informationen zur Verwendung des Einbettungs-Codes für die Experience Platform Tags-Bibliothek finden Sie unter [Hinzufügen von Einbettungs-Code für Experience Platform Tags](https://experienceleague.adobe.com/docs/platform-learn/implement-in-websites/configure-tags/add-embed-code.html?lang=de).

<!-- To be reviewed and updated although this is found live in the Experience ManageraaCS version:
See [Embedding the Video or Image Viewer on a Web Page](https://helpx.adobe.com/experience-manager/6-5/help/assets/embed-code.html) to learn more about how to use the embed code feature of Experience Manager Dynamic Media.
-->

**Tracking von Dynamic Media-Viewern mit Einbettungs-Code:**

1. Verwenden Sie eine Website, die bereit zum Einbetten eines Dynamic Media-Viewers ist.
1. Rufen Sie den Einbettungs-Code für die Experience Platform Tags-Bibliothek ab, indem Sie sich zuerst bei Experience Platform Tags anmelden (siehe [Konfigurieren von Experience Platform Tags](#configuring-adobe-launch-for-the-integration)).
1. Wählen Sie **[!UICONTROL Eigenschaft]** und dann die Registerkarte **[!UICONTROL Umgebungen]** aus.
1. Wählen Sie die für die Umgebung der Web-Seite relevante Umgebungsebene aus. Klicken Sie dann in der Spalte **[!UICONTROL Installieren]** auf das Feldsymbol.
1. Kopieren Sie im Dialogfeld **[!UICONTROL Web-Installationsanweisungen]** den vollständigen Einbettungs-Code der Experience Platform Tags-Bibliothek zusammen mit den zugehörigen `<script/>`-Tags.

## Referenzhandbuch für die Dynamic Media Viewers-Erweiterung {#reference-guide-for-the-dynamic-media-viewers-extension}

### Über die Konfiguration von Dynamic Media Viewers {#about-the-dynamic-media-viewers-configuration}

Die Dynamic Media Viewers Erweiterung wird automatisch in die Experience Platform Tags-Bibliothek integriert, wenn alle folgenden Bedingungen erfüllt sind:

* Das globale Objekt (`_satellite`) der Experience Platform Tags-Bibliothek befindet sich auf der Seite.
* Die Funktion `_dmviewers_v001()` der Dynamic Media Viewers-Erweiterung ist für `_satellite` definiert.

* Der Viewer-Parameter `config2=` wurde nicht angegeben. Das bedeutet, dass der Viewer keine ältere Analytics-Integration verwendet.

Darüber hinaus gibt es eine Option, um die Experience Platform Tags-Integration im Viewer explizit zu deaktivieren, indem in der Viewer-Konfiguration der Parameter `launch=0` angegeben wird. Der Standardwert dieses Parameters ist `1`.

### Konfigurieren der Dynamic Media Viewers-Erweiterung {#configuring-the-dynamic-media-viewers-extension}

Die einzige Konfigurationsoption für die Dynamic Media Viewers-Erweiterung ist **[!UICONTROL Adobe Media Analytics for Audio and Video aktivieren]**.

Wenn Sie diese Option aktivieren und die Erweiterung „Adobe Media Analytics for Audio and Video“ installiert sowie konfiguriert haben, werden Videowiedergabemetriken an die Lösung „Adobe Analytics for Audio and Video“ gesendet. Durch Deaktivieren dieser Option wird das Video-Tracking deaktiviert.

Wenn Sie diese Option aktivieren, *ohne* die Erweiterung „Adobe Media Analytics for Audio and Video“ installiert zu haben, hat diese Option keine Auswirkungen.

![image2019-7-22_12-4-23](assets/image2019-7-22_12-4-23.png)

### Datenelemente in der Dynamic Media Viewers-Erweiterung {#about-data-elements-in-the-dynamic-media-viewers-extension}

Der einzige Datenelementtyp, den die Dynamic Media Viewers-Erweiterung bietet, ist **[!UICONTROL Viewer-Ereignis]** aus der Dropdown-Liste **[!UICONTROL Datenelementtyp]**.

Wenn diese Option aktiviert ist, rendert der Datenelement-Editor ein Formular mit zwei Feldern:

* **[!UICONTROL Ereignisdatentyp DM-Viewer]** – eine Dropdown-Liste, die alle Viewer-Ereignisse identifiziert, die von der Dynamic Media Viewers-Erweiterung unterstützt werden und Argumente sowie ein spezielles **[!UICONTROL COMMON]**-Element aufweisen. Ein **[!UICONTROL COMMON]**-Element stellt eine Liste von Ereignisparametern dar, die allen von den Viewern gesendeten Ereignistypen gemein sind.
* **[!UICONTROL Tracking-Parameter]** – ein Argument des ausgewählten Dynamic Media Viewers-Ereignisses.

![image2019-7-22_12-5-46](assets/image2019-7-22_12-5-46.png)

Eine Liste der unterstützten Ereignisse nach Viewer-Typ finden Sie im [Dynamic Media Viewers-Referenzhandbuch](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers.html?lang=de#viewers-aem-assets-dmc). Konsultieren Sie den Abschnitt zum gewünschten Viewer und klicken Sie auf den Unterabschnitt „Support für Tracking mit Adobe Analytics“. Derzeit sind Ereignisargumente im Referenzhandbuch für Dynamic Media Viewers nicht dokumentiert.

Betrachten Sie nun den Lebenszyklus des *Datenelements* von Dynamic Media Viewers. Der Wert dieses Datenelements wird ausgefüllt, nachdem das entsprechende Dynamic Media-Viewer-Ereignis auf der Seite eintritt. Angenommen, das Datenelement verweist auf das Ereignis **[!UICONTROL LOAD]** und das zugehörige „asset“-Argument. In solchen Fällen empfängt der Wert dieses Datenelements gültige Daten, nachdem der Viewer das **[!UICONTROL LOAD]**-Ereignis zum ersten Mal ausgeführt hat. Wenn das Datenelement auf das **[!UICONTROL ZOOM]**-Ereignis und das zugehörige „scale“-Argument verweist, bleibt der Wert dieses Datenelements leer, bis der Viewer zum ersten Mal ein **[!UICONTROL ZOOM]**-Ereignis sendet.

Gleichermaßen werden die Werte von Datenelementen automatisch aktualisiert, wenn der Viewer ein entsprechendes Ereignis auf der Seite sendet. Der Wert wird auch dann aktualisiert, wenn das betreffende Ereignis nicht in der Regelkonfiguration angegeben ist. Angenommen, das Datenelement **[!UICONTROL ZoomScale]** wird für den Parameter „scale“ des ZOOM-Ereignisses definiert. Die einzige in der Regelkonfiguration vorhandene Regel wird jedoch durch das Ereignis **[!UICONTROL LOAD]** ausgelöst. Der Wert von **[!UICONTROL ZoomScale]** wird dennoch immer dann aktualisiert, wenn ein Benutzer im Viewer einen Zoom ausführt.

Jeder Dynamic Media-Viewer verfügt auf der Website über eine eindeutige Kennung. Das Datenelement verfolgt den Wert selbst und auch den Viewer, der den Wert ausgefüllt hat. Angenommen, es gibt mehrere Viewer auf derselben Seite und ein **[!UICONTROL AssetName]**-Datenelement, das auf das **[!UICONTROL LOAD]**-Ereignis und das zugehörige „asset“-Argument verweist. Das Datenelement **[!UICONTROL AssetName]** verwaltet eine Sammlung von Asset-Namen, die mit jedem auf der Seite geladenen Viewer verknüpft sind.

Der jeweilige vom Datenelement zurückgegebene Wert hängt vom Kontext ab. Wenn das Datenelement in einer Regel angefordert wird, die durch ein Dynamic Media-Viewer-Ereignis ausgelöst wurde, wird der Datenelementwert für den Viewer zurückgegeben, der die Regel initiiert hat. Und das Datenelement wird in einer Regel angefordert, die durch ein Ereignis einer anderen Experience Platform Tags-Erweiterung ausgelöst wurde. In diesem Fall kommt der Wert des Datenelements von dem Viewer, der dieses Datenelement zuletzt aktualisiert hat.

**Betrachten Sie das folgende Beispiel:**

* Eine Webseite mit zwei Dynamic Media-Zoom-Viewern: *viewer1* und *viewer2*.

* Das Datenelement **[!UICONTROL ZoomScale]** verweist auf das **[!UICONTROL ZOOM]**-Ereignis und das zugehörige „scale“-Argument.
* **[!UICONTROL TrackPan]**-Regel mit folgenden Eigenschaften:

   * Verwendet das Dynamic Media-Viewer-Ereignis **[!UICONTROL PAN]** als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]**-Datenelements an Adobe Analytics.

* **[!UICONTROL TrackKey]**-Regel mit folgenden Eigenschaften:

   * Verwendet das Tastendruckereignis der Experience Platform Tags-Core-Erweiterung als Auslöser.
   * Sendet den Wert des **[!UICONTROL ZoomScale]**-Datenelements an Adobe Analytics.

Nehmen wir nun an, dass der Endbenutzer die Web-Seite mit beiden Viewern lädt. In *Viewer1* zoomt er auf eine Skalierung von 50 %. In *Viewer2* zoomt er dann auf eine Skalierung von 25 %. In *Viewer1* schwenkt er das Bild und wählt schließlich eine Taste auf der Tastatur aus.

Die Aktivitäten des Endbenutzers führen dazu, dass die folgenden beiden Tracking-Aufrufe an Adobe Analytics gesendet werden:

* Der erste Aufruf erfolgt, weil die **[!UICONTROL TrackPan]**-Regel ausgelöst wird, wenn der Benutzer in *Viewer1* schwenkt. Dieser Aufruf sendet 50 % als Wert des **[!UICONTROL ZoomScale]**-Datenelements, da das Datenelement weiß, dass die Regel von *Viewer1* ausgelöst wird, und den entsprechenden Skalierungswert abruft.
* Der zweite Aufruf erfolgt, weil die **[!UICONTROL TrackKey]**-Regel ausgelöst wird, wenn der Benutzer eine Taste auf der Tastatur drückt. Bei diesem Aufruf werden 25 % als Wert des **[!UICONTROL ZoomScale]**-Datenelements gesendet, da die Regel nicht vom Viewer ausgelöst wurde. Daher gibt das Datenelement den aktuellsten Wert zurück.

Das oben aufgestellte Beispiel wirkt sich auch auf die Lebensdauer des Datenelementwerts aus. Der Wert des vom Dynamic Media-Viewer verwalteten Datenelements wird im Code der Experience Platform Tags-Bibliothek gespeichert, auch wenn der Viewer selbst auf der Web-Seite beendet wird. Diese Funktion bedeutet, dass das Datenelement den letzten bekannten Wert zurückgibt, wenn es eine Regel gibt, die nicht von einer Dynamic Media Viewers-Erweiterung ausgelöst wird und auf dieses Datenelement verweist. Das gilt auch, wenn der Viewer nicht mehr auf der Website vorhanden ist.

In jedem Fall werden Werte von Datenelementen, die von Dynamic Media Viewers gesteuert werden, nicht im lokalen Speicher oder auf dem Server gespeichert. Sie werden stattdessen nur in der Client-seitigen Experience Platform Tags-Bibliothek gespeichert. Die Werte solcher Datenelemente verschwinden, wenn die Web-Seite neu geladen wird.

Im Allgemeinen unterstützt der Datenelement-Editor eine [Festlegung der Speicherdauer](https://experienceleague.adobe.com/docs/experience-platform/tags/ui/data-elements.html?lang=de#create-a-data-element). Datenelemente, die die Dynamic Media Viewers-Erweiterung verwenden, unterstützen jedoch als Speicherdauer nur die Option **[!UICONTROL Ohne]**. Das Festlegen eines anderen Werts ist in der Benutzeroberfläche möglich, in diesem Fall wird jedoch das Verhalten des Datenelements nicht definiert. Die Erweiterung verwaltet den Wert des Datenelements selbst: das Datenelement, das den Wert des Viewer-Ereignisarguments während des gesamten Lebenszyklus des Viewers beibehält.

### Über Regeln in der Dynamic Media Viewers-Erweiterung {#about-rules-in-the-dynamic-media-viewers-extension}

Im Regeleditor werden mit der Erweiterung neue Konfigurationsoptionen für den Ereigniseditor hinzugefügt. Darüber hinaus gibt es im Editor eine Option zum manuellen Verweisen auf Ereignisparameter im Aktionseditor als schnelle Alternative zur Nutzung vorkonfigurierter Datenelemente.

#### Über den Ereigniseditor {#about-the-events-editor}

Im Ereigniseditor wird mit der Dynamic Media Viewers-Erweiterung ein **[!UICONTROL Ereignistyp]** namens **[!UICONTROL Viewer-Ereignis]** hinzugefügt.

Wenn diese Option aktiviert ist, rendert der Ereigniseditor die Dropdown-Liste **[!UICONTROL Dynamic Media-Viewer-Ereignisse]** und listet alle verfügbaren Ereignisse auf, die von Dynamic Media-Viewern unterstützt werden.

![image2019-8-2_15-13-1](assets/image2019-8-2_15-13-1.png)

#### Über den Aktionseditor {#about-the-actions-editor}

Mit der Dynamic Media Viewers-Erweiterung können Sie Ereignisparameter von Dynamic Media Viewers verwenden, um im Editor „Variablen festlegen“ der Adobe Analytics-Erweiterung Analysevariablen zuzuordnen.

Die einfachste Methode dazu besteht darin, den folgenden zweistufigen Vorgang durchzuführen:

* Definieren Sie zunächst ein oder mehrere Datenelemente, wobei jedes Datenelement einen Parameter eines Dynamic Media-Viewer-Ereignisses darstellt.
* Klicken Sie dann im Editor „Variablen festlegen“ der Adobe Analytics-Erweiterung auf das Auswahlsymbol **[!UICONTROL Datenelement]** (drei gestapelte Festplatten), um das Dialogfeld „Datenelement auswählen“ zu öffnen. Wählen Sie dann ein Datenelement aus.

![image2019-7-10_20-41-52](assets/image2019-7-10_20-41-52.png)

Es ist jedoch möglich, einen anderen Ansatz zu verwenden und die Erstellung von Datenelementen zu umgehen. Sie können direkt auf ein Argument in einem Dynamic Media Viewer-Ereignis verweisen. Geben Sie im Eingabefeld **[!UICONTROL value]** der Analytics-Variablenzuweisung den vollständig qualifizierten Namen des Ereignis-Arguments ein. Stellen Sie sicher, dass Sie um den Namen Prozentzeichen (%) setzen. Beispiel:

`%event.detail.dm.LOAD.asset%`

![image2019-7-12_19-2-35](assets/image2019-7-12_19-2-35.png)

Es gibt einen wichtigen Unterschied zwischen der Verwendung von Datenelementen und dem direkten Verweis auf ein Ereignisargument. Bei Datenelementen spielt es keine Rolle, welches Ereignis die Aktion „Variablen festlegen“ auslöst. Das Ereignis, das die Regel auslöst, muss nicht mit dem dynamischen Viewer verknüpft sein. Wählen Sie beispielsweise die Web-Seite aus der Core-Erweiterung aus. Bei Verwendung eines direkten Argumentverweises muss jedoch sichergestellt werden, dass das Ereignis, das die Regel auslöst, dem Ereignisargument entspricht, auf das es verweist.

Wenn Sie beispielsweise auf `%event.detail.dm.LOAD.asset%` verweisen, wird der richtige Asset-Name zurückgegeben, wenn die Regel durch das **[!UICONTROL LOAD]**-Ereignis der Dynamic Media Viewer-Erweiterung ausgelöst wird. Bei jedem anderen Ereignis wird jedoch ein leerer Wert zurückgegeben.

In der folgenden Tabelle sind die Dynamic Media Viewer-Ereignisse sowie die unterstützten Argumente aufgeführt:

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
   <td><code>BANNER</code><br /> </td>
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

**VORAUSSETZUNGEN**

Adobe empfiehlt, dass Sie die gesamte Dokumentation vor diesem Abschnitt gründlich durchlesen, damit Sie die vollständige Integration verstehen.

In diesem Abschnitt werden die Konfigurationsschritte erläutert, die zur Integration von Dynamic Media Viewern mit Adobe Analytics und Adobe Analytics for Audio and Video erforderlich sind. Zwar kann die Dynamic Media Viewer-Erweiterung in Experience Platform Tags auch für andere Zwecke verwendet werden, doch werden solche Szenarien in dieser Dokumentation nicht behandelt.

Für die Konfiguration Ihrer Integration verwenden Sie die folgenden Adobe-Produkte:

* Adobe Analytics – zum Konfigurieren von Tracking-Variablen und -Berichten.
* Experience Platform Tags – zum Definieren einer Eigenschaft, einer oder mehrerer Regeln und eines oder mehrerer Datenelemente, um das Viewer-Tracking zu ermöglichen.

Wenn diese Integrationslösung mit Experience Manager Sites verwendet wird, muss auch die folgende Konfiguration durchgeführt werden:

* [!DNL Adobe Developer Console]: Die Integration wird für Experience Platform Tags erstellt.
* Experience Manager-Autorenknoten – IMS-Konfiguration und Experience Platform Tags-Cloud-Konfiguration.

Vergewissern Sie sich, dass Sie bei der Konfiguration Zugriff auf eine Firma in Adobe Experience Cloud haben, für die Adobe Analytics und Experience Platform Tags bereits aktiviert sind.

## Konfigurieren von Adobe Analytics für die Integration {#configuring-adobe-analytics-for-the-integration}

Nach der Konfiguration von Adobe Analytics wird Folgendes für die Integration eingerichtet:

* Eine Report Suite ist vorhanden und ausgewählt.
* Analytics-Variablen stehen zum Empfang von Verfolgungsdaten zur Verfügung.
* Es gibt Berichte zur Anzeige der in Adobe Analytics erfassten Daten.

Siehe auch [Analytics-Implementierungshandbuch](https://experienceleague.adobe.com/docs/analytics/implementation/home.html?lang=de).

**So konfigurieren Sie Adobe Analytics für die Integration:**

1. Beginnen Sie, indem Sie über die Experience Cloud-[Startseite](https://experience.adobe.com/#/home) auf Adobe Analytics zugreifen. Klicken Sie in der Menüleiste auf das Symbol **[!UICONTROL Lösungen]** (eine Matrix mit drei mal drei Punkten) oben rechts auf der Seite und klicken Sie dann auf **[!UICONTROL Analytics]**.

   ![2019-07-22_18-08-47](assets/2019-07-22_18-08-47.png)

   Wählen Sie jetzt eine Report Suite aus.

### Auswahl einer Report Suite {#selecting-a-report-suite}

1. Wählen Sie rechts oben auf der Seite „Adobe Analytics“ rechts neben dem Feld **[!UICONTROL Berichte durchsuchen]** die gewünschte Report Suite aus der Dropdown-Liste. Wenn mehrere Report Suites verfügbar sind und Sie nicht sicher sind, welche verwendet werden soll, wenden Sie sich an Ihren Adobe Analytics-Administrator, um sich bei der Auswahl der zu verwendenden Report Suite helfen zu lassen.

   Im folgenden Screenshot hat ein Benutzer eine Report Suite mit dem Namen *DynamicMediaViewersExtensionDoc* erstellt und aus der Dropdown-Liste ausgewählt. Der Name der Report Suite ist nur ein Beispiel. Sie entscheiden selbst, welchen Report Suite-Namen Sie auswählen.

   Wenn keine Report Suite verfügbar ist, müssen Sie oder Ihr Adobe Analytics-Administrator eine erstellen, bevor Sie mit der Konfiguration fortfahren können.

   Siehe [Berichte und Report Suites](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/report-suites-admin.html?lang=de) und [Report Suite erstellen](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/t-create-a-report-suite.html?lang=de).

   In Adobe Analytics werden Report Suites unter **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]** verwaltet.

   ![2019-07-22_18-09-49](assets/2019-07-22_18-09-49.png)

   Richten Sie jetzt Adobe Analytics-Variablen ein.

### Einrichten von Adobe Analytics-Variablen {#setting-up-adobe-analytics-variables}

1. Bestimmen Sie eine oder mehrere Adobe Analytics-Variablen, die Sie zum Tracking des Verhaltens von Dynamic Media Viewers auf der Website verwenden möchten.

   Es lassen sich beliebige Variablentypen verwenden, die von Adobe Analytics unterstützt werden. Die Entscheidung über den Variablentyp (z. B. Custom Traffic [props] und Konversion [eVar]) hängt von den spezifischen Anforderungen Ihrer Analytics-Implementierung ab.

   Siehe [Übersicht über props und eVars](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/evar.html?lang=de#vars).

   Für die Zwecke dieser Dokumentation wird nur eine Variable „Custom Traffic (props)“ verwendet, da diese in einem Analytics-Bericht innerhalb weniger Minuten nach dem Ausführen einer Aktion auf einer Web-Seite verfügbar ist.

   Um eine neue Custom Traffic-Variable zu aktivieren, navigieren Sie in Adobe Analytics in der Symbolleiste zu **[!UICONTROL Admin]** > **[!UICONTROL Report Suites]**.

1. Wählen Sie auf der Seite **[!UICONTROL Report Suite Manager]** den richtigen Bericht aus und navigieren Sie dann in der Symbolleiste zu **[!UICONTROL Einstellungen bearbeiten]** > **[!UICONTROL Traffic]** > **[!UICONTROL Traffic-Variablen]**.
1. Wählen Sie eine nicht verwendete Variable aus, geben Sie ihr einen beschreibenden Namen (**[!UICONTROL Viewer-Asset (prop 30)]**) und ändern Sie das Kombinationsfeld in der Spalte „Aktiviert“ in „Aktiviert“.

   Der folgende Screenshot ist ein Beispiel für eine Custom Traffic-Variable ( **[!UICONTROL prop30]**) zur Verfolgung eines vom Viewer verwendeten Asset-Namens:

   ![image2019-6-26_23-6-59](assets/image2019-6-26_23-6-59.png)

1. Klicken Sie unten in der Variablenliste auf **[!UICONTROL Speichern]**.

### Einrichten eines Berichts {#setting-up-a-report}

1. Im Allgemeinen wird die Einrichtung eines Berichts in Adobe Analytics von den jeweiligen Projektanforderungen bestimmt. Die Einrichtung detaillierter Berichte ist daher für diese Integration nicht relevant.

   Es ist ausreichend zu wissen, dass Custom Traffic-Berichte automatisch in Adobe Analytics verfügbar werden, nachdem Sie unter [Einrichten von Adobe Analytics-Variablen](#setting-up-adobe-analytics-variables) Custom Traffic-Variablen eingerichtet haben.

   Beispielsweise ist der Bericht für **[!UICONTROL Viewer-Asset (prop 30)]** im Menü „Berichte“ unter **[!UICONTROL Custom Traffic]** > **[!UICONTROL Custom Traffic 21-30]** > **[!UICONTROL Viewer-Asset (prop 30)]** verfügbar.

   Beim Aufrufen dieses Berichts direkt nach der Erstellung von **[!UICONTROL Viewer-Asset (prop 30)]** werden keine Daten angezeigt; das ist an diesem Punkt der Integration zu erwarten.

   ![image2019-6-26_23-12-49](assets/image2019-6-26_23-12-49.png)

## Konfigurieren von Experience Platform Tags für die Integration {#configuring-adobe-launch-for-the-integration}

Nachdem Sie Experience Platform Tags konfiguriert haben, werden für die Integration folgende Schritte vorgenommen:

* Erstellung einer neuen Eigenschaft, um alle Konfigurationen zusammenzuhalten.
* Installation und Einrichtung von Erweiterungen. Der Client-seitige Code aller in der Eigenschaft installierten Erweiterungen wird in einer Bibliothek kompiliert. Diese Bibliothek wird später von der Web-Seite verwendet.
* Konfiguration von Datenelementen und Regeln. Diese Konfiguration bestimmt darüber, welche Daten von den Dynamic Media-Viewern erfasst werden, wann die Tracking-Logik ausgelöst wird und wohin die Daten des Viewers in Adobe Analytics gesendet werden.
* Veröffentlichen der Bibliothek.

**So konfigurieren Sie Experience Platform Tags für die Integration:**

1. Beginnen Sie, indem Sie über die Experience Cloud-[Startseite](https://experience.adobe.com/#/home) auf Experience Platform Tags zugreifen. Klicken Sie in der Menüleiste auf das Symbol **[!UICONTROL Lösungen]** (eine Matrix mit drei mal drei Punkten) oben rechts auf der Seite und klicken Sie dann auf **[!UICONTROL Tags]**.

   Alternativ können Sie [Experience Platform Tags direkt öffnen](https://launch.adobe.com/).

   ![image2019-7-8_15-38-44](assets/image2019-7-8_15-38-44.png)

### Erstellen einer Eigenschaft in Experience Platform Tags {#creating-a-property-in-adobe-launch}

Bei einer Eigenschaft in Experience Platform Tags handelt es sich um eine benannte Konfiguration, die alle Ihre Einstellungen zusammenhält. Es wird eine Bibliothek der Konfigurationseinstellungen erstellt und in verschiedenen Umgebungsebenen (Entwicklung, Staging und Produktion) veröffentlicht.

Siehe auch [Erstellen einer Experience Platform Tags-Eigenschaft](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/initial-configuration/configure-tags.html?lang=de).

1. Wählen Sie unter Experience Platform Tags **[!UICONTROL Neue Eigenschaft]** aus.
1. Geben Sie im Dialogfeld **[!UICONTROL Eigenschaft erstellen]** im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein, z. B. den Titel Ihrer Website. Beispiel: `DynamicMediaViewersProp.`
1. Geben Sie im Feld **[!UICONTROL Domains]** die Domain Ihrer Website ein.
1. Aktivieren Sie in der Dropdown-Liste **[!UICONTROL Erweiterte Optionen]** die Option **[!UICONTROL Für Erweiterungsentwicklung konfigurieren (kann später nicht mehr geändert werden)]**, falls die gewünschte Erweiterung (in diesem Fall *Dynamic Media Viewer*) noch nicht veröffentlicht wurde.

   ![image2019-7-8_16-3-47](assets/image2019-7-8_16-3-47.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

   Klicken Sie auf die neu erstellte Eigenschaft und fahren Sie dann mit der *Installation und Einrichtung von Erweiterungen* fort.

### Installieren und Einrichten von Erweiterungen {#installing-and-setup-of-extensions}

Alle verfügbaren Erweiterungen in Experience Platform Tags werden unter **[!UICONTROL Erweiterungen]** > **[!UICONTROL Katalog]** aufgeführt.

Um eine Erweiterung zu installieren, klicken Sie auf **[!UICONTROL Installieren]**. Führen Sie bei Bedarf eine einmalige Erweiterungskonfiguration durch und klicken Sie dann auf **[!UICONTROL Speichern]**.

Wenn erforderlich, müssen die folgenden Erweiterungen installiert und konfiguriert werden:

* (Erforderlich) *Experience Cloud ID-Dienst* -Erweiterung.

Es ist keine zusätzliche Konfiguration erforderlich; akzeptieren Sie die vorgeschlagenen Werte. Wenn Sie fertig sind, klicken Sie unbedingt auf **[!UICONTROL Speichern]**.

Siehe [Adobe Experience Cloud Identity Service-Erweiterung](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/id-service/overview.html?lang=de).

* (Erforderlich) *Adobe Analytics*-Erweiterung

Um diese Erweiterung zu konfigurieren, benötigen Sie die Report Suite-ID aus Adobe Analytics, die Sie unter **[!UICONTROL Admin]** > **[!UICONTROL Report Suite]** unter der Spaltenüberschrift **[!UICONTROL Report Suite-ID]** finden können.

(Die Report Suite-ID der Report Suite **[!UICONTROL DynamicMediaViewersExtensionDoc]** wird in den folgenden Screenshots nur zu Demonstrationszwecken verwendet. Diese ID wurde unter [Auswählen einer Report Suite](#selecting-a-report-suite) zuvor erstellt und eingesetzt.)

![image2019-7-8_16-45-34](assets/image2019-7-8_16-45-34.png)

Geben Sie auf der Seite „Erweiterung installieren“ die Report Suite-ID in das Feld **[!UICONTROL Report Suites Entwicklung]**, das Feld **[!UICONTROL Report Suites Staging]** und das Feld **[!UICONTROL Report Suites Produktion]** ein.

![image2019-7-8_16-47-40](assets/image2019-7-8_16-47-40.png)

*Konfigurieren Sie das folgende Element nur, wenn Sie Video-Tracking verwenden möchten:*

Erweitern Sie auf der Seite **[!UICONTROL Erweiterung installieren]** den Eintrag **[!UICONTROL Allgemein]** und geben Sie dann den Tracking-Server an. Der Tracking-Server folgt der Vorlage `<trackingNamespace>.sc.omtrdc.net`, wobei `<trackingNamespace>` die in der Bereitstellungs-E-Mail abgerufene Information darstellt.

Wählen Sie **[!UICONTROL Speichern]** aus.

Siehe [Adobe Analytics-Erweiterung](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/analytics/overview.html?lang=de).

* (Optional, nur erforderlich, wenn Video-Tracking benötigt wird) Erweiterung *Adobe Media Analytics for Audio and Video*

Füllen Sie das Feld für den Tracking-Server aus. Der Tracking-Server für die Erweiterung *Adobe Media Analytics for Audio and Video* unterscheidet sich von dem für Adobe Analytics verwendeten Tracking-Server. Er folgt der Vorlage `<trackingNamespace>.hb.omtrdc.net`, wobei `<trackingNamespace>` die Information aus der Bereitstellungs-E-Mail darstellt.

Alle anderen Felder sind optional.

Siehe [Erweiterung Adobe Media Analytics for Audio and Video](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/media-analytics/overview.html?lang=de).

* (Erforderlich) Erweiterung *Dynamic Media Viewer*

Wählen Sie **[!UICONTROL Adobe Analytics for Video aktivieren]**, um das Video-Heartbeat-Tracking zu aktivieren (einzuschalten).

Danach ist die Erweiterung *Dynamic Media Viewer* nur verfügbar, wenn die Experience Platform Tags-Eigenschaft für die Entwicklung erstellt wird.

Siehe [Erstellen einer Eigenschaft in Experience Platform Tags](#creating-a-property-in-adobe-launch).

Nachdem die Erweiterungen installiert und eingerichtet wurden, werden mindestens die folgenden fünf Erweiterungen (vier, wenn Sie kein Video verfolgen) im Bereich Erweiterungen > Installiert aufgeführt.

![image2019-7-22_12-7-36](assets/image2019-7-22_12-7-36.png)

### Einrichten von Datenelementen und Regeln {#setting-up-data-elements-and-rules}

Erstellen Sie in Experience Platform Tags Datenelemente und Regeln, die zum Tracking Dynamic Media-Viewern erforderlich sind.

Eine Übersicht über die Verfolgung mit Experience Platform Tags finden Sie unter [Funktionsweise der Daten- und Ereignisverfolgung in der Integration](#how-data-and-event-tracking-works-in-the-integration).

Unter [Beispielkonfiguration](#sample-configuration) finden Sie eine Beispielkonfiguration in Experience Platform Tags, die zeigt, wie ein Asset-Name beim Laden des Viewers verfolgt wird.

Detaillierte Informationen zu den Funktionen der Erweiterung finden Sie unter [Konfigurieren der Erweiterung „Dynamic Media Viewer“](#configuring-the-dynamic-media-viewers-extension).

### Bibliothek veröffentlichen {#publishing-a-library}

Um Änderungen an der Experience Platform Tags-Konfiguration vorzunehmen (einschließlich eingerichteter Eigenschaften, Erweiterungen, Regeln und Datenelemente), müssen Sie diese Änderungen *veröffentlichen*. Die Veröffentlichung in Experience Platform Tags erfolgt über die Registerkarte „Publishing“ unter der Eigenschaftskonfiguration.

Experience Platform Tags kann über mehrere Entwicklungsumgebungen, eine Staging-Umgebung und eine Produktionsumgebung verfügen. Standardmäßig verweist die Experience Platform Tags Cloud-Konfiguration in Experience Manager den Experience Manager-Autorenknoten auf die Staging-Umgebung von Experience Platform Tags. Der Experience Manager-Veröffentlichungsknoten verweist auf die Produktionsumgebung von Experience Platform Tags. Deshalb muss mit den Standardeinstellungen für Experience Manager die Experience Platform Tags-Bibliothek in der Staging-Umgebung veröffentlicht werden. Auf diese Weise kann die Bibliothek im Experience Manager-Autorenknoten verwendet werden. Sie können sie dann in der Produktionsumgebung veröffentlichen, damit sie im Veröffentlichungsknoten von Experience Manager verwendet werden kann.

Weitere Informationen zu Experience Platform Tags-Umgebungen finden Sie unter [Umgebungen](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/environments/environments.html?lang=de).

Das Veröffentlichen einer Bibliothek umfasst die folgenden zwei Schritte:

* Hinzufügen und Erstellen einer neuen Bibliothek, indem alle erforderlichen Änderungen (neue und Aktualisierungen) in die Bibliothek aufgenommen werden.
* Verschieben der Bibliothek durch die verschiedenen Umgebungsebenen (von „Entwicklung“ über „Staging“ zu „Produktion“)

#### Hinzufügen und Erstellen einer neuen Bibliothek {#adding-and-building-a-new-library}

1. Wenn Sie die Registerkarte „Publishing“ in Experience Platform Tags zum ersten Mal öffnen, ist die Bibliotheksliste leer.

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
   >Wenn Sie das nächste Mal Änderungen an Ihrer Experience Platform Tags-Konfiguration vornehmen, wechseln Sie zur Registerkarte **[!UICONTROL Publishing]** unter der Konfiguration **[!UICONTROL Eigenschaft]** und klicken Sie auf Ihre zuvor erstellte Bibliothek.
   >
   >
   >Klicken Sie im Bildschirm zur Bibliotheksveröffentlichung auf **[!UICONTROL Alle geänderten Ressourcen hinzufügen]** und klicken Sie dann auf **[!UICONTROL Für Entwicklung speichern und erstellen]**.

#### Verschieben einer Bibliothek durch Umgebungsebenen {#moving-a-library-up-through-environment-levels}

1. Nachdem Sie eine neue Bibliothek hinzugefügt haben, befindet sich diese in der Entwicklungsumgebung. Um sie auf die Ebene der Staging-Umgebung (was der Spalte „Gesendet“ entspricht) zu verschieben, klicken Sie im Dropdown-Menü der Bibliothek auf **[!UICONTROL Zur Genehmigung senden]**.

   ![image2019-7-15_15-52-37](assets/image2019-7-15_15-52-37.png)

1. Klicken Sie im Bestätigungsdialogfeld auf **[!UICONTROL Senden]**.

   Nachdem die Bibliothek in die Spalte „Gesendet“ verschoben wurde, wählen Sie im Dropdown-Menü der Bibliothek **[!UICONTROL Für Staging erstellen]** aus.

   ![image2019-7-15_15-54-37](assets/image2019-7-15_15-54-37.png)

1. Um die Bibliothek von der Staging-Umgebung in die Produktionsumgebung (die Spalte „Veröffentlicht“) zu verschieben, führen Sie einen ähnlichen Vorgang aus.

   Wählen Sie zunächst im Dropdown-Menü **[!UICONTROL Veröffentlichung genehmigen]** aus.

   ![image2019-7-15_16-7-39](assets/image2019-7-15_16-7-39.png)

1. Wählen Sie im Dropdown-Menü **[!UICONTROL Für Produktion erstellen und veröffentlichen]** aus.

   ![image2019-7-15_16-8-9](assets/image2019-7-15_16-8-9.png)

   Weitere Informationen zum Veröffentlichungsverfahren in Experience Platform Tags finden Sie unter [Veröffentlichung](https://experienceleague.adobe.com/docs/experience-platform/tags/publish/overview.html?lang=de).

## Konfigurieren von Adobe Experience Manager für die Integration {#configuring-adobe-experience-manager-for-the-integration}

Voraussetzungen:

* Experience Manager führt sowohl die Autoren- als auch die Veröffentlichungsinstanz aus.
* Der Experience Manager-Autorenknoten wird im Scene7-Ausführungsmodus von Dynamic Media (dynamicmedia_s7) eingerichtet.
* WCM-Komponenten für Dynamic Media sind in Experience Manager Sites aktiviert.

Die Experience Manager-Konfiguration besteht aus den folgenden zwei Hauptschritten:

* Konfiguration von Experience Manager IMS.
* Konfiguration der Experience Platform Tags Cloud.

### Experience Manager IMS konfigurieren {#configuring-aem-ims}

1. Klicken Sie im Experience Manager-Autorenknoten auf das **[!UICONTROL Werkzeugsymbol]** (Hammer) und navigieren Sie dann zu **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**.

   ![2019-07-25_11-52-58](assets/2019-07-25_11-52-58.png)

1. Klicken Sie auf der Seite „Adobe IMC-Konfigurationen“ links oben auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** die Option **[!UICONTROL Experience Platform Tags]** aus.
1. Aktivieren Sie **[!UICONTROL Neues Zertifikat erstellen]** und geben Sie dann in das Textfeld einen beliebigen aussagekräftigen Wert für das Zertifikat ein. Beispiel: *AdobeLaunchIMSCert*. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**.

   Die folgende Informationsmeldung wird angezeigt:

   *Um ein gültiges Zugriffstoken abzurufen, wird der öffentliche Schlüssel des neuen Zertifikats zum technischen Konto in Adobe Developer Console* hinzugefügt!

   Um das Dialogfeld „Informationen“ zu schließen, klicken Sie auf **[!UICONTROL OK]**.

   ![2019-07-25_12-09-24](assets/2019-07-25_12-09-24.png)

1. Um eine Datei mit öffentlichem Schlüssel (&#42;.crt) in Ihr lokales System herunterzuladen, wählen Sie **[!UICONTROL Öffentlichen Schlüssel herunterladen]** aus.

   >[!NOTE]
   >
   >***Lassen Sie jetzt*** die Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** geöffnet; schließen Sie die Seite ***nicht*** und klicken Sie ***nicht*** auf „Weiter“. Sie werden in den späteren Schritten noch zu dieser Seite zurückkehren.

   ![2019-07-25_12-52-24](assets/2019-07-25_12-52-24.png)

1. Navigieren Sie in einer neuen Browser-Registerkarte zur [[!DNL Adobe Developer Console]](https://developer.adobe.com/console/integrations).

1. Wählen Sie auf der Seite **[!UICONTROL Adobe Developer Console-Integrationen]** rechts oben **[!UICONTROL Neue Integration]** aus.
1. Vergewissern Sie sich, dass im Dialogfeld **[!UICONTROL Neue Integration erstellen]** das Optionsfeld **[!UICONTROL Zugriff auf API]** ausgewählt ist, und klicken Sie dann auf **[!UICONTROL Weiter]**.

   ![2019-07-25_13-04-20](assets/2019-07-25_13-04-20.png)

1. Aktivieren Sie auf der zweiten Seite von **[!UICONTROL Neue Integration erstellen]** das Optionsfeld **[!UICONTROL Experience Platform Tagd-API]**. Klicken Sie unten rechts auf der Seite auf **[!UICONTROL Fortsetzen]**.

   ![2019-07-25_13-13-54](assets/2019-07-25_13-13-54.png)

1. Gehen Sie auf der dritten Seite von **[!UICONTROL Neue Integration erstellen]** wie folgt vor:

   * Geben Sie im Feld **[!UICONTROL Name]** einen beschreibenden Namen ein. Beispielsweise *DynamicMediaViewersIO*.

   * Geben Sie im Feld **[!UICONTROL Beschreibung]** eine Beschreibung für die Integration ein.

   * Laden Sie im Bereich **[!UICONTROL Zertifikate mit öffentlichem Schlüssel]** Ihre Datei mit öffentlichem Schlüssel (&#42;.cert) hoch, die Sie in den Schritten zuvor heruntergeladen haben.

   * Wählen Sie unter der Überschrift **[!UICONTROL Rolle für Experience Platform Tags-API auswählen]** die Option **[!UICONTROL Admin]**.

   * Wählen Sie unter der Überschrift **[!UICONTROL Ein oder mehrere Produktprofile für die Experience Platform Tags-API auswählen]** das Produktprofil **[!UICONTROL Tags – &lt;your_company_name>]**.

   ![2019-07-25_13-49-18](assets/2019-07-25_13-49-18.png)

1. Wählen Sie **[!UICONTROL Integration erstellen]** aus.
1. Klicken Sie auf der Seite **[!UICONTROL Integration erstellt]** auf **[!UICONTROL Weiter zu Integrationsdetails]**.

   ![2019-07-25_14-16-33](assets/2019-07-25_14-16-33.png)

1. Es wird eine Seite mit Integrationsdetails **** (ähnlich der folgenden) angezeigt:

   >[!NOTE]
   >
   >***Lassen Sie die Seite mit Integrationsdetails geöffnet***. In wenigen Augenblicken benötigen Sie verschiedene Informationen aus den Registerkarten **[!UICONTROL Übersicht]** und **[!UICONTROL JWT]**.

   ![2019-07-25_14-35-30](assets/2019-07-25_14-35-30.png)

   Seite mit Integrationsdetails.

1. Kehren Sie zur Seite **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** zurück, die Sie zuvor offen gelassen haben. Klicken Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Weiter]**, um die Seite **[!UICONTROL Konto]** im Fenster **[!UICONTROL Technische Kontokonfiguration für Adobe IMS]** zu öffnen.

   Wenn Sie die Seite zuvor geschlossen haben, kehren Sie zum Experience Manager-Autorenknoten zurück und navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**. Wählen Sie **[!UICONTROL Erstellen]**. Wählen Sie in der Dropdown-Liste **[!UICONTROL Cloud-Lösung]** die Option **[!UICONTROL Experience Platform Tags]**. Wählen Sie in der Dropdown-Liste **[!UICONTROL Zertifikat]** den Namen des zuvor erstellten Zertifikats aus.)

   ![2019-07-25_20-57-50](assets/2019-07-25_20-57-50.png)

   Technische Kontokonfiguration für Adobe IMS – Zertifikatsseite.

1. Die Seite **[!UICONTROL Konto]** enthält fünf Felder, in denen Sie Informationen von der Seite „Integrationsdetails“ (vorheriger Schritt) ausfüllen müssen.

   ![2019-07-25_20-42-45](assets/2019-07-25_20-42-45.png)

   Technische Kontokonfiguration für Adobe IMS – Kontoseite.

1. Füllen Sie auf der Seite **[!UICONTROL Konto]** die folgenden Felder aus:

   * **[!UICONTROL Titel]**: Geben Sie einen beschreibenden Kontonamen ein.
   * **[!UICONTROL Autorisierungs-Server]**: Kehren Sie zur Seite mit den Integrationsdetails zurück, die Sie zuvor geöffnet haben. Klicken Sie auf die Registerkarte **[!UICONTROL JWT]**. Kopieren Sie den Server-Namen – ohne Pfad – wie unten hervorgehoben.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie den Namen in das entsprechende Feld ein.
Beispiel: `https://ims-na1.adobelogin.com/`
(Der Server-Name ist nur ein Beispiel.)

   ![2019-07-25_15-01-53](assets/2019-07-25_15-01-53.png)

   Seite mit Integrationsdetails – Registerkarte „JWT“

1. **[!UICONTROL API-Schlüssel]**: Kehren Sie zur Seite mit Integrationsdetails zurück. Klicken Sie auf die Registerkarte **[!UICONTROL Überblick]** und dann rechts neben dem Feld **[!UICONTROL API-Schlüssel (Client-ID)]** auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Schlüssel in das entsprechende Feld ein.

   ![2019-07-25_14-35-333](assets/2019-07-25_14-35-333.png)

   Seite mit Integrationsdetails.

1. **[!UICONTROL Client-Geheimnis]**: Kehren Sie zur Seite mit Integrationsdetails zurück. Klicken Sie auf der Registerkarte **[!UICONTROL Überblick]** auf **[!UICONTROL Client-Geheimnis abrufen]**. Klicken Sie rechts neben dem Feld **[!UICONTROL Client-Geheimnis]** auf **[!UICONTROL Kopieren]**.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie dann den Schlüssel in das entsprechende Feld ein.

1. **[!UICONTROL Payload]**: Kehren Sie zur Seite „Integrationsdetails“ zurück. Kopieren Sie auf der Registerkarte **[!UICONTROL JWT]** im Feld „JWT-Payload“ den gesamten JSON-Objekt-Code.

   Kehren Sie zur Seite **[!UICONTROL Konto]** zurück und fügen Sie den Code in das entsprechende Feld ein.

   ![2019-07-25_21-59-12](assets/2019-07-25_21-59-12.png)

   Seite mit Integrationsdetails – Registerkarte „JWT“

   Die Kontoseite mit allen ausgefüllten Feldern sieht in etwa wie folgt aus:

   ![2019-07-25_22-08-30](assets/2019-07-25_22-08-30.png)

1. Klicken Sie oben rechts auf der Seite **[!UICONTROL Konto]** auf **[!UICONTROL Erstellen]**.

   Wenn Experience Manager IMS konfiguriert ist, befindet sich jetzt unter **[!UICONTROL Adobe IMS-Konfigurationen]** ein neues IMS-Konto.

   ![image2019-7-15_14-17-54](assets/image2019-7-15_14-17-54.png)

## Konfigurieren von Experience Platform Tags Cloud für die Integration {#configuring-adobe-launch-cloud-for-the-integration}

1. Klicken Sie im Experience Manager-Autorenknoten in der oberen linken Ecke auf das **[!UICONTROL Werkzeugsymbol]** (Hammer), navigieren Sie dann zu **[!UICONTROL Cloud Services]** > **[!UICONTROL Experience Platform Tags-Konfigurationen]**.

   ![26.07.2019_12-10-38](assets/2019-07-26_12-10-38.png)

1. Wählen Sie auf der Seite **[!UICONTROL Experience Platform Tags-Konfigurationen]** im linken Bereich eine Experience Manager-Website aus, auf die Sie Ihre Experience Platform Tags-Konfiguration anwenden möchten.

   Die Website **`We.Retail`** ist im folgenden Screenshot nur zur Veranschaulichung ausgewählt.

   ![26.07.2019_12-20-06](assets/2019-07-26_12-20-06.png)

1. Klicken Sie links oben auf der Seite auf **[!UICONTROL Erstellen]**.
1. Füllen Sie auf der Seite **[!UICONTROL Allgemein]** (1/3 Seiten) des Fensters **[!UICONTROL Experience Platform Tags-Konfiguration erstellen]** die folgenden Felder aus:

   * **[!UICONTROL Titel]** – Geben Sie einen beschreibenden Konfigurationsnamen ein. Beispiel: `We.Retail Tags cloud configuration`.

   * **[!UICONTROL Zugewiesene Adobe IMS-Konfiguration]** – Wählen Sie die IMS-Konfiguration aus, die Sie zuvor unter [Konfigurieren von Experience Manager IMS](#configuring-aem-ims) erstellt haben.

   * **[!UICONTROL Firma]** – Wählen Sie aus der Dropdown-Liste **[!UICONTROL Firma]** Ihre Experience Cloud-Firma aus. Die Liste wird automatisch ausgefüllt.

   * **[!UICONTROL Eigenschaft]** – Wählen Sie in der Dropdown-Liste „Eigenschaft“ die zuvor erstellte Experience Platform Tags-Eigenschaft aus. Die Liste wird automatisch ausgefüllt.

   Nachdem Sie alle Felder ausgefüllt haben, sieht Ihre Seite **[!UICONTROL Allgemein]** wie folgt aus:

   ![image2019-7-15_14-34-23](assets/image2019-7-15_14-34-23.png)

1. Klicken Sie links oben auf **[!UICONTROL Weiter]**.
1. Füllen Sie auf der Seite **[!UICONTROL Staging]** (2/3 Seiten) des Fensters **[!UICONTROL Experience Platform Tags-Konfiguration erstellen]** die folgenden Felder aus:

   Überprüfen Sie im Feld **[!UICONTROL URI der Bibliothek]** (Uniform Resource Identifier) den Speicherort der Staging-Version Ihrer Experience Platform Tags-Bibliothek. Experience Manager füllt dieses Feld automatisch aus.

   Dieser Schritt verwendet nur zu Beispielzwecken Experience Platform-Tags-Bibliotheken, die auf Adobe CDN bereitgestellt werden.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass der automatisch ausgefüllte Bibliotheks-URI (Uniform Resource Identifier) nicht fehlerhaft ist. Korrigieren Sie ihn ggf. so, dass der URI einen protokollrelativen URI darstellt. Das heißt, er beginnt mit einem doppelten Schrägstrich.
   >
   >
   >Beispiel: `//assets.adobetm.com/launch-xxxx`.

   Ihre **[!UICONTROL Staging]**-Seite sieht in etwa wie folgt aus: Die Optionen **[!UICONTROL Archiv]** und **[!UICONTROL Bibliothek asynchron laden]** sind hier ***nicht*** festgelegt:

   ![image2019-7-15_15-21-8](assets/image2019-7-15_15-21-8.png)

1. Klicken Sie rechts oben auf **[!UICONTROL Weiter]**.
1. Korrigieren Sie auf der Seite **[!UICONTROL Produktion]** (3/3 Seiten) des Fensters **[!UICONTROL Experience Platform Tags-Konfiguration erstellen]** bei Bedarf den automatisch ausgefüllten Produktions-URI ähnlich wie auf der vorherigen **[!UICONTROL Staging]**-Seite.
1. Klicken Sie rechts oben auf **[!UICONTROL Erstellen]**.

   Ihre neue Experience Platform Tags Cloud-Konfiguration wird jetzt erstellt und neben Ihrer Website aufgeführt, ähnlich wie im folgenden Beispiel:

1. Wählen Sie Ihre neue Experience Platform Tags Cloud-Konfiguration aus (bei Auswahl wird links neben dem Konfigurationstitel ein Häkchen angezeigt). Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichen]** aus.

   ![image2019-7-15_15-47-6](assets/image2019-7-15_15-47-6.png)

Derzeit unterstützt der Experience Manager-Autorenknoten nicht die Integration von Dynamic Media Viewern mit Experience Platform Tags.

Sie wird jedoch im Experience Manager-Veröffentlichungsknoten unterstützt. Bei Verwendung der Standardeinstellungen der Experience Platform Tags Cloud-Konfiguration wird für den Experience Manager-Veröffentlichungsknoten die Produktionsumgebung von Experience Platform Tags verwendet. Daher müssen Experience Platform Tags-Bibliotheksaktualisierungen jedes Mal beim Test von der Entwicklungsumgebung in die Produktionsumgebung verschoben werden.

Es gibt eine Möglichkeit, diese Einschränkung zu umgehen. Geben Sie in der Experience Platform Tags Cloud-Konfiguration für den Experience Manager-Veröffentlichungsknoten oben die Entwicklungs- oder Staging-URL der Platform Tags-Bibliothek an. Dadurch verwendet der Experience Manager-Veröffentlichungsknoten die Entwicklungs- oder Staging-Version der Experience Platform Tags-Bibliothek.

Weitere Informationen zum Einrichten der Experience Platform Tags Cloud-Konfiguration finden Sie unter [Integrieren von Experience Manager mit Experience Platform Tags über  [!DNL Adobe Developer Console]](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/integrations/experience-platform-data-collection-tags/overview.html?lang=de).
