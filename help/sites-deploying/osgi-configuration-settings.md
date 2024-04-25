---
title: OSGi-Konfigurationseinstellungen
description: In diesem Artikel werden die OSGi-Konfigurationseinstellungen beschrieben (aufgeführt nach Bundle), die für die Projektimplementierung relevant sind. Die Liste dient als Leitlinie und ist nicht vollständig.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
exl-id: 19eedcf2-140a-452d-aa8f-6fd7f219e5f8
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '3360'
ht-degree: 99%

---

# OSGi-Konfigurationseinstellungen{#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von AEM. Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi „*stellt die standardisierten Primitive bereit, mit denen Anwendungen aus kleinen, wiederverwendbaren und gemeinsamen Komponenten konstruiert werden können. Diese Komponenten können zu einer Anwendung zusammengestellt und bereitgestellt werden*“.

Diese Funktionalität ermöglicht eine einfache Verwaltung von Bundles, da diese einzeln beendet, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://docs.osgi.org/specification/)) ist in einem der Bundles enthalten. Bei der Arbeit mit AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Bundles. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Die folgenden OSGi-Konfigurationseinstellungen (aufgeführt nach Bundle) sind für die Projektimplementierung relevant. Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden nur zum besseren Verständnis von AEM erwähnt.

>[!CAUTION]
>
>Die Liste soll als Leitlinie dienen und ist nicht vollständig. Es werden nicht alle Bundles und für einige der Bundles auch nicht alle Parameter aufgelistet.
>
>Die erforderliche Konfiguration variiert von Projekt zu Projekt.
>
>In der Web-Konsole finden Sie verwendete Werte und detaillierte Informationen zu Parametern.

>[!NOTE]
>
>Das OSGi Configuration Diff-Tool, Teil der [AEM Tools](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17488.html), kann verwendet werden, um die standardmäßigen OSGi-Konfigurationen aufzulisten.

>[!NOTE]
>
>Für spezifische Funktionsbereiche in AEM sind möglicherweise weitere Bundles erforderlich. In solchen Fällen können Sie die Konfigurationsdetails der Seite entnehmen, die sich auf die entsprechende Funktion bezieht.

**AEM Replikations-Ereignis-Listener** Konfigurieren Sie:

* Die **Ausführungsmodi**, in denen Replikationsereignisse an Listener verteilt werden. Bei einer Definition als Authoring wird die Replikation z. B. vom System „initiiert“.

* Der Ausführungsmodus **Veröffentlichen** muss hinzugefügt werden, wenn der Projekt-Code Replikationsereignisse (Rückwärtsreplikation) in einer Veröffentlichungsumgebung verarbeitet. Dies ist beispielsweise der Fall, wenn der Dispatcher zum Leeren aus der Publishing-Umgebung verwendet wird oder wenn eine standardmäßige Replikation zu anderen Publishing-Instanzen erfolgt.

**AEM-Repository-Änderungs-Listener** Konfigurieren Sie:

* Die **Pfade**, Speicherorte, an denen auf Repository-Ereignisse, die für die Verteilung bereit sind, gelauscht wird.

**CRX Sling Client Repository** Konfigurieren Sie den Zugriff auf das zugrunde liegende Inhalts-Repository.

* Das **Administratorkennwort** sollte nach der Installation geändert werden, um die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz zu gewährleisten.
* Andere Änderungen sollten nicht erforderlich sein und müssen mit Vorsicht erfolgen, da sie den Zugriff auf das Repository beeinträchtigen können.

**Apache Felix OSGi Management Console:** Konfigurieren Sie:

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

**Apache Sling Customizable Request Data Logger** Konfigurieren Sie:

