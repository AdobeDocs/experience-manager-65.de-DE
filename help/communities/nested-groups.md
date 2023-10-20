---
title: Verfassen verschachtelter Gruppen
description: Erfahren Sie, wie Sie verschachtelte Gruppen für eine Adobe Experience Manager Communities-Site erstellen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 55803b7a-9064-4392-9cc2-9f113fa8dc29
source-git-commit: f03d0ab9d0f491441378e16e1590d33651f064b5
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 4%

---

# Verfassen verschachtelter Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen in der Autoreninstanz {#creating-groups-on-author}

In AEM -Autoreninstanz über die globale Navigation:

* Auswählen **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.
* Auswählen **[!UICONTROL engagieren-Ordner]** , um es zu öffnen.
* Wählen Sie die Karte für die **[!UICONTROL Tutorial &quot;Erste Schritte&quot;]** englische Site.

   * Wählen Sie das Kartenbild aus.
   * Do *not* ein Symbol auswählen.

Das Ergebnis ist, die [Gruppenkonsole](/help/communities/groups.md):

![create-group](assets/create-group.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie zum Öffnen den Ordner Gruppen aus. Die in der Veröffentlichungsinstanz erstellte Gruppe ist sichtbar.

![create-new-group](assets/create-new-group.png)

## Erstellen einer Hauptdarstellungsgruppe {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Website-Struktur für die Interaktion die Funktion einer Gruppe enthält. Die Konfiguration der Funktion im `Reference Template` erlaubt standardmäßig die Auswahl einer beliebigen aktivierten Gruppenvorlage. Die für diese neue Gruppe ausgewählte Vorlage ist daher die `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Auswählen **[!UICONTROL Gruppe erstellen]**

* **Community-Gruppenvorlage**:

   * **[!UICONTROL Community-Gruppentitel]**: Kunst
   * **[!UICONTROL Community-Gruppenbeschreibung]**: Eine übergeordnete Gruppe für verschiedene Kunstgruppen
   * **[!UICONTROL Community-Gruppenstamm]**: *Lassen Sie als Standard*
   * **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprachen]**: Wählen Sie über das Dropdown-Menü die verfügbaren Gemeinschaftsgruppensprachen aus. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * **[!UICONTROL Community-Gruppenname]**: arts
   * **[!UICONTROL Vorlage]**: Dropdown zur Auswahl `Reference Group`
   * Wählen Sie **[!UICONTROL Weiter]** aus

![Verschachtelte Community-Gruppen](assets/parent-to-nestedgroup.png)

Fahren Sie mit den folgenden Einstellungen durch die anderen Bedienfelder:

* **[!UICONTROL Design]**

   * Ändern Sie das Design oder lassen Sie das Standarddesign der übergeordneten Site zu.
   * Wählen Sie **[!UICONTROL Weiter]** aus.

* **[!UICONTROL Einstellungen]**

   * **[!UICONTROL Moderation]**

      * Leer lassen (von der übergeordneten Site übernehmen).

   * **[!UICONTROL Mitgliedschaft]**

      * Standard verwenden `Optional Membership.`

      * **[!UICONTROL Miniaturansicht]**
         * `optional.*`

      * **[!UICONTROL Wählen Sie Weiter]** aus.

* Wählen Sie **[!UICONTROL Erstellen]** aus.

### Verschachteln von Gruppen innerhalb der Artist Group {#nesting-groups-within-arts-group}

Die `groups` -Ordner enthält nun zwei Gruppen (aktualisieren Sie die Seite).

![Verschachteln der Gruppen](assets/create-community-group.png)

####  Gruppe veröffentlichen {#publish-group}

Vor dem Erstellen von Gruppen, die innerhalb der `arts` -Gruppe, bewegen Sie den Mauszeiger über die `arts` und wählen Sie das Veröffentlichungssymbol aus, um es zu veröffentlichen.

![publish-site](assets/publish-site.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![group-publish](assets/group-published.png)

Die `arts` -Gruppe sollte auch `groups` -Ordner, jedoch einer, der leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;Arts-Gruppe&quot;und erstellen Sie drei verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedschaftseinstellungen:

1. **[!UICONTROL Visuell]**

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Auswahl `Optional Membership`, eine öffentliche Gruppe, die allen Mitgliedern offen steht.

1. **[!UICONTROL Zielgruppe]**

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Auswahl `Required Membership`, eine offene Gruppe, der Mitglieder beitreten können.

1. **[!UICONTROL Verlauf]**

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Auswahl `Restricted Membership`, eine geheime Gruppe, die nur für eingeladene Mitglieder sichtbar ist. Beispiel: Einladen [Demobenutzer](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com`.

Aktualisieren Sie die Seite, damit Sie alle drei verschachtelten Gruppen (Untergruppen) sehen können.

So navigieren Sie über die Communities Sites-Konsole zu den verschachtelten Gruppen:

* Wählen Sie die **[!UICONTROL engagieren-Ordner]**
* Auswählen **[!UICONTROL Karte des Tutorials &quot;Erste Schritte&quot;]**
* Wählen Sie die **[!UICONTROL Gruppen]** Ordner
* Auswählen **[!UICONTROL Kundenkarte]**
* Wählen Sie die **[!UICONTROL Gruppen]** Ordner

![create-new-group2](assets/create-new-group2.png)

## Verlagsgruppen {#publishing-groups}

![publish-site](assets/publish-site.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* Jede Gruppe einzeln veröffentlichen:

   * Warten auf die Bestätigung der Veröffentlichung der Gruppe.

* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie verschachtelte Gruppen veröffentlichen:

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![group-publish](assets/group-published.png)

## Erlebnis bei Veröffentlichung {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen bei der Anmeldung zu erleben, z. B. mit der [Demobenutzer](/help/communities/tutorials.md#demo-users) verwendet für:

* Mitglied der Gruppe Kunst/Verlauf : `emily.andrews@mailinator.com/password`
   * Die eingeschränkte (geheime) Gruppe, Kunst/Verlauf, ist sichtbar:
   * Möglichkeit, optionale (öffentliche) Gruppen anzuzeigen.
   * Möglichkeit, eingeschränkten (offenen) Gruppen beizutreten.

* Gruppenmanager: `aaron.mcdonald@mailinator.com/password`

   * Möglichkeit, optionale (öffentliche) Gruppen anzuzeigen.
   * Möglichkeit, eingeschränkten (offenen) Gruppen beizutreten.
   * Eingeschränkte (geheime) Gruppen können nicht angezeigt werden.

Zugriff auf Communities [Mitglieder und Gruppenkonsolen](/help/communities/members.md) auf Autor , um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.
