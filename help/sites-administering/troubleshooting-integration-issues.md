---
title: Fehlerbehebung für Integrationsprobleme
description: Erfahren Sie, wie Sie Probleme bei der Integration in Adobe Experience Manager beheben können.
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 11b0023e-34bd-4dfe-8173-5466db9fbe34
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1078'
ht-degree: 97%

---

# Fehlerbehebung für Integrationsprobleme{#troubleshooting-integration-issues}

## Allgemeine Tipps zur Problembehebung {#general-troubleshooting-tips}

### Sicherstellen, dass es keine JavaScript-Fehler gibt {#ensure-there-are-no-javascript-errors}

Überprüfen Sie, ob in der JavaScript-Konsole des Browsers Fehler angezeigt werden. Nicht behobene Fehler können verhindern, dass der nachfolgende Code ordnungsgemäß ausgeführt wird. Wenn Fehler angezeigt werden, überprüfen Sie, welches Skript den Fehler verursacht und in welchem Bereich. Der Pfad zum Skript weist möglicherweise darauf hin, zu welcher Funktion das Skript gehört.

### Protokollierung auf Komponentenebene {#logging-on-component-level}

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

Weitere Informationen zu Protokollierung finden Sie auf den Seiten [Protokollierung](/help/sites-deploying/configure-logging.md) und [Arbeiten mit Auditdatensätzen und Protokolldateien](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files).

## Probleme bei der Analytics-Integration {#analytics-integration-issues}

### Der Report Importer führt zu hoher CPU-/Speichernutzung {#the-report-importer-causes-high-cpu-memory-usage}

Der Report Importer verursacht hohe CPU-/Speichernutzung oder `OutOfMemoryError`-Ausnahmefehler.

#### Lösung {#solution}

Um dieses Problem zu beheben, können Sie Folgendes versuchen:

* Stellen Sie sicher, dass keine große Anzahl von PollingImporter-Instanzen registriert ist (siehe weiter unten „Herunterfahren dauert aufgrund von PollingImporter lange“).
* Führen Sie Report Importer zu einem bestimmten Zeitpunkt am Tag aus. Verwenden Sie hierfür CRON-Ausdrücke für die `ManagedPollingImporter`-Konfigurationen in der [OSGi-Konsole](/help/sites-deploying/configuring-osgi.md).

Weitere Informationen zum Erstellen benutzerdefinierter Datenimportdienste in AEM finden Sie im Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

### Herunterfahren dauert aufgrund von PollingImporter lange {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analytics wurde basierend auf einem Vererbungsmechanismus entwickelt. In der Regel aktivieren Sie Analytics für eine Site, indem Sie in den Seiteneigenschaften auf der Registerkarte [Cloud-Services](/help/sites-developing/extending-cloud-config.md) einen Verweis zu einer Analytics-Konfiguration hinzufügen. Die Konfiguration wird dann automatisch auf alle Unterseiten vererbt, ohne dass sie erneut referenziert werden muss, es sei denn, eine Seite erfordert eine andere Konfiguration. Durch Hinzufügen einer Referenz zu einer Website werden auch automatisch mehrere Knoten (12 für AEM 6.3 und früher bzw. 6 für AEM 6.4) des Typs `cq;PollConfig` erstellt, der PollingImporter-Instanzen generiert, mit denen Analytics-Daten in AEM importiert werden. Das Ergebnis ist:

* Wenn viele Seiten auf Analytics verweisen, wird eine große Anzahl an PollingImporter-Instanzen generiert.
* Außerdem führt das Kopieren und Einfügen von Seiten mit einem Verweis auf eine Analytics-Konfiguration zu einer Duplizierung der PollingImporter-Instanzen.

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

Stellen Sie außerdem sicher, dass nur Seiten der obersten Ebene (oben in der Hierarchie) auf eine Analytics-Konfiguration verweisen.

