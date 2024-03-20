---
title: Creative Project und PIM-Integration
description: Creative Project optimiert den gesamten Fotoshooting-Workflow, einschließlich der Generierung einer Fotoshooting-Anfrage, des Hochladens eines Fotoshootings, der Zusammenarbeit bei einem Fotoshooting und der Verpackung genehmigter Assets
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
exl-id: c4eff50e-0d55-4a61-98fd-cc42138656cb
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2888'
ht-degree: 51%

---


# Creative Project und PIM-Integration {#creative-project-and-pim-integration}

Als Marketer oder Kreativschaffender können Sie die Creative Project-Werkzeuge in Adobe Experience Manager (AEM) verwenden, um eCommerce-bezogene Produktfotografie und zugehörige kreative Prozesse innerhalb Ihrer Organisation zu verwalten.

Insbesondere können Sie Creative Project zur Optimierung der folgenden Aufgaben in Ihrem Fotoshooting-Workflow nutzen:

* Erstellen einer Fotoshooting-Anfrage
* Fotoshooting hochladen
* Zusammenarbeit bei einem Fotoshooting
* Verpacken genehmigter Assets

>[!NOTE]
>
>Informationen zur Zuweisung von Benutzerrollen und Workflows zu bestimmen Benutzertypen finden Sie unter [Informationen zu Projekt-Benutzerrollen](/help/sites-authoring/projects.md#user-roles-in-a-project).

## Workflow „Produkt-Fotoshooting“  {#exploring-product-photo-shoot-workflows}

Creative Project bietet mehrere Projektvorlagen, die unterschiedlichen Projektanforderungen gerecht werden. Die Vorlage **Projekt für Produkt-Fotoshooting** ist im Lieferumfang enthalten. Diese Vorlage enthält Fotoshooting-Workflows, mit denen Sie Anfragen zu Produktfotos einleiten und verwalten können. Sie enthält darüber hinaus eine Reihe von Aufgaben, die es Ihnen ermöglichen, digitale Bilder für Produkte anhand geeigneter Bewertungs- und Bestätigungsabläufe zu erhalten.

## Erstellen eines Projekts für Produkt-Fotoshootings {#create-a-product-photo-shoot-project}

1. Im **Projekte** Console, klicken Sie auf **Erstellen** und wählen Sie dann **Projekt erstellen** aus der Liste.

   ![Schaltfläche „Projekt erstellen“](assets/chlimage_1-132a.png)

1. Im **Projekt erstellen** Seite, wählen Sie die **Projekt für Produkt-Fotoshooting** Vorlage und klicken Sie auf **Nächste**.

   ![Projekt-Assistent](assets/chlimage_1-133a.png)

1. Geben Sie Projektdetails ein, einschließlich Titel, Beschreibung und Fälligkeitsdatum. Fügen Sie Benutzer hinzu und weisen Sie ihnen verschiedene Rollen zu. Sie können auch eine Miniaturansicht für das Projekt hinzufügen.

   ![Projektdetails](assets/chlimage_1-134a.png)

1. Klicken Sie auf **Erstellen**. Eine Bestätigungsmeldung informiert Sie, dass das Projekt erstellt wurde.
1. Klicks **Fertig** , um zu **Projekte** Konsole. Klicken Sie alternativ auf **Öffnen** , um die Assets innerhalb des Projekts anzuzeigen.

## Beginn der Arbeit an einem Projekt für Produkt-Fotoshooting {#starting-work-in-a-product-photo-shoot-project}

Um eine Fotoshooting-Anfrage zu starten, klicken Sie auf ein Projekt und dann auf **Arbeit hinzufügen** auf der Seite mit den Projektdetails , um einen Workflow zu starten.

![Arbeit hinzufügen](assets/chlimage_1-135a.png)

Ein **Produkt-Fotoshooting-Projekt** umfasst folgende Workflows:

* **Workflow &quot;Produkt-Fotoshooting (Commerce-Integration)&quot;**: Dieser Workflow verwendet die Commerce-Integration in das PIM-System (Product Information Management), um automatisch eine Aufnahmenliste für die ausgewählten Produkte (Hierarchie) zu erstellen. Sie können die Produktdaten als Teil der Asset-Metadaten anzeigen, nachdem der Workflow abgeschlossen wurde.
* Workflow **Produkt-Fotoshooting**: Dieser Workflow ermöglicht es Ihnen, eine Aufnahmenliste bereitzustellen, anstatt dies der Commerce-Integration zu überlassen. Dabei werden die hochgeladenen Bilder in einer CSV-Datei im Assets-Ordner des Projekts protokolliert.

Verwenden Sie den Workflow **Produkt-Fotoshooting (Commerce-Integration)** zur Zuordnung von Bild-Assets zu den Produkten in AEM. Dieser Workflow verwendet die Commerce-Integration, um die genehmigten Bilder mit den vorhandenen Produktdaten am Speicherort zu verknüpfen `/etc/commerce`.

Der Workflow **Produkt-Fotoshooting (Commerce-Integration)** umfasst die folgenden Aufgaben:

* Aufnahmenliste erstellen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Überprüfen und genehmigen
* Zu Produktionsaufgabe wechseln

Wenn in AEM keine Produktinformationen verfügbar sind, verwenden Sie den Workflow **Produkt-Fotoshooting**, um Bild-Assets den Produkten auf der Basis der Informationen zuzuordnen, die Sie in eine CSV-Datei hochladen. Die CSV-Datei muss grundlegende Produktinformationen wie Produkt-ID, Kategorie und Beschreibung enthalten. Der Workflow ruft genehmigte Assets für die Produkte ab.

Dieser Workflow umfasst die folgenden Aufgaben:

* Aufnahmenliste hochladen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Überprüfen und genehmigen
* Zu Produktionsaufgabe wechseln

Sie können diesen Workflow mithilfe der Workflow-Konfigurationsoption anpassen.

Beide Workflows enthalten Schritte zur Verknüpfung von Produkten mit den genehmigten Assets. Jeder Workflow umfasst die folgenden Schritte:

* Workflow-Konfiguration: Beschreibt die Optionen zum Anpassen des Workflows
* Starten eines Projekt-Workflows: Erläutert, wie ein Produkt-Fotoshooting gestartet wird
* Workflow-Aufgabendetails: Bietet Details zu den im Workflow verfügbaren Aufgaben

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Fortschritt eines Projekts verfolgen, indem Sie die aktiven/abgeschlossenen Aufgaben innerhalb eines Projekts überwachen.

Verwenden Sie Folgendes, um den Fortschritt eines Projekts zu überwachen:

* Aufgabenkarte
* Aufgabenliste

Die Aufgabenkarte stellt den Gesamtfortschritt des Projekts dar. Sie wird nur dann auf der Seite „Projektdetails“ angezeigt, wenn das Projekt zugehörige Aufgaben aufweist. Die Aufgabenkarte zeigt den aktuellen Abschlussstatus des Projekts auf der Basis der abgeschlossenen Aufgaben an. Zukünftige Aufgaben werden nicht berücksichtigt.

Die Aufgabenkarte stellt die folgenden Detailinformationen bereit:

* Prozentsatz der aktiven Aufgaben
* Prozentsatz der abgeschlossenen Aufgaben

![Aufgabenkarte](assets/chlimage_1-136a.png)

Die Aufgabenliste stellt detaillierte Information zur aktuell aktiven Workflow-Aufgabe für das Projekt bereit. Um die Liste anzuzeigen, klicken Sie auf die Aufgabenkarte. Die Aufgabenliste zeigt auch Metadaten wie Startdatum, Fälligkeitsdatum, Bevollmächtigter, Priorität und Status der Aufgabe an.

![Aufgabenliste](assets/chlimage_1-137a.png)

## Workflow-Konfiguration {#workflow-configuration}

Diese Aufgabe umfasst die Zuweisung von Workflow-Schritten an Benutzer basierend auf ihren Benutzerrollen.

So konfigurieren Sie die **Produkt-Fotoshooting** workflow:

1. Navigieren Sie zu **Instrumente** > **Workflows** und wählen Sie anschließend die **Modelle** -Kachel zum Öffnen der **Workflow-Modelle** Seite.
1. Wählen Sie die **Produkt-Fotoshooting** und wählen Sie die **Bearbeiten** in der Symbolleiste, um sie im Bearbeitungsmodus zu öffnen.

   ![Modell für Produkt-Fotoshooting](assets/chlimage_1-138a.png)

1. Öffnen Sie auf der Seite **Workflow „Produkt-Fotoshooting“** eine Projektaufgabe. Öffnen Sie z. B. die Aufgabe **Aufnahmenliste hochladen**.

   ![Modell bearbeiten](assets/project-photo-shoot-workflow-model.png)

1. Klicken Sie auf **Aufgabe** -Registerkarte, um Folgendes zu konfigurieren:

   * Name der Aufgabe
   * Standardbenutzer (Rolle), der die Aufgabe erhält
   * Standardpriorität der Aufgabe, die in der Aufgabenliste des Benutzers angezeigt wird
   * Aufgabenbeschreibung, die angezeigt wird, wenn der Verantwortliche die Aufgabe öffnet
   * Fälligkeitsdatum für eine Aufgabe, das auf der Grundlage des Zeitpunkts berechnet wird, zu dem die Aufgabe gestartet wurde

1. Klicks **OK** , um die Konfigurationseinstellungen zu speichern.

Sie können die zusätzlichen Aufgaben für den Workflow **Produkt-Fotoshooting** auf ähnliche Weise konfigurieren.

Gehen Sie in ähnlicher Weise vor, um die Aufgaben im Workflow **Produkt-Fotoshooting (Commerce-Integration)** zu konfigurieren.

## Starten eines Projekt-Workflows {#starting-a-project-workflow}

In diesem Abschnitt wird beschrieben, wie das Produktinformations-Management in Ihr Creative-Projekt integriert wird.

1. Navigieren Sie zu einem Produkt-Fotoshooting-Projekt und klicken Sie auf das **Arbeit hinzufügen** auf dem **Workflows** Karte.
1. Wählen Sie die Workflow-Karte **Produkt-Fotoshooting (Commerce-Integration)** aus, um den entsprechenden Workflow zu starten **.** Wenn die Produktinformationen nicht verfügbar sind unter `/etc/commerce`, wählen Sie die **Produkt-Fotoshooting** und starten Sie **Produkt-Fotoshooting** Arbeitsablauf.

   ![Workflow-Assistent](assets/chlimage_1-140a.png)

1. Klicks **Nächste** , um den Workflow im Projekt zu starten.
1. Geben Sie auf der nächsten Seite Details zum Workflow ein.

   ![Workflow-Details](assets/chlimage_1-141a.png)

1. Klicks **Einsenden** , um den Fotoshooting-Workflow zu starten. Die Seite mit den Details zum Fotoshooting-Projekt wird angezeigt.

   ![Projektseite mit neuem Workflow](assets/chlimage_1-142a.png)

### Workflow-Aufgabendetails {#workflow-tasks-details}

Der Fotoshooting-Workflow umfasst mehrere Aufgaben. Jede Aufgabe wird basierend auf der für die Aufgabe definierten Konfiguration einer Benutzergruppe zugewiesen.

#### Aufnahmenlistenaufgabe erstellen {#create-shot-list-task}

Die Aufgabe **Aufnahmenliste erstellen** ermöglicht dem Projekteigentümer die Auswahl von Produkten, für die Bilder benötigt werden. Je nach vom Benutzer ausgewählter Option wird eine CSV-Datei generiert, die grundlegende Produktinformationen enthält.

1. Klicken Sie im Projektordner auf die Schaltfläche mit Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.

   ![Aufgabenkarte](assets/chlimage_1-143a.png)

1. Wählen Sie die **Aufnahmenliste erstellen** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Aufnahmenlisten-Aufgabe öffnen](assets/chlimage_1-144a.png)

