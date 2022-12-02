---
title: Creative Project und PIM-Integration
seo-title: Creative Project and PIM Integration
description: Creative Project optimiert den gesamten Fotoaufnahme-Workflow, einschließlich Generierung einer Fotoshooting-Anfrage, Hochladen eines Fotoshootings, Zusammenarbeit bei einem Fotoshooting und Verpackung von bestätigten Assets
seo-description: Creative Project streamlines the entire photo shoot workflow that including generating a photo shoot request, uploading a photo shoot, collaborating on a photo shoot, and packaging approved assets
uuid: 09f27d36-e725-45cb-88d1-27383aedceed
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
discoiquuid: 0e5d0a45-c663-4d91-b793-03d39119d103
exl-id: c4eff50e-0d55-4a61-98fd-cc42138656cb
source-git-commit: 200b47070b7ead54ee54eea504bd960d4e0731d9
workflow-type: tm+mt
source-wordcount: '2989'
ht-degree: 100%

---


# Creative Project und PIM-Integration {#creative-project-and-pim-integration}

Als Marketer oder Kreativschaffender können Sie die Creative Project-Werkzeuge in Adobe Experience Manager (AEM) verwenden, um eCommerce-bezogene Produktfotografie und zugehörige kreative Prozesse innerhalb Ihrer Organisation zu verwalten.

Insbesondere können Sie Creative Project zur Optimierung der folgenden Aufgaben in Ihrem Fotoshooting-Workflow nutzen:

* Generieren einer Fotoshooting-Anfrage
* Hochladen eines Fotoshootings
* Zusammenarbeit an einem Fotoshooting
* Verpacken bestätigter Assets

