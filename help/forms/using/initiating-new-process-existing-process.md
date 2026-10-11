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
source-wordcount: '239'
ht-degree: 94%
---
# Starten eines neuen Prozesses mit vorhandenen Prozessdaten in AEM Forms Workspace{#initiating-a-new-process-with-existing-process-data-in-aem-forms-workspace}

Sie können einen neuen Prozess mit den Daten eines vorhandenen Prozesses initiieren. Das Initiieren eines neuen Prozesses auf der Grundlage vorhandener Prozessdaten ist erforderlich, wenn dasselbe Formular häufig verwendet werden muss, wobei sich der Inhalt geringfügig ändert, etwa bei Formularen für bezahlten Urlaub. Mithilfe dieser Funktion können Benutzende Zeit und Mühe sparen, insbesondere, wenn ein umfangreiches Formular für den Prozess ausgefüllt werden muss.

Im Folgenden werden die Schritte zum Initiieren eines neuen Prozesses aus vorhandenen Prozessdaten beschrieben: -

1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie unter „Tracking“ auf die Prozessinstanz, deren Daten verwendet werden sollen. Klicken Sie in der Ansicht des Prozessverlaufs im rechten Bereich auf die Zeile der Aufgabe, die dem Startpunkt entspricht.
   * Wählen Sie unter „Tracking“ eine Suchvorlage aus, um eine Liste der Prozessinstanzen anzuzeigen. Wählen Sie die Instanz aus, deren Daten verwendet werden sollen.
   * Wählen Sie auf der Registerkarte **[!UICONTROL Aufgabenliste]** die Aufgabe aus. Klicken Sie auf die Registerkarte **[!UICONTROL Verlauf]** und wählen Sie die Aufgabe aus, die die Prozessinstanz initiiert hat.

   ![Aufgabe auswählen](assets/start3_new.png) ![Aufgabe auswählen](assets/start1_new.png)

1. In der Aufgabenaktionssymbolleiste klicken Sie auf **[!UICONTROL Start]**. Ein adaptives Formular für die neue Prozessinstanz wird mit automatischer Vorbefüllung angezeigt.

1. Aktualisieren Sie die Daten wie erforderlich und klicken Sie auf **[!UICONTROL Abschließen]** oder die entsprechende Schaltfläche im Formular.
