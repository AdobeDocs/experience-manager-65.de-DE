---
title: Integrieren mit Salesforce
description: Erfahren Sie mehr über die Integration von Adobe Experience Manager (AEM) in Salesforce.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 0f3aaa0a-ccfb-4162-97a6-ee5485595d28
source-git-commit: c7c32130a3257c14c98b52f9db31d80587d7993a
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 29%

---


# Integrieren mit Salesforce {#integrating-with-salesforce}

Die Integration von Salesforce in Adobe Experience Manager (AEM) bietet Lead-Management-Funktionen und nutzt die vorhandenen Funktionen, die Salesforce standardmäßig bereitstellt. Sie können AEM konfigurieren, um Leads in Salesforce zu posten und Komponenten zu erstellen, die direkt über Salesforce auf Daten zugreifen.

Die bidirektionale und erweiterbare Integration zwischen AEM und Salesforce ermöglicht Folgendes:

* Organisationen, Daten vollständig zu verwenden und zu ändern, um das Kundenerlebnis zu verbessern.
* Interaktion von Marketing- zu Verkaufsaktivitäten.
* Organisationen zum automatischen Übertragen und Empfangen von Daten aus einem Salesforce-Datenspeicher.

Dieses Dokument beschäftigt sich mit den folgenden Themen:

* wie Salesforce-Cloud Service konfiguriert werden (konfigurieren Sie AEM für die Integration mit Salesforce).
* Verwendung von Salesforce-Lead-/Kontaktinformationen in ClientContext und zur Personalisierung.
* wie Sie das Salesforce-Workflow-Modell verwenden, um AEM Benutzer als Leads zu Salesforce zu posten.
* wie Sie eine Komponente erstellen, die Daten aus Salesforce anzeigt.

## AEM zur Integration mit Salesforce konfigurieren {#configuring-aem-to-integrate-with-salesforce}

Um AEM für die Integration mit Salesforce zu konfigurieren, konfigurieren Sie zunächst eine Fernzugriffsanwendung in Salesforce. Anschließend konfigurieren Sie den Salesforce-Cloud-Service so, dass er auf diese Remote-Zugriffsanwendung verweist.

>[!NOTE]
>
>Sie können ein kostenloses Entwicklerkonto in Salesforce erstellen.

So konfigurieren Sie AEM für die Integration mit Salesforce:

