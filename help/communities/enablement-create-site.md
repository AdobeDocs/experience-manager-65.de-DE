---
title: Erstellen einer neuen Community-Site zur Aktivierung
seo-title: Author a New Community Site for Enablement
description: Erstellen einer Community-Site für die Aktivierung
seo-description: Create a community site for enablement
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
source-wordcount: '1715'
ht-degree: 4%

---

# Erstellen einer neuen Community-Site zur Aktivierung {#author-a-new-community-site-for-enablement}

## Community-Site erstellen {#create-community-site}

[Community-Site-Erstellung](/help/communities/sites-console.md) verwendet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Es ist möglich, `Next` Schritt oder `Back` in den vorherigen Schritt, bevor die Site im letzten Schritt übergeben wird.

Erste Schritte mit der Erstellung einer neuen Community-Site:

Verwenden der [Autoreninstanz](https://localhost:4502/)

* Melden Sie sich mit Administratorrechten an und navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Wählen Sie **Erstellen**.

### Schritt 1: Site-Vorlage {#step-site-template}

![Aktivierungs-Site-Vorlage](assets/enablement-site-template.png)

Im **Site-Vorlage** Schritt, geben Sie einen Titel, eine Beschreibung, den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B. :

* **Community-Site-Titel**: `Enablement Tutorial`.

* **Community-Site-Beschreibung**: `A site for enabling the community to learn.`

* **Community-Site-Stammordner**: (Leer lassen für Standardstamm `/content/sites`)

* **Cloud-Konfigurationen**: (Lassen Sie das Feld leer, wenn keine Cloud-Konfigurationen angegeben sind) geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (Für eine einzelne Sprache unberührt lassen: Englisch) verwenden Sie die Dropdown-Liste, um eine Auswahl zu treffen. *oder mehr* Basissprachen aus den verfügbaren Sprachen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Site erstellt, die gemäß den Best Practices unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md). Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen des Sprachcodes einer der ausgewählten Sprachen, z. B. &quot;en&quot;für Englisch oder &quot;fr&quot;für Französisch.

* **Community-Site-Name**: `enable`

   * Die ursprüngliche URL wird unter dem Community-Site-Namen angezeigt
   * Hängen Sie für eine gültige URL einen Basissprachcode an + &quot;.html&quot;.
      *Beispiel*, https://localhost:4502/content/sites/ `enable/en.html`

* **Referenz-Site-Vorlage**: nach unten ziehen, um `Reference Structured Learning Site Template`

Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners vorgestellt:

#### SITE-THEMA DER GEMEINSCHAFT {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

#### GEMEINSCHAFTLICHE SITE-BRANCHE {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt werden soll. Das Banner wird zwischen der Community-Site-Kopfzeile und dem Menü (Navigationslinks) am linken Rand des Browsers fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners kann nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst werden.

![site-branding1](assets/site-branding1.png)

