---
title: Entwickeln und Erweitern von Workflows
description: AEM stellt mehrere Tools und Ressourcen zum Erstellen von Workflow-Modellen, Entwickeln von Workflow-Schritten und programmgesteuerten Interagieren mit Workflows bereit.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 041b1767-8b6c-4887-a70d-abc96a116976
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 100%

---


# Entwickeln und Erweitern von Workflows{#developing-and-extending-workflows}

AEM stellt mehrere Tools und Ressourcen zum Erstellen von Workflow-Modellen, Entwickeln von Workflow-Schritten und programmgesteuerten Interagieren mit Workflows bereit.

Mit Workflows können Sie Prozesse zum Verwalten von Ressourcen und Veröffentlichen von Inhalten in der AEM-Umgebung automatisieren. Workflows beinhalten eine Reihe von Schritten, wobei bei jedem Schritt eine bestimmte Aufgabe ausgeführt wird. Dabei können Sie mithilfe von Logik und Laufzeitdaten entscheiden, wann ein Prozess fortgesetzt werden kann, und den nächsten Schritt aus mehreren möglichen Schritten auswählen.

So beinhalten beispielsweise Geschäftsprozesse zum Erstellen und Veröffentlichen von Webseiten Genehmigungs- und Abzeichnungsaufgaben diverser am Prozess beteiligter Personen. Diese Prozesse können mithilfe von AEM-Workflows modelliert und auf bestimmte Inhalte angewendet werden.

