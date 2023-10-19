---
title: Aktivitäts-Streams-Funktion
description: Erfahren Sie, wie die Aktivitäten eines angemeldeten Community-Mitglieds in einem Stream erfasst werden, den Sie über die Komponente "Aktivitäts-Streams"filtern und anzeigen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2b2a5de0-e7c7-4417-a217-4b929bc7dcfb
source-git-commit: b8887b4a6f757352e9dbfdf074c10e9ccd6dbd4f
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 4%

---

# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der durch die Konfiguration der `Activity Streams` -Komponente.

Die Möglichkeit, zu folgen, bietet eine weitere Ansicht der Aktivitäten, wenn Community-Mitglieder Beiträge von Interesse verfolgen oder den Aktivitäten anderer Community-Mitglieder folgen.

Das Dokument beschreibt:

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Komponente &quot;Aktivitäts-Streams&quot;

### Hinzufügen von Aktivitätstreams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie eine `Activity Streams` -Komponente auf einer Seite im Autorenmodus verwenden Sie den Komponenten-Browser, um

* `Communities / Activity Streams`

Ziehen Sie es an eine Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die Variable [erforderliche clientseitige Bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) eingeschlossen sind, wird die `Activity Streams` -Komponente angezeigt:

![activity-streams](assets/activity-component.png)

### Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Auswählen der platzierten `Activity Streams` -Komponente, damit Sie auf die `Configure` -Symbol, über das das Dialogfeld &quot;Bearbeiten&quot;geöffnet wird.

![konfigurieren](assets/configure-new.png)

Unter dem **Benutzeraktivitäten** angeben, welche Aktivitäten angezeigt werden sollen:

![user-activities](assets/user-activities.png)

* **Maximale Anzahl von Aktivitäten**

  Die Anzahl der anzuzeigenden Aktivitäten

* **Stream-Ressourcenpfad**

  Leer lassen, um die Community-Site oder Community-Gruppe standardmäßig zu verwenden. Der Pfad der Stream-Ressource identifiziert die Quelle der Aktivitäten. Der Standardwert ist leer.

* **Ansicht der Benutzeraktivitäten anzeigen**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten auf der Basis der vom aktuellen Mitglied innerhalb der Community generierten Aktivitäten filtert. Die Option Standard ist aktiviert.

* **Ansicht aller Aktivitäten anzeigen**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Die Option Standard ist aktiviert.

* **Follower-Ansicht anzeigen**

  Wenn diese Option aktiviert ist, enthält die Aktivitätsseite einen Tab, der Aktivitäten nach denen filtert, denen das aktuelle Mitglied folgt. Die Option Standard ist aktiviert.

### Folgende Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Funktionen, die Folgendes ermöglichen [Blog](/help/communities/blog-feature.md), [Forum](/help/communities/forum.md), [Fragen und Antworten](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [Dateibibliothek](/help/communities/file-library.md), und [Kommentare](/help/communities/comments.md).

![folgende Ansicht](assets/following-activities.png)

Die **Folgen** -Schaltfläche bietet die Möglichkeit, Einträgen als Aktivitäten zu folgen. [Benachrichtigungen](/help/communities/notifications.md)oder [subscriptions](/help/communities/subscriptions.md). Jedes Mal, wenn **Folgen** ausgewählt ist, können Sie die Auswahl ein- oder ausschalten. Die `Email Subscriptions` Die Auswahl ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in **Folgende**. Zur Vereinfachung können Sie `Unfollow All` , um alle Methoden auszuschalten.

Die **Folgen** -Schaltfläche angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, Fragen und Antworten und Blogs.

   * Folgt allen Aktivitäten für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Frage oder einen Blogartikel.

   * Folgt allen Aktivitäten für diesen spezifischen Eintrag.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Grundlagen zu Aktivitäts-Streams](/help/communities/essentials-activities.md) -Seite für Entwickler.