>[!NOTE]
>
>Informationen zur Zuweisung von Benutzerrollen und Workflows zu bestimmen Benutzertypen finden Sie unter [Informationen zu Projekt-Benutzerrollen](/help/sites-authoring/projects.md#user-roles-in-a-project).

## Workflow „Produkt-Fotoshooting“  {#exploring-product-photo-shoot-workflows}

Creative Project bietet mehrere Projektvorlagen, die unterschiedlichen Projektanforderungen gerecht werden. Die Vorlage **Projekt für Produkt-Fotoshooting** ist im Lieferumfang enthalten. Diese Vorlage stellt Fotoshooting-Workflows bereit, mit denen Sie Anfragen für Produkt-Fotoshootings einleiten und verwalten können. Sie enthält darüber hinaus eine Reihe von Aufgaben, die es Ihnen ermöglichen, digitale Bilder für Produkte anhand geeigneter Bewertungs- und Bestätigungsabläufe zu erhalten.

## Erstellen eines Projekts für Produkt-Fotoshootings {#create-a-product-photo-shoot-project}

1. Klicken oder tippen Sie in der **Projektekonsole** auf **Erstellen** und wählen Sie danach in der Liste **Projekt erstellen** aus.

   ![Schaltfläche „Projekt erstellen“](assets/chlimage_1-132a.png)

1. Wählen Sie auf der Seite **Projekt erstellen** die Vorlage **Projekt für Produkt-Fotoshooting** aus und klicken oder tippen Sie auf **Weiter**.

   ![Projekt-Assistent](assets/chlimage_1-133a.png)

1. Geben Sie Details zum Projekt einschließlich Titel, Beschreibung und Fälligkeitsdaten ein. Fügen Sie Benutzer hinzu und weisen Sie ihnen verschiedene Rollen zu. Sie können auch ein Miniaturbild für das Projekt hinzufügen.

   ![Projektdetails](assets/chlimage_1-134a.png)

1. Tippen oder klicken Sie auf **Erstellen**. Eine Bestätigungsmeldung informiert Sie, dass das Projekt erstellt wurde.
1. Tippen oder klicken Sie auf **Fertig**, um zur **Projektekonsole** zurückzukehren. Sie können auch auf **Öffnen** tippen oder klicken, um die Assets innerhalb des Projekts anzuzeigen.

## Beginn der Arbeit an einem Projekt für Produkt-Fotoshooting {#starting-work-in-a-product-photo-shoot-project}

Um eine Fotoshooting-Anfrage einzuleiten, klicken oder tippen Sie auf ein Projekt und klicken Sie danach auf der Seite mit den Projektdetails auf **Arbeit hinzufügen**, um einen Workflow zu starten.

![Arbeit hinzufügen](assets/chlimage_1-135a.png)

Ein **Produkt-Fotoshooting-Projekt** umfasst folgende Workflows:

* Workflow **Produkt-Fotoshooting (Commerce-Integration)**: Dieser Workflow nutzt die Commerce-Integration in das PIM-System (Produktinformations-Management) zur automatischen Generierung einer Aufnahmenliste für die ausgewählten Produkte (Hierarchie). Sie können die Produktdaten als Teil der Asset-Metadaten anzeigen, nachdem der Workflow abgeschlossen wurde.
* Workflow **Produkt-Fotoshooting**: Dieser Workflow ermöglicht es Ihnen, eine Aufnahmenliste bereitzustellen, anstatt dies der Commerce-Integration zu überlassen. Dabei werden die hochgeladenen Bilder in einer CSV-Datei im Assets-Ordner des Projekts protokolliert.

Verwenden Sie den Workflow **Produkt-Fotoshooting (Commerce-Integration)** zur Zuordnung von Bild-Assets zu den Produkten in AEM. Dieser Workflow nutzt die Commerce-Integration zur Verknüpfung der genehmigten Bilder mit den vorhandenen Produktdaten unter dem Speicherort `/etc/commerce`.

Der Workflow **Produkt-Fotoshooting (Commerce-Integration)** umfasst die folgenden Aufgaben:

* Aufnahmenliste erstellen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Bewerten und bestätigen
* Zu Produktionsaufgabe wechseln

Wenn in AEM keine Produktinformationen verfügbar sind, verwenden Sie den Workflow **Produkt-Fotoshooting**, um Bild-Assets den Produkten auf der Basis der Informationen zuzuordnen, die Sie in eine CSV-Datei hochladen. Die CSV-Datei muss grundlegende Produktinformationen wie zum Beispiel Produkt-ID, Kategorie und Beschreibung enthalten. Der Workflow ruft bestätigte Assets für die Produkte ab.

Dieser Workflow umfasst die folgenden Aufgaben:

* Aufnahmenliste hochladen
* Fotoshooting hochladen
* Fotoaufnahme retuschieren
* Bewerten und bestätigen
* Zu Produktionsaufgabe wechseln

Sie können diesen Workflow mit der Workflow-Konfigurationsoption anpassen.

Beide Workflows umfassen Schritte zur Verknüpfung von Produkten mit ihren bestätigten Assets. Jeder Workflow umfasst die folgenden Schritte:

* Workflow-Konfiguration: Beschreibt die Optionen zur Anpassung des Workflows
* Starten eines Projekt-Workflows: Erläutert, wie ein Produkt-Fotoshooting gestartet wird
* Workflow-Aufgabendetails: Stellt Details von Aufgaben bereit, die im Workflow zur Verfügung stehen

## Verfolgen des Projektfortschritts {#tracking-project-progress}

Sie können den Fortschritt eines Projekts verfolgen, indem Sie die aktiven/abgeschlossenen Aufgaben im Projekt überwachen.

Verwenden Sie Folgendes, um den Fortschritt eines Projekts zu überwachen:

* Aufgabenkarte
* Aufgabenliste

Die Aufgabenkarte stellt den Gesamtfortschritt des Projekts dar. Sie wird nur dann auf der Seite „Projektdetails“ angezeigt, wenn das Projekt zugehörige Aufgaben aufweist. Die Aufgabenkarte zeigt den aktuellen Abschlussstatus des Projekts auf der Basis der abgeschlossenen Aufgaben an. Zukünftige Aufgaben werden nicht berücksichtigt.

Die Aufgabenkarte stellt die folgenden Detailinformationen bereit:

* Prozentsatz der aktiven Aufgaben
* Prozentsatz der abgeschlossenen Aufgaben

![Aufgabenkarte](assets/chlimage_1-136a.png)

Die Aufgabenliste stellt detaillierte Information zur aktuell aktiven Workflow-Aufgabe für das Projekt bereit. Um die Liste anzuzeigen, tippen oder klicken Sie auf die Aufgabenkarte. Die Aufgabenliste zeigt auch Metadaten wie Startdatum, Fälligkeitsdatum, Bevollmächtigter, Priorität und Status der Aufgabe an.

![Aufgabenliste](assets/chlimage_1-137a.png)

## Workflow-Konfiguration {#workflow-configuration}

Diese Aufgabe schließt die Zuweisung von Workflow-Schritten zu Benutzern auf Grundlage ihrer Rollen ein.

So konfigurieren Sie den Workflow **Produkt-Fotoshooting**:

1. Navigieren Sie zu **Werkzeuge** > **Workflows** und tippen Sie anschließend auf den Bereich **Modelle**, um die Seite **Workflow-Modelle** zu öffnen.
1. Wählen Sie den Workflow **Produkt-Fotoshooting** aus und tippen Sie auf der Symbolleiste auf das Symbol **Bearbeiten**, um den Workflow im Bearbeitungsmodus zu öffnen.

   ![Modell für Produkt-Fotoshooting](assets/chlimage_1-138a.png)

1. Öffnen Sie auf der Seite **Workflow „Produkt-Fotoshooting“** eine Projektaufgabe. Öffnen Sie z. B. die Aufgabe **Aufnahmenliste hochladen**.

   ![Modell bearbeiten](assets/project-photo-shoot-workflow-model.png)

1. Tippen oder klicken Sie auf die Registerkarte **Aufgabe**, um Folgendes zu konfigurieren:

   * Name der Aufgabe
   * Standardbenutzer(rolle), der/die die Aufgabe empfängt
   * Standardpriorität der Aufgabe, die in der Aufgabenliste des Benutzers angezeigt wird
   * Aufgabenbeschreibung, die angezeigt wird, wenn der Bevollmächtigte die Aufgabe öffnet
   * Fälligkeitsdatum für eine Aufgabe, das auf Grundlage des Zeitpunkts des Aufgabenbeginns berechnet wird

1. Klicken Sie auf **OK**, um die Konfigurationseinstellungen zu speichern.

Sie können die zusätzlichen Aufgaben für den Workflow **Produkt-Fotoshooting** auf ähnliche Weise konfigurieren.

Gehen Sie in ähnlicher Weise vor, um die Aufgaben im Workflow **Produkt-Fotoshooting (Commerce-Integration)** zu konfigurieren.

## Starten eines Projekt-Workflows {#starting-a-project-workflow}

In diesem Abschnitt wird beschrieben, wie das Produktinformations-Management in Ihr Creative-Projekt integriert wird.

1. Navigieren Sie zu einem Produkt-Fotoshooting-Projekt und tippen oder klicken Sie auf der Karte **Workflows** auf das Symbol **Arbeit hinzufügen**.
1. Wählen Sie die Workflow-Karte **Produkt-Fotoshooting (Commerce-Integration)** aus, um den entsprechenden Workflow zu starten **.** Wenn die Produktinformationen nicht unter `/etc/commerce` verfügbar sind, wählen Sie die Workflow-Karte **Produkt-Fotoshooting (Commerce-Integration)** aus, um den entsprechenden Workflow zu starten **.**

   ![Workflow-Assistent](assets/chlimage_1-140a.png)

1. Tippen oder klicken Sie auf **Weiter**, um den Workflow im Projekt einzuleiten.
1. Geben Sie auf der nächsten Seite Details zum Workflow ein.

   ![Workflow-Details](assets/chlimage_1-141a.png)

1. Tippen oder klicken Sie auf **Übermitteln**, um den Fotoshooting-Workflow zu starten. Die Seite mit den Details zum Fotoshooting-Projekt wird angezeigt.

   ![Projektseite mit neuem Workflow](assets/chlimage_1-142a.png)

### Workflow-Aufgabendetails {#workflow-tasks-details}

Der Fotoshooting-Workflow umfasst mehrere Aufgaben. Jede Aufgabe wird auf Grundlage der für die Aufgabe definierten Konfiguration einer Benutzergruppe zugewiesen.

#### Aufnahmenlistenaufgabe erstellen {#create-shot-list-task}

Die Aufgabe **Aufnahmenliste erstellen** ermöglicht dem Projekteigentümer die Auswahl von Produkten, für die Bilder benötigt werden. Je nach vom Benutzer ausgewählter Option wird eine CSV-Datei generiert, die grundlegende Produktinformationen enthält.

1. Tippen oder klicken Sie im Projektordner auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um die Aufgabe im Workflow anzuzeigen.

   ![Aufgabenkarte](assets/chlimage_1-143a.png)

1. Wählen Sie die Aufgabe **Aufnahmenliste erstellen** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Aufnahmenlisten-Aufgabe öffnen](assets/chlimage_1-144a.png)

