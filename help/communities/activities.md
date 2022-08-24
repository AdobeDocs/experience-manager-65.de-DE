---
title: Aktivitäts-Streams-Funktion
seo-title: Activity Streams Feature
description: Aktivitäten eines angemeldeten Community-Mitglieds
seo-description: Activities of a signed-in community member
uuid: decd2d6c-4d4b-4698-a92c-2b5b441458cf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 89f3630f-c01a-4dc0-9ff5-169785f22c01
docset: aem65
exl-id: 2b2a5de0-e7c7-4417-a217-4b929bc7dcfb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 25%

---

# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung    {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der `Activity Streams` -Komponente.

Diese Verfolgungsmöglichkeit bietet eine zusätzliche Art der Aktivitätenansicht, mit der Community-Mitglieder interessanten Beiträgen oder den Aktivitäten anderer Mitglieder folgen können.

Das Dokument beschreibt:

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Aktivitäts-Streams&quot;

### Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie eine `Activity Streams` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Activity Streams`

und ziehen Sie die Komponente an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderliche clientseitige Bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) eingeschlossen sind, wird die `Activity Streams` -Komponente wird angezeigt:

![activity-streams](assets/activity-component.png)

### Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte `Activity Streams` -Komponente, die aufgerufen und ausgewählt werden soll `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Auf der Registerkarte **Benutzeraktivitäten** können Sie festlegen, welche Aktivitäten angezeigt werden sollen:

![user-activities](assets/user-activities.png)

* **Maximale Anzahl von Aktivitäten**

   Die Anzahl der anzuzeigenden Aktivitäten

* **Stream-Ressourcenpfad**

   Leer lassen, um die Community-Site oder Community-Gruppe standardmäßig zu verwenden. Mit dem Stream-Ressourcenpfad wird die Aktivitätenquelle festgelegt. Standardmäßig ist das Feld leer.

* **Ansicht der Benutzeraktivitäten anzeigen**

   Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, auf dem Aktivitäten basierend auf denen gefiltert werden, die innerhalb der Community vom aktuellen Mitglied generiert wurden. Diese Option ist standardmäßig aktiviert.

* **Ansicht aller Aktivitäten anzeigen**

   Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.

* **Follower-Ansicht anzeigen**

   Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten nach denen filtert, denen das aktuelle Mitglied folgt. Diese Option ist standardmäßig aktiviert.

### Folgende Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Funktionen, die Folgendes ermöglichen [blog](/help/communities/blog-feature.md), [Forum](/help/communities/forum.md), [Fragen und Antworten](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [fileLibrary](/help/communities/file-library.md)und [Kommentare](/help/communities/comments.md).

![folgende Ansicht](assets/following-activities.png)

Die **Folgen** -Schaltfläche bietet die Möglichkeit, Einträgen als Aktivitäten zu folgen. [Benachrichtigungen](/help/communities/notifications.md)oder [subscriptions](/help/communities/subscriptions.md). Jedes Mal, wenn **Folgen** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten. Die `Email Subscriptions` Die Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgende**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs.

   * Folgt allen Aktivitäten für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blogartikel.

   * Folgt allen Aktivitäten für diesen spezifischen Eintrag.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](/help/communities/essentials-activities.md).
