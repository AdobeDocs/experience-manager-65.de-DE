---
title: Konfigurieren von LDAP mit AEM 6
description: Erfahren Sie, wie Sie LDAP mit AEM konfigurieren.
uuid: 0007def4-86f0-401d-aa37-c8d49d5acea1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 5faf6ee5-9242-48f4-87a8-ada887a3be1e
exl-id: 2ebca4fb-20f7-499c-96a0-4018eaeddc1a
source-git-commit: 768576e300b655962adc3e1db20fc5ec06a5ba6c
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 40%

---

# Konfigurieren von LDAP mit AEM 6 {#configuring-ldap-with-aem}

LDAP (die **L** leicht **D** Verzeichnis **A** Zugriff **P** Protokoll) wird für den Zugriff auf zentrale Verzeichnisdienste verwendet. Auf diese Weise wird der Aufwand für die Verwaltung von Benutzerkonten reduziert, da sie von mehreren Anwendungen aufgerufen werden können. Ein solcher LDAP-Server ist Active Directory. LDAP wird häufig für Single-Sign-On-Szenarien eingesetzt, durch die ein Benutzer mit einer Anmeldung auf mehrere Anwendungen zugreifen kann.

Benutzerkonten können zwischen dem LDAP-Server und dem Repository synchronisiert werden, wobei die LDAP-Kontodetails im Repository gespeichert werden. Mit dieser Funktion können die Konten Repository-Gruppen zugewiesen werden, um die erforderlichen Berechtigungen und Berechtigungen zuzuweisen.

Das Repository nutzt die LDAP-Authentifizierung zum Authentifizieren solcher Benutzer. Dabei werden die Anmeldeinformationen zur Validierung an den LDAP-Server weitergegeben. Dies ist erforderlich, um Zugriff auf das Repository zu gewähren. Zur Leistungsverbesserung können erfolgreich validierte Anmeldeinformationen vom Repository zwischengespeichert werden. Über ein Ablauftimeout wird dann sichergestellt, dass nach einem angemessenen Zeitraum eine erneute Validierung erfolgt.

Wenn ein Konto vom LDAP-Server entfernt wird, wird die Validierung nicht mehr gewährt und der Zugriff auf das Repository wird verweigert. Details zu im Repository gespeicherten LDAP-Konten können ebenfalls bereinigt werden.

Die Verwendung solcher Konten ist für Ihre Benutzer transparent. Das heißt, sie sehen keinen Unterschied zwischen Benutzer- und Gruppenkonten, die aus LDAP erstellt wurden, und Konten, die ausschließlich im Repository erstellt wurden.

In AEM 6 umfasst die LDAP-Unterstützung eine neue Implementierung, für die ein anderer Konfigurationstyp erforderlich ist als für frühere Versionen.

Alle LDAP-Konfigurationen sind jetzt als OSGi-Konfigurationen verfügbar. Sie können über die folgende Webverwaltungskonsole konfiguriert werden:
`https://serveraddress:4502/system/console/configMgr`

Damit LDAP mit AEM funktioniert, müssen Sie drei OSGi-Konfigurationen erstellen:

1. einen LDAP-Identitäts-Provider (IDP),
1. Einen Synchronisierungshandler.
1. Ein externes Anmeldemodul.

