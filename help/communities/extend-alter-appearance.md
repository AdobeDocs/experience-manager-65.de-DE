---
title: Erscheinungsbild ändern (HBS)
description: Erfahren Sie, wie Sie das Erscheinungsbild (HBS) ändern können, indem Sie die HBS-Skripte bearbeiten.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
docset: aem65
exl-id: 27e1bff3-385e-4ced-87af-54044b7e8812
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Erscheinungsbild ändern (HBS) {#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das standardmäßige Kommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, können Sie die Implementierung bearbeiten.

Für eine einfache Demonstration, eine visuelle Funktion, wird der Avatar des angemeldeten Benutzers entfernt, der einen Kommentar veröffentlicht.

>[!NOTE]
>
>Um die Erweiterung zu verwenden, muss die Instanz des Kommentar-Systems auf einer Website, auf die sich die Auswirkungen auswirken sollen (/content), seinen resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## HBS-Skripte ändern {#modify-the-hbs-scripts}

Verwenden von [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Öffnen Sie [/apps/custom/components/comments/comment/**comment.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

     ```
       <!--
        <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
        -->
     ```

* Öffnen Sie [/apps/custom/components/comments/**comments.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentar-Eintrag enthält (~ Zeile 44):

     ```
       <!--
        <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
        -->
     ```

* Wählen Sie **Alle speichern**

### Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit hierfür ist:

* Über das Hauptmenü

   * Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]** aus.
   * Wählen Sie **[!UICONTROL Baum aktivieren]**.
   * Setzen Sie `Start Path` auf `/apps/custom`.
   * Heben Sie die Auswahl von **[!UICONTROL Nur geändert]** auf.
   * Wählen Sie die Schaltfläche **[!UICONTROL Aktivieren]** aus.

### Anzeigen von geänderten Kommentaren auf der veröffentlichten Beispielseite {#view-modified-comment-on-published-sample-page}

[Um das Erlebnis](/help/communities/extend-sample-page.md#publish-sample-page) in der Veröffentlichungsinstanz fortzusetzen, die noch als derselbe Benutzer angemeldet ist, ist es jetzt möglich, die Seite in der Veröffentlichungsumgebung zu aktualisieren, um die Änderung anzuzeigen und den Avatar zu entfernen:

![view-modified-content](assets/view-modified-content.png)

### Beispielpaket für Kommentar-Erweiterung {#sample-comment-extension-package}

Angehängt ist ein Paket der benutzerdefinierten Kommentaranwendung, die in diesem Tutorial erstellt wurde.

[Datei abrufen](assets/sample-comment-extension-6-1-fp3.zip)
