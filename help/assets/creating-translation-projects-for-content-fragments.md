---
title: Erstellen von Übersetzungsprojekten für Inhaltsfragmente
description: Erfahren Sie, wie Sie Inhaltsfragmente in Adobe Experience Manager übersetzen.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
feature: Content Fragments
role: User, Admin
exl-id: 19bb58da-8220-404e-bddb-34be94a3a7d7
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 100%

---

# Erstellen von Übersetzungsprojekten für Inhaltsfragmente {#creating-translation-projects-for-content-fragments}

Zusätzlich zu Assets unterstützt Adobe Experience Manager (AEM) Assets Sprachkopie-Workflows für [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) (einschließlich Varianten). Um Sprachkopie-Workflows auf Inhaltsfragmenten auszuführen, ist keine zusätzliche Optimierung erforderlich. In jedem Workflow wird das gesamte Inhaltsfragment zur Übersetzung gesendet.

Die Workflow-Typen, die Sie bei Inhaltsfragmenten ausführen können, entsprechen den Workflow-Typen, die Sie für Assets ausführen können. Die Optionen, die bei jedem Workflow-Typ verfügbar sind, stimmen zudem mit den Optionen überein, die unter den entsprechenden Workflow-Typen für Assets verfügbar sind.

Sie können die folgenden Typen von Sprachkopie-Workflows bei Inhaltsfragmenten ausführen:

**Erstellen und übersetzen**

In diesem Workflow wird das zu übersetzende Inhaltsfragment in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Darüber hinaus wird, abhängig von den gewählten Optionen, ein Übersetzungsprojekt für die Inhaltsfragmente in der Projektekonsole erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald das Übersetzungsprojekt erstellt wurde.

**Aktualisieren von Sprachkopien**

Wenn das Quellinhaltsfragment aktualisiert oder geändert wird, muss das entsprechende Gebietsschema/das sprachspezifische Inhaltsfragment erneut übersetzt werden. Der Workflow „Sprachkopien aktualisieren“ übersetzt eine zusätzliche Gruppe von Inhaltsfragmenten und schließt diese in einer Sprachkopie für ein bestimmtes Gebietsschema ein. In diesem Fall werden die übersetzten Inhaltsfragmente dem Zielordner hinzugefügt, der bereits zuvor übersetzte Inhaltsfragmente enthält.

## Workflow für das Erstellen und Übersetzen {#create-and-translate-workflow}

Der Workflow für das Erstellen und Übersetzen umfasst die folgenden Optionen. Die mit der jeweiligen Option verbundenen Verfahrensschritte ähneln denen, die mit der entsprechenden Option für Assets verbunden sind.

