---
title: Social-Anmeldung bei Facebook und Twitter
seo-title: Social-Anmeldung bei Facebook und Twitter
description: Mit der Anmeldung über Social können sich Site-Besucher mit ihrem Facebook- oder Twitter-Konto anmelden.
seo-description: Mit der Anmeldung über Social können sich Site-Besucher mit ihrem Facebook- oder Twitter-Konto anmelden.
uuid: f70e346e-0d8c-41a0-a100-206a420088dc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c0a71870-8f95-40c8-9ffd-b7af49723288
translation-type: tm+mt
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# Social-Anmeldung bei Facebook und Twitter {#social-login-with-facebook-and-twitter}

Bei der Anmeldung in sozialen Netzwerken handelt es sich um die Möglichkeit, einem Site-Besucher die Möglichkeit zu geben, sich mit seinem Facebook- oder Twitter-Konto anzumelden. Daher sollten Sie zulässige Facebook- oder Twitter-Daten in ihr AEM-Profil aufnehmen.

![socialloginweretail](assets/socialloginweretail.png)

## Übersicht über die Social-Anmeldung {#social-login-overview}

Um die Anmeldung in sozialen Netzwerken einzubeziehen, müssen benutzerdefinierte Facebook- und Twitter-Anwendungen *erstellt werden* .

Während das für den Handel bestimmte Beispiel Beispiele für Facebook- und Twitter-Apps und Cloud-Dienste bereitstellt, sind diese nicht auf einer [Produktions-Website](../../help/sites-administering/production-ready.md)verfügbar.

Die erforderlichen Schritte sind:

