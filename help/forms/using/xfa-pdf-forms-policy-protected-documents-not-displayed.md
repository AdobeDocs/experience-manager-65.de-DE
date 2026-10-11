---
title: Anzeigen von Problemen für XFA-basierte PDF-Formulare und richtliniengeschützte Dokumente
description: Anzeigen von Problemen für XFA-basierte PDF-Formulare und richtliniengeschützte Dokumente
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: c9beefac-14e9-466c-b5bd-44ffab1fb820
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 100%
---
# Anzeigen von Problemen für XFA-basierte PDF-Formulare und richtliniengeschützte Dokumente

Überprüfen Sie, ob es an einem der folgenden Gründe liegt, wenn Sie ein XFA-basiertes PDF-Formular oder ein richtliniengeschütztes Dokument nicht mit Adobe LiveCycle Rights Management öffnen können:

* XFA-basierte PDF-Formulare und richtliniengeschützte Dokumente erfordern Adobe® Acrobat® oder Adobe® Reader®, Version 8 und höher. Unter [Adobe-Downloads](https://www.adobe.com/downloads.html) finden Sie Informationen zum Herunterladen der neuesten Reader oder Acrobat.
* Browser wie Mozilla Firefox und Google Chrome bieten einen integrierten PDF-Viewer, der XFA-basierte PDF-Formulare nicht unterstützt. Um XFA-basierte PDF-Formulare in diesen Browsern anzuzeigen, müssen Sie so konfigurieren, dass PDFs mit Acrobat oder Reader geöffnet werden. Weitere Informationen finden Sie unter „XFA-basierte PDF-Formulare in Mozilla Firefox und Google Chrome“.
* Unter Microsoft® Windows® können Sie Acrobat und Reader so konfigurieren, dass PDFs im geschützten Ansichtsmodus geöffnet werden, was das Öffnen von XFA-basierten PDF-Formularen und richtliniengeschützten Dokumenten verhindert. Stellen Sie sicher, dass der geschützte Anzeigemodus in Ihrem Acrobat oder Reader deaktiviert ist. Weitere Informationen finden Sie unter [Geschützte Ansicht (nur Windows)](https://helpx.adobe.com/de/acrobat/kb/end-of-support-acrobat-x-reader-x.html).
* Wenn Sie versuchen, auf XFA-basierte PDF-Formulare oder richtliniengeschützte Dokumente auf Ihrem Mobilgerät zuzugreifen, sollten Sie Folgendes beachten:

  * Zum Öffnen richtliniengeschützter Dokumente auf Mobilgeräten ist Adobe Reader für Mobilgeräte erforderlich. Weitere Informationen finden Sie unter [Adobe Reader Mobile App](https://www.adobe.com/de/acrobat/mobile/acrobat-reader.html).
  * iOS-, Android- und Blackberry-Mobilgeräte und -Smartphones unterstützen das Adobe Reader-Plug-in mit XFA-Formularen nicht. LiveCycle ES4 bietet einen Service für Mobilgeräte, die HTML5 verwenden. Wer Formulare erstellt, muss diesen Service verwenden, damit Formulare auf diesen Geräten verwendet werden können.
  * Wenn Sie den Metro-Stil auf einem Windows 8-Mobilgerät verwenden, wechseln Sie zur klassischen Ansicht oder nutzen Sie HTML5 mit LiveCycle ES4.

>[!NOTE]
>
>LiveCycle ES4 bietet Unterstützung für die Darstellung von XFA-basierten Formularen in HTML5, sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich solcher, die auf Mobilgeräten wie dem iPad laufen. Die HTML5-Ausgabedarstellung der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechnungen und Formularvalidierungen). Auf diese Weise werden Ihre Technologieinvestitionen in XFA-Formulare einfach auf die Geräte übertragen, auf denen die Ausführung des Adobe Reader-Plug-ins nicht möglich ist.
>Weitere Informationen finden Sie unter „Aktualisieren“ in der [LiveCycle-Produktdokumentation](https://business.adobe.com/products/experience-manager/forms/aem-forms.html).

[Rechtliche Hinweise](https://chl-author-preview.corp.adobe.com/content/help/de/legal/legal-notices.html)    |    [Online-Datenschutzrichtlinie](https://www.adobe.com/de/privacy.html)