* Nur Struktur erstellen: Verfahrensschritte finden Sie unter [Erstellen einer Struktur nur für Assets](translation-projects.md#create-structure-only).
* Übersetzungsprojekt erstellen: Verfahrensschritte finden Sie unter [Erstellen eines Übersetzungsprojekts für Assets](translation-projects.md#create-a-new-translation-project).
* Hinzufügen zu vorhandenem Übersetzungsprojekt: Verfahrensschritte finden Sie unter [Hinzufügen zu einem vorhandenen Übersetzungsprojekt für Assets](translation-projects.md#add-to-existing-translation-project).

## Workflow zum Aktualisieren von Sprachkopien {#update-language-copies-workflow}

Der Workflow zum Aktualisieren der Sprachkopien umfasst die folgenden Optionen. Die mit der jeweiligen Option verbundenen Verfahrensschritte ähneln denen, die mit der entsprechenden Option für Assets verbunden sind.

* Übersetzungsprojekt erstellen: Verfahrensschritte finden Sie unter [Erstellen eines Übersetzungsprojekts für Assets](translation-projects.md#create-a-new-translation-project) (Update-Workflow).
* Hinzufügen zu vorhandenem Übersetzungsprojekt: Verfahrensschritte finden Sie unter [Hinzufügen zu einem vorhandenen Übersetzungsprojekt für Assets](translation-projects.md#add-to-existing-translation-project) (Update-) Workflow.

Sie können auch temporäre Sprachkopien für Fragmente erstellen, ähnlich wie Sie temporäre Kopien für Assets erstellen. Weitere Informationen finden Sie unter [Erstellen temporärer Sprachkopien für Assets](translation-projects.md#creating-temporary-language-copies).

## Übersetzen von Fragmenten mit gemischten Medien {#translating-mixed-media-fragments}

In AEM können Sie Inhaltsfragmente übersetzen, die unterschiedliche Arten von Medien-Assets und Sammlungen enthalten. Wenn Sie ein Inhaltsfragment übersetzen, das Inline-Assets enthält, werden die übersetzten Kopien dieser Assets im Zielsprachstamm gespeichert.

Wenn das Inhaltsfragment eine Sammlung umfasst, werden die darin enthaltenen Assets zusammen mit dem Inhaltsfragment übersetzt. Die übersetzten Kopien der Assets werden in dem jeweiligen Zielsprachstamm an einem Speicherort gespeichert, der dem physischen Speicherort der Quell-Assets unter dem Ausgangssprachstamm entspricht.

Um Inhaltsfragmente zu übersetzen, die gemischte Medien enthalten, bearbeiten Sie zunächst das standardmäßige Übersetzungs-Framework, um die Übersetzung von mit Inhaltsfragmenten verknüpften Inline-Assets und Sammlungen zu ermöglichen.

1. Klicken Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools > Bereitstellung > Cloud-Services]**.
1. Klicken Sie unter **[!UICONTROL Adobe Marketing Cloud]** in **[!UICONTROL Übersetzungsintegration]** auf **[!UICONTROL Konfigurationen anzeigen]**.

   ![chlimage_1-444](assets/chlimage_1-444.png)

1. Klicken Sie in der Liste der verfügbaren Konfigurationen auf **[!UICONTROL Standardkonfiguration (Konfiguration für Übersetzungsintegration)]**, um die Seite **[!UICONTROL Standardkonfiguration]** zu öffnen.

   ![chlimage_1-445](assets/chlimage_1-445.png)

1. Klicken Sie in der Symbolleiste auf **[!UICONTROL Bearbeiten]**, um das Dialogfeld **[!UICONTROL Übersetzungskonfiguration]** anzuzeigen.

   ![chlimage_1-446](assets/chlimage_1-446.png)

1. Navigieren Sie zu der Registerkarte **[!UICONTROL Assets]** und wählen Sie aus der Liste **[!UICONTROL Inhaltsfragment-Assets übersetzen]** die Option **[!UICONTROL Eingebundene Medien-Assets und zugeordnete Sammlungen]** aus. Klicken Sie auf **[!UICONTROL OK]**, um die Änderungen zu speichern.

   ![chlimage_1-447](assets/chlimage_1-447.png)

1. Öffnen Sie aus dem englischen Stammordner ein Inhaltsfragment.

   ![chlimage_1-448](assets/chlimage_1-448.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Asset einfügen]**.

   ![chlimage_1-449](assets/chlimage_1-449.png)

1. Fügen Sie ein Asset in das Inhaltsfragment ein.

   ![Einfügen eines Assets in ein Inhaltsfragment](assets/column-view.png)

1. Klicken Sie auf das Symbol **[!UICONTROL Inhalt verknüpfen]**.

   ![chlimage_1-451](assets/chlimage_1-451.png)

1. Klicken Sie auf **[!UICONTROL Inhalt verknüpfen]**.

   ![chlimage_1-452](assets/chlimage_1-452.png)

1. Wählen Sie eine Sammlung aus und fügen Sie sie in das Inhaltsfragment ein. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![chlimage_1-453](assets/chlimage_1-453.png)

1. Wählen Sie das Inhaltsfragment aus und klicken Sie auf das Symbol **[!UICONTROL GlobalNav]**.
1. Wählen Sie im Menü die Option **[!UICONTROL Verweise]** aus, um das Bedienfeld **[!UICONTROL Verweise]** anzuzeigen.

   ![chlimage_1-454](assets/chlimage_1-454.png)

1. Klicken Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**, um die Sprachkopien anzuzeigen.

   ![chlimage_1-455](assets/chlimage_1-455.png)

1. Klicken Sie im unteren Bereich des Bedienfelds auf **[!UICONTROL Erstellen und übersetzen]**, um das Dialogfeld **[!UICONTROL Erstellen und übersetzen]** anzuzeigen.

   ![chlimage_1-456](assets/chlimage_1-456.png)

1. Wählen Sie in der Liste **[!UICONTROL Zielsprachen]** die Zielsprache aus.

   ![chlimage_1-457](assets/chlimage_1-457.png)

1. Wählen Sie in der Liste **[!UICONTROL Projekt]** den Übersetzungsprojekttyp aus.

   ![chlimage_1-458](assets/chlimage_1-458.png)

1. Geben Sie im Feld **[!UICONTROL Projekttitel]** den Titel des Projekts ein und klicken Sie dann auf **Erstellen**.

   ![chlimage_1-459](assets/chlimage_1-459.png)

1. Navigieren Sie zur **[!UICONTROL Projekte-Konsole]** und öffnen Sie den Projektordner für das von Ihnen erstellte Übersetzungsprojekt.

   ![chlimage_1-460](assets/chlimage_1-460.png)

1. Klicken Sie auf die Projektkachel, um die Seite mit den Projektdetails zu öffnen.

   ![chlimage_1-461](assets/chlimage_1-461.png)

1. Überprüfen Sie auf der Kachel „Übersetzungsauftrag“ die Anzahl der zu übersetzenden Assets.
1. Starten Sie den Übersetzungsauftrag über die Kachel **[!UICONTROL Übersetzungsauftrag]**.

   ![chlimage_1-462](assets/chlimage_1-462.png)

1. Klicken Sie auf die Ellipsen unten auf der Kachel „Übersetzungsauftrag“, um den Status des Übersetzungsauftrags anzuzeigen.

   ![chlimage_1-463](assets/chlimage_1-463.png)

1. Klicken Sie auf das Inhaltsfragment, um den Pfad der übersetzten zugehörigen Assets zu überprüfen.

   ![chlimage_1-464](assets/chlimage_1-464.png)

1. Überprüfen Sie in der Sammlungskonsole die Sprachkopie der Sammlung.

   ![chlimage_1-465](assets/chlimage_1-465.png)

   Beachten Sie, dass nur der Inhalt der Sammlung übersetzt wird. Die Sammlung selbst wird nicht übersetzt.

1. Navigieren Sie zum Pfad des übersetzten zugehörigen Assets. Beachten Sie, dass das übersetzte Asset unter dem Zielsprachenstamm gespeichert wird.

   ![chlimage_1-466](assets/chlimage_1-466.png)

1. Navigieren Sie zu den Assets in der Sammlung, die zusammen mit dem Inhaltsfragment übersetzt werden. Beachten Sie, dass die übersetzten Kopien der Assets im entsprechenden Stammverzeichnis der Zielsprache gespeichert werden.

   ![chlimage_1-467](assets/chlimage_1-467.png)

   >[!NOTE]
   >
   >Die Verfahren zum Hinzufügen eines Inhaltsfragments zu einem vorhandenen Projekt oder zum Durchführen von Aktualisierungsworkflows ähneln den entsprechenden Verfahren für Assets. Hinweise zu diesen Verfahren finden Sie in den für Assets beschriebenen Verfahren.
