---
title: Erstellen einer neuen Community-Site
seo-title: Erstellen einer neuen Community-Site
description: Erstellen einer neuen AEM Communities-Site
seo-description: Erstellen einer neuen AEM Communities-Site
uuid: 4f609f5f-ef07-44fc-aeb3-1c616e120d46
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8ae324ea-8b84-47a3-aabf-1fee2a3bd46d
docset: aem65
translation-type: tm+mt
source-git-commit: 2daf00f17058de8b901848fcf1128a5ee9770368
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 3%

---


# Erstellen einer neuen Community-Site{#author-a-new-community-site}

## Community-Site erstellen {#create-a-community-site}

Verwenden Sie die Autoreninstanz, um eine Community-Site zu erstellen. Auf AEM-Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Gehen Sie von der globalen Navigation zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

Die Communities Sites-Konsole bietet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Es ist möglich, den `Next` Schritt oder `Back` den vorherigen Schritt vor der Verpflichtung der Site im letzten Schritt weiter zu gehen.

So erstellen Sie eine neue Community-Site:

* Wählen Sie die `Create` Schaltfläche aus.

![createcommunitysite](assets/createcommunitysite.png)

### Schritt 1: Site-Vorlage {#step-site-template}

![Vorlage zum Erstellen der Site](assets/create-site.png)

