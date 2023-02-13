---
title: Tagging-Konsole der klassischen Benutzeroberfläche
seo-title: Classic UI Tagging Console
description: Erfahren Sie mehr über die Tagging-Konsole der klassischen Benutzeroberfläche.
seo-description: Learn about the Classic UI Tagging Console.
uuid: 51e29422-f967-424b-a7fd-4ca2ddc6b8a3
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: b279c033-bc93-4e62-81ad-123c40b9fdd2
docset: aem65
exl-id: 8c6ba22f-5555-4e3c-998a-9353bd44715b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '860'
ht-degree: 100%

---

# Tagging-Konsole der klassischen Benutzeroberfläche{#classic-ui-tagging-console}

Dieser Abschnitt bezieht sich auf die Tagging-Konsole der klassischen Benutzeroberfläche.

Informationen zur Tagging-Konsole der Touch-optimierten Benutzeroberfläche finden Sie [hier](/help/sites-administering/tags.md#tagging-console).

So greifen Sie auf die Tagging-Konsole der klassischen Benutzeroberfläche zu:

* in der Autoreninstanz
* Melden Sie sich mit Administratorrechten an.
* Navigieren Sie zur Konsole, zum Beispiel [https://localhost:4502/tagging](https://localhost:4502/tagging).

![](assets/managing_tags_usingthetagasministrationconsole.png)

## Erstellen von Tags und Namespaces {#creating-tags-and-namespaces}

1. Je nachdem, auf welcher Ebene sie beginnen, können Sie mithilfe des Befehls **Neu** ein Tag oder einen Namespace erstellen:

   Wenn Sie **Tags** wählen, können Sie einen Namespace erstellen:

   ![](assets/creating_tags_andnamespaces.png)

   Wenn Sie einen Namespace wählen (zum Beispiel **Demo**), können Sie ein Tag innerhalb dieses Namespace erstellen:

   ![](assets/creating_tags_andnamespacesinnewnamespace.png)

1. Geben Sie in beiden Fällen Folgendes ein:

   * **Titel**
(
*Erforderlich*) Den Anzeigetitel für das Tag. Auch wenn es bei der Eingabe keine verbotenen Zeichen gibt, wird empfohlen, keines dieser Sonderzeichen zu verwenden:

      * `colon (:)` – Namespace-Trennzeichen
      * `forward slash (/)` – Trennzeichen für untergeordnete Tags

      Diese Zeichen werden möglicherweise nicht angezeigt, wenn sie eingegeben werden.

   * **Name**
(
*Erforderlich*) Der Knotenname für das Tag.

   * **Beschreibung**
(
*Optional*) Eine Beschreibung für das Tag.

   * Wählen Sie **Erstellen** aus.


## Bearbeiten von Tags {#editing-tags}

1. Wählen Sie im rechten Fenster das zu bearbeitende Tag aus.
1. Klicken Sie auf **Bearbeiten**.
1. Sie können **Titel** und **Beschreibung** ändern.
1. Klicken Sie auf **Speichern**, um das Dialogfeld zu schließen.

## Löschen von Tags {#deleting-tags}

1. Wählen Sie im rechten Bedienfeld das zu löschende Tag aus.
1. Klicken Sie auf **Löschen**.
1. Klicken Sie auf **Ja**, um das Dialogfeld zu schließen.

   Das Tag sollte nicht mehr aufgeführt werden.

## Aktivieren und Deaktivieren von Tags {#activating-and-deactivating-tags}

1. Wählen Sie im rechten Bedienfeld das Tag bzw. den Namespace aus, das/der aktiviert (veröffentlicht) bzw. deaktiviert (dessen Veröffentlichung rückgängig gemacht) werden soll.
1. Klicken Sie je nach Bedarf auf **Aktivieren** oder **Deaktivieren**.

## Liste – zeigt alle Seiten, die auf Tags verweisen {#list-showing-where-tags-are-referenced}

**Liste** öffnet ein neues Fenster, das die Pfade zu allen Seiten enthält, die das markierte Tag verwenden:

![](assets/list_showing_wheretagsarereferenced.png)

## Verschieben von Tags {#moving-tags}

Um Tag-Administratoren und -Entwicklern die Organisation des Klassifikationsschemas oder die Umbenennung einer Tag-ID zu erleichtern, ist es möglich, ein Tag an einen neuen Ort zu verschieben:

1. Öffnen Sie die **Tagging**-Konsole.
1. Markieren Sie das gewünschte Tag und klicken Sie in der oberen Werkzeugleiste (oder im Kontextmenü) auf **Verschieben...**
1. Legen Sie im Dialogfeld **Tag verschieben** folgende Optionen fest:

   * **nach**, den Zielknoten.
   * **Umbenennen in**, den neuen Namen des Knotens

1. Klicken Sie auf **Verschieben**.

Das Dialogfeld **Tag verschieben** hat folgende Gestalt:

![](assets/move_tag.png)

>[!NOTE]
>
>Autoren sollten Tags nicht verschieben und auch keine Tag-ID ändern. Autoren sollten lediglich [die Tag-Titel ändern](#editing-tags), wenn dies notwendig sein sollte.

## Zusammenführen von Tags {#merging-tags}

Das Zusammenführen von Tags kann sich anbieten, wenn in einer Taxonomie Duplikate vorhanden sind. Wenn Tag A mit Tag B zusammengeführt wird, werden alle mit Tag gekennzeichneten Seiten mit Tag B gekennzeichnet, und Tag A steht Autoren nicht mehr zur Verfügung.

So führen Sie Tags zusammen:

1. Öffnen Sie die **Tagging**-Konsole.
1. Markieren Sie das gewünschte Tag und klicken Sie in der oberen Werkzeugleiste (oder im Kontextmenü) auf **Zusammenführen...**
1. Legen Sie im Dialogfeld **Tag zusammenführen** folgende Optionen fest:

   * **in**, den Zielknoten.

1. Klicken Sie auf **Zusammenführen**.

Das Dialogfeld **Tag zusammenführen** hat folgende Gestalt:

![](assets/mergetag.png)

## Statistik der Tag-Verwendung {#counting-usage-of-tags}

So können Sie anzeigen, wie oft ein Tag verwendet wurde:

1. Öffnen Sie die **Tagging**-Konsole.
1. Klicken Sie in der oberen Werkzeugleiste auf **Verwendung zählen**. In der Spalte „Zählung“ wird das Ergebnis angezeigt.

## Verwalten von Tags in verschiedenen Sprachen {#managing-tags-in-different-languages}

Die optionale Eigenschaft `title` eines Tags kann in mehrere Sprachen übersetzt werden. Tag-`titles` können dann entweder in der Benutzersprache oder in der Seitensprache angezeigt werden.

### Festlegen von Tag-Titeln in verschiedenen Sprachen {#defining-tag-titles-in-multiple-languages}

Anhand des folgenden Verfahrens wird erläutert, wie Sie den `title` des Tags **Animals** in Englisch, Deutsch und Französisch übersetzen:

1. Navigieren Sie zur **Tagging**-Konsole.
1. Bearbeiten Sie das Tag **Animals** unter **Tags** > **Bildarchiv**.
1. Fügen Sie Übersetzungen in den folgenden Sprachen hinzu:

   * **Englisch**: Animals
   * **Deutsch**: Tiere
   * **Französisch**: Animaux

1. Speichern Sie die Änderungen.

Das Dialogfeld hat die folgende Gestalt:

![](assets/edit_tag.png)

Die Tagging-Konsole verwendet die Benutzerspracheinstellung. Wenn also ein Benutzer die Sprache in den Benutzereinstellungen auf Französisch festlegt, wird für das Tag „Animal“ der Begriff „Animaux“ angezeigt.

Wie Sie dem Dialogfeld eine neue Sprache hinzufügen, erfahren Sie im Abschnitt [Hinzufügen einer neuen Sprache zum Dialogfeld „Tag bearbeiten“](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) des Abschnitts **Tagging für Entwickler**.

### Anzeigen von Tag-Titeln in Seiteneigenschaften in der angegebenen Sprache {#displaying-tag-titles-in-page-properties-in-a-specified-language}

Standardmäßig werden die Tag-`titles` in den Seiteneigenschaften in der Seitensprache angezeigt. Das Tag-Dialogfeld in den Seiteneigenschaften verfügt über ein Feld für die Sprache, das die Anzeige der Tag-`titles` in einer anderen Sprache ermöglicht. Das folgende Verfahren erläutert die Anzeige von Tag-`titles` auf Französisch:

1. Fügen Sie entsprechend der Anleitung im vorangehenden Abschnitt eine französische Übersetzung für das Tag **Animals** unter **Tags** > **Bildarchiv** ein.
1. Öffnen Sie die Seiteneigenschaften der Seite **Products** in der englischsprachigen Verzweigung der **Geometrixx**-Website.
1. Öffnen Sie das Dialogfeld **Tags/Keywords** (indem Sie das Pulldown-Menü rechts neben dem Anzeigebereich „Tags/Keywords“ auswählen) und wählen Sie die Sprache **Französisch** aus dem Pulldown-Menü in der unteren rechten Ecke aus.
1. Scrollen Sie mithilfe der linken oder rechten Pfeilschaltfläche nach links oder rechts, bis Sie die Registerkarte **Bildarchiv** auswählen können.

   Wählen Sie das Tag **Animals** (**Animaux**) aus und klicken Sie auf eine beliebige Stelle außerhalb des Dialogfelds, um es zu schließen, und fügen Sie das Tag den Seiteneigenschaften hinzu.

   ![](assets/french_tag.png)

Standardmäßig werden die Tag-`titles` im Dialogfeld „Seiteneigenschaften“ in der Seitensprache angezeigt.

Die Sprache für das Tag wird im Allgemeinen von der Seitensprache übernommen, falls diese eingestellt ist. Wird das [Widget `tag`](/help/sites-developing/building.md#tagging-on-the-client-side) in anderen Fällen verwendet (z. B. in Formularen oder Dialogfeldern), hängt die Tag-Sprache vom Kontext ab.

>[!NOTE]
>
>Die Tag-Cloud und die Meta-Stichwörter in der Standard-Seitenkomponente verwenden die lokalisierten Tag-`titles` basierend auf der Seitensprache, sofern sie festgelegt ist.
