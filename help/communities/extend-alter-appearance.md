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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 0%

---


# Erscheinungsbild (HBS) {#alter-the-appearance-hbs} ändern

Nachdem die Komponenten für das benutzerdefinierte Kommentarsystem im Anwendungsordner (/apps) vorhanden sind, wobei ein resourceSuperType auf das Standardkommentarsystem verweist und das benutzerdefinierte Modell/die benutzerdefinierte Ansicht registriert ist, kann die Implementierung geändert werden.

Bei einer einfachen Demonstration wird der Avatar des angemeldeten Benutzers, der einen Kommentar veröffentlicht, entfernt.

>[!NOTE]
>
>Um die Erweiterung zu verwenden, muss die Instanz des Kommentarsystems auf einer Website, die betroffen sein soll (/content), resourceType als benutzerdefiniertes Kommentarsystem festlegen.

## Ändern Sie die HBS-Skripte {#modify-the-hbs-scripts}

Verwenden von [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md):

* Öffnen Sie [/apps/custom/components/comments/comment/**comment.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comment/comment.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für einen Kommentar-Beitrag enthält (~ Zeile 21):

      ```
        <!--
         <<img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
         -->
      ```

* Öffnen Sie [/apps/custom/components/comments/**comments.hbs**](https://localhost:4502/crx/de/index.jsp#/apps/custom/components/comments/comments.hbs)

   * Kommentieren Sie das Tag aus, das den Avatar für den nächsten Kommentareintrag enthält (~ Zeile 44):

      ```
        <!--
         <img class="scf-composer-avatar" src="{{loggedInUser.avatarUrl}}"></img>
         -->
      ```

* Wählen Sie **Alle speichern**

### Benutzerdefinierte App replizieren {#replicate-custom-app}

Nachdem die Anwendung geändert wurde, muss die benutzerdefinierte Komponente erneut repliziert werden.

Eine Möglichkeit dazu ist:

* Über das Hauptmenü

   * Wählen Sie **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
   * Wählen Sie **[!UICONTROL Baum aktivieren]**.
   * Setzen Sie `Start Path` auf `/apps/custom`.
   * Deaktivieren Sie **[!UICONTROL Nur modifiziert]**.
   * Klicken Sie auf die Schaltfläche **[!UICONTROL Aktivieren]**.

### Ansicht - Modifizierter Kommentar auf der Seite mit veröffentlichten Beispielen {#view-modified-comment-on-published-sample-page}

[Wenn Sie das ](/help/communities/extend-sample-page.md#publish-sample-page) Erlebnis in der Veröffentlichungsinstanz fortsetzen und sich dennoch als derselbe Benutzer angemeldet haben, können Sie jetzt die Seite in der Umgebung &quot;Veröffentlichen&quot;aktualisieren, um die Änderung zum Entfernen des Avatars Ansicht:

![Ansicht-modifiziert-content](assets/view-modified-content.png)

### Beispiel für ein Kommentar-Erweiterungspaket {#sample-comment-extension-package}

Angehängt ist ein Paket der Anwendung für benutzerdefinierte Kommentare, die in diesem Lernprogramm erstellt wurde.

[Datei laden](assets/sample-comment-extension-6-1-fp3.zip)
