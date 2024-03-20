---
title: Fehlerbehebung für Integrationsprobleme
description: Erfahren Sie, wie Sie Probleme bei der Integration mit Adobe Experience Manager beheben können.
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 11b0023e-34bd-4dfe-8173-5466db9fbe34
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 41%

---

# Fehlerbehebung für Integrationsprobleme{#troubleshooting-integration-issues}

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

### Sicherstellen, dass keine JavaScript-Fehler vorliegen {#ensure-there-are-no-javascript-errors}

Überprüfen Sie, ob in der JavaScript-Konsole des Browsers Fehler angezeigt werden. Unbehandelte Fehler könnten die ordnungsgemäße Ausführung des folgenden Codes verhindern. Falls Fehler auftreten, überprüfen Sie, welches Skript den Fehler verursacht und in welchem Bereich. Der Pfad zum Skript kann einen Hinweis darauf geben, zu welcher Funktion das Skript gehört.

### Protokollierung auf Komponentenebene {#logging-on-component-level}

In einigen Fällen kann es hilfreich sein, zusätzliche Anweisungen auf Komponentenebene hinzuzufügen. Da die Komponente gerendert wird, können Sie ein temporäres Markup hinzufügen, um Variablenwerte anzuzeigen, mit denen Sie potenzielle Probleme erkennen können. Beispiel:

```
<%
log.info("myVariable={}", myVariable);
%>

<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

Weitere Informationen zu Protokollierung finden Sie auf den Seiten [Protokollierung](/help/sites-deploying/configure-logging.md) und [Arbeiten mit Auditdatensätzen und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

## Analytics-Integrationsprobleme {#analytics-integration-issues}

### Der Report Importer verursacht eine hohe CPU-/Speicherbelegung {#the-report-importer-causes-high-cpu-memory-usage}

Der Report Importer verursacht hohe CPU-/Speichernutzung oder `OutOfMemoryError`-Ausnahmefehler.

#### Lösung {#solution}

Um dieses Problem zu beheben, können Sie Folgendes versuchen:

* Stellen Sie sicher, dass nicht eine große Anzahl von PollingImportern registriert ist (siehe Abschnitt &quot;Shutdown dauert aufgrund von PollingImporter lange&quot; unten).
* Führen Sie Report Importer zu einem bestimmten Zeitpunkt am Tag aus. Verwenden Sie hierfür CRON-Ausdrücke für die `ManagedPollingImporter`-Konfigurationen in der [OSGi-Konsole](/help/sites-deploying/configuring-osgi.md).

Weitere Informationen zum Erstellen benutzerdefinierter Datenimportdienste in AEM finden Sie im Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

### Aufgrund des PollingImporter dauert das Herunterfahren lange {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analytics wurde mit Blick auf einen Vererbungsmechanismus entwickelt. Normalerweise aktivieren Sie Analytics für eine Site, indem Sie einen Verweis auf eine Analytics-Konfiguration in den Seiteneigenschaften hinzufügen [Cloud Service](/help/sites-developing/extending-cloud-config.md) Registerkarte. Die Konfiguration wird dann automatisch auf allen Unterseiten übernommen, ohne dass ein erneuter Verweis erforderlich ist, es sei denn, für eine Seite ist eine andere Konfiguration erforderlich. Durch Hinzufügen einer Referenz zu einer Website werden auch automatisch mehrere Knoten (12 für AEM 6.3 und früher bzw. 6 für AEM 6.4) des Typs `cq;PollConfig` erstellt, der PollingImporter-Instanzen generiert, mit denen Analytics-Daten in AEM importiert werden. Das Ergebnis ist:

* Viele Seiten, die auf Analytics verweisen, führen zu einer hohen Anzahl von PollingImportern.
* Außerdem führt das Kopieren und Einfügen von Seiten mit einem Verweis auf eine Analytics-Konfiguration zu einer Duplizierung der PollingImporter-Elemente.

#### Lösung {#solution-1}

Zunächst einmal zeigt Ihnen die Analyse von [error.log](/help/sites-deploying/configure-logging.md) möglicherweise die Anzahl der aktiven oder registrierten PollingImporter-Instanzen. Beispiel:

```
# Count PollingImporter entries
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