Weitere Informationen zum Erstellen benutzerdefinierter Datenimportdienste in AEM finden Sie im Artikel [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## Probleme mit DTM (Legacy) {#dtm-legacy-issues}

### Skript-Tag „DTM“ wird in der Seitenquelle nicht gerendert {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

Das Skript-Tag [DTM](/help/sites-administering/dtm.md) wird nicht ordnungsgemäß auf der Seite eingefügt, obwohl auf der Registerkarte [Cloud-Services](/help/sites-developing/extending-cloud-config.md) der Seiteneigenschaften auf die Konfiguration verwiesen wurde.

#### Lösung {#solution-2}

Um das Problem zu beheben, können Sie Folgendes versuchen:

* Stellen Sie sicher, dass verschlüsselte Eigenschaften entschlüsselt werden können. (Bei der Verschlüsselung wird möglicherweise für jede AEM-Instanz ein anderer, automatisch generierter Schlüssel verwendet.) Weitere Informationen finden Sie unter [Verschlüsselungsunterstützung für Konfigurationseigenschaften](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Veröffentlichen Sie die in `/etc/cloudservices/dynamictagmanagement` gefundenen Konfigurationen erneut.
* Überprüfen Sie ACLs unter `/etc/cloudservices`. Die ACLs sollten wie folgt lauten:

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/defaults/`&amp;ast;
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/defaults`
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/public/`&amp;ast;
   * allow; jcr:read; everyone `rep:glob:`&amp;ast;`/public`

Weitere Informationen zur Verwaltung von ACLs finden Sie auf der Seite [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md#permissions-in-aem).

## Probleme bei der Integration in Target {#target-integration-issues}

### Zielgerichtete Inhalte sind im Vorschaumodus nicht sichtbar, wenn benutzerdefinierte Seitenkomponenten verwendet werden {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Dieses Problem tritt auf, da benutzerdefinierte Seitenkomponenten nicht die richtigen JSP- oder Client-Bibliotheken zum Verarbeiten der Target-DTM-Integrationen enthalten.

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

Wenn Sie DTM zur Bereitstellung von `mbox.js` oder `at.js` verwenden, stellen Sie sicher, dass die Bibliotheken geladen werden, bevor der Inhalt gerendert wird. Die Verwendung von Tag-Management-Systemen, die diese Bibliotheken asynchron laden, kann zu Problemen bei der Ausführung des zielspezifischen JavaScript-Codes führen.

Weitere Informationen finden Sie auf der Seite [Entwicklung für zielgerichtete Inhalte](/help/sites-developing/target.md#understanding-the-target-component).

### Fehler „Fehlende Report Suite-ID in AppMeasurement-Initialisierung“ in der Browser-Konsole {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Dieses Problem kann auftreten, wenn Adobe Analytics auf der Website mithilfe von DTM implementiert wird und benutzerdefinierten Code verwendet. Die Ursache dafür ist die Verwendung von `s = new AppMeasurement()` zum Instanziieren des `s`-Objekts.

#### Lösung {#solution-4}

Verwenden Sie `s_gi` anstelle der Instanziierungsmethode `new AppMeasurement`. Beispiel:

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Ein Standardangebot wird nach dem Zufallsprinzip anstelle des richtigen Angebots angezeigt {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Dieses Problem kann mehrere Ursachen haben:

* Das asynchrone Laden von Target-Client-Bibliotheken (`mbox.js` oder `at.js`) mithilfe von Drittanbieter-Tag-Management-Systemen kann das Targeting nach dem Zufallsprinzip außer Kraft setzen. Die Target-Bibliotheken sollten synchron im Seitenkopf geladen werden. Dies gilt immer, wenn die Bibliotheken von AEM bereitgestellt werden. 

* Wenn Sie zwei Target-Client-Bibliotheken (`at.js`) gleichzeitig laden, z. B. eine über DTM und eine über die Target-Konfiguration in AEM, kann dies zu Konflikten in der `adobe.target`-Definition führen, wenn die `at.js`-Versionen unterschiedlich sind.

#### Lösung {#solution-5}

Sie können die folgenden Lösungen ausprobieren:

* Stellen Sie sicher, dass der benutzerspezifische Code, der die DTM-ähnlichen Bibliotheken lädt (die wiederum die Target-Bibliotheken laden), im [Seitenkopf](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages) synchron ausgeführt wird.
* Wenn die Website für die Verwendung von DTM zur Bereitstellung von Target-Bibliotheken konfiguriert ist, stellen Sie sicher, dass die Option **Von DTM gelieferte Clientlib verwenden** in der [Target-Konfiguration](https://helpx.adobe.com/de/experience-manager/6-3/sites/administering/using/target-configuring.html) für die Website aktiviert ist.

### Bei Verwendung von AT.js ab Version 1.3 wird immer ein Standardangebot anstelle des richtigen Angebots angezeigt {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Standardmäßig sind AEM 6.2 und 6.3 nicht mit AT.js der Version 1.3.0 oder höher kompatibel. Ab AT.js Version 1.3.0 wird eine Parametervalidierung für die APIs eingeführt, d. h. `adobe.target.applyOffer()` muss einen „mbox“-Parameter enthalten, der vom `atjs-itegration.js`-Code nicht bereitgestellt wird.

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

Sie müssen sicherstellen, dass A4T für Ihr Target-Konto ordnungsgemäß aktiviert ist, indem Sie die folgende Überprüfungsanfrage an AEM senden:

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

Nachfolgend werden zwei Target-APIs vorgestellt, die bei der Behebung von Target-Problemen hilfreich sein können:

* Ruft den Target-Endpunkt für einen bestimmten Clientcode ab:

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json

{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Ruft das Profil einer Kundin oder eines Kunden ab:

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
