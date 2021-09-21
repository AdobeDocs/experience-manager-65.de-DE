---
title: Integration mit Adobe Target über Adobe I/O
seo-title: Integration with Adobe Target using Adobe I/O
description: Erfahren Sie mehr über die Integration von AEM mit Adobe Target mithilfe von Adobe I/O.
seo-description: Learn about integrating AEM with Adobe Target using Adobe I/O
uuid: dd4ed638-e182-4d7e-9c98-282431812467
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: integration
discoiquuid: 3b9285db-8fba-4d12-8f52-41daa50a5403
docset: aem65
exl-id: ba7abc53-7db8-41b1-a0fa-4e4dbbeca402
source-git-commit: baacb6623757c4a7a67ae2be4232a36c4a509b69
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 18%

---

# Integration mit Adobe Target über Adobe I/O{#integration-with-adobe-target-using-adobe-i-o}

Die Integration von AEM mit Adobe Target über die Target Standard-API erfordert die Konfiguration von Adobe IMS (Identity Management-System) und Adobe I/O.

>[!NOTE]
>
>Die Unterstützung für die Adobe Target Standard-API ist in AEM 6.5 neu. Die Target Standard-API verwendet die IMS-Authentifizierung.
>
>Die Verwendung der Adobe Target Classic-API in AEM wird aus Gründen der Abwärtskompatibilität weiterhin unterstützt. Die [Target Classic-API verwendet die Authentifizierung von Benutzeranmeldeinformationen](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).
>
>Die API-Auswahl wird von der Authentifizierungsmethode gesteuert, die für die AEM/Target-Integration verwendet wird.
>Siehe auch Abschnitt [Mandantenkennung und Clientcode](#tenant-client) .

## Voraussetzungen {#prerequisites}

Bevor Sie mit diesem Verfahren beginnen:

* [Adobe ](https://helpx.adobe.com/de/contact/enterprise-support.ec.html) Support muss Ihr Konto für Folgendes bereitstellen:

   * Adobe Console
   * Adobe I/O
   * Adobe Target und
   * Adobe IMS (Identity Management System)

* Der Systemadministrator Ihres Unternehmens sollte die Admin Console verwenden, um die erforderlichen Entwickler in Ihrem Unternehmen den relevanten Produktprofilen hinzuzufügen.

   * Dadurch erhalten die spezifischen Entwickler Berechtigungen, Integrationen in Adobe I/O zu aktivieren.
   * Weitere Informationen finden Sie unter [Verwalten von Entwicklern](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html).


## Konfigurieren einer IMS-Konfiguration - Generieren eines öffentlichen Schlüssels {#configuring-an-ims-configuration-generating-a-public-key}

Der erste Schritt der Konfiguration besteht darin, eine IMS-Konfiguration in AEM zu erstellen und den öffentlichen Schlüssel zu generieren.

1. Öffnen Sie AEM Menü **Tools** .
1. Wählen Sie im Abschnitt **Sicherheit** **Adobe IMS-Konfigurationen** aus.
1. Wählen Sie **Erstellen** aus, um die **Konfiguration des technischen Adobe IMS-Kontos** zu öffnen.
1. Wählen Sie mithilfe der Dropdown-Liste unter **Cloud-Konfiguration** **Adobe Target** aus.
1. Aktivieren Sie **Erstellen Sie ein neues Zertifikat** und geben Sie einen neuen Alias ein.
1. Bestätigen Sie mit **Zertifikat erstellen**.

   ![](assets/integrate-target-io-01.png)

1. Wählen Sie **Download** (oder **Öffentlichen Schlüssel herunterladen**), um die Datei auf Ihr lokales Laufwerk herunterzuladen, damit sie bei der Konfiguration der Adobe I/O für die Adobe Target-Integration mit AEM](#configuring-adobe-i-o-for-adobe-target-integration-with-aem) verwendet werden kann.[

   >[!CAUTION]
   >
   >Lassen Sie diese Konfiguration geöffnet. Sie wird erneut benötigt, wenn [Sie die IMS-Konfiguration in AEM](#completing-the-ims-configuration-in-aem) abschließen.

   ![](assets/integrate-target-io-02.png)

## Adobe I/O für Adobe Target-Integration mit AEM konfigurieren {#configuring-adobe-i-o-for-adobe-target-integration-with-aem}

Sie müssen das Adobe I/O Project (Integration) mit Adobe Target erstellen, das AEM verwenden wird, und dann die erforderlichen Berechtigungen zuweisen.

### Erstellen des Projekts {#creating-the-project}

Öffnen Sie die Adobe I/O Console, um ein I/O-Projekt mit Adobe Target zu erstellen, das AEM verwenden wird:

>[!NOTE]
>
>Siehe auch die [Adobe I/O-Tutorials](https://www.adobe.io/apis/experienceplatform/home/tutorials/alltutorials.html).

1. Öffnen Sie die Projektekonsole der Adobe I/O:

   [https://console.adobe.io/projects](https://console.adobe.io/projects)

1. Alle Projekte, die Sie haben, werden angezeigt. Wählen Sie **Neues Projekt erstellen** - der Speicherort und die Verwendung hängen von Folgendem ab:

   * Wenn Sie noch kein Projekt haben, wird **Neues Projekt erstellen** zentriert, unten.
      ![Neues Projekt erstellen - erstes Projekt](assets/integration-target-io-02.png)
   * Wenn Sie bereits über vorhandene Projekte verfügen, werden diese aufgelistet und **Neues Projekt erstellen** wird oben rechts angezeigt.
      ![Neues Projekt erstellen - Mehrere Projekte](assets/integration-target-io-03.png)


1. Wählen Sie **Zum Projekt hinzufügen** gefolgt von **API**:

   ![](assets/integration-target-io-10.png)

1. Wählen Sie **Adobe Target** und dann **Next**:

   >[!NOTE]
   >
   >Wenn Sie Adobe Target abonniert haben, es jedoch nicht aufgeführt sehen, sollten Sie die [Voraussetzungen](#prerequisites) überprüfen.

   ![](assets/integration-target-io-12.png)

1. **Laden Sie den öffentlichen Schlüssel** hoch und fahren Sie nach Abschluss mit  **Weiter** fort:

   ![](assets/integration-target-io-13.png)

1. Überprüfen Sie die Anmeldeinformationen und fahren Sie mit **Next** fort:

   ![](assets/integration-target-io-15.png)

1. Wählen Sie die erforderlichen Produktprofile aus und fahren Sie mit **Save configured API** fort:

   >[!NOTE]
   >
   >Welche Produktprofile mit angezeigt werden, hängt davon ab, ob Sie über Folgendes verfügen:
   >
   >* Adobe Target Standard - nur **Der Standardarbeitsbereich** ist verfügbar.
   >* Adobe Target Premium - alle verfügbaren Arbeitsbereiche werden aufgelistet, wie unten dargestellt


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

1. Navigieren Sie zu **Produkte** (obere Symbolleiste) und wählen Sie **Adobe Target - &lt;*Ihre-Mandanten-ID*** (aus dem linken Bereich).
1. Wählen Sie **Produktprofile** und dann Ihren gewünschten Arbeitsbereich aus der angezeigten Liste. Beispiel: Standardarbeitsbereich.
1. Wählen Sie **Integrationen** und dann die erforderliche Integrationskonfiguration.
1. Wählen Sie **Editor** als **Produktrolle** aus. anstelle von **Beobachter**.

## Für das Adobe I/O Integration Project gespeicherte Details {#details-stored-for-the-adobe-io-integration-project}

In der Adobe I/O-Projektekonsole wird eine Liste aller Integrationsprojekte angezeigt:

* [https://console.adobe.io/projects](https://console.adobe.io/projects)

Wählen Sie **Ansicht** (rechts neben einem bestimmten Projekteintrag) aus, um weitere Details zur Konfiguration anzuzeigen. Dazu gehören:

* Projektübersicht
* Insights
* Berechtigungen
   * Dienstkonto (JWT)
      * Details zu Berechtigungen
      * JWT generieren
* APIS
   * Beispiel: Adobe Target

Einige davon müssen Sie in AEM die Adobe I/O-Integration für Target abschließen.

## Abschließen der IMS-Konfiguration in AEM {#completing-the-ims-configuration-in-aem}

Kehren Sie zu AEM zurück und Sie können die IMS-Konfiguration abschließen, indem Sie erforderliche Werte aus der Adobe I/O-Integration für Target hinzufügen:

1. Kehren Sie zur [IMS-Konfiguration zurück, die in AEM](#configuring-an-ims-configuration-generating-a-public-key) geöffnet ist.
1. Wählen Sie **Weiter** aus.

1. Hier können Sie die [Details aus Adobe I/O](#details-stored-for-the-adobe-io-integration-project) verwenden:

   * **Titel**: Ihr Text.
   * **Autorisierungsserver**: Kopieren/fügen Sie dies aus der  `"aud"` Zeile des  **** Abschnitts Payload unten ein, z. B.  `"https://ims-na1.adobelogin.com"` im unten stehenden Beispiel
   * **API-Schlüssel**: Kopieren Sie dies aus dem  [](#details-stored-for-the-adobe-io-integration-project) Übersichtsabschnitt der Adobe I/O-Integration für Target
   * **Client Secret**: Generieren Sie dies im  [](#details-stored-for-the-adobe-io-integration-project) Übersichtsabschnitt der Adobe I/O-Integration für Target und kopieren Sie
   * **Nutzlast**: Kopieren Sie dies aus dem  [Abschnitt ](#details-stored-for-the-adobe-io-integration-project) JWT generieren der Adobe I/O-Integration für Target

   ![](assets/integrate-target-io-10.png)

1. Bestätigen Sie mit **Erstellen**.

1. Ihre Adobe Target-Konfiguration wird in der AEM Console angezeigt.

   ![](assets/integrate-target-io-11.png)

## IMS-Konfiguration bestätigen {#confirming-the-ims-configuration}

So überprüfen Sie, ob die Konfiguration erwartungsgemäß funktioniert:

1. Öffnen Sie:

   * `https://localhost<port>/libs/cq/adobeims-configuration/content/configurations.html`

   Zum Beispiel:

   * `https://localhost:4502/libs/cq/adobeims-configuration/content/configurations.html`


1. Wählen Sie Ihre Konfiguration aus.
1. Wählen Sie **Health** aus der Symbolleiste, gefolgt von **Check**.

   ![](assets/integrate-target-io-12.png)

1. Bei erfolgreicher Ausführung wird die Meldung angezeigt:

   ![](assets/integrate-target-io-13.png)

## Konfigurieren des Adobe Target-Cloud Service {#configuring-the-adobe-target-cloud-service}

Auf die Konfiguration kann nun verwiesen werden, damit ein Cloud Service die Target Standard-API verwenden kann:

1. Öffnen Sie das Menü **Tools** . Wählen Sie dann im Bereich **Cloud Services** die Option **Ältere Cloud Services** aus.
1. Scrollen Sie nach unten zu **Adobe Target** und wählen Sie **Jetzt konfigurieren** aus.

   Das Dialogfeld **Konfiguration erstellen** wird geöffnet.

1. Geben Sie einen **Titel** und ggf. einen **Namen** ein (wenn Sie das Feld leer lassen, wird dies aus dem Titel generiert).

   Sie können auch die gewünschte Vorlage auswählen (wenn mehrere Vorlagen verfügbar sind).

1. Bestätigen Sie mit **Erstellen**.

   Das Dialogfeld **Komponente bearbeiten** wird geöffnet.

1. Geben Sie die Details auf der Registerkarte **Adobe Target Settings** ein:

   * **Authentifizierung**: IMS
   * **Mandantenkennung**: die Adobe IMS-Mandantenkennung. Siehe auch Abschnitt [Mandantenkennung und Clientcode](#tenant-client) .

      >[!NOTE]
      >
      >Für IMS muss dieser Wert aus Target selbst übernommen werden. Sie können sich bei Target anmelden und die Mandantenkennung aus der URL extrahieren.
      >
      >Wenn die URL beispielsweise:
      >
      >`https://experience.adobe.com/#/@yourtenantid/target/activities`
      >
      >Dann würden Sie `yourtenantid` verwenden.
   * **Client-Code**: Siehe  [Mandanten-ID und Client-](#tenant-client) Code.
   * **IMS-Konfiguration**: den Namen der IMS-Konfiguration auswählen
   * **API-Typ**: REST
   * **A4T-Analyse-Cloud-Konfiguration**: Wählen Sie die Analyse-Cloud-Konfiguration aus, die für Target-Aktivitätsziele und -metriken verwendet wird. Sie benötigen sie, wenn Sie Adobe Analytics als Quelle für die Berichterstellung für bestimmte Inhalte verwenden. Wenn Ihre Cloud-Konfiguration nicht angezeigt wird, finden Sie weitere Informationen unter [Konfigurieren der A4T-Analytics Cloud-Konfiguration](/help/sites-administering/target-configuring.md#configuring-a-t-analytics-cloud-configuration).
   * **Verwenden Sie genaues Targeting**: Standardmäßig ist dieses Kontrollkästchen aktiviert. Bei Aktivierung dieser Option wird für die Cloud Service-Konfiguration gewartet, bis das Laden des Kontexts erfolgt ist, bevor der Inhalt geladen wird. Siehe Hinweis unten.
   * **Segmente aus Adobe Target synchronisieren**: Wählen Sie diese Option aus, um in Target definierte Segmente herunterzuladen und in AEM zu verwenden. Sie müssen diese Option auswählen, wenn die Eigenschaft „API-Typ“ auf „REST“ festgelegt ist, da Inline-Segmente nicht unterstützt werden und Sie immer Segmente aus Target verwenden müssen. (Beachten Sie, dass der AEM-Begriff „Segment“ hier dem Target-Begriff „Zielgruppe“ entspricht.)
   * **Client-Bibliothek**: Wählen Sie aus, ob die AT.js-Client-Bibliothek oder mbox.js (veraltet) verwendet werden soll.
   * **Verwenden Sie Tag Management System zur Bereitstellung der Client-Bibliothek**: Verwenden Sie DTM (nicht mehr unterstützt), Adobe Launch oder ein anderes Tag-Management-System.
   * **Benutzerdefinierte at.js**: Lassen Sie das Feld leer, wenn Sie das Kontrollkästchen Tag-Management aktiviert haben oder die standardmäßige at.js-Datei verwenden möchten. Alternativ hierzu können Sie Ihre benutzerdefinierte Datei „AT.js“ hochladen. Sie wird nur angezeigt, wenn Sie „AT.js“ ausgewählt haben.

   >[!NOTE]
   >
   >[Die Konfiguration eines Cloud Service zur Verwendung der Target Classic-](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target) API wird nicht mehr unterstützt (verwendet die Registerkarte Adobe Recommendations-Einstellungen ).
1. Klicken Sie auf **Mit Target** verbinden , um die Verbindung mit Adobe Target zu initialisieren.

   Wenn die Verbindung erfolgreich hergestellt wurde, wird die Meldung **Verbindung erfolgreich** angezeigt.

1. Wählen Sie **OK** in der Nachricht, gefolgt von **OK** im Dialogfeld, um die Konfiguration zu bestätigen.
1. Sie können jetzt mit [Hinzufügen eines Target-Frameworks](/help/sites-administering/target-configuring.md#adding-a-target-framework) fortfahren, um ContextHub- oder ClientContext-Parameter zu konfigurieren, die an Target gesendet werden. Beachten Sie, dass dies möglicherweise nicht für den Export AEM Experience Fragments in Target erforderlich ist.

### Mandanten-ID und Client-Code {#tenant-client}

Mit [Adobe Experience Manager 6.5.8.0](/help/release-notes/sp-release-notes.md) wurde das Feld Client-Code zum Target-Konfigurationsfenster hinzugefügt.

Beachten Sie beim Konfigurieren der Felder Mandanten-ID und Client-Code Folgendes:

1. Für die meisten Kunden sind die Mandanten-ID und der Clientcode identisch. Das bedeutet, dass beide Felder die gleichen Werte enthalten. Achten Sie darauf, dass Sie die Mandanten-ID in beide Felder eingeben.
2. Sollten Sie über ältere Werte verfügen, können Sie auch verschiedene Werte in die Felder „Mandanten-ID“ und „Clientcode“ eingeben.

Beachten Sie in beiden Fällen Folgendes:

* Standardmäßig wird der Clientcode (wenn er zuerst eingegeben wird) automatisch in das Feld „Mandanten-ID“ kopiert.
* Sie haben die Möglichkeit, den Standardwert für die Mandanten-ID zu ändern.
* Dementsprechend basieren die Backend-Target-Aufrufe auf der Mandanten-ID und die Client-seitigen Target-Aufrufe auf dem Clientcode.

Wie bereits erwähnt, ist der erste Fall der häufigste Fall für AEM 6.5. Stellen Sie sicher, dass **beide**-Felder je nach Ihren Anforderungen die richtigen Informationen enthalten.

>[!NOTE]
>
> Wenn Sie eine bestehende Target-Konfiguration ändern möchten:
>
> 1. Geben Sie die Mandanten-ID erneut ein.
> 2. Stellen Sie zu Target eine neue Verbindung her.
> 3. Speichern Sie die Konfiguration.

