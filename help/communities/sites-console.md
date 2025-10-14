---
title: Communities-Sites-Konsole
description: Erfahren Sie, wie Sie für die Erstellung, Bearbeitung und Verwaltung von Sites auf die Communities-Sites-Konsole zugreifen können.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 426e3adf-3723-4d17-a988-6eb050939e68
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '3084'
ht-degree: 1%

---

# Communities-Sites-Konsole {#communities-sites-console}

Die Communities Sites -Konsole bietet Zugriff auf:

* Site-Erstellung
* Site-Bearbeitung
* Site-Management
* [Erstellen und Bearbeiten verschachtelter Gruppen](/help/communities/groups.md) (Untergruppen)

In [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) erfahren Sie, wie schnell eine Community-Site in der Autorenumgebung erstellt werden kann und wie Sie Community-Gruppen aus der Autoren- und Veröffentlichungsumgebung erstellen.

>[!NOTE]
>
>Die wichtigsten Communities-Menüs zur Erstellung von [Community-Sites](/help/communities/sites-console.md), [Community-Site-](/help/communities/sites.md), [Community-Gruppenvorlagen](/help/communities/tools-groups.md) und [Community-Funktionen](/help/communities/functions.md) sind nur für die Autorenumgebung vorgesehen.

## Voraussetzungen {#prerequisites}

Bevor Sie eine Community-Site erstellen, *Sie (*):

