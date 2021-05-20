---
title: Erstellen einer neuen Community-Site zur Aktivierung
seo-title: Erstellen einer neuen Community-Site zur Aktivierung
description: Erstellen einer Community-Site für die Aktivierung
seo-description: Erstellen einer Community-Site für die Aktivierung
uuid: a75fa566-a570-45fd-aabc-23651ef819cc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: b9333558-6af9-46b2-9f03-3722645c69a6
docset: aem65
exl-id: 812bbf7b-c49f-4c34-a47d-636b0468e0ba
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1728'
ht-degree: 4%

---

# Erstellen einer neuen Community-Site für Aktivierung {#author-a-new-community-site-for-enablement}

## Community-Site erstellen {#create-community-site}

[Die ](/help/communities/sites-console.md) Erstellung von Community-Sites erfolgt mithilfe eines Assistenten, der Sie durch die Schritte zur Erstellung einer Community-Site führt. Sie können zum Schritt `Next` oder `Back` zum vorherigen Schritt übergehen, bevor Sie die Site im letzten Schritt übergeben.

Erste Schritte mit der Erstellung einer neuen Community-Site:

Verwenden der [Autoreninstanz](https://localhost:4502/)

* Melden Sie sich mit Administratorrechten an und navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Wählen Sie **Erstellen**.

### Schritt 1: Site-Vorlage {#step-site-template}

![Aktivierungs-Site-Vorlage](assets/enablement-site-template.png)

Geben Sie im Schritt **Site-Vorlage** einen Titel, eine Beschreibung und den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B. :

* **Community-Site-Titel**: `Enablement Tutorial`.

* **Community-Site-Beschreibung**: `A site for enabling the community to learn.`

* **Community-Site-Stammordner**: (Leer lassen für Standardstamm  `/content/sites`)

* **Cloud-Konfigurationen**: (Lassen Sie das Feld leer, wenn keine Cloud-Konfigurationen angegeben sind) geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (Für eine einzelne Sprache unberührt lassen: Englisch) verwenden Sie die Dropdown-Liste, um eine  *oder* mehr Sprachen aus den verfügbaren Sprachen auszuwählen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Site erstellt, die im selben Site-Ordner vorhanden ist. Befolgen Sie dabei die Best Practices, die unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) beschrieben werden. Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen des Sprachcodes einer der ausgewählten Sprachen, z. B. &quot;en&quot;für Englisch oder &quot;fr&quot;für Französisch.

* **Community-Site-Name**: `enable`

   * Die ursprüngliche URL wird unter dem Community-Site-Namen angezeigt
   * Hängen Sie für eine gültige URL einen Basissprachcode + &quot;.html&quot; an.
      *Beispiel:* https://localhost:4502/content/sites/  `enable/en.html`

* **Referenz-Site-Vorlage**: nach unten ziehen, um  `Reference Structured Learning Site Template`

Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners vorgestellt:

#### COMMUNITY SITE-THEMA {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt werden soll. Das Banner wird zwischen der Community-Site-Kopfzeile und dem Menü (Navigationslinks) am linken Rand des Browsers fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners kann nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst werden.

![site-branding1](assets/site-branding1.png)

