---
title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bedienfelds eines adaptiven Formulars extrahieren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms
exl-id: 6a158e18-b7d0-45fb-b4fc-4770e66982b4
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 61%

---

# Verwenden von SOM-Ausdrücken in adaptiven Formularen{#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM Seite modelliert, die in AEM Repository als JCR-Inhaltsstruktur dargestellt wird. Das Schlüsselelement der Inhaltsstruktur ist der Knoten guideContainer . Unter &quot;guideContainer&quot;befindet sich &quot;rootPanel&quot;, das verschachtelte Bedienfelder und Felder enthalten kann.

Sie können ein Skriptobjektmodell (SOM) verwenden, um Werte, Eigenschaften und Methoden innerhalb eines bestimmten Dokumentobjektmodells (DOM) zu referenzieren. Ein DOM organisiert die Speicherobjekte und -eigenschaften in einer Baumstruktur. Ein SOM-Ausdruck verweist auf Felder/Zeichenelemente und Bereiche.

Die folgende Abbildung zeigt eine Knotenstruktur, in die ein adaptives Formular umgesetzt wird, wenn Sie einem Formular Komponenten hinzufügen. Sie können beispielsweise dem Stammbereich einen Bereich und diesem dann ein Optionsfeld hinzufügen. Der Bereich wird dann zur Laufzeit in ein DOM transformiert. Der SOM-Ausdruck für das Optionsfeld im adaptiven Formular wird als `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]` angegeben.

![DOM-Baumstruktur](assets/hierarchy.png)

DOM-Baumstruktur

Einem SOM-Ausdruck für ein beliebiges Element in einem adaptiven Formular wird das Präfix `guide[0].guide1[0]` vorangestellt. Die Position einer Komponente in der hierarchischen Knotenstruktur wird zum Ableiten des entsprechenden SOM-Ausdrucks verwendet.

![DOM-Baumstruktur mit zwei Optionsfeldern](assets/hierarchy_radio_button.png)

DOM-Baumstruktur mit zwei Optionsfeldern

Der SOM-Ausdruck ändert sich, wenn Sie die Position der Optionsfelder im adaptiven Formular ändern. Im Authoring-Modus können Sie den SOM-Ausdruck eines Felds oder Elements in AEM Forms mithilfe der Option SOM-Ausdruck anzeigen anzeigen. Die Option wird auf dem Bereich angezeigt und wenn Sie mit der rechten Maustaste auf das Feld oder Element klicken.

![Extrahieren von SOM-Ausdrücken in einem adaptiven Formular](assets/som-expressions.png)

Extrahieren von SOM-Ausdrücken in einem adaptiven Formular

Innerhalb von Bereichen können Sie von der Bereichssymbolleiste aus auf die Funktion zugreifen. Die Funktion vereinfacht die Skripterstellung durch Autoren adaptiver Formulare.

![Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste](assets/som-expression.png)

Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste

Einige in [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html) aufgeführte APIs verwenden den SOM-Ausdruck eines Elements. Um beispielsweise ein bestimmtes Feld in einem adaptiven Formular hervorzuheben, muss der entsprechende SOM-Ausdruck an die `getFocus`-API in `guideBridge` übergeben werden.
