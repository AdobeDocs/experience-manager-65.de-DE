---
title: Öffnen von XFA-basierten PDF-Formularen in Firefox und Chrome
description: Öffnen von XFA-basierten PDF-Formularen in Firefox und Chrome
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 31b52a82-5062-403e-bba7-e6a7e32ee961
source-git-commit: 913e249ba52f1ee262ed78167ce3b2a857e86213
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---

# Öffnen von XFA-basierten PDF-Formularen in Firefox und Chrome

## Problem

Der integrierte PDF-Viewer, der mit Mozilla Firefox und Google Chrome eingeführt wurde, unterstützt keine XFA-basierten PDF-Formulare. Daher werden XFA-basierte PDF-Formulare in späteren Versionen von Firefox und Chrome nicht geöffnet.

## Lösung

Um XFA-basierte PDF-Formulare unter Firefox und Chrome zu verwenden, führen Sie die folgenden Schritte aus, um Firefox und Chrome so zu konfigurieren, dass PDFs mit Adobe Reader oder Adobe Acrobat geöffnet werden.

>[!NOTE]
> 
> Stellen Sie sicher, dass Adobe Reader oder Adobe Acrobat auf Ihrem Computer installiert ist.

### Konfigurieren von Firefox

1. Wählen Sie in Firefox **Tools > Optionen**.

1. Klicken Sie im Dialogfeld „Optionen“ auf **Anwendungen**.

1. Geben Sie auf der Registerkarte „Anwendungen“ in das Suchfeld „PDF“ ein.

1. Wählen Sie für den Content-Typ „Portable Document Format (PDF)“ im Suchergebnis aus der Dropdown-Liste „Aktion“ die Option **Adobe Acrobat verwenden (in Firefox)**.
   ![use-adobe-acrobat](/help/forms/using/assets/use-adobe-acrobat.png)
1. Klicken Sie auf „OK“.

1. Starten Sie Firefox neu.

### Konfigurieren von Chrome

1. Navigieren Sie in Chrome zu chrome://plugins/ .

1. Klicken Sie unter „Chrome PDF Viewer“ auf „Deaktivieren“ und klicken Sie unter „Adobe PDF Plug-In“ auf „Aktivieren“.
   ![chrome-pdf-viewer](/help/forms/using/assets/chrome-image.png)
Weitere Informationen finden Sie in der Dokumentation zum [Adobe PDF-Plug-in](https://support.google.com/chrome/?hl=en&visit_id=638803785294106945-2276548125&rd=4&topic=3421431#topic=7439538) von Google.

>[!NOTE]
> 
> LiveCycle ES4 bietet Unterstützung für die Darstellung von XFA-basierten Formularen in HTML5, sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich solcher, die auf Mobilgeräten wie dem iPad laufen. Die HTML5-Ausgabedarstellung der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechnungen und Formularvalidierungen). Auf diese Weise werden Ihre Technologieinvestitionen in XFA-Formulare einfach auf Geräte übertragen, auf denen die Ausführung des Adobe Reader-Plug-ins nicht möglich ist.
> >Weitere Informationen finden Sie in der [LiveCycle-Produktdokumentation](https://business.adobe.com/products/experience-manager/forms/aem-forms.html).

[Rechtliche Hinweise](https://chl-author-preview.corp.adobe.com/content/help/de/legal/legal-notices.html)    |    [Online-Datenschutzrichtlinie](https://www.adobe.com/de/privacy.html)
