---
title: Anpassen des Adobe Analytics-Frameworks
seo-title: Anpassen des Adobe Analytics-Frameworks
description: 'null'
seo-description: 'null'
uuid: 444a29c2-3b4e-4d21-adc0-5f317ece2b77
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 11c0aac6-a7f6-4d6b-a080-b04643045a64
translation-type: tm+mt
source-git-commit: 0dc96f07e45ccbfea4edc87431677ada5b1bfa8c

---


# Anpassen des Adobe Analytics-Frameworks{#customizing-the-adobe-analytics-framework}

Das Adobe Analytics-Framework bestimmt die Informationen, die mit Adobe Analytics verfolgt werden. Um das Standardframework anzupassen, verwenden Sie JavaScript, um benutzerdefinierte Verfolgung hinzuzufügen, Adobe Analytics-Plugins zu integrieren und allgemeine Einstellungen in dem für die Verfolgung verwendeten Framework zu ändern.

## Das generierte JavaScript für Frameworks {#about-the-generated-javascript-for-frameworks}

When a page is associated with a Adobe Analytics framework, and the page includes [references to the Analytics module](/help/sites-administering/adobeanalytics.md), a analytics.sitecatalyst.js file is automatically generated for the page.

The javascript in the page creates an `s_gi`object (that the s_code.js Adobe Analytics library defines) and assigns values to its properties. Der Name der Objektinstanz ist `s`. Die Code-Beispiele, die in diesem Abschnitt gezeigt werden, verweisen häufiger auf diese `s`-Variable.

Der folgende Beispielcode ähnelt dem Code in der Datei analytics.sitecatalyst.js:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;

s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";

/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

Wenn Sie mit angepasstem JavaScript-Code das Framework anpassen, ändern Sie den Inhalt dieser Datei.

## Adobe Analytics-Eigenschaften konfigurieren {#configuring-adobe-analytics-properties}

Adobe Analytics verfügt über eine Reihe vordefinierter Variablen, die in einem Framework konfiguriert werden können. The **charset**, **cookieLifetime**, **currencyCode** and **trackInlineStats** variables are included in the **General Analytics Settings** list by default.

![aa-22](assets/aa-22.png)

Sie können Variablennamen und -werte zur Liste hinzufügen. These predefined variables and any variables that you add are used to configure the properties of the `s` object in the analytics.sitecatalyst.js file. Das folgende Beispiel zeigt, wie die hinzugefügte Eigenschaft `prop10` mit dem Wert `CONSTANT` im JavaScript-Code dargestellt wird:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.prop10= 'CONSTANT';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;

