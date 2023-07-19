---
title: Ändern von Standardstilen von HTML5-Formularen
seo-title: Changing default styles of HTML5 forms
description: HTML5-Formularstile basieren auf CSS. Sie können die Standardstile des Formulars ändern.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: 5e23237d-42d8-4d29-b79e-4dc276ef65ff
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 582b0fe8-a92b-4a1d-b859-57f13f53d0d8
docset: aem65
feature: Mobile Forms
exl-id: 4c84cfd1-50a4-416f-b4a5-7f2f4c7f10af
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 54%

---

# Ändern von Standardstilen von HTML5-Formularen{#changing-default-styles-of-html-forms}

HTML5-Formulare werden mithilfe von HTML5-Funktionen gerendert. Der Stil des gerenderten Formulars wird mit CSS festgelegt. Das Standarderscheinungsbild von HTML5-Formularen ist der PDF-Darstellung ähnlich. Entwickler können benutzerdefinierte CSS verwenden, um das standardmäßige Erscheinungsbild von HTML5-Formularen zu ändern.

Dieser Artikel enthält Schritt-für-Schritt-Anleitungen, um den Stil eines HTML5-Formulars zu ändern, und der Artikel [Einführung in Stile](/help/forms/using/css-styles.md) enthält detaillierte Informationen zu den verschiedenen Gestaltungsaspekten von HTML5-Formularen. Stellen Sie sicher, dass Sie den Artikel „Einführung in Stile“ gelesen haben, bevor Sie die in diesem Artikel aufgeführten Schritte ausführen.

Die folgenden beiden Bilder zeigen den Unterschied zwischen Standard- und benutzerdefiniertem Stil.

![images-002-small](assets/pictures-002-small.png)

## Gestalten Sie Ihre Formulare {#style-your-forms}

1. **Wählen Sie ein Profil aus, um benutzerdefinierte Stile hinzuzufügen**

   Rufen Sie die CRX DE-Schnittstelle unter der URL **https://&lt;Server>:&lt;Port>/crx/de** auf und erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil. Wie Sie ein Profil erstellen, erfahren Sie hier: [Erstellen eines neuen Profils](/help/forms/using/custom-profile.md).

1. **Erstellen Sie ein CSS-Stylesheet für die Formatierung der HTML5-Formulare**

   Navigieren Sie zu dem Ordner, in dem Sie den Profil-Renderer erstellt haben, und erstellen Sie eine CSS-Stylesheet-Datei. Die folgenden Schritte sind erforderlich:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie **erstellen** > **Datei erstellen** aus dem Menü

   1. Geben Sie im Dialogfeld &quot;Datei erstellen&quot;den Namen des Stylesheets ein. Stellen Sie sicher, dass Sie die Erweiterung .css (z. B. stylesheet.css) verwenden.
   1. Öffnen Sie im Navigationsfeld die von Ihnen erstellte CSS-Datei.
   1. Definieren Sie die CSS-Klassen der Komponenten, die Sie gestalten wollen, und fügen Sie in diesen Klassen Stile hinzu.

   Informationen darüber, welche CSS-Klassen für eine bestimmte Komponente in Ihren HTML5-Formularen erstellt werden sollen, finden Sie unter [Einführung in Stile](/help/forms/using/css-styles.md).

1. **Einschließen des Stylesheets in den Profil-Renderer**

   Öffnen Sie die Profil-Renderer-Seite (JSP-Datei) in CRX DE und fügen Sie die CSS-Datei in die Seite direkt unter der XFA-Client-Bibliothek ein. Führen Sie diese Schritte aus, um die CSS-Datei in das Profil einzuschließen.

   1. Suchen Sie auf der Renderer-Seite nach der folgenden Zeile:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Fügen Sie Folgendes unter der darüberstehenden Zeile ein, um das Stylesheet einzuschließen:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Speichern Sie die Datei.
