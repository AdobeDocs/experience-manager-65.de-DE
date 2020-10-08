---
title: Communities-Sites-Konsole
seo-title: Communities-Sites-Konsole
description: Zugriff auf die Konsole "Communities Sites"
seo-description: Zugriff auf die Konsole "Communities Sites"
uuid: 74134281-244c-40da-a941-7f2f3e706d4b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 4130f952-5bb5-4e32-91d6-47b2885b30a4
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '3292'
ht-degree: 4%

---


# Communities-Sites-Konsole {#communities-sites-console}

Die Communities Sites-Konsole bietet Zugriff auf:

* Site-Erstellung
* Site-Bearbeitung
* Site-Management
* [Erstellen und Bearbeiten verschachtelter Gruppen](/help/communities/groups.md) (Untergruppen)

Unter [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) erfahren Sie, wie schnell eine Community-Site in der Authoring-Umgebung erstellt werden kann und wie Sie Community-Gruppen aus den Umgebung zum Erstellen und Veröffentlichen erstellen.

>[!NOTE]
>
>Die Hauptmenüs Communities für die Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-Vorlagen](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur für die Verwendung in der Autoren-Umgebung vorgesehen.

## Voraussetzungen {#prerequisites}

Bevor Sie eine Community-Site erstellen, müssen Sie Folgendes *tun* :

* Vergewissern Sie sich, dass eine oder mehrere Instanzen im Veröffentlichungsmodus ausgeführt werden.
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

Das Bedienfeld &quot;Design&quot;enthält 2 Unterbereiche zum Auswählen des Designs und des Branding-Banners:

#### COMMUNITY SITE THEME {#community-site-theme}

![sitetheme](assets/sitetheme.png)

Das Framework verwendet [Twitter-Bootstrap](https://twitterbootstrap.org/) , um ein reaktionsfähiges, flexibles Design auf die Site zu bringen. Es kann eines der vielen vorab geladenen Bootstrap-Themen ausgewählt werden, um die ausgewählte Community-Site-Vorlage zu gestalten, oder es kann ein Bootstrap-Design hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem undurchsichtigen blauen Häkchen überlagert.

Nachdem die Community-Site veröffentlicht wurde, können Sie die Eigenschaften [](#modifying-site-properties) bearbeiten und ein anderes Design auswählen.

#### COMMUNITY SITE BRANDING {#community-site-branding}

![Site-Branding](assets/site-branding.png)

Das Branding einer Community-Site ist ein Bild, das als Kopfzeile am oberen Rand jeder Seite angezeigt wird.

Das Bild sollte so groß sein, dass es im Browser wie erwartet angezeigt wird, und 120 Pixel hoch.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird auf 120 Pixel abgeschnitten, gemessen vom oberen Bildrand.
* Das Bild wird am linken Rand des Browserfensters fixiert.
* Die Bildgröße wird nicht geändert, d. h., wenn die Bildbreite ...

   * Wenn die Breite des Browsers geringer ist, wird das Bild horizontal wiederholt.
   * Größer als die Breite des Browsers, scheint das Bild beschnitten zu sein.

* Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Das Einstellungsbedienfeld enthält mehrere Unterbereiche mit Funktionen, die konfiguriert werden müssen, bevor Sie zum letzten Schritt zur Erstellung der Site wechseln.

* [BENUTZERVERWALTUNG](#user-management)
* [TAG](#tagging)
* [ROLLEN](#roles)
* [MODERATION](#moderation)
* [ANALYSEN](#analytics)
* [ÜBERSETZUNG](#translation)
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
Wenn diese Option deaktiviert ist, ist die Community-Site *eingeschränkt* und die Site-Besucher müssen der Mitgliedergruppe der Community-Site zugewiesen werden, eine Anfrage stellen oder per E-Mail eine Einladung erhalten. Wenn diese Option deaktiviert ist, sollte der anonyme Zugriff nicht erlaubt sein.
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

Die globale Einstellung für die Moderation benutzergenerierter Inhalte (UGC) wird durch diese Einstellungen gesteuert. Die einzelnen Komponenten verfügen über zusätzliche Einstellungen zur Steuerung der Moderation.

* **Inhalt ist vormoderiert**

   Wenn diese Option aktiviert ist, werden gepostete Community-Inhalte erst angezeigt, nachdem sie von einem Moderator genehmigt wurden. Diese Option ist standardmäßig deaktiviert. For more information, see [Moderating Community Content](/help/communities/moderate-ugc.md#premoderation).

* **Kennzeichnung des Schwellenwerts, bevor der Inhalt ausgeblendet wird**

   Wenn der Wert größer als 0 ist, muss ein Thema oder Beitrag vor der öffentlichen Ansicht markiert werden. Bei einem Wert von -1 wird das gekennzeichnete Thema oder der Beitrag nie aus der öffentlichen Ansicht ausgeblendet. Der Standardwert ist 5.

#### ANALYTICS {#analytics}

![site-analytics](assets/site-analytics.png)

* **Analytics aktivieren**

   Nur verfügbar, wenn Adobe Analytics für Communities-Funktionen [konfiguriert](/help/communities/analytics.md) wurde.
Diese Option ist standardmäßig deaktiviert. Wenn diese Option aktiviert ist, wird ein zusätzliches Auswahlmenü angezeigt:

![site-analytics-enable](assets/site-analytics-enable.png)

* **Framework-Verweis der Cloud-Konfiguration**

   Wählen Sie im Pulldown-Menü das für diese Community-Site konfigurierte Analytics Cloud-Service-Framework aus.
   `Communities` ist das Framework-Beispiel aus der Dokumentation [Analytics Configuration for Communities Features](/help/communities/analytics.md#aem-analytics-framework-configuration) .

#### TRANSLATION {#translation}

![site-translation](assets/site-translation.png)

* **Maschinelle Übersetzung zulassen**

   Wenn diese Option aktiviert ist (Standardeinstellung deaktiviert), wird die maschinelle Übersetzung für UGC innerhalb der Site aktiviert. Dies hat keine Auswirkungen auf andere Inhalte wie Seiteninhalte, auch wenn die Site als mehrsprachige Site eingerichtet wurde. Informationen zum Konfigurieren eines lizenzierten Übersetzungsdiensts für AEM Communities finden Sie unter [Übersetzen benutzergenerierter Inhalte](/help/communities/translate-ugc.md) . Eine vollständige Übersicht finden Sie unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) .

![allow-machine-translation](assets/allow-machine-translation.png)

* **Maschinelle Übersetzung für ausgewählte Sprachen aktivieren**

   Die für die maschinelle Übersetzung aktivierten Sprachen entsprechen standardmäßig den Systemeinstellungen, die in der [Konvertierungskonfiguration](/help/communities/translate-ugc.md#translation-integration-configuration)angegeben sind. Diese Standardeinstellungen können für diese Site überschrieben werden, indem Standardwerte gelöscht und/oder andere Sprachen aus dem Pulldown-Menü ausgewählt werden.

* **Übersetzungsanbieter auswählen**

   Standardmäßig ist der Dienstleister ein Testdienst, der nur `microsoft` für Demonstrationen verwendet wird. Wenn kein Dienstleister für Übersetzung lizenziert ist, sollte die Option &quot;maschinelle Übersetzung **zulassen** &quot;deaktiviert werden.

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

Die `ENABLEMENT`Einstellungen gelten, wenn die ausgewählte Community-Site-Vorlage die [Zuweisungsfunktion](/help/communities/functions.md#assignments-function)enthält, die verfügbar ist, wenn die Aktivierungsfunktionen lizenziert und [konfiguriert](/help/communities/enablement.md)sind. Die Referenz-Website-Vorlage, die die Zuweisungsfunktion enthält, lautet `Reference Structured Learning Site Template.`

* **Aktivierungsmanager**(Erforderlich) Nur Mitglieder der `Community Enablementmanagers` Gruppe können ausgewählt werden, um diese Community für die Aktivierung zu verwalten. Aktivierungsmanager sind für die Zuweisung von Mitgliedern zu Ressourcen verantwortlich. Siehe auch [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

* **ID der Marketing Cloud-Organisation**

   (Optional) Die ID für eine [Video Heartbeat Analytics](/help/communities/analytics.md#video-heartbeat-analytics) -Lizenz.

* Wählen Sie **Weiter** aus.

### Schritt 4: Communities-Site erstellen {#step-create-communities-site}

Falls Anpassungen erforderlich sind, verwenden Sie die Schaltfläche &quot; **Zurück** &quot;, um sie vorzunehmen.

Nachdem **Create** ausgewählt und gestartet wurde, kann der Vorgang zum Erstellen der Site nicht unterbrochen werden.

Nachdem die Site erstellt wurde:

* Das Ändern der URL (Knotenname) wird nicht unterstützt.
* Zukünftige Änderungen an der Community-Site-Vorlage haben keine Auswirkungen auf die erstellte Community-Site.
* Die Deaktivierung der Community-Site-Vorlage hat keine Auswirkungen auf die erstellte Community-Site.
* Sie können die [STRUKTUR](#modify-structure) einer Community-Site bearbeiten, indem Sie deren Eigenschaften ändern.

![create-site](assets/create-site1.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Konsole Communities Sites angezeigt, in der Autoren Seiteninhalte hinzufügen können oder Administratoren die Eigenschaften der Site ändern können.

![modify-site-property](assets/modify-site-property.png)

Um eine Community-Site zu ändern, wählen Sie ihren Projektordner aus, um ihn zu öffnen:

![site-project](assets/site-project.png)

Wenn Sie den Mauszeiger über eine Site bewegen oder eine Sitekarte berühren, werden Symbole angezeigt, mit denen Sie die Site im Autorenmodus [](#authoring-site-content)bearbeiten, [die Site-Eigenschaften zur Änderung](#modifying-site-properties)öffnen, die Site [](#publishing-the-site)veröffentlichen, die Site [](#exporting-the-site)exportieren und die Site [löschen](#deleting-the-site)können.

## Erstellen von Site-Inhalten {#authoring-site-content}

Der Inhalt einer Website kann mit den gleichen Tools wie jede andere AEM erstellt werden. Um die Site zum Authoring zu öffnen, wählen Sie das Symbol aus, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen. `Open Site` Die Site wird in einer neuen Registerkarte geöffnet, sodass auf die Konsole Communities Sites weiterhin zugegriffen werden kann.

![site-content](assets/site-content.png)

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](/help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](/help/sites-authoring/qg-page-authoring.md).

## Ändern der Site-Eigenschaften {#modifying-site-properties}

![edit-site](assets/edit-site.png)

Die Eigenschaften einer vorhandenen Site, die während des Site-Erstellungsprozesses angegeben werden, können durch Auswahl des `Edit Site`Symbols geändert werden, das beim Bewegen der Maus über die Site angezeigt wird.

`Details of the following properties match the descriptions provided in the` [Site-Erstellung](#site-creation) .

![modify-site-basicinfo](assets/modify-site-basicinfo.png)

### Basic ändern {#modify-basic}

Das BASIC-Bedienfeld ermöglicht die Änderung von:

* Community-Site-Titel
* Community-Site-Beschreibung

Der Community-Site-Name darf nicht geändert werden.

Die Auswahl einer anderen Community-Site-Vorlage hätte keine Auswirkungen auf eine vorhandene Community-Site, da keine Verbindung zwischen Vorlagen und Sites bestehen bleibt.

Stattdessen kann die [STRUKTUR](#modify-structure) der Community-Site geändert werden.

### Struktur ändern {#modify-structure}

Das STRUKTURbedienfeld ermöglicht die Änderung der Struktur, die ursprünglich aus der ausgewählten Community-Site-Vorlage erstellt wurde. Über den Bereich können Sie:

* Ziehen Sie zusätzliche [Community-Funktionen](/help/communities/functions.md) per Drag &amp; Drop in die Site-Struktur.
* Auf einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

      Bearbeiten Sie Einstellungen, einschließlich des Anzeigentitels und des URL-Namens* sowie [privilegierte Mitgliedergruppen](/help/communities/users.md#privilegedmembersgroups).

   * **`trashcan icon`**

      Entfernen (Löschen) von Funktionen aus der Site-Struktur.

   * **`grid icon`**

      Ändern Sie die Reihenfolge der Funktionen, die in der Navigationsleiste auf der obersten Navigationsebene der Site angezeigt werden.

>[!NOTE]
>
>Sie können die Reihenfolge aller Funktionen in der Site-Struktur mit Ausnahme der Funktion oben ändern. Daher kann die Startseite der Communities site nicht geändert werden.

>[!CAUTION]
>
>* Der Anzeigentitel kann ohne Nebenwirkungen geändert werden, es wird jedoch nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>
Wenn Sie beispielsweise die URL umbenennen, wird die vorhandene UGC nicht verschoben, sodass die UGC verliert wird.

>[!CAUTION]
>
>Die Funktion groups darf *nicht* die *erste oder einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, wie die [Seitenfunktion](/help/communities/functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.

#### Beispiel: Hinzufügen einer Katalogfunktion zu einer Community-Site-Struktur {#example-adding-a-catalog-function-to-a-community-site-structure}

![add-catalog-site](assets/add-catalog-site.png)

### Design ändern {#modify-design}

Das DESIGN-Bedienfeld ermöglicht die Anwendung eines neuen Designs:

* [Community-Site-Thema](#community-site-theme)
* [Community-Site-Branding](#community-site-branding)

   * Blättern Sie nach unten im Bedienfeld, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld &quot;EINSTELLUNGEN&quot;ermöglicht den Zugriff auf die meisten Einstellungen unter den Unterfeldern von Schritt 3 der Community-Site-Erstellung:

* [Benutzerverwaltung](#user-management)
* [Tags](#tagging)
* [Moderation](#moderation)
* [Mitgliederrollen](#roles)
* [Analyse](#analytics)
* [Übersetzung](#translation)

### Miniaturansicht ändern {#modify-thumbnail}

Im Bereich &quot;MINIATURANSICHT&quot;kann ein Bild hochgeladen werden, das die Site in der Konsole &quot;Communities Sites&quot;darstellt.

### Aktivierung ändern {#modify-enablement}

Das Fenster &quot;ENABLEMENT&quot;ermöglicht den Zugriff auf die Einstellungen, die während der Erstellung der Community-Site bereitgestellt werden.

Siehe Beschreibung der [AKTIVIERUNG](#enablement) .

## Veröffentlichen der Site {#publishing-the-site}

Nachdem eine Community-Site neu erstellt oder geändert wurde, ist es möglich, die Site zu veröffentlichen (zu aktivieren), indem Sie das Symbol auswählen, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen. `Publish Site`

![publish-site](assets/publish-site.png)

Nach erfolgreicher Veröffentlichung der Site wird ein Hinweis angezeigt.

![site-published](assets/site-published.png)

### Veröffentlichen mit verschachtelten Gruppen {#publishing-with-nested-groups}

Nach dem Veröffentlichen einer Community-Site muss jede Untergemeinschaft (verschachtelte Gruppe), die mit der [Gruppenkonsole](/help/communities/groups.md)erstellt wurde, einzeln veröffentlicht werden.

## Exportieren der Site {#exporting-the-site}

![export-site](assets/export-site.png)

Wählen Sie das Exportsymbol, wenn Sie den Mauszeiger über die Site bewegen, um ein Paket der Community-Site zu erstellen, das sowohl im [Paketmanager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wird.

Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

## Löschen der Site {#deleting-the-site}

![deleteicon](assets/deleteicon.png)

Um die Community-Site zu löschen, wählen Sie das Symbol &quot;Site löschen&quot;, das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities Site-Konsole bewegen. Durch diese Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. UGC, Benutzergruppen, Assets und Datenbankdatensätze.

## Community-Benutzergruppen erstellt {#created-community-user-groups}

Sobald die neue Community-Site veröffentlicht wurde, werden neue Mitgliedsgruppen (Benutzergruppen werden in der Umgebung zum Veröffentlichen erstellt) mit den entsprechenden Berechtigungen für verschiedene Verwaltungs- und Mitgliedsrollen erstellt.

Der für die Mitgliedergruppen erstellte Name enthält den *Site-Namen* , der in [Schritt 1](#step13asitetemplate) der Site zugewiesen wurde (den Namen, der in der URL angezeigt wird), sowie eine eindeutige ID, um Konflikte mit Community-Sites und -Gruppen zu vermeiden, die denselben Site-Namen für verschiedene Community-Site-Wurzeln haben.

Wenn der Name beispielsweise &quot;interagieren&quot;für eine Site mit dem Titel &quot;Erste Schritte-Tutorial&quot;wäre, wäre die Benutzergruppe für Moderatoren:

* title: Community-Interaktionsmoderatoren
* name: community-*engagement-uid*-moderators

Beachten Sie, dass alle Mitglieder, denen beim Erstellen der Site Rollen als Moderatoren oder Gruppenadministratoren zugewiesen wurden, der entsprechenden Gruppe zugewiesen und der Mitgliedergruppe zugewiesen werden. Diese Gruppen und Mitgliederzuweisungen werden bei der Veröffentlichung der neuen Site erstellt.

Weitere Informationen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

>[!NOTE]
>
>Wenn Social-Anmeldung [zulassen: Facebook](#user-management) ist aktiviert, sobald die Benutzergruppe
>
>* `community-<site-name>-<uid>-members`
>
>
erstellt wurde, sollte der angewendete [Facebook-Cloud-Dienst](/help/communities/social-login.md#createafacebookcloudservice) so konfiguriert sein, dass dieser Gruppe Benutzer hinzugefügt werden.

## Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Standardmäßig wird eine Community-Site zu einer Beispielseite für die Anmeldung umgeleitet, wenn der Benutzer die falschen Anmeldeinformationen eingibt und sich nicht anmeldet. Diese Beispielanmeldung ist auf einem [Produktionsserver](/help/sites-administering/production-ready.md)nicht vorhanden.

Führen Sie zur korrekten Umleitung die folgenden Schritte aus, um sicherzustellen, dass die Authentifizierung bei der Umleitung auf die Community-Site fehlschlägt, sobald eine Site konfiguriert wurde und veröffentlicht wird:

* Auf jeder AEM Instanz im Veröffentlichungsmodus.
* Melden Sie sich mit Administratorrechten an.
* Access the [Web Console](/help/sites-deploying/configuring-osgi.md).

   * For example, [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

* Suchen Sie `Adobe Granite Login Selector Authentication Handler`.
* Wählen Sie das `pencil` Symbol aus, um die Konfiguration zur Bearbeitung zu öffnen.
* Geben Sie eine Seitenzuordnung **für die Anmeldung** wie folgt ein:

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   Beispiel:
   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Wählen Sie **Speichern** aus.

![auth-error](assets/auth-error.png)

### Testauthentifizierungsumleitung {#test-authentication-redirection}

In derselben AEM Instanz im Veröffentlichungsmodus, die mit einer Zuordnung der Anmeldeseite für die Community-Site konfiguriert wurde:

* Navigieren Sie zur Community-Site-Startseite.

   * Beispiel: [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Wählen Sie Abmelden.
* Wählen Sie Anmelden.
* Geben Sie offensichtlich falsche Anmeldeangaben ein, z. B. Benutzername &quot;x&quot;und Kennwort &quot;x&quot;.
* Die Anmeldeseite sollte mit der Fehlermeldung &quot;Ungültige Anmeldung&quot;angezeigt werden.

![test-authentication](assets/test-authentication.png)

## Zugriff auf Community-Sites über die Haupt-Sites-Konsole {#accessing-community-sites-from-main-sites-console}

In der Konsole der globalen Navigations-Sites befinden sich Community-Sites im `Community Sites` Ordner.

Obwohl es möglich ist, auf eine Community-Site auf diese Weise zuzugreifen, sollte die Community-Site für administrative Aufgaben von der Communities Sites-Konsole aus aufgerufen werden.

![access-site](assets/access-site.png)



