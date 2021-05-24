---
title: Fehlerbehebung für Integrationsprobleme
seo-title: Fehlerbehebung für Integrationsprobleme
description: Erfahren Sie, wie Sie Integrationsprobleme beheben.
seo-description: Erfahren Sie, wie Sie Integrationsprobleme beheben.
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
exl-id: 11b0023e-34bd-4dfe-8173-5466db9fbe34
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 67%

---

# Fehlerbehebung für Integrationsprobleme{#troubleshooting-integration-issues}

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

### Sicherstellen, dass es keine JavaScript-Fehler gibt {#ensure-there-are-no-javascript-errors}

Überprüfen Sie, ob in der JavaScript-Konsole des Browsers Fehler angezeigt werden. Nicht behobene Fehler können verhindern, dass der nachfolgende Code ordnungsgemäß ausgeführt wird. Wenn Fehler angezeigt werden, überprüfen Sie, welches Skript den Fehler verursacht und in welchem Bereich. Der Pfad zum Skript weist möglicherweise darauf hin, zu welcher Funktion das Skript gehört.

### Protokollierung auf Komponentenebene  {#logging-on-component-level}

In einigen Fällen kann es hilfreich sein, zusätzliche Anweisungen auf der Komponentenebene hinzuzufügen. Da die Komponente gerendert wird, können Sie ein temporäres Markup hinzufügen, um Variablenwerte anzuzeigen, die Ihnen bei der Erkennung potenzieller Probleme helfen können. Beispiel:

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

Weitere Informationen zur Protokollierung finden Sie auf den Seiten [Protokollierung](/help/sites-deploying/configure-logging.md) und [Arbeiten mit Auditdatensätzen und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) .

## Analytics-Integrationsprobleme {#analytics-integration-issues}

### Report Importer führt zu hoher CPU-/Speichernutzung {#the-report-importer-causes-high-cpu-memory-usage}

Der Report Importer verursacht hohe CPU-/Speichernutzung oder `OutOfMemoryError`-Ausnahmefehler.

#### Lösung {#solution}

Um dieses Problem zu beheben, können Sie Folgendes versuchen:

* Überprüfen Sie, ob eine große Anzahl von PollingImporter-Instanzen registriert ist (siehe „Herunterfahren dauert aufgrund von PollingImporter lange“ weiter unten).
* Führen Sie Report Importer zu einem bestimmten Zeitpunkt am Tag aus. Verwenden Sie hierfür CRON-Ausdrücke für die `ManagedPollingImporter`-Konfigurationen in der [OSGi-Konsole](/help/sites-deploying/configuring-osgi.md).

Weitere Informationen zum Erstellen von benutzerdefinierten Daten-Importtool-Diensten in AEM finden Sie im folgenden Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/de/experience-manager/using/polling.html).

### Herunterfahren dauert aufgrund von PollingImporter lange {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analytics wurde basierend auf einem Vererbungsmechanismus entwickelt. In der Regel aktivieren Sie Analytics für eine Site, indem Sie auf der Registerkarte [Cloud-Services](/help/sites-developing/extending-cloud-config.md) der Seiteneigenschaften eine Referenz zu einer Analytics-Konfiguration hinzufügen. Die Konfiguration wird dann automatisch auf alle Unterseiten vererbt, ohne dass sie erneut referenziert werden muss, es sei denn, eine Seite erfordert eine andere Konfiguration. Durch Hinzufügen eines Verweises zu einer Site werden auch automatisch mehrere Knoten erstellt (12 für AEM 6.3 und früher oder 6 für AEM 6.4)   und höher) des Typs `cq;PollConfig`, der PollingImporter instanziiert, die zum Importieren von Analytics-Daten in AEM verwendet werden. Das führt zu folgenden Problemen:

* Wenn viele Seiten auf Analytics verweisen, wird eine große Anzahl an PollingImporter-Instanzen generiert.
* Außerdem führt das Kopieren und Einfügen von Seiten mit einem Verweis auf eine Analytics-Konfiguration zu einer Duplizierung der PollingImporter-Instanzen.

