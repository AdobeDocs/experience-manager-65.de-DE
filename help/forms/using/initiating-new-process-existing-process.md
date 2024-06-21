---
title: Starten eines neuen Prozesses mit vorhandenen Prozessdaten in AEM Forms Workspace
description: Erfahren Sie, wie Sie einen neuen Prozess mit vorhandenen Prozessdaten in AEM Forms Workspace starten können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 6fa97c06-9238-4444-b67f-983ef3b6fdc8
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 100%

---

# Starten eines neuen Prozesses mit vorhandenen Prozessdaten in AEM Forms Workspace{#initiating-a-new-process-with-existing-process-data-in-aem-forms-workspace}

Sie können einen neuen Prozess mit den Daten eines vorhandenen Prozesses initiieren. Das Initiieren eines neuen Prozesses auf der Grundlage vorhandener Prozessdaten ist erforderlich, wenn dasselbe Formular häufig verwendet werden muss, wobei sich der Inhalt geringfügig ändert, etwa bei Formularen für bezahlten Urlaub. Mithilfe dieser Funktion können Benutzende Zeit und Mühe sparen, insbesondere, wenn ein umfangreiches Formular für den Prozess ausgefüllt werden muss.

Zum Initiieren eines neuen Prozesses aus bestehenden Prozessdaten sind die folgenden Schritte erforderlich:

1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie unter „Tracking“ auf die Prozessinstanz, deren Daten verwendet werden sollen. Klicken Sie in der Ansicht des Prozessverlaufs im rechten Bereich auf die Zeile der Aufgabe, die dem Startpunkt entspricht.
   * Wählen Sie unter „Tracking“ eine Suchvorlage aus, um eine Liste der Prozessinstanzen anzuzeigen. Wählen Sie die Instanz aus, deren Daten verwendet werden sollen.
   * Wählen Sie auf der Registerkarte **[!UICONTROL Aufgabenliste]** die Aufgabe aus. Klicken Sie auf die Registerkarte **[!UICONTROL Verlauf]** und wählen Sie die Aufgabe aus, die die Prozessinstanz initiiert hat.

   ![Aufgabe auswählen](assets/start3_new.png) ![Aufgabe auswählen](assets/start1_new.png)

1. In der Aufgabenaktionssymbolleiste klicken Sie auf **[!UICONTROL Start]**. Ein adaptives Formular für die neue Prozessinstanz wird mit automatischer Vorbefüllung angezeigt.

1. Aktualisieren Sie die Daten wie erforderlich und klicken Sie auf **[!UICONTROL Abschließen]** oder die entsprechende Schaltfläche im Formular.
