---
title: Erstellen einer neuen Community-Site für die Aktivierung
seo-title: Erstellen einer neuen Community-Site für die Aktivierung
description: Community-Site zur Aktivierung erstellen
seo-description: Community-Site zur Aktivierung erstellen
uuid: a75fa566-a570-45fd-aabc-23651ef819cc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: b9333558-6af9-46b2-9f03-3722645c69a6
docset: aem65
translation-type: tm+mt
source-git-commit: e9d5a7acad04d841cbc7d62050163f3de998fab6
workflow-type: tm+mt
source-wordcount: '1728'
ht-degree: 4%

---


# Erstellen einer neuen Community-Site für Aktivierung {#author-a-new-community-site-for-enablement}

## Community-Site erstellen {#create-community-site}

[Die ](/help/communities/sites-console.md) Erstellung von Community-Sites erfolgt mithilfe eines Assistenten, der Sie durch die Schritte zur Erstellung einer Community-Site führt. Es ist möglich, zum Schritt `Next` oder `Back` zum vorherigen Schritt vorzugehen, bevor Sie die Site im letzten Schritt verpflichten.

So erstellen Sie eine neue Community-Site:

Verwenden der Autoreninstanz [a1/>](https://localhost:4502/)

* Melden Sie sich mit Administratorberechtigungen an und navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Wählen Sie **Erstellen**.

### Schritt 1: Site-Vorlage {#step-site-template}

![Aktivieren der Site-Vorlage](assets/enablement-site-template.png)

Geben Sie im Schritt **Site-Vorlage** einen Titel, eine Beschreibung und den Namen der URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **Community-Site-Titel**: `Enablement Tutorial`.

* **Community-Site-Beschreibung**: `A site for enabling the community to learn.`

* **Community-Site-Stammordner**: (Leer lassen für Standard-Stammordner  `/content/sites`)

* **Cloud-Konfigurationen**: (leer lassen, wenn keine Cloud-Konfigurationen angegeben wurden) Geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (unberührt lassen für eine Sprache: Englisch) verwenden Sie die Dropdownliste, um eine  *oder* mehr Basissprachen aus den verfügbaren Sprachen Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht) auszuwählen. Eine Community-Site wird für jede hinzugefügte Sprache erstellt und befindet sich im selben Site-Ordner, wie unter [Übersetzung von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) beschrieben. Die Stammseite jeder Site enthält eine untergeordnete Seite, die nach dem Sprachcode einer der ausgewählten Sprachen benannt ist, wie z.B. &quot;en&quot; für Englisch oder &quot;fr&quot; für Französisch.

* **Community-Site-Name**: `enable`

   * Die anfängliche URL wird unter dem Site-Namen der Community angezeigt
   * Für eine gültige URL hängen Sie einen Basissprachcode an + &quot;.html&quot;
      *Beispiel*: https://localhost:4502/content/sites/  `enable/en.html`

* **Referenz-Site-Vorlage**: nach unten ziehen  `Reference Structured Learning Site Template`

Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners angezeigt:

#### COMMUNITY SITE-THEMA {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt wird. Das Banner wird am linken Rand des Browsers zwischen dem Community-Site-Header und dem Menü (Navigationslinks) fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners wird nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst.

![site-branding1](assets/site-branding1.png)

