---
title: Asset-Vorlagen
description: Erfahren Sie mehr über Asset-Vorlagen in AEM Assets und wie Sie mit Asset-Vorlagen Marketingmaterial erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: c7d0bcbf39adfc7dfd01742651589efb72959603

---


# Asset templates {#asset-templates}

Asset-Vorlagen sind eine spezielle Asset-Klasse, die eine schnelle Wiederverwendung visuell reicher Inhalte für digitale und Druckmedien ermöglicht. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messagingabschnitt und den bearbeitbaren Abschnitt.

Der unveränderliche Messagingabschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Abschnitt kann visuelle und textuelle Inhalte in Feldern enthalten, die bearbeitet werden können, um Messaging anzupassen.

Die Flexibilität, begrenzte Bearbeitungen bei gleichzeitiger Sicherung globaler Signaturen vorzunehmen, macht Asset-Vorlagen zu idealen Bausteinen für die schnelle Anpassung und Verteilung von Inhalten als Inhaltsartefakte für verschiedene Funktionen. Die Wiederverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Print- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse in diesen Kanälen bereitzustellen.

Marketingexperten können Vorlagen in AEM Assets speichern und verwalten und eine einzige Basisvorlage verwenden, um mühelos mehrere personalisierte Druckerlebnisse zu erstellen. Sie können verschiedene Arten von Marketingmaterial erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kunden Ihre Marketingbotschaft eindeutig und klar zu vermitteln. Außerdem können Sie aus vorhandenen oder neuen Druckausgaben mehrseitige Druckausgaben zusammenstellen. Und das Beste ist: Sie können ohne großen Aufwand gleichzeitig digitale Umgebungen und Printumgebungen bereitstellen, um für Benutzer eine konsistente integrierte Erfahrung zu schaffen.

Während Asset-Vorlagen hauptsächlich Adobe InDesign-Dateien sind, stellt die Kompetenz in Adobe InDesign keine Barriere für die Erstellung von Sternartefakten dar. Sie müssen die Felder Ihrer Adobe InDesign-Vorlage nicht den Produktfeldern zuordnen, die Sie sonst beim Erstellen von Katalogen benötigen. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Weboberfläche bearbeiten. Damit Adobe InDesign Ihre Bearbeitungsänderungen verarbeiten kann, müssen Sie zunächst AEM Assets für die Integration mit dem Adobe InDesign-Server konfigurieren.

Die Möglichkeit, Adobe InDesign-Vorlagen über die Weboberfläche zu bearbeiten, trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern und gleichzeitig die Time-to-Market für lokale Werbemaßnahmen zu verkürzen.

Sie können Asset-Vorlagen für folgende Zwecke nutzen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Webbenutzeroberfläche
* Steuern der grundlegenden Textformatierung, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene
* Ändern von Bildern in der Vorlage per Inhaltsauswahl
* Anzeigen von Vorlagenbearbeitungen in der Vorschau
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts

Wenn Sie eine Vorlage für Ihr Marketingmaterial auswählen, erstellt AEM Assets eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in den folgenden Formaten exportieren:

* INDD
* PDF
* JPG

Außerdem können Sie die Ausgabe in diesen Formaten auf Ihr lokales System herunterladen.

## Erstellen von Sicherheiten {#creating-a-collateral}

Stellen Sie sich einen Fall vor, in dem Sie digitales druckbares Marketingmaterial, z. B. Broschüren, Flyer und Anzeigen, für eine anstehende Kampagne erstellen und für Ihre Geschäfte weltweit bereitstellen möchten. Wenn Sie das Material basierend auf einer Vorlage erstellen, können Sie kanalübergreifend eine einheitliche Kundenerfahrung erzielen. Designer können die Kampagnenvorlagen (ein- oder mehrseitig) erstellen, indem sie eine Lösung für die Kreativarbeit nutzen, z. B. InDesign, und die Vorlagen für Sie in AEM Assets hochladen. Bevor Sie eine Sicherheit erstellen, sollten Sie eine oder mehrere INDD-Vorlagen vorab in Experience Manager hochladen und verfügbar machen.

