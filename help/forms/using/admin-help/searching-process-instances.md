---
title: Nach Prozessinstanzen suchen
seo-title: Nach Prozessinstanzen suchen
description: Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben.
seo-description: Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben.
uuid: 4a9c5b05-add5-4278-9c6f-d1928b6860d2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 88b634bb-8f6c-4830-ad01-821668609615
exl-id: 35f9acbf-7a82-43b1-9e17-9be4de666212
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 98%

---

# Nach Prozessinstanzen suchen{#searching-for-process-instances}

Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben. Sie können über die Seite „Arbeitsablauf für Formulare“ auf die Seite „Prozesssuche“ zugreifen oder stattdessen auf der Seite „Prozessinstanz“ auf „Suchen“ klicken.

Sie können grundlegende Kriterien zur Durchführung einer allgemeinen Suche eingeben, spezifische Attribute zur Durchführung einer Detailsuche oder eine Kombination aus grundlegenden Kriterien und spezifischen Attributen zur Durchführung einer kombinierten Suche.

## Eine allgemeine Suche durchführen {#perform-a-general-search}

Eine allgemeine Suche nach einem Prozess eignet sich optimal, wenn Sie die Prozess-ID der Prozessinstanz kennen, wenn Sie versuchen, eine Gruppe verwandter Prozessinstanzen zu finden oder wenn nur wenige Prozessinstanzen ausgeführt werden.

Geben Sie zum Durchführen einer allgemeinen Suche grundlegende Kriterien ein. Wenn Sie mehrere Kriterien eingeben, wird die Suche mit einer impliziten UND-Bedingung ausgeführt.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Allgemeine Suche“ die folgenden Kriterien ein:

   * **Prozess-ID:** Die positive ganze Zahl, die jede eindeutige Prozessinstanz identifiziert.
   * **Prozessstatus:** Wählen Sie den gewünschten Status in der Liste.
   * **Anwendung:** Wählen Sie die gewünschte Anwendung in der Liste. Nur bereitgestellte Anwendungen werden angezeigt.
   * **Prozessname/-version:** Wählen Sie einen Prozessnamen im Menü. Nur bereitgestellte Prozesse werden angezeigt.

1. Klicken Sie auf Suchen. Die Seite „Prozessinstanz“ wird mit einer Liste der gefundenen Instanzen angezeigt.

## Eine Detailsuche nach einem Prozess durchführen  {#perform-a-detailed-search-for-a-process}

Zum Durchführen einer Detailsuche geben Sie spezifische Attribute ein. Eine Detailsuche eignet sich optimal, wenn zahlreiche Prozessinstanzen ausgeführt werden und Sie die möglichen Suchergebnisse durch bestimmte Kriterien einschränken müssen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Arbeitsablauf für Formulare“ > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Detailsuche“ den ersten Kriteriensatz an:

   * Wählen Sie in der Liste „Attribut“ ein Attribut aus.
   * Wählen Sie in der Liste „Filter“ einen Operator aus.
   * Geben Sie in das Feld „Wert“ einen dem ausgewählten Attribut entsprechenden Wert ein.

1. Klicken Sie zum Hinzufügen einer weiteren Zeile auf „Mehr Filter“. Ein weiterer Satz von „Attribut“-, „Filter“- und „Wert“-Listen sowie die Liste „Bedingung“ werden angezeigt.
1. Wählen Sie unter „Bedingung“ UND oder ODER. Wiederholen Sie die Schritte 1 bis 3 nach Bedarf, um die Suche weiter einzuschränken.
1. Klicken Sie zum Hinzufügen oder Löschen von Zeilen auf „Mehr Filter“ oder „Weniger Filter“. Es können eine bis vier Zeilen verwendet werden.
1. Klicken Sie auf Suchen. Die Seite „Prozessinstanz“ wird mit einer Liste der gefundenen Instanzen angezeigt.

[Informationen zum Status von Prozessinstanzen](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Eine kombinierten Suche nach einem Prozess durchführen {#perform-a-combined-search-for-a-process}

Um eine Suche zu erstellen, die sowohl auf einer allgemeinen als auch auf einer Detailsuche basiert, wobei beide Bereiche durch ein implizites UND verknüpft sind, geben Sie die Suchkriterien auf der Seite „Prozesssuche“ in die beiden Bereiche „Allgemeine Suche“ und „Detailsuche“ ein.

Wenn die Suche zu stark eingeschränkt ist, werden keine Instanzen gefunden.
