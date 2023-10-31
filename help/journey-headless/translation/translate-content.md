---
title: Übersetzen von Inhalten
description: Verwenden Sie den Übersetzungs-Connector und die Regeln, um Ihre Headless-Inhalte zu übersetzen.
exl-id: a2c2bb9f-97b9-42fd-9bd1-e75c113fb514
source-git-commit: f627bc2b58578df1b4ff6c95d87f0c64daafa1c7
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 86%

---

# Übersetzen von Inhalten {#translate-content}

Verwenden Sie die Übersetzungsintegration und -regeln, um Ihre Headless Content zu übersetzen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM Headless-Übersetzungs-Tour, [Konfigurieren von Übersetzungsregeln](translation-rules.md), haben Sie gelernt, wie Sie die Übersetzungsregeln von AEM verwenden, um Ihre zu übersetzenden Inhalte zu bestimmen. Sie sollten jetzt:

* Verstehen, was die Übersetzungsregeln bewirken.
* Eigene Übersetzungsregeln definieren können.

Nachdem Sie nun Ihren Connector und Ihre Übersetzungsregeln eingerichtet haben, führt Sie dieser Artikel durch den nächsten Schritt der Übersetzung Ihrer Headless-Inhalte.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie AEM-Übersetzungsprojekte zusammen mit dem Connector und Ihren Übersetzungsregeln verwenden können, um Inhalte zu übersetzen. Nach dem Lesen dieses Dokuments sollten Sie Folgendes tun:

* Verstehen, was ein Übersetzungsprojekt ist.
* Erstellen von Übersetzungsprojekten.
* Übersetzungsprojekte verwenden können, um Ihre Headless-Inhalte zu übersetzen.

## Erstellen eines Übersetzungsprojekts {#creating-translation-project}

Mithilfe von Übersetzungsprojekten können Sie die Übersetzung von AEM Headless-Inhalten verwalten. Ein Übersetzungsprojekt sammelt die Inhalte, die in andere Sprachen übersetzt werden sollen, an einem Ort, um einen zentralen Überblick über den Übersetzungsaufwand zu erhalten.

Wenn einem Übersetzungsprojekt Inhalte hinzugefügt werden, wird ein Übersetzungsauftrag für sie erstellt. Aufträge beinhalten Befehle und Statusinformationen, mit denen Sie die Workflows für menschliche und maschinelle Übersetzungen, die für die Ressourcen ausgeführt werden, verwalten.

Übersetzungsprojekte können auf zwei Arten erstellt werden:

1. Wählen Sie den Sprachstamm des Inhalts aus und lassen Sie AEM das Übersetzungsprojekt automatisch basierend auf dem Inhaltspfad erstellen.
1. Erstellen Sie ein leeres Projekt und wählen Sie manuell die Inhalte aus, die zum Übersetzungsprojekt hinzugefügt werden sollen.

Beide Ansätze unterscheiden sich nur je nach der Person, die die Übersetzung durchführt:

* Der Übersetzungsprojekt-Manager (TPM) benötigt häufig die Flexibilität, die Inhalte manuell für das Übersetzungsprojekt auszuwählen.
* Wenn der Inhaltsverantwortliche auch für die Übersetzung verantwortlich ist, ist es oft einfacher, das Projekt anhand des ausgewählten Inhaltspfads automatisch von AEM erstellen zu lassen.

Auf beide Ansätze wird in den folgenden Abschnitten eingegangen.

### Automatisches Erstellen eines Übersetzungsprojekts basierend auf dem Inhaltspfad {#automatically-creating}

Für Inhaltsverantwortliche, die auch für die Übersetzung verantwortlich ist, ist es oft einfacher, das Projekt anhand des ausgewählten Inhaltspfads automatisch von AEM erstellen zu lassen. Gehen Sie wie folgt vor, um von AEM automatisch ein Übersetzungsprojekt auf der Grundlage Ihres Inhaltspfads erstellen zu lassen:

