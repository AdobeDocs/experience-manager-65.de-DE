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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Erstellen von verschachtelten Gruppen{#authoring-nested-groups}

## Erstellen von Gruppen beim Autor {#creating-groups-on-author}

Bei AEM-Autoreninstanz aus der globalen Navigation:

* Wählen Sie** Communities, Sites.**
* Wählen Sie **Ordner** für Interaktion aus, um ihn zu öffnen.
* Wählen Sie die Karte für die Seite &quot; **Erste Schritte - Tutorial** Englisch&quot;.

   * Wählen Sie das Kartenbild aus.
   * Wählen Sie *kein* Symbol aus.

Das Ergebnis ist, die [Gruppenkonsole](/help/communities/groups.md)zu erreichen:

![chlimage_1-91](assets/chlimage_1-91.png)

Die Funktion &quot;Gruppen&quot;wird als Ordner angezeigt, in dem Instanzen von Gruppen erstellt werden. Wählen Sie den Ordner &quot;Gruppen&quot;, um ihn zu öffnen. Die bei der Veröffentlichung erstellte Gruppe ist sichtbar.

![chlimage_1-92](assets/chlimage_1-92.png)

## Hauptkunstgruppe erstellen {#create-main-arts-group}

Diese Gruppe kann erstellt werden, da die Sitestruktur für den Einsatz eine Gruppenfunktion enthält. Die Konfiguration der Funktion in der `Reference Template` Standardeinstellung der Site ermöglicht die Auswahl einer aktivierten Gruppenvorlage. Die Vorlage, die für diese neue Gruppe gewählt wird, ist daher die `Reference Group`.

Diese Konsolen ähneln der Communities Sites-Konsole.

* Wählen Sie Gruppe **erstellen.**
* **Community-Gruppenvorlage**:

   * Community-Gruppentitel: Kunst.
   * Community-Gruppenbeschreibung: Eine übergeordnete Gruppe für verschiedene Kunstgruppen.
   * Community-Gruppenstamm: Als Standard *beibehalten.*
   * Zusätzliche verfügbare Community-Gruppensprache(n): Verwenden Sie das Dropdownmenü, um die verfügbaren Gemeinschaftsgruppensprachen auszuwählen. Das Menü zeigt alle Sprachen an, in denen die übergeordnete Community-Site erstellt wurde. Benutzer können in diesem Schritt eine der folgenden Sprachen auswählen, um Gruppen in mehreren Gebietsschemas zu erstellen. Dieselbe Gruppe wird in mehreren angegebenen Sprachen in der Gruppenkonsole der jeweiligen Community-Sites erstellt.
   * Community-Gruppenname: Kunst.
   * Vorlage: Dropdown-Liste `Reference Group.`
   * `Select Next.`

![Verschachtelte Community-Gruppen](assets/parent-to-nestedgroup.png)

Führen Sie mit den folgenden Einstellungen weitere Schritte durch:

* **Design**

   * Ändern Sie den Entwurf oder lassen Sie das Standarddesign der übergeordneten Site zu.
   * Wählen Sie **Weiter.**

* **Einstellungen**

   * **Moderation**

      * leer lassen (von der übergeordneten Site übernehmen).
   * **Mitgliedschaft**

      * use default `Optional Membership.`
   * **Miniatur**

      * `*optional.*`
   * `Select Next.`




* Wählen Sie **Erstellen.**

### Verschachteln von Gruppen innerhalb der Artgruppe {#nesting-groups-within-arts-group}

Der `groups` Ordner enthält jetzt zwei Gruppen (aktualisieren Sie die Seite).

![Verschachteln von Gruppen](assets/create-community-group.png)

####  Gruppe veröffentlichen{#publish-group}

Bewegen Sie den Mauszeiger vor dem Erstellen von innerhalb der `arts`Gruppe verschachtelten Gruppen über die `arts` Karte und wählen Sie das Symbol &quot;Veröffentlichen&quot;, um sie zu veröffentlichen.

![chlimage_1-93](assets/chlimage_1-93.png)

Warten Sie auf die Bestätigung, dass die Gruppe veröffentlicht wurde.

![chlimage_1-94](assets/chlimage_1-94.png)

Die `arts` Gruppe sollte auch einen `groups` Ordner enthalten, der jedoch leer ist und in dem neue Gruppen erstellt werden können. Navigieren Sie zum Ordner &quot;art group&quot;und erstellen Sie 3 verschachtelte Gruppen mit jeweils unterschiedlichen Mitgliedseinstellungen:

1. Visuell

   * Titel: `Visual Arts`
   * Name: `visual`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Optional Membership`eine öffentliche Gruppe, die allen Mitgliedern offen steht

1. Audition

   * Titel: `Auditory Arts`
   * Name: `auditory`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Required Membership`eine offene Gruppe aus, die für die Mitglieder verfügbar ist

1. Verlauf

   * Titel: `Art History`
   * Name: `history`
   * Vorlage: `Reference Group`
   * Mitgliedschaft: Wählen Sie `Restricted Membership`eine geheime Gruppe, die nur für eingeladene Mitglieder als Beispiel sichtbar ist, und laden Sie [Demo-Benutzer](/help/communities/tutorials.md#demo-users) ein `emily.andrews@mailinator.com`

Aktualisieren Sie die Seite, um alle drei verschachtelten Gruppen (Unter-Communities) anzuzeigen.

So navigieren Sie von der Konsole Communities Sites zu den verschachtelten Gruppen:

* Interaktiven Ordner auswählen
* Erste Schritte - Lernkarte auswählen
* Ordner &quot;Gruppen&quot;
* Kundenkarte auswählen
* Ordner &quot;Gruppen&quot;

![chlimage_1-95](assets/chlimage_1-95.png)

## Veröffentlichungsgruppen {#publishing-groups}

![chlimage_1-96](assets/chlimage_1-96.png)

Nach der Veröffentlichung der Haupt-Community-Site:

* jede Gruppe einzeln veröffentlichen

   * auf Bestätigung der Veröffentlichung der Gruppe warten

* Veröffentlichen Sie die übergeordnete Gruppe, bevor Sie in

   * Alle Gruppen müssen von oben nach unten veröffentlicht werden.

![chlimage_1-97](assets/chlimage_1-97.png)

## Erlebnis bei Veröffentlichung {#experience-on-publish}

Es ist möglich, die verschiedenen Gruppen bei der Anmeldung zu erleben, zum Beispiel mit der [Demo-Benutzer](/help/communities/tutorials.md#demo-users) für

* Mitglied der Gruppe &quot;Kunst/Verlauf&quot;: emily.andrews@mailinator.com/Kennwort

   * die eingeschränkte (geheime) Gruppe, Kunst/Geschichte, sichtbar ist
   * kann optionale (öffentliche) Gruppen anzeigen
   * kann eingeschränkte (offene) Gruppen beitreten

* Gruppenmanager: aaron.mcdonald@mailinator.com/Kennwort

   * kann optionale (öffentliche) Gruppen anzeigen
   * kann eingeschränkte (offene) Gruppen beitreten
   * Eingeschränkte (geheime) Gruppen können nicht angezeigt werden

Greifen Sie auf die Communities [Members and Groups consoles](/help/communities/members.md) on author zu, um weitere Benutzer zu verschiedenen Mitgliedergruppen hinzuzufügen, die den Community-Gruppen entsprechen.

