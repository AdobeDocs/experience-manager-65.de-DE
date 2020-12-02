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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---


# Initial Setup for Enablement {#initial-setup-for-enablement}

## Autoreninstanzen und Veröffentlichungsinstanzen für Beginn {#start-author-and-publish-instances}

Aus Entwicklungs- und Demonstrationsgründen müssen ein Autor und eine Instanz im Veröffentlichungsmodus ausgeführt werden.

Befolgen Sie die grundlegenden AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), die zu

* Autorendatei auf [localhost:4502](http://localhost:4502/)
* Umgebung für Veröffentlichung auf [localhost:4503](http://localhost:4503/)

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
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [basic handling](../../help/sites-authoring/basic-handling.md) und [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version {#install-latest-communities-release} installieren

Dieses Lernprogramm erstellt eine [Community-Site für die Aktivierung](overview.md#enablement-community). Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Übung, die eine [Community-Site für Interaktionen](overview.md#engagement-community) erstellt, finden Sie unter [Erste Schritte mit AEM Communities](getting-started.md).

## Aktivierungsfunktionen konfigurieren {#configure-enablement-features}

Um diesem Lernprogramm zu folgen, müssen Sie die [configure-Aktivierung](enablement.md) ordnungsgemäß installieren und konfigurieren. Hierfür sind Drittanbieterprodukte wie MySQL und FFmpeg erforderlich.

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md) konfiguriert ist, stehen weitere Informationen in den [Berichten](reports.md) zur Verfügung, die für Aktivierungsressourcen und Lernpfade generiert wurden, die Community-Mitgliedern (Lernenden) zugewiesen wurden.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der Konsole `Communities Sites` erstellt wurden, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert sein.

Siehe [E-Mail konfigurieren](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autor-Umgebung ermöglicht der Tunnel-Dienst das Erstellen und Verwalten von in der Veröffentlichungs-Umgebung (Mitglieder) registrierten Benutzern und Benutzergruppen, das Zuweisen von Rollen zu vertrauenswürdigen Community-Mitgliedern und das Zuweisen von Inhalten zu Lernenden.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Eine einfache Anleitung zum Aktivieren des Tunneldienstes finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Tutorial-Tags erstellen {#create-tutorial-tags}

Erstellen Sie mithilfe des Tag-Namensraums von `Tutorial` Tags, die für die Interaktions- und Aktivierungsübungen verwendet werden sollen.

Verwenden Sie die Tagging-Konsole [Tagging](../../help/sites-administering/tags.md#tagging-console), um die folgenden Tags zu erstellen:

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

Für eine Community-Site, auf der eine Aktivierung möglich ist, sollten Site-Besucher nicht in der Lage sein, [sich selbst zu registrieren oder die Anmeldung über soziale Netzwerke](sites-console.md#user-management) zu verwenden.

Stattdessen wird bei aktiviertem [Tunneldienst](#enable-the-tunnel-service) die [Members-Konsole](members.md) verwendet, um neue Mitglieder in der Veröffentlichungs-Umgebung zu registrieren.

In diesem Lernprogramm werden in der Umgebung &quot;Veröffentlichen&quot;drei Mitglieder erstellt. Zwei Mitglieder werden Mitglieder einer Benutzergruppe, die einem Lernpfad zugeordnet ist, während das dritte Mitglied ein Kontakt zu einer Ressource für die Aktivierung wird.

Ein vierter Benutzer wird in der Umgebung &quot;Autor&quot;erstellt und hat die Rollen &quot;Communities Administrator&quot;und &quot;Community Enablement Manager&quot;zugewiesen.

>[!NOTE]
>
>Diese Mitglieder werden vor der Erstellung der Community-Site *Aktivierungsübung* erstellt.
>
>Wenn sie anschließend erstellt wurden, könnten sie während der Mitgliedererstellung als Mitglieder der Gruppe *Aktivierungsübungsmitglieder* hinzugefügt werden.
>
>Stattdessen werden sie später [der Mitgliedergruppe](enablement-create-site.md#assignuserstocommunityenablemembersgroup) zugewiesen.

### Riley Taylor - Einschreibung {#riley-taylor-enrollee}

[Erstellen Sie ein ](members.md#create-new-member) Mitglied, das zu einer Gruppe von Lernenden hinzugefügt wird - der Community Ski Class Gruppe.

* **ID**: Riley
* **E-Mail**: riley.taylor@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Riley
* **Nachname**: Taylor

### Sidney Croft - Einschreibung {#sidney-croft-enrollee}

[Erstellen Sie ein zweites ](members.md#create-new-member) Mitglied, das der Community Ski Class Gruppe hinzugefügt wird.

* **ID**: sidney
* **E-Mail**: sidney.croft@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Sidney
* **Nachname**: Überlappend

### Quinn Harper - Ansprechpartner für die Aktivierungsressource und Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Erstellen Sie ein ](members.md#create-new-member) Mitglied, das der Community-Site-Gruppe hinzugefügt wird, sobald die Site erstellt wurde. Durch diese Mitgliedschaft kann dem Mitglied die Aktivierung [Ressourcenkontakt](resources.md#settings) zugewiesen werden, wenn eine Aktivierungsressource für die Site erstellt wird.

* **ID**: Quinn
* **E-Mail**: quinn.harper@mailinator.com
* **Kennwort:** password
* **Kennwort** bestätigen: password
* **Vorname**: Quinn
* **Nachname**: Harper

### hinzufügen einer Benutzergruppe - Community Ski Class {#add-a-user-group-community-ski-class}

[hinzufügen eine neue ](members.md#create-new-group) Gruppe mit dem Namen Community Ski Class.

* **ID**: community-ski-class
* **Name**: Community Ski Class
* **Beschreibung**: eine Beispielgruppe zum Zuweisen von Ressourcen für die Aktivierung
* **hinzufügen Mitglieder zu Gruppe** &#39;hinzufügen&#39;:

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

Erstellen Sie einen Benutzer unter *author*, dem die Rolle des Community-Administrators zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorberechtigungen

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **[!UICONTROL Bearbeiten]** **[!UICONTROL Hinzufügen Benutzer]**.

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **ID&amp;ast;**: Sirius
   * **E-Mail-Adresse**: sirius.nilson@mailinator.com
   * **Password&amp;ast;**: password
   * **Kennwort&amp;Bestätigen;**: password
   * **Vorname**: Sirius
   * **Nachname&amp;last;**: Nilson

### Sirius der Community-Administratorgruppe {#assign-sirius-to-community-administrators-group} zuweisen

Blättern Sie nach unten zu `Add User to Groups`:

* &quot;C&quot;für die Suche eingeben

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus

![admin-role](assets/admin-role.png)

