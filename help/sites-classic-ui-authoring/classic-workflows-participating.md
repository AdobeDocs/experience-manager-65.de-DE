---
title: Teilnehmen an Workflows
description: Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt eine Benutzerin bzw. einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 2f1a3a73-7a20-48c7-8f3e-54252f5fb71c
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 97%

---

# Teilnehmen an Workflows{#participating-in-workflows}

Workflows enthalten normalerweise Schritte, bei denen eine Person eine Aktivität auf einer Seite oder in einem Asset ausführen muss. Der Workflow wählt eine Benutzerin bzw. einen Benutzer oder eine Gruppe aus, um die Aktivität auszuführen, und weist dieser Person oder Gruppe ein Arbeitselement zu.

## Verarbeiten Ihrer Arbeitselemente {#processing-your-work-items}

Sie können die folgenden Aktionen ausführen, um ein Arbeitselement zu bearbeiten:

* **Fertig stellen**

  Sie können ein Element abschließen, damit der Workflow mit dem nächsten Schritt fortfahren kann.

* **Delegieren**

  Wenn Ihnen ein Schritt zugewiesen wurde, Sie jedoch aus irgendeinem Grund die Aktion nicht ausführen können, können Sie den Schritt an eine andere Person oder Gruppe delegieren.

  An welche Benutzenden delegiert werden kann, hängt davon ab, wem das Arbeitselement zugewiesen wurde:

   * Wenn das Arbeitselement einer Gruppe zugewiesen wurde, sind die Gruppenmitglieder verfügbar.
   * Wenn das Arbeitselement einer Gruppe zugewiesen und dann an einen Benutzer delegiert wurde, sind die Gruppenmitglieder und die Gruppe verfügbar.
   * Wenn das Arbeitselement einem einzelnen Benutzer zugewiesen wurde, kann es nicht delegiert werden.

* **Schritt zurück**

  Wenn Sie erkennen, dass ein Schritt oder eine Reihe von Schritten wiederholt werden muss, können Sie zu einem vorherigen Schritt zurückkehren. Auf diese Weise können Sie einen früheren Schritt im Workflow zur erneuten Verarbeitung auswählen. Der Workflow kehrt zu dem von Ihnen angegebenen Schritt zurück und fährt dann von dort fort.

## Teilnehmen an einem Workflow {#participating-in-a-workflow}

### Benachrichtigungen über zugewiesene Workflow-Aktionen {#notifications-of-assigned-workflow-actions}

Wenn Ihnen ein Arbeitselement zugewiesen wird (z. B. **Inhalte genehmigen**), werden verschiedene Warnungen und/oder Benachrichtigungen angezeigt:

* Die Spalte **Status** der Websites-Konsole zeigt an, wenn eine Seite in einem Workflow enthalten ist:

  ![workflowstatus-1](assets/workflowstatus-1.png)

* Wenn Ihnen oder einer Gruppe, der Sie angehören, ein Arbeitselement im Rahmen eines Workflows zugewiesen wird, wird das Arbeitselement in Ihrem AEM-Workflow-Posteingang angezeigt.

  ![workflowinbox](assets/workflowinbox.png)

### Fertigstellen eines Teilnehmerschritts {#completing-a-participant-step}

Nachdem Sie die angegebene Aktion abgeschlossen haben, können Sie das Arbeitselement fertig stellen, damit der Workflow fortgesetzt wird. Gehen Sie folgendermaßen vor, um das Arbeitselement abzuschließen.

1. Wählen Sie den Workflow-Schritt aus und klicken Sie in der oberen Navigationsleiste auf die Schaltfläche **Fertig stellen**.
1. Wählen Sie im angezeigten Dialogfeld die Option **Nächster Schritt** aus. Damit ist der Schritt gemeint, der als nächster ausgeführt werden soll. Eine Dropdown-Liste zeigt alle entsprechenden Ziele an. Sie können auch einen **Kommentar** eingeben.

   ![workflowcomplete](assets/workflowcomplete.png)

   Die Anzahl der aufgeführten Schritte hängt vom Design des Workflow-Modells ab.

1. Klicken Sie auf **OK**, um die Aktion zu bestätigen.

### Delegieren eines Teilnehmerschritts {#delegating-a-participant-step}

Gehen Sie folgendermaßen vor, um ein Arbeitselement zu delegieren.

1. Klicken Sie in der oberen Navigationsleiste auf die Schaltfläche **Delegieren**.
1. Wählen Sie im Dialogfeld mithilfe der Dropdown-Liste den **Benutzer** aus, an den das Arbeitselement delegiert wird. Sie können auch einen **Kommentar** hinzufügen.

   ![workflowdelegate](assets/workflowdelegate.png)

1. Klicken Sie auf **OK**, um die Aktion zu bestätigen.

### Wechseln zu einem vorherigen Teilnehmerschritt {#performing-step-back-on-a-participant-step}

Gehen Sie wie folgt vor, um einen Schritt zurückzugehen.

1. Klicken Sie in der oberen Navigationsleiste auf die Schaltfläche „Schritt zurück“.
1. Wählen Sie im angezeigten Dialogfeld einen Schritt unter „Vorheriger Schritt“ aus. Dies ist der Schritt, der als nächster ausgeführt werden soll (wobei es sich natürlich um einen Schritt handelt, der weiter vorne im Workflow steht). Eine Dropdown-Liste zeigt alle entsprechenden Ziele an.

   ![screen_shot_2018-08-10at155325](assets/screen_shot_2018-08-10at155325.jpg)

1. Klicken Sie auf „OK“, um die Aktion zu bestätigen.