s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";
```

Mit dem folgenden Verfahren können Sie Variablen zur Liste hinzufügen:

1. Erweitern Sie auf Ihrer Adobe Analytics-Framework-Seite den Bereich **Allgemeine Analytics-Einstellungen** .
1. Klicken Sie unter der Liste der Variablen auf „Element hinzufügen“, um eine neue Variable zur Liste hinzuzufügen.
1. Geben Sie in der linken Zelle einen Namenfür die Variable ein, zum Beispiel `prop10`.

1. Geben Sie in der rechten Spalte einen Wertfür die Variable ein, zum Beispiel `CONSTANT`.

1. Um eine Variable zu entfernen, klicken Sie auf das Minuszeichen (-) neben der Variablen.

>[!NOTE]
>
>Stellen Sie bei der Eingabe von Variablen und Werten sicher, dass sie korrekt formatiert und geschrieben sind. Andernfalls werden die **Aufrufe nicht** mit dem korrekten Wert/Variable-Paar gesendet. Falsch geschriebene Variablen und Werte können Aufrufe sogar komplett verhindern.
>
>Wenden Sie sich an Ihren Adobe Analytics-Kundenbetreuer, um sicherzustellen, dass diese Variablen korrekt eingestellt sind.

>[!CAUTION]
>
>Some of the variables in this list are **mandatory** in order for Adobe Analytics calls to function correctly, (e.g. **currencyCode**, **charSet**)
>
>Selbst wenn sie also selbst aus dem Framework entfernt werden, werden sie beim Aufruf von Adobe Analytics weiterhin mit einem Standardwert versehen.

### Hinzufügen von benutzerdefiniertem JavaScript zu einem Adobe Analytics Framework {#adding-custom-javascript-to-an-adobe-analytics-framework}

The free-from javascript box in the **General Analytics Settings** area enables you to add custom code to a Adobe Analytics framework.

![aa-21](assets/aa-21.png)

Der Code, den Sie hinzufügen, wird an die Datei analytics.sitecatalyst.js angehängt. Therefore, you can access the `s` variable, which is an instance of the `s_gi` javascript object that is defined in `s_code.js`. Wenn Sie beispielsweise den folgenden Code hinzufügen, entspricht dies dem Hinzufügen einer Variable namens `prop10` mit dem Wert `CONSTANT` (das Beispiel aus dem vorhergehenden Abschnitt):

`s.prop10= 'CONSTANT';`

The code in the [analytics.sitecatalyst.js](/help/sites-developing/extending-analytics-components.md) file (which includes the content of the Adobe Analytics `s-code.js` file) contains the following code:

`if (s.usePlugins) s.doPlugins(s)`

Im folgenden Verfahren wird veranschaulicht, wie Adobe Analytics-Verfolgung mithilfe des JavaScript-Felds angepasst werden kann. If your javascript needs to use Adobe Analytics plugins, [integrate them](/help/sites-administering/adobeanalytics.md) into AEM.

1. Fügen Sie den folgenden JavaScript-Code in das Feld ein, damit `s.doPlugins` ausgeführt wird:

   ```
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom code here
   }
   s.doPlugins=s_doPlugins;
   ```

   >[!CAUTION]
   >
   >Dieser Code ist erforderlich, wenn Sie Variablen in einem Adobe Analytics-Aufruf senden möchten, die auf eine Weise angepasst wurden, die nicht über die einfache Drag&amp;Drop-Oberfläche ODER über Inline-JavaScript in der Adobe Analytics-Ansicht durchgeführt werden kann.
   >
   >Wenn die benutzerdefinierten Variablen außerhalb der Funktion s_doPlugins liegen, werden sie als *undefined *im Adobe Analytics-Aufruf gesendet

1. Add your javascript code in the **s_doPlugins** function.

Beim folgenden Beispiel werden die auf einer Seite erfassten Daten in hierarchischer Reihenfolge verbunden. Dabei wird das gemeinsame Trennzeichen „|“ genutzt.

Ein Adobe Analytics-Framework verfügt über die folgenden Konfigurationen:

* Die `prop2` Adobe Analytics-Variable wird der `pagedata.sitesection` Site-Eigenschaft zugeordnet.

* Die `prop3` Adobe Analytics-Variable wird der `pagedata.subsection` Site-Eigenschaft zugeordnet.

* Der folgende Code wird im Freiform-JavaScript-Feld hinzugefügt:

   ```
   s.usePlugins=true;
    function s_doPlugins(s) {
    s.prop1 = s.prop2+'|'+s.prop3;
    }
    s.doPlugins=s_doPlugins;
   ```

* Wenn die Webseite, die das Framework verwendet, besucht wird (oder die Seite im Bearbeitungsmodus neu geladen oder in der Vorschau angezeigt wird), werden die Aufrufe an Adobe Analytics ausgeführt.

Folgende Werte werden beispielsweise in Adobe Analytics generiert:

![aa-20](assets/aa-20.png)

### Adding Global Custom Code for All Adobe Analytics Frameworks {#adding-global-custom-code-for-all-adobe-analytics-frameworks}

Stellen Sie benutzerdefinierten JavaScript-Code bereit, der in alle Adobe Analytics-Frameworks integriert ist. When a page&#39;s Adobe Analytics framework contains no custom [free-form javascript](/help/sites-administering/adobeanalytics.md), the javascript that the /libs/cq/analytics/components/sitecatalyst/config.js.jsp script generates is appended to the [analytics.sitecatalyst.js](/help/sites-administering/adobeanalytics.md) file. Standardmäßig hat das Skript keine Wirkung, da es auskommentiert ist. The code also sets `s.usePlugins` to `false`:

```
/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

Code in der Datei &quot;analytics.sitecatalyst.js&quot;(die den Inhalt der Datei &quot;s_code.js&quot;von Adobe Analytics enthält) enthält den folgenden Code:

if (s.usePlugins) s.doPlugins(s)

Therefore, your javascript should set `s.usePlugins` to `true` so that any code in the `s_doPlugins` function is executed. Um den Code anzupassen, überlagern Sie die Datei config.js.jsp mit einer Datei, die Ihr eigenes JavaScript nutzt. If your javascript needs to use Adobe Analytics plugins, [integrate them](/help/sites-administering/adobeanalytics.md) into AEM.

