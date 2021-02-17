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

## Community-Site {#create-a-community-site} erstellen

Verwenden Sie die Autoreninstanz, um eine Community-Site zu erstellen. Auf AEM-Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Wechseln Sie in der globalen Navigation zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

Die Communities Sites-Konsole bietet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Es ist möglich, zum Schritt `Next` oder `Back` zum vorherigen Schritt vorzugehen, bevor Sie die Site im letzten Schritt verpflichten.

So erstellen Sie eine neue Community-Site:

* Klicken Sie auf die Schaltfläche `Create`.

![createcommunitysite](assets/createcommunitysite.png)

### Schritt 1: Site-Vorlage {#step-site-template}

![Vorlage zum Erstellen der Site](assets/create-site.png)

Geben Sie im Schritt [Site-Vorlage](/help/communities/sites-console.md#step2013asitetemplate) einen Titel, eine Beschreibung und den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **Community-Site-Titel**: `Getting Started Tutorial`
* **Community-Site-Beschreibung**: `A site for engaging with the community.`
* **Community-Site-Stammordner**: (Leer lassen für Standard-Stammordner  `/content/sites`)
* **Cloud-Konfigurationen**: (leer lassen, wenn keine Cloud-Konfigurationen angegeben wurden) Geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (Für eine Sprache unberührt lassen: Englisch) verwenden Sie die Dropdown-Liste, um eine  *oder* mehr Basissprachen aus den verfügbaren Sprachen Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (traditionell) und Chinesisch (vereinfacht) auszuwählen. Eine Community-Site wird für jede hinzugefügte Sprache erstellt und befindet sich im selben Site-Ordner, wie unter [Übersetzung von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) beschrieben. Die Stammseite jeder Site enthält eine untergeordnete Seite, die nach dem Sprachcode einer der ausgewählten Sprachen benannt ist, wie z.B. &quot;en&quot; für Englisch oder &quot;fr&quot; für Französisch.

* **Community-Site-Name**: take

   * Überprüfen Sie die Dublette, da der Name nach der Erstellung der Site nicht leicht geändert werden kann.
   * Die anfängliche URL wird unter dem Site-Namen der Community angezeigt
   * Für eine gültige URL hängen Sie einen Basissprachcode an + &quot;.html&quot;
   * *Beispiel*: https://localhost:4502/content/sites/  `engage/en.html`

* **Vorlage**: nach unten ziehen  `Reference Site`

* Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners angezeigt:

#### COMMUNITY SITE-THEMA {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Bei Auswahl dieser Option wird das Design mit einem Häkchen überlagert.

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt wird. Das Banner wird an der linken Kante des Browsers zwischen dem Community-Site-Header und den Navigationslinks fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners wird nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst.

![community-site-branding](assets/community-site-branding.png)

![upload-image-site](assets/upload-image-site.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie, dass im Schritt &quot;Einstellungen&quot;vor der Auswahl von `Next` sieben Abschnitte den Zugriff auf Konfigurationen bieten, die unter anderem Benutzerverwaltung, Tagging, Moderation, Gruppenverwaltung, Analyse, Übersetzung und Aktivierung umfassen.

Besuchen Sie das Tutorial [Erste Schritte mit AEM Communities für Aktivierung](/help/communities/getting-started-enablement.md), um mehr über die Arbeit mit den Aktivierungsfunktionen zu erfahren.

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

#### TAGGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden gesteuert, indem Sie AEM Namensraum auswählen, die zuvor über die [Tagging-Konsole](/help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. den [Tutorial-Namensraum](/help/communities/setup.md#create-tutorial-tags)).

Die Suche nach Namensräumen ist mit der Typenvorschau einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![tagging](assets/tagging.png)

#### ROLLEN {#roles}

[Community-Mitglieder ](/help/communities/users.md) Rollen werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die &quot;Type-ahead&quot;-Suche und wählen Sie den Mitglieds- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Wählen Sie [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-](https://helpx.adobe.com/experience-manager/6-3/help/communities/deploy-communities.html#tunnel-service-on-author) Dienst ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Umgebung &quot;Veröffentlichen&quot;vorhanden sind.

![Benutzerrollen in neuen Sites](assets/site-admin-1.png)

#### MODERATION {#moderation}

Übernehmen Sie die globalen Standardeinstellungen für [Moderation](/help/communities/sites-console.md#moderation) Benutzergenerierte Inhalte (UGC).

![Moderation](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wenn Adobe Analytics lizenziert ist und ein Analytics-Cloud-Dienst und -Framework konfiguriert wurden, können Sie Analytics aktivieren und das Framework auswählen.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

![Analyse](assets/analytics.png)

#### TRANSLATION {#translation}

Die [Übersetzungseinstellungen](/help/communities/sites-console.md#translation) geben die Basissprache für die Site sowie ggf. an, ob UGC übersetzt werden darf und in welche Sprache.

* **Maschinelle Übersetzung zulassen**
* Lassen Sie Standardsprachen für die Übersetzung vom standardmäßigen maschinellen Übersetzungsdienst ausgewählt
* Übersetzungsdienstleister und Konfiguration beibehalten
* Ein globaler Store ist nicht erforderlich, da es keine Sprachkopien gibt
* Wählen Sie **Gesamte Seite**
* Standardpersistenzoption deaktivieren

![translation-settings](assets/translation-settings.png)

#### AKTIVIERUNG {#enablement}

Lassen Sie beim Erstellen einer Interaktionsgemeinschaft leer.

Eine ähnliche Übung zum schnellen Erstellen einer [Aktivierungs-Community](/help/communities/overview.md#enablement-community) finden Sie unter [Erste Schritte mit AEM Communities für Aktivierung](/help/communities/getting-started-enablement.md).

Wählen Sie **Weiter** aus.

![Aktivierung](assets/enablement.png)

### Schritt 4: Communities-Site {#step-create-communities-site} erstellen

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

   Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das sowohl in [Package Manager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wird.
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Wählen Sie das Symbol zum Löschen, um die Community-Site aus **[!UICONTROL Communities > Sites console]** zu löschen. Durch diese Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. UGC, Benutzergruppen, Assets und Datenbankdatensätze.

![sitteactions](assets/siteactions.png)

>[!NOTE]
>
>Wenn Sie nicht den Standardanschluss 4503 für die Instanz im Veröffentlichungsmodus verwenden, bearbeiten Sie den standardmäßigen Replizierungsagenten, um die Anschlussnummer auf den richtigen Wert festzulegen.
>
>Auf der Autoreninstanz über das Hauptmenü:
>
>1. Navigieren Sie zum Menü **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]**.
>1. Wählen Sie **[!UICONTROL Agenten auf Autor]**.
>1. Wählen Sie **[!UICONTROL Standardagent (publish)]**.
>1. Wählen Sie neben **[!UICONTROL Einstellungen]** **[!UICONTROL Bearbeiten]**.
>1. Wählen Sie im Popup-Dialogfeld für Agenteneinstellungen die Registerkarte **[!UICONTROL Transport]**.
>1. Ändern Sie in URI die Anschlussnummer 4503 in die gewünschte Anschlussnummer. So verwenden Sie z. B. Port 6103: https://localhost:6103/bin/receive?sling:authRequestLogin=1
>1. Wählen Sie **[!UICONTROL OK]** aus.
>1. (Optional) Wählen Sie **[!UICONTROL Clear]** oder **[!UICONTROL Erzwingen des Wiederholens]** aus, um die Replikationswarteschlange zurückzusetzen.


### Wählen Sie Veröffentlichen {#select-publish}

Nachdem Sie sichergestellt haben, dass der Veröffentlichungsserver ausgeführt wird, wählen Sie das Symbol Welt, um die Community-Site zu veröffentlichen.

![publish-site](assets/publish-site.png)

Wenn die Community-Site erfolgreich veröffentlicht wurde, wird kurz die Meldung &quot;Site veröffentlicht&quot;angezeigt.

### Neue Community-Benutzergruppen {#new-community-user-groups}

Neben der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die vier neuen Benutzergruppen unter dem Site-Namen &quot;locken&quot;in Schritt 1 aus der [Gruppenkonsole](/help/communities/members.md) (globale Navigation: Communities, Gruppen):

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

## Konfigurieren für Authentifizierungsfehler {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gesendet wurde, konfigurieren Sie die Anmeldezuordnung [für die Veröffentlichungsinstanz ](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`). Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldeinformationen der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut angezeigt wird.

hinzufügen ein `Login Page Mapping` als

* `/content/sites/engage/en/signin:/content/sites/engage/en`

## Optionale Schritte {#optional-steps}

### Standardmäßige Startseite {#change-the-default-home-page} ändern

Wenn Sie zu Demonstrationszwecken mit der Veröffentlichungs-Site arbeiten, ist es ggf. sinnvoll, die standardmäßige Startseite auf die neue Site zu ändern.

Hierzu müssen Sie [CRXDE](https://localhost:4503/crx/de) Lite verwenden, um die [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md)-Tabelle bei der Veröffentlichung zu bearbeiten.

Erste Schritte:

1. Melden Sie sich in der Veröffentlichungsinstanz mit Administratorrechten an.
1. Gehen Sie zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de).
1. Erweitern Sie im Projektbrowser `/etc/map.`
1. Wählen Sie den Knoten `http` aus:

   * Wählen Sie **Knoten erstellen:**

      * **** Namelocalhost.4503 (do  ** not use &#39;:&#39;)

      * **** [Typisierung:Zuordnung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Bei Auswahl des neu erstellten `localhost.4503`-Knotens:

   * hinzufügen Eigenschaft:

   * **Name** sling:match
      * **** TypeString
      * **** ValueOcalhost.4503/$ (muss mit &#39;$&#39; char enden)
   * hinzufügen Eigenschaft:

      * **Name** sling:internalRedirect
      * **** TypeString
      * **Wert** /content/sites/engage/en.html


1. Wählen Sie **Alle speichern.**
1. (Optional) Löschen Sie den Browserverlauf.
1. Gehen Sie zu https://localhost:4503/.

   * Ankunft unter https://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Zur Deaktivierung setzen Sie einfach den `sling:match`-Eigenschaftswert mit einem &#39;x&#39; - `xlocalhost.4503/$` - und **Save All**.

![optionale Schritte](assets/optional-steps.png)

#### Fehlerbehebung: Fehler beim Speichern der Map {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503` mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen ist, da `localhost`kein gültiges Namensraum-Präfix ist.

![error-message](assets/error-message.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Die Zeichenfolge &quot;**$**&quot;am Ende des regulären Ausdrucks `sling:match`ist ausschlaggebend, sodass nur genau `https://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der nach dem server:port in der URL existieren könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt sie fehl.

### Ändern Sie die Site {#modify-the-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das [Symbol &quot;Site öffnen](/help/communities/sites-console.md#authoring-site-content)&quot;verwenden, um standardmäßige AEM Authoring-Aktivitäten durchzuführen.

Administratoren können außerdem das Symbol [Site bearbeiten](/help/communities/sites-console.md#modifying-site-properties) verwenden, um Eigenschaften der Site wie den Titel zu ändern.

Denken Sie nach jeder Änderung daran, **Save** und re-**Publish** auf der Site zu speichern.

>[!NOTE]
>
>Wenn Sie mit AEM nicht vertraut sind, Ansicht der Dokumentation unter [basic handling](/help/sites-authoring/basic-handling.md) und [quick guide to authoring pages](/help/sites-authoring/qg-page-authoring.md).
