---
title: Catalog Producer
seo-title: Catalog Producer
seo-description: Learn how to use Catalog Producer in AEM Assets to generate product catalogs using your digital assets.
uuid: da822d83-8b99-4089-ae1b-11d897d4044e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 90e36522-3af1-4a8a-b044-1c828c52974e
description: Catalog Producer
exl-id: 76a46c62-d47d-4970-8a3a-d56015639548
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '882'
ht-degree: 100%

---

# Catalog Producer{#catalog-producer}

Erfahren Sie, wie Sie mit Catalog Producer in AEM Assets Produktkataloge mit Ihren digitalen Assets generieren.

Mit dem Catalog Producer von Adobe Experience Manager (AEM) Assets können Sie mit InDesign-Vorlagen, die Sie aus einer InDesign-Anwendung importieren, Kataloge für Ihre Markenprodukte erstellen. Um InDesign-Vorlagen zu importieren, integrieren Sie zunächst AEM Assets mit einem InDesign-Server.

## Integration mit einem InDesign-Server {#integrating-with-indesign-server}

Als Teil des Integrationsvorgangs konfigurieren Sie den Workflow **DAM-Update-Asset**, der sich besonders für die Integration mit InDesign eignet. Konfigurieren Sie außerdem einen Proxy Worker für den InDesign-Server. Weitere Informationen finden Sie unter [Integrieren von AEM Assets mit InDesign Server](/help/assets/indesign.md).