>[!NOTE]
>
>Bearbeiten Sie die Datei /libs/cq/analytics/components/sitecatalyst/config.js.jsp nicht. Bei bestimmten AEM-Upgrade- oder Wartungsaufgaben wird möglicherweise die Originaldatei erneut installiert und ihre Änderungen werden dabei entfernt.

1. Erstellen Sie in CRXDE Lite die Ordnerstruktur /apps/cq/analytics/components:

   1. Klicken Sie mit der rechten Maustaste auf den Ordner /apps und anschließend auf „Erstellen“ > „Ordner erstellen“.
   1. Legen Sie als Ordnernamen `cq` fest und klicken Sie auf „OK“.
   1. Similarly, create the `analytics` and `components` folders.

1. Klicken Sie mit der rechten Maustaste auf den Ordner `components`, den Sie gerade erstellt haben, und klicken Sie auf „Erstellen“ > „Komponente erstellen“. Legen Sie die folgenden Eigenschaftswerte fest:

   * Etikett: `sitecatalyst`
   * Titel: `sitecatalyst`
   * Super Type: `/libs/cq/analytics/components/sitecatalyst`
   * Gruppe: `hidden`

1. Klicken Sie mehrfach auf „Weiter“, bis die Schaltfläche „OK“ aktiviert wird, und klicken Sie dann auf „OK“.

   Die SiteCatalyst-Komponente enthält die automatisch erstellte Datei sitecatalyst.jsp.

1. Klicken Sie mit der rechten Maustaste auf die Datei sitecatalyst.jsp und klicken Sie dann auf „Löschen“.

1. Klicken Sie mit der rechten Maustaste auf die SiteCatalyst-Komponente und klicken Sie auf „Erstellen“ > „Datei erstellen“. Legen Sie den Namen `config.js.jsp` fest und klicken Sie dann auf „OK“.

   Die Datei config.js.jsp wird automatisch zur Bearbeitung geöffnet.

1. Fügen Sie den folgenden Text zur Datei hinzu und klicken Sie auf „Alle speichern“:

   ```java
   <%@page session="true"%>
   /* Plugin Config */
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom plugin code here
   }
   s.doPlugins=s_doPlugins;
   ```

   Der JavaScript-Code, den das Skript /apps/cq/analytics/components/sitecatalyst/config.js.jsp generiert, wird jetzt für alle Seiten, die ein Adobe Analytics-Framework verwenden, in die Datei &quot;analytics.sitecatalyst.js&quot;eingefügt.

1. Fügen Sie den JavaScript-Code hinzu, den Sie in der Funktion `s_doPlugins` ausführen möchten, und klicken Sie auf „Alle speichern“.

>[!CAUTION]
>
>Wenn im Freiform-JavaScript des Frameworks einer Seite Text vorhanden ist (selbst, wenn es sich nur um Leerzeichen handelt), wird config.js.jsp ignoriert.

### Using Adobe Analytics Plugins in AEM {#using-adobe-analytics-plugins-in-aem}

Rufen Sie den JavaScript-Code für Adobe Analytics-Plugins ab und integrieren Sie sie in Ihr Adobe Analytics-Framework in AEM. Fügen Sie den Code zu einem Client-Bibliotheksordner der Kategorie `sitecatalyst.plugins` hinzu, damit sie für den angepassten JavaScript-Code verfügbar sind.

Wenn Sie beispielsweise das Plug-in `getQueryParams` integrieren, können Sie dieses Plug-in über die Funktion `s_doPlugins` des angepassten JavaScripts aufrufen. The following example code sends the query string in **&quot;pid&quot;** from the referrer&#39;s URL as **eVar1**, when a Adobe Analytics call is triggered.

```
s.usePlugins=true;
function s_doPlugins(s) {
   // take the query string from the referrer
   s.eVar1=s.getQueryParam('pid','',document.referrer);
}
s.doPlugins=s_doPlugins;
```

AEM installiert die folgenden Adobe Analytics-Plugins, sodass sie standardmäßig verfügbar sind:

* getQueryParam()
* getPreviousValue()
* split()

Der Client-Bibliotheksordner /libs/cq/analytics/clientlibs/sitecatalyst/plugins enthält diese Plugins in der Kategorie sitecatalyst.plugins.

