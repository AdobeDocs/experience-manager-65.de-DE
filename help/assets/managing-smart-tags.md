---
title: Verwalten von Smart-Tags und Suchvorgängen
description: Aktualisieren oder entfernen Sie die ungenauen Smarttags, um die Relevanz von Tags zu verbessern
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Verwalten von Smart-Tags und Suchvorgängen {#manage-smart-tags-and-searches}

<!--
TBD: This article should be merged into a new, uber article for Smart Tags. Delete this article then. Cloud service article is merged.
-->

Sie können Smart-Tags kuratieren, um alle falschen Tags zu entfernen, die Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Sie können einem Tag auch einen höheren Rang zuweisen, um seine Relevanz im Hinblick auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Select the image, and then tap **[!UICONTROL Manage Tags]** from the toolbar.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. If you don&#39;t want the image to be searched based on a specific tag, select the tag and then tap **[!UICONTROL Delete]** from the toolbar. Alternatively, click/tap `X` symbol that appears beside the label.
1. To assign a higher rank to a tag, select the tag and tap **[!UICONTROL Promote]** from the toolbar. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Click/tap **[!UICONTROL Save]**, and then click/tap **[!UICONTROL OK]** to close the Success dialog.
1. Navigieren Sie zur Seite „Eigenschaften“ des betreffenden Bildes. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

## AEM-Suchergebnisse mit Smart-Tags {#understandsearch}

By default, AEM search combines the search terms with an `AND` clause. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Using smart tags adds an additional `OR` clause to find any of the search terms in the applies smart tags. For example, consider searching for `woman running`. Assets with just `woman` or just `running` keyword in the metadata do not appear in the search results by default. However, an asset tagged with either `woman` or `running` using smart tags appears in such a search query. Die Suchergebnisse sind also eine Kombination aus

* assets with `woman` and `running` keywords in the metadata.

* Assets, die über Smart-Tags mit einem der Schlüsselwörter getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. matches of `woman running` in the various metadata fields.
1. Übereinstimmungen `woman running` in Smart-Tags.
1. matches of `woman` or of `running` in smart tags.
