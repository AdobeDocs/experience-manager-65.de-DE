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
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 100%

---

# Allgemeine Überlegungen zur Sicherheit von AEM Forms on JEE{#general-security-considerations-for-aem-forms-on-jee}

In diesem Artikel finden Sie einleitende Informationen, die Ihnen die Vorbereitung auf das Härten Ihrer AEM Forms-Umgebung erleichtern sollen. Hier finden Sie Informationen zu AEM Forms on JEE, zum Betriebssystem, Anwendungsserver und Datenbanksicherheit, die Sie als Grundvoraussetzung benötigen. Sie sollten diese Informationen lesen, bevor Sie Ihre Umgebung sperren.

## Herstellerspezifische Sicherheitsinformationen {#vendor-specific-security-information}

Dieser Abschnitt enthält sicherheitsbezogene Informationen zu Betriebssystemen, Anwendungsservern und Datenbanken, die in Ihre AEM Forms on JEE-Lösung integriert sind.

Verwenden Sie die angezeigten Links, um herstellerspezifische Sicherheitsinformationen zu Betriebssystem, Datenbank und Anwendungsserver zu suchen.

### Informationen zur Betriebssystemsicherheit {#operating-system-security-information}

Berücksichtigen Sie bei der Absicherung Ihres Betriebssystems sorgfältig die vom Hersteller Ihres Betriebssystems beschriebenen Maßnahmen, einschließlich der folgenden:

* Definieren und Steuern von Benutzern, Rollen und Berechtigungen
* Überwachen von Protokollen und Prüfspuren
* Entfernen unnötiger Dienste und Anwendungen
* Erstellen von Sicherungskopien der Dateien

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
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">IBM AIX-Sicherheitsvorteile</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft Windows Server 2016 </p> </td>
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 Security Guide</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Linux® AP oder ES</p> </td>
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat Enterprise Linux Security Guide</a></p> </td>
  </tr>
  <tr>
   <td><p>Sun Solaris 11</p> </td>
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Richtlinien zur Sicherheit und Härtung</a></p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3</td>
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">Security Guide for Release 7</a><br /> </td>
  </tr>
  <tr>
   <td>CentOS 7<sup> </sup></td>
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Protection documentation</a></td>
  </tr>
 </tbody>
</table>

### Informationen zur Sicherheit des Anwendungs-Servers {#application-server-security-information}

Berücksichtigen Sie bei der Sicherung Ihres Anwendungs-Servers sorgfältig die von Ihrem Serveranbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Verwenden eines nicht offensichtlichen Benutzernamens für den Administrator
* Deaktivieren unnötiger Dienste
* Schützen des Konsolenmanagers
* Aktivieren sicherer Cookies
* Schließen nicht benötigter Anschlüsse
* Einschränken von Clients nach IP-Adressen oder Domänen
* Verwenden von Java™ Security Manager, um Berechtigungen programmgesteuert einzuschränken

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Anwendungsservern finden Sie in den nachfolgend aufgeführten Ressourcen.

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
   <td><p>Suchen Sie unter <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a> nach „Understanding WebLogic Security“.</p> </td>
  </tr>
  <tr>
   <td><p>IBM WebSphere®</p> </td>
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Anwendungen und ihre Umgebung sichern</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® JBoss®</p> </td>
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">Konfiguration des Sicherheitssystems</a></p> </td>
  </tr>
 </tbody>
</table>

### Informationen zur Datenbanksicherheit {#database-security-information}

Berücksichtigen Sie bei der Sicherung Ihrer Datenbank die von Ihrem Datenbankanbieter beschriebenen Maßnahmen, einschließlich der folgenden:

* Einschränken der Vorgänge durch Zugriffssteuerungslisten
* Verwendung nicht standardmäßiger Anschlüsse
* Schützen der Datenbank durch eine Firewall
* Verschlüsseln sensibler Daten vor dem Schreiben in die Datenbank (siehe Dokumentation des Datenbankherstellers)

Sicherheitsinformationen zu von AEM Forms on JEE unterstützten Datenbanken finden Sie in den nachfolgend aufgeführten Ressourcen.

<table>
 <thead>
  <tr>
   <th><p>Datenbank</p> </th>
   <th><p>Sicherheitsressource</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM DB2 11.1</p> </td>
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2 Product Family Library</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft SQL Server 2016</p> </td>
   <td>Suchen Sie im Web nach „SQL Server 2016: Sicherheit“</td>
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

In der folgenden Tabelle werden die Standardanschlüsse aufgeführt, die während des AEM Forms on JEE-Konfigurationsprozesses geöffnet sein müssen. Wenn Sie die Verbindung über HTTPS herstellen, passen Sie Ihre Anschlussinformationen und IP-Adressen entsprechend an. Weitere Informationen zum Konfigurieren von Anschlüssen finden Sie im Dokument *Installieren und Bereitstellen von AEM Forms on JEE* für Ihren Anwendungsserver.

