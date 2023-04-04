---
title: Entwickeln und Erweitern von Workflows
seo-title: Developing and Extending Workflows
description: AEM stellt mehrere Tools und Ressourcen zum Erstellen von Workflow-Modellen, Entwickeln von Workflow-Schritten und programmgesteuerten Interagieren mit Workflows bereit.
seo-description: AEM provides several tools and resources for creating workflow models, developing workflow steps, and for programmatically interacting with workflows
uuid: 5a857589-3b13-4519-bda2-b1dab6005550
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 8954e3df-3afa-4d53-a7e1-255f3b8f499f
exl-id: 041b1767-8b6c-4887-a70d-abc96a116976
source-git-commit: 768576e300b655962adc3e1db20fc5ec06a5ba6c
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 35%

---


# Entwickeln und Erweitern von Workflows{#developing-and-extending-workflows}

AEM stellt mehrere Tools und Ressourcen zum Erstellen von Workflow-Modellen, Entwickeln von Workflow-Schritten und programmgesteuerten Interagieren mit Workflows bereit.

Mit Workflows können Sie Prozesse zum Verwalten von Ressourcen und Veröffentlichen von Inhalten in der AEM-Umgebung automatisieren. Workflows bestehen aus einer Reihe von Schritten, bei denen jeder Schritt eine diskrete Aufgabe erledigt. Sie können Logik- und Laufzeitdaten verwenden, um zu entscheiden, wann ein Prozess fortgesetzt werden kann, und den nächsten Schritt aus einem von mehreren möglichen Schritten auswählen.

So beinhalten beispielsweise Geschäftsprozesse zum Erstellen und Veröffentlichen von Webseiten Genehmigungs- und Abzeichnungsaufgaben diverser am Prozess beteiligter Personen. Diese Prozesse können mithilfe von AEM-Workflows modelliert und auf bestimmte Inhalte angewendet werden.

Die wichtigsten Aspekte werden im Folgenden behandelt, während die folgenden Seiten weitere Details enthalten:

* [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md)
* [Erweitern der Workflow-Funktionen](/help/sites-developing/workflows-customizing-extending.md)
* [Programmgesteuerte Interaktion mit Workflows](/help/sites-developing/workflows-program-interaction.md)
* [Referenz für Workflow-Schritte](/help/sites-developing/workflows-step-ref.md)
* [Prozessreferenz für Workflows](/help/sites-developing/workflows-process-ref.md)
* [Best Practices für Workflows](/help/sites-developing/workflows-best-practices.md)

