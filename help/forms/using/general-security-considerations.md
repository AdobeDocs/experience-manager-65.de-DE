---
title: Allgemeine Überlegungen zur Sicherheit von AEM Forms on JEE
seo-title: General Security Considerations for AEM Forms on JEE
description: Erfahren Sie, wie Sie sich auf die Härtung der AEM Forms on JEE-Umgebung vorbereiten.
seo-description: Learn how to prepare for hardening your AEM Forms on JEE environment.
uuid: 4d098731-fc8f-41d7-98b5-5c2e31211614
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 64bc6018-2828-4634-9275-48f1d411452b
docset: aem65
role: Admin
exl-id: 3f150dd5-f486-4f16-9de9-035cde53b034
source-git-commit: c47b4dcfd2fbdcb0b98ad815f5b04d8f593e4f64
workflow-type: ht
source-wordcount: '1059'
ht-degree: 100%

---

# Allgemeine Überlegungen zur Sicherheit von AEM Forms on JEE{#general-security-considerations-for-aem-forms-on-jee}

Dieser Artikel bietet einleitende Informationen, die Sie bei der Vorbereitung auf die Härtung Ihrer AEM Forms-Umgebung unterstützen. Er enthält voraussetzungsvolle Informationen über AEM Forms on JEE, Betriebssystem, Anwendungs-Server und Datenbanksicherheit. Sie sollten diese Informationen lesen, bevor Sie Ihre Umgebung sperren.

## Anbieterspezifische Sicherheitsinformationen {#vendor-specific-security-information}

Dieser Abschnitt enthält sicherheitsbezogene Informationen zu Betriebssystemen, Anwendungs-Servern und Datenbanken, die in Ihre AEM Forms on JEE-Lösung integriert sind.

Verwenden Sie die Links in diesem Abschnitt, um anbieterspezifische Sicherheitsinformationen für Ihr Betriebssystem, Ihre Datenbank und Ihren Anwendungs-Server zu finden.

### Informationen zur Betriebssystemsicherheit {#operating-system-security-information}

Berücksichtigen Sie bei der Absicherung Ihres Betriebssystems sorgfältig die vom Hersteller Ihres Betriebssystems beschriebenen Maßnahmen, einschließlich der folgenden:

* Definieren und Steuern von Benutzenden, Rollen und Berechtigungen
* Überwachungsprotokolle und Prüfprotokolle
* Entfernen unnötiger Dienste und Anwendungen
* Sichern von Dateien

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Betriebssystemen finden Sie in der nachfolgenden Tabelle:

<table>
 <thead>
  <tr>
   <th><p>Betriebssystem</p> </th>
   <th><p>Sicherheitsressource</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM® AIX® 7.2</p> </td>
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">IBM® AIX®-Sicherheitsvorteile</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® Windows Server® 2016 </p> </td>
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 Security Guide</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Linux® AP oder ES</p> </td>
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat® Enterprise Linux®-Sicherheitshandbuch</a></p> </td>
  </tr>
  <tr>
   <td><p>Sun Solaris™ 11</p> </td>
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Richtlinien zur Sicherheit und Härtung</a></p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3</td>
   <td><a href="https://docs.oracle.com/de/operating-systems/oracle-linux/7/security/" target="_blank">Security Guide for Release 7</a><br /> </td>
  </tr>
  <tr>
   <td>CentOS 7<sup> </sup></td>
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Protection documentation</a></td>
  </tr>
 </tbody>
</table>

### Informationen zur Sicherheit des Anwendungs-Servers {#application-server-security-information}

Berücksichtigen Sie bei der Sicherung Ihres Anwendungs-Servers sorgfältig die von Ihrem Serveranbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Verwenden eines nicht offensichtlichen Benutzernamens für Admins
* Deaktivieren unnötiger Dienste
* Schützen des Konsolen-Managers
* Aktivieren sicherer Cookies
* Schließen nicht benötigter Ports
* Einschränken von Clients nach IP-Adressen oder Domains
* Verwenden von Java™ Security Manager zum programmgesteuerten Einschränken von Berechtigungen

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Betriebssystemen finden Sie in der nachfolgenden Tabelle.

