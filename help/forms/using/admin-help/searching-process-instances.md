---
title: Nach Prozessinstanzen suchen
description: Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 35f9acbf-7a82-43b1-9e17-9be4de666212
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '449'
ht-degree: 100%

---

# Nach Prozessinstanzen suchen{#searching-for-process-instances}

Verwenden Sie die Seite „Prozesssuche“, um Suchkriterien zum Auffinden einer Prozessinstanz einzugeben. Sie können über die Seite „Arbeitsablauf für Formulare“ auf die Seite „Prozesssuche“ zugreifen oder stattdessen auf der Seite „Prozessinstanz“ auf „Suchen“ klicken.

Sie können grundlegende Kriterien zur Durchführung einer allgemeinen Suche eingeben, spezifische Attribute zur Durchführung einer Detailsuche oder eine Kombination aus grundlegenden Kriterien und spezifischen Attributen zur Durchführung einer kombinierten Suche.

## Durchführen einer allgemeinen Suche {#perform-a-general-search}

Eine allgemeine Suche nach einem Prozess eignet sich optimal, wenn Sie die Prozess-ID der Prozessinstanz kennen, wenn Sie versuchen, eine Gruppe verwandter Prozessinstanzen zu finden oder wenn nur wenige Prozessinstanzen ausgeführt werden.

Geben Sie zum Durchführen einer allgemeinen Suche grundlegende Kriterien ein. Wenn Sie mehrere Kriterien eingeben, wird die Suche mit einer impliziten UND-Bedingung ausgeführt.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Allgemeine Suche“ die folgenden Kriterien ein:

   * **Prozess-ID:** Die positive Ganzzahl, die jede eindeutige Prozessinstanz identifiziert.
   * **Prozessstatus:** Wählen Sie den gewünschten Status in der Liste.
   * **Programm:** Wählen Sie das gewünschte Programm in der Liste. Nur bereitgestellte Programme werden angezeigt.
   * **Prozessname/-version:** Wählen Sie einen Prozessnamen im Menü. Nur bereitgestellte Prozesse werden angezeigt.

1. Klicken Sie auf „Suchen“. Die Seite „Prozessinstanzen“ wird mit einer Liste der gefundenen Instanzen angezeigt.

## Durchführen einer Detailsuche nach einem Prozess {#perform-a-detailed-search-for-a-process}

Zum Durchführen einer Detailsuche geben Sie spezifische Attribute ein. Eine Detailsuche eignet sich am besten, wenn zahlreiche Prozessinstanzen ausgeführt werden und Sie die möglichen Suchergebnisse durch bestimmte Kriterien einschränken müssen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Forms Workflow“ > „Prozesssuche“.
1. Geben Sie auf der Seite „Prozesssuche“ unter „Detailsuche“ den ersten Kriteriensatz an:

   * Wählen Sie in der Liste „Attribut“ ein Attribut aus.
   * Wählen Sie in der Liste „Filter“ einen Operator aus.
   * Geben Sie in das Feld „Wert“ einen dem ausgewählten Attribut entsprechenden Wert ein.

1. Wählen Sie zum Hinzufügen einer weiteren Zeile „Mehr Filter“ aus. Ein weiterer Satz von „Attribut“-, „Filter“- sowie „Wert“-Listen und die Liste „Bedingung“ werden angezeigt.
1. Wählen Sie unter „Bedingung“ UND oder ODER. Wiederholen Sie die Schritte 1 bis 3 nach Bedarf, um die Suche weiter einzuschränken.
1. Klicken Sie zum Hinzufügen oder Löschen von Zeilen auf „Mehr Filter“ oder „Weniger Filter“. Es können eine bis vier Zeilen verwendet werden.
1. Klicken Sie auf „Suchen“. Die Seite „Prozessinstanzen“ wird mit einer Liste der gefundenen Instanzen angezeigt.

[Informationen zum Status von Prozessinstanzen](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Durchführen einer kombinierten Suche nach einem Prozess {#perform-a-combined-search-for-a-process}

Um eine Suche zu erstellen, die sowohl auf einer allgemeinen als auch auf einer Detailsuche basiert, wobei beide Bereiche durch ein implizites UND verknüpft sind, geben Sie die Suchkriterien auf der Seite „Prozesssuche“ in die beiden Bereiche „Allgemeine Suche“ und „Detailsuche“ ein.

Wenn die Suche zu stark eingeschränkt ist, werden keine Instanzen gefunden.
