---
title: Anmeldung über Social Media mit Facebook und Twitter
description: Mit der Anmeldung in Social können sich Besucher der Site mit ihrem Facebook- oder Twitter-Konto anmelden.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: aed9247c-eb81-470c-9fa4-a98c3df2dcaa
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2672'
ht-degree: 1%

---

# Anmeldung über Social Media mit Facebook und Twitter {#social-login-with-facebook-and-twitter}

Die Anmeldung in Social bietet die Möglichkeit, einem Site-Besucher die Möglichkeit zu geben, sich mit seinem Facebook- oder Twitter-Konto anzumelden. Daher, einschließlich zulässiger Facebook- oder Twitter-Daten in ihr AEM Mitgliederprofil.

![socialloginweretail](assets/socialloginweretail.png)

## Social-Anmeldeübersicht {#social-login-overview}

Um die Anmeldung über soziale Netzwerke einzubeziehen, ist es *erforderlich*, benutzerdefinierte Facebook- und Twitter-Anwendungen zu erstellen.

Während das Beispiel für &quot;We-Retail&quot;Beispiel-Facebook- und Twitter-Apps und Cloud-Services bereitstellt, sind diese nicht auf einer [Produktions-Website](../../help/sites-administering/production-ready.md) verfügbar.

Die erforderlichen Schritte sind:

