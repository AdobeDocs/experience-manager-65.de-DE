---
title: Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister
description: Formularentwicklerinnen und -entwickler können der Liste der Formulare auf der Formularportalseite weitere Aktionen hinzufügen. Standardmäßig können Sie über die Formularliste auf das Formular zugreifen, es ausfüllen und abschicken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 7c2a91c8-9b68-4491-88e2-f7ea68f5a79f
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 7da902b6-fe94-5180-8e7c-f6d1e38d01d5
    internal-label: Foundation Components
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 100%
---
# Hinzufügen benutzerdefinierter Aktionen zu Elementen im Formularauflister{#adding-custom-action-on-form-lister-items}

In AEM Forms können Sie eine Portalseite erstellen, in der die verfügbaren Formulare aufgelistet werden. Standardmäßig können Sie Formulare auf einer Portalseite suchen und auflisten. Sie können Formulare zum Ausfüllen öffnen und Ihre Angaben übermitteln. Bei Formularen, die auf einer Portalseite gelistet sind, stehen für den sofortigen Einsatz nur Render-Aktionen zur Verfügung. Weitere Informationen über die verfügbaren Aktionen auf einer Portalseite finden Sie unter [Erstellen einer Forms Portal-Seite](../../forms/using/creating-form-portal-page.md).

Sie können der Portalseite weitere Optionen hinzufügen. Diese Optionen bzw. Aktionen können angepasst werden, indem die Formularportal-Vorlage angepasst wird.

In diesem Artikel wird beschrieben, wie Sie eine Schaltfläche erstellen, um den Link eines Formulars direkt von einer Formularportalseite zu senden. Diese Anpassung erfordert eine Aktualisierung der Vorlage für die Komponente „Suche und Auflister“.

Der erforderliche Code zum Hinzufügen der Aktion zur Vorlage ist unten zu finden. Das `onclick`-Attribut im Codebeispiel enthält ein Skript, um die Verknüpfung eines Formulars per E-Mail zu senden.

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
