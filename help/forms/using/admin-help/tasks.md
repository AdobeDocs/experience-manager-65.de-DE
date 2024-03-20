---
title: Arbeiten mit Aufgaben
description: Verwenden Sie die Seite "Aufgabensuche", um nach Aufgaben nach Benutzername oder Aufgaben-ID zu suchen. Erfahren Sie mehr über das Arbeiten mit Aufgaben.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 375376d1-60b3-49a4-8893-ba9336e6bf7b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 41%

---

# Arbeiten mit Aufgaben {#working-with-tasks}

Verwenden Sie die Seite &quot;Aufgabensuche&quot;, um nach Aufgaben nach Benutzername oder Aufgaben-ID zu suchen. Die Suchergebnisse werden auf der Seite Aufgabenliste angezeigt, auf der Sie auf den Verlauf einer Aufgabe zugreifen können. Sie können eine Aufgabe auch neu zuweisen, wenn ein Benutzer zu viele Aufgaben hat oder wenn ein Benutzer eine Aufgabenzuweisung fälschlicherweise erhalten hat.

>[!NOTE]
>
>Bei der Aufgabensuche werden keine Ergebnisse für Benutzernamen zurückgegeben, die mit einem Nummernzeichen (#) beginnen. Vermeiden Sie, möglichst Benutzernamen zu erstellen, die mit einem Nummernzeichen beginnen.

## Suchen nach Aufgaben, die mit einem Benutzer verknüpft sind {#search-for-tasks-associated-with-a-user}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Aufgabensuche&quot;.
1. Wählen Sie unter &quot;Suchen nach&quot;die Option &quot;Benutzername&quot;. Wenn Sie einen Teil des gesuchten Benutzernamens kennen, geben Sie ihn in das Feld ein. Klicken Sie auf Benutzer suchen .
1. Die Seite &quot;Benutzer suchen&quot;wird angezeigt. Sie können Ihre Suche weiter verfeinern, indem Sie nach Benutzername oder E-Mail suchen. Wenn Sie den gesuchten Benutzer gefunden haben, wählen Sie das Optionsfeld neben dem Namen aus und klicken Sie auf &quot;OK&quot;.
1. Standardmäßig sucht die Aufgabensuche nach Aufgaben, die dem Benutzer derzeit zugewiesen sind. Um auch nach Aufgaben zu suchen, die dem Benutzer zuvor zugewiesen waren, wählen Sie &quot;Nicht zugewiesene Aufgabe anzeigen&quot;. Um auch nach Aufgaben zu suchen, die der Benutzer abgeschlossen hat, wählen Sie &quot;Abgeschlossene Aufgabe anzeigen&quot;.
1. Klicken Sie auf Suchen. Die Seite &quot;Aufgabenliste&quot;wird mit einer Liste der Suchergebnisse angezeigt.

## Suchen nach einer Aufgabe, wenn Sie ihre Aufgaben-ID kennen {#search-for-a-task-when-you-know-its-task-id}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Arbeitsablauf für Formulare&quot;> &quot;Aufgabensuche&quot;.
1. Wählen Sie unter &quot;Suchen nach&quot;die Option &quot;Task ID&quot;aus und geben Sie die Aufgaben-ID in das Feld ein.
1. Klicken Sie auf Suchen. Die Seite &quot;Aufgabenliste&quot;wird mit einer Liste der Suchergebnisse angezeigt.

## Arbeiten mit der Aufgabenliste {#working-with-the-task-list}

Die Ergebnisse einer Aufgabensuche werden auf der Seite Aufgabenliste angezeigt. Sie können eine Aufgabe auswählen, um die Seite &quot;Aufgabenverlauf&quot;zu öffnen. Von dort aus können Sie die Aufgabe einem anderen Benutzer zuweisen.

Die Aufgaben werden mit den folgenden Informationen angezeigt:

**Aufgaben-ID**: Die positive Ganzzahl, die vom Arbeitsablauf für Formulare zugewiesen wird, wenn die Aufgabe instanziiert (von einem Benutzer initiiert) wird. Sie können diese Kennung verwenden, um die Aufgabe während ihres gesamten Lebenszyklus zu verfolgen. Klicken Sie auf eine Aufgaben-ID, um Details zum Aufgabenverlauf anzuzeigen oder die Aufgabe einem anderen Benutzer neu zuzuweisen.

**Status**: Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war. Möglich ist auch der Status Abgeschlossen.

**Aktivität**: Zeigt das Formular und den Namen für einen anfänglichen Vorgang oder den Prozessvorgang an, der die Aufgabe generiert hat.

**Prozess-ID**: Die positive Ganzzahl, die vom Arbeitsablauf für Formulare zugewiesen wird, wenn der Prozess instanziiert (d. h. von einem Benutzer oder einem automatisierten Schritt initiiert) wird. Anhand dieser ID können Sie die Prozessinstanz während ihres gesamten Lebenszyklus verfolgen.

**Prozessname/-version**: Der Name des Prozesses, wie in Workbench definiert.

**Programm**: Der Name des Programms, zu dem der Vorgang gehört, wie in Workbench definiert.

**Erstellungsdatum**: Das Datum und die Uhrzeit, zu der die Aufgabe erstellt wurde.

## Aufgabenverlauf anzeigen und Aufgaben neu zuweisen {#viewing-task-history-and-reassigning-tasks}

Auf der Seite &quot;Aufgabenverlauf&quot;wird eine Liste der Benutzer und Gruppen angezeigt, die einer bestimmten Aufgabe zugewiesen wurden.

Für jede Aufgabenzuweisung werden in der Liste die folgenden Informationen angezeigt:

**Name**: Der Name des Benutzers.

**Status**: Zugewiesen bedeutet, dass die Aufgabe derzeit dem Benutzer zugewiesen ist. Nicht zugewiesen bedeutet, dass die Aufgabe dem Benutzer zuvor zugewiesen war.

**Arbeitslisten-ID**: Die numerische Kennung der Benutzerwarteschlange, zu der die Aufgabe gehört. Ein Prozess kann von mehreren Benutzern gemeinsam verwendet werden.

**Typ**: Gibt an, wie die Aufgabe zugewiesen wurde:

**Anfänglich**: Dem Benutzer wurde die Aufgabe ursprünglich zugewiesen.

**Weiterleiten**: Der ursprüngliche Aufgabenbesitzer hat die Aufgabe einem anderen Benutzer zugewiesen.

**Ablehnen**: Eine weitergeleitete Aufgabe wurde abgelehnt, oder eine Aufgabe wurde an eine Arbeitsliste zurückgegeben, ohne erledigt worden zu sein.

**Anfordern**: Der Benutzer hat die Aufgabe in einer freigegebenen Arbeitsliste angefordert.

**Eskalation**: Ein zuvor festgelegter Zeitraum (wie in der Benutzeraktion in Workbench festgelegt) ist ohne Benutzerinteraktion verstrichen, und die Aufgabe wurde einem anderen Benutzer zugewiesen..

**Besprechen**: Der Aufgabenbesitzer hat diese Aufgabe zur Besprechung an einen anderen Benutzer weitergeleitet, der das Formular öffnen, Daten speichern und die Anlagen und Notizen bearbeiten, jedoch nicht den Schritt abschließen darf. Der Benutzer muss die Aufgabe an den Aufgabenbesitzer zurückgeben, der sich mit dem Benutzer besprochen hat.

**Admin-Neuzuweisung**: Die Aufgabe wurde von einem Administrator neu zugewiesen.

**Zuweisungsdatum**: Das Datum und die Uhrzeit, zu der die Aufgabe dem Benutzer zugewiesen wurde.

### Zuweisen eines neuen Benutzers zu einer Aufgabe {#assigning-a-new-user-to-a-task}

Auf der Seite &quot;Benutzer zuweisen&quot;werden die Benutzer aufgelistet, die einer Aufgabe zugewiesen werden können. Sie greifen auf die Seite &quot;Benutzer zuweisen&quot;zu, indem Sie auf der Seite &quot;Aufgabenverlauf&quot;auf &quot;Neuen Benutzer zuweisen&quot;klicken.

1. Geben Sie im Feld &quot;Suchen nach&quot;auf der Seite &quot;Benutzer zuweisen&quot;einen Teil oder alle erforderlichen Benutzernamen oder E-Mail-Adresse ein.
1. Wählen Sie unter &quot;Verwenden&quot;den Eintrag &quot;Name&quot;oder &quot;E-Mail-Adresse&quot;und klicken Sie auf &quot;Suchen&quot;. Die Benutzer, die mit der Suche übereinstimmen, werden angezeigt.
1. Wählen Sie den Benutzer aus der Liste aus und klicken Sie auf OK. Die Seite &quot;Aufgabenverlauf&quot;wird mit der neuen Benutzerzuweisung angezeigt.
