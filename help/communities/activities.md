---
title: Aktivitäts-Streams-Funktion
seo-title: Aktivitäts-Streams-Funktion
description: Aktivitäten eines angemeldeten Community-Mitglieds
seo-description: Aktivitäten eines angemeldeten Community-Mitglieds
uuid: decd2d6c-4d4b-4698-a92c-2b5b441458cf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 89f3630f-c01a-4dc0-9ff5-169785f22c01
docset: aem65
translation-type: tm+mt
source-git-commit: fcdae5363e7a0070b5d6b76227e5c65efb71bc03
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 25%

---


# Aktivitäts-Streams-Funktion {#activity-streams-feature}

## Einführung {#introduction}

Die Aktivitäten eines angemeldeten Community-Mitglieds, wie z.B. das Posten in einem Forum oder Blog, werden in einem Stream gesammelt, der durch die Konfiguration der `Activity Streams`-Komponente gefiltert und angezeigt werden kann.

Diese Verfolgungsmöglichkeit bietet eine zusätzliche Art der Aktivitätenansicht, mit der Community-Mitglieder interessanten Beiträgen oder den Aktivitäten anderer Mitglieder folgen können.

Das Dokument beschreibt:

* Hinzufügen der Aktivität Streams-Komponente zu einer AEM Site
* Konfigurationseinstellungen für die Aktivität Streams-Komponente

### Hinzufügen von Aktivitäts-Streams zu einer Seite {#adding-activity-streams-to-a-page}

Wenn Sie eine `Activity Streams`-Komponente zu einer Seite im Autorenmodus hinzufügen möchten, verwenden Sie den Komponenten-Browser, um

* `Communities / Activity Streams`

und ziehen Sie die Komponente an die gewünschte Stelle auf einer Seite, auf der Aktivitäts-Streams angezeigt werden sollen.

Die erforderlichen Informationen finden Sie unter [Komponenten der Communities](/help/communities/basics.md).

Wenn die [erforderlichen clientseitigen Bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) einbezogen werden, wird die `Activity Streams`-Komponente wie folgt angezeigt:

![Aktivität-Streams](assets/activity-component.png)

### Konfigurieren von Aktivitäts-Streams {#configuring-activity-streams}

Wählen Sie die platzierte Komponente `Activity Streams` aus, auf die zugegriffen werden soll, und wählen Sie das Symbol `Configure` aus, mit dem das Bearbeitungsdialogfeld geöffnet wird.

![konfigurieren](assets/configure-new.png)

Auf der Registerkarte **Benutzeraktivitäten** können Sie festlegen, welche Aktivitäten angezeigt werden sollen:

![user-Aktivitäten](assets/user-activities.png)

* **Maximale Anzahl von Aktivitäten**

   Die Anzahl der anzuzeigenden Aktivitäten

* **Stream-Ressourcenpfad**

   Leer lassen, um standardmäßig die Community-Site oder Community-Gruppe zu verwenden. Mit dem Stream-Ressourcenpfad wird die Aktivitätenquelle festgelegt. Standardmäßig ist das Feld leer.

* **Ansicht der Benutzeraktivitäten anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, die vom aktuellen Mitglied innerhalb der Community generiert wurden. Diese Option ist standardmäßig aktiviert.

* **Ansicht aller Aktivitäten anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, die alle in der Community generierten Aktivitäten enthält, auf die das aktuelle Mitglied Zugriff hat. Diese Option ist standardmäßig aktiviert.

* **Follower-Ansicht anzeigen**

   Wenn diese Option aktiviert ist, enthält die Seite &quot;Aktivitäten&quot;eine Registerkarte, auf der die Aktivitäten der Filter basieren, die vom aktuellen Member ausgeführt werden. Diese Option ist standardmäßig aktiviert.

### Nach der Ansicht {#following-view}

Komponenten müssen konfiguriert werden, um Folgendes zu aktivieren. Folgende Funktionen sind zulässig: [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [calendar](/help/communities/calendar.md), [fileLibrary](/help/communities/file-library.md) und [comments](/help/communities/comments.md).

![after-Ansicht](assets/following-activities.png)

Mit der Schaltfläche **Folgen** können Sie Einsendungen als Aktivitäten, [Benachrichtigungen](/help/communities/notifications.md) oder [Abonnement](/help/communities/subscriptions.md) folgen. Jedes Mal, wenn die Schaltfläche **Folgen** ausgewählt ist, können Sie eine Auswahl ein- oder ausschalten. Die Auswahl `Email Subscriptions` ist nur bei der Konfiguration vorhanden.

Wenn eine der folgenden Methoden ausgewählt ist, wird der Text der Schaltfläche in **Nach** geändert. Aus praktischen Gründen können Sie `Unfollow All` auswählen, um alle Methoden auszuschalten.

Die Schaltfläche **Folgen** wird angezeigt:

* Beim Anzeigen des Profils eines anderen Mitglieds.
* Auf einer Hauptseite mit Funktionen wie Foren, QnA und Blogs.

   * Folgt der gesamten Aktivität für diese allgemeine Funktion.

* Für einen bestimmten Eintrag, z. B. ein Forenthema, eine Frage zur Servicequalität oder einen Blog-Artikel.

   * Folgt der gesamten Aktivität für diesen spezifischen Eintrag.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Aktivitäts-Streams-Grundlagen](/help/communities/essentials-activities.md).
