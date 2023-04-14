---
title: OSGi-Konfigurationseinstellungen
seo-title: OSGi Configuration Settings
description: In diesem Artikel werden die OSGi-Konfigurationseinstellungen (aufgeführt gemäß Bundle) beschrieben, die für die Projektimplementierung relevant sind. Die Liste dient als Leitlinie und ist nicht vollständig.
seo-description: This article details the OSGi configuration settings (listed according to bundle) that are relevant to project implementation. The list acts as a guideline and it is not exhaustive.
uuid: 192d3287-ec99-403b-bab0-45721e4e3abd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ed3a858c-7a43-4515-a2ff-43ca465c7d7d
docset: aem65
feature: Configuring
exl-id: 19eedcf2-140a-452d-aa8f-6fd7f219e5f8
source-git-commit: af60428255fb883265ade7b2d9f363aacb84b9ad
workflow-type: tm+mt
source-wordcount: '3431'
ht-degree: 47%

---

# OSGi-Konfigurationseinstellungen{#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von AEM. Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi &quot;*stellt die standardisierten Grundbausteine bereit, mit denen Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten erstellt werden können. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden*&quot;.

Diese Funktion ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage)) ist in einem der Bundles enthalten. Beim Arbeiten mit AEM gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Bundles. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für weitere Details und empfohlene Vorgehensweisen.

Die folgenden OSGi-Konfigurationseinstellungen (aufgeführt gemäß Bundle) sind für die Projektimplementierung relevant. Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden nur zum besseren Verständnis von AEM erwähnt.

>[!CAUTION]
>
>Die Liste soll als Leitlinie dienen und ist nicht vollständig. Es werden nicht alle Bundles aufgelistet und auch nicht alle Parameter für einige der Bundles, die vorhanden sind.
>
>Die erforderliche Konfiguration variiert von Projekt zu Projekt.
>
>In der Webkonsole finden Sie verwendete Werte und detaillierte Informationen zu Parametern.

>[!NOTE]
>
>Das OSGi Configuration Diff-Tool, Teil der [AEM Tools](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17488.html?lang=en), kann verwendet werden, um die standardmäßigen OSGi-Konfigurationen aufzulisten.

>[!NOTE]
>
>Für spezifische Funktionsbereiche in AEM sind möglicherweise weitere Bundles erforderlich. In solchen Fällen können Sie die Konfigurationsdetails der Seite entnehmen, die sich auf die entsprechende Funktion bezieht.

**AEM Replikations-Ereignis-Listener** Konfigurieren Sie:

* Die **Ausführungsmodi**, in dem Replikationsereignisse an Listener verteilt werden. Wenn beispielsweise als Autor definiert, wird die Replikation vom System &quot;initiiert&quot;.

* Ausführungsmodus hinzufügen **publish** wenn der Projektcode Replikationsereignisse (Rückwärtsreplikation) in einer Veröffentlichungsumgebung verarbeitet. Dies ist beispielsweise der Fall, wenn der Dispatcher zum Leeren aus der Veröffentlichungsumgebung verwendet wird oder wenn eine standardmäßige Replikation auf andere Veröffentlichungsinstanzen erfolgt.

**AEM-Repository-Änderungs-Listener** Konfigurieren Sie:

* Die **Pfade**, Speicherorte, an denen auf Repository-Ereignisse, die für die Verteilung bereit sind, gelauscht wird.

**CRX Sling Client Repository** Konfigurieren Sie den Zugriff auf das zugrunde liegende Inhalts-Repository.

* Das **Administratorkennwort** sollte nach der Installation geändert werden, um die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz zu gewährleisten.
* Andere Änderungen sollten nicht erforderlich sein und müssen mit Vorsicht erfolgen, da sie den Zugriff auf das Repository beeinträchtigen können.

**Apache Felix OSGi Management Console:** Konfigurieren Sie:

* **Plugins**, die Hauptnavigationselemente (Konsolen-Plug-ins), die im **Apache Felix Web Management Console** als Menüelemente der obersten Ebene. Deaktivieren Sie alle nicht benötigten Elemente, da sie sonst Platz und Ressourcen verbrauchen.

>[!CAUTION]
>
>Konfigurieren Sie Folgendes:
>
>**Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.
>Das Kennwort muss nach der ersten Installation geändert werden, damit die [Sicherheit](/help/sites-administering/security-checklist.md) Ihrer Instanz gewährleistet ist.

