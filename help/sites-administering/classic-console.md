---
title: Tagging-Konsole der klassischen Benutzeroberfläche
description: Erfahren Sie mehr über die Tagging-Konsole der klassischen Adobe Experience Manager-Benutzeroberfläche.
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
docset: aem65
exl-id: 8c6ba22f-5555-4e3c-998a-9353bd44715b
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '887'
ht-degree: 100%

---


# Tagging-Konsole der klassischen Benutzeroberfläche{#classic-ui-tagging-console}

Dieser Abschnitt bezieht sich auf die Tagging-Konsole der klassischen Benutzeroberfläche.

Informationen zur Tagging-Konsole der Touch-optimierten Benutzeroberfläche finden Sie [hier](/help/sites-administering/tags.md#tagging-console).

So greifen Sie auf die Tagging-Konsole der klassischen Benutzeroberfläche zu:

* in der Autoreninstanz
* Melden Sie sich mit Administratorrechten an.
* Navigieren Sie zur Konsole, zum Beispiel [https://localhost:4502/tagging](https://localhost:4502/tagging).

![Fenster der klassischen Konsole](assets/managing_tags_usingthetagasministrationconsole.png)

## Erstellen von Tags und Namespaces {#creating-tags-and-namespaces}

1. Je nachdem, auf welcher Ebene sie beginnen, können Sie mithilfe des Befehls **Neu** ein Tag oder einen Namespace erstellen:

   Wenn Sie **Tags** auswählen, können Sie einen Namespace erstellen:

   ![Dialogfeld zur Namespace-Erstellung](assets/creating_tags_andnamespaces.png)

   Wenn Sie einen Namespace auswählen (zum Beispiel **Demo**), können Sie ein Tag innerhalb dieses Namespace erstellen:

   ![Dialogfeld zur Tag-Erstellung](assets/creating_tags_andnamespacesinnewnamespace.png)

1. Geben Sie in beiden Fällen Folgendes ein:

   * **Titel**
(*Erforderlich*) Der Anzeigetitel für das Tag. Auch wenn es bei der Eingabe keine verbotenen Zeichen gibt, wird empfohlen, keines dieser Sonderzeichen zu verwenden:

      * `colon (:)` – Namespace-Trennzeichen
      * `forward slash (/)` – Trennzeichen für untergeordnete Tags

     Diese Zeichen werden möglicherweise nicht angezeigt, wenn sie eingegeben werden.

   * **Name**
(*Erforderlich*) Der Knotenname für das Tag.

   * **Beschreibung**
(*Optional*) Eine Beschreibung für das Tag.

   * Wählen Sie **Erstellen** aus.

## Bearbeiten von Tags {#editing-tags}

1. Wählen Sie im rechten Bereich das zu bearbeitende Tag aus.
1. Klicken Sie auf **Bearbeiten**.
1. Sie können den **Titel** und die **Beschreibung** ändern.
1. Klicken Sie auf **Speichern**, um das Dialogfeld zu schließen.

## Löschen von Tags {#deleting-tags}

1. Wählen Sie im rechten Bereich das zu löschende Tag aus.
1. Klicken Sie auf **Löschen**.
1. Klicken Sie auf **Ja**, um das Dialogfeld zu schließen.

   Das Tag sollte nicht mehr aufgeführt werden.

## Aktivieren und Deaktivieren von Tags {#activating-and-deactivating-tags}

1. Wählen Sie im rechten Bereich das Tag oder den Namespace aus, das bzw. der aktiviert (veröffentlicht) oder deaktiviert (dessen Veröffentlichung rückgängig gemacht) werden soll.
1. Klicken Sie je nach Bedarf auf **Aktivieren** oder **Deaktivieren**.

## Liste – Anzeigen der Seiten mit Tag-Verweis {#list-showing-where-tags-are-referenced}

**Liste** öffnet ein neues Fenster mit den Pfaden zu allen Seiten, die das markierte Tag verwenden:

![Herausfinden, wo auf Tags verwiesen wird](assets/list_showing_wheretagsarereferenced.png)

## Verschieben von Tags {#moving-tags}

Um Tag-Admins und Entwickelnden die Organisation des Klassifikationsschemas oder die Umbenennung einer Tag-ID zu erleichtern, ist es möglich, ein Tag an einen neuen Ort zu verschieben:

1. Öffnen Sie die **Tagging-Konsole**.
1. Wählen Sie das gewünschte Tag aus und klicken Sie in der oberen Symbolleiste (oder im Kontextmenü) auf **Verschieben**.
1. Definieren Sie im Dialogfeld **Tag verschieben** Folgendes:

   * **nach**: Geben Sie den Zielknoten an.
   * **Umbenennen in**: Geben Sie den neuen Knotennamen an.

1. Klicken Sie auf **Verschieben**.

Das Dialogfeld **Tag verschieben** sieht wie folgt aus:

![Verschieben eines Tags](assets/move_tag.png)

>[!NOTE]
>
>Autoren sollten Tags nicht verschieben und auch keine Tag-ID ändern. Autoren sollten lediglich [die Tag-Titel ändern](#editing-tags), wenn dies notwendig sein sollte.

## Zusammenführen von Tags {#merging-tags}

Das Zusammenführen von Tags kann sich anbieten, wenn in einer Taxonomie Duplikate vorhanden sind. Wenn Tag A mit Tag B zusammengeführt wird, werden alle mit Tag gekennzeichneten Seiten mit Tag B gekennzeichnet, und Tag A steht Autoren nicht mehr zur Verfügung.

So führen Sie Tags zusammen:

1. Öffnen Sie die **Tagging**-Konsole.
1. Wählen Sie das gewünschte Tag aus und klicken Sie in der oberen Symbolleiste (oder im Kontextmenü) auf **Zusammenführen**.
1. Definieren Sie im Dialogfeld **Tag zusammenführen** Folgendes:

   * **in**: Geben Sie den Zielknoten an.

1. Klicken Sie auf **Zusammenführen**.

Das Dialogfeld **Tag zusammenführen** hat folgende Gestalt:

![Zusammenführen von Tags](assets/mergetag.png)

## Zählen der Tag-Verwendung {#counting-usage-of-tags}

So können Sie anzeigen, wie oft ein Tag verwendet wird:

1. Öffnen Sie die **Tagging-Konsole**.
1. Klicken Sie in der oberen Symbolleiste auf **Verwendung zählen**. In der Spalte „Anzahl“ wird das Ergebnis angezeigt.

## Verwalten von Tags in verschiedenen Sprachen {#managing-tags-in-different-languages}

Die optionale Eigenschaft `title` eines Tags kann in mehrere Sprachen übersetzt werden. Tag-`titles` können dann entweder in der Benutzersprache oder in der Seitensprache angezeigt werden.

### Festlegen von Tag-Titeln in verschiedenen Sprachen {#defining-tag-titles-in-multiple-languages}

Anhand des folgenden Verfahrens wird erläutert, wie Sie den `title` des Tags **Animals** in Englisch, Deutsch und Französisch übersetzen:

1. Navigieren Sie zur **Tagging**-Konsole.
1. Bearbeiten Sie das Tag **Animals** unter **Tags** > **Bildarchiv**.
1. Sie können Übersetzungen in den folgenden Sprachen hinzufügen:

   * **Englisch**: Animals
   * **Deutsch**: Tiere
   * **Französisch**: Animaux

1. Speichern Sie die Änderungen.

Das Dialogfeld sieht wie folgt aus:

![Bearbeiten eines Tags](assets/edit_tag.png)

Die Tagging-Konsole verwendet die Benutzerspracheinstellung. Wenn also jemand die Sprache in den Benutzereinstellungen auf Französisch festlegt, wird für das Tag „Animals“ der Begriff „Animaux“ angezeigt.

Wie Sie dem Dialogfeld eine neue Sprache hinzufügen, erfahren Sie unter [Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) im Abschnitt **Tagging für Entwickelnde**.

### Anzeigen von Tag-Titeln in Seiteneigenschaften in der angegebenen Sprache {#displaying-tag-titles-in-page-properties-in-a-specified-language}

Standardmäßig werden die Tag-`titles` in den Seiteneigenschaften in der Seitensprache angezeigt. Das Tag-Dialogfeld in den Seiteneigenschaften verfügt über ein Feld für die Sprache, das die Anzeige der Tag-`titles` in einer anderen Sprache ermöglicht. Das folgende Verfahren erläutert die Anzeige von Tag-`titles` auf Französisch:

1. Fügen Sie entsprechend der Anleitung im vorangehenden Abschnitt eine französische Übersetzung für das Tag **Animals** unter **Tags** > **Bildarchiv** ein.
1. Öffnen Sie die Seiteneigenschaften der Seite **Products** in der englischsprachigen Verzweigung der **Geometrixx**-Website.
1. Öffnen Sie das Dialogfeld **Tags/Keywords** (indem Sie das Pulldown-Menü rechts neben dem Anzeigebereich „Tags/Keywords“ auswählen) und wählen Sie die Sprache **Französisch** aus dem Pulldown-Menü in der unteren rechten Ecke aus.
1. Scrollen Sie mithilfe der linken oder rechten Pfeilschaltfläche nach links oder rechts, bis Sie die Registerkarte **Bildarchiv** auswählen können.

   Wählen Sie das Tag **Animals** (**Animaux**) aus und klicken Sie auf eine beliebige Stelle außerhalb des Dialogfelds, um es zu schließen, und fügen Sie das Tag den Seiteneigenschaften hinzu.

   ![Bearbeiten eines anderen Tags](assets/french_tag.png)

Standardmäßig werden die Tag-`titles` im Dialogfeld „Seiteneigenschaften“ in der Seitensprache angezeigt.

Die Sprache für das Tag wird im Allgemeinen von der Seitensprache übernommen, falls diese eingestellt ist. Wird das [`tag`Widget](/help/sites-developing/building.md#tagging-on-the-client-side) in anderen Fällen verwendet (z. B. in Formularen oder Dialogfeldern), hängt die Tag-Sprache vom Kontext ab.

>[!NOTE]
>
>Die Tag-Cloud und die Meta-Schlüsselwörter in der Standard-Seitenkomponente verwenden die lokalisierten Tag-`titles` basierend auf der Sprache der Seite, sofern sie festgelegt ist.