1. Klicken Sie in der Experience Manager-Oberfläche auf [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Click **[!UICONTROL Create]**, and then choose the collateral you want to create from the menu. For example, choose **[!UICONTROL Brochure]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Lassen Sie eine oder mehrere INDD-Vorlagen im Voraus in Experience Manager hochgeladen und verfügbar sein. Choose a template for your brochure, and click **[!UICONTROL Next]**.

   ![chlimage_1-103](assets/chlimage_1-308.png)

1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Click **[!UICONTROL Confirm]** to confirm your selection.

   ![chlimage_1-105](assets/chlimage_1-310.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**. In einem Dialogfeld mit einem Hinweis wird bestätigt, dass eine neue Broschüre erstellt wurde. Click **[!UICONTROL Open]** to open the brochure in edit mode.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ hierzu können Sie das Dialogfeld schließen und auf der Seite „Vorlagen“ zu dem Ordner navigieren, mit dem Sie den Vorgang begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht in der dazugehörigen Miniaturansicht angezeigt. In diesem Fall wird in der Miniaturansicht beispielsweise „Broschüre“ angezeigt.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Zusätzen {#editing-a-collateral}

Sie können Material sofort nach dem Erstellen bearbeiten. Alternativ hierzu können Sie es über die Seite „Vorlagen“ oder die Asset-Seite öffnen.

1. Sie haben folgende Möglichkeiten, um das Material zur Bearbeitung zu öffnen:

   * Open the collateral (brochure in this case) you created in step 7 of [Create a collateral](/help/assets/asset-templates.md#creating-a-collateral).
   * From the Templates page, navigate to a folder where you created the collateral, and click the [!UICONTROL Edit] quick action on the thumbnail of a collateral.
   * In the asset page for the collateral, click **[!UICONTROL Edit]** from the toolbar.
   * Select the collateral and click **[!UICONTROL Edit]** from the toolbar.
   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Links auf der Seite werden die Asset-Suche und der Text-Editor angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Sie können den Text-Editor verwenden, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, -stil, -farbe und -typ auf der Tag-Ebene ändern.

   Mithilfe der Asset-Suche können Sie in AEM Assets nach Bildern suchen und die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl ersetzen.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld in AEM Assets bearbeitbar ist, muss das entsprechende Feld in der Vorlage in InDesign mit einem Tag versehen sein. Mit anderen Worten, sie sollten in InDesign als bearbeitbar markiert werden.

   ![chlimage_1-110](assets/chlimage_1-315.png)

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Ihre AEM-Instanz in einen InDesign-Server integriert ist, damit AEM Assets Daten aus der InDesign-Vorlage extrahieren und für die Bearbeitung bereitstellen kann. For details, see [Integrating AEM Assets with InDesign Server](/help/assets/indesign.md).

1. Um den Text in einem bearbeitbaren Feld zu ändern, klicken Sie in der Liste der bearbeitbaren Felder auf das Textfeld und bearbeiten Sie den Text im Feld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, -farbe und -größe, mit den vorhandenen Optionen bearbeiten.

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um die Textänderungen Vorschau.

   ![chlimage_1-112](assets/chlimage_1-317.png)

1. To swap an image, click the **[!UICONTROL Asset Finder]**.

   ![chlimage_1-113](assets/chlimage_1-318.png)

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Stichwörter, Tags und den Veröffentlichungsstatus angeben. Sie können das AEM Assets-Repository durchsuchen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um das Bild Vorschau.

   ![chlimage_1-116](assets/chlimage_1-321.png)

1. Verwenden Sie den Seitennavigator unten, um eine bestimmte Seite in einem mehrseitigen Begleitmaterial zu bearbeiten.

   ![chlimage_1-117](assets/chlimage_1-322.png)

1. Click **[!UICONTROL Preview]**  on the toolbar to preview all the changes. Click **[!UICONTROL Done]** to save the editing changes to the collateral.

   >[!NOTE]
   >
   >Die Symbole „Vorschau“ und „Fertig“ sind nur aktiviert, wenn die bearbeitbaren Bildfelder im Material keine fehlenden Symbole aufweisen. Falls in Ihrem Material Symbole fehlen, liegt dies daran, dass AEM die Bilder in der InDesign-Vorlage nicht auflösen kann. Normalerweise können Bilder von AEM in den folgenden Fällen nicht aufgelöst werden:
   >
   >    * Bilder werden nicht in die zugrunde liegende InDesign-Vorlage eingebettet
   >    * Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem
   >
   >Gehen Sie wie folgt vor, um für AEM das Auflösen von Bildern zu ermöglichen:
   >
   >    * Betten Sie Bilder ein, während Sie InDesign-Vorlagen erstellen (siehe [Informationen zu Links und eingebetteten Grafiken](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >    * Stellen Sie AEM in Ihrem lokalen Dateisystem bereit und ordnen Sie anschließend fehlende Symbole den vorhandenen AEM-Assets zu.
   >
   >For more information around working with InDesign documents, see [Best Practices for Working with InDesign Documents in AEM](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Wählen Sie zum Generieren einer PDF-Ausgabe für die Broschüre im Dialogfeld die Acrobat-Option aus und klicken Sie anschließend auf **[!UICONTROL Weiter]**.
1. Das Marketingmaterial wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben. Öffnen Sie das Marketingmaterialelement und wählen Sie in der GlobalNav-Liste die Option **[!UICONTROL Ausgabeformate]**, um die Ausgabeformate anzuzeigen.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Klicken Sie in der Liste der Darstellungen auf die PDF-Darstellung, um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Material zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Merge collateral {#merge-collateral}

1. Klicken Sie auf der Navigationsseite in der Experience Manager-Oberfläche auf [!UICONTROL Assets] .

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

1. Click **[!UICONTROL Create]** and the choose **[!UICONTROL Merge]** from the menu.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Klicken Sie auf der Seite [!UICONTROL Vorlagenzusammenführung] auf **[!UICONTROL Zusammenführen]**.

   ![chlimage_1-121](assets/chlimage_1-326.png)

1. Navigieren Sie zum Speicherort der zusammenzuführenden Sicherheiten und klicken Sie auf die Miniaturansichten der zusammenzuführenden Sicherheiten, um sie auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das Omniture Suchfeld nach Vorlagen suchen.

   ![chlimage_1-123](assets/chlimage_1-328.png)

   Sie können das AEM Assets-Repository bzw. die Sammlungen durchsuchen, zum Speicherort der gewünschten Vorlagen navigieren und sie dann für die Zusammenführung auswählen.

   ![chlimage_1-124](assets/chlimage_1-329.png)

   Sie können verschiedene Filter anwenden, um nach den gewünschten Vorlagen zu suchen. Es ist beispielsweise möglich, basierend auf dem Dateityp oder auf Tags nach Vorlagen zu suchen.

   ![chlimage_1-125](assets/chlimage_1-330.png)

1. Click **[!UICONTROL Next]** from the toolbar.
1. In the **[!UICONTROL Preview &amp; Reorder]** screen, rearrange the templates if required and preview the selection of templates to merge. Then, click **[!UICONTROL Next]** from the toolbar.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. In the [!UICONTROL Configure Template] screen, specify a name for the collateral. Geben Sie optional Tags an, die jeweils geeignet sind. If you want to export the output in PDF format, select **[!UICONTROL Acrobat (.PDF)]**. Standardmäßig wird das Material im JPG- und InDesign-Format exportiert. To change the display thumbnail for the multi-page collateral, click **[!UICONTROL Change Thumbnail]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Click **[!UICONTROL Save]** and then click **[!UICONTROL OK]** in the dialog to close the dialog. Die mehrseitigen Sicherheiten werden in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Material später zu ändern oder zum Erstellen von anderem Material zu verwenden.
