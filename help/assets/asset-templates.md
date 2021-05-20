---
title: Asset-Vorlagen
description: Erfahren Sie mehr über Asset-Vorlagen in [!DNL Adobe Experience Manager Assets] und wie Sie mit Asset-Vorlagen Marketingmaterialien erstellen können.
contentOwner: AG
role: Business Practitioner
feature: Asset Management,Entwicklertools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1548'
ht-degree: 33%

---

# Asset-Vorlagen {#asset-templates}

Asset-Vorlagen sind eine spezielle Asset-Klasse, die die schnelle Wiederverwendung visuell ansprechender Inhalte für digitale und Druckmedien erleichtert. Eine Asset-Vorlage enthält zwei Teile: den unveränderlichen Messagingabschnitt und den bearbeitbaren Abschnitt. Der unveränderliche Messagingabschnitt kann proprietären Inhalt enthalten, z. B. das Markenlogo und Copyright-Informationen, die nicht bearbeitet werden können. Der bearbeitbare Bereich kann visuelle und textuelle Inhalte in Feldern enthalten, die bearbeitet werden können, um Nachrichten anzupassen.

Die Flexibilität, begrenzte Änderungen vorzunehmen und gleichzeitig die globale Beschilderung zu sichern, macht Asset-Vorlagen zu idealen Bausteinen für die schnelle Anpassung und Verteilung von Inhalten als Inhaltsartefakte für verschiedene Funktionen. Die Wiederverwendung von Inhalten trägt dazu bei, die Kosten für die Verwaltung von Druck- und digitalen Kanälen zu senken und ganzheitliche und konsistente Erlebnisse über diese Kanäle hinweg bereitzustellen.

Als Marketer können Sie Vorlagen in [!DNL Experience Manager Assets] speichern und verwalten und eine einfache Basisvorlage verwenden, um auf einfache Weise mehrere personalisierte Druckerfahrungen zu erstellen. Sie können verschiedene Arten von Marketingmaterial erstellen, z. B. Broschüren, Flyer, Postkarten, Visitenkarten usw., um Kunden Ihre Marketingbotschaft eindeutig und klar zu vermitteln. Außerdem können Sie aus vorhandenen oder neuen Druckausgaben mehrseitige Druckausgaben zusammenstellen. Und das Beste ist: Sie können ohne großen Aufwand gleichzeitig digitale Umgebungen und Printumgebungen bereitstellen, um für Benutzer eine konsistente integrierte Erfahrung zu schaffen.

Während Asset-Vorlagen hauptsächlich [!DNL Adobe InDesign]-Dateien sind, ist die Kompetenz in [!DNL Adobe InDesign] keine Barriere für die Erstellung von Sternartefakten. Sie müssen die Felder Ihrer [!DNL Adobe InDesign]-Vorlage nicht Ihren Produktfeldern zuordnen, die Sie sonst beim Erstellen von Katalogen benötigen. Sie können die Vorlagen im WYSIWYG-Modus direkt auf der Web-Oberfläche bearbeiten. Damit [!DNL Adobe InDesign] Ihre Bearbeitungsänderungen verarbeiten kann, müssen Sie [!DNL Experience Manager Assets] zunächst zur Integration mit [!DNL Adobe InDesign Server] konfigurieren.

Die Möglichkeit, [!DNL Adobe InDesign]-Vorlagen über die Web-Oberfläche zu bearbeiten, trägt dazu bei, die Zusammenarbeit zwischen Kreativ- und Marketingmitarbeitern zu verbessern. Die höhere Content-Geschwindigkeit reduziert die Time-to-Market für Marketing-Collaterals.

Mit Asset-Vorlagen können Sie Folgendes erreichen:

* Ändern von bearbeitbaren Vorlagenfeldern über die Webbenutzeroberfläche.
* Steuern der grundlegenden Textformatierung, z. B. Schriftgröße, -stil und -typ auf Tag-Ebene.
* Ändern von Bildern in der Vorlage per Inhaltsauswahl.
* Anzeigen von Vorlagenbearbeitungen in der Vorschau.
* Zusammenführen mehrerer Vorlagendateien zum Erstellen eines mehrseitigen Artefakts.

