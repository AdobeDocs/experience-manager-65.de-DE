---
title: Grundlagen der Konfiguration von Formularen
description: Erfahren Sie mehr über die verschiedenen Formulardienste, mit denen Sie interaktive Datenerfassungsanwendungen erstellen können.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 169f3d94-ac00-41c7-853e-ecf0dbee559f
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 100%

---

# Grundlagen der Konfiguration von Formularen {#basics-of-configuring-forms}

Der AEM Forms-Dienst ermöglicht es Ihnen, interaktive Client-Anwendungen zur Datenerfassung zu erstellen, die üblicherweise in Designer erstellte Formulare überprüfen, verarbeiten, transformieren und bereitstellen. Formularautorinnen und -autoren entwickeln einen einzelnen Formularentwurf, den der Forms-Dienst in verschiedenen Formaten rendert:

* als PDF in Adobe Reader oder in einem Browser
* als HTML in verschiedenen Browser-Umgebungen, einschließlich kompatiblem XHTML 1.0-Rendering
* als Formularleitfäden in verschiedenen Browser-Umgebungen, die Adobe Flash Player unterstützen

Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz](https://www.adobe.com/go/learn_aemforms_services_63).

Mithilfe der Forms-Seite in der Administrationskonsole können Sie das Verhalten des Forms-Dienstes konfigurieren. Diese Einstellungen gelten für alle Aufrufe des Dienstes. Alle Parameter, die durch das AEM Forms-SDK gesendet werden, überschreiben die in der Administrationskonsole festgelegten Einstellungen. Sie betreffen jedoch nur diesen bestimmten Aufruf. 

Nachdem Sie die Forms-Einstellungen in der Administrationskonsole geändert haben, klicken Sie auf „Speichern“. Der Server muss nicht neu gestartet werden, damit die Änderungen wirksam werden. Sie müssen jedoch ggf. den Forms-Dienst anhalten und neu starten, wenn Sie Cache-Moduseinstellungen konfigurieren. (Siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
