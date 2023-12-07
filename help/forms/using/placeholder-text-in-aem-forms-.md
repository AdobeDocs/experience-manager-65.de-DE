---
title: Platzhaltertext in AEM Forms
description: Platzhaltertext soll Benutzern bei der Dateneingabe helfen, wenn das Steuerelement keinen Wert hat. Es kann sich um einen Beispielwert oder eine kurze Beschreibung des erwarteten Formats handeln.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms
exl-id: 6b6e27b5-8b4e-489c-9e72-4d256692c1ca
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 69%

---

# Platzhaltertext in AEM Forms {#placeholder-text-in-aem-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

Der Platzhaltertext stellt ein Wort oder einen kurzen Satz dar. Sie soll den Benutzer bei der Dateneingabe unterstützen, wenn das Steuerelement keinen Wert hat. Ein Platzhaltertext kann ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein. Der Platzhaltertext wird gezeigt, bevor der Benutzer einen Text eingibt, und entfernt, wenn der Benutzer einen Wert eingibt oder auswählt.

>[!NOTE]
>
>Der Platzhaltertext muss, falls angegeben, einen Wert enthalten, der keine neuen Zeilenzeichen enthält.

![Datumskomponente mit und ohne Platzhaltertext](assets/dat-picker-place-holder-text.png)

**A.** Datumskomponente mit Platzhaltertext **B.** Datumskomponente ohne Platzhaltertext

AEM Forms unterstützt Platzhaltertext für die Felder vom Typ „Kennwort“, „Datumsauswahl“, „Numerisches Feld“ und „Textfeld“.\
Platzhaltertexte werden für das native HTML5-Datum-Widget nicht unterstützt. Angeben eines Platzhaltertexts:

1. Klicken Sie mit der rechten Maustaste auf eine Komponente, die Platzhaltertext unterstützt, und klicken Sie auf **Bearbeiten**. Das Dialogfeld „Komponente bearbeiten“ wird angezeigt.

1. Öffnen Sie die Registerkarte **Titel und Text**.
1. Geben Sie ein Wort oder einen kurzen Satz im Feld **Platzhaltertext** ein. Klicken Sie auf **OK**.

>[!NOTE]
>
>Platzhaltertext wird in Microsoft Internet Explorer 9 nicht unterstützt.
