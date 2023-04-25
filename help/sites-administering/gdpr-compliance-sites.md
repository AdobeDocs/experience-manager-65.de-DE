---
title: AEM Sites – Einhaltung der DSGVO
seo-title: AEM Sites - GDPR Readiness
description: Erfahren Sie mehr über die DSGVO-Bereitschaft für AEM Sites.
seo-description: Learn about the details of GDPR Readiness for AEM Sites.
uuid: 00d1fdce-ef9a-4902-a7a5-7225728e8ffc
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 772f6188-5e0b-4e66-b94a-65a0cc267ed3
exl-id: 8c1ea483-7319-4e5c-be4c-d43a2b67d316
source-git-commit: d8ae63edd71c7d27fe93d24b30fb00a29332658d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 23%

---

# AEM Sites – Einhaltung der DSGVO{#aem-sites-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, aber die behandelten Details gelten für alle Datenschutzbestimmungen wie die DSGVO, CCPA usw.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft.

AEM Sites ist bereit, Kunden bei der Erfüllung ihrer DSGVO-Verpflichtungen zu unterstützen. Diese Seite führt Kunden durch die Verfahren zur Verarbeitung von DSGVO-Anfragen in AEM Sites. Sie beschreibt den Speicherort der privaten Daten und wie diese manuell oder per Code entfernt werden können.

