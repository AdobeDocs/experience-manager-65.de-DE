---
title: Konfigurieren von LDAP mit AEM 6
description: Erfahren Sie, wie Sie LDAP-Dienste mit AEM verwenden und konfigurieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 2ebca4fb-20f7-499c-96a0-4018eaeddc1a
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 98%

---

# Konfigurieren von LDAP mit AEM 6 {#configuring-ldap-with-aem}

LDAP (das **L** ightweight **D** irectory **A** ccess **P** rotocol) wird für den Zugriff auf zentrale Verzeichnisdienste verwendet. Auf diese Weise wird der Aufwand für die Verwaltung von Benutzerkonten reduziert, da sie von mehreren Anwendungen aufgerufen werden können. Ein solcher LDAP-Server ist Active Directory. LDAP wird häufig für Single-Sign-On-Szenarien eingesetzt, durch die ein Benutzer mit einer Anmeldung auf mehrere Anwendungen zugreifen kann.

Benutzerkonten können zwischen dem LDAP-Server und dem Repository synchronisiert werden, wobei die LDAP-Kontodetails im Repository gespeichert werden. Hierdurch ist es möglich, Konten Repository-Gruppen zuzuordnen, um die erforderlichen Berechtigungen und Rechte zuzuweisen.

Das Repository nutzt die LDAP-Authentifizierung zum Authentifizieren solcher Benutzer. Dabei werden die Anmeldeinformationen zur Validierung an den LDAP-Server weitergegeben. Dies ist erforderlich, um Zugriff auf das Repository zu gewähren. Zur Leistungsverbesserung können erfolgreich validierte Anmeldeinformationen vom Repository zwischengespeichert werden. Über ein Ablauftimeout wird dann sichergestellt, dass nach einem angemessenen Zeitraum eine erneute Validierung erfolgt.

Wenn ein Konto vom LDAP-Server entfernt wird, wird die Validierung nicht mehr gewährt und der Zugriff auf das Repository wird verweigert. Details zu im Repository gespeicherten LDAP-Konten können ebenfalls bereinigt werden.

Die Verwendung solcher Konten ist für Ihre Benutzerinnen und Benutzer transparent. Das heißt, sie sehen keinen Unterschied zwischen Benutzer- und Gruppenkonten, die aus LDAP erstellt wurden, und Konten, die ausschließlich im Repository erstellt wurden.

In AEM 6 umfasst die LDAP-Unterstützung eine neue Implementierung, für die ein anderer Konfigurationstyp erforderlich ist als für frühere Versionen.

Alle LDAP-Konfigurationen sind jetzt als OSGi-Konfigurationen verfügbar. Sie können über die folgende Webverwaltungskonsole konfiguriert werden:
`https://serveraddress:4502/system/console/configMgr`

Damit LDAP mit AEM funktioniert, müssen Sie drei OSGi-Konfigurationen erstellen:

1. einen LDAP-Identitäts-Provider (IDP),
1. einen Synchronisierungs-Handler.
1. ein externes Anmeldemodul.