>[!NOTE]
>
>Sehen Sie sich das Tutorial [Oak&#39;s External Login Module – Authenticating with LDAP and Beyond](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2015/aem-oak-external-login-module-authenticating-with-ldap-and-beyond.html?lang=en) an, um sich ausführlich über externe Anmeldemodule zu informieren.
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
   <td>DN des Benutzers für die Authentifizierung. Wenn dieses Feld leer gelassen wird, wird eine anonyme Bindung durchgeführt.</td>
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

## Konfigurieren des Synchronisierungshandlers {#configuring-the-synchronization-handler}

Der Synchronisierungshandler definiert, wie die Identity Provider-Benutzer und -Gruppen mit dem Repository synchronisiert werden.

Sie befindet sich unter der **Apache Jackrabbit Oak Standard Sync Handler** in der Verwaltungskonsole.

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
   <td>Liste der Gruppen, denen ein synchronisierter Benutzer automatisch hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><strong>User property mapping</strong></td>
   <td>Definition des Listen-Mappings für lokale Eigenschaften von externen.</td>
  </tr>
  <tr>
   <td><strong>User Path Prefix</strong></td>
   <td>Das beim Erstellen von Benutzern verwendete Pfadpräfix.</td>
  </tr>
  <tr>
   <td><strong>User Membership Expiration</strong></td>
   <td>Zeitraum, nach dem die Mitgliedschaft abläuft.<br /> </td>
  </tr>
  <tr>
   <td><strong>User membership nesting depth</strong></td>
   <td>Gibt die maximale Tiefe der Gruppenverschachtelung zurück, wenn Mitgliedschaftsbeziehungen synchronisiert werden. Der Wert 0 deaktiviert die Suche nach Gruppenmitgliedschaften. Bei einem Wert von 1 werden nur die direkten Gruppen eines Benutzers hinzugefügt. Dieser Wert hat keine Auswirkung beim Synchronisieren einzelner Gruppen nur bei der Synchronisierung der Abstammung einer Benutzermitgliedschaft.</td>
  </tr>
  <tr>
   <td><strong>Group Expiration Time</strong></td>
   <td>Dauer, bis eine synchronisierte Gruppe abläuft.</td>
  </tr>
  <tr>
   <td><strong>Group auto membership</strong></td>
   <td>Liste der Gruppen, denen automatisch eine synchronisierte Gruppe hinzugefügt wird.</td>
  </tr>
  <tr>
   <td><strong>Group property mapping</strong></td>
   <td>Definition des Listen-Mappings für lokale Eigenschaften von externen.</td>
  </tr>
  <tr>
   <td><strong>Group path prefix</strong></td>
   <td>Das beim Erstellen von Gruppen verwendete Pfadpräfix.</td>
  </tr>
 </tbody>
</table>

## Das externe Anmeldemodul {#the-external-login-module}

Das externe Anmeldemodul befindet sich unter der **Externes Apache Jackrabbit Oak-Anmeldemodul** in der Verwaltungskonsole.

>[!NOTE]
>
>Das externe Anmeldemodul von Apache Jackrabbit Oak implementiert die Java™ Authentication and Authorization Service (JAAS)-Spezifikationen. Siehe [Offizielles Oracle Java™-Sicherheitsreferenzhandbuch](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jaas/JAASRefGuide.html) für weitere Informationen.

Die Aufgabe besteht darin, zu definieren, welcher Identitäts-Provider und welcher Synchronisierungshandler verwendet werden soll, und die beiden Module effektiv zu binden.

Folgende Konfigurationsoptionen sind verfügbar:

| **JAAS Ranking** | Angabe des Rangs (d. h. der Sortierreihenfolge) dieses Anmeldemoduleintrags. Die Einträge werden in absteigender Reihenfolge sortiert (d. h. die Konfigurationen mit höherem Rang kommen an erster Stelle). |
|---|---|
| **JAAS Control Flag** | Eigenschaft, die angibt, ob ein LoginModule erforderlich, REQUISITE, SUFFICIENT oder OPTIONAL ist. Weitere Informationen zur Bedeutung dieser Flags finden Sie in der Dokumentation zur JAAS-Konfiguration . |
| **JAAS Realm** | Der Bereichsname (oder Anwendungsname), für den das LoginModule registriert ist. Wenn kein Bereichsname angegeben wird, wird das LoginModule bei einem Standardbereich registriert, wie in der Felix JAAS-Konfiguration konfiguriert. |
| **Identity Provider Name** | Name des Identitäts-Providers. |
| **Sync Handler Name** | Name des Synchronisierungs-Handlers. |

>[!NOTE]
Wenn Sie mehr als eine LDAP-Konfiguration mit Ihrer AEM-Instanz planen, müssen für jede Konfiguration separate Identitäts-Provider und Synchronisierungshandler erstellt werden.

## LDAP über SSL konfigurieren {#configure-ldap-over-ssl}

AEM 6 kann so konfiguriert werden, dass eine Authentifizierung mit LDAP über SSL erfolgt. Gehen Sie dazu wie folgt vor:

1. Überprüfen Sie die **SSL verwenden** oder **Verwenden von TLS** Kontrollkästchen beim Konfigurieren der [LDAP Identity Provider](#configuring-the-ldap-identity-provider).
1. Konfigurieren Sie den Synchronisierungshandler und das externe Anmeldemodul entsprechend Ihrer Einrichtung.
1. Installieren Sie bei Bedarf die SSL-Zertifikate in Ihrer Java™-VM. Diese Installation kann mit dem Keytool durchgeführt werden:

   `keytool -import -alias localCA -file <certificate location> -keystore <keystore location>`

1. Testen Sie die Verbindung zum LDAP-Server.

### Erstellen von SSL-Zertifikaten {#creating-ssl-certificates}

Selbstsignierte Zertifikate können verwendet werden, wenn AEM für die Authentifizierung mit LDAP über SSL konfiguriert werden. Nachfolgend finden Sie ein Beispiel für ein Arbeitsverfahren zum Generieren von Zertifikaten zur Verwendung mit AEM.

1. Stellen Sie sicher, dass eine SSL-Bibliothek installiert ist und funktioniert. Dieses Verfahren verwendet OpenSSL als Beispiel.

1. Erstellen Sie eine benutzerdefinierte OpenSSL-Konfigurationsdatei (.cnf). Diese Konfiguration kann durch Kopieren der standardmäßigen Konfigurationsdatei &quot;openssl.cnf&quot;und Anpassen vorgenommen werden. Auf UNIX®-Systemen befindet er sich unter `/usr/lib/ssl/openssl.cnf`

1. Erstellen Sie dann den Zertifizierungsstellen-Stammschlüssel, indem Sie den nachfolgenden Befehl an einem Terminal ausführen:

   ```
   openssl genpkey -algorithm [public key algorithm] -out certificatefile.key -pkeyopt [public key algorithm option]
   ```

1. Erstellen Sie anschließend ein selbstsigniertes Zertifikat:

   `openssl req -new -x509 -days [number of days for certification] -key certificatefile.key -out root-ca.crt -config CA/openssl.cnf`

1. Um sicherzustellen, dass alles in Ordnung ist, überprüfen Sie das neu generierte Zertifikat:

   `openssl x509 -noout -text -in root-ca.crt`

1. Vergewissern Sie sich, dass alle in der Zertifikatkonfigurationsdatei (.cnf) angegebenen Ordner vorhanden sind. Wenn nicht, erstellen Sie sie.
1. Erstellen Sie einen zufälligen Test, indem Sie beispielsweise Folgendes ausführen:

   `openssl rand -out private/.rand 8192`

1. Verschieben Sie die erstellten .pem-Dateien an die in der .cnf-Datei konfigurierten Speicherorte.

1. Fügen Sie das Zertifikat schließlich zum Java™-Keystore hinzu.

## Debugging-Protokollierung aktivieren {#enabling-debug-logging}

Die Debug-Protokollierung kann sowohl für den LDAP-Identitätsanbieter als auch für das externe Anmeldemodul aktiviert werden, um Verbindungsprobleme zu beheben.

Um die Debug-Protokollierung zu aktivieren, müssen Sie Folgendes tun:

1. Wechseln Sie zur Web-Management-Konsole.
1. Suchen Sie nach &quot;Apache Sling Logging Logger Configuration&quot;und erstellen Sie zwei Logger mit den folgenden Optionen:

* Protokollebene: Debuggen
* Protokolldatei logs/ldap.log
* Meldungsmuster: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.security.authentication.ldap

* Protokollebene: Debuggen
* Protokolldatei: logs/external.log
* Meldungsmuster: {0,date,dd.MM.yyyy HH:mm:ss.SSS} &amp;ast;{4}&amp;ast; {2} {3} {5}
* Logger: org.apache.jackrabbit.oak.spi.security.authentication.external

## Ein Wort zur Gruppenzuordnung {#a-word-on-group-affiliation}

Benutzer, die über LDAP synchronisiert werden, können zu verschiedenen Gruppen in AEM gehören. Diese Gruppen können externe LDAP-Gruppen sein, die AEM im Rahmen des Synchronisierungsprozesses hinzugefügt werden. Sie können jedoch auch Gruppen sein, die separat hinzugefügt werden und nicht zum ursprünglichen LDAP-Gruppenzuordnungsschema gehören.

Normalerweise werden diese Gruppen von einem lokalen AEM-Administrator oder einem anderen Identitäts-Provider hinzugefügt.

Wenn ein Benutzer aus einer Gruppe auf dem LDAP-Server entfernt wird, wird die Änderung bei der Synchronisierung auf der AEM Seite angezeigt. Alle anderen Gruppenzuordnungen des Benutzers, die nicht von LDAP hinzugefügt wurden, bleiben jedoch erhalten.

AEM erkennt und verarbeitet das Bereinigen von Benutzern aus externen Gruppen mithilfe der `rep:externalId` -Eigenschaft. Diese Eigenschaft (mit Informationen zum ursprünglichen Identitäts-Provider) wird automatisch allen Benutzern oder Gruppen hinzugefügt, die durch den Synchronisierungshandler synchronisiert werden.

Siehe Apache Oak-Dokumentation unter [Benutzer- und Gruppensynchronisierung](https://jackrabbit.apache.org/oak/docs/security/authentication/usersync.html).

## Bekannte Probleme {#known-issues}

Wenn Sie LDAP über SSL verwenden möchten, stellen Sie sicher, dass die von Ihnen verwendeten Zertifikate ohne die Netscape-Kommentaroption erstellt wurden. Wenn diese Option aktiviert ist, schlägt die Authentifizierung mit einem SSL-Handshake-Fehler fehl.