* Stellen Sie sicher, dass mindestens eine Publish-Instanz ausgeführt wird.
* Aktivieren Sie den [Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author), um Mitglieder und Mitgliedergruppen zu verwalten.
* Identifizieren Sie den [primären Herausgeber](/help/communities/deploy-communities.md#primary-publisher).
* [Konfigurieren Sie die &#x200B;](/help/communities/deploy-communities.md#replication-agents-on-author), wenn der primäre Publisher-Port nicht der Standard ist (4503).

Um sicherzustellen, dass die Site für viele Funktionen bereit ist, sollten Sie die folgenden Schritte ausführen:

* Installieren Sie [neueste Feature Pack](/help/communities/deploy-communities.md#latestfeaturepack).
* Aktivieren Sie [Adobe Analytics](/help/communities/analytics.md) für AEM Communities.
* Konfigurieren von [email](/help/communities/email.md)
* Identifizieren Sie [Community-Administratoren](/help/communities/users.md#creating-community-members).
* [OAuth-Handler aktivieren](/help/communities/social-login.md#adobe-granite-oauth-authentication-handler) für die Anmeldung bei sozialen Netzwerken.

## Zugriff auf die Communities Sites-Konsole {#accessing-communities-sites-console}

Gehen Sie in der Autorenumgebung wie folgt vor, um zur Konsole „Communities Sites“ zu gelangen:

* Von der globalen Navigation: **[!UICONTROL Communities]** > **[!UICONTROL Sites]**

Die Konsole Communities-Sites zeigt alle vorhandenen Community-Sites an. In dieser Konsole können Community-Sites erstellt, bearbeitet, verwaltet und gelöscht werden.

Um eine Community-Site zu erstellen, klicken Sie auf das Symbol **Erstellen** .

Um auf eine vorhandene Community-Site zum Erstellen, Ändern, Veröffentlichen, Exportieren oder Hinzufügen einer verschachtelten Gruppe zuzugreifen, wählen Sie das Ordnersymbol der Site aus.

## Site-Erstellung {#site-creation}

Die Konsole zur Site-Erstellung bietet einen schrittweisen Ansatz zum Zusammenstellen von Funktionen der Site basierend auf einer ausgewählten [Community-Site-Vorlage](/help/communities/sites.md) und Einstellungen.

Jede erstellte Site enthält eine Anmeldefunktion, da sich Website-Besuchende anmelden müssen, bevor sie Inhalte posten, Nachrichten senden oder einer Gruppe beitreten können. Weitere eingeschlossene Funktionen sind Benutzerprofile, Messaging, Benachrichtigungen, Site-Menü, Suche, Themen und Branding.

Der Prozess wird gestartet, indem Sie auf die Schaltfläche `Create` oben in der Communities-Sites-Konsole klicken.

Der Erstellungsprozess ist eine Reihe von Schritten, die als Bedienfelder präsentiert werden und eine Reihe von zu konfigurierenden Funktionen enthalten (die als Unterbedienfelder präsentiert werden). Es ist möglich, mit dem **nächsten** **Schritt oder „Zurück** zum vorherigen Schritt fortzufahren, bevor die Site im letzten Schritt übergeben wird.

### Schritt 1 : Site-Vorlage {#step-site-template}

![newSiteTemplate](assets/newsitetemplate.png)

Im Bedienfeld Site-Vorlage werden Titel, Beschreibung, Site-Stamm, Basissprache, Name und Site-Vorlage angegeben:

* **Community-Site-Titel**

  Ein Anzeigetitel für die Site.

  Der Titel wird auf der veröffentlichten Site und in der Site-Admin-Benutzeroberfläche angezeigt.

* **Community-Site-Beschreibung**

  Eine Beschreibung der Site.

  Die Beschreibung wird nicht auf der veröffentlichten Site angezeigt.

* **Community-Site-Stamm**

  Der Stammpfad zur Site.

  Der Standardstamm ist `/content/sites`, der Stamm kann jedoch an eine beliebige Stelle innerhalb der Website verschoben werden.

* **Basissprache der Community-Site**

  (Für eine einzelne Sprache unberührt lassen: Englisch) Verwenden Sie das Pulldown-Menü, um eine *oder mehrere* Basissprachen aus den verfügbaren Sprachen auszuwählen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (Vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Website erstellt, die im selben Site-Ordner vorhanden ist. Befolgen Sie dazu die Best Practice unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md). Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen einer der ausgewählten Sprachen, z. B. „en“ für Englisch oder „fr“ für Französisch.

* **Community-Site-Name**:

  Der Name der Stammseite der Site, der in der URL angezeigt wird.

   * Überprüfen Sie den Namen , da er nach der Erstellung der Site nicht einfach geändert werden kann.
   * Die Basis-URL ( `https://server:port/site root/site name)` wird unter dem `Community Site Name` angezeigt.

   * Hängen Sie für eine gültige URL einen Basissprachcode + &quot;.html“ an

     *Beispiel*, `https://localhost:4502/content/sites/mysight/en.html`

* **Community-Site-Vorlage** Menü

  Wählen Sie im Pulldown-Menü eine verfügbare [Community-Site-Vorlage](/help/communities/tools.md) aus.

* Wählen Sie **Weiter** aus.

### Schritt 2 : Entwurf {#step-design}

Das Bedienfeld „Design“ enthält zwei Unterbedienfelder zum Auswählen des Designs und des Branding-Banners:

#### COMMUNITY-WEBSITE-DESIGN {#community-site-theme}

![SiteTheme](assets/sitetheme.png)

Das Framework verwendet `Twitter Bootstrap`, um der Site ein responsives, flexibles Design zu verleihen. Eines der vielen vorab geladenen Bootstrap-Designs kann ausgewählt werden, um die ausgewählte Community-Site-Vorlage zu gestalten, oder ein Bootstrap-Design kann hochgeladen werden.

Wenn diese Option aktiviert ist, wird das Design mit einem opaken blauen Häkchen überlagert.

Nachdem die Community-Site veröffentlicht wurde, können Sie [die Eigenschaften bearbeiten](#modifying-site-properties) und ein anderes Design auswählen.

#### COMMUNITY-WEBSITE-BRANDING {#community-site-branding}

![Site-Branding](assets/site-branding.png)

Das Community-Website-Branding ist ein Bild, das als Kopfzeile am oberen Rand jeder Seite angezeigt wird.

Das Bild sollte so breit wie die erwartete Anzeige der Seite im Browser und 120 Pixel hoch sein.

Beachten Sie beim Erstellen oder Auswählen eines Bildes Folgendes:

* Die Bildhöhe wird auf 120 Pixel abgeschnitten, gemessen vom oberen Rand des Bildes.
* Das Bild wird an den linken Rand des Browser-Fensters angeheftet.
* Es gibt keine Größenanpassung des Bildes, sodass, wenn die Bildbreite…

   * Weniger als die Breite des Browsers wird das Bild horizontal wiederholt.
   * Größer als die Breite des Browsers, scheint das Bild abgeschnitten zu sein.

* Wählen Sie **Weiter** aus.

### Schritt 3 : Einstellungen {#step-settings}

Das Bedienfeld Einstellungen enthält mehrere Unterbedienfelder mit zu konfigurierenden Funktionen, bevor Sie mit dem letzten Schritt zur Erstellung der Site fortfahren.

* [BENUTZERVERWALTUNG](#user-management)
* [TAGGING](#tagging)
* [ROLLEN](#roles)
* [MÄSSIGUNG](#moderation)
* [ANALYTICS](#analytics)
* [ÜBERSETZUNG](#translation)

>[!NOTE]
>
>**Aktivieren des Tunneldienstes**
>
>Mehrere Unterbedienfelder Einstellungen ermöglichen die Zuweisung eines vertrauenswürdigen Mitglieds zur moderaten Benutzergenerierung, zur Verwaltung von Gruppen oder als Ansprechpartner für Aktivierungsressourcen in der Veröffentlichungsumgebung.
>
>Die Konvention sieht vor, dass [&#x200B; Veröffentlichungsseite (Benutzer und Benutzergruppen](/help/communities/users.md) (Mitglieder und Mitgliedergruppen) in der Autorenumgebung nicht dupliziert wird.
>
>Daher müssen beim Erstellen der Community-Site in der Autorenumgebung und beim Zuweisen vertrauenswürdiger Mitglieder zu verschiedenen Rollen die Mitgliederdaten aus der Veröffentlichungsumgebung abgerufen werden.
>
>Dies wird erreicht, indem die ` [AEM Communities Publish Tunnel Service](/help/communities/deploy-communities.md#tunnel-service-on-author)` für die Autorenumgebung aktiviert wird.

#### BENUTZERVERWALTUNG {#user-management}

![createsitesettings](assets/createsitesettings.png)

* **Benutzerregistrierung zulassen**

  Wenn diese Option aktiviert ist, können Besucher der Site durch Selbstregistrierung Community-Mitglieder werden.
Wenn diese Option deaktiviert ist*ist die Community-Site*eingeschränkt) und Besucher müssen der Mitgliedergruppe der Community-Site zugewiesen werden, eine Anfrage stellen oder per E-Mail eine Einladung erhalten. Wenn diese Option deaktiviert ist, sollte kein anonymer Zugriff erlaubt sein.
Deaktivieren Sie die Option für *private* Community-Site. Die Standardeinstellung ist aktiviert.

* **Anonymen Zugriff zulassen**

  Wenn diese Option aktiviert ist, ist die Community *Site* und jeder Site-Besucher kann auf die Site zugreifen.
Wenn diese Option deaktiviert ist, können nur angemeldete Mitglieder auf die Website zugreifen.
Deaktivieren Sie die Option für *private* Community-Site. Die Standardeinstellung ist aktiviert.

* **Nachrichten zulassen**

  Wenn diese Option aktiviert ist, können Mitglieder Nachrichten an einander und an die Gruppe innerhalb der Community-Site senden.
Wenn diese Option deaktiviert ist, ist das Messaging für die Community nicht eingerichtet.
Standard ist deaktiviert.

* **Social-Media-Anmeldungen zulassen: Facebook**

  Wenn diese Option aktiviert ist, können sich Website-Besuchende mit ihren Facebook-Kontoanmeldeinformationen anmelden. Die ausgewählte [Facebook-Cloud](/help/communities/social-login.md#create-a-facebook-connect-cloud-service)Konfiguration sollte so konfiguriert werden, dass Benutzende zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.
Wenn diese Option deaktiviert ist, wird keine Facebook-Anmeldung angezeigt.
Deaktivieren Sie diese Option für eine *private* Community-Site. Standard ist deaktiviert.

* **Social-Media-Anmeldungen zulassen: Twitter**

  Wenn diese Option aktiviert ist, können sich Website-Besuchende mit ihren Twitter-Kontoanmeldeinformationen anmelden. Die ausgewählte [Twitter-Cloud](/help/communities/social-login.md#create-a-twitter-connect-cloud-service)Konfiguration sollte so konfiguriert werden, dass Benutzende zur Mitgliedergruppe der Community-Site hinzugefügt werden, sobald die Community-Site erstellt wurde.
Wenn diese Option deaktiviert ist, wird keine Twitter-Anmeldung angezeigt.
Deaktivieren Sie diese Option für eine *private* Community-Site. Standard ist deaktiviert.

>[!NOTE]
>
>**Zulassen von Social-Media-Anmeldungen**
>
>Obwohl es möglicherweise Beispielkonfigurationen für Facebook und Twitter gibt, die für eine [Produktionsumgebung“ auswählbar &#x200B;](/help/sites-administering/production-ready.md), müssen benutzerdefinierte Programme für Facebook und Twitter erstellt werden. Siehe [Social-Anmeldung mit Facebook und Twitter](/help/communities/social-login.md).

#### TAGGING {#tagging}

![site-tagging](assets/site-tagging.png)

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl von Tag-Namespaces gesteuert, die zuvor über die [Tagging-Konsole“ definiert &#x200B;](/help/sites-administering/tags.md#tagging-console).

Darüber hinaus wird durch die Auswahl von Tag-Namespaces für die Community-Site die Auswahl eingeschränkt, die beim Definieren von Katalogen und Ressourcen angezeigt wird.

* Suchfeld : Beginnen Sie mit der Eingabe von Tags, die auf der Website verwendet werden dürfen.

#### ROLLEN {#roles}

![Community-Rollen](assets/site-admin-2.png)

Die [Rollen von Community](/help/communities/users.md)Mitgliedern) werden mit diesen Einstellungen zugewiesen.

Die Suche nach Community-Mitgliedern gestaltet sich mithilfe der Suche mit automatischer Textvervollständigung sehr einfach.

* **Community-Manager**

  Beginnen Sie mit der Eingabe, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, die Community-Mitglieder und Mitgliedergruppen verwalten dürfen.

* **Community-Moderatoren**

  Beginnen Sie mit der Eingabe, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, die als Moderatoren für benutzergenerierte Inhalte vertrauenswürdig sind.

* **Community Privileged Members**

  Beginnen Sie mit der Eingabe, um ein oder mehrere Community-Mitglieder oder Mitgliedergruppen auszuwählen, denen die Möglichkeit zum Erstellen von Inhalten eingeräumt werden soll, wenn `Allow Privileged Member` für eine [Community-Funktion“ ausgewählt &#x200B;](/help/communities/functions.md).

* **Community-Administratoren**

  Beginnen Sie mit der Eingabe von , um einen oder mehrere Site-Administratoren auszuwählen, die die Site-Struktur unabhängig von anderen Site-Administratoren und dem Standard-Community-Administrator verwalten können. Sie können Gruppen auf jeder Hierarchieebene erstellen und Standardadministrator der verschachtelten Gruppen werden (können jedoch später aus der Administratorrolle verschachtelter Gruppen entfernt werden).

#### MÄSSIGUNG {#moderation}

![site-moderation](assets/site-moderation.png)

Die globale Einstellung für die Moderation von benutzergenerierten Inhalten (User-Generated Content, UGC) wird durch diese Einstellungen gesteuert. Einzelne Komponenten verfügen über zusätzliche Einstellungen zur Steuerung der Moderation.

* **Inhalte werden vormoderiert**

  Wenn diese Option aktiviert ist, werden gepostete Community-Inhalte erst angezeigt, nachdem sie von einem Moderator genehmigt wurden. Standard ist deaktiviert. Weitere Informationen finden Sie unter &quot;[&#x200B; von Community-Inhalten](/help/communities/moderate-ugc.md#premoderation).

* **Kennzeichnen eines Schwellenwerts, bevor der Inhalt ausgeblendet wird**

  Wenn größer als 0, die Häufigkeit, mit der ein Thema oder ein Beitrag gekennzeichnet werden muss, bevor er aus der öffentlichen Ansicht ausgeblendet wird. Wenn auf -1 gesetzt, wird das markierte Thema oder der markierte Beitrag nie aus der öffentlichen Ansicht ausgeblendet. Der Standardwert lautet 5.

#### ANALYTICS {#analytics}

![site-analytics](assets/site-analytics.png)

* **Analytics aktivieren**

  Nur verfügbar, wenn Adobe Analytics für Communities[Funktionen &#x200B;](/help/communities/analytics.md) wurde.
Standard ist deaktiviert. Wenn diese Option aktiviert ist, wird ein zusätzliches Auswahlmenü angezeigt:

![site-analytics-enable](assets/site-analytics-enable.png)

* **Cloud Config Framework-Referenz**

  Wählen Sie aus dem Pulldown-Menü das für diese Community-Site konfigurierte Analytics Cloud-Service-Framework aus.
  `Communities` ist das Framework-Beispiel aus der Dokumentation [Analytics-Konfiguration für Communities](/help/communities/analytics.md#aem-analytics-framework-configuration) .

#### ÜBERSETZUNG {#translation}

![site-translation](assets/site-translation.png)

* **Maschinelle Übersetzung zulassen**

  Wenn diese Option aktiviert ist (standardmäßig ist sie deaktiviert), wird die maschinelle Übersetzung für benutzergenerierten Inhalt innerhalb der Site aktiviert. Dies wirkt sich nicht auf andere Inhalte wie Seiteninhalte aus, auch wenn die Website als mehrsprachige Website eingerichtet wurde. Unter [Übersetzen von benutzergenerierten Inhalten](/help/communities/translate-ugc.md) finden Sie Informationen zum Konfigurieren eines lizenzierten Übersetzungs-Services für AEM Communities. Unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) finden Sie einen vollständigen Überblick.

![allow-machine-translation](assets/allow-machine-translation.png)

* **Aktivieren der maschinellen Übersetzung für ausgewählte Sprachen**

  Die für die maschinelle Übersetzung aktivierten Sprachen entsprechen standardmäßig der in der [Konfiguration der Übersetzungsintegration](/help/communities/translate-ugc.md#translation-integration-configuration) angegebenen Systemeinstellung. Diese Standardeinstellungen können für diese Site außer Kraft gesetzt werden, indem die Standardeinstellungen gelöscht und/oder andere Sprachen aus dem Pulldown-Menü ausgewählt werden.

* **Wählen Sie einen Übersetzungsanbieter**

  Standardmäßig ist der Service Provider ein Testdienst, der `microsoft` nur zur Veranschaulichung verwendet. Wenn kein Übersetzungsdienstleister lizenziert ist, sollte **Maschinelle Übersetzung zulassen** deaktiviert werden.

* **Globalen freigegebenen Speicher auswählen**

  Bei einer Website mit mehreren Sprachkopien bietet ein globaler freigegebener Speicher einen einzigen Konversationsfaden, der von jeder Sprachkopie sichtbar ist. Dies wird erreicht, indem eine der Sprachen ausgewählt wird, die als Sprachkopie enthalten sind. Der Standardwert lautet *Kein globaler freigegebener Speicher*.

* **Wählen Sie die Konfiguration des Übersetzungsanbieters**

  Wählen Sie ein [Framework für die Übersetzungsintegration](/help/sites-administering/tc-tic.md), das für den lizenzierten Übersetzungsanbieter erstellt wurde.

* **Wählen Sie die Übersetzungsoptionen für Ihre Community-Site aus**

   * **Übersetzen der gesamten Seite**

     Wenn diese Option aktiviert ist, werden alle benutzergenerierten Inhalte einer Seite in die Basissprache der Seite übersetzt.

     Standard ist *nicht ausgewählt*.

   * **Nur Auswahl übersetzen**

     Wenn diese Option ausgewählt ist, wird neben jedem Beitrag eine Übersetzungsoption angezeigt, mit der einzelne Beiträge in die Basissprache der Seite übersetzt werden können.
Der Standardwert ist *ausgewählt*.

* **Persistenzoptionen auswählen**

   * **Übersetzen Sie Beiträge auf Benutzeranfrage und speichern Sie sie anschließend**
Wenn diese Option aktiviert ist, werden Inhalte erst übersetzt, nachdem eine Anforderung erfolgt ist. Nach der Übersetzung wird die Übersetzung im Repository gespeichert.

     Standard ist *nicht ausgewählt*.

   * **Übersetzungen nicht beibehalten**

     Wenn diese Option aktiviert ist, werden Übersetzungen nicht im Repository gespeichert.

     Wenn sie nicht ausgewählt ist, werden Übersetzungen beibehalten.

     Standard ist *nicht ausgewählt*.

* **Smart Render**

  Eine der folgenden Optionen auswählen:

   * `Always show contributions in the original language` (Standard)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

### Schritt 4: Erstellen einer Communities-Site {#step-create-communities-site}

Wenn Anpassungen erforderlich sind, verwenden Sie die Schaltfläche **Zurück**, um diese vorzunehmen.

Sobald **Erstellen** ausgewählt und gestartet wurde, kann der Prozess der Erstellung der Site nicht mehr unterbrochen werden.

Nachdem die Site erstellt wurde:

* Das Ändern der URL (Knotenname) wird nicht unterstützt.
* Zukünftige Änderungen an der Community-Site-Vorlage wirken sich nicht auf die erstellte Community-Site aus.
* Die Deaktivierung der Community-Site-Vorlage hat keine Auswirkungen auf die erstellte Community-Site.
* Es ist möglich, die [STRUKTUR) einer Community](#modify-structure)Site zu bearbeiten, indem ihre Eigenschaften geändert werden.

![create-site](assets/create-site1.png)

Wenn der Vorgang abgeschlossen ist, wird der Ordner für die neue Site in der Communities-Sites-Konsole angezeigt, wo Autoren Seiteninhalte hinzufügen oder Administratoren die Eigenschaften der Site ändern können.

![modify-site-property](assets/modify-site-property.png)

Um eine Community-Site zu bearbeiten, wählen Sie ihren Projektordner aus, um sie zu öffnen:

![site-project](assets/site-project.png)

Wenn Sie den Mauszeiger über eine Site mit der Maus bewegen oder eine Site-Karte berühren, werden Symbole angezeigt, die Folgendes ermöglichen:

* [Bearbeiten der Site im Autorenmodus](#authoring-site-content)
* [Öffnen der Site-Eigenschaften zur Bearbeitung](#modifying-site-properties)
* [Veröffentlichen der Site](#publishing-the-site)
* [Exportieren der Site](#exporting-the-site)
* [Löschen der Site](#deleting-the-site)

## Verfassen von Site-Inhalten {#authoring-site-content}

Der Inhalt einer Website kann mit den gleichen Tools wie jede andere AEM-Website erstellt werden. Um die Site für das Authoring zu öffnen, wählen Sie das `Open Site` aus, das angezeigt wird, wenn Sie den Mauszeiger über die Site bewegen. Die Site wird auf einer neuen Registerkarte geöffnet, sodass die Communities-Sites-Konsole weiterhin verfügbar ist.

![site-content](assets/site-content.png)

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [Grundlegende Handhabung](/help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zur Seitenbearbeitung](/help/sites-authoring/qg-page-authoring.md).

## Ändern von Site-Eigenschaften {#modifying-site-properties}

![edit-site](assets/edit-site.png)

Die Eigenschaften einer vorhandenen Site, die während des Site-Erstellungsprozesses angegeben wurden, können geändert werden, indem Sie auf das `Edit Site`Symbol klicken, das beim Bewegen des Mauszeigers über die Site angezeigt wird.

`Details of the following properties match the descriptions provided in the` [Site-Erstellung](#site-creation) Abschnitt.

![modify-site-basicinfo](assets/modify-site-basicinfo.png)

### Einfach ändern {#modify-basic}

Das Bedienfeld STANDARD ermöglicht die Änderung von:

* Community-Site-Titel
* Community-Site-Beschreibung

Der Community-Site-Name darf nicht geändert werden.

Die Auswahl einer anderen Community-Site-Vorlage hätte keine Auswirkungen auf eine vorhandene Community-Site, da keine Verbindung zwischen Vorlagen und Sites mehr besteht.

Stattdessen kann [STRUKTUR](#modify-structure) der Community-Site geändert werden.

### Struktur ändern {#modify-structure}

Das Bedienfeld STRUKTUR ermöglicht das Ändern der Struktur, die ursprünglich aus der ausgewählten Community-Site-Vorlage erstellt wurde. Im Bedienfeld können Sie Folgendes tun:

* Ziehen Sie zusätzliche [Community-Funktionen](/help/communities/functions.md) per Drag-and-Drop in die Site-Struktur.
* Bei einer Instanz einer Community-Funktion in der Site-Struktur:

   * **`gear icon`**

     Bearbeiten Sie Einstellungen, einschließlich des Anzeigetitels und des URL-Namens und [privilegierte Mitgliedergruppen](/help/communities/users.md#privilegedmembersgroups).

   * **`trashcan icon`**

     Entfernen (Löschen) von Funktionen aus der Site-Struktur.

   * **`grid icon`**

     Ändern Sie die Reihenfolge der Funktionen, wie sie in der Navigationsleiste der obersten Ebene der Site angezeigt wird.

>[!NOTE]
>
>Sie können die Reihenfolge aller Funktionen in der Site-Struktur mit Ausnahme der Funktion oben ändern. Daher kann die Startseite einer Community-Site nicht geändert werden.

>[!CAUTION]
>
>* Obwohl der Anzeigetitel ohne Nebenwirkungen geändert werden kann, wird nicht empfohlen, den URL-Namen einer Community-Funktion zu bearbeiten, die zu einer Community-Site gehört.
>
>Beim Umbenennen der URL werden beispielsweise vorhandene benutzergenerierte Inhalte nicht verschoben, sodass sie verloren gehen.

>[!CAUTION]
>
>Die Gruppenfunktion darf *nicht* die (*- oder einzige* Funktion in der Site-Struktur sein.
>
>Jede andere Funktion, z. B. die [Seitenfunktion](/help/communities/functions.md#page-function), muss eingeschlossen und zuerst aufgeführt werden.

#### Beispiel : Hinzufügen einer Katalogfunktion zu einer Community-Site-Struktur {#example-adding-a-catalog-function-to-a-community-site-structure}

![add-catalog-site](assets/add-catalog-site.png)

### Entwurf ändern {#modify-design}

Das Bedienfeld „DESIGN“ ermöglicht die Anwendung eines neuen Designs:

* [Community-Site-Thema](#community-site-theme)
* [Community-Site-Branding](#community-site-branding)

   * Scrollen Sie zum unteren Rand des Bedienfelds, um das Markenbild zu ändern.

### Einstellungen ändern {#modify-settings}

Das Bedienfeld EINSTELLUNGEN ermöglicht den Zugriff auf die meisten Einstellungen in den Unterbedienfeldern von für Schritt 3 der Erstellung von Community-Sites:

* [User Management](#user-management)
* [Tags](#tagging)
* [Moderation](#moderation)
* [Mitgliederrollen](#roles)
* [Analyse](#analytics)
* [Übersetzung](#translation)

### Miniaturansicht ändern {#modify-thumbnail}

Das Bedienfeld „MINIATUR“ ermöglicht den Upload eines Bildes, das die Site in der Communities-Sites-Konsole darstellt.

## Veröffentlichen der Site {#publishing-the-site}

Nachdem eine Community-Site neu erstellt oder geändert wurde, ist es möglich, die Site zu veröffentlichen (zu aktivieren), indem Sie das `Publish Site` auswählen, das beim Bewegen der Maus über die Site angezeigt wird.

![publish-site](assets/publish-site.png)

Es gibt einen Hinweis nach der erfolgreichen Veröffentlichung der Site.

![site-published](assets/site-published.png)

### Veröffentlichen mit verschachtelten Gruppen {#publishing-with-nested-groups}

Nach dem Veröffentlichen einer Community-Site ist es erforderlich, jede mithilfe der „Gruppen-Konsole“ erstellte Untercommunity (verschachtelte [) einzeln zu &#x200B;](/help/communities/groups.md).

## Exportieren der Site {#exporting-the-site}

![export-site](assets/export-site.png)

Wählen Sie das Exportsymbol aus, bewegen Sie den Mauszeiger über die Website, damit Sie ein Paket der Community-Site erstellen können, das sowohl im [Package Manager“ gespeichert &#x200B;](/help/sites-administering/package-manager.md) heruntergeladen wird.

UGC ist nicht im Site-Paket enthalten.

## Löschen der Site {#deleting-the-site}

![deleteIcon](assets/deleteicon.png)

Um die Community-Site zu löschen, klicken Sie auf das Symbol Site löschen , das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities-Site-Konsole bewegen. Diese Aktion entfernt alle mit der Site verbundenen Elemente wie benutzergenerierten Inhalt, Benutzergruppen, Assets und Datenbankdatensätze.

## hat Community-Benutzergruppen erstellt {#created-community-user-groups}

Nach der Veröffentlichung der neuen Community-Site werden neue Mitgliedergruppen (Benutzergruppen werden in der Veröffentlichungsumgebung erstellt) mit den entsprechenden Berechtigungen für verschiedene Administrations- und Mitgliederrollen festgelegt.

Der für die Mitgliedergruppen erstellte Name enthält den *Site-*) aus [Schritt 1](#step13asitetemplate) (der Name, der in der URL angezeigt wird). Sie enthält auch eine eindeutige ID, um Konflikte mit Community-Sites und Gruppen zu vermeiden, die denselben Site-Namen für verschiedene Community-Site-Stammverzeichnisse haben.

Wenn der Name beispielsweise „Engagement“ für eine Site mit dem Titel „Erste Schritte-Tutorial“ lauten würde, dann wäre die Benutzergruppe für Moderatoren:

* Titel: Community-Engage-Moderatoren
* Name: community-*engage-uid*-moderators

Alle Mitglieder, denen beim Erstellen der Site Rollen als Moderatoren oder Gruppenadministratoren zugewiesen sind, werden der entsprechenden Gruppe zugewiesen und der Mitgliedergruppe zugewiesen. Diese Gruppen und Mitgliedschaftszuweisungen werden bei der Veröffentlichung erstellt, wenn die neue Site veröffentlicht wird.

Weitere Informationen finden Sie [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).

>[!NOTE]
>
>Wenn [Social-Media-Anmeldung zulassen: Facebook](#user-management) aktiviert ist, sobald die Benutzergruppe `community-<site-name>-<uid>-members`
>erstellt wurde, sollte der angewendete [Facebook-Cloud](/help/communities/social-login.md#createafacebookcloudservice)Service so konfiguriert werden, dass Benutzer zu dieser Gruppe hinzugefügt werden.

## Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Standardmäßig leitet eine Community-Site zu einer Beispiel-Anmeldeseite um, wenn Benutzende falsche Anmeldeinformationen eingeben und sich nicht anmelden. Diese Beispiel-Anmeldung ist auf einem [Produktions-Server](/help/sites-administering/production-ready.md) nicht vorhanden.

Um eine korrekte Weiterleitung durchzuführen, nachdem eine Site konfiguriert und zur Veröffentlichung gepusht wurde, führen Sie die folgenden Schritte aus, um zu einer fehlgeschlagenen Authentifizierung zu gelangen und zur Community-Site weiterzuleiten:

* In jeder AEM-Veröffentlichungsinstanz.
* Melden Sie sich mit Administratorrechten an.
* Rufen Sie die [Web-Konsole](/help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [https://localhost:4503/system/console/configMgr](https://localhost:4503/system/console/configMgr).

* Suchen Sie `Adobe Granite Login Selector Authentication Handler`.
* Wählen Sie das Symbol `pencil` aus, um die Konfiguration zur Bearbeitung zu öffnen.
* Geben Sie **Anmeldeseitenzuordnungen** wie folgt ein:

  `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

  Zum Beispiel:
  `/content/sites/engage/en/signin:/content/sites/engage/en`

* Wählen Sie **Speichern** aus.

![auth-error](assets/auth-error.png)

### Umleitung der Testauthentifizierung {#test-authentication-redirection}

Auf derselben AEM-Veröffentlichungsinstanz, die mit einer Anmeldeseitenzuordnung für die Community-Site konfiguriert wurde:

* Navigieren Sie zur Homepage der Community-Site.

   * Beispiel: [https://localhost:4503/content/sites/engage/en.html](https://localhost:4503/content/sites/engage/en.html)

* Wählen Sie Abmelden aus.
* Wählen Sie Anmelden aus.
* Geben Sie falsche Anmeldeinformationen ein, z. B. Benutzername „x“ und Kennwort „x“.
* Die Anmeldeseite sollte mit dem Fehler „Ungültige Anmeldung“ angezeigt werden.

![test-authentication](assets/test-authentication.png)

## Zugreifen auf Community-Sites über die Hauptkonsole Sites {#accessing-community-sites-from-main-sites-console}

In der globalen Sites-Navigationskonsole befinden sich Community-Sites im Ordner `Community Sites` .

Auf diese Weise kann zwar auf eine Community-Site zugegriffen werden, für Verwaltungsaufgaben sollte jedoch über die Communities-Sites-Konsole auf die Community-Site zugegriffen werden.

![access-site](assets/access-site.png)
