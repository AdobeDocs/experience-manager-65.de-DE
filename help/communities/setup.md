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
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 3%

---


# Initial-Setup {#initial-setup}

## Autoreninstanzen und Veröffentlichungsinstanzen für Beginn {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoreninstanz und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden Anweisungen AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), die Folgendes ergeben:

* Autorendatei auf [localhost:4502](http://localhost:4502/)
* Umgebung für Veröffentlichung auf [localhost:4503](http://localhost:4503/)

AEM Communities:

* Die Umgebung des Verfassers dient:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Verwaltungs- und Konfigurationseinstellungen.

* Die Umgebung zur Veröffentlichung ist für folgende Zwecke gedacht:

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten.
   * Erstellen von Community-Gruppen, Mitgliedern und Mitgliedsgruppen.

>[!NOTE]
>
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [basic handling](../../help/sites-authoring/basic-handling.md) und [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version {#install-latest-communities-release} installieren

Dieses Lernprogramm erstellt eine [Community-Site für Interaktionen](overview.md#engagement-community) und basiert auf dem AEM Communities 6.2 Feature Pack Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Übung, die eine [Community-Site für die Aktivierung](overview.md#enablement-community) erstellt, finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md) konfiguriert ist, stehen Informationen zur Community-Aktivität zur Verfügung, die das Erlebnis des Community-Mitglieds verbessern und Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der Konsole `Communities Sites` erstellt wurden, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert sein.

Siehe [E-Mail konfigurieren](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autor-Umgebung ermöglicht der Tunneldienst die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern, die in der Veröffentlichungs-Umgebung registriert sind. Der Tunneldienst erlaubt auch den Zugriff auf Community-Mitglieder über die [Mitglieder- und Gruppenkonsolen](members.md) in der Autorenversion-Umgebung.

Die Konvention gilt für Mitglieder und Mitgliedsgruppen, die in der Umgebung zum Veröffentlichen auf *nicht* erstellt wurden, in der Autorenversion neu erstellt werden. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Eine einfache Anleitung zum Aktivieren des Tunneldienstes auf einer **author**-Instanz finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratorgruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (Mitglieder können aus der Community ausgeschlossen werden) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer unter *author*, dem die Rolle des Community-Administrators zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorberechtigungen

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **Bearbeiten** **[!UICONTROL Hinzufügen Benutzer]**

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **[!UICONTROL ID]**: Sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Kennwort&amp;Bestätigen;]**: password
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Sirius der Community-Administratorgruppe {#assign-sirius-to-community-administrators-group} zuweisen

Blättern Sie nach unten zu `Add User to Groups`:

* &quot;C&quot;für die Suche eingeben

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![create-user](assets/create-user.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demoversionen für die Anmeldung bei Facebook und Twitter verwendet werden können, müssen Sie

1. Installieren Sie ein Fixpack oder [das neueste Feature Pack](deploy-communities.md#latestfeaturepack) (für Änderungen an der Facebook-API vom März 2017).
1. [Aktivieren Sie den OAuth-](social-login.md#adobe-granite-oauth-authentication-handler) Anbieter in der Umgebung &quot;Veröffentlichen&quot;.

Bei Produktionsservern müssen die Cloud-Dienste erstellt werden, die für die Anmeldung in sozialen Netzwerken erforderlich sind.

Siehe [Social-Anmeldung bei Facebook und Twitter](social-login.md).

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

1. [Legen Sie die Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions) fest.
1. [Veröffentlichen Sie die Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket mit Tags, die für die Tutorials Erste Schritte mit AEM Communities erstellt wurden

[Datei laden](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, jedoch optional, [MSRP](msrp.md) (MongoDB) als [Common Store](working-with-srp.md) festzulegen, um die Flexibilität zu erleben, alle UGC-Daten entweder aus der Umgebung &quot;Veröffentlichen&quot;oder &quot;Autor&quot;zu moderieren.

Anweisungen finden Sie unter [Wie Sie MongoDB für Demo](demo-mongo.md) einrichten.

Standardmäßig führt die Installation der Instanz im Autorenmodus und der Instanz im Veröffentlichungsmodus dazu, dass benutzerdefinierte Inhalte (UGC) in der Datenspeicherung [JCR Tar](../../help/sites-deploying/platform.md) gespeichert werden, auf die mit [JSRP](jsrp.md) zugegriffen wird. JSRP ist kein allgemeiner Speicher, d. h., UGC ist nur auf der Instanz sichtbar, auf der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autoreninstanz sichtbar, sodass alle Moderations-Aufgaben die Veröffentlichungsinstanz verwenden müssen.