---
title: Erscheinungsbild ändern (HBS)
description: Erfahren Sie, wie Sie das Erscheinungsbild (HBS) ändern können, indem Sie die HBS-Skripte bearbeiten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 27e1bff3-385e-4ced-87af-54044b7e8812
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# Erscheinungsbild ändern (HBS) {#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das standardmäßige Kommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, können Sie die Implementierung bearbeiten.

Für eine einfache Demonstration, eine visuelle Funktion, wird der Avatar des angemeldeten Benutzers entfernt, der einen Kommentar veröffentlicht.

>[!NOTE]
>
>Um die Erweiterung zu verwenden, muss die Instanz des Kommentar-Systems auf einer Website, auf die sich die Auswirkungen auswirken sollen (/content), seinen resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## HBS-Skripte ändern {#modify-the-hbs-scripts}

Verwenden [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Öffnen [/apps/custom/components/comments/comment/**comment.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

     ```
       <!--
        <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
        -->
     ```

* Öffnen [/apps/custom/components/comments/**comments.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentar-Eintrag enthält (~ Zeile 44):

     ```
       <!--
        <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
        -->
     ```

* Klicken Sie auf **Alle speichern**

### Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit hierfür ist:

* Über das Hauptmenü

   * Auswählen **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Replikation]**.
   * Auswählen **[!UICONTROL Baum aktivieren]**.
   * Setzen Sie `Start Path` auf `/apps/custom`.
   * Auswahl deaktivieren **[!UICONTROL Nur geändert]**.
   * Auswählen **[!UICONTROL Aktivieren]** Schaltfläche.

### Anzeigen von geänderten Kommentaren auf der veröffentlichten Beispielseite {#view-modified-comment-on-published-sample-page}

[Fortführen des Erlebnisses](/help/communities/extend-sample-page.md#publish-sample-page) In der Veröffentlichungsinstanz, die noch als derselbe Benutzer angemeldet ist, ist es jetzt möglich, die Seite in der Veröffentlichungsumgebung zu aktualisieren, um die Änderung zum Entfernen des Avatars anzuzeigen:

![view-modified-content](assets/view-modified-content.png)

### Beispielpaket für Kommentar-Erweiterung {#sample-comment-extension-package}

Angehängt ist ein Paket der benutzerdefinierten Kommentaranwendung, die in diesem Tutorial erstellt wurde.

[Datei abrufen](assets/sample-comment-extension-6-1-fp3.zip)
