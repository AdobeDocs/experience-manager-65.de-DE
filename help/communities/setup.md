---
title: Ersteinrichtung
seo-title: Initial Setup
description: Einrichten von Communities
seo-description: Setting up Communities
uuid: c53d280c-c5ae-47cf-8038-f0dea68e15ff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 0d462ad1-5619-4bb6-9609-bc8987c40a0c
exl-id: 6bda0f09-7ae5-4540-b035-9dd249ac3186
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 3%

---

# Ersteinrichtung {#initial-setup}

## Starten von Autoren- und Veröffentlichungsinstanzen {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Gehen Sie dazu wie folgt AEM vor [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started) Anweisungen, die zu Folgendem führen:

* Autorenumgebung in [localhost:4502](http://localhost:4502/)
* Veröffentlichungsumgebung in [localhost:4503](http://localhost:4503/)

Für AEM Communities:

* Die Autorenumgebung dient folgenden Zwecken:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Verwaltung und Konfiguration

* Die Veröffentlichungsumgebung dient folgenden Zwecken:

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten.
   * Erstellung von Community-Gruppen, Mitgliedern und Mitgliedergruppen.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](../../help/sites-authoring/basic-handling.md) und [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

In diesem Tutorial wird eine [Interaktionswebsite](overview.md#engagement-community) und basiert auf AEM Communities 6.2 Feature Pack Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, gehen Sie zu:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Für ein Tutorial, das eine [Community-Site für Aktivierung](overview.md#enablement-community), Besuch [Erste Schritte mit AEM Communities zur Aktivierung](getting-started-enablement.md).

## Konfigurieren Sie Analytics {#configure-analytics}

Wann [Adobe Analytics ist für die Community-Site konfiguriert.](analytics.md), stehen Informationen zur Community-Aktivität zur Verfügung, die die Erlebnisse der Community-Mitglieder verbessern und den Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mithilfe der `Communities Sites` bietet einen E-Mail-Kanal für Benachrichtigungen.

E-Mail muss für die Site ordnungsgemäß konfiguriert werden.

Siehe [E-Mail konfigurieren](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Zuweisung von Rollen an vertrauenswürdige Community-Mitglieder, die in der Veröffentlichungsumgebung registriert sind. Der Tunneldienst ermöglicht auch den Zugang zu Community-Mitgliedern von der [Mitglieder und Gruppenkonsolen](members.md) in der Autorenumgebung.

Die Konvention richtet sich an Mitglieder und Mitgliedergruppen, die in der Veröffentlichungsumgebung in erstellt wurden. *not* in der Autorenumgebung neu erstellt werden. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Für einfache Anweisungen zum Aktivieren des Tunneldienstes auf einem **author** -Instanz, siehe [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratoren-Gruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Benutzer erstellen in *author*, dem die Rolle &quot;Community-Administrator&quot;zugewiesen wurde:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Instrumente]** > **[!UICONTROL Aktivitäten]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Aus dem **Bearbeiten** Menü auswählen **[!UICONTROL Benutzer hinzufügen]**

* Im `Create New User` dialog enter:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Password&amp;ast bestätigen;]**: password
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Zuweisen von Sirius zur Community-Administratorengruppe {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Geben Sie &quot;C&quot;zur Suche ein.

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![create-user](assets/create-user.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demonstrationsversionen für die Anmeldung in sozialen Netzwerken mit Facebook und Twitter verwendet werden können, müssen Sie

1. Installieren Sie ein Fixpack oder [neueste Feature Pack](deploy-communities.md#latestfeaturepack) (für März 2017 Facebook-API-Änderungen).
1. [OAuth-Provider aktivieren](social-login.md#adobe-granite-oauth-authentication-handler) in der Veröffentlichungsumgebung.

Für Produktionsserver ist es erforderlich, die Cloud-Services zu erstellen, die für die Anmeldung über soziale Netzwerke erforderlich sind.

Siehe [Anmeldung über Social Media mit Facebook und Twitter](social-login.md).

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

1. [Festlegen der Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions).
1. [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket mit Tags, die für die Tutorials für die ersten Schritte mit AEM Communities erstellt wurden

[Datei herunterladen](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, jedoch optional [MSRP](msrp.md) (MongoDB) als [gemeinsamer Speicher](working-with-srp.md) , um die Flexibilität zu erleben, alle benutzergenerierten Inhalte entweder in der Veröffentlichungs- und/oder der Autorenumgebung zu moderieren.

Anleitungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Autoren- und Veröffentlichungsinstanzen dazu, dass benutzergenerierte Inhalte (UGC) in gespeichert werden. [JCR-Tar-Speicher](../../help/sites-deploying/platform.md) , auf die über [JSRP](jsrp.md). JSRP ist kein allgemeiner Speicher, d. h. UGC ist nur in der Instanz sichtbar, in der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autorenumgebung sichtbar, sodass alle Moderationsaufgaben die Veröffentlichungsinstanz verwenden müssen.
