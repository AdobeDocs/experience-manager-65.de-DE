---
title: Catalog Producer
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
description: Catalog Producer
exl-id: 76a46c62-d47d-4970-8a3a-d56015639548
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 100%

---

# Catalog Producer{#catalog-producer}

Erfahren Sie, wie Sie mit Catalog Producer in AEM Assets Produktkataloge mit Ihren digitalen Assets erstellen können.

Mit dem Catalog Producer von Adobe Experience Manager (AEM) Assets können Sie mit InDesign-Vorlagen, die Sie aus einer InDesign-Anwendung importieren, Kataloge für Ihre Markenprodukte erstellen. Um InDesign-Vorlagen zu importieren, integrieren Sie zunächst AEM Assets mit einem InDesign-Server.

## Integration mit einem InDesign-Server {#integrating-with-indesign-server}

Als Teil des Integrationsvorgangs konfigurieren Sie den Workflow **DAM-Update-Asset**, der sich besonders für die Integration mit InDesign eignet. Konfigurieren Sie außerdem einen Proxy Worker für den InDesign-Server. Weitere Informationen finden Sie unter [Integrieren von AEM Assets mit InDesign Server](/help/assets/indesign.md).

>[!NOTE]
>
>Sie können InDesign-Vorlagen aus InDesign-Dateien generieren, bevor Sie sie in AEM Assets importieren. Weitere Informationen finden Sie unter [Arbeiten mit Dateien und Vorlagen](https://helpx.adobe.com/de/indesign/using/files-templates.html).
>
>Sie können den Elementen in Ihren InDesign-Vorlagen XML-Tags zuordnen. Die zugeordneten Tags werden als Eigenschaften angezeigt, wenn Sie die Produkteigenschaften den Vorlageneigenschaften in Catalog Producer zuordnen. Informationen zu XML-Tags in InDesign-Dateien finden Sie unter [Taggen von Inhalten für XML](https://helpx.adobe.com/de/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Als Vorlagen werden nur InDesign-Dateien (INDD) verwendet. Dateien mit der Erweiterung INDT werden nicht unterstützt.

## Erstellen eines Katalogs {#creating-a-catalog}

Catalog Producer verwendet Produktinformationsverwaltungsdaten (PIM), um Produkteigenschaften den in der Vorlage angezeigten XML-Eigenschaften zuzuordnen. Um einen Katalog zu erstellen, führen Sie die folgenden Schritte durch:

1. Klicken Sie in der Assets-Oberfläche auf das **AEM-Logo**. Rufen Sie dann **Assets > Kataloge** auf.
1. Klicken Sie auf der Seite **Kataloge** in der Symbolleiste auf **Erstellen**. Wählen Sie anschließend aus der Liste **Katalog** aus.
1. Geben Sie auf der Seite **Katalog erstellen** einen Namen und eine Beschreibung (optional) für den Katalog ein. Sie können bei Bedarf auch Tags festlegen. Außerdem können Sie ein Miniaturbild für den Katalog hinzufügen.

   ![create_catalog](assets/create_catalog.png)

1. Klicken Sie auf **Speichern**. Ein Dialogfeld bestätigt, dass der Katalog erstellt wurde. Klicken Sie auf **Fertig**, um das Dialogfeld zu schließen.
1. Um den erstellten Katalog zu öffnen, klicken Sie auf der Seite **Kataloge** darauf.

   >[!NOTE]
   >
   >Alternativ können Sie auch in dem Dialogfeld, das im vorhergehenden Schritt erwähnt wurde, auf **Öffnen** klicken.

1. Um Seiten zum Katalog hinzuzufügen, klicken Sie in der Symbolleiste auf **Erstellen** und wählen dann die Option **Neue Seite** aus.
1. Wählen Sie im Assistenten eine InDesign-Vorlage für Ihre Seite aus. Klicken Sie dann auf **Weiter**.
1. Geben Sie einen Namen für die Seite und optional eine Beschreibung an. Geben Sie gegebenenfalls Tags an.
1. Klicken Sie in der Symbolleiste auf **Erstellen**. Klicken Sie dann im Dialogfeld auf **Öffnen**. Die Eigenschaften für das Produkt werden im linken Bereich angezeigt. Die vordefinierten Eigenschaften für die InDesign-Vorlage werden im rechten Bereich angezeigt.
1. Ziehen Sie aus dem linken Bereich die Produkteigenschaften in die Eigenschaften der InDesign-Vorlage und erstellen Sie eine Zuordnung zwischen ihnen.

   Um anzuzeigen, wie die Seite in Echtzeit angezeigt wird, klicken Sie im rechten Bereich auf die Registerkarte **Vorschau**.

1. Wenn Sie weitere Seiten erstellen möchten, wiederholen Sie die Schritte 6–9. Um ähnliche Seiten für andere Produkte zu erstellen, wählen Sie die Seite aus und klicken Sie in der Symbolleiste auf das Symbol **Ähnliche Seiten erstellen**.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >Sie können nur ähnliche Seiten für Produkte mit ähnlicher Struktur erstellen.

   Klicken Sie auf das Symbol zum Hinzufügen, wählen Sie die Produkte aus Produktauswahl aus und klicken Sie dann in der Symbolleiste auf **Auswählen**.

   ![select_product](assets/select_product.png)

1. Klicken Sie in der Symbolleiste auf **Erstellen**. Klicken Sie auf **Fertig**, um das Dialogfeld zu schließen. Ähnliche Seiten sind in Ihrem Katalog enthalten.
1. Um eine vorhandene InDesign-Datei zu Ihrem Katalog hinzuzufügen, klicken Sie in der Symbolleiste auf **Erstellen** und wählen Sie die Option **Zu vorhandener Seite hinzufügen** aus.
1. Wählen Sie die InDesign-Datei aus und klicken Sie in der Symbolleiste auf **Hinzufügen**. Klicken Sie dann auf **OK**, um das Dialogfeld zu schließen.

   Wenn die Metadaten der Produkte, auf die Sie auf den Katalogseiten verweisen, sich ändern, werden diese Änderungen von den Katalogseiten nicht automatisch übernommen. Dafür wird ein Banner mit der Beschriftung **Veraltet** auf den Produktbildern auf den entsprechenden Katalogseiten angezeigt. Es weist darauf hin, dass die Metadaten für diese Produkte nicht aktuell sind.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Um sicherzustellen, dass die Produktbilder die neuesten Änderungen der Metadaten widerspiegeln, wählen Sie die Seite in der Katalogkonsole aus und klicken Sie in der Symbolleiste auf das Symbol **Seite aktualisieren**.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Um die Metadaten für ein referenziertes Produkt zu ändern, navigieren Sie zur Produktkonsole (**AEM-Logo** > **Commerce** > **Produkte**). Wählen Sie dort das Produkt aus. Klicken Sie dann in der Symbolleiste auf das Symbol **Eigenschaften anzeigen** und bearbeiten Sie auf der Seite mit den Eigenschaften des Assets die Metadaten.

1. Um die Seiten im Katalog neu anzuordnen, klicken Sie in der Symbolleiste auf das Symbol **Erstellen**. Wählen Sie dann **Zusammenführen** aus dem Menü aus. Im Assistenten können Sie über das Karussell am oberen Bildschirmrand die Seiten durch Ziehen neu anordnen. Sie können auch Seiten entfernen.

1. Klicken Sie auf **Weiter**. Um eine vorhandene InDesign-Datei als Titelseite zum Katalog hinzuzufügen, klicken Sie auf **Durchsuchen** neben dem Feld **Titelseite wählen** und geben Sie den Pfad der gewünschten Titelseitenvorlage ein.
1. Klicken Sie auf **Speichern** und dann auf **Fertig**, um den Bestätigungsdialog u schließen.
Bei Auswahl der Option **Fertig** wird ein Dialogfeld geöffnet, in dem Sie auswählen können, ob Sie die PDF-Ausgabedarstellung verwenden möchten.
   ![In PDF exportieren](assets/CatalogPDF.png)
Wenn die Option „Acrobat (PDF)“ ausgewählt ist, wird zusätzlich zur InDesign-Ausgabedarstellung eine PDF-Ausgabedarstellung in **/jcr:content/renditions** erstellt. Sie können alle Ausgabedarstellungen herunterladen, indem Sie das Kontrollkästchen „Ausgabedarstellungen“ im Dialogfeld „Herunterladen“ aktivieren.

1. Um eine Vorschau des erstellten Katalogs zu generieren, wählen Sie den Katalog in der Konsole **Katalog** aus und klicken Sie in der Symbolleiste auf das Symbol **Vorschau**.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Überprüfen Sie die Seiten in Ihrem Katalog in der Vorschau. Klicken Sie auf **Schließen**, um die Vorschau zu schließen.
