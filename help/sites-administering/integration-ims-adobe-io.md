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
source-git-commit: 26efba567985dcb89b2610935cab18943b7034b3
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 11%

---


# Integration mit Adobe Target über Adobe I/O{#integration-with-adobe-target-using-adobe-i-o}

Die Integration von AEM mit Adobe Target über die Target Standard-API erfordert die Konfiguration von Adobe IMS (Identity Management System) und Adobe I/O.

>[!NOTE]
>
>Die Unterstützung für die Adobe Target Standard-API ist neu in AEM 6.5. Die Target Standard-API verwendet die IMS-Authentifizierung.
>
>Die Verwendung der Adobe Target Classic API in AEM wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt. Die [Zielgruppe Classic-API verwendet die Authentifizierung](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target)mit Benutzeranmeldeinformationen.
>
>Die API-Auswahl wird von der Authentifizierungsmethode gesteuert, die für die AEM/Zielgruppe-Integration verwendet wird.

## Voraussetzungen {#prerequisites}

Bevor Sie mit diesem Verfahren beginnen:

* [Adobe Support](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) muss Ihr Konto für Folgendes bereitstellen:

   * Adobe Console
   * Adobe I/O
   * Adobe Target und
   * Adobe IMS (Identity Management-System)

* Der Systemadministrator Ihres Unternehmens sollte die Admin Console verwenden, um die erforderlichen Entwickler in Ihrem Unternehmen zu den entsprechenden Profilen hinzuzufügen.

   * Dadurch erhalten bestimmte Entwickler die Berechtigung, Integrationen in der Adobe I/O zu aktivieren.
   * Weitere Informationen finden Sie unter Entwickler [verwalten](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Konfigurieren einer IMS-Konfiguration - Generieren eines öffentlichen Schlüssels {#configuring-an-ims-configuration-generating-a-public-key}

Der erste Schritt der Konfiguration besteht darin, eine IMS-Konfiguration in AEM zu erstellen und den öffentlichen Schlüssel zu generieren.

1. Öffnen Sie AEM das Menü **Extras** .
1. Wählen Sie im Abschnitt **Sicherheit** die Option **Adobe IMS-Konfigurationen**.
1. Wählen Sie **Erstellen** , um die **Adobe IMS Technical Account Configuration** zu öffnen.
1. Wählen Sie in der Dropdown-Liste unter **Cloud-Konfiguration** die Option **Adobe Target**.
1. Aktivieren Sie **Neues Zertifikat** erstellen und geben Sie einen neuen Alias ein.
1. Bestätigen Sie mit **Zertifikat** erstellen.

   ![](assets/integrate-target-io-01.png)

1. Wählen Sie &quot; **Herunterladen** &quot;(oder &quot;Öffentlichen **Schlüssel** herunterladen&quot;), um die Datei auf Ihr lokales Laufwerk herunterzuladen, damit sie bei der [Konfiguration der E/A-Adobe für die Adobe Target-Integration mit AEM](#configuring-adobe-i-o-for-adobe-target-integration-with-aem)verwendet werden kann.

   >[!CAUTION]
   >
   >Lassen Sie diese Konfiguration geöffnet, wird sie beim [Abschluss der IMS-Konfiguration in AEM](#completing-the-ims-configuration-in-aem)erneut benötigt.

   ![](assets/integrate-target-io-02.png)

## Konfigurieren der Adobe-E/A für die Adobe Target-Integration mit AEM {#configuring-adobe-i-o-for-adobe-target-integration-with-aem}

Sie müssen das Adoben-E/A-Projekt (Integration) mit Adobe Target erstellen, das AEM verwenden wird, und dann die erforderlichen Berechtigungen zuweisen.

### Erstellen des Projekts {#creating-the-project}

Öffnen Sie die E/A-Konsole der Adobe, um ein E/A-Projekt mit Adobe Target zu erstellen, das AEM Folgendes verwenden wird:

>[!NOTE]
>
>Siehe auch die [Adoben-E/A-Tutorials](https://www.adobe.io/apis/experienceplatform/home/tutorials/alltutorials.html).

1. Öffnen Sie die Adoben-E/A-Konsole für Projekte:

   [https://console.adobe.io/projects](https://console.adobe.io/projects)

1. Alle Projekte, die Sie haben, werden angezeigt. Wählen Sie &quot;Neues Projekt **** erstellen&quot;. Der Ort und die Nutzung hängen von Folgendem ab:

   * Wenn Sie noch kein Projekt haben, wird &quot; **Neues Projekt** erstellen&quot;zentriert, unten angezeigt.
      ![Neues Projekt erstellen - Erstes Projekt](assets/integration-target-io-02.png)
   * Wenn Sie bereits über bestehende Projekte verfügen, werden diese aufgelistet und **Neues Projekt** erstellen wird oben rechts angezeigt.
      ![Neues Projekt erstellen - Mehrere Projekte](assets/integration-target-io-03.png)


1. Wählen Sie **Hinzufügen zu Projekt** , gefolgt von **API**:

   ![](assets/integration-target-io-10.png)

1. Wählen Sie **Adobe Target** und dann **Weiter**:

   >[!NOTE]
   >
   >Wenn Sie Adobe Target abonniert haben, es aber nicht aufgelistet sehen, sollten Sie die [Prerequistes](#prerequisites)überprüfen.

   ![](assets/integration-target-io-12.png)

1. **Laden Sie den öffentlichen Schlüssel** hoch und fahren Sie nach Abschluss mit **Weiter** fort:

   ![](assets/integration-target-io-13.png)

1. Überprüfen Sie die Anmeldeinformationen und fahren Sie mit **Weiter** fort:

   ![](assets/integration-target-io-15.png)

1. Wählen Sie die erforderlichen Profil aus und fahren Sie mit der **Save-konfigurierten API** fort:

   >[!NOTE]
   >
   >Die angezeigten Profil hängen davon ab, ob Sie über Folgendes verfügen:
   >
   >* Adobe Target Standard - nur **Standardarbeitsbereich** verfügbar
   >* Adobe Target Premium - alle verfügbaren Arbeitsflächen werden wie unten dargestellt aufgelistet


   ![](assets/integration-target-io-16.png)

1. Die Erstellung wird bestätigt.

<!--
1. The creation will be confirmed, you can now **Continue to integration details**; these are needed for [Completing the IMS Configuration in AEM](#completing-the-ims-configuration-in-aem).

   ![](assets/integrate-target-io-07.png)
-->

### Berechtigungen der Integration zuweisen {#assigning-privileges-to-the-integration}

Sie müssen der Integration jetzt die erforderlichen Berechtigungen zuweisen:

1. Öffnen Sie die **Admin Console** Adobe:

   * [https://adminconsole.adobe.com](https://adminconsole.adobe.com/)

1. Navigieren Sie zu **Produkte** (obere Symbolleiste) und wählen Sie dann **Adobe Target - &lt;*Ihre-Mandant-ID*>** (aus dem linken Bereich).
1. Wählen Sie **Product Profils** und dann Ihren gewünschten Arbeitsbereich aus der präsentierten Liste. Beispiel: Standard-Arbeitsbereich.
1. Wählen Sie **Integrationen** und dann die erforderliche Integrationskonfiguration.
1. Wählen Sie **Editor** als **Produktrolle** aus; anstatt **Beobachter**.

## Für das E/A-Integrationsprojekt der Adobe gespeicherte Details {#details-stored-for-the-adobe-io-integration-project}

In der Konsole &quot;Adobe-E/A-Projekte&quot;sehen Sie eine Liste aller Integrationsprojekte:

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

Einige davon müssen Sie zur Zielgruppe in AEM die Adobe-I/O-Integration abschließen.

## Abschluss der IMS-Konfiguration in AEM {#completing-the-ims-configuration-in-aem}

Zurück zum AEM können Sie die IMS-Konfiguration abschließen, indem Sie erforderliche Werte aus der Adoben-E/A-Integration für die Zielgruppe hinzufügen:

1. Kehren Sie zur [IMS-Konfiguration zurück, die in AEM](#configuring-an-ims-configuration-generating-a-public-key)geöffnet ist.
1. Wählen Sie **Weiter** aus.

1. Hier können Sie die [Angaben aus der Adobe I/O](#details-stored-for-the-adobe-io-integration-project)verwenden:

   * **Titel**: Ihr Text.
   * **Autorisierungsserver**: Kopieren/fügen Sie dies aus der `"aud"` Zeile im Abschnitt **Nutzlast** unten ein, z.B. `"https://ims-na1.adobelogin.com"` im Beispiel unten
   * **API-Schlüssel**: Kopieren Sie dies aus dem [Übersichtsabschnitt](#details-stored-for-the-adobe-io-integration-project) der Adoben-E/A-Integration für die Zielgruppe
   * **geheim**: Generieren Sie dies im [Übersichtsbereich](#details-stored-for-the-adobe-io-integration-project) der Adoben-E/A-Integration für die Zielgruppe und kopieren Sie
   * **Nutzlast**: Kopieren Sie dies aus dem Abschnitt [Generate JWT](#details-stored-for-the-adobe-io-integration-project) der Adoben-E/A-Integration für die Zielgruppe

   ![](assets/integrate-target-io-10.png)

1. Bestätigen Sie mit **Erstellen**.

1. Ihre Adobe Target-Konfiguration wird in der AEM Konsole angezeigt.

   ![](assets/integrate-target-io-11.png)

## IMS-Konfiguration bestätigen {#confirming-the-ims-configuration}

So bestätigen Sie, dass die Konfiguration erwartungsgemäß funktioniert:

1. Öffnen Sie:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Beispiel:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Wählen Sie Ihre Konfiguration aus.
1. Wählen Sie in der Symbolleiste die Option &quot; **Prüfstatus** &quot;und anschließend &quot; **Prüfung**&quot;aus.

   ![](assets/integrate-target-io-12.png)

1. Bei erfolgreichem Abschluss wird folgende Meldung angezeigt:

   ![](assets/integrate-target-io-13.png)

## Adobe Target Cloud Service konfigurieren {#configuring-the-adobe-target-cloud-service}

Auf die Konfiguration kann nun verwiesen werden, damit ein Cloud Service die Target Standard-API verwenden kann:

1. Open the **Tools** menu. Wählen Sie dann im Abschnitt **Cloud Services** die Option **Legacy-Cloud Services**.
1. Blättern Sie nach unten zu **Adobe Target** und wählen Sie Jetzt **konfigurieren**.

   The **Create Configuration** dialog will open.

1. Geben Sie einen **Titel** und, falls gewünscht, einen **Namen** ein (leer gelassen, wird dieser aus dem Titel generiert).

   Sie können auch die gewünschte Vorlage auswählen (wenn mehrere Vorlagen verfügbar sind).

1. Bestätigen Sie mit **Erstellen**.

   Das Dialogfeld Komponente **bearbeiten** wird geöffnet.

1. Geben Sie die Details auf der Registerkarte &quot; **Adobe Target-Einstellungen** &quot;ein:

   * **Authentifizierung**: IMS
   * **Mandant-ID**: die Adobe IMS Tenant ID

      >[!NOTE]
      >
      >Für IMS muss dieser Wert der Zielgruppe selbst entnommen werden. Sie können sich bei der Zielgruppe anmelden und die Mandanten-ID aus der URL extrahieren.
      >
      >Beispiel:
      >
      >`https://experience.adobe.com/#/@yourtenantid/target/activities`
      >
      >Dann würden Sie es benutzen `yourtenantid`.

   * **IMS-Konfiguration**: den Namen der IMS-Konfiguration auswählen
   * **API-Typ**: REST
   * **A4T-Analyse-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für die Berichterstellung für bestimmte Inhalte verwenden. If you do not see your cloud configuration, see note in [Configuring A4T Analytics Cloud Configuration](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).
   * **Verwenden Sie genaues Targeting**: Standardmäßig ist dieses Kontrollkästchen aktiviert. Bei Aktivierung dieser Option wird für die Cloud Service-Konfiguration gewartet, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Siehe Hinweis unten.
   * **Segmente aus Adobe Target** synchronisieren: Wählen Sie diese Option, um in der Zielgruppe definierte Segmente herunterzuladen, um sie in AEM zu verwenden. Sie müssen diese Option auswählen, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Beachten Sie, dass der AEM-Begriff „Segment“ hier dem Target-Begriff „Zielgruppe“ entspricht.)
   * **Client-Bibliothek**: Wählen Sie aus, ob die AT.js-Client-Bibliothek oder mbox.js (nicht mehr unterstützt) verwendet werden soll.
   * **Verwenden Sie das Tag-Management-System zur Bereitstellung der Client-Bibliothek**: Verwenden Sie DTM (nicht mehr unterstützt), Adobe Launch oder ein anderes Tag-Management-System.
   * **Benutzerspezifische AT.js**: Lassen Sie das Feld Tag-Management leer, wenn Sie das Feld Tag-Management markiert haben oder die standardmäßige Version von AT.js verwenden. Alternativ hierzu können Sie Ihre benutzerdefinierte Datei „AT.js“ hochladen. Sie wird nur angezeigt, wenn Sie „AT.js“ ausgewählt haben.

   >[!NOTE]
   >
   >[Die Konfiguration eines Cloud Service zur Verwendung der Zielgruppe Classic API](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) wurde eingestellt (unter Verwendung der Registerkarte &quot;Adobe Recommendations-Einstellungen&quot;).

   Beispiel:

   ![](assets/integrate-target-io-14.png)

1. Click **Connect to Target** to initialize the connection with Adobe Target.

   If the connection is successful, the message **Connection successful** is displayed.

1. Wählen Sie in der Nachricht **OK** und anschließend im Dialogfeld **OK** , um die Konfiguration zu bestätigen.
1. Sie können jetzt mit dem [Hinzufügen eines Zielgruppe Framework](/help/sites-administering/target-configuring.md#adding-a-target-framework) fortfahren, um ContextHub- oder ClientContext-Parameter zu konfigurieren, die an Zielgruppe gesendet werden. Beachten Sie, dass dies möglicherweise nicht erforderlich ist, um AEM Erlebnisfragmente in die Zielgruppe zu exportieren.