1. Gehen Sie zu **Navigation** > **Assets** > **Dateien**. Beachten Sie, dass Headless-Inhalte in AEM als Assets gespeichert werden. Diese werden auch als Inhaltsfragmente bezeichnet.
1. Wählen Sie den Sprachstamm Ihres Projekts aus. In diesem Fall `/content/dam/wknd/en` ausgewählt ist.
1. Tippen oder klicken Sie auf die Auswahlleiste und zeigen Sie den Bereich **Verweise** an.
1. Tippen oder klicken **Sprachkopien**.
1. Aktivieren Sie das Kontrollkästchen **Sprachkopien**.
1. Erweitern Sie den Abschnitt **Sprachkopien aktualisieren** unten im Bereich „Verweise“.
1. Wählen Sie in der Dropdown-Liste **Projekt** die Option **Übersetzungsprojekt(e) erstellen** aus.
1. Geben Sie einen passenden Titel für Ihr Übersetzungsprojekt an.
1. Tippen oder klicken Sie auf **Start**.

![Erstellen eines Übersetzungsprojekts](assets/create-translation-project.png)

Sie erhalten eine Nachricht, dass das Projekt erstellt wurde.

>[!NOTE]
>
>Es wird davon ausgegangen, dass die erforderliche Sprachstruktur für die Übersetzungssprachen bereits im Rahmen der [Definition Ihrer Inhaltsstruktur erstellt wurde.](getting-started.md#content-structure) Dies sollte in Zusammenarbeit mit dem Inhaltsarchitekten erfolgen.
>
>Wenn die Sprachordner nicht vorab erstellt werden, können Sie keine Sprachkopien, wie in den vorherigen Schritten beschrieben, erstellen.

### Manuelles Erstellen eines Übersetzungsprojekts durch Auswahl von Inhalten {#manually-creating}

Für Übersetzungsprojekt-Manager ist es oft erforderlich, bestimmte Inhalte, die in ein Übersetzungsprojekt aufgenommen werden sollen, manuell auszuwählen. Um ein solches manuelles Übersetzungsprojekt zu erstellen, müssen Sie zunächst ein leeres Projekt erstellen und dann die hinzuzufügenden Inhalte auswählen.

1. Gehen Sie zu **Navigation** > **Projekte**.
1. Tippen oder klicken Sie auf **Erstellen** > **Ordner**, um einen Ordner für Ihre Projekte zu erstellen.
   * Dies ist optional, aber hilfreich, um Ihre Übersetzungsarbeit zu organisieren.
1. Im **Ordner erstellen** ein Fenster, fügen Sie eine **Titel** für den Ordner und tippen oder klicken Sie dann auf **Erstellen**.

   ![Erstellen von Projektordnern](assets/create-project-folder.png)

1. Tippen oder klicken Sie auf den Ordner, um ihn zu öffnen.
1. Tippen oder klicken Sie in Ihrem neuen Projektordner auf **Erstellen** > **Projekt**.
1. Projekte basieren auf Vorlagen. Tippen oder klicken Sie auf die Vorlage **Übersetzungsprojekt**, um sie auszuwählen, und tippen oder klicken Sie auf **Weiter**.

   ![Übersetzungsprojektvorlage auswählen](assets/select-translation-project-template.png)

1. Geben Sie in der Registerkarte **Allgemein** einen Namen für Ihr neues Projekt ein.

   ![Registerkarte „Allgemein“ des Projekts](assets/project-basic-tab.png)

1. Im **Erweitert** Registerkarte, verwenden Sie die **Zielsprache** die Sprachen auswählen, in die der Inhalt übersetzt werden soll. Tippen oder klicken Sie auf **Erstellen**.

   ![Registerkarte „Erweitert“ des Projekts](assets/project-advanced-tab.png)

1. Tippen oder klicken Sie im Bestätigungsdialogfeld auf **Öffnen**.

   ![Bestätigungsdialogfeld für das Projekt](assets/project-confirmation-dialog.png)

Das Projekt wurde erstellt, enthält jedoch keine zu übersetzenden Inhalte. Im nächsten Abschnitt wird beschrieben, wie das Projekt strukturiert ist und wie Inhalte hinzugefügt werden.

## Verwenden eines Übersetzungsprojekts {#using-translation-project}

Übersetzungsprojekte dienen dazu, alle Inhalte und Aufgaben im Zusammenhang mit einem Übersetzungsangebot an einem Ort zu erfassen, damit die Übersetzung einfach verwaltet werden kann.

So zeigen Sie das Übersetzungsprojekt an:

1. Gehen Sie zu **Navigation** > **Projekte**.
1. Tippen oder klicken Sie auf das Projekt, das im vorherigen Abschnitt erstellt wurde.

![Übersetzungsprojekt](assets/translation-project.png)

Das Projekt ist in mehrere Karten unterteilt.

* **Zusammenfassung**: Diese Karte zeigt die grundlegenden Kopfzeileninformationen des Projekts, einschließlich des Verantwortlichen, der Sprache und des Übersetzungsdienstleisters.
* **Übersetzungsauftrag** - Diese Karte bzw. diese Karten bieten einen Überblick über den tatsächlichen Übersetzungsauftrag, einschließlich Status, Anzahl der Assets usw. Im Allgemeinen gibt es pro Sprache einen Auftrag, wobei der ISO-2-Sprach-Code an den Auftragsnamen angehängt wird.
* **Team**: Auf dieser Karte werden die Benutzer angezeigt, die an diesem Übersetzungsprojekt mitarbeiten. Diese Tour behandelt dieses Thema nicht.
* **Aufgaben**: Zusätzliche Aufgaben im Zusammenhang mit der Übersetzung der Inhalte, z. B. zum Erstellen von Elementen oder Workflow-Elementen. Diese Tour behandelt dieses Thema nicht.

Wie Sie ein Übersetzungsprojekt verwenden, hängt davon ab, wie es erstellt wurde: entweder automatisch durch AEM oder manuell.

### Verwenden eines automatisch erstellten Übersetzungsprojekts {#using-automatic-project}

Beim automatischen Erstellen des Übersetzungsprojekts bewertet AEM die Headless-Inhalte unter dem von Ihnen ausgewählten Pfad anhand der zuvor definierten Übersetzungsregeln. Basierend auf dieser Auswertung extrahiert es die Inhalte, die übersetzt werden müssen, in ein neues Übersetzungsprojekt.

So sehen Sie die Details der Headless-Inhalte in diesem Projekt:

1. Tippen oder klicken Sie unten im **Übersetzungsauftrag** Karte.
1. Im Fenster **Übersetzungsauftrag** werden alle Elemente des Auftrags aufgelistet.
   ![Detail des Übersetzungsauftrags](assets/translation-job-detail.png)
1. Tippen oder klicken Sie auf eine Zeile, um die Details dieser Zeile anzuzeigen. Dabei ist zu beachten, dass eine Zeile mehrere zu übersetzende Inhaltselemente darstellen kann.
1. Tippen oder klicken Sie auf das Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. die Option, es aus dem Auftrag zu löschen oder in den Konsolen „Inhaltsfragmente“ oder „Assets“ anzuzeigen.
   ![Optionen für Übersetzungsaufträge](assets/translation-job-options.png)

Normalerweise beginnt der Inhalt des Übersetzungsauftrags im Status **Entwurf**, wie in der Spalte **Status** im Fenster **Übersetzungsauftrag** angegeben.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück und tippen oder klicken Sie auf die Pfeil-Schaltfläche oben in der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung verfolgen, indem Sie zum Fenster **Übersetzungsauftrag** zurückkehren und in der Spalte **Status** der Einträge nachsehen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Menschliche Übersetzung ermöglicht mehr Interaktion, sprengt aber den Rahmen dieser Tour.

### Verwenden eines manuell erstellten Übersetzungsprojekts {#using-manual-project}

Beim manuellen Erstellen eines Übersetzungsprojekts erstellt AEM die erforderlichen Aufträge, wählt jedoch nicht automatisch die einzuschließenden Inhalte aus. Dadurch kann der Übersetzungsprojektmanager flexibel entscheiden, welche Inhalte übersetzt werden sollen.

So fügen Sie einem Übersetzungsauftrag Inhalte hinzu:

1. Tippen oder klicken Sie auf die Schaltfläche mit den Auslassungszeichen unten in einer der Karten **Übersetzungsauftrag**.
1. Stellen Sie sicher, dass der Auftrag keinen Inhalt enthält. Tippen oder klicken Sie auf die Schaltfläche **Hinzufügen** oben im Fenster und wählen Sie dann aus der Dropdown-Liste **Assets/Seiten** aus.

   ![Leerer Übersetzungsauftrag](assets/empty-translation-job.png)

1. Ein Pfad-Browser wird geöffnet, in dem Sie auswählen können, welche Inhalte hinzugefügt werden sollen. Suchen Sie Ihre Inhalte und tippen oder klicken Sie zur Auswahl darauf.

   ![Pfad-Browser](assets/path-browser.png)

1. Tippen oder klicken Sie auf **Auswählen**, um die ausgewählten Inhalte zum Auftrag hinzuzufügen.
1. Geben Sie im Dialogfeld **Übersetzen** an, dass Sie eine **Sprachkopie erstellen** möchten.

   ![Sprachkopie erstellen](assets/translate-copy-master.png)

1. Der Inhalt ist jetzt im Auftrag enthalten.

   ![Zum Übersetzungsauftrag hinzugefügte Inhalte](assets/content-added.png)

1. Tippen oder klicken Sie auf das Kontrollkästchen für ein Zeilenelement, um weitere Optionen anzuzeigen, z. B. die Option, es aus dem Auftrag zu löschen oder in den Konsolen „Inhaltsfragmente“ oder „Assets“ anzuzeigen.
   ![Optionen für Übersetzungsaufträge](assets/translation-job-options-manual.png)

1. Wiederholen Sie diese Schritte, um alle erforderlichen Inhalte in den Auftrag einzuschließen.

>[!TIP]
>
>Der Pfad-Browser ist ein leistungsstarkes Tool, mit dem Sie Inhalte suchen, filtern und darin navigieren können. Tippen oder klicken Sie auf die Schaltfläche **Nur Inhalt/Filter** zum Umschalten des Seitenbereichs und zum Einblenden erweiterter Filter wie **Änderungsdatum** oder **Übersetzungsstatus**.
>
>Weitere Informationen zum Pfad-Browser finden Sie im [Abschnitt mit zusätzlichen Ressourcen](#additional-resources).

Sie können die vorherigen Schritte verwenden, um den erforderlichen Inhalt zu allen Sprachen (Aufträgen) für das Projekt hinzuzufügen. Nachdem Sie alle Inhalte ausgewählt haben, können Sie mit der Übersetzung beginnen.

Normalerweise beginnt der Inhalt des Übersetzungsauftrags im Status **Entwurf**, wie in der Spalte **Status** im Fenster **Übersetzungsauftrag** angegeben.

Um den Übersetzungsauftrag zu starten, kehren Sie zur Übersicht des Übersetzungsprojekts zurück und tippen oder klicken Sie auf die Pfeil-Schaltfläche oben in der Karte **Übersetzungsauftrag** und wählen Sie **Starten** aus.

![Übersetzungsauftrag starten](assets/start-translation-job-manual.png)

AEM kommuniziert nun mit Ihrer Übersetzungskonfiguration und dem Connector, um den Inhalt an den Übersetzungsdienstleister zu senden. Sie können den Fortschritt der Übersetzung verfolgen, indem Sie zum Fenster **Übersetzungsauftrag** zurückkehren und in der Spalte **Status** der Einträge nachsehen.

![Übersetzungsauftrag genehmigt](assets/translation-job-approved-manual.png)

Maschinelle Übersetzungen werden automatisch mit dem Status **Genehmigt** zurückgegeben. Menschliche Übersetzung ermöglicht mehr Interaktion, sprengt aber den Rahmen dieser Tour.

## Überprüfen übersetzter Inhalte {#reviewing}

[Wie bereits erwähnt,](#using-translation-project) maschinell übersetzte Inhalte fließen zurück in AEM mit dem Status **Genehmigt** Da die Annahme ist, dass aufgrund der Verwendung von maschineller Übersetzung kein menschliches Eingreifen erforderlich ist. Es ist jedoch weiterhin möglich, den übersetzten Inhalt zu überprüfen.

Wechseln Sie einfach zum abgeschlossenen Übersetzungsauftrag und wählen Sie ein Zeilenelement aus, indem Sie auf das Kontrollkästchen tippen oder klicken. Das Symbol **In Inhaltsfragment anzeigen** wird in der Symbolleiste angezeigt.

![In Inhaltsfragment anzeigen](assets/reveal-in-content-fragment.png)

Tippen oder klicken Sie auf dieses Symbol, um das übersetzte Inhaltsfragment in der Editor-Konsole zu öffnen, um die Details des übersetzten Inhalts anzuzeigen.

![Ein übersetztes Inhaltsfragment](assets/translated-content-fragment.png)

Sie können das Inhaltsfragment nach Bedarf weiter ändern, vorausgesetzt Sie verfügen über die entsprechenden Berechtigungen, aber die Bearbeitung von Inhaltsfragmenten sprengt den Rahmen dieser Tour. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments.

Ziel des Projekts ist es, alle Ressourcen, die mit einer Übersetzung verbunden sind, an einem Ort zu sammeln, um einen einfachen Zugriff und einen klaren Überblick zu erhalten. Wie Sie jedoch sehen können, indem Sie die Details eines übersetzten Elements anzeigen, fließen die Übersetzungen selbst in den Asset-Ordner der Übersetzungssprache zurück. In diesem Beispiel lautet der Ordner:

```text
/content/dam/wknd/es
```

Wenn Sie über **Navigation** -> **Assets** -> **Dateien** zu diesem Ordner navigieren, sehen Sie die übersetzten Inhalte.

![Struktur von Ordnern mit übersetzten Inhalten](assets/translated-file-content.png)

Das Übersetzungs-Framework von AEM erhält die Übersetzungen vom Übersetzungs-Connector und erstellt dann automatisch die Inhaltsstruktur, basierend auf dem Sprachstamm und unter Verwendung der vom Connector bereitgestellten Übersetzungen.

Es ist wichtig zu verstehen, dass diese Inhalte nicht veröffentlicht werden und daher nicht für Ihre Headless-Services verfügbar sind. Sie erfahren mehr über diese Autoren- und Veröffentlichungsstruktur und erfahren, wie Sie die übersetzten Inhalte im nächsten Schritt der Journey veröffentlichen.

## Menschliche Übersetzung {#human-translation}

Wenn Ihr Übersetzungsdienstleister menschliche Übersetzung bereitstellt, bietet der Überprüfungsprozess mehr Optionen. Übersetzungen gelangen beispielsweise mit dem Status **Entwurf** zurück in das Projekt und müssen manuell überprüft und genehmigt oder abgelehnt werden.

Die menschliche Übersetzung sprengt den Rahmen dieser Tour zur Lokalisierung. Weitere Informationen zu diesem Thema finden Sie im Abschnitt [Zusätzliche Ressourcen](#additional-resources) am Ende dieses Dokuments. Abgesehen von den zusätzlichen Genehmigungsoptionen ist der Workflow für menschliche Übersetzungen mit dem für maschinelle Übersetzungen identisch, wie in dieser Tour beschrieben.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der Headless-Übersetzungs-Journey abgeschlossen haben, sollten Sie Folgendes tun können:

* Verstehen, was ein Übersetzungsprojekt ist.
* Erstellen von Übersetzungsprojekten.
* Übersetzungsprojekte verwenden können, um Ihre Headless-Inhalte zu übersetzen.

Auf diesen Erkenntnissen aufbauen und Ihre Journey-zur Headless-AEM-Übersetzung fortsetzen, indem Sie das Dokument erneut überprüfen. [Übersetzten Inhalt veröffentlichen](publish-content.md) Hier erfahren Sie, wie Sie Ihre übersetzten Inhalte veröffentlichen und diese Übersetzungen aktualisieren können, wenn sich Ihr Sprachstamm ändert.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Übersetzungs-Tour voranzuschreiten, indem Sie das Dokument [Veröffentlichen übersetzter Inhalte](publish-content.md) lesen. Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige in diesem Dokument erwähnte Konzepte vertiefen. Aber sie sind nicht erforderlich, um mit der Headless-Tour fortzufahren.

* [Verwalten von Übersetzungsprojekten](/help/sites-administering/tc-manage.md) – Erfahren Sie mehr über die Einzelheiten von Übersetzungsprojekten und über zusätzliche Funktionen wie Workflows für menschliche Übersetzung und mehrsprachige Projekte.
* [Autorenumgebung und Tools](/help/sites-authoring/author-environment-tools.md#path-selection) – AEM bietet verschiedene Mechanismen für die Organisation und Bearbeitung von Inhalten, einschließlich eines robusten Pfad-Browsers.
