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
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Ersteinrichtung {#initial-setup}

## Start Author and Publish Instances {#start-author-and-publish-instances}

Für Entwicklungs- und Demonstrationszwecke ist es erforderlich, eine Autoreninstanz und eine Veröffentlichungsinstanz auszuführen.

Befolgen Sie dazu die grundlegenden Anweisungen [für](../../help/sites-deploying/deploy.md#getting-started) die ersten Schritte mit AEM, die in

* Autorenumgebung auf [localhost:4502](http://localhost:4502/)
* Veröffentlichungsumgebung auf [localhost: 4503](http://localhost:4503/)

Für AEM Communities

* Die Autorenumgebung ist für

   * Entwicklung von Sites, Vorlagen und Komponenten
   * Verwaltungs- und Konfigurationsaufgaben

* Die Veröffentlichungsumgebung ist

   * Die Community-Erfahrung beim Posten und Moderieren von Inhalten
   * Erstellen von Community-Gruppen, Mitgliedern und Mitgliedsgruppen

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).

## Neueste Communities-Version installieren {#install-latest-communities-release}

Dieses Lernprogramm erstellt eine [Community-Site](overview.md#engagement-community) für Interaktionen und basiert auf AEM Communities 6.2 Feature Pack Version 1.10.

Um sicherzustellen, dass das neueste Feature Pack installiert ist, besuchen Sie:

* [Neueste Versionen](deploy-communities.md#latest-releases)

Eine Übung, die eine [Community-Site](overview.md#enablement-community)für die Aktivierung erstellt, finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](getting-started-enablement.md).

## Konfigurieren Sie Analytics {#configure-analytics}

Wenn [Adobe Analytics für die Community-Site](analytics.md)konfiguriert ist, stehen Informationen zu Community-Aktivitäten zur Verfügung, die die Benutzererfahrung verbessern und Administratoren der Site Feedback geben.

Die Integration mit Adobe Analytics ist optional.

## E-Mail für Benachrichtigungen konfigurieren {#configure-email-for-notifications}

Die Benachrichtigungsfunktion, die standardmäßig für alle Sites verfügbar ist, die mit der `Communities Sites` Konsole erstellt wurden, bietet einen E-Mail-Kanal für Benachrichtigungen.

E-Mail muss für die Site ordnungsgemäß konfiguriert sein.

See [Configuring Email](email.md).

## Tunneldienst aktivieren {#enable-the-tunnel-service}

Beim Erstellen einer Community-Site in der Autorenumgebung ermöglicht der Tunneldienst die Zuweisung von Rollen zu vertrauenswürdigen Community-Mitgliedern, die in der Veröffentlichungsumgebung registriert sind. Der Tunneldienst erlaubt auch den Zugriff auf Community-Mitglieder von den [Mitgliedern und Gruppen-Konsolen](members.md) in der Autorenumgebung.

Die Konvention gilt, dass in der Veröffentlichungsumgebung erstellte Mitglieder und Mitgliedsgruppen in der Autorenumgebung *nicht* neu erstellt werden. For more information see [Managing Users and User Groups](users.md).

Eine einfache Anleitung zum Aktivieren des Tunneldienstes auf einer **Autoreninstanz** finden Sie unter [Tunneldienst](deploy-communities.md#tunnel-service-on-author).

## Community-Administratorrolle {#community-administrator-role}

Mitglieder der Community-Administratorgruppe können Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (Mitglieder können aus der Community ausgeschlossen werden) und Inhalte moderieren.

### Benutzer erstellen {#create-user}

Erstellen Sie einen Benutzer beim *Autor*, dem die Rolle des Community-Administrators zugewiesen wurde:

* In der Autoreninstanz

   * For example, [http://localhost:4502/](http://localhost:4503/)

* Anmelden mit Administratorrechten

   * Beispiel: Benutzername &quot;admin&quot;/ Kennwort &quot;admin&quot;

* Navigieren Sie in der Hauptkonsole zu **[!UICONTROL Tools > Vorgänge > Sicherheit > Benutzer]**
* Wählen Sie im Menü **Bearbeiten **die Option Benutzer**[!UICONTROL hinzufügen ]**

* Geben Sie im `Create New User` Dialogfeld

   * **[!UICONTROL ID&amp;ast;]**: Sirius
   * **[!UICONTROL E-Mail-Adresse]**: sirius.nilson@mailinator.com
   * **[!UICONTROL Password&amp;ast;]**:password
   * **[!UICONTROL Password&amp;amp bestätigen;ast;]**:password
   * **[!UICONTROL Vorname]**: Sirius
   * **[!UICONTROL Nachname&amp;last;]**: Nilson

### Sirius der Community-Administratorgruppe zuweisen {#assign-sirius-to-community-administrators-group}

Blättern Sie nach unten zu `Add User to Groups`:

* &quot;C&quot;für die Suche eingeben

   * Wählen Sie nun eine der folgenden Optionen aus `Community Administrators`
   * Wählen Sie nun eine der folgenden Optionen aus `Community Enablement Managers`

* Wählen Sie **[!UICONTROL Speichern]**

![chlimage_1-301](assets/chlimage_1-301.png)

## Social-Anmeldung aktivieren {#enable-social-login}

Bevor die Demoversionen für die Anmeldung bei Facebook und Twitter verwendet werden können, müssen Sie

1. Fixpack oder [neuestes Feature Pack](deploy-communities.md#latestfeaturepack) installieren (für Änderungen der Facebook-API vom März 2017)
1. [OAuth-Anbieter](social-login.md#adobe-granite-oauth-authentication-handler) in der Veröffentlichungsumgebung aktivieren

Bei Produktionsservern müssen die Cloud-Dienste erstellt werden, die für die Anmeldung in sozialen Netzwerken erforderlich sind.

Siehe [Social-Anmeldung bei Facebook und Twitter](social-login.md).

## Tutorial-Tags erstellen {#create-tutorial-tags}

Erstellen Sie Tags, die für die Interaktions- und Aktivierungsübungen mit dem Tag-Namespace von verwendet werden `Tutorial`.

Verwenden Sie die [Tagging-Konsole](../../help/sites-administering/tags.md#tagging-console) , um die folgenden Tags zu erstellen:

* `Tutorial: Sports / Baseball`
* `Tutorial: Sports / Gymnastics`
* `Tutorial: Sports / Skiing`
* `Tutorial: Arts / Visual`
* `Tutorial: Arts / Auditory`
* `Tutorial: Arts / History`

![chlimage_1-302](assets/chlimage_1-302.png)

Folgen Sie dann den Anweisungen zum

1. [Festlegen der Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions)
1. [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)

Beispielpaket mit Tags, die für die Erste Schritte-Tutorials in AEM Communities erstellt wurden

[Datei laden](assets/tutorial_tags-v63.zip)

## MongoDB für UGC Common Store {#mongodb-for-ugc-common-store}

Es wird empfohlen, jedoch optional, [MSRP](msrp.md) (MongoDB) als [gemeinsamen Speicher](working-with-srp.md) festzulegen, um die Flexibilität bei der Moderation aller UGC in Veröffentlichungs- und/oder Autorenumgebungen zu nutzen.

Anweisungen finden Sie unter [Einrichten von MongoDB für Demo](demo-mongo.md).

Standardmäßig führt die Installation der Autor- und Veröffentlichungsinstanzen dazu, dass benutzerdefinierte Inhalte (UGC) im [JCR-Speicher](../../help/sites-deploying/platform.md) gespeichert werden, auf den mit [JSRP](jsrp.md)zugegriffen wird. JSRP ist kein allgemeiner Speicher, d. h., UGC ist nur auf der Instanz sichtbar, auf der es eingegeben wurde. Normalerweise wird UGC in einer Veröffentlichungsinstanz eingegeben und ist nicht in der Autorenumgebung sichtbar, sodass alle Moderationsaufgaben die Veröffentlichungsinstanz verwenden müssen.