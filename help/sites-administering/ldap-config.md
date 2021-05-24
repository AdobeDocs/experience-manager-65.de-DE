---
title: Konfigurieren von LDAP mit AEM 6
seo-title: Konfigurieren von LDAP mit AEM 6
description: Erfahren Sie, wie Sie LDAP mit AEM konfigurieren.
seo-description: Erfahren Sie, wie Sie LDAP mit AEM konfigurieren.
uuid: 0007def4-86f0-401d-aa37-c8d49d5acea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 5faf6ee5-9242-48f4-87a8-ada887a3be1e
exl-id: 2ebca4fb-20f7-499c-96a0-4018eaeddc1a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1661'
ht-degree: 68%

---

# Konfigurieren von LDAP mit AEM 6  {#configuring-ldap-with-aem}

LDAP (**L** ightweight **D** irectory **A** ccess **P** rotocol) dient dem Zugriff auf zentrale Verzeichnisdienste. Hierdurch wird der Verwaltungsaufwand für Benutzerkonten reduziert, da auf sie über mehrere Anwendungen zugegriffen werden kann. Ein solcher LDAP-Server ist Active Directory. LDAP wird häufig für Single-Sign-On-Szenarien eingesetzt, durch die ein Benutzer mit einer Anmeldung auf mehrere Anwendungen zugreifen kann.

Benutzerkonten können zwischen dem LDAP-Server und dem Repository synchronisiert werden, wobei die LDAP-Kontodetails im Repository gespeichert werden. Hierdurch ist es möglich, Konten Repository-Gruppen zuzuordnen, um die erforderlichen Berechtigungen und Rechte zuzuweisen.

Das Repository nutzt die LDAP-Authentifizierung zum Authentifizieren solcher Benutzer. Dabei werden die Anmeldeinformationen zur Validierung an den LDAP-Server weitergegeben. Dies ist erforderlich, um Zugriff auf das Repository zu gewähren. Zur Leistungsverbesserung können erfolgreich validierte Anmeldeinformationen vom Repository zwischengespeichert werden. Über ein Ablauftimeout wird dann sichergestellt, dass nach einem angemessenen Zeitraum eine erneute Validierung erfolgt.

Wenn ein Konto vom LDAP-Server entfernt wird, ist keine Validierung mehr möglich, sodass der Zugriff auf das Repository abgelehnt wird. Details zu den im Repository gespeicherten LDAP-Konten können auch gelöscht werden.

Die Verwendung solcher Konten ist für Ihre Benutzer transparent. Sie erkennen keinen Unterschied zwischen Benutzer- und Gruppenkonten auf LDAP-Basis und denen, die ausschließlich im Repository erstellt wurden.

In AEM 6 umfasst die LDAP-Unterstützung eine neue Implementierung, für die im Vergleich zu früheren Versionen ein anderer Konfigurationstyp erforderlich ist.

Alle LDAP-Konfigurationen sind jetzt als OSGi-Konfigurationen verfügbar. Sie können über die Web-Management-Konsole konfiguriert werden unter:
`https://serveraddress:4502/system/console/configMgr`

Damit LDAP mit AEM verwendet werden kann, müssen Sie drei OSGi-Konfigurationen erstellen:

1. einen LDAP-Identitäts-Provider (IDP),
1. einen Synchroniserungshandler und
1. ein externes Anmeldemodul.

