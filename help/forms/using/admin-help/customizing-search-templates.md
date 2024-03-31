---
title: Anpassen von Suchvorlagen
description: Sie können Suchvorlagen erstellen, die in Workspace verwendet werden sollen, um von den Seiten „Aufgaben“ und „Verfolgung“ aus nach Prozessinstanzen zu suchen. Außerdem können Sie vorhandene Suchvorlagen bearbeiten oder löschen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: bf69de86-2ca6-4d21-936c-07c1debacfa0
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 100%

---

# Anpassen von Suchvorlagen {#customizing-search-templates}

Sie können Suchvorlagen erstellen, die in Workspace verwendet werden sollen, um von den Seiten „Aufgaben“ und „Verfolgung“ aus nach Prozessinstanzen zu suchen. Außerdem können Sie vorhandene Suchvorlagen bearbeiten oder löschen.

Beim Erstellen oder Bearbeiten einer Suchvorlage können Sie das Layout und die Sortierreihenfolge der Suchergebnisse festlegen. Benutzende können diese Einstellungen jedoch ändern, wenn die Suchergebnisse in Workspace angezeigt werden.

Sie können ganz nach Bedarf eine beliebige Anzahl von Suchvorlagen erstellen.

>[!NOTE]
>
>Geben Sie beim Speichern einer Suchvorlage einen eindeutigen Namen an. Andernfalls ist es möglich, dass eine vorhandene Vorlage ohne Warnmeldung überschrieben wird.

## Erstellen einer einfachen Suchvorlage {#create-a-simple-search-template}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Workspace“ > „Suchvorlagen“.
1. Geben Sie auf der Registerkarte „Kennung“ im Feld „Suchvorlagenbeschreibung“ den Zweck der Vorlage an.
1. (Optional) Klicken Sie auf die Registerkarte „Kriterien“ und geben Sie die Suchkriterien für die Vorlage an.
1. Klicken Sie auf die Registerkarte „Speichern“, geben Sie einen eindeutigen Namen für die Vorlage ein und klicken Sie auf „Speichern“.

## Erstellen oder Bearbeiten einer Suchvorlage {#create-or-edit-a-search-template}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Workspace“ > „Suchvorlagen“.
1. (Optional) Wenn Sie eine vorhandene Vorlage bearbeiten oder eine bestehende Vorlage als Grundlage für eine neue Vorlage verwenden, wählen Sie die Vorlage aus der Liste der Suchvorlagen aus.
1. Geben Sie im Feld „Suchvorlagenbeschreibung“ den Verwendungszweck der Suchvorlage ein.
1. (Optional) Geben Sie im Feld „Benutzeranweisungen“ alle Anweisungen an, die bei der Verwendung der Vorlage hilfreich sein können. Diese Anweisungen werden in Workspace angezeigt, wenn eine Benutzerin oder ein Benutzer die Suchvorlage auswählt.
1. Klicken Sie auf die Registerkarte „Kriterien“. Hier können Sie Suchkriterien definieren. So fügen Sie Suchkriterien hinzu:

   * Wählen Sie oben auf der Registerkarte „Kriterien“ ein Prozess- oder Aufgabenelement aus.

     **Tipp**: *Wenn Sie zuvor das Element „Prozessname“ ausgewählt und einen Prozess angegeben haben, sind alle in diesem Prozess definierten Prozessvariablen ebenfalls zur Auswahl verfügbar.*

     **Tipp**: *IWenn Sie das Element „Aufgabe sichtbar“ auswählen, können Benutzer abgeschlossene Aufgaben aus den Suchergebnissen entfernen.*

     Die Suchkriterienfelder für das ausgewählte Element werden unten auf der Registerkarte „Kriterien“ angezeigt.

   * Füllen Sie unten auf der Registerkarte „Kriterien“ die entsprechenden Suchfelder für alle Prozesselemente, Aufgabenelemente und Prozessvariablen aus:

      * Wählen Sie einen relationalen Operator (z. B. „gleich“) aus der bereitgestellten Liste aus und geben Sie den Wert des Operanden im Feld daneben an.
      * (Optional) Damit Benutzende den Operandenwert in Workspace ändern können, aktivieren Sie „Dem Benutzer das Ändern des Operanden gestatten“.
      * (Optional) Damit Benutzende den Wert des relationalen Operators ändern können, aktivieren Sie „Dem Benutzer das Auswählen eines anderen relationalen Operators gestatten“. Wählen Sie in der angezeigten Liste die Operatoren aus, die für die Benutzerin oder den Benutzer verfügbar sein sollen.

     **Tipp**: *Wenn Sie den Prozessnamen als Element ausgewählt haben, können Sie auf das Symbol neben dem Operandenfeld klicken, um eine Liste anzuzeigen, in der Sie einen Prozess auswählen können, der auf dem Formular-Server ausgeführt wird. Nachdem Sie einen Vorgang ausgewählt haben, sind alle in diesem Prozess definierten Prozessvariablen im oberen Bereich der Registerkarte „Kriterien“ unter „Prozessvariablen“ verfügbar.*

     **Tipp**: *Ein Element der Suchvorlage kann gelöscht werden, indem Sie auf das Löschen-Symbol neben den Suchkriterien des Elements klicken.*

