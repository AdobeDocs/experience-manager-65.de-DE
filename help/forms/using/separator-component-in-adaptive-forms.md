---
title: Trennzeichenkomponenten in adaptiven Formularen
seo-title: Trennzeichenkomponenten in adaptiven Formularen
description: Sie können die Trennzeichenkomponente verwenden, um Abschnitte eines Formulars visuell zu trennen.
seo-description: Sie können die Trennzeichenkomponente verwenden, um Abschnitte eines Formulars visuell zu trennen.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: a8aa77fe-5880-4c4e-9e1b-3c5a8772c29d
docset: aem65
translation-type: tm+mt
source-git-commit: 5a76200a573d95026e2347d2049a089d975b5619

---


# Trennzeichenkomponenten in adaptiven Formularen{#separator-component-in-adaptive-forms}

Sie können die Trennzeichenkomponente verwenden, um Bereiche eines Formulars visuell zu trennen. Sie können die Gesamtdarstellung und den Stil einer Trennzeichenkomponente definieren, indem Sie die folgenden Eigenschaften einer Trennzeichenkomponente angeben:

* **Elementname:** Gibt den Namen der Komponente an. Die SOM-Ausdrücke richten sich an die Komponenten mit dem Wert, der im Feld „Elementname“ angegeben ist.
* **** Dicke: Gibt die Stärke der Trennzeichenkomponente in Pixel an.

* **CSS-Klasse:** Gibt die benutzerdefinierte CSS-Klasse für die Trennzeichenkomponente an

* **Inline-Stile:** Mit AEM Forms können Sie jetzt CSS-Inline-Stile auf individuelle adaptive Formularkomponenten anwenden und eine Vorschau der Änderungen in Echtzeit anzeigen.

Im Layoutmodus können Sie die Anzahl der Spalten festlegen, die die Trennzeichenkomponente umfasst. Weitere Informationen finden Sie unter [Verwenden des Layoutmodus zum Ändern der Größe von Komponenten](../../forms/using/resize-using-layout-mode.md).

Angeben der Eigenschaften einer Trennzeichenkomponente:

1. Select a separator component and tap ![cmppr](assets/cmppr.png). Die Eigenschaften werden in der Seitenleiste angezeigt.
1. Klicken Sie auf eine Registerkarte im Abschnitt „Inline-CSS-Eigenschaften“, um CSS-Eigenschaften festzulegen. Beispiel: Klicken Sie auf der Registerkarte „Feld“ auf **Element hinzufügen**. Es wird eine Zeile mit zwei Feldern hinzugefügt.
1. Geben Sie im ersten Feld von links eine CSS3-Eigenschaft an, die Sie anwenden möchten. Beispielsweise **Rahmen**. Sie können eine Eigenschaft auch auswählen, indem Sie auf den Pfeil nach unten klicken. Die Dropdownliste ist nicht vollständig und Sie können einen beliebigen unterstützten CSS3-Eigenschaftennamen in dieses Feld eingeben.
1. Geben Sie im angrenzenden Feld einen gültigen Wert für die angegebene CSS3-Eigenschaft an. Beispielsweise **3px solid black**.
1. Klicken Sie auf **Element hinzufügen**, um eine andere Eigenschaft und deren Wert anzugeben.
1. Klicken Sie auf **Vorschau**, um eine Vorschau der Änderungen im Formular anzuzeigen.
1. Klicken Sie auf **OK**, um die Änderungen zu bestätigen oder auf **Abbrechen**, um das Dialogfeld ohne Änderungen zu schließen.

