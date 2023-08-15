---
title: Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister
seo-title: Adding custom action on form lister items
description: Formularentwickler können der Liste der Formulare auf der Forms Portal-Seite weitere Aktionen hinzufügen. Standardmäßig können Sie über die Formularauflistung auf das Formular zugreifen, es ausfüllen und es senden.
seo-description: Form developers can add more actions to the listing of forms on the forms portal page. By default, the form listing lets you access the form, fill it, and submit it.
uuid: 5703ba27-7fb8-482e-b933-a060574165dc
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: c34dd4c2-5fff-4355-b86d-cc8a956dd8af
docset: aem65
exl-id: 7c2a91c8-9b68-4491-88e2-f7ea68f5a79f
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 43%

---

# Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister{#adding-custom-action-on-form-lister-items}

In AEM Forms können Sie eine Portalseite erstellen, in der die verfügbaren Formulare aufgelistet werden. Standardmäßig können Sie Formulare auf einer Portalseite suchen und auflisten. Sie können Formulare zum Ausfüllen und Senden Ihrer Informationen öffnen. Bei Formularen, die auf einer Portalseite gelistet sind, stehen für den sofortigen Einsatz nur Render-Aktionen zur Verfügung. Weitere Informationen über die verfügbaren Aktionen auf einer Portalseite finden Sie unter [Erstellen einer Forms Portal-Seite](../../forms/using/creating-form-portal-page.md).

Sie können der Portalseite weitere Optionen hinzufügen. Diese Optionen oder Aktionen können durch Anpassen der Formularportalvorlage angepasst werden.

In diesem Artikel wird beschrieben, wie Sie eine Schaltfläche erstellen, um den Link eines Formulars direkt von einer Forms Portal-Seite zu senden. Für diese Anpassung muss die Vorlage für die Komponente &quot;Search &amp; Lister&quot;aktualisiert werden.

Der erforderliche Code zum Hinzufügen der Aktion zur Vorlage ist unten verfügbar. Das `onclick`-Attribut im Codebeispiel enthält ein Skript, um die Verknüpfung eines Formulars per E-Mail zu senden.

```html
<div class="__FP_boxes-container __FP_single-color">
    <div class="boxes __FP_boxes __FP_single-color" data-repeatable="true">
  <div class="__FP_boxes-thumbnail">
            <img src ="${contextPath}${path}/jcr:content/renditions/cq5dam.thumbnail.319.319.png">
        </div>
        <h3 class="__FP_single-color" title="${name}" tabindex="0">${name}</h3>
        <p>${description}</p>
        <div class="boxes-icon-cont __FP_boxes-icon-cont">
            <div class="op-dow">
                <a href="${formUrl}" target="_blank" class="__FP_button ${htmlStyle}" title="${config-htmlLinkText}">Apply</a>
                <a class="__FP_button" title="Email a friend" href="#" onclick="javascript:window.location=&apos;mailto:?subject=Interesting information&body=I thought you might find {name} form helpful :  &apos;+window.location.protocol+window.location.host+&apos;${formUrl}&apos; ;">Email</a>
                <a href="${pdfUrl}" class="__FP_button ${pdfStyle}" title="${config-pdfLinkText}">Download</a>
            </div>
        </div>
    </div>
</div>
```

Sie können ähnliche Aktionen in Ihrer benutzerdefinierten Vorlage hinzufügen. Um eine JavaScript-Funktion zu definieren, fügen Sie die Funktion in einem Skript auf Seitenebene hinzu und verknüpfen Sie sie mit dem erforderlichen HTML-Element. Im Beispiel oben ist der `onclick`-Ausdruck die verknüpfte Funktion.

Nachdem Sie die Änderungen an der Vorlage vorgenommen haben, enthält die Portal-Beispielseite, wie nachfolgend in der Abbildung dargestellt, eine Schaltfläche, um die Verknüpfung des Formulars per E-Mail zu senden.

![email](assets/email.png)