<table>
 <thead>
  <tr>
   <th><p>Anwendungs-Server</p> </th>
   <th><p>Sicherheitsressource</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Oracle WebLogic®</p> </td>
   <td><p>Suchen Sie unter <a href="https://docs.oracle.com/de">https://docs.oracle.com/</a> nach „Understanding WebLogic Security“.</p> </td>
  </tr>
  <tr>
   <td><p>IBM® WebSphere®</p> </td>
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Anwendungen und ihre Umgebung sichern</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® JBoss®</p> </td>
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security%20subsystem%20configuration.html">Konfiguration des Sicherheitssystems</a></p> </td>
  </tr>
 </tbody>
</table>

### Informationen zur Datenbanksicherheit {#database-security-information}

Berücksichtigen Sie bei der Sicherung Ihrer Datenbank die von Ihrem Datenbankanbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Einschränken von Vorgängen mit Zugriffssteuerungslisten (ACLs)
* Verwenden von nicht standardmäßigen Ports
* Schützen der Datenbank durch eine Firewall
* Verschlüsseln sensibler Daten vor dem Schreiben in die Datenbank (siehe die Dokumentation des Datenbankherstellers)

Sicherheitsinformationen zu Datenbanken, die von AEM Forms on JEE unterstützt werden, finden Sie in den Ressourcen in dieser Tabelle.

<table>
 <thead>
  <tr>
   <th><p>Datenbank</p> </th>
   <th><p>Sicherheitsressource</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM® DB2® 11.1</p> </td>
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2® Product Family Library</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2016</p> </td>
   <td>Suchen im Web nach „SQL Server 2016: Sicherheit“</td>
  </tr>
  <tr>
   <td><p>MySQL 5</p> </td>
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 Allgemeine Sicherheitsprobleme</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 Allgemeine Sicherheitsprobleme</a></p> </td>
  </tr>
  <tr>
   <td><p>Oracle 12c</p> </td>
   <td><p>Weitere Informationen finden Sie im Kapitel „Sicherheit“ in der <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g Dokumentation</a></p> </td>
  </tr>
 </tbody>
</table>

In dieser Tabelle werden die Standardanschlüsse beschrieben, die während des Konfigurationsprozesses von AEM Forms on JEE geöffnet sein müssen. Wenn Sie die Verbindung über HTTPS herstellen, passen Sie Ihre Anschlussinformationen und IP-Adressen entsprechend an. Weitere Informationen zum Konfigurieren von Anschlüssen finden Sie im Dokument *Installieren und Bereitstellen von AEM Forms on JEE* für Ihren Anwendungsserver.

<table>
 <thead>
  <tr>
   <th><p>Produkt oder Dienst</p> </th>
   <th><p>Port-Nummer</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>JBoss®</p> </td>
   <td><p>8080</p> </td>
  </tr>
  <tr>
   <td><p>WebLogic</p> </td>
   <td><p>7001</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebLogic Managed Server</p> </td>
   <td><p>Wird von Admin während der Konfiguration festgelegt</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebSphere®</p> </td>
   <td><p>9060; wenn die globale Sicherheit aktiviert wurde, wird als standardmäßiger SSL-Anschluss der Anschluss 9043 verwendet.</p> <p>9080</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>BAM-Server</p> </td>
   <td><p>7001</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>SOAP</p> </td>
   <td><p>8880</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>MySQL</p> </td>
   <td><p>3306</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>Oracle</p> </td>
   <td><p>1521</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>DB2®</p> </td>
   <td><p>50000</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>SQL Server</p> </td>
   <td><p>1433</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>LDAP</p> </td>
   <td><p>Der Anschluss, an dem der LDAP-Server ausgeführt wird. Der Standardanschluss ist in der Regel 389. Wenn Sie jedoch die SSL-Option auswählen, ist der Standardanschluss in der Regel 636. Erkundigen Sie sich beim LDAP-Administrator, welchen Anschluss Sie angeben müssen.</p> </td>
  </tr>
 </tbody>
</table>

