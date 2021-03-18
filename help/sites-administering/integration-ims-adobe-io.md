---
title: Integration mit Adobe Target über Adobe I/O
seo-title: Integration mit Adobe Target über Adobe I/O
description: Erfahren Sie mehr über die Integration von AEM mit Adobe Target mithilfe der Adobe I/O
seo-description: Erfahren Sie mehr über die Integration von AEM mit Adobe Target mithilfe der Adobe I/O
uuid: dd4ed638-e182-4d7e-9c98-282431812467
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: integration
discoiquuid: 3b9285db-8fba-4d12-8f52-41daa50a5403
docset: aem65
translation-type: tm+mt
source-git-commit: 07f354ccfb8741f0de4fc85ba1575ead3b8ea6e4
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 9%

---


# Integration mit Adobe Target über Adobe I/O{#integration-with-adobe-target-using-adobe-i-o}

Die Integration von AEM mit Adobe Target über die Target Standard-API erfordert die Konfiguration von Adobe IMS (Identity Management System) und Adobe I/O.

>[!NOTE]
>
>Die Unterstützung für die Adobe Target Standard-API ist neu in AEM 6.5. Die Target Standard-API verwendet die IMS-Authentifizierung.
>
>Die Verwendung der Adobe Target Classic API in AEM wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt. Die [Zielgruppe Classic-API verwendet die Benutzeranmeldeauthentifizierung](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).
>
>Die API-Auswahl wird von der Authentifizierungsmethode gesteuert, die für die AEM/Zielgruppe-Integration verwendet wird.
>Siehe auch Abschnitt [Mandant-ID und Client-Code](#tenant-client).

## Voraussetzungen {#prerequisites}

Bevor Sie mit diesem Verfahren beginnen:

* [Adobe ](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) Support muss Ihr Konto für Folgendes bereitstellen:

   * Adobe Console
   * Adobe I/O
   * Adobe Target und
   * Adobe IMS (Identity Management-System)

* Der Systemadministrator Ihres Unternehmens sollte die Admin Console verwenden, um die erforderlichen Entwickler in Ihrem Unternehmen zu den entsprechenden Profilen hinzuzufügen.

   * Dadurch erhalten bestimmte Entwickler die Berechtigung, Integrationen in der Adobe I/O zu aktivieren.
   * Weitere Informationen finden Sie unter [Entwickler verwalten](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Konfigurieren einer IMS-Konfiguration - Generieren eines öffentlichen Schlüssels {#configuring-an-ims-configuration-generating-a-public-key}

Der erste Schritt der Konfiguration besteht darin, eine IMS-Konfiguration in AEM zu erstellen und den öffentlichen Schlüssel zu generieren.

1. Öffnen Sie AEM Menü **Tools**.
1. Wählen Sie im Abschnitt **Security** **Adobe IMS Configurations**.
1. Wählen Sie **Create**, um die Adobe **IMS Technical Account Configuration** zu öffnen.
1. Wählen Sie unter **Cloud-Konfiguration** **Adobe Target** aus.
1. Aktivieren Sie **Neues Zertifikat** erstellen und geben Sie einen neuen Alias ein.
1. Bestätigen Sie mit **Zertifikat erstellen**.

   ![](assets/integrate-target-io-01.png)

1. Wählen Sie **Herunterladen** (oder **Öffentlichen Schlüssel herunterladen**), um die Datei auf Ihr lokales Laufwerk herunterzuladen, damit sie einsatzbereit ist, wenn [die Adobe I/O für die Adobe Target-Integration mit AEM](#configuring-adobe-i-o-for-adobe-target-integration-with-aem) konfiguriert wird.

   >[!CAUTION]
   >
   >Lassen Sie diese Konfiguration geöffnet, wird sie erneut benötigt, wenn [die IMS-Konfiguration in AEM](#completing-the-ims-configuration-in-aem) abgeschlossen wird.

   ![](assets/integrate-target-io-02.png)

## Adobe I/O für Adobe Target-Integration mit AEM {#configuring-adobe-i-o-for-adobe-target-integration-with-aem} konfigurieren

Sie müssen das Adobe I/O Project (Integration) mit Adobe Target erstellen, das AEM verwenden wird, und dann die erforderlichen Berechtigungen zuweisen.

### Erstellen des Projekts {#creating-the-project}

Öffnen Sie die Adobe I/O-Konsole, um ein E/A-Projekt mit Adobe Target zu erstellen, das AEM Folgendes verwenden wird:

>[!NOTE]
>
>Siehe auch die [Adobe I/O-Tutorials](https://www.adobe.io/apis/experienceplatform/home/tutorials/alltutorials.html).

1. Öffnen Sie die Projektkonsole für Adoben I/O:

   [https://console.adobe.io/projects](https://console.adobe.io/projects)

1. Alle Projekte, die Sie haben, werden angezeigt. Wählen Sie **Neues Projekt erstellen** - der Ort und die Nutzung hängen von:

   * Wenn Sie noch kein Projekt haben, wird **Neues Projekt erstellen** zentriert, unten.
      ![Neues Projekt erstellen - Erstes Projekt](assets/integration-target-io-02.png)
   * Wenn Sie bereits über bestehende Projekte verfügen, werden diese aufgelistet und **Neues Projekt erstellen** wird oben rechts angezeigt.
      ![Neues Projekt erstellen - Mehrere Projekte](assets/integration-target-io-03.png)


1. Wählen Sie **Hinzufügen zu Projekt**, gefolgt von **API**:

   ![](assets/integration-target-io-10.png)

1. Wählen Sie **Adobe Target** und dann **Weiter**:

   >[!NOTE]
   >
   >Wenn Sie Adobe Target abonniert haben, es aber nicht aufgeführt sehen, sollten Sie [Prerequistes](#prerequisites) überprüfen.

   ![](assets/integration-target-io-12.png)

1. **Laden Sie den öffentlichen Schlüssel** hoch und fahren Sie nach Abschluss mit  **Weiter** fort:

   ![](assets/integration-target-io-13.png)

1. Überprüfen Sie die Anmeldeinformationen und fahren Sie mit **Weiter** fort:

   ![](assets/integration-target-io-15.png)

1. Wählen Sie die erforderlichen Profil aus und fahren Sie mit **Konfigurierte API speichern** fort:

   >[!NOTE]
   >
   >Die angezeigten Profil hängen davon ab, ob Sie über Folgendes verfügen:
   >
   >* Adobe Target Standard - nur **Standardarbeitsbereich** ist verfügbar
   >* Adobe Target Premium - alle verfügbaren Arbeitsflächen werden wie unten dargestellt aufgelistet


   ![](assets/integration-target-io-16.png)

1. Die Erstellung wird bestätigt.

<!--
1. The creation will be confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-07.png)
-->

### Zuweisen von Berechtigungen zur Integration {#assigning-privileges-to-the-integration}

Sie müssen der Integration jetzt die erforderlichen Berechtigungen zuweisen:

1. Öffnen Sie die Adobe **Admin Console**:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigieren Sie zu **Produkte** (obere Symbolleiste) und wählen Sie **Adobe Target - &lt;*Ihre-Mandant-ID*** (aus dem linken Bereich).
1. Wählen Sie **Product Profils** und dann Ihren erforderlichen Arbeitsbereich aus der gezeigten Liste. Beispiel: Standard-Arbeitsbereich.
1. Wählen Sie **Integrationen** und dann die erforderliche Integrationskonfiguration.
1. Wählen Sie **Editor** als **Produktrolle** aus. anstelle von **Beobachter**.

## Für das Adobe I/O Integration Project {#details-stored-for-the-adobe-io-integration-project} gespeicherte Details

In der Adobe I/O Projects Console können Sie eine Liste aller Integrationsprojekte anzeigen:

* [https://console.adobe.io/projects](https://console.adobe.io/projects)

Wählen Sie **Ansicht** (rechts neben einem bestimmten Projekteintrag), um weitere Details zur Konfiguration anzuzeigen. Dazu gehören:

* Projektübersicht
* Insights
* Berechtigungen
   * Dienstkonto (JWT)
      * Berechtigungsdetails
      * JWT generieren
* APIS
   * Adobe Target

Einige davon müssen Sie für die Zielgruppe in AEM die Adobe I/O-Integration abschließen.

## Abschluss der IMS-Konfiguration in AEM {#completing-the-ims-configuration-in-aem}

Zurück zum AEM können Sie die IMS-Konfiguration abschließen, indem Sie erforderliche Werte aus der Adobe I/O-Integration für die Zielgruppe hinzufügen:

1. Kehren Sie zur unter AEM](#configuring-an-ims-configuration-generating-a-public-key) geöffneten IMS-Konfiguration zurück.[
1. Wählen Sie **Weiter** aus.

1. Hier können Sie die [Details aus Adobe I/O](#details-stored-for-the-adobe-io-integration-project) verwenden:

   * **Titel**: Ihr Text.
   * **Autorisierungsserver**: Kopieren/fügen Sie dies aus der  `"aud"` Zeile des  **** Payloadsection unten ein, z.B.  `"https://ims-na1.adobelogin.com"` im Beispiel unten
   * **API-Schlüssel**: Kopieren Sie dies aus dem  [](#details-stored-for-the-adobe-io-integration-project) Übersichtsabschnitt der Adobe I/O-Integration für Zielgruppe
   * **geheim**: Generieren Sie dies im  [](#details-stored-for-the-adobe-io-integration-project) Übersichtsabschnitt der Adobe I/O-Integration für die Zielgruppe und kopieren Sie
   * **Nutzlast**: Kopieren Sie dies aus dem Abschnitt  [Generate ](#details-stored-for-the-adobe-io-integration-project) JWT in der Adobe I/O-Integration für Zielgruppe

   ![](assets/integrate-target-io-10.png)

1. Bestätigen Sie mit **Create**.

1. Ihre Adobe Target-Konfiguration wird in der AEM Konsole angezeigt.

   ![](assets/integrate-target-io-11.png)

## Bestätigung der IMS-Konfiguration {#confirming-the-ims-configuration}

So bestätigen Sie, dass die Konfiguration erwartungsgemäß funktioniert:

1. Öffnen Sie:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Beispiel:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Wählen Sie Ihre Konfiguration aus.
1. Wählen Sie **Health** in der Symbolleiste aus, gefolgt von **Check**.

   ![](assets/integrate-target-io-12.png)

1. Bei erfolgreichem Abschluss wird folgende Meldung angezeigt:

   ![](assets/integrate-target-io-13.png)

## Konfigurieren des Adobe Target-Cloud Service {#configuring-the-adobe-target-cloud-service}

Auf die Konfiguration kann nun verwiesen werden, damit ein Cloud Service die Target Standard-API verwenden kann:

1. Öffnen Sie das Menü **Tools**. Wählen Sie dann im Abschnitt **Cloud Services** die Option **Ältere Cloud Services**.
1. Blättern Sie nach unten zu **Adobe Target** und wählen Sie **Jetzt konfigurieren**.

   Das Dialogfeld **Konfiguration erstellen** wird geöffnet.

1. Geben Sie einen **Titel** und, falls gewünscht, einen **Name** ein (wenn Sie das Feld leer lassen, wird dies aus dem Titel generiert).

   Sie können auch die gewünschte Vorlage auswählen (wenn mehrere Vorlagen verfügbar sind).

1. Bestätigen Sie mit **Create**.

   Das Dialogfeld **Komponente bearbeiten** wird geöffnet.

1. Geben Sie die Details auf der Registerkarte **Adobe Target Settings** ein:

   * **Authentifizierung**: IMS
   * **Mandant-ID**: die Adobe IMS Tenant ID. Siehe auch den Abschnitt [Mandanten-ID und Client-Code](#tenant-client) weiter unten.

      >[!NOTE]
      >
      >Für IMS muss dieser Wert der Zielgruppe selbst entnommen werden. Sie können sich bei der Zielgruppe anmelden und die Mandanten-ID aus der URL extrahieren.
      >
      >Beispiel:
      >
      >`https://experience.adobe.com/#/@yourtenantid/target/activities`
      >
      >Dann würden Sie `yourtenantid` verwenden.
   * **Client-Code**: Siehe  [Mandanten-ID und Client-](#tenant-client) Code unten.
   * **IMS-Konfiguration**: den Namen der IMS-Konfiguration auswählen
   * **API-Typ**: REST
   * **A4T-Analyse-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für die Berichterstellung für bestimmte Inhalte verwenden. Wenn Ihre Cloud-Konfiguration nicht angezeigt wird, finden Sie weitere Informationen unter [Konfigurieren der A4T-Analytics Cloud-Konfiguration](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).
   * **Verwenden Sie genaues Targeting**: Standardmäßig ist dieses Kontrollkästchen aktiviert. Bei Aktivierung dieser Option wird für die Cloud Service-Konfiguration gewartet, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Siehe Hinweis unten.
   * **Segmente aus Adobe Target** synchronisieren: Wählen Sie diese Option, um in der Zielgruppe definierte Segmente herunterzuladen, um sie in AEM zu verwenden. Sie müssen diese Option auswählen, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Beachten Sie, dass der AEM-Begriff „Segment“ hier dem Target-Begriff „Zielgruppe“ entspricht.)
   * **Client-Bibliothek**: Wählen Sie aus, ob die AT.js-Client-Bibliothek oder mbox.js (nicht mehr unterstützt) verwendet werden soll.
   * **Verwenden Sie das Tag-Management-System zur Bereitstellung der Client-Bibliothek**: Verwenden Sie DTM (nicht mehr unterstützt), Adobe Launch oder ein anderes Tag-Management-System.
   * **Benutzerspezifische AT.js**: Lassen Sie das Feld Tag-Management leer, wenn Sie das Feld Tag-Management markiert haben oder die standardmäßige Version von AT.js verwenden. Alternativ hierzu können Sie Ihre benutzerdefinierte Datei „AT.js“ hochladen. Sie wird nur angezeigt, wenn Sie „AT.js“ ausgewählt haben.

   >[!NOTE]
   >
   >[Die Konfiguration eines Cloud Service zur Verwendung der Zielgruppe Classic ](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) API wurde eingestellt (unter Verwendung der Registerkarte &quot;Adobe Recommendations-Einstellungen&quot;).
1. Klicken Sie auf **Mit Zielgruppe verbinden**, um die Verbindung mit Adobe Target zu initialisieren.

   Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung **Verbindung erfolgreich** angezeigt.

1. Wählen Sie in der Meldung **OK** und anschließend **OK** im Dialogfeld aus, um die Konfiguration zu bestätigen.
1. Sie können jetzt mit [Hinzufügen eines Zielgruppe-Frameworks](/help/sites-administering/target-configuring.md#adding-a-target-framework) fortfahren, um ContextHub- oder ClientContext-Parameter zu konfigurieren, die an die Zielgruppe gesendet werden. Beachten Sie, dass dies möglicherweise nicht erforderlich ist, um AEM Erlebnisfragmente in die Zielgruppe zu exportieren.

### Mandanten-ID und Client-Code {#tenant-client}

Mit [Adobe Experience Manager 6.5.8.0](/help/release-notes/sp-release-notes.md) wurde das Feld Client-Code zum Konfigurationsfenster der Zielgruppe hinzugefügt.

Achten Sie bei der Konfiguration der Felder Mandant-ID und Client-Code auf Folgendes:

1. Für die meisten Kunden sind die Mandant-ID und der Client-Code identisch. Das bedeutet, dass beide Felder die gleichen Informationen enthalten und identisch sind. Vergewissern Sie sich, dass Sie die Mandant-ID in beide Felder eingeben.
2. Zu älteren Zwecken können Sie auch verschiedene Werte in die Felder &quot;Mandant-ID&quot;und &quot;Client-Code&quot;eingeben.

Beachten Sie in beiden Fällen Folgendes:

* Standardmäßig wird auch der Client-Code (wenn er zuerst hinzugefügt wird) automatisch in das Feld &quot;Mandant-ID&quot;kopiert.
* Sie haben die Möglichkeit, den Standardsatz für die Mandant-ID zu ändern.
* Dementsprechend basieren die Backend-Aufrufe zur Zielgruppe auf der Mandanten-ID und die clientseitigen Aufrufe zur Zielgruppe basieren auf dem Client-Code.

Wie bereits erwähnt, ist der erste Fall der häufigste Fall für AEM 6.5. Stellen Sie in beiden Fällen sicher, dass die Felder **beide** je nach Bedarf die richtigen Informationen enthalten.

>[!NOTE]
>
> Wenn Sie eine bestehende Konfiguration der Zielgruppe ändern möchten:
>
> 1. Geben Sie die Tenant-ID erneut ein.
> 2. Stellen Sie eine erneute Verbindung zur Zielgruppe her.
> 3. Speichern Sie die Konfiguration.

