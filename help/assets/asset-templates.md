---
title: Asset-Vorlagen
description: Informationen zu Asset-Vorlagen in [!DNL Adobe Experience Manager Assets] und wie Sie Asset-Vorlagen verwenden, um Marketingmaterial zu erstellen.
contentOwner: AG
role: User
feature: Asset Management,Developer Tools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
source-git-commit: bb46b0301c61c07a8967d285ad7977514efbe7ab
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 33%

---

# Asset-Vorlagen {#asset-templates}

Asset-Vorlagen sind eine spezielle Asset-Klasse, die die schnelle Wiederverwendung visuell ansprechender Inhalte für digitale und Druckmedien erleichtert. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messagingabschnitt und den bearbeitbaren Abschnitt. Der unveränderliche Messagingabschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Bereich kann visuelle und textuelle Inhalte in Feldern enthalten, die bearbeitet werden können, um Nachrichten anzupassen.

Die Flexibilität, begrenzte Änderungen vorzunehmen und gleichzeitig die globale Beschilderung zu sichern, macht Asset-Vorlagen zu idealen Bausteinen für die schnelle Anpassung und Verteilung von Inhalten als Inhaltsartefakte für verschiedene Funktionen. Die Wiederverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Druck- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse über diese Kanäle hinweg bereitzustellen.

Marketer können Vorlagen in [!DNL Experience Manager Assets] und verwenden Sie eine Basisvorlage, um mühelos mehrere personalisierte Druckerlebnisse zu erstellen. Sie können verschiedene Arten von Marketingmaterial erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kunden Ihre Marketingbotschaft eindeutig und klar zu vermitteln. Außerdem können Sie aus vorhandenen oder neuen Druckausgaben mehrseitige Druckausgaben zusammenstellen. Und das Beste ist: Sie können ohne großen Aufwand gleichzeitig digitale Umgebungen und Printumgebungen bereitstellen, um für Benutzer eine konsistente integrierte Erfahrung zu schaffen.

Während Asset-Vorlagen hauptsächlich [!DNL Adobe InDesign] Dateien, Kompetenz in [!DNL Adobe InDesign] ist kein Hindernis für die Erstellung von Sternartefakten. Sie müssen die Felder Ihrer [!DNL Adobe InDesign] Vorlage mit Ihren Produktfeldern, die Sie sonst beim Erstellen von Katalogen benötigen. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Web-Oberfläche bearbeiten. Allerdings gilt Folgendes: [!DNL Adobe InDesign] Um Ihre Bearbeitungsänderungen zu verarbeiten, müssen Sie zunächst [!DNL Experience Manager Assets] zur Integration mit [!DNL Adobe InDesign Server].

Die Möglichkeit zur Bearbeitung [!DNL Adobe InDesign] Vorlagen aus der Web-Oberfläche tragen dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern. Die höhere Content-Geschwindigkeit reduziert die Time-to-Market für Marketing-Collaterals.

Mit Asset-Vorlagen können Sie Folgendes erreichen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Webbenutzeroberfläche.
* Steuern der grundlegenden Textformatierung, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene.
* Ändern von Bildern in der Vorlage per Inhaltsauswahl.
* Anzeigen von Vorlagenbearbeitungen in der Vorschau.
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts.

Wenn Sie eine Vorlage für Ihr Material auswählen, [!DNL Experience Manager Assets] erstellt eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in die Formate INDD, PDF oder JPG exportieren. Sie können die Ausgabe in diesen Formaten auch in Ihr lokales Dateisystem herunterladen.

## Erstellen von Material {#creating-a-collateral}

Stellen Sie sich einen Fall vor, in dem Sie digitales druckbares Marketingmaterial, z. B. Broschüren, Flyer und Anzeigen, für eine anstehende Kampagne erstellen und für Ihre Geschäfte weltweit bereitstellen möchten. Wenn Sie das Material basierend auf einer Vorlage erstellen, können Sie kanalübergreifend eine einheitliche Kundenerfahrung erzielen. Designer können die Kampagnenvorlagen (einseitige oder mehrseitige) mithilfe einer kreativen Lösung erstellen, z. B. [!DNL InDesign] und laden Sie die Vorlagen in [!DNL Experience Manager Assets] für Sie. Bevor Sie ein Material erstellen, sollten Sie mindestens eine INDD-Vorlage in hochladen und in verfügbar machen. [!DNL Experience Manager] im Voraus.

