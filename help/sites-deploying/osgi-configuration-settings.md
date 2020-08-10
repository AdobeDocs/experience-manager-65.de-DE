---
title: OSGi-Konfigurationseinstellungen
seo-title: OSGi-Konfigurationseinstellungen
description: In diesem Artikel werden die OSGi-Konfigurationseinstellungen (nach Bundle aufgelistet) beschrieben, die für die Projektimplementierung relevant sind. Die Liste dient als Leitfaden und ist nicht vollständig.
seo-description: In diesem Artikel werden die OSGi-Konfigurationseinstellungen (nach Bundle aufgelistet) beschrieben, die für die Projektimplementierung relevant sind. Die Liste dient als Leitfaden und ist nicht vollständig.
uuid: 192d3287-ec99-403b-bab0-45721e4e3abd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ed3a858c-7a43-4515-a2ff-43ca465c7d7d
docset: aem65
translation-type: tm+mt
source-git-commit: 474fc122f557f32d34fddd9d35a113431f6ce491
workflow-type: tm+mt
source-wordcount: '3805'
ht-degree: 60%

---


# OSGi-Konfigurationseinstellungen{#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) ist ein grundlegendes Element im Technologiestapel von AEM. OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet.

OSGi *bietet standardisierte Grundbausteine – kleine, wiederverwendbare, gemeinsame genutzte Komponenten. Diese Komponenten können zu einer Anwendung zusammengefügt und bereitgestellt werden*&quot;.

Dies ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage)) ist in einem der Bundles enthalten. Beim Arbeiten mit AEM haben Sie verschiedene Möglichkeiten, Konfigurationseinstellungen für diese Bundles zu verwalten. Einzelheiten und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Die folgenden OSGi-Konfigurationseinstellungen (nach Bundle aufgelistet) sind für die Projektimplementierung relevant. Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden nur zum besseren Verständnis von AEM erwähnt.

>[!CAUTION]
>
>Die Liste soll als Leitfaden dienen und ist nicht vollständig. Nicht alle Bundles sind aufgelistet. Und für die genannten Bundles sind nicht alle Parameter aufgelistet.
>
>Die erforderliche Konfiguration hängt vom jeweiligen Projekt ab.
>
>Informationen zu den verwendeten Werten und Details zu den Parametern finden Sie in der Web-Konsole.

>[!NOTE]
>
>Das OSGi Configuration Diff Tool, Teil der [AEM Tools](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), kann zur Liste der standardmäßigen OSGi-Konfigurationen verwendet werden.

>[!NOTE]
>
>Für spezifische Funktionsbereiche in AEM sind möglicherweise weitere Bundles erforderlich. In solchen Fällen können Sie die Konfigurationsdetails der Seite entnehmen, die sich auf die entsprechende Funktion bezieht.

**AEM Replication Ereignis-Listener** konfigurieren:

* Die **Ausführungsmodi**, in denen Replikations-Ereignis an Listener verteilt werden. Wenn dies beispielsweise als &quot;author&quot;definiert ist, wird die Replikation durch dieses System &quot;initiiert&quot;.

* Der **Veröffentlichungsmodus** im Ausführungsmodus muss hinzugefügt werden, wenn der Projektcode Replizierungs-Ereignis (umgekehrte Replizierung) in einer Veröffentlichungs-Umgebung verarbeitet. Wenn der Dispatcher beispielsweise zum Löschen aus der Veröffentlichungsinstanz verwendet wird oder wenn eine standardmäßige Replizierung in andere Veröffentlichungsinstanzen erfolgt.

**AEM Repository Change-Listener** konfigurieren:

* Die **Pfade**, Positionen, die auf Repository-Ereignis warten, die für die Verteilung bereit sind.

**CRX Sling Client Repository** Konfigurieren Sie den Zugriff auf das zugrunde liegende Inhalts-Repository.

* Das **Administratorkennwort** sollte nach der Installation geändert werden, um die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz zu gewährleisten.
* Andere Änderungen sollten nicht erforderlich sein und müssen sorgfältig durchgeführt werden, da sie den Zugriff auf das Repository beeinträchtigen können.

