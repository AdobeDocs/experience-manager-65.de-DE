---
title: Ersteinrichtung für Aktivierung
seo-title: Initial Setup
description: Ersteinrichtung für Aktivierung
seo-description: Initial Setup for Enablement
uuid: 873ec41d-c088-41d9-a535-de5300661de6
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: f2ac3d66-cc79-498f-83fb-dd96feb88de2
exl-id: ed494922-3e15-4778-84c1-35c8846ce980
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 3%

---

# Ersteinrichtung für Aktivierung  {#initial-setup-for-enablement}

## Starten von Autoren- und Veröffentlichungsinstanzen {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Grundlegende AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started) Anweisungen, die zu

* Autorenumgebung in [localhost:4502](http://localhost:4502/)
* Veröffentlichungsumgebung in [localhost:4503](http://localhost:4503/)

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
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md) und [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

In diesem Tutorial wird eine [Community-Site für Aktivierung](overview.md#enablement-community). Um sicherzustellen, dass das neueste Feature Pack installiert ist, gehen Sie zu:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Für ein Tutorial, das eine [Interaktionswebsite](overview.md#engagement-community), Besuch [Erste Schritte mit AEM Communities](getting-started.md).

## Aktivierungsfunktionen konfigurieren {#configure-enablement-features}

Um diesem Tutorial zu folgen, ist es erforderlich, ordnungsgemäß zu installieren und [Aktivierung konfigurieren](enablement.md), für die Drittanbieterprodukte wie MySQL und FFmpeg erforderlich sind.

## Konfigurieren Sie Analytics {#configure-analytics}

Wann [Adobe Analytics ist für die Community-Site konfiguriert.](analytics.md), weitere Informationen finden Sie im Abschnitt [Berichte](reports.md) generiert anhand von Aktivierungsressourcen und Lernpfaden, die Community-Mitgliedern (Lernenden) zugewiesen wurden.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mithilfe der `Communities Sites` bietet einen E-Mail-Kanal für Benachrichtigungen.

E-Mail muss für die Site ordnungsgemäß konfiguriert werden.

Siehe [E-Mail konfigurieren](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Erstellung und Verwaltung von in der Veröffentlichungsumgebung registrierten Benutzern und Benutzergruppen (Mitglieder), die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern und die Zuweisung von Inhalten zu Lernenden.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Einfache Anweisungen zum Aktivieren des Tunneldienstes finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Erstellen von Tutorial-Tags {#create-tutorial-tags}

Erstellen Sie Tags, die für die Tutorials zur Interaktion und Aktivierung verwendet werden sollen, mithilfe des Tag-Namespace von `Tutorial`.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) um die folgenden Tags zu erstellen:

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

[Datei herunterladen](assets/communities_tutorialtags-10.zip)

## Erstellen von Aktivierungsmitgliedern und -gruppen {#create-enablement-members-and-groups}

Bei einer Community-Site für die Aktivierung sollte es Site-Besuchern nicht möglich sein, [sich selbst registrieren und keine Anmeldung über soziale Netzwerke verwenden](sites-console.md#user-management).

Stattdessen wird mit dem [Tunneldienst](#enable-the-tunnel-service) aktiviert, wird die [Mitgliederkonsole](members.md) wird verwendet, um neue Mitglieder in der Veröffentlichungsumgebung zu registrieren.

In diesem Tutorial werden drei Mitglieder in der Veröffentlichungsumgebung erstellt. Zwei Mitglieder werden Mitglieder einer Benutzergruppe, die einem Lernpfad zugewiesen ist, während das dritte Mitglied ein Kontakt für Aktivierungsressourcen wird.

Ein vierter Benutzer wird in der Autorenumgebung erstellt und die Rollen &quot;Communities-Administrator&quot;und &quot;Community-Aktivierungsmanager&quot;zugewiesen.

>[!NOTE]
>
>Diese Mitglieder werden vor der Erstellung der *Tutorial zur Aktivierung* Community-Site.
>
>Wenn sie danach erstellt wurden, können sie als Mitglieder der *Gruppe von Aktivierungs-Tutorial-Mitgliedern* während der Mitgliedererstellung.
>
>Stattdessen werden sie später [der Mitgliedergruppe zugewiesen wurde](enablement-create-site.md#assignuserstocommunityenablemembersgroup).

### Riley Taylor - Enrollee {#riley-taylor-enrollee}

[Mitglied erstellen](members.md#create-new-member) die zu einer Gruppe von Lernenden hinzugefügt werden - der Community Ski Class Gruppe.

* **ID**: Riley
* **Email**: riley.taylor@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Riley
* **Nachname**: Taylor

### Sidney Croft - Enrollee {#sidney-croft-enrollee}

[Zweites Mitglied erstellen](members.md#create-new-member) die der Gruppe Community Ski Class hinzugefügt werden.

* **ID**: sidney
* **Email**: sidney.croft@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Sidney
* **Nachname**: Zuschneiden

### Quinn Harper - Kontakt für Aktivierungsressourcen und Moderator {#quinn-harper-enablement-resource-contact-and-moderator}

[Mitglied erstellen](members.md#create-new-member) die zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Site erstellt wurde. Diese Mitgliedschaft ermöglicht die Zuweisung des Mitglieds zur Aktivierung [Ressourcenkontakt](resources.md#settings) wenn eine Aktivierungsressource für die Site erstellt wird.

* **ID**: Quinn
* **Email**: quinn.harper@mailinator.com
* **Kennwort:** password
* **Kennwort bestätigen**: password
* **Vorname**: Quinn
* **Nachname**: Harper

### Hinzufügen einer Benutzergruppe - Community-Ski-Klasse {#add-a-user-group-community-ski-class}

[Neue Gruppe hinzufügen](members.md#create-new-group) der Community Ski Class.

* **ID**: community-ski-class
* **Name**: Community-Ski-Klasse
* **Beschreibung**: Beispielgruppe für die Zuweisung von Aktivierungsressourcen
* **Mitglieder zu Gruppe hinzufügen** &quot;add&quot;:

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

Benutzer erstellen in *author*, dem die Rolle &quot;Community-Administrator&quot;zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Aus dem **[!UICONTROL Bearbeiten]** Menü auswählen **[!UICONTROL Benutzer hinzufügen]**.

* Im `Create New User` dialog enter:

   * **ID&amp;ast;**: sirius
   * **E-Mail-Adresse**: sirius.nilson@mailinator.com
   * **Password&amp;ast;**: password
   * **Password&amp;ast bestätigen;**: password
   * **Vorname**: Sirius
   * **Nachname&amp;ast;**: Nilson

### Zuweisen von Sirius zur Community-Administratorengruppe {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Geben Sie &quot;C&quot;zur Suche ein.

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus

![admin-role](assets/admin-role.png)
