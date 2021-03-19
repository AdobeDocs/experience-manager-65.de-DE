---
title: 'Platzhaltertext in AEM Forms '
seo-title: 'Platzhaltertext in AEM Forms '
description: Platzhaltertext unterstützt den Benutzer bei der Dateneingabe, wenn das Steuerelement keinen Wert hat. Das könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein.
seo-description: Platzhaltertext unterstützt den Benutzer bei der Dateneingabe, wenn das Steuerelement keinen Wert hat. Das könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein.
uuid: 69f80722-93db-4932-9016-4b530e183d4e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: f9ff2cc5-3f0a-4b2f-a206-2fe0985646ea
docset: aem65
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 95%

---


# Platzhaltertext in AEM Forms {#placeholder-text-in-aem-forms}

Der Platzhaltertext stellt ein Wort oder einen kurzen Satz dar. Er unterstützt den Benutzer bei der Dateneingabe, wenn das Steuerelement keinen Wert hat. Ein Platzhaltertext könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein. Der Platzhaltertext wird gezeigt, bevor der Benutzer einen Text eingibt, und entfernt, wenn der Benutzer einen Wert eingibt oder auswählt.

>[!NOTE]
>
>Der Platzhaltertext muss, falls angegeben, einen Wert enthalten, der keine neuen Zeilenzeichen enthält.

![Datumskomponente mit und ohne Platzhaltertext](assets/dat-picker-place-holder-text.png)

**A.** Date-Komponente mit Platzhaltertext  **B.** Date-Komponente ohne Platzhaltertext

AEM Forms unterstützt Platzhaltertext für die Felder „Kennwort“, „Datumsauswahl“, „Numerisches Feld“ und „Textfeld“.\
Platzhaltertexte werden für das native HTML5-Datumswidget nicht unterstützt. Abgabe eines Platzhaltertexts:

1. Kicken Sie mit der rechten Maustaste auf eine Komponente, die Platzhaltertext unterstützt, und klicken Sie auf **Bearbeiten**. Das Dialogfeld „Komponente bearbeiten“ wird angezeigt.

1. Öffnen Sie die Registerkarte **Titel und Text.**
1. Geben Sie ein Wort oder einen kurzen Satz im Feld **Platzhaltertext** ein. Klicken Sie auf **OK**.

>[!NOTE]
>
>Platzhaltertext wird nicht in Microsoft Internet Explorer 9 unterstützt.

