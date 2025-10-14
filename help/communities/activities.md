---
title: Aktivitäts-Streams-Funktion
description: Erfahren Sie, wie die Aktivitäten eines angemeldeten Community-Mitglieds in einem Stream erfasst werden, den Sie mithilfe der Aktivitäts-Streams-Komponente filtern und anzeigen können.
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

Die Aktivitäten eines angemeldeten Community-Mitglieds, z. B. das Posten in einem Forum oder Blog, werden in einem Stream erfasst, der auf verschiedene Arten gefiltert und angezeigt werden kann, indem die `Activity Streams` konfiguriert wird.

Die Möglichkeit, zu folgen, fügt eine weitere Ansicht von Aktivitäten hinzu, wenn Community-Mitglieder Interessensnachrichten folgen oder den Aktivitäten anderer Community-Mitglieder folgen.

In dem Dokument wird Folgendes beschrieben:

* Hinzufügen der Aktivitäts-Streams-Komponente zu einer AEM-Site
* Konfigurationseinstellungen für die Aktivitäts-Streams-Komponente

### Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie einer Seite im Autorenmodus eine `Activity Streams` Komponente hinzufügen möchten, suchen Sie im Komponenten-Browser nach .

* `Communities / Activity Streams`

und ziehen Sie sie auf eine Seite, auf der Aktivitätsströme angezeigt werden sollen.

Weitere Informationen finden Sie unter [Grundlagen zu Communities-Komponenten](/help/communities/basics.md).

Wenn die [erforderlichen Client-seitigen &#x200B;](/help/communities/essentials-activities.md#essentials-for-client-side) enthalten sind, wird die `Activity Streams` Komponente wie folgt angezeigt:

![activity-streams](assets/activity-component.png)

### Aktivitäts-Streams konfigurieren {#configuring-activity-streams}

Wählen Sie die platzierte `Activity Streams` aus, um auf das Symbol `Configure` zuzugreifen, das das Dialogfeld „Bearbeiten“ öffnet.

![Konfigurieren](assets/configure-new.png)

Geben **auf der Registerkarte** Benutzeraktivitäten“ an, welche Aktivitäten angezeigt werden sollen:

![user-activities](assets/user-activities.png)

* **Maximale Anzahl von Aktivitäten**

  Die Anzahl der anzuzeigenden Aktivitäten

* **Stream-Ressourcenpfad**

  Lassen Sie das Feld leer, um die Community-Site oder Community-Gruppe standardmäßig anzuzeigen. Der Stream-Ressourcenpfad identifiziert die Quelle der Aktivitäten. Der Standardwert ist leer.

* **Ansicht Benutzeraktivitäten anzeigen**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, auf der Aktivitäten anhand der Community-Inhalte gefiltert werden, die vom aktuellen Mitglied generiert wurden. Die Standardeinstellung ist aktiviert.

* **Ansicht „Alle Aktivitäten anzeigen“**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, die alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Die Standardeinstellung ist aktiviert.

* **Folgende Ansicht anzeigen**

  Wenn diese Option aktiviert ist, enthält die Seite Aktivitäten eine Registerkarte, auf der Aktivitäten anhand der Aktivitäten des aktuellen Mitglieds gefiltert werden. Die Standardeinstellung ist aktiviert.

### folgende Ansicht {#following-view}

Komponenten müssen so konfiguriert sein, dass Folgendes aktiviert wird. Funktionen, die Folgendes ermöglichen[&#x200B; sind &#x200B;](/help/communities/blog-feature.md)blog[, forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [file library](/help/communities/file-library.md) und [comments](/help/communities/comments.md).

![folgende Ansicht](assets/following-activities.png)

Die **Folgen**-Schaltfläche bietet die Möglichkeit, Einträgen als Aktivitäten, [Benachrichtigungen](/help/communities/notifications.md) oder [Abonnements](/help/communities/subscriptions.md) zu folgen. Jedes Mal, wenn die **Folgen**-Schaltfläche ausgewählt ist, kann eine Auswahl ein- oder ausgeschaltet werden. Die `Email Subscriptions` ist nur vorhanden, wenn konfiguriert.

Wenn eine der folgenden Methoden ausgewählt ist, ändert sich der Text der Schaltfläche in &quot;**&quot;**. Der Einfachheit halber können Sie `Unfollow All` auswählen, um alle Methoden zu deaktivieren.

Die Schaltfläche **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Haupt-Funktionsseite wie Foren, QNa und Blogs.

   * Führt alle Aktivitäten für diese allgemeine Funktion aus.

* Für einen bestimmten Eintrag, z. B. ein Forumsthema, eine Frage oder einen Blog-Artikel.

   * Führt alle Aktivitäten für diesen bestimmten Eintrag aus.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Activity Streams Essentials](/help/communities/essentials-activities.md) für Entwickler.