Die wichtigsten Aspekte werden unten beschrieben, wobei die folgenden Seiten weitere Einzelheiten enthalten:

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
>* Lesen Sie den umfassenden Community-Artikel zum Thema [Ändern digitaler Assets mit Workflows in Adobe Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html?lang=de).
>* Sehen Sie sich das [AEM-Experten-Webinar zum Thema Workflows](https://communities.adobeconnect.com/p5s33iburd54/) an.
>* Informationen zu Änderungen der Datenspeicherorte finden Sie unter [Neustrukturierung von Repositorys in AEM 6.5](/help/sites-deploying/repository-restructuring.md) und [Best Practices für Workflows – Speicherorte](/help/sites-developing/workflows-best-practices.md#locations).
>

## Modell {#model}

Ein `WorkflowModel` steht für eine Definition (bzw. ein Modell) eines Workflows. Es besteht aus `WorkflowNodes` und `WorkflowTransitions`. Die Übergänge verbinden die Knoten und definieren den *Fluss*. Das Modell hat immer einen Start- und einen Endknoten.

### Laufzeitmodell {#runtime-model}

Workflow-Modelle sind versioniert. Wenn Sie eine Workflow-Instanz ausführen, wird das Laufzeitmodell des Workflows verwendet und so beibehalten, wie es zum Zeitpunkt des Starts des Workflows verfügbar war.

Ein Laufzeitmodell wird [erzeugt, sobald die **Synchronisierung** im Workflow-Modell-Editor ausgelöst wird](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model).

Änderungen am Workflow-Modell, die *nach* dem Start der spezifischen Instanz auftreten, und/oder Laufzeitmodelle, die danach erzeugt werden, werden nicht auf diese Instanz angewendet.

>[!CAUTION]
>
>Die durchgeführten Schritte werden durch das [Laufzeitmodell](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model) definiert, das zum Zeitpunkt der Auslösung der **Synchronisierungs**-Aktion im Workflow-Modell-Editor generiert wird.
>
>Falls das Workflow-Modell nach diesem Zeitpunkt geändert wird (ohne dass eine **Synchronisierung** ausgelöst wird), werden diese Änderungen nicht auf die Laufzeitinstanz angewandt. Nur Laufzeitmodelle, die nach der Aktualisierung erstellt werden, spiegeln die Änderungen wider. Ausnahmen sind die zugrunde liegenden ECMA-Skripte, die nur einmal gespeichert werden, sodass Änderungen an diesen übernommen werden.

### Schritt {#step}

Jeder Schritt führt eine diskrete Aufgabe aus. Es gibt verschiedene Arten von Workflow-Schritten:

* Teilnehmerin bzw. Teilnehmer (Benutzende/Gruppen): Diese Schritte generieren ein Arbeitselement und weisen es einer Person oder einer Gruppe zu. Ein Benutzer muss das Arbeitselement abschließen, damit der Workflow zum nächsten Schritt fortschreiten kann.
* Prozess (Skript, Java™-Methodenaufruf): Diese Schritte werden automatisch vom System ausgeführt. Ein ECMA-Skript oder eine Java™-Klasse implementiert den Schritt. Es können Dienste entwickelt werden, um spezielle Workflow-Ereignisse zu überwachen und Aufgaben gemäß der Business-Logik auszuführen.
* Container (Untergeordneter Workflow): Diese Art von Schritt startet ein anderes Workflow-Modell.
* ODER-Teilung/Verbindung: Verwendet Logik, um zu entscheiden, welcher Schritt als nächster im Workflow ausgeführt werden soll.
* UND-Teilung/Verbindung: Damit können mehrere Schritte gleichzeitig ausgeführt werden.

Alle Schritte verwenden gemeinsam folgende Eigenschaften: `Autoadvance` und `Timeout`-Warnungen (skriptfähig).

### Übergang {#transition}

Ein `WorkflowTransition` steht für den Übergang zwischen zwei `WorkflowNodes` in einem `WorkflowModel`.

* Er definiert die Verbindung zwischen zwei aufeinander folgenden Schritten.
* Auf ihn können Regeln angewandt werden.

### Arbeitselement {#workitem}

Ein `WorkItem` ist die Einheit, die die `Workflow`-Instanz eines `WorkflowModel` durchläuft. Es enthält `WorkflowData`, die von der Instanz ausgeführt werden, und einen Verweis auf den `WorkflowNode`, der den zugrunde liegenden Workflow-Schritt beschreibt.

* Arbeitselemente werden verwendet, um eine Aufgabe zu identifizieren und in den entsprechenden Posteingang weiterzuleiten.
* Eine Workflow-Instanz kann ein oder mehrere `WorkItems` gleichzeitig enthalten (je nach Workflow-Modell).
* Das `WorkItem` verweist auf die Workflow-Instanz.
* Im Repository wird das `WorkItem` unterhalb der Workflow-Instanz gespeichert.

### Payload {#payload}

Verweist auf die Ressource, die über einen Workflow erweitert werden muss.

Die Payload-Implementierung verweist auf eine Ressource im Repository (über einen Pfad, eine UUID oder URL) oder auf ein serialisiertes Java™-Objekt. Das Referenzieren einer Ressource im Repository ist flexibel und mit Sling produktiv. Beispielsweise kann der referenzierte Knoten als Formular dargestellt werden.

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

Die `WorkItems` werden dem Benutzerkonto direkt oder der Gruppe, zu der die Person gehört, zugewiesen.

### Workflow-Typen {#workflow-types}

Es gibt diverse Workflow-Typen, wie aus der Konsole für Workflow-Modelle ersichtlich:

![wf-upgraded-03](assets/wf-upgraded-03.png)

* **Standard**

  Dies sind vorkonfigurierte Workflows, die in einer Standard-AEM-Instanz enthalten sind.

* Benutzerdefinierte Workflows (kein Indikator in der Konsole)

  Hierbei handelt es sich um Workflows, die neu oder aus vorkonfigurierten Workflows erstellt wurden, die mit Anpassungen überlagert wurden.

* **Veraltet**

  Mit einer älteren Version von AEM erstellte Workflows. Diese Workflows können während einer Aktualisierung beibehalten oder als Workflow-Paket aus der vorherigen Version exportiert und dann in die neue Version importiert werden.

### Übergangs-Workflows {#transient-workflows}

Standard-Workflows speichern während ihrer Ausführung Laufzeit- bzw. Verlaufsdaten. Sie können ein Workflow-Modell auch als **Übergang** definieren, um das persistente Speichern des Verlaufs zu vermeiden. Dieser Workflow dient zur Leistungsoptimierung, da er Zeit und Ressourcen spart, die sonst für das persistente Speichern der Informationen verwendet würden.

Übergangs-Workflows können für alle Workflows verwendet werden, die:

* Oft ausgeführt werden.
* Den Workflow-Verlauf nicht benötigen.

Übergangs-Workflows wurden eingeführt, um eine große Anzahl von Assets zu laden, wobei die Asset-Informationen wichtig sind, jedoch nicht der Laufzeitverlauf des Workflows.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Erstellen eines Übergangs-Workflows](/help/sites-developing/workflows-models.md#creating-a-transient-workflow).

>[!CAUTION]
>
>Wenn ein Workflow-Modell als „Übergang“ gekennzeichnet ist, gibt es einige Szenarien, bei denen die Laufzeitdaten dennoch persistent gespeichert werden müssen:
>
>* Für den Payload-Typ (z. B. Video) sind externe Verarbeitungsschritte erforderlich. In diesem Fall ist der Laufzeitverlauf zum Bestätigen des Status erforderlich.
>* Der Workflow gelangt zu einer **UND-Teilung**. In solchen Fällen ist der Laufzeitverlauf für die Statusbestätigung erforderlich.
>* Wenn der Übergangs-Workflow in einen Teilnehmerschritt eintritt, ändert sich der Modus zur Laufzeit in einen Nicht-Übergangs-Workflow. Da die Aufgabe an eine Person übergeben wird, muss der Verlauf persistiert werden.
>

>[!CAUTION]
>
>In einem Übergangs-Workflow sollten Sie keinen **Goto-Schritt** verwenden.
>
>Der Grund dafür ist, dass der **Goto-Schritt** einen Sling-Auftrag erzeugt, um den Workflow am Punkt `goto` fortzusetzen. Dies widerspricht dem Zweck eines Übergangs-Workflows und erzeugt einen Fehler in der Protokolldatei.
>
>Verwenden Sie eine **ODER-Teilung**, um innerhalb eines Übergangs-Workflows eine Auswahl zu treffen.

>[!NOTE]
>
>Weitere Informationen, wie sich Übergangs-Workflows auf die Asset-Leistung auswirken, finden Sie unter [Best Practices für Assets](/help/assets/performance-tuning-guidelines.md#transient-workflows).

### Unterstützung für mehrere Ressourcen {#multi-resource-support}

Die Aktivierung von **Unterstützung mehrerer Ressourcen** für Ihr Workflow-Modell bedeutet, dass eine einzige Workflow-Instanz gestartet wird, auch wenn Sie mehrere Ressourcen auswählen. Diese werden jeweils als Paket beigefügt.

Wenn für Ihr Workflow-Modell die **Unterstützung mehrerer Ressourcen** nicht aktiviert ist und mehrere Ressourcen ausgewählt werden, wird für jede Ressource eine einzelne Workflow-Instanz gestartet.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Konfigurieren eines Workflows für die Unterstützung mehrerer Ressourcen](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support).

### Workflow-Phasen {#workflow-stages}

Die Workflow-Phasen sind hilfreich, um den Fortschritt eines Workflows beim Ausführen von Aufgaben anzuzeigen. Sie können einen Überblick darüber geben, wie weit der Workflow durch die Verarbeitung fortgeschritten ist. Wenn der Workflow ausgeführt wird, lässt sich der Fortschritt anhand von **Staging** (im Gegensatz zu einzelnen Schritten) einsehen.

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

1. Wenn der Workflow ausgeführt wird, kann der Benutzer den Fortschritt anhand des Phasenamens (anstelle des Schrittnamens) anzeigen. Der Workflow-Fortschritt wird auf der Registerkarte [WORKFLOW-INFO des Aufgabendetailfensters des Workflow-Elements](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) angezeigt, das im [Posteingang](/help/sites-authoring/inbox.md) aufgelistet ist.

### Workflows und Formulare {#workflows-and-forms}

In der Regel werden Workflows dazu benutzt, die Übermittlung von Formularen in AEM zu verarbeiten. Dies kann mit den [Formularkomponenten der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html?lang=de), die in einer Standard-AEM-Instanz verfügbar sind, oder mit der [AEM Forms-Lösung](/help/forms/using/aem-forms-workflow.md) erfolgen.

Beim Erstellen eines Formulars kann die Formularübermittlung einfach mit einem Workflow-Modell verknüpft werden. Beispielsweise um den Inhalt an einem bestimmten Speicherort des Repositorys zu speichern oder eine Person über die Formularübermittlung und deren Inhalt zu benachrichtigen.

### Workflows und Übersetzung {#workflows-and-translation}

Workflows sind auch ein fester Bestandteil des [Übersetzungs](/help/sites-administering/translation.md)-Prozesses.
