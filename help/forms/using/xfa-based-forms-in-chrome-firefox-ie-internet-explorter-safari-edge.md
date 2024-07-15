---
title: XFA-basierte PDF-Formulare können in Google Chrome, Firefox, Microsoft® Edge, Microsoft® Internet Explorer oder Apple Safari nicht geöffnet werden.
description: XFA-basierte PDF-Formulare können in Google Chrome, Firefox, Microsoft® Edge, Microsoft® Internet Explorer oder Apple Safari nicht geöffnet werden.
feature: Adaptive Forms,Document Services
exl-id: fdd15315-e0d6-4d80-acb4-2e0ecec716c4
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 100%

---

# XFA-basierte PDF-Formulare können in Google Chrome, Firefox, Microsoft® Edge, Microsoft® Internet Explorer oder Apple Safari nicht geöffnet werden.{#unable-to-open-XFA-based-PDF-forms-in-Google-Chrome-Firefox-Microsoft-Edge-Microsoft-Internet-Explorer-or-Apple-Safari}

Viele neuere Browserversionen bieten eine eigene, begrenzte Unterstützung für XFA-basierte PDF-Formulare. Auch wenn diese Browser XFA-basierte PDF-Formulare öffnen können, sind die zur Verfügung stehenden Möglichkeiten begrenzt. Wenn Sie ein XFA-basiertes PDF-Formular nicht in einem modernen Browser öffnen oder senden können, verwenden Sie eine der folgenden Methoden:

* Verwenden Sie [Adobe® Acrobat®](https://www.adobe.com/acrobat.html) oder [Adobe® Adobe® Reader®](https://get.adobe.com/de/reader/), Version 8 oder höher, um XFA-basierte PDF-Formulare zu öffnen und zu senden.
* Unter Microsoft® Windows® können Sie Acrobat und Reader so konfigurieren, dass PDFs im geschützten Ansichtsmodus geöffnet werden, was das Öffnen von XFA-basierten PDF-Formularen verhindert. Stellen Sie sicher, dass der geschützte Anzeigemodus in Ihrem Acrobat oder Reader deaktiviert ist. Weitere Informationen finden Sie unter [Geschützte Ansicht (nur Windows)](https://helpx.adobe.com/de/reader/using/protected-mode-windows.html).
* (Für Formularentwickler) Adobe Experience Manager Forms bietet außerdem Unterstützung für:

   * [Rendern von XFA-basierten Formularen in HTML5-Formularen](https://experienceleague.adobe.com/docs/experience-manager-65/forms/html5-forms/introduction.html?lang=de#key-capabilities-of-html-forms-br), sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich Browsern, die auf Mobilgeräten wie dem iPad laufen. Die HTML5-Ausgabedarstellung der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechnungen und Formularvalidierungen).
   * [Konvertieren von XFA-basierten Formularen in responsive adaptive Formulare für Mobilgeräte](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?lang=de#create-an-adaptive-form-based-on-an-xfa-form-template). Diese Formulare bieten ein responsives Layout und Personalisierungsfunktionen und passen sich dynamisch an Benutzerantworten an, indem nach Bedarf Felder oder Abschnitte hinzugefügt oder entfernt werden. Sie bieten außerdem vorkonfigurierte Connectoren für verschiedene Datenquellen, Datensatzdokumentfunktionen und eine einfache Verbindung zu Adobe Analytics zur Leistungsbewertung. Weitere Informationen finden Sie unter [Wichtige Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/home.html?lang=de)
Auf diese Weise sind Ihre Technologieinvestitionen in XFA-Formulare geschützt und bieten Ihren Endbenutzerinnen und Endbenutzern weiterhin optimale Erlebnisse. Weitere Informationen finden Sie in der [Produktdokumentation zu Adobe Experience Manager Forms](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/home.html?lang=de).
