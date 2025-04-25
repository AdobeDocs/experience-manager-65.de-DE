---
title: Ersteinrichtung
description: Erfahren Sie, wie Sie Adobe Experience Manager Communities anfänglich einrichten.
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

## Starten von Authoring- und Publish-Instanzen {#start-author-and-publish-instances}

Zu Entwicklungs- und Demonstrationszwecken ist es erforderlich, eine Autoren- und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden Anweisungen in Adobe Experience Manager (AEM) [Erste Schritte](../../help/sites-deploying/deploy.md#getting-started), die Folgendes bewirken:

* Autorenumgebung auf [localhost:4502](http://localhost:4502/)
* Publish-Umgebung auf [localhost:4503](http://localhost:4503/)

Für AEM Communities

* Die Autorenumgebung ist für Folgendes vorgesehen:

   * Entwicklung von Sites, Vorlagen und Komponenten.
   * Administrations- und Konfigurationsaufgaben.

* Die Publish-Umgebung ist für Folgendes vorgesehen:

   * Die Community-Erfahrung mit dem Posten und Moderieren von Inhalten.
   * Erstellen von Community-Gruppen, Mitgliedern und Mitgliedergruppen.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [Grundlegende Handhabung](../../help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zur Seitenbearbeitung](../../help/sites-authoring/qg-page-authoring.md).

## Installieren der neuesten Communities-Version {#install-latest-communities-release}

In diesem Tutorial wird eine [Interaktions-Community](overview.md#engagement-community)Site erstellt, die auf AEM Communities 6.2 Feature Pack 1.10 basiert.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Aktuelle Versionen](deploy-communities.md#latest-releases)

## Analytics konfig. {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site konfiguriert ist](analytics.md) sind Informationen über Community-Aktivitäten verfügbar, die das Erlebnis der Community-Mitglieder verbessern und den Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## Konfigurieren von E-Mails für Benachrichtigungen {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der `Communities Sites`-Konsole erstellt wurden, bietet einen E-Mail-Kanal für Benachrichtigungen.

E-Mails müssen jedoch ordnungsgemäß für die Website konfiguriert sein.

Siehe [Konfigurieren von E-](email.md).

## Aktivieren des Tunneldienstes {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern, die in der Publish-Umgebung registriert sind. Der Tunnel-Service ermöglicht auch den Zugriff auf Community-Mitglieder über die Konsolen [Mitglieder und Gruppen](members.md) in der Autorenumgebung.

Die Konvention sieht vor, dass Mitglieder und Mitgliedsgruppen, die in der Publish-Umgebung erstellt wurden *in* Autorenumgebung nicht neu erstellt werden. Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](users.md).

Einfache Anweisungen zum Aktivieren des Tunneldienstes auf einer **Author**-Instanz finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratorgruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbannen) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer in *author*, dem die Rolle Community-Administrator zugewiesen ist:

* In der Autoreninstanz

   * Beispiel: [http://localhost:4502/](http://localhost:4503/)

* Mit Administratorrechten anmelden

   * Beispiel: Benutzername &#39;admin&#39; / Kennwort &#39;admin&#39;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
* Wählen Sie im **Bearbeiten** die Option **[!UICONTROL Benutzer hinzufügen]**

* Geben Sie im Dialogfeld `Create New User` Folgendes ein:

   * **[!UICONTROL ID]**: sirius
   * **[!UICONTROL E-Mail-]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Kennwort:]** password
   * **[!UICONTROL Kennwort bestätigen&ast;]**: Kennwort
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname]**: Nilson

### Sirius der Gruppe der Community-Administratoren zuweisen {#assign-sirius-to-community-administrators-group}

Scrollen Sie nach unten zu `Add User to Groups`:

* Zum Suchen „C“ eingeben

   * Klicken Sie auf `Community Administrators`
   * Klicken Sie auf `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]** aus.

![create-user](assets/create-user.png)

## Social-Media-Anmeldung aktivieren {#enable-social-login}

Bevor die Demoversionen der Social-Media-Anmeldung mit Facebook und Twitter verwendet werden können, müssen Sie Folgendes tun

1. Installieren Sie ein Fix Pack oder [neueste Feature Pack](deploy-communities.md#latestfeaturepack) (für Änderungen an der Facebook-API im März 2017).
1. [Aktivieren des OAuth](social-login.md#adobe-granite-oauth-authentication-handler)Anbieters in der Veröffentlichungsumgebung.

Für Produktions-Server ist es erforderlich, die Cloud-Services zu erstellen, die für die Bereitstellung der Social-Media-Anmeldung erforderlich sind.

Siehe [Social-Anmeldung mit Facebook und Twitter](social-login.md).

## Tutorial-Tags erstellen {#create-tutorial-tags}

Erstellen Sie Tags, damit Sie sie für die Engage-Tutorials verwenden können, indem Sie den Tag-Namespace von `Tutorial` verwenden.

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
1. [Publish die Tags](../../help/sites-administering/tags.md#publishing-tags).

Beispielpaket von Tags, die für die Tutorials „Erste Schritte“ in AEM Communities erstellt wurden

[Datei abrufen](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, jedoch optional, [MSRP](msrp.md) (MongoDB) als [Common Store](working-with-srp.md) festzulegen, um die Flexibilität der Moderation aller UGC in Veröffentlichungs- und/oder Autorenumgebungen zu nutzen.

Anweisungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Authoring- und Publishing-AEM-Instanzen dazu, dass benutzergenerierte Inhalte (User Generated Content, UGC) im [JCR-Tar-Speicher) gespeichert ](../../help/sites-deploying/platform.md), auf den über [JSRP](jsrp.md) zugegriffen wird. JSRP ist kein gewöhnlicher Speicher, was bedeutet, dass UGC nur in der Instanz sichtbar ist, in der sie eingegeben wurde. Normalerweise wird der benutzergenerierte Inhalt (UGC) in einer Veröffentlichungsinstanz eingegeben und wäre in der Autorenumgebung nicht sichtbar, was dazu führt, dass alle Moderationsaufgaben die Veröffentlichungsinstanz verwenden müssen.