1. (Optional) Klicken Sie für jede in den Suchergebnissen anzuzeigende Spaltenüberschrift auf die Registerkarte „Layout“ und führen Sie folgende Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil, um es in die Liste „Anzuzeigende Spalten“ zu übernehmen.
   * Wählen Sie in der Liste „Anzuzeigende Spalten“ das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- oder Nach-unten-Pfeil´, um es an die gewünschte Position in der Spaltenreihenfolge zu verschieben. Die Spaltenüberschriften der Suchergebnisse werden in der hier aufgeführten Reihenfolge angezeigt.
   * (Optional) Um den Namen des Elements für die Spaltenüberschrift zu ändern, wählen Sie das Element in der Liste „Anzuzeigende Spalten“ aus und geben Sie den neuen Namen an.

   >[!NOTE]
   >
   >Das in der Suchvorlage angegebene Layout setzt die für Spaltenüberschriften in Workspace festgelegten Voreinstellungen der Benutzenden außer Kraft.

1. (Optional) Klicken Sie für jede Spalte, die in den Suchergebnissen sortiert werden soll, auf die Registerkarte „Sortierung“ und führen Sie folgende Schritte aus:

   * Wählen Sie ein Prozess- oder Aufgabenelement aus und klicken Sie auf den Pfeil, um es in die Liste „Sortierreihenfolge“ zu übernehmen.
   * Wählen Sie in der Liste „Sortierreihenfolge“ das Prozess- oder Aufgabenelement aus und klicken Sie auf den Nach-oben- bzw. Nach-unten-Pfeil, um es an die gewünschte Position in der Sortierreihenfolge zu verschieben. Die Spalten der Suchergebnisse werden auf Grundlage der Reihenfolge sortiert, in der sie hier aufgeführt sind.
   * (Optional) Um eine Spalte absteigend zu sortieren, aktivieren Sie das Kontrollkästchen neben dem jeweiligen Elementnamen. Ist das Kontrollkästchen nicht aktiviert, wird die Spalte in aufsteigender Reihenfolge sortiert.

1. Klicken Sie auf die Registerkarte „Speichern“.
1. (Optional) Geben Sie beim Erstellen einer Suchvorlage einen eindeutigen Namen an.  Falls Sie keinen eindeutigen Namen angeben, wird eventuell eine vorhandene Vorlage überschrieben.
1. Klicken Sie auf die Schaltfläche „Speichern“.

## Löschen einer Suchvorlage {#delete-a-search-template}

1. Wählen Sie auf der Registerkarte „Identifizierung“ einen Namen in der Liste „Suchvorlagenname“ aus.
1. Klicken Sie auf „Diese Vorlage löschen“ und dann auf „OK“.