1. Überprüfen Sie die Aufgabendetails und tippen/klicken Sie dann auf die Schaltfläche **Aufnahmenliste erstellen**.

   ![Details der Aufnahmenlisten-Aufgabe](assets/chlimage_1-145a.png)

1. Wählen Sie Produkte, für die Produktdaten ohne verknüpfte Bilder vorhanden sind.

   ![Auswählen von Produkten](assets/chlimage_1-146a.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Aufnahmenliste hinzufügen**, um eine CSV-Datei mit einer Liste all dieser Produkte zu erstellen. Eine Meldung betätigt, dass die Aufnahmenliste für die ausgewählten Produkte erstellt wird. Klicken Sie auf **Schließen**, um den Workflow abzuschließen.

1. Nach dem Erstellen einer Aufnahmenliste wird der Link **Aufnahmenliste anzeigen** angezeigt. Um weitere Produkte in die Aufnahmenliste aufzunehmen, tippen oder klicken Sie auf **Zu Aufnahmenliste hinzufügen**. In diesem Fall werden die Daten an die anfangs erstellte Aufnahmenliste angehängt.

   ![Zu Aufnahmenliste hinzufügen](assets/chlimage_1-147a.png)

1. Tippen oder klicken Sie auf **Aufnahmenliste anzeigen**, um die neue Aufnahmenliste anzuzeigen.

   ![Aufnahmenliste anzeigen](assets/chlimage_1-148a.png)

   Um die vorhandenen Daten zu bearbeiten oder neue Daten hinzuzufügen, tippen/klicken Sie in der Symbolleiste auf **Bearbeiten**. Sie können nur die Felder **Produkt** und **Beschreibung** bearbeiten.

   ![Aufnahmenliste bearbeiten](assets/chlimage_1-149a.png)

   Klicken Sie nach dem Aktualisieren der Datei auf der Symbolleiste auf **Speichern**, um die Datei zu speichern.

1. Klicken Sie nach dem Hinzufügen der Produkte auf der Aufgabendetailseite **Aufnahmenliste erstellen** auf das Symbol **Fertigstellen**, um die Aufgabe als abgeschlossen zu markieren. Sie können wahlweise einen Kommentar hinzufügen.

Durch Abschluss der Aufgabe werden die folgenden Änderungen innerhalb des Projekts eingeführt:

* Der Produkthierarchie entsprechende Assets werden in einem Ordner mit demselben Namen wie der Titel des Workflow erstellt.
* Die Metadaten für die Assets werden in der Konsole „Assets“ bearbeitbar, sogar bevor der Fotograf die Bilder zur Verfügung stellt.
* Es wird ein Fotoshooting-Ordner erstellt, in dem die vom Fotografen bereitgestellten Bilder gespeichert werden. Dieser Ordner enthält Unterordner für jeden Produkteintrag in der Aufnahmenliste.

### Aufnahmenlistenaufgabe hochladen {#upload-shot-list-task}

Diese Aufgabe ist Teil des Produkt-Fotoshooting-Workflows. Diese Aufgabe führen Sie aus, wenn in AEM keine Produktinformationen verfügbar sind. In diesem Fall laden Sie eine Liste von Produkten in einer CSV-Datei hoch, für die Bild-Assets erforderlich sind. Anhand der Informationen in der CSV-Datei ordnen Sie die Bild-Assets den Produkten zu. Bei der Datei muss es sich um eine CSV-Datei mit dem Namen `shotlist.csv` handeln.

Verwenden Sie den Link **Aufnahmenliste anzeigen** unter der Projektkarte im vorherigen Verfahren, um eine Beispieldatei im CSV-Format herunterzuladen. Überprüfen Sie die Beispieldatei, um sich mit dem üblichen Inhalt einer CSV-Datei vertraut zu machen.

Die Produktliste oder CSV-Datei kann Felder wie z. B. **Kategorie, Produkt, ID, Beschreibung** und **Pfad** enthalten. Das Feld **ID** ist obligatorisch und enthält die Produkt-ID. Die anderen Felder sind optional.

Ein Produkt kann zu einer bestimmten Kategorie gehören. Die Produktkategorie kann in der CSV-Datei unterhalb der Spalte **Kategorie** aufgeführt werden. Das Feld **Produkt** enthält den Namen des Produkts. Geben Sie im Feld **Beschreibung** die Produktbeschreibung oder Anleitungen für Fotografen ein.

1. Tippen oder klicken Sie im Projektordner auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um eine Liste der Aufgaben im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Aufnahmenliste hochladen** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Aufnahmenliste hochladen](assets/chlimage_1-150a.png)