1. Überprüfen Sie die Aufgabendetails und klicken Sie dann auf die **Aufnahmenliste erstellen** Schaltfläche.

   ![Details der Aufnahmenlisten-Aufgabe](assets/chlimage_1-145a.png)

1. Wählen Sie Produkte, für die Produktdaten ohne verknüpfte Bilder vorhanden sind.

   ![Auswählen von Produkten](assets/chlimage_1-146a.png)

1. Klicken Sie auf **Zu Aufnahmenliste hinzufügen** -Schaltfläche, um eine CSV-Datei zu erstellen, die eine Liste all dieser Produkte enthält. Eine Meldung bestätigt, dass die Aufnahmenliste für die ausgewählten Produkte erstellt wurde. Klicks **Schließen** , um den Workflow abzuschließen.

1. Nachdem Sie eine Aufnahmenliste erstellt haben, wird die **Aufnahmenliste anzeigen** angezeigt. Um weitere Produkte zur Aufnahmenliste hinzuzufügen, klicken Sie auf **Zur Aufnahmenliste hinzufügen**. In diesem Fall werden die Daten an die anfangs erstellte Aufnahmenliste angehängt.

   ![Zu Aufnahmenliste hinzufügen](assets/chlimage_1-147a.png)

1. Klicks **Aufnahmenliste anzeigen** um die neue Aufnahmenliste anzuzeigen.

   ![Aufnahmenliste anzeigen](assets/chlimage_1-148a.png)

   Um die vorhandenen Daten zu bearbeiten oder neue Daten hinzuzufügen, klicken Sie auf **Bearbeiten** aus der Symbolleiste. Sie können nur die Felder **Produkt** und **Beschreibung** bearbeiten.

   ![Aufnahmenliste bearbeiten](assets/chlimage_1-149a.png)

   Klicken Sie nach dem Aktualisieren der Datei auf **Speichern** in der Symbolleiste, um die Datei zu speichern.

