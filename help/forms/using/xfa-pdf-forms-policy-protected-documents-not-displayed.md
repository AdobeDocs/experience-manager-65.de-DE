---
title: Probleme für XFA-basierte PDF forms und richtliniengeschützte Dokumente anzeigen
description: Probleme für XFA-basierte PDF forms und richtliniengeschützte Dokumente anzeigen
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: ebb61f2c5056a780e829e64031f8eba69a8ae25b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 5%

---

# Probleme für XFA-basierte PDF forms und richtliniengeschützte Dokumente anzeigen

Überprüfen Sie aus den folgenden Gründen, ob Sie ein XFA-basiertes PDF-Formular oder ein richtliniengeschütztes Dokument nicht mit Adobe LiveCycle Rights Management öffnen können:

* XFA-basierte PDF forms und richtliniengeschützte Dokumente erfordern Adobe® Acrobat® oder Adobe® Reader®, Version 8 und höher. Unter [Adobe-Downloads](https://www.adobe.com/downloads.html) finden Sie Informationen zum Herunterladen der neuesten Reader oder Acrobat.
* Browser wie Mozilla Firefox und Google Chrome bieten einen integrierten PDF-Viewer, der XFA-basierte PDF forms nicht unterstützt. Um XFA-basierte PDF forms in diesen Browsern anzuzeigen, müssen Sie so konfigurieren, dass PDFs mit Acrobat oder Reader geöffnet werden. Weitere Informationen finden Sie unter XFA-basierte PDF forms in Mozilla Firefox und Google Chrome.
* Acrobat und Reader ermöglichen es Ihnen unter Microsoft® Windows®, das Öffnen von PDFs im geschützten Ansichtsmodus zu konfigurieren, wodurch das Öffnen von XFA-basierten PDF forms- und richtliniengeschützten Dokumenten verhindert wird. Stellen Sie sicher, dass der geschützte Anzeigemodus in Ihrem Acrobat oder Reader deaktiviert ist. Weitere Informationen finden Sie unter [Geschützte Ansicht (nur Windows)](https://helpx.adobe.com/de/acrobat/kb/end-of-support-acrobat-x-reader-x.html).
* Wenn Sie versuchen, auf XFA-basierte PDF forms oder richtliniengeschützte Dokumente auf Ihrem Mobilgerät zuzugreifen, sollten Sie Folgendes beachten:

   * Zum Öffnen richtliniengeschützter Dokumente auf Mobilgeräten ist Adobe Reader für Mobilgeräte erforderlich. Weitere Informationen finden Sie unter [Adobe Reader Mobile App](https://www.adobe.com/in/acrobat/mobile/acrobat-reader.html).
   * iOS-, Android- und Blackberry-Mobilgeräte und -Smartphones unterstützen das Adobe Reader-Plug-in mit XFA-Formularen nicht. LiveCycle ES4 bietet einen Service für Mobilgeräte, die HTML5 verwenden. Der Formularersteller muss diesen Service verwenden, damit Formulare auf diesen Geräten verwendet werden können.
   * Wenn Sie den Metro-Stil auf einem Windows 8-Mobilgerät verwenden, wechseln Sie zur klassischen Ansicht oder nutzen Sie HTML5 mit LiveCycle ES4.

>[!NOTE]
>
>LiveCycle ES4 unterstützt die Wiedergabe von XFA-basierten Formularen in HTML5, sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich solcher, die auf Mobilgeräten wie iPad ausgeführt werden. Die HTML5-Ausgabedarstellung der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechnungen und Formularvalidierungen). Auf diese Weise können Ihre Technologieinvestitionen in XFA-Formulare einfach auf die Geräte übertragen werden, auf denen das Adobe Reader-Plug-in nicht ausgeführt werden kann.
>Weitere Informationen finden Sie unter Aktualisieren auf [LiveCycle-Produktdokumentation](https://business.adobe.com/products/experience-manager/forms/aem-forms.html).

[Rechtliche Hinweise](https://chl-author-preview.corp.adobe.com/content/help/en/legal/legal-notices.html)    |    [Online-Datenschutzrichtlinie](https://www.adobe.com/de/privacy.html)