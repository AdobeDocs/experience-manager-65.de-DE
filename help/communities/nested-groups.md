---
title: Erstellen von verschachtelten Gruppen
seo-title: Erstellen von verschachtelten Gruppen
description: Verschachtelte Gruppen erstellen
seo-description: Verschachtelte Gruppen erstellen
uuid: b377dc1b-bbb6-41c9-b0fc-8281e1410685
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 752235d2-21ac-46d2-82ed-5fec09c645e9
docset: aem65
translation-type: tm+mt
source-git-commit: c9fa5624a59f4b9a6f970628b03bbd8b7a277a73
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 5%

---


# Erstellen von verschachtelten Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen beim Autor {#creating-groups-on-author}

Bei AEM Author-Instanz über die globale Navigation:

* Wählen Sie **[!UICONTROL Communities] > **[!UICONTROL Sites]**.
* Wählen Sie **[!UICONTROL Ordner]** für Interaktion aus, um ihn zu öffnen.
* Wählen Sie die Karte für die Seite &quot; **[!UICONTROL Erste Schritte - Tutorial]** Englisch&quot;.

   * Wählen Sie das Kartenbild aus.
   * Wählen Sie *kein* Symbol aus.

Das Ergebnis ist, die [Gruppenkonsole](/help/communities/groups.md)zu erreichen:

![chlimage_1-91](assets/chlimage_1-91.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie den Ordner &quot;Gruppen&quot;, um ihn zu öffnen. Die bei der Veröffentlichung erstellte Gruppe ist sichtbar.

![chlimage_1-92](assets/chlimage_1-92.png)

## Hauptkunstgruppe erstellen {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Sitestruktur für den Einsatz eine Gruppenfunktion enthält. Die Konfiguration der Funktion in der `Reference Template` Standardeinstellung der Site ermöglicht die Auswahl einer aktivierten Gruppenvorlage. Die Vorlage, die für diese neue Gruppe gewählt wird, ist daher die `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Wählen Sie Gruppe **[!UICONTROL erstellen]**.

* **Community-Gruppenvorlage**:

   * **[!UICONTROL Community-Gruppentitel]**: Kunst.
   * **[!UICONTROL Community-Gruppenbeschreibung]**: Eine übergeordnete Gruppe für verschiedene Kunstgruppen.
   * **[!UICONTROL Community-Gruppenstamm]**: *als Standard* beibehalten.
   * **[!UICONTROL Zusätzliche verfügbare Community-Gruppensprache(n)]**: Verwenden Sie das Dropdownmenü, um die verfügbaren Gemeinschaftsgruppensprachen auszuwählen. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wurde. Benutzer können in diesem Schritt eine der folgenden Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Konsole &quot;Gruppen&quot;der jeweiligen Community-Sites erstellt.
   * **[!UICONTROL Community-Gruppenname]**: Kunst.
   * **[!UICONTROL Vorlage]**: Dropdown-Liste `Reference Group.`
   * Wählen Sie **[!UICONTROL Weiter]** aus.

![Verschachtelte Community-Gruppen](assets/parent-to-nestedgroup.png)

Führen Sie mit den folgenden Einstellungen weitere Schritte durch:

* **[!UICONTROL Design]**

   * Ändern Sie den Entwurf oder lassen Sie das Standarddesign der übergeordneten Site zu.
   * Wählen Sie **[!UICONTROL Weiter]** aus.

* **[!UICONTROL Einstellungen]**

   * **[!UICONTROL Moderation]**

      * Leer lassen (von übergeordneter Site übernehmen).
   * **[!UICONTROL Mitgliedschaft]**

      * Use default `Optional Membership.`

      * **[!UICONTROL Miniaturansicht]**
         * `optional.*`
      * **[!UICONTROL Wählen Sie Weiter]** aus.



* Wählen Sie **[!UICONTROL Erstellen]**.

### Verschachteln von Gruppen innerhalb der Artgruppe {#nesting-groups-within-arts-group}

Der `groups` Ordner enthält jetzt zwei Gruppen (aktualisieren Sie die Seite).

![Verschachteln von Gruppen](assets/create-community-group.png)

####  Gruppe veröffentlichen{#publish-group}

Bewegen Sie den Mauszeiger vor dem Erstellen von Gruppen, die innerhalb der `arts` Gruppe verschachtelt sind, über die `arts` Karte und wählen Sie das Symbol &quot;Veröffentlichen&quot;aus, um sie zu veröffentlichen.

![liking-component](assets/liking-component.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![chlimage_1-94](assets/chlimage_1-94.png)

Die `arts` Gruppe sollte auch einen `groups` Ordner enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;art group&quot;und erstellen Sie 3 verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedseinstellungen:

1. **[!UICONTROL Visuell]**

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`, eine öffentliche Gruppe, die für alle Mitglieder geöffnet ist.

1. **[!UICONTROL Audition]**

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`, eine offene Gruppe, die für Mitglieder zur Verfügung steht.

1. **[!UICONTROL Verlauf]**

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: select `Restricted Membership`, eine geheime Gruppe, die nur für eingeladene Mitglieder sichtbar ist. Beispiel: Einladen eines [Demobenutzers](/help/communities/tutorials.md#demo-users) `emily.andrews@mailinator.com`.

Aktualisieren Sie die Seite, um alle drei verschachtelten Gruppen (Unter-Communities) anzuzeigen.

So navigieren Sie von der Konsole Communities Sites zu den verschachtelten Gruppen:

* Ordner **[!UICONTROL für Interaktion auswählen]**
* Karte &quot;Erste **[!UICONTROL Schritte&quot;auswählen]**
* Ordner &quot; **[!UICONTROL Gruppen]** &quot;auswählen
* Karte **[!UICONTROL für Kunst auswählen]**
* Ordner &quot; **[!UICONTROL Gruppen]** &quot;auswählen

![configure-like](assets/configure-liking.png)

## Veröffentlichungsgruppen {#publishing-groups}

![chlimage_1-96](assets/chlimage_1-96.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* Veröffentlichen Sie jede Gruppe einzeln:

   * Warten auf Bestätigung der Veröffentlichung der Gruppe.

* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie verschachtelte Gruppen veröffentlichen:

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![chlimage_1-97](assets/chlimage_1-97.png)

## Erlebnis bei Veröffentlichung {#experience-on-publish}

Bei der Anmeldung können die verschiedenen Gruppen angezeigt werden, z. B. mit der [Demo-Benutzer](/help/communities/tutorials.md#demo-users) für:

* Mitglied der Gruppe &quot;Kunst/Verlauf&quot;: emily.andrews@mailinator.com/Kennwort
   * Die eingeschränkte (geheime) Gruppe, Kunst/Geschichte, ist sichtbar:
   * Können optionale (öffentliche) Gruppen sehen.
   * Kann eingeschränkten (offenen) Gruppen beitreten.

* Gruppenmanager: aaron.mcdonald@mailinator.com/Kennwort

   * Können optionale (öffentliche) Gruppen sehen.
   * Kann eingeschränkten (offenen) Gruppen beitreten.
   * Eingeschränkte (geheime) Gruppen können nicht angezeigt werden.

Greifen Sie auf die Communities [Members and Groups consoles](/help/communities/members.md) on author zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.