>[!NOTE]
>
>Sehen Sie sich das Tutorial [Oak&#39;s External Login Module – Authenticating with LDAP and Beyond](https://docs.adobe.com/content/ddc/en/gems/oak-s-external-login-module---authenticating-with-ldap-and-beyon.html#) an, um sich ausführlich über externe Anmeldemodule zu informieren.
>
>Weitere Informationen zum Konfigurieren von Experience Manager mit Apache DS finden Sie unter [Konfigurieren von Adobe Experience Manager 6.5 für Apache Directory Service](https://helpx.adobe.com/de/experience-manager/using/configuring-aem64-apache-directory-service.html).

## Konfigurieren des LDAP-Identitäts-Providers {#configuring-the-ldap-identity-provider}

Über den LDAP-Identitäts-Provider wird definiert, wie Benutzer vom LDAP-Server abgerufen werden.

Sie finden ihn in der Verwaltungskonsole unter dem Namen **Apache Jackrabbit Oak LDAP Identity Provider**.

Die folgenden Konfigurationsoptionen sind für den LDAP-Identitäts-Provider verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>LDAP-Anbietername</strong></td>
   <td>Name dieser LDAP-Provider-Konfiguration.</td>
  </tr>
  <tr>
   <td><strong>LDAP-Server-Hostname</strong><br /> </td>
   <td>Hostname des LDAP-Servers</td>
  </tr>
  <tr>
   <td><strong>LDAP-Server-Anschluss</strong></td>
   <td>Anschluss des LDAP-Servers</td>
  </tr>
  <tr>
   <td><strong>SSL verwenden</strong></td>
   <td>Gibt an, ob eine SSL-Verbindung (LDAPs) verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Verwenden von TLS</strong></td>
   <td>Gibt an, ob TLS bei Verbindungen gestartet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Zertifikatüberprüfung deaktivieren</strong></td>
   <td>Gibt an, ob die Validierung des Serverzertifikats deaktiviert werden soll.</td>
  </tr>
  <tr>
   <td><strong>Bindungs-DN</strong></td>
   <td>DN des Benutzers für die Authentifizierung. Ohne Angabe erfolgt eine anonyme Bindung.</td>
  </tr>
  <tr>
   <td><strong>Bindungskennwort</strong></td>
   <td>Kennwort des Benutzers für die Authentifizierung</td>
  </tr>
  <tr>
   <td><strong>Zeitüberschreitung der Suche</strong></td>
   <td>Zeit bis zum Timeout einer Suche</td>
  </tr>
  <tr>
   <td><strong>Maximaler Admin-Pool aktiv</strong></td>
   <td>Die maximale aktive Größe des Admin-Verbindungspools.</td>
  </tr>
  <tr>
   <td><strong>Maximale Anzahl aktiver Benutzer-Pool</strong></td>
   <td>Die maximale aktive Größe des Benutzerverbindungspools.</td>
  </tr>
  <tr>
   <td><strong>Benutzerdefinierter DN</strong></td>
   <td>Der DN für Benutzersuchen</td>
  </tr>
  <tr>
   <td><strong>Benutzerobjektklassen</strong></td>
   <td>Die Liste der Objektklassen, die ein Benutzereintrag enthalten muss.</td>
  </tr>
  <tr>
   <td><strong>Benutzer-ID-Attribut</strong></td>
   <td>Name des Attributs, das die Benutzer-ID enthält.</td>
  </tr>
  <tr>
   <td><strong>Zusätzlicher Filter für Benutzer</strong></td>
   <td>Zusätzlicher LDAP-Filter zur Verwendung bei der Suche nach Benutzern. Der endgültige Filter ist wie folgt formatiert: '(&amp;(&lt;idAttr&gt;=&lt;userId&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)' (user.extraFilter)</td>
  </tr>
  <tr>
   <td><strong>Benutzer-DN-Pfade</strong></td>
   <td>Steuert, ob der DN zur Berechnung eines Teils des Zwischenpfads verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Group base DN</strong></td>
   <td>Der Basis-DN für Gruppensuchen.</td>
  </tr>
  <tr>
   <td><strong>Gruppenobjektklassen</strong></td>
   <td>Die Liste der Objektklassen, die ein Gruppeneintrag enthalten muss.</td>
  </tr>
  <tr>
   <td><strong>Group name attribute</strong></td>
   <td>Name des Attributs, das den Gruppennamen enthält.</td>
  </tr>
  <tr>
   <td><strong>Zusätzlichen Filter gruppieren</strong></td>
   <td>Zusätzlicher LDAP-Filter zur Verwendung bei der Suche nach Gruppen. Der endgültige Filter ist wie folgt formatiert: '(&amp;(&lt;nameAttr&gt;=&lt;groupName&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)'</td>
  </tr>
  <tr>
   <td><strong>Gruppen-DN-Pfade</strong></td>
   <td>Steuert, ob der DN zur Berechnung eines Teils des Zwischenpfads verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Group member attribute</strong></td>
   <td>Gruppenattribut, das die Mitglieder einer Gruppe enthält.</td>
  </tr>
 </tbody>
</table>

## Konfigurieren des Synchronisierungshandlers {#configuring-the-synchronization-handler}

Der Synchronisierungshandler definiert, wie die Benutzer und Gruppen des Identitäts-Providers mit dem Repository synchronisiert werden.

Sie finden ihn in der Verwaltungskonsole unter dem Namen **Apache Jackrabbit Oak Default Sync Handler**.

Die folgenden Konfigurationsoptionen sind für den Synchronisierungshandler verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Sync Handler Name</strong></td>
   <td>Name der Synchronisierungskonfiguration.</td>
  </tr>
  <tr>
   <td><strong>User Expiration Time</strong></td>
   <td>Dauer, bis ein synchronisierter Benutzer abgelaufen ist.</td>
  </tr>
  <tr>
   <td><strong>Automatische Benutzermitgliedschaft</strong></td>
   <td>Liste der Gruppen, denen ein synchronisierter Benutzer automatisch hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><strong>User property mapping</strong></td>
   <td>Definition des Listen-Mappings für lokale Eigenschaften von externen.</td>
  </tr>
  <tr>
   <td><strong>Benutzerpfadpräfix</strong></td>
   <td>Das beim Erstellen neuer Benutzer verwendete Pfadpräfix.</td>
  </tr>
  <tr>
   <td><strong>Ablauf der Benutzermitgliedschaft</strong></td>
   <td>Zeitpunkt, nach dem die Mitgliedschaft abläuft.<br /> </td>
  </tr>
  <tr>
   <td><strong>User membership nesting depth</strong></td>
   <td>Gibt die maximale Tiefe der Gruppenverschachtelung zurück, wenn Mitgliedschaftsbeziehungen synchronisiert werden. Mit dem Wert „0“ wird die Suche nach Gruppenmitgliedschaften deaktiviert. Mit dem Wert „1“ werden nur die direkten Gruppen eines Benutzers hinzugefügt. Dieser Wert hat keinerlei Wirkung, wenn beim Synchronisieren der mitgliedsbezogenen Herkunft eines Benutzers nur einzelne Gruppen synchronisiert werden.</td>
  </tr>
  <tr>
   <td><strong>Group Expiration Time</strong></td>
   <td>Dauer, bis eine synchronisierte Gruppe abläuft.</td>
  </tr>
  <tr>
   <td><strong>Gruppenauto-Mitgliedschaft</strong></td>
   <td>Liste der Gruppen, denen automatisch eine synchronisierte Gruppe hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><strong>Gruppeneigenschaftszuordnung</strong></td>
   <td>Definition des Listen-Mappings für lokale Eigenschaften von externen.</td>
  </tr>
  <tr>
   <td><strong>Group path prefix</strong></td>
   <td>Das beim Erstellen neuer Gruppen verwendete Pfadpräfix.</td>
  </tr>
 </tbody>
</table>

## Externes Anmeldemodul {#the-external-login-module}

Sie finden das externe Anmeldemodul in der Verwaltungskonsole unter dem Namen **Apache Jackrabbit Oak External Login Module**.

>[!NOTE]
>
>Das Apache Jackrabbit Oak External Login Module implementiert die JAAS-Spezifikationen (Java Authentication and Authorization Service). Weitere Informationen finden Sie im [offiziellen Oracle Java-Sicherheitshandbuch](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html).

Seine Aufgabe besteht in der Definition des zu verwendenden Identitäts-Providers und Synchronisierungshandlers, wodurch die beiden Module miteinander verbunden werden.

Die folgenden Konfigurationsoptionen sind verfügbar:

| **JAAS Ranking** | Angabe des Rangs (d. h. der Sortierreihenfolge) dieses Anmeldemoduleintrags. Die Einträge sind in absteigender Reihenfolge sortiert (d. h., höher bewertete Konfigurationen werden zuerst aufgeführt). |
|---|---|
| **JAAS Control Flag** | Eigenschaft, die angibt, ob ein LoginModule erforderlich, REQUISITE, SUFFICIENT oder OPTIONAL ist. Weitere Informationen zur Bedeutung dieser Flags finden Sie in der JAAS-Konfigurationsdokumentation. |
| **JAAS Realm** | Der Bereichsname (oder Anwendungsname), mit dem das LoginModule registriert wird. Ohne Angabe eines Bereichsnamens wird das Anmeldemodul mit einem Standardbereich registriert, wie in der Felix JAAS-Konfiguration konfiguriert. |
| **Identity Provider Name** | Name des Identitäts-Providers. |
| **Sync Handler Name** | Name des Synchronisierungs-Handlers. |

>[!NOTE]
>
>Wenn für Ihre AEM-Instanz mehr als eine LDAP-Konfiguration vorgesehen ist, müssen Sie für jede Konfiguration separate Identitäts-Provider und Synchronisierungshandler erstellen.

## Konfigurieren von LDAP über SSL {#configure-ldap-over-ssl}

AEM 6 kann so konfiguriert werden, dass eine LDAP-Authentifizierung über SSL erfolgt. Gehen Sie hierzu wie folgt vor:

1. Aktivieren Sie die Kontrollkästchen **Use SSL** oder **Use TLS**, wenn Sie den [LDAP-Identitäts-Provider](#configuring-the-ldap-identity-provider) konfigurieren.
1. Konfigurieren Sie den Synchronisierungshandler und das externe Anmeldemodul gemäß Setup.
1. Installieren Sie ggf. die SSL-Zertifikate auf Ihrer virtuellen Java-Maschine. Hierzu kann das Keytool verwendet werden:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Testen Sie die Verbindung zum LDAP-Server.

### Erstellen von SSL-Zertifikaten  {#creating-ssl-certificates}

Über selbstsignierte Zertifikate kann AEM so konfiguriert werden, dass eine LDAP-Authentifizierung über SSL erfolgt. Im Folgenden finden Sie ein Beispielverfahren zum Generieren von Zertifikaten für AEM.

1. Vergewissern Sie sich, dass eine funktionstüchtige SSL-Bibliothek installiert ist. Bei dieser Vorgehensweise wird beispielhaft OpenSSL verwendet.

1. Erstellen Sie eine benutzerdefinierte OpenSSL-Konfigurationsdatei (.cnf). Kopieren Sie dazu die standardmäßige Konfigurationsdatei **openssl.cnf**und passen Sie sie an. Auf UNIX-Systemen befindet er sich normalerweise unter `/usr/lib/ssl/openssl.cnf`

1. Erstellen Sie dann den Zertifizierungsstellen-Stammschlüssel, indem Sie den nachfolgenden Befehl an einem Terminal ausführen:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option]
   ```

1. Erstellen Sie als Nächstes ein selbstsigniertes Zertifikat:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Überprüfen Sie das neu generierte Zertifikat, um seine Ordnungsmäßigkeit sicherzustellen:

   `openssl x509 -noout -text -in root-ca.crt`

1. Vergewissern Sie sich, dass alle in der Konfigurationsdatei des Zertifikats (.cnf) angegebenen Ordner vorhanden sind. Ist dies nicht der Fall, erstellen Sie diese.
1. Erstellen Sie einen zufälligen Ausgangswert, indem Sie beispielsweise Folgendes ausführen:

   `openssl rand -out private/.rand 8192`

1. Verschieben Sie die erstellten .pem-Dateien an die in der .cnf-Datei konfigurierten Speicherorte.

1. Fügen Sie schließlich dem Java-Keystore das Zertifikat hinzu.

## Aktivieren der Debug-Protokollierung  {#enabling-debug-logging}

Die Debug-Protokollierung kann sowohl für den LDAP-Identitäts-Provider als auch das externe Anmeldemodul aktiviert werden, um Verbindungsprobleme zu beheben.

Zum Aktivieren der Debug-Protokollierung gehen Sie wie folgt vor:

1. Gehen Sie zur Webverwaltungskonsole.
1. Suchen Sie nach „Apache Sling Logging Logger Configuration“ und erstellen Sie zwei Logger mit den folgenden Optionen:

* Protokollebene: Debug
* Protokolldatei: logs/ldap.log
* Nachrichtenmuster: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Protokollebene: Debug
* Protokolldatei: logs/external.log
* Nachrichtenmuster: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Hinweis zur Gruppenzuordnung {#a-word-on-group-affiliation}

Durch LDAP synchronisierte Benutzer können verschiedenen Gruppen in AEM angehören. Bei diesen Gruppen kann es sich um externe LDAP-Gruppen handeln, die AEM im Zuge des Synchronisierungsvorgangs hinzugefügt werden. Die Gruppen können aber auch separat hinzugefügt werden und nicht zum ursprünglichen LDAP-Gruppenzuordnungsplan gehören.

In den meisten Fälle können dies Gruppen sein, die von einem lokalen AEM-Administrator oder einem anderen Identitäts-Provider hinzugefügt werden.

Wenn ein Benutzer aus einer Gruppe auf dem LDAP-Server entfernt wird, spiegelt sich diese Änderung bei einer Synchronisierung auf AEM-Seite wider. Alle anderen Gruppenzuordnungen des Benutzers, die nicht durch LDAP hinzugefügt wurden, bleiben allerdings bestehen.

Über die Eigenschaft `rep:externalId` erkennt und verarbeitet AEM die Löschung von Benutzern aus externen Gruppen. Diese Eigenschaft (mit Informationen zum ursprünglichen Identitäts-Provider) wird automatisch allen Benutzern oder Gruppen hinzugefügt, die durch den Synchronisierungshandler synchronisiert werden.

Weitere Informationen finden Sie in der Apache Oak-Dokumentation zum Thema [Benutzer- und Gruppensynchronisierung](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html).

## Bekannte Probleme {#known-issues}

Wenn Sie LDAP über SSL verwenden möchten, stellen Sie sicher, dass die von Ihnen verwendeten Zertifikate ohne Netscape-Kommentaroption erstellt werden. Ist diese Option aktiviert, schlägt die Authentifizierung mit einem SSL-Handshake-Fehler fehl.
