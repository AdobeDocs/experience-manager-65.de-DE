---
title: Erscheinungsbild ändern (HBS)
seo-title: Erscheinungsbild ändern
description: Ändern der HBS-Skripten
seo-description: Ändern der HBS-Skripten
uuid: cff24505-dbb3-4312-9b1b-c1693b8d1c98
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e0da09b3-725d-4ed1-9273-2532132f6918
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Erscheinungsbild ändern (HBS){#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsverzeichnis (/apps) vorhanden sind, wobei ein resourceSuperType auf das Standard-Kommentarsystem verweist und das benutzerdefinierte Modell/View registriert ist, kann die Implementierung geändert werden.

Bei einer einfachen Demonstration wird der Avatar des angemeldeten Benutzers, der einen Kommentar veröffentlicht, entfernt.

>[!NOTE]
>
>Um die Erweiterung zu verwenden, muss die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll (/content), resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## Ändern der HBS-Skripten {#modify-the-hbs-scripts}

Using [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* open [/apps/custom/components/comments/comment/**comment.hbs **](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
      <!--
       <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
       -->
      ```

* open [/apps/custom/components/comments/**comments.hbs **](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentar-Eintrag enthält (~ Zeile 44):

      ```
      <!--
       <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
       -->
      ```

* Wählen Sie **Alle speichern** aus.

### Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit dazu ist

* aus dem Hauptmenü

   * Wählen Sie **Tools > Vorgänge > Replikation**
   * auswählen `Activate Tree`
   * einstellen `Start Path`: nach `/apps/custom`
   * deselect `Only Modified`
   * Schaltfläche `Activate`auswählen

### Änderungskommentar auf der Seite &quot;Veröffentlichte Beispielseite&quot;anzeigen {#view-modified-comment-on-published-sample-page}

[Wenn Sie das Erlebnis](/help/communities/extend-sample-page.md#publish-sample-page) auf der Veröffentlichungsinstanz fortsetzen, die noch als derselbe Benutzer angemeldet ist, können Sie jetzt die Seite in der Veröffentlichungsumgebung aktualisieren, um die Änderung zum Entfernen des Avatars anzuzeigen:

![chlimage_1-136](assets/chlimage_1-136.png)

### Beispielkommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der Anwendung für benutzerdefinierte Kommentare, die in diesem Lernprogramm erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)