>[!CAUTION]
>
>Installieren Sie die [Salesforce Force-API](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=salesforce*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=2&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcom.adobe.cq.mcm.salesforce.content-1.0.4.zip) Integrationspaket erstellen, bevor Sie mit dem Verfahren fortfahren. Weitere Informationen zum Arbeiten mit Paketen finden Sie auf der Seite [Arbeiten mit Paketen](/help/sites-administering/package-manager.md#package-share).

1. Navigieren Sie in AEM zu **Cloud-Services**. Klicken Sie unter „Services von Dritten“ auf **Jetzt konfigurieren** unter **Salesforce**.

   ![chlimage_1-70](assets/chlimage_1-70.png)

1. Erstellen Sie beispielsweise eine Konfiguration. **Entwickler**.

   >[!NOTE]
   >
   >Die neue Konfiguration leitet zu einer neuen Seite um: **http://localhost:4502/etc/cloudservices/salesforce/developer.html**. Dies ist genau der Wert, den Sie beim Erstellen der Remote-Zugriffsanwendung in Salesforce in der Callback-URL angeben müssen. Diese Werte müssen übereinstimmen.

1. Melden Sie sich bei Ihrem Salesforce-Konto an (oder erstellen Sie eines unter [https://developer.salesforce.com](https://developer.salesforce.com).
1. Navigieren Sie in Salesforce zu **Erstellen** > **Apps** um **Connected Apps** (In früheren Versionen von Salesforce war der Workflow **Bereitstellen** > **Remote Access**).
1. Klicks **Neu** damit Sie AEM mit Salesforce verbinden können.

   ![chlimage_1-71](assets/chlimage_1-71.png)

1. Geben Sie die **Name der Connected App**, **API-Name**, und **Kontakt-E-Mail**. Wählen Sie die **Aktivieren der OAuth-Einstellungen** aktivieren und die **Callback-URL** und fügen Sie einen OAuth-Bereich hinzu (z. B. vollständigen Zugriff). Die Rückruf-URL sieht in etwa folgendermaßen aus: `http://localhost:4502/etc/cloudservices/salesforce/developer.html`

   Ändern Sie den Server-Namen/die Port-Nummer und den Seitennamen, sodass sie Ihrer Konfiguration entsprechen.

   ![chlimage_1-72](assets/chlimage_1-72.png)

1. Klicks **Speichern** , um die Salesforce-Konfiguration zu speichern. Salesforce erstellt einen **Kundenschlüssel** und ein **Kundengeheimnis**, die Sie für die AEM-Konfiguration benötigen.

   ![chlimage_1-73](assets/chlimage_1-73.png)

   >[!NOTE]
   >
   >Warten Sie einige Minuten (bis zu 15 Minuten), bis die Fernzugriffsanwendung in Salesforce aktiviert wird.

1. Navigieren Sie in AEM zu **Cloud Service** und navigieren Sie zur zuvor erstellten Salesforce-Konfiguration (z. B. **Entwickler**). Klicks **Bearbeiten** und geben Sie den Kundenschlüssel und das Kundengeheimnis von salesforce.com ein.

   ![chlimage_1-15](assets/chlimage_1-15.jpeg)

   | Login-URL | Dies ist der Salesforce-Autorisierungsendpunkt. Der Wert ist bereits ausgefüllt und kann in den meisten Fällen verwendet werden. |
   |---|---|
   | Kundenschlüssel | Geben Sie den Wert ein, der von der Seite &quot;Registrierung für Remote-Zugriffsanwendungen&quot;unter salesforce.com abgerufen wurde. |
   | Kundengeheimnis | Geben Sie den Wert ein, der von der Seite &quot;Registrierung für Remote-Zugriffsanwendungen&quot;unter salesforce.com abgerufen wurde. |

1. Klicks **Mit Salesforce verbinden** um eine Verbindung herzustellen. Salesforce fordert Sie auf, dass Ihre Konfiguration eine Verbindung zu Salesforce herstellt.

   ![chlimage_1-74](assets/chlimage_1-74.png)

   In AEM wird ein Bestätigungsdialogfeld mit der Meldung geöffnet, dass die Verbindung hergestellt wurde.

1. Navigieren Sie zur Stammseite Ihrer Website und klicken Sie auf **Seiteneigenschaften**. Wählen Sie dann **Cloud-Services** aus und fügen Sie **Salesforce** hinzu. Wählen Sie die richtige Konfiguration aus (beispielsweise **developer**).

   ![chlimage_1-75](assets/chlimage_1-75.png)

   Jetzt können Sie das Workflow-Modell verwenden, um Leads an Salesforce zu posten und Komponenten zu erstellen, die auf Daten aus Salesforce zugreifen.

## AEM Benutzer als Salesforce Leads exportieren {#exporting-aem-users-as-salesforce-leads}

Wenn Sie einen AEM-Benutzer als Salesforce-Lead exportieren möchten, konfigurieren Sie den Workflow so, dass Leads an Salesforce gepostet werden.

So exportieren Sie AEM Benutzer als Salesforce-Leads:

1. Navigieren Sie zum Salesforce-Workflow unter `http://localhost:4502/workflow`. Klicken Sie dazu mit der rechten Maustaste auf den Workflow **Salesforce.com-Export** und klicken Sie dann auf **Start**.

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Wählen Sie den AEM Benutzer, den Sie als Lead erstellen möchten, als **Nutzlast** für diesen Workflow (Startseite -> Benutzer). Stellen Sie sicher, dass Sie den Profilknoten des Benutzers auswählen, da er Informationen wie **givenName**, und  **familyName**, die Salesforce-Leads zugeordnet sind **FirstName** und **LastName** -Felder.

   ![chlimage_1-77](assets/chlimage_1-77.png)

   >[!NOTE]
   >
   >Vor Beginn dieses Workflows gibt es bestimmte Pflichtfelder, die ein Lead-Knoten in AEM vor der Veröffentlichung bei Salesforce aufweisen muss. Diese **givenName**, **familyName**, **Firma**, und **email**. Eine vollständige Liste der Zuordnungen zwischen AEM Benutzer und Salesforce-Lead finden Sie unter [Zuordnen der Konfiguration zwischen AEM Benutzer und Salesforce Lead.](#mapping-configuration-between-aem-user-and-salesforce-lead)

1. Klicken Sie auf **OK**. Die Benutzerinformationen werden nach salesforce.com exportiert. Sie können es unter salesforce.com überprüfen.

   >[!NOTE]
   >
   >Die Fehlerprotokolle zeigen Ihnen, ob ein Lead importiert wird. Weitere Informationen finden Sie im Fehlerprotokoll .

### Konfigurieren des Salesforce.com Export-Workflows {#configuring-the-salesforce-com-export-workflow}

Konfigurieren Sie bei Bedarf den Workflow Salesforce.com Export , um ihn mit der richtigen Salesforce.com Konfiguration abzugleichen oder um andere Änderungen vorzunehmen.

So konfigurieren Sie den Salesforce.com Export-Workflow:

1. Navigieren Sie zu `http://localhost:4502/cf#/etc/workflow/models/salesforce-com-export.html.`

   ![chlimage_1-16](assets/chlimage_1-16.jpeg)

1. Öffnen Sie den Schritt „Salesforce.com-Export“ und wählen Sie die Registerkarte **Argumente** aus. Stellen Sie sicher, dass die richtige Konfiguration ausgewählt ist, und klicken Sie auf **OK**. Aktivieren Sie zudem das Kontrollkästchen, wenn Sie möchten, dass der Workflow einen Lead, der in Salesforce gelöscht wurde, neu erstellt.

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

   ![chlimage_1-79](assets/chlimage_1-79.png)

### Zuordnungskonfiguration zwischen AEM-Benutzer und Salesforce-Lead {#mapping-configuration-between-aem-user-and-salesforce-lead}

Um die aktuelle Zuordnungskonfiguration zwischen einem AEM-Benutzer und einem Salesforce-Lead einzusehen oder zu bearbeiten, öffnen Sie den Konfigurations-Manager unter `https://<hostname>:<port>/system/console/configMgr` und suchen Sie nach **Salesforce-Lead-Zuordnungskonfiguration**.

1. Öffnen Sie den Konfigurations-Manager. Dazu klicken Sie auf **Web-Konsole** oder Sie gehen direkt zu `https://<hostname>:<port>/system/console/configMgr.`
1. Suchen Sie nach **Salesforce-Lead-Zuordnungskonfiguration**.

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Ändern Sie die Zuordnungen nach Bedarf. Die Standardzuordnung folgt dem Muster **aemUserAttribute=sfLeadAttribute**. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

## Konfigurieren des Salesforce ClientContext Store {#configuring-salesforce-client-context-store}

Der Salesforce-Client-Kontextspeicher zeigt zusätzliche Informationen zum derzeit angemeldeten Benutzer an, als bereits in AEM verfügbar sind. Diese zusätzlichen Informationen werden abhängig von der Verbindung des Benutzers mit Salesforce von Salesforce abgerufen.

Konfigurieren Sie dazu Folgendes:

1. Verknüpfen Sie einen AEM mit einer Salesforce-ID über die Salesforce Connect-Komponente.
1. Fügen Sie die Salesforce-Profildaten zur Client-Kontextseite hinzu, damit Sie konfigurieren können, welche Eigenschaften angezeigt werden sollen.
1. (Optional) Erstellen Sie ein Segment, das die Daten aus dem Salesforce Client Context Store verwendet.

### Verknüpfen eines AEM Benutzers mit einer Salesforce ID {#linking-an-aem-user-with-a-salesforce-id}

Ordnen Sie einen AEM Benutzer einer Salesforce-ID zu, damit Sie sie im Client-Kontext laden können. In einem realen Szenario würden Sie basierend auf bekannten Benutzerdaten eine Verknüpfung mit einer Validierung herstellen. Zu Demonstrationszwecken verwenden Sie in diesem Verfahren die **Salesforce Connect** -Komponente.

1. Navigieren Sie in AEM zu einer Website, melden Sie sich an und ziehen Sie die **Salesforce Connect** -Komponente aus dem Sidekick.

   >[!NOTE]
   >
   >Wenn die Variable **Salesforce Connect** -Komponente nicht verfügbar ist, navigieren Sie zum **Design** anzeigen und auswählen, um sie im **Bearbeiten** anzeigen.

   ![chlimage_1-17](assets/chlimage_1-17.jpeg)

   Wenn Sie die Komponente auf die Seite ziehen, zeigt diese **Verknüpfung zu Salesforce=Aus** an.

   ![chlimage_1-81](assets/chlimage_1-81.png)

   >[!NOTE]
   >
   >Diese Komponente dient nur zu Demonstrationszwecken. Für reale Szenarien gibt es einen weiteren Prozess, um Benutzer mit Leads zu verknüpfen/zuzuordnen.

1. Nachdem Sie die Komponente auf die Seite gezogen haben, öffnen Sie sie, um sie zu konfigurieren. Wählen Sie die Konfiguration, den Kontakttyp und den Salesforce-Lead oder -Kontakt aus und klicken Sie auf **OK**.

   ![chlimage_1-82](assets/chlimage_1-82.png)

   AEM verknüpft den Benutzer mit dem Salesforce-Kontakt oder -Lead.

   ![chlimage_1-83](assets/chlimage_1-83.png)

### Hinzufügen von Salesforce-Daten zu ClientContext {#adding-salesforce-data-to-client-context}

Sie können Benutzerdaten aus Salesforce in ClientContext laden, um sie für die Personalisierung zu verwenden:

1. Öffnen Sie den Client-Kontext, den Sie erweitern möchten, indem Sie dort z. B. navigieren. `http://localhost:4502/etc/clientcontext/default/content.html.`

   ![chlimage_1-18](assets/chlimage_1-18.jpeg)

1. Ziehen Sie die **Salesforce-Profildaten**-Komponente auf den ClientContext.

   ![chlimage_1-19](assets/chlimage_1-19.jpeg)

1. Öffnen Sie die Komponente, indem Sie darauf doppelklicken. Auswählen **Element hinzufügen** und wählen Sie eine Eigenschaft aus der Dropdownliste aus. Fügen Sie beliebig viele Eigenschaften hinzu und wählen Sie **OK**.

   ![chlimage_1-84](assets/chlimage_1-84.png)

1. Jetzt können Sie die Salesforce-spezifischen Eigenschaften aus Salesforce im ClientContext sehen.

   ![chlimage_1-85](assets/chlimage_1-85.png)

### Erstellen eines Segments mithilfe von Daten aus dem Salesforce Client Context Store {#building-a-segment-using-data-from-salesforce-client-context-store}

Sie können ein Segment erstellen, das Daten aus dem Salesforce Client Context Store verwendet. Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zur Segmentierung in AEM, entweder indem Sie zu **Tools** > **Segmentierung** oder aber zu [http://localhost:4502/miscadmin#/etc/segmentation](http://localhost:4502/miscadmin#/etc/segmentation) wechseln.
1. Erstellen oder aktualisieren Sie ein Segment, um Daten aus Salesforce einzuschließen. Weitere Informationen finden Sie unter [Segmentierung](/help/sites-administering/campaign-segmentation.md).

## Suchen nach Leads {#searching-leads}

AEM wird mit einer Beispielsuchkomponente geliefert, die Leads in Salesforce gemäß den angegebenen Kriterien durchsucht. Diese Komponente zeigt Ihnen, wie Sie mit der Salesforce REST API nach Salesforce-Objekten suchen können. Um einen Aufruf an salesforce.com Trigger, verknüpfen Sie eine Seite mit einer Salesforce-Konfiguration.

>[!NOTE]
>
>Dies ist eine Beispielkomponente, die Ihnen zeigt, wie Sie die Salesforce REST API zum Abfragen von Salesforce-Objekten verwenden. Verwenden Sie es als Beispiel, um komplexere Komponenten basierend auf Ihren Anforderungen zu erstellen.

So verwenden Sie diese Komponente:

1. Navigieren Sie zu der Seite, auf der Sie diese Konfiguration verwenden möchten. Öffnen Sie die Seiteneigenschaften und wählen Sie **Cloud Service.** Klicks **Dienste hinzufügen** und wählen **Salesforce** und klicken Sie auf **OK**.

   ![chlimage_1-20](assets/chlimage_1-20.jpeg)

1. Ziehen Sie die Salesforce-Suchkomponente auf die Seite (sofern sie aktiviert wurde). Um sie zu aktivieren, wechseln Sie zum Designmodus und fügen Sie ihn dem entsprechenden Bereich hinzu).

   ![chlimage_1-21](assets/chlimage_1-21.jpeg)

1. Öffnen Sie die Suchkomponente und legen Sie die Suchparameter fest. Klicken Sie dann auf **OK**.

   ![chlimage_1-86](assets/chlimage_1-86.png)

1. AEM zeigt die in Ihrer Suchkomponente aufgeführten Leads an, die den angegebenen Kriterien entsprechen.

   ![chlimage_1-87](assets/chlimage_1-87.png)
