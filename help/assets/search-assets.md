---
title: Suchen nach digitalen Assets und Bildern in [!DNL Adobe Experience Manager].
description: Learn how to find the required assets in [!DNL Adobe Experience Manager] by using Filters panel, and how to use the assets that show up in search.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '5869'
ht-degree: 57%

---


# Search assets in [!DNL Adobe Experience Manager] {#search-assets-in-aem}

[!DNL Adobe Experience Manager Assets] bietet stabile Methoden zur Ermittlung von Assets, mit denen Sie eine höhere Inhaltsgeschwindigkeit erzielen können. Ihre Teams reduzieren die Time-to-Market mit einer nahtlosen, intelligenten Sucherfahrung, indem Sie vordefinierte Funktionen und benutzerdefinierte Methoden verwenden. Die Suche nach Assets spielt bei der Nutzung eines Digital-Asset-Management-Systems eine zentrale Rolle – sowohl für eine weitere Verwendung durch Kreativprofis als auch für eine robuste Verwaltung von Assets durch Geschäftsbenutzer und Marketing-Experten oder für die Verwaltung durch DAM-Administratoren. Simple, advanced, and custom searches that you can perform via [!DNL Assets] user interface or other apps and surfaces help fulfill these use cases.

[!DNL Experience Manager Assets] unterstützt folgende Anwendungsfälle und in diesem Artikel werden Verwendung, Konzepte, Konfigurationen, Einschränkungen und Fehlerbehebung für diese Fälle beschrieben.

