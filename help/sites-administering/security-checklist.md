---
title: Sicherheitscheckliste
seo-title: Security Checklist
description: Erfahren Sie mehr über die verschiedenen Sicherheitsüberlegungen beim Konfigurieren und Bereitstellen von AEM.
seo-description: Learn about the various security considerations when configuring and deploying AEM.
uuid: 8e293316-4177-4271-87c6-9dc1a2e85a07
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: de7d7209-c194-4d19-853b-468ebf3fa4b2
docset: aem65
exl-id: 314a6409-398c-470b-8799-0c4e6f745141
feature: Security
source-git-commit: e44480535ea7058dc41fc747351446b670d03b7f
workflow-type: tm+mt
source-wordcount: '2986'
ht-degree: 30%

---

# Sicherheitscheckliste {#security-checklist}

Dieser Abschnitt behandelt die verschiedenen Schritte, mit denen Sie sicherstellen können, dass Ihre AEM-Installation bei der Bereitstellung sicher ist. Die Checkliste ist so konzipiert, dass sie von oben nach unten abgearbeitet werden sollte.

>[!NOTE]
>
>Weitere Informationen zu den gefährlichsten Sicherheitsbedrohungen werden vom [Open Web Application Security Project (OWASP)](https://owasp.org/www-project-top-ten/) veröffentlicht.

>[!NOTE]
>
>Es gibt einige zusätzliche [Sicherheitsüberlegungen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations), die in der Entwicklungsphase berücksichtig werden müssen.

## Wichtigste Sicherheitsmaßnahmen {#main-security-measures}

### AEM im produktionsbereiten Modus ausführen {#run-aem-in-production-ready-mode}

Weitere Informationen finden Sie unter [Ausführen von AEM im produktionsbereiten Modus](/help/sites-administering/production-ready.md).

### Aktivieren von HTTPS für Transport Layer Security {#enable-https-for-transport-layer-security}

Die Aktivierung der HTTPS-Transportschicht (Transport Layer) in den Autoren- und Veröffentlichungsinstanzen ist obligatorisch, um eine sichere Instanz zu erhalten.

>[!NOTE]
>
>Weitere Informationen finden Sie im Abschnitt [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### Installieren von Sicherheits-Hotfixes {#install-security-hotfixes}

Vergewissern Sie sich, dass Sie die neueste Version installiert haben [Von Adobe bereitgestellte Sicherheits-Hotfixes](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de).

### Standardkennwörter für AEM und OSGi Console Admin-Konten ändern {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe empfiehlt nach der Installation, das Kennwort für die berechtigten [**AEM** `admin` Konten](#changing-the-aem-admin-password) (in allen Fällen).

Diese Konten beinhalten:

* Das `admin`-Konto von AEM

   Nachdem Sie das Kennwort für das AEM-Administratorkonto geändert haben, verwenden Sie beim Zugriff auf CRX das neue Kennwort.

* Das `admin`-Passwort für die OSGi-Web-Konsole

   Diese Änderung wird auch auf das Administratorkonto angewendet, das für den Zugriff auf die Web-Konsole verwendet wird. Verwenden Sie daher beim Zugriff darauf dasselbe Kennwort.

Diese beiden Konten nutzen separate Kontoanmeldeinformationen und die Verwendung von unterschiedlichen sicheren Passwörtern für jedes Konto ist für eine sichere Bereitstellung von entscheidender Bedeutung.

#### Ändern des AEM Administratorkennworts {#changing-the-aem-admin-password}

Das Kennwort für das AEM Administratorkonto kann über die [Granite-Vorgänge - Benutzer](/help/sites-administering/granite-user-group-admin.md) Konsole.

Dort können Sie das `admin`-Konto bearbeiten und [das Kennwort ändern](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Durch das Ändern des Admin-Kontos wird auch das OSGi-Web-Konsolenkonto geändert. Nachdem Sie das Administratorkonto geändert haben, sollten Sie das OSGi-Konto in etwas Anderes ändern.

#### Bedeutung der Änderung des Kennworts für die OSGi-Web-Konsole {#importance-of-changing-the-osgi-web-console-password}

Unabhängig vom `admin`-Konto von AEM kann eine Nichtänderung des Standardkennworts für die OSGi-Web-Konsole dazu führen, dass:

* Verfügbarkeit des Servers mit einem Standardkennwort beim Start und beim Herunterfahren (das bei großen Servern Minuten dauern kann);
* Exposition des Servers, wenn das Repository heruntergefahren/neu gestartet wird - und OSGi ausgeführt wird.

Weitere Informationen zum Ändern des Kennworts für die Web-Konsole finden Sie unter [Ändern des Administratorkennworts der OSGi-Web-Konsole](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) unten.

#### Ändern des Administratorkennworts der OSGi-Web-Konsole {#changing-the-osgi-web-console-admin-password}

Ändern Sie das Kennwort für den Zugriff auf die Webkonsole. Verwenden Sie eine [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) , um die folgenden Eigenschaften der **Apache Felix OSGi Management Console**:

* **Benutzername** und **Kennwort**: die Anmeldedaten für den Zugriff auf die Apache Felix Web Management Console.
Das Kennwort muss geändert werden *after* die Erstinstallation, um die Sicherheit Ihrer Instanz sicherzustellen.

>[!NOTE]
>
>Siehe [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen zur Konfiguration der OSGi-Einstellungen.

**So ändern Sie das Administratorkennwort der OSGi-Web-Konsole**:

1. Verwenden der **Instrumente**, **Aktivitäten** öffnen Sie das Menü **Web-Konsole** und navigieren Sie zum **Konfiguration** Abschnitt.
Beispiel: unter `<server>:<port>/system/console/configMgr`.
1. Navigieren Sie zum Eintrag für und öffnen Sie ihn. **Apache Felix OSGi Management Console**.
1. Ändern Sie die **Benutzername** und **password**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Wählen Sie **Speichern** aus.

### Benutzerdefinierten Fehler-Handler implementieren {#implement-custom-error-handler}

Adobe empfiehlt die Definition benutzerdefinierter Fehler-Handler-Seiten, insbesondere für 404- und 500-HTTP-Antwortcodes, um die Offenlegung von Informationen zu verhindern.

>[!NOTE]
>
>Siehe [Wie kann ich benutzerdefinierte Skripte oder Fehler-Handler erstellen?](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/full-stack/custom-error-page.html?lang=en) für weitere Details.

### Vollständige Dispatcher-Sicherheitscheckliste {#complete-dispatcher-security-checklist}

AEM Dispatcher ist ein wichtiger Teil Ihrer Infrastruktur. Adobe empfiehlt, die [Dispatcher-Sicherheitscheckliste](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/security-checklist.html?lang=en).

>[!CAUTION]
>
>Mithilfe des Dispatchers müssen Sie den &quot;.form&quot;-Selektor deaktivieren.

## Überprüfungsschritte {#verification-steps}

### Konfigurieren von Replikations- und Transportbenutzern {#configure-replication-and-transport-users}

Bei einer Standardinstallation von AEM wird `admin` als Benutzer für die Transport-Anmeldedaten in den Standard-[Replikationsagenten](/help/sites-deploying/replication.md) angegeben. Außerdem wird der Admin-Benutzer verwendet, um die Replikation auf dem Autorensystem zu beziehen.

Aus Sicherheitsgründen sollten beide geändert werden, um dem jeweiligen Anwendungsfall Rechnung zu tragen, wobei die beiden folgenden Aspekte zu berücksichtigen sind:

* Die **Transportnutzer** darf nicht der Administratorbenutzer sein. Richten Sie stattdessen einen Benutzer im Veröffentlichungssystem ein, der nur über Zugriffsrechte auf die relevanten Teile des Veröffentlichungssystems verfügt, und verwenden Sie die Anmeldeinformationen dieses Benutzers für den Transport.

     Sie können mit dem gebündelten Benutzer „Replikations-Empfänger“ beginnen und die Zugriffsrechte dieses Benutzenden so konfigurieren, dass sie Ihren Anforderungen entsprechen.

* Die **Replikationsbenutzer** oder **Agenten-Benutzer-ID** darf auch nicht der Admin-Benutzer sein, sondern ein Benutzer, der nur replizierte Inhalte sehen kann. Der Replikationsbenutzende wird auch zum Erfassen von Inhalten verwendet, die auf dem Autorensystem repliziert werden sollen, bevor sie an den Publisher gesendet werden.

### Überprüfen der Sicherheits-Konsistenzprüfungen im Vorgangs-Dashboard {#check-the-operations-dashboard-security-health-checks}

Mit AEM 6 wird das neue Vorgangs-Dashboard eingeführt, das Systembetreibern bei der Fehlerbehebung und der Überwachung des Zustands einer Instanz helfen soll.

Das Dashboard enthält außerdem eine Sammlung von Konsistenzprüfungen. Es wird empfohlen, den Status aller Sicherheits-Konsistenzprüfungen zu überprüfen, bevor Sie mit Ihrer Produktionsinstanz live gehen. Weitere Informationen dazu finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

### Überprüfen, ob Beispielinhalt vorhanden ist {#check-if-example-content-is-present}

Alle Beispielinhalte und -benutzer (z. B. das Geometrixx und seine Komponenten) sollten deinstalliert und vollständig auf einem Produktionssystem gelöscht werden, bevor sie öffentlich zugänglich gemacht werden.

>[!NOTE]
>
>Beispiel `We.Retail` -Anwendungen werden entfernt, wenn diese Instanz in ausgeführt wird [Produktionsbereiter Modus](/help/sites-administering/production-ready.md). Ist dies nicht der Fall, können Sie den Beispielinhalt deinstallieren, indem Sie Package Manager aufrufen und dann nach allen `We.Retail` Packages.

Siehe [Arbeiten mit Paketen](package-manager.md).

### Überprüfen Sie, ob die CRX-Entwicklungs-Bundles vorhanden sind. {#check-if-the-crx-development-bundles-are-present}

Diese Entwicklungs-OSGi-Pakete sollten sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor sie verfügbar gemacht werden.

* Adobe CRXDE-Unterstützung (com.adobe.granite.crxde-support)
* Adobe Granite CRX Explorer (com.adobe.granite.crx-explorer)
* Adobe Granite-CRXDE Lite (com.adobe.granite.crxde-lite)

### Überprüfen Sie, ob das Sling-Entwicklungsbundle vorhanden ist. {#check-if-the-sling-development-bundle-is-present}

Die [AEM Developer Tools](/help/sites-developing/aem-eclipse.md) stellen Sie die Installation der Apache Sling Tooling-Unterstützung bereit (org.apache.sling.tooling.support.install).

Dieses OSGi-Bundle sollte sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor sie verfügbar gemacht werden.

### Protect gegen Cross-Site Request Forgery {#protect-against-cross-site-request-forgery}

#### Das CSRF Protection Framework {#the-csrf-protection-framework}

AEM 6.1 verfügt über einen Mechanismus namens **CSRF Protection Framework**, der vor Cross-Site Request Forgery-Angriffen (Website-übergreifende Anfragenfälschung) schützt. Weitere Informationen zur Verwendungsweise finden Sie in der entsprechenden [Dokumentation](/help/sites-developing/csrf-protection.md).

#### Der Sling Referrer-Filter {#the-sling-referrer-filter}

Um bekannte Sicherheitsprobleme mit Cross-Site Request Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, fügen Sie Konfigurationen für den Referrer-Filter hinzu, um ihn zu verwenden.

Der Referrer-Filterdienst ist ein OSGi-Dienst, mit dem Sie Folgendes konfigurieren können:

* welche HTTP-Methoden gefiltert werden sollen
* Ob eine leere Referrer-Kopfzeile zulässig ist
* Eine Whitelist von Servern, die zusätzlich zum Serverhost zugelassen werden sollen.

   Standardmäßig sind alle Varianten von „localhost“ und die aktuellen Host-Namen, mit denen der Server verknüpft ist, in der Whitelist enthalten.

So konfigurieren Sie den Referrer-Filterdienst:

1. Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) unter:

   `https://<server>:<port_number>/system/console/configMgr`

1. Melden Sie sich als `admin` an.
1. Wählen Sie im Menü **Konfigurationen** folgende Option aus:

   `Apache Sling Referrer Filter`

1. Geben Sie im Feld `Allow Hosts` alle Hosts ein, die als Referrer zugelassen werden sollen. Jeder Eintrag muss im Formular enthalten sein.

   &lt;Protokoll>://&lt;Server>:&lt;Port>

   Beispiel:

   * `https://allowed.server:80`: Alle Anfragen von diesem Server mit dem angegebenen Port sind zugelassen.
   * Wenn Sie auch HTTPS-Anfragen zulassen wollen, müssen Sie eine zweite Zeile eingeben.
   * Wenn Sie alle Ports dieses Servers zulassen, können Sie `0` als Portnummer.

1. Aktivieren Sie das Feld `Allow Empty`, wenn Sie leere/fehlende Referrer-Kopfzeilen zulassen möchten.

   >[!CAUTION]
   >
   >Adobe empfiehlt, dass Sie einen Referrer bereitstellen, während Sie Befehlszeilen-Tools wie `cURL` anstatt einen leeren Wert zuzulassen, da dies Ihr System CSRF-Angriffen aussetzen könnte.

1. Bearbeiten Sie die Methoden, die dieser Filter für Prüfungen verwendet, mit dem `Filter Methods` -Feld.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### OSGi-Einstellungen {#osgi-settings}

Einige OSGi-Einstellungen sind standardmäßig festgelegt, um das Debugging der Anwendung zu erleichtern. Ändern Sie diese Einstellungen in Ihren Veröffentlichungs- und Autorenproduktionsinstanzen, um zu verhindern, dass interne Informationen an die Öffentlichkeit weitergegeben werden.

>[!NOTE]
>
>Alle unten aufgeführten Einstellungen mit Ausnahme von **Der Day CQ WCM Debug-Filter** werden automatisch von der [Produktionsbereiter Modus](/help/sites-administering/production-ready.md). Daher empfiehlt Adobe, alle Einstellungen zu überprüfen, bevor Sie Ihre Instanz in einer Produktionsumgebung bereitstellen.

Für jeden der folgenden Dienste müssen die angegebenen Einstellungen geändert werden:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * enable **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * enable **Gzip** (damit Dateien komprimiert und mit einer Anfrage aufgerufen werden können).
   * disable **Debuggen**
   * disable **Zeit**

* [Day CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter):

   * uncheck **Aktivieren**

* [Day CQ WCM-Filter](/help/sites-deploying/osgi-configuration-settings.md):

   * Legen Sie die Option **WCM-Modus** nur auf der Veröffentlichungsinstanz auf „Deaktiviert“ fest.

* [Apache Sling JavaScript Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * Deaktivieren Sie **die Funktion zum Erzeugen von Debug-Informationen**.

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * Deaktivieren Sie **Generate Debug Info**.
   * Deaktivieren Sie **Mapped Content**.

Siehe [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

Beim Arbeiten mit AEM gibt es mehrere Methoden zum Verwalten der Konfigurationseinstellungen für diese Dienste. see [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md) für weitere Details und empfohlene Vorgehensweisen.

## Weitere Informationen {#further-readings}

### Vermeiden von DoS-Angriffen (Denial of Service) {#mitigate-denial-of-service-dos-attacks}

Ein Denial-of-Service-Angriff (DoS) zielt darauf ab, eine Computer-Ressource für die vorgesehenen Benutzenden unzugänglich zu machen. Dieser Angriff erfolgt oft durch Überlastung der Ressource. Beispiel:

* Eine Flut von Anforderungen aus einer externen Quelle.
* Eine Anfrage nach mehr Informationen, als das System erfolgreich bereitstellen kann.

   Beispiel: Eine JSON-Darstellung des gesamten Repositorys.

* Wenn eine Seite mit einer unbegrenzten Anzahl an URLs angefordert wird, kann die URL einen Handler, einige Selektoren, eine Erweiterung und einen Suffix enthalten. Diese Elemente können alle geändert werden.

   So kann `.../en.html` angefordert werden als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

   Alle gültigen Varianten (z. B. `200` Antwort und sind so konfiguriert, dass sie zwischengespeichert werden) vom Dispatcher zwischengespeichert werden, was letztendlich zu einem vollständigen Dateisystem und zu keinem Dienst für weitere Anfragen führt.

Es gibt viele Konfigurationsmöglichkeiten, um solche Angriffe zu verhindern, aber nur die Punkte, die sich auf AEM beziehen, werden hier besprochen.

**Konfigurieren von Sling zum Verhindern von DoS**

Sling ist *content-centric*. Die Verarbeitung konzentriert sich auf den Inhalt, da jede (HTTP-)Anforderung in Form einer JCR-Ressource (eines Repository-Knotens) Inhalten zugeordnet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die den Inhalt enthält.
* Zweitens befindet sich der Renderer bzw. das Skript in den Ressourceneigenschaften mit bestimmten Teilen der Anforderung (z. B. Selektoren und/oder die Erweiterung).

Siehe [Verarbeitung von Sling-Anfragen](/help/sites-developing/the-basics.md#sling-request-processing) für weitere Informationen.

Dieser Ansatz macht Sling leistungsstark und flexibel, aber wie immer muss die Flexibilität sorgfältig verwaltet werden.

Um DoS-Missbrauch zu verhindern, können Sie Folgendes tun:

1. Einbinden von Steuerelementen auf Anwendungsebene. Aufgrund der möglichen Anzahl von Varianten ist eine Standardkonfiguration nicht möglich.

   In Ihrer Anwendung sollten Sie:

   * die Selektoren in der Anwendung steuern, sodass Sie *nur* die erforderlichen expliziten Selektoren verwenden und für alle anderen den Wert `404` zurückgeben.
   * Verhindern der Ausgabe einer unbegrenzten Anzahl von Inhaltsknoten.

1. Überprüfen Sie die Konfiguration der Standard-Renderer, was ein Problembereich sein kann.

   * Insbesondere überträgt der JSON-Renderer die Baumstruktur über mehrere Ebenen.

      Beispiel: Die Anfrage

      `http://localhost:4502/.json`

      könnte das gesamte Repository in einer JSON-Darstellung ablegen, was zu erheblichen Serverproblemen führen kann. Aus diesem Grund begrenzt Sling die Anzahl der maximalen Ergebnisse. Um die Tiefe des JSON-Renderings zu begrenzen, legen Sie den Wert für Folgendes fest:

      **Max. JSON-Ergebnisse** (`json.maximumresults`)

      in der Konfiguration für das [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet) festlegen. Wenn diese Grenze überschritten wird, wird das Rendering reduziert. Der Standardwert für Sling innerhalb von AEM ist `1000`.

   * Als vorbeugende Maßnahme sollten Sie die anderen Standard-Renderer deaktivieren (HTML, Nur-Text, XML). Auch hier wird die [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet).
   >[!CAUTION]
   >
   >Deaktivieren Sie den JSON-Renderer nicht, da er für den normalen AEM erforderlich ist.

1. Verwenden Sie eine Firewall, um den Zugriff auf Ihre Instanz zu filtern.

   * Die Verwendung einer Firewall auf Betriebssystemebene ist erforderlich, um den Zugriff auf Punkte Ihrer Instanz zu filtern, die zu Denial-of-Service-Angriffen führen können, wenn sie nicht geschützt bleiben.

**Abmildern von DoS mithilfe der Formularauswahl**

>[!NOTE]
>
>Diese Abmilderung sollte nur für AEM-Umgebungen durchgeführt werden, die keine Formulare verwenden.

Da AEM keine nativen Indizes für die `FormChooserServlet`, kann die Verwendung von Formularselektoren in Abfragen einen kostspieligen Repository-Durchlauf Trigger werden, der normalerweise die AEM-Instanz stoppt. Formularauswahl-Instanzen können anhand der Zeichenfolge **&amp;ast;.form.&amp;ast;** in Abfragen erkannt werden.

Um dieses Problem zu beheben, können Sie die folgenden Schritte ausführen:

1. Gehen Sie zur Web-Konsole, indem Sie im Browser *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr* aufrufen.

1. Suchen Sie nach **Day CQ WCM Form Chooser Servlet**.
1. Nachdem Sie auf den Eintrag geklickt haben, deaktivieren Sie die **Erweiterte Suche erforderlich** im folgenden Fenster.

1. Klicken Sie auf **Speichern**.

**Abmildern von DoS durch Asset Download Servlet**

Das standardmäßige Asset-Download-Servlet ermöglicht es authentifizierten Benutzern, beliebig große, gleichzeitige Download-Anfragen zum Erstellen von ZIP-Dateien von Assets zu stellen. Das Erstellen großer ZIP-Archive kann den Server und das Netzwerk überlasten. Um ein mögliches DoS-Risiko (Denial of Service) zu reduzieren, das durch dieses Verhalten verursacht wird, `AssetDownloadServlet`ist die OSGi-Komponente auf der [!DNL Experience Manager]-Veröffentlichungsinstanz standardmäßig deaktiviert. Auf der [!DNL Experience Manager]-Autoreninstanz ist sie standardmäßig aktiviert.

Wenn Sie die Download-Funktion nicht benötigen, deaktivieren Sie das Servlet in Autoren- und Veröffentlichungsbereitstellungen. Wenn Sie die Asset-Download-Funktion im Rahmen Ihrer Einrichtung aktivieren müssen, finden Sie weitere Informationen in [diesem Artikel](/help/assets/download-assets-from-aem.md). Sie können auch eine maximale Download-Grenze definieren, die Ihre Bereitstellung unterstützen kann.

### WebDAV deaktivieren {#disable-webdav}

Deaktivieren Sie WebDAV sowohl in der Autoren- als auch in der Veröffentlichungsumgebung, indem Sie die entsprechenden OSGi-Bundles anhalten.

1. Stellen Sie eine Verbindung zum **Felix Management Console** ausgeführt auf:

   `https://<*host*>:<*port*>/system/console`

   Beispiel: `http://localhost:4503/system/console/bundles`.

1. Suchen Sie in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Um dieses Bundle zu stoppen, klicken Sie in der Spalte Aktionen auf die Schaltfläche Stoppen .

1. Suchen Sie erneut in der Liste der Bundles das Bundle mit dem Namen:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Um dieses Bundle zu stoppen, klicken Sie auf die Schaltfläche &quot;Stopp&quot;.

   >[!NOTE]
   >
   >Ein Neustart von AEM ist nicht erforderlich.

### Sicherstellen, dass keine personenbezogenen Informationen im Home-Pfad von Benutzern offengelegt werden {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Es ist wichtig, Ihre Benutzer zu schützen, indem Sie sicherstellen, dass Sie keine persönlich identifizierbaren Informationen im Home-Pfad der Repository-Benutzer verfügbar machen.

Ab AEM 6.1 ändert sich mit der neuen Implementierung der Schnittstelle `AuthorizableNodeName` die Art, wie Benutzer-ID-Knotennamen (auch als autorisierbare ID-Knotennamen bezeichnet) gespeichert werden. Die neue Schnittstelle legt die Benutzer-ID nicht mehr im Knotennamen offen, sondern generiert stattdessen einen zufälligen Namen.

Es muss keine Konfiguration vorgenommen werden, um sie zu aktivieren, da sie jetzt die Standardmethode zum Generieren autorisierbarer IDs in AEM ist.

Obwohl dies nicht empfohlen wird, können Sie es deaktivieren, falls Sie die alte Implementierung aus Gründen der Abwärtskompatibilität mit Ihren vorhandenen Anwendungen benötigen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zur Web-Konsole und entfernen Sie den Eintrag **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** aus der Eigenschaft **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   Sie können den Oak Security Provider auch finden, indem Sie in den OSGi-Konfigurationen nach der PID **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** suchen.

1. Löschen Sie die OSGi-Konfiguration **Apache Jackrabbit Oak Random Authorizable Node Name** aus der Web-Konsole.

   Für eine einfachere Suche lautet die PID für diese Konfiguration: **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName**.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Oak-Dokumentation unter [Namenserstellung für autorisierbare Knoten](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

**Anonymes Berechtigungs-Härtungspaket**

Standardmäßig speichert AEM Systemmetadaten wie `jcr:createdBy` oder `jcr:lastModifiedBy` als Knoteneigenschaften neben regulärem Inhalt im Repository. Abhängig von der Konfiguration und der Einrichtung der Zugriffskontrolle kann dies in einigen Fällen zur Anzeige persönlich identifizierbarer Informationen (PII) führen, z. B. wenn solche Knoten als rohe JSON- oder XML-Dateien gerendert werden.

Wie alle Repository-Daten werden diese Eigenschaften durch den Oak-Autorisierungsstapel vermittelt. Der Zugang zu ihnen sollte gemäß dem Grundsatz des geringsten Vertrauens eingeschränkt werden.

Um dies zu unterstützen, bietet Adobe ein Berechtigungs-Härtungspaket als Grundlage für die Erstellung durch Kunden. Es funktioniert durch die Installation eines Zugriffssteuerungseintrags &quot;Verweigern&quot;im Repository-Stammverzeichnis, wodurch der anonyme Zugriff auf häufig verwendete Systemeigenschaften eingeschränkt wird. Das Paket kann heruntergeladen werden [here](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/helper/anonymous-permissions-pkg-0.1.2.zip) und kann in allen unterstützten Versionen von AEM installiert werden. Weitere Informationen finden Sie in den Versionshinweisen .

### Verhindern von Clickjacking {#prevent-clickjacking}

Um Clickjacking zu verhindern, empfiehlt Adobe, dass Sie Ihren Webserver so konfigurieren, dass `X-FRAME-OPTIONS` HTTP-Header auf `SAMEORIGIN`.

Weitere Informationen zu Clickjacking finden Sie unter [OWASP-Site](https://www.owasp.org/index.php/Clickjacking).

### Vergewissern Sie sich bei Bedarf, dass Sie Verschlüsselungsschlüssel ordnungsgemäß replizieren. {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bestimmte AEM Funktionen und Authentifizierungsschemas erfordern, dass Sie Ihre Verschlüsselungsschlüssel über alle AEM Instanzen hinweg replizieren.

Bevor Sie dies tun, erfolgt die Schlüsselreplikation in verschiedenen Versionen unterschiedlich, da die Art und Weise, wie Schlüssel gespeichert werden, zwischen 6.3 und älteren Versionen unterschiedlich ist.

Weitere Informationen finden Sie unten.

#### Replizieren von Schlüsseln für AEM 6.3 {#replicating-keys-for-aem}

Während in älteren Versionen die Replikationsschlüssel im Repository gespeichert wurden, ab AEM 6.3 werden sie im Dateisystem gespeichert.

Um Ihre Schlüssel über Instanzen hinweg zu replizieren, kopieren Sie sie daher von der Quellinstanz an den Speicherort der Zielinstanzen im Dateisystem.

Im Einzelnen müssen Sie Folgendes tun:

1. Greifen Sie auf die AEM -Instanz zu - normalerweise eine Autoreninstanz -, die das zu kopierende Schlüsselmaterial enthält.
1. Suchen Sie im lokalen Dateisystem das Bundle com.adobe.granite.crypto.file. Es kann sich z. B. unter diesem Pfad befinden:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   Die `bundle.info` -Datei in jedem Ordner identifiziert den Bundle-Namen.

1. Navigieren Sie zum Ordner „data“. Beispiel:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieren Sie die HMAC- und Übergeordneten Dateien.
1. Navigieren Sie dann zur Zielinstanz, auf der Sie den HMAC-Schlüssel duplizieren möchten, und dann zum Ordner „data“. Beispiel:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Fügen Sie die beiden zuvor kopierten Dateien ein.
1. [Aktualisieren Sie das Crypto-Bundle](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle), wenn die Zielinstanz bereits ausgeführt wird.
1. Wiederholen Sie die obigen Schritte für alle Instanzen, in denen Sie den Schlüssel replizieren möchten.

>[!NOTE]
>
>Sie können zur Methode zum Speichern von Schlüsseln vor Version 6.3 zurückkehren, indem Sie den folgenden Parameter bei der ersten Installation von AEM hinzufügen:
>
>`-Dcom.adobe.granite.crypto.file.disable=true`

#### Replizieren von Schlüsseln in AEM 6.2 und älteren Versionen {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 und älteren Versionen werden die Schlüssel im Repository im Knoten `/etc/key` gespeichert.

Die empfohlene Methode zur sicheren Replikation der Schlüssel in allen Ihren Instanzen besteht darin, nur diesen Knoten zu replizieren. Sie können Knoten selektiv über CRXDE Lite replizieren:

1. Öffnen von CRXDE Lite über *`https://&lt;serveraddress&gt;:4502/crx/de/index.jsp`*
1. Wählen Sie den `/etc/key`-Knoten aus.
1. Navigieren Sie zu **Replikation** Registerkarte.
1. Drücken Sie die **Replikation** Schaltfläche.

### Durchführen eines Penetrationstests {#perform-a-penetration-test}

Adobe empfiehlt, vor der Produktion einen Penetrationstest für Ihre AEM durchzuführen.

### Best Practices für die Entwicklung {#development-best-practices}

Es ist von entscheidender Bedeutung, dass die neue Entwicklung dem [Best Practices für die Sicherheit](/help/sites-developing/security.md) , um sicherzustellen, dass Ihre AEM-Umgebung sicher bleibt.
