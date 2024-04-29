---
title: Asset-Vorlagen
description: Erfahren Sie mehr über Asset-Vorlagen in  [!DNL Adobe Experience Manager Assets]  und wie Sie die Vorlagen zur Erstellung von Marketingmaterialien verwenden können.
contentOwner: AG
role: User
feature: Asset Management,Developer Tools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1576'
ht-degree: 100%

---

# Asset-Vorlagen {#asset-templates}

Bei Asset-Vorlagen handelt es sich um eine spezielle Klasse von Assets, die das schnelle Wiederverwenden von visuell reichhaltigen Inhalten für digitale Medien und Printmedien ermöglichen.  Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messaging-Abschnitt und den bearbeitbaren Abschnitt. Der unveränderliche Messaging-Abschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Abschnitt kann visuelle Inhalte und Textinhalte in Feldern enthalten, die bearbeitet werden können, um das Messaging anzupassen.

Da eingeschränkte Bearbeitungen flexibel vorgenommen werden können, während das globale Erscheinungsbild geschützt ist, sind Asset-Vorlagen ideale Bausteine für die schnelle Inhaltsadaptation und Verteilung als Inhaltsartefakte für verschiedene Funktionen. Durch die Wiederverwendung von Inhalten werden die Kosten für die Verwaltung von Druckkanälen und digitalen Kanälen reduziert und ganzheitliche und konsistente Umgebungen für diese Kanäle bereitgestellt.

Als Marketing-Fachkraft können Sie Vorlagen in [!DNL Experience Manager Assets] speichern und verwalten und eine zentrale Basisvorlage verwenden, um auf einfache Weise mehrere personalisierte Druckerlebnisse zu schaffen. Sie können verschiedene Arten von Marketing-Material erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kundinnen und Kunden Ihre Marketing-Botschaft eindeutig und klar zu vermitteln. Außerdem können Sie aus vorhandenen oder neuen Druckausgaben mehrseitige Druckausgaben zusammenstellen. Und das Beste ist: Sie können ohne großen Aufwand gleichzeitig digitale Erfahrungen und gedruckte Erfahrungen bereitstellen, um für Benutzende eine konsistente integrierte Erfahrung zu schaffen.

Bei Asset-Vorlagen handelt es sich zwar meistens um [!DNL Adobe InDesign]-Dateien, aber gute [!DNL Adobe InDesign]-Kenntnisse sind keine Grundvoraussetzung für die Erstellung von beeindruckenden Artefakten. Sie müssen die Felder Ihrer [!DNL Adobe InDesign]-Vorlage nicht den Produktfeldern zuordnen, wie dies sonst beim Erstellen von Katalogen der Fall ist. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Web-Benutzeroberfläche bearbeiten. Damit Ihre Änderungen von [!DNL Adobe InDesign] verarbeitet werden können, müssen Sie aber zuerst [!DNL Experience Manager Assets] für die Integration in [!DNL Adobe InDesign Server] konfigurieren.

Die Möglichkeit zur Bearbeitung von [!DNL Adobe InDesign]-Vorlagen über die Web-Benutzeroberfläche trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern. Die höhere Inhaltsgeschwindigkeit reduziert die Time-to-Market für Marketingmaterial.

Sie können Asset-Vorlagen für folgende Zwecke nutzen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Web-Benutzeroberfläche.
* Steuern der grundlegenden Textformatierung, z. B. Schriftgrad, -stil und -typ auf Tag-Ebene.
* Ändern von Bildern in der Vorlage per Inhaltsauswahl.
* Anzeigen von Vorlagenbearbeitungen in der Vorschau.
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts.

Wenn Sie eine Vorlage für Ihr Marketingmaterial auswählen, erstellt [!DNL Experience Manager Assets] eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in den Formaten INDD, PDF oder JPG exportieren. Außerdem können Sie die Ausgabe in diesen Formaten in Ihr lokales Dateisystem herunterladen.

## Erstellen von Marketing-Material {#creating-a-collateral}

