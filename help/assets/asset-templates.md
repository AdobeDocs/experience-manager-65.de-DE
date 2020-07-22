---
title: Asset-Vorlagen in [!DNL Adobe Experience Manager Assets].
description: Learn about Asset templates in [!DNL Adobe Experience Manager Assets] and how to use asset templates to create marketing collateral.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 91caca39b0b6c5c0c98b58be02f518901a3d90e3
workflow-type: tm+mt
source-wordcount: '1554'
ht-degree: 33%

---


# Asset templates {#asset-templates}

Asset-Vorlagen sind eine spezielle Asset-Klasse, die eine schnelle Wiederverwendung visuell reicher Inhalte für digitale und Druckmedien ermöglicht. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messagingabschnitt und den bearbeitbaren Abschnitt. Der unveränderliche Messagingabschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Abschnitt kann visuelle und textuelle Inhalte in Feldern enthalten, die bearbeitet werden können, um Messaging anzupassen.

Die Flexibilität, begrenzte Bearbeitungen bei gleichzeitiger Sicherung globaler Signaturen vorzunehmen, macht Asset-Vorlagen zu idealen Bausteinen für die schnelle Anpassung und Verteilung von Inhalten als Inhaltsartefakte für verschiedene Funktionen. Die Wiederverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Print- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse in diesen Kanälen bereitzustellen.

As a marketer, you can store and manage templates within [!DNL Experience Manager Assets] and use a single base template to create multiple personalized print experiences with ease. Sie können verschiedene Arten von Marketingmaterial erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kunden Ihre Marketingbotschaft eindeutig und klar zu vermitteln. Außerdem können Sie aus vorhandenen oder neuen Druckausgaben mehrseitige Druckausgaben zusammenstellen. Und das Beste ist: Sie können ohne großen Aufwand gleichzeitig digitale Umgebungen und Printumgebungen bereitstellen, um für Benutzer eine konsistente integrierte Erfahrung zu schaffen.

While asset templates are mostly [!DNL Adobe InDesign] files, proficiency in [!DNL Adobe InDesign] is not a barrier to creating stellar artifacts. You need not map the fields of your [!DNL Adobe InDesign] template with your product fields that you otherwise require to when creating catalogs. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Weboberfläche bearbeiten. However, for [!DNL Adobe InDesign] to process your editing changes, you must first configure [!DNL Experience Manager Assets] to integrate with [!DNL Adobe InDesign Server].

Die Möglichkeit, [!DNL Adobe InDesign] Vorlagen über die Web-Oberfläche zu bearbeiten, trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern. Die höhere Inhaltsgeschwindigkeit verringert die Markteinführungszeit für Marketingsicherheiten.

Mit Asset-Vorlagen können Sie Folgendes erreichen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Webbenutzeroberfläche.
* Steuern der grundlegenden Textformatierung, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene.
* Ändern von Bildern in der Vorlage per Inhaltsauswahl.
* Anzeigen von Vorlagenbearbeitungen in der Vorschau.
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts.

When you choose a template for your collateral, [!DNL Experience Manager Assets] creates a copy of the template that you can edit. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in die Formate INDD, PDF oder JPG exportieren. Sie können die Ausgabe in diesen Formaten auch in Ihr lokales Dateisystem herunterladen.

## Erstellen von Sicherheiten {#creating-a-collateral}

Stellen Sie sich einen Fall vor, in dem Sie digitales druckbares Marketingmaterial, z. B. Broschüren, Flyer und Anzeigen, für eine anstehende Kampagne erstellen und für Ihre Geschäfte weltweit bereitstellen möchten. Wenn Sie das Material basierend auf einer Vorlage erstellen, können Sie kanalübergreifend eine einheitliche Kundenerfahrung erzielen. Designers can create the campaign templates (single-page or multi-page) using a creative solution, such as [!DNL InDesign] and upload the templates to [!DNL Experience Manager Assets] for you. Bevor Sie eine Sicherheit erstellen, sollten Sie eine oder mehrere INDD-Vorlagen hochladen und [!DNL Experience Manager] im Voraus verfügbar machen.

