---
title: Dialogfeldeditor
description: Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 57303608-c3e1-4201-8054-1a1798613e2c
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 51%

---

# Dialogfeldeditor{#dialog-editor}

Der Dialogfeldeditor bietet eine grafische Oberfläche zur einfachen Erstellung und Bearbeitung von Dialogfeldern und Strukturvorlagen.

Um zu sehen, wie es funktioniert, gehen Sie zu CRXDE Lite, öffnen Sie den Explorer-Baum zu `/libs/foundation/components/chart` und durch Doppelklicken auf den Knoten `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

Der Dialogfeldknoten wird im **Dialog Editor**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Überblick über die Benutzeroberfläche {#user-interface-overview}

Die Benutzeroberfläche des Dialogfeldeditors besteht aus vier Bereichen:

* Die **Palette** in der linken oberen Ecke. Dieser Bereich enthält die Widgets, die zum Erstellen eines Dialogfelds verfügbar sind, z. B. Registerkarten-Bedienfelder, Textfelder, Auswahllisten und Schaltflächen. Sie können die verschiedenen Kategorien in der Palette erweitern, indem Sie auf die gewünschte Trennleiste klicken.
* Die **structure** in der linken unteren Ecke. In diesem Bereich wird die hierarchische Struktur der Knoten angezeigt, aus der die Dialogfelddefinition besteht. Dieselbe Struktur können Sie sehen, wenn Sie den Dialogfeldknoten in CRXDE Lite oder CRX Content Explorer maximieren.
* Der Fensterbereich **Rendern** befindet sich in der Mitte des Fensters. Dieser Bereich zeigt, wie die im Strukturbereich definierte Dialogfelddefinition als tatsächliches Dialogfeld dargestellt wird.
* Der Fensterbereich **Eigenschaften**. Dieser Bereich zeigt die Eigenschaften des Knotens, der im Strukturbereich hervorgehoben ist.

### Verwenden des Dialogfeldeditors {#using-the-dialog-editor}

Erstellen Sie ein Dialogfeld, indem Sie Elemente innerhalb der Dialogfeld-Definitionshierarchie aus der Palette in den Strukturbereich in Position ziehen.

Wenn Sie die gewünschte Struktur abgeschlossen haben, klicken Sie ganz oben im Bereich „Rendern“ auf **Speichern**.

>[!CAUTION]
>
>Der Dialogfeldeditor dient zum Erstellen einfacher Dialogfelder. Es ist möglicherweise nicht möglich, komplexere Dialogfelddefinitionen zu bearbeiten. In Fällen, in denen der Dialogfeldeditor die Bearbeitung einer Dialogfeldstruktur nicht zulässt, muss die Dialogfelddefinition manuell erstellt oder bearbeitet werden oder beides. Bearbeiten Sie dazu die Knotenstruktur beispielsweise direkt mit CRXDE Lite oder CRX Content Explorer.

### Erstellen eines neuen Dialogfelds {#creating-a-new-dialog}

Um ein Dialogfeld zu erstellen, wählen Sie die gewünschte Komponente aus und klicken Sie auf **Erstellen...** und dann **Dialogfeld erstellen...**.

Geben Sie die erforderlichen Details ein und klicken Sie auf **Alle speichern** - Jetzt können Sie auf das Dialogfeld doppelklicken, damit es mit dem Editor geöffnet wird.

### Verwenden des Dialogfeldeditors für Strukturvorlagen {#using-the-dialog-editor-for-scaffolds}

Eine Strukturvorlage ist eine spezielle Seite mit einem Formular, das in einem Schritt ausgefüllt und gesendet werden kann. Damit können Sie mithilfe der eingegebenen Inhalte sehr schnell eine Seite erstellen.

Das Formular, aus dem eine Strukturvorlage besteht, wird durch eine Dialogfelddefinition definiert, im Grunde wie ein normales Dialogfeld, mit dem Unterschied, dass es auf der Strukturvorlagenseite in einer anderen Form erscheint. Da Dialogfelddefinitionen zum Definieren von Strukturvorlagen verwendet werden, können Sie Strukturvorlagen mit dem Dialogfeldeditor entwerfen. Wenn Sie den Dialogfeldeditor auf diese Weise verwenden, zeigt der Renderbereich weiterhin die Dialogfelddefinition in Form eines Dialogfelds und nicht als Grundlage an.

Weitere Informationen zum Erstellen von Strukturvorlagen mithilfe des Dialogfeldeditors finden Sie in [Strukturvorlagen](/help/sites-authoring/scaffolding.md).
