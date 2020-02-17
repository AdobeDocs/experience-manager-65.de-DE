---
title: Grundlagen der Konfiguration von Formularen
seo-title: Grundlagen der Konfiguration von Formularen
description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
seo-description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

Der Forms-Dienst ermöglicht das Erstellen interaktiver Clientanwendungen zur Datenerfassung, die in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und übermitteln. Formularersteller entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten wiedergibt:

* als PDF in Adobe Reader oder in einem Browser;
* als HTML in verschiedenen Browserumgebungen, einschließlich einer kompatiblen XHTML 1.0-Wiedergabe;
* als Formular-Guides in verschiedenen Browserumgebungen, die Adobe Flash Player unterstützen.

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

Mithilfe der Forms-Seite in Administration Console können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die durch die AEM Forms-SDK gesendet werden, überschreiben die Einstellungen, die in Administration Console festgelegt werden. Sie betreffen jedoch nur diesen bestimmten Aufruf.

Nachdem Sie die Forms-Einstellungen in Administration Console geändert haben, klicken Sie auf „Speichern“. Der Server muss nicht neu gestartet werden, um die Änderungen zu übernehmen. Sie müssen jedoch ggf. den Forms-Dienst anhalten und neu starten, wenn Sie Cachemoduseinstellungen konfigurieren. (Siehe [ Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
