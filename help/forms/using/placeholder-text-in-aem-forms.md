---
title: Platzhaltertext in AEM Forms
description: Platzhaltertext soll Benutzenden bei der Dateneingabe helfen, wenn das Steuerelement keinen Wert hat. Dabei kann es sich um einen Beispielwert oder eine kurze Beschreibung des erwarteten Formats handeln.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 6b6e27b5-8b4e-489c-9e72-4d256692c1ca
solution: Experience Manager, Experience Manager Forms
role: User, Developer
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
source-wordcount: '278'
ht-degree: 100%
---
# Platzhaltertext in AEM Forms {#placeholder-text-in-aem-forms}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

Der Platzhaltertext stellt ein Wort oder einen kurzen Satz dar. Er soll Benutzenden bei der Dateneingabe helfen, wenn das Steuerelement keinen Wert hat. Ein Platzhaltertext könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein. Der Platzhaltertext wird gezeigt, bevor der Benutzer einen Text eingibt, und entfernt, wenn der Benutzer einen Wert eingibt oder auswählt.

>[!NOTE]
>
>Der Platzhaltertext muss, falls angegeben, einen Wert enthalten, der keine neuen Zeilenzeichen enthält.

![Datumskomponente mit und ohne Platzhaltertext](assets/dat-picker-place-holder-text.png)

**A.** Datumskomponente mit Platzhaltertext **B.** Datumskomponente ohne Platzhaltertext

AEM Forms unterstützt Platzhaltertext für die Felder vom Typ „Kennwort“, „Datumsauswahl“, „Numerisches Feld“ und „Textfeld“.\
Platzhaltertexte werden für das native HTML5-Datum-Widget nicht unterstützt. Angeben eines Platzhaltertexts:

1. Klicken Sie mit der rechten Maustaste auf eine Komponente, die Platzhaltertext unterstützt, und klicken Sie dann auf **Bearbeiten**. Das Dialogfeld „Komponente bearbeiten“ wird angezeigt.

1. Öffnen Sie die Registerkarte **Titel und Text**.
1. Geben Sie ein Wort oder einen kurzen Satz im Feld **Platzhaltertext** ein. Klicken Sie auf **OK**.

>[!NOTE]
>
>Platzhaltertext wird in Microsoft Internet Explorer 9 nicht unterstützt.