1. Klicken Sie in der [!DNL Experience Manager] Benutzeroberfläche auf [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Click **[!UICONTROL Create]**, and then choose the collateral you want to create from the menu. For example, choose **[!UICONTROL Brochure]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Lassen Sie eine oder mehrere INDD-Vorlagen [!DNL Experience Manager] im Voraus hochladen und verfügbar sein. Choose a template for your brochure, and click **[!UICONTROL Next]**.

   ![chlimage_1-103](assets/chlimage_1-308.png)

1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Click **[!UICONTROL Confirm]** to confirm your selection.

   ![chlimage_1-105](assets/chlimage_1-310.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**. In einem Dialogfeld mit einem Hinweis wird bestätigt, dass eine neue Broschüre erstellt wurde. Click **[!UICONTROL Open]** to open the brochure in edit mode.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ hierzu können Sie das Dialogfeld schließen und auf der Seite „Vorlagen“ zu dem Ordner navigieren, mit dem Sie den Vorgang begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht in der dazugehörigen Miniaturansicht angezeigt. For example, in this case, the word [!UICONTROL Brochure] is displayed on the thumbnail.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Zusätzen {#editing-a-collateral}

Sie können Material sofort nach dem Erstellen bearbeiten. Alternatively, you open it from the [!UICONTROL Templates] page or the asset page.

1. Sie haben folgende Möglichkeiten, um das Material zur Bearbeitung zu öffnen:

   * Open the collateral (brochure in this case) you created in step 7 of [Create a collateral](/help/assets/asset-templates.md#creating-a-collateral).
   * From the Templates page, navigate to a folder where you created the collateral, and click the [!UICONTROL Edit] quick action on the thumbnail of a collateral.
   * In the asset page for the collateral, click **[!UICONTROL Edit]** from the toolbar.
   * Select the collateral and click **[!UICONTROL Edit]** from the toolbar.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Links auf der Seite werden die Asset-Suche und der Text-Editor angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Sie können den Text-Editor verwenden, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, -stil, -farbe und -typ auf der Tag-Ebene ändern.

   Using the asset finder, you can browse or search for images within [!DNL Experience Manager Assets] and replace the editable images in the template with images of your choice.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. For a field to be editable in [!DNL Experience Manager Assets], corresponding field in the template must be tagged in [!DNL InDesign]. In other words, they should be marked as editable in [!DNL InDesign].

   ![chlimage_1-110](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Ensure that your [!DNL Experience Manager] deployment is integrated with an [!DNL InDesign Server] to enable [!DNL Experience Manager Assets] to extract data from the [!DNL InDesign] template and make it available for editing. Weitere Informationen finden Sie unter [Integrieren von Experience Manager-Assets in InDesign Server](/help/assets/indesign.md).

1. Um den Text in einem bearbeitbaren Feld zu ändern, klicken Sie in der Liste der bearbeitbaren Felder auf das Textfeld und bearbeiten Sie den Text im Feld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftschnitt, Farbe und Größe, mithilfe der bereitgestellten Optionen bearbeiten.

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um die Textänderungen Vorschau.

   ![chlimage_1-112](assets/chlimage_1-317.png)

1. To swap an image, click the **[!UICONTROL Asset Finder]**.

   ![chlimage_1-113](assets/chlimage_1-318.png)

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Stichwörter, Tags und den Veröffentlichungsstatus angeben. You can browse through the [!DNL Experience Manager Assets] repository and navigate to the location of the desired image.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um das Bild Vorschau.

   ![chlimage_1-116](assets/chlimage_1-321.png)

1. Verwenden Sie den Seitennavigator unten, um eine bestimmte Seite in einem mehrseitigen Begleitmaterial zu bearbeiten.

   ![chlimage_1-117](assets/chlimage_1-322.png)

1. Click **[!UICONTROL Preview]** on the toolbar to preview all the changes. Click **[!UICONTROL Done]** to save the editing changes to the collateral.

   >[!NOTE]
   >
   >Die Optionen &quot;Vorschau&quot;und &quot;Fertig&quot;sind nur aktiviert, wenn die bearbeitbaren Bildfelder in den Zusätzen keine fehlenden Symbole aufweisen. If there are missing icons in your collateral, it is because [!DNL Experience Manager] is unable to resolve the images in the [!DNL InDesign] template. Usually, [!DNL Experience Manager] is unable to resolve images in the following cases:
   >
   >* Images are not embedded in the underlying [!DNL InDesign] template.
   >* Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem.

   >
   >To enable [!DNL Experience Manager] to resolve images, do the following:
   >
   >* Embed images while creating [!DNL InDesign] templates (See [About links and embedded graphics](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >* Mount [!DNL Experience Manager] to your local file system, and then map missing icons with existing assets in [!DNL Experience Manager].

   >
   >Weitere Informationen zum Arbeiten mit [!DNL InDesign] Dokumenten finden Sie unter [Best Practices für die Arbeit mit InDesign-Dokumenten in Experience Manager](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Wählen Sie zum Generieren einer PDF-Ausgabe für die Broschüre im Dialogfeld die Acrobat-Option aus und klicken Sie anschließend auf **[!UICONTROL Weiter]**.
1. Das Marketingmaterial wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben. Öffnen Sie das Marketingmaterialelement und wählen Sie in der GlobalNav-Liste die Option **[!UICONTROL Ausgabeformate]**, um die Ausgabeformate anzuzeigen.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Klicken Sie in der Liste der Darstellungen auf die PDF-Darstellung, um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Material zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Merge collateral {#merge-collateral}

1. Klicken Sie auf der [!DNL Experience Manager] Navigationsseite auf [!UICONTROL Assets] .

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

1. Click **[!UICONTROL Create]** and the choose **[!UICONTROL Merge]** from the menu.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Klicken Sie auf der Seite &quot; [!UICONTROL Vorlagenzusammenführung] &quot;auf **[!UICONTROL Zusammenführen]** , um Elemente ![](assets/do-not-localize/assets_add_icon.png)hinzuzufügen.

1. Navigieren Sie zum Speicherort der zusammenzuführenden Sicherheiten und klicken Sie auf die Miniaturansichten der zusammenzuführenden Sicherheiten, um sie auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das Omniture Suchfeld nach Vorlagen suchen.

   ![chlimage_1-123](assets/chlimage_1-328.png)

   You can browse through the [!DNL Experience Manager Assets] repository or collections, and navigate to the location of the desired templates and then select them to merge.

   ![chlimage_1-124](assets/chlimage_1-329.png)

   Sie können verschiedene Filter anwenden, um nach den gewünschten Vorlagen zu suchen. Es ist beispielsweise möglich, basierend auf dem Dateityp oder auf Tags nach Vorlagen zu suchen.

   ![chlimage_1-125](assets/chlimage_1-330.png)

1. Click **[!UICONTROL Next]** from the toolbar.
1. In the **[!UICONTROL Preview &amp; Reorder]** screen, rearrange the templates if required and preview the selection of templates to merge. Then, click **[!UICONTROL Next]** from the toolbar.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. In the [!UICONTROL Configure Template] screen, specify a name for the collateral. Geben Sie optional Tags an, die jeweils geeignet sind. If you want to export the output in PDF format, select **[!UICONTROL Acrobat (.PDF)]**. By default, the collateral is exported in JPG and [!DNL InDesign] format. To change the display thumbnail for the multi-page collateral, click **[!UICONTROL Change Thumbnail]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL OK]** in the dialog to close the dialog. Die mehrseitigen Sicherheiten werden in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Material später zu ändern oder zum Erstellen von anderem Material zu verwenden.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Der [!DNL InDesign] Editor in [!DNL Experience Manager] funktioniert auf Tag-Ebene, und der gesamte Text unter einem einzelnen Tag wird als einzelne Entität betrachtet. Um Textformatierung und -stile bei der Bearbeitung beizubehalten, müssen Sie jeden Absatz (oder Text mit einem anderen Stil) separat taggen.
