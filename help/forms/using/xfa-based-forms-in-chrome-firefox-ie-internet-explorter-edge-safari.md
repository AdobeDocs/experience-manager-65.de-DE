---
title: XFA-basierte PDF forms können nicht in Google Chrome, Firefox, Microsoft Edge, Microsoft Internet Explorer oder Apple Safari geöffnet werden.
seo-title: Unable to open XFA-based PDF forms in Google Chrome, Firefox, Microsoft Edge, Microsoft Internet Explorer, or Apple Safari
feature: Adaptive Forms
source-git-commit: f2b76ce0c2f296f81c3748794bf2ab74ccd5bb95
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---


# XFA-basierte PDF forms können nicht in Google Chrome, Firefox, Microsoft Edge, Microsoft Internet Explorer oder Apple Safari geöffnet werden.{#unable-to-open-XFA-based-PDF-forms-in-Google-Chrome-Firefox-Microsoft-Edge-Microsoft-Internet-Explorer-or-Apple-Safari}

Viele neuere Browserversionen haben ihre eigene eingeschränkte Unterstützung für XFA-basierte PDF forms enthalten. Obwohl diese Browser XFA-basierte PDF forms öffnen können, sind die bereitgestellten Funktionen begrenzt. Wenn Sie ein XFA-basiertes PDF-Formular nicht in einem modernen Browser öffnen oder senden können, verwenden Sie eine der folgenden Methoden:

* Verwendung [Adobe® Acrobat®](https://www.adobe.com/acrobat.html) oder [Adobe® Adobe® Reader®](https://get.adobe.com/de/reader/), Version 8 oder höher zum Öffnen und Senden von XFA-basierten PDF forms.
* Mit Acrobat und Reader können Sie unter Microsoft® Windows® konfigurieren, dass PDF im geschützten Ansichtsmodus geöffnet werden, was das Öffnen von XFA-basierten PDF forms verhindert. Stellen Sie sicher, dass der geschützte Anzeigemodus in Ihrer Acrobat oder Ihrem Reader deaktiviert ist. Weitere Informationen finden Sie unter [Geschützte Ansicht (nur Windows)](https://helpx.adobe.com/in/reader/using/protected-mode-windows.html).
* (Für Forms-Entwickler) Adobe Experience Manager Forms bietet außerdem Unterstützung für:

   * [Rendern von XFA-basierten Formularen in HTML5 Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/html5-forms/introduction.html?#key-capabilities-of-html-forms-br) sodass die Formulare in Browsern mit HTML5-Unterstützung geöffnet werden können, einschließlich solcher, die auf Mobilgeräten wie iPad ausgeführt werden. Die HTML5-Ausgabe der Formulare behält das Layout des Formularentwurfs bei und unterstützt die meisten in die XFA-Formularvorlage eingebetteten Formularlogiken (z. B. JavaScript, Formularberechtigungen und Formularvalidierungen).
   * [Konvertieren von XFA-basierten Formularen in mobile responsive adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/creating-adaptive-form.html?#create-an-adaptive-form-based-on-an-xfa-form-template). Diese Formulare bieten ein responsives Layout, Personalisierungsfunktionen und passen sich dynamisch an Benutzerantworten an, indem Sie nach Bedarf Felder oder Abschnitte hinzufügen oder entfernen. Diese bieten außerdem vorkonfigurierte Connectoren für verschiedene Datenquellen, Datensatzdokumentfunktionen und eine einfache Verbindung zu Adobe Analytics zur Leistungsbewertung. Weitere Informationen finden Sie unter [Wichtige Funktionen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/key-features.html).

Auf diese Weise sind Ihre Technologieinvestitionen in XFA-Formulare geschützt und bieten Ihren Endbenutzern weiterhin optimale Erlebnisse. Weitere Informationen finden Sie unter [Adobe Experience Manager Forms-Produktdokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html).
