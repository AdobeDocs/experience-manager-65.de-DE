---
title: Anpassen von Suchvorlagen
seo-title: Customizing search templates
description: Sie können Suchvorlagen erstellen, die in Workspace verwendet werden, um von den Seiten "Aufgaben"und "Verfolgung"aus nach Instanzen von Prozessen zu suchen. Sie können auch vorhandene Suchvorlagen bearbeiten oder löschen.
seo-description: You can create search templates to be used in Workspace to search for instances of processes from the To Do and Tracking pages. You can also edit or delete existing search templates.
uuid: 2043ba8a-07f0-4054-af3c-f3a14c2183ab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6e4b4dfa-3af5-4c21-a2a1-b90ef02d8514
exl-id: bf69de86-2ca6-4d21-936c-07c1debacfa0
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 19%

---

# Anpassen von Suchvorlagen {#customizing-search-templates}

Sie können Suchvorlagen erstellen, die in Workspace verwendet werden, um von den Seiten &quot;Aufgaben&quot;und &quot;Verfolgung&quot;aus nach Instanzen von Prozessen zu suchen. Sie können auch vorhandene Suchvorlagen bearbeiten oder löschen.

Beim Erstellen oder Bearbeiten einer Suchvorlage können Sie das Layout und die Sortierreihenfolge der Suchergebnisse festlegen. Benutzer können diese Einstellungen jedoch in Workspace ändern, nachdem die Suchergebnisse angezeigt wurden.

Sie können beliebig viele Suchvorlagen erstellen.

>[!NOTE]
>
>Beim Speichern einer Suchvorlage müssen Sie ihr einen eindeutigen Namen geben. Andernfalls kann eine vorhandene Vorlage ohne Warnmeldung überschrieben werden.

## Einfache Suchvorlage erstellen {#create-a-simple-search-template}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Workspace&quot;> &quot;Suchvorlagen&quot;.
1. Geben Sie auf der Registerkarte Identifizierung im Feld Suchvorlagenbeschreibung den Zweck der Vorlage an.
1. (Optional) Klicken Sie auf die Registerkarte Kriterien und geben Sie die Suchkriterien für die Vorlage an.
1. Klicken Sie auf die Registerkarte &quot;Speichern&quot;, geben Sie einen eindeutigen Namen für die Vorlage ein und klicken Sie auf &quot;Speichern&quot;.

## Erstellen oder Bearbeiten einer Suchvorlage {#create-or-edit-a-search-template}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Workspace&quot;> &quot;Suchvorlagen&quot;.
1. (Optional) Wenn Sie eine vorhandene Vorlage bearbeiten oder eine vorhandene Vorlage als Grundlage für eine neue Vorlage verwenden, wählen Sie die Vorlage aus der Liste Suchvorlagenname aus.
1. Geben Sie im Feld Suchvorlagenbeschreibung den Zweck der Vorlage an.
1. (Optional) Geben Sie im Feld &quot;Benutzeranweisungen&quot;alle Anweisungen ein, die bei der Verwendung der Vorlage hilfreich sein können. Diese Anweisungen werden in Workspace angezeigt, wenn ein Benutzer die Suchvorlage auswählt.
1. Klicken Sie auf die Registerkarte Kriterien . Hier definieren Sie ein oder mehrere Suchkriterien. Hinzufügen von Suchkriterien:

   * Wählen Sie oben auf der Registerkarte Kriterien ein Prozess- oder Aufgabenelement aus.

     **Tipp**: *Wenn Sie zuvor das Element „Prozessname“ ausgewählt und einen Prozess angegeben haben, sind alle in diesem Prozess definierten Prozessvariablen ebenfalls zur Auswahl verfügbar.*

     **Tipp**: *IWenn Sie das Element „Aufgabe sichtbar“ auswählen, können Benutzer abgeschlossene Aufgaben aus den Suchergebnissen entfernen.*

     Die Suchkriterienfelder für das ausgewählte Element werden unten auf der Registerkarte Kriterien angezeigt.

   * Füllen Sie für jedes Prozesselement, jedes Aufgabenelement und jede Prozessvariable, die Sie auswählen, die entsprechenden Suchfelder unten auf der Registerkarte &quot;Kriterien&quot;aus:

      * Wählen Sie einen relationalen Operator (z. B. &quot;gleich&quot;) aus der bereitgestellten Liste aus und geben Sie den Wert des Operanden im Feld daneben an.
      * (Optional) Damit Benutzer den Operandenwert in Workspace ändern können, aktivieren Sie die Option &quot;Allow The User To Change The Operand&quot;(Benutzer darf den Operand ändern).
      * (Optional) Damit Benutzer den relationalen Operator ändern können, aktivieren Sie die Option &quot;Allow The User to Select Other Relational Operator (Dem Benutzer erlauben, einen anderen relationalen Operator auszuwählen)&quot;. Wählen Sie in der angezeigten Liste die Benutzer aus, die für den Benutzer verfügbar sein sollen.

     **Tipp**: *Wenn Sie Prozessname als Element ausgewählt haben, können Sie auf das Symbol neben dem Operandenfeld klicken, um eine Liste anzuzeigen, in der Sie einen Prozess auswählen können, der auf dem Forms-Server ausgeführt wird. Nachdem Sie einen Vorgang ausgewählt haben, sind alle in diesem Prozess definierten Prozessvariablen im oberen Bereich der Registerkarte „Kriterien“ unter „Prozessvariablen“ verfügbar.*

     **Tipp**: *Ein Element der Suchvorlage kann gelöscht werden, indem Sie auf das Löschen-Symbol neben den Suchkriterien des Elements klicken.*