![site-branding2](assets/site-branding2.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie, dass im Schritt &quot;Einstellungen&quot;vor der Auswahl von `Next` sieben Abschnitte den Zugriff auf Konfigurationen bieten, die Benutzerverwaltung, Tagging, Rollen, Moderation, Analyse, Übersetzung und Aktivierung umfassen.

#### BENUTZERVERWALTUNG {#user-management}

Es wird empfohlen, dass [Aktivierungs-Communities](/help/communities/overview.md#enablement-community) privat sein sollten.

Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich nicht selbst registrieren können und sie möglicherweise keine Social-Anmeldung verwenden.

Stellen Sie sicher, dass die meisten Kontrollkästchen für [Benutzerverwaltung](/help/communities/sites-console.md#user-management) deaktiviert sind:

* Site-Besucher dürfen sich NICHT selbst registrieren.
* Die Ansicht der Site durch anonyme Site-Besucher ist NICHT zulässig.
* Optional, ob das Messaging unter Community-Mitgliedern erlaubt werden soll oder nicht.
* Lassen Sie die Anmeldung bei Facebook NICHT zu.
* Anmeldung mit Twitter NICHT zulassen.

![user-mgmt](assets/user-mgmt.png)

#### TAGGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden gesteuert, indem Sie AEM Namensraum auswählen, die zuvor über die [Tagging-Konsole](/help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. den [Tutorial-Namensraum](/help/communities/enablement-setup.md#create-tutorial-tags)).

Darüber hinaus wird bei der Auswahl von Tag-Namensräumen für die Community-Site die Auswahl beim Definieren von Katalogen und Aktivierungsressourcen eingeschränkt. Wichtige Informationen finden Sie unter [Tagging-Aktivierungsressourcen](/help/communities/tag-resources.md).

Die Suche nach Namensräumen ist mit der Typenvorschau einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![enable-tagging](assets/enablement-tagging.png)

### ROLLEN {#roles}

[Community-Mitglieder ](/help/communities/users.md) Rollen werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die &quot;Type-ahead&quot;-Suche und wählen Sie den Mitglieds- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Wählen Sie [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-](/help/communities/deploy-communities.md#tunnel-service-on-author) Dienst ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Umgebung &quot;Veröffentlichen&quot;vorhanden sind.

![Rollen aktivieren](assets/site-admin.png)

#### MODERATION {#moderation}

Übernehmen Sie die globalen Standardeinstellungen für [Moderation](/help/communities/sites-console.md#moderation) Benutzergenerierte Inhalte (UGC).

![moderation1](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wählen Sie aus der Dropdownliste das für diese Community-Site konfigurierte Analytics Cloud-Service-Framework aus.

Die im Screenshot angezeigte Auswahl ist das Framework-Beispiel aus der [Konfigurationsdokumentation.](/help/communities/analytics.md#aem-analytics-framework-configuration)`Communities`

![Analyse](assets/analytics.png)

#### TRANSLATION {#translation}

Die [Übersetzungseinstellungen](/help/communities/sites-console.md#translation) geben an, ob und in welche Sprache UGC übersetzt werden darf.

* **Maschinelle Übersetzung zulassen**
* Standardeinstellungen verwenden

![Übersetzung](assets/translation.png)

#### AKTIVIERUNG {#enablement}

Für eine Aktivierungsgemeinschaft ist es erforderlich, einen oder mehrere Community-Aktivierungsmanager zu identifizieren.

* **Aktivierungsmanager**
 (erforderlich) Mitglieder der 
`Community Enablement Managers` zur Verwaltung dieser Community-Site ausgewählt werden.

   * Typ `s`
   * Wählen Sie nun eine der folgenden Optionen aus `Sirius Nilson`

* **Marketing Cloud-Organisations-ID**
(optional) Die ID für ein Adobe Analytics-Konto, die erforderlich ist, wenn  [Video Heartbeat ](/help/communities/analytics.md#video-heartbeat-analytics) Analytics in den Berichte für die Aktivierung aufgenommen wird.

![Aktivierung](assets/enablement.png)

Wählen Sie **Weiter** aus.

### Schritt 4: Community-Site {#step-create-community-site} erstellen

Wählen Sie **Erstellen.**

![vorschau](assets/preview.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Konsole Communities > Sites angezeigt.

![enabledSitecreated](assets/enablementsitecreated.png)

### Veröffentlichen der neuen Community-Site {#publish-the-new-community-site}

Die erstellte Site sollte über die Communities - Sites-Konsole verwaltet werden, in der auch neue Sites erstellt werden können.

Wenn Sie den Ordner der Community-Site ausgewählt haben, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons](assets/siteactionicons.png)

Wenn Sie das Symbol &quot;Auslassungszeichen&quot;auswählen (Symbol &quot;Weitere Aktionen&quot;), werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![SiteactionsNeue](assets/siteactionsnew.png)

Von links nach rechts:

* **Site öffnen**

   Wählen Sie das Stiftsymbol aus, um die Community-Site im Autorenbearbeitungsmodus zu öffnen, um Seitenkomponenten hinzuzufügen und/oder zu konfigurieren.

* **Site bearbeiten**

   Wählen Sie das Symbol Eigenschaften aus, um die Community-Site zum Ändern von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen.

* **Site veröffentlichen**

   Wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen (standardmäßig auf localhost:4503).

* **Site exportieren**

   Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das sowohl in [Package Manager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wird.
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Um die Community-Site zu löschen, wählen Sie das Symbol &quot;Site löschen&quot;, das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities Site-Konsole bewegen. Durch diese Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. UGC, Benutzergruppen, Assets und Datenbankdatensätze.

   ![enabledEvents](assets/enablesiteactions.png)

#### Wählen Sie Veröffentlichen {#select-publish}

Wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen.

![publish-site](assets/publish-site.png)

Es wird ein Hinweis geben, dass die Site veröffentlicht wurde.

![site-published](assets/site-published.png)

## Community-Benutzer und -Benutzergruppen {#community-users-user-groups}

### Neue Community-Benutzergruppen {#notice-new-community-user-groups}

Neben der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können unter dem Site-Namen &quot;Aktivieren&quot;in Schritt 1 die neuen Benutzergruppen, die in der Veröffentlichungs-Umgebung vorhanden sind, in der [Communities Members &amp; Groups-Konsole](/help/communities/members.md#groups-console) angezeigt werden:

![community_usergroup](assets/community_usergroup.png)

### Mitglieder der Gruppe Community-Aktivierungsmitglieder zuweisen {#assign-members-to-community-enable-members-group}

Bei aktiviertem Tunneldienst ist es möglich, die [Benutzer, die während des ersten Setups ](/help/communities/enablement-setup.md#publishcreateenablementmembers) erstellt wurden, der Community-Mitgliedergruppe für die neu erstellte Community-Site zuzuweisen.

Mithilfe der Community-Gruppenkonsole können Mitglieder einzeln hinzugefügt oder über die Mitgliedschaft in einer Gruppe hinzugefügt werden.

In diesem Beispiel wird die Gruppe `Community Ski Class` als Mitglied der Gruppe `Community Enable Members` sowie als Mitglied `Quinn Harper` hinzugefügt.

* Navigieren Sie zur Konsole **Communities, Groups**
* Gruppe *Community-Aktivierungsmitglieder* auswählen
* Geben Sie &#39;ski&#39; in das Suchfeld **Hinzufügen Mitglieder zu Gruppe** ein
* Wählen Sie *Community Ski Class* (Gruppe der Lernenden)
* &quot;quinn&quot;in das Suchfeld eingeben
* Wählen Sie *Quinn Harper* (Ansprechpartner für die Aktivierungsressource)

* Wählen Sie **Speichern** aus

![edit-group-settings](assets/edit-group-settings.png)

## Konfigurationen bei Veröffentlichung {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enable-login](assets/enablement-login.png)

### Konfigurieren für Authentifizierungsfehler {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gesendet wurde, konfigurieren Sie die Anmeldezuordnung [für die Veröffentlichungsinstanz ](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`). Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldeinformationen der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut angezeigt wird.

hinzufügen a `Login Page Mapping` wie:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optional) Ändern Sie die Standardeinstellung für die Startseite {#optional-change-the-default-home-page}

Wenn Sie zu Demonstrationszwecken mit der Veröffentlichungs-Site arbeiten, ist es ggf. sinnvoll, die standardmäßige Startseite auf die neue Site zu ändern.

Hierzu müssen Sie [CRX|DE](https://localhost:4503/crx/de) Lite verwenden, um die [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md)-Tabelle beim Veröffentlichen zu bearbeiten.

Erste Schritte:

1. Greifen Sie beim Veröffentlichen auf CRXDE zu und melden Sie sich mit Administratorberechtigungen an

   * Gehen Sie beispielsweise zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de) und melden Sie sich mit `admin/admin` an

1. Erweitern Sie im Projektbrowser `/etc/map`
1. Wählen Sie den Knoten `http`

   * Wählen Sie **Knoten erstellen**

      * **** Namelocalhost.4503

         (do *not* use &#39;:&#39;)

      * **** [Typisierung:Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Mit neu erstelltem `localhost.4503`-Knoten ausgewählt

   * hinzufügen

      * **Name** sling:match
      * **** TypeString
      * **Wert** localhost.4503/$

   (muss mit &#39;$&#39; Zeichen enden)

   * hinzufügen

      * **Name** sling:internalRedirect
      * **** TypeString
      * **Wert** /content/sites/enable/en.html


1. Wählen Sie **Alle speichern**
1. (Optional) Löschen des Browserverlaufs
1. Navigieren Sie zu https://localhost:4503/

   * Ankunft unter https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Zur Deaktivierung müssen Sie den `sling:match`-Eigenschaftswert einfach mit einem &#39;x&#39; - `xlocalhost.4503/$` - und **Save All** vorlegen.

![change-default-homepage](assets/change-default-homepage.png)

#### Fehlerbehebung: Fehler beim Speichern der Map {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503` mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen ist, da `localhost` kein gültiges Namensraum-Präfix ist.

![error-map](assets/error-map.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Die Zeichenfolge &quot;**$**&quot;am Ende des regulären Ausdrucks `sling:match` ist von entscheidender Bedeutung, sodass nur genau `https://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der nach dem server:port in der URL existieren könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt sie fehl.

## Ändern der Community-Site {#modifying-the-community-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das [Symbol &quot;Site öffnen](/help/communities/sites-console.md#authoring-site-content)&quot;verwenden, um standardmäßige AEM Authoring-Aktivitäten durchzuführen.

Administratoren können außerdem das Symbol [Site bearbeiten](/help/communities/sites-console.md#modifying-site-properties) verwenden, um Eigenschaften der Site wie den Titel zu ändern.

Denken Sie nach jeder Änderung daran, **Save** und re-**Publish** auf der Site zu speichern.

>[!NOTE]
>
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [basic handling](/help/sites-authoring/basic-handling.md) und [quick guide to authoring pages](/help/sites-authoring/qg-page-authoring.md).

### hinzufügen eines Katalogs {#add-a-catalog}

Die für diese Community-Site ausgewählte Community-Site-Vorlage sollte die Katalogfunktion enthalten.

Ist dies nicht der Fall, kann die Katalogfunktion einfach hinzugefügt werden. Dadurch können andere Mitglieder der Community, die nicht für Aktivierungsressourcen oder Lernpfade vorgesehen sind, die Ressourcen für die Aktivierung aus einem Katalog auswählen.

Wenn die Site-Struktur bereits die Katalogfunktion enthält, kann deren Titel geändert werden.

Um die Struktur der Site zu ändern, navigieren Sie zur Konsole **[!UICONTROL Communities]** > **[!UICONTROL Sites]**, öffnen Sie den Ordner `enable` und wählen Sie das Symbol **Site bearbeiten**, um auf die Eigenschaften von `Enablement Tutorial` zuzugreifen.

Wählen Sie das STRUKTURbedienfeld aus, um einen Katalog hinzuzufügen oder einen vorhandenen Katalog zu ändern:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle Namensraum** auswählen: als Standard beibehalten.

* Wählen Sie **Speichern** aus.

![modify-site-structure](assets/modify-site-structure.png)

Verwenden Sie das Positionssymbol, um die Katalogfunktion nach den Zuweisungen an die zweite Position zu verschieben.

![move-catalog-func](assets/move-catalog-func.png)

Wählen Sie **Speichern** in der oberen rechten Ecke, um die Änderungen an der Community-Site zu speichern.

Dann die Site erneut-**Veröffentlichen**.