### Konfigurieren von JBoss® zur Verwendung eines nicht standardmäßigen HTTP-Ports {#configuring-jboss-to-use-a-non-default-http-port}

Der Anwendungs-Server von JBoss® verwendet 8080 als standardmäßigen HTTP-Port. JBoss® verfügt außerdem über die vorkonfigurierten Ports 8180, 8280 und 8380, die in der Datei „jboss-service.xml“ auskommentiert sind. Wenn Sie auf Ihrem Computer über eine Anwendung verfügen, die bereits diesen Port verwendet, ändern Sie den von AEM Forms on JEE verwendeten Port, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie die folgende Datei zum Bearbeiten:

   Einzel-Server-Installation: [JBoss®-Stamm]/standalone/configuration/standalone.xml

   Cluster-Installationen: [JBoss®-Stamm]/domain/configuration/domain.xml

1. Ändern Sie den Wert des Attributs **Port** im Tag **&lt;socket-binding>** in eine benutzerdefinierte Port-Nummer. Im Folgenden wird beispielsweise Port 8090 verwendet:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Speichern und schließen Sie die Datei.
1. Starten Sie den JBoss®-Anwendungs-Server neu.

## Sicherheitsüberlegungen zu AEM Forms on JEE {#aem-forms-on-jee-security-considerations}

In diesem Abschnitt werden einige für AEM Forms on JEE spezifische Sicherheitsprobleme beschrieben, die Sie kennen sollten.

### Keine Verschlüsselung von E-Mail-Anmeldeinformationen in der Datenbank {#email-credentials-not-encrypted-in-database}

Die von Applikationen gespeicherten E-Mail-Anmeldeinformationen werden nicht verschlüsselt, bevor sie in der Datenbank von AEM Forms on JEE gespeichert werden. Wenn Sie einen Dienstendpunkt für die Verwendung von E-Mails konfigurieren, werden Passwortinformationen, die im Rahmen dieser Endpunktkonfiguration verwendet werden, nicht verschlüsselt, wenn sie in der Datenbank gespeichert werden.

### Sensible Inhalte für Rights Management in der Datenbank {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE verwendet die AEM Forms on JEE-Datenbank, um vertrauliche Informationen über Dokumentschlüssel und anderes kryptographisches Material zu speichern, das für Richtliniendokumente verwendet wird. Wenn Sie die Datenbank gegen unberechtigten Zugriff schützen, erhöht dies den Schutz dieser sensiblen Informationen.

### Kennwort in unverschlüsseltem Textformular {#password-in-clear-text-format-in-adobe-ds-xml}

Der zum Ausführen von AEM Forms on JEE verwendete Anwendungs-Server muss eigens konfiguriert werden, um über eine auf dem Anwendungs-Server konfigurierte Datenquelle auf Ihre Datenbank zuzugreifen. Stellen Sie sicher, dass der Anwendungs-Server Ihr Datenbankkennwort in seiner Datenquellenkonfigurationsdatei nicht in unverschlüsseltem Textformat offen legt.

Die Datei lc_[Datenbank].xml sollte kein Kennwort in unverschlüsseltem Textformat enthalten. Fragen Sie beim Hersteller des Anwendungs-Servers nach, wie Sie diese Kennwörter für Ihren Anwendungs-Server verschlüsseln sollen.

>[!NOTE]
>
>Das AEM Forms on JEE JBoss® Turnkey-Installationsprogramm verschlüsselt das Datenbankpasswort.

Bei IBM® WebSphere® Anwendungs-Server und Oracle WebLogic Server werden Datenquellenkennwörter eventuell standardmäßig verschlüsselt. Sie sollten sich jedoch anhand der Dokumentation Ihres Anwendungs-Servers vergewissern, dass eine Verschlüsselung erfolgt.

### Schutz des in Trust Store gespeicherten privaten Schlüssels {#protecting-the-private-key-stored-in-trust-store}

Die privaten Schlüssel oder Berechtigungen, die in Trust Store importiert wurden, werden in der Datenbank von AEM Forms on JEE gespeichert. Um die Datenbank zu schützen und den Zugriff auf bestimmte Admins zu beschränken, treffen Sie geeignete Vorkehrungen.