1. Nachdem Sie die Produkte hinzugefügt haben, klicken Sie auf **Fertig** auf dem **Aufnahmenliste erstellen** Aufgabendetailseite, um die Aufgabe als abgeschlossen zu markieren. Sie können einen optionalen Kommentar hinzufügen.

Nach Abschluss der Aufgabe werden die folgenden Änderungen innerhalb des Projekts eingeführt:

* Assets, die der Produkthierarchie entsprechen, werden in einem Ordner mit demselben Namen wie der Workflow-Titel erstellt.
* Die Metadaten für die Assets können über die Konsole &quot;Assets&quot;bearbeitet werden, selbst bevor der Fotograf die Bilder bereitstellt.
* Es wird ein Fotoshooting-Ordner erstellt, in dem die vom Fotografen bereitgestellten Bilder gespeichert werden. Dieser Ordner enthält Unterordner für jeden Produkteintrag in der Aufnahmenliste.

### Aufnahmenlistenaufgabe hochladen {#upload-shot-list-task}

Diese Aufgabe ist Teil des Produkt-Fotoshooting-Workflows. Diese Aufgabe führen Sie aus, wenn in AEM keine Produktinformationen verfügbar sind. In diesem Fall laden Sie eine Liste von Produkten in eine CSV-Datei hoch, für die Bild-Assets erforderlich sind. Anhand der Informationen in der CSV-Datei ordnen Sie die Bild-Assets den Produkten zu. Bei der Datei muss es sich um eine CSV-Datei mit dem Namen `shotlist.csv` handeln.

