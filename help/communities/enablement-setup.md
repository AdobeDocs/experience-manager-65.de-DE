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
exl-id: ed494922-3e15-4778-84c1-35c8846ce980
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---

# Ersteinrichtung für Aktivierung {#initial-setup-for-enablement}

## Starten Sie Autoren- und Veröffentlichungsinstanzen {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie die grundlegenden AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), die zu

* Autorenumgebung auf [localhost:4502](http://localhost:4502/)
* Veröffentlichungsumgebung auf [localhost:4503](http://localhost:4503/)

Für AEM Communities:

* Die Autorenumgebung dient folgenden Zwecken:

   * Entwicklung von Sites, Vorlagen, Komponenten, Aktivierungsressourcen und Lernpfaden.
   * Zuweisung von Mitgliedern und Gruppen von Mitgliedern zur Aktivierung von Ressourcen und Lernpfaden.
   * Erstellen von Berichten zu Zuweisungen, Ansichten und Beiträgen.
   * Verwaltung und Konfiguration

* Die Veröffentlichungsumgebung dient folgenden Zwecken:

   * Lernen/Training basierend auf Themen, die vom Aktivierungs-Manager verwaltet werden.
   * Kommentieren und Bewerten von Aktivierungsressourcen und Lernpfaden.
   * Kontakt mit den Kontakten der Ressource aufnehmen.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](../../help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

In diesem Tutorial wird eine [Aktivierungs-Community-Site](overview.md#enablement-community) erstellt. Um sicherzustellen, dass das neueste Feature Pack installiert ist, gehen Sie zu:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Anleitung zum Erstellen einer [Community-Seite für Interaktionen](overview.md#engagement-community) finden Sie unter [Erste Schritte mit AEM Communities](getting-started.md).

## Aktivierungsfunktionen konfigurieren {#configure-enablement-features}

Um diesem Tutorial zu folgen, müssen Sie die Aktivierung [konfigurieren](enablement.md) ordnungsgemäß installieren und konfigurieren. Dazu sind Drittanbieterprodukte wie MySQL und FFmpeg erforderlich.

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md) konfiguriert ist, sind weitere Informationen in den [Berichten](reports.md) verfügbar, die für Aktivierungsressourcen und Lernpfade generiert wurden, die Community-Mitgliedern (Lernenden) zugewiesen wurden.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle mit der `Communities Sites`-Konsole erstellten Sites verfügbar ist, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert werden.

Siehe [Konfigurieren von E-Mail](email.md).

## Aktivieren Sie den Tunnel-Dienst {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Erstellung und Verwaltung von in der Veröffentlichungsumgebung registrierten Benutzern und Benutzergruppen (Mitglieder), die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern und die Zuweisung von Inhalten zu Lernenden.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Einfache Anweisungen zum Aktivieren des Tunneldienstes finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Erstellen von Tutorial-Tags {#create-tutorial-tags}

Erstellen Sie Tags, die für die Tutorials zur Interaktion und Aktivierung verwendet werden sollen, mithilfe des Tag-Namespace von `Tutorial`.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console), um die folgenden Tags zu erstellen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![tutorial-tags](assets/tutorial-tags.png)

Folgen Sie dann den Anweisungen, um:

1. [Festlegen der Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions)
1. [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)

Beispielpaket mit Tags, die für die Tutorials für die ersten Schritte mit AEM Communities erstellt wurden

[Datei laden](assets/communities_tutorialtags-10.zip)

## Erstellen von Aktivierungsmitgliedern und -gruppen {#create-enablement-members-and-groups}

Für eine Community-Site für die Aktivierung sollten Site-Besucher nicht in der Lage sein, [sich selbst zu registrieren oder soziale Anmeldungen](sites-console.md#user-management) zu verwenden.

Stattdessen wird bei aktiviertem [Tunneldienst](#enable-the-tunnel-service) die [Mitglieder-Konsole](members.md) verwendet, um neue Mitglieder in der Veröffentlichungsumgebung zu registrieren.

In diesem Tutorial werden drei Mitglieder in der Veröffentlichungsumgebung erstellt. Zwei Mitglieder werden zu Mitgliedern einer Benutzergruppe, die einem Lernpfad zugewiesen ist, während das dritte Mitglied ein Kontakt mit einer Aktivierungsressource wird.

Ein vierter Benutzer wird in der Autorenumgebung erstellt und die Rollen &quot;Communities-Administrator&quot;und &quot;Community-Aktivierungsmanager&quot;zugewiesen.

>[!NOTE]
>
>Diese Mitglieder werden vor der Erstellung der Community-Site *Aktivierungs-Tutorial* erstellt.
>
>Wenn sie danach erstellt wurden, könnten sie bei der Mitgliedererstellung als Mitglieder der Gruppe *Aktivierungstutorial-Mitglieder* hinzugefügt werden.
>
>Stattdessen werden sie später [der Mitgliedergruppe](enablement-create-site.md#assignuserstocommunityenablemembersgroup) zugewiesen.

### Riley Taylor - Enrollee {#riley-taylor-enrollee}

[Erstellen Sie ein ](members.md#create-new-member) Mitglied, das zu einer Gruppe von Lernenden hinzugefügt wird - der Community Ski Class Gruppe.

* **ID**: Riley
* **E-Mail**: riley.taylor@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Riley
* **Nachname**: Taylor

### Sidney Croft - Enrollee {#sidney-croft-enrollee}

[Erstellen Sie ein zweites ](members.md#create-new-member) Mitglied, das der Gruppe Community Ski Class hinzugefügt wird.

* **ID**: sidney
* **E-Mail**: sidney.croft@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Sidney
* **Nachname**: Zuschneiden

### Quinn Harper - Kontakt für Aktivierungsressourcen und Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Erstellen Sie ein ](members.md#create-new-member) Mitglied, das zur Mitgliedergruppe der Community-Site hinzugefügt wird, sobald die Site erstellt wurde. Durch diese Mitgliedschaft kann das Mitglied als Aktivierungsressource [Resource Contact](resources.md#settings) zugewiesen werden, wenn eine Aktivierungsressource für die Site erstellt wird.

* **ID**: Quinn
* **E-Mail**: quinn.harper@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Quinn
* **Nachname**: Harper

### Benutzergruppe hinzufügen - Community-Ski-Klasse {#add-a-user-group-community-ski-class}

[Fügen Sie eine neue ](members.md#create-new-group) Gruppe mit dem Namen Community Ski Class hinzu.

* **ID**: community-ski-class
* **Name**: Community-Ski-Klasse
* **Beschreibung**: Beispielgruppe für die Zuweisung von Aktivierungsressourcen
* **Mitglieder zur Gruppe hinzufügen** &#39;add&#39;:

   * Riley
   * sidney

* Wählen Sie **[!UICONTROL Speichern]** aus

### Eigenschaften der Community-Ski-Klasse {#community-ski-class-properties}

![ski-class-properties](assets/ski-class-properties.png)

>[!NOTE]
>
>Während der Erstellung der Community-Site können bestehende Mitglieder und Gruppen zur Mitgliedergruppe der Community-Site hinzugefügt werden.

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratoren-Gruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer für *author*, dem die Rolle &quot;Community-Administrator&quot;zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **[!UICONTROL Bearbeiten]** **[!UICONTROL Benutzer hinzufügen]** aus.

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **ID&amp;ast;**: sirius
   * **E-Mail-Adresse**: sirius.nilson@mailinator.com
   * **Password&amp;ast;**: password
   * **Password&amp;ast bestätigen;**: password
   * **Vorname**: Sirius
   * **Nachname&amp;ast;**: Nilson

### Zuweisen von Sirius zur Community-Administrator-Gruppe {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Geben Sie &quot;C&quot;zur Suche ein.

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus

![admin-role](assets/admin-role.png)
