---
title: Ersteinrichtung für Aktivierung
seo-title: Ersteinrichtung
description: Ersteinrichtung für Aktivierung
seo-description: Ersteinrichtung für Aktivierung
uuid: 873ec41d-c088-41d9-a535-de5300661de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: f2ac3d66-cc79-498f-83fb-dd96feb88de2
translation-type: tm+mt
source-git-commit: 570c970c328ded828680baeb1b04ab4361a36226
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---


# Ersteinrichtung für Aktivierung  {#initial-setup-for-enablement}

## Instanzen für Autoren- und Veröffentlichungsinstanzen in Beginn {#start-author-and-publish-instances}

Aus Entwicklungs- und Demonstrationsgründen müssen ein Autor und eine Instanz im Veröffentlichungsmodus ausgeführt werden.

Befolgen Sie die grundlegenden AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started) , die zu

* Autorendatei auf [localhost:4502](http://localhost:4502/)
* Umgebung auf [localhost veröffentlichen: 4503](http://localhost:4503/)

AEM Communities:

* Die Umgebung des Verfassers dient:

   * Entwicklung von Sites, Vorlagen, Komponenten, Ressourcen für die Aktivierung und Lernpfade.
   * Zuweisung von Mitgliedern und Gruppen von Mitgliedern zur Aktivierung von Ressourcen und Lernpfaden.
   * Erstellen von Berichten zu Zuweisungen, Ansichten und Beiträgen.
   * Verwaltungs- und Konfigurationseinstellungen.

* Die Umgebung zur Veröffentlichung ist für folgende Zwecke gedacht:

   * Schulung/Schulung auf der Grundlage von Themen, die vom Aktivierungsmanager verwaltet werden.
   * Ressourcen und Lernpfade für die Aktivierung und Bewertung kommentieren.
   * Kontakt mit den Ansprechpartnern für Ressourcen.

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).


## Neueste Communities-Version installieren {#install-latest-communities-release}

Dieses Lernprogramm erstellt eine [Community-Site](overview.md#enablement-community)für die Aktivierung. Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Ein Tutorial zur Erstellung einer [Interaktionssite](overview.md#engagement-community)finden Sie unter [Erste Schritte mit AEM Communities](getting-started.md).

## Aktivierungsfunktionen konfigurieren {#configure-enablement-features}

Um diesem Lernprogramm zu folgen, müssen Sie die Aktivierung [ordnungsgemäß installieren und](enablement.md)konfigurieren. Dazu sind Produkte von Drittanbietern wie MySQL und FFmpeg erforderlich.

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md)konfiguriert ist, stehen weitere Informationen in den [Berichten](reports.md) zur Verfügung, die zu Aktivierungsressourcen und Lernpfaden erstellt wurden, die Mitgliedern der Community (Lernenden) zugewiesen wurden.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der `Communities Sites` Konsole erstellt wurden, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert sein.

See [Configuring Email](email.md).

## Tunneldienst aktivieren {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autor-Umgebung ermöglicht der Tunnel-Dienst das Erstellen und Verwalten von in der Veröffentlichungs-Umgebung (Mitglieder) registrierten Benutzern und Benutzergruppen, das Zuweisen von Rollen zu vertrauenswürdigen Community-Mitgliedern und das Zuweisen von Inhalten zu Lernenden.

For more information see [Managing Users and User Groups](users.md).

Eine einfache Anleitung zum Aktivieren des Tunneldienstes finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Tutorial-Tags erstellen {#create-tutorial-tags}

Erstellen Sie Tags, die mithilfe des Tag-Namensraums von für die Interaktions- und Aktivierungsübungen verwendet werden `Tutorial`.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) , um die folgenden Tags zu erstellen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![tutorial-tags](assets/tutorial-tags.png)

Folgen Sie dann den Anweisungen:

1. [Festlegen der Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions)
1. [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)

Beispielpaket mit Tags, die für die Tutorials Erste Schritte mit AEM Communities erstellt wurden

[Datei laden](assets/communities_tutorialtags-10.zip)

## Aktivierungsmitglieder und -gruppen erstellen {#create-enablement-members-and-groups}

Für eine Community-Site, die eine Aktivierung ermöglicht, sollten Site-Besucher sich nicht [selbst registrieren und keine Social-Anmeldung](sites-console.md#user-management)verwenden können.

Stattdessen wird bei aktiviertem [Tunneldienst](#enable-the-tunnel-service) die [Mitgliederkonsole](members.md) verwendet, um neue Mitglieder in der Veröffentlichungs-Umgebung zu registrieren.

In diesem Lernprogramm werden in der Umgebung &quot;Veröffentlichen&quot;drei Mitglieder erstellt. Zwei Mitglieder werden Mitglieder einer Benutzergruppe, die einem Lernpfad zugeordnet ist, während das dritte Mitglied ein Kontakt zu einer Ressource für die Aktivierung wird.

Ein vierter Benutzer wird in der Umgebung &quot;Autor&quot;erstellt und hat die Rollen &quot;Communities Administrator&quot;und &quot;Community Enablement Manager&quot;zugewiesen.

>[!NOTE]
>
>Diese Mitglieder werden vor der Einrichtung der Community-Site für *Übungen* zur Aktivierung erstellt.
>
>Wenn sie danach erstellt wurden, könnten sie während der Mitgliedererstellung als Mitglieder der Gruppe *der* Übungsmitglieder hinzugefügt werden.
>
>Stattdessen werden sie später der Mitgliedergruppe [zugewiesen](enablement-create-site.md#assignuserstocommunityenablemembersgroup).


### Riley Taylor - Kursteilnehmer {#riley-taylor-enrollee}

[Erstellen Sie ein Mitglied](members.md#create-new-member) , das zu einer Gruppe von Lernenden hinzugefügt wird - der Community Ski Class Gruppe.

* **ID**: Riley
* **E-Mail**: riley.taylor@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Riley
* **Nachname**: Taylor

### Sidney Croft - Kursteilnehmer {#sidney-croft-enrollee}

[Erstellen Sie ein zweites Mitglied](members.md#create-new-member) , das der Community Ski Class Gruppe hinzugefügt wird.

* **ID**: sidney
* **E-Mail**: sidney.croft@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Sidney
* **Nachname**: Überlappend

### Quinn Harper - Ansprechpartner für die Aktivierungsressource und Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Erstellen Sie ein Mitglied](members.md#create-new-member) , das der Community-Site-Gruppe hinzugefügt wird, sobald die Site erstellt wurde. Mit dieser Mitgliedschaft kann das Mitglied als [Ressourcenkontakt](resources.md#settings) für die Aktivierung zugewiesen werden, wenn eine Aktivierungsressource für die Site erstellt wird.

* **ID**: Quinn
* **E-Mail**: quinn.harper@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Quinn
* **Nachname**: Harper

### hinzufügen einer Benutzergruppe - Community-Skiklasse {#add-a-user-group-community-ski-class}

[hinzufügen eine neue Gruppe](members.md#create-new-group) namens Community Ski Class.

* **ID**: community-ski-class
* **Name**: Community Ski Class
* **Beschreibung**: eine Beispielgruppe zum Zuweisen von Ressourcen für die Aktivierung
* **hinzufügen Mitglieder zu Gruppe** hinzufügen:

   * Riley
   * sidney

* Wählen Sie **[!UICONTROL Speichern]** aus

### Community-Ski-Klasseneigenschaften {#community-ski-class-properties}

![ski-class-properties](assets/ski-class-properties.png)

>[!NOTE]
>
>Während der Erstellung der Community-Site können bestehende Mitglieder und Gruppen zur Mitgliedergruppe der Community-Site hinzugefügt werden.


## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratorgruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (Mitglieder können aus der Community ausgeschlossen werden) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer beim *Autor*, dem die Rolle des Community-Administrators zugewiesen wurde:

* In der Autoreninstanz

   * For example, [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorberechtigungen

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **[!UICONTROL Bearbeiten]** die Option **[!UICONTROL Hinzufügen Benutzer]**.

* Geben Sie im `Create New User` Dialogfeld Folgendes ein:

   * **ID&amp;ast;**: Sirius
   * **E-Mail-Adresse**: sirius.nilson@mailinator.com
   * **Password&amp;ast;**: password
   * **Password&amp;amp bestätigen;ast;**: password
   * **Vorname**: Sirius
   * **Nachname&amp;last;**: Nilson

### Sirius der Community-Administratorgruppe zuweisen {#assign-sirius-to-community-administrators-group}

Blättern Sie nach unten zu `Add User to Groups`:

* &quot;C&quot;für die Suche eingeben

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus

![admin-role](assets/admin-role.png)