| Suchen von Assets | Konfiguration und Verwaltung | Arbeiten mit Suchergebnissen |
|---|---|---|
| [Einfache Suchvorgänge](#searchbasics) | [Suchindex](#searchindex) | [Ergebnisse sortieren](#sort) |
| [Benutzeroberfläche für Suchen](#searchui) | [Visuelle Suche oder Ähnlichkeitssuche](#configvisualsearch) | [Eigenschaften und Metadaten eines Assets überprüfen](#checkinfo) |
| [Suchvorschläge](#searchsuggestions) | [Obligatorische Metadaten](#mandatorymetadata) | [Download](#download) |
| [Suchergebnisse und -verhalten verstehen](#searchbehavior) | [Suchfacetten ändern](#searchfacets) | [Massenaktualisierung von Metadaten](#metadataupdates) |
| [Such-Ranking und -Optimierung](#searchrank) | [Textextraktion](#extracttextupload) | [Smart-Sammlungen](#collections) |
| [Erweiterte Suche: Filtern und Suchbereich](#scope) | [Benutzerdefinierte Prädikate](#custompredicates) | [Unerwartete Ergebnisse und Fehlerbehebung](#troubleshoot-unexpected-search-results-and-issues) |
| [Suchen Sie nach anderen Lösungen und Apps](#beyondomnisearch):<ul><li>[Adobe Asset Link](#aal)</li><li>[Brand Portal](#brandportal)</li><li>[Experience Manager Desktop-App](#desktopapp)</li><li>[Adobe Stock-Fotos](#adobestock)</li><li>[Dynamic Media-Assets](#dynamicmedia)</li></ul> |  |  |
| [Asset-Auswahl](#assetselector) |  |  |
| [Einschränkungen](#limitations) und [Tipps](#tips) |  |  |
| [Illustrierte Beispiele](#samples) |  |  |

Search for assets using the Omnisearch field at the top of the [!DNL Experience Manager] web interface. Go to **[!UICONTROL Assets]** > **[!UICONTROL Files]** in [!DNL Experience Manager], click search icon in top bar, enter search keyword, and press return. Alternativ können Sie den Suchbegriff-Shortcut / (Schrägstrich) verwenden, um das Omniture-Suchfeld zu öffnen. `Location:Assets` ist vorausgewählt, um die Suche auf DAM-Assets zu begrenzen. [!DNL Experience Manager] bietet Vorschläge, wie Ihr Beginn einen Suchbegriff eingeben kann.

Verwenden Sie das Bedienfeld &quot; **[!UICONTROL Filter]** &quot;, um die Suche einzuschränken, indem Sie die Suchergebnisse auf Grundlage der verschiedenen Optionen (Prädikate) filtern, z. B. Dateityp, Dateigröße, Datum der letzten Änderung, Status des Assets, Insight-Daten und Adobe Stock-Lizenzierung. Ihre Administratoren können das Bedienfeld &quot;Filter&quot;anpassen und mithilfe von Suchfacetten Suchvorhersagen hinzufügen oder entfernen. Der [!UICONTROL Dateityp] -Filter im Bedienfeld &quot; [!UICONTROL Filter] &quot;enthält Kontrollkästchen mit gemischtem Status. Wenn Sie also nicht alle verschachtelten Prädikate (oder Formate) auswählen, werden die Kontrollkästchen der ersten Ebene teilweise markiert.

[!DNL Experience Manager] Suchfunktion unterstützt die Suche nach Sammlungen und die Suche nach Assets in einer Sammlung. Siehe [Suchen nach Sammlungen](/help/assets/managing-collections-touch-ui.md).

## Suchoberfläche verstehen {#searchui}

Machen Sie sich mit der Suchoberfläche und den verfügbaren Aktionen vertraut.

![Benutzeroberfläche der Suchergebnisse von Experience Manager Assets](assets/aem_search_results.png)

*Abbildung: Erkennen Sie die Oberfläche[!DNL Experience Manager Assets]der Suchergebnisse.*

**A.** Speichern Sie die Suche als intelligente Sammlung. **B.** Filter oder Vorhersagen zur Eingrenzung der Suchergebnisse. **C.** Anzeigen von Dateien, Ordnern oder beidem. **D.** Klicken Sie auf „Filter“, um die linke Leiste zu öffnen oder zu schließen. **E.** Die Suchposition ist DAM. **F.** Omniture Suchfeld mit benutzerdefiniertem Suchbegriff. **G.** Wählen Sie die geladenen Suchergebnisse aus. **H.** Anzahl der angezeigten Suchergebnisse aus den gesamten Suchergebnissen. **I.** Schließen Sie die Suche **J.** Wechseln Sie zwischen der Ansicht der Karte und der Ansicht der Liste.

### Dynamische Suchfacetten {#dynamicfacets}

Sie können die gewünschten Assets schneller auf der Suchergebnisseite ausfindig machen, indem Sie die dynamisch aktualisierte Anzahl der erwarteten Suchergebnisse in den Suchfacetten verwenden. Die erwartete Anzahl an Assets wird noch vor Anwendung des Suchfilters aktualisiert. Durch Anzeige der erwarteten Anzahl im Filter können Sie schnell und effizient durch Suchergebnisse navigieren. For more info, see [Search assets in Experience Manager](search-assets.md).

![Anzeigen der ungefähren Asset-Anzahl ohne Filterung der Suchergebnisse in Suchfacetten](assets/asset_search_results_in_facets_filters.png)

*Abbildung: Sehen Sie sich die ungefähre Anzahl der Assets an, ohne die Suchergebnisse in den Suchfacetten zu filtern.*

## Suchergebnisse und -verhalten verstehen {#searchbehavior}

### Grundlegende Suchbegriffe und -ergebnisse {#searchbasics}

Sie können im OmniSearch-Feld mit Suchbegriffen suchen. Bei der Suche mit Suchbegriffen wird nicht zwischen Groß- und Kleinschreibung unterschieden und es handelt sich um eine Volltextsuche (über die gängigen Metadatenfelder hinweg. Wenn mehr als ein Suchbegriff gesucht wird, wird der Standardoperator zwischen den Suchbegriffen `AND` für die Standardsuche verwendet, `OR` wenn Assets mit intelligenten Tags versehen sind.

Die Ergebnisse werden nach Relevanz sortiert, beginnend mit den größten Übereinstimmungen. Bei mehreren Suchbegriffen sind Assets, die beide Begriffe in ihren Metadaten enthalten, relevanter. In Metadaten werden Suchbegriffe, die als Smart-Tags erscheinen, höher eingestuft als Suchbegriffe, die in anderen Metadatenfeldern auftauchen. [!DNL Experience Manager] bietet Ihnen die Möglichkeit, einem bestimmten Suchbegriff mehr Gewicht zu verleihen. Also, it is possible to [boost the rank](#searchrank) of a few targeted assets for specific search terms.

Zum schnellen Auffinden der benötigten Assets bietet die Rich-Oberfläche Filter-, Sortierungs- und Auswahlverfahren. Sie können Ergebnisse anhand mehrerer Kriterien filtern und für verschiedene Filter die Anzahl der durchsuchten Assets anzeigen. Alternativ können Sie die Suche erneut ausführen, indem Sie die Abfrage im OmniSearch-Feld ändern. Wenn Sie Suchbegriffe oder Filter ändern, bleiben die anderen Filter angewendet, um den Kontext Ihrer Suche zu wahren.

Wenn die Ergebnisse viele Assets sind, [!DNL Experience Manager] werden die ersten 100 in der Ansicht und 200 in der Ansicht Liste angezeigt. Wenn Benutzer einen Bildlauf durchführen, werden weitere Assets geladen. Dadurch soll die Leistung verbessert werden.

>[!VIDEO](https://www.youtube.com/watch?v=LcrGPDLDf4o)

Manchmal werden in den Suchergebnissen auch unerwartete Assets angezeigt. Weitere Informationen dazu finden Sie unter [Unerwartete Ergebnisse](#troubleshoot-unexpected-search-results-and-issues).

[!DNL Experience Manager] kann viele Dateiformate suchen und die Suchfilter können an Ihre geschäftlichen Anforderungen angepasst werden. Wenden Sie sich an Ihren Administrator, um zu verstehen, welche Suchoptionen für Ihr DAM-Repository verfügbar sind und welche Einschränkungen Ihr Konto hat.

### Ergebnisse mit und ohne erweiterte Smarttags {#withsmarttags}

By default, [!DNL Experience Manager] search combines the search terms with an AND clause. Suchen Sie beispielsweise nach einer Frau mit Keywords. In den Suchergebnissen werden standardmäßig nur die Assets angezeigt, bei denen in den Metadaten sowohl weibliche als auch ausgeführte Suchbegriffe aufgeführt sind. Das gleiche Verhalten wird beibehalten, wenn mit den Suchbegriffen Sonderzeichen (Punkte, Unterstriche oder Gedankenstriche) verwendet werden. Die folgenden Abfragen geben die gleichen Ergebnisse zurück:

* `woman running`
* `woman.running`
* `woman-running`

Die Abfrage `woman -running` gibt jedoch Assets ohne `running` Metadaten zurück.
Using smart tags adds an extra `OR` clause to find any of the search terms as the applied smart tags. An asset tagged with either `woman` or `running` using smart tags also appear in such a search query. Die Suchergebnisse sind also eine Kombination aus

* Assets with `woman` and `running` keywords in the metadata (default behavior).

* Assets smart getaggt mit einem der Suchbegriffe (Verhalten von Smarttags).

### Suchvorschläge bei der Eingabe {#searchsuggestions}

When you start typing keywords, [!DNL Experience Manager] suggests the possible search keywords or phrases. Die Vorschläge basieren auf den Metadaten der vorhandenen Assets. [!DNL Experience Manager] indiziert alle Metadatenfelder, um die Suche zu erleichtern. Zur Bereitstellung von Suchvorschlägen verwendet das System die Werte der folgenden Metadatenfelder. Um Suchvorschläge zu erhalten, können Sie die folgenden Felder mit geeigneten Suchbegriffen ausfüllen:

* Asset-Tags. (Zuordnung zu `jcr:content/metadata/cq:tags`)
* Asset-Titel. (Zuordnung zu `jcr:content/metadata/dc:title`)
* Asset-Beschreibung. (Zuordnung zu `jcr:content/metadata/dc:description`)
* Titel im JCR-Repository. Der Wert wird ggf. dem Asset-Titel zugeordnet. (Zuordnung zu `jcr:content/jcr:title`)
* Beschreibung im JCR-Repository. Der Wert wird ggf. der Asset-Beschreibung zugeordnet. (Zuordnung zu `jcr:content/jcr:description`)

Um Vorschläge für mehr als einen Suchbegriff zu erhalten, geben Sie weiterhin alle Suchbegriffe ein, ohne einen Vorschlag für einen einzelnen Suchbegriff auszuwählen.

![Geben Sie mehrere Suchbegriffe in Ansichten ein, die allen entsprechen](assets/search_suggestionsmanykeywords.gif)

*Abbildung: Geben Sie mehrere Suchbegriffe ein, um Vorschläge zur Ansicht einzugeben.*

### Such-Ranking und -Optimierung {#searchrank}

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.

Sie können die Relevanz von Suchbegriffen für bestimmte Assets verbessern, um die auf Suchbegriffen basierenden Suchen zu optimieren. D. h. die Bilder, für die Sie bestimmte Suchbegriffe festlegen, erscheinen bei der Suche nach diesen Suchbegriffen oben in den Suchergebnissen.

1. From the [!DNL Assets] user interface, open the properties page for the asset. Click **[!UICONTROL Advanced]** and click **[!UICONTROL Add]** under **[!UICONTROL Elevate for search keywords]**.
1. In the **[!UICONTROL Search Promote]** box, specify a keyword for which you want to boost the search for the image and then click **[!UICONTROL Add]**. Sie können auf dieselbe Weise mehrere Suchbegriffe eingeben.
1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Das Asset, das Sie für diesen Suchbegriff erhöht haben, befindet sich unter den obersten Suchergebnissen.

So können Sie das Ranking bestimmter Assets in den Suchergebnissen für den jeweiligen Suchbegriff erhöhen. Siehe Beispielvideo unten. For detailed info, see [search in Experience Manager](https://helpx.adobe.com/experience-manager/kt/assets/using/search-feature-video-use.html).

>[!VIDEO](https://video.tv.adobe.com/v/16766/?quality=6)

*Erfahren Sie, wie Suchergebnisse ihren Rang erhalten und wie der Rang beeinflusst werden kann.*

## Erweiterte Suche {#scope}

[!DNL Experience Manager] bietet verschiedene Methoden wie Filter, die sich auf die durchsuchten Assets anwenden lassen, damit Sie gewünschte Assets schneller finden können. Nachfolgend werden einige häufig verwendete Methoden beschrieben. Im Folgenden werden einige [illustrierte Beispiele](#samples) vorgestellt.

**Nach Dateien oder Ordnern suchen**: In den Suchergebnissen sehen Sie entweder Dateien, Ordner oder beides. Wählen Sie im Bedienfeld **[!UICONTROL Filter]** die entsprechende Option aus. Siehe [Suchoberfläche](#searchui).

**In einem Ordner nach Assets suchen**: Sie können die Suche auf einen bestimmten Ordner beschränken. Fügen Sie im Bedienfeld **[!UICONTROL Filter]** den Pfad eines Ordners hinzu. Sie können immer nur einen Ordner auf einmal hinzufügen.

![Suchergebnisse durch Hinzufügen eines Ordnerpfads im Bedienfeld „Filter“ auf einen Ordner begrenzen](assets/search_folder_select.gif)

*Abbildung: Beschränken Sie die Suchergebnisse auf einen Ordner, indem Sie im Bedienfeld &quot;Filter&quot;einen Ordnerpfad hinzufügen.*

### Ähnliche Bilder suchen {#visualsearch}

Wenn Sie Bilder suchen möchten, die einem vom Benutzer ausgewählten Bild ähneln, klicken Sie in der Kartenansicht eines Bildes oder in der Symbolleiste auf **[!UICONTROL Ähnliche suchen]**. [!DNL Experience Manager] zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. Siehe [Konfigurieren der Ähnlichkeitssuche](#configvisualsearch).

![Suchen Sie ähnliche Bilder mithilfe der Option in der Ansicht der Karte](assets/search_find_similar.png)

*Abbildung: Suchen Sie ähnliche Bilder mithilfe der Option in der Ansicht.*

### Adobe Stock-Fotos {#adobestock}

From within the [!DNL Experience Manager] user interface, users can search [Adobe Stock assets](/help/assets/aem-assets-adobe-stock.md) and license the required assets. Fügen Sie `Location: Adobe Stock` in der OmniSearch-Leiste hinzu. Sie können auch das Bedienfeld „Filter“ verwenden, um alle lizenzierten oder nicht lizenzierten Assets zu suchen bzw. mit der Adobe Stock-Dateinummer nach einem bestimmten Asset suchen.

### Dynamic Media-Assets {#dmassets}

Sie können nach Dynamic Media-Bildern filtern, indem Sie die Option **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** im Bedienfeld **[!UICONTROL Filter]** auswählen. Dadurch werden Assets wie Bildsets, Karussells, gemischte Mediensets und Rotationssets gefiltert und angezeigt.

### Mit bestimmten Werten in Metadatenfeldern suchen {#gqlsearch}

Sie können nach Assets suchen, die auf exakten Werten bestimmter Metadatenfelder wie Titel, Beschreibung und Autor basieren. Die Volltextsuchfunktion GQL ruft nur jene Assets ab, deren Metadatenwert exakt mit Ihrer Suchanfrage übereinstimmt. Bei den Namen der Eigenschaften (z. B. Autor, Titel usw.) und Werten wird zwischen Groß- und Kleinschreibung unterschieden.

| Metadatenfeld | Facettenwert und Nutzung |
| ----------------------------------------- | ------------------------------------- |
| Titel | title:John |
| Ersteller | creator:John |
| Standort | location:NA |
| Beschreibung | description:&quot;Sample Image&quot; |
| Erstellungswerkzeug | creatortool:&quot;Adobe Photoshop CC 2015&quot; |
| Urheberrechtsbesitzer | copyrightowner:&quot;Adobe Systems&quot; |
| Mitarbeiter | contributor:John |
| Nutzungsbedingungen | usageterms:„CopyRights Reserved“ |
| Erstellt | created:YYYY-MM-DDTHH |
| Ablaufdatum | expires:YYYY-MM-DDTHH |
| Einschaltzeit | ontime:YYYY-MM-DDTHH |
| Ausschaltzeit | offtime:YYYY-MM-DDTHH |
| Zeitraum (expires dateontime,offtime) | facet field : lowerbound..upperbound |
| Pfad | /content/dam/&lt;Ordnername> |
| PDF-Titel | pdftitle:„Adobe Document“ |
| Betreff | subject:„Training“ |
| Tags | tags:„Location And Travel“ |
| Typ | type:&quot;image\png&quot; |
| Bildbreite | width:lowerbound..upperbound |
| Bildhöhe | height:lowerbound..upperbound |
| Person | person:John |

Die Eigenschaften „path“, „limit“, „size“ und „orderby“ können nicht über OR mit einer anderen Eigenschaft verknüpft werden.

Der Suchbegriff für eine von einem Benutzer erstellte Eigenschaft ist ihre Feldbeschriftung im Eigenschafteneditor in Kleinbuchstaben und ohne Leerzeichen.

Im Folgenden finden Sie einige Beispiele für Suchformate für komplexe Abfragen:

* So zeigen Sie alle Assets mit mehreren Facettenfeldern an (wie: title=John Doe und creator tool = Adobe Photoshop):     `tiltle:"John Doe" creatortool : Adobe*`
* So zeigen Sie alle Assets an, wenn der Facettenwert nicht ein einzelnes Wort, sondern ein Satz ist (wie: title=Scott Reynolds): `title:"Scott Reynolds"`
* So zeigen Sie alle Assets mit mehreren Werten für eine einzelne Eigenschaft an (wie: title=Scott Reynolds oder John Doe): `title:"Scott Reynolds" OR "John Doe"`
* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge beginnen (wie: title ist Scott Reynolds): `title:Scott*`
* So zeigen Sie Assets an, deren Eigenschaftswerte mit einer bestimmten Zeichenfolge enden (wie: title ist Scott Reynolds): `title:*Reynolds`
* So zeigen Sie Assets mit einem Eigenschaftswert an, der eine bestimmte Zeichenfolge enthält (wie: title=Basel Meeting Room): `title:*Meeting*`
* So zeigen Sie Assets an, die eine bestimmte Zeichenfolge enthalten und einen bestimmten Eigenschaftswert aufweisen (wie die Suche nach der Zeichenfolge „Adobe“ in Assets mit title=John Doe): `*Adobe* title:"John Doe"`

## Search assets from other [!DNL Experience Manager] offerings or interfaces {#beyondomnisearch}

[!DNL Adobe Experience Manager] verbindet das DAM-Repository mit verschiedenen anderen [!DNL Experience Manager] Lösungen, um einen schnelleren Zugriff auf digitale Assets zu ermöglichen und die kreativen Workflows zu optimieren. Jede Asset-Erkennung beginnt mit dem Durchsuchen oder Suchen. Das Suchverhalten ist über die verschiedenen Oberflächen und Lösungen hinweg weitgehend gleich. Some search methods change as the target audience, the use cases, and the user interface vary across the [!DNL Experience Manager] solutions. Die genauen Methoden für die einzelnen Lösungen sind unter den unten stehenden Links dokumentiert. Die allgemein anwendbaren Tipps und Verhaltensweisen werden in diesem Artikel beschrieben.

### Nach Assets über das Bedienfeld „Adobe Asset Link“ suchen {#aal}

Using Adobe Asset Link, the creative professionals can now access content stored in [!DNL Experience Manager Assets], without leaving the supported Adobe Creative Cloud apps. Kreative können mit dem In-App-Bedienfeld in folgenden Creative Cloud-Programmen Assets nahtlos suchen, durchsuchen sowie ein- und auschecken: Photoshop, Illustrator und InDesign. Asset Link ermöglicht es Benutzern auch, nach visuell ähnlichen Ergebnissen zu suchen. Die Ergebnisse der visuellen Suchanzeige basieren auf den maschinellen Lernalgorithmen von Adobe Sensei und helfen Benutzern dabei, optisch ähnliche Bilder zu finden. Siehe [Assets suchen und durchsuchen](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html#UseAdobeAssetLink) mit Adobe Asset Link.

### Search assets in [!DNL Experience Manager] desktop app {#desktopapp}

Creative professionals use the desktop app to make the [!DNL Experience Manager Assets] easily searchable and available on their local desktop (Win or Mac). Creatives can easily reveal the desired assets in Mac Finder or Windows Explorer, opened in desktop applications, and changed locally - the changes are saved back to [!DNL Experience Manager] with a new version created in the repository. The application supports basic searches using one or more keywords, `*` and `?` wildcards, and `AND` operator. Siehe [Assets durchsuchen und suchen sowie Vorschau für Assets anzeigen](https://docs.adobe.com/content/help/de-DE/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) im Desktop-Programm.

### Search assets in [!DNL Brand Portal] {#brandportal}

Geschäftsbenutzer und Marketing-Experten nutzen Brand Portal, um genehmigte digitale Assets effizient und sicher mit erweiterten internen Teams, Partnern und Wiederverkäufern zu teilen. Siehe [Suchen von Assets in Brand Portal](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/search-capabilities/brand-portal-searching.html).

### Suchen [!DNL Adobe Stock] von Bildern {#adobestock-1}

From within the [!DNL Experience Manager] user interface, users can search Adobe Stock assets and license the required assets. Fügen Sie `Location: Adobe Stock` im OmniSearch-Feld hinzu. Sie können auch das Bedienfeld **[!UICONTROL Filter]** verwenden, um alle lizenzierten oder nicht lizenzierten Assets zu suchen bzw. mit der Adobe Stock-Dateinummer ein bestimmtes Asset zu suchen. See [manage Adobe Stock images in Experience Manager](/help/assets/aem-assets-adobe-stock.md#usemanage).

### Suchen nach Dynamic Media-Assets {#dynamicmedia}

Sie können nach Dynamic Media-Bildern filtern, indem Sie die Option **[!UICONTROL Dynamic Media]** > **[!UICONTROL Sets]** im Bedienfeld **[!UICONTROL Filter]** auswählen. Dadurch werden Assets wie Bildsets, Karussells, gemischte Mediensets und Rotationssets gefiltert und angezeigt. Beim Erstellen von Web-Seiten können Autoren in der Inhaltssuche nach Sets suchen. Ein Filter für Sets ist in einem Popup-Menü verfügbar.

### Suchen nach Assets in der Inhaltssuche beim Erstellen von Web-Seiten {#contentfinder}

Autoren können mit der Inhaltssuche das DAM-Repository nach den relevanten Assets durchsuchen und die Assets auf den von ihnen erstellten Web-Seiten verwenden. Autoren können auch die Funktion &quot;Connected Assets&quot;verwenden, um nach Assets zu suchen, die in einer Remote- [!DNL Experience Manager] Bereitstellung verfügbar sind. Autoren können diese Assets dann auf Webseiten in einer lokalen [!DNL Experience Manager] Bereitstellung verwenden. See [use remote assets](/help/assets/use-assets-across-connected-assets-instances.md#use-remote-assets).

### Suchen nach Sammlungen {#collections}

[!DNL Experience Manager] Suchfunktion unterstützt die Suche nach Sammlungen und die Suche nach Assets in einer Sammlung. Siehe [Suchen nach Sammlungen](/help/assets/managing-collections-touch-ui.md).

## Asset-Auswahl {#assetselector}

Mit der Asset-Auswahl können Sie die DAM-Assets auf besondere Weise suchen, filtern und durchsuchen. Asset Picker is available at `https://[aem-server]:[port]/aem/assetpicker.html`. Mit dieser Funktion können Sie die Metadaten der ausgewählten Assets abrufen. Sie können ihn mit unterstützten Anfrageparametern wie dem Asset-Typ (Bild, Video, Text) und dem Auswahlmodus (eine oder mehrere Auswahlen) starten. Diese Parameter legen den Kontext der Asset-Auswahl für eine bestimmte Suchinstanz fest und bleiben während der Auswahl intakt.

The asset Picker uses the HTML5 `Window.postMessage` message to send data for the selected asset to the recipient. Die Elementauswahl funktioniert nur im Durchsuchen-Modus und nur mit der Omniture Suchergebnisseite.

Sie können die folgenden Anforderungsparameter in einer URL übergeben, um die Asset-Auswahl in einem bestimmten Kontext zu starten:

| Name | Werte | Beispiel | Zweck |
|---|---|---|---|
| resource suffix (B) | Ordnerpfad als Ressourcensuffix in der URL:[https://localhost:4502/aem/assetpicker.html/&lt;Ordnerpfad>](https://localhost:4502/aem/assetpicker.html) | To launch the asset Picker with a particular folder selected, for example with the folder `/content/dam/we-retail/en/activities` selected, the URL should be of the form: [https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images](https://localhost:4502/aem/assetpicker.html/content/dam/we-retail/en/activities?assettype=images) | Wenn beim Starten des Asset-Wählers ein bestimmter Ordner ausgewählt sein soll, können Sie ihn als Ressourcensuffix übergeben. |
| mode | single, multiple | <ul><li>[https://localhost:4502/aem/assetpicker.html?mode=single](https://localhost:4502/aem/assetpicker.html?mode=single)</li><li>[https://localhost:4502/aem/assetpicker.html?mode=multiple](https://localhost:4502/aem/assetpicker.html?mode=multiple)</li></ul> | Im Modus „multiple“ können Sie mit dem Asset-Wähler mehrere Assets gleichzeitig auswählen. |
| mimetype | MIME-Typen (`/jcr:content/metadata/dc:format`) eines Assets (Platzhalter wird ebenfalls unterstützt) | <ul><li>[https://localhost:4502/aem/assetpicker.html?mimetype=image/png](https://localhost:4502/aem/assetpicker.html?mimetype=image/png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*png)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation)</li><li>[https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png](https://localhost:4502/aem/assetpicker.html?mimetype=*presentation&amp;mimetype=*png)</li></ul> | Verwenden Sie diese Option zum Filtern von Assets anhand von MIME-Typen. |
| dialog | true, false | [https://localhost:4502/aem/assetpicker.html?dialog=true](https://localhost:4502/aem/assetpicker.html?dialog=true) | Verwenden Sie diese Parameter, um den Asset-Wähler als Granite-Dialogfeld zu öffnen. Diese Option ist nur relevant, wenn Sie den Asset-Wähler per Granite-Pfadfeld starten und als pickerSrc-URL konfigurieren. |
| assettype (S) | images, documents, multimedia, archives | <ul><li>[https://localhost:4502/aem/assetpicker.html?assettype=images](https://localhost:4502/aem/assetpicker.html?assettype=images)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=documents](https://localhost:4502/aem/assetpicker.html?assettype=documents)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=multimedia](https://localhost:4502/aem/assetpicker.html?assettype=multimedia)</li><li>[https://localhost:4502/aem/assetpicker.html?assettype=archives](https://localhost:4502/aem/assetpicker.html?assettype=archives)</li></ul> | Verwenden Sie diese Option, um die Asset-Typen basierend auf dem übergebenen Wert zu filtern. |
| root | &lt;Ordnerpfad> | [https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities](https://localhost:4502/aem/assetpicker.html?assettype=images&amp;root=/content/dam/we-retail/en/activities) | Verwenden Sie diese Option, um den Stammordner für den Asset-Wähler anzugeben. In diesem Fall können Sie mit dem Asset-Wähler nur untergeordnete Assets (direkt/indirekt) unter dem Stammordner auswählen. |

To access the asset Picker interface, go to `https://[aem_server]:[port]/aem/assetpicker`. Navigieren Sie zum gewünschten Ordner und wählen Sie mindestens ein Asset aus. Alternativ können Sie im OmniSearch-Feld nach dem gewünschten Asset suchen, je nach Bedarf filtern und das Asset dann auswählen.

![Asset in der Asset-Auswahl suchen und auswählen](assets/assetpicker.png)

*Abbildung: Durchsuchen Sie das Asset und wählen Sie es in der Asset-Auswahl aus.*

## Beschränkungen {#limitations}

The search capability in [!DNL Experience Manager Assets] has the following limitations:

* Beginnen Sie die Suchanfrage nicht mit einem Leerzeichen, da die Suche sonst nicht funktioniert.
* [!DNL Experience Manager] zeigt den Suchbegriff ggf. weiter an, nachdem Sie Eigenschaften eines Assets aus den Suchergebnissen ausgewählt und die Suche dann abgebrochen haben. <!-- (CQ-4273540) -->
* Bei der Suche nach Ordnern bzw. Dateien und Ordnern können die Suchergebnisse mit keinem anderen Parameter sortiert werden.
* If you press return without typing anything in Omnisearch bar, [!DNL Experience Manager] returns a list of only files and not folders. If you search specifically for folders without using a keyword, [!DNL Experience Manager] does not return any results.
* Verwenden Sie die Option &quot;Alle **[!UICONTROL auswählen]** &quot;in der oberen rechten Ecke der Suchseite, um die gesuchten Assets auszuwählen. [!DNL Experience Manager] zeigt zunächst 100 Assets in der Ansicht der Karten und 200 Assets in der Ansicht der Liste an. Während des Bildlaufs der Suchergebnisse werden weitere Assets geladen. Sie können mehr Assets als die geladenen Assets auswählen. Die Anzahl der ausgewählten Assets wird oben rechts auf der Suchergebnisseite angezeigt. Sie können die Auswahl bearbeiten, indem Sie beispielsweise die ausgewählten Assets herunterladen, die Metadateneigenschaften stapelweise für die ausgewählten Assets aktualisieren oder die ausgewählten Assets einer Sammlung hinzufügen. Wenn mehr Assets ausgewählt als angezeigt werden, wird entweder eine Aktion auf alle ausgewählten Assets angewendet oder ein Dialogfeld zeigt die Anzahl der Assets an, auf die sie angewendet werden. Um eine Aktion auf die Assets anzuwenden, die nicht geladen wurden, stellen Sie sicher, dass alle Assets explizit ausgewählt sind.

Visuelle Suchen oder Ähnlichkeitssuchen weisen die folgenden Einschränkungen auf:

* Die visuelle Suche funktioniert am besten mit größeren Repositorys. Zwar ist keine Mindestanzahl von Bildern für gute Ergebnisse erforderlich, doch ist die Qualität der Treffer bei einigen Bildern möglicherweise nicht so hoch wie bei Treffern aus einem großen Repository.
* You cannot change the model or train [!DNL Experience Manager] to find similar images. Das Hinzufügen oder Entfernen von Smart-Tags zu bzw. von einigen Assets verändert das Modell beispielsweise nicht. Die Assets werden aus den visuell ähnlichen Suchergebnissen ausgeschlossen.

Die Suchfunktion weist in den folgenden Szenarien möglicherweise Leistungseinschränkungen auf:

* Die Ansicht der Karten ist schneller als die Ansicht der Liste, die Suchergebnisse anzuzeigen.

## Suchtipps {#tips}

* Wenn Sie den Prüfungsstatus von Assets überwachen, verwenden Sie die entsprechende Option, um herauszufinden, welche Assets genehmigt wurden und für welche Assets die Genehmigung aussteht.
* Verwenden Sie das Prädikat „Einblicke“, um basierend auf den Nutzungsstatistiken diverser Creative Cloud-Programme nach unterstützten Assets zu suchen. Nutzungsdaten werden unter Nutzungsbewertung, Impressions, Klicks und Medienkanäle gruppiert, in denen die Assets anhand von Kategorien angezeigt werden.
* Aktivieren Sie das Kontrollkästchen &quot;Alle **[!UICONTROL auswählen]** &quot;, um die gesuchten Assets auszuwählen. [!DNL Experience Manager] zeigt zunächst 100 Assets in der Ansicht der Karten und 200 Assets in der Ansicht der Liste an. Während des Bildlaufs der Suchergebnisse werden weitere Assets geladen. Sie können mehr Assets als die geladenen Assets auswählen. Die Anzahl der ausgewählten Assets wird oben rechts auf der Suchergebnisseite angezeigt. Sie können die Auswahl bearbeiten, indem Sie beispielsweise die ausgewählten Assets herunterladen, die Metadateneigenschaften stapelweise für die ausgewählten Assets aktualisieren oder die ausgewählten Assets einer Sammlung hinzufügen. Wenn mehr Assets ausgewählt als angezeigt werden, wird entweder eine Aktion auf alle ausgewählten Assets angewendet oder ein Dialogfeld zeigt die Anzahl der Assets an, auf die sie angewendet werden. Um eine Aktion auf die Assets anzuwenden, die nicht geladen wurden, stellen Sie sicher, dass alle Assets explizit ausgewählt sind.
* Informationen zum Suchen nach Assets, die keine obligatorischen Metadaten enthalten, finden Sie unter [Obligatorische Metadaten](#mandatorymetadata).
* Die Suche nutzt alle Metadatenfelder. Eine allgemeine Suche, z. B. nach 12, gibt in der Regel viele Ergebnisse zurück. Für bessere Ergebnisse sollten Sie doppelte (nicht einfache) Anführungszeichen verwenden oder sicherstellen, dass die Zahl an ein Wort ohne Sonderzeichen angrenzt (z. B. *Schuh12*).
* Die Volltextsuche unterstützt Operatoren wie „-“, „^“ und andere. Um diese Buchstaben als alphabetische Zeichenfolgen zu suchen, setzen Sie den Suchausdruck in doppelte Anführungszeichen. Verwenden Sie z. B. „Notebook - Schönheit“ statt Notebook - Schönheit.
* Wenn es zu viele Suchergebnisse gibt, schränken Sie den [Suchbereich](#scope) ein, um die gewünschten Assets leichter finden zu können. Das funktioniert am besten, wenn Sie eine Ahnung davon haben, wie Sie besser nach den gewünschten Assets suchen können (z. B. nach einem bestimmten Dateityp, nach einem bestimmten Speicherort, nach bestimmten Metadaten usw.).

* **Tagging**: Mit Tags können Sie Assets kategorisieren, damit sie sich leichter durchsuchen und suchen lassen. Tagging hilft bei der Verbreitung der entsprechenden Taxonomie an andere Benutzer und Workflows. [!DNL Experience Manager] bietet Methoden zum automatischen Taggen von Assets mit den KI-Diensten von Adobe Sensei, die beim Taggen von Assets durch Verwendung und Training immer besser werden. Bei der Suche nach Assets werden die Smart-Tags berücksichtigt, wenn die Funktion in Ihrem Konto aktiviert ist. Sie funktioniert zusammen mit der integrierten Suchfunktion. Siehe [Suchverhalten](#searchbehavior). Um die Reihenfolge zu optimieren, in der die Suchergebnisse angezeigt werden, können Sie für einige ausgewählte Assets das [Such-Ranking optimieren](#searchrank).

* **Indizierung**: In den Suchergebnissen werden nur indizierte Metadaten und Assets zurückgegeben. Um eine bessere Abdeckung und Leistung zu erzielen, stellen Sie eine ordnungsgemäße Indizierung sicher und befolgen Sie die Best Practices. Siehe [Indizierung](#searchindex).

## Einige Beispiele zur Illustration der Suche {#samples}

Verwenden Sie doppelte Anführungszeichen um Suchbegriffe, um Assets zu finden, die den genauen Wortlaut in der genauen vom Benutzer angegebenen Reihenfolge enthalten.

![Suchverhalten mit und ohne Anführungszeichen](assets/search_with_quotes.gif)

*Abbildung: Suchverhalten mit und ohne Anführungszeichen.*

**Suche mit Sternchen als Platzhalter**: Wenn Sie die Suche erweitern möchten, verwenden Sie ein Sternchen vor oder nach dem Suchbegriff, um Treffer mit einer beliebigen Anzahl von Zeichen zu erhalten. Wenn Sie beispielsweise ohne Sternchen nach „run“ suchen, werden keine Assets zurückgegeben, die Varianten des Worts enthalten (auch in den Metadaten). Ein Sternchen ersetzt eine beliebige Anzahl von Zeichen. Beispiel:

* `run` gibt Assets mit dem genauen Suchbegriff „run“ zurück.
* `run*` gibt Assets mit „running“, „run“, „runaway“ usw. zurück.
* `*run` gibt „outrun“, „rerun“ usw. zurück.
* `*run*` gibt alle möglichen Kombinationen zurück.

![Illustration der Nutzung eines Sternchen-Platzhalters bei der Asset-Suche anhand eines Beispiels](assets/search_with_asterisk_run.gif)

*Abbildung: Die Verwendung eines Sternchen-Platzhalters bei der Asset-Suche anhand eines Beispiels.*

**Suchen mit Fragezeichen als Platzhalter**: Verwenden Sie zur Erweiterung der Suche ein oder mehrere Fragezeichen („?“), um Treffer mit der genauen Zeichenzahl zu erhalten. So gilt beispielsweise in der folgenden Illustration:

* Abfrage `run???` stimmt mit keinem Asset überein.

* Abfrage `run????` stimmt mit dem Wort `running` überein (vier Zeichen nach `run`).

* Abfrage `??run` stimmt mit dem Wort `rerun` überein (zwei Zeichen vor `run`).

![Illustration der Nutzung eines Fragezeichen-Platzhalters bei der Asset-Suche anhand eines Beispiels](assets/search_with_questionmark_run.gif)

*Abbildung: Die Verwendung des Platzhalters für Fragezeichen bei der Asset-Suche anhand eines Beispiels wird veranschaulicht.*

**Suchbegriff ausschließen**: Verwenden Sie einen Bindestrich, um nach Assets zu suchen, die einen Suchbegriff nicht enthalten. Beispielsweise gibt die Abfrage `running -shoe` Assets zurück, die `running`, aber nicht `shoe` enthalten. Gleichermaßen gibt die Abfrage `camp -night` Assets zurück, die `camp`, aber nicht `night` enthalten. Beachten Sie, dass die Abfrage `camp-night` Assets zurückgibt, die sowohl `camp` als auch `night` enthalten.

![Verwendung eines Bindestrichs zur Suche nach Assets, die keinen ausgeschlossenen Suchbegriff enthalten](assets/search_dash_exclude_keyword.gif)

*Abbildung: Verwendung eines Bindestrichs zur Suche nach Assets, die keinen ausgeschlossenen Suchbegriff enthalten.*

## Konfigurations- und Verwaltungsfunktionen in Bezug auf die Suchfunktion {#configadmin}

### Suchindexkonfigurationen {#searchindex}

Die Ermittlung von Assets beruht auf der Indexierung von DAM-Inhalten, einschließlich der Metadaten. Die schnellere und genaue Erkennung von Assets beruht auf optimierter Indexierung und geeigneten Konfigurationen. Siehe [Suchindex](/help/assets/performance-tuning-guidelines.md#search-indexes), [Eichen-Abfragen und Indexierung](/help/sites-deploying/queries-and-indexing.md)und [Best Practices](/help/sites-deploying/best-practices-for-queries-and-indexing.md).

### Visuelle Suche oder Ähnlichkeitssuche {#configvisualsearch}

Die visuelle Suche verwendet intelligentes Tagging und erfordert [!DNL Experience Manager] 6.5.2.0 oder höher. Führen Sie nach der Konfiguration der Funktion für intelligentes Tagging die folgenden Schritte aus.

1. Fügen Sie in [!DNL Experience Manager] CRXDE im `/oak:index/lucene` Knoten die folgenden Eigenschaften und Werte hinzu und speichern Sie die Änderungen.

   * `costPerEntry` Eigenschaft des Typs `Double` mit dem Wert `10`.

   * `costPerExecution` Eigenschaft des Typs `Double` mit dem Wert `2`.

   * `refresh` Eigenschaft des Typs `Boolean` mit dem Wert `true`.
   Diese Konfiguration ermöglicht Suchen vom entsprechenden Index.

1. Um einen Lucene-Index zu erstellen, erstellen Sie in CRXDE einen Knoten mit dem Namen `/oak:index/damAssetLucene/indexRules/dam:Asset/properties`des Typs `imageFeatures` `nt-unstructured`. Im `imageFeatures` Knoten

   * Hinzufügen `name` Eigenschaft des Typs `String` mit dem Wert `jcr:content/metadata/imageFeatures/haystack0`.

   * Hinzufügen `nodeScopeIndex` Eigenschaft des Typs `Boolean` mit dem Wert `true`.

   * Hinzufügen `propertyIndex` Eigenschaft des Typs `Boolean` mit dem Wert `true`.

   * Hinzufügen `useInSimilarity` Eigenschaft des Typs `Boolean` mit dem Wert `true`.
   Speichern Sie die Änderungen.

1. Zugriff `/oak:index/damAssetLucene/indexRules/dam:Asset/properties/predictedTags` und Hinzufügen `similarityTags` der Eigenschaft vom Typ `Boolean` mit dem Wert `true`.
1. Wenden Sie intelligente Tags auf die Assets in Ihrem [!DNL Experience Manager] Repository an. Erfahren Sie, [wie Sie Smarttags](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/smart-tags-technical-video-setup.html)konfigurieren.
1. Legen Sie in CRXDE im `/oak-index/damAssetLucene` Knoten die `reindex` Eigenschaft auf `true`. Speichern Sie die Änderungen.
1. (Optional) Wenn Sie über ein benutzerdefiniertes Suchformular verfügen, kopieren Sie die `/libs/settings/dam/search/facets/assets/jcr%3Acontent/items/similaritysearch` Node in `/conf/global/settings/dam/search/facets/assets/jcr:content/items`. Speichern Sie alle Änderungen.

Weitere Informationen zu [Smart-Tags in Experience Manager](https://helpx.adobe.com/experience-manager/kt/assets/using/smart-tags-feature-video-understand.html) und zur [Verwaltung von Smart-Tags](/help/assets/managing-smart-tags.md).

### Obligatorische Metadaten {#mandatorymetadata}

Geschäftsbenutzer, Administratoren oder DAM-Bibliothekare können einige Metadaten als obligatorische Metadaten definieren, die für die Geschäftsprozesse erforderlich sind. Aus verschiedenen Gründen fehlen bei einigen Assets diese Metadaten, z. B. ältere Assets oder Assets, die stapelweise migriert werden. Assets mit fehlenden oder ungültigen Metadaten werden basierend auf der Eigenschaft für indizierte Metadaten erkannt und gemeldet. Informationen zum Konfigurieren finden Sie unter [Erforderliche Metadaten](/help/assets/metadata-schemas.md#define-mandatory-metadata).

### Suchfacetten ändern {#searchfacets}

Um die Suchgeschwindigkeit zu erhöhen, suchen Sie [!DNL Experience Manager Assets] Angebote nach Facetten, mit denen Sie die Suchergebnisse filtern können. Das Bedienfeld &quot;Filter&quot;enthält standardmäßig einige Standardfacetten. Administratoren können das Bedienfeld &quot;Filter&quot;anpassen, um die Standardfacetten mithilfe der integrierten Prädikate zu ändern. [!DNL Experience Manager] bietet eine gute Sammlung von integrierten Prädikaten und einen Editor zum Anpassen der Facetten. Siehe [Suchfacetten](/help/assets/search-facets.md).

### Text beim Hochladen von Assets extrahieren {#extracttextupload}

Sie können konfigurieren, [!DNL Experience Manager] dass Text aus den Assets extrahiert wird, wenn Benutzer Assets wie PSD- oder PDF-Dateien hochladen. [!DNL Experience Manager] indiziert den extrahierten Text und hilft Benutzern, diese Assets anhand des extrahierten Textes zu suchen. See [upload assets](/help/assets/managing-assets-touch-ui.md#uploading-assets).

### Benutzerdefinierte Vorhersagen zum Filtern von Suchergebnissen {#custompredicates}

Mit Eigenschaften werden Facetten erstellt. Administratoren können die Suchfacetten im Bedienfeld &quot;Filter&quot;mithilfe vorkonfigurierter Voreinstellungen anpassen. Diese Vorhersagen können mithilfe von Überlagerungen angepasst werden. Siehe [Erstellen benutzerdefinierter Prädikate](/help/assets/searchx.md).

Sie können basierend auf den folgenden Eigenschaften nach digitalen Assets suchen. Filter, die für einige dieser Eigenschaften gelten, sind standardmäßig verfügbar, und einige andere Filter können benutzerdefiniert erstellt werden, um sie auf die anderen Eigenschaften anzuwenden.

| Suchfeld | Sucheigenschaftswerte |
|---|---|
| MIME-Typen  | Bilder, Dokumente, Multimedia, Archive oder Sonstige |
| Zuletzt geändert | Stunde, Tag, Woche, Monat oder Jahr |
| Dateigröße | Klein, Mittel oder Groß |
| Veröffentlichungsstatus | Veröffentlicht oder Veröffentlichung rückgängig gemacht |
| Genehmigungsstatus | Genehmigt oder Abgelehnt |
| Ausrichtung | Horizontal, Vertikal oder Quadrat |
| Stil | Farbe oder Schwarzweiß |
| Videohöhe | Wird als Mindest- oder Höchstwert angegeben. Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |
| Videobreite | Wird als Mindest- oder Höchstwert angegeben. Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |
| Videoformat | DVI, Flash, MPEG4, MPEG, OGG, Quicktime, WMV, WebM Der Wert wird in den Metadaten des Quellvideos und aller Darstellungen gespeichert. |
| Video-Codec | x264 Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |
| Video-Bitrate | Wird als Mindest- oder Höchstwert angegeben. Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |
| Audio-Codec | Libvorbis, Lame MP3, AAC-Kodierung. Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |
| Audiobitrate   | Wird als Mindest- oder Höchstwert angegeben. Der Wert wird nur in den Metadaten der Videoausgabeformate gespeichert. |

## Arbeiten mit Asset-Suchergebnissen {#aftersearch}

Sobald Ihnen durchsuchte Assets angezeigt werden, die Ihren Kriterien entsprechen, können Sie folgende typische Aufgaben mit diesen Suchergebnissen ausführen oder die folgenden Aktionen vornehmen:

* Metadateneigenschaften und andere Informationen anzeigen.
* Ein oder mehrere Assets herunterladen.
* Desktop-Aktionen verwenden, um die Assets im Desktop-Programm zu öffnen.
* Smart-Sammlungen erstellen.

### Sortieren von Suchergebnissen {#sort}

Das Sortieren von Suchergebnissen hilft Ihnen, erforderliche Assets schneller zu finden. Das Sortieren von Suchergebnissen ist in der Listenansicht möglich und nur, wenn Sie die Option **[!UICONTROL [Dateien](#searchui)]**im Bedienfeld**[!UICONTROL  Filter ]**auswählen.[!DNL Experience Manager Assets]nutzt eine Server-seitige Sortierung, um alle Assets (wie viele auch immer) in einem Ordner oder den Ergebnissen einer Suchanfrage schnell zu sortieren. Server-seitige Sortierung liefert schnellere und genauere Ergebnisse als Client-seitige Sortierung.

In der Listenansicht lassen sich die Suchergebnisse genauso sortieren, wie Sie Assets in einem beliebigen Ordner sortieren. Die Sortierung funktioniert mit diesen Spalten: Name, Titel, Status, Dimensionen, Größe, Bewertung, Nutzung, (Datum) erstellt, (Datum) geändert, (Datum) Veröffentlicht, Workflow und Checked-out.

Mehr über Einschränkungen bei der Sortierfunktion finden Sie unter [Einschränkungen](#limitations).

### Überprüfen fon detaillierten Informationen zu einem Asset {#checkinfo}

Sie können auf der Suchergebnisseite genauere Informationen zu gefundenen Assets anzeigen.

Um alle Metadaten eines Assets anzuzeigen, wählen Sie das Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**.

Um die Kommentare zu einem Asset oder den Versionsverlauf eines Assets zu überprüfen, klicken Sie auf das Asset, um eine große Vorschau zu öffnen. Öffnen Sie in der linken Leiste die Timeline und wählen Sie **[!UICONTROL Kommentare]** oder **[!UICONTROL Versionen]**. Sie können die Timeline-Aktivität genauso wie Kommentare oder Versionen auch in chronologischer Reihenfolge sortieren.

![Sortieren von Timeline-Einträgen für ein gesuchtes Asset](assets/sort_timeline_search_results.gif)

*Abbildung: Sortieren von Zeitleisteneinträgen für ein Suchelement*

### Herunterladen gesuchter Assets {#download}

Sie können die gesuchten Assets und ihre Ausgaben herunterladen, und zwar genauso wie normale Assets aus Ordnern. Wählen Sie in den Suchergebnissen mindestens ein Asset aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**.

### Massenaktualisierungen für Metadateneigenschaften {#metadataupdates}

Es lassen sich für die gängigen Metadatenfelder verschiedener Assets Massenaktualisierungen durchführen. Wählen Sie aus den Suchergebnissen ein oder mehrere Assets aus. Klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]** und aktualisieren Sie die Metadaten nach Bedarf. Klicken Sie abschließend auf **[!UICONTROL Speichern und schließen]**. Die zuvor vorhandenen Metadaten in den aktualisierten Feldern werden überschrieben.

For the assets that are available in a single folder or a collection, it is easier to [update the metadata in bulk](/help/assets/managing-multiple-assets.md) without using the search functionality. Bei Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, ist es schneller, durch Suchen eine Massenaktualisierung der Metadaten vorzunehmen.

### Smart-Sammlungen {#collections-1}

Eine Sammlung ist ein geordneter Satz von Assets, der Assets von verschiedenen Speicherorten enthalten kann, da Sammlungen lediglich Verweise auf diese Assets enthalten. Es gibt zwei Arten von Sammlungen:

* Eine statische Referenzliste mit Assets, Ordnern und anderen Sammlungen
* Eine dynamische Liste (Smart-Sammlung), die Assets in der Sammlung basierend auf einem Suchkriterium ausfüllt.

Sie können Smart-Sammlungen auf Grundlage der Suchkriterien erstellen. Wählen Sie im Bedienfeld **[!UICONTROL Filter]** die Option **[!UICONTROL Dateien]** und klicken Sie auf **[!UICONTROL Smart-Sammlung speichern]**. Siehe [Verwalten von Sammlungen](/help/assets/managing-collections-touch-ui.md).

## Fehlerbehebung bei unerwarteten Suchergebnissen und -problemen {#troubleshoot-unexpected-search-results-and-issues}

| Fehler, Probleme, Symptome | Möglicher Grund | Mögliche Lösung oder Verständnis des Problems |
|---|---|---|
| Falsche Ergebnisse bei der Suche nach Assets mit fehlenden Metadaten | When searching for assets that are missing the mandatory metadata, [!DNL Experience Manager] may display some assets that have valid metadata. Die Ergebnisse basieren auf der Eigenschaft &quot;Indizierte Metadaten&quot;. | Nach der Aktualisierung der Metadaten ist eine erneute Dekodierung erforderlich, um den korrekten Status der Asset-Metadaten widerzuspiegeln. Siehe [Obligatorische Metadaten](metadata-schemas.md#define-mandatory-metadata). |
| Zu viele Suchergebnisse | Umfassender Suchparameter. | Erwägen Sie, den [Suchbereich](#scope)zu beschränken. Die Verwendung intelligenter Tags kann zu mehr Suchergebnissen führen als erwartet. Siehe [Suchverhalten mit Smart-Tags](#withsmarttags). |
| Nicht zusammenhängende oder teilweise zugehörige Suchergebnisse | Das Suchverhalten ändert sich beim intelligenten Tagging. | Verstehen Sie, [wie sich die Suche nach intelligentem Tagging](#withsmarttags)verändert. |
| Keine Vorschläge zum automatischen Ausfüllen für Assets | Neu hochgeladene Assets werden noch nicht indiziert. Die Metadaten stehen nicht sofort als Vorschläge zur Verfügung, wenn Sie einen Suchbegriff in die Omniture Suchleiste eingeben. | [!DNL Assets] erstellt erst nach dem Ablauf eines Timeout-Zeitraums (standardmäßig eine Stunde) im Hintergrund einen Index der Metadaten für alle neu hochgeladenen oder aktualisierten Assets und fügt die Metadaten der Liste der Vorschläge hinzu. |
| Keine Suchergebnisse | <ul><li>Es sind keine Assets vorhanden, die Ihrer Abfrage entsprechen.</li><li>Vor der Abfrage der Suche wurde ein Leerzeichen hinzugefügt.</li><li>Ein nicht unterstütztes Metadatenfeld enthält den Suchbegriff, nach dem Sie suchen.</li><li>Die Ein- und Ausschaltzeit wurde für ein Asset konfiguriert und die Suche wurde während der Ausschaltzeit des Assets durchgeführt.</li></ul> | <ul><li>Suche mit einem anderen Suchbegriff. Alternativ können Sie (intelligente) Tagging verwenden, um die Suchergebnisse zu verbessern.</li><li>Dabei handelt es sich um eine [bekannte Einschränkung](#limitations).</li><li>Nicht alle Metadatenfelder werden bei Suchvorgängen berücksichtigt. Siehe [Suchbereich](#scope).</li><li>Suchen Sie später oder ändern Sie die Ein- und Ausschaltzeiten für die erforderlichen Assets.</li></ul> |
| Suchfilter/-vorhersage ist nicht verfügbar | <ul><li>Der Suchfilter ist entweder nicht konfiguriert.</li><li>Es ist nicht für Ihre Anmeldung verfügbar.</li><li>(Weniger wahrscheinlich) Die Suchoptionen werden nicht auf die verwendete Bereitstellung angepasst.</li></ul> | <ul><li>Wenden Sie sich an den Administrator, um zu prüfen, ob die Suchanpassungen verfügbar sind oder nicht.</li><li>Wenden Sie sich an den Administrator, um zu prüfen, ob Ihr Konto über die Berechtigung/Berechtigungen zur Verwendung der Anpassung verfügt.</li><li>Wenden Sie sich an den Administrator und überprüfen Sie die verfügbaren Anpassungen für die [!DNL Assets] Bereitstellung, die Sie verwenden.</li></ul> |
| Bei der Suche nach visuell ähnlichen Bildern fehlt ein erwartetes Bild | <ul><li>Bild ist in nicht verfügbar [!DNL Experience Manager].</li><li>Bild wird nicht indiziert. In der Regel, wenn es kürzlich hochgeladen wurde.</li><li>Bild ist nicht intelligent getaggt.</li></ul> | <ul><li>Hinzufügen Sie das Bild an [!DNL Assets].</li><li>Wenden Sie sich an Ihren Administrator, um das Repository erneut zu indizieren. Stellen Sie außerdem sicher, dass Sie den entsprechenden Index verwenden.</li><li>Wenden Sie sich an Ihren Administrator, um die relevanten Assets mit einem intelligenten Tag zu versehen.</li></ul> |
| Wenn Sie nach visuell ähnlichen Bildern suchen, wird ein irrelevantes Bild angezeigt | Visuelles Suchverhalten. | [!DNL Experience Manager] zeigt so viele potenziell passende Assets wie möglich an. Weniger relevante Bilder werden den Ergebnissen hinzugefügt, jedoch mit einem niedrigeren Such-Ranking. Die Qualität der Treffer und die Relevanz der gefundenen Assets nehmen ab, je weiter Sie nach unten scrollen. |
| Bei Auswahl und Verwendung der Suchergebnisse werden nicht alle gesuchten Assets verarbeitet | Die Option &quot;Alle  auswählen&quot;wählt nur die ersten 100 Suchergebnisse in der Ansicht der Karte und die ersten 200 Suchergebnisse in der Ansicht der Liste aus. |  |

>[!MORELIKETHIS]
>
>* [Implementierungshandbuch zur Experience Manager-Suche](https://docs.adobe.com/content/help/en/experience-manager-learn/sites/developing/search-tutorial-develop.html)
>* [Die erweiterte Konfiguration von Multi-Wert- und Tag-Suche sagt Folgendes voraus:](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/metadata/search-feature-video-use.html)
>* [Intelligente Übersetzungssuche konfigurieren](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/translation/smart-translation-search-technical-video-setup.html)

