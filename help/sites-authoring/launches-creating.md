---
title: Erstellen von Launches
seo-title: Erstellen von Launches
description: Sie können einen Launch erstellen, um die Aktualisierung einer neuen Version bestehender Webseiten für die zukünftige Aktivierung zu aktivieren.
seo-description: Sie können einen Launch erstellen, um die Aktualisierung einer neuen Version bestehender Webseiten für die zukünftige Aktivierung zu aktivieren.
uuid: c1a32710-8189-4a2e-bf2f-428ab30d48c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 4ec6b408-a165-4617-8d90-e89d8a415bb3
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: bc7897da-15f6-4de4-a9fd-9dd84e6c7eed
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 98%

---

# Erstellen von Launches{#creating-launches}

Erstellen Sie einen Launch, um die Aktualisierung einer neuen Version bestehender Web-Seiten für die zukünftige Aktivierung zu aktivieren. Wenn Sie einen Launch erstellen, können Sie einen Titel und die Quellseite angeben:

* Der Titel wird in der Leiste [Verweise](/help/sites-authoring/author-environment-tools.md#references) angezeigt. Von dort aus haben Autoren Zugriff zur Bearbeitung.
* Die untergeordneten Seiten der Quellseiten werden standardmäßig in den Launch eingeschlossen. Sie können bei Bedarf nur die Quellseite verwenden.
* Standardmäßig aktualisiert [Live Copy](/help/sites-administering/msm.md) automatisch die Launch-Seiten, wenn sich die Quellseiten ändern. Zur Vermeidung automatischer Änderungen können Sie festlegen, dass eine statische Kopie erstellt wird.

Optional können Sie das **Launch-Datum** (und die Uhrzeit) für die Bewerbung und Aktivierung der Launch-Seiten angeben. Das **Launch-Datum** funktioniert allerdings nur in Kombination mit der Kennzeichnung **Produktionsbereit** (siehe [Bearbeiten einer Launch-Konfiguration](/help/sites-authoring/launches-editing.md#editing-a-launch-configuration)). Damit die Aktionen automatisch erfolgen, muss beides festgelegt werden.

## Erstellen eines Launches {#creating-a-launch}

Sie können den Launch über die Sites- oder Launches-Konsole erstellen oder starten:

1. Öffnen Sie die Konsole **Sites** oder die Konsole **Launches**.

   >[!NOTE]
   >
   >Wenn Sie die Konsole **Sites** verwenden, wird normalerweise zum Speicherort der Quellseite navigiert, dies ist jedoch nicht zwingend erforderlich, da die Navigation auch durch Auswahl von **Quelle starten** im Assistenten erfolgen kann.

1. In Abhängigkeit der von Ihnen verwendeten Konsole:

   * **Launches**:

      1. Wählen Sie in der Symbolleiste **Launch erstellen** aus, um den Assistenten zu öffnen.
   * **Sites**:

      1. Wählen Sie in der Symbolleiste **Erstellen** aus, um das Auswahlfeld zu öffnen.
      1. Wählen Sie dann **Launch erstellen** aus, um den Assistenten zu öffnen.

   >[!NOTE]
   >
   >In der **Sites**-Konsole können Sie auch den [Auswahlmodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) verwenden, um eine Seite auszuwählen, bevor Sie **Erstellen** auswählen.
   >
   >Dadurch wird die ausgewählte Seite als Anfangsquellseite verwendet.

1. Im Schritt **Quelle auswählen** müssen Sie **Seiten hinzufügen**. Sie können mehrere Seiten auswählen, wobei jeweils der Pfad angegeben werden muss:

   * Navigieren Sie zur erforderlichen Position.
   * Wählen Sie die Quellseite(n) aus und bestätigen Sie (durch ein Häkchen).

   Wiederholen Sie dies nach Bedarf.

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >Um Seiten und/oder Verzweigungen zu einem Launch hinzuzufügen, müssen diese sich innerhalb einer Site befinden, d. h. unterhalb eines gemeinsamen Stamms auf oberster Ebene.
   >
   >Wenn eine Site Sprachstämme unterhalb der obersten Ebene enthält, müssen sich die Seiten und Verzweigungen für einen Launch unterhalb eines gemeinsamen Sprachstamms befinden.

1. Für jeden Eintrag können Sie Folgendes angeben:

   * **Unterseiten einschließen**:

      * Geben Sie an, ob der Launch mit den oder ohne die untergeordneten Seiten erstellt werden soll.  Standardmäßig werden Unterseiten eingeschlossen.

   Fahren Sie mit **Weiter** fort.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. Im Schritt **Eigenschaften** des Assistenten können Sie Folgendes festlegen:

   * **Launch-Titel**: Der Name des Launches. Der Name sollte für Autoren einen Sinn ergeben.
   * **mit vorhandenem Inhalt**: Der ursprüngliche Inhalt wird verwendet, um den Launch zu erstellen.
   * **mit einer neuen Vorlage, um die Seite zu ersetzen**: Weitere Einzelheiten erfahren Sie unter [Erstellen von Launches mit einer neuen Vorlage](#create-launch-with-new-template).
   * **Quellseiten-Live-Daten übernehmen**: Wählen Sie diese Option aus, um den Inhalt von Launch-Seiten automatisch zu aktualisieren, wenn die Quellseiten sich ändern. Diese Option erreicht dies, indem der Launch zu einer [Live Copy](/help/sites-administering/msm.md) gemacht wird.

      Standardmäßig ist diese Option aktiviert.

   * **Launch-Datum**: Das Datum und die Uhrzeit für die Aktivierung der Launch-Kopie (abhängig von der Markierung **Produktionsbereit**. Siehe [Launches: Reihenfolge von Ereignissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und den neuen Launch zu erstellen. Im Bestätigungsdialogfeld werden Sie gefragt, ob Sie den Launch sofort öffnen möchten.

   Wenn Sie zur Konsole zurückkehren (über **Fertig**), können Sie den Launch wie folgt einsehen (und darauf zugreifen):

   * in der [**Launch-Konsole**](/help/sites-authoring/launches.md#the-launches-console)
   * unter [**Verweise** in der Konsole **Sites**](/help/sites-authoring/launches.md#launches-in-references-sites-console)

### Erstellen von Launches mit einer neuen Vorlage {#create-launch-with-new-template}

Bei der [Erstellung eines Launches](/help/sites-authoring/launches-creating.md#create-launch-with-new-template) können Sie auswählen, ob eine neue Vorlage verwendet werden soll:

**mit einer neuen Vorlage, um die Seite zu ersetzen**

>[!CAUTION]
>
>Diese Option ist nur verfügbar, wenn ein Launch über die Konsole **Sites** erstellt wird. Sie steht nicht zur Verfügung, wenn ein Launch über die Konsole **Launches** erstellt wird.

![chlimage_1-228](assets/chlimage_1-228.png)

Die Auswahl dieser Option bewirkt Folgendes:

* die anderen verfügbaren Optionen werden aktualisiert,
* ein neuer Schritt wird einbezogen, mit dem Sie die gewünschte Vorlage auswählen können.

![chlimage_1-229](assets/chlimage_1-229.png)

>[!CAUTION]
>
>Da eine andere Vorlage verwendet wird, ist die neue Seite leer. Aufgrund der unterschiedlichen Seitenstruktur werden keine Inhalte kopiert.
>
>Dieser Mechanismus kann verwendet werden, um die Vorlage einer [vorhandenen Seite](/help/sites-authoring/managing-pages.md#creating-a-new-page) zu ändern, wobei jedoch der Verlust von Inhalten zu berücksichtigen ist.

### Erstellen von verschachtelten Launches  {#creating-a-nested-launch}

Das Erstellen eines verschachtelten Launches (eines Launches innerhalb eines Launches) bietet Ihnen die Möglichkeit, einen Launch aus einem vorhandenen Launch zu erstellen, sodass Autoren bereits vorgenommene Änderungen nutzen können, anstatt dieselben Änderungen für jeden Launch erneut vornehmen zu müssen.

>[!NOTE]
>
>Siehe auch [Weiterleiten eines verschachtelten Launches](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch).

#### Erstellen von verschachtelten Launches: Konsole „Launches“ {#creating-a-nested-launch-launches-console}

Das Erstellen eines verschachtelten Launches über die Konsole **Launches** ist im Wesentlichen das Gleiche wie das Erstellen jeder anderen Form eines Launches mit der Ausnahme, dass Sie zu der Launch-Verzweigung `/content/launches` navigieren müssen:

1. Wählen Sie in der Konsole **Launches** die Option **Erstellen** aus.
1. Wählen Sie **Seiten hinzufügen** aus und navigieren Sie zur Launch-Verzweigung, indem Sie `/content/launches` im Filter angeben. Wählen Sie den gewünschten Launch aus und bestätigen Sie mit **Auswählen**:

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Klicken Sie auf **Weiter**, um fortzufahren. Geben Sie die **Eigenschaften** dann wie bei jedem anderen Launch an.

   ![chlimage_1-231](assets/chlimage_1-231.png)

#### Erstellen von verschachtelten Launches: Konsole „Sites“ {#creating-a-nested-launch-sites-console}

So erstellen Sie einen verschachtelten Launch auf Grundlage eines vorhandenen Launches über die Konsole **Sites**:

1. Rufen Sie [Launches aus Verweisen (Konsole „Sites“)](/help/sites-authoring/launches.md#launches-in-references-sites-console) auf, um die verfügbaren Aktionen anzuzeigen.
1. Wählen Sie **Launch erstellen** aus, um den Assistenten zu öffnen (da die Quelle bereits ausgewählt wurde, wird der Schritt **Quelle auswählen** übersprungen).

1. Geben Sie den **Launch-Titel** und jegliche weiteren erforderlichen Details ein (wie bei einem normalen Launch).

1. Verwenden Sie **Erstellen**, um den Vorgang abzuschließen und den neuen Launch zu erstellen. Im Bestätigungsdialogfeld werden Sie gefragt, ob Sie den Launch sofort öffnen möchten.

   Bei Auswahl von **Fertig** wird erneut die Leiste **Verweise** der Konsole **Sites** angezeigt. Bei Auswahl der entsprechenden Seite wird der neue Launch angezeigt.

### Löschen von Launches {#deleting-a-launch}

Sie können einen Launch aus der [Launch-Konsole](/help/sites-authoring/launches.md#the-launches-console) löschen:

* Wählen Sie den Launch aus, indem Sie auf die Miniatur tippen/klicken.
* Die Symbolleiste wird angezeigt. Wählen Sie „Löschen“ aus.
* Bestätigen Sie die Aktion.

>[!CAUTION]
>
>Durch Löschen eines Launches werden der Launch selbst sowie alle nachfolgenden verschachtelten Launches entfernt.
