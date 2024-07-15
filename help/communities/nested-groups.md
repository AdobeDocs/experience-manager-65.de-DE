---
title: Verfassen verschachtelter Gruppen
description: Erfahren Sie, wie Sie verschachtelte Gruppen für eine Adobe Experience Manager Communities-Site erstellen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 55803b7a-9064-4392-9cc2-9f113fa8dc29
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---

# Verfassen verschachtelter Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen in der Autoreninstanz {#creating-groups-on-author}

In AEM -Autoreninstanz über die globale Navigation:

* Wählen Sie **[!UICONTROL Communities]** > **[!UICONTROL Sites]** aus.
* Wählen Sie **[!UICONTROL engage folder]** aus, um ihn zu öffnen.
* Wählen Sie die Karte für die englische Site **[!UICONTROL Erste Schritte-Tutorial]** aus.

   * Wählen Sie das Kartenbild aus.
   * Wählen Sie ein Symbol *nicht* aus.

Das Ergebnis besteht darin, die [Gruppenkonsole](/help/communities/groups.md) zu erreichen:

![create-group](assets/create-group.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie zum Öffnen den Ordner Gruppen aus. Die in Publish erstellte Gruppe wird angezeigt.

![create-new-group](assets/create-new-group.png)

## Erstellen einer Hauptdarstellungsgruppe {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Website-Struktur für die Interaktion die Funktion einer Gruppe enthält. Die Konfiguration der Funktion im `Reference Template` der Site ermöglicht standardmäßig die Auswahl einer beliebigen aktivierten Gruppenvorlage. Die für diese neue Gruppe ausgewählte Vorlage ist daher der `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Wählen Sie **[!UICONTROL Gruppe erstellen]**

* **Community-Gruppenvorlage**:

   * **[!UICONTROL Community-Gruppentitel]**: Kunst
   * **[!UICONTROL Community-Gruppenbeschreibung]**: Eine übergeordnete Gruppe für verschiedene Artgruppen
   * **[!UICONTROL Community-Gruppenstamm]**: *Behalten Sie den Standardwert* bei
   * **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprache(n)]**: Wählen Sie über das Dropdown-Menü die verfügbaren Community-Gruppensprachen aus. Im Menü werden alle Sprachen angezeigt, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt unter diesen Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * **[!UICONTROL Community-Gruppenname]**: arts
   * **[!UICONTROL Vorlage]**: Dropdown zur Auswahl von `Reference Group`
   * Wählen Sie **[!UICONTROL Weiter]**

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

* Wählen Sie **[!UICONTROL Erstellen]** aus.

### Verschachteln von Gruppen innerhalb der Artist Group {#nesting-groups-within-arts-group}

Der Ordner &quot;`groups`&quot; enthält jetzt zwei Gruppen (aktualisieren Sie die Seite).

![Verschachteln der Gruppen](assets/create-community-group.png)

#### Publish-Gruppe {#publish-group}

Bevor Sie in der Gruppe `arts` verschachtelte Gruppen erstellen, halten Sie den Mauszeiger über die Karte `arts` und wählen Sie das Veröffentlichungssymbol aus, um sie zu veröffentlichen.

![publish-site](assets/publish-site.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![group-publish](assets/group-published.png)

Die Gruppe `arts` sollte auch einen Ordner `groups` enthalten, jedoch einen, der leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;Arts-Gruppe&quot;und erstellen Sie drei verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedschaftseinstellungen:

1. **[!UICONTROL Visual]**

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`, eine öffentliche Gruppe, die allen Mitgliedern offen steht.

1. **[!UICONTROL Auditory]**

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`, eine offene Gruppe, die Mitgliedern zur Verfügung steht.

1. **[!UICONTROL Verlauf]**

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Restricted Membership` aus, eine geheime Gruppe, die nur für eingeladene Mitglieder sichtbar ist. Laden Sie beispielsweise [Demobenutzer](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com` ein.

Aktualisieren Sie die Seite, damit Sie alle drei verschachtelten Gruppen (Untergruppen) sehen können.

So navigieren Sie über die Communities Sites-Konsole zu den verschachtelten Gruppen:

* Wählen Sie den Ordner **[!UICONTROL engage]** aus.
* Wählen Sie die Karte **[!UICONTROL Erste Schritte - Tutorial]** aus.
* Wählen Sie den Ordner **[!UICONTROL Gruppen]** aus
* Wählen Sie **[!UICONTROL arts card]** aus
* Wählen Sie den Ordner **[!UICONTROL Gruppen]** aus

![create-new-group2](assets/create-new-group2.png)

## Verlagsgruppen {#publishing-groups}

![publish-site](assets/publish-site.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* Publish für jede Gruppe einzeln:

   * Warten auf die Bestätigung der Veröffentlichung der Gruppe.

* Publish die übergeordnete Gruppe vor der Veröffentlichung von Gruppen, die in Folgendes verschachtelt sind:

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![group-publish](assets/group-published.png)

## Erlebnis in Publish {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen zu erleben, wenn Sie sich angemeldet haben, z. B. mit den [Demobenutzern](/help/communities/tutorials.md#demo-users), die für Folgendes verwendet werden:

* Mitglied der Kunst-/Verlaufsgruppe: `emily.andrews@mailinator.com/password`
   * Die eingeschränkte (geheime) Gruppe, Kunst/Verlauf, ist sichtbar:
   * Möglichkeit, optionale (öffentliche) Gruppen anzuzeigen.
   * Möglichkeit, eingeschränkten (offenen) Gruppen beizutreten.

* Gruppenmanager: `aaron.mcdonald@mailinator.com/password`

   * Möglichkeit, optionale (öffentliche) Gruppen anzuzeigen.
   * Möglichkeit, eingeschränkten (offenen) Gruppen beizutreten.
   * Eingeschränkte (geheime) Gruppen können nicht angezeigt werden.

Greifen Sie auf die Communities [Mitglieder und Gruppen-Konsolen](/help/communities/members.md) auf der Autoreninstanz zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.
