---
title: Speichern von Formularen als Vorlagen
description: Informationen zum Erstellen von Vorlagen aus Formularen mit häufig benötigten Daten.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-app
exl-id: b97175fd-cc3d-457a-af11-1f8c83192eb7
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 95%
---
# Speichern von Formularen als Vorlagen {#save-forms-as-templates}

>[!NOTE]
>
>Die AEM Forms-App wird derzeit nicht mehr unterstützt. Bei Fragen oder Hilfe wenden Sie sich an [aemformsapp-android@adobe.com](mailto:aemformsapp-android@adobe.com).

Wenn Benutzende ein Formular ausfüllen, müssen Eingaben in bestimmten Feldern manchmal unbedingt übereinstimmen. In solchen Fällen können Sie die Felder ausfüllen, für die in allen Instanzen dieselben Werte benötigt werden, und das Formular bzw. den Entwurf als Vorlage speichern. Danach sind die angegebenen Felder jedes Mal, wenn Sie eine Instanz der Vorlage erstellen, bereits mit den Werten aus der Vorlage ausgefüllt. Dies spart Zeit und Mühe beim Ausfüllen des Formulars.

Führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen:

1. Öffnen Sie ein Formular und wählen Sie die Felder aus, für bei jeder Verwendung gleichbleibende Werte verwendet werden sollen, bzw. geben Sie diese Werte dort ein. Sie eine Anlage in die Vorlage einbeziehen, die normalerweise beim Ausfüllen des Formulars hinzugefügt wird.
1. Wählen Sie das Symbol **Als Vorlage speichern** ![save_as_template](assets/save_as_template.png) aus. Ein Dialogfeld, in dem Sie den Namen der Vorlage eingeben können, wird angezeigt.
1. Geben Sie den Namen der Vorlage ein und wählen Sie **Speichern** aus. Die Vorlage wird im Vorlagenordner angezeigt.

   Wenn eine Vorlage mit demselben Namen vorhanden ist, wird ein Dialogfeld angezeigt, in dem Sie bestätigen müssen, dass die vorhandene Vorlage überschrieben werden soll. Um die vorhandene Vorlage durch die neue Vorlage zu ersetzen, wählen Sie **Weiter** aus, oder wählen Sie **Abbrechen** aus, um die Vorlage unter einem anderen Namen zu speichern.

Jetzt können Sie die gespeicherte Vorlage öffnen. Jedes Mal, wenn eine Vorlage geöffnet wird, wird ein neues Formular oder eine Aufgabe erstellt, und das Formular zeigt die gespeicherten Daten und Optionen an. Mit Vorlagen können Sie die vorausgefüllten Daten bearbeiten, eine Anlage hinzufügen, als Entwurf speichern, die Aufgabe übermitteln oder andere Vorlagen erstellen. Vorlagen sind für Mobilgeräte spezifisch und werden nicht mit dem Adobe Experience Manager-Formular-Server synchronisiert.

Eine nicht mehr benötigte Vorlage kann gelöscht werden. Um eine Vorlage zu löschen, navigieren Sie zum Vorlagenordner, wählen Sie das Auslassungszeichen und anschließend **Vorlage löschen** aus.

>[!NOTE]
>
>Eine Vorlage ist lokal verfügbar, wird jedoch nicht mit dem Server synchronisiert. Durch Löschen der lokalen Daten der App wird die Vorlage gelöscht.
