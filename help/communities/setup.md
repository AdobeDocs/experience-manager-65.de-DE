---
title: Ersteinrichtung
seo-title: Ersteinrichtung
description: Communities einrichten
seo-description: Communities einrichten
uuid: c53d280c-c5ae-47cf-8038-f0dea68e15ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 0d462ad1-5619-4bb6-9609-bc8987c40a0c
translation-type: tm+mt
source-git-commit: 6d425dcec4fab19243be9acb41c25b531a84ea74

---


# Ersteinrichtung {#initial-setup}

## Start Author and Publish Instances {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoreninstanz und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden Anweisungen [für die ersten Schritte](../../help/sites-deploying/deploy.md#getting-started) in AEM. Dies führt zu Folgendem:

* Autorendatei auf [localhost:4502](http://localhost:4502/)
* Umgebung auf [localhost veröffentlichen: 4503](http://localhost:4503/)

Für AEM Communities

* Die Umgebung des Verfassers dient:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Verwaltungs- und Konfigurationseinstellungen.

* Die Umgebung zur Veröffentlichung ist für folgende Zwecke gedacht:

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten.
   * Erstellen von Community-Gruppen, Mitgliedern und Mitgliedsgruppen.

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).


## Neueste Communities-Version installieren {#install-latest-communities-release}

Dieses Lernprogramm erstellt eine [Community-Site](overview.md#engagement-community) für Interaktionen und basiert auf AEM Communities 6.2 Feature Pack Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Übung, die eine [Community-Site](overview.md#enablement-community)für die Aktivierung erstellt, finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md)konfiguriert ist, stehen Informationen zur Community-Aktivität zur Verfügung, die die Benutzererfahrung verbessern und Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der `Communities Sites` Konsole erstellt wurden, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert sein.

See [Configuring Email](email.md).

## Tunneldienst aktivieren {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autor-Umgebung ermöglicht der Tunneldienst die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern, die in der Veröffentlichungs-Umgebung registriert sind. Der Tunneldienst ermöglicht auch den Zugang zu Community-Mitgliedern der [Mitglieder- und Gruppenkonsolen](members.md) in der Autorendatei.

Die Konvention ist dafür gedacht, dass in der Umgebung zum Veröffentlichen erstellte Mitglieder und Mitgliedsgruppen in der Umgebung zum Autor *nicht* neu erstellt werden. For more information see [Managing Users and User Groups](users.md).

Eine einfache Anleitung zum Aktivieren des Tunneldienstes auf einer **Autoreninstanz** finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratorgruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (Mitglieder können aus der Community ausgeschlossen werden) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer beim *Autor*, dem die Rolle des Community-Administrators zugewiesen wurde:

* In der Autoreninstanz

   * For example, [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorberechtigungen

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **Bearbeiten **die Option**[!UICONTROL Hinzufügen Benutzer ]**

* Geben Sie im `Create New User` Dialogfeld Folgendes ein:

   * **[!UICONTROL ID]**: Sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Password&amp;amp bestätigen;ast;]**: password
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Sirius der Community-Administratorgruppe zuweisen {#assign-sirius-to-community-administrators-group}

Blättern Sie nach unten zu `Add User to Groups`:

* &quot;C&quot;für die Suche eingeben

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![chlimage_1-301](assets/chlimage_1-301.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demoversionen für die Anmeldung bei Facebook und Twitter verwendet werden können, müssen Sie

1. Installieren Sie ein Fix Pack oder ein [neuestes Feature Pack](deploy-communities.md#latestfeaturepack) (für Änderungen der Facebook-API vom März 2017).
1. [Aktivieren Sie den OAuth-Anbieter](social-login.md#adobe-granite-oauth-authentication-handler) in der Umgebung &quot;Veröffentlichen&quot;.

Bei Produktionsservern müssen die Cloud-Dienste erstellt werden, die für die Anmeldung in sozialen Netzwerken erforderlich sind.

Siehe [Social-Anmeldung bei Facebook und Twitter](social-login.md).

## Tutorial-Tags erstellen {#create-tutorial-tags}

Erstellen Sie Tags, die mithilfe des Tag-Namensraums von für die Interaktions- und Aktivierungsübungen verwendet werden `Tutorial`.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) , um die folgenden Tags zu erstellen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![chlimage_1-302](assets/chlimage_1-302.png)

Folgen Sie dann den Anweisungen:

1. [Legen Sie die Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions)fest.
1. [Veröffentlichen Sie die Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket mit Tags, die für die Erste Schritte-Tutorials in AEM Communities erstellt wurden

[Datei laden](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, jedoch optional, [MSRP](msrp.md) (MongoDB) als [gemeinsamen Speicher](working-with-srp.md) festzulegen, um die Flexibilität zu nutzen, alle UGC von Veröffentlichungs- und/oder Autor-Umgebung zu moderieren.

Anweisungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Autor- und Veröffentlichungsinstanzen dazu, dass benutzerdefinierte Inhalte (UGC) in der [JCR Tar-Datenspeicherung](../../help/sites-deploying/platform.md) gespeichert werden, auf die mit [JSRP](jsrp.md)zugegriffen wird. JSRP ist kein allgemeiner Speicher, d. h., UGC ist nur auf der Instanz sichtbar, auf der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autoreninstanz sichtbar, sodass alle Moderations-Aufgaben die Veröffentlichungsinstanz verwenden müssen.