Geben Sie im Schritt [&quot;](/help/communities/sites-console.md#step2013asitetemplate)Site-Vorlage&quot;einen Titel, eine Beschreibung und den Namen der URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **Community-Site-Titel**: `Getting Started Tutorial`
* **Community-Site-Beschreibung**: `A site for engaging with the community.`
* **Community-Site-Stammordner**: (Leer lassen für Standard-Stammordner `/content/sites`)
* **Cloud-Konfigurationen**: (leer lassen, wenn keine Cloud-Konfigurationen angegeben wurden) Geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (Für eine Sprache unberührt lassen: Englisch) verwenden Sie die Dropdown-Liste, um eine *oder mehrere* Basissprachen aus den verfügbaren Sprachen Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (traditionell) und Chinesisch (vereinfacht) auszuwählen. Eine Community-Site wird für jede hinzugefügte Sprache erstellt und befindet sich im selben Site-Ordner, wie unter [Übersetzung von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md)beschrieben. Die Stammseite jeder Site enthält eine untergeordnete Seite, die nach dem Sprachcode einer der ausgewählten Sprachen benannt ist, wie z.B. &quot;en&quot; für Englisch oder &quot;fr&quot; für Französisch.

* **Community-Site-Name**: take

   * Überprüfen Sie die Dublette, da der Name nach der Erstellung der Site nicht leicht geändert werden kann.
   * Die anfängliche URL wird unter dem Site-Namen der Community angezeigt
   * Für eine gültige URL hängen Sie einen Basissprachcode an + &quot;.html&quot;
   * *Beispiel*: https://localhost:4502/content/sites/ `engage/en.html`

* **Vorlage**: nach unten ziehen `Reference Site`

* Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners angezeigt:

#### COMMUNITY SITE THEME {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Bei Auswahl dieser Option wird das Design mit einem Häkchen überlagert.

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt wird. Das Banner wird an der linken Kante des Browsers zwischen dem Community-Site-Header und den Navigationslinks fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners wird nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst.

![community-site-branding](assets/community-site-branding.png)

![upload-image-site](assets/upload-image-site.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie, dass im Schritt Einstellungen vor der Auswahl `Next`sieben Abschnitte für den Zugriff auf Konfigurationen mit Benutzerverwaltung, Tagging, Moderation, Gruppenverwaltung, Analyse, Übersetzung und Aktivierung zur Verfügung stehen.

Besuchen Sie das Tutorial [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md) , um mehr über die Funktionen zur Aktivierung zu erfahren.

#### Benutzerverwaltung {#user-management}

Aktivieren Sie alle Kontrollkästchen für [Benutzerverwaltung](/help/communities/sites-console.md#user-management)

* So erlauben Sie Site-Besuchern, sich selbst zu registrieren
* So können Site-Besucher die Ansicht der Site ohne Anmeldung zulassen
* So ermöglichen Sie es Mitgliedern, Nachrichten von anderen Community-Mitgliedern zu senden und zu empfangen
* So lassen Sie die Anmeldung bei Facebook zu, anstatt sich zu registrieren und ein Profil zu erstellen
* So lassen Sie die Anmeldung bei Twitter statt der Registrierung und Erstellung eines Profils zu

>[!NOTE]
>
>Für eine Produktions-Umgebung ist es erforderlich, benutzerdefinierte Facebook- und Twitter-Anwendungen zu erstellen. Siehe [Social-Anmeldung bei Facebook und Twitter](/help/communities/social-login.md).

![Community-Site-Einstellungen](assets/site-settings.png)

#### TAGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden gesteuert, indem AEM Namensraum ausgewählt werden, die zuvor über die [Tagging-Konsole](/help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. der [Tutorial-Namensraum](/help/communities/setup.md#create-tutorial-tags)).

Die Suche nach Namensräumen ist mit der Typenvorschau einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![tagging](assets/tagging.png)

#### ROLES {#roles}

[Community-Mitgliedsrollen](/help/communities/users.md) werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die &quot;Type-ahead&quot;-Suche und wählen Sie den Mitglieds- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Wählen Sie [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-Dienst](https://helpx.adobe.com/experience-manager/6-3/help/communities/deploy-communities.html#tunnel-service-on-author) ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Veröffentlichungs-Umgebung vorhanden sind.

![Benutzerrollen in neuen Sites](assets/site-admin-1.png)

#### MODERATION {#moderation}

Übernehmen Sie die globalen Standardeinstellungen für die [Moderation](/help/communities/sites-console.md#moderation) benutzergenerierter Inhalte (UGC).

![Moderation](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wenn Adobe Analytics lizenziert ist und ein Analytics-Cloud-Dienst und -Framework konfiguriert wurden, können Sie Analytics aktivieren und das Framework auswählen.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

![Analyse](assets/analytics.png)

#### TRANSLATION {#translation}

Die [Übersetzungseinstellungen](/help/communities/sites-console.md#translation) geben die Basissprache für die Site sowie ggf. an, ob UGC übersetzt werden darf und in welche Sprache.

* Maschinelle Übersetzung **zulassen prüfen**
* Lassen Sie Standardsprachen für die Übersetzung vom standardmäßigen maschinellen Übersetzungsdienst ausgewählt
* Übersetzungsdienstleister und Konfiguration beibehalten
* Ein globaler Store ist nicht erforderlich, da es keine Sprachkopien gibt
* Gesamte Seite **übersetzen auswählen**
* Standardpersistenzoption deaktivieren

![translation-settings](assets/translation-settings.png)

#### ENABLEMENT {#enablement}

Lassen Sie beim Erstellen einer Interaktionsgemeinschaft leer.

Eine ähnliche Übung zum schnellen Erstellen einer [Aktivierungs-Community](/help/communities/overview.md#enablement-community)finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

Wählen Sie **Weiter** aus.

![Aktivierung](assets/enablement.png)

### Schritt 4: Communities-Site erstellen {#step-create-communities-site}

Wählen Sie **Erstellen.**

![create-site](assets/create-site2.png)

Nach Abschluss des Prozesses wird der Ordner für die neue Site in der Konsole Communities - Sites angezeigt.

![communitiessitesconsole](assets/communitiessitesconsole.png)

## Veröffentlichen der Community-Site {#publish-the-community-site}

Die erstellte Site sollte über die Communities - Sites-Konsole verwaltet werden, in der auch neue Sites erstellt werden können.

Nachdem Sie den Ordner der Community-Site ausgewählt haben, um ihn zu öffnen, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons-1](assets/siteactionicons-1.png)

Wenn Sie das vierte Auslassungszeichen auswählen (Mehr Aktionen), werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![sitteactionsnew-1](assets/siteactionsnew-1.png)

Von links nach rechts:

* **Site öffnen**

   Wählen Sie das Stiftsymbol, um die Community-Site im Autorenbearbeitungsmodus zu öffnen, um Seitenkomponenten hinzuzufügen und/oder zu konfigurieren

* **Site bearbeiten**

   Wählen Sie das Symbol Eigenschaften aus, um die Community-Site zum Ändern von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen

* **Site veröffentlichen**

   Wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen (z. B. wenn Ihr Veröffentlichungsserver auf Ihrem lokalen Computer ausgeführt wird, dann standardmäßig auf localhost:4503)

* **Site exportieren**

   Wählen Sie das Exportsymbol, um ein Paket der Community-Site zu erstellen, das sowohl im [Paketmanager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wird.
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Wählen Sie das Symbol Löschen, um die Community-Site in der Konsole **[!UICONTROL Communities > Sites zu löschen]**. Durch diese Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. UGC, Benutzergruppen, Assets und Datenbankdatensätze.

![sitteactions](assets/siteactions.png)

>[!NOTE]
>
>Wenn Sie nicht den Standardanschluss 4503 für die Instanz im Veröffentlichungsmodus verwenden, bearbeiten Sie den standardmäßigen Replizierungsagenten, um die Anschlussnummer auf den richtigen Wert festzulegen.
>
>Auf der Autoreninstanz über das Hauptmenü:
>
>1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > Menü **[!UICONTROL Replikation]** .
>1. Wählen Sie **[!UICONTROL Agenten beim Autor]**.
>1. Wählen Sie **[!UICONTROL Standardagent (publish)]**.
>1. Wählen Sie neben **[!UICONTROL Einstellungen]** die Option **[!UICONTROL Bearbeiten]**.
>1. Wählen Sie im Popup-Dialogfeld für Agenteneinstellungen die Registerkarte **[!UICONTROL Transport]** .
>1. Ändern Sie in URI die Anschlussnummer 4503 in die gewünschte Anschlussnummer. So verwenden Sie z. B. Port 6103: https://localhost:6103/bin/receive?sling:authRequestLogin=1
>1. Wählen Sie **[!UICONTROL OK]** aus.
>1. (Optional) Wählen Sie **[!UICONTROL Löschen]** oder Wiederholen **[!UICONTROL erzwingen]** , um die Replikationswarteschlange zurückzusetzen.


### Wählen Sie Veröffentlichen {#select-publish}

Nachdem Sie sichergestellt haben, dass der Veröffentlichungsserver ausgeführt wird, wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen.

![publish-site](assets/publish-site.png)

Wenn die Community-Site erfolgreich veröffentlicht wurde, wird kurz die Meldung &quot;Site veröffentlicht&quot;angezeigt.

### Neue Community-Benutzergruppen {#new-community-user-groups}

Neben der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site werden die vier neuen Benutzergruppen unter dem Site-Namen &quot;locken&quot;in Schritt 1 in der [Gruppenkonsole](/help/communities/members.md) angezeigt (globale Navigation: Communities, Gruppen):

* Community Interagieren von Community Managern
* Community-Gruppenadministratoren
* Community-Interaktionsmitglieder
* Community-Interaktionsmoderatoren
* Community Interagieren mit privilegierten Mitgliedern
* Community Engage Site Content Manager

Beachten Sie, dass [Aaron McDonald](/help/communities/tutorials.md#demo-users) Mitglied von

* Community Interagieren von Community Managern
* Community-Interaktionsmoderatoren
* Community-Interage-Mitglieder (indirekt als Mitglied der Moderatoren-Gruppe)

![Benutzergruppe](assets/user-group.png)

#### https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![take](assets/engage.png)

## Authentifizierungsfehler konfigurieren {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gesendet wurde, [konfigurieren Sie die Anmeldezuordnung](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) in der Veröffentlichungsinstanz. Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldeinformationen der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut angezeigt wird.

hinzufügen `Login Page Mapping` als

* `/content/sites/engage/en/signin:/content/sites/engage/en`

## Optionale Schritte {#optional-steps}

### Standardmäßige Startseite ändern {#change-the-default-home-page}

Wenn Sie zu Demonstrationszwecken mit der Veröffentlichungs-Site arbeiten, ist es ggf. sinnvoll, die standardmäßige Startseite auf die neue Site zu ändern.

Hierzu müssen Sie [CRXDE](https://localhost:4503/crx/de) Lite verwenden, um die [Ressourcenzuordnungstabelle](/help/sites-deploying/resource-mapping.md) bei der Veröffentlichung zu bearbeiten.

Erste Schritte:

1. Melden Sie sich in der Veröffentlichungsinstanz mit Administratorrechten an.
1. Navigieren Sie zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de).
1. Erweitern Sie im Projektbrowser die `/etc/map.`
1. Wählen Sie die `http` Node aus:

   * Wählen Sie **Knoten erstellen:**

      * **Name** localhost.4503( *nicht* verwenden &#39;:&#39;)

      * **Typ** [sling:Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Bei Auswahl des neu erstellten `localhost.4503` Knotens:

   * hinzufügen Eigenschaft:

   * **Name** sling:match
      * **Typzeichenfolge**
      * **Wert** localhost.4503/$(muss mit &#39;$&#39; char enden)
   * hinzufügen Eigenschaft:

      * **Name** sling:internalRedirect
      * **Typzeichenfolge**
      * **Wert** /content/sites/engage/en.html


1. Select **Save All.**
1. (Optional) Löschen Sie den Browserverlauf.
1. Gehen Sie zu https://localhost:4503/.

   * Ankunft unter https://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Zur Deaktivierung setzen Sie dem `sling:match` Eigenschaftswert einfach das Präfix &quot;x&quot;- `xlocalhost.4503/$` - und das Präfix &quot; **Alle** speichern&quot;.

![optionale Schritte](assets/optional-steps.png)

#### Fehlerbehebung: Fehler beim Speichern der Map {#troubleshooting-error-saving-map}

Wenn die Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503`mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen versehen ist, da es sich nicht um ein gültiges Namensraum-Präfix `localhost`handelt.

![error-message](assets/error-message.png)

#### Fehlerbehebung: Fehler bei der Umleitung {#troubleshooting-fail-to-redirect}

Die **Zeichenfolge &#39;**$ `sling:match`&#39; am Ende des regulären Ausdrucks ist von entscheidender Bedeutung, sodass nur exakt `https://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der nach server:port in der URL existieren könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt sie fehl.

### Ändern der Site {#modify-the-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das Symbol [Site öffnen verwenden, um Aktivitäten zum Erstellen AEM Standarddokuments](/help/communities/sites-console.md#authoring-site-content) durchzuführen.

Darüber hinaus können Administratoren die Eigenschaften der Site, z. B. den Titel, über das Symbol [&quot;Site](/help/communities/sites-console.md#modifying-site-properties) bearbeiten&quot;ändern.

Denken Sie nach jeder Änderung daran, die Site zu **speichern** und erneut zu **veröffentlichen** .

>[!NOTE]
>
>If not familiar with AEM, view the documentation on [basic handling](/help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](/help/sites-authoring/qg-page-authoring.md).