Verwenden Sie den Link **Aufnahmenliste anzeigen** unter der Projektkarte im vorherigen Verfahren, um eine Beispieldatei im CSV-Format herunterzuladen. Überprüfen Sie die Beispieldatei, um den üblichen Inhalt einer CSV-Datei zu ermitteln.

Die Produktliste oder die CSV-Datei kann Felder wie **Kategorie, Produkt, ID, Beschreibung**, und **Pfad**. Das Feld **ID** ist obligatorisch und enthält die Produkt-ID. Die anderen Felder sind optional.

Ein Produkt kann zu einer bestimmten Kategorie gehören. Die Produktkategorie kann in der CSV-Datei unterhalb der Spalte **Kategorie** aufgeführt werden. Das Feld **Produkt** enthält den Namen des Produkts. Geben Sie im Feld **Beschreibung** die Produktbeschreibung oder Anleitungen für Fotografen ein.

1. Klicken Sie im Projektordner auf die Schaltfläche mit Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) um die Liste der Aufgaben im Workflow anzuzeigen.
1. Wählen Sie die **Aufnahmenliste hochladen** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Aufnahmenliste hochladen](assets/chlimage_1-150a.png)

1. Überprüfen Sie die Aufgabendetails und klicken Sie dann auf die **Aufnahmenliste hochladen** Schaltfläche.

   ![Hochladen der Aufnahmenliste](assets/chlimage_1-151a.png)