>[!NOTE]
>
>Informationen:
>
>* Informationen zum Teilnehmen an Workflows finden Sie unter [Verwenden von Workflows](/help/sites-authoring/workflows.md).
>* Informationen zum Verwalten von Workflows und Workflow-Instanzen finden Sie unter [Verwalten von Workflows](/help/sites-administering/workflows.md).
>* Ein durchgängiger Gemeinschaftsartikel finden Sie unter [Ändern digitaler Assets mit Adobe Experience Manager-Workflows.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=de)
>* Sehen Sie sich das [AEM-Experten-Webinar zum Thema Workflows](https://communities.adobeconnect.com/p5s33iburd54/) an.
>* Informationen zu Änderungen der Datenspeicherorte finden Sie unter [Neustrukturierung von Repositorys in AEM 6.5](/help/sites-deploying/repository-restructuring.md) und [Best Practices für Workflows – Speicherorte](/help/sites-developing/workflows-best-practices.md#locations).
>


## Modell {#model}

Ein `WorkflowModel` steht für eine Definition (bzw. ein Modell) eines Workflows. Es besteht aus `WorkflowNodes` und `WorkflowTransitions`. Die Übergänge verbinden die Knoten und definieren den *Fluss*. Das Modell verfügt immer über einen Start- und einen Endknoten.

### Laufzeitmodell {#runtime-model}

Workflow-Modelle sind versioniert. Wenn Sie eine Workflow-Instanz ausführen, wird das Laufzeitmodell des Workflows verwendet und beibehalten, wie es zum Zeitpunkt des Starts des Workflows verfügbar war.

Ein Laufzeitmodell ist [generiert **Synchronisieren** wird im Workflow-Modell-Editor ausgelöst](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model).

Änderungen am Workflow-Modell, die auftreten, oder an den generierten Laufzeitmodellen oder beidem *after* die spezifische Instanz, die gestartet wurde, nicht auf diese Instanz angewendet wird.

>[!CAUTION]
>
>Die durchgeführten Schritte werden durch die Variable [Laufzeitmodell](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model), der zum Zeitpunkt der **Synchronisieren** -Aktion wird im Workflow-Modell-Editor ausgelöst.
>
>Wenn das Workflow-Modell nach diesem Zeitpunkt geändert wird (ohne **Synchronisieren** ausgelöst wird), dann spiegelt die Laufzeitinstanz diese Änderungen nicht wider. Nur nach der Aktualisierung generierte Laufzeitmodelle spiegeln die Änderungen wider. Die Ausnahmen sind die zugrunde liegenden ECMA-Skripte, die nur einmal gespeichert werden, damit diese Änderungen vorgenommen werden.

### Schritt {#step}

Jeder Schritt führt eine diskrete Aufgabe aus. Es gibt verschiedene Arten von Workflow-Schritten:

* Teilnehmer (Benutzer/Gruppe): Diese Schritte generieren ein Arbeitselement und weisen es einem Benutzer oder einer Gruppe zu. Ein Benutzer muss das Arbeitselement abschließen, damit der Workflow zum nächsten Schritt fortschreiten kann.
* Prozess (Skript, Java™-Methodenaufruf): Diese Schritte werden automatisch vom System ausgeführt. Ein ECMA-Skript oder eine Java™-Klasse implementiert den Schritt. Dienste können entwickelt werden, um spezielle Workflow-Ereignisse zu überwachen und Aufgaben gemäß der Geschäftslogik auszuführen.
* Container (Unter-Workflow): Dieser Schritttyp startet ein anderes Workflow-Modell.
* ODER-Teilung/Verknüpfung: Legen Sie mithilfe der Logik fest, welcher Schritt im Workflow als Nächstes ausgeführt werden soll.
* UND-Teilung/Verknüpfung: Ermöglicht die gleichzeitige Ausführung mehrerer Schritte.

Alle Schritte verwenden gemeinsam folgende Eigenschaften: `Autoadvance` und `Timeout`-Warnungen (skriptfähig).

### Übergang {#transition}

Ein `WorkflowTransition` steht für den Übergang zwischen zwei `WorkflowNodes` in einem `WorkflowModel`.

* Sie definiert die Verknüpfung zwischen zwei aufeinander folgenden Schritten.
* Es ist möglich, Regeln anzuwenden.

### Arbeitselement {#workitem}

Ein `WorkItem` ist die Einheit, die die `Workflow`-Instanz eines `WorkflowModel` durchläuft. Es enthält `WorkflowData`, die von der Instanz ausgeführt werden, und einen Verweis auf den `WorkflowNode`, der den zugrunde liegenden Workflow-Schritt beschreibt.

* Arbeitselemente werden verwendet, um eine Aufgabe zu identifizieren und in den entsprechenden Posteingang weiterzuleiten.
* Eine Workflow-Instanz kann ein oder mehrere `WorkItems` gleichzeitig enthalten (je nach Workflow-Modell).
* Das `WorkItem` verweist auf die Workflow-Instanz.
* Im Repository wird die `WorkItem` wird unter der Workflow-Instanz gespeichert.

### Payload {#payload}

Verweist auf die Ressource, die über einen Workflow erweitert werden muss.

Die Payload-Implementierung verweist auf eine Ressource im Repository (nach Pfad, UUID oder URL) oder auf ein serialisiertes Java™-Objekt. Das Referenzieren einer Ressource im Repository ist flexibel und mit Sling produktiv. Beispielsweise kann der referenzierte Knoten als Formular wiedergegeben werden.

### Lebenszyklus {#lifecycle}

Wird beim Starten eines neuen Workflows (durch Auswählen des jeweiligen Workflow-Modells und Definieren der Payload) erstellt und endet, sobald der Endknoten verarbeitet ist.

Folgende Aktionen können für eine Workflow-Instanz ausgeführt werden:

* Beenden
* Aussetzen
* Fortsetzen 
* Neu starten

Abgeschlossene und beendete Instanzen werden archiviert.

### Posteingang {#inbox}

Jedes Benutzerkonto hat einen eigenen Workflow-Posteingang, in dem die zugewiesenen `WorkItems` verfügbar sind.

Die `WorkItems` entweder dem Benutzerkonto direkt oder der Gruppe zugewiesen werden, zu der sie gehören.

### Workflow-Typen {#workflow-types}

Es gibt verschiedene Arten von Workflows, wie in der Konsole Workflow-Modelle angegeben:

![wf-upgraded-03](assets/wf-upgraded-03.png)

* **Standard**

   Bei diesen Typen handelt es sich um vordefinierte Workflows, die in einer standardmäßigen AEM-Instanz enthalten sind.

* Benutzerdefinierte Workflows (kein Indikator in der Konsole)

   Diese Workflows wurden als neu oder aus nativen Workflows erstellt, die mit Anpassungen überlagert wurden.

* **Veraltet**

   Mit einer älteren Version von AEM erstellte Workflows. Diese Workflows können während einer Aktualisierung beibehalten oder aus der vorherigen Version als Workflow-Paket exportiert und dann in die neue Version importiert werden.

### Übergangs-Workflows {#transient-workflows}

Standardarbeitsabläufe speichern Laufzeitinformationen (Verlaufsinformationen) während ihrer Ausführung. Sie können ein Workflow-Modell auch als **Übergang** definieren, um das persistente Speichern des Verlaufs zu vermeiden. Dieser Workflow dient zur Leistungsoptimierung, da er Zeit und Ressourcen spart, die für die Speicherung der Informationen verwendet werden.

Übergangs-Workflows können für alle Workflows verwendet werden, die:

* werden oft ausgeführt.
* den Workflow-Verlauf nicht benötigen.

Übergangs-Workflows wurden zum Laden vieler Assets eingeführt, bei denen die Asset-Informationen wichtig sind, jedoch nicht der Workflow-Laufzeitverlauf.

>[!NOTE]
>
>Siehe [Erstellen eines Verlaufs-Workflows](/help/sites-developing/workflows-models.md#creating-a-transient-workflow) für weitere Informationen.

>[!CAUTION]
>
>Wenn ein Workflow-Modell als Übergangs gekennzeichnet ist, gibt es einige Szenarien, in denen die Laufzeitinformationen beibehalten werden müssen:
>
>* Für den Payload-Typ (z. B. Video) sind externe Verarbeitungsschritte erforderlich. In diesem Fall ist der Laufzeitverlauf zum Bestätigen des Status erforderlich.
>* Der Workflow wird in ein **UND-Teilung**. In solchen Fällen ist der Laufzeitverlauf für die Statusbestätigung erforderlich.
>* Wenn der Verlaufs-Workflow in einen Teilnehmerschritt eintritt, ändert sich der Modus zur Laufzeit in Nicht-Verlaufs-Workflow. Da die Aufgabe an eine Person übergeben wird, muss der Verlauf beibehalten werden.
>


>[!CAUTION]
>
>Innerhalb eines Verlaufs-Workflows sollten Sie keine **Zum Schritt wechseln**.
>
>Der Grund dafür ist, dass die **Zum Schritt wechseln** erstellt einen Sling-Auftrag, um den Workflow im `goto` Punkt. Dadurch wird der Workflow vorübergehend und in der Protokolldatei wird ein Fehler erzeugt.
>
>Verwendung **ODER-Teilung** , um innerhalb eines Verlaufs-Workflows eine Auswahl zu treffen.

>[!NOTE]
>
>Siehe [Best Practices für Assets](/help/assets/performance-tuning-guidelines.md#transient-workflows) Weitere Informationen dazu, wie sich Übergangs-Workflows auf die Asset-Leistung auswirken.

### Unterstützung für mehrere Ressourcen {#multi-resource-support}

Aktivieren **Unterstützung mehrerer Ressourcen** für Ihr Workflow-Modell bedeutet, dass eine einzelne Workflow-Instanz gestartet wird, selbst wenn Sie mehrere Ressourcen auswählen. Jeder wird als Paket angehängt.

Wenn **Unterstützung mehrerer Ressourcen** nicht für Ihr Workflow-Modell aktiviert ist und mehrere Ressourcen ausgewählt sind, wird für jede Ressource eine einzelne Workflow-Instanz gestartet.

>[!NOTE]
>
>Siehe [Konfigurieren eines Workflows für die Unterstützung mehrerer Ressourcen](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) für weitere Informationen.

### Workflow-Phasen {#workflow-stages}

Die Workflow-Phasen sind hilfreich, um den Fortschritt eines Workflows beim Ausführen von Aufgaben anzuzeigen. Sie können einen Überblick darüber geben, wie weit der Workflow durch die Verarbeitung fortgeschritten ist. Wenn der Workflow ausgeführt wird, kann der Benutzer den Fortschritt anzeigen, der unter **Staging** (im Gegensatz zu einzelnen Schritten).

Da die Namen der einzelnen Schritte spezifisch und technisch sein können, kann der Name der Phase eine Konzeptansicht des Workflow-Fortschritts vermitteln.

Für einen Workflow mit sechs Schritten und vier Phasen kann dies wie folgt aussehen:

1. Sie können die [Workflow-Phase (die den jeweiligen Fortschritt anzeigt) konfigurieren und dann die Phase dem entsprechenden Schritt im Workflow zuweisen](/help/sites-developing/workflows-models.md#configuring-workflow-stages-that-show-workflow-progress):

   * Mehrere Phasennamen können erstellt werden.
   * Dann wird jedem Schritt ein einzelner Phasenname zugewiesen (ein Phasenname kann einem oder mehreren Schritten zu gewiesen werden).

   | **Schrittname** | **Phase (dem Schritt zugewiesen)** |
   |---|---|
   | Schritt 1 | Erstellen |
   | Schritt 2 | Erstellen |
   | Schritt 3 | Überprüfung |
   | Schritt 4 | Genehmigen |
   | Schritt 5 | Fertig stellen |
   | Schritt 6 | Fertig stellen |

1. Wenn der Workflow ausgeführt wird, kann der Benutzer den Fortschritt anhand des Phasenamens (anstelle des Schrittnamens) anzeigen. Der Workflow-Fortschritt wird im [Registerkarte &quot;WORKFLOW-INFORMATIONEN&quot;im Fenster mit Aufgabendetails des Workflow-Elements](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) im [Posteingang](/help/sites-authoring/inbox.md).

### Workflows und Forms {#workflows-and-forms}

In der Regel werden Workflows zur Verarbeitung von Formularübermittlungen in AEM verwendet. Sie kann mit der [Kernkomponenten - Formularkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html?lang=en) in einer Standard-AEM oder mit der [AEM Forms-Lösung](/help/forms/using/aem-forms-workflow.md).

Beim Erstellen eines Formulars kann die Formularübermittlung einfach mit einem Workflow-Modell verknüpft werden. Beispielsweise um den Inhalt an einem bestimmten Speicherort des Repositorys zu speichern oder einen Benutzer über die Formularübermittlung und deren Inhalt zu benachrichtigen.

### Workflows und Übersetzung {#workflows-and-translation}

Workflows sind auch Teil der [Übersetzung](/help/sites-administering/translation.md) Prozess.
