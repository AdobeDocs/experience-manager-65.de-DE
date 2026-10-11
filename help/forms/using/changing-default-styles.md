---
title: Ändern von Standardstilen von HTML5-Formularen
description: Die Stile von HTML5-Formularen basieren auf CSS. Sie können die Standardstile des Formulars ändern.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 4c84cfd1-50a4-416f-b4a5-7f2f4c7f10af
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 99%
---
# Ändern von Standardstilen von HTML5-Formularen{#changing-default-styles-of-html-forms}

HTML5-Formulare werden mithilfe von HTML5-Funktionen gerendert. Der Stil des gerenderten Formulars wird mit CSS festgelegt. Das Standarderscheinungsbild von HTML5-Formularen ist der PDF-Darstellung ähnlich. Entwickelnde können benutzerdefinierte CSS verwenden, um das Standarderscheinungsbild von HTML5-Formularen zu ändern.

Dieser Artikel enthält Schritt-für-Schritt-Anleitungen, um den Stil eines HTML5-Formulars zu ändern, und der Artikel [Einführung in Stile](/help/forms/using/css-styles.md) enthält detaillierte Informationen zu den verschiedenen Gestaltungsaspekten von HTML5-Formularen. Stellen Sie sicher, dass Sie den Artikel „Einführung in Stile“ gelesen haben, bevor Sie die in diesem Artikel aufgeführten Schritte ausführen.

Die folgenden beiden Bilder zeigen den Unterschied zwischen Standard- und benutzerdefiniertem Stil.

![images-002-small](assets/pictures-002-small.png)

## Gestalten Sie Ihre Formulare {#style-your-forms}

1. **Wählen Sie ein Profil aus, um benutzerdefinierte Stile hinzufügen**

   Rufen Sie die CRX DE-Schnittstelle unter der URL **https://&lt;Server>:&lt;Port>/crx/de** auf und erstellen Sie ein Profil oder wählen Sie ein vorhandenes Profil. Wie Sie ein Profil erstellen, erfahren Sie hier: [Erstellen eines Profils](/help/forms/using/custom-profile.md).

1. **Erstellen Sie ein CSS-Stylesheet zum Gestalten der HTML5-Formulare**

   Navigieren Sie zu dem Ordner, in dem Sie den Profil-Renderer erstellt haben, und erstellen Sie eine CSS-Stylesheet-Datei. Die zu befolgenden Schritte:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner und wählen Sie **Erstellen**-> **Datei erstellen** im Menü aus.

   1. Geben Sie im Dateierstellungsdialog den Namen des Stylesheets ein. Achten Sie darauf, die Erweiterung „.css“ (z. B. stylesheet.css) zu verwenden.
   1. Öffnen Sie im Navigationsfeld die von Ihnen erstellte CSS-Datei.
   1. Definieren Sie die CSS-Klassen der Komponenten, die Sie gestalten wollen, und fügen Sie in diesen Klassen Stile hinzu.

   Welche CSS-Klassen für eine bestimmte Komponente in Ihrem HTML5-Formular zu erstellen sind, erfahren Sie in der [Einführung zu Stilen](/help/forms/using/css-styles.md).

1. **Schließen Sie das Stylesheet im Profil-Renderer ein**

   Öffnen Sie die Profil-Renderer-Seite (JSP-Datei) in CRX DE und schließen Sie die CSS-Datei auf der Seite direkt unter der XFA-Clientbibliothek ein. Führen Sie diese Schritte durch, um die css-Datei im Profil einzuschließen.

   1. Suchen Sie auf der Renderer-Seite nach der folgenden Zeile:

      &lt;cq:includeClientLib categories=„xfaforms.profile“ />

   1. Fügen Sie Folgendes unter der darüberstehenden Zeile ein, um das Stylesheet einzuschließen:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Speichern Sie die Datei.