1. Klicken Sie auf **Aufnahmenliste hochladen** Schaltfläche zum Hochladen der CSV-Datei. Der Workflow erkennt diese Datei als Quelle, die zum Extrahieren von Produktdaten für die nächste Aufgabe verwendet werden kann.
1. Laden Sie eine CSV-Datei hoch, die Produktinformationen im entsprechenden Format enthält. Der Link **Hochgeladene Assets anzeigen** wird unterhalb der Karte angezeigt, nachdem die CSV-Datei hochgeladen wurde.

   ![Produktinformationen hochladen](assets/chlimage_1-152a.png)

   Klicken Sie auf das Symbol **Fertig stellen**, um diese Aufgabe abzuschließen.

1. Klicken Sie auf das Symbol **Fertig stellen**, um diese Aufgabe abzuschließen.

### Aufgabe „Fotoshooting hochladen“ {#upload-photo-shoot-task}

Als Redakteur können Sie Aufnahmen für Produkte hochladen, die in der Datei **shotlist.csv** aufgeführt sind, welche in der vorherigen Aufgabe erstellt oder hochgeladen wurde.

Der Name der Bilder für den Upload sollte mit `<ProductId_>` beginnen, wobei die `ProductId` aus dem Feld **ID** in der Datei `shotlist.csv` stammt. Beispiel: Für ein Produkt in der Aufnahmenliste mit der **ID** `397122` können Sie Dateien hochladen, die die Namen `397122_lowlight.png`, `397122_highcontrast.jpg` usw. aufweisen.

Sie können entweder die Bilder direkt hochladen oder eine ZIP-Datei hochladen, die die Bilder enthält. Basierend auf ihren Namen werden die Bilder in entsprechenden Produktordnern innerhalb des Ordners Fotoshooting abgelegt.

1. Klicken Sie unter dem Projektordner auf die Schaltfläche mit den Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Fotoshooting hochladen** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Fotoshooting hochladen](assets/chlimage_1-153a.png)

1. Klicks **Fotoshooting hochladen** und laden Sie die Fotoshootbilder hoch.
1. Klicken Sie auf **Fertig** in der Symbolleiste, um die Aufgabe abzuschließen.

### Aufgabe „Fotoaufnahme retuschieren“ {#retouch-photo-shoot-task}

Wenn Sie Bearbeitungsrechte haben, führen Sie die Aufgabe **Fotoaufnahme retuschieren** aus, um die in den Ordner „Fotoshooting“ hochgeladenen Bilder zu bearbeiten.

1. Klicken Sie unter dem Projektordner auf die Schaltfläche mit den Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Fotoaufnahme retuschieren** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Fotoaufnahme retuschieren](assets/chlimage_1-154a.png)

1. Klicken Sie auf **Hochgeladene Assets anzeigen** -Link in **Fotoaufnahme retuschieren** Seite, um die hochgeladenen Bilder zu durchsuchen.

   ![Hochgeladene Assets anzeigen](assets/chlimage_1-155a.png)

   Falls erforderlich, bearbeiten Sie die Bilder mit einer Adobe Creative Cloud-Applikation.

   ![Asset bearbeiten](assets/chlimage_1-156a.png)

1. Klicken Sie auf **Fertig** in der Symbolleiste, um die Aufgabe abzuschließen.

### Aufgabe überprüfen und genehmigen {#review-and-approve-task}

In dieser Aufgabe überprüfen Sie die von einem Fotografen hochgeladenen Fotoshootbilder und markieren Bilder als zur Verwendung freigegeben.

1. Klicken Sie unter dem Projektordner auf die Schaltfläche mit den Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Überprüfen und genehmigen** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Überprüfen und bestätigen](assets/chlimage_1-157a.png)

1. Im **Überprüfen und genehmigen** Seite, die Prüfungsaufgabe einer Rolle zuweisen, und klicken Sie dann auf **Überprüfen** , um mit der Überprüfung der hochgeladenen Produktbilder zu beginnen.

   ![Überprüfen von Assets beginnen](assets/chlimage_1-158a.png)

1. Wählen Sie ein Produktbild aus und klicken Sie auf das **Genehmigen** in der Symbolleiste, um sie als genehmigt zu markieren. Sobald Sie ein Bild genehmigt haben, wird darüber ein „Genehmigt“-Banner angezeigt.

   ![Genehmigen eines Bildes](assets/chlimage_1-159a.png)

