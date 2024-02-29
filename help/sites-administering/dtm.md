---
title: Integrieren mit Adobe Dynamic Tag Management
description: Erfahren Sie mehr über die Integration mit Adobe Dynamic Tag Management.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 1e0821f5-627f-4262-ba76-62303890e112
source-git-commit: 4289c68feb51842b5649f7cff73c5c4bc38add6c
workflow-type: tm+mt
source-wordcount: '2146'
ht-degree: 46%

---

# Integrieren mit Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

Integrieren Sie [Adobe Dynamic Tag Management](https://business.adobe.com/de/products/experience-platform/adobe-experience-platform.html) mit AEM, sodass Sie Ihre Dynamic Tag Management-Webeigenschaften für das Tracking von AEM Sites verwenden können. Dynamic Tag Management ermöglicht Marketingexperten die Verwaltung von Tags für die Datensammlung und die Verteilung von Daten auf Systeme für Digital Marketing. Verwenden Sie Dynamic Tag Management zum Beispiel für die Erfassung der Nutzungsdaten zu Ihrer AEM-Website und die Verteilung der Daten für die Analyse in Adobe Analytics oder Adobe Target.

Erstellen Sie vor der Integration die Dynamic Tag Management [Webeigenschaft](https://microsite.omniture.com/t2/help/en_US/dtm/#Web_Properties) , der die Domäne Ihrer AEM verfolgt. Die [Hostingoptionen](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) der Webeigenschaft müssen so konfiguriert werden, dass Sie AEM für den Zugriff auf die Dynamic Tag Management-Bibliotheken konfigurieren können.

Nach der Konfiguration der Integration müssen Sie bei Änderungen an den Dynamic Tag Management-Bereitstellungswerkzeugen und -regeln die Dynamic Tag Management-Konfiguration in AEM nicht ändern. Die Änderungen stehen AEM automatisch zur Verfügung.

>[!NOTE]
>
>Wenn Sie DTM mit einer benutzerdefinierten Proxy-Konfiguration verwenden, konfigurieren Sie beide HTTP-Client-Proxy-Konfigurationen, da einige Funktionen von AEM die 3.x-APIs und andere die 4.x-APIs verwenden:
>
>* 3.x wird mit [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) konfiguriert.
>* 4.x wird mit [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator) konfiguriert.
>

## Bereitstellungsoptionen {#deployment-options}

Die folgenden Bereitstellungsoptionen wirken sich auf die Konfiguration der Integration mit Dynamic Tag Management aus.

### Dynamic Tag Management Hosting {#dynamic-tag-management-hosting}

AEM unterstützt Dynamic Tag Management, das in der Cloud gehostet oder auf AEM gehostet wird.

* Cloud-gehostet: Die Dynamic Tag Management JavaScript-Bibliotheken werden in der Cloud gespeichert und Ihre AEM verweisen direkt auf sie.
* AEM gehostet: Dynamic Tag Management generiert JavaScript-Bibliotheken. AEM verwendet ein Workflow-Modell zum Abrufen und Installieren der Bibliotheken.

Der Hosting-Typ, den Ihre Implementierung verwendet, bestimmt einige der Konfigurations- und Implementierungsaufgaben, die Sie ausführen. Informationen zu den Hosting-Optionen finden Sie unter [Hosting - Registerkarte &quot;Einbetten&quot;](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) in der Hilfe zu Dynamic Tag Management.

### Staging- und Produktionsbibliothek {#staging-and-production-library}

Entscheiden Sie, ob Ihre AEM-Autoreninstanz den Staging- oder Produktions-Code von Dynamic Tag Management verwenden soll.

Normalerweise verwendet Ihre Autoreninstanz die Dynamic Tag Management-Staging-Bibliotheken und die Produktionsinstanz verwendet die Produktionsbibliotheken. Mit diesem Szenario können Sie die Autoreninstanz verwenden, um nicht genehmigte Dynamic Tag Management-Konfigurationen zu testen.

Bei Bedarf kann Ihre Autoreninstanz die Produktionsbibliotheken nutzen. Es sind Webbrowser-Plug-ins verfügbar, die Ihnen den Wechsel zwischen der Verwendung der Staging-Bibliotheken zu Testzwecken ermöglichen, wenn die Bibliotheken in der Cloud gehostet werden.

### Verwenden des Dynamic Tag Management-Bereitstellungs-Hooks {#using-the-dynamic-tag-management-deployment-hook}

Wenn AEM die Dynamic Tag Management-Bibliotheken hostet, können Sie den Bereitstellungs-Hook-Dienst für Dynamic Tag Management verwenden, um Bibliotheksaktualisierungen automatisch an AEM zu pushen. Das Pushen von Bibliothekaktualisierungen erfolgt, wenn Änderungen an den Bibliotheken vorgenommen werden – so zum Beispiel, wenn die Dynamic Tag Management-Webeigenschaften bearbeitet werden.

Um den Bereitstellungs-Hook zu verwenden, muss Dynamic Tag Management eine Verbindung zur AEM-Instanz herstellen können, in der die Bibliotheken gehostet werden. [Zugriff auf AEM aktivieren](/help/sites-administering/dtm.md#enabling-access-for-the-deployment-hook-service) für die Dynamic Tag Management-Server.

Unter manchen Umständen kann AEM nicht erreichbar sein, so zum Beispiel, wenn AEM sich hinter einer Firewall befindet. In diesen Fällen können Sie die Option Abruf-Import-Tool von AEM verwenden, um die Bibliotheken regelmäßig abzurufen. Ein Cron-Auftragsausdruck bestimmt den Zeitplan für Bibliotheksdownloads.

## Aktivieren des Zugriffs für den Bereitstellungs-Hook-Dienst {#enabling-access-for-the-deployment-hook-service}

Aktivieren Sie den Bereitstellungs-Hook-Dienst für Dynamic Tag Management für den Zugriff auf AEM, damit der Dienst die AEM gehosteten Bibliotheken aktualisieren kann. Geben Sie die IP-Adresse der Dynamic Tag Management-Server an, die die Staging- und Produktionsbibliotheken nach Bedarf aktualisieren:

* Staging: `107.21.99.31`
* Produktion: `23.23.225.112` und `204.236.240.48`

Führen Sie die Konfiguration entweder mit der [Web-Konsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oder einem [`sling:OsgiConfig`](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository)-Knoten durch:

* Verwenden Sie in der Web-Konsole das Element zur Konfiguration mit dem Bereitstellungs-Hook für Adobe DTM, das Sie auf der Seite „Konfiguration“ finden.
* Für eine OSGi-Konfiguration lautet die PID des Dienstes `com.adobe.cq.dtm.impl.servlets.DTMDeployHookServlet`.

In der folgenden Tabelle sind die zu konfigurierenden Eigenschaften beschrieben.

| Eigenschaft in der Web-Konsole | OSGi-Eigenschaft | Beschreibung |
|---|---|---|
| Staging-DTM-IP-Zulassungsliste | `dtm.staging.ip.whitelist` | Die IP-Adresse des Dynamic Tag Management-Servers, der die Staging-Bibliotheken aktualisiert. |
| IP-Zulassungsliste für Produktions-DTM | `dtm.production.ip.whitelist` | Die IP-Adresse des Dynamic Tag Management-Servers, der die Produktionsbibliotheken aktualisiert. |

## Erstellen der Dynamic Tag Management-Konfiguration {#creating-the-dynamic-tag-management-configuration}

Erstellen Sie eine Cloud-Konfiguration, damit die AEM-Instanz sich mit Dynamic Tag Management authentifizieren und mit Ihrer Webeigenschaft interagieren kann.

>[!NOTE]
>
>Vermeiden Sie die Einbeziehung von zwei Adobe Analytics-Trackingcodes auf Ihren Seiten, wenn Ihre DTM-Webeigenschaft das Adobe Analytics-Tool enthält und Sie auch [Inhaltseinblicke](/help/sites-authoring/content-insights.md). In der [Adobe Analytics Cloud-Konfiguration](/help/sites-administering/adobeanalytics-connect.md#configuring-the-connection-to-adobe-analytics)wählen Sie die Option &quot;Rückverfolgungscode nicht einschließen&quot;.

### Allgemeine Einstellungen {#general-settings}

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>API-Token</td>
   <td>Der -Wert der API-Token-Eigenschaft Ihres Dynamic Tag Management-Benutzerkontos. AEM verwendet diese Eigenschaft für die Authentifizierung mit Dynamic Tag Management.</td>
  </tr>
  <tr>
   <td>Unternehmen</td>
   <td>Das Unternehmen, mit dem Ihre Anmelde-ID verknüpft ist.</td>
  </tr>
  <tr>
   <td>Eigenschaft</td>
   <td>Der Name der Webeigenschaft, die Sie zum Verwalten der Tags für Ihre AEM-Website erstellt haben.</td>
  </tr>
  <tr>
   <td>Produktions-Code bei Autor mit angeben</td>
   <td><p>Wählen Sie diese Option aus, damit die AEM Autoren- und Veröffentlichungsinstanzen die Produktionsversion der Dynamic Tag Management-Bibliotheken verwenden. </p> <p>Wird diese Option nicht ausgewählt, werden die Staging-Einstellungen auf die Autoreninstanz angewandt und die Produktionseinstellungen auf die Veröffentlichungsinstanz.</p> </td>
  </tr>
 </tbody>
</table>

### Self-Hosting-Eigenschaften - Staging und Produktion {#self-hosting-properties-staging-and-production}

Die folgenden Eigenschaften der Dynamic Tag Management-Konfiguration ermöglichen es AEM, die Dynamic Tag Management-Bibliotheken zu hosten. Die Eigenschaften ermöglichen es AEM, die Bibliotheken herunterzuladen und zu installieren. Optional können Sie die Bibliotheken automatisch aktualisieren, um sicherzustellen, dass sie alle Änderungen widerspiegeln, die in der Dynamic Tag Management Management-Anwendung vorgenommen wurden.

Einige Eigenschaften verwenden Werte, die Sie im Abschnitt &quot;Bibliotheksdownload&quot;auf der Registerkarte &quot;Einbettung&quot;für Ihre Dynamic Tag Management-Webeigenschaft abrufen. Weitere Informationen finden Sie unter [Bibliotheksdownload](https://microsite.omniture.com/t2/help/en_US/dtm/#Library_Download) in der Hilfe zu Dynamic Tag Management.

>[!NOTE]
>
>Wenn Sie das Dynamic Tag Management-Bundle auf AEM hosten, muss der Bibliotheksdownload in Dynamic Tag Management aktiviert sein, bevor Sie die Konfiguration erstellen. Außerdem muss Akamai aktiviert sein, da Akamai die Bibliotheken zum Herunterladen bereitstellt.

Beim Hosten der Dynamic Tag Management-Bibliotheken auf AEM konfiguriert AEM automatisch einige Eigenschaften der Webeigenschaft entsprechend Ihrer Konfiguration. Siehe Beschreibungen in der folgenden Tabelle.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Self-Hosting verwenden</td>
   <td>Wählen Sie diese Option aus, wenn Sie die Dynamic Tag Management-Bibliotheksdatei auf AEM hosten. Die Auswahl dieser Option sorgt dafür, dass die anderen Eigenschaften in dieser Tabelle angezeigt werden.</td>
  </tr>
  <tr>
   <td>URL des DTM-Bundles</td>
   <td>Die URL, die zum Herunterladen der Dynamic Tag Management-Bibliothek verwendet werden soll. Rufen Sie diesen Wert im Abschnitt "URLs herunterladen"auf der Seite "Bibliotheksdownload"von Dynamic Tag Management ab. Aus Sicherheitsgründen muss dieser Wert manuell konfiguriert werden.</td>
  </tr>
  <tr>
   <td>Download-Workflow</td>
   <td><p>Das Workflow-Modell, das zum Herunterladen und Installieren der Dynamic Tag Management-Bibliothek verwendet werden soll. Das Standardmodell ist "DTM-Bundle-Download". Verwenden Sie dieses Modell, es sei denn, Sie haben ein benutzerdefiniertes Modell erstellt.</p> <p>Der standardmäßige Download-Workflow aktiviert die Bibliotheken automatisch, wenn sie heruntergeladen werden.</p> </td>
  </tr>
  <tr>
   <td>Domain-Hinweis</td>
   <td><p>(Optional) Die Domain des AEM-Servers, auf dem die Dynamic Tag Management-Bibliothek gehostet wird. Geben Sie einen Wert an, damit Sie die Standarddomäne, die für die <a href="/help/sites-developing/externalizer.md">Day CQ Link Externalizer-Dienst</a>.</p> <p>Wenn AEM mit Dynamic Tag Management verbunden ist, nutzt es diesen Wert zum Konfigurieren des Staging-HTTP-Pfads oder des Produktions-HTTP-Pfads der Eigenschaften zum Herunterladen von Bibliotheken der Dynamic Tag Management-Web-Eigenschaft.</p> </td>
  </tr>
  <tr>
   <td>Hinweis für sichere Domain</td>
   <td><p>(Optional) Die Domain des AEM-Servers, der die Dynamic Tag Management-Bibliothek über HTTPS hostet. Geben Sie einen Wert an, damit Sie die Standarddomäne, die für die <a href="/help/sites-developing/externalizer.md">Day CQ Link Externalizer-Dienst</a>.</p> <p>Wenn AEM mit Dynamic Tag Management verbunden ist, nutzt es diesen Wert zum Konfigurieren des Staging-HTTPS-Pfads oder des Produktions-HTTPS-Pfads der Eigenschaften zum Herunterladen von Bibliotheken der Dynamic Tag Management-Web-Eigenschaft.</p> </td>
  </tr>
  <tr>
   <td>Gemeinsamer geheimer Schlüssel</td>
   <td><p>(Optional) Das gemeinsam genutzte Geheimnis, das zum Entschlüsseln des Downloads verwendet werden soll. Rufen Sie diesen Wert im Feld „Gemeinsames Geheimnis“ auf der Seite „Herunterladen von Bibliotheken“ von Dynamic Tag Management ab.</p> <p><strong>Hinweis:</strong> Sie müssen die OpenSSL-Bibliotheken auf dem Computer installiert haben, auf dem AEM installiert ist, damit AEM die heruntergeladenen Bibliotheken entschlüsseln kann.</p> </td>
  </tr>
  <tr>
   <td>Abruf-Import-Tool aktivieren</td>
   <td><p>(Optional) Wählen Sie diese Option, um die Dynamic Tag Management-Bibliothek regelmäßig herunterzuladen und zu installieren, um sicherzustellen, dass Sie eine aktualisierte Version verwenden. Ist dies ausgewählt, sendet Dynamic Tag Management keine HTTP-POST-Anfragen an die URL des Bereitstellungs-Hooks.</p> <p>AEM konfiguriert automatisch die Bereitstellungs-Hook-URL-Eigenschaft der Eigenschaften zum Herunterladen von Bibliotheken für die Dynamic Tag Management-Webeigenschaft. Ist dies ausgewählt, wird die Eigenschaft ohne Wert konfiguriert. Ist dies nicht ausgewählt, wird die Eigenschaft mit der URL der Dynamic Tag Management-Konfiguration konfiguriert.</p> <p>Aktivieren Sie das Abruf-Importtool, wenn der Bereitstellungs-Hook von Dynamic Tag Management keine Verbindung zu AEM herstellen kann, z. B. wenn sich AEM hinter einer Firewall befindet.</p> </td>
  </tr>
  <tr>
   <td>Wert für Terminplan</td>
   <td>(Wird angezeigt und ist erforderlich, wenn „Abruf-Import-Tool aktivieren“ ausgewählt ist.) Ein Cron-Ausdruck, der steuert, wann die Dynamic Tag Management-Bibliotheken heruntergeladen werden.</td>
  </tr>
 </tbody>
</table>

![chlimage_1-352](assets/chlimage_1-352.png)

### Cloud-Hosting-Eigenschaften - Staging und Produktion {#cloud-hosting-properties-staging-and-production}

Sie konfigurieren die folgenden Eigenschaften für Ihre Dynamic Tag Management-Konfiguration, wenn die Dynamic Tag Configuration in der Cloud gehostet wird.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>Self-Hosting verwenden</td>
   <td>Deaktivieren Sie diese Option, wenn die Dynamic Tag Management-Bibliotheksdatei in der Cloud gehostet wird.</td>
  </tr>
  <tr>
   <td>Kopfzeilen-Code</td>
   <td><p>Der Kopfzeilen-Code für das Staging, der von Dynamic Tag Management für Ihren Host abgerufen wird. Dieser Wert wird automatisch aufgefüllt, wenn Sie eine Verbindung zu Dynamic Tag Management herstellen.</p> <p> Um den Code in Dynamic Tag Management anzuzeigen, klicken Sie auf die Registerkarte „Einbetten“ und klicken Sie dann auf den Hostnamen. Erweitern Sie den Abschnitt „Kopfzeilen-Code“ und klicken Sie im Bereich „Einbettungs-Code für das Staging“ oder „Einbettungs-Code für die Produktion“ auf „Einbettungs-Code kopieren“.</p> </td>
  </tr>
  <tr>
   <td>Fußzeilen-Code</td>
   <td><p>Der Fußzeilen-Code für das Staging, der von Dynamic Tag Management für Ihren Host abgerufen wird. Dieser Wert wird automatisch aufgefüllt, wenn Sie eine Verbindung zu Dynamic Tag Management herstellen.</p> <p>Um den Code in Dynamic Tag Management anzuzeigen, klicken Sie auf die Registerkarte „Einbetten“ und klicken Sie dann auf den Hostnamen. Erweitern Sie den Abschnitt „Fußzeilen-Code“ und klicken Sie im Bereich „Einbettungs-Code für das Staging“ oder „Einbettungs-Code für die Produktion“ auf „Einbettungs-Code kopieren“.</p> </td>
  </tr>
 </tbody>
</table>

![chlimage_1-353](assets/chlimage_1-353.png)

Im folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um die Integration mit Dynamic Tag Management zu konfigurieren.

1. Klicken Sie auf der Leiste auf Tools > Vorgänge > Cloud > Cloud Service.
1. Im Bereich &quot;Dynamischer Tag Management&quot;wird einer der folgenden Links zum Hinzufügen einer Konfiguration angezeigt:

   * Klicken Sie auf „Jetzt konfigurieren“, wenn dies die erste Konfiguration ist, die Sie hinzufügen.
   * Klicken Sie auf „Konfigurationen anzeigen“ und anschließend auf den „+“-Link neben „Verfügbare Konfigurationen“, wenn eine oder mehrere Konfigurationen erstellt wurden.

   ![chlimage_1-354](assets/chlimage_1-354.png)

1. Geben Sie einen Titel für die Konfiguration ein und klicken Sie auf Erstellen .
1. Geben Sie im Feld &quot;API-Token&quot;den Wert der Eigenschaft &quot;API-Token&quot;Ihres Dynamic Tag Management-Benutzerkontos ein.

   Wenden Sie sich an DTM-Kunden-Support, um den Wert Ihres API-Tokens abzurufen.

   >[!NOTE]
   >
   >Der API-Token läuft erst ab, wenn der Dynamic Tag Management-Benutzer dies explizit anfordert.

   ![chlimage_1-355](assets/chlimage_1-355.png)

1. Klicken Sie auf Mit DTM verbinden . AEM authentifiziert sich bei Dynamic Tag Management und ruft die Liste der Unternehmen ab, mit denen Ihr Konto verknüpft ist.
1. Wählen Sie das Unternehmen aus und wählen Sie dann die Eigenschaft aus, mit der Sie Ihre AEM Site verfolgen.
1. Wenn Sie Staging-Code in der Autoreninstanz verwenden, deaktivieren Sie die Option Produktionscode bei Autor einschließen .
1. Geben Sie bei Bedarf Werte für die Eigenschaften auf der Registerkarte &quot;Staging-Einstellungen&quot;und auf der Registerkarte &quot;Produktionseinstellungen&quot;an und klicken Sie dann auf &quot;OK&quot;.

## Manuelles Herunterladen der Dynamic Tag Management Library {#manually-downloading-the-dynamic-tag-management-library}

Laden Sie die Dynamic Tag Management-Bibliotheken manuell herunter, um sie auf AEM sofort zu aktualisieren. Beispielsweise können Sie manuell herunterladen, wenn Sie eine aktualisierte Bibliothek testen möchten, bevor der Abruf-Importtool planmäßig automatisch die Bibliothek herunterladen soll.

1. Klicken Sie auf der Leiste auf Tools > Vorgänge > Cloud > Cloud Service.
1. Klicken Sie im Bereich &quot;Dynamische Tag Management&quot;auf Konfigurationen anzeigen und dann auf Ihre Konfiguration.
1. Klicken Sie im Bereich &quot;Staging-Einstellungen&quot;oder &quot;Produktionseinstellungen&quot;auf die Schaltfläche &quot;Trigger-Workflow herunterladen&quot;, um das Bibliotheksbundle herunterzuladen und bereitzustellen.

   ![chlimage_1-356](assets/chlimage_1-356.png)

>[!NOTE]
>
>Die heruntergeladenen Dateien werden unter `/etc/clientlibs/dtm/my config/companyID/propertyID/servertype` gespeichert.
>
>Folgendes wird direkt Ihrer [DTM-Konfiguration](#creating-the-dynamic-tag-management-configuration) entnommen:
>
>* `myconfig`
>* `companyID`
>* `propertyID`
>* `servertype`
>

## Verknüpfen einer dynamischen Tag Management-Konfiguration mit Ihrer Site {#associating-a-dynamic-tag-management-configuration-with-your-site}

Verknüpfen Sie Ihre Dynamic Tag Management-Konfiguration mit den Seiten Ihrer Website, damit AEM das erforderliche Skript zu den Seiten hinzufügt. Verknüpfen Sie die Stammseite Ihrer Site mit der Konfiguration. Alle untergeordneten Elemente dieser Seite übernehmen die Verknüpfung. Bei Bedarf können Sie die Verknüpfung auf einer untergeordneten Seite überschreiben.

Gehen Sie wie folgt vor, um eine Seite und die untergeordneten Elemente mit einer Dynamic Tag Management-Konfiguration zu verknüpfen.

1. Öffnen Sie die Stammseite Ihrer Site in der klassischen Benutzeroberfläche.
1. Öffnen Sie die Seiteneigenschaften mithilfe von Sidekick.
1. Klicken Sie auf der Registerkarte Cloud Service auf Dienst hinzufügen , wählen Sie Dynamic Tag Management und klicken Sie auf OK.

   ![chlimage_1-357](assets/chlimage_1-357.png)

1. Wählen Sie Ihre Konfiguration mithilfe des Dropdown-Menüs Dynamische Tag Management aus und klicken Sie auf OK.

Gehen Sie wie folgt vor, um die geerbte Konfigurationsverknüpfung für eine Seite zu überschreiben. Die Überschreibung wirkt sich auf die Seite und alle untergeordneten Seiten aus.

1. Öffnen Sie die Seite in der klassischen Benutzeroberfläche.
1. Öffnen Sie die Seiteneigenschaften mithilfe von Sidekick.
1. Klicken Sie auf der Registerkarte Cloud Service auf das Vorhängeschloss-Symbol neben der Eigenschaft Vererbt von und klicken Sie dann im Bestätigungsdialogfeld auf Ja .

   ![chlimage_1-358](assets/chlimage_1-358.png)

1. Entfernen oder wählen Sie eine Dynamic Tag Management-Konfiguration und klicken Sie dann auf „OK“.
