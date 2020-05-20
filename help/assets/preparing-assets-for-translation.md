---
title: Vorbereiten von Assets für die Übersetzung
description: Erstellen Sie sprachliche Stammordner, um Assets für die Übersetzung vorzubereiten und damit mehrsprachige Assets zu unterstützen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 66%

---


# Vorbereiten von Assets für die Übersetzung {#preparing-assets-for-translation}

Bei mehrsprachigen Assets handelt es sich um Assets mit Binärdateien, Metadaten und Tags in verschiedenen Sprachen. Im Allgemeinen liegen Binärdateien, Metadaten und Tags für Assets in einer Sprache vor, die dann für die Verwendung in mehrsprachigen Projekten in andere Sprachen übersetzt wird.

In Adobe Experience Manager (AEM) Assets sind mehrsprachige Assets in Ordnern enthalten, wobei jeder Ordner die Assets in einer anderen Sprache enthält.

Jeder Sprachordner wird als eine Sprachkopie bezeichnet. Der Stammordner einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. For example, */content/dam/it* is the Italian language root for the Italian language copy. Sprachkopien müssen einen [korrekt konfigurierten Sprachstamm](preparing-assets-for-translation.md#creating-a-language-root) verwenden, damit die korrekte Sprache angesprochen wird, wenn Übersetzungen von Quell-Assets durchgeführt werden.

Die Sprachkopie, für die Sie ursprünglich Assets hinzufügen, ist die Sprach-Master-Vorlage. Die Sprach-Master-Vorlage ist die Quelle, die in andere Sprachen übersetzt wird. Eine Beispielordnerhierarchie enthält mehrere Sprachstämme:

```
 /content
  /- dam
   |- en
   |- fr
   |- de
   |- es
   |- it
   |- ja
   |- zh
```

Führen Sie die folgenden Schritte aus, um Ihre Assets für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Beispielsweise lautet der Sprachstamm der englischen Sprachkopie in der Beispielordnerhierarchie `/content/dam/en`. Ensure that the language root is correctly configured according to the information in [Create a Language Root](preparing-assets-for-translation.md#creating-a-language-root).

1. Fügen Sie Assets zu Ihrer Sprach-Master-Vorlage hinzu.
1. Erstellen Sie den Sprachstamm der jeweiligen Zielsprache, für die Sie eine Sprachkopie benötigen.

## Create a language root {#creating-a-language-root}

Um den Sprachstamm zu erstellen, erstellen Sie einen Ordner und verwenden Sie einen ISO-Sprachcode als Wert für die Name-Eigenschaft. Nachdem Sie den Sprachstamm erstellt haben, können Sie eine Sprachkopie auf jeder beliebigen Ebene im Sprachstamm erstellen.

Beispielsweise verfügt die Stammseite der italienischsprachigen Kopie der Beispielhierarchie über `it` als Eigenschaft „Name“. The Name property is used as the name of the asset node in the repository, and therefore determines the path of the assets. (`https://[aem_server]:[port]/assets.html/content/dam/it/`).

1. From the Assets console, click **[!UICONTROL Create]** and choose **[!UICONTROL Folder]** from the menu.

   ![Ordner erstellen](assets/Create-folder.png)

1. In the **[!UICONTROL Name]** field type the country code in the format of `<language-code>`.

   ![Hinzufügen Sprachencode im Ordner](assets/Add-language-code-in-folder.png)

1. Klicken Sie auf **[!UICONTROL Erstellen]**. Der Sprachstamm wird in der Konsole „Assets“ erstellt. 

## Anzeigen von Sprachstämmen {#viewing-language-roots}

AEM interface provides a **[!UICONTROL References]** panel that displays a list of language roots that have been created within AEM Assets.

1. In der Konsole „Assets“ wählen Sie die Sprach-Master-Vorlage aus, für die Sie Sprachkopien erstellen möchten.
1. Click the GlobalNav icon, and choose **[!UICONTROL References]** to open the [!UICONTROL Reference] pane.

   ![chlimage_1-122](assets/chlimage_1-122.png)

1. In the References pane, click **[!UICONTROL Language Copies]**. The [!UICONTROL Language Copies] panel shows the language copies of the assets.

   ![chlimage_1-123](assets/chlimage_1-123.png)