<table>
 <thead>
  <tr>
   <th><p>Produkt oder Dienst</p> </th>
   <th><p>Anschlussnummer</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>JBoss</p> </td>
   <td><p>8080</p> </td>
  </tr>
  <tr>
   <td><p>WebLogic</p> </td>
   <td><p>7001</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebLogic Managed Server</p> </td>
   <td><p>Legt der Administrator während der Konfiguration fest</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebSphere</p> </td>
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
   <td>&gt;<p>DB2</p> </td>
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

### JBoss zur Verwendung eines nicht standardmäßigen HTTP-Anschlusses konfigurieren {#configuring-jboss-to-use-a-non-default-http-port}

Der JBoss-Anwendungsserver verwendet 8080 als HTTP-Standardanschluss. JBoss verfügt außerdem über die vorkonfigurierten Anschlüsse 8180, 8280 und 8380, die in der Datei „jboss-service.xml“ auskommentiert sind. Wenn Sie auf Ihrem Computer über eine Anwendung verfügen, die bereits diesen Anschluss verwendet, ändern Sie den von AEM Forms on JEE verwendeten Anschluss, indem Sie die folgenden Schritte ausführen:

1. Öffnen Sie die folgende Datei zum Bearbeiten:

   Einzelserverinstallation: [JBoss-Stamm]/standalone/configuration/standalone.xml

   Cluster-Installationen: [JBoss-Stamm]/domain/configuration/domain.xml

1. Ändern Sie den Wert des Attributs **port** im Tag **&lt;socket-binding>** in eine benutzerdefinierte Port-Nummer. Im Folgenden wird beispielsweise Port 8090 verwendet:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Speichern und schließen Sie die Datei.
1. Starten Sie den JBoss Anwendungs-Server neu.

## Sicherheitsüberlegungen zu AEM Forms on JEE {#aem-forms-on-jee-security-considerations}

In diesem Abschnitt werden bestimmte Sicherheitsprobleme für AEM Forms on JEE beschrieben, über die Sie sich bewusst sein sollen.

### Keine Verschlüsselung von E-Mail-Berechtigungen in der Datenbank {#email-credentials-not-encrypted-in-database}

Die von -Anwendungen gespeicherten E-Mail-Berechtigungen werden nicht verschlüsselt, bevor sie in der AEM Forms on JEE-Datenbank gespeichert werden. Wenn Sie einen Dienstendpunkt für die Verwendung von E-Mail konfigurieren, werden Kennwortinformationen, die bei der Endpunktkonfiguration verwendet werden, beim Speichern in der Datenbank nicht verschlüsselt.

### Sensibler Inhalt für Rights Management in der Datenbank {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE verwendet die AEM Forms on JEE-Datenbank, um vertrauliche Informationen über Dokumentschlüssel und anderes kryptographisches Material zu speichern, das für Richtliniendokumente verwendet wird. Wenn Sie die Datenbank gegen unberechtigten Zugriff schützen, erhöht dies den Schutz dieser sensiblen Informationen.

### Kennwort in unverschlüsseltem Textformular {#password-in-clear-text-format-in-adobe-ds-xml}

Der zum Ausführen von AEM Forms on JEE verwendete Anwendungs-Server muss eigens konfiguriert werden, um über eine auf dem Anwendungs-Server konfigurierte Datenquelle auf Ihre Datenbank zuzugreifen. Stellen Sie sicher, dass der Anwendungs-Server Ihr Datenbankkennwort in seiner Datenquellenkonfigurationsdatei nicht in unverschlüsseltem Textformat offen legt.

Die Datei lc_[Datenbank].xml sollte kein Kennwort in unverschlüsseltem Textformat enthalten. Fragen Sie beim Hersteller des Anwendungs-Servers nach, wie Sie diese Kennwörter für Ihren Anwendungs-Server verschlüsseln sollen.

>[!NOTE]
>
>AEM Forms on JEE JBoss Turnkey-Programm verschlüsselt das Datenbankkennwort.

Bei IBM® WebSphere Application Server und Oracle WebLogic Server werden Datenquellenkennwörter eventuell standardmäßig verschlüsselt. Schlagen Sie in der Dokumentation zu Ihrem Anwendungs-Server nach, um sicherzustellen, dass eine Verschlüsselung erfolgt.

### Schützen des in Trust Store gespeicherten privaten Schlüssels {#protecting-the-private-key-stored-in-trust-store}

Die privaten Schlüssel oder Berechtigungen, die in Trust Store importiert wurden, werden in der AEM Forms on JEE-Datenbank gespeichert. Sie müssen entsprechende Sicherheitsmaßnahmen treffen, um die Datenbank zu schützen und den Zugriff auf benannte Administratoren zu beschränken.
