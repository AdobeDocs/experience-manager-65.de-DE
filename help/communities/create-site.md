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
exl-id: d4c1895f-421c-4146-b94a-8d11065ef9e3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 3%

---

# Erstellen einer neuen Community-Site{#author-a-new-community-site}

## Erstellen einer Community-Site {#create-a-community-site}

Verwenden Sie die Autoreninstanz, um eine Community-Site zu erstellen. In der AEM-Autoreninstanz:

1. Melden Sie sich mit Administratorrechten an.
1. Navigieren Sie von der globalen Navigation zu **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

Die Communities Sites-Konsole bietet einen Assistenten, der Sie durch die Schritte zum Erstellen einer Community-Site führt. Sie können zum Schritt `Next` oder `Back` zum vorherigen Schritt übergehen, bevor Sie die Site im letzten Schritt übergeben.

So erstellen Sie eine neue Community-Site:

* Wählen Sie die Schaltfläche `Create` aus.

![createcommunitysite](assets/createcommunitysite.png)

### Schritt 1: Site-Vorlage {#step-site-template}

![Vorlage zum Erstellen der Site](assets/create-site.png)

Geben Sie im Schritt [Site-Vorlage](/help/communities/sites-console.md#step2013asitetemplate) einen Titel, eine Beschreibung und den Namen für die URL ein und wählen Sie eine Community-Site-Vorlage aus, z. B.:

* **Community-Site-Titel**: `Getting Started Tutorial`
* **Community-Site-Beschreibung**: `A site for engaging with the community.`
* **Community-Site-Stammordner**: (Leer lassen für Standardstamm  `/content/sites`)
* **Cloud-Konfigurationen**: (Lassen Sie das Feld leer, wenn keine Cloud-Konfigurationen angegeben sind) geben Sie den Pfad zu den angegebenen Cloud-Konfigurationen an.
* **Community-Site-Basissprache**: (lassen Sie für eine einzelne Sprache unberührt: Englisch) verwenden Sie die Dropdownliste, um eine  *oder* mehr Basissprachen aus den verfügbaren Sprachen auszuwählen: Deutsch, Italienisch, Französisch, Japanisch, Spanisch, Portugiesisch (Brasilien), Chinesisch (Traditionell) und Chinesisch (vereinfacht). Für jede hinzugefügte Sprache wird eine Community-Site erstellt, die im selben Site-Ordner vorhanden ist. Befolgen Sie dabei die Best Practices, die unter [Übersetzen von Inhalten für mehrsprachige Sites](/help/sites-administering/translation.md) beschrieben werden. Die Stammseite jeder Site enthält eine untergeordnete Seite mit dem Namen des Sprachcodes einer der ausgewählten Sprachen, z. B. &quot;en&quot;für Englisch oder &quot;fr&quot;für Französisch.

* **Community-Site-Name**: interagieren

   * Überprüfen Sie den Namen, da er nach der Erstellung der Site nicht einfach geändert werden kann.
   * Die ursprüngliche URL wird unter dem Community-Site-Namen angezeigt
   * Hängen Sie für eine gültige URL einen Basissprachcode + &quot;.html&quot; an.
   * *Beispiel:* https://localhost:4502/content/sites/  `engage/en.html`

* **Vorlage**: nach unten ziehen, um  `Reference Site`

* Wählen Sie **Weiter** aus.

### Schritt 2: Design {#step-design}

Der Schritt &quot;Design&quot;wird in zwei Abschnitten zur Auswahl des Designs und des Branding-Banners vorgestellt:

#### COMMUNITY SITE-THEMA {#community-site-theme}

Wählen Sie den gewünschten Stil aus, der auf die Vorlage angewendet werden soll. Wenn diese Option aktiviert ist, wird das Design mit einem Häkchen überlagert.

#### COMMUNITY SITE BRANDING {#community-site-branding}

(Optional) Laden Sie ein Bannerbild hoch, das auf den Seiten der Site angezeigt werden soll. Das Banner wird an den linken Rand des Browsers zwischen dem Community-Site-Header und den Navigationslinks fixiert. Die Bannerhöhe wird auf 120 Pixel zugeschnitten. Die Größe des Banners kann nicht an die Breite des Browsers und die Höhe von 120 Pixel angepasst werden.

![Community-Site-Branding](assets/community-site-branding.png)

![upload-image-site](assets/upload-image-site.png)

Wählen Sie **Weiter** aus.

### Schritt 3: Einstellungen {#step-settings}

Beachten Sie im Schritt Einstellungen vor der Auswahl von `Next`, dass es sieben Abschnitte gibt, die Zugriff auf Konfigurationen bieten, die Benutzerverwaltung, Tagging, Moderation, Gruppenverwaltung, Analyse, Übersetzung und Aktivierung umfassen.

Besuchen Sie das Tutorial [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md) , um zu erfahren, wie Sie mit den Aktivierungsfunktionen arbeiten.

#### Benutzerverwaltung {#user-management}

Aktivieren Sie alle Kontrollkästchen für [Benutzerverwaltung](/help/communities/sites-console.md#user-management)

* So lassen Sie die Selbstregistrierung von Site-Besuchern zu
* So ermöglichen Sie es Site-Besuchern, die Site anzuzeigen, ohne sich anzumelden
* So können Mitglieder Nachrichten von anderen Community-Mitgliedern senden und empfangen
* So lassen Sie die Anmeldung mit Facebook zu, anstatt ein Profil zu registrieren und zu erstellen
* So lassen Sie die Anmeldung mit Twitter zu, anstatt ein Profil zu registrieren und zu erstellen

>[!NOTE]
>
>Für eine Produktionsumgebung ist es erforderlich, benutzerdefinierte Facebook- und Twitter-Anwendungen zu erstellen. Siehe [Anmeldung in sozialen Netzwerken mit Facebook und Twitter](/help/communities/social-login.md).

![Community-Site-Einstellungen](assets/site-settings.png)

#### TAGGING {#tagging}

Die Tags, die auf Community-Inhalte angewendet werden können, werden durch die Auswahl AEM Namespaces gesteuert, die zuvor über die [Tagging Console](/help/sites-administering/tags.md#tagging-console) definiert wurden (z. B. den [Tutorial-Namespace](/help/communities/setup.md#create-tutorial-tags)).

Die Suche nach Namespaces ist mit der Typvorsuche einfach. Beispiel:

* Typ `tut`
* Wählen Sie nun eine der folgenden Optionen aus `Tutorial`

![tagging](assets/tagging.png)

#### ROLLEN {#roles}

[Die ](/help/communities/users.md) Rollen von Community-Mitgliedern werden über die Einstellungen im Abschnitt Rollen zugewiesen.

Damit ein Community-Mitglied (oder eine Gruppe von Mitgliedern) die Site als Community-Manager erleben kann, verwenden Sie die Typvorsuche und wählen Sie den Mitglied- oder Gruppennamen aus den Optionen in der Dropdown-Liste aus.

Beispiel:

* Typ `q`
* Wählen Sie [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Der Tunnel-](https://helpx.adobe.com/experience-manager/6-3/help/communities/deploy-communities.html#tunnel-service-on-author) Service ermöglicht die Auswahl von Mitgliedern und Gruppen, die nur in der Veröffentlichungsumgebung existieren.

![Benutzerrollen in der neuen Site](assets/site-admin-1.png)

#### MODERATION {#moderation}

Akzeptieren Sie die globalen Standardeinstellungen für [Moderation](/help/communities/sites-console.md#moderation) benutzergenerierte Inhalte (UGC).

![Moderation](assets/moderation1.png)

#### ANALYTICS {#analytics}

Wenn Adobe Analytics lizenziert ist und ein Analytics-Cloud-Service und -Framework konfiguriert wurden, können Sie Analytics aktivieren und das Framework auswählen.

Siehe [Analytics-Konfiguration für Communities-Funktionen](/help/communities/analytics.md).

![Analyse](assets/analytics.png)

#### ÜBERSETZUNG {#translation}

Die [Übersetzungseinstellungen](/help/communities/sites-console.md#translation) geben die Basissprache für die Site an sowie, ob UGC übersetzt werden kann und in welche Sprache, falls dies der Fall ist.

* Überprüfen Sie **Maschinelle Übersetzung zulassen**
* Behalten Sie die für die Übersetzung ausgewählten Standardsprachen beim standardmäßigen Dienst für maschinelle Übersetzung bei.
* Behalten Sie den Standard-Übersetzungsanbieter bei und konfigurieren Sie ihn.
* Ein globaler Store ist nicht erforderlich, da es keine Sprachkopien gibt
* Wählen Sie **Gesamte Seite übersetzen** aus.
* Behalten Sie die Standardpersistenzoption bei

![translation-settings](assets/translation-settings.png)

#### AKTIVIERUNG {#enablement}

Lassen Sie beim Erstellen einer Interaktionsgemeinschaft leer.

Ein ähnliches Tutorial zum schnellen Erstellen einer [Aktivierungs-Community](/help/communities/overview.md#enablement-community) finden Sie unter [Erste Schritte mit AEM Communities für die Aktivierung](/help/communities/getting-started-enablement.md).

Wählen Sie **Weiter** aus.

![Aktivierung](assets/enablement.png)

### Schritt 4: Erstellen der Communities-Site {#step-create-communities-site}

Wählen Sie **Erstellen.**

![create-site](assets/create-site2.png)

Nach Abschluss des Vorgangs wird der Ordner für die neue Site in der Konsole Communities - Sites angezeigt.

![communitiessitesconsole](assets/communitiessitesconsole.png)

## Veröffentlichen der Community-Site {#publish-the-community-site}

Die erstellte Site sollte über die Konsole Communities - Sites verwaltet werden. Dieselbe Konsole, von der aus neue Sites erstellt werden können.

Nachdem Sie den Ordner der Community-Site ausgewählt haben, um ihn zu öffnen, halten Sie den Mauszeiger über das Site-Symbol, sodass vier Aktionssymbole angezeigt werden:

![siteactionicons-1](assets/siteactionicons-1.png)

Bei Auswahl des vierten Ellipsensymbols (Weitere Aktionen) werden die Optionen &quot;Site exportieren&quot;und &quot;Site löschen&quot;angezeigt.

![siteactionsnew-1](assets/siteactionsnew-1.png)

Von links nach rechts sind sie:

* **Site öffnen**

   Wählen Sie das Stiftsymbol aus, um die Community-Site im Bearbeitungsmodus für Autoren zu öffnen, um Seitenkomponenten hinzuzufügen und/oder zu konfigurieren

* **Site bearbeiten**

   Wählen Sie das Eigenschaftensymbol aus, um die Community-Site zur Änderung von Eigenschaften wie dem Titel oder zum Ändern des Designs zu öffnen.

* **Site veröffentlichen**

   Wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen (z. B. wenn Ihr Veröffentlichungsserver auf Ihrem lokalen Computer ausgeführt wird, und klicken Sie dann standardmäßig auf localhost:4503 ).

* **Site exportieren**

   Wählen Sie das Exportsymbol aus, um ein Paket der Community-Site zu erstellen, das sowohl im [Package Manager](/help/sites-administering/package-manager.md) gespeichert als auch heruntergeladen wurde.
Beachten Sie, dass UGC nicht im Site-Paket enthalten ist.

* **Site löschen**

   Wählen Sie das Löschsymbol aus, um die Community-Site in **[!UICONTROL Communities > Sites Console]** zu löschen. Mit dieser Aktion werden alle mit der Site verknüpften Elemente entfernt, z. B. benutzergenerierte Inhalte, Benutzergruppen, Assets und Datenbankdatensätze.

![siteactions](assets/siteactions.png)

>[!NOTE]
>
>Wenn Sie nicht den standardmäßigen Port 4503 für die Veröffentlichungsinstanz verwenden, bearbeiten Sie den standardmäßigen Replikationsagenten, um die Anschlussnummer auf den richtigen Wert festzulegen.
>
>In der Autoreninstanz über das Hauptmenü:
>
>1. Navigieren Sie zum Menü **[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Replikation]** .
>1. Wählen Sie **[!UICONTROL Agenten für Autor]** aus.
>1. Wählen Sie **[!UICONTROL Standardagent (publish)]** aus.
>1. Wählen Sie neben **[!UICONTROL Einstellungen]** **[!UICONTROL Bearbeiten]** aus.
>1. Wählen Sie im Popup-Dialogfeld für Agenteneinstellungen die Registerkarte **[!UICONTROL Transport]** aus.
>1. Ändern Sie in URI die Portnummer 4503 in die gewünschte Portnummer. So verwenden Sie beispielsweise Port 6103: https://localhost:6103/bin/receive?sling:authRequestLogin=1
>1. Wählen Sie **[!UICONTROL OK]** aus.
>1. (Optional) Wählen Sie **[!UICONTROL Clear]** oder **[!UICONTROL Erzwingen des erneuten Versuchs]** aus, um die Replikationswarteschlange zurückzusetzen.


### Wählen Sie Veröffentlichen {#select-publish}

Nachdem Sie sichergestellt haben, dass der Veröffentlichungsserver ausgeführt wird, wählen Sie das Weltsymbol aus, um die Community-Site zu veröffentlichen.

![publish-site](assets/publish-site.png)

Wenn die Community-Site erfolgreich veröffentlicht wurde, erscheint kurz eine Meldung &quot;Site veröffentlicht&quot;.

### Neue Community-Benutzergruppen {#new-community-user-groups}

Zusammen mit der neuen Community-Site werden neue Benutzergruppen erstellt, die über die entsprechenden Berechtigungen für verschiedene Verwaltungsfunktionen verfügen. Weitere Informationen finden Sie unter [Benutzergruppen für Community-Sites](/help/communities/users.md#usergroupsforcommunitysites).

Für diese neue Community-Site können die vier neuen Benutzergruppen unter dem Site-Namen &quot;engage&quot;in Schritt 1 aus der [Gruppenkonsole](/help/communities/members.md) (globale Navigation: Communities, Gruppen):

* Community-Manager einbinden
* Community-Engage-Gruppenadministratoren
* Community-Engage-Mitglieder
* Community-Moderatoren einbinden
* Community-Interaktion mit privilegierten Mitgliedern
* Community Engage Site Content Manager

Beachten Sie, dass [Aaron McDonald](/help/communities/tutorials.md#demo-users) Mitglied von

* Community-Manager einbinden
* Community-Moderatoren einbinden
* Community-Engage-Mitglieder (indirekt als Mitglied der Gruppe Moderatoren )

![Benutzergruppe](assets/user-group.png)

#### https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![interagieren](assets/engage.png)

## Konfigurieren für Authentifizierungsfehler {#configure-for-authentication-error}

Nachdem eine Site konfiguriert und zur Veröffentlichung gepusht wurde, [Konfigurieren Sie die Anmelde-Zuordnung](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) in der Veröffentlichungsinstanz. Der Vorteil besteht darin, dass bei nicht korrekter Eingabe der Anmeldedaten der Authentifizierungsfehler die Anmeldeseite der Community-Site mit einer Fehlermeldung erneut anzeigt.

Fügen Sie `Login Page Mapping` als

* `/content/sites/engage/en/signin:/content/sites/engage/en`

## Optionale Schritte {#optional-steps}

### Ändern der Standard-Startseite {#change-the-default-home-page}

Wenn Sie zur Veranschaulichung mit der Veröffentlichungs-Site arbeiten, kann es nützlich sein, die standardmäßige Startseite auf die neue Site zu ändern.

Dazu müssen Sie [CRXDE](https://localhost:4503/crx/de) Lite verwenden, um die [resource-mapping](/help/sites-deploying/resource-mapping.md)-Tabelle in der Veröffentlichungsumgebung zu bearbeiten.

Erste Schritte:

1. Melden Sie sich in der Veröffentlichungsinstanz mit Administratorrechten an.
1. Navigieren Sie zu [https://localhost:4503/crx/de](https://localhost:4503/crx/de).
1. Erweitern Sie im Projektbrowser `/etc/map.` .
1. Wählen Sie den Knoten `http` aus:

   * Wählen Sie **Knoten erstellen:**

      * **** Namelocalhost.4503 (do  ** not use &#39;:&#39;)

      * **** [Typesling:Mapping](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Mit neu erstelltem `localhost.4503`-Knoten:

   * Eigenschaft hinzufügen:

   * **Name** sling:match
      * **** TypeString
      * **** ValueOcalhost.4503/$ (muss mit &quot;$&quot;char enden)
   * Eigenschaft hinzufügen:

      * **Name** sling:internalRedirect
      * **** TypeString
      * **Wert** /content/sites/engage/en.html


1. Wählen Sie **Alle speichern** aus.
1. (Optional) Löschen Sie den Browser-Verlauf.
1. Navigieren Sie zu https://localhost:4503/.

   * Ankunft unter https://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Um zu deaktivieren, setzen Sie einfach den Wert der `sling:match`-Eigenschaft mit dem Präfix &quot;x&quot;- `xlocalhost.4503/$` - und **Alle speichern**.

![optionale Schritte](assets/optional-steps.png)

#### Fehlerbehebung: Fehler beim Speichern der Karte {#troubleshooting-error-saving-map}

Wenn Änderungen nicht gespeichert werden können, stellen Sie sicher, dass der Knotenname `localhost.4503` mit einem Punkt-Trennzeichen und nicht `localhost:4503` mit einem Doppelpunkt-Trennzeichen ist, da `localhost`kein gültiges Namespace-Präfix ist.

![error-message](assets/error-message.png)

#### Fehlerbehebung: Fehler bei Umleitung {#troubleshooting-fail-to-redirect}

Die Zeichenfolge &quot;**$**&quot;am Ende des regulären Ausdrucks `sling:match`ist von entscheidender Bedeutung, sodass nur genau `https://localhost:4503/` zugeordnet wird. Andernfalls wird der Umleitungswert jedem Pfad vorangestellt, der nach der server:port in der URL vorhanden sein könnte. Wenn AEM also versucht, zur Anmeldeseite umzuleiten, schlägt dies fehl.

### Ändern Sie die Site {#modify-the-site}

Nachdem die Site zum ersten Mal erstellt wurde, können Autoren das [Symbol &quot;Site öffnen](/help/communities/sites-console.md#authoring-site-content) verwenden, um standardmäßige AEM zu erstellen.

Darüber hinaus können Administratoren das [Symbol &quot;Site bearbeiten](/help/communities/sites-console.md#modifying-site-properties)&quot;verwenden, um Eigenschaften der Site zu ändern, z. B. den Titel.

Denken Sie nach jeder Änderung an **Save** und re-**Publish** die Site.

>[!NOTE]
>
>Wenn Sie nicht mit AEM vertraut sind, lesen Sie die Dokumentation zu [Grundlegender Umgang](/help/sites-authoring/basic-handling.md) und eine [Kurzanleitung zum Erstellen von Seiten](/help/sites-authoring/qg-page-authoring.md).
