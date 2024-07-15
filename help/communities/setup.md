---
title: Ersteinrichtung
description: Erfahren Sie, wie Sie Adobe Experience Manager Communities zum ersten Mal einrichten.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
exl-id: 6bda0f09-7ae5-4540-b035-9dd249ac3186
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 2%

---

# Ersteinrichtung {#initial-setup}

## Starten von Autoren- und Publish-Instanzen {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden Anweisungen für Adobe Experience Manager (AEM) [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), die zu Folgendem führen:

* Autorenumgebung auf [localhost:4502](http://localhost:4502/)
* Publish-Umgebung auf [localhost:4503](http://localhost:4503/)

Für AEM Communities:

* Die Autorenumgebung dient folgenden Zwecken:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Verwaltung und Konfiguration

* Die Publish-Umgebung dient folgenden Zwecken:

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten.
   * Erstellung von Community-Gruppen, Mitgliedern und Mitgliedergruppen.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](../../help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zum Erstellen von Seiten](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

Dieses Tutorial erstellt eine [Community-Site für Interaktionen](overview.md#engagement-community) und basiert auf AEM Communities 6.2 Feature Pack-Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, gehen Sie zu:

* [Neueste Versionen](deploy-communities.md#latest-releases)

## Analytics konfig. {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site konfiguriert ist](analytics.md), stehen Informationen zur Community-Aktivität zur Verfügung, die das Erlebnis des Community-Mitglieds verbessern und Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle mit der Konsole `Communities Sites` erstellten Sites verfügbar ist, stellt einen E-Mail-Kanal für Benachrichtigungen bereit.

E-Mail muss für die Site ordnungsgemäß konfiguriert werden.

Siehe [Konfigurieren von E-Mail](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Zuweisung von Rollen an vertrauenswürdige Community-Mitglieder, die in der Publish-Umgebung registriert sind. Der Tunneldienst ermöglicht auch den Zugriff auf Community-Mitglieder aus den [Mitgliedern und Gruppen-Konsolen](members.md) in der Autorenumgebung.

Die Konvention ist für Mitglieder und Mitgliedergruppen bestimmt, die in der Publish-Umgebung erstellt wurden, um *nicht* in der Autorenumgebung neu zu erstellen. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Einfache Anweisungen zum Aktivieren des Tunneldienstes in einer **Autoreninstanz** finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratoren-Gruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer für *author*, dem die Rolle &quot;Community-Administrator&quot;zugewiesen wurde:

* Auf der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu &quot;**[!UICONTROL Tools]**&quot;> &quot;**[!UICONTROL Vorgänge]**&quot;> &quot;**[!UICONTROL Sicherheit]**&quot;> &quot;**[!UICONTROL Benutzer]**&quot;.
* Wählen Sie im Menü **Bearbeiten** die Option **[!UICONTROL Benutzer hinzufügen]**

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Kennwort bestätigen&amp;ast;]**: Kennwort
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Zuweisen von Sirius zur Community-Administratorengruppe {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Geben Sie &quot;C&quot;zur Suche ein.

   * Klicken Sie auf `Community Administrators`
   * Klicken Sie auf `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![create-user](assets/create-user.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demonstrationsversionen für die Anmeldung in sozialen Netzwerken mit Facebook und Twitter verwendet werden können, ist es erforderlich,

1. Installieren Sie ein Fixpack oder das [neueste Feature Pack](deploy-communities.md#latestfeaturepack) (für Facebook-API-Änderungen vom März 2017).
1. [Aktivieren Sie den OAuth-Provider](social-login.md#adobe-granite-oauth-authentication-handler) in der Veröffentlichungsumgebung.

Für Produktionsserver ist es erforderlich, die Cloud-Services zu erstellen, die für die Anmeldung über soziale Netzwerke erforderlich sind.

Siehe [Anmeldung in sozialen Netzwerken mit Facebook und Twitter](social-login.md).

## Erstellen von Tutorial-Tags {#create-tutorial-tags}

Erstellen Sie Tags, damit Sie sie für die Tutorials zum Interagieren verwenden können, indem Sie den Tag-Namespace von `Tutorial` verwenden.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) , um die folgenden Tags zu erstellen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![tutorial-tags](assets/tutorial-tags.png)

Folgen Sie dann den Anweisungen, um:

1. [Legen Sie die Tag-Berechtigungen fest](../../help/sites-administering/tags.md#setting-tag-permissions).
1. [Publish der Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket mit Tags, die für die Tutorials für die ersten Schritte mit AEM Communities erstellt wurden

[Datei abrufen](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, ist jedoch optional, [MSRP](msrp.md) (MongoDB) als [gemeinsamen Speicher](working-with-srp.md) festzulegen, um die Flexibilität zu erleben, alle benutzergenerierten Inhalte entweder in der Veröffentlichungs- und/oder der Autorenumgebung zu moderieren.

Anweisungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Autoren- und Veröffentlichungsinstanzen dazu, dass benutzergenerierte Inhalte (UGC) im [JCR Tar Storage](../../help/sites-deploying/platform.md) gespeichert werden, auf den mit [JSRP](jsrp.md) zugegriffen wird. JSRP ist kein allgemeiner Speicher, d. h. UGC ist nur in der Instanz sichtbar, in der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autorenumgebung sichtbar, sodass alle Moderationsaufgaben die Veröffentlichungsinstanz verwenden müssen.
