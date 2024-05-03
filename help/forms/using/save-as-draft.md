---
title: Speichern einer Aufgabe oder eines Formulars als Entwurf
description: Schritte zum Speichern eines Entwurfs für eine Aufgabe oder ein Formular in der AEM Forms-App
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b4a23b2e-ab18-402c-8dfa-2533ee692912
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 100%

---

# Speichern einer Aufgabe oder eines Formulars als Entwurf {#saving-a-task-or-form-as-a-draft}

Bei der Option „Als Entwurf speichern“ wird ein Schnappschuss einer Aufgabe oder eines Formulars zusammen mit den Daten im dazugehörigen Formular gespeichert. Sie können einen Entwurf auch aus einer Vorlage erstellen. Die Entwürfe werden auf dem Mobilgerät gespeichert und mit Adobe Experience Manager Forms-Server für den späteren Abruf synchronisiert.

Sie können das [Formular aktualisieren](/help/forms/using/working-with-form.md), [mit Fotos versehen](/help/forms/using/add-attachments.md) und Notizen machen. Wenn Sie ein Formular aktualisieren, wird empfohlen, es als Entwurf zu speichern. Wenn Sie ein ausgefülltes Formular zu einem späteren Zeitpunkt übermitteln möchten, kann ein gespeicherter Entwurf sehr hilfreich sein.

Um die Funktion „Als Entwurf speichern“ für Formulare, die im Forms-Portal gespeichert sind, zu aktivieren, siehe [Speichern eines HTML5-Formulars als Entwurf](/help/forms/using/saving-html5-form-draft.md).
Siehe [Entwürfe und Übermittlungen-Komponente](/help/forms/using/draft-submission-component.md), um die Übermittlung von adaptiven Formularen zu konfigurieren. (Nicht gültig für Formulare, die mit dem AEM Forms auf JEE-Server synchronisiert werden.)

Um einen Entwurf zu erstellen, öffnen Sie das Formular und wählen Sie **Als Entwurf speichern** ![save-as-draft](assets/save-as-draft.png) aus. Geben Sie den Namen des Entwurfs an und wählen Sie **Speichern** aus. Der Entwurf wird im Ordner „Entwürfe“ gespeichert und mit dem Server synchronisiert. Er wird im Ordner „Postausgang“ gespeichert, falls die App offline ist.

Falls Sie sich das entsprechende Formular anschließend aktualisieren, werden die Änderungen sofort übernommen. Wenn Sie die AEM Forms App mit dem AEM Forms-Server synchronisieren, wird der Entwurf auf den AEM Forms-Server hochgeladen. Zudem wird der Entwurf aus der Outbox in den Aufgaben- oder Entwurfsordner verschoben. Das Symbol „Bearbeiten“ wird daneben angezeigt.

Während Sie weiterhin mehrere Aufgaben und Startpunkte bearbeiten und speichern, werden diese Entwürfe gespeichert. Jedes Mal, wenn Sie Ihre App mit den AEM Forms-Server synchronisieren, wird der Entwurf auf dem Server gespeichert. Dadurch wird sichergestellt, dass Sie Ihre Entwürfe jederzeit in dem Zustand der letzten Speicherung wiederherstellen können. Wenn Sie beispielsweise die App neu installieren oder Ihr Mobilgerät austauschen, können Sie den Entwurf vom Server herunterladen.

## Löschen von Entwürfen {#delete-a-draft}

Der Ordner „Entwürfe“ enthält alle Entwürfe. Sie können die Option „Entwurf löschen“ verwenden, um die Entwürfe dauerhaft vom Mobilgerät bzw. Server zu löschen.

Die Option zum Löschen von Entwürfen, die mit einer Aufgabe erstellt wurden, ist nicht verfügbar. Beim Löschen eines Entwurfs, der aus einer Aufgabe erstellt wurde, wird die Aufgabe verlassen.

Sie können Entwürfe sowohl im Online- als auch im Offline-Modus verwerfen. Beim Verwerfen von Entwürfen im Offline-Modus werden die Entwürfe erst vom Server gelöscht, wenn die Verbindung zum Server wiederhergestellt ist.

Führen Sie die folgenden Schritte aus, um einen Entwurf zu löschen:

1. Navigieren Sie in der AEM Forms-App zu **Formulare**.
1. Wählen Sie **Entwürfe** aus der Dropdown-Liste neben „Suchen“. 
1. Bei einem Formular mit dem Bearbeitungssymbol ![edit-draft-app](assets/edit-draft-app.png) handelt es sich um einen Entwurf. Wählen Sie die Auslassungspunkte neben dem Entwurf aus.
1. Wählen Sie in den Optionen, die bei Auswahl der Auslassungspunkte angezeigt werden, die Option **Entwurf löschen** aus.