>[!NOTE]
>
>Erstellen Sie einen neuen Client-Bibliotheksordner für Ihre Plug-ins. Do not add plugins to the `/libs/cq/analytics/clientlibs/sitecatalyst/plugins` folder. Dadurch wird sichergestellt, dass Ihre Beiträge zur Kategorie `sitecatalyst.plugins` bei erneuten Installationen oder Upgrades von AEM nicht überschrieben werden.

Mit dem folgenden Verfahren können Sie den Client-Bibliotheksordner für Ihre Plug-ins erstellen. Sie müssen diesen Vorgang nur einmal durchführen. Über das darauffolgende Verfahren können Sie ein Plug-in zum Client-Bibliotheksordner hinzufügen.

1. Öffnen Sie CRXDE Lite in einem Webbrowser. ([http://localhost:4502/crx/de](http://localhost:4502/crx/de))

1. Klicken Sie mit der rechten Maustaste auf den Ordner /apps/my-app/clientlibs und klicken Sie auf Erstellen > Knoten erstellen. Geben Sie die folgenden Eigenschaftswerte ein und klicken Sie dann auf „OK“:

   * Name: ein Name für den Client-Bibliotheksordner, z. B. „meine-plug-ins“

   * Typ: cq:ClientLibraryFolder

1. Wählen Sie den gerade erstellten Client-Bibliotheksordner aus und fügen Sie über die Eigenschaftsleiste rechts unten die folgende Eigenschaft hinzu:

   * Name: categories
   * Typ: String
   * Wert: sitecatalyst.plugins
   * Multi: ausgewählt
   Klicken Sie im Eigenschaftsfenster auf „OK“, um den Eigenschaftswert zu bestätigen.

1. Klicken Sie mit der rechten Maustaste auf den Client-Bibliotheksordner, den Sie gerade erstellt haben, und klicken Sie auf „Erstellen“ > „Datei erstellen“. Geben Sie als Dateinamen „js.txt“ ein und klicken Sie dann auf „OK“.

1. Klicken Sie auf „Alle speichern“.

Mit dem folgenden Verfahren können Sie sich den Plug-in-Code beschaffen, den Code im AEM-Repository speichern und den Code zu Ihrem Client-Bibliotheksordner hinzufügen.

1. Log in to [sc.omniture.com](https://sc.omniture.com) using your Adobe Analytics account.
1. Klicken Sie auf der Landingpage auf „Hilfe“ > „Hilfe-Startseite“.
1. Klicken Sie im Inhaltsverzeichnis links auf „Implementierungs-Plug-ins“.
1. Klicken Sie auf den Link zu dem Plug-in, das Sie hinzufügen möchten. Wenn sich die Seite öffnet, suchen Sie den JavaScript-Quellcode für das Plug-in, wählen Sie den Code aus und kopieren Sie ihn.

1. Klicken Sie mit der rechten Maustaste auf den Client-Bibliotheksordner und klicken Sie auf „Erstellen“ > „Datei erstellen“. Geben Sie als Dateinamen den Namen des zu integrierenden Plug-ins gefolgt von „.js“ ein und klicken Sie dann auf „OK“. Wenn Sie z. B. das Plug-in getQueryParam integrieren, nennen Sie die Datei „getQueryParam.js“.

   Wenn Sie die Datei erstellen, wird sie zur Bearbeitung geöffnet.

1. Kopieren Sie den JavaScript-Code des Plug-ins in die Datei, klicken Sie auf „Alle speichern“ und schließen Sie dann die Datei.

1. Öffnen Sie die Datei js.txt aus dem Client-Bibliotheksordner.

1. Fügen Sie in einer neuen Zeile den Namen der Datei ein, die das Plug-in enthält, z. B. getQueryParam.js. Klicken Sie dann auf „Alle speichern“ und schließen Sie die Datei.

>[!NOTE]
>
>Stellen Sie bei der Verwendung von Plug-ins sicher, dass Sie auch unterstützende Plug-ins integrieren. Andernfalls erkennt das JavaScript des Plug-ins die Aufrufe nicht, die an die Funktionen im unterstützenden Plug-in erfolgen. Beispielsweise muss für das Plug-in getPreviousValue() das Plug-in split() ordnungsgemäß funktionieren.
>
>Den Namen des unterstützenden Plug-ins müssen Sie ebenfalls in die Datei **js.txt** einfügen.
