---
title: Dialogfeldeditor
seo-title: Dialog Editor
description: Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.
seo-description: The dialog editor provides a graphical interface for easily creating and editing dialog boxes and scaffolds
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
exl-id: 57303608-c3e1-4201-8054-1a1798613e2c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '491'
ht-degree: 100%

---

# Dialogfeldeditor{#dialog-editor}

Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.

Sehen Sie sich die Funktionsweise genauer an, indem Sie CRXDE Lite aufrufen, in der Explorer-Struktur zu `/libs/foundation/components/chart` navigieren und auf den Knoten `dialog` doppelklicken:

![chlimage_1-247](assets/chlimage_1-247.png)

Der Dialogknoten wird anschließend im **Dialogfeldeditor** geöffnet:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Benutzeroberfläche: Überblick {#user-interface-overview}

Die Oberfläche des Dialogfeldeditors besteht aus vier Bereichen:

* **Palette** links oben In diesem Bereich befinden sich die zum Erstellen eines Dialogfelds erforderlichen Widgets, etwa Registerkartenfelder, Textfelder, Auswahllisten und Schaltflächen. Sie können die verschiedenen Kategorien in der Palette maximieren, indem Sie auf die gewünschte Trennleiste klicken.
* **Struktur** links unten In diesem Bereich wird die hierarchische Struktur der Knoten angezeigt, aus der die Dialogfelddefinition besteht. Dieselbe Struktur können Sie sehen, wenn Sie den Dialogknoten in CRXDE Lite oder CRX Content Explorer maximieren.
* Der Fensterbereich **Rendern** befindet sich in der Mitte des Fensters. Darin ist zu sehen, wie die im Strukturfenster definierte Dialogfelddefinition als tatsächliches Dialogfeld gerendert wird.
* Der Fensterbereich **Eigenschaften**. In diesem Bereich werden die Eigenschaften des aktuell im Bereich „Struktur“ markierten Knotens angezeigt.

### Verwenden des Dialogfeldeditors {#using-the-dialog-editor}

Erstellen Sie ein Dialogfeld, indem Sie Elemente innerhalb der Dialogfeld-Definitionshierarchie aus der Palette in den Strukturbereich in Position ziehen.

Wenn Sie die gewünschte Struktur abgeschlossen haben, klicken Sie ganz oben im Bereich „Rendern“ auf **Speichern**.

>[!CAUTION]
>
>Beachten Sie, dass der Dialogfeldeditor für die Erstellung relativ einfacher Dialogfelder vorgesehen ist und Sie damit möglicherweise keine komplexen Dialogfelddefinitionen bearbeiten können. In Fällen, in denen der Editor die Bearbeitung einer Dialogfeldstruktur nicht zulässt, muss die Dialogfelddefinition manuell erstellt und/oder bearbeitet werden, indem die Knotenstruktur anhand von CRXDE Lite, CRX Content Explorer oder eines anderen Tools direkt bearbeitet wird.

### Erstellen eines neuen Dialogfelds {#creating-a-new-dialog}

Erstellen Sie ein neues Dialogfeld, indem Sie die erforderliche Komponente auswählen, auf **Erstellen...** klicken und anschließend **Dialogfeld erstellen...** auswählen.

Geben Sie die erforderlichen Informationen ein und klicken Sie auf **Alle speichern**. Nun können Sie doppelt auf das Dialogfeld klicken, um es im Editor zu öffnen.

### Verwenden des Dialogfeldeditors für Strukturvorlagen {#using-the-dialog-editor-for-scaffolds}

Eine Strukturvorlage ist eine spezielle Seite mit einem Formular, das in einem Schritt ausgefüllt und gesendet werden kann. Damit können Sie anhand der eingegebenen Inhalte sehr schnell eine Seite erstellen.

Das Formular, aus dem eine Strukturvorlage besteht, wird durch eine Dialogfelddefinition definiert, im Grunde wie ein normales Dialogfeld, mit dem Unterschied, dass es auf der Strukturvorlagenseite in einer anderen Form erscheint. Da Dialogfelddefinitionen zum Definieren von Strukturvorlagen verwendet werden, können Sie Strukturvorlagen mit dem Dialogfeldeditor entwerfen. Beachten Sie, dass bei dieser Art der Verwendung des Dialogeditors der Fensterbereich „Rendern“ die Dialogdefinition immer noch in Form eines Dialogfelds und nicht als Strukturvorlage anzeigt.

Weitere Informationen zum Erstellen von Strukturvorlagen mithilfe des Dialogfeldeditors finden Sie in [Strukturvorlagen](/help/sites-authoring/scaffolding.md).
