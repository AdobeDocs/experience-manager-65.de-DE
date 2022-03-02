---
title: Integration mit Adobe Analytics mithilfe von IMS
description: Erfahren Sie mehr über die Integration von AEM mit Adobe Analytics mithilfe von IMS.
source-git-commit: eb05fb92491932e4c2489c5adb533bbbae1d2870
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 2%

---

# Integration mit Adobe Analytics mithilfe von IMS {#integration-with-adobe-analytics-using-ims}

Die Integration von AEM mit Adobe Analytics über die Analytics Standard-API erfordert die Konfiguration von Adobe IMS (Identity Management-System) mithilfe der Adobe Developer Console.

>[!NOTE]
>
>Die Unterstützung für die Adobe Analytics Standard API 2.0 ist neu in AEM 6.5.12.0. Diese API-Version unterstützt die IMS-Authentifizierung.
>
>Die Verwendung der Adobe Analytics Classic API 1.4 in AEM wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt. Die [Die Analytics Classic-API verwendet die Authentifizierung von Benutzeranmeldeinformationen](/help/sites-administering/adobeanalytics-connect.md).
>
>Die API-Auswahl wird von der Authentifizierungsmethode gesteuert, die für die AEM/Analytics-Integration verwendet wird.
>
>Weitere Informationen finden Sie unter [Migration zu den 2.0-APIs](https://developer.adobe.com/analytics-apis/docs/2.0/guides/migration/).

## Voraussetzungen {#prerequisites}

Bevor Sie mit diesem Verfahren beginnen:

* [Adobe-Support](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) muss Ihr Konto für Folgendes bereitstellen:

   * Adobe Console
   * Adobe Developer Console
   * Adobe Analytics und
   * Adobe IMS (Identity Management System)

* Der Systemadministrator Ihres Unternehmens sollte die Admin Console verwenden, um die erforderlichen Entwickler in Ihrem Unternehmen den relevanten Produktprofilen hinzuzufügen.

   * Dadurch erhalten die spezifischen Entwickler Berechtigungen zum Aktivieren von Integrationen in der Adobe Developer Console.
   * Weitere Informationen finden Sie unter [Verwalten von Entwicklern](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Konfigurieren einer IMS-Konfiguration - Generieren eines öffentlichen Schlüssels {#configuring-an-ims-configuration-generating-a-public-key}

Der erste Schritt der Konfiguration besteht darin, eine IMS-Konfiguration in AEM zu erstellen und den öffentlichen Schlüssel zu generieren.

1. Öffnen Sie AEM **Instrumente** Menü.
1. Im **Sicherheit** Abschnittsauswahl **Adobe IMS-Konfigurationen**.
1. Auswählen **Erstellen** , um **Technische Kontokonfiguration für Adobe IMS**.
1. Verwenden der Dropdown-Liste unter **Cloud-Konfiguration** auswählen **Adobe Analytics**.
1. Aktivieren **Neues Zertifikat erstellen** und geben Sie einen neuen Alias ein.
1. Bestätigen mit **Zertifikat erstellen**.

   ![](assets/integrate-analytics-io-01.png)

1. Auswählen **Download** (oder **Öffentlichen Schlüssel herunterladen**), um die Datei auf Ihr lokales Laufwerk herunterzuladen, damit sie einsatzbereit ist, wenn [IMS für die Adobe Analytics-Integration mit AEM konfigurieren](#configuring-ims-for-adobe-analytics-integration-with-aem).

   >[!CAUTION]
   >
   >Lassen Sie diese Konfiguration geöffnet. Sie wird bei [Abschließen der IMS-Konfiguration in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-analytics-io-02.png)

## IMS für Adobe Analytics-Integration mit AEM konfigurieren {#configuring-ims-for-adobe-analytics-integration-with-aem}

Mithilfe der Adobe Developer Console müssen Sie ein Projekt (Integration) mit Adobe Analytics erstellen (AEM verwenden) und dann die erforderlichen Berechtigungen zuweisen.

### Erstellen des Projekts {#creating-the-project}

Öffnen Sie die Adobe Developer Console, um ein Projekt mit Adobe Analytics zu erstellen, das AEM Folgendes verwenden wird:

1. Öffnen Sie die Adobe Developer Console for Projects:

   [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

1. Alle Projekte, die Sie haben, werden angezeigt. Auswählen **Neues Projekt erstellen** - Ort und Nutzung hängen von Folgendem ab:

   * Wenn Sie noch kein Projekt haben, **Neues Projekt erstellen** wird zentriert sein, unten.
      ![Neues Projekt erstellen - erstes Projekt](assets/integration-analytics-io-02.png)
   * Wenn Sie bereits über vorhandene Projekte verfügen, werden diese aufgelistet und **Neues Projekt erstellen** oben rechts.
      ![Neues Projekt erstellen - Mehrere Projekte](assets/integration-analytics-io-03.png)


1. Auswählen **Zum Projekt hinzufügen** gefolgt von **API**:

   ![Erste Schritte mit Ihrem neuen Projekt](assets/integration-analytics-io-10.png)

1. Auswählen **Adobe Analytics**, dann **Nächste**:

   >[!NOTE]
   >
   >Wenn Sie Adobe Analytics abonniert haben, es jedoch nicht aufgeführt sehen, sollten Sie die Option [Voraussetzungen](#prerequisites).

   ![Fügen Sie eine API hinzu](assets/integration-analytics-io-12.png)

1. Auswählen **Dienstkonto (JWT)** als Authentifizierungstyp angeben, fahren Sie dann mit **Nächste**:

   ![Authentifizierungstyp auswählen](assets/integration-analytics-io-12a.png)

1. **Öffentlichen Schlüssel hochladen** und nach Abschluss des Vorgangs mit **Nächste**:

   ![Öffentlichen Schlüssel hochladen](assets/integration-analytics-io-13.png)

1. Überprüfen Sie die Anmeldeinformationen und fahren Sie mit **Nächste**:

   ![Prüfberechtigungen](assets/integration-analytics-io-15.png)

1. Wählen Sie die erforderlichen Produktprofile aus und fahren Sie mit **Konfigurierte API speichern**:

   ![Erforderliche Produktprofile auswählen](assets/integration-analytics-io-16.png)

1. Die Konfiguration wird bestätigt.

### Zuweisen von Berechtigungen zur Integration {#assigning-privileges-to-the-integration}

Sie müssen der Integration jetzt die erforderlichen Berechtigungen zuweisen:

1. Adobe öffnen **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigieren Sie zu **Produkte** (obere Symbolleiste) und wählen Sie **Adobe Analytics - &lt;*your-tenant-id*>** (im linken Bereich).
1. Auswählen **Produktprofile**, dann den gewünschten Arbeitsbereich aus der angezeigten Liste. Beispiel: Standardarbeitsbereich.
1. Auswählen **API-Anmeldeinformationen**, dann die erforderliche Integrationskonfiguration.
1. Auswählen **Editor** als **Produktrolle**; anstelle von **Beobachter**.

## Für das Adobe Developer Console-Integrationsprojekt gespeicherte Details {#details-stored-for-the-ims-integration-project}

In der Adobe Developer Projects Console können Sie eine Liste aller Integrationsprojekte anzeigen:

* [https://developer.adobe.com/console/projects](https://developer.adobe.com/console/projects)

Wählen Sie einen bestimmten Projekteintrag aus, um weitere Details zur Konfiguration anzuzeigen. Dazu gehören:

* Projektübersicht
* Insights
* Berechtigungen
   * Dienstkonto (JWT)
      * Details zu Berechtigungen
      * JWT generieren
* APIS
   * Beispiel: Adobe Analytics

Einige davon müssen Sie in AEM die Integration für Adobe Analytics abschließen.

## Abschließen der IMS-Konfiguration in AEM {#completing-the-ims-configuration-in-aem}

Kehren Sie zu AEM zurück und Sie können die IMS-Konfiguration abschließen, indem Sie erforderliche Werte aus dem Integrationsprojekt für Analytics hinzufügen:

1. Kehren Sie zu [IMS-Konfiguration geöffnet in AEM](#configuring-an-ims-configuration-generating-a-public-key).
1. Wählen Sie **Weiter** aus.

1. Hier können Sie die [Für das Adobe Developer Console-Integrationsprojekt gespeicherte Details](#details-stored-for-the-ims-integration-project):

   * **Titel**: Ihr Text.
   * **Autorisierungsserver**: Kopieren/Einfügen Sie dies aus dem `aud` der **Nutzlast** unten, z. B. `https://ims-na1.adobelogin.com` im Beispiel unten
   * **API-Schlüssel**: Kopieren Sie dies aus dem **Anmeldeinformationen** Abschnitt [Projektübersicht](#details-stored-for-the-ims-integration-project)
   * **Client Secret**: Generieren Sie dies im [Registerkarte &quot;Client-Geheimnis&quot;im Abschnitt &quot;Service-Konto (JWT)&quot;](#details-stored-for-the-ims-integration-project)und kopieren
   * **Nutzlast**: Kopieren Sie dies aus dem [Registerkarte &quot;JWT generieren&quot;im Abschnitt &quot;Dienstkonto (JWT)&quot;](#details-stored-for-the-ims-integration-project)

   ![AEM IMS-Konfigurationsdetails](assets/integrate-analytics-io-10.png)

1. Bestätigen Sie mit **Erstellen**.

1. Ihre Adobe Analytics-Konfiguration wird in der AEM Console angezeigt.

   ![IMS-Konfiguration](assets/integrate-analytics-io-11.png)

## IMS-Konfiguration bestätigen {#confirming-the-ims-configuration}

So überprüfen Sie, ob die Konfiguration erwartungsgemäß funktioniert:

1. Öffnen Sie:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Beispiel:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Wählen Sie Ihre Konfiguration aus.
1. Auswählen **Konsistenzprüfung** aus der Symbolleiste, gefolgt von **Überprüfen**.

   ![IMS-Konfiguration - Systemdiagnose](assets/integrate-analytics-io-12.png)

1. Bei erfolgreicher Ausführung wird eine Bestätigungsmeldung angezeigt.

## Konfigurieren des Adobe Analytics Cloud-Dienstes {#configuring-the-adobe-analytics-cloud-service}

Auf die Konfiguration kann nun verwiesen werden, damit ein Cloud Service die Analytics Standard-API verwenden kann:

1. Öffnen Sie die **Instrumente** Menü. Anschließend innerhalb der **Cloud Services** Bereich, wählen Sie **Ältere Cloud Services**.
1. Scrollen Sie nach unten zu **Adobe Analytics** und wählen Sie **Jetzt konfigurieren**.

   Die **Konfiguration erstellen** wird geöffnet.

1. Geben Sie einen **Titel** und, falls gewünscht, ein **Name** (Wenn Sie das Feld leer lassen, wird dies aus dem Titel generiert.)

   Sie können auch die gewünschte Vorlage auswählen (wenn mehrere Vorlagen verfügbar sind).

1. Bestätigen Sie mit **Erstellen**.

   Die **Komponente bearbeiten** wird geöffnet.

1. Geben Sie die Details im **Analytics-Einstellungen** tab:

   * **Authentifizierung**: IMS

   * **IMS-Konfiguration**: den Namen der IMS-Konfiguration auswählen

1. Klicken **Verbindung zu Analytics herstellen** , um die Verbindung mit Adobe Analytics zu initialisieren.

   Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung **Verbindung erfolgreich** angezeigt.

1. Auswählen **OK** auf der Nachricht angezeigt.

1. Füllen Sie ggf. weitere Parameter aus, gefolgt von **OK** im Dialogfeld, um die Konfiguration zu bestätigen.

1. Sie können jetzt fortfahren [Hinzufügen eines Analytics-Frameworks](/help/sites-administering/adobeanalytics-connect.md) , um Parameter zu konfigurieren, die an Adobe Analytics gesendet werden.