1. Klicks **Fertig**. Die bestätigten Bilder werden mit den leeren Assets verknüpft, die erstellt wurden.

Sie können einige Produkte ohne Bilder auslassen. Später können Sie die Aufgabe erneut aufrufen und nach Abschluss markieren.

Mithilfe der Assets-Benutzeroberfläche können Sie zu den Projekt-Assets navigieren und die genehmigten Bilder überprüfen.

Klicken Sie auf die nächste Ebene, um Produkte gemäß Ihrer Produktdatenhierarchie anzuzeigen.

Creative Project verbindet bestätigte Assets mit dem referenzierten Produkt. Die Asset-Metadaten werden mit dem Produktverweis und grundlegenden Informationen auf der Registerkarte **Produktdaten** unter den Asset-Eigenschaften aktualisiert. Sie werden im Abschnitt mit den AEM Assets-Metadaten angezeigt.

>[!NOTE]
>
>Im Workflow **Produkt-Fotoshooting** (ohne Commerce-Integration) sind die bestätigten Bilder mit keinen Produkten verbunden.

### Zu Produktionsaufgabe wechseln {#move-to-production-task}

Durch diese Aufgabe werden die genehmigten Assets in den produktionsbereiten Ordner verschoben, damit sie zur Verwendung verfügbar sind.

