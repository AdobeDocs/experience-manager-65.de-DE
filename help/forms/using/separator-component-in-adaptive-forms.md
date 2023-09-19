---
title: Trennzeichenkomponente in adaptiven Formularen
description: Sie können die Trennzeichenkomponente verwenden, um Abschnitte eines Formulars visuell zu trennen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms
exl-id: 11cbf865-c8e2-4833-b0b8-a3cb5e42f5cd
source-git-commit: 99808cb38c5d376ccb7fb550c5212138890cec11
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 37%

---

# Trennzeichenkomponenten in adaptiven Formularen{#separator-component-in-adaptive-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird ein älterer Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

Sie können die Trennzeichenkomponente verwenden, um Bereiche eines Formulars visuell zu trennen. Sie können die Gesamtdarstellung und den Stil einer Trennzeichenkomponente definieren, indem Sie die folgenden Eigenschaften der Trennzeichenkomponente angeben:

* **Elementname:** Gibt den Namen der Komponente an. Die SOM-Ausdrücke adressieren die Komponente mit einem Wert, der im Feld &quot;Elementname&quot;angegeben ist.
* **Stärke:** Gibt die Stärke der Trennzeichenkomponente in Pixel an.

* **CSS-Klasse:** Gibt die benutzerdefinierte CSS-Klasse für die Trennzeichenkomponente an.

* **Inline-Stile:** Mit AEM Forms können Sie jetzt CSS-Inline-Stile auf individuelle adaptive Formularkomponenten anwenden und eine Vorschau der Änderungen in Echtzeit anzeigen.

Im Layout-Modus können Sie die Anzahl der Spalten festlegen, die die Trennzeichenkomponente umfasst. Weitere Informationen finden Sie unter [Verwenden des Layout-Modus, um die Größe von Komponenten anzupassen](../../forms/using/resize-using-layout-mode.md).

So legen Sie die Eigenschaften einer Trennzeichenkomponente fest:

1. Wählen Sie eine Trennzeichenkomponente aus und tippen Sie auf ![cmppr](assets/cmppr.png). Die Eigenschaften werden in der Seitenleiste geöffnet.
1. Klicken Sie auf eine Registerkarte im Abschnitt Inline-CSS-Eigenschaften , damit Sie CSS-Eigenschaften angeben können. Beispiel: a. Klicken Sie auf der Registerkarte Feld auf **Element hinzufügen**. Eine Zeile mit zwei Feldern wird hinzugefügt.
1. Geben Sie im ersten Feld links eine CSS3-Eigenschaft an, die Sie anwenden möchten. Beispiel: **border**. Sie können auch eine Eigenschaft auswählen, indem Sie auf die Nach-unten-Taste klicken. Die Dropdown-Liste ist nicht vollständig und Sie können einen beliebigen unterstützten CSS3-Eigenschaftennamen in dieses Feld eingeben.
1. Geben Sie im angrenzenden Feld einen gültigen Wert für die angegebene CSS3-Eigenschaft an. Beispiel: **3-px-Vollschwarz**.
1. Klicken Sie auf **Element hinzufügen**, um eine andere Eigenschaft und deren Wert anzugeben.
1. Klicks **Vorschau** sodass Sie eine Vorschau der Änderungen im Formular anzeigen können.
1. Klicks **OK** wenn Sie die Änderungen bestätigen möchten oder **Abbrechen** , um das Dialogfeld ohne Änderungen zu schließen.