1. [Aktivieren Sie die OAuth-Authentifizierung](#adobe-granite-oauth-authentication-handler) für alle AEM Veröffentlichungsinstanzen.

   Wenn OAuth nicht aktiviert ist, schlagen die Anmeldeversuche fehl.

1. **Erstellen Sie** eine Social-App und einen Cloud-Service.

   * So unterstützen Sie die Anmeldung mit Facebook:

      * Erstellen Sie eine [Facebook-App](#create-a-facebook-app).
      * Erstellen und veröffentlichen Sie einen [Facebook Connect-Cloud-Dienst](#create-a-facebook-connect-cloud-service).

   * So unterstützen Sie die Anmeldung mit Twitter:

      * Erstellen Sie eine [Twitter-App](#create-a-twitter-app).
      * Erstellen und veröffentlichen Sie einen [Twitter Connect-Cloud-Service](#create-a-twitter-connect-cloud-service).

1. [**Aktivieren Sie** Social Login](#enable-social-login) für eine Community-Site.

Es gibt zwei grundlegende Konzepte:

1. **Umfang** (Berechtigungen) gibt die Daten an, die die App anfordern darf.

   * Die Instanzen Facebook und Twitter [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) beinhalten standardmäßig die grundlegenden App-Berechtigungen in ihren Geltungsbereich.

1. **Felder** (Parameter) gibt die tatsächlichen Daten an, die mithilfe von URL-Parametern angefordert werden.

   * Diese Felder werden unter [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) und [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider) angegeben.
   * Die Standardfelder reichen für die meisten Anwendungsfälle aus, können jedoch geändert werden.

## Facebook-Anmeldung {#facebook-login}

### Facebook API-Version {#facebook-api-version}

Die Anmeldung über Social Media und das Facebook-Beispiel für We-Retail wurden entwickelt, als die Facebook Graph-API Version 1.0 war.
Ab AEM 6.4 wurde die GA- und AEM 6.3 SP1-Social-Anmeldung aktualisiert, um mit der neueren Facebook Graph API 2.5-Version zu funktionieren.

>[!NOTE]
>
>Wenn bei älteren AEM eine Ausnahme in den Protokollen **Kann kein Token aus diesem** extrahieren, aktualisieren Sie für diese AEM Version auf die neueste CFP.

Informationen zur Version der Facebook Graph-API finden Sie in der [Facebook-API-Änderung](https://developers.facebook.com/docs/apps/changelog).

### Erstellen einer Facebook App {#create-a-facebook-app}

Eine ordnungsgemäß konfigurierte Facebook-Anwendung ist erforderlich, um die Anmeldung in Facebook Social zu aktivieren.

Um eine Facebook-Anwendung zu erstellen, befolgen Sie die Anweisungen von Facebook unter [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/). Änderungen an ihren Anweisungen werden in den folgenden Informationen nicht berücksichtigt.

Im Allgemeinen ab Facebook API v2.7:

* *Neue Facebook-App hinzufügen*
   * Wählen Sie für *Plattform* Website:
      * Geben Sie für *Site-URL* `  https://<server>:<port>.` ein.
      * Geben Sie für &quot;*Anzeigename*&quot;einen Titel ein, der als Titel des Facebook Connect-Dienstes verwendet werden soll.
      * Für *Kategorie* wird empfohlen, *Apps für Seiten* zu wählen, kann jedoch alles sein.
      * *Produkt hinzufügen: Facebook-Anmeldung*
      * Geben Sie für *gültige OAuth-Umleitungs-URIs* `  https://<server>:<port>.` ein.

>[!NOTE]
>
>Für die Entwicklung funktioniert http://localhost:4503.

Suchen Sie nach den Einstellungen **[!UICONTROL App-ID]** und **[!UICONTROL App-Geheimnis]** , nachdem die Anwendung erstellt wurde. Diese Informationen sind für die Konfiguration des [Facebook-Cloud-Service](#createafacebookcloudservice) erforderlich.

### Erstellen eines Facebook Connect-Cloud Service {#create-a-facebook-connect-cloud-service}

Die Instanz [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) , die durch Erstellen einer Cloud Service-Konfiguration instanziiert wird, identifiziert die Facebook-Anwendung und die Mitgliedsgruppe(n), zu denen die neuen Benutzer hinzugefügt werden.

1. Melden Sie sich auf der AEM Autoreninstanz mit Administratorrechten an.
1. Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Anmeldekonfiguration für Facebook Social]** aus.
1. Wählen Sie die Konfiguration **[!UICONTROL Kontextpfad]** aus.

   **[!UICONTROL Kontextpfad]** sollte dem Cloud-Konfigurationspfad entsprechen, den Sie beim Erstellen/Bearbeiten einer Community-Site ausgewählt haben.

1. Überprüfen Sie, ob Ihr Kontextpfad aktiviert ist, um Cloud-Services darunter zu erstellen.
1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**. Wählen Sie Ihren Kontext aus und bearbeiten Sie Eigenschaften. Aktivieren Sie Cloud-Konfigurationen , falls noch nicht aktiviert.

   ![config-propertiespng](assets/config-propertiespng.png)

   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser](/help/sites-administering/configurations.md).

1. **Erstellen/Bearbeiten** Facebook-Cloud-Service-Konfiguration.

   ![fbsocialloginconfig](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Titel]** (*Erforderlich*) Geben Sie einen Anzeigetitel ein, der die Facebook-App identifiziert. Verwenden Sie denselben Namen, der als *Anzeigenamen* für die Facebook-App eingegeben wurde.
   * **[!UICONTROL App-ID/API-Schlüssel]** (*Erforderlich*) Geben Sie die ***App-ID*** für die Facebook-App ein. Dadurch wird die im Dialogfeld erstellte [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider)-Instanz identifiziert.
   * **[!UICONTROL App-Geheimnis]** (*Erforderlich*) Geben Sie den ***App-Geheimnis*** für die Facebook-App ein.
   * **[!UICONTROL Benutzer erstellen]** Wenn diese Option aktiviert ist, wird durch die Anmeldung bei einem Facebook-Konto ein AEM Benutzereintrag erstellt und dieser als Mitglied der ausgewählten Benutzergruppe(n) hinzugefügt.  Die Standardeinstellung ist aktiviert (dringend empfohlen).
   * **[!UICONTROL Benutzer-IDs maskieren]**: Lassen Sie die Auswahl deaktiviert.
   * **[!UICONTROL Umfang-E-Mail]**: Die E-Mail-ID des Benutzers sollte aus Facebook abgerufen werden.
   * **[!UICONTROL Zu Benutzergruppen hinzufügen]** Wählen Sie Benutzergruppe hinzufügen aus, um eine oder mehrere [Mitgliedergruppen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) für die Community-Site auszuwählen, der Benutzer hinzugefügt werden sollen.

   >[!NOTE]
   >
   >Gruppen können jederzeit hinzugefügt oder entfernt werden. Die Mitgliedschaften bestehender Benutzer sind jedoch nicht betroffen. Die automatische Mitgliedschaft gilt nur für neue Benutzer, die nach der Aktualisierung dieses Felds erstellt werden. Wählen Sie für Sites, bei denen anonyme Benutzer deaktiviert sind, Benutzer zu der entsprechenden Community-Mitgliedergruppe für diese geschlossene Community-Site hinzufügen.

   * Wählen Sie **[!UICONTROL SPEICHERN]** aus.
   * **[!UICONTROL Publish]**.

Das Ergebnis ist eine [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -Instanz, die keine weitere Änderung erfordert, es sei denn, es werden zusätzliche Bereiche (Berechtigungen) hinzugefügt. Der Standardbereich sind die Standardberechtigungen für die Facebook-Anmeldung. Wenn zusätzlicher Umfang gewünscht wird, muss die OSGi-Konfiguration direkt bearbeitet werden. Wenn Änderungen direkt über System/Konsole vorgenommen werden, sollten Sie die Cloud Service-Konfigurationen nicht über die Touch-optimierte Benutzeroberfläche bearbeiten, um eine Überschrift zu vermeiden.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

Der AEM Communities-Provider erweitert die [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -Instanz.

Dieser Provider muss bearbeitet werden, um:

* Benutzeraktualisierungen zulassen
* Zusätzliche Felder [im Bereich](#adobe-granite-oauth-application-and-provider) hinzufügen

   * Standardmäßig sind nicht alle Felder eingeschlossen, die zulässig sind.

Wenn die Bearbeitung in jeder AEM Veröffentlichungsinstanz erforderlich ist:

1. Melden Sie sich mit Administratorrechten an.
1. Navigieren Sie zur [Web-Konsole](../../help/sites-deploying/configuring-osgi.md). Beispiel: http://localhost:4503/system/console/configMgr.
1. Suchen Sie nach AEM Communities Facebook OAuth Provider.
1. Wählen Sie das Stiftsymbol aus, um es zur Bearbeitung zu öffnen.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider ID]**

     (*Erforderlich*) Der Standardwert ist *soco -facebook*. Bearbeiten Sie nicht.

   * **[!UICONTROL Cloud Service-Konfiguration]**

     Der Standardwert ist `/etc/  cloudservices /  facebookconnect`. Bearbeiten Sie nicht.

   * **[!UICONTROL OAuth Provider-Dienstkonfiguration]**

     Der Standardwert ist `/apps/social/facebookprovider/config/`. Bearbeiten Sie nicht.

   * **[!UICONTROL Aktivieren von Tags]**

     Nicht bearbeiten.

   * **[!UICONTROL Benutzerpfad]**

     Speicherort im Repository, an dem Benutzerdaten gespeichert werden. Für eine Community-Site sollte der Pfad der standardmäßige Pfad &quot;*/home/users/community*&quot;sein, um sicherzustellen, dass Mitglieder das Profil einer anderen Person anzeigen können.

   * **[!UICONTROL Felder aktivieren]**

     Wenn diese Option aktiviert ist, werden die aufgeführten Felder in der Anforderung an Facebook zur Benutzerauthentifizierung und -informationen angegeben. Die Standardeinstellung ist deaktiviert.

   * **[!UICONTROL Felder]**

     Wenn Felder aktiviert sind, werden beim Aufrufen der Facebook Graph-API die folgenden Felder eingeschlossen. Die Felder müssen innerhalb des in der Cloud Service-Konfiguration definierten Bereichs zulässig sein. Zusätzliche Felder erfordern möglicherweise eine Genehmigung durch Facebook. Weitere Informationen finden Sie im Abschnitt Facebook-Anmeldeberechtigungen in der Facebook-Dokumentation. Als Parameter hinzugefügte Standardfelder sind:

      * id
      * name
      * first_name
      * last_name
      * Verknüpfung
      * locale
      * picture
      * timezone
      * updated_time
      * verifiziert
      * email

   Wenn ein Feld hinzugefügt oder geändert wird, aktualisieren Sie die entsprechende Standardsynchronisierungshandler-Konfiguration, um die Zuordnung zu korrigieren.

   * **[!UICONTROL Benutzer aktualisieren]**

     Wenn diese Option aktiviert ist, werden die Benutzerdaten im Repository bei jeder Anmeldung aktualisiert, um Profiländerungen oder zusätzliche angeforderte Daten widerzuspiegeln. Die Option Standard ist deaktiviert.

#### Nächste Schritte {#next-steps}

Die nächsten Schritte sind für Facebook und Twitter gleich:

* [Publish der Cloud-Dienstkonfigurationen](#publishcloudservices)
* [Aktivieren für eine Community-Site](#enable-social-login)

## Twitter Login {#twitter-login}

### Twitter App erstellen {#create-a-twitter-app}

Eine konfigurierte Twitter-Anwendung ist erforderlich, um die Anmeldung über Twitter Social zu aktivieren.

Befolgen Sie die neuesten Anweisungen zum Erstellen einer Twitter-Anwendung unter [https://apps.twitter.com](https://apps.twitter.com/).

Allgemein:

1. Geben Sie einen *Namen* ein, der Ihre Twitter-App für die Benutzer Ihrer Website kennzeichnet.
1. Geben Sie eine *Beschreibung* ein.
1. Geben Sie für *website* den Wert `https://<server>` ein.
1. Geben Sie für *Callback-URL* den Wert `https://server` ein.

   >[!NOTE]
   >
   >Es ist nicht erforderlich, den Port anzugeben.
   >
   >Für die Entwicklung funktioniert https://127.0.0.1/.

1. Suchen Sie nach der Erstellung der Anwendung den Schlüssel **[!UICONTROL Verbraucher (API)]** und den geheimen Schlüssel **[!UICONTROL Verbraucher (API)]**. Diese Informationen sind für die Konfiguration des [Twitter-Cloud-Service](#createatwittercloudservice) erforderlich.

#### Berechtigungen {#permissions}

Im Abschnitt Berechtigungen der Twitter-Anwendungsverwaltung:

* **[!UICONTROL Zugriff]**: Wählen Sie `Read only` aus.

   * Andere Optionen werden nicht unterstützt

* **[!UICONTROL Zusätzliche Berechtigungen]**: Wählen Sie optional `Request email addresses from users` aus.

   * Wenn diese Option nicht ausgewählt ist, enthält das Benutzerprofil in AEM keine E-Mail-Adresse.
   * In den Anweisungen unter Twitter werden zusätzliche Schritte beschrieben.

Die einzige REST-Anfrage, die für die Anmeldung über soziale Netzwerke gestellt wird, lautet *[Anmeldedaten für das GET/die Überprüfung](https://dev.twitter.com/rest/reference/get/account/verify_credentials)*.

### Erstellen eines Twitter Connect-Cloud Service {#create-a-twitter-connect-cloud-service}

Die Instanz [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) , die durch Erstellen einer Cloud Service-Konfiguration instanziiert wird, identifiziert die Twitter-Anwendung und die Mitgliedergruppe(n), zu denen die neuen Benutzer hinzugefügt werden.

1. Melden Sie sich auf der Autoreninstanz mit Administratorrechten an.
1. Wählen Sie in der globalen Navigation **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Twitter Social-Anmeldekonfiguration]** aus.
1. Wählen Sie die Konfiguration **[!UICONTROL Kontextpfad]** aus.

   Der Kontextpfad sollte mit dem Cloud-Konfigurationspfad übereinstimmen, den Sie beim Erstellen/Bearbeiten einer Community-Site ausgewählt haben.

1. Überprüfen Sie, ob Ihr Kontextpfad aktiviert ist, um Cloud-Services darunter zu erstellen.
1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Allgemein]** > **[!UICONTROL Konfigurations-Browser]**. Wählen Sie Ihren Kontext aus und bearbeiten Sie Eigenschaften. Aktivieren Sie Cloud-Konfigurationen , falls noch nicht aktiviert.

   ![twitterconfigprop](assets/twitterconfigproppng.png)

   * Weitere Informationen finden Sie in der Dokumentation zum [Konfigurations-Browser](/help/sites-administering/configurations.md).

1. Erstellen/Bearbeiten Sie die Cloud-Service-Konfiguration für Twitter.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Titel]**

     (*Erforderlich*) Geben Sie einen Anzeigetitel ein, der die Twitter App angibt. Verwenden Sie denselben Namen, der als *Anzeigenamen* für die Twitter-App eingegeben wurde.

   * **[!UICONTROL Consumer Key]**

     (*Erforderlich*) Geben Sie den **Consumer (API) Key** für die Twitter-App ein. Dadurch wird die im Dialogfeld erstellte [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider)-Instanz identifiziert.

   * **[!UICONTROL Consumer Secret]**

     (*Erforderlich*) Geben Sie den geheimen ***Verbraucher(API)-Schlüssel*** für die Twitter App ein.

   * **[!UICONTROL Benutzer erstellen]**

     Wenn diese Option aktiviert ist, wird durch die Anmeldung mit einem Twitter-Konto ein AEM Benutzereintrag erstellt und als Mitglied zu den ausgewählten Benutzergruppen hinzugefügt. Die Standardeinstellung ist aktiviert (dringend empfohlen).

   * **[!UICONTROL Benutzer-IDs maskieren]**

     Lassen Sie die Auswahl aufgehoben.

   * **[!UICONTROL Zu Benutzergruppen hinzufügen]**

     Wählen Sie Benutzergruppe hinzufügen aus, um eine oder mehrere [Mitgliedergruppen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) für die Community-Site auszuwählen, zu der Benutzer hinzugefügt werden sollen.

   >[!NOTE]
   >
   >Gruppen können jederzeit hinzugefügt oder entfernt werden. Die Mitgliedschaften bestehender Benutzer sind jedoch nicht betroffen. Die automatische Mitgliedschaft gilt nur für neue Benutzer, die nach der Aktualisierung dieses Felds erstellt werden. Fügen Sie für Sites, bei denen anonyme Benutzer deaktiviert sind, Benutzer der entsprechenden Community-Mitglieder-Gruppe hinzu, die für diese geschlossene Community-Site vorgesehen ist.
   >

1. Wählen Sie **[!UICONTROL SAVE]** und **[!UICONTROL Publish]** aus.

Das Ergebnis ist eine [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -Instanz, die keine weiteren Änderungen erfordert. Der Standardbereich sind die Standardberechtigungen für die Twitter-Anmeldung.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

Die AEM Communities-Konfiguration erweitert die [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -Instanz. Dieser Provider muss bearbeitet werden, um Benutzeraktualisierungen zu ermöglichen.

Wenn die Bearbeitung in jeder AEM Veröffentlichungsinstanz erforderlich ist:

1. Melden Sie sich mit Administratorrechten an.
1. Navigieren Sie zur [Web-Konsole](../../help/sites-deploying/configuring-osgi.md).

   Beispiel: http://localhost:4503/system/console/configMgr.

1. Suchen Sie nach AEM Communities Twitter OAuth Provider.
1. Wählen Sie das Stiftsymbol aus, um es zur Bearbeitung zu öffnen.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider ID]**

   (*Erforderlich*) Der Standardwert ist *soco -twitter*. Bearbeiten Sie nicht.

   * **[!UICONTROL Cloud Service-Konfiguration]**

     Der Standardwert ist *conf.* Nicht bearbeiten.

   * **[!UICONTROL OAuth Provider-Dienstkonfiguration]**

     Der Standardwert ist `/apps/social/twitterprovider/config/`. Bearbeiten Sie nicht.

   * **[!UICONTROL Benutzerpfad]**

     Speicherort im Repository, an dem Benutzerdaten gespeichert werden. Für eine Community-Site sollte der Pfad der standardmäßige `/home/users/community` sein, um sicherzustellen, dass Mitglieder das Profil einer anderen Person anzeigen können.

   * **[!UICONTROL Parameter aktivieren]** - nicht bearbeiten
   * **[!UICONTROL URL-Parameter]** - Nicht bearbeiten
   * **[!UICONTROL Benutzer aktualisieren]**

     Wenn diese Option aktiviert ist, werden die Benutzerdaten im Repository bei jeder Anmeldung aktualisiert, um Profiländerungen oder zusätzliche angeforderte Daten widerzuspiegeln. Die Standardeinstellung ist deaktiviert.

#### Nächste Schritte {#next-steps-1}

Die nächsten Schritte sind für Facebook und Twitter gleich:

* [Publish der Cloud-Dienstkonfigurationen](#publishcloudservices)
* [Aktivieren für eine Community-Site](#enable-social-login)

## Social-Anmeldung aktivieren {#enable-social-login}

### AEM Communities Sites-Konsole {#aem-communities-sites-console}

Sobald ein Cloud-Service konfiguriert ist, kann er für die entsprechende Social-Anmeldeeinstellung für eine Community-Site aktiviert werden. Verwenden Sie dazu das Unterbedienfeld [Benutzerverwaltung](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) Einstellungen während der Community-Site-Erstellung [3} oder [Verwaltung](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties).](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation)

1. Wählen Sie den Site-Konfigurationskontext aus, in dem Sie Ihre Social-Anmeldekonfigurationen gespeichert haben.

1. Legen Sie auf der Registerkarte Allgemein Cloud-Konfigurationen fest.

   ![managesites_png](assets/managesites_png.png)

1. Aktivieren Sie auf der Registerkarte &quot;Einstellungen&quot;die Optionen **[!UICONTROL Social-Anmeldungen]** und Speichern.

   ![usermgmt_png](assets/usermgmt_png.png)

## Social-Anmeldung testen {#test-social-login}

* Stellen Sie sicher, dass [Adobe Granite OAuth Authentication Handler](#adobe-granite-oauth-authentication-handler) für alle Veröffentlichungsinstanzen aktiviert wurde.
* Stellen Sie sicher, dass die Cloud-Services veröffentlicht wurden.
* Stellen Sie sicher, dass die Community-Site veröffentlicht wurde.
* Starten Sie die veröffentlichte Site in einem Browser.
Beispiel: http://localhost:4503/content/sites/engage/en.html
* Wählen Sie **[!UICONTROL Anmelden]** aus.
* Wählen Sie entweder **[!UICONTROL Mit Facebook anmelden]** oder **[!UICONTROL Anmelden mit Twitter]** aus.
* Wenn Sie noch nicht bei Facebook oder Twitter angemeldet sind, melden Sie sich mit den entsprechenden Anmeldeinformationen an.
* Abhängig vom Dialogfeld, das von der Facebook- oder Twitter-App angezeigt wird, kann es erforderlich sein, Berechtigungen zu erteilen.
* Beachten Sie, dass die Symbolleiste oben auf der Seite aktualisiert wird, um die erfolgreiche Anmeldung widerzuspiegeln.
* Wählen Sie **[!UICONTROL Profil]** aus: Auf der Profilseite werden das Avatarbild, der Vorname und der Nachname des Benutzers angezeigt. Außerdem werden die Informationen aus dem Facebook- oder Twitter-Profil entsprechend den zulässigen Feldern/Parametern angezeigt.

## OAuth-Konfigurationen AEM Platform {#aem-platform-oauth-configurations}

### Adobe Granite OAuth Authentication Handler {#adobe-granite-oauth-authentication-handler}

`Adobe Granite OAuth Authentication Handler` ist standardmäßig nicht aktiviert und ***muss in allen AEM Veröffentlichungsinstanzen aktiviert sein.***

Um den Authentifizierungs-Handler bei der Veröffentlichung zu aktivieren, öffnen Sie einfach die OSGi-Konfiguration und speichern Sie sie:

* Melden Sie sich mit Administratorrechten an.
* Navigieren Sie zur [Web-Konsole](../../help/sites-deploying/configuring-osgi.md).
Beispiel: http://localhost:4503/system/console/configMgr
* Suchen Sie `Adobe Granite OAuth Authentication Handler`.
* Wählen Sie diese Option aus, um die Konfiguration zur Bearbeitung zu öffnen.
* Wählen Sie **[!UICONTROL Speichern]** aus.

![graniteoauth](assets/graniteoauth.png)

>[!CAUTION]
>
>Verwechseln Sie den Authentifizierungs-Handler nicht mit einer Facebook- oder Twitter-Instanz von *Adobe Granite OAuth Application and Provider*.

![graniteoauth1](assets/graniteoauth1.png)

### Adobe Granite OAuth Application and Provider {#adobe-granite-oauth-application-and-provider}

Wenn ein Cloud-Dienst für Facebook oder Twitter erstellt wird, wird eine Instanz von `Adobe Granite OAuth Authentication Handler` erstellt.

So suchen Sie die erstellte Instanz für eine Facebook- oder Twitter-App:

1. Melden Sie sich mit Administratorrechten an.
1. Navigieren Sie zur [Web-Konsole](../../help/sites-deploying/configuring-osgi.md).

   Beispiel: http://localhost:4503/system/console/configMgr.

1. Suchen Sie Adobe Granite OAuth Application und Provider.

   * Suchen Sie die Instanz, in der **[!UICONTROL Client-ID]** mit der **[!UICONTROL App-ID]** übereinstimmt.

     ![graniteoauth2](assets/graniteoauth2.png)

     Mit Ausnahme der folgenden Eigenschaften bleiben die anderen Eigenschaften der Konfiguration unverändert:

   * **[!UICONTROL Konfigurations-ID]**

     (*Erforderlich*) OAuth-Konfigurations-IDs müssen eindeutig sein. Wird automatisch generiert, wenn der Cloud-Service erstellt wird.

   * **[!UICONTROL Client-ID]**

     (*Erforderlich*) Die bei der Erstellung des Cloud-Dienstes angegebene Anwendungs-ID.

   * **[!UICONTROL Client-Geheimnis]**

     (*Erforderlich*) Das Anwendungsgeheimnis, das beim Erstellen des Cloud-Dienstes angegeben wurde.

   * **[!UICONTROL Umfang]**

     (*Optional*) Der Anbieter kann zusätzliche Bereiche anfordern, die zulässig sind. Der Standardbereich umfasst die Berechtigungen, die für die Bereitstellung von Social-Authentifizierung und Profildaten erforderlich sind.

   * **[!UICONTROL Anbieter-ID]**

     (*Erforderlich*) Die Anbieter-ID für AEM Communities wird bei der Erstellung des Cloud-Service festgelegt. Bearbeiten Sie nicht. Für Facebook Connect ist der Wert *soco -facebook*. Für Twitter Connect ist der Wert *soco -twitter*.

   * **[!UICONTROL Gruppen]**

     (*Empfohlen*) Eine oder mehrere Mitgliedergruppen, denen erstellte Benutzer hinzugefügt werden. Für AEM Communities wird empfohlen, die Mitgliedergruppe für die Community-Site aufzulisten.

   * **[!UICONTROL Callback-URL]**

     (*Optional*) URL, die mit den OAuth-Anbietern konfiguriert wurde, um den Client zurück zu leiten. Verwenden Sie eine relative URL, um den Host der ursprünglichen Anforderung zu verwenden. Lassen Sie das Feld leer, um stattdessen die ursprünglich angeforderte URL zu verwenden. Das Suffix &quot;/callback/j_security_check&quot;wird automatisch an diese URL angehängt.

   >[!NOTE]
   >
   >Die Domäne für den Rückruf muss beim Provider (Facebook oder Twitter) registriert sein.

Für jede OAuth-Authentifizierungs-Handler-Konfiguration werden in der Instanz zwei zusätzliche Konfigurationen erstellt:

* Apache Jackrabbit Oak Default Sync Handler (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler) - Dort sind keine Änderungen erforderlich. Sie können sich jedoch die Benutzerfeldzuordnungen ansehen, wie Facebook-Felder einem CQ-Benutzerprofilknoten zugeordnet werden. Beachten Sie außerdem, dass &quot;Sync Handler Name&quot;mit der Konfigurations-ID der OAuth-Provider-Konfiguration übereinstimmt.
* Apache Jackrabbit Oak External Login Module (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory) - Dort sind keine Änderungen erforderlich, Sie werden jedoch feststellen, dass &quot;Identity Provider Name&quot;und &quot;Sync Handler Name&quot;identisch sind und auf die entsprechenden OAuth- bzw. Synchronisations-Handler-Konfigurationen verweisen.

Weitere Informationen finden Sie unter [Authentifizierung mit dem externen Apache Oak-Anmeldemodul](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).

## OAuth-Benutzerübergreifende Leistung {#oauth-user-traversal-performance}

Bei Community-Sites, bei denen sich Hunderttausende von Benutzern mit ihrer Facebook- oder Twitter-Anmeldung registrieren, kann die durchgängige Leistung der Abfrage, die ausgeführt wird, wenn ein Site-Besucher seine Anmeldung über soziale Netzwerke verwendet, durch Hinzufügen des folgenden Oak-Index verbessert werden.

Wenn in den Protokollen übergreifende Warnungen angezeigt werden, wird empfohlen, diesen Index hinzuzufügen.

Auf einer Autoreninstanz, die mit Administratorrechten angemeldet ist:

1. Wählen Sie in der globalen Navigation **Tools, [CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
1. Erstellen Sie einen Index mit dem Namen ntBaseLucene-oauth aus einer Kopie von ntBaseLucene:

   * Unter dem Knoten `/oak:index`
   * Knoten `ntBaseLucene` auswählen
   * Wählen Sie **[!UICONTROL Kopieren]**
   * Klicken Sie auf `/oak:index`
   * Wählen Sie **[!UICONTROL Einfügen]** aus
   * Umbenennen der Kopie von ntBaseLucene in `ntBaseLucene-oauth`

1. Ändern Sie die Eigenschaften des Knotens ntBaseLucene-oauth:

   * **[!UICONTROL indexPath]**: `/oak:index/ntBaseLucene-oauth`
   * **[!UICONTROL name]**: `oauthid-123****`
   * **[!UICONTROL reindex]**: `true`
   * **[!UICONTROL reindexCount]**: `1`

1. Unter dem Knoten /oak:index/ntBaseLucene-oauth/indexRules/nt:base/properties:

   * Löschen Sie alle untergeordneten Knoten mit Ausnahme von cqTags.
   * Umbenennen von cqTags in `oauthid-123****`
   * Ändern der Eigenschaften des Knotens `oauthid-123****`

      * **[!UICONTROL name]**: `oauthid-123****`

   * Klicken Sie auf **[!UICONTROL Alle speichern]**.

* Ersetzen Sie für **name** `oauthid-123` den Wert *123* durch den Facebook ***App ID*** oder den Twitter ***Consumer (API) Key***, der dem Wert der **Client-ID** in der Konfiguration [Adobe Granite OAuth Application and Provider](social-login.md#adobe-granite-oauth-application-and-provider) entspricht.

  ![graniteoauth-crxde](assets/graniteoauth-crxde.png)

Weitere Informationen und Tools finden Sie unter [Oak-Abfragen und -Indizierung](../../help/sites-deploying/queries-and-indexing.md).

## Dispatcher-Konfiguration {#dispatcher-configuration}

Siehe [Konfigurieren von Dispatcher für Communities](dispatcher.md).
