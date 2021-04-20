---
title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
seo-title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bereichs eines adaptiven Formulars extrahieren.
seo-description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bereichs eines adaptiven Formulars extrahieren.
uuid: c5d55aff-fb69-4a1c-96ea-fb3f9322cbb0
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 13f00bb2-561f-4d64-8829-292c663abeab
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 91%

---


# Verwenden von SOM-Ausdrücken in adaptiven Formularen{#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM-Seite modelliert, die als JCR-Inhaltstruktur im AEM-Repository repräsentiert wird. Das Schlüsselelement der Inhaltstruktur ist der Knoten „guideContainer“. Unter „guideContainer“ befindet sich der Knoten „rootPanel“, der verschachtelte Bereiche und Felder enthalten kann.

Sie können ein Scripting Object Model (SOM) zum Referenzieren von Werten, Eigenschaften und Methoden innerhalb eines bestimmten Document Object Model (DOM) verwenden. Ein DOM organisiert die Speicherobjekte und -eigenschaften in einer hierarchischen Baumstruktur. Ein SOM-Ausdruck referenziert Felder/Zeichenelemente und Bereiche.

Die folgende Abbildung zeigt eine Knotenstruktur, in die ein adaptives Formular übersetzt wird, wenn Sie einem Formular Komponenten hinzufügen. Sie können beispielsweise dem Stammbereich einen Bereich und dann in dem Bereich ein Optionsfeld hinzufügen. Der Bereich wird dann zur Laufzeit in ein DOM transformiert. Der SOM-Ausdruck für das Optionsfeld im adaptiven Formular wird als `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]` angegeben.

![DOM-Baumstruktur](assets/hierarchy.png)

DOM-Baumstruktur

Einem SOM-Ausdruck für ein beliebiges Element in einem adaptiven Formular wird das Präfix `guide[0].guide1[0]` ] vorangestellt. Die Position einer Komponente in der hierarchischen Knotenstruktur wird zum Ableiten ihres SOM-Ausdrucks verwendet.

![DOM-Baumstruktur mit zwei Optionsfeldern](assets/hierarchy_radio_button.png)

DOM-Baumstruktur mit zwei Optionsfeldern

Der SOM-Ausdruck ändert sich, wenn Sie die Position der Optionsfelder im adaptiven Formular ändern. Im Bearbeitungsmodus können Sie den SOM-Ausdruck eines Felds oder Elements in AEM Forms mithilfe der Option „SOM-Ausdruck anzeigen“ anzeigen. Die Option wird auf dem Bereich, und wenn Sie mit der rechten Maustaste auf das Feld oder Element klicken, angezeigt.

![Extrahieren von SOM-Ausdrücken in einem adaptiven Formular](assets/som-expressions.png)

Extrahieren von SOM-Ausdrücken in einem adaptiven Formular

Innerhalb von Bereichen können Sie von der Bereichssymbolleiste aus auf die Funktion zugreifen. Die Funktion vereinfacht die Skripterstellung durch Autoren adaptiver Formulare.

![Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste](assets/som-expression.png)

Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste

Einige in [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html) aufgeführten APIs verwenden den SOM-Ausdruck eines Elements. Um beispielsweise ein bestimmtes Feld in einem adaptiven Formular hervorzuheben, muss der entsprechende SOM-Ausdruck an die `getFocus`-API in `guideBridge` übergeben werden.
