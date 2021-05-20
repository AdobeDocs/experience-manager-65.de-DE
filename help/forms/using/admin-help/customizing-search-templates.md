---
title: Suchvorlagen anpassen
seo-title: Suchvorlagen anpassen
description: Sie können Suchvorlagen erstellen, die in Workspace verwendet werden sollen, um von den Seiten „Aufgaben“ und „Verfolgung“ aus nach Prozessinstanzen zu suchen. Außerdem können Sie vorhandene Suchvorlagen bearbeiten oder löschen.
seo-description: Sie können Suchvorlagen erstellen, die in Workspace verwendet werden sollen, um von den Seiten „Aufgaben“ und „Verfolgung“ aus nach Prozessinstanzen zu suchen. Außerdem können Sie vorhandene Suchvorlagen bearbeiten oder löschen.
uuid: 2043ba8a-07f0-4054-af3c-f3a14c2183ab
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6e4b4dfa-3af5-4c21-a2a1-b90ef02d8514
exl-id: bf69de86-2ca6-4d21-936c-07c1debacfa0
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 88%

---

# Suchvorlagen anpassen {#customizing-search-templates}

Sie können Suchvorlagen erstellen, die in Workspace verwendet werden sollen, um von den Seiten „Aufgaben“ und „Verfolgung“ aus nach Prozessinstanzen zu suchen. Außerdem können Sie vorhandene Suchvorlagen bearbeiten oder löschen.

Beim Erstellen oder Bearbeiten einer Suchvorlagen können Sie das Layout und die Sortierreihenfolge der Suchergebnisse festlegen. Sie können diese Einstellungen jedoch im Anschluss an die Anzeige der Suchergebnisse in Workspace ändern.

Sie können ganz nach Bedarf beliebig viele Suchvorlagen erstellen.

>[!NOTE]
>
>Geben Sie beim Speichern einer Suchvorlage einen eindeutigen Namen an. Andernfalls könnte eine vorhandene Vorlage ohne Warnmeldung überschrieben werden.

## Eine einfache Suchvorlage erstellen {#create-a-simple-search-template}

1. Klicken Sie in Administration Console auf „Dienste“ > „ Workspace “ > „Suchvorlagen“.
1. Geben Sie auf der Registerkarte „Kennung“ im Feld „Suchvorlagenbeschreibung“ den Zweck der Vorlage an.
1. (Optional) Klicken Sie auf die Registerkarte „Kriterien“ und geben Sie die Suchkriterien für die Vorlage an.
1. Klicken Sie auf die Registerkarte „Speichern“, geben Sie einen eindeutigen Namen für die Vorlage ein und klicken Sie auf „Speichern“.

## Suchvorlagen erstellen oder bearbeiten  {#create-or-edit-a-search-template}