* **Name der Protokollfunktion** und **Protokollformat** für den Speicherort und das Format von Anforderungen und Zugriffsprotokollierung (Standard: `request.log`). Diese Protokolldatei ist sehr wichtig, wenn Sie die Leistung analysieren oder auf die Web-Kette bezogene Funktionen debuggen möchten. Sie ist gepaart mit dem [Apache Sling Request Logger](#apacheslingrequestlogger).

Siehe [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Eventing Thread Pool** Konfigurieren Sie:

* **Minimale Poolgröße** und **Maximale Poolgröße**, die Größe des Pools, der zum Speichern von Ereignis-Threads verwendet wird.

* **Warteschlangengröße**, die maximale Größe der Thread-Warteschlange, wenn der Pool erschöpft ist.
Der empfohlene Wert ist `-1`, da dadurch die Warteschlange auf unbegrenzt gesetzt wird. Wenn ein Limit festgelegt ist, kann es bei Überschreitung zu Verlusten kommen.

* Das Ändern dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Ereignissen verbessern, z. B. bei starker Nutzung von AEM DAM oder Workflow.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Diese Einstellungen können sich auf die Leistung Ihrer Instanz auswirken. Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling GET Servlet** Konfigurieren Sie einige Aspekte des Renderings:

* **Auto Index** zum Aktivieren/Deaktivieren der Verzeichnisausgabe beim Browsen.
* **Aktivieren** (oder Deaktivieren) von Standardwiedergaben, wie **HTML**, **Nur Text**, **JSON** oder **XML**.
Deaktivieren Sie JSON nicht.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling JavaScript Handler** Konfigurieren Sie Einstellungen für die Kompilierung von Java-Dateien als Skripte (Servlets).

Bestimmte Einstellungen können sich auf die Leistung auswirken. Deaktivieren Sie diese Einstellungen nach Möglichkeit, insbesondere für eine Produktionsinstanz.

* **Quell-VM** und **Ziel-VM** definieren die JDK-Version als die für Runtime JVM verwendete Version

* für Produktionsinstanzen:

   * Deaktivieren Sie **Generate Debug Info**.

**Apache Sling JCR Installer** Diese Parameter müssen wahrscheinlich nicht konfiguriert werden. Es ist jedoch nützlich, diese beim Entwickeln oder Debuggen zu kennen. Die Installationsordner können beispielsweise zum Ein- oder Auschecken oder zum Erstellen eines Pakets nützlich sein.

* **Name des Installationsordners regexp** und **Maximale Hierarchietiefe von Installationsordnern** – geben an, wo und bis zu welcher Tiefe die Repository-Ordner nach zu installierenden Ressourcen durchsucht werden. Wenn ein Platzhalter verwendet wird (wie in.&#42;/install), werden alle passenden Ordner durchsucht, z. B. hier `/libs/sling/install` und `/libs/cq/core/install`.

* **Search Path** listet die Pfade auf, in denen jcrinstall nach zu installierenden Ressourcen sucht, und eine Ziffer, die den Gewichtungsfaktor für den Pfad angibt.

**Apache Sling Job Event Handler** Konfigurieren Sie Parameter, die die Auftragsplanung verwalten:

* **Wiederholungsintervall**, **Maximale Wiederholungsversuche**, **Maximale parallele Aufträge**, **Wartezeit für die Bestätigung** und andere.

* Eine Änderung dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Aufträgen verbessern. z. B. starke Nutzung von AEM DAM und Workflows.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling JSP Script Handler** Konfigurieren Sie leistungsrelevante Einstellungen für den JSP-Skript-Handler. Um die Leistung zu verbessern, sollten Sie so viel wie möglich deaktivieren.

Insbesondere für Produktionsinstanzen:

* Deaktivieren Sie **Generate Debug Info**.
* Deaktivieren Sie **Generiertes Java™ beibehalten**
* Deaktivieren Sie **Mapped Content**.
* Deaktivieren Sie **Quellfragmente anzeigen**

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Logging Configuration** Konfigurieren Sie:

* **Log Level** und **Log File** definieren den Speicherort und die Protokollebene der zentralen Protokollierungskonfiguration (error.log). Die Ebene kann auf einen der Werte `DEBUG`, `INFO`, `WARN`, `ERROR` und `FATAL` eingestellt werden.

* **Anzahl der Protokolldateien** und **Schwellenwert für Protokolldateien**, um die Größe und Versionsrotation der Protokolldatei zu definieren.

* **Meldungsmuster** definiert das Format der Protokollmeldungen.

Siehe [AEM-Protokollierung](/help/sites-deploying/configure-logging.md#global-logging) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Logging Logger Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log Level**, **Log File** und **Message Format** definieren Details in den Protokolldateien und -meldungen.

* **Logger** gibt die Kategorie an, z. B. nur Protokollierungen für com.day.cq.

* Durch Verwendung von **Werkskonfigurationen** können beliebig viele zusätzliche Konfigurationen hinzugefügt werden, um die verschiedenen erforderlichen Protokollebenen und Kategorien zu berücksichtigen.
* Solche Konfigurationen sind während der Entwicklung hilfreich, beispielsweise, um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Meldungen über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Siehe [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Logging Writer Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log File** gibt an, dass eine Protokolldatei vorhanden ist.
* **Number of Log Files** gibt die Versionsrotation an.

* Der Writer kann von **Apache Sling Logging-Logger-Konfiguration** Konfigurationen verwendet werden.

* Solche Konfigurationen sind während der Entwicklung hilfreich, beispielsweise, um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Meldungen über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Siehe [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Main Servlet** Konfigurieren Sie:

* **Number of Calls per Request** und **Recursion Depth**, um das System vor unendlichen Rekursionen und übermäßigen Skript-Aufrufen zu schützen.

**Apache Sling MIME Type Service** Konfigurieren Sie:

* **MIME-Typen**, um die für Ihr Projekt erforderlichen Typen hinzuzufügen. Dadurch kann mit einer `GET`-Anfrage einer Datei die richtige Kopfzeile für den Inhaltstyp zum Verknüpfen von Dateityp und Applikation festgelegt werden.

**Apache Sling Referrer-Filter** Um bekannte Sicherheitsprobleme mit Cross-Site Request-Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, müssen Sie den Referrer-Filter konfigurieren.

Der Referrer-Filter-Service ist ein OSGi-Service, mit dem Sie Folgendes konfigurieren können:

* welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* Eine Zulassungsliste von Servern, die zusätzlich zum Serverhost zugelassen werden sollen.

Weitere Informationen finden Sie unter [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).

>[!NOTE]
>
>Für den Apache Sling Referrer-Filter muss ein Schnellkorrekturpaket installiert werden.

**Apache Sling Request Logger** Konfigurieren Sie:

* unterschiedliche Parameter, die festlegen, wie Anforderungen zugeordnet werden.
* **Anforderungsprotokoll aktivieren** zum Aktivieren oder Deaktivieren.

* **Zugangsprotokoll aktivieren** zum Aktivieren oder Deaktivieren.

Gepaart mit dem [Apache Sling Customizable Request Data Logger](#apacheslingcustomizablerequestdatalogger).

Siehe [AEM-Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Resource Resolver Factory** Konfigurieren Sie zentrale Aspekte der Sling-Ressourcenauflösung:

* **Ressourcen-Suchpfade**, fügen Sie alle projektspezifischen Pfade hinzu (aber entfernen Sie weder `/libs` noch `/apps`).

* **Virtuelle URLs** zum Definieren der Vanity-URL-Zuweisungen.

* **URL-Zuordnungen** zum Definieren der Aliasse. Zum Beispiel von `/content` auf `/`.

* **Mapping Location**, die Zuordnungskonfiguration, die in `/etc/map` externalisiert ist.

* Verwenden Sie die lokale Installation (z. B. `https://localhost:4502/system/console/jcrresolver`), um herauszufinden, welcher Ressourcenkonfliktlöser aktiv ist.

Siehe: [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Konfigurieren Sie diese Optionen im Repository.
>
>Andernfalls werden Änderungen an **URL-Zuordnungen**, die mit der Felix-Konsole vorgenommen wurden, möglicherweise beim nächsten Start von AEM überschrieben.

**Apache Sling Servlet/Script Resolver and Error Handler** Das Sling-Servlet und der Skript-Resolver haben mehrere Aufgaben:

1. Sie werden als `ServletResolver` verwendet, die das Servlet oder Skript zum Abwickeln der Anforderung auswählen.

1. Sie dienen als `SlingScriptResolver`.

1. Sie sind für die Fehlerbehebung zuständig, indem sie die `ErrorHandler`-Schnittstelle implementieren und dabei denselben Algorithmus für Servlets und Skripts auswählen, der auch für Servlets und Skripts für die Anforderungsabwicklung verwendet wird.

Es können verschiedene Parameter festgelegt werden, darunter:

* **Ausführungspfade** – Listet die Pfade für die Suche nach ausführbaren Skripten auf. Durch die Konfiguration bestimmter Pfade können Sie einschränken, welche Skripte ausgeführt werden können. Wenn kein Pfad konfiguriert ist, wird der Standard verwendet (`/` = Stammpfad), sodass alle Skripte ausgeführt werden können.
Falls ein konfigurierter Pfadwert mit einem Schrägstrich endet, wird die gesamte Unterstruktur durchsucht. Ohne einen solchen Schrägstrich wird das Skript nur bei einer exakten Übereinstimmung ausgeführt.

* **Skript-Benutzer**: Diese optionale Eigenschaft kann das Repository-Benutzerkonto angeben, das zum Lesen der Skripte verwendet wird. Wenn kein Konto angegeben wird, wird standardmäßig `admin` als Benutzer verwendet.

* **Standarderweiterungen** – Die Liste der Erweiterungen, für die das Standardverhalten verwendet wird. Das letzte Pfadsegment des Ressourcentyps kann als Skriptname verwendet werden.

**Apache HTTP-Komponenten-Proxy-Konfiguration** – Die Proxy-Konfiguration für den gesamten Code, der den Apache HTTP-Client verwendet, wenn ein HTTP durchgeführt wird. Zum Beispiel bei der Replikation.

Ändern Sie beim Erstellen einer Konfiguration nicht die Werkskonfiguration. Erstellen Sie stattdessen eine Werkskonfiguration für diese Komponente mit dem Konfigurations-Manager, der hier verfügbar ist: **https://localhost:4502/system/console/configMgr/**. Die Proxy-Konfiguration ist in **org.apache.http.proxyconfigurator** verfügbar.

>[!NOTE]
>
>In AEM 6.0 und früheren Versionen wurde der Proxy im Day Commons HTTP Client konfiguriert. Ab AEM 6.1 und späteren Versionen wurde die Proxy-Konfiguration in die „Apache HTTP-Komponenten-Proxy-Konfiguration“ anstelle der „Day Commons HTTP Client“-Konfiguration verschoben.

**Day CQ Antispam** Konfigurieren Sie den verwendeten Anti-Spam-Dienst (Akismet). Für diese Funktion müssen Sie Folgendes registrieren:

* **Provider**
* **API-Schlüssel**
* **Registrierte URL**

**Adobe Granite HTML-Bibliotheksmanager** Konfigurieren Sie diesen, um die Handhabung von Client-Bibliotheken (css oder js) zu kontrollieren, einschließlich, wie zum Beispiel die zugrunde liegende Struktur gesehen wird.

* Für Produktionsinstanzen:

   * Aktivieren Sie **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * Aktivieren Sie **gzip** (damit Dateien ins gzip-Format komprimiert und mit einer Anfrage aufgerufen werden können).
   * Deaktivieren Sie **Debuggen**.
   * Deaktivieren Sie **Zeitplanung**.

* Für die JS-Entwicklung (insbesondere beim Firebugging/Debugging):

   * Deaktivieren Sie **Minimieren**
   * Aktivieren Sie **Debugging**, um die Dateien für die Fehlersuche und die Verwendung mit Fire Bug zu trennen.
   * Aktivieren Sie **Zeitplanung**, wenn Sie an der Zeitplanung interessiert sind.
   * Aktivieren Sie die **Debugging**-Konsole, um die Protokollmeldungen der JS-Konsole anzuzeigen.

>[!CAUTION]
>
>Wenn Sie die Einstellung für **Minimieren** oder **Gzip** ändern, löschen Sie die Inhalte des Clientlibs-Caches. Mehr Details finden Sie im [Knowledgebase-Artikel](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html).

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ HTTP Header Authentication Handler** Systemweite Einstellungen für die grundlegende Authentifizierungsmethode der HTTP-Anfrage.

Wenn Sie [geschlossene Benutzergruppen](/help/sites-administering/cug.md) verwenden, können Sie unter anderem Folgendes konfigurieren:

* **HTTP-Bereich**
* Die **Standard-Anmeldeseite**

**Day CQ Link Checker Service** Überprüfen und konfigurieren Sie bei Bedarf Folgendes:

* **Scheduler Period**: definiert das Intervall, in dem externe Links automatisch überprüft werden.

* Überprüfen Sie das **Intervall der Fehlertoleranz für ungültige Links** für den Zeitraum, nach dem ein erfolgloser externer Link als ungültig betrachtet wird.
* **Muster für Link-Check-Überschreibungen**, um alle Pfade zu definieren, die von der Link-Überprüfung ausgeschlossen werden sollen.

**Day CQ Link Checker Task** Konfigurieren Sie die Einstellungen für eine Aufgabe mit einem einzelnen Link-Checker (eine Aufgabe, die einen externen Link überprüft):

* Überprüfen Sie die unter **Good Link Test Interval** und **Bad Link Test Interval** festgelegten Intervalle.

* Die diversen Parameter, die sich auf Proxys für den Internetzugriff und NTLM beziehen und beim Überprüfen eines Links für den externen Zugriff benötigt werden.

**Day CQ Mail Service** Konfigurieren Sie den Host-Namen und die Zugriffsdetails für den E-Mail-Server. Siehe Abschnitt „Konfigurieren des E-Mail-Dienstes“.

**Day CQ MCM Newsletter** Konfigurieren Sie die verschiedenen Einstellungen, die für den Newsletter verwendet werden.

**Day CQ Root Mapping** Konfigurieren Sie:

* **Zielpfad**, um festzulegen, wohin eine an „`/`“ gerichtete Anfrage umgeleitet wird.

In AEM sind zwei Benutzeroberflächen verfügbar:

* Die Touch-optimierte Benutzeroberfläche ist die standardmäßige Benutzeroberfläche von AEM
* und die veraltete klassische Benutzeroberfläche ist weiterhin voll funktionsfähig.

Mit AEM Root Mapping können Sie die Benutzeroberfläche konfigurieren, die Sie als Standard für Ihre Instanz verwenden möchten:

* Wenn Sie die Touch-optimierte Benutzeroberfläche als Standard-Benutzeroberfläche verwenden möchten, muss der **Zielpfad** auf Folgendes verweisen:

  ```shell
     /projects.html
  ```

* Wenn Sie die klassische Benutzeroberfläche als Standard-Benutzeroberfläche verwenden möchten, muss der **Zielpfad** auf Folgendes verweisen:

  ```shell
     /welcome.html
  ```

>[!NOTE]
>
>Nach einer Standardinstallation wird die Touch-optimierte Benutzeroberfläche zur Standardbenutzeroberfläche.

**Adobe Granite-SSO-Authentifizierungs-Handler** – Konfigurieren von SSO-Details (Single Sign-On). Diese Details werden oft in Authoring-Setups für Unternehmen benötigt, oft mit LDAP.

Verschiedene Eigenschaften können konfiguriert werden: 

* **Pfad**
Der Pfad, für den dieser Authentifizierungs-Handler aktiv ist. Wenn dieser Parameter nicht angegeben wird, ist der Authentifizierungs-Handler deaktiviert. Beispielsweise wird beim Pfad / der Authentifizierungs-Handler für das gesamte Repository verwendet.

* **Service Ranking** Der Rangfolge-Wert für den OSGi-Framework-Dienst gibt die Reihenfolge an, in der dieser Dienst aufgerufen wird. Dieser Wert ist ein `int`-Wert, wobei höhere Werte eine höhere Priorität bezeichnen.
Der Standardwert ist `0`.

* **Kopfzeilen-Namen**
Die Namen von Kopfzeilen, die möglicherweise eine Benutzer-ID enthalten.

* **Cookie-Namen**
Die Namen von Cookies, die möglicherweise eine Benutzer-ID enthalten.

* **Parameter-Namen**
Die Namen von Anfrageparametern, die möglicherweise eine Benutzer-ID angeben.

* **User Map** Für bestimmte Benutzer kann der aus der HTTP-Anforderung extrahierte Benutzername im Anmeldedaten-Objekt durch einen anderen Namen ersetzt werden. Die Zuordnung ist hier definiert. Falls der Benutzername `admin` auf beiden Seiten der Zuordnung angezeigt wird, wird die Zuordnung ignoriert. Das Zeichen „=“ muss mit einem vorangestellten „\“ versehen werden.

* **Format** Gibt das Format an, in dem die Benutzer-ID angegeben ist. Verwenden Sie:

   * `Basic`, falls die Benutzer-ID im HTTP-Standard-Authentifizierungsformat kodiert ist
   * `AsIs`, falls die Benutzer-ID im Nur-Text-Format bereitgestellt wird, oder jeder für reguläre Ausdrücke gültige Wert unverändert bzw. jeder reguläre Ausdruck verwendet werden soll

**Day CQ WCM Debug Filter** Dies ist beim Entwickeln hilfreich, da Suffixe wie ?debug=layout beim Zugriff auf eine Seite verwendet werden können. Zum Beispiel liefert https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout Layout-Informationen, die für Entwicklungspersonen von Interesse sein können.

* Um Leistung und Sicherheit zu gewährleisten, deaktivieren Sie diese Option auf Produktionsinstanzen.

**Day CQ WCM Filter** Konfigurieren Sie:

* **WCM-Modus**, um den Standardmodus festzulegen.
* Bei einer Authoring-Instanz kann dieser Modus `edit`, `disable,preview` oder `analytics` sein.
Auf die anderen Modi kann über den Sidekick zugegriffen werden, oder es kann das Suffix `?wcmmode=disabled` zum Emulieren einer Produktionsumgebung verwendet werden.

* Bei einer Publishing-Instanz muss dieser Modus auf `disabled` gesetzt werden, um sicherzustellen, dass kein anderer Modus zugänglich ist.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ WCM Link Checker Configurator** Konfigurieren Sie:

* **Liste der Neuschreibungs-Konfigurationen**, um eine Liste der Speicherorte für inhaltsbasierte Link-Prüfer-Konfigurationen anzugeben. Die Konfigurationen können auf dem Ausführungsmodus basieren. Diese Tatsache ist wichtig, um zwischen Authoring- und Publishing-Umgebungen zu unterscheiden, da die Einstellungen des Link-Prüfers unterschiedlich sein können.

**Day CQ WCM Page Manager Factory** Konfigurieren Sie:

* **Page Subtree Activation Check** für einen Benutzer (ohne Replikationsberechtigungen), um Seiten zu löschen oder zu verschieben (auch wenn die Seiten nicht aktiviert sind).

**Day CQ WCM Page Processor** Konfigurieren Sie:

* **Paths**, eine Liste der Speicherorte, die das System auf Seitenänderungen überwacht, bevor ein `jcr:Event` ausgelöst wird.

**Adobe Page Impressions Tracker** Konfigurieren Sie für eine Authoring-Instanz Folgendes:

* **sling.auth.requirements**: Legen Sie für diese Eigenschaft den Wert auf `-/libs/wcm/stats/tracker` fest.

>[!CAUTION]
>
>Diese Konfiguration ermöglicht anonyme Anfragen an den Tracking-Dienst.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Page Statistics** Konfigurieren Sie für eine Veröffentlichungsinstanz Folgendes:

* **URL zum Senden von Daten**, um die URL zu konfigurieren, die zum Nachverfolgen von Seitenstatistiken verwendet wird (ist wichtig, wenn eine Nachverfolgungsanfrage über den Dispatcher läuft). Der Standardwert ist beispielsweise `https://localhost:4502/libs/wcm/stats/tracker`.

* **Tracking script enabled**: aktiviert (`true`) oder deaktiviert (`false`) den Einschluss der Nachverfolgungsskripts auf den Seiten. Der Standardwert ist `false`.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Version Manager** Steuern Sie, ob und wie Versionen in Ihrem System verwaltet werden:

* **Create Version on Activation** ist bei der Standardinstallation aktiviert.
* **Enable Purging**

* **Bereinigungspfade**: die von einem Suchvorgang durchsuchten Pfade.
* **Implicit Versioning Paths**: die Pfade, bei denen die implizite Versionierung aktiv ist.

* **Max Version Age**: das maximale Alter (in Tagen) einer Version.

* **Max Number Versions**: die maximale Anzahl der beizubehaltender Versionen.

Weitere Informationen finden Sie unter [Löschen von Versionen](/help/sites-deploying/version-purging.md).

**Day CQ Workflow Email Notification Service** Konfigurieren Sie die E-Mail-Einstellungen für Benachrichtigungen, die von einem Workflow gesendet werden.

**CQ Rewriter HTML Parser Factory**

Steuert den HTML-Parser für den CQ-Rewriter.

* **Zusätzliche Tags zur Verarbeitung** – Sie können HTML-Tags hinzufügen oder entfernen, die vom Parser verarbeitet werden sollen. Standardmäßig werden die folgenden Tags verarbeitet: A, IMG, AREA, FORM, BASE, LINK, SCRIPT, BODY, HEAD.
* **Groß-/Kleinschreibung beibehalten** – Standardmäßig wandelt der HTML-Parser Attribute in gemischter Groß-/Kleinschreibung (z. B. `eBay`) in Kleinschreibung um (z. B. `ebay`). Sie können diese Einstellung deaktivieren, um die Attribute der Groß-/Kleinschreibung beizubehalten. Diese Einstellung ist nützlich bei der Verwendung von Frontend-Frameworks wie Angular 2.

**Day Commons JDBC Connections Pool** Konfigurieren Sie den Zugriff auf eine externe Datenbank, die als Quelle für Inhalte verwendet wird.

Dies ist eine Werkskonfiguration, sodass mehrere Instanzen konfiguriert werden können.

**CDN Rewriter** Die Kommunikation zwischen AEM und einem CDN muss sichergestellt sein, damit Assets/Binärdateien sicher an Endbenutzende übermittelt werden. Dieser Prozess umfasst die beiden folgenden Aufgaben:

* Zugriff auf die Ressource von AEM über das CDN beim ersten Mal (oder nachdem sie im Cache abgelaufen ist).
* Sicherer Zugriff auf die im CDN zwischengespeicherte Ressource. Nachdem die Ressource im CDN zwischengespeichert wurde, wird die Anfrage nicht an AEM gesendet und alle Benutzenden, die Zugriff auf diese Ressource haben, sollten vom CDN aus bedient werden.

AEM bietet einen Rewriter zum Neuschreiben interner Asset-URLs in externe CDN-URLs. Er schreibt die an das CDN weiterzuleitenden Links um und fügt eine JWS-Signatur und eine Ablaufzeit hinzu, damit der Zugriff auf das Asset sicher ist. Diese Funktion wird in Authoring-Instanzen verwendet.

Der Gesamtablauf ist wie folgt:

1. Benutzende authentifizieren sich bei AEM und fordern eine Seite mit Assets an.
1. Die angefragte Seite enthält ein Asset, das dem `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png` ähnelt.
1. Rewriter wandelt den Link in eine CDN-URL um, die eine JWS-Signatur enthält:
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. Der Browser des Benutzers leitet die Asset-Anforderung an den CDN-Server weiter.
1. CDN sollte so konfiguriert werden, dass die Anforderung zusammen mit dem `cdn_sign`-Parameter an AEM weitergeleitet wird.
1. Ein Authentifizierungs-Handler validiert den `cdn_sign`-Parameter und gibt das Asset an CDN zurück. Von dort wird es an den Benutzer übermittelt.

Der Fluss zwischen dem Browser des Benutzers, dem CDN und AEM sieht wie folgt aus:

![chlimage_1-8](assets/chlimage_1-8.png)

>[!NOTE]
>
>Diese Funktion ist derzeit nur für die AEM-Authoring-Instanzen aktiviert.

**CDNConfigServiceImpl** Bietet CDN-Konfigurationen

Sie können die CDN-Rewriter-Funktion aktivieren, indem Sie den **Domain-Namen der CDN-Verteilung** in der Konfiguration für com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl angeben.

Der Service enthält auch andere Konfigurationsoptionen wie das Aktivieren/Deaktivieren der CDN-Neuschreib-Funktion, Pfad-Präfixe für das Neuschreiben durch CDN, TTL-Werte und Protokolle (HTTP oder HTTPS).

**CDNRewriter** Ein Rewriter für das Neuschreiben interner Image-URLs als CDN-URLs

Der Wert **Tag Attributes** in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kann so definiert werden, dass nur bestimmte Image-Links neu geschrieben werden.