![site-branding2](assets/site-branding2.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Im Schritt Einstellungen vor Auswahl von `Next`Beachten Sie, dass es sieben Abschnitte gibt, die Zugriff auf Konfigurationen bieten, die Benutzerverwaltung, Tagging, Rollen, Moderation, Analyse, Übersetzung und Aktivierung umfassen.

#### BENUTZERVERWALTUNG {#user-management}

Es wird empfohlen, [Aktivierungsgemeinschaften](/help/communities/overview.md#enablement-community) privat sein.

Eine Community-Site ist privat, wenn anonymen Site-Besuchern der Zugriff verweigert wird, sie sich möglicherweise nicht selbst registrieren und keine Anmeldung über soziale Netzwerke verwenden.

Stellen Sie sicher, dass die meisten Kontrollkästchen für [Benutzerverwaltung](/help/communities/sites-console.md#user-management) :

* Lassen Sie die Selbstregistrierung der Site-Besucher NICHT zu.
* Lassen Sie es NICHT zu, dass anonyme Site-Besucher die Site anzeigen.
* Optional, ob Nachrichten zwischen Community-Mitgliedern zugelassen werden sollen oder nicht.
* Lassen Sie die Anmeldung mit Facebook NICHT zu.
* Lassen Sie die Anmeldung mit Twitter NICHT zu.

![user-mgmt](assets/user-mgmt.png)

#### TAGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl AEM Namespaces gesteuert, die zuvor durch die [Tagging-Konsole](/help/sites-administering/tags.md#tagging-console) (z. B. [Tutorial-Namespace](/help/communities/enablement-setup.md#create-tutorial-tags)).

Durch die Auswahl von Tag-Namespaces für die Community-Site wird außerdem die Auswahl eingeschränkt, die beim Definieren von Katalogen und Aktivierungsressourcen angezeigt wird. Siehe [Tagging von Aktivierungsressourcen](/help/communities/tag-resources.md) für wichtige Informationen.

Die Suche nach Namespaces ist mit der Typvorsuche einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![Aktivierungs-Tagging](assets/enablement-tagging.png)

### ROLLEN {#roles}

[Community-Mitgliederrollen](/help/communities/users.md) werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die Typvorsuche und wählen Sie den Mitglied- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Auswählen [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Veröffentlichungsumgebung vorhanden sind.

![Aktivierungsrollen](assets/site-admin.png)

#### MODERATION {#moderation}

Globale Standardeinstellungen akzeptieren für [moderieren](/help/communities/sites-console.md#moderation) benutzergenerierte Inhalte (UGC).

![moderation1](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wählen Sie aus der Dropdown-Liste das für diese Community-Site konfigurierte Analytics Cloud Service-Framework aus.

Die im Screenshot angezeigte Auswahl, `Communities`, ist ein Framework-Beispiel aus der [Konfigurationsdokumentation.](/help/communities/analytics.md#aem-analytics-framework-configuration)

![Analyse](assets/analytics.png)

#### ÜBERSETZUNG {#translation}

Die [Übersetzungsparameter](/help/communities/sites-console.md#translation) Geben Sie an, ob UGC übersetzt werden darf und in welche Sprache, falls ja.

* Überprüfen **Maschinelle Übersetzung zulassen**
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
(optional) Die Kennung für ein Adobe Analytics-Konto, die erforderlich ist, wenn [Video Heartbeat Analytics](/help/communities/analytics.md#video-heartbeat-analytics) in der Aktivierungsberichterstellung.

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

   Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das beide in gespeichert ist. [Package Manager](/help/sites-administering/package-manager.md) und heruntergeladen.
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

### Neue Community-Benutzergruppen {#notice-new-community-user-groups}

Zusammen mit der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die neuen Benutzergruppen, die in der Veröffentlichungsumgebung vorhanden sind, unter Berücksichtigung des Site-Namens &quot;Aktivieren&quot;in Schritt 1 aus dem [Communities Mitglieder &amp; Gruppen-Konsole](/help/communities/members.md#groups-console):

![community_usergroup](assets/community_usergroup.png)

### Zuweisen von Mitgliedern zur Community Aktivieren-Gruppe {#assign-members-to-community-enable-members-group}

Wenn der Tunnel-Dienst für die Autoreninstanz aktiviert ist, kann die [bei der Ersteinrichtung erstellte Benutzer](/help/communities/enablement-setup.md#publishcreateenablementmembers) zur Community-Mitgliedergruppe für die neu erstellte Community-Site.

Über die Community-Gruppenkonsole können Mitglieder einzeln hinzugefügt oder über die Mitgliedschaft in einer Gruppe hinzugefügt werden.

In diesem Beispiel wird die Gruppe `Community Ski Class` wird als Mitglied der Gruppe hinzugefügt `Community Enable Members` sowie Mitglied `Quinn Harper`.

* Navigieren Sie zu **Communities, Gruppen** console
* Auswählen *Community-Aktivierte Mitglieder* Gruppe
* Geben Sie &quot;ski&quot;in die **Mitglieder zu Gruppe hinzufügen** Suchfeld
* Auswählen *Community-Ski-Klasse* (Gruppe der Lernenden)
* Geben Sie &#39;quinn&#39; in das Suchfeld ein
* Auswählen *Quinn Harper* (Kontakt für Aktivierungsressource)

* Klicken Sie auf **Speichern**

![edit-group-settings](assets/edit-group-settings.png)

## Veröffentlichungskonfigurationen {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enable-login](assets/enablement-login.png)

### Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Sobald eine Site konfiguriert und zur Veröffentlichung gepusht wurde, [Anmeldezuordnung konfigurieren](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) in der Veröffentlichungsinstanz. Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldedaten der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut anzeigt.

Hinzufügen einer `Login Page Mapping` as:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optional) Ändern der Standard-Startseite {#optional-change-the-default-home-page}

Wenn Sie zur Veranschaulichung mit der Veröffentlichungs-Site arbeiten, kann es nützlich sein, die standardmäßige Startseite auf die neue Site zu ändern.

Dazu müssen Sie Folgendes verwenden: [CRX|DE](https://localhost:4503/crx/de) Lite zum Bearbeiten [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md) -Tabelle auf der Veröffentlichungsinstanz.

Erste Schritte:

1. Greifen Sie beim Veröffentlichen auf CRXDE zu und melden Sie sich mit Administratorrechten an

   * Navigieren Sie beispielsweise zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de) und melden Sie sich mit `admin/admin`

1. Erweitern Sie im Projektbrowser die `/etc/map`
1. Wählen Sie die `http` Knoten

   * Auswählen **Knoten erstellen**

      * **Name** localhost.4503

         (do *not* use &#39;:&#39;)

      * **Typ** [sling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Mit neu erstellt `localhost.4503` Knoten ausgewählt

   * Eigenschaft hinzufügen

      * **Name** sling:match
      * **Typ** Zeichenfolge
      * **Wert** localhost.4503/$

   (muss mit &#39;$&#39; char enden)

   * Eigenschaft hinzufügen

      * **Name** sling:internalRedirect
      * **Typ** Zeichenfolge
      * **Wert** /content/sites/enable/en.html


1. Wählen Sie **Alle speichern** aus
1. (Optional) Löschen Sie den Browser-Verlauf.
1. Navigieren Sie zu https://localhost:4503/

   * Ankunft unter https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Um zu deaktivieren, hängen Sie einfach die `sling:match` Eigenschaftswert mit einem &quot;x&quot;- `xlocalhost.4503/$` - und **Alle speichern**.

![change-default-homepage](assets/change-default-homepage.png)

#### Fehlerbehebung: Fehler beim Speichern der Karte {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503`, mit einem &quot;Punkt&quot;-Trennzeichen und nicht `localhost:4503` mit einem &quot;Doppelpunkt&quot;-Trennzeichen `localhost` ist kein gültiges Namespace-Präfix.

![error-map](assets/error-map.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Der **$**&quot; am Ende des regulären Ausdrucks `sling:match` Zeichenfolge ist von entscheidender Bedeutung, sodass nur genau `https://localhost:4503/` zugeordnet ist, wird der Umleitungswert ansonsten jedem Pfad vorangestellt, der nach der Datei server:port in der URL vorhanden sein könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt dies fehl.

## Ändern der Community-Site {#modifying-the-community-site}

Nachdem die Site ursprünglich erstellt wurde, können Autoren die [Symbol &quot;Site öffnen&quot;](/help/communities/sites-console.md#authoring-site-content) , um standardmäßige AEM zu erstellen.

Administratoren können außerdem die [Symbol &quot;Site bearbeiten&quot;](/help/communities/sites-console.md#modifying-site-properties) , um Eigenschaften der Site zu ändern, z. B. den Titel.

Denken Sie nach jeder Änderung daran, **Speichern** und erneute **Veröffentlichen** die Site.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation unter [grundlegende Handhabung](/help/sites-authoring/basic-handling.md) und [Kurzanleitung zum Erstellen von Seiten](/help/sites-authoring/qg-page-authoring.md).

### Hinzufügen eines Katalogs {#add-a-catalog}

Die für diese Community-Site ausgewählte Community-Site-Vorlage sollte die Katalogfunktion enthalten.

Ist dies nicht der Fall, kann die Katalogfunktion einfach hinzugefügt werden. Dadurch können andere Mitglieder der Community, die nicht Aktivierungsressourcen oder Lernpfaden zugewiesen sind, Aktivierungsressourcen aus einem Katalog auswählen.

Wenn die Site-Struktur bereits die Katalogfunktion enthält, kann deren Titel geändert werden.

Um die Struktur der Site zu ändern, navigieren Sie zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]** Konsole, öffnen Sie die `enable` und wählen Sie die **Site bearbeiten** -Symbol, um auf die Eigenschaften von `Enablement Tutorial`.

Wählen Sie das Bedienfeld STRUKTUR aus, um einen Katalog hinzuzufügen oder einen vorhandenen Katalog zu ändern:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle Namespaces auswählen**: Behalten Sie die Standardeinstellung bei.

* Klicken Sie auf **Speichern**.

![modify-site-structure](assets/modify-site-structure.png)

Verwenden Sie das Symbol Position , um die Katalogfunktion nach den Zuweisungen an die zweite Position zu verschieben.

![move-catalog-func](assets/move-catalog-func.png)

Auswählen **Speichern** in der oberen rechten Ecke, um die Änderungen an der Community-Site zu speichern.

Dann erneut **Veröffentlichen** die Site.