1. Überprüfen Sie die Aufgabendetails und tippen oder klicken Sie dann auf die Schaltfläche **Aufnahmenliste hochladen**.

   ![Hochladen der Aufnahmenliste](assets/chlimage_1-151a.png)

1. Tippen oder klicken Sie auf die Schaltfläche **Aufnahmenliste hochladen**, um die CSV-Datei hochzuladen. Der Workflow erkennt diese Datei als eine Quelle, die zum Extrahieren von Produktdaten für die nächste Aufgabe verwendet werden kann.
1. Laden Sie eine CSV-Datei hoch, die Produktinformationen im entsprechenden Format enthält. Der Link **Hochgeladene Assets anzeigen** wird unterhalb der Karte angezeigt, nachdem die CSV-Datei hochgeladen wurde.

   ![Produktinformationen hochladen](assets/chlimage_1-152a.png)

   Klicken Sie auf das Symbol **Fertig stellen**, um diese Aufgabe abzuschließen.

1. Tippen/klicken Sie auf das Symbol **Fertigstellen**, um die Aufgabe abzuschließen.

### Aufgabe „Fotoshooting hochladen“ {#upload-photo-shoot-task}

Als Redakteur können Sie Aufnahmen für Produkte hochladen, die in der Datei **shotlist.csv** aufgeführt sind, welche in der vorherigen Aufgabe erstellt oder hochgeladen wurde.