Stellen Sie sich einen Fall vor, in dem Sie digitales, druckbares Material, z. B. Broschüren, Flyer und Anzeigen, für eine anstehende Kampagne erstellen und für Ihre Filialgeschäfte weltweit bereitstellen möchten. Wenn Sie das Material basierend auf einer Vorlage erstellen, können Sie kanalübergreifend ein einheitliches Kundenerlebnis erzielen. Designer können die Kampagnenvorlagen (ein- oder mehrseitig) erstellen, indem sie eine Lösung für die Kreativarbeit nutzen, z. B. [!DNL InDesign], und die Vorlagen für Sie in [!DNL Experience Manager Assets] hochladen. Bevor Sie Marketing-Material erstellen, sollten Sie im Voraus mindestens eine INDD-Vorlage in [!DNL Experience Manager] hochladen und verfügbar machen.

1. Wählen Sie in der [!DNL Experience Manager]-Benutzeroberfläche [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]** aus.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Wählen Sie **[!UICONTROL Erstellen]** und dann im Menü das Marketing-Material aus, das Sie erstellen möchten. Wählen Sie beispielsweise die Option **[!UICONTROL Broschüre]** aus.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Sie sollten im Voraus eine oder mehrere INDD-Vorlagen in [!DNL Experience Manager] hochladen und verfügbar machen. Wählen Sie eine Vorlage für Ihre Broschüre aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie einen oder mehrere Tags für die Broschüre aus. Klicken Sie auf **[!UICONTROL Bestätigen]**, um Ihre Auswahl zu bestätigen.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. In einem Dialogfeld mit einem Hinweis wird bestätigt, dass eine neue Broschüre erstellt wurde. Klicken Sie auf **[!UICONTROL Öffnen]**, um die Broschüre im Bearbeitungsmodus zu öffnen.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ hierzu können Sie das Dialogfeld schließen und auf der Seite „Vorlagen“ zu dem Ordner navigieren, mit dem Sie den Vorgang begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht als die dazugehörige Miniaturansicht angezeigt. In diesem Fall wird in der Miniaturansicht beispielsweise das Wort [!UICONTROL Broschüre] angezeigt.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Marketing-Material {#editing-a-collateral}

Sie können Marketing-Material sofort nach dem Erstellen bearbeiten. Alternativ hierzu können Sie es über die Seite [!UICONTROL Vorlagen] oder die Asset-Seite öffnen.

1. Sie haben folgende Möglichkeiten, um das Marketingmaterial zur Bearbeitung zu öffnen:

   * Öffnen Sie das Marketing-Material (in diesem Fall die Broschüre), das Sie in Schritt 7 unter [Erstellen von Marketing-Material](/help/assets/asset-templates.md#creating-a-collateral) erstellt haben.
   * Navigieren Sie auf der Seite „Vorlagen“ zu einem Ordner, in dem Sie das Marketing-Material erstellt haben, und klicken Sie in der Miniaturansicht eines Materialelements auf die Schnellaktion [!UICONTROL Bearbeiten].
   * Klicken Sie auf der Asset-Seite für das Marketingmaterial in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.
   * Wählen Sie das Marketingmaterial aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Links auf der Seite werden die Asset-Suche und der Texteditor angezeigt. Der Texteditor ist standardmäßig geöffnet.

   Verwenden Sie den Texteditor, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgrad, -stil, -farbe und -typ auf der Tag-Ebene ändern.

   Zum Verwenden der Asset-Suche können Sie in [!DNL Experience Manager Assets] nach Bildern suchen und die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl ersetzen.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld in [!DNL Experience Manager Assets] bearbeitbar ist, muss das entsprechende Feld in der Vorlage in [!DNL InDesign]mit einem Tag versehen sein. Anders ausgedrückt: Es muss in [!DNL InDesign] als bearbeitbar gekennzeichnet sein.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Ihre [!DNL Experience Manager]-Implementierung in [!DNL InDesign Server] integriert ist, damit [!DNL Experience Manager Assets] Daten aus der [!DNL InDesign]-Vorlage extrahieren und für die Bearbeitung bereitstellen kann. Weitere Informationen finden Sie unter [Integrieren von Experience Manager Assets in InDesign Server](/help/assets/indesign.md).

1. Klicken Sie zum Ändern des Texts in einem bearbeitbaren Feld in der Liste mit den entsprechenden Feldern auf das Textfeld und bearbeiten Sie den Text.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, -farbe und -grad, mit den vorhandenen Optionen bearbeiten.

1. Wählen Sie **[!UICONTROL Vorschau]**, um eine Vorschau der Textänderungen anzuzeigen.

1. Um ein Bild auszutauschen, wählen Sie **[!UICONTROL Asset-Suche]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Schlüsselwörter, Tags oder den Veröffentlichungsstatus angeben. Sie können das [!DNL Experience Manager Assets]-Repository durchsuchen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Wählen Sie **[!UICONTROL Vorschau]**, um eine Vorschau des Bildes anzuzeigen.
1. Verwenden Sie unten die Optionen für die Seitennavigation, um für mehrseitiges Marketing-Material eine bestimmte Seite zu bearbeiten.

1. Wählen Sie in der Symbolleiste **[!UICONTROL Vorschau]**, um eine Vorschau für alle Änderungen anzuzeigen. Wählen Sie **[!UICONTROL Fertig]**, um die Änderungen für das Marketing-Material zu speichern.

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

1. Wählen Sie zum Generieren einer PDF-Ausgabedarstellung für die Broschüre im Dialogfeld die Acrobat-Option aus und klicken Sie anschließend auf **[!UICONTROL Weiter]**.
1. Das Material wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben. Öffnen Sie das Material und wählen Sie in der GlobalNav-Liste die Option **[!UICONTROL Ausgabedarstellungen]**, um die Ausgabedarstellungen anzuzeigen.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Wählen Sie in der Liste mit den Ausgabedarstellungen die PDF-Ausgabedarstellung aus, um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Marketingmaterial zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Zusammenführen von Maketingmaterial {#merge-collateral}

1. Wählen Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf der Navigationsseite die Option [!UICONTROL Assets] aus.

1. Wählen Sie aus den Optionen die Option **[!UICONTROL Vorlagen]** aus.

1. Wählen Sie **[!UICONTROL Erstellen]** und dann aus dem Menü die Option **[!UICONTROL Zusammenführen]** aus.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Wählen Sie auf der Seite [!UICONTROL Vorlagenzusammenführung] die Option **[!UICONTROL Zusammenführen]** ![Assets hinzufügen](assets/do-not-localize/assets_add_icon.png) aus.

1. Navigieren Sie zum Speicherort des Marketing-Materials, das Sie zusammenführen möchten, und wählen Sie die Miniaturansichten des entsprechenden Marketing-Materials aus, um es auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das Omnisearch-Feld nach Vorlagen suchen.

   Sie können das [!DNL Experience Manager Assets]-Repository bzw. die Sammlungen durchsuchen, zum Speicherort der gewünschten Vorlagen navigieren und sie dann für die Zusammenführung auswählen.

   Sie können verschiedene Filter anwenden, um nach den gewünschten Vorlagen zu suchen. Es ist beispielsweise möglich, basierend auf dem Dateityp oder auf Tags nach Vorlagen zu suchen.

1. Wählen Sie in der Symbolleiste die Option **[!UICONTROL Weiter]** aus.
1. Ordnen Sie die Vorlagen ggf. auf dem Bildschirm **[!UICONTROL Vorschau anzeigen und neu anordnen]** neu an und zeigen Sie eine Vorschau für die ausgewählten Vorlagen an, die zusammengeführt werden sollen. Wählen Sie in der Symbolleiste die Option **[!UICONTROL Weiter]** aus.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Geben Sie auf dem Bildschirm [!UICONTROL Vorlage konfigurieren] einen Namen für das Marketingmaterial an. Geben Sie optional Tags an, die jeweils geeignet sind. Wählen Sie **[!UICONTROL Acrobat (.PDF)]** aus, falls Sie die Ausgabe im PDF-Format exportieren möchten. Standardmäßig wird das Marketingmaterial im JPG- und [!DNL InDesign]-Format exportiert. Klicken Sie auf **[!UICONTROL Miniatur ändern]**, um die angezeigte Miniaturansicht für das mehrseitige Marketingmaterial zu ändern.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus und schließen Sie das Dialogfeld mit **[!UICONTROL OK]**. Das mehrseitige Marketing-Material wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Marketing-Material später zu ändern oder zum Erstellen von anderem Marketing-Material zu verwenden.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Der [!DNL InDesign]-Editor in [!DNL Experience Manager] funktioniert auf Tag-Ebene und der gesamte Text unter einem einzelnen Tag wird als einzelne Entität betrachtet. Damit die Textformatierung und die Stile beim Bearbeiten erhalten bleiben, müssen Sie jeden Absatz (oder Text mit unterschiedlichen Stilen) separat taggen.
