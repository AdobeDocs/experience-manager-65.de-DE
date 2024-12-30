---
title: Erstellen verschachtelter Gruppen
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

# Erstellen verschachtelter Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen in der Autoreninstanz {#creating-groups-on-author}

In der AEM-Autoreninstanz über die globale Navigation:

* Wählen Sie **[!UICONTROL Communities]** > **[!UICONTROL Sites]** aus.
* Wählen Sie **[!UICONTROL Engage-Ordner]** aus, um ihn zu öffnen.
* Wählen Sie die Karte für die englische Site **[!UICONTROL Erste Schritte]** aus.

   * Wählen Sie das Kartenbild aus.
   * Wählen *nicht* Symbol aus.

Dadurch wird die „Gruppen[Konsole“ ](/help/communities/groups.md):

![create-group](assets/create-group.png)

Die Gruppenfunktion wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie zum Öffnen den Ordner Gruppen aus. Die in Publish erstellte Gruppe ist sichtbar.

![create-new-group](assets/create-new-group.png)

## Erstellen einer Hauptgruppe für Kunst {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Site-Struktur für die Interaktion die Funktion einer Gruppe enthält. Die Konfiguration der Funktion im `Reference Template` der Site ermöglicht standardmäßig die Auswahl einer beliebigen aktivierten Gruppenvorlage. Die für diese neue Gruppe ausgewählte Vorlage ist daher die `Reference Group`.

Diese Konsolen ähneln der Communities Sites -Konsole.

* Wählen Sie **[!UICONTROL Gruppe erstellen]**

* **Community-Gruppenvorlage**:

   * **[!UICONTROL Community-Gruppentitel]**: Künste
   * **[!UICONTROL Community-Gruppenbeschreibung]**: Eine übergeordnete Gruppe für verschiedene Kunstgruppen
   * **[!UICONTROL Community-Gruppenstamm]**: *Als Standard beibehalten*
   * **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprachen]**: Wählen Sie über das Dropdown-Menü die verfügbaren Community-Gruppensprachen aus. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wird. Benutzer können in diesem Schritt eine dieser Sprachen auswählen, um Gruppen in mehreren Gebietsschemata zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * **[!UICONTROL Community-Gruppenname]**: arts
   * **[!UICONTROL Vorlage]**: Dropdown zur Auswahl von `Reference Group`
   * Wählen Sie **[!UICONTROL Weiter]**

![Verschachtelte Community-Gruppen](assets/parent-to-nestedgroup.png)

Gehen Sie mit diesen Einstellungen durch die anderen Bedienfelder:

* **[!UICONTROL Design]**

   * Ändern Sie das Design oder lassen Sie das Design der standardmäßigen übergeordneten Site zu.
   * Wählen Sie **[!UICONTROL Weiter]** aus.

* **[!UICONTROL Einstellungen]**

   * **[!UICONTROL Moderation]**

      * Leer lassen (von übergeordneter Site erben).

   * **[!UICONTROL Mitgliedschaft]**

      * Standard-`Optional Membership.` verwenden

      * **[!UICONTROL Miniaturansicht]**
         * `optional.*`

      * **[!UICONTROL Klicken Sie auf Weiter]**.

* Wählen Sie **[!UICONTROL Erstellen]** aus.

### Verschachteln von Gruppen innerhalb der Arts-Gruppe {#nesting-groups-within-arts-group}

Der Ordner &quot;`groups`&quot; enthält jetzt zwei Gruppen (Seite aktualisieren).

![Verschachteln der Gruppen](assets/create-community-group.png)

#### Publish-Gruppe {#publish-group}

Bevor Sie innerhalb der `arts` verschachtelte Gruppen erstellen, bewegen Sie den Mauszeiger über die `arts` Karte und wählen Sie das Symbol Veröffentlichen aus, um sie zu veröffentlichen.

![publish-site](assets/publish-site.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![group-published](assets/group-published.png)

Die `arts` sollte auch einen `groups` Ordner enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner „Kunst-Gruppen“ und erstellen Sie drei verschachtelte Gruppen mit jeweils einer anderen Mitgliedschaftseinstellung:

1. **[!UICONTROL Visual]**

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`, eine öffentliche Gruppe, die für alle Mitglieder offen ist.

1. **[!UICONTROL auditiv]**

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`, eine offene Gruppe, die Mitgliedern zum Beitritt zur Verfügung steht.

1. **[!UICONTROL Verlauf]**

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Restricted Membership`, eine geheime Gruppe, die nur für eingeladene Mitglieder sichtbar ist. Laden Sie beispielsweise [Demo-Benutzer](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com` ein.

Aktualisieren Sie die Seite, damit alle drei verschachtelten Gruppen (Untergruppen) angezeigt werden.

So navigieren Sie über die Communities-Sites-Konsole zu den verschachtelten Gruppen:

* Wählen Sie den **[!UICONTROL Engage-Ordner]**
* Wählen Sie **[!UICONTROL Karte „Erste Schritte-Tutorial“]**
* Wählen Sie den Ordner **[!UICONTROL Gruppen]** aus
* Wählen Sie **[!UICONTROL Kunstkarte]**
* Wählen Sie den Ordner **[!UICONTROL Gruppen]** aus

![create-new-group2](assets/create-new-group2.png)

## Veröffentlichen von Gruppen {#publishing-groups}

![publish-site](assets/publish-site.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* Publish - jede Gruppe einzeln:

   * Warten auf Bestätigung, dass die Gruppe veröffentlicht wurde.

* Publish legt die übergeordnete Gruppe fest, bevor verschachtelte Gruppen veröffentlicht werden in:

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![group-published](assets/group-published.png)

## Erfahrung mit Publish {#experience-on-publish}

Sie können die verschiedenen Gruppen erleben, wenn Sie angemeldet sind, z. B. mit den [Demo-Benutzern](/help/communities/tutorials.md#demo-users) für:

* Art/History Gruppenmitglied: `emily.andrews@mailinator.com/password`
   * Die eingeschränkte (geheime) Gruppe, „Kunst/Geschichte“ ist sichtbar:
   * Kann optionale (öffentliche) Gruppen anzeigen.
   * Kann eingeschränkten (offenen) Gruppen beitreten.

* Gruppenleiter: `aaron.mcdonald@mailinator.com/password`

   * Kann optionale (öffentliche) Gruppen anzeigen.
   * Kann eingeschränkten (offenen) Gruppen beitreten.
   * Eingeschränkte (geheime) Gruppen können nicht angezeigt werden.

Greifen Sie auf der Autoreninstanz auf die Konsolen [Mitglieder und Gruppen](/help/communities/members.md) zu, um andere Benutzer zu verschiedenen Mitgliedsgruppen hinzuzufügen, die den Community-Gruppen entsprechen.
