---
title: Projekte
description: Mithilfe von Projekten können Sie Ressourcen zu einer Einheit gruppieren, deren gemeinsame Umgebung die Verwaltung Ihrer Projekte erleichtert.
exl-id: 632c0608-2ab8-4a5b-8251-cd747535449b
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1360'
ht-degree: 96%

---


# Projekte {#projects}

Mithilfe von Projekten können Sie Ressourcen zu einer Einheit gruppieren. Eine gemeinsam genutzte Umgebung erleichtert die Projektverwaltung. Die Ressourcentypen, die Sie mit einem Projekt verknüpfen können, werden in AEM als Kacheln bezeichnet. Kacheln können Projekt- und Team-Informationen, Assets, Workflows und andere Arten von Informationen sein. Ausführliche Informationen finden Sie unter [Projektkacheln](#project-tiles).

Als Benutzer haben Sie folgende Möglichkeiten:

* Erstellen und Löschen von Projekten
* Zuordnen von Inhalten und Asset-Ordnern zu einem Projekt
* Entfernen von Inhaltsverknüpfungen aus einem Projekt

## Zugriffsanfrorderungen {#access-requirements}

Erstellt eine standardmäßige AEM und erfordert keine zusätzliche Einrichtung.

Damit Benutzer in „Projekte“ andere Benutzer/Gruppen sehen können, während sie mit Projektfunktionen wie Erstellen von Projekten, Erstellen von Aufgaben/Workflows, Anzeigen und Verwalten des Teams arbeiten, benötigen sie Lesezugriff auf `/home/users` und `/home/groups`.

Um dies umzusetzen, erteilen Sie am besten der Gruppe **projects-users** Lesezugriff auf `/home/users` und `/home/groups`.

## Projektekonsole {#projects-console}

In der Projektekonsole können Sie innerhalb von AEM auf Ihre Projekte zugreifen und diese verwalten.

![Die Projektekonsole](assets/screen-shot_2019-03-05at125110.png)

Die Projektekonsole ähnelt anderen Konsolen in AEM, erlaubt mehrere Aktionen für einzelne Projekte und passt Ihre Ansicht der Projekte an.

### Modus umschalten {#modes}

Sie können die Leistenauswahl verwenden, um zwischen den Konsolenmodi zu wechseln.

![Leistenauswahl](assets/projects-rail.png)

#### Nur Inhalte {#content-only}

„Nur Inhalte“ ist der Standardmodus beim Öffnen der Konsole. Er zeigt alle Ihre Projekte.

#### Zeitleiste {#timeline}

In der Timeline-Ansicht können Sie ein einzelnes Projekt auswählen und die Aktivitäten in diesem Projekt anzeigen. Verwenden Sie die Leistenauswahl oder den Hotkey `alt+1`, um zu dieser Ansicht zu wechseln.

![Zeitleistenmodus](assets/project-timeline.png)

### Ansicht umschalten {#views}

Mit der Ansichtsauswahl können Sie zwischen der Anzeige von Projekten als große Kacheln (Standard), der Anzeige als Liste oder in einem Kalender wechseln.

![Ansichten](assets/projects-views.png)

### Filtern der Ansicht {#filter}

Mit dem Filter können Sie zwischen allen Projekten und nur den aktiven wechseln.

![Filter](assets/projects-filter.png)

### Auswählen und Anzeigen von Projekten {#selecting}

Wählen Sie ein Projekt aus, indem Sie den Mauszeiger über die Projektkachel bewegen und auf das Häkchen klicken.

Zeigen Sie die Details eines Projekts an, indem Sie darauf klicken, um eine detaillierte Ansicht zu erhalten.

### Erstellen neuer Projekte {#creating}

Klicken Sie auf **Erstellen**, um ein neues Projekt hinzuzufügen.

## Projektkacheln {#project-tiles}

Projekte bestehen aus verschiedenen Arten von Informationen, die Sie gemeinsam verwalten möchten. Diese Informationen werden durch verschiedene **Kacheln** dargestellt.

Sie können die folgenden Kacheln mit Ihrem Projekt verknüpfen.

* [Assets](#assets)
* [Asset-Sammlungen](#asset-collections)
* [Erlebnisse](#experiences)
* [Links](#links)
* [Projektinformationen](#project-info)
* [Team](#team)
* [Landing Pages](#landing-pages)
* [E-Mails](#emails)
* [Workflows](#workflows)
* [Launches](#launches)
* [Aufgaben](#tasks)

Klicken Sie oben rechts in einer Kachel auf das Dropdown-Menü, um der Kachel weitere Daten hinzuzufügen.

Klicken Sie auf die Schaltfläche mit den Auslassungspunkten unten rechts in einer beliebigen Kachel, um die Daten der Kachel in der zugehörigen Konsole zu öffnen.

### Assets {#assets}

In der Kachel **Assets** können Sie alle Assets zusammenstellen, die Sie für ein bestimmtes Projekt verwenden.

![Assets-Kachel](assets/project-tile-assets.png)

Laden Sie Assets direkt in die Kachel hoch.

### Asset-Sammlungen {#asset-collections}

[Asset-Sammlungen](/help/assets/manage-collections.md) können Ihrem Projekt ähnlich wie Assets direkt hinzugefügt werden. Sie definieren die Sammlungen unter „Assets“.

![Asset-Sammlungs-Kachel](assets/project-tile-asset-collection.png)

Fügen Sie eine Sammlung hinzu, indem Sie auf **Sammlung hinzufügen** klicken und die entsprechende Sammlung in der Liste auswählen.

### Erlebnisse {#experiences}

Über die Kachel **Erlebnisse** können Sie eine Mobile App, eine Website oder eine Veröffentlichung zum Projekt hinzufügen.

![Erlebnis-Kachel](assets/project-tile-experiences.png)

Die Symbole geben an, welche Art von Erlebnis dargestellt wird.

* Website
* Mobile App

### Links {#links}

Über die Kachel **Links** können Sie externe Links mit Ihrem Projekt verknüpfen.

![Link-Kachel](assets/project-tile-links.png)

Sie können dem Link einen aussagekräftigen Namen geben und das Miniaturbild ändern.

### Projektinformationen {#project-info}

Die Kachel **Projektinformationen** enthält allgemeine Informationen zum Projekt, einschließlich einer Beschreibung, des Projektstatus (inaktiv oder aktiv), eines Fälligkeitsdatums und der Mitglieder. Darüber hinaus können Sie eine ProjektMiniatur hinzufügen, die auf der Hauptprojektseite angezeigt wird.

![Projektinformationen-Kachel](assets/project-tile-info.png)

### Übersetzungsauftrag {#translation-job}

In der Kachel **Übersetzungsauftrag** können Sie eine Übersetzung starten und sehen den jeweiligen Status Ihrer Übersetzungen.

![Kachel des Übersetzungsauftrags](assets/project-tile-translation.png)

Informationen zum Einrichten Ihrer Übersetzung finden Sie unter [Erstellen von Übersetzungsprojekten](/help/assets/translation-projects.md).

### Team {#team}

In dieser Kachel können Sie die Mitglieder des Projekt-Teams angeben. Geben Sie die Namen der Team-Mitglieder ein und weisen Sie Benutzerrollen zu.

![Kachel „Team“](assets/project-tile-team.png)

Sie können Team-Mitglieder zum Team hinzufügen und aus ihm löschen. Darüber hinaus können Sie die [Benutzerrolle](#userroles) bearbeiten, die dem jeweiligen Team-Mitglied zugewiesen ist.

### Landing Pages {#landing-pages}

Über die Kachel **Landingpages** können Sie eine neue Landingpage anfragen.

![Landingpage-Kachel](assets/project-tile-landing.png)

Dieser Workflow wird im Dokument [Erstellen eines Landingpage-Workflows](/help/sites-authoring/projects-with-workflows.md#request-landing-page-workflow) beschrieben.

### E-Mails {#emails}

In der Kachel **E-Mails** können Sie E-Mail-Anfragen verwalten. Hierüber lässt sich der auch der Workflow zum **Anfragen einer E-Mail** starten.

![E-Mail-Kachel](assets/project-tile-email.png)

Weitere Informationen finden Sie im [Workflow „E-Mail anfordern“](/help/sites-authoring/projects-with-workflows.md#request-email-workflow).

### Workflows {#workflows}

Sie können Workflows für Ihr Projekt starten. Wenn Workflows ausgeführt werden, wird ihr Status in der Kachel **Workflows** angezeigt.

![Workflows-Kachel](assets/project-tile-workflows.png)

Je nachdem, welches Projekt Sie erstellen, sind unterschiedliche Workflows verfügbar.

Diese werden unter [Arbeiten mit Projekt-Workflows](/help/sites-authoring/projects-with-workflows.md) beschrieben.

### Launches {#launches}

Die Kachel **Launches** enthält alle Launches, die mit einem [Workflow für die Launch-Anfrage](/help/sites-authoring/projects-with-workflows.md) angefragt wurden.

![Launches-Kachel](assets/project-tile-launches.png)

### Aufgaben {#tasks}

Mithilfe von Aufgaben können Sie den Status aller projektbezogenen Aufgaben überwachen, einschließlich Workflows. Aufgaben werden im Detail unter [Arbeiten mit Aufgaben](/help/sites-authoring/task-content.md) beschrieben.

![Aufgaben-Kachel](assets/project-tile-tasks.png)

## Projektvorlagen {#project-templates}

Vorlagen dienen als Grundlage für den Projektstart. AEM stellt diese Standardprojektvorlagen bereit.

* **Medienprojekt**: Dies ist ein Referenzbeispielprojekt für medienbezogene Aktivitäten. Es enthält mehrere medienbezogene Projektrollen und auch Workflows, die mit Medieninhalten in Verbindung stehen.
* **[Projekt für Produkt-Fotoshooting](/help/sites-authoring/managing-product-information.md)**: Dies ist ein beispielhaftes Referenzprojekt für Produktfotografie im Bereich E-Commerce.
* **[Übersetzungsprojekt](/help/sites-administering/translation.md)**: Dies ist ein beispielhaftes Referenzprojekt für die Verwaltung von übersetzungsbezogenen Aktivitäten. Es enthält grundlegende Rollen und Workflows für die Verwaltung von Übersetzungen.
* **Einfaches Projekt**: Dies ist ein Referenzbeispiel für alle Projekte, die nicht in andere Kategorien passen. Es umfasst drei grundlegende Rollen und vier allgemeine AEM-Workflows.

Je nach ausgewählter Vorlage stehen Ihnen im Projekt verschiedene Optionen zur Verfügung, z. B. die Benutzerrollen und Workflows.

## Benutzerrollen in einem Projekt {#user-roles-in-a-project}

Die verschiedenen Benutzerrollen werden in einer Projektvorlage festgelegt und werden in erster Linie aus zwei Gründen verwendet:

1. Berechtigungen: Die Benutzerrollen fallen in eine der drei genannten Kategorien: Beobachter, Bearbeiter, Verantwortlicher. Ein Fotograf oder Werbetexter hat z. B. dieselben Berechtigungen wie ein Bearbeiter. Über die Berechtigungen wird festgelegt, inwiefern ein Benutzer Inhalte in einem Projekt ändern kann.
1. Workflows: Mit Workflows wird festgelegt, wem welche Aufgaben in einem Projekt zugewiesen sind. Die Aufgaben können einer Projektrolle zugeordnet werden. Beispielsweise kann Fotografen eine Aufgabe zugewiesen werden, sodass alle Team-Mitglieder mit der Rolle „Fotograf“ die Aufgabe erhalten.

Alle Projekte unterstützen die folgenden Standardrollen, mit denen Sie Sicherheits- und Kontrollberechtigungen verwalten können.

| Rolle | Beschreibung | Berechtigungen | Gruppenmitgliedschaft |
|---|---|---|---|
| Beobachter | Ein Benutzer mit dieser Rolle kann Projektdetails, einschließlich des Projektstatus, anzeigen. | Nur-Lese-Zugriff auf ein Projekt | `workflow-users`-Gruppe |
| Bearbeiter | Ein Benutzer mit dieser Rolle kann Inhalt in ein Projekt hochladen und Projektinhalte bearbeiten. | Lese- und Schreibzugriff auf ein Projekt, zugehörige Metadaten und zugehörige Assets<br>Berechtigungen zum Hochladen einer Einstellungsliste, zum Fotografieren sowie zum Überprüfen und Genehmigen von Assets<br>Schreibberechtigung für `/etc/commerce`<br>Ändern der Berechtigung für ein bestimmtes Projekt | `workflow-users`-Gruppe |
| Inhaber | Ein Benutzer mit dieser Rolle kann ein Projekt erstellen, die Arbeit an einem Projekt initiieren und genehmigte Assets in den Produktionsordner verschieben. Aber auch alle anderen Aufgaben im Projekt können vom Verantwortlichen angezeigt und ausgeführt werden. | Schreibberechtigung für `/etc/commerce` | Die Gruppe `dam-users` soll ein Projekt erstellen können, die Gruppe <br>`projects-administrators` soll ein Projekt erstellen und Assets verschieben können. |

Für kreative Projekte stehen zusätzliche Rollen, z. B. Fotografen, zur Verfügung. Sie können diese Rollen verwenden, um auf deren Grundlage benutzerdefinierte Rollen für ein bestimmtes Projekt zu erstellen.

### Automatische Gruppenerstellung {#auto-group-creation}

Wenn Sie das Projekt erstellen und den verschiedenen Rollen Benutzer hinzufügen, werden mit dem Projekt verknüpfte Gruppen automatisch erstellt, um die zugehörigen Berechtigungen zu verwalten.

Ein Projekt mit dem Namen Myproject könnte z. B. drei Gruppen **Myproject-Eigentümer**, **Myproject-Editor**, **Myproject-Beobachter** haben.

Wenn das Projekt gelöscht wird, werden diese Gruppen nur gelöscht, [wenn Sie beim Löschen des Projekts die entsprechende Option auswählen.](/help/sites-authoring/touch-ui-managing-projects.md#deleting-a-project) Eine bzw. ein Admin kann die Gruppen unter **Tools** > **Sicherheit** > **Gruppen** manuell löschen.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zur Verwendung von Projekten finden Sie in den folgenden zusätzlichen Dokumenten:

* [Verwalten von Projekten](/help/sites-authoring/touch-ui-managing-projects.md)
* [Arbeiten mit Aufgaben](/help/sites-authoring/task-content.md)
* [Arbeiten mit Projekt-Workflows](/help/sites-authoring/projects-with-workflows.md)
* [Creative Project und PIM-Integration](/help/sites-authoring/managing-product-information.md)
