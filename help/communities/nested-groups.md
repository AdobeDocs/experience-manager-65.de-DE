---
title: Verfassen verschachtelter Gruppen
seo-title: Verfassen verschachtelter Gruppen
description: Erstellen verschachtelter Gruppen
seo-description: Erstellen verschachtelter Gruppen
uuid: b377dc1b-bbb6-41c9-b0fc-8281e1410685
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 752235d2-21ac-46d2-82ed-5fec09c645e9
docset: aem65
exl-id: 55803b7a-9064-4392-9cc2-9f113fa8dc29
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 5%

---

# Erstellen verschachtelter Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen in der Autoreninstanz {#creating-groups-on-author}

In der AEM-Autoreninstanz über die globale Navigation:

* Wählen Sie **[!UICONTROL Communities]** > **[!UICONTROL Sites]** aus.
* Wählen Sie **[!UICONTROL engage folder]** aus, um ihn zu öffnen.
* Wählen Sie die Karte für die englische Site **[!UICONTROL Tutorial zu den ersten Schritten]** aus.

   * Wählen Sie das Kartenbild aus.
   * Wählen Sie *not* ein Symbol aus.

Das Ergebnis ist, die [Gruppenkonsole](/help/communities/groups.md) zu erreichen:

![create-group](assets/create-group.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie den Ordner Gruppen aus, um ihn zu öffnen. Die in der Veröffentlichung erstellte Gruppe ist sichtbar.

![create-new-group](assets/create-new-group.png)

## Hauptdarstellungsgruppe erstellen {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Site-Struktur für die Interaktion eine Gruppenfunktion enthält. Die Konfiguration der Funktion im `Reference Template` der Site ermöglicht standardmäßig die Auswahl einer beliebigen aktivierten Gruppenvorlage. Die für diese neue Gruppe ausgewählte Vorlage ist daher `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Wählen Sie **[!UICONTROL Gruppe erstellen]** aus.

* **Community-Gruppenvorlage**:

   * **[!UICONTROL Community-Gruppentitel]**: Kunst.
   * **[!UICONTROL Community-Gruppenbeschreibung]**: Eine übergeordnete Gruppe für verschiedene Kunstgruppen.
   * **[!UICONTROL Community-Gruppenstamm]**:  *als Standard* beibehalten.
   * **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprachen]**: Wählen Sie im Dropdown-Menü die verfügbaren Gemeinschaftsgruppensprachen aus. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * **[!UICONTROL Community-Gruppenname]**: Kunst.
   * **[!UICONTROL Vorlage]**: Dropdown-Liste auswählen  `Reference Group.`
   * Wählen Sie **[!UICONTROL Weiter]** aus.

![Verschachtelte Community-Gruppen](assets/parent-to-nestedgroup.png)

Fahren Sie mit den folgenden Einstellungen durch die anderen Bedienfelder:

* **[!UICONTROL Design]**

   * Ändern Sie das Design oder lassen Sie das Standarddesign der übergeordneten Site zu.
   * Wählen Sie **[!UICONTROL Weiter]** aus.

* **[!UICONTROL Einstellungen]**

   * **[!UICONTROL Moderation]**

      * Leer lassen (von der übergeordneten Site übernehmen).
   * **[!UICONTROL Mitgliedschaft]**

      * Standard `Optional Membership.` verwenden

      * **[!UICONTROL Miniaturansicht]**
         * `optional.*`
      * **[!UICONTROL Wählen Sie Weiter]** aus.



* Wählen Sie **[!UICONTROL Erstellen]**.

### Verschachtelung von Gruppen innerhalb der Artgruppe {#nesting-groups-within-arts-group}

Der Ordner `groups` enthält jetzt zwei Gruppen (aktualisieren Sie die Seite).

![Verschachteln der Gruppen](assets/create-community-group.png)

####  Gruppe veröffentlichen{#publish-group}

Bevor Sie in der Gruppe `arts` verschachtelte Gruppen erstellen, halten Sie den Mauszeiger über die Karte `arts` und wählen Sie das Veröffentlichungssymbol aus, um sie zu veröffentlichen.

![publish-site](assets/publish-site.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![group-publish](assets/group-published.png)

Die Gruppe `arts` sollte auch einen Ordner `groups` enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;Arts-Gruppe&quot;und erstellen Sie 3 verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedschaftseinstellungen:

1. **[!UICONTROL Visuell]**

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`, eine öffentliche Gruppe, die für alle Mitglieder geöffnet ist.

1. **[!UICONTROL Zielgruppe]**

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`, eine offene Gruppe, die für Mitglieder zur Verfügung steht.

1. **[!UICONTROL Verlauf]**

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Restricted Membership`, eine geheime Gruppe, die nur für eingeladene Mitglieder sichtbar ist. Laden Sie beispielsweise [demo user](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com` ein.

Aktualisieren Sie die Seite, um alle drei verschachtelten Gruppen (Untergruppen) anzuzeigen.

So navigieren Sie über die Communities Sites-Konsole zu den verschachtelten Gruppen:

* Wählen Sie **[!UICONTROL engagieren Sie den Ordner]**
* Wählen Sie die Karte **[!UICONTROL Erste Schritte - Tutorial]** aus.
* Ordner **[!UICONTROL Gruppen]** auswählen
* Wählen Sie **[!UICONTROL arts card]** aus.
* Ordner **[!UICONTROL Gruppen]** auswählen

![create-new-group2](assets/create-new-group2.png)

## Verlagsgruppen {#publishing-groups}

![publish-site](assets/publish-site.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* Jede Gruppe einzeln veröffentlichen:

   * Warten auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie verschachtelte Gruppen veröffentlichen:

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![group-publish](assets/group-published.png)

## Erlebnis bei der Veröffentlichung {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen zu erleben, wenn sie angemeldet sind, z. B. mit den [Demobenutzern](/help/communities/tutorials.md#demo-users), die für Folgendes verwendet werden:

* Mitglied der Gruppe Kunst/Verlauf : emily.andrews@mailinator.com/password
   * Die eingeschränkte (geheime) Gruppe, Kunst/Verlauf, ist sichtbar:
   * Kann optionale (öffentliche) Gruppen anzeigen.
   * Können eingeschränkten (offenen) Gruppen beitreten.

* Gruppenmanager: aaron.mcdonald@mailinator.com/password

   * Kann optionale (öffentliche) Gruppen anzeigen.
   * Können eingeschränkten (offenen) Gruppen beitreten.
   * Eingeschränkte (geheime) Gruppen werden nicht angezeigt.

Greifen Sie auf die Communities [Mitglieder und Gruppen-Konsolen](/help/communities/members.md) auf der Autoreninstanz zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.
