---
title: Ersteinrichtung
seo-title: Ersteinrichtung
description: Einrichten von Communities
seo-description: Einrichten von Communities
uuid: c53d280c-c5ae-47cf-8038-f0dea68e15ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 0d462ad1-5619-4bb6-9609-bc8987c40a0c
exl-id: 6bda0f09-7ae5-4540-b035-9dd249ac3186
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 3%

---

# Ersteinrichtung {#initial-setup}

## Starten Sie Autoren- und Veröffentlichungsinstanzen {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden AEM [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), was zu folgenden Ergebnissen führt:

* Autorenumgebung auf [localhost:4502](http://localhost:4502/)
* Veröffentlichungsumgebung auf [localhost:4503](http://localhost:4503/)

Für AEM Communities:

* Die Autorenumgebung dient folgenden Zwecken:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Verwaltung und Konfiguration

* Die Veröffentlichungsumgebung dient folgenden Zwecken:

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten.
   * Erstellung von Community-Gruppen, Mitgliedern und Mitgliedergruppen.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](../../help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

Dieses Tutorial erstellt eine [Community-Seite für Interaktionen](overview.md#engagement-community) und basiert auf AEM Communities 6.2 Feature Pack-Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, gehen Sie zu:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Anleitung zum Erstellen einer [Aktivierungs-Community-Site](overview.md#enablement-community) finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md) konfiguriert ist, stehen Informationen zur Community-Aktivität zur Verfügung, die das Erlebnis der Community-Mitglieder verbessern und den Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle mit der `Communities Sites`-Konsole erstellten Sites verfügbar ist, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert werden.

Siehe [Konfigurieren von E-Mail](email.md).

## Aktivieren Sie den Tunnel-Dienst {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Zuweisung von Rollen an vertrauenswürdige Community-Mitglieder, die in der Veröffentlichungsumgebung registriert sind. Der Tunneldienst ermöglicht auch den Zugriff auf Community-Mitglieder über die [Mitglieder und Gruppen-Konsolen](members.md) in der Autorenumgebung.

Die Konvention richtet sich an Mitglieder und Mitgliedergruppen, die in der Veröffentlichungsumgebung in *not* erstellt wurden, in der Autorenumgebung neu erstellt werden. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Einfache Anweisungen zum Aktivieren des Tunneldienstes auf einer **author**-Instanz finden Sie unter [Tunnel Service](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratoren-Gruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer für *author*, dem die Rolle &quot;Community-Administrator&quot;zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im Menü **Bearbeiten** **[!UICONTROL Benutzer hinzufügen]** aus.

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Password&amp;ast bestätigen;]**: password
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Zuweisen von Sirius zur Community-Administrator-Gruppe {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Geben Sie &quot;C&quot;zur Suche ein.

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![create-user](assets/create-user.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demonstrationsversionen für die Anmeldung in sozialen Netzwerken mit Facebook und Twitter verwendet werden können, müssen Sie

1. Installieren Sie ein Fixpack oder das [neueste Feature Pack](deploy-communities.md#latestfeaturepack) (für Facebook-API-Änderungen vom März 2017).
1. [Aktivieren Sie den OAuth-](social-login.md#adobe-granite-oauth-authentication-handler) Anbieter in der Veröffentlichungsumgebung.

Für Produktionsserver ist es erforderlich, die Cloud-Services zu erstellen, die für die Anmeldung über soziale Netzwerke erforderlich sind.

Siehe [Anmeldung in sozialen Netzwerken mit Facebook und Twitter](social-login.md).

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

1. [Legen Sie die Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions) fest.
1. [Veröffentlichen Sie die Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket mit Tags, die für die Tutorials für die ersten Schritte mit AEM Communities erstellt wurden

[Datei laden](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, ist jedoch optional, [MSRP](msrp.md) (MongoDB) als [Common Store](working-with-srp.md) festzulegen, um die Flexibilität zu erleben, die beim Moderieren aller benutzergenerierten Inhalte aus Veröffentlichungs- und/oder Autorenumgebungen entsteht.

Anweisungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Autoren- und Veröffentlichungsinstanzen dazu, dass benutzergenerierte Inhalte (UGC) in [JCR Tar Storage](../../help/sites-deploying/platform.md) gespeichert werden, auf den über [JSRP](jsrp.md) zugegriffen wird. JSRP ist kein allgemeiner Speicher, d. h. UGC ist nur in der Instanz sichtbar, in der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autorenumgebung sichtbar, sodass alle Moderationsaufgaben die Veröffentlichungsinstanz verwenden müssen.
