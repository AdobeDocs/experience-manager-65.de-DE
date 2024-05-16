---
title: Speichern von Formularen als Vorlagen
description: Informationen zum Erstellen von Vorlagen aus Formularen mit häufig benötigten Daten.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b97175fd-cc3d-457a-af11-1f8c83192eb7
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '326'
ht-degree: 100%

---

# Speichern von Formularen als Vorlagen {#save-forms-as-templates}

Wenn Benutzende ein Formular ausfüllen, müssen Eingaben in bestimmten Feldern manchmal unbedingt übereinstimmen. In solchen Fällen können Sie die Felder ausfüllen, für die in allen Instanzen dieselben Werte benötigt werden, und das Formular bzw. den Entwurf als Vorlage speichern. Danach sind die angegebenen Felder jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, bereits mit den Werten aus der Vorlage ausgefüllt. Dies spart Zeit und Mühe beim Ausfüllen des Formulars.

Führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen: 

1. Öffnen Sie ein Formular und wählen Sie die Felder aus, für bei jeder Verwendung gleichbleibende Werte verwendet werden sollen, bzw. geben Sie diese Werte dort ein. Sie eine Anlage in die Vorlage einbeziehen, die normalerweise beim Ausfüllen des Formulars hinzugefügt wird.
1. Wählen Sie das Symbol **Als Vorlage speichern** ![save_as_template](assets/save_as_template.png) aus.  Ein Dialogfeld, in dem Sie den Namen der Vorlage eingeben können, wird angezeigt.
1. Geben Sie den Namen der Vorlage ein und wählen Sie **Speichern** aus. Die Vorlage wird im Vorlagenordner angezeigt.

   Wenn eine Vorlage mit demselben Namen vorhanden ist, wird ein Dialogfeld angezeigt, in dem Sie bestätigen müssen, dass die vorhandene Vorlage überschrieben werden soll.  Um die vorhandene Vorlage durch die neue Vorlage zu ersetzen, wählen Sie **Weiter** aus, oder wählen Sie **Abbrechen** aus, um die Vorlage unter einem anderen Namen zu speichern.

Jetzt können Sie die gespeicherte Vorlage öffnen.  Jedes Mal, wenn eine Vorlage geöffnet wird, wird ein neues Formular oder eine Aufgabe erstellt, und das Formular zeigt die gespeicherten Daten und Optionen an.  Mit Vorlagen können Sie die vorausgefüllten Daten bearbeiten, eine Anlage hinzufügen, als Entwurf speichern, die Aufgabe übermitteln oder andere Vorlagen erstellen. Vorlagen sind für Mobilgeräte spezifisch und werden nicht mit dem Adobe Experience Manager-Formular-Server synchronisiert.

Eine nicht mehr benötigte Vorlage kann gelöscht werden.  Um eine Vorlage zu löschen, navigieren Sie zum Vorlagenordner, wählen Sie das Auslassungszeichen und anschließend **Vorlage löschen** aus.

>[!NOTE]
>
>Eine Vorlage ist lokal verfügbar, wird jedoch nicht mit dem Server synchronisiert.  Durch Löschen der lokalen Daten der App wird die Vorlage gelöscht.