Der Name der Bilder für den Upload sollte mit `<ProductId_>` beginnen, wobei die `ProductId` aus dem Feld **ID** in der Datei `shotlist.csv` stammt. Beispiel: Für ein Produkt in der Aufnahmenliste mit der **ID** `397122` können Sie Dateien hochladen, die die Namen `397122_lowlight.png`, `397122_highcontrast.jpg` usw. aufweisen.

Sie können entweder die Bilder direkt hochladen oder eine ZIP-Datei hochladen, die die Bilder enthält. Basierend auf ihren Namen werden die Bilder in entsprechenden Produktordnern innerhalb des Ordners Fotoshooting abgelegt.

1. Tippen oder klicken Sie im Projektordner rechts unten auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um die Aufgabe im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Fotoshooting hochladen** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Fotoshooting hochladen](assets/chlimage_1-153a.png)

1. Klicken Sie auf **Fotoshooting hochladen** und laden Sie die Bilder des Fotoshootings hoch.
1. Tippen oder klicken Sie auf der Symbolleiste auf das Symbol **Fertigstellen**, um die Aufgabe abzuschließen.

### Aufgabe „Fotoaufnahme retuschieren“ {#retouch-photo-shoot-task}

Wenn Sie Bearbeitungsrechte haben, führen Sie die Aufgabe **Fotoaufnahme retuschieren** aus, um die in den Ordner „Fotoshooting“ hochgeladenen Bilder zu bearbeiten.

1. Tippen oder klicken Sie im Projektordner rechts unten auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um die Aufgabe im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Fotoaufnahme retuschieren** aus und tippen/klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Fotoaufnahme retuschieren](assets/chlimage_1-154a.png)

1. Tippen oder klicken Sie auf der Seite **Fotoaufnahme retuschieren** auf den Link **Hochgeladene Assets anzeigen**, um die hochgeladenen Bilder zu durchsuchen.

   ![Hochgeladene Assets anzeigen](assets/chlimage_1-155a.png)

   Falls erforderlich, bearbeiten Sie die Bilder mit einer Adobe Creative Cloud-Applikation.

   ![Asset bearbeiten](assets/chlimage_1-156a.png)

1. Tippen oder klicken Sie auf der Symbolleiste auf das Symbol **Fertigstellen**, um die Aufgabe abzuschließen.

### Aufgabe „Überprüfen und bestätigen“ {#review-and-approve-task}

In dieser Aufgabe prüfen Sie die Fotoaufnahmen, die von einem Fotografen hochgeladen wurden, und markieren die Aufnahmen als für die Nutzung freigegeben.

