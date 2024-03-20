---
title: Asset-Vorlagen
description: Erfahren Sie mehr über Asset-Vorlagen in  [!DNL Adobe Experience Manager Assets]  und wie Sie die Vorlagen zur Erstellung von Marketingmaterialien verwenden können.
contentOwner: AG
role: User
feature: Asset Management,Developer Tools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 54%

---

# Asset-Vorlagen {#asset-templates}

Asset-Vorlagen sind eine spezielle Asset-Klasse, die die schnelle Wiederverwendung visuell ansprechender Inhalte für digitale und Druckmedien erleichtert. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messaging-Abschnitt und den bearbeitbaren Abschnitt. Der unveränderliche Messaging-Abschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Abschnitt kann visuelle Inhalte und Textinhalte in Feldern enthalten, die bearbeitet werden können, um das Messaging anzupassen.

Da eingeschränkte Bearbeitungen flexibel vorgenommen werden können, während das globale Erscheinungsbild geschützt ist, sind Asset-Vorlagen ideale Bausteine für die schnelle Inhaltsadaptation und Verteilung als Inhaltsartefakte für verschiedene Funktionen. Die Neuverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Druck- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse über diese Kanäle hinweg bereitzustellen.

Als Marketingexperte können Sie Vorlagen in [!DNL Experience Manager Assets] speichern und verwalten und eine zentrale Basisvorlage verwenden, um auf einfache Weise mehrere personalisierte Druckerlebnisse zu schaffen. Sie können verschiedene Arten von Marketingmaterial erstellen, darunter Broschüren, Flyer, Postkarten, Visitenkarten usw., um Ihre Marketingbotschaft eindeutig an Kunden zu übermitteln. Sie können auch mehrseitige Druckausgaben aus vorhandenen oder neuen Druckausgaben zusammenstellen. Vor allem können Sie gleichzeitig digitale und gedruckte Erlebnisse bereitstellen, um den Benutzern ein konsistentes, integriertes Erlebnis zu bieten.

Bei Asset-Vorlagen handelt es sich zwar meistens um [!DNL Adobe InDesign]-Dateien, aber gute [!DNL Adobe InDesign]-Kenntnisse sind keine Grundvoraussetzung für die Erstellung von beeindruckenden Artefakten. Sie müssen die Felder Ihrer [!DNL Adobe InDesign] Vorlage mit Ihren Produktfeldern, die Sie sonst beim Erstellen von Katalogen benötigen. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Web-Benutzeroberfläche bearbeiten. Damit Ihre Änderungen von [!DNL Adobe InDesign] verarbeitet werden können, müssen Sie aber zuerst [!DNL Experience Manager Assets] für die Integration in [!DNL Adobe InDesign Server] konfigurieren.

Die Möglichkeit zur Bearbeitung von [!DNL Adobe InDesign]-Vorlagen über die Web-Benutzeroberfläche trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern. Die höhere Inhaltsgeschwindigkeit reduziert die Time-to-Market für Marketingmaterial.

Sie können Asset-Vorlagen für folgende Zwecke nutzen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Web-Benutzeroberfläche.
* Steuern Sie die grundlegende Formatierung von Text, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene.
* Ändern von Bildern in der Vorlage per Inhaltsauswahl.
* Anzeigen von Vorlagenbearbeitungen in der Vorschau.
* Führen Sie mehrere Vorlagendateien zusammen, damit Sie ein mehrseitiges Artefakt erstellen können.

Wenn Sie eine Vorlage für Ihr Marketingmaterial auswählen, erstellt [!DNL Experience Manager Assets] eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in den Formaten INDD, PDF oder JPG exportieren. Außerdem können Sie die Ausgabe in diesen Formaten in Ihr lokales Dateisystem herunterladen.

## Erstellen eines Sicherheitsteils {#creating-a-collateral}

Stellen Sie sich ein Szenario vor, in dem Sie digitale druckbare Materialien wie Broschüren, Flyer und Anzeigen für eine bevorstehende Kampagne erstellen und für eine globale Freigabe mit Verkaufsstellen verwenden möchten. Das Erstellen von Begleitmaterial basierend auf einer Vorlage hilft, kanalübergreifend ein einheitliches Kundenerlebnis zu bieten. Designer können die Kampagnenvorlagen (ein- oder mehrseitig) erstellen, indem sie eine Lösung für die Kreativarbeit nutzen, z. B. [!DNL InDesign], und die Vorlagen für Sie in [!DNL Experience Manager Assets] hochladen. Bevor Sie ein Sicherheitselement erstellen, lassen Sie eine oder mehrere INDD-Vorlagen in hochladen und verfügbar in [!DNL Experience Manager] im Voraus.

