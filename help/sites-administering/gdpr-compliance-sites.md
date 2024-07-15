---
title: AEM Sites – Einhaltung der DSGVO
description: Erfahren Sie mehr über die Verarbeitungsprozeduren für DSGVO-Anfragen in AEM Sites und wie sie verwendet werden.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: 8c1ea483-7319-4e5c-be4c-d43a2b67d316
solution: Experience Manager, Experience Manager Sites
feature: Compliance
role: Admin, Architect, Developer, Leader, User, Data Architect, Data Engineer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 100%

---

# AEM Sites – Einhaltung der DSGVO{#aem-sites-gdpr-readiness}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel benutzt, aber die genannten Details lassen sich auf alle Regulierungen zum Datenschutz anwenden; zum Beispiel GDPR, CCPA usw.

Die Datenschutz-Grundverordnung der Europäischen Union ist seit Mai 2018 in Kraft.

AEM Sites ist bereit, Kundinnen und Kunden bei der Erfüllung ihrer DSGVO-Verpflichtungen zu unterstützen. Auf dieser Seite werden die Verfahren zur Handhabung DSGVO-bezogener Anfragen in AEM Sites beschrieben. Sie beschreibt den Speicherort der privaten Daten und wie diese manuell oder per Code entfernt werden können.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Adobe Privacy Center](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [AEM – Einhaltung der DSGVO](/help/managing/data-protection-and-privacy.md).

## Authoring-Server {#author-server}

Auf dem Authoring-Server gespeicherte Benutzerkonten und benutzergenerierte Inhalte (User Generated Content, UGC) werden in der [DSGVO-Dokumentation zur Plattform](/help/managing/data-protection-and-privacy.md) erläutert.

## Veröffentlichungs-Server {#publish-server}

Die für die Authentifizierung von Besuchenden der Website verwendeten Benutzerkonten und die UGC-Inhalte, die auf dem Veröffentlichungs-Server gespeichert werden, werden in der [DSGVO-Dokumentation zur Plattform](/help/managing/data-protection-and-privacy.md) erläutert.

Standardmäßig speichern die Komponenten von AEM Sites keine von Besuchenden auf dem Publishing-Server eingegebenen Daten. Es wird empfohlen, diese Daten zur weiteren Verarbeitung an ein Drittanbietersystem oder an Adobe Campaign zu übermitteln.

## Opt-in/Opt-out {#opt-in-opt-out}

AEM bietet einen [Service zum Deaktivieren von Cookies](/help/sites-developing/cookie-optout.md), mit dem die Entscheidung der Benutzer bezüglich der Verwendung von Cookies verwaltet werden kann.

## Enhanced Insights von Analytics {#enhanced-insights-by-analytics}

AEM Sites bietet eine optionale Integration mit Enhanced Insights von Analytics, das Funktionen innerhalb von On-demand Service von Adobe Analytics nutzt.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von betroffenen Personen in Adobe Analytics finden Sie unter [Adobe Analytics und DSGVO](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-overview.html?lang=de).

## Verbesserte Personalisierung durch Target {#enhanced-personalization-by-target}

AEM Sites bietet eine optionale Integration mit verbesserter Personalisierung durch Target, das Funktionen innerhalb des On-Demand-Service von Adobe Target verwendet.

Weitere Informationen zur Verwaltung von DSGVO-Anfragen von betroffenen Personen in Adobe Target finden Sie unter [Adobe Target – Datenschutz und die DSGVO](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=de).

## ContextHub {#contexthub}

AEM bietet mit [ContextHub](/help/sites-developing/contexthub.md) eine optionale Datenebene. Dadurch werden besucherspezifische Daten im Browser beibehalten, die für eine regelbasierte Personalisierung verwendet werden können.

Standardmäßig werden diese Besucherdaten nicht in AEM gespeichert. AEM sendet Regeln an die Datenschicht, um im Browser Personalisierungsentscheidungen zu treffen.

>[!NOTE]
>
>Vor Adobe CQ 5.6 hat ClientContext (eine frühere Version von ContextHub) die Daten an den Server gesendet, aber nicht gespeichert.
>
>Adobe CQ 5.5 und frühere Versionen wurden mittlerweile eingestellt und werden in dieser Dokumentation nicht behandelt.

### Implementieren von Opt-in-/Opt-out-Komponenten {#implementing-opt-in-opt-out}

Der Site-Eigentümer oder die Site-Eigentümerin muss eine Opt-out-Komponente gemäß den folgenden Richtlinien implementieren.

Diese Richtlinien sehen eine standardmäßige Opt-in-Implementierung vor. Deshalb müssen Website-Besuchende klar zustimmen, bevor personenbezogene Daten im Persistenzspeicher des Browsers (auf Client-Seite) abgelegt werden.

* Die Opt-out-Komponente sollte immer dann integriert werden, wenn die ContextHub-Komponente vorhanden ist.
* Die Datenschutz-bezogenen Bedingungen für die Website müssen den Website-Besuchenden angezeigt werden, um ihnen Folgendes zu ermöglichen:

   * Akzeptieren der Bedingungen
   * Ablehnen der Bedingungen
   * Ändern der vorherigen Auswahl

* Wenn Site-Besuchende die Nutzungsbedingungen der Site akzeptieren, sollte das ContextHub-Opt-out-Cookie entfernt werden:

  ```
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  ```

* Wenn Besuchende der Site die Nutzungsbedingungen der Site nicht akzeptieren, sollte das ContextHub-Ausschluss-Cookie gesetzt werden:

  ```
  ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
  ```

* Um zu überprüfen, ob ContextHub im Opt-out-Modus ausgeführt wird, sollte der folgende Aufruf in der Browser-Konsole erfolgen:

  ```
  var isOptedOut = ContextHub.isOptedOut(true) === true;
  // if isOptedOut is true, ContextHub is running in opt-out mode
  ```

### Vorschau der ContextHub-Persistenz {#previewing-persistence-of-contexthub}

Um eine Vorschau der von ContextHub verwendeten Persistenz zu sehen, können Benutzende:

* Die Browser-Konsole verwenden, zum Beispiel:

   * Chrome:

      * Öffnen Sie: Entwicklertools > Applikation > Speicher:

         * Lokaler Speicher => (Website) => ContextHubPersistence
         * Sitzungsspeicher => (Website) => ContextHubPersistence
         * Cookies => (Website) => SessionPersistence

   * Firefox:

      * Öffnen Sie: Entwicklertools > Konsole:

         * Lokaler Speicher => (Website) => ContextHubPersistence
         * Sitzungsspeicher => (Website) => ContextHubPersistence
         * Cookies => (Website) => SessionPersistence

   * Safari:

      * Öffnen Sie: Einstellungen > Erweitert > Entwicklungsmenü in der Menüleiste anzeigen
      * Öffnen Sie: Entwickeln > JavaScript-Konsole anzeigen

         * Konsole => Speicher => Lokaler Speicher => (Website) => ContextHubPersistence
         * Konsole => Speicher => Sitzungsspeicher => (Website) => ContextHubPersistence
         * Konsole => Speicher => Cookies => (Website) => ContextHubPersistence

   * Internet Explorer:

      * Öffnen Sie „Entwicklertools“ > „Konsole“:

         * localStorage.getItem(&#39;ContextHubPersistence&#39;)
         * sessionStorage.getItem(&#39;ContextHubPersistence&#39;)
         * document.cookie

* Verwenden Sie die ContextHub-API in der Browser-Konsole:

   * ContextHub bietet die folgenden Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (default)
      * ContextHub.Utils.Persistence.Modes.SESSION
      * ContextHub.Utils.Persistence.Modes.COOKIE
      * ContextHub.Utils.Persistence.Modes.WINDOW

     Der ContextHub-Store definiert, welche Persistenzschicht verwendet wird. Damit der aktuelle Status der Persistenz angezeigt wird, sollten alle Ebenen überprüft werden.

So zeigen Sie beispielsweise in localStorage gespeicherte Daten an:

Um eine Vorschau der von ContextHub verwendeten Persistenz zu sehen, können Benutzende:

* Verwenden Sie die Browser-Konsole:

   * In Chrome öffnen Sie: Developer Tools > Applikation > Speicher:

      * Lokaler Speicher => (Website) => ContextHubPersistence
      * Sitzungsspeicher => (Website) => ContextHubPersistence
      * Cookies => (Website) => SessionPersistence

   * In Firefox öffnen Sie: Entwicklertools > Speicher:

      * Lokaler Speicher => (Website) => ContextHubPersistence
      * Sitzungsspeicher => (Website) => ContextHubPersistence
      * Cookies => (Website) => SessionPersistence

* Verwenden Sie die ContextHub-API in der Browser-Konsole:

   * ContextHub bietet die folgenden Datenpersistenzschichten:

      * ContextHub.Utils.Persistence.Modes.LOCAL (default)
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

* So löschen Sie die Persistenz von aktuell geladenen Speichern:

  ```
  // to be able to fully access persistence layer, Opt-Out must be turned off
  ContextHub.Utils.Cookie.removeItem('cq-opt-out');
  
  // following call asks all currently loaded stores to clear their data
  ContextHub.cleanAllStores();
  
  // following call asks all currently loaded stores to set back default values (provided in their configs)
  ContextHub.resetAllStores();
  ```

* So löschen Sie eine bestimmte Persistenzschicht, z. B. sessionStorage:

  ```
  var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
  storage.setItem('/store', null);
  storage.setItem('/_', null);
  
  // to confirm that nothing is stored:
  console.log(storage.getTree());
  ```

* Um alle ContextHub-Persistenzschichten zu löschen, muss der entsprechende Code für alle Ebenen aufgerufen werden:

   * ContextHub.Utils.Persistence.Modes.LOCAL (default)
   * ContextHub.Utils.Persistence.Modes.SESSION
   * ContextHub.Utils.Persistence.Modes.COOKIE
   * ContextHub.Utils.Persistence.Modes.WINDOW