Weitere Informationen finden Sie unter [DSGVO-Seite im Adobe Privacy Center](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Siehe [AEM Einhaltung der DSGVO](/help/managing/data-protection-and-privacy.md) für weitere Informationen.

## Autorenserver {#author-server}

Benutzerkonten und benutzergenerierte Inhalte auf dem Autorenserver werden im Abschnitt [Dokumentation zur DSGVO in Platform](/help/managing/data-protection-and-privacy.md).

## Veröffentlichungsserver {#publish-server}

Benutzerkonten, die zur Authentifizierung von Besuchern auf der Site verwendet werden, und benutzergenerierte Inhalte auf dem Veröffentlichungsserver werden im Abschnitt [Dokumentation zur DSGVO in Platform](/help/managing/data-protection-and-privacy.md).

Standardmäßig speichern die Komponenten von AEM Sites keine von Besuchern auf dem Publishing-Server eingegebenen Daten. Es wird empfohlen, diese Daten zur weiteren Verarbeitung an ein Drittanbietersystem oder an Adobe Campaign zu übermitteln.

## Opt-in/Opt-out {#opt-in-opt-out}

AEM bietet einen [Service zum Deaktivieren von Cookies](/help/sites-developing/cookie-optout.md), mit dem die Entscheidung der Benutzer bezüglich der Verwendung von Cookies verwaltet werden kann.

## Verbesserte Einblicke in Analytics {#enhanced-insights-by-analytics}

AEM Sites bietet eine optionale Integration in Enhanced Insights by Analytics, die Funktionen innerhalb des On-Demand-Dienstes von Adobe Analytics verwendet.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von Datensubjekten im Zusammenhang mit Adobe Analytics finden Sie unter [Adobe Analytics und DSGVO](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-overview.html?lang=de).

## Verbesserte Personalisierung durch Target {#enhanced-personalization-by-target}

AEM Sites bietet eine optionale Integration mit verbesserter Personalisierung durch Target, das Funktionen innerhalb des On-Demand-Service von Adobe Target verwendet.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von Datensubjekten im Zusammenhang mit Adobe Target finden Sie unter [Adobe Target - Privatsphäre und Datenschutz-Grundverordnung](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en).

## ContextHub {#contexthub}

AEM bietet mit [ContextHub](/help/sites-developing/contexthub.md) eine optionale Datenebene. Dadurch werden besucherspezifische Daten im Browser beibehalten, die für eine regelbasierte Personalisierung verwendet werden können.

Standardmäßig werden diese Besucherdaten nicht in AEM gespeichert. AEM sendet Regeln an die Datenschicht, um im Browser Personalisierungsentscheidungen zu treffen.

>[!NOTE]
>
>Vor Adobe CQ 5.6 hat die ClientContext (eine frühere Version von ContextHub) die Daten an den Server gesendet, aber nicht gespeichert.
>
>Adobe CQ 5.5 und frühere Versionen sind jetzt EOL und werden nicht mehr in dieser Dokumentation behandelt.

### Implementieren von Opt-in-/Opt-out-Komponenten {#implementing-opt-in-opt-out}

Der Site-Eigentümer muss eine Opt-out-Komponente gemäß den folgenden Richtlinien implementieren.

Diese Richtlinien implementieren Opt-in als Standard. Daher muss ein Besucher einer Website eindeutig zustimmen, bevor personenbezogene Daten in der (clientseitigen) Persistenz des Browsers gespeichert werden.

* Die Opt-out-Komponente sollte immer dann integriert werden, wenn die ContextHub-Komponente vorhanden ist.
* Die Geschäftsbedingungen, die sich auf die DSGVO für die Website beziehen, müssen dem Besucher der Website angezeigt werden, damit er:

   * Akzeptieren der Bedingungen
   * Ablehnen der Bedingungen
   * Ändern der vorherigen Auswahl

* Wenn ein Site-Besucher die Nutzungsbedingungen der Site akzeptiert, sollte das ContextHub-Opt-out-Cookie entfernt werden:

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* Wenn ein Besucher der Site die Nutzungsbedingungen der Site nicht akzeptiert, sollte das ContextHub-Ausschluss-Cookie gesetzt werden:

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* Um zu überprüfen, ob ContextHub im Opt-out-Modus ausgeführt wird, sollte der folgende Aufruf in der Browser-Konsole erfolgen:

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### Vorschau der ContextHub-Persistenz {#previewing-persistence-of-contexthub}

Zur Vorschau der verwendeten Persistenz kann ein Benutzer:

* Verwenden Sie die Browser-Konsole. Beispiel:

   * Chrome:

      * Öffnen Sie Entwicklertools > Anwendung > Speicher:

         * Lokaler Speicher > (Website) > ContextHubPersistence
         * Sitzungsspeicher > (Website) > ContextHubPersistence
         * Cookies > (Website) > SessionPersistence
   * Firefox:

      * Öffnen Sie Entwicklertools > Speicher:

         * Lokaler Speicher > (Website) > ContextHubPersistence
         * Sitzungsspeicher > (Website) > ContextHubPersistence
         * Cookies > (Website) > SessionPersistence
   * Safari:

      * Öffnen Sie Voreinstellungen > Erweitert > Menü &quot;Entwicklung anzeigen&quot;in der Menüleiste
      * Öffnen Sie &quot;Entwickeln&quot;> &quot;JavaScript-Konsole anzeigen&quot;

         * Konsole > Speicher > Lokaler Speicher > (Website) > ContextHubPersistence
         * Konsole > Speicher > Sitzungsspeicher > (Website) > ContextHubPersistence
         * Konsole > Speicher > Cookies > (Website) > ContextHubPersistence
   * Internet Explorer:

      * Öffnen Sie „Entwicklertools“ > „Konsole“:

         * localStorage.getItem(&#39;ContextHubPersistence&#39;)
         * sessionStorage.getItem(&#39;ContextHubPersistence&#39;)
         * document.cookie




* Verwenden Sie die ContextHub-API in der Browserkonsole:

   * ContextHub bietet die folgenden Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (Standard)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW

      Der ContextHub-Store definiert, welche Persistenzschicht verwendet wird. Damit der aktuelle Status der Persistenz angezeigt wird, sollten alle Ebenen überprüft werden.


So zeigen Sie beispielsweise in localStorage gespeicherte Daten an:

Zur Vorschau der verwendeten Persistenz kann ein Benutzer:

* Verwenden Sie die Browser-Konsole:

   * Chrome - Öffnen Sie &quot;Developer Tools&quot;> &quot;Application&quot;> &quot;Storage&quot;:

      * Lokaler Speicher > (Website) > ContextHubPersistence
      * Sitzungsspeicher > (Website) > ContextHubPersistence
      * Cookies > (Website) > SessionPersistence
   * Firefox - Öffnen Sie Entwicklertools > Speicher:

      * Lokaler Speicher > (Website) > ContextHubPersistence
      * Sitzungsspeicher > (Website) > ContextHubPersistence
      * Cookies > (Website) > SessionPersistence


* Verwenden Sie die ContextHub-API in der Browserkonsole:

   * ContextHub bietet die folgenden Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (Standard)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW

      Der ContextHub-Store definiert, welche Persistenzschicht verwendet wird. Damit der aktuelle Status der Persistenz angezeigt wird, sollten alle Ebenen überprüft werden.


So zeigen Sie beispielsweise in localStorage gespeicherte Daten an:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Löschen der ContextHub-Persistenz {#clearing-persistence-of-contexthub}

So löschen Sie die ContextHub-Persistenz:

* So löschen Sie die Persistenz der aktuell geladenen Stores:

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* So löschen Sie eine bestimmte Persistenzschicht: Beispiel: sessionStorage:

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
