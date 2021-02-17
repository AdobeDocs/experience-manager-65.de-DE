---
title: Sicherheitscheckliste
seo-title: Sicherheitscheckliste
description: Erfahren Sie mehr über die verschiedenen Sicherheitsüberlegungen beim Konfigurieren und Bereitstellen von AEM.
seo-description: Erfahren Sie mehr über die verschiedenen Sicherheitsüberlegungen beim Konfigurieren und Bereitstellen von AEM.
uuid: 8e293316-4177-4271-87c6-9dc1a2e85a07
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: de7d7209-c194-4d19-853b-468ebf3fa4b2
docset: aem65
translation-type: tm+mt
source-git-commit: 474fc122f557f32d34fddd9d35a113431f6ce491
workflow-type: tm+mt
source-wordcount: '2841'
ht-degree: 88%

---


# Sicherheitscheckliste {#security-checklist}

Dieser Abschnitt behandelt die verschiedenen Schritte, mit denen Sie sicherstellen können, dass Ihre AEM-Installation bei der Bereitstellung sicher ist. Die Checkliste ist so konzipiert, dass sie von oben nach unten abgearbeitet werden sollte.

>[!NOTE]
>
>Weitere Informationen [zu den gefährlichsten Sicherheitsbedrohungen (veröffentlicht vom Open Web Application Security Project (OWASP)) sind ebenfalls verfügbar](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

>[!NOTE]
>
>Es gibt einige zusätzliche [Sicherheitsüberlegungen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations), die in der Entwicklungsphase berücksichtig werden müssen.

## Hauptsicherheitsmaßnahmen {#main-security-measures}

### Ausführen von AEM im produktionsbereiten Modus {#run-aem-in-production-ready-mode}

Weitere Informationen dazu finden Sie in [Ausführen von AEM im produktionsbereiten Modus](/help/sites-administering/production-ready.md).

### Aktivieren von HTTPS für Transport Layer Security {#enable-https-for-transport-layer-security}

Die Aktivierung der HTTPS-Transportschicht (Transport Layer) in den Autoren- und Veröffentlichungsinstanzen ist obligatorisch, um eine sichere Instanz zu erhalten.

>[!NOTE]
>
>Weitere Informationen finden Sie im Abschnitt [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### Installieren von Sicherheit-Hotfixes {#install-security-hotfixes}

Stellen Sie sicher, dass die neuesten, [von Adobe bereitgestellten Sicherheits-Hotfixes](https://helpx.adobe.com/de/experience-manager/kb/aem63-available-hotfixes.html) installiert sind.

### Änderung von Standardkennwörtern für die Admin-Konten von AEM und der OSGi-Konsole {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe empfiehlt dringend, dass Sie das Kennwort für die mit allen Berechtigungen ausgestatteten [**-Konten von** AEM`admin` nach der Installation ändern (in allen Instanzen).](#changing-the-aem-admin-password)

Diese Konten beinhalten:

* AEM `admin`-Konto

   Nachdem Sie das Kennwort für das AEM Admin-Konto geändert haben, müssen Sie beim Zugriff auf CRX das neue Kennwort verwenden.

* Das `admin`-Kennwort für die OSGi-Webkonsole

   Diese Änderung wird auch auf das Administratorkonto angewendet, das für den Zugriff auf die Web-Konsole verwendet wird. Daher müssen Sie beim Zugriff darauf dasselbe Kennwort verwenden.

Diese beiden Konten nutzen separate Kontoanmeldeinformationen und die Verwendung von unterschiedlichen sicheren Kennwörtern für jedes Konto ist für eine sichere Bereitstellung von entscheidender Bedeutung.

#### Ändern des Admin-Kennworts von AEM {#changing-the-aem-admin-password}

Das Kennwort für das Admin-Konto von AEM kann über die Konsole [Granite-Vorgänge – Benutzer](/help/sites-administering/granite-user-group-admin.md) geändert werden.

Dort können Sie das `admin`-Konto bearbeiten und [das Kennwort ändern](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Eine Änderung des Admin-Kontos führt auch zu einer Änderung des OSGi-Webkonsolenkontos. Nachdem Sie das Admin-Konto geändert haben, sollten Sie das OSGi-Konto so ändern, dass es sich vom Admin-Konto unterscheidet.

#### Bedeutung der Änderung des Kennworts für die OSGi-Web-Konsole {#importance-of-changing-the-osgi-web-console-password}

Unabhängig vom `admin`-Konto von AEM kann eine Nichtänderung des Standardkennworts für die OSGi-Web-Konsole dazu führen, dass:

* der Server aufgrund des Standardkennworts beim Starten und Herunterfahren einem Sicherheitsrisiko ausgesetzt ist (bei großen Servern kann dies einige Minuten dauern).
* der Server einem Sicherheitsrisiko ausgesetzt ist, wenn das Repository nicht aktiv ist oder ein Bundle neu startet und OSGi ausgeführt wird.

Weitere Informationen zum Ändern des Kennworts für die Web-Konsole finden Sie im nachfolgenden Abschnitt [Ändern des Admin-Kennworts für die OSGi-Web-Konsole](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password).

#### Ändern des Admin-Kennworts für die OSGi-Web-Konsole  {#changing-the-osgi-web-console-admin-password}

Sie müssen auch das Kennwort ändern, das für den Zugriff auf die Web-Konsole verwendet wird. Dies erfolgt durch Konfiguration der folgenden Eigenschaften der Verwaltungskonsole [Apache Felix OSGi ](/help/sites-deploying/osgi-configuration-settings.md):

**Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.
Das Kennwort muss nach der ersten Installation geändert werden, damit die Sicherheit Ihrer Instanz gewährleistet ist.

Gehen Sie hierfür wie folgt vor:

1. Navigieren Sie zur Webkonsole unter `<server>:<port>/system/console/configMgr`.
1. Navigieren Sie zu **Apache Felix OSGi Management Console** und ändern Sie den **Benutzernamen** und das **Kennwort**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Klicken Sie auf **Speichern**.

### Implementieren von benutzerdefinierten Fehler-Handlern  {#implement-custom-error-handler}

Adobe empfiehlt die Definition von benutzerdefinierten Fehler-Handler-Seiten, insbesondere für 404- und 500-HTTP-Antwortcodes, um die Offenlegung von Informationen zu verhindern.

>[!NOTE]
>
>Weitere Details finden Sie im Knowledgebase-Artikel [Erstellen von benutzerdefinierten Skripten oder Fehler-Handlern](https://helpx.adobe.com/de/experience-manager/kb/CustomErrorHandling.html).

### Durchgehen der Dispatcher-Sicherheitscheckliste {#complete-dispatcher-security-checklist}

Der AEM-Dispatcher ist ein wichtiger Teil Ihrer Infrastruktur. Adobe empfiehlt dringend, dass Sie die [Dispatcher-Sicherheitscheckliste](https://helpx.adobe.com/experience-manager/dispatcher/using/security-checklist.html) durchgehen.

>[!CAUTION]
>
>Zur Verwendung des Dispatchers müssen Sie den „.form“-Selektor deaktivieren.

## Überprüfungsschritte  {#verification-steps}

### Konfigurieren von Replikations- und Transportbenutzer {#configure-replication-and-transport-users}

Bei einer Standardinstallation von AEM wird `admin` als Benutzer für die Transport-Anmeldedaten in den Standard-[Replikationsagenten](/help/sites-deploying/replication.md) angegeben. Der Admin-Benutzer wird auch verwendet, um die Replikation auf dem Autorensystem zu beziehen.

Aus Sicherheitsgründen sollte beides unter Berücksichtigung der folgenden beiden Aspekte geändert werden, um den bestimmten vorliegenden Anwendungsfall widerzuspiegeln:

* Der **Transport-Benutzer** sollte nicht der Admin-Benutzer sein. Richten Sie stattdessen einen Benutzer auf dem Veröffentlichungssystem ein, der nur über Zugriffsrechte für die relevanten Abschnitte des Veröffentlichungssystems verfügt, und verwenden Sie die Anmeldedaten dieses Benutzers für den Transport.

     Sie können mit dem gebündelten Benutzer „Replikations-Empfänger“ beginnen und die Zugriffsrechte dieses Benutzers so konfigurieren, dass sie Ihren Anforderungen entsprechen.

* Der **Replikationsbenutzer** oder die **Agenten-Benutzer-ID** sollte auch nicht der Admin-Benutzer sein, sondern ein Benutzer, der nur die Inhalte sehen kann, die repliziert werden sollen. Der Replikationsbenutzer wird auch zum Erfassen von Inhalten verwendet, die auf dem Autorensystem repliziert werden sollen, bevor sie an den Publisher gesendet werden.

### Kontrollieren der Sicherheits-Konsistenzprüfungen auf dem Vorgangs-Dashboard {#check-the-operations-dashboard-security-health-checks}

In AEM 6 wird das neue Vorgangs-Dashboard eingeführt, das Systembedienern bei der Behebung von Problemen und der Überwachung des Zustands einer Instanz helfen soll.

Das Dashboard umfasst eine Reihe von Sicherheits-Konsistenzprüfungen. Es empfiehlt sich, den Status aller Sicherheits-Konsistenzprüfungen zu kontrollieren, bevor Sie Ihre Produktionsinstanz in Betrieb nehmen. Weitere Informationen dazu finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

### Prüfen, ob Beispielinhalte vorhanden sind {#check-if-example-content-is-present}

Alle Beispielinhalte und -benutzer (z. B. das Geometrixx-Projekt und die zugehörigen Komponenten) sollten deinstalliert und vollständig von einem Produktionssystem gelöscht werden, bevor es öffentlich zugänglich gemacht wird.

>[!NOTE]
>
>Die We.Retail-Beispielanwendungen werden entfernt, wenn diese Instanz im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausgeführt wird. Wenn dies aus irgendeinem Grund nicht der Fall ist, können Sie den Beispielinhalt deinstallieren, indem Sie Package Manager aufrufen und dann nach allen We.Retail-Paketen suchen und sie deinstallieren. Weitere Informationen finden Sie unter [Mit Paketen arbeiten](package-manager.md).

### Prüfen, ob die CRX-Entwicklungsbundles vorhanden sind {#check-if-the-crx-development-bundles-are-present}

Die OSGi-Entwicklungsbundles sollten sowohl auf dem Autoren- als auch auf dem Veröffentlichungs-Produktionssystem deinstalliert werden, bevor sie zugänglich gemacht werden.

* Unterstützung von Adobe CRXDE (com.adobe.granite.crxde-support)
* Adobe Granite CRX Explorer (com.adobe.granite.crx-explorer)
* Adobe Granite CRXDE Lite (com.adobe.granite.crxde-lite)

### Prüfen, ob das Sling-Entwicklungsbundle vorhanden ist  {#check-if-the-sling-development-bundle-is-present}

[AEM Developer Tools for Eclipse](/help/sites-developing/aem-eclipse.md) stellt das Tool „Apache Sling Tooling Support Install“ (org.apache.sling.tooling.support.install) bereit.

Dieses OSGi-Bundle sollte sowohl auf dem Autoren- als auch auf dem Veröffentlichungs-Produktionssystem deinstalliert werden, bevor diese zugänglich gemacht werden.

### Schutz vor Cross-Site Request Forgery-Angriffen  {#protect-against-cross-site-request-forgery}

#### Das CSRF Protection Framework {#the-csrf-protection-framework}

AEM 6.1 verfügt über einen Mechanismus namens **CSRF Protection Framework**, der vor Cross-Site Request Forgery-Angriffen (Website-übergreifende Anfragenfälschung) schützt. Weitere Informationen zur Verwendungsweise finden Sie in der entsprechenden [Dokumentation](/help/sites-developing/csrf-protection.md).

#### Der Sling Referrer Filter {#the-sling-referrer-filter}

Zur Behebung bekannter Sicherheitsprobleme hinsichtlich Cross-Site Request Forgery-(CSRF-)Angriffen in CRX WebDAV und Apache Sling müssen Sie Konfigurationen für den Referrer Filter hinzufügen, um diesen verwenden zu können.

Der Referrer-Filter-Dienst ist ein OSGi-Dienst, mit dem Sie Folgendes konfigurieren können:

* Welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* und eine Liste von Servern, die zusätzlich zum Server-Host zulässig sind.

   Standardmäßig befinden sich alle Varianten von localhost und die aktuellen Hostnamen, an die der Server gebunden ist, in der Liste.

So konfigurieren Sie den Referrer-Filterdienst:

1. Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) unter:

   `https://<server>:<port_number>/system/console/configMgr`

1. Melden Sie sich als `admin` an.
1. Wählen Sie im Menü **Konfigurationen** folgende Option aus:

   `Apache Sling Referrer Filter`

1. Geben Sie im Feld `Allow Hosts` alle Hosts ein, die als Werber zulässig sind. Jeder Eintrag muss vom Formular sein

   &lt;protocol>://&lt;server>:&lt;port>

   Beispiel:

   * `https://allowed.server:80`: Alle Anfragen von diesem Server mit dem angegebenen Port sind zugelassen.
   * Wenn Sie auch HTTPS-Anfragen zulassen wollen, müssen Sie eine zweite Zeile eingeben.
   * Falls Sie alle Ports dieses Servers zulassen wollen, können Sie als Portnummer eine `0` eingeben.

1. Markieren Sie das Feld `Allow Empty`, wenn Sie leere/fehlende Werber-Kopfzeilen zulassen möchten.

   >[!CAUTION]
   >
   >Es wird empfohlen, einen Referrer bereitzustellen, wenn Sie Befehlszeilen-Tools wie `cURL` verwenden, anstatt einen leeren Wert zuzulassen, da andernfalls das Risiko besteht, dass Ihr System CSRF-Angriffen ausgesetzt ist.

1. Bearbeiten Sie die Methoden, die dieser Filter für Prüfungen mit dem Feld `Filter Methods` verwenden soll.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### OSGi-Einstellungen {#osgi-settings}

Einige OSGi-Einstellungen sind standardmäßig festgelegt, um ein einfacheres Debugging der Anwendung zu ermöglichen. Diese müssen in der Veröffentlichungs- und der Autoren-Produktionsinstanz geändert werden, um zu verhindern, dass interne Informationen offengelegt werden.

>[!NOTE]
>
>Alle nachfolgenden Einstellungen mit Ausnahme des **Day CQ WCM Debug Filters** sind automatisch im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) enthalten. Aus diesem Grund wird empfohlen, alle Einstellungen vor der Bereitstellung der Instanz in einer Produktionsumgebung zu überprüfen.

Sie müssen für jeden der folgenden Dienste die angegebenen Einstellungen ändern:

* [Adobe Granite HTML-Bibliotheksmanager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * Aktivieren Sie **Minify** (um Neuzeilenzeichen [CRLF] und Leerzeichen zu löschen).
   * Aktivieren Sie **Gzip** (um Dateien als GZIP zu komprimieren und mit einer Anforderung darauf zuzugreifen).
   * Deaktivieren Sie **Debug**.
   * Deaktivieren Sie **Timing**.

* [Day CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter):

   * Heben Sie die Auswahl von **Aktivieren** auf.

* [Day CQ WCM-Filter](/help/sites-deploying/osgi-configuration-settings.md):

   * Legen Sie die Option **WCM-Modus** nur auf der Veröffentlichungsinstanz auf „Deaktiviert“ fest.

* [Apache Sling Java Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * Deaktivieren Sie **Generate Debug Info**.

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * Deaktivieren Sie **Generate Debug Info**.
   * Deaktivieren Sie **Mapped Content**.

Weitere Informationen finden Sie in [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Weitere Informationen  {#further-readings}

### Verringern von Denial-of-Service-(DoS-)Angriffen {#mitigate-denial-of-service-dos-attacks}

Ein Denial-of-Service-Angriff (DoS) zielt darauf ab, eine Computerressource für die vorgesehenen Benutzer unzugänglich zu machen. Dies geschieht häufig, indem die Ressource überlastet wird, zum Beispiel:

* durch eine Flut von Anfragen von einer externen Quelle;
* durch eine Anforderung von mehr Informationen, als das System erfolgreich bereitstellen kann.

   Beispiel: Eine JSON-Darstellung des gesamten Repositorys.

* Wenn eine Seite mit einer unbegrenzten Anzahl an URLs angefordert wird, kann die URL einen Handler, einige Selektoren, eine Erweiterung und einen Suffix enthalten. Diese Elemente können alle geändert werden.

   `.../en.html` kann beispielsweise auch wie folgt angefordert werden:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

   Alle gültigen Varianten (geben z. B. die Antwort `200` zurück und werden per Konfiguration zwischengespeichert) werden vom Dispatcher zwischengespeichert, was möglicherweise zu einem vollen Dateisystem führen kann, sodass kein Dienst für weitere Anfragen verfügbar ist.

Es gibt viele Konfigurationspunkte zum Verhindern solcher Angriffe. In diesem Dokument gehen wir jedoch nur auf die ein, die direkt für AEM relevant sind.

**Konfigurieren von Sling zum Verhindern von DoS-Angriffen**

Sling ist *inhaltsorientiert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anfrage auf den Inhalt in Form einer JCR-Ressource (eines Repository-Knotens) abgebildet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die die Inhalte enthält..
* Als Zweites wird der Renderer oder das Skript aus den Ressourceneigenschaften ausgelesen – zusammen mit bestimmten Teilen der Anfrage (z. B. Selektoren und/oder die Erweiterung).

>[!NOTE]
>
>Dies wird ausführlicher im Abschnitt [Verarbeiten von Sling-Anfragen](/help/sites-developing/the-basics.md#sling-request-processing) beschrieben.

Durch diesen Ansatz wird Sling zu einem leistungsstarken und sehr flexiblen Tool, aber wie immer ist es die Flexibilität, die sorgfältig verwaltet werden muss.

So verhindern Sie einen Missbrauch infolge von DoS-Angriffen:

1. Steuerungen auf Anwendungsebene implementieren. Aufgrund der Anzahl an möglichen Varianten ist eine Standardkonfiguration nicht praktikabel.

   In Ihrer Anwendung sollten Sie:

   * die Selektoren in der Anwendung steuern, sodass Sie *nur* die erforderlichen expliziten Selektoren verwenden und für alle anderen den Wert `404` zurückgeben.
   * die Ausgabe einer unbegrenzten Anzahl an Inhaltsknoten vermeiden.

1. die Konfiguration der Standard-Renderer überprüfen, die eine Problemquelle darstellen können.

   * Dies gilt insbesondere für den JSON-Renderer, der sich über mehrere Ebenen der hierarchischen Struktur erstrecken kann.

      Beispielsweise die Anforderung:

      `http://localhost:4502/.json`

      könnte das gesamte Repository in einer JSON-Darstellung ablegen. Dies würde zu erheblichen Serverproblemen führen. Aus diesem Grund beschränkt Sling die Anzahl an maximalen Ergebnissen. Um die Tiefe des JSON-Renderings zu begrenzen, können Sie den Wert für Folgendes festlegen:

      **JSON Max. Ergebnisse** (  `json.maximumresults`)

      in der Konfiguration für den Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet). [ Wenn dieser Grenzwert überschritten wird, wird das Rendering ausgeblendet. Der Standardwert für Sling innerhalb von AEM ist `200`.

   * Deaktivieren Sie als Präventivmaßnahme die anderen Standard-Renderer (HTML, Nur Text, XML). Konfigurieren Sie dazu ebenfalls das [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet).
   >[!CAUTION]
   >
   >Deaktivieren Sie nicht den JSON-Renderer. Dieser ist für den normalen Betrieb von AEM erforderlich.

1. Verwenden Sie eine Firewall, um den Zugriff auf Ihre Instanz zu filtern.

   * Eine Firewall auf Betriebssystemebene ist erforderlich, um den Zugriff auf Punkte Ihrer Instanz zu filtern, die ungeschützt möglicherweise zu DoS-Angriffen führen können.

**Abmildern von DoS mithilfe der Formularauswahl**

>[!NOTE]
>
>Diese Abmilderung sollte nur für AEM-Umgebungen durchgeführt werden, die keine Formulare verwenden.

Da AEM keine Standardindizes für `FormChooserServlet` bereitstellt, löst die Verwendung der Formularauswahl in Abfragen einen aufwändigen Repository-Durchlauf aus, der meist die AEM-Instanz stoppt. Formularauswahlen können durch das Vorhandensein von **&amp;ast;.form erkannt werden.&amp;ast;**-Zeichenfolge in Abfragen.

Führen Sie zum Beheben dieses Problems die folgenden Schritte aus:

1. Gehen Sie zur Web-Konsole, indem Sie Ihren Browser auf *https://&lt;server-Adresse>:&lt;server-Anschluss>/system/console/configMgr* zeigen.

1. Suchen nach **Day CQ WCM Form Chooser Servlet**
1. Klicken Sie auf den Eintrag, deaktivieren Sie im folgenden Fenster die Option **Advanced Search Require** (Erweiterte Suche erforderlich).

1. Klicken Sie auf **Speichern**.

**Abmildern von DoS durch Asset Download Servlet**

Das standardmäßig in AEM enthaltene Asset Download Servlet ermöglicht es authentifizierten Benutzern, willkürlich große gleichzeitige Download-Anfragen zum Erstellen von ZIP-Dateien von für sie sichtbaren Assets zu erstellen, die den Server und das Netzwerk überlasten können.

Um potenzielle DoS-Risiken zu reduzieren, die durch diese Funktion verursacht werden, ist die `AssetDownloadServlet`-OSGi-Komponente für Veröffentlichungsinstanzen in den neuesten AEM-Versionen standardmäßig deaktiviert.

Wenn Sie Asset Download Server im Rahmen Ihrer Einrichtung aktivieren müssen, finden Sie in [diesem Artikel](/help/assets/download-assets-from-aem.md) weitere Informationen.

### Deaktivieren von WebDAV {#disable-webdav}

WebDAV sollte sowohl in Autoren- als auch in Veröffentlichungsumgebungen deaktiviert werden. Stoppen Sie dazu die entsprechenden OSGi-Bundles.

1. Stellen Sie eine Verbindung zur **Felix Management Console** her, die ausgeführt wird unter:

   `https://<*host*>:<*port*>/system/console`

   Beispiel `http://localhost:4503/system/console/bundles`.

1. Suchen Sie in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Klicken Sie in der Spalte „Aktionen“ auf die Schaltfläche „Stopp“, um dieses Bundle zu stoppen.

1. Suchen Sie erneut in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Klicken Sie auf die Schaltfläche „Stopp“, um dieses Bundle zu stoppen.

   >[!NOTE]
   >
   >Ein Neustart von AEM ist nicht erforderlich.

### Sicherstellen, dass keine personenbezogenen Informationen im Home-Pfad von Benutzern offengelegt werden {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Der Schutz Ihrer Benutzer ist wichtig. Stellen Sie daher sicher, dass Sie keine personenbezogenen Informationen im Home-Pfad von Repository-Benutzern offenlegen.

Ab AEM 6.1 ändert sich mit der neuen Implementierung der Schnittstelle `AuthorizableNodeName` die Art, wie Benutzer-ID-Knotennamen (auch als autorisierbare ID-Knotennamen bezeichnet) gespeichert werden. Die neue Schnittstelle legt nicht mehr die Benutzer-ID im Knotennamen offen, sondern generiert stattdessen einen zufälligen Namen.

Es ist keine Konfiguration erforderlich, um sie zu aktivieren, da dies nun die Standardvorgehensweise zum Generieren von autorisierbaren IDs in AEM ist.

Obwohl dies nicht empfohlen wird, können Sie sie deaktivieren, wenn Sie die alte Implementierung aus Gründen der Abwärtskompatibilität mit vorhandenen Applikationen benötigen. Gehen Sie dazu wie folgt vor:

1. Gehen Sie zur Web-Konsole und entfernen Sie den Eintrag** org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** aus der Eigenschaft **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   Sie können den Oak Security Provider auch finden, indem Sie in den OSGi-Konfigurationen nach der PID **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** suchen.

1. Löschen Sie die OSGi-Konfiguration **Apache Jackrabbit Oak Random Authorizable Node Name** aus der Web-Konsole.

   Um die Suche zu vereinfachen, beachten Sie, dass die PID für diese Konfiguration **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** lautet.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Oak-Dokumentation zur [Namenserstellung für autorisierbare Knoten](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Verhindern von Clickjacking {#prevent-clickjacking}

Um Clickjacking zu verhindern, sollten Sie Ihren Webserver so konfigurieren, dass er die HTTP-Kopfzeile `X-FRAME-OPTIONS` bereitstellt, die auf `SAMEORIGIN` festgelegt ist.

Weitere [Informationen zum Thema Clickjacking finden Sie auf der OWASP-Website](https://www.owasp.org/index.php/Clickjacking).

### Sicherstellen, dass Verschlüsselungsschlüssel bei Bedarf korrekt repliziert werden {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bestimmte AEM-Funktionen und Authentisierungsschemata erfordern, dass Sie Ihre Verschlüsselungsschlüssel in allen AEM-Instanzen replizieren.

Bevor Sie das tun, beachten Sie, dass die Schlüsselreplikation von Version zu Version unterschiedlich sein kann, da die Art der Speicherung von Schlüsseln zwischen der Version 6.3 und älteren Versionen unterschiedlich ist.

Weitere Informationen finden Sie im folgenden Abschnitt.

#### Replizieren von Schlüsseln in AEM 6.3  {#replicating-keys-for-aem}

In älteren Versionen wurden die Replikationsschlüssel im Repository gespeichert, ab AEM-Version 6.3 werden sie jedoch im Dateisystem gespeichert.

Daher müssen Sie zum Replizieren Ihrer Schlüssel auf den Instanzen diese von der Quellinstanz an den Speicherort im Dateisystem der Zielinstanzen kopieren.

Genauer gesagt, müssen Sie Folgendes tun:

1. Greifen Sie auf die AEM-Instanz zu, auf der sich die zu kopierenden Schlüsseldaten befinden. In der Regel handelt es sich dabei um eine Autoreninstanz.
1. Suchen Sie im lokalen Dateisystem das Bundle com.adobe.granite.crypto.file. Es kann sich z. B. unter diesem Pfad befinden:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   Die Datei `bundle.info` in jedem Ordner identifiziert den Bundle-Namen.

1. Navigieren Sie zum Ordner „data“. Beispiel:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieren Sie die HMAC- und die Master-Dateien.
1. Navigieren Sie dann zur Zielinstanz, auf der Sie den HMAC-Schlüssel duplizieren möchten, und dann zum Ordner „data“. Beispiel:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Fügen Sie die beiden zuvor kopierten Dateien ein.
1. [Aktualisieren Sie das Crypto-Bundle](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle), wenn die Zielinstanz bereits ausgeführt wird.
1. Wiederholen Sie die vorherigen Schritte für alle Instanzen, auf denen Sie den Schlüssel replizieren möchten.

>[!NOTE]
>
>Sie können zum älteren Verfahren zum Speichern von Schlüssel (vor der Version 6.3) zurückkehren, indem Sie den folgenden Parameter bei der ersten Installation von AEM hinzufügen:
>
>`-Dcom.adobe.granite.crypto.file.disable=true`

#### Replizieren von Schlüsseln in AEM 6.2 und älteren Versionen {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 und älteren Versionen werden die Schlüssel im Repository unter dem Knoten `/etc/key` gespeichert.

Für eine sichere Replikation der Schlüssel auf Ihren Instanzen wird empfohlen, nur diesen Knoten zu replizieren. Sie können Knoten in CRXDE Lite selektiv replizieren:

1. Öffnen Sie die CRXDE Lite, indem Sie zu *https://&lt;server-Adresse>:4502/crx/de/index.jsp* wechseln.
1. Wählen Sie den Knoten `/etc/key` aus.
1. Wechseln Sie zur Registerkarte **Replikation**.
1. Klicken Sie auf die Schaltfläche **Replikation**.

### Durchführen eines Penetrationstests {#perform-a-penetration-test}

Adobe empfiehlt dringend, Ihre AEM-Infrastruktur vor dem Einsatz in einer Produktionsumgebung einem Penetrationstest zu unterziehen. 

### Best Practices für die Entwicklung {#development-best-practices}

Es ist wichtig, dass neue Entwicklungen den [Best Practices](/help/sites-developing/security.md) entsprechen, um eine dauerhaft sichere AEM-Umgebung zu gewährleisten.
