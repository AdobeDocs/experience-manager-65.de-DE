---
title: AEM Sites – Einhaltung der Datenschutz-Grundverordnung
seo-title: AEM Sites – Einhaltung der Datenschutz-Grundverordnung
description: Hier erfahren Sie, wie AEM Sites die Anforderungen der Datenschutz-Grundverordnung erfüllt.
seo-description: Hier erfahren Sie, wie AEM Sites die Anforderungen der Datenschutz-Grundverordnung erfüllt.
uuid: 00d1fdce-ef9a-4902-a7a5-7225728e8ffc
contentOwner: aheimoz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 772f6188-5e0b-4e66-b94a-65a0cc267ed3
exl-id: 8c1ea483-7319-4e5c-be4c-d43a2b67d316
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 91%

---

# AEM Sites – Einhaltung der Datenschutz-Grundverordnung{#aem-sites-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die betroffenen Informationen gelten jedoch für alle Datenschutz- und Datenschutzbestimmungen. wie DSGVO, CCPA usw.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft.

AEM Sites kann Kunden bei der Erfüllung ihrer DSGVO-Compliancepflichten unterstützen. Auf dieser Seite werden die Verfahren zur Handhabung DSGVO-bezogener Anfragen in AEM Sites beschrieben. Sie beschreibt den Speicherort der privaten Daten und wie diese manuell oder per Code entfernt werden können.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Weitere Details hierzu finden Sie unter [Einhaltung der Datenschutz-Grundverordnung mit AEM](/help/managing/data-protection-and-privacy.md).

## Autorenserver {#author-server}

Auf dem Autorenserver gespeicherte Benutzerkonten und benutzergenerierte Inhalte (User Generated Content, UGC) werden in der [DSGVO-Dokumentation für die Plattform](/help/managing/data-protection-and-privacy.md) erläutert.

## Publish-Server {#publish-server}

Die für die Authentifizierung von Besuchern verwendeten Benutzerkonten und die UGC-Inhalte, die auf dem Publish-Server gespeichert werden, werden in der [DSGVO-Dokumentation für die Plattform](/help/managing/data-protection-and-privacy.md) erläutert.

Standardmäßig speichern die Komponenten von AEM Sites keine von Besuchern eingegebenen Daten auf dem  Veröffentlichungs-Server. Es wird empfohlen, diese Daten zur weiteren Verarbeitung an ein Drittanbietersystem oder an Adobe Campaign zu übermitteln.

## Opt-in/Opt-out {#opt-in-opt-out}

AEM verfügt über einen [Cookie-Opt-out-Dienst](/help/sites-developing/cookie-optout.md) , der für die Verwaltung des Opt-in/Opt-outs für Benutzer verwendet werden kann.

## Enhanced Insights by Analytics {#enhanced-insights-by-analytics}

AEM Sites bietet eine optionale Integration mit Enhanced Insights by Analytics, das Funktionen innerhalb des On-Demand-Service von Adobe Analytics verwendet.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von Datensubjekten in Adobe Analytics finden Sie unter [Adobe Analytics und die DSGVO](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-overview.html).

## Verbesserte Personalisierung durch Target  {#enhanced-personalization-by-target}

