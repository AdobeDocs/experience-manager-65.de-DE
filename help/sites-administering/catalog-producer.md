---
title: Catalog Producer
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
description: Catalog Producer
exl-id: 76a46c62-d47d-4970-8a3a-d56015639548
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '847'
ht-degree: 39%

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
>Sie können die Elemente in Ihren InDesign-Vorlagen XML-Tags zuordnen. Die zugeordneten Tags werden als Eigenschaften angezeigt, wenn Sie die Produkteigenschaften den Vorlageneigenschaften in Catalog Producer zuordnen. Informationen zu XML-Tags in InDesign-Dateien finden Sie unter [Taggen von Inhalten für XML](https://helpx.adobe.com/de/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Als Vorlagen werden nur InDesign-Dateien (.indd) verwendet. Dateien mit der Erweiterung .indt werden nicht unterstützt.

## Erstellen eines Katalogs {#creating-a-catalog}

Catalog Producer verwendet Produktinformationsverwaltungsdaten (PIM), um Produkteigenschaften den in der Vorlage angezeigten XML-Eigenschaften zuzuordnen. Um einen Katalog zu erstellen, führen Sie die folgenden Schritte durch:

1. Klicken Sie in der Assets-Benutzeroberfläche auf das **AEM** und navigieren Sie zu **Assets > Kataloge**.
1. Im **Kataloge** Seite, klicken **Erstellen** in der Symbolleiste und wählen Sie **Katalog** aus der Liste.
1. Geben Sie auf der Seite **Katalog erstellen** einen Namen und eine Beschreibung (optional) für den Katalog ein. Sie können bei Bedarf auch Tags festlegen. Außerdem können Sie ein Miniaturbild für den Katalog hinzufügen.

   ![create_catalog](assets/create_catalog.png)

1. Klicken Sie auf **Speichern**. Ein Dialogfeld bestätigt, dass der Katalog erstellt wurde. Klicks **Fertig** , um das Dialogfeld zu schließen.
1. Um den von Ihnen erstellten Katalog zu öffnen, klicken Sie in der **Kataloge** Seite.

   >[!NOTE]
   >
   >Um den Katalog zu öffnen, klicken Sie auf **Öffnen** im Bestätigungsdialogfeld, das im vorherigen Schritt erwähnt wurde.

1. Um dem Katalog Seiten hinzuzufügen, klicken Sie auf **Erstellen** Wählen Sie in der Symbolleiste die **Neue Seite** -Option.
1. Wählen Sie im Assistenten eine InDesign-Vorlage für Ihre Seite aus. Klicken Sie dann auf **Weiter**.
1. Geben Sie einen Namen für die Seite und eine optionale Beschreibung an. Geben Sie gegebenenfalls Tags an.
1. Klicken Sie auf **Erstellen** aus der Symbolleiste. Klicken Sie anschließend auf **Öffnen** aus dem Dialogfeld. Die Eigenschaften für das Produkt werden im linken Bereich angezeigt. Die vordefinierten Eigenschaften für die InDesign-Vorlage werden im rechten Bereich angezeigt.
1. Ziehen Sie aus dem linken Bereich die Produkteigenschaften in die Eigenschaften der InDesign-Vorlage und erstellen Sie eine Zuordnung zwischen ihnen.

   Um anzuzeigen, wie die Seite in Echtzeit angezeigt wird, klicken Sie auf das **Vorschau** im rechten Bereich.

1. Wenn Sie weitere Seiten erstellen möchten, wiederholen Sie die Schritte 6–9. Um ähnliche Seiten für andere Produkte zu erstellen, wählen Sie die Seite aus und klicken Sie auf die Schaltfläche **Erstellen ähnlicher Seiten** in der Symbolleiste.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >Sie können nur ähnliche Seiten für Produkte mit ähnlicher Struktur erstellen.

   Klicken Sie auf das Symbol Hinzufügen , wählen Sie Produkte aus der Produktauswahl aus und klicken Sie dann auf **Auswählen** aus der Symbolleiste.

   ![select_product](assets/select_product.png)

1. Klicken Sie in der Symbolleiste auf **Erstellen**. Klicks **Fertig** , um das Dialogfeld zu schließen. Ähnliche Seiten sind in Ihrem Katalog enthalten.
1. Um eine vorhandene InDesign-Datei zu Ihrem Katalog hinzuzufügen, klicken Sie auf **Erstellen** in der Symbolleiste und wählen Sie die **Hinzufügen zu vorhandener Seite** -Option.
1. Wählen Sie die InDesign-Datei aus und klicken Sie auf **Hinzufügen** aus der Symbolleiste. Klicken Sie anschließend auf **OK** , um das Dialogfeld zu schließen.

   Wenn die Metadaten der Produkte, auf die Sie auf den Katalogseiten verweisen, sich ändern, werden diese Änderungen von den Katalogseiten nicht automatisch übernommen. Dafür wird ein Banner mit der Beschriftung **Veraltet** auf den Produktbildern auf den entsprechenden Katalogseiten angezeigt. Es weist darauf hin, dass die Metadaten für diese Produkte nicht aktuell sind.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Um sicherzustellen, dass die Produktbilder die neuesten Metadatenänderungen widerspiegeln, wählen Sie die Seite in der Katalogkonsole aus und klicken Sie auf **Seite aktualisieren** in der Symbolleiste.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Um die Metadaten für ein referenziertes Produkt zu ändern, navigieren Sie zur Produktkonsole (**AEM-Logo** > **Commerce** > **Produkte**). Wählen Sie dort das Produkt aus. Klicken Sie dann auf die **Eigenschaften anzeigen** in der Symbolleiste und bearbeiten Sie die Metadaten auf der Seite Eigenschaften des Assets.

1. Um die Seiten im Katalog neu anzuordnen, klicken Sie auf das **Erstellen** Symbol in der Symbolleiste und wählen Sie dann **Zusammenführen** aus dem Menü. Im Assistenten können Sie mit dem Karussell oben die Seiten durch Ziehen neu anordnen. Sie können Seiten auch entfernen.

1. Klicken Sie auf **Weiter**. Um eine vorhandene InDesign-Datei als Titelseite hinzuzufügen, klicken Sie auf **Durchsuchen** neben dem **Titelseite auswählen** und geben Sie den Pfad für die Titelseitenvorlage an.
1. Klicks **Speichern** und klicken Sie anschließend auf **Fertig** , um das Bestätigungsdialogfeld zu schließen.
Bei Auswahl der Option **Fertig** wird ein Dialogfeld geöffnet, in dem Sie auswählen können, ob Sie die PDF-Ausgabedarstellung verwenden möchten.
   ![In PDF exportieren](assets/CatalogPDF.png)
Wenn die Option „Acrobat (PDF)“ ausgewählt ist, wird zusätzlich zur InDesign-Ausgabedarstellung eine PDF-Ausgabedarstellung in **/jcr:content/renditions** erstellt. Sie können alle Ausgabedarstellungen herunterladen, indem Sie das Kontrollkästchen „Ausgabedarstellungen“ im Dialogfeld „Herunterladen“ aktivieren.

1. Um eine Vorschau des erstellten Katalogs zu generieren, wählen Sie den Katalog in der Konsole **Katalog** aus und klicken Sie in der Symbolleiste auf das Symbol **Vorschau**.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Überprüfen Sie die Seiten in Ihrem Katalog in der Vorschau. Klicks **Schließen** , um die Vorschau zu schließen.
