---
title: Öffnen von XFA-basierten PDF forms in Firefox und Chrome
description: Öffnen von XFA-basierten PDF forms in Firefox und Chrome
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: ebb61f2c5056a780e829e64031f8eba69a8ae25b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 1%

---

# Öffnen von XFA-basierten PDF forms in Firefox und Chrome

## Problem

Der integrierte PDF-Viewer, der mit Mozilla Firefox und Google Chrome eingeführt wurde, unterstützt keine XFA-basierte PDF forms. Daher wird die XFA-basierte PDF forms nicht in späteren Versionen von Firefox und Chrome geöffnet.

## Lösung

Um die XFA-basierte PDF forms unter Firefox und Chrome zu verwenden, führen Sie die folgenden Schritte aus, um Firefox und Chrome so zu konfigurieren, dass PDFs mit Adobe Reader oder Adobe Acrobat geöffnet werden.

>[!NOTE]
> 
> Stellen Sie sicher, dass Adobe Reader oder Adobe Acrobat auf Ihrem Computer installiert ist.

### Firefox konfigurieren

1. Wählen Sie in Firefox &quot;**&quot; > „Optionen**.

1. Klicken Sie im Dialogfeld „Optionen“ auf **Anwendungen**.

1. Geben Sie auf der Registerkarte Anwendungen in das Suchfeld PDF ein.

1. Wählen Sie für den Content-Typ Portable Document Format (PDF) im Suchergebnis **Verwenden von Adobe Acrobat (in Firefox)** aus der Dropdown-Liste Aktion .
   ![use-adobe-acrobat](/help/forms/using/assets/use-adobe-acrobat.png)
1. Klicken Sie auf „OK“.

1. Starten Sie Firefox neu.

### Konfigurieren von Chrome

1. Navigieren Sie in Chrome zu chrome://plugins/ .

1. Klicken Sie unter Chrome PDF Viewer auf Deaktivieren und klicken Sie unter Adobe PDF Plug-In auf Aktivieren .
   ![chrome-pdf-viewer](/help/forms/using/assets/chrome-image.png)
Weitere Informationen finden Sie in der Dokumentation zum [Adobe PDF-Plug](https://support.google.com/chrome/?hl=en&amp;visit_id=638803785294106945-2276548125&amp;rd=4&amp;topic=3421431#topic=7439538)in von Google.

>[!NOTE]
> 
> LiveCycle ES4 unterstützt die Wiedergabe von XFA-basierten Formularen in HTML5, sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich solcher, die auf Mobilgeräten wie iPad ausgeführt werden. Die HTML5-Ausgabedarstellung der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechnungen und Formularvalidierungen). Auf diese Weise werden Ihre Technologieinvestitionen in XFA-Formulare einfach auf Geräte übertragen, auf denen die Ausführung des Adobe Reader-Plug-ins nicht möglich ist.
>Weitere Informationen finden Sie unter [LiveCycle-Produktdokumentation](https://business.adobe.com/products/experience-manager/forms/aem-forms.html).

[Rechtliche Hinweise](https://chl-author-preview.corp.adobe.com/content/help/en/legal/legal-notices.html)    |    [Online-Datenschutzrichtlinie](https://www.adobe.com/de/privacy.html)