1. Tippen oder klicken Sie im Projektordner rechts unten auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um die Aufgabe im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Überprüfen und bestätigen** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Überprüfen und bestätigen](assets/chlimage_1-157a.png)

1. Weisen Sie auf der Seite **Überprüfen und bestätigen** die Überprüfungsaufgabe einer Rolle zu und klicken Sie danach auf **Überprüfen**, um mit der Überprüfung der hochgeladenen Produktbilder zu beginnen.

   ![Überprüfen von Assets beginnen](assets/chlimage_1-158a.png)

1. Wählen Sie ein Produktbild aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Genehmigen**, um das Produktbild als genehmigt zu markieren. Sobald Sie ein Bild genehmigt haben, wird darüber ein „Genehmigt“-Banner angezeigt.

   ![Genehmigen eines Bildes](assets/chlimage_1-159a.png)

1. Tippen oder klicken Sie auf **Fertigstellen**. Die bestätigten Bilder werden mit den leeren Assets verknüpft, die erstellt wurden.

Sie können Produkte ohne Bilder übergehen. Zu einem späteren Zeitpunkt können Sie zur Aufgabe zurückkehren und sie nach Erledigung als abgeschlossen kennzeichnen.

Mithilfe der Assets-Benutzeroberfläche können Sie zu den Projekt-Assets navigieren und die genehmigten Bilder überprüfen.

Tippen oder klicken Sie auf die nächste Ebene, um Produkte entsprechend Ihrer Produktdatenhierarchie anzuzeigen.

Creative Project verbindet bestätigte Assets mit dem referenzierten Produkt. Die Asset-Metadaten werden mit dem Produktverweis und grundlegenden Informationen auf der Registerkarte **Produktdaten** unter den Asset-Eigenschaften aktualisiert. Sie werden im Abschnitt mit den AEM Assets-Metadaten angezeigt.

>[!NOTE]
>
>Im Workflow **Produkt-Fotoshooting** (ohne Commerce-Integration) sind die bestätigten Bilder mit keinen Produkten verbunden.

### Zu Produktionsaufgabe wechseln {#move-to-production-task}

Mit dieser Aufgabe werden die bestätigten Assets in den produktionsbereiten Ordner verschoben, damit sie verwendet werden können.

