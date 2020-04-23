---
title: Anfänglicher Sandbox-Antrag
seo-title: Anfänglicher Sandbox-Antrag
description: Erstellen von Vorlagen, Komponenten und Skripten
seo-description: Erstellen von Vorlagen, Komponenten und Skripten
uuid: b0d03376-d8bc-4e98-aea2-a01744c64ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f74d225e-0245-4d5a-bb93-0ee3f31557aa
translation-type: tm+mt
source-git-commit: 85f3b8f2a5f079954f4907037c1c722a6b25fd91

---


# Anfänglicher Sandbox-Antrag {#initial-sandbox-application}

In diesem Abschnitt erstellen Sie Folgendes:

* The **[template](#createthepagetemplate)**that will be used to create content pages in the example website.
* Die **[Komponente und das Skript](#create-the-template-s-rendering-component)**, die zum Rendern der Webseiten verwendet werden.

## Create the Content Template {#create-the-content-template}

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Bei komplexen Websites werden ggf. auch mehrere Vorlagen für die Erstellung der verschiedenen Seitentypen der Website verwendet. Darüber hinaus kann der Vorlagensatz zu einem Entwurf werden, mit dem Änderungen in einem Servercluster eingeführt werden.

Bei dieser Übung basieren jedoch alle Seiten auf einer einfachen Vorlage.

1. Im Explorer-Bereich von CRXDE Lite:

   * Wählen Sie nun eine der folgenden Optionen aus `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Erstellen]** > Vorlage **[!UICONTROL erstellen]**

1. Geben Sie im Dialogfeld „Vorlage erstellen“ die folgenden Werte ein und klicken Sie anschließend auf **[!UICONTROL Weiter]**:

   * Etikett: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschreibung: `An SCF Sandbox template for play pages`
   * Ressourcentyp: `an-scf-sandbox/components/playpage`
   * Rangansicht: &lt;Als Standard beibehalten>
   Die Beschriftung wird für den Knotennamen verwendet.

   Der Ressourcentyp wird auf dem Knoten &quot;jcr:content&quot;des `playpage`Benutzers als Eigenschaft angezeigt `sling:resourceType`. Er identifiziert die Komponente (Ressource), die den Inhalt auf Anforderung eines Browsers rendert.

   In this case, all pages created using the `playpage` template are rendered by the `an-scf-sandbox/components/playpage` component. Standardmäßig ist der Pfad zur Komponente relativ, sodass Sling die Ressource zuerst im `/apps` Ordner und, falls nicht gefunden, im `/libs` Ordner suchen kann.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Stellen Sie bei Verwendung von &quot;Kopieren/Einfügen&quot;sicher, dass der Wert &quot;Ressourcentyp&quot;keine Leerzeichen am Anfang oder Ende enthält.

   Klicken Sie auf **[!UICONTROL Weiter]**.

1. &quot;Zulässige Pfade&quot;bezieht sich auf die Pfade von Seiten, die diese Vorlage verwenden, sodass die Vorlage für das Dialogfeld &quot; **[!UICONTROL Neue Seite]** &quot;aufgelistet wird.

   Um einen Pfad hinzuzufügen, klicken Sie auf die Plusschaltfläche `+` und geben Sie `/content(/.&ast;)?` in das angezeigte Textfeld ein. Wenn Sie Kopieren/Einfügen verwenden, stellen Sie sicher, dass keine Leerzeichen am Anfang oder am Ende vorhanden sind.

   Note: The value of the allowed path property is a *regular expression.* Inhaltsseiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In this case, the regular expression matches the path of the **/content** folder and all its subpages.

   Wenn ein Autor eine Seite unterhalb `/content`erstellt, wird die `playpage` Vorlage &quot;Eine SCF-Sandbox-Seitenvorlage&quot;in einer Liste der verfügbaren Vorlagen angezeigt.

   Nachdem die Stammseite aus der Vorlage erstellt wurde, kann der Zugriff auf die Vorlage auf diese Website eingeschränkt werden, indem die Eigenschaft geändert wird, um den Stammpfad in den regulären Ausdruck einzuschließen, d. h.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Klicken Sie im Bedienfeld &quot; **[!UICONTROL Zulässige Eltern]** &quot;auf **[!UICONTROL Weiter]** .

   Klicken Sie **[!UICONTROL auf Weiter]** in den Bedienfeldern **[!UICONTROL Zulässige Kinder]** .

   Klicken Sie auf **[!UICONTROL OK]**.

1. Wenn Sie auf &quot;OK&quot;klicken und die Vorlage erstellen, werden rote Dreiecke angezeigt, die in den Ecken der Registerkarte &quot;Eigenschaften&quot;für die neue `playpage` Vorlage angezeigt werden. Diese roten Dreiecke zeigen Bearbeitungen an, die noch nicht gespeichert wurden.

   Klicken Sie auf Alle **[!UICONTROL speichern]** , um die neue Vorlage im Repository zu speichern.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### Erstellen der Renderingkomponente der Vorlage {#create-the-template-s-rendering-component}

Erstellen Sie die *Komponente* , die den Inhalt definiert und alle Seiten wiedergibt, die auf der [Layoutvorlage](#createthepagetemplate)erstellt wurden.

1. In CRXDE Lite, right-click **`/apps/an-scf-sandbox/components`** and click **[!UICONTROL Create > Component]**.
1. Indem Sie den Namen (Bezeichnung) des Knotens auf *playpage* festlegen, lautet der Pfad zur Komponente

   `/apps/an-scf-sandbox/components/playpage`

   die dem Ressourcentyp der PayPal-Vorlage entspricht (optional minus dem anfänglichen **`/apps/`** Teil des Pfades).

   Geben Sie im Dialogfeld **[!UICONTROL Komponente erstellen]** die folgenden Eigenschaftswerte ein:

   * Beschriftung: **Playpage**
   * Titel: **Eine SCF-Sandbox-Wiedergabekomponente**
   * Beschreibung: **Diese Komponente rendert Inhalte für eine SCF-Sandbox-Seite.**
   * Super Type: *&lt;leer lassen>*
   * Gruppe:
   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Click **[!UICONTROL Next]** until the **[!UICONTROL Allowed Children]** panel of the dialog appears:

   * Klicken Sie auf **[!UICONTROL OK]**
   * Klicken Sie auf **[!UICONTROL Alle speichern]**

1. Überprüfen Sie, ob der Pfad zur Komponente und der resourceType der Vorlage übereinstimmen.

   >[!CAUTION]
   >
   >Die Korrespondenz zwischen dem Pfad zur PayPal-Komponente und der sling:resourceType-Eigenschaft der PayPal-Vorlage ist für das ordnungsgemäße Funktionieren der Website von entscheidender Bedeutung.

   ![chlimage_1-79](assets/chlimage_1-79.png)