1. Klicken Sie in Administration Console auf „Dienste“ > „ Workspace “ > „Suchvorlagen“
1. (Optional) Wenn Sie eine vorhandene Vorlage bearbeiten oder eine bestehende Vorlage als Grundlage für eine neue Vorlage verwenden, wählen Sie die Vorlage aus der Liste der Suchvorlagen aus.
1. Geben Sie im Feld „Suchvorlagenbeschreibung“ den Verwendungszweck der Suchvorlage ein.
1. (Optional) Geben Sie im Feld „Benutzeranweisungen“ alle Anweisungen an, die bei der Verwendung der Suchvorlage hilfreich sein können. Diese Anweisungen werden in Workspace angezeigt, wenn ein Benutzer die Suchvorlage auswählt.
1. Klicken Sie auf die Registerkarte „Kriterien“. Hier können Sie Suchkriterien definieren. Hinzufügen von Suchkriterien:

   * Wählen Sie oben in der Registerkarte „Kriterien“ ein Prozess- oder Aufgabenelement aus.

      **Tipp**:  *Wenn Sie zuvor das Element &quot;Process Name&quot;ausgewählt und einen Prozess angegeben haben, können auch alle in diesem Prozess definierten Prozessvariablen ausgewählt werden.*

      **Tipp**:  *Wenn Sie das Element &quot;Aufgabe eingeblendet&quot;auswählen, können Benutzer abgeschlossene Aufgaben aus den Suchergebnissen entfernen.*

      Die Suchkriterienfelder für das ausgewählte Element werden am unteren Rand der Registerkarte angezeigt.

   * Füllen Sie für alle Prozesselemente, Aufgabenelemente und Prozessvariablen die entsprechenden Suchfelder unten auf der Registerkarte „Kriterien“ aus:

      * Wählen Sie einen Vergleichsoperator (z. B. „gleich“) aus der bereitgestellten Liste aus und geben Sie den Wert des Operanden im Feld daneben an.
      * (Optional) Damit Benutzer den Operandenwert in Workspace ändern können, aktivieren Sie „Dem Benutzer das Ändern des Operanden gestatten“.
      * (Optional) Damit Benutzer den Wert des relationalen Operators in Workspace ES ändern können, aktivieren Sie „Dem Benutzer das Auswählen eines anderen relationalen Operators gestatten“. Wählen Sie in der angezeigten Liste die Operatoren, die für den Benutzer verfügbar sein sollen.

      **Tipp**:  *Wenn Sie Prozessname als Element ausgewählt haben, können Sie auf das Symbol neben dem Operandenfeld klicken, um eine Liste anzuzeigen, in der Sie einen Prozess auswählen können, der auf dem Formularserver ausgeführt wird. Nachdem Sie einen Vorgang ausgewählt haben, sind alle in diesem Prozess definierten Prozessvariablen im oberen Bereich der Registerkarte „Kriterien“ unter „Prozessvariablen“ verfügbar.*

      **Tipp**:  *Sie können ein Element aus der Suchvorlage löschen, indem Sie auf das Symbol Löschen neben den Suchkriterien des Elements klicken.*


1. (Optional) Klicken Sie für jede Spaltenüberschrift, die in den Suchergebnissen angezeigt werden soll, auf die Registerkarte „Layout“ und führen Sie folgende Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil  , um es in die Liste „Anzuzeigende Spalten“ zu übernehmen.
   * Wählen Sie in der Liste „Anzuzeigende Spalten“ das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- oder Nach-unten-Pfeil´ , um es an die gewünschte Position in der Spaltenreihenfolge zu verschieben. Die Spaltenüberschriften der Suchergebnisse werden in der hier aufgeführten Reihenfolge angezeigt.
   * (Optional) Wählen Sie zum Ändern des Namens des Elements für die Spaltenüberschrift das Element in der Liste „Anzuzeigende Spalten“ aus und geben Sie den neuen Namen an.

   >[!NOTE]
   >
   >Das in der Suchvorlage angegebene Layout setzt die für Spaltenüberschriften in Workspace festgelegten Voreinstellungen des Benutzers außer Kraft.

1. (Optional) Klicken Sie für jede Spalte, die in den Suchergebnissen sortiert werden soll, auf die Registerkarte „Sortierung“ und führen Sie folgende Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil  , um es in die Liste „Sortierreihenfolge“ zu übernehmen.
   * Wählen Sie in der Liste „Sortierreihenfolge“ das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- oder Nach-unten-Pfeil, um es an die gewünschte Position in der Sortierreihenfolge zu verschieben. Die Spalten der Suchergebnisse werden auf Grundlage der Reihenfolge, in der sie hier aufgeführt sind, sortiert.
   * (Optional) Aktivieren Sie zum absteigenden Sortieren einer Spalte das Kontrollkästchen neben dem jeweiligen Elementnamen. Ist das Kontrollkästchen nicht aktiviert, wird in die Spalte in aufsteigender Reihenfolge sortiert.

1. Klicken Sie auf die Registerkarte „Speichern“.
1. (Optional) Geben Sie beim Erstellen einer neuen Suchvorlage einen eindeutigen Namen an. Falls Sie keinen eindeutigen Namen angeben, wird eventuell eine vorhandene Vorlage überschrieben.
1. Klicken Sie auf die Schaltfläche „Speichern“.

## Eine Suchvorlage löschen  {#delete-a-search-template}

1. Wählen Sie auf der Registerkarte „Kennung“ einen Namen in der Liste „Suchvorlagenname“ aus.
1. Klicken Sie auf „Diese Vorlage löschen“ und dann auf „OK“.