AEM Sites bietet eine optionale Integration mit verbesserter Personalisierung durch Target, das Funktionen innerhalb des On-Demand-Service von Adobe Analytics verwendet.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von Datensubjekten in Adobe Target finden Sie unter [Adobe Target – Datenschutz und die DSGVO](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

AEM bietet eine optionale Datenschicht mit [ContextHub](/help/sites-developing/contexthub.md). Dadurch verbleiben besucherspezifische Daten im Browser, die dort für eine regelbasierte Personalisierung verwendet werden.

Standardmäßig werden diese Besucherdaten nicht in AEM gespeichert. AEM übermittelt Regeln an die Datenebene, sodass personalisierungsbezogene Entscheidungen direkt im Browser getroffen werden.

>[!NOTE]
>
>Vor Adobe CQ 5.6 wurden die Daten durch ClientContext (eine frühere Version von ContextHub) an den Server übermittelt, jedoch nicht auf diesem gespeichert.
>
>Adobe CQ 5.5 und frühere Versionen wurden mittlerweile eingestellt und werden in dieser Dokumentation nicht behandelt.

### Implementieren von Opt-in-/Opt-out-Komponenten  {#implementing-opt-in-opt-out}

Der Website-Inhaber muss eine Opt-out-Komponente gemäß den folgenden Richtlinien implementieren.

Diese Richtlinien sehen eine standardmäßige Opt-in-Implementierung vor. Deshalb müssen Website-Besucher klar zustimmen, bevor personenbezogene Daten im Persistenzspeicher des Browsers (auf Clientseite) abgelegt werden.

* Die Opt-out-Komponente sollte immer dann integriert werden, wenn die ContextHub-Komponente vorhanden ist.
* Die DSGVO-bezogenen Bedingungen für die Website müssen Website-Besuchern angezeigt werden, um ihnen Folgendes zu ermöglichen:

   * Akzeptieren der Bedingungen
   * Ablehnen der Bedingungen
   * Ändern der vorherigen Auswahl

* Wenn ein Besucher der Website die zugehörigen Nutzungsbedingungen akzeptiert, sollte das ContextHub-Opt-out-Cookie entfernt werden:

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* Wenn ein Besucher der Website die zugehörigen Nutzungsbedingungen nicht akzeptiert, sollte das ContextHub-Opt-out-Cookie gesetzt werden:

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* Um zu überprüfen, ob ContextHub im Opt-out-Modus ausgeführt wird, sollte folgender Aufruf in der Browserkonsole erfolgen:

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### Vorschau der ContextHub-Persistenz  {#previewing-persistence-of-contexthub}

Zum Anzeigen der von ContextHub verwendeten Persistenz bestehen folgende Möglichkeiten:

* Verwenden der Browserkonsole, z. B.:

   * Chrome:

      * Öffnen Sie „Entwicklertools“ > „Anwendung“ > „Speicher“:

         * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Firefox:

      * Öffnen Sie „Entwicklertools“ > „Speicher“:

         * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Safari:

      * Öffnen Sie „Voreinstellungen“ > „Erweitert“ > „Menü ‚Entwickeln‘ in der Menüleiste anzeigen“.
      * Öffnen Sie „Entwickeln“ > „JavaScript-Konsole anzeigen“:

         * „Konsole“ > „Speicher“ > „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Konsole“ > „Speicher“ > „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Konsole“ > „Speicher“ > „Cookies“ > „(Website)“ > „ContextHubPersistence“
   * Internet Explorer:

      * Öffnen Sie „Entwicklertools“ > „Konsole“:

         * localStorage.getItem(&#39;ContextHubPersistence&#39;)
         * sessionStorage.getItem(&#39;ContextHubPersistence&#39;)
         * document.cookie




* Verwenden der ContextHub-API in der Browserkonsole:

   * ContextHub bietet folgende Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (Standard)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW

      Der ContextHub-Speicher definiert, welche Persistenzschicht verwendet wird. Um den aktuellen Status der Persistenz anzuzeigen, sollten daher alle Schichten überprüft werden.


So können beispielsweise in localStorage gespeicherte Daten angezeigt werden:

Zum Anzeigen der von ContextHub verwendeten Persistenz bestehen folgende Möglichkeiten:

* Verwenden der Browserkonsole:

   * Öffnen Sie in Chrome „Entwicklertools“ > „Anwendung“ > „Speicher“:

      * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
      * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
      * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Öffnen Sie in Firefox „Entwicklertools“ > „Speicher“:

      * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
      * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
      * „Cookies“ > „(Website)“ > „SessionPersistence“


* Verwenden der ContextHub-API in der Browserkonsole:

   * ContextHub bietet folgende Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (Standard)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW

      Der ContextHub-Speicher definiert, welche Persistenzschicht verwendet wird. Um den aktuellen Status der Persistenz anzuzeigen, sollten daher alle Schichten überprüft werden.


So können beispielsweise in localStorage gespeicherte Daten angezeigt werden:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Löschen der ContextHub-Persistenz  {#clearing-persistence-of-contexthub}

So löschen Sie die ContextHub-Persistenz:

* So löschen Sie die Persistenz von aktuell geladenen Speichern:

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* So löschen Sie eine bestimmte Persistenzschicht, z. B. „sessionStorage“:

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* Um alle ContextHub-Persistenzschichten zu löschen, muss der entsprechende Code für alle Ebenen aufgerufen werden:

   * ContextHub.Utils.Persistence.Modes.LOCAL (Standard)
   * ContextHub.Utils.Persistence.Modes.SESSION
   * ContextHub.Utils.Persistence.Modes.COOKIE
   * ContextHub.Utils.Persistence.Modes.WINDOW