>[!NOTE]
>
>Nehmen Sie diese Konfiguration in der Felix Console vor, die zum Starten erforderlich ist – bevor das Repository verfügbar ist.

**Apache Sling Customizable Request Data Logger** Konfigurieren Sie:

* **Name der Protokollfunktion** und **Protokollformat** für den Speicherort und das Format von Anforderungen und Zugriffsprotokollierung (Standard: `request.log`). Diese Protokolldatei ist sehr wichtig, wenn Sie die Leistung analysieren oder auf die Web-Kette bezogene Funktionen debuggen möchten. Sie wird mit der [Apache Sling Request Logger](#apacheslingrequestlogger).

Siehe [AEM Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Eventing Thread Pool** Konfigurieren Sie:

* **Minimale Poolgröße** und **Maximale Poolgröße**, die Größe des Pools, der zum Speichern von Ereignis-Threads verwendet wird.

* **Warteschlangengröße**, die maximale Größe der Thread-Warteschlange, wenn der Pool erschöpft ist.
Der empfohlene Wert lautet `-1` weil sie die Warteschlange auf unbegrenzt festlegt. Wenn ein Limit festgelegt ist, kann es bei Überschreitung zu Verlusten kommen.

* Eine Änderung dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Ereignissen verbessern. Beispielsweise starke AEM DAM- oder Workflow-Nutzung.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Diese Einstellungen können sich auf die Leistung Ihrer Instanz auswirken. Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling GET Servlet** Konfigurieren Sie einige Aspekte des Renderings:

* **Auto Index** zum Aktivieren/Deaktivieren der Verzeichnisausgabe beim Browsen.
* **Aktivieren** (oder deaktivieren) Standardausgabeformate wie **HTML**, **Nur Text**, **JSON** oder **XML**.
Deaktivieren Sie JSON nicht.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling JavaScript Handler** Konfigurieren Sie Einstellungen für die Kompilierung von Java-Dateien als Skripten (Servlets).

Bestimmte Einstellungen können sich auf die Leistung auswirken. Deaktivieren Sie diese Einstellungen nach Möglichkeit, insbesondere für eine Produktionsinstanz.

* **Quell-VM** und **Target VM**, definieren Sie die JDK-Version, die als LaufzeitjVM verwendet wird.

* für Produktionsinstanzen:

   * Deaktivieren Sie **Generate Debug Info**.

**Apache Sling JCR Installer** Diese Parameter müssen wahrscheinlich nicht konfiguriert werden. Es ist jedoch nützlich, diese beim Entwickeln oder Debuggen zu kennen. Beispielsweise können die Installationsordner zum Ein- oder Auschecken oder zum Erstellen eines Pakets nützlich sein.

* **Name des Installationsordners regexp** und **Maximale Hierarchietiefe von Installationsordnern** - Geben Sie an, wo und in welcher Tiefe Repository-Ordner nach Ressourcen gesucht werden, die installiert werden sollen. Wenn ein Platzhalter verwendet wird (wie in .&#42;/install) alle passenden Übereinstimmungen durchsucht werden, z. B. `/libs/sling/install` und `/libs/cq/core/install`.

* **Search Path** listet die Pfade auf, in denen jcrinstall nach zu installierenden Ressourcen sucht, und eine Ziffer, die den Gewichtungsfaktor für den Pfad angibt.

**Apache Sling Job Event Handler** Konfigurieren Sie Parameter, die die Auftragsplanung verwalten:

* **Wiederholungsintervall**, **Maximale Wiederholungen**, **Maximale Anzahl paralleler Aufträge**, **Wartezeit für Bestätigung**, unter anderem.

* Eine Änderung dieser Einstellungen kann die Leistung in Szenarien mit einer hohen Anzahl von Aufträgen verbessern. z. B. starke Nutzung von AEM DAM und Workflows.
* Für Ihr Szenario spezifische Werte sollten mithilfe von Tests festgelegt werden.
* Ändern Sie sie daher nicht ohne Grund und nur nach reiflicher Überlegung.

**Apache Sling JSP Script Handler** Konfigurieren Sie leistungsrelevante Einstellungen für den JSP-Skript-Handler. Um die Leistung zu verbessern, sollten Sie so weit wie möglich deaktivieren.

Insbesondere für Produktionsinstanzen:

* Deaktivieren Sie **Generate Debug Info**.
* disable **Generiertes Java™ beibehalten**
* Deaktivieren Sie **Mapped Content**.
* disable **Anzeigen von Quellfragmenten**

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Apache Sling Logging Configuration** Konfigurieren Sie:

* **Log Level** und **Log File** definieren den Speicherort und die Protokollebene der zentralen Protokollierungskonfiguration (error.log). Die Ebene kann auf einen von `DEBUG`, `INFO`, `WARN`, `ERROR`und `FATAL`.

* **Anzahl Protokolldateien** und **Schwellenwert für Protokolldateien** , um die Größe und Versionsrotation der Protokolldatei zu definieren.

* **Nachrichtenmuster** definiert das Format der Protokollmeldungen.

Siehe [AEM Protokollierung](/help/sites-deploying/configure-logging.md#global-logging) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Logging Logger Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log Level**, **Log File** und **Message Format** definieren Details in den Protokolldateien und -meldungen.

* **Logger** gibt die Kategorie an, z. B. nur Protokollierungen für com.day.cq.

* Durch Verwendung von **Factory-Konfigurationen** können beliebig viele zusätzliche Konfigurationen hinzugefügt werden, um die verschiedenen erforderlichen Protokollebenen und Kategorien zu berücksichtigen.
* Solche Konfigurationen sind während der Entwicklung hilfreich. Beispielsweise um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Nachrichten über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Siehe [AEM Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Logging Writer Configuration (Factory Configuration)** Konfigurieren Sie:

* **Log File** gibt an, dass eine Protokolldatei vorhanden ist.
* **Number of Log Files** gibt die Versionsrotation an.

* Der Autor kann von einem **Apache Sling Logging Logger-Konfiguration** Konfiguration.

* Solche Konfigurationen sind während der Entwicklung hilfreich. Beispielsweise um TRACE-Meldungen für einen bestimmten Dienst in einer bestimmten Protokolldatei zu protokollieren.
* Solche Konfigurationen sind in einer Produktionsumgebung hilfreich. Sie können beispielsweise Nachrichten über einen bestimmten Dienst in einer einzelnen Protokolldatei protokollieren, um die Überwachung zu erleichtern.

Siehe [AEM Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Main Servlet** Konfigurieren Sie:

* **Number of Calls per Request** und **Recursion Depth**, um das System vor unendlichen Rekursionen und übermäßigen Skript-Aufrufen zu schützen.

**Apache Sling MIME Type Service** Konfigurieren Sie:

* **MIME-Typen** , um dem System Typen hinzuzufügen, die für Ihr Projekt erforderlich sind. Dies ermöglicht eine `GET` -Anfrage für eine Datei, um die richtige Kopfzeile für den Inhaltstyp für die Verknüpfung von Dateityp und Anwendung festzulegen.

**Apache Sling Referrer Filter** Um bekannte Sicherheitsprobleme mit Cross-Site Request Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, müssen Sie den Filter Referrer konfigurieren.

Der Referrer-Filterdienst ist ein OSGi-Dienst, mit dem Sie Folgendes konfigurieren können:

* welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* Eine Zulassungsliste von Servern, die zusätzlich zum Serverhost zugelassen werden sollen.

Weitere Informationen finden Sie unter [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).

>[!NOTE]
>
>Der Apache Sling Referrer-Filter hängt von der Installation eines Schnellkorrekturpakets ab.

**Apache Sling Request Logger** Konfigurieren Sie:

* unterschiedliche Parameter, die festlegen, wie Anforderungen zugeordnet werden.
* **Anfrageprotokoll aktivieren**, um zu aktivieren oder zu deaktivieren.

* **Zugriffsprotokoll aktivieren**, um zu aktivieren oder zu deaktivieren.

Gemeinsam mit der [Apache Sling Customizable Request Data Logger](#apacheslingcustomizablerequestdatalogger).

Siehe [AEM Protokollierung](/help/sites-deploying/configure-logging.md) und [Sling-Protokollierung](https://sling.apache.org/documentation/development/logging.html).

**Apache Sling Resource Resolver Factory** Konfigurieren Sie zentrale Aspekte der Sling-Ressourcenauflösung:

* **Ressourcen-Suchpfade**, fügen Sie projektspezifische Pfade hinzu (entfernen Sie sie jedoch nicht `/libs` oder `/apps`).

* **Virtual URLs** zum Definieren der Vanity-URL-Zuweisungen.

* **URL-Zuordnungen** , um Aliase zu definieren. Beispiel: von `/content` nach `/`.

* **Mapping Location**, die Zuordnungskonfiguration, die in `/etc/map` externalisiert ist.

* Verwenden Sie die lokale Installation (z. B. `https://localhost:4502/system/console/jcrresolver`), um herauszufinden, welcher Ressourcenkonfliktlöser aktiv ist.

Siehe: [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Konfigurieren Sie diese Optionen im Repository.
>
>Andernfalls werden Änderungen an **URL-Zuordnungen** Die Verwendung der Felix-Konsole kann beim nächsten Start durch AEM überschrieben werden.

**Apache Sling Servlet/Script Resolver and Error Handler** Das Sling-Servlet und der Skript-Resolver haben mehrere Aufgaben:

1. Sie werden als `ServletResolver` verwendet, die das Servlet oder Skript zum Abwickeln der Anforderung auswählen.

1. Sie dienen als `SlingScriptResolver`.

1. Sie sind für die Fehlerbehebung zuständig, indem sie die `ErrorHandler`-Schnittstelle implementieren und dabei denselben Algorithmus für Servlets und Skripts auswählen, der auch für Servlets und Skripts für die Anforderungsabwicklung verwendet wird.

Es können verschiedene Parameter festgelegt werden, darunter:

* **Ausführungspfade** - Listet die Pfade auf, nach ausführbaren Skripten zu suchen. Durch die Konfiguration bestimmter Pfade können Sie einschränken, welche Skripte ausgeführt werden können. Wenn kein Pfad konfiguriert ist, wird der Standard verwendet ( `/` = root), sodass alle Skripte ausgeführt werden können.
Wenn ein konfigurierter Pfadwert mit einem Schrägstrich endet, wird die gesamte Unterstruktur durchsucht. Ohne einen solchen Schrägstrich wird das Skript nur ausgeführt, wenn es eine exakte Übereinstimmung ist.

* **Skript-Benutzer** - Diese optionale Eigenschaft kann das Repository-Benutzerkonto angeben, das zum Lesen der Skripte verwendet wird. Wenn kein Konto angegeben ist, wird die `admin` Der Benutzer wird standardmäßig verwendet.

* **Standarderweiterungen** - Die Liste der Erweiterungen, für die das Standardverhalten verwendet wird. Das letzte Pfadsegment des Ressourcentyps kann als Skriptname verwendet werden.

**Apache HTTP Components Proxy Configuration** - Die Proxy-Konfiguration für den gesamten Code, der den Apache HTTP-Client verwendet, der beim Erstellen eines HTTP verwendet wird. Beispielsweise bei der Replikation.

Ändern Sie beim Erstellen einer Konfiguration nicht die Werkskonfiguration. Erstellen Sie stattdessen eine Werkskonfiguration für diese Komponente mit dem Konfigurationsmanager, der hier verfügbar ist: **https://localhost:4502/system/console/configMgr/**. Die Proxy-Konfiguration ist in **org.apache.http.proxyconfigurator** verfügbar.

>[!NOTE]
>
>In AEM 6.0 und früheren Versionen wurde der Proxy im Day Commons HTTP Client konfiguriert. Ab AEM Version 6.1 und höher wurde die Proxy-Konfiguration in die &quot;Apache HTTP Components Proxy Configuration&quot;statt in die &quot;Day Commons HTTP Client&quot;-Konfiguration verschoben.

**Day CQ Antispam** Konfigurieren Sie den verwendeten Anti-Spam-Dienst (Akismet). Für diese Funktion müssen Sie Folgendes registrieren:

* **Provider**
* **API-Schlüssel**
* **Registrierte URL**

**Adobe Granite HTML Library Manager** Konfigurieren Sie diese Konfiguration, um die Verarbeitung von Client-Bibliotheken (css oder js) zu steuern, einschließlich beispielsweise der Anzeige der zugrunde liegenden Struktur.

* Für Produktionsinstanzen:

   * enable **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * enable **Gzip** (damit Dateien komprimiert und mit einer Anfrage aufgerufen werden können).
   * disable **Debuggen**
   * disable **Zeit**

* Für die JS-Entwicklung (insbesondere beim Firebugging/Debugging):

   * disable **Minimieren**
   * enable **Debuggen** , um die Dateien für das Debugging zu trennen und mit dem Fehler auszulösen.
   * enable **Zeit** wenn Interesse an der Zeitplanung.
   * enable **Debuggen** -Konsole, um die Protokollmeldungen der JS-Konsole anzuzeigen.

>[!CAUTION]
>
>Wenn Sie die Einstellung für **Minimieren** oder **Gzip**, löschen Sie den Inhalt des Zwischenspeichers clientlibs . Siehe [Knowledge Base-Artikel](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=en) für Details.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ HTTP Header Authentication Handler** Systemweite Einstellungen für die grundlegende Authentifizierungsmethode der HTTP-Anfrage.

Bei Verwendung von [geschlossene Benutzergruppen](/help/sites-administering/cug.md)können Sie unter anderem Folgendes konfigurieren:

* **HTTP-Bereich**
* Die **Standard-Anmeldeseite**

**Day CQ Link Checker Service** Überprüfen und konfigurieren Sie bei Bedarf Folgendes:

* **Scheduler Period**: definiert das Intervall, in dem externe Links automatisch überprüft werden.

* Überprüfen **Schlechtes Linktoleranzintervall** für den Zeitraum, nach dem ein nicht erfolgreicher externer Link als fehlerhaft betrachtet wird.
* **Link Check Override Patterns**, um alle Pfade zu definieren, die von der Linküberprüfung ausgeschlossen werden sollen.

**Day CQ Link Checker Task** Konfigurieren Sie die Einstellungen für eine Aufgabe mit einem einzelnen Link-Checker (eine Aufgabe, die einen externen Link überprüft):

* Überprüfen Sie die unter **Good Link Test Interval** und **Bad Link Test Interval** festgelegten Intervalle.

* Die diversen Parameter, die sich auf Proxys für den Internetzugriff und NTLM beziehen und beim Überprüfen eines Links für den externen Zugriff benötigt werden.

**Day CQ Mail Service** Konfigurieren Sie den Host-Namen und die Zugriffsdetails für den E-Mail-Server. Siehe Abschnitt Konfigurieren des E-Mail-Dienstes .

**Day CQ MCM Newsletter** Konfigurieren Sie die verschiedenen Einstellungen, die für den Newsletter verwendet werden.

**Day CQ Root Mapping** Konfigurieren Sie:

* **Zielpfad** , um festzulegen, wo eine Anforderung an &quot; `/`&quot; wird zu umgeleitet.

In AEM sind zwei Benutzeroberflächen verfügbar:

* Die Touch-optimierte Benutzeroberfläche ist die standardmäßige Benutzeroberfläche von AEM
* und die veraltete klassische Benutzeroberfläche ist weiterhin voll funktionsfähig.

Mit AEM Root Mapping können Sie die Benutzeroberfläche konfigurieren, die Sie als Standard für Ihre Instanz verwenden möchten:

* Damit die Touch-optimierte Benutzeroberfläche als Standardbenutzeroberfläche verwendet werden kann, muss die **Zielpfad** sollte auf Folgendes verweisen:

   ```shell
      /projects.html
   ```

* Um die klassische Benutzeroberfläche als Standard-Benutzeroberfläche zu verwenden, muss die **Zielpfad** sollte auf Folgendes verweisen:

   ```shell
      /welcome.html
   ```

>[!NOTE]
>
>Bei einer Standardinstallation ist die Touch-optimierte Benutzeroberfläche die Standardbenutzeroberfläche.

**Adobe Granite SSO Authentication Handler** - Konfigurieren von SSO-Details (Single Sign-On). Diese Details werden oft in Unternehmensautorenkonfigurationen benötigt, oft mit LDAP.

Verschiedene Eigenschaften können konfiguriert werden: 

* **Pfad**
Der Pfad, für den dieser Authentifizierungs-Handler aktiv ist. Wenn dieser Parameter leer gelassen wird, ist der Authentifizierungs-Handler deaktiviert. Beispielsweise wird beim Pfad / der Authentifizierungs-Handler für das gesamte Repository verwendet.

* **Service Ranking** Der Rangfolge-Wert für den OSGi-Framework-Dienst gibt die Reihenfolge an, in der dieser Dienst aufgerufen wird. Dieser Wert ist 
`int`-Wert, wobei höhere Werte eine höhere Priorität angeben.
Der Standardwert ist `0`.

* **Kopfzeilennamen**
Die Namen der Kopfzeilen, die möglicherweise eine Benutzer-ID enthalten.

* **Cookie-Namen**
Die Namen der Cookies, die möglicherweise eine Benutzer-ID enthalten.

* **Parameternamen**
Die Namen der Anforderungsparameter, die die Benutzer-ID bereitstellen können.

* **User Map** Für bestimmte Benutzer kann der aus der HTTP-Anforderung extrahierte Benutzername im Anmeldedaten-Objekt durch einen anderen Namen ersetzt werden. Die Zuordnung ist hier definiert. Wenn der Benutzername 
`admin` auf beiden Seiten der Zuordnung angezeigt wird, wird die Zuordnung ignoriert. Das Zeichen &quot;=&quot;muss mit einem vorangestellten &quot;\&quot; als Escape-Zeichen versehen werden.

* **Format** Gibt das Format an, in dem die Benutzer-ID angegeben ist. Verwenden Sie:

   * `Basic`, falls die Benutzer-ID im HTTP-Standard-Authentifizierungsformat kodiert ist
   * `AsIs`, falls die Benutzer-ID im Nur-Text-Format bereitgestellt wird, oder jeder für reguläre Ausdrücke gültige Wert unverändert bzw. jeder reguläre Ausdruck verwendet werden soll

**Day CQ WCM Debug Filter** Dies ist beim Entwickeln hilfreich, da Suffixe wie ?debug=layout beim Zugriff auf eine Seite verwendet werden können. Beispielsweise stellt https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout Layoutinformationen bereit, die für den Entwickler von Interesse sein können.

* Um die Leistung und Sicherheit sicherzustellen, deaktivieren Sie auf Produktionsinstanzen.

**Day CQ WCM Filter** Konfigurieren Sie:

* **WCM-Modus** , um den Standardmodus zu definieren.
* Auf einer Autoreninstanz kann dieser Modus `edit`, `disable,preview`oder `analytics`.
Auf die anderen Modi kann aus dem Sidekick zugegriffen werden. Oder das Suffix `?wcmmode=disabled` kann zum Emulieren der Produktionsumgebung verwendet werden.

* In einer Veröffentlichungsinstanz muss dieser Modus auf `disabled` um sicherzustellen, dass kein anderer Modus verfügbar ist.

>[!NOTE]
>
>Diese Einstellung wird für Produktionsinstanzen automatisch konfiguriert, wenn Sie AEM im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausführen.

**Day CQ WCM Link Checker Configurator** Konfigurieren Sie:

* **Liste der Neuschreibungskonfigurationen** , um eine Liste der Speicherorte für inhaltsbasierte Link-Checker-Konfigurationen anzugeben. Die Konfigurationen können auf dem Ausführungsmodus basieren. Diese Tatsache ist wichtig, um zwischen Autoren- und Veröffentlichungsumgebungen zu unterscheiden, da die Einstellungen des Link-Checkers unterschiedlich sein können.

**Day CQ WCM Page Manager Factory** Konfigurieren Sie:

* **Page Subtree Activation Check** für einen Benutzer (ohne Replikationsberechtigungen), um Seiten zu löschen oder zu verschieben (auch wenn die Seiten nicht aktiviert sind).

**Day CQ WCM Page Processor** Konfigurieren Sie:

* **Paths**, eine Liste der Speicherorte, die das System auf Seitenänderungen überwacht, bevor ein `jcr:Event` ausgelöst wird.

**Adobe Page Impressions Tracker** Konfigurieren Sie für eine Autoreninstanz wie folgt:

* **sling.auth.requirements**: legen Sie für diese Eigenschaft den Wert auf `-/libs/wcm/stats/tracker` fest.

>[!CAUTION]
>
>Diese Konfiguration ermöglicht anonyme Anfragen an den Tracking-Dienst.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Page Statistics** Konfigurieren Sie für eine Veröffentlichungsinstanz Folgendes:

* **URL zum Senden von Daten** Konfigurieren der URL, die zur Verfolgung von Seitenstatistiken verwendet wird (ist wichtig, wenn eine Tracker-Anforderung den Dispatcher durchläuft); Beispielsweise ist der Standardwert `https://localhost:4502/libs/wcm/stats/tracker`.

* **Tracking script enabled**: aktiviert (`true`) oder deaktiviert (`false`) den Einschluss der Nachverfolgungsskripts auf den Seiten. Der Standardwert ist `false`.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Seitenimpressionen](/help/sites-deploying/configuring.md#enabling-page-impressions).

**Day CQ WCM Version Manager** Steuern Sie, ob und wie Versionen in Ihrem System verwaltet werden:

* **Create Version on Activation** ist bei der Standardinstallation aktiviert.
* **Enable Purging**

* **Pfade bereinigen**, die Pfade, nach denen eine Suchaktion sucht.
* **Implicit Versioning Paths**: die Pfade, bei denen die implizite Versionierung aktiv ist.

* **Max Version Age**: das maximale Alter (in Tagen) einer Version.

* **Max Number Versions**: die maximale Anzahl der beizubehaltender Versionen.

Weitere Informationen finden Sie unter [Löschen von Versionen](/help/sites-deploying/version-purging.md).

**Day CQ Workflow Email Notification Service** Konfigurieren Sie die E-Mail-Einstellungen für Benachrichtigungen, die von einem Workflow gesendet werden.

**CQ Rewriter HTML Parser Factory**

Steuert den HTML-Parser für den CQ-Rewriter.

* **Zusätzliche Tags zur Verarbeitung** - Sie können HTML-Tags hinzufügen oder entfernen, die vom Parser verarbeitet werden sollen. Standardmäßig werden die folgenden Tags verarbeitet: A,IMG,AREA,FORM,BASE,LINK,SCRIPT,BODY,HEAD.
* **Camel Case beibehalten** - Standardmäßig konvertiert der HTML-Parser Attribute in Binnenmajuskel-Schreibweise (z. B. `eBay`) in Kleinbuchstaben (z. B. `ebay`). Sie können diese Einstellung deaktivieren, um die Attribute der Binnenmajuskel-Groß-/Kleinschreibung beizubehalten. Diese Einstellung ist nützlich bei der Verwendung von Frontend-Frameworks wie Angular 2.

**Day Commons JDBC Connections Pool** Konfigurieren Sie den Zugriff auf eine externe Datenbank, die als Quelle für Inhalte verwendet wird.

Eine Factory-Konfiguration, sodass mehrere Instanzen konfiguriert werden können.

**CDN Rewriter** Die Kommunikation zwischen AEM und einem CDN muss sichergestellt sein, damit Assets/Binärdateien auf sichere Weise an einen Endbenutzer übermittelt werden. Dieser Prozess umfasst die beiden folgenden Aufgaben:

* Zugriff auf die Ressource von AEM über das CDN beim ersten Mal (oder nachdem sie im Cache abgelaufen ist).
* Sicherer Zugriff auf die im CDN zwischengespeicherte Ressource. Nachdem die Ressource im CDN zwischengespeichert wurde, wird die Anfrage nicht an AEM gesendet und alle Benutzer, die Zugriff auf diese Ressource haben, sollten vom CDN bereitgestellt werden.

AEM bietet einen Rewriter zum Neuschreiben interner Asset-URLs in externe CDN-URLs. Es schreibt Links, die an das CDN weitergegeben werden sollen, einschließlich einer JWS-Signatur, und läuft die Zeit ab, damit der Asset sicher aufgerufen werden kann. Diese Funktion wird in Autoreninstanzen verwendet.

Der Gesamtdurchsatz sieht wie folgt aus:

1. Der Benutzer authentifiziert sich bei AEM und fordert eine Seite mit Assets an.
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
>Diese Funktion ist nur für AEM Autoreninstanzen aktiviert.

**CDNConfigServiceImpl** Bietet CDN-Konfigurationen

Sie können die CDN-Rewriter-Funktion aktivieren, indem Sie den **Domain-Namen der CDN-Verteilung** in der Konfiguration für com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl angeben.

Der Service enthält auch andere Konfigurationsoptionen wie das Aktivieren/Deaktivieren der CDN-Neuschreib-Funktion, Pfad-Präfixe für das Neuschreiben durch CDN, TTL-Werte und Protokolle (HTTP oder HTTPS).

**CDNRewriter** Ein Rewriter für das Neuschreiben interner Image-URLs als CDN-URLs

Der Wert **Tag Attributes** in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kann so definiert werden, dass nur bestimmte Image-Links neu geschrieben werden.