#### Lösung {#solution-1}

Zunächst könnte Ihnen die Analyse von [error.log](/help/sites-deploying/configure-logging.md) einen Einblick in die Menge der aktiven oder registrierten PollingImporter geben. Beispiel:

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

Stellen Sie außerdem sicher, dass nur Seiten der obersten Ebene (oben in der Hierarchie) auf eine Analytics-Konfiguration verweisen.

Weitere Informationen zum Erstellen von benutzerdefinierten Daten-Importtool-Diensten in AEM finden Sie im folgenden Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## Probleme mit DTM (Legacy){#dtm-legacy-issues}

### Skript-Tag „DTM“ wird in der Seitenquelle nicht gerendert {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

Das Skript-Tag [DTM](/help/sites-administering/dtm.md) wird nicht ordnungsgemäß auf der Seite eingefügt, obwohl auf der Registerkarte [Cloud-Services](/help/sites-developing/extending-cloud-config.md) der Seiteneigenschaften auf die Konfiguration verwiesen wurde.

#### Lösung {#solution-2}

Um dieses Problem zu beheben, können Sie Folgendes versuchen:

* Stellen Sie sicher, dass verschlüsselte Eigenschaften entschlüsselt werden können (beachten Sie, dass für die Verschlüsselung möglicherweise für jede AEM-Instanz ein anderer automatisch generierter Schlüssel verwendet wird). Weitere Informationen finden Sie unter [Verschlüsselungsunterstützung für Konfigurationseigenschaften](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Veröffentlichen Sie die Konfigurationen in `/etc/cloudservices/dynamictagmanagement` erneut.
* Überprüfen Sie ACLs auf `/etc/cloudservices`. Die ACLs sollten wie folgt lauten:

   * allow; jcr:read; webservice-support-servicelibfinder
   * zulassen; jcr:read; alle; rep:glob:&amp;ast;/defaults/&amp;ast;
   * zulassen; jcr:read; alle; rep:glob:&amp;ast;/defaults
   * zulassen; jcr:read; alle; rep:glob:&amp;ast;/public/&amp;ast;
   * zulassen; jcr:read; alle; rep:glob:&amp;ast;/public

Weitere Informationen zur Verwaltung von ACLs finden Sie auf der Seite [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md#permissions-in-aem).

## Integrationsprobleme in Target  {#target-integration-issues}

### Zielgerichteter Inhalt im Vorschaumodus nicht sichtbar, wenn benutzerdefinierte Seitenkomponenten verwendet werden {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dieses Problem tritt auf, da benutzerdefinierte Seitenkomponenten nicht die richtigen JSP- oder Client-Bibliotheken zum Verarbeiten der Target-DTM-Integrationen enthalten.

#### Lösung {#solution-3}

Sie können die folgenden Lösungen ausprobieren:

* Stellen Sie sicher, dass der benutzerdefinierte `headlibs.jsp` (falls vorhanden `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) Folgendes enthält:

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Stellen Sie sicher, dass die benutzerdefinierte `head.html` (falls `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **nicht** bestimmte Integrations-Headlibs selektiv enthält, wie im folgenden Beispiel:

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

`servicelibs.jsp` fügt die erforderlichen JavaScript-Analyseobjekte hinzu und lädt die Cloud-Service-Bibliotheken, die mit der Website verbunden sind. Für den Target-Dienst werden die Bibliotheken über den geladen`/libs/cq/analytics/components/testandtarget/headlibs.jsp`

Die geladenen Bibliotheken hängen von der Art der Ziel-Client-Bibliothek (`mbox.js` oder `at.js`) ab, die in der Target-Konfiguration verwendet wird.

Wenn Sie DTM zur Bereitstellung von `mbox.js` oder `at.js` verwenden, stellen Sie sicher, dass die Bibliotheken geladen werden, bevor der Inhalt gerendert wird. Die Verwendung von Tag-Management-Systemen, die diese Bibliotheken asynchron laden, kann zu Problemen bei der Ausführung des zielspezifischen JavaScript-Codes führen.

Weitere Informationen finden Sie auf der Seite [Entwickeln für zielgerichtete Inhalte](/help/sites-developing/target.md#understanding-the-target-component).

### Fehler „Fehlende Report Suite-ID in AppMeasurement-Initialisierung“ in der Browser-Konsole  {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dieses Problem tritt möglicherweise auf, wenn Adobe Analytics mithilfe von DTM auf der Website implementiert wird und benutzerspezifischen Code verwendet. Die Ursache dafür ist die Verwendung von `s = new AppMeasurement()` zum Instanziieren des `s` -Objekts.

#### Lösung {#solution-4}

Verwenden Sie `s_gi` anstelle der Instanziierungsmethode `new AppMeasurement`. Beispiel:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Standardangebot wird nach dem Zufallsprinzip anstelle des richtigen Angebots angezeigt  {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dieses Problem kann mehrere Ursachen haben:

* Das asynchrone Laden von Target-Client-Bibliotheken ( `mbox.js` oder `at.js`) mithilfe von Drittanbieter-Tag-Management-Systemen kann das Targeting nach dem Zufallsprinzip unterbrechen. Die Target-Bibliotheken sollen synchron im Seitenheader geladen werden. Dies ist immer dann der Fall, wenn die Bibliotheken von AEM bereitgestellt werden.

* Das gleichzeitige Laden von zwei Target-Client-Bibliotheken ( `at.js`), z. B. einer mit DTM und einer mit der Target-Konfiguration in AEM. kann dies zu Konflikten in der `adobe.target`-Definition führen, wenn die `at.js`-Versionen unterschiedlich sind.

#### Lösung {#solution-5}

Sie können die folgenden Lösungen ausprobieren:

* Stellen Sie sicher, dass der benutzerspezifische Code, der die DTM-ähnlichen Bibliotheken lädt (die wiederum die Target-Bibliotheken laden), im [Seitenheader](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages) synchron ausgeführt wird.
* Wenn die Site für die Verwendung von DTM zur Bereitstellung von Target-Bibliotheken konfiguriert ist, stellen Sie sicher, dass die Option **Von DTM** bereitgestellte Clientlib in der [Target-Konfiguration](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) für die Site aktiviert ist.

### Bei Verwendung von AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js} wird immer ein Standardangebot anstelle des richtigen Angebots angezeigt

Standardmäßig sind AEM 6.2 und 6.3 nicht mit AT.js Version 1.3.0 und höher kompatibel. Bei AT.js-Version 1.3.0, die die Parametervalidierung für die APIs einführt, erfordert `adobe.target.applyOffer()` einen &quot;mbox&quot;-Parameter, der vom `atjs-itegration.js`-Code nicht bereitgestellt wird.

#### Lösung {#solution-6}

Um dieses Problem zu beheben, bearbeiten Sie `atjs-itegration.js` und fügen Sie das `"mbox": mboxName`-Feld im Parameterobjekt für `adobe.target.applyOffer()` wie folgt hinzu:

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

Dieses Problem ist höchstwahrscheinlich ein Bereitstellungsproblem mit der [A4T-Analytics Cloud-Konfiguration](/help/sites-administering/target-configuring.md).

#### Lösung {#solution-7}

Sie müssen sicherstellen, dass A4T für Ihr Target-Konto ordnungsgemäß aktiviert ist, indem Sie die folgende Überprüfungsanforderung für AEM senden:

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

### Nützliche Target-APIs {#helpful-target-apis}

Nachfolgend werden zwei Target-APIs aufgeführt, die bei der Behebung von Target-Problemen hilfreich sein können:

* Ruft den Target-Endpunkt für einen bestimmten Clientcode ab:

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json

{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Ruft das Profil eines Kunden ab:

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