Stellen Sie zweitens sicher, dass nur oberste Seiten (in der Hierarchie ganz oben) auf eine Analytics-Konfiguration verwiesen werden.

Weitere Informationen zum Erstellen benutzerdefinierter Datenimportdienste in AEM finden Sie im Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## DTM-(Legacy-)Probleme {#dtm-legacy-issues}

### Das DTM-Skript-Tag wird nicht in der Seitenquelle gerendert {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

Die [DTM](/help/sites-administering/dtm.md) Skript-Tag wird nicht ordnungsgemäß auf der Seite eingefügt, obwohl die Konfiguration in den Seiteneigenschaften referenziert wurde [Cloud Service](/help/sites-developing/extending-cloud-config.md) Registerkarte.

#### Lösung {#solution-2}

Um das Problem zu beheben, können Sie Folgendes versuchen:

* Stellen Sie sicher, dass verschlüsselte Eigenschaften entschlüsselt werden können (beachten Sie, dass bei der Verschlüsselung in jeder AEM-Instanz möglicherweise ein anderer automatisch generierter Schlüssel verwendet wird). Weitere Informationen finden Sie auch unter [Verschlüsselungsunterstützung für Konfigurationseigenschaften](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Veröffentlichen Sie die in `/etc/cloudservices/dynamictagmanagement` gefundenen Konfigurationen erneut.
* Überprüfen Sie ACLs unter `/etc/cloudservices`. Die ACLs sollten:

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/defaults/`&amp;ast;
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/defaults`
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/public/`&amp;ast;
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/public`

Weitere Informationen zur Verwaltung von ACLs finden Sie im Abschnitt [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md#permissions-in-aem) Seite.

## Target-Integrationsprobleme {#target-integration-issues}

### Zielgerichteter Inhalt ist im Vorschaumodus nicht sichtbar, wenn benutzerdefinierte Seitenkomponenten verwendet werden {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dieses Problem tritt auf, weil benutzerdefinierte Seitenkomponenten nicht die richtigen JSP- oder Client-Bibliotheken enthalten, die die Target DTM-Integrationen verarbeiten.

#### Lösung {#solution-3}

Sie können die folgenden Lösungen ausprobieren:

* Stellen Sie sicher, dass die benutzerdefinierte `headlibs.jsp` (falls `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp` vorhanden) Folgendes enthält:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Stellen Sie sicher, dass die benutzerdefinierte Datei `head.html` (falls `/apps/<CUSTOM-COMPONENTS-PATH>/head.html` vorhanden) **nicht** selektiv spezifische Integrations-Headlibs wie im unten stehenden Beispiel enthält:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

`servicelibs.jsp` fügt die erforderlichen JavaScript-Analyseobjekte hinzu und lädt die Cloud-Service-Bibliotheken, die mit der Website verbunden sind. Für den Target-Service werden die Bibliotheken über die `/libs/cq/analytics/components/testandtarget/headlibs.jsp` geladen.

Die geladenen Bibliotheken hängen von der Art der Ziel-Client-Bibliothek (`mbox.js` oder `at.js`) ab, die in der Target-Konfiguration verwendet wird.

Wenn Sie DTM zur Bereitstellung von `mbox.js` oder `at.js` verwenden, stellen Sie sicher, dass die Bibliotheken geladen werden, bevor der Inhalt gerendert wird. Die Verwendung von Tag Management-Systemen, die diese Bibliotheken asynchron laden, kann Probleme bei der Ausführung des zielspezifischen JavaScript-Codes verursachen.

Weitere Informationen finden Sie im Abschnitt [Entwickeln für zielgerichtete Inhalte](/help/sites-developing/target.md#understanding-the-target-component) Seite.

### Der Fehler &quot;Fehlende Report Suite-ID bei AppMeasurement-Initialisierung&quot;wird in der Browserkonsole angezeigt {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dieses Problem kann auftreten, wenn Adobe Analytics auf der Website mithilfe von DTM implementiert wird und benutzerdefinierten Code verwendet. Die Ursache dafür ist die Verwendung von `s = new AppMeasurement()` zum Instanziieren des `s`-Objekts.

#### Lösung {#solution-4}

Verwenden Sie `s_gi` anstelle der Instanziierungsmethode `new AppMeasurement`. Beispiel:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Ein Standardangebot wird nach dem Zufallsprinzip anstelle des richtigen Angebots angezeigt {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dieses Problem kann mehrere Ursachen haben:

* Das asynchrone Laden von Target-Client-Bibliotheken (`mbox.js` oder `at.js`) mithilfe von Drittanbieter-Tag-Management-Systemen kann das Targeting nach dem Zufallsprinzip außer Kraft setzen. Die Target-Bibliotheken sollen synchron im Seitenkopf geladen werden. Dies gilt immer, wenn die Bibliotheken von AEM bereitgestellt werden.

* Wenn Sie zwei Target-Client-Bibliotheken (`at.js`) gleichzeitig laden, z. B. eine über DTM und eine über die Target-Konfiguration in AEM, kann dies zu Konflikten in der `adobe.target`-Definition führen, wenn die `at.js`-Versionen unterschiedlich sind.

#### Lösung {#solution-5}

Sie können die folgenden Lösungen ausprobieren:

* Stellen Sie sicher, dass der Kundencode, der die DTM-ähnlichen Bibliotheken lädt (die wiederum die Target-Bibliotheken laden), synchron in der [Seitenkopf](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* Wenn die Website für die Verwendung von DTM zur Bereitstellung von Target-Bibliotheken konfiguriert ist, stellen Sie sicher, dass die Option **Von DTM gelieferte Clientlib verwenden** in der [Target-Konfiguration](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/target-configuring.html) für die Website aktiviert ist.

### Bei Verwendung von AT.js 1.3+ wird immer ein Standardangebot anstelle des richtigen Angebots angezeigt {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Standardmäßig sind AEM 6.2 und 6.3 nicht mit AT.js ab Version 1.3.0 kompatibel. Ab AT.js Version 1.3.0 wird eine Parametervalidierung für die APIs eingeführt, d. h. `adobe.target.applyOffer()` muss einen „mbox“-Parameter enthalten, der vom `atjs-itegration.js`-Code nicht bereitgestellt wird.

#### Lösung {#solution-6}

Um dieses Problem zu beheben, bearbeiten Sie `atjs-itegration.js` und fügen Sie das Feld `"mbox": mboxName` im Parameterobjekt für `adobe.target.applyOffer()` hinzu:

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### Auf der Seite „Ziele und Einstellungen“ wird der Abschnitt „Berichtsquellen“ nicht angezeigt {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

Dieses Problem ist höchstwahrscheinlich ein Bereitstellungsproblem mit der [A4T-Analytics-Cloud-Konfiguration](/help/sites-administering/target-configuring.md).

#### Lösung {#solution-7}

Sie müssen sicherstellen, dass A4T für Ihr Target-Konto ordnungsgemäß aktiviert ist, indem Sie die folgende Überprüfungsanforderung an AEM senden:

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json

{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

Wenn die Antwort die Zeile `a4tEnabled:false` enthält, wenden Sie sich an die [Adobe-Kundenunterstützung,](https://helpx.adobe.com/de/contact.html), um die Bereitstellung Ihres Kontos zu korrigieren.

### Hilfreiche Target-APIs {#helpful-target-apis}

Nachfolgend sind zwei Target-APIs aufgeführt, die bei der Fehlerbehebung von Target-Problemen nützlich sein können:

* Abrufen des Target-Endpunkts für einen bestimmten Clientcode

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json

{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Profil eines Kunden abrufen

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>

Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```