1. In [!DNL Experience Manager] Oberflächenklick [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Klicken **[!UICONTROL Erstellen]** und wählen Sie dann im Menü das zu erstellende Material aus. Wählen Sie beispielsweise **[!UICONTROL Broschüre]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Lassen Sie eine oder mehrere INDD-Vorlagen hochladen und in verfügbar sein. [!DNL Experience Manager] im Voraus. Wählen Sie eine Vorlage für Ihre Broschüre aus und klicken Sie auf **[!UICONTROL Nächste]**.
1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Klicken **[!UICONTROL Bestätigen]** um Ihre Auswahl zu bestätigen.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. In einem Dialogfeld mit einem Hinweis wird bestätigt, dass eine neue Broschüre erstellt wurde. Klicken **[!UICONTROL Öffnen]** um die Broschüre im Bearbeitungsmodus zu öffnen.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ hierzu können Sie das Dialogfeld schließen und auf der Seite „Vorlagen“ zu dem Ordner navigieren, mit dem Sie den Vorgang begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht in der dazugehörigen Miniaturansicht angezeigt. In diesem Fall würde beispielsweise das Wort [!UICONTROL Broschüre] wird auf der Miniaturansicht angezeigt.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Sicherheiten {#editing-a-collateral}

Sie können Material sofort nach dem Erstellen bearbeiten. Alternativ können Sie sie über die [!UICONTROL Vorlagen] oder der Asset-Seite.

1. Sie haben folgende Möglichkeiten, um das Material zur Bearbeitung zu öffnen:

   * Öffnen Sie das Material (in diesem Fall die Broschüre), das Sie in Schritt 7 von erstellt haben. [Erstellen von Material](/help/assets/asset-templates.md#creating-a-collateral).
   * Navigieren Sie auf der Seite &quot;Vorlagen&quot;zu einem Ordner, in dem Sie das Material erstellt haben, und klicken Sie auf die Schaltfläche [!UICONTROL Bearbeiten] Schnellzugriff auf die Miniaturansicht eines Materials.
   * Klicken Sie auf der Asset-Seite für das Material auf **[!UICONTROL Bearbeiten]** aus der Symbolleiste.
   * Wählen Sie das Material aus und klicken Sie auf **[!UICONTROL Bearbeiten]** aus der Symbolleiste.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Links auf der Seite werden die Asset-Suche und der Text-Editor angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Sie können den Text-Editor verwenden, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, -stil, -farbe und -typ auf der Tag-Ebene ändern.

   Mit der Asset-Suche können Sie in [!DNL Experience Manager Assets] und ersetzen Sie die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld bearbeitet werden kann in [!DNL Experience Manager Assets], muss das entsprechende Feld in der Vorlage mit Tags versehen werden in [!DNL InDesign]. Mit anderen Worten: Sie sollten als bearbeitbar markiert werden in [!DNL InDesign].

   >[!NOTE]
   >
   >Stellen Sie sicher, dass [!DNL Experience Manager] -Implementierung in eine [!DNL InDesign Server] aktivieren [!DNL Experience Manager Assets] zum Extrahieren von Daten aus dem [!DNL InDesign] und stellen Sie sie zur Bearbeitung zur Verfügung. Weitere Informationen finden Sie unter [Experience Manager Assets mit InDesign Server integrieren](/help/assets/indesign.md).

1. Um den Text in einem bearbeitbaren Feld zu ändern, klicken Sie in der Liste der bearbeitbaren Felder auf das Textfeld und bearbeiten Sie den Text im Feld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, Farbe und Größe, mithilfe der bereitgestellten Optionen bearbeiten.

1. Klicken **[!UICONTROL Vorschau]** um eine Vorschau der Textänderungen anzuzeigen.

1. Um ein Bild auszutauschen, klicken Sie auf die **[!UICONTROL Asset Finder]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Stichwörter, Tags und den Veröffentlichungsstatus angeben. Sie können die [!DNL Experience Manager Assets] Repository erstellen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Klicken **[!UICONTROL Vorschau]** um eine Vorschau des Bildes anzuzeigen.
1. Um eine bestimmte Seite in einem mehrseitigen Material zu bearbeiten, verwenden Sie den Seitennavigator am unteren Rand.

1. Klicken **[!UICONTROL Vorschau]** in der Symbolleiste, um eine Vorschau aller Änderungen anzuzeigen. Klicken **[!UICONTROL Fertig]** , um die Bearbeitungsänderungen am Material zu speichern.

   >[!NOTE]
   >
   >Die Optionen Vorschau und Fertig sind nur dann aktiviert, wenn die bearbeitbaren Bildfelder im Material keine fehlenden Symbole aufweisen. Wenn in Ihrem Material Symbole fehlen, liegt dies daran, dass [!DNL Experience Manager] kann die Bilder im [!DNL InDesign] Vorlage. Normalerweise [!DNL Experience Manager] kann in folgenden Fällen keine Bilder auflösen:
   >
   >* Bilder werden nicht in den zugrunde liegenden [!DNL InDesign] Vorlage.
   >* Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem.

   >
   >Aktivieren [!DNL Experience Manager] Gehen Sie wie folgt vor, um Bilder aufzulösen:
   >
   >* Bilder beim Erstellen einbetten [!DNL InDesign] templates (siehe [Über Links und eingebettete Grafiken](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >* Berg [!DNL Experience Manager] Ihrem lokalen Dateisystem und ordnen Sie dann fehlende Symbole vorhandenen Assets in zu. [!DNL Experience Manager].

   >
   >Weitere Informationen zum Arbeiten mit [!DNL InDesign] Dokumente, siehe [Best Practices für die Arbeit mit InDesign-Dokumenten in Experience Manager](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Wählen Sie zum Generieren einer PDF-Ausgabe für die Broschüre im Dialogfeld die Acrobat-Option aus und klicken Sie anschließend auf **[!UICONTROL Weiter]**.
1. Das Marketingmaterial wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben. Öffnen Sie das Marketingmaterialelement und wählen Sie in der GlobalNav-Liste die Option **[!UICONTROL Ausgabeformate]**, um die Ausgabeformate anzuzeigen.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Klicken Sie in der Ausgabedarstellungsliste auf die PDF-Ausgabedarstellung , um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Material zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Zusammenführen von Sicherheiten {#merge-collateral}

1. Im [!DNL Experience Manager] Oberflächenklick [!UICONTROL Assets] auf der Navigationsseite.

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

1. Klicken **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Zusammenführen]** aus dem Menü.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Aus dem [!UICONTROL Vorlagenzusammenführung] Seite, klicken Sie auf **[!UICONTROL Zusammenführen]** ![Assets hinzufügen](assets/do-not-localize/assets_add_icon.png).

1. Navigieren Sie zum Speicherort des Assets, das Sie zusammenführen möchten, und klicken Sie auf die Miniaturansichten des Assets, das Sie zusammenführen möchten, um es auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das OmniSearch-Feld nach Vorlagen suchen.

   Sie können die [!DNL Experience Manager Assets] Repository oder Sammlungen, navigieren Sie zum Speicherort der gewünschten Vorlagen und wählen Sie sie aus, um sie zusammenzuführen.

   Sie können verschiedene Filter anwenden, um nach den gewünschten Vorlagen zu suchen. Es ist beispielsweise möglich, basierend auf dem Dateityp oder auf Tags nach Vorlagen zu suchen.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Im **[!UICONTROL Vorschau &amp; Neu anordnen]** , ordnen Sie bei Bedarf die Vorlagen neu und zeigen Sie eine Vorschau der Auswahl der zusammenzuführenden Vorlagen an. Klicken Sie anschließend auf **[!UICONTROL Nächste]** aus der Symbolleiste.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Im [!UICONTROL Vorlage konfigurieren] -Bildschirm einen Namen für das Material angeben. Geben Sie optional Tags an, die jeweils geeignet sind. Wenn Sie die Ausgabe im PDF-Format exportieren möchten, wählen Sie **[!UICONTROL Acrobat (.PDF)]**. Standardmäßig wird das Material in JPG exportiert und [!DNL InDesign] Format. Um die Miniaturansicht für mehrseitige Assets zu ändern, klicken Sie auf **[!UICONTROL Miniatur ändern]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Klicken **[!UICONTROL Speichern]** und klicken Sie anschließend auf **[!UICONTROL OK]** im Dialogfeld, um das Dialogfeld zu schließen. Das mehrseitige Material wird in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Material später zu ändern oder zum Erstellen von anderem Material zu verwenden.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Die [!DNL InDesign] Editor in [!DNL Experience Manager] funktioniert auf Tag-Ebene und der gesamte Text unter einem einzelnen Tag wird als einzelne Entität betrachtet. Damit die Textformatierung und die Stile beim Bearbeiten erhalten bleiben, müssen Sie jeden Absatz (oder Text mit unterschiedlichen Stilen) separat taggen.