>[!NOTE]
>
>Sehen Sie sich das Tutorial [Oak&#39;s External Login Module – Authenticating with LDAP and Beyond](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-oak-external-login-module-authenticating-with-ldap-and-beyond.html) an, um sich ausführlich über externe Anmeldemodule zu informieren.
>
>Weitere Informationen zum Konfigurieren von Experience Manager mit Apache DS finden Sie unter [Konfigurieren von Adobe Experience Manager 6.5 für Apache Directory Service](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/configuring-adobe-experience-manager-6-to-use-apache-directory/m-p/183805).

## Konfigurieren des LDAP-Identitäts-Providers {#configuring-the-ldap-identity-provider}

Über den LDAP-Identitäts-Provider wird definiert, wie Benutzer vom LDAP-Server abgerufen werden.

Sie finden ihn in der Verwaltungskonsole unter dem Namen **Apache Jackrabbit Oak LDAP Identity Provider**.

Die folgenden Konfigurationsoptionen sind für den LDAP-Identitäts-Provider verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>LDAP-Provider-Name</strong></td>
   <td>Name dieser LDAP-Provider-Konfiguration</td>
  </tr>
  <tr>
   <td><strong>LDAP-Server-Hostname</strong><br /> </td>
   <td>Hostname des LDAP-Servers</td>
  </tr>
  <tr>
   <td><strong>LDAP-Server-Anschluss</strong></td>
   <td>Die Anschlussnummer des LDAP-Servers</td>
  </tr>
  <tr>
   <td><strong>SSL verwenden</strong></td>
   <td>Gibt an, ob eine SSL-Verbindung (LDAPs) verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>TLS verwenden</strong></td>
   <td>Gibt an, ob TLS bei Verbindungen gestartet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Zertifikatüberprüfung deaktivieren</strong></td>
   <td>Gibt an, ob die Validierung des Serverzertifikats deaktiviert werden soll.</td>
  </tr>
  <tr>
   <td><strong>Bindungs-DN</strong></td>
   <td>DN des Benutzers für die Authentifizierung. Ohne Eintrag in diesem Feld erfolgt eine anonyme Bindung.</td>
  </tr>
  <tr>
   <td><strong>Bindungspasswort</strong></td>
   <td>Passwort des Benutzers für die Authentifizierung</td>
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
   <td><strong>Maximale Anzahl aktiver Benutzerpools</strong></td>
   <td>Die maximale aktive Größe des Benutzerverbindungspools.</td>
  </tr>
  <tr>
   <td><strong>Benutzerbasis-DN</strong></td>
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
   <td><strong>Zusätzlicher Filter für Benutzerinnen und Benutzer</strong></td>
   <td>Zusätzlicher LDAP-Filter zur Verwendung bei der Suche nach Benutzerinnen und Benutzern. Der endgültige Filter ist wie folgt formatiert: '(&amp;(&lt;idAttr&gt;=&lt;userId&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)' (user.extraFilter)</td>
  </tr>
  <tr>
   <td><strong>Benutzer-DN-Pfade</strong></td>
   <td>Steuert, ob der DN zur Berechnung eines Teils des Zwischenpfads verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Gruppenbasis-DN</strong></td>
   <td>Der Basis-DN für Gruppensuchen.</td>
  </tr>
  <tr>
   <td><strong>Gruppenobjektklassen</strong></td>
   <td>Die Liste der Objektklassen, die ein Gruppeneintrag enthalten muss.</td>
  </tr>
  <tr>
   <td><strong>Gruppennamenattribut</strong></td>
   <td>Name des Attributs, das den Gruppennamen enthält.</td>
  </tr>
  <tr>
   <td><strong>Zusätzlicher Filter für Gruppen</strong></td>
   <td>Zusätzlicher LDAP-Filter zur Verwendung bei der Suche nach Gruppen. Der endgültige Filter ist wie folgt formatiert: '(&amp;(&lt;nameAttr&gt;=&lt;groupName&gt;)(objectclass=&lt;objectclass&gt;)&lt;extraFilter&gt;)'</td>
  </tr>
  <tr>
   <td><strong>Gruppen-DN-Pfade</strong></td>
   <td>Steuert, ob der DN zur Berechnung eines Teils des Zwischenpfads verwendet werden soll.</td>
  </tr>
  <tr>
   <td><strong>Gruppenmitgliedsattribut</strong></td>
   <td>Gruppenattribut, das ein oder mehrere Mitglieder einer Gruppe enthält.</td>
  </tr>
 </tbody>
</table>

## Konfigurieren des Synchronisierungs-Handlers {#configuring-the-synchronization-handler}

Der Synchronisierungs-Handler definiert, wie die Benutzerinnen bzw. Benutzer und Gruppen des Identitäts-Providers mit dem Repository synchronisiert werden.

Er ist unter dem Namen **Apache Jackrabbit Oak Standard Sync Handler** in der Verwaltungskonsole zu finden.

Die folgenden Konfigurationsoptionen sind für den Synchronisierungshandler verfügbar:

<table>
 <tbody>
  <tr>
   <td><strong>Sync Handler Name</strong></td>
   <td>Name der Synchronisierungskonfiguration.</td>
  </tr>
  <tr>
   <td><strong>User Expiration Time</strong></td>
   <td>Dauer, bis synchronisierte Benutzerinnen und Benutzer abgelaufen sind.</td>
  </tr>
  <tr>
   <td><strong>User auto membership</strong></td>
   <td>Liste der Gruppen, denen synchronisierte Benutzerinnen und Benutzer automatisch hinzugefügt werden.</td>
  </tr>
  <tr>
   <td><strong>Zuordnung der Benutzereigenschaften</strong></td>
   <td>Listenzuordnungsdefinition für lokale Eigenschaften von externen Eigenschaften.</td>
  </tr>
  <tr>
   <td><strong>Benutzerpfadpräfix</strong></td>
   <td>Das beim Erstellen neuer Benutzerinnen und Benutzer verwendete Pfadpräfix.</td>
  </tr>
  <tr>
   <td><strong>User Membership Expiration</strong></td>
   <td>Zeitraum, nach dem die Mitgliedschaft abläuft.<br /> </td>
  </tr>
  <tr>
   <td><strong>User membership nesting depth</strong></td>
   <td>Gibt die maximale Tiefe der Gruppenverschachtelung zurück, wenn Mitgliedschaftsbeziehungen synchronisiert werden. Der Wert 0 deaktiviert die Suche nach Gruppenmitgliedschaften. Bei einem Wert von 1 werden nur die direkten Gruppen eines Benutzers hinzugefügt. Dieser Wert hat keinerlei Wirkung, wenn beim Synchronisieren der mitgliedsbezogenen Herkunft eines Benutzers nur einzelne Gruppen synchronisiert werden.</td>
  </tr>
  <tr>
   <td><strong>Group Expiration Time</strong></td>
   <td>Dauer, bis eine synchronisierte Gruppe abläuft.</td>
  </tr>
  <tr>
   <td><strong>Group auto membership</strong></td>
   <td>Liste der Gruppen, denen eine synchronisierte Gruppe automatisch hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><strong>Zuordnung von Gruppeneigenschaften</strong></td>
   <td>Listenzuordnungsdefinition für lokale Eigenschaften von externen Eigenschaften.</td>
  </tr>
  <tr>
   <td><strong>Gruppenpfadpräfix</strong></td>
   <td>Das bei der Erstellung von Gruppen verwendete Pfadpräfix.</td>
  </tr>
 </tbody>
</table>

## Das externe Anmeldemodul {#the-external-login-module}

Sie finden das externe Anmeldemodul in der Verwaltungskonsole unter dem Namen **Apache Jackrabbit Oak External Login Module**.

>[!NOTE]
>
>Das Apache Jackrabbit Oak External Login Module implementiert die JAAS-Spezifikationen (Java™ Authentication and Authorization Service). Weitere Informationen finden Sie im [offiziellen Oracle Java™-Sicherheitshandbuch](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html).

Seine Aufgabe besteht in der Definition des zu verwendenden Identitäts-Providers und Synchronisierungs-Handlers, wodurch die beiden Module miteinander verbunden werden.

Folgende Konfigurationsoptionen sind verfügbar:

| **JAAS Ranking** | Angabe des Rankings (d. h. der Sortierreihenfolge) dieses Anmeldemoduleintrags. Die Einträge sind in absteigender Reihenfolge sortiert (d. h., höher bewertete Konfigurationen werden zuerst aufgeführt). |
|---|---|
| **JAAS Control Flag** | Eigenschaft, die angibt, ob ein Anmeldemodul ERFORDERLICH, eine VORAUSSETZUNG, AUSREICHEND oder OPTIONAL ist. Weitere Informationen zur Bedeutung dieser Flags finden Sie in der Dokumentation zur JAAS-Konfiguration . |
| **JAAS Realm** | Der Bereichsname (oder Anwendungsname), mit dem das Anmeldemodule registriert wird. Ohne Angabe eines Bereichsnamens wird das Anmeldemodul mit einem Standardbereich registriert, wie in der Felix JAAS-Konfiguration konfiguriert. |
| **Identity Provider Name** | Name des Identitäts-Providers. |
| **Sync Handler Name** | Name des Synchronisierungs-Handlers. |

>[!NOTE]
>
>Wenn für Ihre AEM-Instanz mehr als eine LDAP-Konfiguration vorgesehen ist, müssen Sie für jede Konfiguration separate Identitäts-Provider und Synchronisierungs-Handler erstellen. 

## Konfigurieren von LDAP über SSL {#configure-ldap-over-ssl}

AEM 6 kann so konfiguriert werden, dass eine LDAP-Authentifizierung über SSL erfolgt. Gehen Sie hierzu wie folgt vor:

1. Aktivieren Sie die Kontrollkästchen **Use SSL** oder **Use TLS**, wenn Sie den [LDAP-Identitäts-Provider](#configuring-the-ldap-identity-provider) konfigurieren.
1. Konfigurieren Sie den Synchronisierungs-Handler und das externe Anmeldemodul gemäß Ihrem Setup.
1. Installieren Sie ggf. die SSL-Zertifikate auf Ihrer virtuellen Java™-Maschine. Für diese Installation kann das Keytool verwendet werden:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Testen Sie die Verbindung zum LDAP-Server.

### Erstellen von SSL-Zertifikaten {#creating-ssl-certificates}

Über selbstsignierte Zertifikate kann AEM so konfiguriert werden, dass eine LDAP-Authentifizierung über SSL erfolgt. Im Folgenden finden Sie ein Beispielverfahren zum Generieren von Zertifikaten für die Verwendung mit AEM.

1. Vergewissern Sie sich, dass eine funktionstüchtige SSL-Bibliothek installiert ist. Bei dieser Vorgehensweise wird beispielhaft OpenSSL verwendet.

1. Erstellen Sie eine benutzerdefinierte OpenSSL-Konfigurationsdatei (.cnf). Kopieren Sie für diese Konfiguration die Konfigurationsdatei **openssl.cnf ** und passen Sie diese an. Auf UNIX-Systemen befindet sie sich unter `/usr/lib/ssl/openssl.cnf`.

1. Erstellen Sie dann den Zertifizierungsstellen-Stammschlüssel, indem Sie den nachfolgenden Befehl in einem Terminal ausführen:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option]
   ```

1. Erstellen Sie als Nächstes ein selbstsigniertes Zertifikat:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Um sicherzustellen, dass alles in Ordnung ist, überprüfen Sie das neu generierte Zertifikat:

   `openssl x509 -noout -text -in root-ca.crt`

1. Vergewissern Sie sich, dass alle in der Zertifikatkonfigurationsdatei (.cnf) angegebenen Ordner vorhanden sind. Ist dies nicht der Fall, erstellen Sie diese.
1. Erstellen Sie einen Zufalls-Startwert, indem Sie beispielsweise Folgendes ausführen:

   `openssl rand -out private/.rand 8192`

1. Verschieben Sie die erstellten .pem-Dateien an die in der .cnf-Datei konfigurierten Speicherorte.

1. Fügen Sie schließlich das Zertifikat zum Java™-Keystore hinzu.

## Aktivieren der Debug-Protokollierung {#enabling-debug-logging}

Die Debug-Protokollierung kann sowohl für den LDAP-Identitätsanbieter als auch für das externe Anmeldemodul aktiviert werden, um Verbindungsprobleme zu beheben.

Um die Debug-Protokollierung zu aktivieren, müssen Sie Folgendes tun:

1. Wechseln Sie zur Web-Management-Konsole.
1. Suchen Sie nach „Apache Sling Logging Logger Configuration“ und erstellen Sie zwei Logger mit den folgenden Optionen:

* Protokollstufe: Debug
* Protokolldatei logs/ldap.log
* Nachrichtenmuster: {0,date,`dd.MM.yyyy` `HH:mm:ss.SSS`} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Protokollstufe: Debug
* Protokolldatei: logs/external.log
* Nachrichtenmuster: {0,date,`dd.MM.yyyy` `HH:mm:ss.SSS`} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Hinweis zur Gruppenzuordnung {#a-word-on-group-affiliation}

Benutzerinnen und Benutzer, die über LDAP synchronisiert werden, können zu verschiedenen Gruppen in AEM gehören. Diese Gruppen können externe LDAP-Gruppen sein, die AEM im Rahmen des Synchronisierungsprozesses hinzugefügt werden. Sie können jedoch auch Gruppen sein, die separat hinzugefügt werden und nicht zum ursprünglichen LDAP-Gruppenzuordnungsschema gehören.

Normalerweise werden diese Gruppen von einem lokalen AEM-Administrator oder einem anderen Identitätsanbieter hinzugefügt.

Wenn eine Benutzerin oder ein Benutzer aus einer Gruppe auf dem LDAP-Server entfernt wird, wird die Änderung bei der Synchronisierung auf der AEM-Seite angezeigt. Alle anderen Gruppenzuordnungen der Benutzerin oder des Benutzers, die nicht von LDAP hinzugefügt wurden, bleiben jedoch erhalten.

Über die Eigenschaft `rep:externalId` erkennt und verarbeitet AEM die Löschung von Benutzerinnen und Benutzern aus externen Gruppen. Diese Eigenschaft (mit Informationen zum ursprünglichen Identitäts-Provider) wird automatisch allen Benutzern oder Gruppen hinzugefügt, die durch den Synchronisierungs-Handler synchronisiert werden.

Siehe die Apache Oak-Dokumentation unter [Benutzer- und Gruppensynchronisierung](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html).

## Bekannte Probleme {#known-issues}

Wenn Sie LDAP über SSL verwenden möchten, stellen Sie sicher, dass die von Ihnen verwendeten Zertifikate ohne die Netscape-Kommentaroption erstellt wurden. Ist diese Option aktiviert, schlägt die Authentifizierung mit einem SSL-Handshake-Fehler fehl.