Wenn Sie eine Vorlage für Ihr Material auswählen, erstellt [!DNL Experience Manager Assets] eine Kopie der Vorlage, die Sie bearbeiten können. Die ursprüngliche Vorlage wird beibehalten, um sicherzustellen, dass Ihre globalen Logos und Unternehmenskennzeichnungen intakt bleiben und wiederverwendet werden können, um für eine einheitliche Markendarstellung zu sorgen.

Sie können die aktualisierte Datei im übergeordneten Ordner in die Formate INDD, PDF oder JPG exportieren. Sie können die Ausgabe in diesen Formaten auch in Ihr lokales Dateisystem herunterladen.

## Erstellen Sie ein Material {#creating-a-collateral}

Stellen Sie sich einen Fall vor, in dem Sie digitales druckbares Marketingmaterial, z. B. Broschüren, Flyer und Anzeigen, für eine anstehende Kampagne erstellen und für Ihre Geschäfte weltweit bereitstellen möchten. Wenn Sie das Material basierend auf einer Vorlage erstellen, können Sie kanalübergreifend eine einheitliche Kundenerfahrung erzielen. Designer können die Kampagnenvorlagen (einseitige oder mehrseitige) mithilfe einer kreativen Lösung wie [!DNL InDesign] erstellen und die Vorlagen für Sie in [!DNL Experience Manager Assets] hochladen. Bevor Sie ein Material erstellen, lassen Sie eine oder mehrere INDD-Vorlagen im Voraus in [!DNL Experience Manager] hochladen und verfügbar sein.