1. Klicken Sie unter dem Projektordner auf die Schaltfläche mit den Auslassungspunkten unten rechts im [Aufgabenkarte](#tracking-project-progress) , um das Aufgabenelement im Workflow anzuzeigen.
1. Wählen Sie die **Zur Produktion wechseln** und klicken Sie dann auf die **Öffnen** in der Symbolleiste.

   ![Zur Produktion wechseln](assets/chlimage_1-160a.png)

1. Um die bestätigten Assets für das Fotoshooting vor dem Verschieben in den produktionsbereiten Ordner anzuzeigen, klicken Sie auf den Link **Bestätigte Assets anzeigen** unter der Projektminiatur auf der Aufgabenseite **Zur Produktion wechseln**.

   ![Seite der Aufgabe „Zur Produktion wechseln“](assets/chlimage_1-161a.png)

1. Geben Sie den Pfad des produktionsbereiten Ordners im Feld **Verschieben nach** ein.

   ![In Pfad verschieben](assets/chlimage_1-162a.png)

1. Klicks **Zur Produktion wechseln**. Schließen Sie die Bestätigungsmeldung. Die Assets werden in den angegebenen Pfad verschoben, und es wird automatisch ein Rotationsset für die bestätigten Assets für jedes Produkt basierend auf der Ordnerhierarchie erstellt.

1. Klicken Sie auf **Fertig** in der Symbolleiste. Der Workflow wird abgeschlossen, wenn der letzte Schritt als abgeschlossen markiert ist.

## Anzeigen von DAM-Asset-Metadaten {#viewing-dam-asset-metadata}

Nach erfolgter Bestätigung werden die Assets mit den entsprechenden Produkten verknüpft. Die [Eigenschaftenseite](/help/assets/manage-assets.md#editing-properties) der bestätigten Assets weist nunmehr die zusätzliche Registerkarte **Produktdaten** (verknüpfte Produktinformationen) auf. Auf dieser Registerkarte werden die Produktdetails, SKU-Nummer und weitere produktbezogene Details angezeigt, die das Asset verknüpfen. Klicken Sie auf **Bearbeiten** -Symbol, um eine Asset-Eigenschaft zu aktualisieren. Die produktbezogenen Informationen sind stets schreibgeschützt.

Klicken Sie auf den angezeigten Link, um zur entsprechenden Produktdetailseite in der Produktkonsole zu navigieren, mit der das Asset verknüpft ist.

## Anpassen der Workflows für Projekt-Fotoshootings {#customizing-the-project-photo-shoot-workflows}

Sie können die Workflows **Projekt-Fotoshootings** an Ihre Anforderungen anpassen. Dies ist eine optionale rollenbasierte Aufgabe, die Sie ausführen, um den Wert einer Variablen innerhalb des Projekts festzulegen. Später können Sie dann den konfigurierten Wert verwenden, um zu einer Entscheidung zu gelangen.

1. Klicken Sie auf das AEM-Logo und navigieren Sie zu **Instrumente** > **Workflow** > **Modelle** , um die **Workflow-Modelle** Seite.
1. Wählen Sie die **Produkt-Fotoshooting (Commerce-Integration)** oder **Produkt-Fotoshooting** Workflow und Klick **Bearbeiten** in der Symbolleiste, um den Workflow im Bearbeitungsmodus zu öffnen.
1. Öffnen Sie das seitliche Bedienfeld, suchen Sie den Schritt **Rollenbasierte Projektaufgabe erstellen** und ziehen Sie ihn in den Workflow.

   ![Rollenbasierte Projektaufgabe erstellen](assets/project-model-role-based.png)

1. Öffnen Sie den Schritt **Rollenbasierte Aufgabe**.
1. Geben Sie auf der Registerkarte **Aufgabe** einen Namen für die Aufgabe ein, der in der Aufgabenliste angezeigt wird. Sie können die Aufgabe auch einer Rolle zuweisen, die Standardpriorität festlegen, eine Beschreibung angeben und einen Fälligkeitszeitpunkt für die Aufgabe bestimmen.

   ![Workflow-Schritt konfigurieren](assets/project-task-step.png)

1. Geben Sie auf der Registerkarte **Routing** die Aktionen für die Aufgabe an. Um mehrere Aktionen hinzuzufügen, klicken Sie auf die **Element hinzufügen** -Link.

   ![Registerkarte „Routing“](assets/project-task-step-routing.png)

1. Klicken Sie nach dem Hinzufügen der Optionen auf **OK**, um die Änderungen zum Schritt hinzuzufügen.

1. Zurück im **Workflow-Modell** Fensterklick **Synchronisieren** , um die Änderungen des gesamten Workflows zu speichern. Durch Tippen oder Klicken auf **OK** für den Schritt werden die Änderungen nicht im Workflow gespeichert. Klicken Sie zum Speichern der Änderungen im Workflow auf **Synchronisieren**.

1. Öffnen Sie das seitliche Bedienfeld, suchen Sie den Workflow **Zum Schritt wechseln** und ziehen Sie ihn in den Workflow.

1. Öffnen Sie die **Goto** und klicken Sie auf **Prozess** Registerkarte.

1. Wählen Sie den **Target-Schritt** aus, um zu wechseln und anzugeben, dass **Routing-Ausdruck** ein ECMA-Skript ist. Geben Sie dann den folgenden Code im Feld **Skript** ein:

   ```javascript
   function check() {
   
   if (workflowData.getMetaDataMap().get("lastTaskAction","") == "Reject All") {
   
   return true
   
   }
   
   // set copywriter user in metadata
   
   var previousId = workflowData.getMetaDataMap().get("lastTaskCompletedBy", "");
   
   workflowData.getMetaDataMap().put("copywriter", previousId);
   
   return false;
   
   }
   ```

   >[!TIP]
   >
   >Einzelheiten zu Skripten in Workflow-Schritten finden Sie unter [Definieren einer Regel für eine ODER-Teilung](/help/sites-developing/workflows-models.md).

   ![Zu Skript wechseln](assets/project-workflow-goto.png)

1. Klicken Sie auf **OK**.

1. Klicks **Synchronisieren** , um den Workflow zu speichern.

Nachdem die Aufgabe [Zur Produktion wechseln](#move-to-production-task) abgeschlossen und dem Eigentümer zugewiesen wurde, wird eine neue Aufgabe angezeigt.

Die Benutzerin oder der Benutzer mit der **Eigentümerrolle** kann die Aufgabe abschließen und eine Aktion (in der Liste der in den Workflow-Schrittkonfigurationen hinzugefügten Aktionen) in der Liste im Kommentar-Popup auswählen.

>[!NOTE]
>
>Wenn Sie einen Server starten, speichert das Servlet für die Projektaufgabenliste die Zuordnungen zwischen Aufgabentypen und den unter `/libs/cq/core/content/projects/tasktypes` definierten URLs im Zwischenspeicher. Sie können danach die übliche Überlagerung durchführen und benutzerdefinierte Aufgabentypen hinzufügen, indem Sie sie unter `/apps/cq/core/content/projects/tasktypes` ablegen.
