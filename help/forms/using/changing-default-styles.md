---
title: Ändern von Standardstilen von HTML5-Formularen
seo-title: Ändern von Standardstilen von HTML5-Formularen
description: Der Stil von HTML5-Formularen basiert auf CSS. Sie können die Standardstile des Formulars ändern.
seo-description: Der Stil von HTML5-Formularen basiert auf CSS. Sie können die Standardstile des Formulars ändern.
uuid: 5e23237d-42d8-4d29-b79e-4dc276ef65ff
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 582b0fe8-a92b-4a1d-b859-57f13f53d0d8
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Ändern von Standardstilen von HTML5-Formularen{#changing-default-styles-of-html-forms}

HTML5-Formulare werden mithilfe von HTML5-Funktionen gerendert. Der Stil des gerenderten Formulars wird mit CSS festgelegt. Das Standarderscheinungsbild von HTML5-Formularen ist der PDF-Darstellung ähnlich. Entwickler können benutzerdefinierte CSS verwenden, um das Standarderscheinungsbild von HTML5-Formularen zu ändern.

This article provides step-by-step information to change style of an HTML5 form and [Introduction to Styles](/help/forms/using/css-styles.md) article contains detailed information about various styling aspects of HTML5 forms. Lesen Sie den Artikel &quot;Einführung zu Stilen&quot;, bevor Sie die in diesem Artikel genannten Schritte durchführen.

Die folgenden beiden Bilder zeigen den Unterschied zwischen Standard- und benutzerdefiniertem Stil.

![images-002-small](assets/pictures-002-small.png)

## Gestalten Sie Ihre Formulare {#style-your-forms}

1. **Wählen Sie ein Profil, um benutzerdefinierte Stile hinzufügen**

   Access the CRX DE interface at the URL: **https://&lt;server>:&lt;port>/crx/de** and create a profile or choose an existing profile. To know how to create a profile, see [Creating a new Profile](/help/forms/using/custom-profile.md)

1. **Erstellen Sie ein CSS-Stylesheet zum Gestalten der HTML5-Formulare**

   Navigieren Sie zu dem Ordner, in dem Sie den Profil-Renderer erstellt haben, und erstellen Sie eine CSS-Stylesheet-Datei. Die zu befolgenden Schritte:

   1. Right click the folder and select **create** > **create File** from the menu

   1. Geben Sie im Dateierstellungsdialog den Namen des Stylesheets ein. Achten Sife darauf, die Erweiterung .css (z. B. stylesheet.css) zu verwenden.
   1. Öffnen Sie im Navigationsbereich die von Ihnen erstellte CSS-Datei.
   1. Definieren Sie die CSS-Klassen der Komponenten, die Sie gestalten wollen, und fügen Sie in diesen Klassen Stile hinzu.
   Welche CSS-Klassen für eine bestimmte Komponente in Ihrem HTML5-Formular zu erstellen sind, erfahren Sie unter [Einführung zu Stilen](/help/forms/using/css-styles.md).

1. **Schließen Sie das Stylesheet im Profil-Renderer ein.**

   Öffnen Sie die Profil-Renderer-Seite (JSP-Datei) in CRX DE und schließen Sie die CSS-Datei auf der Seite direkt unter der XFA-Clientbibliothek ein. Führen Sie diese Schritte durch, um die css-Datei im Profil einzuschließen.

   1. Suchen Sie auf der Renderer-Seite nach der folgenden Zeile:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Fügen Sie Folgendes unter der darüberstehenden Zeile ein, um das Stylesheet einzuschließen:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Speichern Sie die Datei .