1. Klicken Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie dann im Menü das zu erstellende Material aus. Wählen Sie beispielsweise **[!UICONTROL Broschüre]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Lassen Sie eine oder mehrere INDD-Vorlagen im Voraus in [!DNL Experience Manager] hochgeladen und verfügbar. Wählen Sie eine Vorlage für Ihre Broschüre aus und klicken Sie auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Namen und eine optionale Beschreibung für die Broschüre an.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optional) Klicken Sie auf **[!UICONTROL Tags]** und wählen Sie mindestens ein Tag für die Broschüre aus. Klicken Sie auf **[!UICONTROL Bestätigen]** , um Ihre Auswahl zu bestätigen.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. In einem Dialogfeld mit einem Hinweis wird bestätigt, dass eine neue Broschüre erstellt wurde. Klicken Sie auf **[!UICONTROL Öffnen]** , um die Broschüre im Bearbeitungsmodus zu öffnen.

   <!--![chlimage_1-106](assets/.png) -->

   Alternativ hierzu können Sie das Dialogfeld schließen und auf der Seite „Vorlagen“ zu dem Ordner navigieren, mit dem Sie den Vorgang begonnen haben, um die erstellte Broschüre anzuzeigen. Der Typ des Materials wird in der Kartenansicht in der dazugehörigen Miniaturansicht angezeigt. In diesem Fall wird beispielsweise das Wort [!UICONTROL Broschüre] auf der Miniaturansicht angezeigt.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Bearbeiten von Zusätzen {#editing-a-collateral}

Sie können Material sofort nach dem Erstellen bearbeiten. Alternativ können Sie sie über die Seite [!UICONTROL Vorlagen] oder die Asset-Seite öffnen.

1. Sie haben folgende Möglichkeiten, um das Material zur Bearbeitung zu öffnen:

   * Öffnen Sie das Material (in diesem Fall die Broschüre), das Sie in Schritt 7 von [Erstellen Sie ein Material](/help/assets/asset-templates.md#creating-a-collateral) erstellt haben.
   * Navigieren Sie auf der Seite &quot;Vorlagen&quot;zu einem Ordner, in dem Sie das Material erstellt haben, und klicken Sie auf die Schnellaktion [!UICONTROL Bearbeiten] in der Miniaturansicht eines Materials.
   * Klicken Sie auf der Asset-Seite für das Material in der Symbolleiste auf **[!UICONTROL Bearbeiten]** .
   * Wählen Sie das Material aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]** .

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   Links auf der Seite werden die Asset-Suche und der Text-Editor angezeigt. Der Text-Editor ist standardmäßig geöffnet.

   Sie können den Text-Editor verwenden, um den Text zu ändern, der im Textfeld angezeigt werden soll. Sie können Schriftgröße, -stil, -farbe und -typ auf der Tag-Ebene ändern.

   Mit der Asset-Suche können Sie in [!DNL Experience Manager Assets] nach Bildern suchen oder nach Bildern suchen und die bearbeitbaren Bilder in der Vorlage durch Bilder Ihrer Wahl ersetzen.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   Die bearbeitbaren Bilder werden rechts angezeigt. Damit ein Feld in [!DNL Experience Manager Assets] bearbeitet werden kann, muss das entsprechende Feld in der Vorlage mit [!DNL InDesign] markiert sein. Mit anderen Worten, sie sollten in [!DNL InDesign] als bearbeitbar markiert werden.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Ihre [!DNL Experience Manager]-Implementierung in eine [!DNL InDesign Server] integriert ist, damit [!DNL Experience Manager Assets] Daten aus der [!DNL InDesign]-Vorlage extrahieren und zur Bearbeitung verfügbar machen kann. Weitere Informationen finden Sie unter [Integrieren von Experience Manager-Assets mit InDesign Server](/help/assets/indesign.md).

1. Um den Text in einem bearbeitbaren Feld zu ändern, klicken Sie in der Liste der bearbeitbaren Felder auf das Textfeld und bearbeiten Sie den Text im Feld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   Sie können die Texteigenschaften, z. B. Schriftstil, Farbe und Größe, mithilfe der bereitgestellten Optionen bearbeiten.

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um eine Vorschau der Textänderungen anzuzeigen.

1. Um ein Bild auszutauschen, klicken Sie auf **[!UICONTROL Asset Finder]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Wählen Sie in der Liste mit den bearbeitbaren Feldern das Bildfeld aus und ziehen Sie das gewünschte Bild dann aus der Asset-Auswahl in das bearbeitbare Feld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   Sie können auch nach Bildern suchen, indem Sie Stichwörter, Tags und den Veröffentlichungsstatus angeben. Sie können das [!DNL Experience Manager Assets]-Repository durchsuchen und zum Speicherort des gewünschten Bildes navigieren.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Klicken Sie auf **[!UICONTROL Vorschau]** , um eine Vorschau des Bildes anzuzeigen.
1. Um eine bestimmte Seite in einem mehrseitigen Material zu bearbeiten, verwenden Sie den Seitennavigator am unteren Rand.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Vorschau]** , um eine Vorschau aller Änderungen anzuzeigen. Klicken Sie auf **[!UICONTROL Fertig]** , um die Bearbeitungsänderungen am Material zu speichern.

   >[!NOTE]
   >
   >Die Optionen Vorschau und Fertig sind nur dann aktiviert, wenn die bearbeitbaren Bildfelder im Material keine fehlenden Symbole aufweisen. Wenn in Ihrem Material Symbole fehlen, liegt dies daran, dass [!DNL Experience Manager] die Bilder in der [!DNL InDesign]-Vorlage nicht auflösen kann. Normalerweise kann [!DNL Experience Manager] in folgenden Fällen keine Bilder auflösen:
   >
   >* Bilder werden nicht in die zugrunde liegende [!DNL InDesign]-Vorlage eingebettet.
   >* Bilder verfügen über Verknüpfungen mit dem lokalen Dateisystem.

   >
   >Gehen Sie wie folgt vor, um [!DNL Experience Manager] zu aktivieren, um Bilder aufzulösen:
   >
   >* Betten Sie Bilder beim Erstellen von [!DNL InDesign]-Vorlagen ein (siehe [Über Links und eingebettete Grafiken](https://helpx.adobe.com/de/indesign/using/graphics-links.html)).
   >* Stellen Sie [!DNL Experience Manager] in Ihr lokales Dateisystem ein und ordnen Sie dann fehlende Symbole vorhandenen Assets in [!DNL Experience Manager] zu.

   >
   >Weitere Informationen zum Arbeiten mit [!DNL InDesign]-Dokumenten finden Sie unter [Best Practices zum Arbeiten mit InDesign-Dokumenten in Experience Manager](https://helpx.adobe.com/de/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Wählen Sie zum Generieren einer PDF-Ausgabe für die Broschüre im Dialogfeld die Acrobat-Option aus und klicken Sie anschließend auf **[!UICONTROL Weiter]**.
1. Das Marketingmaterial wird in dem Ordner erstellt, in dem Sie den Vorgang begonnen haben. Öffnen Sie das Marketingmaterialelement und wählen Sie in der GlobalNav-Liste die Option **[!UICONTROL Ausgabeformate]**, um die Ausgabeformate anzuzeigen.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Klicken Sie in der Liste der Ausgabeformate auf die PDF-Ausgabe, um die PDF-Datei herunterzuladen. Öffnen Sie die PDF-Datei, um das Material zu überprüfen.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Zusammenführen von Sicherheiten {#merge-collateral}

1. Klicken Sie in der [!DNL Experience Manager]-Benutzeroberfläche auf der Navigationsseite auf [!UICONTROL Assets].

1. Wählen Sie in den Optionen die Option **[!UICONTROL Vorlagen]**.

1. Klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Zusammenführen]** aus dem Menü aus.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Klicken Sie auf der Seite [!UICONTROL Vorlagenzusammenführung] auf **[!UICONTROL Zusammenführen]** ![Hinzufügen von Assets](assets/do-not-localize/assets_add_icon.png).

1. Navigieren Sie zum Speicherort des Assets, das Sie zusammenführen möchten, und klicken Sie auf die Miniaturansichten des Assets, das Sie zusammenführen möchten, um es auszuwählen.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   Sie können auch über das OmniSearch-Feld nach Vorlagen suchen.

   Sie können das [!DNL Experience Manager Assets]-Repository oder die Sammlungen durchsuchen, zum Speicherort der gewünschten Vorlagen navigieren und diese dann zum Zusammenführen auswählen.

   Sie können verschiedene Filter anwenden, um nach den gewünschten Vorlagen zu suchen. Es ist beispielsweise möglich, basierend auf dem Dateityp oder auf Tags nach Vorlagen zu suchen.

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Ordnen Sie die Vorlagen im Bildschirm **[!UICONTROL Vorschau &amp; Neu anordnen]** bei Bedarf neu an und zeigen Sie eine Vorschau der Auswahl der zusammenzuführenden Vorlagen an. Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]** .

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Geben Sie im Bildschirm [!UICONTROL Vorlage konfigurieren] einen Namen für das Material an. Geben Sie optional Tags an, die jeweils geeignet sind. Wenn Sie die Ausgabe im PDF-Format exportieren möchten, wählen Sie **[!UICONTROL Acrobat (.PDF)]** aus. Standardmäßig wird das Material im JPG- und [!DNL InDesign]-Format exportiert. Um die Miniaturansicht für mehrseitige Assets zu ändern, klicken Sie auf **[!UICONTROL Miniaturansicht ändern]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Klicken Sie auf **[!UICONTROL Save]** und dann im Dialogfeld auf **[!UICONTROL OK]** , um das Dialogfeld zu schließen. Das mehrseitige Material wird in dem Ordner erstellt, mit dem Sie begonnen haben.

   >[!NOTE]
   >
   >Es ist nicht möglich, zusammengeführtes Material später zu ändern oder zum Erstellen von anderem Material zu verwenden.

## Best Practices und Einschränkungen {#best-practices-limitations-tips}

* Der [!DNL InDesign]-Editor in [!DNL Experience Manager] funktioniert auf Tag-Ebene und der gesamte Text unter einem einzelnen Tag wird als einzelne Entität betrachtet. Damit die Textformatierung und die Stile beim Bearbeiten erhalten bleiben, müssen Sie jeden Absatz (oder Text mit unterschiedlichen Stilen) separat taggen.
