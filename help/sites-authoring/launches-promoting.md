---
title: Hochstufen von Launches
description: Sie stufen Launch-Seiten hoch, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: f59f12a2-ecd6-49cf-90ad-621719fe51bf
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Launches
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 100%

---

# Weiterleiten von Launches{#promoting-launches}

Sie müssen Launch-Seiten weiterleiten, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert. Beim Weiterleiten einer Launch-Seite stehen die folgenden Optionen zur Verfügung:

* Ob nur die aktuelle Seite oder der gesamte Launch weitergeleitet werden soll.
* Ob die untergeordneten Seiten der aktuellen Seite weitergeleitet werden sollen.
* Ob der vollständige Launch weitergeleitet werden soll oder nur Seiten, die geändert wurden.
* Ob der Launch nach der Weiterleitung gelöscht werden soll.

>[!NOTE]
>
>Nach dem Weiterleiten der Launch-Seiten zum Ziel (**Produktion**) können Sie die **Produktionsseiten** als Entität aktivieren (um den Prozess schneller zu gestalten). Fügen Sie die Seiten einem Workflow-Paket hinzu und verwenden Sie es als Payload für einen Workflow, der ein Paket mit Seiten aktiviert. Sie müssen das Workflow-Paket erstellen, bevor Sie den Launch weiterleiten. Siehe [Bearbeiten weitergeleiteter Seiten mit einem AEM-Workflow ](#processing-promoted-pages-using-aem-workflow)

>[!CAUTION]
>
>Ein einzelner Launch kann nicht gleichzeitig mehrfach weitergeleitet werden. Dies bedeutet, dass zwei gleichzeitig ausgeführte Weiterleitungen für denselben Launch einen Fehler verursachen können: `Launch could not be promoted` (zusammen mit Konfliktfehlern im Protokoll).

>[!CAUTION]
>
>Beim Weiterleiten von Launches für *geänderte* Seiten werden Anpassungen sowohl im Quell- als auch im Launch-Zweig berücksichtigt.

## Weiterleiten von Launch-Seiten {#promoting-launch-pages}

>[!NOTE]
>
>Dies umfasst die manuelle Aktion des Weiterleitens von Launch-Seiten, wenn nur eine Launch-Ebene vorhanden ist. Siehe:
>
>* [Weiterleiten eines verschachtelten Launches](#promoting-a-nested-launch), wenn sich in der Struktur mehrere Launches befinden.
>* [Launches – die Reihenfolge der Ereignisse](/help/sites-authoring/launches.md#launches-the-order-of-events) für weitere Informationen zur automatischen Weiterleitung und Veröffentlichung.
>

Sie können Launches über die Konsolen **Sites** oder **Launches** weiterleiten.

1. Öffnen Sie:

   * In der **Sites**-Konsole:

      1. Öffnen Sie die Leiste [Verweise](/help/sites-authoring/author-environment-tools.md#showingpagereferences) und wählen Sie die gewünschte Quellseite mithilfe des [Auswahlmodus](/help/sites-authoring/basic-handling.md) aus. (Oder wählen Sie die Seite aus und öffnen die Verweisleiste. Die Reihenfolge ist nicht wichtig.) Alle Verweise werden angezeigt.

      1. Wählen Sie **Launches** aus (z. B. „Launches (1)“), um eine Liste der spezifischen Launches anzuzeigen.
      1. Wählen Sie den gewünschten Launch aus, damit die verfügbaren Aktionen angezeigt werden.
      1. Wählen Sie **Launch bewerben** aus, um den Assistenten zu öffnen.

   * die **Launch**-Konsole:

      1. Wählen Sie den Launch aus (klicken Sie auf die Miniaturansicht).
      1. Wählen Sie **Bewerben** aus.

1. Im ersten Schritt können Sie folgende Optionen festlegen:

   * **Ziel**

      * **Launch nach der Veröffentlichung löschen**

   * **Umfang**

      * **Vollständigen Launch weiterleiten**
      * **Geänderte Seiten hochstufen**
      * **Aktuelle Seite hochstufen**
      * **Aktuelle Seite und Unterseiten weiterleiten**

   Wenn beispielsweise nur geänderte Seiten weitergeleitet werden sollen:

   ![launches-pd-06](assets/launches-pd-06.png)

   >[!NOTE]
   >
   >Dies behandelt einen einzelnen Launch. Falls Sie verschachtelte Launches haben, siehe [Hochstufen eines verschachtelten Launches](#promoting-a-nested-launch).

1. Klicken Sie auf **Weiter**, um fortzufahren.
1. Sie können die weiterzuleitenden Seiten überprüfen. Diese Überprüfung hängt vom ausgewählten Seitenbereich ab:

   ![Überprüfen von Seiten, die beworben werden sollen](assets/chlimage_1-102.png)

1. Wählen Sie **Bewerben** aus.

## Weiterleiten von Launch-Seiten bei der Bearbeitung {#promoting-launch-pages-when-editing}

Wenn Sie eine Launch-Seite bearbeiten, steht die Aktion **Launch bewerben** auch im Bereich **Seiteninformationen** zur Verfügung. Dadurch wird der Assistent geöffnet, um die benötigten Informationen zusammenzustellen.

![Launch bewerben](assets/chlimage_1-103.png)

>[!NOTE]
>
>Diese Option steht für einzelne und [verschachtelte Launches](#promoting-a-nested-launch) zur Verfügung.

## Weiterleiten eines verschachtelten Launches {#promoting-a-nested-launch}

Wenn Sie einen verschachtelten Launch erstellt haben, können Sie ihn wieder an jede der Quellen weiterleiten, auch an die Stammquelle (Produktion).

![Übersicht über das Weiterleiten eines verschachtelten Launches](assets/chlimage_1-104.png)

1. Wie beim [Erstellen eines verschachtelten Starts](#creatinganestedlaunchlaunchwithinalaunch) navigieren Sie entweder über die Konsole **Launches** oder die Leiste **Verweise** zum gewünschten Launch und wählen diesen aus.
1. Wählen Sie **Launch bewerben** aus, um den Assistenten zu öffnen.

1. Geben Sie die erforderlichen Details ein:

   * **Ziel**

      * **Ziel der Promotion** Sie können an eine beliebige Quelle weiterleiten.

      * **Launch nach der Veröffentlichung löschen** Nach der Promotion wird der ausgewählte Launch und alle darin enthaltenen Launches gelöscht.

   * **Bereich** Hier können Sie auswählen, ob der gesamte Launch weitergeleitet werden soll oder nur die Seiten, die bearbeitet wurden. Im zweiten Fall können Sie dann auswählen, welche Unterseiten einbezogen bzw. ausgeschlossen werden. Die Standardkonfiguration besteht darin, nur Seitenänderungen für die aktuelle Seite weiterzuleiten 

      * **Vollständigen Launch weiterleiten**
      * **Geänderte Seiten hochstufen**
      * **Aktuelle Seite hochstufen**
      * **Aktuelle Seite und Unterseiten weiterleiten**

   ![Einstellungen für das Bewerben eines Launches](assets/chlimage_1-105.png)

1. Wählen Sie **Weiter** aus.
1. Überprüfen Sie die Details, bevor Sie **Bewerben** auswählen:

   ![Details überprüfen und bewerben](assets/chlimage_1-106.png)

   >[!NOTE]
   >
   >Die aufgeführten Seiten hängen vom definierten **Anwendungsbereich** ab und möglicherweise den Seiten, die tatsächlich bearbeitet wurden.

1. Ihre Änderungen werden hochgestuft und in der Konsole **Launches** dargestellt:

   ![Launch-Konsole](assets/chlimage_1-107.png)

## Bearbeiten weitergeleiteter Seiten mit einem AEM-Workflow {#processing-promoted-pages-using-aem-workflow}

Verwenden Sie Workflow-Modelle, um Seiten von weitergeleiteten Launches massenweise zu verarbeiten:

1. Erstellen Sie ein Workflow-Paket.
1. Wenn Autorinnen und Autoren Launch-Seiten weiterleiten, speichern sie sie im Workflow-Paket.
1. Starten Sie ein Workflow-Modell mit dem Paket als Payload.

Um einen Workflow automatisch zu starten, wenn Seiten hochgestuft werden, [konfigurieren Sie einen Workflow-Launcher](/help/sites-administering/workflows-starting.md#workflows-launchers) für den Paketknoten.

Sie können z. B. automatisch Seitenaktivierungsanfragen generieren, wenn Autoren Launches-Seiten weiterleiten. Konfigurieren Sie einen Workflow-Starter, um den Aktivierungsanfrage-Workflow zu starten, wenn der Paketknoten geändert wurde.

![Workflow-Starter](assets/chlimage_1-108.png)
