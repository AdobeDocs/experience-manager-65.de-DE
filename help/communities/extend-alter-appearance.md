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
source-git-commit: 570c970c328ded828680baeb1b04ab4361a36226
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Erscheinungsbild ändern (HBS) {#alter-the-appearance-hbs}

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, wobei ein resourceSuperType auf das Standardkommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, kann die Implementierung geändert werden.

Bei einer einfachen Demonstration wird der Avatar des angemeldeten Benutzers, der einen Kommentar veröffentlicht, entfernt.

>[!NOTE]
>
>Um die Erweiterung zu verwenden, muss die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll (/content), resourceType als benutzerdefiniertes Kommentarsystem festlegen.


## Ändern der HBS-Skripten {#modify-the-hbs-scripts}

Using [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Öffnen [/apps/custom/components/comments/comment/**comment.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
        <!--
         <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
         -->
      ```

* Öffnen [/apps/custom/components/comments/**comments.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentareintrag enthält (~ Zeile 44):

      ```
        <!--
         <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
         -->
      ```

* Select **Save All**

### Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit dazu ist:

* Über das Hauptmenü

   * Wählen Sie **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
   * Wählen Sie **[!UICONTROL Baum]** aktivieren.
   * Auf `Start Path``/apps/custom`.
   * Deaktivieren Sie die Option **[!UICONTROL Nur geändert]**.
   * Klicken Sie auf **[!UICONTROL Aktivieren]** .

### Änderungskommentar zur Ansicht auf der Seite &quot;Veröffentlichte Beispieldatei&quot; {#view-modified-comment-on-published-sample-page}

[Wenn Sie das Erlebnis](/help/communities/extend-sample-page.md#publish-sample-page) in der Veröffentlichungsinstanz fortsetzen und weiterhin als derselbe Benutzer angemeldet sind, können Sie jetzt die Seite in der Umgebung &quot;Veröffentlichen&quot;aktualisieren, um die Änderung zum Entfernen des Avatars Ansicht:

![ansicht-modifiziert-content](assets/view-modified-content.png)

### Beispielkommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der Anwendung für benutzerdefinierte Kommentare, die in diesem Lernprogramm erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)