>[!NOTE]
>
>Sie können aus InDesign-Dateien InDesign-Vorlagen erstellen, bevor Sie sie in AEM Assets importieren. Weitere Informationen finden Sie unter [Arbeiten mit Dateien und Vorlagen](https://helpx.adobe.com/de/indesign/using/files-templates.html).
>
>Sie können die Elemente in Ihren InDesign-Vorlagen XML-Tags zuordnen. Die zugeordneten Tags werden als Eigenschaften angezeigt, wenn Sie im Catalog Producer den Vorlageneigenschaften Produkteigenschaften zuordnen. Informationen zu XML-Tags in InDesign-Dateien finden Sie unter [Taggen von Inhalten für XML](https://helpx.adobe.com/de/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Nur InDesign-Dateien (.indd) werden als Vorlagen verwendet. Dateien mit der Erweiterung .indt werden nicht unterstützt.

## Erstellen eines Katalogs {#creating-a-catalog}

Der Catalog Producer verwendet Daten der Produktdatenverwaltung (PIM), um Produkteigenschaften den in der Vorlage angezeigten XML-Eigenschaften zuzuordnen. Um einen Katalog zu erstellen, führen Sie die folgenden Schritte durch:

1. Tippen oder klicken Sie in der Assets-Oberfläche auf das **AEM-Logo**. Rufen Sie dann **Assets > Kataloge** auf.
1. Tippen oder klicken Sie auf der Seite **Kataloge** in der Symbolleiste auf **Erstellen**. Wählen Sie anschließend aus der Liste **Katalog** aus.
1. Geben Sie auf der Seite **Katalog erstellen** einen Namen und eine Beschreibung (optional) für den Katalog ein. Sie können bei Bedarf auch Tags festlegen. Außerdem können Sie ein Miniaturbild für den Katalog hinzufügen.

   ![create_catalog](assets/create_catalog.png)

1. Tippen oder klicken Sie auf **Speichern**. Ein Dialogfeld bestätigt, dass der Katalog erstellt wurde. Tippen oder klicken Sie auf **Fertig**, um das Dialogfeld zu schließen.
1. Um den erstellten Katalog zu öffnen, tippen oder klicken Sie auf der Seite **Kataloge** darauf.

   >[!NOTE]
   >
   >Alternativ können Sie auch in dem Dialogfeld, das im vorhergehenden Schritt genannt wurde, auf **Öffnen** tippen oder klicken.

1. Um Seiten zum Katalog hinzuzufügen, tippen oder klicken Sie in der Symbolleiste auf **Erstellen** und wählen dann die Option **Neue Seite** aus.
1. Wählen Sie im Assistenten eine InDesign-Vorlage für Ihre Seite aus. Tippen oder klicken Sie anschließend auf **Weiter**.
1. Geben Sie einen Namen für die Seite sowie eine optionale Beschreibung an. Legen Sie ggf. Tags fest.
1. Tippen oder klicken Sie in der Symbolleiste auf **Erstellen**. Tippen oder klicken Sie dann im Dialogfeld auf **Öffnen**. Die Eigenschaften des Produkts werden im linken Fensterbereich angezeigt. Die vordefinierten Eigenschaften der InDesign-Vorlage werden im rechten Bereich angezeigt.
1. Ziehen Sie die Produkteigenschaften aus dem linken Bereich in die InDesign-Vorlageneigenschaften und erstellen Sie eine Zuordnung zwischen diesen Eigenschaften.

   Um anzuzeigen, wie die Seite in Echtzeit angezeigt wird, tippen oder klicken Sie im rechten Bereich auf die Registerkarte **Vorschau**.

1. Wenn Sie weitere Seiten erstellen möchten, wiederholen Sie die Schritte 6–9. Um ähnliche Seiten für andere Produkte zu erstellen, wählen Sie die Seite aus und tippen oder klicken Sie auf das Symbol **Ähnliche Seiten erstellen** in der Symbolleiste.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >Sie können nur ähnliche Seiten für Produkte mit ähnlicher Struktur erstellen.

   Tippen oder klicken Sie auf das Symbol zum Hinzufügen, wählen Sie die Produkte aus Produktauswahl aus und tippen oder klicken Sie in der Symbolleiste auf **Auswählen**.

   ![select_product](assets/select_product.png)

1. Klicken oder tippen Sie in der Symbolleiste auf **Erstellen**. Tippen oder klicken Sie auf **Fertig**, um das Dialogfeld zu schließen. Ähnliche Seiten sind in Ihrem Katalog enthalten.
1. Um eine vorhandene InDesign-Datei zu Ihrem Katalog hinzuzufügen, tippen oder klicken Sie in der Symbolleiste auf **Erstellen** und wählen Sie die Option **Zu vorhandener Seite hinzufügen** aus.
1. Wählen Sie die InDesign-Datei aus und tippen oder klicken Sie in der Symbolleiste auf **Hinzufügen**. Tippen oder klicken Sie dann auf **OK**, um das Dialogfeld zu schließen.

   Wenn die Metadaten der Produkte, auf die Sie auf den Katalogseiten verweisen, sich ändern, werden diese Änderungen von den Katalogseiten nicht automatisch übernommen. Dafür wird ein Banner mit der Beschriftung **Veraltet** auf den Produktbildern auf den entsprechenden Katalogseiten angezeigt. Es weist darauf hin, dass die Metadaten für diese Produkte nicht aktuell sind.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Um sicherzustellen, dass die Produktbilder die neuesten Änderungen der Metadaten widerspiegeln, wählen Sie die Seite in der Katalogkonsole aus und tippen oder klicken Sie in der Symbolleiste auf das Symbol **Seite aktualisieren**.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Um die Metadaten für ein referenziertes Produkt zu ändern, navigieren Sie zur Produktkonsole (**AEM-Logo** > **Commerce** > **Produkte**). Wählen Sie dort das Produkt aus. Tippen oder klicken Sie dann in der Symbolleiste auf das Symbol **Eigenschaften anzeigen** und bearbeiten Sie auf der Seite mit den Eigenschaften des Assets die Metadaten.

1. Um die Seiten im Katalog neu anzuordnen, tippen oder klicken Sie in der Symbolleiste auf das Symbol **Erstellen**. Wählen Sie dann aus dem Menü **Zusammenführen** aus. Im Assistenten können Sie über das Karussell am oberen Bildschirmrand die Seiten durch Ziehen neu anordnen. Sie können Seiten auch entfernen.

1. Tippen oder klicken Sie auf **Weiter**. Um eine vorhandene InDesign-Datei als Titelseite zum Katalog hinzuzufügen, tippen oder klicken Sie auf **Durchsuchen** neben dem Feld **Titelseite wählen**. Geben Sie den Pfad der gewünschten Titelseitenvorlage ein.
1. Tippen oder klicken Sie auf **Speichern** und anschließend auf **Fertig**, um das Dialogfeld zu schließen.
Bei Auswahl der Option **Fertig** wird ein Dialogfeld geöffnet, in dem Sie auswählen können, ob Sie die PDF-Ausgabedarstellung verwenden möchten.
   ![In PDF exportieren](assets/CatalogPDF.png)
Wenn die Option „Acrobat (PDF)“ ausgewählt ist, wird zusätzlich zur InDesign-Ausgabedarstellung eine PDF-Ausgabedarstellung in **/jcr:content/renditions** erstellt. Sie können alle Ausgabedarstellungen herunterladen, indem Sie das Kontrollkästchen „Ausgabedarstellungen“ im Dialogfeld „Herunterladen“ aktivieren.

1. Um eine Vorschau des erstellten Katalogs zu generieren, wählen Sie den Katalog in der Konsole **Katalog** aus und klicken Sie in der Symbolleiste auf das Symbol **Vorschau**.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Überprüfen Sie die Seiten in Ihrem Katalog in der Vorschau. Tippen oder klicken Sie auf **Schließen**, um die Vorschau zu schließen.
