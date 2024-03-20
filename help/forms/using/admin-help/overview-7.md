---
title: Grundlagen der Konfiguration von Formularen
description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 169f3d94-ac00-41c7-853e-ecf0dbee559f
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 7%

---

# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

Mit dem Forms-Dienst können Sie interaktive Clientanwendungen zur Datenerfassung erstellen, mit denen typischerweise in Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Formularverfasser entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten wiedergibt:

* als PDF in Adobe Reader oder im Browser
* als HTML in verschiedenen Browserumgebungen, einschließlich einer konformen XHTML 1.0-Wiedergabe
* als Formular-Guides in verschiedenen Browserumgebungen, die Adobe-Flash Player unterstützen.

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz](https://www.adobe.com/go/learn_aemforms_services_63).

Auf der Seite &quot;Forms&quot;in Administration Console können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die über das AEM Forms SDK gesendet werden, überschreiben die Einstellungen, die in Administration Console festgelegt wurden. Sie wirken sich jedoch nur auf diesen bestimmten Aufruf aus.

Nachdem Sie die Forms-Einstellungen in Administration Console geändert haben, klicken Sie auf Speichern. Sie müssen den Server nicht neu starten, damit die Änderungen wirksam werden. Möglicherweise müssen Sie den Forms-Dienst jedoch beim Konfigurieren der Cachemodus-Einstellungen anhalten und neu starten. (Siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
