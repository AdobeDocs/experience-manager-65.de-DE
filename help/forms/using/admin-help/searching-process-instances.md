---
title: Nach Prozessinstanzen suchen
description: Verwenden Sie die Seite "Prozesssuche", um Suchkriterien zum Suchen einer Prozessinstanz einzugeben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 35f9acbf-7a82-43b1-9e17-9be4de666212
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 15%

---

# Nach Prozessinstanzen suchen{#searching-for-process-instances}

Verwenden Sie die Seite &quot;Prozesssuche&quot;, um Suchkriterien zum Suchen einer Prozessinstanz einzugeben. Sie können auf die Seite &quot;Prozesssuche&quot;über die Seite des Arbeitsablaufs für Formulare zugreifen oder indem Sie auf der Seite &quot;Prozessinstanz&quot;auf Suchen klicken.

Sie können grundlegende Kriterien für eine allgemeine Suche, spezifische Attribute für eine detaillierte Suche oder eine Kombination aus grundlegenden Kriterien und spezifischen Attributen eingeben, um eine kombinierte Suche durchzuführen.

## Allgemeine Suche durchführen {#perform-a-general-search}

Eine allgemeine Suche nach einem Prozess ist am besten geeignet, wenn Sie die Prozess-ID der Prozessinstanz kennen, wenn Sie nach einer Gruppe verwandter Prozessinstanzen suchen oder wenn nur einige Prozessinstanzen ausgeführt werden.

Geben Sie grundlegende Kriterien für eine allgemeine Suche ein. Wenn Sie mehrere Kriterien eingeben, wird die Suche mit einer impliziten UND-Bedingung durchgeführt.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Prozesssuche&quot;.
1. Geben Sie auf der Seite &quot;Prozesssuche&quot;unter &quot;Allgemeine Suche&quot;die folgenden Kriterien ein:

   * **Prozess-ID:** Die positive Ganzzahl, die jede eindeutige Prozessinstanz identifiziert.
   * **Prozessstatus:** Wählen Sie den gewünschten Status in der Liste.
   * **Programm:** Wählen Sie das gewünschte Programm in der Liste. Nur bereitgestellte Programme werden angezeigt.
   * **Prozessname/-version:** Wählen Sie einen Prozessnamen im Menü. Es werden nur bereitgestellte Prozesse angezeigt.

1. Klicken Sie auf „Suchen“. Die Seite &quot;Prozessinstanz&quot;wird angezeigt und listet die gefundenen Instanzen auf.

## Detailsuche nach einem Prozess durchführen {#perform-a-detailed-search-for-a-process}

Sie können bestimmte Attribute eingeben, um eine Detailsuche durchzuführen. Eine detaillierte Suche ist am besten geeignet, wenn viele Prozessinstanzen ausgeführt werden und Sie die möglichen Suchen nach bestimmten Kriterien eingrenzen müssen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Forms-Workflow&quot;> &quot;Prozesssuche&quot;.
1. Geben Sie auf der Seite &quot;Prozesssuche&quot;unter &quot;Detailsuche&quot;den ersten Kriteriensatz an:

   * Wählen Sie in der Liste Attribut ein Attribut aus.
   * Wählen Sie in der Liste Filter einen Operator aus.
   * Geben Sie in das Feld &quot;Value&quot;einen Wert ein, der dem ausgewählten Attribut entspricht.

1. Um eine weitere Zeile hinzuzufügen, wählen Sie Weitere Filter aus. Eine weitere Gruppe von Listen &quot;Attribut&quot;, &quot;Filter&quot;und &quot;Wert&quot;sowie eine Liste &quot;Bedingung&quot;werden angezeigt.
1. Wählen Sie unter &quot;Bedingung&quot;UND oder ODER aus. Wiederholen Sie die Schritte 1 bis 3 nach Bedarf, um die Suche weiter einzuschränken.
1. Um Zeilen hinzuzufügen oder zu entfernen, klicken Sie auf &quot;Mehr Filter&quot;oder &quot;Weniger Filter&quot;. Sie können eine bis vier Zeilen haben.
1. Klicken Sie auf „Suchen“. Die Seite &quot;Prozessinstanz&quot;wird angezeigt und listet die gefundenen Instanzen auf.

[Informationen zum Status von Prozessinstanzen](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Kombinierte Suche nach einem Prozess durchführen {#perform-a-combined-search-for-a-process}

Um eine Suche zu erstellen, die sowohl auf einer allgemeinen als auch auf einer detaillierten Suche basiert, mit einem impliziten UND zwischen den Bereichen, geben Sie Ihre Suchkriterien sowohl in die Bereiche &quot;Allgemeine Suche&quot;als auch &quot;Detailsuche&quot;auf der Seite &quot;Prozesssuche&quot;ein.

Wenn die Suche zu eng ist, werden keine Instanzen gefunden.
