---
title: Speichern von Formularen als Vorlagen
description: Erfahren Sie, wie Sie Vorlagen aus Formularen mit wiederholt erforderlichen Daten erstellen.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b97175fd-cc3d-457a-af11-1f8c83192eb7
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 26%

---

# Speichern von Formularen als Vorlagen {#save-forms-as-templates}

Wenn Benutzer ein Formular ausfüllen, bleiben die Eingaben in einige Felder manchmal gleich. In solchen Fällen können Sie die Felder ausfüllen, für die in jeder Instanz identische Werte erforderlich sind, und das Formular oder den Entwurf als Vorlage speichern. Jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, werden die angegebenen Felder bereits mit den in der Vorlage angegebenen Werten ausgefüllt. Auf diese Weise sparen Sie Zeit und Mühe beim Ausfüllen des Formulars.

Führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen: 

1. Öffnen Sie ein Formular und wählen Sie die Felder aus, für bei jeder Verwendung gleichbleibende Werte verwendet werden sollen, bzw. geben Sie diese Werte dort ein. Sie eine Anlage in die Vorlage einbeziehen, die normalerweise beim Ausfüllen des Formulars hinzugefügt wird.
1. Wählen Sie die **Als Vorlage speichern** ![save_as_template](assets/save_as_template.png)Symbol. Ein Dialogfeld, in dem Sie den Namen der Vorlage eingeben können, wird angezeigt.
1. Geben Sie den Namen der Vorlage an und wählen Sie **Speichern**. Die Vorlage wird im Vorlagenordner angezeigt.

   Wenn eine Vorlage mit demselben Namen vorhanden ist, wird ein Dialogfeld angezeigt, in dem Sie bestätigen können, dass die vorhandene Vorlage überschrieben wird. Um die vorhandene Vorlage durch eine neue Vorlage zu ersetzen, wählen Sie **Weiter** oder um die Vorlage mit einem anderen Namen zu speichern, wählen Sie **Abbrechen**.

Jetzt können Sie die gespeicherte Vorlage öffnen. Jedes Mal, wenn eine Vorlage geöffnet wird, wird ein neues Formular oder eine Aufgabe erstellt und das Formular zeigt die gespeicherten Daten und Optionen an. Mit Vorlagen können Sie die vorausgefüllten Daten bearbeiten, eine Anlage hinzufügen, als Entwurf speichern, die Aufgabe übermitteln oder andere Vorlagen erstellen. Vorlagen sind für Mobilgeräte spezifisch und werden nicht mit dem Adobe Experience Manager Forms-Server synchronisiert.

Sie können eine nicht mehr benötigte Vorlage auch löschen. Um eine Vorlage zu löschen, navigieren Sie zum Ordner &quot;templates&quot;, wählen die Auslassungspunkte aus und klicken Sie auf **Vorlage löschen**.

>[!NOTE]
>
>Eine Vorlage ist lokal verfügbar und wird nicht mit dem Server synchronisiert. Durch Löschen der lokalen Daten der App wird die Vorlage gelöscht.
