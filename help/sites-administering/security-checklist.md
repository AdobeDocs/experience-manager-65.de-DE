---
title: Sicherheitscheckliste
description: Erfahren Sie mehr über die verschiedenen Sicherheitsüberlegungen beim Konfigurieren und Bereitstellen von AEM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 314a6409-398c-470b-8799-0c4e6f745141
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '2959'
ht-degree: 100%

---

# Sicherheitscheckliste {#security-checklist}

Dieser Abschnitt behandelt die verschiedenen Schritte, mit denen Sie sicherstellen können, dass Ihre AEM-Installation bei der Bereitstellung sicher ist. Die Checkliste ist so konzipiert, dass sie von oben nach unten abgearbeitet werden sollte.

>[!NOTE]
>
>Weitere Informationen zu den gefährlichsten Sicherheitsbedrohungen werden vom [Open Web Application Security Project (OWASP)](https://owasp.org/www-project-top-ten/) veröffentlicht.

>[!NOTE]
>
>Es gibt einige zusätzliche [Sicherheitsüberlegungen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations), die in der Entwicklungsphase berücksichtig werden müssen.

## Hauptsicherheitsmaßnahmen {#main-security-measures}

### Ausführen von AEM im produktionsbereiten Modus {#run-aem-in-production-ready-mode}

Weitere Informationen finden Sie unter [Ausführen von AEM im produktionsbereiten Modus](/help/sites-administering/production-ready.md).

### Aktivieren von HTTPS für Transport Layer Security {#enable-https-for-transport-layer-security}

Die Aktivierung der HTTPS-Transportschicht (Transport Layer) in den Autoren- und Veröffentlichungsinstanzen ist obligatorisch, um eine sichere Instanz zu erhalten.

>[!NOTE]
>
>Weitere Informationen finden Sie im Abschnitt [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### Installieren von Sicherheits-Hotfixes {#install-security-hotfixes}

Vergewissern Sie sich, dass Sie die neuesten [von Adobe bereitgestellten Sicherheits-Hotfixes](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=de) installiert haben.

### Ändern von Standardkennwörtern für AEM- und OSGi Console-Administratorkonten {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe empfiehlt dringend, dass Sie das Passwort für die mit allen Berechtigungen ausgestatteten [**AEM**-`admin`Konten](#changing-the-aem-admin-password) nach der Installation ändern (in allen Instanzen).

Diese Konten beinhalten:

* Das `admin`-Konto von AEM

  Sobald Sie das Passwort für das AEM-Admin-Konto geändert haben, müssen Sie für den Zugriff auf CRX das neue Passwort verwenden.

* Das `admin`-Passwort für die OSGi-Web-Konsole

  Diese Änderung wird auch für das Admin-Konto übernommen, das für den Zugriff auf die Web-Konsole verwendet wird. Daher müssen Sie dafür dasselbe Passwort verwenden.

Diese beiden Konten nutzen separate Kontoanmeldeinformationen und die Verwendung von unterschiedlichen sicheren Passwörtern für jedes Konto ist für eine sichere Bereitstellung von entscheidender Bedeutung.

#### Ändern des AEM-Administratorkennworts {#changing-the-aem-admin-password}

Das Kennwort für das AEM-Administratorkonto kann über die Konsole für [Granite-Vorgänge – Benutzer](/help/sites-administering/granite-user-group-admin.md) geändert werden.

Dort können Sie das `admin`-Konto bearbeiten und [das Kennwort ändern](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Durch das Ändern des Administratorkontos wird auch das OSGi-Web-Konsolenkonto geändert. Nachdem Sie das Administratorkonto geändert haben, sollten Sie das OSGi-Konto in etwas Anderes ändern.

#### Bedeutung der Änderung des Kennworts für die OSGi-Web-Konsole {#importance-of-changing-the-osgi-web-console-password}

Unabhängig vom `admin`-Konto von AEM kann eine Nichtänderung des Standardkennworts für die OSGi-Web-Konsole dazu führen, dass:

* Offenlegung des Servers mit einem Standardkennwort beim Start und beim Herunterfahren (was bei großen Servern mehrere Minuten dauern kann);
* Offenlegung des Servers, wenn das Repository heruntergefahren/ein Bundle neu gestartet wird – und OSGi ausgeführt wird.

Weitere Informationen zum Ändern des Kennworts für die Web-Konsole finden Sie unter [Ändern des Administratorkennworts der OSGi-Web-Konsole](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) unten.

#### Ändern des Administratorkennworts der OSGi-Web-Konsole {#changing-the-osgi-web-console-admin-password}

Ändern Sie das Passwort für den Zugriff auf die Web-Konsole. Dies geschieht mithilfe einer [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md), um die folgenden Eigenschaften der **Apache Felix OSGi Management Console** zu aktualisieren:

* **Benutzername** und **Kennwort**: die Anmeldeinformationen für den Zugriff auf die Apache Felix Web Management Console.
Das Kennwort muss *nach* der ersten Installation geändert werden, damit die Sicherheit Ihrer Instanz gewährleistet ist.

>[!NOTE]
>
>Siehe [OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md) für ausführliche Informationen zur Konfiguration der OSGi-Einstellungen.

**So ändern Sie das Administratorpasswort der OSGi-Web-Konsole**:

1. Öffnen Sie über das Menü **Tools**, **Vorgänge** die **Web-Konsole** und navigieren Sie zum Abschnitt **Konfiguration**.
Zum Beispiel unter `<server>:<port>/system/console/configMgr`.
1. Navigieren Sie zum Eintrag für die **Management-Konsole für Apache Felix OSGi** und öffnen Sie ihn.
1. Ändern Sie den **Benutzernamen** und das **Kennwort**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Wählen Sie **Speichern** aus.

### Implementieren eines benutzerdefinierten Fehler-Handlers {#implement-custom-error-handler}

Adobe empfiehlt, benutzerdefinierte Fehler-Handler-Seiten festzulegen, insbesondere für die HTTP-Antwort-Codes 404 und 500, um die Offenlegung von Informationen zu verhindern.

>[!NOTE]
>
>Weitere Details finden Sie im Artikel [Erstellen von benutzerdefinierten Skripten oder Fehler-Handlern](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/full-stack/custom-error-page.html?lang=de).

### Vollständige Dispatcher-Sicherheits-Checkliste {#complete-dispatcher-security-checklist}

AEM Dispatcher ist ein wichtiger Teil Ihrer Infrastruktur. Adobe empfiehlt dringend, dass Sie die [Dispatcher-Sicherheitscheckliste](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/security-checklist.html?lang=de) durchgehen.

>[!CAUTION]
>
>Mithilfe des Dispatchers müssen Sie den „.form“-Selektor deaktivieren.

## Überprüfungsschritte {#verification-steps}

### Konfigurieren von Replikations- und Transport-Benutzenden {#configure-replication-and-transport-users}

Bei einer Standardinstallation von AEM wird `admin` als Benutzer für die Transport-Anmeldedaten in den Standard-[Replikationsagenten](/help/sites-deploying/replication.md) angegeben. Außerdem werden Admin-Benutzende verwendet, um die Replikation auf dem Autorensystem zu beziehen.

Aus Sicherheitsgründen sollten beide geändert werden, um dem jeweiligen Anwendungsfall Rechnung zu tragen, wobei die beiden folgenden Aspekte zu berücksichtigen sind:

* **Transport-Benutzer** dürfen keine Admin-Benutzer sein. Richten Sie stattdessen einen Benutzer im Veröffentlichungssystem ein, der nur über Zugriffsrechte für die relevanten Teile des Veröffentlichungssystems verfügt, und verwenden Sie die Anmeldeinformationen dieses Benutzers für den Transport.

    Sie können mit dem gebündelten Benutzer „Replikations-Empfänger“ beginnen und die Zugriffsrechte dieses Benutzenden so konfigurieren, dass sie Ihren Anforderungen entsprechen.

* Der **Replikationsbenutzer** oder die **Agenten-Benutzer-ID** sollte auch nicht der Admin-Benutzer sein, sondern ein Benutzer, der nur replizierte Inhalte sehen kann. Der Replikationsbenutzende wird auch zum Erfassen von Inhalten verwendet, die auf dem Autorensystem repliziert werden sollen, bevor sie an den Publisher gesendet werden.

### Überprüfen der Sicherheitskonsistenzprüfungen im Vorgangs-Dashboard {#check-the-operations-dashboard-security-health-checks}

Mit AEM 6 wird das neue Vorgangs-Dashboard eingeführt, das Systembetreibenden bei der Fehlerbehebung und der Überwachung des Status einer Instanz helfen soll.

Das Dashboard enthält außerdem eine Sammlung von Sicherheitskonsistenzprüfungen. Es wird empfohlen, den Status aller Sicherheitskonsistenzprüfungen zu überprüfen, bevor Sie mit Ihrer Produktionsinstanz live gehen. Weitere Informationen dazu finden Sie in der [Dokumentation zum Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

### Überprüfen, ob Beispielinhalte vorhanden sind {#check-if-example-content-is-present}

Alle Beispielinhalte und -benutzer (z. B. das Geometrixx-Projekt und seine Komponenten) sollten deinstalliert und vollständig von einem Produktionssystem gelöscht sein, bevor es öffentlich zugänglich gemacht wird.

>[!NOTE]
>
>Die `We.Retail`-Beispielanwendungen werden entfernt, wenn diese Instanz im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) ausgeführt wird. Wenn dieses Szenario nicht zutrifft, können Sie den Beispielinhalt deinstallieren, indem Sie zum Package Manager navigieren und alle `We.Retail`-Pakete suchen und deinstallieren.

Siehe [Arbeiten mit Paketen](package-manager.md).

### Überprüfen, ob die CRX-Entwicklungs-Bundles vorhanden sind {#check-if-the-crx-development-bundles-are-present}

Diese Entwicklungs-OSGi-Bundles sollten sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor diese verfügbar gemacht werden.

* Adobe CRXDE-Unterstützung (com.adobe.granite.crxde-support)
* Adobe Granite CRX-Explorer (com.adobe.granite.crx-explorer)
* Adobe Granite CRXDE Lite (com.adobe.granite.crxde-lite)

### Überprüfen, ob das Sling-Entwicklungs-Bundle vorhanden ist {#check-if-the-sling-development-bundle-is-present}

[AEM Developer Tools](/help/sites-developing/aem-eclipse.md) stellt das Tool „Apache Sling Tooling Support Install“ (org.apache.sling.tooling.support.install) bereit.

Dieses OSGi-Bundle sollte sowohl auf Autoren- als auch auf Veröffentlichungs-Produktionssystemen deinstalliert werden, bevor sie verfügbar gemacht werden.

### Schutz vor Cross-Site Request-Forgery {#protect-against-cross-site-request-forgery}

#### Das CSRF Protection Framework {#the-csrf-protection-framework}

AEM 6.1 verfügt über einen Mechanismus namens **CSRF Protection Framework**, der vor Cross-Site Request Forgery-Angriffen (Website-übergreifende Anfragenfälschung) schützt. Weitere Informationen zur Verwendungsweise finden Sie in der entsprechenden [Dokumentation](/help/sites-developing/csrf-protection.md).

#### Der Sling Referrer-Filter {#the-sling-referrer-filter}

Um bekannte Sicherheitsprobleme mit Cross-Site Request-Forgery (CSRF) in CRX WebDAV und Apache Sling zu beheben, müssen Sie Konfigurationen für den Referrer-Filter hinzufügen, um ihn verwenden zu können.

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

1. Geben Sie im Feld `Allow Hosts` alle Hosts ein, die als Referrer zugelassen werden sollen. Jeder Eintrag muss folgendes Format aufweisen:

   &lt;Protokoll>://&lt;Server>:&lt;Port>

   Beispiel:

   * `https://allowed.server:80`: Alle Anfragen von diesem Server mit dem angegebenen Port sind zugelassen.
   * Wenn Sie auch HTTPS-Anfragen zulassen wollen, müssen Sie eine zweite Zeile eingeben.
   * Falls Sie alle Ports dieses Servers zulassen wollen, können Sie als Port-Nummer eine `0` eingeben.

1. Aktivieren Sie das Feld `Allow Empty`, wenn Sie leere/fehlende Referrer-Kopfzeilen zulassen möchten.

   >[!CAUTION]
   >
   >Wenn Sie Befehlszeilen-Tools wie `cURL` verwenden, wird empfohlen, einen Referrer anzugeben, anstatt einen leeren Wert zuzulassen, da andernfalls das Risiko besteht, dass Ihr System CSRF-Angriffen ausgesetzt ist.

1. Bearbeiten Sie die Methoden, die dieser Filter für Prüfungen verwenden soll, über das Feld `Filter Methods`.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### OSGi-Einstellungen {#osgi-settings}

Einige OSGi-Einstellungen sind standardmäßig festgelegt, um das Debugging der Anwendung zu erleichtern. Ändern Sie diese Einstellungen in Ihren Publishing- und Authoring-Produktionsinstanzen, um zu verhindern, dass interne Informationen an die Öffentlichkeit weitergegeben werden.

>[!NOTE]
>
>Alle folgenden Einstellungen, mit Ausnahme des **Day CQ WCM Debug-Filters**, werden automatisch im [produktionsbereiten Modus](/help/sites-administering/production-ready.md) angewendet. Aus diesem Grund wird empfohlen, alle Einstellungen zu überprüfen, bevor Sie Ihre Instanz in einer Produktionsumgebung bereitstellen.

Sie müssen für jeden der folgenden Dienste die angegebenen Einstellungen ändern:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * Aktivieren Sie **Minimieren** (um CRLF- und Leerzeichen zu entfernen).
   * Aktivieren Sie **gzip** (damit Dateien ins gzip-Format komprimiert und mit einer Anfrage aufgerufen werden können).
   * Deaktivieren Sie **Debuggen**.
   * Deaktivieren Sie **Zeitplanung**.

* [Day CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter):

   * Entfernen Sie den Haken bei **Aktivieren**.

* [Day CQ WCM-Filter](/help/sites-deploying/osgi-configuration-settings.md):

   * Legen Sie die Option **WCM-Modus** nur auf der Veröffentlichungsinstanz auf „Deaktiviert“ fest.

* [Apache Sling JavaScript Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * Deaktivieren Sie **die Funktion zum Erzeugen von Debug-Informationen**.

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * Deaktivieren Sie **Generate Debug Info**.
   * Deaktivieren Sie **Mapped Content**.

Weitere Informationen finden Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

## Weitere Informationen {#further-readings}

### Vermeiden von Denial-of-Service (DoS)-Angriffen {#mitigate-denial-of-service-dos-attacks}

Ein Denial-of-Service-Angriff (DoS) zielt darauf ab, eine Computer-Ressource für die vorgesehenen Benutzenden unzugänglich zu machen. Dies geschieht häufig, indem die Ressource überlastet wird, zum Beispiel:

* durch eine Flut von Anfragen von einer externen Quelle;
* durch eine Anforderung von mehr Informationen, als das System erfolgreich bereitstellen kann.

  Beispiel: Eine JSON-Darstellung des gesamten Repositorys.

* Wenn eine Seite mit einer unbegrenzten Anzahl an URLs angefordert wird, kann die URL einen Handler, einige Selektoren, eine Erweiterung und einen Suffix enthalten. Diese Elemente können alle geändert werden.

  So kann `.../en.html` angefordert werden als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

  Alle gültigen Varianten (geben z. B. die Antwort `200` zurück und werden zur Zwischenspeicherung konfiguriert) werden vom Dispatcher zwischengespeichert, was letztendlich zu einem vollen Dateisystem führt, sodass kein Dienst für weitere Anfragen verfügbar ist.

Es gibt viele Konfigurationsmöglichkeiten, um solche Angriffe zu verhindern. Hier gehen wir jedoch nur auf die ein, die direkt für AEM relevant sind.

**Konfigurieren von Sling zum Verhindern von DoS**

Sling ist *inhaltzentriert*. Dies bedeutet, dass sich die Verarbeitung auf den Inhalt konzentriert, da jede (HTTP-)Anfrage Inhalten in Form einer JCR-Ressource (eines Repository-Knotens) zugeordnet wird:

* Das erste Ziel ist die Ressource (JCR-Knoten), die die Inhalte enthält.
* Zweitens wird der Renderer (oder das Skript) aus den Ressourceneigenschaften in Kombination mit bestimmten Teilen der Anfrage (z. B. Selektoren und/oder der Erweiterung) ermittelt

Weitere Einzelheiten hierzu finden Sie unter [Verarbeitung von Sling-Anfragen](/help/sites-developing/the-basics.md#sling-request-processing).

Durch diesen Ansatz wird Sling zu einem leistungsstarken und flexiblen Tool, aber wie immer muss mit der Flexibilität sorgfältig umgegangen werden.

So verhindern Sie einen Missbrauch infolge von DoS-Angriffen:

1. Binden Sie Kontrollen auf Anwendungsebene ein. Aufgrund der Anzahl der möglichen Varianten ist eine Standardkonfiguration nicht praktikabel.

   In Ihrem Programm sollten Sie Folgendes tun:

   * die Selektoren in der Anwendung steuern, sodass Sie *nur* die erforderlichen expliziten Selektoren verwenden und für alle anderen den Wert `404` zurückgeben.
   * Verhindern Sie die Ausgabe einer unbegrenzten Anzahl von Inhaltsknoten.

1. Überprüfen Sie die Konfiguration der Standard-Renderer, was ein Problembereich sein kann.

   * Insbesondere der JSON-Renderer, der die Baumstruktur über mehrere Ebenen hinweg durchlaufen kann.

     Beispiel: Die Anfrage

     `http://localhost:4502/.json`

     könnte das gesamte Repository in einer JSON-Darstellung abbilden, was zu erheblichen Server-Problemen führen kann. Aus diesem Grund legt Sling eine Begrenzung für die maximale Anzahl der Ergebnisse fest. Um die Tiefe des JSON-Renderings zu begrenzen, können Sie den Wert für

     **Max. JSON-Ergebnisse** (`json.maximumresults`)

     in der Konfiguration für das [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet) festlegen. Wenn dieser Grenzwert überschritten wird, wird das Rendering abgebrochen. Der Standardwert für Sling innerhalb von AEM ist `1000`.

   * Deaktivieren Sie als vorbeugende Maßnahme die anderen Standard-Renderer (HTML, einfacher Text, XML). Dies erreichen Sie erneut, indem Sie das [Apache Sling-GET-Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet) konfigurieren.

   >[!CAUTION]
   >
   >Deaktivieren Sie nicht den JSON-Renderer, denn dieser ist für den normalen Betrieb von AEM erforderlich.

1. Verwenden Sie eine Firewall, um den Zugriff auf Ihre Instanz zu filtern.

   * Die Verwendung einer Firewall auf Betriebssystemebene ist erforderlich, um den Zugriff auf Punkte Ihrer Instanz zu filtern, die zu Denial-of-Service-Angriffen führen können, wenn sie ungeschützt bleiben.

**Abmildern von DoS mithilfe der Formularauswahl**

>[!NOTE]
>
>Diese Abmilderung sollte nur für AEM-Umgebungen durchgeführt werden, die keine Formulare verwenden.

Da AEM keine vorkonfigurierten Indizes für `FormChooserServlet` bereitstellt, löst die Verwendung der Formularauswahl in Abfragen einen aufwändigen Repository-Durchlauf aus, der meist die AEM-Instanz zum Stoppen bringt. Formularauswahl-Instanzen können anhand der Zeichenfolge **&amp;ast;.form.&amp;ast;** in Abfragen erkannt werden.

Um dieses Problem abzumildern, können Sie die folgenden Schritte durchführen:

1. Gehen Sie zur Web-Konsole, indem Sie im Browser *https://&lt;Server-Adresse>:&lt;Serverport>/system/console/configMgr* aufrufen.

1. Suchen Sie nach **Day CQ WCM Form Chooser Servlet**.
1. Klicken Sie auf den Eintrag und deaktivieren Sie im folgenden Fenster die Option **Advanced Search Require** (Erweiterte Suche erforderlich).

1. Klicken Sie auf **Speichern**.

**Schützen gegen durch Asset-Download-Servlets ausgelöste DoS**

Das standardmäßige Asset-Download-Servlet ermöglicht es authentifizierten Benutzerinnen und Benutzern, beliebig große, gleichzeitige Download-Anfragen zur Erstellung von ZIP-Dateien von Assets zu stellen. Das Erstellen großer ZIP-Archive kann den Server und das Netzwerk überlasten. Um ein mögliches DoS-Risiko (Denial of Service) zu reduzieren, das durch dieses Verhalten verursacht wird, `AssetDownloadServlet`ist die OSGi-Komponente auf der [!DNL Experience Manager]-Veröffentlichungsinstanz standardmäßig deaktiviert. Auf der [!DNL Experience Manager]-Autoreninstanz ist sie standardmäßig aktiviert.

Wenn Sie die Download-Funktion nicht benötigen, deaktivieren Sie das Servlet auf Authoring- und Publishing-Bereitstellungen. Wenn Sie die Asset-Download-Funktion im Rahmen Ihrer Einrichtung aktivieren müssen, finden Sie weitere Informationen in [diesem Artikel](/help/assets/download-assets-from-aem.md). Sie können auch eine maximale Download-Grenze definieren, die Ihre Bereitstellung unterstützen kann.

### Deaktivieren von WebDAV {#disable-webdav}

WebDAV sollte sowohl in der Authoring- als auch in der Publishing-Umgebung deaktiviert sein. Dies kann durch Anhalten der entsprechenden OSGi-Bundles erfolgen.

1. Stellen Sie eine Verbindung zur **Felix-Management-Konsole** her, ausgeführt unter:

   `https://<*host*>:<*port*>/system/console`

   Beispiel: `http://localhost:4503/system/console/bundles`.

1. Suchen Sie in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Klicken Sie in der Spalte „Aktionen“ auf die Schaltfläche „Anhalten“, um dieses Bundle anzuhalten.

1. Suchen Sie in der Liste der Bundles nach einem Bundle mit dem folgenden Namen:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Klicken Sie auf den Button „Anhalten“, um dieses Bundle anzuhalten.

   >[!NOTE]
   >
   >Ein Neustart von AEM ist nicht erforderlich.

### Sicherstellen, dass keine personenbezogenen Informationen im Home-Pfad von Benutzern offengelegt werden {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Es ist wichtig, dass Sie Ihre Benutzer bzw. Benutzerinnen schützen, indem Sie sicherstellen, dass Sie keine persönlich identifizierbaren Informationen im Home-Pfad der Repository-Benutzer bzw. -Benutzerinnen bereitstellen.

Ab AEM 6.1 ändert sich mit der neuen Implementierung der Schnittstelle `AuthorizableNodeName` die Art, wie Benutzer-ID-Knotennamen (auch als autorisierbare ID-Knotennamen bezeichnet) gespeichert werden. Die neue Benutzeroberfläche gibt die Benutzer-ID nicht mehr im Knotennamen aus, sondern generiert stattdessen einen Zufallsnamen.

Es muss keine Konfiguration vorgenommen werden, um sie zu aktivieren, da dies nun die Standardmethode zur Erzeugung autorisierbarer IDs in AEM ist.

Obwohl es nicht empfohlen wird, können Sie dies deaktivieren, falls Sie die alte Implementierung aus Gründen der Abwärtskompatibilität mit Ihren vorhandenen Anwendungen benötigen. Gehen Sie dazu wie folgt vor:

1. Navigieren Sie zur Web-Konsole und entfernen Sie den Eintrag **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** aus der Eigenschaft **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   Sie können den Oak Security Provider auch finden, indem Sie in den OSGi-Konfigurationen nach der PID **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** suchen.

1. Löschen Sie die OSGi-Konfiguration **Apache Jackrabbit Oak Random Authorizable Node Name** aus der Web-Konsole.

   Um die Suche zu vereinfachen, beachten Sie, dass die PID für diese Konfiguration **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** lautet.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Oak-Dokumentation unter [Namenserstellung für autorisierbare Knoten](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Paket für anonyme Berechtigungs-Härtung {#anonymous-permission-hardening-package}

Standardmäßig speichert AEM Systemmetadaten wie `jcr:createdBy` oder `jcr:lastModifiedBy` als Knoteneigenschaften neben regulären Inhalten im Repository. Abhängig von der Konfiguration und der Einrichtung der Zugriffssteuerung kann dies in einigen Fällen zur Offenlegung personenbezogener Daten führen, z. B. wenn solche Knoten als rohe JSON- oder XML-Dateien gerendert werden.

Wie alle Repository-Daten werden diese Eigenschaften durch den Oak-Autorisierungs-Stapel vermittelt. Der Zugriff auf sie sollte gemäß dem Grundsatz der geringsten Rechte eingeschränkt werden.

Adobe bietet ein Paket zur Berechtigungs-Härtung als Grundlage, um Kunden dabei zu unterstützen, hierauf aufzubauen. Es funktioniert durch die Installation eines Zugriffssteuerungseintrags „Verweigern“ im Repository-Stammverzeichnis, wodurch der anonyme Zugriff auf häufig verwendete Systemeigenschaften eingeschränkt wird. Das Paket kann [hier](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/helper/anonymous-permissions-pkg-0.1.2.zip) heruntergeladen werden und kann in allen unterstützten Versionen von AEM installiert werden.

Um die Änderungen zu veranschaulichen, können wir die Knoteneigenschaften, die vor der Installation des Pakets anonym angezeigt werden können:

![Vor der Installation des Pakets](/help/sites-administering/assets/before_resized.png)

mit den Optionen vergleichen, die nach der Installation des Pakets angezeigt werden können, wobei `jcr:createdBy` und `jcr:lastModifiedBy` nicht sichtbar sind:

![Nach der Installation des Pakets](/help/sites-administering/assets/after_resized.png)

Weitere Informationen finden Sie in den Versionshinweisen zu Paketen.

### Verhindern von Clickjacking {#prevent-clickjacking}

Um Clickjacking zu verhindern, sollten Sie Ihren Webserver so konfigurieren, dass er den HTTP-Header `X-FRAME-OPTIONS` bereitstellt, der auf `SAMEORIGIN` festgelegt ist.

Weitere Informationen zum Thema Clickjacking finden Sie auf der [OWASP-Website](https://www.owasp.org/index.php/Clickjacking).

### Achten Sie bei Bedarf darauf, dass Verschlüsselungsschlüssel ordnungsgemäß repliziert werden. {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bestimmte AEM-Funktionen und Authentifizierungsschemata erfordern, dass Sie Ihre Verschlüsselungsschlüssel über alle AEM-Instanzen hinweg replizieren.

Beachten Sie zunächst, dass die Schlüsselreplikation zwischen verschiedenen Versionen unterschiedlich ausgeführt wird, da die Art und Weise, in der Schlüssel in 6.3 gespeichert werden, von älteren Versionen abweicht.

Nachfolgenden finden Sie weitere Informationen.

#### Replizieren von Schlüsseln für AEM 6.3 {#replicating-keys-for-aem}

Während in älteren Versionen die Replikationsschlüssel im Repository gespeichert wurden, werden sie ab AEM 6.3 im Dateisystem gespeichert.

Um Ihre Schlüssel über Instanzen hinweg zu replizieren, müssen Sie sie daher von der Quellinstanz an den Speicherort der Zielinstanzen im Dateisystem kopieren.

Im Einzelnen müssen Sie Folgendes tun:

1. Greifen Sie auf die AEM-Instanz zu, auf der sich die zu kopierenden Schlüsseldaten befinden. In der Regel handelt es sich dabei um eine Authoring-Instanz.
1. Suchen Sie im lokalen Dateisystem das Bundle com.adobe.granite.crypto.file. Es kann sich z. B. unter diesem Pfad befinden:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   Die in jedem Ordner befindliche Datei `bundle.info` identifiziert den Bundle-Namen.

1. Navigieren Sie zum Ordner „data“. Beispiel:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. die HMAC- und Master-Dateien kopieren.
1. Navigieren Sie dann zur Zielinstanz, auf der Sie den HMAC-Schlüssel duplizieren möchten, und dann zum Ordner „data“. Beispiel:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Fügen Sie die beiden zuvor kopierten Dateien ein.
1. [Aktualisieren Sie das Crypto-Bundle](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle), wenn die Zielinstanz bereits ausgeführt wird.
1. Wiederholen Sie die vorherigen Schritte für alle Instanzen, zu denen Sie den Schlüssel replizieren möchten.

#### Replizieren von Schlüsseln in AEM 6.2 und älteren Versionen {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 und älteren Versionen werden die Schlüssel im Repository im Knoten `/etc/key` gespeichert.

Die empfohlene Methode zur sicheren Replikation der Schlüssel in allen Ihren Instanzen besteht darin, nur diesen Knoten zu replizieren. Sie können Knoten selektiv über CRXDE Lite replizieren:

1. Öffnen von CRXDE Lite über *`https://&lt;serveraddress&gt;:4502/crx/de/index.jsp`*
1. Wählen Sie den `/etc/key`-Knoten aus.
1. Wechseln Sie zur Registerkarte **Replikation**.
1. Klicken Sie auf die Schaltfläche **Replikation**.

### Durchführen eines Penetrationstests {#perform-a-penetration-test}

Adobe empfiehlt dringend, Ihre AEM-Infrastruktur vor dem Einsatz in einer Produktionsumgebung einem Penetrationstest zu unterziehen.

### Best Practices für die Entwicklung {#development-best-practices}

Es ist von kritischer Bedeutung, dass die neue Entwicklung den [Best Practices für die Sicherheit](/help/sites-developing/security.md) entsprechen, um zu gewährleisten, dass Ihre AEM-Umgebung sicher bleibt.