1. Im [!DNL Experience Manager] Benutzeroberfläche, wählen Sie [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]** aus.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Auswählen **[!UICONTROL Erstellen]** und wählen Sie dann im Menü das gewünschte Material aus. Wählen Sie beispielsweise die Option **[!UICONTROL Broschüre]** aus.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Sie sollten im Voraus eine oder mehrere INDD-Vorlagen in [!DNL Experience Manager] hochladen und verfügbar machen. Wählen Sie eine Vorlage für Ihre Broschüre aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Klicken Sie auf **[!UICONTROL Bestätigen]**, um Ihre Auswahl zu bestätigen.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Ein Dialogfeld bestätigt, dass eine neue Broschüre erstellt wurde. Klicken Sie auf **[!UICONTROL Öffnen]**, um die Broschüre im Bearbeitungsmodus zu öffnen.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ können Sie das Dialogfeld schließen und auf der Seite &quot;Vorlagen&quot;zu dem Ordner navigieren, mit dem Sie begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht auf der Miniaturansicht angezeigt. In diesem Fall wird in der Miniaturansicht beispielsweise das Wort [!UICONTROL Broschüre] angezeigt.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Kollaterstücken {#editing-a-collateral}

Sie können ein Material direkt nach seiner Erstellung bearbeiten. Alternativ hierzu können Sie es über die Seite [!UICONTROL Vorlagen] oder die Asset-Seite öffnen.

1. Sie haben folgende Möglichkeiten, um das Marketingmaterial zur Bearbeitung zu öffnen:

   * Öffnen Sie das Material (in diesem Fall die Broschüre), das Sie in Schritt 7 von [Erstellen eines Sicherheitsteils](/help/assets/asset-templates.md#creating-a-collateral).
   * Navigieren Sie auf der Seite &quot;Vorlagen&quot;zu einem Ordner, in dem Sie das Material erstellt haben, und klicken Sie auf die Schaltfläche [!UICONTROL Bearbeiten] Schnellzugriff auf die Miniaturansicht eines Kollateralstücks.
   * Klicken Sie auf der Asset-Seite für das Marketingmaterial in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
   * Wählen Sie das Marketingmaterial aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Die Asset-Suche und der Texteditor werden links auf der Seite angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Ändern Sie mit dem Texteditor den Text, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, Stil, Farbe und Typ auf Tag-Ebene ändern.

   Um die Asset-Suche zu verwenden, können Sie in [!DNL Experience Manager Assets] und ersetzen Sie die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld in [!DNL Experience Manager Assets] bearbeitbar ist, muss das entsprechende Feld in der Vorlage in [!DNL InDesign]mit einem Tag versehen sein. Anders ausgedrückt: Es muss in [!DNL InDesign] als bearbeitbar gekennzeichnet sein.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Ihre [!DNL Experience Manager]-Implementierung in [!DNL InDesign Server] integriert ist, damit [!DNL Experience Manager Assets] Daten aus der [!DNL InDesign]-Vorlage extrahieren und für die Bearbeitung bereitstellen kann. Weitere Informationen finden Sie unter [Integrieren von Experience Manager Assets mit InDesign Server](/help/assets/indesign.md).

1. Klicken Sie zum Ändern des Texts in einem bearbeitbaren Feld in der Liste mit den entsprechenden Feldern auf das Textfeld und bearbeiten Sie den Text.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, Farbe und Größe, mithilfe der bereitgestellten Optionen bearbeiten.

1. Auswählen **[!UICONTROL Vorschau]** sodass Sie eine Vorschau der Textänderungen anzeigen können.

1. Um ein Bild auszutauschen, wählen Sie die **[!UICONTROL Asset Finder]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch mithilfe von Keywords, Tags und basierend auf ihrem Veröffentlichungsstatus nach Bildern suchen. Sie können das [!DNL Experience Manager Assets]-Repository durchsuchen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Auswählen **[!UICONTROL Vorschau]** sodass Sie eine Vorschau des Bildes anzeigen können.
1. Verwenden Sie unten die Optionen für die Seitennavigation, um für mehrseitiges Marketingmaterial eine bestimmte Seite zu bearbeiten.

1. Auswählen **[!UICONTROL Vorschau]** in der Symbolleiste, damit Sie eine Vorschau aller Änderungen anzeigen können. Auswählen **[!UICONTROL Fertig]** , um die Bearbeitungsänderungen am Material zu speichern.

   >[!NOTE]
   >
   >Die Optionen „Vorschau“ und „Fertig“ sind nur aktiviert, wenn die bearbeitbaren Bildfelder im Marketingmaterial keine fehlenden Symbole aufweisen. Falls in Ihrem Marketingmaterial Symbole fehlen, liegt dies daran, dass [!DNL Experience Manager] die Bilder in der [!DNL InDesign]-Vorlage nicht auflösen kann. Normalerweise können Bilder von [!DNL Experience Manager] in den folgenden Fällen nicht aufgelöst werden:
   >
   >* Bilder sind nicht in die zugrunde liegende [!DNL InDesign]-Vorlage eingebettet.
   >* Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem.
   >
   >Gehen Sie wie folgt vor, um für [!DNL Experience Manager] das Auflösen von Bildern zu ermöglichen:
   >
   >* Betten Sie Bilder ein, während Sie [!DNL InDesign]-Vorlagen erstellen (siehe [Informationen zu Links und eingebetteten Grafiken](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >* Stellen Sie [!DNL Experience Manager] in Ihrem lokalen Dateisystem bereit und ordnen Sie anschließend fehlende Symbole den vorhandenen Assets in [!DNL Experience Manager] zu.
   >
   >Weitere Informationen zum Arbeiten mit [!DNL InDesign]-Dokumenten finden Sie in den [Best Practices für die Arbeit mit InDesign-Dokumenten in Experience Manager](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Um eine PDF-Ausgabedarstellung für die Broschüre zu generieren, wählen Sie die Option Acrobat im Dialogfeld aus und klicken Sie dann auf **[!UICONTROL Weiter]**.
1. Das Material wird in dem Ordner erstellt, mit dem Sie begonnen haben. Um die Ausgabedarstellungen anzuzeigen, öffnen Sie das Material und wählen Sie **[!UICONTROL Ausgabeformate]** aus der GlobalNav-Liste.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Wählen Sie die PDF-Ausgabedarstellung aus der Liste der Ausgabedarstellungen aus, damit Sie die PDF-Datei herunterladen können. Öffnen Sie die PDF-Datei, um das Marketingmaterial zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Zusammenführen von Maketingmaterial {#merge-collateral}

1. Im [!DNL Experience Manager] Benutzeroberfläche, wählen Sie [!UICONTROL Assets] auf der Navigationsseite.

1. Wählen Sie aus den Optionen **[!UICONTROL Vorlagen]**.

1. Auswählen **[!UICONTROL Erstellen]** und wählen Sie dann im Menü **[!UICONTROL Zusammenführen]**.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Aus dem [!UICONTROL Vorlagenzusammenführung] Seite, auswählen **[!UICONTROL Zusammenführen]** ![Assets hinzufügen](assets/do-not-localize/assets_add_icon.png).

1. Navigieren Sie zum Speicherort des zu verschmelzenden Sicherheitselements und wählen Sie die Miniaturansichten des zu verschmelzenden Materials aus, um sie auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das Omnisearch-Feld nach Vorlagen suchen.

   Sie können das [!DNL Experience Manager Assets]-Repository bzw. die Sammlungen durchsuchen, zum Speicherort der gewünschten Vorlagen navigieren und sie dann für die Zusammenführung auswählen.

   Sie können verschiedene Filter anwenden, um die gewünschten Vorlagen zu durchsuchen. Sie können beispielsweise nach Vorlagen suchen, die auf dem Dateityp oder den Tags basieren.

1. Auswählen **[!UICONTROL Nächste]** aus der Symbolleiste.
1. Im **[!UICONTROL Vorschau &amp; Neu anordnen]** , ordnen Sie bei Bedarf die Vorlagen neu und zeigen Sie sich eine Vorschau der zusammenzuführenden Vorlagen an. Wählen Sie in der Symbolleiste **[!UICONTROL Nächste]**.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Geben Sie auf dem Bildschirm [!UICONTROL Vorlage konfigurieren] einen Namen für das Marketingmaterial an. Geben Sie optional Tags an, die jeweils geeignet sind. Wählen Sie **[!UICONTROL Acrobat (.PDF)]** aus, falls Sie die Ausgabe im PDF-Format exportieren möchten. Standardmäßig wird das Marketingmaterial im JPG- und [!DNL InDesign]-Format exportiert. Klicken Sie auf **[!UICONTROL Miniatur ändern]**, um die angezeigte Miniaturansicht für das mehrseitige Marketingmaterial zu ändern.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Auswählen **[!UICONTROL Speichern]** und schließen Sie das Dialogfeld, indem Sie **[!UICONTROL OK]**. Das mehrseitige Material wird in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Sie können ein zusammengeführtes Sicherheitselement nicht später bearbeiten oder es zur Erstellung eines anderen Sicherheitsteils verwenden.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Der [!DNL InDesign]-Editor in [!DNL Experience Manager] funktioniert auf Tag-Ebene und der gesamte Text unter einem einzelnen Tag wird als einzelne Entität betrachtet. Damit die Textformatierung und die Stile beim Bearbeiten erhalten bleiben, müssen Sie jeden Absatz (oder Text mit unterschiedlichen Stilen) separat taggen.