**Wiki-Mail-Dienst** Konfigurieren Sie die E-Mail-Einstellungen für E-Mails, die von einem Wiki gesendet werden.

**Apache Felix OSGi Management Console** konfigurieren:

* **Plug-ins**: die Hauptnavigationselemente (Konsolen-Plug-ins), die als oberste Menüelemente in der **Apache Felix Web Management Console** verfügbar sein sollen. Deaktivieren Sie alle nicht benötigten Elemente, da sie sonst Platz und Ressourcen verbrauchen.

>[!CAUTION]
>
>Stellen Sie sicher, dass Sie Folgendes konfigurieren:
>
>**Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.
>Das Kennwort muss nach der ersten Installation geändert werden, damit die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz gewährleistet ist.

>[!NOTE]
>
>Nehmen Sie diese Konfiguration in der Felix Console vor, die zum Starten erforderlich ist – bevor das Repository verfügbar ist.

**Apache Sling Anpassbare Anforderungsdatenprotokollierer** konfigurieren:

* **Name der Protokollfunktion** und **Protokollformat** für den Speicherort und das Format von Anforderungen und Zugriffsprotokollierung (Standard: `request.log`). Diese Protokolldatei ist sehr wichtig, wenn Sie die Leistung analysieren oder auf die Web-Kette bezogene Funktionen debuggen möchten.
Dieser ist gepaart mit dem [Apache Sling Request Logger](#apacheslingrequestlogger).

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Eventing Thread Pool** Configure:

* **Min Pool Size** and **Max Pool Size**, the size of the pool used to hold event threads.

* **Queue Size**, the maximum size of the thread queue if the pool is exhausted.
The recommended value is `-1` as this sets the queue to unlimited; if a limit is set then losses might occur when it is exceeded.

* Changing these settings can help performance in scenarios with a high number of events; for example, heavy AEM DAM or Workflow usage.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* These settings can affect the performance of your instance, so do not change them without reason and due consideration.

**Apache Sling GET Servlet** Konfigurieren Sie einige Aspekte des Renderings:

* **Auto Index** zum Aktivieren/Deaktivieren der Verzeichnisausgabe beim Browsen.
* **Aktivieren** (oder deaktivieren) Sie Standardausgaben wie **HMTL**, **Nur Text**, **JSON** oder **XML**.
Sie sollten JSON nicht deaktivieren.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Java Script Handler** Configure settings for the compilation of .java files as scripts (servlets).

Bestimmte Einstellungen können die Leistung beeinträchtigen. Deaktivieren Sie diese, falls möglich, insbesondere für Produktionsinstanzen.

* S **ource VM** und **Target VM** definieren die JDK-Version als die für Runtime JVM verwendete Version.

* Für Produktionsinstanzen:

   * Deaktivieren Sie **Generate Debug Info**.

**Apache Sling JCR Installer** Diese Parameter benötigen wahrscheinlich keine Konfiguration, können aber nützlich sein, um zu wissen, wenn Entwicklung oder Debugging. Beispielsweise kann es nützlich sein, die Installationsordner ein- oder auszuchecken oder ein Paket zu erstellen.

* **Installation folders name regexp** und **Max hierarchy depth of install folders** geben an, wo und bis zu welcher Ebene Repository-Ordner nach zu installierenden Ressourcen durchsucht werden. Bei Verwendung eines Platzhalters (wie in*/install) all appropriate matches will be searched, for example, `/libs/sling/install` and `/libs/cq/core/install`.

* **Search Path** listet die Pfade auf, in denen jcrinstall nach zu installierenden Ressourcen sucht, und eine Ziffer, die den Gewichtungsfaktor für den Pfad angibt.

**Apache Sling Job Ereignis Handler** konfiguriert Parameter, die die Auftragsplanung verwalten:

* **Wiederholungsintervall**, **Maximale Weitere Zustellversuche**, **maximale Anzahl paralleler Aufträge**, **Anerkennungswartezeit** u. a.

* Eine Änderung dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Aufträgen verbessern. z. B. starke Nutzung von AEM DAM und Workflows.
* Values specific to your scenario should be established using tests.
* Ändern Sie diese Einstellungen nicht ohne Grund, sondern nur nach gebührender Berücksichtigung.

**Apache Sling JSP Script Handler** Konfigurieren Sie leistungsrelevante Einstellungen für den JSP-Skript-Handler. Um die Leistung zu verbessern, sollten Sie so viele Parameter wie möglich deaktivieren.

Insbesondere für Produktionsinstanzen:

* Deaktivieren Sie **Generate Debug Info**.
* Deaktivieren Sie **Keep Generated Java**.
* Deaktivieren Sie **Mapped Content**.
* Deaktivieren Sie **Display Source Fragments**.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Logging Configuration** konfigurieren:

* **Log Level** und **Log File** definieren den Speicherort und die Protokollebene der zentralen Protokollierungskonfiguration (error.log). The level can be set to one of `DEBUG`, `INFO`, `WARN`, `ERROR` and `FATAL`.

* **Number of Log Files** und **Log File Threshold** geben die Größe und die Versionsrotation der Protokolldatei an.

* **Message Pattern** definiert das Format der Protokollmeldungen.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md#global-logging) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Logging Logger Configuration (Factory Configuration)** konfigurieren:

* **Log Level**, **Log File** und **Message Format** definieren Details in den Protokolldateien und -meldungen.

* **Logger** gibt die Kategorie an, z. B. nur Protokollierungen für com.day.cq.

* Anhand der **Factory-Konfigurationen** können beliebig viele zusätzliche Konfigurationen für die gewünschten Protokollierungsebenen und Kategorien hinzugefügt werden.
* Diese Konfigurationen sind bei der Entwicklung hilfreich, z. B. um TRACE-Benachrichtigungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu erfassen.
* Diese Konfigurationen sind in einer Produktionsumgebung hilfreich, z. B. Benachrichtigungen zu einem bestimmten, in einer Protokolldatei erfassten Dienst für eine einfachere Überwachung.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Logging Writer Configuration (Factory Configuration)** konfigurieren:

* **Log File** gibt an, dass eine Protokolldatei vorhanden ist.
* **Number of Log Files** gibt die Versionsrotation an.

* Der Verfasser kann von **Apache Sling Logging Logger**-Konfigurationen verwendet werden.

* Diese Konfigurationen sind bei der Entwicklung hilfreich, z. B. um TRACE-Benachrichtigungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu erfassen.
* Diese Konfigurationen sind in einer Produktionsumgebung hilfreich, z. B. Benachrichtigungen zu einem bestimmten, in einer Protokolldatei erfassten Dienst für eine einfachere Überwachung.

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Main Servlet** konfigurieren:

* **Number of Calls per Request** und **Recursion Depth**, um das System vor unendlichen Rekursionen und übermäßigen Skript-Aufrufen zu schützen.

**Apache Sling MIME Type Service** konfigurieren:

* **MIME-Typen**, um die für Ihr Projekt erforderlichen Typen hinzuzufügen. Dadurch kann eine `GET`-Anforderung einer Datei die richtige Kopfzeile für den Inhaltstyp zum Verknüpfen von Dateityp und Anwendung festlegen.

**Apache Sling Werber-Filter** Um bekannte Sicherheitsprobleme mit Cross-Site Request Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, müssen Sie den Werber-Filter konfigurieren.

Der Referrer-Filter-Dienst ist ein OSGi-Dienst, mit dem Sie Folgendes konfigurieren können:

* Welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* und eine Liste von Servern, die zusätzlich zum Server-Host zulässig sind.

Weitere Informationen finden Sie unter [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).

>[!NOTE]
>
>Für den Apache Sling Referrer-Filter muss ein Quick Fix-Paket installiert werden.

**Apache Sling Request Logger** Configure:

* unterschiedliche Parameter, die festlegen, wie Anforderungen zugeordnet werden.
* **Enable Request Log** zum Aktivieren oder Deaktivieren.

* **Enable Access Log** zum Aktivieren oder Deaktivieren.

Dies ist gepaart mit dem [Apache Sling Customizable Request Data Logger](#apacheslingcustomizablerequestdatalogger).

Weitere Informationen finden Sie unter [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/site/logging.html).

**Apache Sling Resource Resolver Factory** Konfigurieren Sie zentrale Aspekte der Sling-Ressourcenauflösung:

* **Ressourcensuchpfad**(e), fügen Sie projektspezifische Pfade hinzu (entfernen `/libs` oder `/apps`).

* **Virtual URLs** zum Definieren der Vanity-URL-Zuweisungen.

* **URL-Zuordnungen** zum Definieren von Aliasnamen; zum Beispiel von `/content` zu `/`.

* **Zuordnungsort**, die Zuordnungskonfiguration extern nach `/etc/map`.

* Use your local installation (for example, use `https://localhost:4502/system/console/jcrresolver`) to determine which Resource Resolver is active.

Weitere Informationen finden Sie unter [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution.](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution)

>[!CAUTION]
>
>Insbesondere diese Optionen müssen im Repository konfiguriert werden.
>
>Andernfalls werden die mit der Felix-Konsole vorgenommenen Änderungen an **URL-Zuordnungen** beim nächsten Neustart möglicherweise von AEM überschrieben.

**Apache Sling Servlet/Script Resolver und Error Handler** Das Sling Servlet und der Script Resolver haben mehrere Aufgaben:

1. Sie werden als `ServletResolver` verwendet, die das Servlet oder Skript zum Abwickeln der Anforderung auswählen.

1. It acts as the `SlingScriptResolver`.

1. Sie sind für die Fehlerbehebung zuständig, indem sie die `ErrorHandler`-Schnittstelle implementieren und dabei denselben Algorithmus für Servlets und Skripts auswählen, der auch für Servlets und Skripts für die Anforderungsabwicklung verwendet wird.

Verschiedene Parameter können festgelegt werden, z. B.:

* **Execution Paths** gibt die Pfade an, die nach ausführbaren Skripts durchsucht werden sollen. Durch Konfigurieren bestimmter Pfade können Sie begrenzen, welche Skripts ausgeführt werden. If no path is configured then the default is used ( `/` = root), this allows the execution of all scripts.
Falls ein konfigurierter Pfadwert mit einem Schrägstrich endet, wird die gesamte Unterstruktur durchsucht. Ohne einen Schrägstrich am Ende wird das Skript nur ausgeführt, wenn es sich um eine genaue Übereinstimmung handelt.

* **Script User**: Mit dieser optionalen Eigenschaft kann das Repository-Benutzerkonto angegeben werden, das zum Lesen der Skripts verwendet wird. Falls kein Konto angegeben ist, wird standardmäßig das `admin`-Benutzerkonto verwendet.

* **Default Extensions**: Die Liste der Erweiterungen, für die das Standardverhalten verwendet wird. Dies bedeutet, dass das letzte Pfadsegment des Ressourcentyps als Skriptname verwendet werden kann.

**Day Commons GFX Font Helper** Beim Rendern von Grafiken können Sie DrawText zum Einbetten von Text verwenden. Dazu können Sie auch eigene Schriftarten installieren:

* Definieren Sie den **Schriftpfad** , der nach projektspezifischen Schriftarten gesucht werden soll.
Beispiel: `/apps/myapp/fonts`.

**Apache HTTP-Komponenten Proxy Configuration** Proxy Configuration Proxy-Konfiguration für alle Code, der den Apache HTTP-Client verwendet, wenn ein HTTP-Vorgang ausgeführt wird; z. B. bei der Replikation.

When creating a new configuration, do not make changes to the factory configuration but instead create a new factory configuration for this component using the configuration manager available here: **https://localhost:4502/system/console/configMgr/**. The proxy configuration is available in **org.apache.http.proxyconfigurator.**

>[!NOTE]
>
>In AEM 6.0 und früheren Versionen wurde der Proxy im Day Commons-HTTP-Client konfiguriert. Ab AEM 6.1 erfolgt die Proxy-Konfiguration über die „Apache HTTP Components Proxy Configuration“ anstatt im „Day Commons HTTP Client“.

**Day CQ Antispam** Konfigurieren Sie den verwendeten Anti-Spam-Dienst (Akismet). Hierfür müssen Sie Folgendes registrieren:

* **Provider**
* **API-Schlüssel**
* **Registrierte URL**

**Adobe Granite HTML Library Manager** Konfigurieren Sie dies, um die Handhabung von Client-Bibliotheken (css oder js) zu steuern. einschließlich, wie beispielsweise die zugrunde liegende Struktur gesehen wird.

* Für Produktionsinstanzen:

   * Aktivieren Sie **Minify** (um Neuzeilenzeichen [CRLF] und Leerzeichen zu löschen).
   * Aktivieren Sie **Gzip** (um Dateien als GZIP zu komprimieren und mit einer Anforderung darauf zuzugreifen).
   * Deaktivieren Sie **Debug**.
   * Deaktivieren Sie **Timing**.

* Für die JS-Entwicklung (insbesondere beim Firebugging/Debugging):

   * Deaktivieren Sie **Minify**.
   * Aktivieren Sie **Debug**, um die Dateien für das Debuggen und für die Verwendung mit Firebug zu trennen.
   * Aktivieren Sie **Timing**, falls das Timing von Interesse ist.
   * Aktivieren Sie **Debug Console**, um die Protokollmeldungen der JS-Konsole anzuzeigen.

>[!CAUTION]
>
>When changing the setting for either **Minify** or **Gzip** you will also need to delete the contents of `/var/clientlibs`. Dies ist eine zwischengespeicherte Version der Client-Bibliotheken, die bei der nächsten Anforderung neu erstellt werden.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ HTTP Header Authentication Handler** Systemweite Einstellungen für die einfache Authentifizierungsmethode der HTTP-Anforderung.

Wenn Sie [geschlossene Benutzergruppen](/help/sites-administering/cug.md) verwenden, können Sie u. a. Folgendes konfigurieren:

* Den **HTTP-Bereich**
* Die **Standard-Anmeldeseite**

**Day CQ Link Checker Service** Check und bei Bedarf konfigurieren:

* **Scheduler Period**: definiert das Intervall, in dem externe Links automatisch überprüft werden.

* Überprüfen Sie **Bad Link Tolerance Interval** für den Zeitraum, nach dem ein nicht erfolgreicher externer Link als nicht korrekt betrachtet wird.
* **Link Check Override Patterns**: definiert alle Pfade, die von der Link-Überprüfung ausgenommen werden sollen.

**Day CQ Link Checker-Aufgabe** Einstellungen für eine Aufgabe zur Prüfung einzelner Links konfigurieren (eine Aufgabe, die einen externen Link überprüft):

* Überprüfen Sie die unter **Good Link Test Interval** und **Bad Link Test Interval**  festgelegten Intervalle.

* Die diversen Parameter, die sich auf Proxys für den Internetzugriff und NTLM beziehen und beim Überprüfen eines Links für den externen Zugriff benötigt werden.

**Day CQ Mail Service** Konfigurieren Sie Hostname und Zugriffsdetails für den Mail-Server. Einzelheiten finden Sie im Abschnitt Konfigurieren des E-Mail-Dienstes.

**Day CQ MCM Newsletter** Konfigurieren Sie die verschiedenen Einstellungen, die mit dem Newsletter verwendet werden.

**Tag-CQ-Stammzuordnung** konfigurieren:

* **Target Path** to define where a request to &quot; `/`&quot; will be redirected to.

In AEM sind zwei Benutzeroberflächen verfügbar:

* Die Touch-optimierte Benutzeroberfläche ist die standardmäßige Benutzeroberfläche von AEM
* und die veraltete klassische Benutzeroberfläche ist weiterhin voll funktionsfähig

Mit AEM Root Mapping können Sie die Benutzeroberfläche konfigurieren, die Sie als Standard für Ihre Instanz verwenden möchten:

* To have the touch-enabled UI as the default UI the **Target Path** should point to:

   ```
      /projects.html
   ```

* Wenn Sie die klassische Benutzeroberfläche als Standard verwenden möchten, muss der **Zielpfad** auf Folgendes verweisen:

   ```
      /welcome.html
   ```

>[!NOTE]
>
>Nach einer Standardinstallation wird die Touch-optimierte Benutzeroberfläche zur Standardbenutzeroberfläche.

**Adobe Granite SSO Authentication Handler** Configure Single Sign On (SSO) details; these are often needed in enterprise author setups, often in conjunction with LDAP.

Verschiedene Eigenschaften können konfiguriert werden: 

* **Path** Der Pfad, für den dieser Authentifizierungs-Handler aktiv ist. Wenn dieser Parameter nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert. Beispielsweise wird beim Pfad / der Authentifizierungs-Handler für das gesamte Repository verwendet.

* **Service Ranking** Der Rangfolge-Wert für den OSGi-Framework-Dienst gibt die Reihenfolge an, in der dieser Dienst aufgerufen wird. Dies ist eine 
`int` Wert, bei dem höhere Werte eine höhere Priorität angeben.
Der Standardwert ist `0`.

* **Header Names** Die Namen von Kopfzeilen, die möglicherweise eine Benutzer-ID enthalten.

* **Cookie Names** Die Namen von Cookies, die möglicherweise eine Benutzer-ID enthalten.

* **Parameter Names** Die Namen von Anforderungsparametern, die möglicherweise eine Benutzer-ID angeben.

* **User Map** Für bestimmte Benutzer kann der aus der HTTP-Anforderung extrahierte Benutzername im Anmeldedaten-Objekt durch einen anderen Namen ersetzt werden. Die Zuordnung ist hier definiert. Wenn der Benutzername 
`admin` auf beiden Seiten der Map angezeigt wird, wird die Zuordnung ignoriert. Beachten Sie, dass das Zeichen „=“ durch ein führendes „\“ geschützt werden muss.

* **Format** Gibt das Format an, in dem die Benutzer-ID angegeben ist. Verwenden:

   * `Basic`, falls die Benutzer-ID im HTTP-Standard-Authentifizierungsformat kodiert ist
   * `AsIs`, falls die Benutzer-ID im Nur-Text-Format bereitgestellt wird, oder jeder für reguläre Ausdrücke gültige Wert unverändert bzw. jeder reguläre Ausdruck verwendet werden soll

**Day CQ WCM Debug-Filter** Dies ist nützlich, wenn Sie Entwicklungsprozesse durchführen, da Suffixe wie ?debug=layout beim Zugriff auf eine Seite verwendet werden können. Beispielsweise stellt https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout Layoutinformationen bereit, die für den Entwickler von Interesse sein könnten.

* Deaktivieren Sie diese Option bei Produktionsinstanzen, um die Leistung und Sicherheit zu gewährleisten.

**Day CQ WCM Filter** konfigurieren:

* **WCM-Modus **zum Definieren des Standardmodus.
* On an author instance this might be `edit`, `disable,preview` or `analytics`.
The other modes can be accessed from the sidekick, or the suffix `?wcmmode=disabled` can be used to emulate a production environment.

* Auf einer Veröffentlichungsinstanz muss für diesen Modus `disabled` festgelegt sein, um sicherzustellen, dass keine anderen Modi zugänglich sind.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ WCM Link Checker Configurator** konfigurieren:

* Die **Liste der Rewrite-Konfigurationen** enthält die Speicherorte für Inhalts-basierte Link-Prüfer-Konfigurationen. Die Konfigurationen können auf dem Ausführungsmodus basieren. Es muss zwischen Autoren- und Veröffentlichungsumgebungen unterschieden werden, da die Einstellungen des Link-Prüfers für diese unterschiedlich sein können.

**Day CQ WCM Page Processor** Configure:

* **Paths**: eine Liste der Speicherorte, die das System auf Seitenänderungen überwacht, bevor ein `jcr:Event` ausgelöst wird.

**Adobe Page Impressions Tracker** Für eine Autoreninstanz konfigurieren:

* **sling.auth.requirements**: den Wert dieser Eigenschaft auf `-/libs/wcm/stats/tracker`

>[!CAUTION]
>
>Diese Konfiguration ermöglicht anonyme Anforderungen an den Nachverfolgungsdienst.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Page Statistics** For a publish instance configure:

* **URL to send data**: konfiguriert die zum Nachverfolgen der Seitenstatistiken verwendete URL (wichtig, falls eine Nachverfolgungsanforderung über den Dispatcher geleitet wird); der Standardwert lautet beispielsweise `https://localhost:4502/libs/wcm/stats/tracker`.

* **Tracking script enabled**: aktiviert (`true`) oder deaktiviert (`false`) den Einschluss der Nachverfolgungsskripts auf den Seiten. Der Standardwert ist `false`.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Version Manager** Steuern Sie, ob und wie Versionen in Ihrem System verwaltet werden:

* **Create Version on Activation** ist bei der Standardinstallation aktiviert.
* **Enable Purging**

* **Purge Paths**: die von einem Suchvorgang durchsuchten Pfade.
* **Implicit Versioning Paths**: die Pfade, bei denen die implizite Versionierung aktiv ist.

* **Max Version Age**: das maximale Alter (in Tagen) einer Version.

* **Max Number Versions**: die maximale Anzahl der beizubehaltender Versionen.

Weitere Informationen finden Sie unter [Löschen von Versionen](/help/sites-deploying/version-purging.md).

**Day CQ Workflow Email Notification Service** Configure the email settings for notifications sent by a workflow.

**Day CQSE HTTP Service** Control CQ Servlet Engine:

* **NIO für HTTP, **Ob NIO für HTTP verwendet werden soll oder nicht. Standardwert ist „true“. Wird nur verwendet, wenn HTTP aktiviert ist.
* **Connection Timeout, **Connection timeout in Millisekunden. Diese Eigenschaft gilt für HTTP- und HTTPS-Verbindungen. Defaults to 60 seconds.

* **Enable HTTPS,** Whether or not HTTPS is enabled. Der Standardwert ist false.
* **Session Timeout**, Default lifetime of an HTTP session specified in minutes. If the timeout is 0 or less, sessions will never timeout. Defaults to 10 minutes.
* **Debug-Protokollierung**, ob Meldungen auf DEBUG-Ebene geschrieben werden sollen oder nicht. Der Standardwert ist false.
* **Anforderungs-Puffergröße**, Größe des Puffers für Anforderungen in Byte. Der Standardwert ist 8 KB.
* **Maximale Anzahl an Threads**, maximale Anzahl an Threads, die zur Bearbeitung von Anforderungen verwendet werden. Der Standardwert ist 200.

Die folgenden Eigenschaften gelten nur, wenn HTTPS aktiviert ist.

* **HTTPS-Anschluss**, Anschluss für HTTPS-Anforderung. Standardwert ist 433.
* **NIO für HTTPS**, ob NIO für HTTP verwendet werden soll oder nicht. Der Standardwert ist der NIO-Wert für die HTTP-Eigenschaft.
* **Keystore**, Absoluter Pfad zum Keystore, der für HTTPS verwendet werden soll. Erforderlich, wenn HTTPS aktiviert ist.
* **Keystore Password**, Password, um auf den Keystore zuzugreifen.
* **Key Alias**, Alias des geheimen Schlüssels im Keystore.
* **Key Password**, Password, um den geheimen Schlüssel im Keystore zu entsperren.
* **Client-Zertifikat**, Anforderung, dass der Client ein gültiges Zertifikat bereitstellt. Die Standardeinstellung ist &quot;Ohne&quot;.

Einzelheiten zu den SSL-bezogenen Optionen und eine vollständige Beschreibung zur Aktivierung von HTTPS für CQSE finden Sie unter auch [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md) .

**CQ-Rewriter – HTML-Parser-Factory**

Steuert den HTML-Parser für den CQ-Rewriter.

* **Additional Tags to Process**: Sie können HTML-Tags, die vom Parser verarbeitet werden sollen, hinzufügen oder entfernen. Standardmäßig werden die folgenden Tags verarbeitet: A, IMG, AREA, FORM, BASE, LINK, SCRIPT, BODY, HEAD.
* **Preserve Camel Case** - By default, the HTML parser converts attributes in camel case (e.g. eBay) to lower case (e.g. ebay). Sie können dies jedoch deaktivieren, um die gemischte Groß-/Kleinschreibung von Attributen beizubehalten. Dies ist hilfreich, wenn Sie Frontend-Frameworks wie Angular 2 verwenden.

**Day Commons JDBC Connections Pool** Konfigurieren Sie den Zugriff auf eine externe Datenbank, die als Quelle für Inhalte verwendet wird.

Dies ist eine Factory-Konfiguration, sodass mehrere Instanzen konfiguriert werden. 

**Adobe CQ Media DPS Sessions Service** Manage DPS Sessions for use with Publications.

Insbesondere können Sie `dps.session.service.url.name` konfigurieren. Die Standardeinstellung ist [https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions](https://dpsapi2.digitalpublishing.acrobat.com/webservices/sessions)

**Die Kommunikation zwischen AEM und einem CDN mit dem CDN-Rewriter** muss sichergestellt werden, damit Assets/Binärdateien auf sichere Weise an den Endbenutzer gesendet werden. Dies beinhaltet zwei Aufgaben:

* Den Zugriff auf die Ressource von AEM aus über das CDN beim ersten Versuch (oder wenn sich die Ressource nicht mehr im Zwischenspeicher befindet).
* Den sicheren Zugriff auf die im CDN zwischengespeicherte Ressource, denn sobald die Ressource im CDN zwischengespeichert ist, wird die Anforderung nicht an AEM gerichtet, sondern alle Benutzer mit Zugriff auf die Ressource werden vom CDN bedient.

AEM stellt einen Rewriter für das Neuschreiben interner Asset-URLs als externe CDN-URLs bereit. Für den sicheren Zugriff auf das Asset schreibt AEM Links neu, die an das CDN weitergegeben werden, einschließlich einer JWS-Signatur und einer Ablaufzeit. Diese Funktion ist für die Verwendung auf Autoreninstanzen gedacht.

Der Gesamtablauf sieht wie folgt aus:

1. Der Benutzer authentifiziert sich bei AEM und fordert eine Seite mit Assets an.
1. Requested page contains an asset similar to `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`
1. Rewriter transforms the link to a CDN URL containing a JWS Signature:
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. Der Browser des Benutzers leitet die Asset-Anforderung an den CDN-Server weiter.
1. CDN sollte so konfiguriert werden, dass die Anforderung zusammen mit dem `cdn_sign`-Parameter an AEM weitergeleitet wird.
1. Ein Authentifizierungs-Handler validiert den `cdn_sign`-Parameter und gibt das Asset an CDN zurück. Von dort wird es an den Benutzer übermittelt.

Der Fluss zwischen dem Browser des Benutzers, dem CDN und AEM sieht wie folgt aus:

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Diese Funktion ist derzeit nur für AEM-Autoreninstanzen aktiviert.

**CDNConfigServiceImpl** Provides CDN configurations

The CDN rewriting feature can be enabled by providing **CDN distribution domain name** in the configuration for com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl.

Der Dienst enthält auch andere Konfigurationsoptionen wie das Aktivieren/Deaktivieren der CDN-Neuschreib-Funktion, Pfad-Präfixe für das Neuschreiben durch CDN, TTL-Werte und Protokolle (HTTP oder HTTPS).

**CDNRewriter** Ein Rewriter zum Umschreiben interner Bild-URLs in CDN-URLs

The **Tag Attributes** value in com.adobe.cq.cdn.rewriter.impl.CDNRewriter can be defined so that only selective image links are rewritten.