1. (Optional) Klicken Sie für jede Spaltenüberschrift, die in den Suchergebnissen angezeigt werden soll, auf die Registerkarte Layout und führen Sie die folgenden Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil, um es in die Liste „Anzuzeigende Spalten“ zu übernehmen.
   * Wählen Sie in der Liste „Anzuzeigende Spalten“ das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- oder Nach-unten-Pfeil´, um es an die gewünschte Position in der Spaltenreihenfolge zu verschieben. Die Spaltenüberschriften in den Suchergebnissen werden in der Reihenfolge angezeigt, in der sie hier aufgeführt sind.
   * (Optional) Um den Namen des Elements für die Spaltenüberschrift zu ändern, wählen Sie das Element aus der Liste Zu meldende Spalten aus und geben Sie den neuen Namen ein.

   >[!NOTE]
   >
   >Das in der Suchvorlage angegebene Layout setzt die Voreinstellungen des Benutzers für Spaltenüberschriften in Workspace außer Kraft.

1. (Optional) Klicken Sie für jede Spalte, die in den Suchergebnissen sortiert werden soll, auf die Registerkarte Sortierung und führen Sie die folgenden Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil, um es in die Liste „Sortierreihenfolge“ zu übernehmen.
   * Wählen Sie in der Liste &quot;Sortierreihenfolge&quot;das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- oder Nach-unten-Pfeil, um es an die gewünschte Position in der Sortierreihenfolge zu verschieben. Die Spalten in den Suchergebnissen werden nach der Reihenfolge sortiert, in der sie hier aufgeführt sind.
   * (Optional) Um eine Spalte in absteigender Reihenfolge zu sortieren, aktivieren Sie das Kontrollkästchen neben dem Elementnamen. Wenn das Kontrollkästchen nicht aktiviert ist, wird die Spalte in aufsteigender Reihenfolge sortiert.

1. Klicken Sie auf die Registerkarte Speichern .
1. (Optional) Wenn Sie eine Suchvorlage erstellen, geben Sie ihr einen eindeutigen Namen. Wenn Sie keinen eindeutigen Namen angeben, können Sie eine vorhandene Vorlage überschreiben.
1. Klicken Sie auf die Schaltfläche Speichern.

## Suchvorlage löschen {#delete-a-search-template}

1. Wählen Sie auf der Registerkarte Identifizierung einen Namen aus der Liste Suchvorlagenname aus.
1. Klicken Sie auf Vorlage löschen und dann auf OK.
