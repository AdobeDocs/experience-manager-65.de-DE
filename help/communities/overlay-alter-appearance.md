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
exl-id: cb8f6967-216c-46d3-a7ba-068b0f5e3b94
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Erscheinungsbild ändern {#alter-the-appearance}

## Skript {#modify-the-script} ändern

Das Skript comment.hbs ist für die Erstellung des gesamten HTML-Codes für jeden Kommentar verantwortlich.

So zeigen Sie den Avatar nicht neben jedem veröffentlichten Kommentar an:

1. Kopieren Sie `comment.hbs`von `libs`nach `apps`

   1. Wählen Sie nun eine der folgenden Optionen aus `/libs/social/commons/components/hbs/comments/comment/comment.hbs`
   1. Wählen Sie **[!UICONTROL Copy]**
   1. Wählen Sie nun eine der folgenden Optionen aus `/apps/social/commons/components/hbs/comments/comment`
   1. Wählen Sie **[!UICONTROL Paste]** aus.

1. Öffnen Sie die überlagerte `comment.hbs`

   * Doppelklicken Sie auf den Knoten `comment.hbs` in `/apps/social/commons/components/hbs/comments/comment folder`

1. Suchen Sie die folgenden Zeilen und löschen oder kommentieren Sie sie aus:

```xml
  <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

Löschen Sie die Zeilen oder umschließen Sie sie mit `<!--` und `-->`, um sie herauszukommentieren. Außerdem werden die Zeichen &quot;xxx&quot;als visueller Indikator hinzugefügt, wo der Avatar gewesen wäre.

```xml
   xxx
   <!-- do not display avatar with comment
    <aside class="scf-comment-author">
        <img class="scf-comment-avatar {{#if topLevel}}withTopLevel{{/if}}" src="{{author.avatarUrl}}"></img>
```

### Replizieren Sie die Überlagerung {#replicate-the-overlay}

Pushen Sie die überlagerte Kommentar-Komponente mithilfe des Replikations-Tools an die Veröffentlichungsinstanz.

>[!NOTE]
>
>Eine robustere Form der Replikation wäre, ein Paket in Package Manager zu erstellen und [zu aktivieren](/help/sites-administering/package-manager.md#replicating-packages). Ein Package kann exportiert und archiviert werden.

Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Bereitstellung]** > **[!UICONTROL Replikation]** und klicken Sie auf **[!UICONTROL Struktur aktivieren]**.

Geben Sie für den Startpfad `/apps/social/commons` ein und wählen Sie **[!UICONTROL Aktivieren]**.

![verify-content-template](assets/verify-content-template.png)

### Ergebnisse anzeigen {#view-results}

Wenn Sie sich als Administrator bei der Veröffentlichungsinstanz anmelden, z. B. https://localhost:4503/crx/de als Administrator/Administrator, können Sie überprüfen, ob die überlagerten Komponenten vorhanden sind.

Wenn Sie sich abmelden und sich erneut als `aaron.mcdonald@mailinator.com/password` anmelden und die Seite aktualisieren, werden Sie feststellen, dass der veröffentlichte Kommentar nicht mehr mit einem Avatar angezeigt wird, stattdessen wird eine einfache &quot;xxx&quot;angezeigt.

![create-template-component](assets/create-template-component.png)
