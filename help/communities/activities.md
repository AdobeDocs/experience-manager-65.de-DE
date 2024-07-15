---
title: Aktivitäts-Streams-Funktion
description: Erfahren Sie, wie die Aktivitäten eines angemeldeten Community-Mitglieds in einem Stream erfasst werden, den Sie über die Komponente "Aktivitäts-Streams"filtern und anzeigen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2b2a5de0-e7c7-4417-a217-4b929bc7dcfb
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der `Activity Streams` -Komponente auf verschiedene Weise gefiltert und angezeigt werden kann.

Die Möglichkeit, zu folgen, bietet eine weitere Ansicht der Aktivitäten, wenn Community-Mitglieder Beiträge von Interesse verfolgen oder den Aktivitäten anderer Community-Mitglieder folgen.

Das Dokument beschreibt:

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Aktivitäts-Streams&quot;

### Hinzufügen von Aktivitätstreams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie im Autorenmodus einer Seite die Komponente `Activity Streams` hinzufügen möchten, suchen Sie mit dem Komponenten-Browser nach

* `Communities / Activity Streams`

Ziehen Sie es an eine Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen der Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) eingeschlossen sind, wird die Komponente `Activity Streams` wie folgt angezeigt:

![activity-streams](assets/activity-component.png)

### Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte Komponente `Activity Streams` aus, damit Sie auf das Symbol `Configure` zugreifen und dieses auswählen können, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![configure](assets/configure-new.png)

Geben Sie auf der Registerkarte **Benutzeraktivitäten** an, welche Aktivitäten angezeigt werden sollen:

![user-activities](assets/user-activities.png)

* **Maximale Aktivitätsanzahl**

  Die Anzahl der anzuzeigenden Aktivitäten

* **Pfad der Stream-Ressource**

  Leer lassen, um die Community-Site oder Community-Gruppe standardmäßig zu verwenden. Der Pfad der Stream-Ressource identifiziert die Quelle der Aktivitäten. Der Standardwert ist leer.

* **Ansicht der Benutzeraktivitäten**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten auf der Basis der vom aktuellen Mitglied innerhalb der Community generierten Aktivitäten filtert. Die Option Standard ist aktiviert.

* **Ansicht aller Aktivitäten**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Die Option Standard ist aktiviert.

* **Anzeige nach Ansicht**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten nach denen filtert, denen das aktuelle Mitglied folgt. Die Option Standard ist aktiviert.

### Folgende Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [file library](/help/communities/file-library.md) und [comments](/help/communities/comments.md).

![following-view](assets/following-activities.png)

Die Schaltfläche **Befolgen** bietet die Möglichkeit, Einträgen als Aktivitäten, [Benachrichtigungen](/help/communities/notifications.md) oder [Abonnements](/help/communities/subscriptions.md) zu folgen. Jedes Mal, wenn die Schaltfläche **Befolgen** ausgewählt wird, kann eine Auswahl ein- oder ausgeschaltet werden. Die Auswahl `Email Subscriptions` ist nur bei Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgt**. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs.

   * Folgt allen Aktivitäten für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blogartikel.

   * Folgt allen Aktivitäten für diesen spezifischen Eintrag.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](/help/communities/essentials-activities.md) .
