---
title: Erscheinungsbild ändern
seo-title: Erscheinungsbild ändern
description: Skript ändern
seo-description: Skript ändern
uuid: 30555b9f-da29-4115-9ed5-25f80a247bd6
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c9d31ed8-c105-453b-bd3c-4660dfd81272
docset: aem65
translation-type: tm+mt
source-git-commit: 48afa2146d0dcbab4beaa1044645c269b49fd7ff

---


# Erscheinungsbild ändern {#alter-the-appearance}

## Skript ändern {#modify-the-script}

Das Skript &quot;comment.hbs&quot;ist für die Erstellung des gesamten HTML für jeden Kommentar zuständig.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren `comment.hbs`von `libs`nach `apps`

   1. Wählen Sie nun eine der folgenden Optionen aus `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Auswahl **kopieren**
   1. Wählen Sie nun eine der folgenden Optionen aus `/apps/social/commons/components/hbs/comments/comment`
   1. Einfügen **auswählen**

1. Öffnen Sie die Überlagerung `comment.hbs`

   * Dublette-Click auf Knoten `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Löschen Sie entweder die Zeilen oder umschließen Sie sie `<!--` und `-->` kommentieren Sie sie aus. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

```xml
   xxx
   <!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

### Overlay replizieren {#replicate-the-overlay}

Schieben Sie die überlagerte Kommentarkomponente mithilfe des Replizierungswerkzeugs an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine stabilere Form der Replikation wäre, ein Paket im Package Manager zu erstellen und es zu [aktivieren](/help/sites-administering/package-manager.md#replicating-packages) . Ein Paket kann exportiert und archiviert werden.


Wählen Sie in der globalen Navigation &quot; **[!UICONTROL Werkzeuge]** &quot;> &quot; **[!UICONTROL Bereitstellung]** &quot;> &quot; **[!UICONTROL Replikation]** &quot;und klicken Sie auf &quot; **[!UICONTROL Struktur]** aktivieren&quot;.

Geben Sie für den Beginn Pfad ein `/apps/social/commons` und wählen Sie **[!UICONTROL Aktivieren]**.

![chlimage_1-77](assets/chlimage_1-77.png)

### Ansichten {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. https://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden, sich erneut anmelden `aaron.mcdonald@mailinator.com/password` und die Seite aktualisieren, werden Sie feststellen, dass der gepostete Kommentar nicht mehr mit einem Avatar angezeigt wird, sondern eine einfache &quot;xxx&quot;.

![chlimage_1-78](assets/chlimage_1-78.png)