1. Tippen oder klicken Sie im Projektordner rechts unten auf der [Aufgabenkarte](#tracking-project-progress) auf die Ellipsen, um die Aufgabe im Workflow anzuzeigen.
1. Wählen Sie die Aufgabe **Zur Produktion wechseln** aus und tippen oder klicken Sie dann auf der Symbolleiste auf das Symbol **Öffnen**.

   ![Zur Produktion wechseln](assets/chlimage_1-160a.png)

1. Um die bestätigten Assets für das Fotoshooting vor dem Verschieben in den produktionsbereiten Ordner anzuzeigen, klicken Sie auf den Link **Bestätigte Assets anzeigen** unter der Projektminiatur auf der Aufgabenseite **Zur Produktion wechseln**.

   ![Seite der Aufgabe „Zur Produktion wechseln“](assets/chlimage_1-161a.png)

1. Geben Sie den Pfad des produktionsbereiten Ordners im Feld **Verschieben nach** ein.

   ![In Pfad verschieben](assets/chlimage_1-162a.png)

1. Tippen oder klicken Sie auf **Zur Produktion wechseln**. Schließen Sie die Bestätigungsmeldung. Die Assets werden in den angegebenen Pfad verschoben, und es wird automatisch ein Rotationsset für die bestätigten Assets für jedes Produkt basierend auf der Ordnerhierarchie erstellt.

1. Tippen/klicken Sie in der Symbolleiste auf das Symbol **Fertig stellen**. Der Workflow wird mit Kennzeichnung des letzten Schritts als fertig gestellt abgeschlossen.

## Anzeigen von DAM-Asset-Metadaten {#viewing-dam-asset-metadata}

Nach erfolgter Bestätigung werden die Assets mit den entsprechenden Produkten verknüpft. Die [Eigenschaftenseite](/help/assets/manage-assets.md#editing-properties) der bestätigten Assets weist nunmehr die zusätzliche Registerkarte **Produktdaten** (verknüpfte Produktinformationen) auf. Auf dieser Registerkarte werden die Produktdetails, SKU-Nummer und weitere produktbezogene Details angezeigt, die das Asset verknüpfen. Tippen oder klicken Sie auf das Symbol **Bearbeiten**, um die Eigenschaften eines Assets zu aktualisieren. Die produktbezogenen Informationen sind stets schreibgeschützt.

Tippen oder klicken Sie auf den angezeigten Link, um zur entsprechenden Produktdetailseite in der Produktekonsole zu navigieren, mit der das Asset verknüpft ist.

## Anpassen der Workflows für Projekt-Fotoshootings {#customizing-the-project-photo-shoot-workflows}

Sie können die Workflows **Projekt-Fotoshootings** an Ihre Anforderungen anpassen. Dies ist eine optionale rollenbasierte Aufgabe, die zum Festlegen des Werts einer Variablen innerhalb des Projekts durchgeführt wird. Sie können danach den konfigurierten Wert zur Entscheidungsfindung heranziehen.

1. Klicken oder tippen Sie auf das AEM-Logo und navigieren Sie dann zu **Tools** > **Workflow** > **Modelle**, um die Seite **Workflow-Modelle** zu öffnen.
1. Wählen Sie den Workflow **Produkt-Fotoshooting (Commerce-Integration)** oder **Produkt-Fotoshooting** aus und klicken oder tippen Sie auf der Symbolleiste auf **Bearbeiten**, um den Workflow im Bearbeitungsmodus zu öffnen.
1. Öffnen Sie das seitliche Bedienfeld, suchen Sie den Schritt **Rollenbasierte Projektaufgabe erstellen** und ziehen Sie ihn in den Workflow.

   ![Rollenbasierte Projektaufgabe erstellen](assets/project-model-role-based.png)

1. Öffnen Sie den Schritt **Rollenbasierte Aufgabe**.
1. Geben Sie auf der Registerkarte **Aufgabe** einen Namen für die Aufgabe ein, der in der Aufgabenliste angezeigt wird. Sie können die Aufgabe auch einer Rolle zuweisen, die Standardpriorität festlegen, eine Beschreibung angeben und einen Fälligkeitszeitpunkt für die Aufgabe bestimmen.

   ![Workflow-Schritt konfigurieren](assets/project-task-step.png)

1. Geben Sie auf der Registerkarte **Routing** die Aktionen für die Aufgabe an. Um mehrere Aktionen hinzuzufügen, tippen oder klicken Sie auf den Link **Element hinzufügen**.

   ![Registerkarte „Routing“](assets/project-task-step-routing.png)

1. Klicken Sie nach dem Hinzufügen der Optionen auf **OK**, um die Änderungen zum Schritt hinzuzufügen.

1. Tippen oder klicken Sie zurück im **Workflow-Modell** auf **Synchronisieren**, um die Änderungen des gesamten Workflows zu speichern. Durch Tippen oder Klicken auf **OK** für den Schritt werden die Änderungen nicht im Workflow gespeichert. Tippen oder klicken Sie zum Speichern der Änderungen im Workflow auf **Speichern**.

1. Öffnen Sie das seitliche Bedienfeld, suchen Sie den Workflow **Zum Schritt wechseln** und ziehen Sie ihn in den Workflow.

1. Öffnen Sie die Aufgabe **Gehe zu** und tippen oder klicken Sie auf die Registerkarte **Prozess**.

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

1. Tippen oder klicken Sie auf **OK**.

1. Tippen oder klicken Sie auf **Synchronisieren**, um den Workflow zu speichern.

Nachdem die Aufgabe [Zur Produktion wechseln](#move-to-production-task) abgeschlossen und dem Eigentümer zugewiesen wurde, wird eine neue Aufgabe angezeigt.

Die Benutzerin oder der Benutzer mit der **Eigentümerrolle** kann die Aufgabe abschließen und eine Aktion (in der Liste der in den Workflow-Schrittkonfigurationen hinzugefügten Aktionen) in der Liste im Kommentar-Popup auswählen.

>[!NOTE]
>
>Wenn Sie einen Server starten, speichert das Servlet für die Projektaufgabenliste die Zuordnungen zwischen Aufgabentypen und den unter `/libs/cq/core/content/projects/tasktypes` definierten URLs im Zwischenspeicher. Sie können danach die übliche Überlagerung durchführen und benutzerdefinierte Aufgabentypen hinzufügen, indem Sie sie unter `/apps/cq/core/content/projects/tasktypes` ablegen.