![site-branding2](assets/site-branding2.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie, dass im Schritt Einstellungen vor der Auswahl von `Next` sieben Abschnitte für den Zugriff auf Konfigurationen mit Benutzerverwaltung, Tagging, Rollen, Moderation, Analyse, Übersetzung und Aktivierung verfügbar sind.

#### BENUTZERVERWALTUNG {#user-management}

Es wird empfohlen, [Aktivierungscommunities](/help/communities/overview.md#enablement-community) privat zu sein.

Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich möglicherweise nicht selbst registrieren und keine Anmeldung über soziale Netzwerke verwenden.

Stellen Sie sicher, dass die meisten Kontrollkästchen für [Benutzerverwaltung](/help/communities/sites-console.md#user-management) deaktiviert sind:

* Lassen Sie die Selbstregistrierung der Site-Besucher NICHT zu.
* Lassen Sie NICHT zu, dass anonyme Site-Besucher die Site anzeigen.
* Optional, ob Nachrichten zwischen Community-Mitgliedern zugelassen werden sollen oder nicht.
* Lassen Sie die Anmeldung mit Facebook NICHT zu.
* Lassen Sie die Anmeldung mit Twitter NICHT zu.

![user-mgmt](assets/user-mgmt.png)

#### TAGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl AEM Namespaces gesteuert, die zuvor über die [Tagging Console](/help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. den [Tutorial-Namespace](/help/communities/enablement-setup.md#create-tutorial-tags)).

Durch die Auswahl von Tag-Namespaces für die Community-Site wird außerdem die Auswahl eingeschränkt, die beim Definieren von Katalogen und Aktivierungsressourcen angezeigt wird. Wichtige Informationen finden Sie unter [Tagging von Aktivierungsressourcen](/help/communities/tag-resources.md) .

Die Suche nach Namespaces ist mit der Typvorsuche einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![Aktivierungs-Tagging](assets/enablement-tagging.png)

### ROLLEN {#roles}

[Die ](/help/communities/users.md) Rollen von Community-Mitgliedern werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die Typvorsuche und wählen Sie den Mitglied- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Wählen Sie [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-](/help/communities/deploy-communities.md#tunnel-service-on-author) Service ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Veröffentlichungsumgebung existieren.

![Aktivierungsrollen](assets/site-admin.png)

#### MODERATION {#moderation}

Akzeptieren Sie die globalen Standardeinstellungen für [Moderation](/help/communities/sites-console.md#moderation) benutzergenerierte Inhalte (UGC).

![moderation1](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wählen Sie aus der Dropdown-Liste das für diese Community-Site konfigurierte Analytics Cloud Service-Framework aus.

Die im Screenshot angezeigte Auswahl `Communities` ist das Framework-Beispiel aus der [Konfigurationsdokumentation.](/help/communities/analytics.md#aem-analytics-framework-configuration)

![Analyse](assets/analytics.png)

#### ÜBERSETZUNG {#translation}

Die [Übersetzungsparameter](/help/communities/sites-console.md#translation) geben an, ob UGC übersetzt werden darf und in welche Sprache, falls dies der Fall ist.

* Überprüfen Sie **Maschinelle Übersetzung zulassen**
* Standardeinstellungen verwenden

![Übersetzung](assets/translation.png)

#### AKTIVIERUNG {#enablement}

Für eine Aktivierungs-Community ist es erforderlich, einen oder mehrere Community-Aktivierungsmanager zu identifizieren.

* **Aktivierungsmanager**
 (erforderlich) Mitglieder der 
`Community Enablement Managers` zur Verwaltung dieser Community-Site ausgewählt werden.

   * Typ `s`
   * Wählen Sie nun eine der folgenden Optionen aus `Sirius Nilson`

* **Marketing Cloud-Organisations-ID**
 (optional) Die ID für ein Adobe Analytics-Konto, die erforderlich ist, wenn die  [Video Heartbeat-](/help/communities/analytics.md#video-heartbeat-analytics) Analyse in die Aktivierungsberichte aufgenommen wird.

![Aktivierung](assets/enablement.png)

Wählen Sie **Weiter** aus.

### Schritt 4: Community-Site erstellen {#step-create-community-site}

Wählen Sie **Erstellen.**

![Vorschau](assets/preview.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Konsole Communities > Sites angezeigt.

![enablementsitecreated](assets/enablementsitecreated.png)

### Veröffentlichen der neuen Community-Site {#publish-the-new-community-site}

Die erstellte Site sollte über die Konsole Communities - Sites verwaltet werden. Dieselbe Konsole, von der aus neue Sites erstellt werden können.

Nachdem Sie den Ordner der Community-Site ausgewählt haben, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons](assets/siteactionicons.png)

Bei Auswahl des Ellipsensymbols (Symbol &quot;Mehr Aktionen&quot;) werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![siteactionsnew](assets/siteactionsnew.png)

Von links nach rechts sind sie:

* **Site öffnen**

   Wählen Sie das Stiftsymbol aus, um die Community-Site im Bearbeitungsmodus für Autoren zu öffnen und Seitenkomponenten hinzuzufügen und/oder zu konfigurieren.

* **Site bearbeiten**

   Wählen Sie das Eigenschaftensymbol aus, um die Community-Site zur Änderung von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen.

* **Site veröffentlichen**

   Wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen (standardmäßig localhost:4503 ).

* **Site exportieren**

   Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das sowohl im [Package Manager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wurde.
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Um die Community-Site zu löschen, wählen Sie das Symbol Site löschen aus, das angezeigt wird, wenn Sie den Mauszeiger über die Site in der Communities-Site-Konsole bewegen. Mit dieser Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. benutzergenerierte Inhalte, Benutzergruppen, Assets und Datenbankdatensätze.

   ![enablesiteactions](assets/enablesiteactions.png)

#### Wählen Sie Veröffentlichen {#select-publish}

Wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen.

![publish-site](assets/publish-site.png)

Es wird ein Hinweis geben, dass die Website veröffentlicht wurde.

![site-publish](assets/site-published.png)

## Community-Benutzer und Benutzergruppen {#community-users-user-groups}

### Beachten Sie die neuen Community-Benutzergruppen {#notice-new-community-user-groups}

Zusammen mit der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die neuen Benutzergruppen, die in der Veröffentlichungsumgebung vorhanden sind, unter dem Site-Namen &quot;enable&quot;in Schritt 1 in der [Communities-Mitglieder- und Gruppenkonsole](/help/communities/members.md#groups-console) angezeigt werden:

![community_usergroup](assets/community_usergroup.png)

### Zuweisen von Mitgliedern zur Community Enable Members Group {#assign-members-to-community-enable-members-group}

Wenn der Tunnel-Dienst auf der Autoreninstanz aktiviert ist, können die [Benutzer, die während der Ersteinrichtung](/help/communities/enablement-setup.md#publishcreateenablementmembers) erstellt wurden, der Community-Mitgliedergruppe für die neu erstellte Community-Site zugewiesen werden.

Über die Community-Gruppenkonsole können Mitglieder einzeln hinzugefügt oder über die Mitgliedschaft in einer Gruppe hinzugefügt werden.

In diesem Beispiel wird die Gruppe `Community Ski Class` als Mitglied der Gruppe `Community Enable Members` sowie als Mitglied `Quinn Harper` hinzugefügt.

* Navigieren Sie zur Konsole **Communities, Gruppen** .
* Gruppe *Community-Aktivierungsmitglieder* auswählen
* Geben Sie &quot;ski&quot;in das Suchfeld **Mitglieder zur Gruppe hinzufügen** ein.
* Wählen Sie *Community-Ski-Klasse* (Gruppe der Lernenden)
* Geben Sie &#39;quinn&#39; in das Suchfeld ein
* Wählen Sie *Quinn Harper* (Kontakt für Aktivierungsressource) aus.

* Wählen Sie **Speichern** aus

![edit-group-settings](assets/edit-group-settings.png)

## Veröffentlichungskonfigurationen {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enable-login](assets/enablement-login.png)

### Konfigurieren für Authentifizierungsfehler {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gepusht wurde, [Konfigurieren Sie die Anmelde-Zuordnung](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) in der Veröffentlichungsinstanz. Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldedaten der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut anzeigt.

Fügen Sie einen `Login Page Mapping` als hinzu:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optional) Ändern Sie die Standard-Startseite {#optional-change-the-default-home-page}

Wenn Sie zur Veranschaulichung mit der Veröffentlichungs-Site arbeiten, kann es nützlich sein, die standardmäßige Startseite auf die neue Site zu ändern.

Dazu müssen Sie [CRX|DE](https://localhost:4503/crx/de) Lite verwenden, um die [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md)-Tabelle in der Veröffentlichungsumgebung zu bearbeiten.

Erste Schritte:

1. Greifen Sie beim Veröffentlichen auf CRXDE zu und melden Sie sich mit Administratorrechten an

   * Navigieren Sie beispielsweise zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de) und melden Sie sich mit `admin/admin` an.

1. Erweitern Sie im Projektbrowser `/etc/map` .
1. Wählen Sie den Knoten `http` aus.

   * Wählen Sie **Knoten erstellen**

      * **** Namelocalhost.4503

         (do *not* use &#39;:&#39;)

      * **** [Typesling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Neu erstellter `localhost.4503`-Knoten ausgewählt

   * Eigenschaft hinzufügen

      * **Name** sling:match
      * **** TypeString
      * **Wert** localhost.4503/$

   (muss mit &#39;$&#39; char enden)

   * Eigenschaft hinzufügen

      * **Name** sling:internalRedirect
      * **** TypeString
      * **Wert** /content/sites/enable/en.html


1. Wählen Sie **Alle speichern**
1. (Optional) Löschen Sie den Browser-Verlauf.
1. Navigieren Sie zu https://localhost:4503/

   * Ankunft unter https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Um zu deaktivieren, hängen Sie einfach den Wert der `sling:match`-Eigenschaft mit einem &quot;x&quot;- `xlocalhost.4503/$` - und **Alle speichern** voran.

![change-default-homepage](assets/change-default-homepage.png)

#### Fehlerbehebung: Fehler beim Speichern der Karte {#troubleshooting-error-saving-map}

Wenn die Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503` mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen ist, da `localhost` kein gültiges Namespace-Präfix ist.

![error-map](assets/error-map.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Die Zeichenfolge &quot;**$**&quot;am Ende des regulären Ausdrucks `sling:match` ist von entscheidender Bedeutung, sodass nur genau `https://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der möglicherweise nach der server:port in der URL existiert. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt dies fehl.

## Ändern der Community-Site {#modifying-the-community-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das [Symbol &quot;Site öffnen](/help/communities/sites-console.md#authoring-site-content) verwenden, um standardmäßige AEM zu erstellen.

Darüber hinaus können Administratoren das [Symbol &quot;Site bearbeiten](/help/communities/sites-console.md#modifying-site-properties)&quot;verwenden, um Eigenschaften der Site zu ändern, z. B. den Titel.

Denken Sie nach jeder Änderung an **Save** und re-**Publish** die Site.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](/help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zum Erstellen von Seiten](/help/sites-authoring/qg-page-authoring.md).

### Hinzufügen eines Katalogs {#add-a-catalog}

Die für diese Community-Site ausgewählte Community-Site-Vorlage sollte die Katalogfunktion enthalten.

Ist dies nicht der Fall, kann die Katalogfunktion einfach hinzugefügt werden. Dadurch können andere Mitglieder der Community, die nicht Aktivierungsressourcen oder Lernpfaden zugewiesen sind, Aktivierungsressourcen aus einem Katalog auswählen.

Wenn die Site-Struktur bereits die Katalogfunktion enthält, kann deren Titel geändert werden.

Um die Struktur der Site zu ändern, navigieren Sie zur Konsole **[!UICONTROL Communities]** > **[!UICONTROL Sites]**, öffnen Sie den Ordner `enable` und wählen Sie das Symbol **Site bearbeiten** aus, um auf die Eigenschaften von `Enablement Tutorial` zuzugreifen.

Wählen Sie das Bedienfeld STRUKTUR aus, um einen Katalog hinzuzufügen oder einen vorhandenen Katalog zu ändern:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle Namespaces auswählen**: Behalten Sie die Standardeinstellung bei.

* Wählen Sie **Speichern** aus.

![modify-site-structure](assets/modify-site-structure.png)

Verwenden Sie das Symbol Position , um die Katalogfunktion nach den Zuweisungen an die zweite Position zu verschieben.

![move-catalog-func](assets/move-catalog-func.png)

Wählen Sie **Save** in der oberen rechten Ecke aus, um die Änderungen an der Community-Site zu speichern.

Dann erneut-**Veröffentlichen Sie** die Site.
