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
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 43%

---

# Dialogfeldeditor{#dialog-editor}

Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.

Um zu sehen, wie es funktioniert, gehen Sie zu CRXDE Lite, öffnen Sie den Explorer-Baum zu `/libs/foundation/components/chart` und doppelklicken Sie auf den Knoten `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

Der Dialogknoten wird anschließend im **Dialogfeldeditor** geöffnet:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Übersicht über die Benutzeroberfläche {#user-interface-overview}

Die Benutzeroberfläche des Dialogfeldeditors besteht aus vier Bereichen:

* **Palette** links oben Dieser Bereich enthält die Widgets, die zum Erstellen eines Dialogfelds verfügbar sind, z. B. Registerkarten-Bedienfelder, Textfelder, Auswahllisten und Schaltflächen. Sie können die verschiedenen Kategorien in der Palette erweitern, indem Sie auf die gewünschte Trennleiste klicken.
* **Struktur** links unten Dieser Bereich zeigt die hierarchische Struktur von Knoten, aus denen die Dialogfelddefinition besteht. Dieselbe Struktur können Sie sehen, indem Sie den Dialogfeldknoten in CRXDE Lite oder CRX Content Explorer erweitern.
* Der Fensterbereich **Rendern** befindet sich in der Mitte des Fensters. Dieser Bereich zeigt, wie die im Strukturbereich definierte Dialogfelddefinition als tatsächliches Dialogfeld dargestellt wird.
* Der Fensterbereich **Eigenschaften**. Dieser Bereich zeigt die Eigenschaften des Knotens an, der derzeit im Strukturbereich hervorgehoben ist.

### Verwenden des Dialogfeldeditors {#using-the-dialog-editor}

Um ein Dialogfeld zu erstellen, zieht der Benutzer Elemente aus der Palette in den Strukturbereich und legt sie innerhalb der Dialogfelddefinitionshierarchie ab.

Sobald die gewünschte Struktur abgeschlossen ist, klickt der Benutzer auf **Speichern**, am oberen Rand des Renderbereichs.

>[!CAUTION]
>
>Beachten Sie, dass der Dialogfeldeditor für die Erstellung relativ einfache Dialogfelder vorgesehen ist und möglicherweise keine komplexeren Dialogfelddefinitionen bearbeiten kann. Wenn der Dialog-Editor die Bearbeitung einer Dialogfeldstruktur nicht zulässt, muss die Dialogfelddefinition manuell erstellt und/oder bearbeitet werden, indem die Knotenstruktur direkt bearbeitet wird, z. B. mit CRXDE Lite oder CRX Content Explorer.

### Erstellen eines neuen Dialogfelds {#creating-a-new-dialog}

Um ein neues Dialogfeld zu erstellen, müssen Sie die gewünschte Komponente auswählen. Klicken Sie auf **Erstellen...** und dann **Dialogfeld erstellen...**.

Geben Sie die erforderlichen Informationen ein und klicken Sie auf **Alle speichern**. Nun können Sie doppelt auf das Dialogfeld klicken, um es im Editor zu öffnen.

### Verwenden des Dialogfeldeditors für Strukturvorlagen {#using-the-dialog-editor-for-scaffolds}

Eine Strukturvorlage ist eine spezielle Seite mit einem Formular, das in einem Schritt ausgefüllt und gesendet werden kann. Auf diese Weise können Sie schnell eine Seite mit dem eingegebenen Inhalt erstellen.

Das Formular, aus dem eine Strukturvorlage besteht, wird durch eine Dialogfelddefinition definiert, im Grunde wie ein normales Dialogfeld, mit dem Unterschied, dass es auf der Strukturvorlagenseite in einer anderen Form erscheint. Da Dialogfelddefinitionen zum Definieren von Strukturvorlagen verwendet werden, können Sie Strukturvorlagen mit dem Dialogfeldeditor entwerfen. Beachten Sie, dass bei dieser Art der Verwendung des Dialogeditors der Fensterbereich „Rendern“ die Dialogdefinition immer noch in Form eines Dialogfelds und nicht als Strukturvorlage anzeigt.

Weitere Informationen zum Erstellen von Strukturvorlagen mithilfe des Dialogfeldeditors finden Sie in [Strukturvorlagen](/help/sites-authoring/scaffolding.md).