1. [Aktivieren Sie die OAuth-Authentifizierung](#adobe-granite-oauth-authentication-handler) für alle AEM-Veröffentlichungsinstanzen.

   Wenn OAuth nicht aktiviert ist, schlägt die Anmeldung fehl.

1. **Erstellen** Sie eine Social-App und einen Cloud-Dienst.

   * So unterstützen Sie die Anmeldung bei Facebook:

      * Erstellen Sie eine [Facebook-App](#create-a-facebook-app).
      * Erstellen und veröffentlichen Sie einen [Facebook Connect-Cloud-Dienst](#create-a-facebook-connect-cloud-service).
   * So unterstützen Sie die Anmeldung bei Twitter:

      * Erstellen Sie eine [Twitter-App](#create-a-twitter-app).
      * Erstellen und veröffentlichen Sie einen [Twitter Connect-Cloud-Dienst](#create-a-twitter-connect-cloud-service).


1. [**Aktivieren **Sie die Anmeldung](#enable-social-login)in sozialen Netzwerken für eine Community-Site.

Es gibt zwei grundlegende Konzepte:

1. **Umfang** (Berechtigungen) gibt die Daten an, die die App anfordern darf.

   * Die Facebook- und Twitter-Instanzen [Adobe Granite OAuth Application und Provider](#adobe-granite-oauth-application-and-provider) beinhalten standardmäßig die grundlegenden App-Berechtigungen in ihren Geltungsbereich.

1. **Felder** (Parameter) geben die tatsächlichen Daten an, die mit URL-Parametern angefordert werden.

   * Diese Felder werden in [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) und [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider)angegeben.
   * Die Standardfelder reichen für die meisten Anwendungsfälle aus, können jedoch geändert werden.

## Facebook-Anmeldung {#facebook-login}

### Facebook-API-Version {#facebook-api-version}

Die Anmeldung in sozialen Netzwerken und das Facebook-Beispiel für den Handel wurden entwickelt, als die Facebook-Grafik-API Version 1.0 war.
Ab AEM 6.4 GA und AEM 6.3 SP1 wurde die Anmeldung für soziale Netzwerke aktualisiert und funktioniert nun mit der neueren Facebook Graph API 2.5 Version.

>[!NOTE]
>
>Wenn Sie bei älteren AEM-Versionen eine Ausnahme in Protokollen sehen **Kann kein Token aus dieser** Version extrahieren, aktualisieren Sie auf die neueste CFP für diese AEM-Version.


Informationen zur Version der Facebook-Grafik-API finden Sie im [Facebook-API-Changelog](https://developers.facebook.com/docs/apps/changelog).

### Facebook-App erstellen {#create-a-facebook-app}

Zur Aktivierung der Social-Anmeldung für Facebook ist eine ordnungsgemäß konfigurierte Facebook-Anwendung erforderlich.

Um eine Facebook-Anwendung zu erstellen, befolgen Sie die Anweisungen von Facebook unter [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/). Änderungen an ihren Anweisungen werden in den folgenden Informationen nicht widergespiegelt.

Im Allgemeinen ab Facebook API Version 2.7:

* *Hinzufügen einer neuen Facebook-App*
   * Wählen Sie als *Plattform* Website:
      * Geben Sie für *Site-URL*`  https://<server>:<port>.`
      * Geben Sie als *Anzeigename* einen Titel ein, der als Titel des Facebook-Verbindungs-Dienstes verwendet werden soll.
      * Zur *Kategorie* wird empfohlen, &quot; *Apps für Seiten*&quot;zu wählen, kann jedoch alles sein.
      * *Hinzufügen Produkt:  Facebook-Anmeldung*
      * Geben Sie für *gültige OAuth-Umleitungs-URIs*`  https://<server>:<port>.`

>[!NOTE]
>
>Für die Entwicklung funktioniert http://localhost:4503.


Nachdem die Anwendung erstellt wurde, suchen Sie die Einstellungen für die **[!UICONTROL App-ID]** und den **[!UICONTROL geheimen]** Schlüssel. Diese Informationen sind für die Konfiguration des [Facebook-Cloud-Dienstes](#createafacebookcloudservice)erforderlich.

### Facebook Connect Cloud-Dienst erstellen {#create-a-facebook-connect-cloud-service}

Die [Adobe Granite OAuth Application and Provider](https://chl-author.corp.adobe.com/content/help/en/experience-manager/6-4/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -Instanz, instanziiert durch Erstellen einer Cloud-Service-Konfiguration, identifiziert die Facebook-Anwendung und die Mitgliedsgruppe/n, der/denen die neuen Benutzer hinzugefügt werden.

1. Melden Sie sich auf der AEM-Autoreninstanz mit Administratorrechten an.
1. Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Facebook Social-Anmeldekonfiguration]**.
1. Wählen Sie den **[!UICONTROL Kontextpfad]** für die Konfiguration aus.

   **[!UICONTROL Der Kontextpfad]** sollte mit dem Cloud-Konfigurationspfad übereinstimmen, den Sie beim Erstellen/Bearbeiten einer Community-Site ausgewählt haben.

1. Überprüfen Sie, ob Ihr Kontextpfad aktiviert ist, um Cloud-Dienste darunter zu erstellen.
1. Go to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Wählen Sie den Kontext und bearbeiten Sie die Eigenschaften. Aktivieren Sie Cloud-Konfigurationen, wenn sie noch nicht aktiviert sind.

   ![config-properties](assets/config-propertiespng.png)

1. **Konfiguration des Facebook-Cloud-Dienstes erstellen/bearbeiten** .

   ![fbsocialloginconfig](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Titel]** (*erforderlich*) Geben Sie einen Anzeigentitel ein, der die Facebook-App identifiziert. Es wird empfohlen, denselben Namen zu verwenden, der als *Anzeigename* für die Facebook-App eingegeben wurde.
   * **[!UICONTROL App-ID/API-Schlüssel]** (*erforderlich*) Geben Sie die ***App-ID*** für die Facebook-App ein. Dadurch wird die [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -Instanz identifiziert, die über das Dialogfeld erstellt wurde.
   * **[!UICONTROL App-Geheimer]** (*erforderlich*) Geben Sie den ***App-Geheimen*** für die Facebook-App ein.
   * **[!UICONTROL Benutzer]** erstellen Wenn diese Option aktiviert ist, wird bei der Anmeldung bei einem Facebook-Konto ein AEM-Benutzereintrag erstellt und als Mitglied der ausgewählten Benutzergruppe(n) hinzugefügt.  Die Standardeinstellung ist aktiviert (wird dringend empfohlen).
   * **[!UICONTROL Benutzer-IDs]** maskieren: Lassen Sie die Auswahl aufgehoben.
   * **[!UICONTROL Scope-E-Mail]**: Die E-Mail-ID des Benutzers sollte von Facebook abgerufen werden.
   * **[!UICONTROL Hinzufügen zu Benutzergruppen]** wählen Sie Hinzufügen Benutzergruppe aus, um eine oder mehrere [Mitgliedsgruppen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) für die Community-Site auszuwählen, der Benutzer hinzugefügt werden sollen.
   >[!NOTE]
   >
   >Gruppen können jederzeit hinzugefügt oder entfernt werden. Die Mitgliedschaft bestehender Benutzer wird jedoch nicht beeinträchtigt. Die automatische Mitgliedschaft gilt nur für neue Benutzer, die nach dieser Feldaktualisierung erstellt werden. Wählen Sie für Sites, bei denen anonyme Benutzer deaktiviert sind, Benutzer zu der entsprechenden Community-Mitglieder-Gruppe für diese geschlossene Community-Site hinzuzufügen.

   * Select **[!UICONTROL SAVE]**.
   * **[!UICONTROL Veröffentlichen]**.




Das Ergebnis ist eine [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -Instanz, die keine weitere Änderung erfordert, es sei denn, es werden zusätzliche Gültigkeitsbereiche (Berechtigungen) hinzugefügt. Der Standardbereich ist die Standardberechtigung für die Anmeldung bei Facebook. Wenn Sie zusätzlichen Umfang wünschen, müssen Sie die OSGI-Konfiguration direkt bearbeiten. Wenn Änderungen direkt über das System/die Konsole vorgenommen werden, sollten Sie Ihre Cloud-Service-Konfigurationen nicht über die Touch-Benutzeroberfläche bearbeiten, um ein Überschreiben zu vermeiden.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

Der AEM Communities-Anbieter erweitert die [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -Instanz.

Dieser Anbieter muss bearbeitet werden, um:

* Benutzeraktualisierungen zulassen
* Hinzufügen zusätzlicher Felder [im Anwendungsbereich](#adobe-granite-oauth-application-and-provider)

   * Nicht alle standardmäßig zulässigen Felder sind standardmäßig eingeschlossen.

Wenn eine Bearbeitung erforderlich ist, führen Sie bei jeder AEM-Veröffentlichungsinstanz folgende Schritte durch:

1. Melden Sie sich mit Administratorrechten an.
1. Navigate to the [Web Console](../../help/sites-deploying/configuring-osgi.md). Beispiel: http://localhost:4503/system/console/configMgr.
1. Suchen Sie nach AEM Communities Facebook OAuth Provider.
1. Wählen Sie das Stiftsymbol aus, das zur Bearbeitung geöffnet werden soll.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider-ID]**

      (*Erforderlich*) Der Standardwert ist *soco -facebook*. Bearbeiten Sie nicht.

   * **[!UICONTROL Cloud-Dienstkonfiguration]**

      Der Standardwert ist `/etc/  cloudservices /  facebookconnect`. Bearbeiten Sie nicht.

   * **[!UICONTROL OAuth Provider Service Config]**

      Der Standardwert ist `/apps/social/facebookprovider/config/`. Bearbeiten Sie nicht.

   * **[!UICONTROL Tags aktivieren]**

      Nicht bearbeiten.

   * **[!UICONTROL Benutzerpfad]**

      Speicherort im Repository, an dem Benutzerdaten gespeichert werden. Für eine Community-Site sollte der Pfad der Standard-/Home-/Benutzer-/Community-Pfad sein, um sicherzustellen, dass die Mitglieder das Profil einer anderen Ansicht nutzen können **.

   * **[!UICONTROL Felder aktivieren]**

      Wenn diese Option aktiviert ist, werden die aufgelisteten Felder in der Anforderung an Facebook zur Benutzerauthentifizierung und Informationen angegeben. Die Standardeinstellung ist deaktiviert.

   * **[!UICONTROL Felder]**

      Wenn Felder aktiviert sind, werden beim Aufruf der Facebook-Grafik-API die folgenden Felder eingeschlossen. Die Felder müssen innerhalb des in der Cloud-Dienstkonfiguration definierten Bereichs zulässig sein. Zusätzliche Felder müssen möglicherweise von Facebook genehmigt werden. Verweisen Sie in der Facebook-Dokumentation auf den Abschnitt &quot;Facebook-Anmeldeberechtigungen&quot;. Als Parameter hinzugefügte Standardfelder sind:

      * id
      * name
      * first_name
      * last_name
      * Link
      * locale
      * picture
      * timezone
      * updated_time
      * überprüft
      * email
   Wenn ein Feld hinzugefügt oder geändert wird, aktualisieren Sie die entsprechende Konfiguration des Standard-Synchronisierungs-Handlers, um die Zuordnung zu korrigieren.

   * **[!UICONTROL Benutzer aktualisieren]**

      Wenn diese Option aktiviert ist, werden die Benutzerdaten im Repository bei jeder Anmeldung aktualisiert, um Änderungen am Profil oder weitere angeforderte Daten widerzuspiegeln. Die Option &quot;Standard&quot;ist deaktiviert.


#### Nächste Schritte {#next-steps}

Die nächsten Schritte sind für Facebook und Twitter gleich:

* [Veröffentlichen der Cloud-Dienstkonfigurationen](#publishcloudservices)
* [Aktivieren für eine Community-Site](#enable-social-login)

## Twitter-Anmeldung {#twitter-login}

### Erstellen einer Twitter-App {#create-a-twitter-app}

Zur Aktivierung der Twitter-Anmeldung in sozialen Netzwerken ist eine konfigurierte Twitter-Anwendung erforderlich.

Befolgen Sie die neuesten Anweisungen zum Erstellen einer neuen Twitter-Anwendung unter [https://apps.twitter.com](https://apps.twitter.com/).

Im Allgemeinen:

1. Geben Sie einen *Namen* ein, der Ihre Twitter-Anwendung für die Benutzer Ihrer Website kennzeichnet.
1. Geben Sie eine *Beschreibung* ein.
1. Für *Website* - geben Sie `https://<server>`.
1. Für *Rückruf-URL* geben Sie `https://server`.

   >[!NOTE]
   >
   >Es ist nicht erforderlich, den Anschluss anzugeben.
   >
   >Für die Entwicklung funktioniert https://127.0.0.1/.

1. Nachdem die Anwendung erstellt wurde, suchen Sie den **[!UICONTROL Consumer (API) Key]** und den **[!UICONTROL Consumer (API) Secret]**. Diese Informationen werden zur Konfiguration des [Twitter-Cloud-Dienstes](#createatwittercloudservice)benötigt.

#### Berechtigungen {#permissions}

Im Abschnitt Berechtigungen für Twitter-Anwendungsverwaltung:

* **[!UICONTROL Zugriff]**: Wählen Sie `Read only`.

   * Andere Optionen werden nicht unterstützt

* **[!UICONTROL Zusätzliche Berechtigungen]**: Wählen Sie optional `Request email addresses from users`.

   * Wenn diese Option nicht ausgewählt ist, enthält das Profil des Benutzers in AEM keine E-Mail-Adresse.
   * In den Anweisungen von Twitter werden zusätzliche Schritte beschrieben.

Die einzige REST-Anforderung, die für die Anmeldung in sozialen Netzwerken gestellt wird, ist *[GET Konto/Verification-Anmeldeinformationen](https://dev.twitter.com/rest/reference/get/account/verify_credentials)*.

### Erstellen eines Twitter Connect Cloud-Dienstes {#create-a-twitter-connect-cloud-service}

Die [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -Instanz, instanziiert durch Erstellen einer Cloud-Service-Konfiguration, identifiziert die Twitter-Anwendung und die Mitgliedsgruppe/n, der/denen die neuen Benutzer hinzugefügt werden.

1. Melden Sie sich auf der Autoreninstanz mit Administratorrechten an.
1. Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Cloud-Services]** > **[!UICONTROL Twitter Social-Anmeldekonfiguration]**.
1. Wählen Sie die **[!UICONTROL Kontextpfadkonfiguration]** .

   Der Kontextpfad sollte mit dem Cloud-Konfigurationspfad übereinstimmen, den Sie beim Erstellen/Bearbeiten einer Community-Site ausgewählt haben.

1. Überprüfen Sie, ob Ihr Kontextpfad aktiviert ist, um Cloud-Dienste darunter zu erstellen.
1. Go to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Wählen Sie den Kontext und bearbeiten Sie die Eigenschaften. Aktivieren Sie Cloud-Konfigurationen, wenn sie noch nicht aktiviert sind.

   ![twitterconfigpropng](assets/twitterconfigproppng.png)

1. Konfiguration des Twitter-Cloud-Dienstes erstellen/bearbeiten.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Titel]**

      (*Erforderlich*) Geben Sie einen Anzeigentitel ein, der die Twitter-App identifiziert. Es wird empfohlen, denselben Namen zu verwenden, der als *Anzeigename* für die Twitter-App eingegeben wurde.

   * **[!UICONTROL Verbraucherschlüssel]**

      (*Erforderlich*) Geben Sie den **API-Schlüssel** für die Twitter-App ein. Dadurch wird die [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -Instanz identifiziert, die über das Dialogfeld erstellt wurde.

   * **[!UICONTROL Kundengeheimnis]**

      (*Erforderlich*) Geben Sie den geheimen ***Verbraucher(API)-Schlüssel*** für die Twitter-App ein.

   * **[!UICONTROL Benutzer erstellen]**

      Wenn diese Option aktiviert ist, wird bei der Anmeldung bei einem Twitter-Konto ein AEM-Benutzereintrag erstellt und als Mitglied der ausgewählten Benutzergruppe(n) hinzugefügt. Die Standardeinstellung ist aktiviert (wird dringend empfohlen).

   * **[!UICONTROL Benutzer-IDs verschleiern]**

      Lassen Sie die Auswahl aufgehoben.

   * **[!UICONTROL Zu Benutzergruppen hinzufügen]**

      Wählen Sie Hinzufügen Benutzergruppe aus, um eine oder mehrere [Mitgliedsgruppen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) für die Community-Site auszuwählen, der Benutzer hinzugefügt werden sollen.
   >[!NOTE]
   >
   >Gruppen können jederzeit hinzugefügt oder entfernt werden. Die Mitgliedschaft bestehender Benutzer wird jedoch nicht beeinträchtigt. Die automatische Mitgliedschaft gilt nur für neue Benutzer, die nach dieser Feldaktualisierung erstellt werden. Fügen Sie für Sites, bei denen anonyme Benutzer deaktiviert sind, Benutzer zu der entsprechenden Community-Mitglieder-Gruppe hinzu, die für diese geschlossene Community-Site vorgesehen ist.

1. Wählen Sie **[!UICONTROL SPEICHERN]** und **[!UICONTROL Veröffentlichen]**.

Das Ergebnis ist eine [Adobe Granite OAuth-Anwendungs- und Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -Instanz, die keine weitere Änderung erfordert. Der Standardbereich ist die Standardberechtigung für die Twitter-Anmeldung.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

Die AEM Communities-Konfiguration erweitert die [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -Instanz. Dieser Anbieter muss bearbeitet werden, um Benutzeraktualisierungen zu ermöglichen.

Wenn eine Bearbeitung erforderlich ist, führen Sie bei jeder AEM-Veröffentlichungsinstanz folgende Schritte durch:

1. Melden Sie sich mit Administratorrechten an.
1. Navigate to the [Web Console](../../help/sites-deploying/configuring-osgi.md).

   Beispiel: http://localhost:4503/system/console/configMgr.

1. Suchen Sie nach AEM Communities Twitter OAuth Provider.
1. Wählen Sie das Stiftsymbol aus, das zur Bearbeitung geöffnet werden soll.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider-ID]**
   (*Erforderlich*) Der Standardwert ist *soco -twitter*. Bearbeiten Sie nicht.

   * **[!UICONTROL Cloud-Dienstkonfiguration]**

      The default value is *conf.* Bearbeiten Sie nicht.

   * **[!UICONTROL OAuth Provider Service Config]**

      Der Standardwert ist `/apps/social/twitterprovider/config/`. Bearbeiten Sie nicht.

   * **[!UICONTROL Benutzerpfad]**

      Speicherort im Repository, an dem Benutzerdaten gespeichert werden. Bei einer Community-Site sollte der Pfad der Standardpfad sein, um sicherzustellen, dass die Mitglieder das Profil einer anderen Ansicht ausführen `/home/users/community`.

   * **[!UICONTROL Parameter]** aktivieren bearbeiten nicht
   * **[!UICONTROL URL-Parameter]** bearbeiten nicht
   * **[!UICONTROL Benutzer aktualisieren]**

      Wenn diese Option aktiviert ist, werden die Benutzerdaten im Repository bei jeder Anmeldung aktualisiert, um Änderungen am Profil oder weitere angeforderte Daten widerzuspiegeln. Die Standardeinstellung ist deaktiviert.


#### Nächste Schritte {#next-steps-1}

Die nächsten Schritte sind für Facebook und Twitter gleich:

* [Veröffentlichen der Cloud-Dienstkonfigurationen](#publishcloudservices)
* [Aktivieren für eine Community-Site](#enable-social-login)

## Social-Anmeldung aktivieren {#enable-social-login}

### AEM Communities Sites Console {#aem-communities-sites-console}

Nachdem ein Cloud-Dienst konfiguriert wurde, kann er für die entsprechende Social-Anmeldeeinstellung für eine Community-Site aktiviert werden. Verwenden Sie dazu das Unterbedienfeld [Benutzerverwaltungseinstellungen](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) , während Sie Community-Sites [erstellen](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation) oder [verwalten](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties).

1. Wählen Sie den Kontext für die Site-Konfiguration aus, in dem Sie Ihre Social-Anmeldekonfigurationen gespeichert haben.

1. Legen Sie auf der Registerkarte Allgemein die Cloud-Konfigurationen fest.

   ![managesites_png](assets/managesites_png.png)

1. Aktivieren Sie auf der Registerkarte Einstellungen die Optionen **[!UICONTROL Social-Anmeldung]** und Speichern.

   ![usermgmt_png](assets/usermgmt_png.png)

## Social-Anmeldung testen {#test-social-login}

* Vergewissern Sie sich, dass der [Adobe Granite OAuth Authentication Handler](#adobe-granite-oauth-authentication-handler) für alle Veröffentlichungsinstanzen aktiviert wurde.
* Vergewissern Sie sich, dass die Cloud-Dienste veröffentlicht wurden.
* Vergewissern Sie sich, dass die Community-Site veröffentlicht wurde.
* Starten Sie die veröffentlichte Site in einem Browser.
Beispiel: http://localhost:4503/content/sites/engage/en.html
* Wählen Sie **[!UICONTROL Anmelden]**.
* Wählen Sie entweder **[!UICONTROL Anmelden bei Facebook]** oder **[!UICONTROL Anmelden bei Twitter]**.
* Wenn Sie sich noch nicht bei Facebook oder Twitter angemeldet haben, melden Sie sich mit den entsprechenden Anmeldeinformationen an.
* Es kann erforderlich sein, Berechtigungen zu gewähren, je nach dem von der Facebook- oder Twitter-App angezeigten Dialogfeld.
* Beachten Sie, dass die Symbolleiste oben auf der Seite aktualisiert wird, um die erfolgreiche Anmeldung widerzuspiegeln.
* Wählen Sie **[!UICONTROL Profil]**: Auf der Seite &quot;Profil&quot;werden das Avatarbild, der Vorname und der Nachname des Benutzers angezeigt. Außerdem werden die Informationen aus dem Facebook- oder Twitter-Profil entsprechend den zulässigen Feldern/Parametern angezeigt.

## AEM Platform OAuth Configurations {#aem-platform-oauth-configurations}

### Adobe Granite OAuth Authentication Handler {#adobe-granite-oauth-authentication-handler}

Die Funktion `Adobe Granite OAuth Authentication Handler` ist nicht standardmäßig aktiviert und ***muss in allen AEM-Veröffentlichungsinstanzen aktiviert sein.***

Um den Authentifizierungshandler bei der Veröffentlichung zu aktivieren, öffnen Sie einfach die OSGi-Konfiguration und speichern Sie sie:

* Melden Sie sich mit Administratorrechten an.
* Navigate to the [Web Console](../../help/sites-deploying/configuring-osgi.md).
Beispiel: http://localhost:4503/system/console/configMgr
* Suchen Sie `Adobe Granite OAuth Authentication Handler`.
* Wählen Sie diese Option, um die Konfiguration zur Bearbeitung zu öffnen.
* Wählen Sie **[!UICONTROL Speichern]** aus.

![chlimage_1-489](assets/chlimage_1-489.png)

>[!CAUTION]
>
>Verwechseln Sie den Authentifizierungshandler nicht mit einer Facebook- oder Twitter-Instanz von *Adobe Granite OAuth Application and Provider*.


![chlimage_1-490](assets/chlimage_1-490.png)

### Adobe Granite OAuth Application and Provider {#adobe-granite-oauth-application-and-provider}

Wenn ein Cloud-Dienst für Facebook oder Twitter erstellt wird, `Adobe Granite OAuth Authentication Handler` wird eine Instanz von erstellt.

So suchen Sie die erstellte Instanz für eine Facebook- oder Twitter-App:

1. Melden Sie sich mit Administratorrechten an.
1. Navigate to the [Web Console](../../help/sites-deploying/configuring-osgi.md).

   Beispiel: http://localhost:4503/system/console/configMgr.

1. Suchen Sie Adobe Granite OAuth Application and Provider.

   * Suchen Sie die Instanz, in der die **[!UICONTROL Client-ID]** mit der **[!UICONTROL App-ID]**&#x200B;übereinstimmt.

      ![chlimage_1-491](assets/chlimage_1-491.png)

      Mit Ausnahme der folgenden Eigenschaften bleiben die anderen Eigenschaften der Konfiguration unverändert:

   * **[!UICONTROL Konfigurations-ID]**

      (*Erforderlich*) OAuth-Konfigurations-IDs müssen eindeutig sein. Automatisch generiert, wenn der Cloud-Dienst erstellt wird.

   * **[!UICONTROL Client-ID]**

      (*Erforderlich*) Die Anwendungs-ID, die beim Erstellen des Cloud-Dienstes angegeben wurde.

   * **[!UICONTROL Client-Geheimnis]**

      (*Erforderlich*) Der Anwendungs-Geheimcode, der beim Erstellen des Cloud-Dienstes angegeben wurde.

   * **[!UICONTROL Umfang]**

      (*Optional*) Der Anbieter kann weitere Möglichkeiten für das Erlaubte anfordern. Der Standardbereich umfasst die Berechtigungen, die für die Bereitstellung von Social-Authentifizierung und Profil-Daten erforderlich sind.

   * **[!UICONTROL Anbieter-ID]**

      (*Erforderlich*) Die Anbieter-ID für AEM Communities wird festgelegt, wenn der Cloud-Dienst erstellt wurde. Bearbeiten Sie nicht. Bei Facebook Connect ist der Wert *soco -facebook*. Bei Twitter Connect ist der Wert *soco -twitter*.

   * **[!UICONTROL Gruppen]**

      (*Empfohlen*) Eine oder mehrere Mitgliedsgruppen, denen erstellte Benutzer hinzugefügt werden. Für AEM Communities wird empfohlen, die Mitgliedsgruppe für die Community-Site Liste.

   * **[!UICONTROL Rückruf-URL]**

      (*Optional*) URL, die mit den OAuth-Anbietern konfiguriert wurde, um den Client zurück zu leiten. Verwenden Sie eine relative URL, um den Host der ursprünglichen Anforderung zu verwenden. Lassen Sie leer, um stattdessen die ursprünglich angeforderte URL zu verwenden. Das Suffix &quot;/callback/j_security_check&quot;wird automatisch an diese URL angehängt.
   >[!NOTE]
   >
   >Die Domäne für den Rückruf muss beim Anbieter (Facebook oder Twitter) registriert sein.

Für jede OAuth-Authentifizierungshandler-Konfiguration gibt es zwei zusätzliche Konfigurationen, die in der Instanz erstellt werden:

* Apache Jackrabbit Oak Default Sync Handler (org.apache.jackrabbit.oak.security.authentication.external.impl.DefaultSyncHandler) - Es sind keine Änderungen erforderlich, Sie können jedoch die Zuordnungen der Benutzerfelder ansehen, wie Facebook-Profile einem CQ-Benutzerfeldknoten zugeordnet werden. Beachten Sie auch, dass &quot;Synchronisierungs-Handler-Name&quot;mit der Konfigurations-ID des OAuth-Anbieters übereinstimmt.
* Apache Jackrabbit Oak External Login Module (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory) - Es sind dort keine Änderungen erforderlich, Sie können jedoch bemerken, dass &quot;Identity Provider Name&quot;und &quot;Sync Handler Name&quot;identisch sind und auf die entsprechenden Konfigurationen von OAuth und Synchronisierungs-Handler verweisen.

For more information, see [Authentication with Apache Oak External Login Module](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).

## OAuth Benutzerübergreifende Leistung {#oauth-user-traversal-performance}

Bei Community-Sites, auf denen sich Hunderttausende von Benutzern mit ihrer Facebook- oder Twitter-Anmeldung registrieren, kann die allgemeine Performance der Abfrage, die ausgeführt wird, wenn ein Site-Besucher seine Social-Anmeldung verwendet, durch Hinzufügen des folgenden Oak-Index verbessert werden.

Wenn in den Protokollen übergreifende Warnungen angezeigt werden, wird empfohlen, diesen Index hinzuzufügen.

Auf einer Autoreninstanz, die mit Administratorrechten angemeldet ist:

1. Aus globaler Navigation: Wählen Sie **Tools,[CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
1. Erstellen Sie einen Index mit dem Namen ntBaseLucene-oauth aus einer Kopie von ntBaseLucene:

   * under node `/oak:index`
   * Knoten auswählen `ntBaseLucene`
   * Auswahl **[!UICONTROL kopieren]**
   * Wählen Sie nun eine der folgenden Optionen aus `/oak:index`
   * Einfügen **[!UICONTROL auswählen]**
   * Kopie von ntBaseLucene umbenennen in `ntBaseLucene-oauth`

1. Ändern Sie die Eigenschaften von node ntBaseLucene-oauth:

   * **[!UICONTROL indexPath]**: `/oak:index/ntBaseLucene-oauth`
   * **[!UICONTROL name]**: `oauthid-123****`
   * **[!UICONTROL reindex]**: `true`
   * **[!UICONTROL reindexCount]**: `1`

1. Unter Knoten /oak:index/ntBaseLucene-oauth/indexRules/nt:base/properties:

   * Löschen Sie alle untergeordneten Knoten mit Ausnahme von cqTags.
   * Umbenennen von cqTags in `oauthid-123****`
   * Eigenschaften des Knotens ändern `oauthid-123****`

      * **[!UICONTROL name]**: `oauthid-123****`
   * Select **[!UICONTROL Save All]**.


* Ersetzen Sie für den **Namen** `oauthid-123`123 *durch die Facebook-* App-ID ***oder den Twitter-*** Consumer-Schlüssel ***(API), der den Wert der*** Client-IDin der Konfiguration von Adobe **** [](social-login.md#adobe-granite-oauth-application-and-provider) Granite OAuth Application und Provider darstellt.

   ![chlimage_1-492](assets/chlimage_1-492.png)

Weitere Informationen und Tools finden Sie unter [Oak-Abfragen und Indizierung](../../help/sites-deploying/queries-and-indexing.md).

## Dispatcher-Konfiguration {#dispatcher-configuration}

Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md).
