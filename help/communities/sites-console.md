---
title: Communities-Sites-Konsole
seo-title: Communities Sites Console
description: How to access the Communities Sites console
seo-description: How to access the Communities Sites console
uuid: 74134281-244c-40da-a941-7f2f3e706d4b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4130f952-5bb5-4e32-91d6-47b2885b30a4
docset: aem65
translation-type: tm+mt
source-git-commit: e49acbc042d84ae970058b4e99ab6f980866db5a
workflow-type: tm+mt
source-wordcount: '3292'
ht-degree: 4%

---


# Communities Sites Console {#communities-sites-console}

The Communities Sites console provides access to:

* Site creation
* Site editing
* Site management
* [Creating and editing nested groups](/help/communities/groups.md) (sub-communities)

See [Getting Started with AEM Communities](/help/communities/getting-started.md) to experience how quickly a community site can be created in the author environment, as well as how to create community groups from the author and publish environments.

>[!NOTE]
>
>The main Communities menus for the creation of [community sites](/help/communities/sites-console.md), [community site templates](/help/communities/sites.md), [community group templates](/help/communities/tools-groups.md) and [community functions](/help/communities/functions.md) are for use only in the author environment.


## Voraussetzungen {#prerequisites}

Before creating a community site, it is *required* to:

* Ensure one or more publish instances are running.
* Aktivieren Sie den [Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) , um Mitglieder und Mitgliedsgruppen zu verwalten.
* Identifizieren Sie den [primären Herausgeber](/help/communities/deploy-communities.md#primary-publisher).
* [Konfigurieren Sie die Replikation](/help/communities/deploy-communities.md#replication-agents-on-author) , wenn der primäre Herausgeberanschluss nicht der Standard ist (4503).

Um sicherzustellen, dass die Site viele Funktionen unterstützt, sollten Sie folgende Schritte durchführen:

* Installieren Sie das [neueste Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack).
* Aktivieren Sie [Adobe Analytics](/help/communities/analytics.md) für AEM Communities.
* Konfigurieren von [E-Mail](/help/communities/email.md)
* Identifizieren Sie [Community-Administratoren](/help/communities/users.md#creating-community-members).
* [Aktivieren Sie den OAuth-Handler](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) für die Anmeldung in sozialen Netzwerken.

## Zugriff auf die Sites-Konsole von Communities {#accessing-communities-sites-console}

In der Umgebung &quot;Autor&quot;zur Konsole &quot;Communities Sites&quot;gelangen Sie wie folgt:

* Aus globaler Navigation: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**

Die Communities Sites-Konsole zeigt alle vorhandenen Community-Sites an. In dieser Konsole können Community-Sites erstellt, bearbeitet, verwaltet und gelöscht werden.

To create a new community site, select the **Create** icon.

Um auf eine bestehende Community-Site zuzugreifen, um eine verschachtelte Gruppe zu erstellen, zu bearbeiten, zu veröffentlichen, zu exportieren oder hinzuzufügen, wählen Sie das Ordnersymbol der Site aus.

Die folgende Abbildung zeigt beispielsweise die Haupt-Konsole Communities Sites , in der die Ordner für zwei Community-Sites angezeigt werden: [aktivieren](/help/communities/getting-started-enablement.md) und [aktivieren](/help/communities/getting-started.md):

![site-console](assets/site-console.png)

## Site-Erstellung {#site-creation}

Die Site-Erstellungskonsole bietet einen schrittweisen Ansatz, um Funktionen der Site basierend auf einer ausgewählten [Community-Site-Vorlage](/help/communities/sites.md) und -Einstellungen zusammenzustellen.

Jede erstellte Site verfügt über eine Anmeldefunktion, da Site-Besucher sich anmelden müssen, bevor sie Inhalte posten, Nachrichten senden oder an einer Gruppe teilnehmen können. Zu den weiteren Funktionen gehören Profil, Nachrichten, Benachrichtigungen, Site-Menü, Suche, Design und Branding.

Der Prozess wird gestartet, indem Sie die `Create` Schaltfläche oben in der Communities Sites-Konsole auswählen.

Der Erstellungsprozess besteht aus einer Reihe von Schritten, die als Bedienfelder mit einer Reihe von zu konfigurierenden Funktionen (die als Unterbereiche dargestellt werden) dargestellt werden. Es ist möglich, zum **nächsten** Schritt oder zum vorherigen Schritt **Zurück** vorzugehen, bevor Sie die Site im letzten Schritt verpflichten.

### Schritt 1: Site-Vorlage {#step-site-template}

![newsitetemplate](assets/newsitetemplate.png)

Im Bedienfeld &quot;Site-Vorlage&quot;werden Titel, Beschreibung, Site-Stammordner, Basissprache, Name und Site-Vorlage angegeben:

* **Community-Site-Titel**

   Ein Anzeigentitel für die Site.

   Der Titel wird sowohl auf der veröffentlichten Site als auch in der Benutzeroberfläche des Site-Administrators angezeigt.

* **Community-Site-Beschreibung**

   Eine Beschreibung der Site.

   Die Beschreibung wird nicht auf der veröffentlichten Site angezeigt.

* **Community-Site-Stammordner**

   Der Stammpfad zur Site.

   Der Standard-Stammordner ist `/content/sites`festgelegt, der Stammordner kann jedoch an einen beliebigen Speicherort auf der Website verschoben werden.

* **Grundsprache der Community-Site**

   (Für eine Sprache unberührt lassen: Englisch) Verwenden Sie das Pulldown-Menü, um eine *oder mehrere* Basissprachen aus den verfügbaren Sprachen (Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht) auszuwählen. Eine Community-Site wird für jede hinzugefügte Sprache erstellt und befindet sich im selben Site-Ordner, wie unter [Übersetzung von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md)beschrieben. Die Stammseite jeder Site enthält eine untergeordnete Seite, die nach dem Sprachcode einer der ausgewählten Sprachen benannt ist, wie z.B. &quot;en&quot; für Englisch oder &quot;fr&quot; für Französisch.

* **Community-Site-Name**:

   Der Name der Stammseite der Site, die in der URL angezeigt wird.

   * Überprüfen Sie den Dublette-Namen, da er nach dem Erstellen der Site nicht leicht geändert werden kann.
   * Die Basis-URL ( `https://server:port/site root/site name)` wird unterhalb des `Community Site Name`.

   * Für eine gültige URL hängen Sie einen Basissprachcode an + &quot;.html&quot;

      *Beispiel*, `https://localhost:4502/content/sites/mysight/en.html`

* **Menü &quot;Community-Site-Vorlage** &quot;

   Verwenden Sie das Pulldown-Menü, um eine verfügbare [Community-Site-Vorlage](/help/communities/tools.md)auszuwählen.

* Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

The Design panel contains 2 sub-panels for selecing the theme and branding banner:

#### COMMUNITY SITE THEME {#community-site-theme}

![sitetheme](assets/sitetheme.png)

Das Framework verwendet [Twitter-Bootstrap](https://twitterbootstrap.org/) , um ein reaktionsfähiges, flexibles Design auf die Site zu bringen. One of the many preloaded Bootstrap themes may be selected to style the selected community site template, or a Bootstrap theme may be uploaded.

When selected, the theme will be overlayed with an opaque blue checkmark.

After the community site is published, it is possible to [edit the properties](#modifying-site-properties) and select a different theme.

#### COMMUNITY SITE BRANDING {#community-site-branding}

![site-branding](assets/site-branding.png)

Community site branding is an image displayed as a header across the top of each page.

The image should be sized to be as wide as the expected display of the page in the browser and 120 pixels in height.

When creating or selecting an image, keep in mind:

* The image height will be cropped to 120 pixels measured from the top edge of the image.
* The image is pinned to the left edge of the browser window.
* There is no resizing of the image, such that when the image width is...

   * Less than the browser&#39;s width, the image will repeat horizontally.
   * Greater than the browser&#39;s width, the image will appear to be cropped.

* Wählen Sie **Weiter** aus.

### Step 3 : Settings {#step-settings}

Das Einstellungsbedienfeld enthält mehrere Unterbereiche mit Funktionen, die konfiguriert werden müssen, bevor Sie zum letzten Schritt zur Erstellung der Site wechseln.

* [USER MANAGEMENT](#user-management)
* [TAGGING](#tagging)
* [ROLLEN](#roles)
* [MODERATION](#moderation)
* [ANALYSEN](#analytics)
* [TRANSLATION](#translation)
* [AKTIVIERUNG](#enablement)

>[!NOTE]
>
>**Tunnel-Dienst aktivieren**
>
>Mehrere Unterbereiche unter &quot;Einstellungen&quot;ermöglichen es einem vertrauenswürdigen Mitglied, UGC zu moderieren, Gruppen zu verwalten oder Kontaktpersonen für die Aktivierung von Ressourcen in der Umgebung &quot;Veröffentlichen&quot;zu sein.
>
>Die Regel besteht darin, dass [Benutzer und Benutzergruppen](/help/communities/users.md) (Mitglieder und Mitgliedsgruppen) auf der Veröffentlichungsseite nicht in der Umgebung des Verfassers dupliziert werden dürfen.
>
>Daher ist es beim Erstellen der Community-Site in der Autorenrolle und beim Zuweisen von vertrauenswürdigen Mitgliedern zu verschiedenen Rollen erforderlich, Mitgliedsdaten aus der Veröffentlichungs-Umgebung abzurufen.
>
>Dies wird erreicht, indem Sie die ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)` für die Autorenversion Umgebung aktivieren.


#### USER MANAGEMENT {#user-management}

![createsitesettings](assets/createsitesettings.png)

>[!NOTE]
>
>Es wird empfohlen, dass [Community-Sites](/help/communities/overview.md#enablement-community) privat genutzt werden (weitere Informationen erhalten Sie von Ihrem Kundenbetreuer).
>
>Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich nicht selbst registrieren können und sie möglicherweise keine Social-Anmeldung verwenden.


* **Benutzerregistrierung zulassen**

   Wenn diese Option aktiviert ist, können Site-Besucher durch Selbstregistrierung Community-Mitglieder werden.
Wenn diese Option deaktiviert ist, ist die Community-Site *eingeschränkt* und die Site-Besucher müssen der Mitgliedergruppe der Community-Site zugewiesen werden, eine Anforderung stellen oder per E-Mail eine Einladung erhalten. Wenn diese Option deaktiviert ist, sollte der anonyme Zugriff nicht erlaubt sein.
Deaktivieren Sie die Option für eine *private* Community-Site. Diese Option ist standardmäßig aktiviert.

* **Anonymen Zugriff erlauben**

   Wenn aktiviert, ist die Community-Site *open *und jeder Site-Besucher kann auf die Site zugreifen.
Wenn diese Option deaktiviert ist, können nur angemeldete Mitglieder auf die Site zugreifen.
Deaktivieren Sie die Option für eine *private *Community-Site. Diese Option ist standardmäßig aktiviert.

* **Messaging zulassen**

   Wenn diese Option aktiviert ist, können Mitglieder Nachrichten an einander und an die Gruppe innerhalb der Community-Site senden.
Wenn diese Option deaktiviert ist, wird Messaging für die Community nicht eingerichtet.
Diese Option ist standardmäßig deaktiviert.

* **Anmeldung über soziale Medien erlauben: Facebook**

   Wenn diese Option aktiviert ist, erlauben Sie Site-Besuchern, sich mit ihren Facebook-Kontoangaben anzumelden. Die ausgewählte [Facebook-Cloud-Konfiguration](/help/communities/social-login.md#create-a-facebook-connect-cloud-service) sollte so konfiguriert werden, dass Benutzer zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.
Wenn diese Option deaktiviert ist, wird keine Facebook-Anmeldung angezeigt.
Lassen Sie das Kontrollkästchen für eine *private* Community-Site deaktiviert. Diese Option ist standardmäßig deaktiviert.

* **Anmeldung über soziale Medien erlauben: Twitter**

   Wenn diese Option aktiviert ist, erlauben Sie Site-Besuchern, sich mit ihren Twitter-Kontoangaben anzumelden. Die ausgewählte [Twitter-Cloud-Konfiguration](/help/communities/social-login.md#create-a-twitter-connect-cloud-service) sollte so konfiguriert werden, dass Benutzer zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.
Wenn diese Option deaktiviert ist, wird keine Twitter-Anmeldung angezeigt.
Lassen Sie das Kontrollkästchen für eine *private* Community-Site deaktiviert. Diese Option ist standardmäßig deaktiviert.

>[!NOTE]
>
>**Zulassen von Social-Anmeldungen**
>
>Während Beispielkonfigurationen für Facebook und Twitter existieren und auswählbar sind, müssen für eine [Produktions-Umgebung](/help/sites-administering/production-ready.md)benutzerdefinierte Facebook- und Twitter-Anwendungen erstellt werden. Siehe [Social-Anmeldung bei Facebook und Twitter](/help/communities/social-login.md).


#### TAGGING {#tagging}

![Site-Tagging](assets/site-tagging.png)

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch Auswahl von Tag-Namensräumen gesteuert, die zuvor über die [Tagging-Konsole](/help/sites-administering/tags.md#tagging-console)definiert wurden.

Darüber hinaus wird bei der Auswahl von Tag-Namensräumen für die Community-Site die Auswahl beim Definieren von Katalogen und Ressourcen eingeschränkt. Wichtige Informationen finden Sie unter [Tagging-Aktivierungsressourcen](/help/communities/tag-resources.md) .

* Textfeld: Eingabe von Beginn zur Identifizierung von Tags, die auf der Site verwendet werden dürfen.

#### ROLES {#roles}

![Community-Rollen](assets/site-admin-2.png)

Die [Rollen von Community-Mitgliedern](/help/communities/users.md) werden mit diesen Einstellungen zugewiesen.

Die Suche nach Community-Mitgliedern ist mit der Type-Ahead-Suche einfach.

* **Community-Manager**

   Beginn eingeben, um ein oder mehrere Community-Mitglieder oder Mitgliedsgruppen auszuwählen, die Community-Mitglieder und -Mitgliedsgruppen verwalten können.

* **Community-Moderatoren**

   Beginn eingeben, um ein oder mehrere Community-Mitglieder oder Mitgliedsgruppen auszuwählen, denen als Moderatoren von benutzergenerierten Inhalten vertraut werden soll.

* **Privilegierte Community-Mitglieder**

   Beginn eingeben, um ein oder mehrere Community-Mitglieder oder -Mitgliedsgruppen auszuwählen, damit neue Inhalte erstellt werden können, wenn `Allow Privileged Member` diese für eine [Community-Funktion](/help/communities/functions.md)ausgewählt wurden.

* **Community-Administratoren**

   Beginn eingeben, um einen oder mehrere Site-Administratoren auszuwählen, die die Sitestruktur unabhängig von anderen Site-Administratoren und dem standardmäßigen Community-Administrator verwalten können. Sie können Gruppen auf jeder Ebene der Hierarchie erstellen und zum Standardadministrator der verschachtelten Gruppen werden (sie können später jedoch aus der Administratorrolle verschachtelter Gruppen entfernt werden).

#### MODERATION {#moderation}

![site-moderation](assets/site-moderation.png)

Die globale Einstellung für die Moderation benutzergenerierter Inhalte (UGC) wird durch diese Einstellungen gesteuert. Individual components have additional settings to control moderation.

* **Inhalt ist vormoderiert**

   If checked, posted community content will not appear until approved by a moderator. Diese Option ist standardmäßig deaktiviert. For more information, see [Moderating Community Content](/help/communities/moderate-ugc.md#premoderation).

* **Kennzeichnung des Schwellenwerts, bevor der Inhalt ausgeblendet wird**

   Wenn der Wert größer als 0 ist, muss ein Thema oder Beitrag vor der öffentlichen Ansicht markiert werden. If set to -1, the flagged topic or post is never hidden from public view. Der Standardwert ist 5.

#### ANALYTICS {#analytics}

![site-analytics](assets/site-analytics.png)

* **Analytics aktivieren**

   Only available when Adobe Analytics has been [configured](/help/communities/analytics.md) for Communities features.
Diese Option ist standardmäßig deaktiviert. When checked, an additional selection menu appears:

![site-analytics-enable](assets/site-analytics-enable.png)

* **Framework-Verweis der Cloud-Konfiguration**

   From the pull-down menu, select the Analytics cloud service framework configured for this community site.
   `Communities` is the framework example from [Analytics Configuration for Communities Features](/help/communities/analytics.md#aem-analytics-framework-configuration) documentation.

#### TRANSLATION {#translation}

![site-translation](assets/site-translation.png)

* **Maschinelle Übersetzung zulassen**

   When checked (default is unchecked), machine translation is enabled for UGC within the site. This does not affect any other content, such as page content, even if the site is setup as a multilingual site. See [Translating User Generated Content](/help/communities/translate-ugc.md) for information on configuring a licensed translation service for AEM Communities. See [Translating Content for Multilingual Sites](/help/sites-administering/translation.md) for a complete overview.

![allow-machine-translation](assets/allow-machine-translation.png)

* **Maschinelle Übersetzung für ausgewählte Sprachen aktivieren**

   The languages enabled for machine translation default to the system setting specified by the [translation integration configuration](/help/communities/translate-ugc.md#translation-integration-configuration). Diese Standardeinstellungen können für diese Site überschrieben werden, indem Standardwerte gelöscht und/oder andere Sprachen aus dem Pulldown-Menü ausgewählt werden.

* **Übersetzungsanbieter auswählen**

   By default, the service provider is a trial service using `microsoft` for demonstration only. Wenn kein Dienstleister für Übersetzung lizenziert ist, sollte die Option &quot;maschinelle Übersetzung **zulassen** &quot;deaktiviert werden.

* **Globalen geteilten Speicher auswählen**

   Für eine Website mit mehreren Sprachkopien bietet ein globaler gemeinsamer Store einen einzigen Konversationsthread, der von jeder Sprachkopie aus sichtbar ist. Dies wird erreicht, indem eine der Sprachen als Sprachkopie ausgewählt wird. Der Standardwert ist *kein globaler freigegebener Store*.

* **Übersetzungsanbieter-Konfiguration auswählen**

   Wählen Sie ein [Übersetzungs-Integrationsframework](/help/sites-administering/tc-tic.md) , das für den lizenzierten Übersetzungsanbieter erstellt wurde.

* **Wählen Sie die Übersetzungsoptionen für Ihre Community-Site**

   * **Gesamte Seite übersetzen**

      Wenn diese Option aktiviert ist, werden alle UGC auf einer Seite in die Basissprache der Seite übersetzt.

      &quot;Standard&quot;ist *nicht ausgewählt*.

   * **Nur Auswahl übersetzen**

      Wenn diese Option aktiviert ist, wird neben jedem Beitrag eine Übersetzungsoption angezeigt, mit der einzelne Beiträge in die Basissprache der Seite übersetzt werden können.
Default is *selected*.

* **Speicheroptionen auswählen**

   * **Übersetzen Sie Beiträge auf Benutzeranforderung und bleiben Sie anschließend** bestehen. Wenn diese Option aktiviert ist, werden die Inhalte erst übersetzt, wenn eine Anforderung gestellt wurde. Nach der Übersetzung wird die Übersetzung im Repository gespeichert.

      &quot;Standard&quot;ist *nicht ausgewählt*.

   * **Übersetzungen nicht behalten**

      Wenn diese Option aktiviert ist, werden Übersetzungen nicht im Repository gespeichert.

      Wenn diese Option nicht ausgewählt ist, bleiben die Übersetzungen erhalten.

      &quot;Standard&quot;ist *nicht ausgewählt*.

* **Smart Rendering**

   Wählen Sie eine der folgenden Optionen:

   * `Always show contributions in the original language` (default)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### ENABLEMENT {#enablement}

![Site-Aktivierung](assets/site-enablement.png)

Die `ENABLEMENT`Einstellungen gelten, wenn die ausgewählte Community-Site-Vorlage die [Zuweisungsfunktion](/help/communities/functions.md#assignments-function)enthält, die verfügbar ist, wenn die Aktivierungsfunktionen lizenziert und [konfiguriert](/help/communities/enablement.md)sind. The reference site template that includes the assignments function is `Reference Structured Learning Site Template.`

* **Enablement Managers**
(Required) Only members of the `Community Enablementmanagers` group are available to be selected to manage this enablement community. Enablement managers are responsible for assigning members to resources. See also [Managing Users and User Groups](/help/communities/users.md).

* **ID der Marketing Cloud-Organisation**

   (optional) The ID for a [Video Heartbeat Analytics](/help/communities/analytics.md#video-heartbeat-analytics) license.

* Wählen Sie **Weiter** aus.

### Step 4 : Create Communities Site {#step-create-communities-site}

If any adjustments are needed, use the **Back** button to make them.

Once **Create** is selected and started, the process of creating the site cannot be interrupted.

Once the site is created:

* Changing the url (node name) is not supported.
* Future changes to the community site template will not affect the created community site.
* Disabling the community site template will not affect the created community site.
* It is possible to edit the [STRUCTURE](#modify-structure) of a community site by modifying its properties.

![create-site](assets/create-site1.png)

When the process completes, the folder for the new site is displayed in the Communities Sites console, from where authors may add page content or administrators may modify the properties of the site.

![modify-site-property](assets/modify-site-property.png)

Um eine Community-Site zu ändern, wählen Sie ihren Projektordner aus, um ihn zu öffnen:

![site-project](assets/site-project.png)

Wenn Sie den Mauszeiger über eine Site bewegen oder eine Sitekarte berühren, werden Symbole angezeigt, mit denen Sie die Site im Autorenmodus [](#authoring-site-content)bearbeiten, [die Site-Eigenschaften zur Änderung](#modifying-site-properties)öffnen, die Site [](#publishing-the-site)veröffentlichen, die Site [](#exporting-the-site)exportieren und die Site [löschen](#deleting-the-site)können.

## Erstellen von Site-Inhalten {#authoring-site-content}

The content of a site may be authored with the same tools as any other AEM website. To open the site for authoring, select the `Open Site` icon that appears on hovering the site with mouse. The site will open in a new tab such that the Communities Sites console remains accessible.

![site-content](assets/site-content.png)

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](/help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](/help/sites-authoring/qg-page-authoring.md).


## Modifying Site Properties {#modifying-site-properties}

![edit-site](assets/edit-site.png)

The properties of an exisitng site, specified during the site creation process, can be modified by selecting the `Edit Site`icon that appears on hovering the site with mouse.

`Details of the following properties match the descriptions provided in the` [Site Creation](#site-creation) section.

![modify-site-basicinfo](assets/modify-site-basicinfo.png)

### Basic ändern {#modify-basic}

Das BASIC-Bedienfeld ermöglicht die Änderung von:

* Community-Site-Titel
* Community-Site-Beschreibung

The Community Site Name may not be modified.

Choosing a different community site template would have no affect on an existing community site as no connection remains between templates and sites.

Instead, the [STRUCTURE](#modify-structure) of the community site may be modified.

### Modify Structure {#modify-structure}

Das STRUKTURbedienfeld ermöglicht die Änderung der Struktur, die ursprünglich aus der ausgewählten Community-Site-Vorlage erstellt wurde. Über den Bereich können Sie:

* Drag-and-drop additional [community functions](/help/communities/functions.md) into the site structure.
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

      Bearbeiten Sie Einstellungen, einschließlich des Anzeigentitels und des URL-Namens* sowie [privilegierte Mitgliedergruppen](/help/communities/users.md#privilegedmembersgroups).

   * **`trashcan icon`**

      Remove (delete) functions from the site structure.

   * **`grid icon`**

      Ändern Sie die Reihenfolge der Funktionen, die in der Navigationsleiste auf der obersten Navigationsebene der Site angezeigt werden.

>[!NOTE]
>
>Sie können die Reihenfolge aller Funktionen in der Site-Struktur mit Ausnahme der Funktion oben ändern. Therefore, the home page of communities site cannot be changed.


>[!CAUTION]
>
>* While the display title may be changed without side-effects, it is not recommended to edit the URL name of a community function belonging to a community site.
>
>
Wenn Sie beispielsweise die URL umbenennen, wird die vorhandene UGC nicht verschoben, sodass die UGC verliert wird.


>[!CAUTION]
>
>The groups function must *not* be the *first nor the only* function in the site structure.
>
>Any other function, such as the [page function](/help/communities/functions.md#page-function), must be included and listed first.


#### Example : Adding a Catalog Function to a Community Site Structure {#example-adding-a-catalog-function-to-a-community-site-structure}

![add-catalog-site](assets/add-catalog-site.png)

### Modify Design {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Anwendung eines neuen Designs:

* [Community-Site-Thema](#community-site-theme)
* [Community-Site-Branding](#community-site-branding)

   * Scroll to the bottom of the panel to change the brand image.

### Modify Settings {#modify-settings}

The SETTINGS panel allows access to most of the settings under the sub-panels of for Step 3 of community site creation:

* [Benutzerverwaltung](#user-management)
* [Tags](#tagging)
* [Moderation](#moderation)
* [Mitgliederrollen](#roles)
* [Analyse](#analytics)
* [Übersetzung](#translation)

### Modify Thumbnail {#modify-thumbnail}

Im Bereich &quot;MINIATURANSICHT&quot;kann ein Bild hochgeladen werden, das die Site in der Konsole &quot;Communities Sites&quot;darstellt.

### Aktivierung ändern {#modify-enablement}

Das Fenster &quot;ENABLEMENT&quot;ermöglicht den Zugriff auf die Einstellungen, die während der Erstellung der Community-Site bereitgestellt werden.

See the [ENABLEMENT](#enablement) description.

## Veröffentlichen der Site {#publishing-the-site}

Nachdem eine Community-Site neu erstellt oder geändert wurde, ist es möglich, die Site zu veröffentlichen (zu aktivieren), indem Sie das Symbol auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen. `Publish Site`

![publish-site](assets/publish-site.png)

There will be an indication after site is successfully published.

![site-published](assets/site-published.png)

### Publishing with Nested Groups {#publishing-with-nested-groups}

After publishing a community site, it is necessary to individually publish each sub-community (nested group) created using the [Groups console](/help/communities/groups.md).

## Exporting the Site {#exporting-the-site}

![export-site](assets/export-site.png)

Select the export icon, on mouse hover over the site, to create a package of the community site that is both stored in [package manager](/help/sites-administering/package-manager.md) and downloaded.

Note that UGC is not included in the site package.

## Deleting the Site {#deleting-the-site}

![deleteicon](assets/deleteicon.png)

To delete the community site, select the Delete Site icon that appears on hovering the mouse over the site in Communities Site Console. This action removes all the items associated with the site, such as UGC, user groups, assets and database records.

## Created Community User Groups {#created-community-user-groups}

Once the new community site is published, new member groups (user groups are created in the publish environment) which have the appropriate permissions set for various administrative and member roles.

The name created for the member groups includes the *site-name* given the site in [Step 1](#step13asitetemplate) (the name which appears in the URL) as well as an unique ID to avoid conflicts with community sites and groups having the same site-name for different community site roots.

For example, if the name were &quot;engage&quot; for a site titled &quot;Getting Started Tutorial&quot;, then the user group for moderators would be :

* title: Community Engage Moderators
* name: community-*engage-uid*-moderators

Notice that any members assigned roles as moderators or group administrators while creating the site, will be assigned to the appropriate group as well as assigned to the members group. These groups and member assignments are created on publish when the new site is published.

For details, see [Managing Users and User Groups](/help/communities/users.md).

>[!NOTE]
>
>If [Allow Social Login: Facebook](#user-management) is enabled, once the user group
>
>* `community-<site-name>-<uid>-members`
>
>
is created, the applied [Facebook cloud service](/help/communities/social-login.md#createafacebookcloudservice) should be configured to add users to this group.


## Configure for Authentication Error {#configure-for-authentication-error}

By default, a community site will redirect to a sample login page when the user enters the wrong credentials and fails to login. This sample login will not be present on a [production server](/help/sites-administering/production-ready.md).

To correctly redirect, once a site has been configured and pushed to publish, complete these steps to get authentication failure to redirect to the community site:

* Auf jeder AEM Instanz im Veröffentlichungsmodus.
* Sign in with administrator privileges.
* Access the [Web Console](/help/sites-deploying/configuring-osgi.md).

   * For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

* Locate `Adobe Granite Login Selector Authentication Handler`.
* Select the `pencil` icon to open the configuration for edit.
* Enter a **Login Page Mappings** as follows:

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   Beispiel:
   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Wählen Sie **Speichern** aus.

![auth-error](assets/auth-error.png)

### Test Authentication Redirection {#test-authentication-redirection}

On the same AEM publish instance configured with a login page mapping for the community site:

* Browse to the community site home page.

   * For example, [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Select Log Out.
* Select Log In.
* Enter obviously incorrect credentials, such as username &quot;x&quot; and password &quot;x&quot;.
* Die Anmeldeseite sollte mit der Fehlermeldung &quot;Ungültige Anmeldung&quot;angezeigt werden.

![test-authentication](assets/test-authentication.png)

## Accessing Community Sites from Main Sites Console {#accessing-community-sites-from-main-sites-console}

From the global navigation Sites console, community sites are located in the `Community Sites` folder.

While it is possible to access a community site in this manner, for administrative tasks, the community site should be accessed from the Communities Sites console.

![access-site](assets/access-site.png)



