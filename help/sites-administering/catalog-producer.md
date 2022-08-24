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
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 39%

---

# Catalog Producer{#catalog-producer}

Erfahren Sie, wie Sie mit Catalog Producer in AEM Assets Produktkataloge mit Ihren digitalen Assets generieren.

Mit dem Catalog Producer von Adobe Experience Manager (AEM) Assets können Sie mit InDesign-Vorlagen, die Sie aus einer InDesign-Anwendung importieren, Kataloge für Ihre Markenprodukte erstellen. Um InDesign-Vorlagen zu importieren, integrieren Sie zunächst AEM Assets mit einem InDesign-Server.

## Integration mit einem InDesign-Server {#integrating-with-indesign-server}

Konfigurieren Sie im Rahmen des Integrationsprozesses die **DAM-Update-Asset** -Arbeitsablauf, der für die Integration mit InDesign geeignet ist. Konfigurieren Sie außerdem einen Proxy Worker für den InDesign-Server. Weitere Informationen finden Sie unter [Integrieren von AEM Assets mit InDesign Server](/help/assets/indesign.md).

>[!NOTE]
>
>Sie können aus InDesign-Dateien InDesign-Vorlagen erstellen, bevor Sie sie in AEM Assets importieren. Weitere Informationen finden Sie unter [Arbeiten mit Dateien und Vorlagen](https://helpx.adobe.com/indesign/using/files-templates.html).
>
>Sie können die Elemente in Ihren InDesign-Vorlagen XML-Tags zuordnen. Die zugeordneten Tags werden als Eigenschaften angezeigt, wenn Sie im Catalog Producer den Vorlageneigenschaften Produkteigenschaften zuordnen. Informationen zum XML-Tagging in InDesign-Dateien finden Sie unter [Tagging von Inhalten für XML](https://helpx.adobe.com/indesign/using/tagging-content-xml.html).

>[!NOTE]
>
>Nur InDesign-Dateien (.indd) werden als Vorlagen verwendet. Dateien mit der Erweiterung .indt werden nicht unterstützt.

## Erstellen eines Katalogs {#creating-a-catalog}

Der Catalog Producer verwendet Daten der Produktdatenverwaltung (PIM), um Produkteigenschaften den in der Vorlage angezeigten XML-Eigenschaften zuzuordnen. Um einen Katalog zu erstellen, führen Sie die folgenden Schritte durch:

1. Tippen/klicken Sie in der Assets-Benutzeroberfläche auf das Symbol **AEM** und navigieren Sie zu **Assets > Kataloge**.
1. Im **Kataloge** Seite, tippen/klicken **Erstellen** in der Symbolleiste und wählen Sie **Katalog** aus der Liste.
1. Im **Katalog erstellen** Seite, geben Sie einen Namen und eine Beschreibung (optional) für den Katalog ein und geben Sie ggf. Tags an. Außerdem können Sie ein Miniaturbild für den Katalog hinzufügen.

   ![create_catalog](assets/create_catalog.png)

1. Tippen oder klicken Sie auf **Speichern**. Ein Dialogfeld bestätigt, dass der Katalog erstellt wurde. Tippen/klicken **Fertig** , um das Dialogfeld zu schließen.
1. Um den erstellten Katalog zu öffnen, tippen/klicken Sie in der **Kataloge** Seite.

   >[!NOTE]
   >
   >Um den Katalog zu öffnen, können Sie auch auf **Öffnen** im Bestätigungsdialogfeld, das im vorherigen Schritt erwähnt wurde.

1. Um Seiten zum Katalog hinzuzufügen, tippen/klicken Sie auf **Erstellen** Wählen Sie in der Symbolleiste die **Neue Seite** -Option.
1. Wählen Sie im Assistenten eine InDesign-Vorlage für Ihre Seite aus. Tippen/klicken Sie dann auf **Nächste**.
1. Geben Sie einen Namen für die Seite sowie eine optionale Beschreibung an. Legen Sie ggf. Tags fest.
1. Tippen/klicken Sie auf **Erstellen** aus der Symbolleiste. Tippen/klicken Sie dann auf **Öffnen** aus dem Dialogfeld. Die Eigenschaften des Produkts werden im linken Fensterbereich angezeigt. Die vordefinierten Eigenschaften der InDesign-Vorlage werden im rechten Bereich angezeigt.
1. Ziehen Sie die Produkteigenschaften aus dem linken Bereich in die InDesign-Vorlageneigenschaften und erstellen Sie eine Zuordnung zwischen diesen Eigenschaften.

   Um anzuzeigen, wie die Seite in Echtzeit angezeigt wird, tippen/klicken Sie auf das **Vorschau** im rechten Bereich.

1. Wenn Sie weitere Seiten erstellen möchten, wiederholen Sie die Schritte 6–9. Um ähnliche Seiten für andere Produkte zu erstellen, wählen Sie die Seite aus und tippen/klicken Sie auf die **Erstellen ähnlicher Seiten** in der Symbolleiste.

   ![create_similar_pages](assets/create_similar_pages.png)

   >[!NOTE]
   >
   >Sie können nur ähnliche Seiten für Produkte mit ähnlicher Struktur erstellen.

   Tippen oder klicken Sie auf das Symbol zum Hinzufügen, wählen Sie die Produkte aus Produktauswahl und klicken Sie in der Symbolleiste auf **Auswählen**.

   ![select_product](assets/select_product.png)

1. Klicken/tippen Sie in der Symbolleiste auf **Erstellen**. Tippen/klicken **Fertig** , um das Dialogfeld zu schließen. Ähnliche Seiten sind in Ihrem Katalog enthalten.
1. Um eine vorhandene InDesign-Datei zum Katalog hinzuzufügen, tippen/klicken Sie auf **Erstellen** in der Symbolleiste und wählen Sie die **Hinzufügen zu vorhandener Seite** -Option.
1. Wählen Sie die InDesign-Datei aus und tippen/klicken Sie auf **Hinzufügen** aus der Symbolleiste. Tippen oder klicken Sie dann auf **OK**, um das Dialogfeld zu schließen.

   Wenn die Metadaten der Produkte, auf die Sie auf den Katalogseiten verweisen, geändert werden, werden die Änderungen nicht automatisch auf den Katalogseiten übernommen. Ein Banner mit der Bezeichnung **Statisch** wird auf den Produktbildern auf den referenzierenden Katalogseiten angezeigt und zeigt an, dass die Metadaten für die referenzierten Produkte nicht aktuell sind.

   ![chlimage_1-117](assets/chlimage_1-117a.png)

   Um sicherzustellen, dass die Produktbilder die neuesten Metadatenänderungen widerspiegeln, wählen Sie die Seite in der Katalogkonsole aus und klicken/tippen Sie auf die **Seite aktualisieren** in der Symbolleiste.

   ![chlimage_1-118](assets/chlimage_1-118a.png)

   >[!NOTE]
   >
   >Navigieren Sie zur Produktkonsole (**AEM** > **Handel** > **Produkte**) und wählen Sie das Produkt aus. Klicken/tippen Sie dann auf die **Eigenschaften anzeigen** in der Symbolleiste und bearbeiten Sie die Metadaten auf der Seite Eigenschaften des Assets.

1. Um die Seiten im Katalog neu anzuordnen, tippen/klicken Sie auf das **Erstellen** Symbol in der Symbolleiste und wählen Sie dann **Zusammenführen** aus dem Menü. Im Assistenten können Sie über das Karussell am oberen Bildschirmrand die Seiten durch Ziehen neu anordnen. Sie können Seiten auch entfernen.

1. Klicken oder tippen Sie auf **Weiter**. Um eine vorhandene InDesign-Datei als Titelseite hinzuzufügen, tippen/klicken Sie auf **Durchsuchen** neben dem **Titelseite auswählen** und geben Sie den Pfad für die Titelseitenvorlage an.
1. Tippen/klicken **Speichern** und tippen/klicken Sie dann auf **Fertig** , um das Bestätigungsdialogfeld zu schließen.
Bei Auswahl der **Fertig** -Option wird ein Dialogfeld geöffnet, in dem Sie auswählen können, ob Sie die PDF-Ausgabe verwenden möchten.
   ![Export in PDF](assets/CatalogPDF.png)
Wenn die Option Acrobat (PDF) ausgewählt ist, wird eine PDF-Ausgabe in erstellt  **/jcr:content/renditions** zusätzlich zur Indizierung der Ausgabedarstellung. Sie können alle Ausgabedarstellungen herunterladen, indem Sie das Kontrollkästchen &quot;Ausgabedarstellungen&quot;im Dialogfeld &quot;Download&quot;aktivieren.

1. Um eine Vorschau für den erstellten Katalog zu erzeugen, wählen Sie ihn im **Kataloge** und klicken Sie dann auf die **Vorschau** in der Symbolleiste.

   ![chlimage_1-119](assets/chlimage_1-119a.png)

   Überprüfen Sie die Seiten in Ihrem Katalog in der Vorschau. Tippen oder klicken Sie auf **Schließen**, um die Vorschau zu schließen.
