---
title: Härtung Ihrer AEM Forms on JEE-Umgebung
seo-title: Hardening Your AEM Forms on JEE Environment
description: Erfahren Sie mehr über die verschiedenen Einstellungen zum Stärken der Sicherheit, um die Sicherheit von AEM Forms auf JEE bei der Ausführung in einem firmeninternen Intranet zu verbessern.
seo-description: Learn a variety of security-hardening settings to enhance the security of AEM Forms on JEE running in a corporate intranet.
uuid: f6c63690-6376-4fe1-9df2-a14fbfd62aff
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 6b380e92-f90d-4875-b7a2-f3958daf2364
role: Admin
exl-id: 6fb260f9-d0f8-431e-8d4e-535b451e4124
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '7665'
ht-degree: 97%

---

# Härtung Ihrer AEM Forms on JEE-Umgebung {#hardening-your-aem-forms-on-jee-environment}

Erfahren Sie mehr über die verschiedenen Einstellungen zum Stärken der Sicherheit, um die Sicherheit von AEM Forms auf JEE bei der Ausführung in einem firmeninternen Intranet zu verbessern.

In diesem Artikel werden Empfehlungen und Best Practices beschrieben, um Server zu schützen, auf denen AEM Forms on JEE ausgeführt wird. Dieses Dokument stellt keine umfassende Anleitung zum Härten (Absichern) des Hosts für das Betriebssystem und die Anwendungsserver dar. Stattdessen werden in diesem Artikel eine Reihe von Einstellungen zum Stärken der Sicherheit beschrieben, die Sie implementieren sollten, um die Sicherheit von AEM Forms auf JEE bei der Ausführung in einem firmeninternen Intranet zu verbessern. Um sicherzustellen, dass die Anwendungs-Server von AEM Forms on JEE sicher bleiben, sollten Sie jedoch auch Verfahren zur Sicherheitsüberwachung, -erkennung und -reaktion implementieren.

In diesem Artikel werden Härtungsverfahren beschrieben, die in den folgenden Phasen des Installations- und Konfigurationszyklus angewendet werden sollten:

* **Vorinstallation:** Verwenden Sie diese Verfahren, bevor Sie AEM Forms on JEE installieren.
* **Installation**: Verwenden Sie diese Verfahren während der Installation von AEM Forms auf JEE.
* **Nach der Installation:** Verwenden Sie diese Verfahren nach der Installation und danach in regelmäßigen Abständen.

AEM Forms on JEE ist in hohem Maße anpassbar und kann in vielen verschiedenen Umgebungen verwendet werden. Einige der Empfehlungen entsprechen möglicherweise nicht den Anforderungen Ihrer Organisation.

## Vorinstallation {#preinstallation}

Vor der Installation von AEM Forms on JEE können Sie Sicherheitslösungen auf die Netzwerkschicht und das Betriebssystem anwenden. In diesem Abschnitt finden Sie Beschreibungen zu einigen Sicherheitslücken sowie Empfehlungen dazu, wie Sie die Lücken in diesen Bereichen schließen können.

**Installation und Konfiguration unter UNIX und Linux**

Sie sollten AEM Forms on JEE nicht mit einer Root Shell installieren oder konfigurieren. Standardmäßig werden alle Dateien im Ordner „/opt“ installiert. Der Benutzer, der die Installation durchführt, benötigt daher sämtliche Dateiberechtigungen für den Ordner „/opt“. Alternativ kann eine Installation unter dem Verzeichnis „/user“ einer einzelnen Person durchgeführt werden, für die bereits alle Dateiberechtigungen vorliegen.

**Installation und Konfiguration unter Windows**

Sie müssen die Installation unter Windows als Administrator durchführen, wenn Sie AEM Forms on JEE mit der Turnkey-Methode oder PDF Generator installieren. Wenn Sie PDF Generator unter Windows mit nativer Anwendungsunterstützung installieren, müssen Sie die Installation außerdem als die Windows-Benutzerin oder der -Benutzer ausführen, die bzw. der Microsoft Office installiert hat. Weitere Informationen zu Installationsberechtigungen finden Sie im Dokument „Installieren und Bereitstellen von AEM Forms auf JEE“ für Ihren Programm-Server.

### Sicherheit der Netzwerkebene {#network-layer-security}

Sicherheitslücken der Netzwerkschicht gehören zu den Hauptbedrohungen für Internet- oder Intranet-orientierte Anwendungsserver. In diesem Abschnitt wird der Prozess zum Absichern von Hostrechnern im Netzwerk gegen diese Schwachstellen beschrieben. Dabei geht es um die Netzwerksegmentierung, das Härten des TCP/IP-Stacks (Transmission Control Protocol/Internet Protocol) und die Verwendung von Firewalls für den Schutz des Hosts.

In der folgenden Tabelle werden gängige Prozesse beschrieben, die Sicherheitslücken im Netzwerk reduzieren.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Demilitarisierte Zonen (DMZs)</p> </td> 
   <td><p>Stellen Sie Formular-Server innerhalb einer demilitarisierten Zone (DMZ) bereit. Die Segmentierung sollte in mindestens zwei Schichten bestehen, wobei sich der Anwendungsserver, auf dem AEM Forms on JEE ausgeführt wird, hinter der inneren Firewall befindet. Schirmen Sie das externe Netzwerk von der DMZ ab, die die Webserver enthält, und schirmen Sie die DMZ wiederum vom internen Netzwerk ab. Verwenden Sie Firewalls für die Implementierung der Abschirmungsebenen. Kategorisieren und steuern Sie den Traffic, der durch die einzelnen Netzwerkebenen geleitet wird, um sicherzustellen, dass nur das absolute Minimum der erforderlichen Daten erlaubt wird.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Private IP-Adressen</p> </td> 
   <td><p>Verwenden Sie auf AEM Forms-Programm-Servern durch NAT (Network Address Translation) geschützte private IP-Adressen gemäß RFC 1918. Weisen Sie private IP-Adressen (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) zu, um es einem Angreifer zu erschweren, Netzwerkverkehr über das Internet zu und von einem internen Host mit NAT zu leiten.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Firewalls</p> </td> 
   <td><p>Verwenden Sie die folgenden Kriterien, um eine Firewall-Lösung auszuwählen:</p> 
    <ul> 
     <li><p>Implementieren Sie Firewalls, die Proxy-Server unterstützen, und/oder eine <em>statusbehaftete Inspektion</em> anstelle von einfachen Paketfilterlösungen.</p> </li> 
     <li><p>Verwenden Sie eine Firewall, die ein Sicherheitsparadigma unterstützt, das <em>alle Services verweigert, außer denen, die ausdrücklich erlaubt sind</em>.</p> </li> 
     <li><p>Implementieren Sie eine Dual-Homed- oder Multi-Homed-Firewall-Lösung. Diese Architektur bietet ein Höchstmaß an Sicherheit und hilft zu verhindern, dass nicht berechtigte Benutzerinnen oder Benutzer die Firewall-Sicherheit umgehen.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Datenbank-Ports</p> </td> 
   <td><p>Verwenden Sie keine standardmäßigen Listening-Anschlüsse für Datenbanken (MySQL - 3306, Oracle - 1521, MS SQL - 1433). Informationen zum Ändern von Datenbank-Ports finden Sie in der Datenbankdokumentation.</p> <p>Die Verwendung eines anderen Datenbank-Ports wirkt sich auf die gesamte Konfiguration von AEM Forms on JEE aus. Wenn Sie die Standard-Ports ändern, müssen Sie entsprechende Änderungen in anderen Konfigurationsbereichen vornehmen, z. B. in den Datenquellen für AEM Forms on JEE.</p> <p>Informationen zum Konfigurieren von Datenquellen in AEM Forms auf JEE finden Sie unter „Installieren und Aktualisieren von AEM Forms auf JEE“ oder „Aktualisieren auf AEM Forms auf JEE“ für Ihren Programm-Server im <a href="/help/forms/using/introduction-aem-forms.md" target="_blank">AEM Forms-Benutzerhandbuch</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Betriebssystemsicherheit {#operating-system-security}

In der folgenden Tabelle werden mögliche Ansätze zum Verringern von Sicherheitslücken im Betriebssystem beschrieben.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p></th> 
   <th><p>Beschreibung</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Sicherheits-Patches</p></td> 
   <td><p>Wenn vom Hersteller bereitgestellte Sicherheits-Patches und -Aktualisierungen nicht zeitnah installiert werden, besteht ein erhöhtes Risiko, dass nicht autorisierte Benutzer Zugriff auf den Anwendungsserver erlangen. Testen Sie Sicherheits-Patches, bevor Sie sie auf Produktions-Server anwenden.</p><p>Erstellen Sie zudem Richtlinien und Prozeduren, damit regelmäßig Patches gesucht und installiert werden.</p></td> 
  </tr> 
  <tr> 
   <td><p>Virenschutz-Software</p></td> 
   <td><p>Virenscanner können infizierte Dateien erkennen, indem sie nach einer Signatur suchen oder ungewöhnliches Verhalten ermitteln. Virenscanner speichern die Virussignaturen in einer Datei, die in der Regel auf der lokalen Festplatte abgelegt wird. Da häufig neue Viren entdeckt werden, sollten Sie diese Datei regelmäßig aktualisieren, damit der Viren-Scanner alle aktuellen Viren erkennt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Network Time Protocol (NTP)</p></td> 
   <td><p>Für die forensische Analyse ist es erforderlich, dass die Uhrzeit auf den Formular-Servern exakt ist. Verwenden Sie NTP, um die Zeit auf allen Systemen zu synchronisieren, die direkt mit dem Internet verbunden sind.</p></td> 
  </tr> 
 </tbody> 
</table>

Weitere Informationen zur Sicherheit für Ihr Betriebssystem finden Sie unter [Informationen zur Betriebssystemsicherheit](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/general-security-considerations.html#operating_system_security_information).

## Installation {#installation}

In diesem Abschnitt werden Verfahren beschrieben, die Sie während des AEM Forms-Installationsprozesses verwenden können, um Sicherheitslücken zu schließen. In einigen Fällen nutzen diese Verfahren Optionen, die Teil des Installationsprozesses sind. Diese Verfahren werden in der folgenden Tabelle beschrieben.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Berechtigungen</p> </td> 
   <td><p>Verwenden Sie die Mindestanzahl an Berechtigungen, die für die Installation der Software erforderlich sind. Melden Sie sich über ein Benutzerkonto, das nicht zur Gruppe „Administratoren“ gehört, bei Ihrem Computer an. Unter Windows können Sie den Befehl „Run As“ verwenden, um das AEM Forms on JEE-Installationsprogramm als Benutzer mit Administratorrechten auszuführen. Auf UNIX- und Linux-Systemen verwenden Sie einen Befehl wie <code>sudo</code> für die Installation der Software.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Ursprung der Software</p> </td> 
   <td><p>Verwenden Sie zum Herunterladen oder Ausführen von AEM Forms on JEE nur vertrauenswürdige Quellen.</p> <p>Bösartige Programme können Code enthalten, der die Sicherheit auf verschiedene Weise verletzt, etwa durch Diebstahl, Ändern und Löschen von Daten sowie Dienstblockade (Denial of Service = DoS). Installieren Sie AEM Forms on JEE ausschließlich von der Adobe-DVD oder einer vertrauenswürdigen Quelle.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Festplattenpartitionen</p> </td> 
   <td><p>Platzieren Sie AEM Forms on JEE auf einer dedizierten Festplattenpartition. Die Festplattenaufteilung ist ein Prozess, bei dem bestimmte Daten auf dem Server auf separaten physischen Festplatten verwaltet werden, um die Sicherheit zu erhöhen. Durch eine solche Datenanordnung lässt sich das Risiko von Directory Traversal-Angriffen verringern. Planen Sie die Erstellung einer von der Systempartition getrennten Partition, auf der Sie das AEM Forms on JEE-Inhaltsverzeichnis installieren können. (Unter Windows enthält die Systempartition das Verzeichnis „system32“, das auch als Boot-Partition bezeichnet wird.)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Komponenten</p> </td> 
   <td><p>Prüfen Sie die vorhandenen Dienste und deaktivieren oder deinstallieren Sie nicht erforderliche Dienste. Installieren Sie keine unnötigen Komponenten und Dienste.</p> <p>Die Standardinstallation eines Anwendungsservers kann Dienste beinhalten, die Sie nicht benötigen. Sie sollten alle unnötigen Dienste vor der Bereitstellung deaktivieren, um die Einstiegspunkte für Angriffe zu minimieren. Auf JBoss können Sie beispielsweise unnötige Dienste in der Deskriptordatei „META-INF/jboss-service.xml“ auskommentieren.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Domain-übergreifende Richtliniendatei</p> </td> 
   <td><p>Das Vorhandensein einer Datei<code>crossdomain.xml</code> auf dem Server kann diesen Server unmittelbar schwächen. Es wird empfohlen, die Liste der Domains so weit wie möglich einzuschränken. Platzieren Sie die während der Entwicklungsphase verwendete <code>crossdomain.xml</code>-Datei nicht in der Produktionsumgebung, wenn Sie Guides verwenden <em>(nicht mehr unterstützt)</em>. Bei einem Guide, der Webdienste verwendet, wird keine <code>crossdomain.xml</code>-Datei benötigt, wenn sich der Dienst auf demselben Server befindet wie der Server, der den Guide zur Verfügung gestellt hat. Wenn es sich jedoch um einen anderen Dienst handelt oder wenn Cluster betroffen sind, muss eine <code>crossdomain.xml</code>-Datei vorhanden sein. Weitere Informationen zur Datei „crossdomain.xml“ finden Sie unter <a href="https://kb2.adobe.com/cps/142/tn_14213.html">https://kb2.adobe.com/cps/142/tn_14213.html</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Sicherheitseinstellungen des Betriebssystems</p> </td> 
   <td><p>Wenn Sie 192-Bit- oder 256-Bit-XML-Verschlüsselung auf Solaris-Plattformen verwenden müssen, sollten Sie sicherstellen, dass Sie <code>pkcs11_softtoken_extra.so</code> anstelle von <code>pkcs11_softtoken.so</code> installieren.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Schritte nach der Installation {#post-installation-steps}

Nachdem Sie AEM Forms on JEE erfolgreich installiert haben, sollten Sie die Sicherheitseinrichtungen der Umgebung unbedingt in regelmäßigen Abständen warten.

Im folgenden Abschnitt werden die verschiedenen Aufgaben, die zum Schützen des bereitgestellten Formular-Servers empfohlen werden, ausführlich beschrieben.

### Sicherheit von AEM Forms {#aem-forms-security}

Die folgenden empfohlenen Einstellungen gelten für den AEM Forms on JEE-Server außerhalb der Verwaltungs-Webanwendung. Um die Sicherheitsrisiken für den Server zu verringern, wenden Sie diese Einstellungen unmittelbar nach der Installation von AEM Forms on JEE an.

**Sicherheits-Patches**

Wenn vom Hersteller bereitgestellte Sicherheits-Patches und -Aktualisierungen nicht zeitnah installiert werden, besteht ein erhöhtes Risiko, dass nicht autorisierte Benutzer Zugriff auf den Anwendungsserver erlangen. Testen Sie Sicherheits-Patches, bevor Sie sie auf Produktions-Server anwenden, um die Kompatibilität und Verfügbarkeit von Anwendungen sicherzustellen. Erstellen Sie zudem Richtlinien und Prozeduren, damit Patches regelmäßig gesucht und installiert werden. Aktualisierungen für AEM Forms on JEE finden Sie auf der Download-Site für Enterprise-Produkte.

**Dienstkonten (nur JBoss-Turnkey unter Windows)**

AEM Forms on JEE installiert standardmäßig einen Dienst unter Verwendung des LocalSystem-Kontos. Das integrierte Benutzerkonto „Lokales System“ hat hohe Zugriffsrechte; es gehört zur Gruppe „Administratoren“. Wenn eine Worker Process-Identität als das Benutzerkonto „LocalSystem“ ausgeführt wird, hat dieser Worker Process vollen Zugriff auf das gesamte System.

Um den Anwendungs-Server, auf dem AEM Forms on JEE bereitgestellt wird, mit einem bestimmten Konto ohne Administratorrechte auszuführen, führen Sie die folgenden Anweisungen aus:

1. Erstellen Sie in der Microsoft Management Console (MMC) einen lokalen Benutzer für den Formular-Server-Dienst, der sich wie folgt anmeldet:

   * Wählen Sie **Benutzer kann Passwort nicht ändern** aus.
   * Stellen Sie sicher, dass auf der Registerkarte **Mitglied von** die Gruppe **Benutzer** aufgeführt ist.

   >[!NOTE]
   >
   >Sie können diese Einstellung für PDF Generator nicht ändern.

1. Wählen Sie **Starten** > **Einstellungen** > **Admin Tools** > **Dienste** aus.
1. Doppelklicken Sie auf JBoss für AEM Forms on JEE und beenden Sie den Dienst.
1. Wählen Sie auf der Registerkarte **Anmelden** die Option **Dieses Konto** aus, suchen Sie das von Ihnen erstellte Benutzerkonto und geben Sie das Passwort für das Konto ein.
1. Öffnen Sie im MMC die Option **Lokale Sicherheitseinstellungen** und wählen Sie **Lokale Richtlinien** > **Zuweisen von Benutzerrechten** aus.
1. Weisen Sie dem Benutzerkonto, unter dem der Formular-Server ausgeführt wird, die folgenden Berechtigungen zu:

   * Anmeldung über Terminal-Dienste verweigern
   * Lokale Anmeldung verweigern
   * Als Dienst anmelden (sollte bereits festgelegt sein)

1. Weisen Sie dem neuen Benutzerkonto Berechtigungen zum Ändern der folgenden Verzeichnisse zu:
   * **Verzeichnis des globalen Dokumentenspeichers (GDS)**: Der Speicherort des GDS-Verzeichnisses wird während der Installation von AEM Forms manuell konfiguriert. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Verzeichnis unter dem Installationsverzeichnis des Anwendungsservers gewählt: `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository-Verzeichnis**: Der Standardspeicherort lautet `[AEM-Forms-installation-location]\crx-repository`
   * **Temporäre Verzeichnisse von AEM Forms**:
      * (Windows) TMP- oder TEMP-Pfad gemäß Einstellung in den Umgebungsvariablen
      * (AIX, Linux oder Solaris) Basisordner der angemeldeten Person
Auf UNIX-basierten Systemen kann eine Benutzerin oder ein Benutzer ohne Stammordner den folgenden Ordner als temporären Ordner verwenden:
      * (Linux) /var/tmp oder /usr/tmp
      * (AIX) /tmp oder /usr/tmp
      * (Solaris) /var/tmp oder /usr/tmp
1. Weisen Sie dem neuen Benutzerkonto Schreibberechtigungen für die folgenden Verzeichnisse zu:
   * [JBoss-directory]\standalone\deployment
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\

   >[!NOTE]
   >
   >Der standardmäßige Installationsspeicherort von JBoss Application Server ist folgender:
   >
   >* Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   >* Linux: /opt/jboss/

1. Starten Sie den Anwendungs-Server.

**Deaktivieren des Bootstrap-Servlets von Configuration Manager**

Configuration Manager verwendete ein auf Ihrem Anwendungsserver bereitgestelltes Servlet, um das Bootstrapping der AEM Forms on JEE-Datenbank durchzuführen. Da Configuration Manager auf dieses Servlet zugreift, bevor die Konfiguration abgeschlossen ist, wurde der Zugriff darauf für autorisierte Benutzerinnen und Benutzer nicht gesichert und sollte deswegen deaktiviert werden, nachdem Sie Configuration Manager erfolgreich für die Konfiguration von AEM Forms on JEE verwendet haben.

1. Dekomprimieren Sie die Datei „adobe-livecycle-[Programm-Server].ear“.
1. Öffnen Sie die Datei META-INF/application.xml.
1. Suchen Sie den Abschnitt adobe-bootstrapper.war:

   ```java
   <!-- bootstrapper start --> 
   <module id="WebApp_adobe_bootstrapper"> 
       <web> 
           <web-uri>adobe-bootstrapper.war</web-uri> 
           <context-root>/adobe-bootstrapper</context-root> 
       </web> 
   </module> 
   <module id="WebApp_adobe_lcm_bootstrapper_redirector"> 
       <web> 
           <web-uri>adobe-lcm-bootstrapper-redirector.war</web-uri> 
           <context-root>/adobe-lcm-bootstrapper</context-root> 
       </web> 
   </module> 
   <!-- bootstrapper end-->
   ```

1. Beenden Sie den AEM Forms-Server.
1. Kommentieren Sie die Module „adobe-bootstrapper.war“ und „adobe-lcm-bootstrapper-redirectory.war“ aus. wie folgt aus:

   ```java
   <!-- bootstrapper start --> 
   <!-- 
   <module id="WebApp_adobe_bootstrapper"> 
       <web> 
           <web-uri>adobe-bootstrapper.war</web-uri> 
           <context-root>/adobe-bootstrapper</context-root> 
       </web> 
   </module> 
   <module id="WebApp_adobe_lcm_bootstrapper_redirector"> 
       <web> 
           <web-uri>adobe-lcm-bootstrapper-redirector.war</web-uri> 
           <context-root>/adobe-lcm-bootstrapper</context-root> 
       </web> 
   </module> 
   --> 
   <!-- bootstrapper end-->
   ```

1. Speichern und schließen Sie die Datei „META-INF/application.xml“.
1. Komprimieren Sie die EAR-Datei und stellen Sie sie erneut auf dem Anwendungs-Server bereit.
1. Starten Sie den AEM Forms-Server.
1. Geben Sie die nachstehende URL in einen Browser ein, um die Änderung zu testen und sicherzustellen, dass sie nicht mehr funktioniert.

   https://&lt;localhost>:&lt;port>/adobe-bootstrapper/bootstrap

**Sperren des Remote-Zugriffs auf den Trust Store**

Configuration Manager ermöglicht Ihnen, eine Berechtigung für Acrobat Reader DC Extensions in den Trust Store von AEM Forms on JEE hochzuladen. Das bedeutet, dass der Zugriff auf den Trust Store-Berechtigungsdienst über Remote-Protokolle (SOAP und EJB) standardmäßig aktiviert wurde. Dieser Zugriff ist nicht mehr notwendig, nachdem Sie die Berechtigung für Berechtigungsnachweise mithilfe von Configuration Manager hochgeladen haben, oder wenn Sie beschließen, Berechtigungen später mit der Administration-Console zu verwalten.

Sie können den Remote-Zugriff auf alle Trust Store-Dienste deaktivieren, indem Sie die Schritte im Abschnitt [Deaktivieren von nicht erforderlichem Remote-Zugiff auf Dienste](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_remote_access_to_services) befolgen.

**Deaktivieren von nicht erforderlichem anonymen Zugriff**

Einige Formular-Server-Dienste verfügen über Vorgänge, die von einem anonymen Aufrufer aufgerufen werden können. Wenn kein anonymer Zugriff auf diese Dienste erforderlich ist, deaktivieren Sie ihn, indem Sie die Schritte unter [Deaktivieren von nicht erforderlichem anonymen Zugriff auf Dienste](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_anonymous_access_to_services) befolgen.

#### Ändern des Standardpasswort für Admins {#change-the-default-administrator-password}

Beim Installieren von AEM Forms on JEE wird ein Standardbenutzerkonto für den Benutzer „Superadministrator“ mit der Anmelde-ID „Administrator“ und dem Standardkennwort *password* erstellt. Sie sollten dieses Passwort sofort mithilfe von Configuration Manager ändern.

1. Geben Sie die folgende URL in einen Webbrowser ein:

   ```java
   https://[host name]:[port]/adminui
   ```

   Die standardmäßige Port-Nummer ist eine der folgenden:

   **JBoss**: 8080

   **WebLogic Server:** 7001

   **WebSphere:** 9080.

1. Geben Sie in das Feld **Benutzername** den Wert `administrator` und in das Feld **Kennwort** den Wert `password` ein.
1. Klicken Sie auf **Einstellungen** > **User Management** > **Benutzer und Gruppen**.
1. Geben Sie den Begriff `administrator` in das Feld **Suchen** ein und klicken Sie auf **Suchen**.
1. Klicken Sie in der Benutzerliste auf **Superadministrator**.
1. Klicken Sie auf der Seite „Benutzer bearbeiten“ auf **Passwort ändern**.
1. Geben Sie das neue Passwort an und klicken Sie auf **Speichern**.

Darüber hinaus wird empfohlen, das Standardpasswort für CRX Administrator zu ändern, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich bei `https://[server]:[port]/lc/libs/granite/security/content/useradmin.html` mit dem standardmäßigen Benutzernamen/Kennwort an.
1. Geben Sie „Administrator“ in das Suchfeld ein und klicken Sie auf **Suchen**.
1. Wählen Sie **Administrator** aus dem Suchergebnis und klicken Sie auf das Symbol **Bearbeiten** unten rechts auf der Benutzeroberfläche.
1. Geben Sie das neue Kennwort in das Feld **Neues Kennwort** und das alte Kennwort in das Feld **Ihr Kennwort** ein.
1. Klicken Sie auf das Symbol „Speichern“ unten rechts auf der Benutzeroberfläche.

#### Deaktivieren der WSDL-Generierung {#disable-wsdl-generation}

Die WSDL-Generierung (Web Service Definition Language) sollte nur in Entwicklungsumgebungen aktiviert sein, in denen Entwickler mithilfe der WSDL-Generierung Clientanwendungen erstellen. Sie können die WSDL-Generierung in einer Produktionsumgebung deaktivieren, um zu vermeiden, dass interne Details eines Dienstes offengelegt werden.

1. Geben Sie die folgende URL in einen Webbrowser ein:

   ```java
   https://[host name]:[port]/adminui
   ```

1. Klicken Sie auf **Einstellungen > Core-Systemeinstellungen > Konfigurationen**.
1. Deaktivieren Sie **WSDL aktivieren** und klicken Sie auf **OK**.

### Sicherheit des Anwendungs-Servers {#application-server-security}

In der folgenden Tabelle werden einige Verfahren zum Schützen des Anwendungs-Servers nach der Installation der AEM Forms on JEE-Anwendung beschrieben.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Verwaltungskonsole des Anwendungs-Servers</p> </td> 
   <td><p>Nach der Installation, Konfiguration und Bereitstellung von AEM Forms on JEE auf dem Anwendungsserver müssen Sie den Zugriff auf die Verwaltungskonsolen des Anwendungsservers deaktivieren. Weitere Informationen finden Sie in der Dokumentation zu Ihrem jeweiligen Anwendungs-Server.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Cookie-Einstellungen des Anwendungs-Servers</p> </td> 
   <td><p>Anwendungs-Cookies werden vom Anwendungsserver gesteuert. Beim Bereitstellen der Anwendung kann der Administrator des Anwendungsservers Cookie-Voreinstellungen serverweit oder anwendungsspezifisch festlegen. Standardmäßig haben die Server-Einstellungen Vorrang.</p> <p>Alle vom Anwendungsserver erstellten Sitzungs-Cookies müssen das <code>HttpOnly</code>-Attribut enthalten. Wenn Sie beispielsweise den JBoss Application Server verwenden, können Sie das Element „SessionCookie“ in der Datei <code>WEB-INF/web.xml</code> auf <code>httpOnly="true"</code> ändern.</p> <p>Sie können festlegen, dass Cookies ausschließlich unter Verwendung von HTTPS gesendet werden. Dadurch wird verhindert, dass Cookies unverschlüsselt über HTTP gesendet werden. Anwendungsserveradministratoren sollten sichere Cookies für den Server global aktivieren. Bei Verwendung des JBoss-Anwendungsservers können Sie beispielsweise das Element „connector“ in der Datei <code>secure=true</code> in <code>server.xml</code> ändern.</p> <p>Weitere Informationen zu Cookie-Einstellungen finden Sie in der Dokumentation zum Anwendungs-Server.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Directory Browsing</p> </td> 
   <td><p>Wenn eine Person eine nicht vorhandene Seite oder den Namen eines Ordners anfordert (die Anforderungszeichenfolge endet in diesem Fall mit einem Schrägstrich (/)), sollte der Anwendungsserver den Inhalt dieses Ordners nicht zurückgeben. Damit dies nicht geschieht, können Sie das Directory Browsing auf Ihrem Anwendungsserver deaktivieren. Dies sollten Sie für die Administration-Console-Anwendung und für andere Anwendungen tun, die auf Ihrem Server ausgeführt werden.</p> <p>Für JBoss stellen Sie in der Datei „web.xml“ den Wert des Auflistungsinitialisierungsparameters der Eigenschaft <code>DefaultServlet</code> auf <code>false</code> ein, wie im folgenden Beispiel gezeigt wird:</p> <p>&lt;servlet&gt;</p> <p>&lt;servlet-name&gt;default&lt;/servlet-name&gt;</p> <p>&lt;servlet-class&gt;</p> <p>org.apache.catalina.servlets.DefaultServlet</p> <p>&lt;/servlet-class&gt;</p> <p>&lt;init-param&gt;</p> <p>&lt;param-name&gt;listings&lt;/param-name&gt;</p> <p>&lt;param-value&gt;false&lt;/param-value&gt;</p> <p>&lt;/init-param&gt;</p> <p>&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;</p> <p>&lt;/servlet&gt;</p> <p>Für WebSphere stellen Sie in der Datei „ibm-web-ext.xml“ die Eigenschaft <code>directoryBrowsingEnabled</code> auf <code>false</code> ein.</p> <p>Für WebLogic stellen Sie in der Datei „weblogic.xml“ die Eigenschaften zu „index-directories“ auf <code>false</code> ein, wie im folgenden Beispiel gezeigt:</p> <p>&lt;container-descriptor&gt;</p> <p>&lt;index-directory-enabled&gt;false</p> <p>&lt;/index-directory-enabled&gt;</p> <p>&lt;/container-descriptor&gt;</p> </td> 
  </tr> 
 </tbody> 
</table>

### Datenbanksicherheit {#database-security}

Beim Schützen der Datenbank sollten Sie die vom Datenbankhersteller beschriebenen Sicherheitsmaßnahmen implementieren. Sie sollten einem Datenbankbenutzer die minimal für die Verwendung von AEM Forms on JEE erforderlichen Datenbankberechtigungen zuweisen. Verwenden Sie beispielsweise kein Konto mit Datenbankadministrator-Berechtigungen.

Unter Oracle benötigt das verwendete Datenbankkonto nur die Berechtigungen CONNECT, RESOURCE und CREATE VIEW. Für ähnliche Anforderungen an andere Datenbanken siehe [Vorbereiten der Installation von AEM Forms on JEE (Einzel-Server)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64_de).

#### Konfigurieren der integrierten Sicherheit für SQL Server unter Windows für JBoss {#configuring-integrated-security-for-sql-server-on-windows-for-jboss}

1. Ändern Sie [JBOSS_HOME]\\standalone\configuration\lc_{datasource.xml}, um `integratedSecurity=true` zur Verbindungs-URL hinzuzufügen, wie in diesem Beispiel gezeigt:

   ```java
    jdbc:sqlserver://<serverhost>:<port>;databaseName=<dbname>;integratedSecurity=true
   ```

1. Fügen Sie die Datei „sqljdbc_auth.dll“ zum Windows-Systempfad (C:\Windows) auf dem Computer hinzu, auf dem der Anwendungsserver ausgeführt wird. Die Datei „sqljdbc_auth.dll“ wird zusammen mit dem Microsoft SQL JDBC 6.2.1.0-Treiber installiert.
1. Ändern Sie die Eigenschaft des JBoss Windows-Dienstes (JBoss for AEM Forms on JEE) für „Anmelden als“ von „Lokales System“ in ein Anmeldekonto mit einer AEM Forms-Datenbank und einem Mindestsatz von Berechtigungen. Wenn Sie JBoss von der Befehlszeile und nicht als Windows-Dienst ausführen, ist dieser Schritt nicht erforderlich.
1. Ändern Sie die Sicherheitseinstellung von SQL Server von **Gemischt** in **Nur Windows-Authentifizierung**.

#### Integrierte Sicherheit für SQL Server unter Windows für WebLogic konfigurieren  {#configuring-integrated-security-for-sql-server-on-windows-for-weblogic}

1. Starten Sie die Administration-Console von WebLogic Server, indem Sie die folgende URL in die Adresszeile eines Webbrowsers eingeben:

   ```java
   https://[host name]:7001/console
   ```

1. Klicken Sie unter „Change Center“ auf **Lock &amp; Edit**.
1. Klicken Sie unter „Domain Structure“ auf *[base_domain]* > **Services** > **JDBC** > **Data Sources** und im rechten Bereich auf **IDP_DS**.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte **Configuration** und dann auf die Registerkarte **Connection Pool**. Geben Sie in das Feld **Properties** den Eintrag `integratedSecurity=true` ein.
1. Klicken Sie unter „Domain Structure“ auf **[base_domain]** > **Services** > **JDBC** > **Data Sources** und klicken Sie im rechten Bereich auf **RM_DS**.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarte **Configuration** und dann auf die Registerkarte **Connection Pool**. Geben Sie in das Feld **Properties** den Eintrag `integratedSecurity=true` ein.
1. Fügen Sie die Datei „sqljdbc_auth.dll“ zum Windows-Systempfad (C:\Windows) auf dem Computer hinzu, auf dem der Anwendungsserver ausgeführt wird. Die Datei „sqljdbc_auth.dll“ wird zusammen mit dem Microsoft SQL JDBC 6.2.1.0-Treiber installiert.
1. Ändern Sie die Sicherheitseinstellung von SQL Server von **Gemischt** in **Nur Windows-Authentifizierung**.

#### Konfigurieren der integrierten Sicherheit für SQL Server unter Windows für WebSphere {#configuring-integrated-security-for-sql-server-on-windows-for-websphere}

Unter WebSphere können Sie die integrierte Sicherheit nur dann konfigurieren, wenn Sie einen externen JDBC-Treiber für SQL Server und nicht den in WebSphere eingebetteten JDBC-Treiber für SQL Server verwenden.

1. Melden Sie sich bei WebSphere Administrative Console an.
1. Klicken Sie in der Navigationsstruktur auf **Resources** > **JDBC** > **Data Sources** und klicken Sie dann im rechten Bereich auf **IDP_DS**.
1. Klicken Sie im rechten Bereich unter „Additional Properties“ auf **Custom Properties** und dann auf **New**.
1. Geben Sie in das Feld **Name** den Wert `integratedSecurity` und in das Feld **Value** den Wert `true` ein.
1. Klicken Sie in der Navigationsstruktur auf **Resources** > **JDBC** > **Data Sources** und dann im rechten Bereich auf **RM_DS**.
1. Klicken Sie im rechten Bereich unter „Additional Properties“ auf **Custom Properties** und dann auf **New**.
1. Geben Sie in das Feld **Name** den Wert `integratedSecurity` und in das Feld **Value** den Wert `true` ein.
1. Fügen Sie auf dem Computer, auf dem WebSphere installiert ist, die Datei „sqljdbc_auth.dll“ dem Windows-Systempfad (C:\Windows) hinzu. Die Datei „sqljdbc_auth.dll“ befindet sich am selben Speicherort wie die Microsoft SQL JDBC 1.2-Treiberinstallation (standardmäßig unter *[Installationsordner]*/sqljdbc_1.2/enu/auth/x86).
1. Wählen Sie **Start** > **Systemsteuerung** > **Dienste** aus, klicken Sie mit der rechten Maustaste auf den Windows-Dienst für WebSphere (IBM WebSphere Application Server &lt;Version> - &lt;Knoten>) und wählen Sie **Eigenschaften** aus.
1. Klicken Sie im Dialogfeld „Eigenschaften“ auf die Registerkarte **Anmelden**.
1. Wählen Sie **Dieses Konto** aus und geben Sie die benötigten Informationen ein, um das gewünschte Anmeldekonto festzulegen.
1. Ändern Sie den Sicherheitsmodus von SQL Server von **Gemischt** in **Nur Windows-Authentifizierung**.

### Schützen des Zugriffs auf sensible Inhalte in der Datenbank {#protecting-access-to-sensitive-content-in-the-database}

Das AEM Forms-Datenbankschema enthält sensible Informationen über die Systemkonfiguration und Geschäftsprozesse und sollte hinter der Firewall geschützt sein. Für die Datenbank sollte dieselbe Sicherheitsstufe wie für den Formular-Server gelten. Um die Offenlegung von Informationen und den Diebstahl von Geschäftsdaten zu verhindern, muss die Datenbank vom DBA (Datenbankadministrator) so konfiguriert werden, dass nur autorisierte Admins Zugriff haben.

Als zusätzliche Sicherheitsmaßnahme sollten Sie überlegen, spezifische Werkzeuge des Datenbankherstellers für die Verschlüsselung von Spalten in Tabellen zu verwenden, die folgende Daten enthalten:

* Rights Management-Dokumentschlüssel
* PIN-Verschlüsselungsschlüssel für HSM-Geräte im Trust Store
* Hashes für lokale Benutzerkennwörter

Informationen zu herstellerspezifischen Tools finden Sie unter [Informationen zur Datenbanksicherheit](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/general-security-considerations.html#database_security_information).

### LDAP-Sicherheit {#ldap-security}

AEM Forms on JEE nutzt meist einen LDAP-Ordner (Lightweight Directory Access Protocol) als Quelle für Informationen über Unternehmensbenutzer und Gruppen sowie zur Durchführung der Kennwortauthentifizierung. Sie sollten sicherstellen, dass Ihr LDAP-Ordner für die Verwendung von Secure Socket Layer (SSL) konfiguriert ist und AEM Forms on JEE für den Zugriff auf das LDAP-Verzeichnis über dessen SSL-Port konfiguriert ist.

#### LDAP-Dienstverweigerung {#ldap-denial-of-service}

Angriffe mittels LDAP bestehen häufig darin, dass ein Angreifer die Authentifizierung bewusst mehrmals fehlschlagen lässt. Dies zwingt den LDAP-Verzeichnis-Server, eine Benutzerin bzw. einen Benutzer für alle auf LDAP basierenden Dienste zu sperren.

Sie können die Anzahl fehlgeschlagener Versuche sowie die nachfolgende Sperrdauer festlegen, die AEM Forms implementiert, wenn die AEM Forms-Authentifizierung eines Benutzers wiederholt fehlschlägt. Wählen Sie in der Administration-Console niedrige Werte. Bei der Auswahl der Anzahl fehlgeschlagener Versuche ist zu beachten, dass nach allen Versuchen die Benutzerin bzw. der Benutzer durch AEM Forms gesperrt wird, bevor dies durch den LDAP-Verzeichnis-Server erfolgt.

#### Festlegen der automatischen Kontosperrung {#set-automatic-account-locking}

1. Melden Sie sich bei Administration Console an.
1. Klicken Sie auf **Einstellungen** > **User Management** > **Domain-Verwaltung**.
1. Legen Sie unter „Einstellungen für die automatische Kontosperrung“ die Option **Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler** auf eine niedrige Zahl, wie etwa 3, fest.
1. Klicken Sie auf **Speichern**.

### Auditing und Protokollierung {#auditing-and-logging}

Der richtige und sichere Einsatz der Anwendungsprüfung und -protokollierung kann dazu beitragen, dass sicherheitsrelevante und andere, unnormale Ereignisse schnellstmöglich verfolgt und erkannt werden. Die effektive Verwendung von Prüfung und Protokollierung innerhalb einer Anwendung umfasst Elemente wie das Verfolgen erfolgreicher und fehlgeschlagener Anmeldungen sowie wichtige Anwendungsereignisse wie das Erstellen oder Löschen von Schlüsseldatensätzen.

Sie können das Auditing verwenden, um viele Arten von Angriffen zu erkennen, darunter die folgenden:

* Brute-Force-Passwortangriffe
* Denial-of-Service-Angriffe
* Einschleusen von feindseligen Eingaben und ähnliche Klassen von Skriptangriffen

In dieser Tabelle werden Auditing- und Protokollierungsverfahren beschrieben, mit denen Sie die Sicherheitsanfälligkeit Ihres Servers verringern können.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Zugriffssteuerungslisten für Protokolldateien</p> </td> 
   <td><p>Legen Sie die entsprechenden Zugriffssteuerungslisten (ACLs) für die Protokolldateien von AEM Forms on JEE fest.</p> <p>Das Festlegen der entsprechenden Anmeldeinformationen verhindert, dass Angreiferinnen oder Angreifer die Dateien löschen.</p> <p>Als Sicherheitsberechtigung für das Protokolldateiordner sollte „Alle Berechtigungen“ für Administratoren und SYSTEM-Gruppen festgelegt werden. Das AEM Forms-Benutzerkonto sollte nur Lese- und Schreibberechtigungen besitzen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Redundanz der Protokolldateien</p> </td> 
   <td><p>Wenn die Ressourcen dies zulassen, senden Sie Protokolle in Echtzeit an einen anderen Server, auf den die angreifende Person keinen Zugriff hat (nur Schreiben), indem Sie Syslog, Tivoli, den MOM-Server (Microsoft Operations Manager) oder einen anderen Mechanismus verwenden.</p> <p>Wenn Sie Protokolle auf diese Weise schützen, erschweren Sie damit mögliche Manipulationen. Das Speichern von Protokollen in einem zentralen Repository erleichtert zudem die Korrelation und Überwachung (z. B. wenn mehrere Formular-Server verwendet werden und ein Angriff zum Erraten von Passwörtern auf mehreren Computern stattfindet, bei dem von jedem Computer ein Passwort abgefragt wird).</p> </td> 
  </tr> 
 </tbody> 
</table>

### Aktivieren der Ausführung von PDF Generator durch Nicht-Administrator-Benutzende

Sie können Benutzerinnen und Benutzern, die keine Admins sind, die Verwendung des PDF Generator-Dienstes erlauben. Normalerweise können nur Benutzende mit Administratorrechten den Dienst verwenden. Führen Sie die folgenden Schritte aus, um Benutzerinnen und Benutzern ohne Administratorrechte die Ausführung von PDF Generator zu ermöglichen:

1. Erstellen Sie den Umgebungsvariablennamen PDFG_NON_ADMIN_ENABLED.

1. Legen Sie als Wert der Variablen TRUE fest.

1. Starten Sie die AEM Forms-Instanz neu.

## Konfigurieren von AEM Forms on JEE für den Zugriff außerhalb des Unternehmens {#configuring-aem-forms-on-jee-for-access-beyond-the-enterprise}

Nachdem Sie AEM Forms on JEE erfolgreich installiert haben, müssen Sie die Sicherheitseinrichtungen der Umgebung unbedingt in regelmäßigen Abständen warten. In diesem Abschnitt werden die empfohlenen Aufgaben zur Gewährleistung der Sicherheit Ihres AEM Forms on JEE-Produktions-Servers beschrieben.

### Einrichten eines Reverse-Proxys für den Web-Zugang {#setting-up-a-reverse-proxy-for-web-access}

Sie können einen *Reverse-Proxy* verwenden, um sicherzustellen, dass eine Gruppe von URLs für AEM Forms on JEE-Webanwendungen sowohl für externe als auch interne Benutzer verfügbar ist. Diese Konfiguration bietet mehr Sicherheit als die Erlaubnis für Benutzer, eine direkte Verbindung zu dem Anwendungsserver herzustellen, auf dem AEM Forms on JEE ausgeführt wird. Der Reverse-Proxy führt alle HTTP-Anfragen für den Anwendungsserver durch, auf dem AEM Forms on JEE läuft. Benutzerinnen und Benutzer haben nur Netzwerkzugriff auf den Reverse-Proxy und können nur URL-Verbindungen versuchen, die vom Reverse-Proxy unterstützt werden.

**Stammordner-URLs in AEM Forms auf JEE für die Verwendung mit dem Reverse-Proxy-Server**

Die folgenden Anwendungsstamm-URLs für jede Web-Anwendung von AEM Forms on JEE. Sie sollten Ihren Reverse-Proxy so konfigurieren, dass nur URLs für Web-Anwendungsfunktionen verfügbar gemacht werden, die Sie Endbenutzerinnen und Endbenutzern bereitstellen möchten.

Einige URLs sind als Endbenutzer-orientierte Webanwendungen gekennzeichnet. Sie sollten vermeiden, andere URLs für Configuration Manager für den externen Benutzerzugriff über den Reverse-Proxy verfügbar zu machen.

<table> 
 <thead> 
  <tr> 
   <th><p>Stamm-URL</p> </th> 
   <th><p>Zweck und/oder verknüpfte Web-Anwendung</p> </th> 
   <th><p>Web-basierte Benutzeroberfläche</p> </th> 
   <th><p>Endbenutzerzugriff</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>/ReaderExtensions/*</p> </td> 
   <td><p>Acrobat Reader DC-Erweiterungen – Web-Anwendung für Endbenutzerinnen und Endbenutzer zum Anwenden von Verwendungsrechten auf PDF-Dokumente</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/*</p> </td> 
   <td><p>Rights Management – Web-Anwendung für Endbenutzerinnen und Endbenutzer</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edcws/*</p> </td> 
   <td><p>Web-Dienst-URL für Rights Management</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/pdfgui/*</p> </td> 
   <td><p>PDF Generator – Web-Anwendung für die Administration</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/Arbeitsbereich/*</p> </td> 
   <td><p>Workspace – Web-Anwendung für Endbenutzerinnen und Endbenutzer</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/workspace-server/*</p> </td> 
   <td><p>Workspace-Servlets und -Datendienste, die von der Workspace-Client-Anwendung benötigt werden</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/adobe-bootstrapper/*</p> </td> 
   <td><p>Servlet für das Bootstrapping des Repositorys von AEM Forms on JEE</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/SOAP/*</p> </td> 
   <td><p>Informationsseite für Formular-Server-Web-Dienste</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/soap/services/*</p> </td> 
   <td><p>Web-Dienst-URL für alle Formular-Server-Dienste</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/admin/*</p> </td> 
   <td><p>Rights Management – Web-Anwendung für die Administration</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/adminui/*</p> </td> 
   <td><p>Administration Console-Startseite</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/TruststoreComponent/</p> <p>secured/*</p> </td> 
   <td><p>Verwaltungsseiten für die Trust Store-Verwaltung</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormsIVS/*</p> </td> 
   <td><p>Forms IVS – Anwendung zum Testen und Debuggen der Formularwiedergabe</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/OutputIVS/*</p> </td> 
   <td><p>Output IVS – Anwendung zum Testen und Debuggen des Output-Dienstes</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/rmws/*</p> </td> 
   <td><p>REST-URL für Rights Management</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/OutputAdmin/*</p> </td> 
   <td><p>Output-Verwaltungsseiten</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServer/*</p> </td> 
   <td><p>Dateien für die Forms-Web-Anwendung</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServer/GetImage</p> <p>Servlet</p> </td> 
   <td><p>Dient zum Abrufen von JavaScript während der HTML-Transformation</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServerAdmin/*</p> </td> 
   <td><p>Forms-Verwaltungsseiten</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/repository/*</p> </td> 
   <td><p>URL für WebDAV-Zugriff (Debugging)</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/AACComponent/*</p> </td> 
   <td><p>Anwendungen und Dienste – Benutzeroberfläche</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/WorkspaceAdmin/*</p> </td> 
   <td><p>Workspace-Verwaltungsseiten</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/rest/*</p> </td> 
   <td><p>Rest-Supportseiten</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/CoreSystemConfig/*</p> </td> 
   <td><p>Seite mit den Core-Konfigurationseinstellungen für AEM Forms on JEE</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/um/</p> </td> 
   <td><p>User Management-Authentifizierung</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/um/*</p> </td> 
   <td><p>User Management-Verwaltungsoberfläche</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/DocumentManager/*</p> </td> 
   <td><p>Hoch- und Herunterladen von zu verarbeitenden Dokumenten beim Zugriff auf Remoting-Endpunkte, SOAP WSDL-Endpunkte und das Java-SDK mittels SOAP-Transport oder EJB-Transport bei aktivierten HTTP-Dokumenten.</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
 </tbody> 
</table>

## Schützen vor Angriffen durch Cross-Site Request Forgery {#protecting-from-cross-site-request-forgery-attacks}

Bei einem Cross-Site Request Forgery-Angriff (CSRF) wird die Vertrauensstellung einer Website für den Benutzer ausgenutzt, um Befehle zu übertragen, die vom Benutzer nicht autorisiert wurden und vom Benutzer nicht beabsichtigt sind. Dazu wird ein Link oder ein Skript in eine Web-Seite bzw. eine URL in eine E-Mail-Nachricht eingefügt, um auf eine andere Website zuzugreifen, für die der Benutzer bereits authentifiziert wurde.

Sie könnten beispielsweise bei der Administration-Console angemeldet sein und gleichzeitig eine andere Website durchsuchen. Eine der Webseiten kann ein HTML-Bild-Tag mit einem `src`-Attribut enthalten, dessen Ziel ein serverseitiges Skript auf einer Opfer-Website ist. Durch die Verwendung des Cookie-basierten Sitzungsauthentifizierungsmechanismus, der von Webbrowsern bereitgestellt wird, kann die angreifende Website böswillige Anfragen an dieses serverseitige Opferskript senden, das sich als legitimer Benutzer ausgibt. Weitere Beispiele finden Sie unter [https://owasp.org/www-community/attacks/csrf#Examples](https://owasp.org/www-community/attacks/csrf#Examples).

Die folgenden Merkmale sind für CSRF-Angriffe charakteristisch:

* Betreffen Sites, die auf die Identität einer Benutzerin oder eines Benutzers angewiesen sind.
* Nutzen das Vertrauen der Site in diese Identität.
* Verleiten den Browser der Benutzerin oder des Benutzers dazu, HTTP-Anfragen an eine Ziel-Site zu senden.
* Beinhalten HTTP-Anfragen, die Nebeneffekte haben.

AEM Forms auf JEE verwendet die Referrer-Filter-Funktion, um CSRF-Angriffe abzuwehren. Die folgenden Begriffe werden in diesem Abschnitt zum Beschreiben der Referrer-Filter-Funktion verwendet:

* **Zulässiger Referrer**: Ein Referrer ist die Adresse der Quellseite, die eine Anforderung an den Server sendet. Bei JSP-Seiten oder -Formularen ist der Referrer in der Regel die vorherige Seite im Browser-Verlauf. Referrer für Bilder sind in der Regel die Seiten, auf denen die Bilder angezeigt werden. Sie können Referrer, die auf Ihre Server-Ressourcen zugreifen dürfen, identifizieren, indem Sie sie zur Liste der zulässigen Referrer hinzufügen.
* **Zulässige Referrer – Ausnahmen**: Möglicherweise möchten Sie den Zugriffsbereich für einen bestimmten Referrer in Ihrer Liste der zulässigen Referrer einschränken. Um diese Einschränkung vorzunehmen, können Sie einzelne Pfade dieses Referrers zur Liste „Zulässige Referrer – Ausnahmen“ hinzufügen. Anforderungen, die von Pfaden in der Liste „Zulässige Referrer – Ausnahmen“ stammen, können keine Ressourcen auf dem Formular-Server aufrufen. Sie können Ausnahmen zu zulässigen Referrern für ein bestimmtes Programm definieren und zudem eine globale Liste mit Ausnahmen verwenden, die für alle Programme gilt.
* **Zulässige URIs**: Hierbei handelt es sich um eine Liste mit Ressourcen, die ohne Prüfung der Referrer-Kopfzeile bereitgestellt werden sollen. Ressourcen, z. B. Hilfeseiten, die auf dem Server keine Statusänderungen hervorrufen, können zu dieser Liste hinzugefügt werden. Die Ressourcen in der Liste der zulässigen URIs werden unabhängig vom Referrer nie durch den Referrer-Filter gesperrt.
* **Null-Referrer**: Eine Server-Anforderung, die nicht mit einer übergeordneten Web-Seite verknüpft ist oder nicht von einer übergeordneten Web-Seite stammt, gilt als Anforderung von einem Null-Referrer. Wenn Sie beispielsweise ein neues Browser-Fenster öffnen, eine Adresse eingeben und die Eingabetaste drücken, ist der an den Server gesendete Referrer null. Ein Desktop-Programm (.NET oder SWING), das eine HTTP-Anfrage an einen Webserver sendet, sendet auch einen Null-Referrer an den Server.

### Referrer-Filter {#referer-filtering}

Der Referrer-Filter funktioniert wie folgt:

1. Der Formularserver prüft die für den Aufruf verwendete HTTP-Methode:

   1. Wenn es sich um POST handelt, prüft der Formular-Server die Referrer-Kopfzeile.
   1. Wenn es sich um GET handelt, umgeht der Formular-Server die Referrer-Prüfung, es sei denn, *CSRF_CHECK_GETS* ist auf „true“ festgelegt. In diesem Fall wird die Referrer-Kopfzeile überprüft. *CSRF_CHECK_GETS* ist in der Datei *web.xml* für Ihre Anwendung festgelegt.

1. Der Formular-Server prüft, ob der angeforderte URI in der Zulassungsliste vorhanden ist:

   1. Wenn der URI in der Zulassungsliste eingetragen ist, akzeptiert der Server die Anfrage.
   1. Wenn der angeforderte URI nicht in der Zulassungsliste eingetragen ist, ruft der Server den Referrer der Anfrage ab.

1. Wenn in der Anfrage ein Referrer angegeben ist, prüft der Server, ob es sich um einen zulässigen Referrer handelt. Wenn der Referrer zulässig ist, prüft der Server, ob es sich um eine Referrer-Ausnahme handelt:

   1. Wenn es sich um eine Ausnahme handelt, wird die Anfrage blockiert.
   1. Wenn es sich nicht um eine Ausnahme handelt, wird die Anfrage übergeben.

1. Wenn in der Anfrage kein Referrer angegeben ist, prüft der Server, ob ein Null-Referrer zulässig ist:

   1. Wenn ein Null-Referrer zulässig ist, wird die Anfrage übergeben.
   1. Wenn ein Null-Referrer nicht zulässig ist, prüft der Server, ob der angeforderte URI eine Ausnahme für den Null-Referrer ist, und behandelt die Anfrage entsprechend.

### Verwalten des Referrer-Filters {#managing-referer-filtering}

AEM Forms auf JEE bietet einen Referrer-Filter, um Referrer anzugeben, denen der Zugriff auf Server-Ressourcen erlaubt wird. Standardmäßig filtert der Filter &quot;Referrer&quot;keine Anforderungen, die eine sichere HTTP-Methode verwenden, z. B. GET, es sei denn, *CSRF_CHECK_GETS* auf &quot;true&quot;gesetzt ist. Wenn die Port-Nummer für den Eintrag eines zulässigen Referrers auf 0 festgelegt ist, lässt AEM Forms auf JEE alle Anfragen mit Referrern von diesem Host unabhängig von der Port-Nummer zu. Wenn keine Anschlussnummer angegeben wird, werden nur Anforderungen vom Standardanschluss 80 (HTTP) oder von Anschluss 443(HTTPS) zugelassen. Der Referrer-Filter wird deaktiviert, wenn alle Einträge in der Liste der zulässigen Referrer gelöscht werden.

Wenn Sie Document Services zum ersten Mal installieren, wird die Liste für zulässige Referrer mit der Adresse des Servers aktualisiert, auf dem Document Services installiert wird. Die Einträge für den Server enthalten den vollständig Servernamen, die IPv4-Adresse, die IPv6-Adresse, wenn IPv6 aktiviert ist, die Loopback-Adresse und einen „localhost“-Eintrag. Die Namen, die zur Liste der zulässigen verweisenden Stellen (auch als Liste „Zulässige Referrer“ bezeichnet)“ hinzugefügt wurden, werden vom Betriebssystem des Hosts zurückgegeben. Beispielsweise enthält ein Server mit einer IP-Adresse von 10.40.54.187 die folgenden Einträge: `https://server-name:0, https://10.40.54.187:0, https://127.0.0.1:0, http://localhost:0`. Für nicht qualifizierten Namen, die vom Host-Betriebssystem zurückgegeben wurden (Namen, die keine IPv4-Adresse, IPv6-Adresse oder qualifizierte Domain-Namen haben), erfolgt keine Aktualisierung der Zulassungsliste. Ändern Sie die Liste der zulässigen verweisenden Stellen entsprechend Ihrer Geschäftsumgebung. Den Formular-Server nicht mit der Standardliste der zulässigen verweisenden Stellen in der Produktionsumgebung bereitstellen. Nachdem Sie die zulässigen Referrer, Referrer-Ausnahmen oder URIs geändert haben, müssen Sie den Server neu starten, damit die Änderungen wirksam werden.

**Verwalten der Liste der zulässigen verweisenden Stellen**

Sie können die Liste der zulässigen verweisenden Stellen über die User Management-Oberfläche von Administration Console verwalten. Die User Management-Oberfläche stellt Funktionen zum Erstellen, Bearbeiten oder Löschen der Liste bereit. Weitere Informationen zur Verwendung der Liste der zulässigen verweisenden Stellen finden Sie im Abschnitt [Verhindern von CSRF-Angriffen](/help/forms/using/admin-help/preventing-csrf-attacks.md) der *Administration-Hilfe*.

**Verwalten der Listen „Zulässige Referrer – Ausnahmen“ und „Zulässige URIs“**

AEM Forms on JEE stellt APIs zum Verwalten der Listen „Zulässige Referrer – Ausnahmen“ und „Zulässige URIs“ bereit. Sie können diese APIs verwenden, um die Liste abzurufen, zu erstellen, zu bearbeiten oder zu löschen. Im Folgenden finden Sie eine Liste der verfügbaren APIs:

* createAllowedURIsList
* getAllowedURIsList
* updateAllowedURIsList
* deleteAllowedURIsList
* addAllowedRefererExceptions
* getAllowedRefererExceptions
* updateAllowedRefererExceptions
* deleteAllowedRefererExceptions

Weitere Informationen zu den APIs finden Sie in der AEM Forms on JEE API-Referenz.

Verwenden Sie die Liste ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** für „Zulässige Referrer – Ausnahmen“ auf globaler Ebene, d. h. um Ausnahmen zu definieren, die für alle Anwendungen gelten. Diese Liste enthält nur URIs mit einem absoluten Pfad (zum Beispiel `/index.html`) oder einen relativen Pfad (z. B. `/sample/`). Sie können auch einen regulären Ausdruck an das Ende eines relativen URI anhängen, beispielsweise: `/sample/(.)*`.

Die Listen-ID ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** wird als Konstante in der Klasse `UMConstants` des Namespace `com.adobe.idp.um.api` definiert, der in `adobe-usermanager-client.jar` zu finden ist. Sie können die AEM Forms-APIs zum Erstellen, Ändern oder Bearbeiten dieser Liste verwenden. Um beispielsweise die Liste für globale zulässigen Referrer - Ausnahmen zu verwenden, gehen Sie folgendermaßen vor:

```java
addAllowedRefererExceptions(UMConstants.LC_GLOBAL_ALLOWED_REFERER_EXCEPTION, Arrays.asList("/index.html", "/sample/(.)*"))
```

Verwenden Sie die Liste ***CSRF_ALLOWED_REFERER_EXCEPTIONS*** für anwendungsspezifische Ausnahmen.

**Deaktivieren des Referrer-Filters**

Falls der Referrer-Filter den Zugriff auf den Formularserver vollkommen sperrt und Sie die Liste der zulässigen verweisenden Stellen nicht bearbeiten können, können Sie das Startskript des Server aktualisieren und die Referrer-Filterung deaktivieren.

Fügen Sie das JAVA-Argument `-Dlc.um.csrffilter.disabled=true` in das Startskript ein und starten Sie den Server neu. Löschen Sie das JAVA-Argument, nachdem Sie die Liste der zulässigen verweisenden Stellen entsprechend neu konfiguriert haben.

**Referrer-Filterung bei benutzerdefinierten WAR-Dateien**

Möglicherweise haben Sie benutzerdefinierte WAR-Dateien erstellt, um mit AEM Forms on JEE zusammenzuarbeiten und Ihre Geschäftsanforderungen zu erfüllen. Um die Referrer-Filterung bei benutzerdefinierten WAR-Dateien zu aktivieren, fügen Sie ***adobe-usermanager-client.jar*** in den Klassenpfad für die WAR-Datei ein und nehmen Sie in die Datei web.xml einen Filtereintrag mit den folgenden Parametern vor:

**CSRF_CHECK_GETS** – steuert die Referrer-Prüfung bei GET-Anforderungen. Wenn dieser Parameter nicht definiert ist, wird für den Standardwert „false“ festgelegt. Schließen Sie diesen Parameter nur ein, wenn Sie Ihre GET-Anfragen filtern möchten.

**CSRF_ALLOWED_REFERER_EXCEPTIONS** – ist die ID der Liste „Zulässige Referrer – Ausnahmen“. Der Referrer-Filter verhindert, dass Anfragen, die von Referrern in der durch die Listen-ID identifizierten Liste stammen, Ressourcen auf dem Formularserver aufrufen.

**CSRF_ALLOWED_URIS_LIST_NAME** ist die ID der Liste „Zulässige URIs“. Der Referrer-Filter blockiert keine Anfragen an Ressourcen der Liste, die unabhängig vom Wert des Referrer-Headers in der Anfrage durch die Listen-ID identifiziert wird.

**CSRF_ALLOW_NULL_REFERER** – steuert das Verhalten des Referrer-Filters, wenn der Referrer null oder nicht vorhanden ist. Wenn dieser Parameter nicht definiert wird, wird für den Standardwert „false“ festgelegt. Fügen Sie diesen Parameter nur ein, wenn Sie Null-Referrer zulassen möchten. Das Zulassen eines Null-Referrers kann einige Arten von CSRF-Angriffen ermöglichen.

**CSRF_NULL_REFERER_EXCEPTIONS** – ist eine Liste der URIs, für die keine Referrer-Prüfung durchgeführt wird, wenn der Referrer null ist. Dieser Parameter wird nur aktiviert, wenn für *CSRF_ALLOW_NULL_REFERER* „false“ festgelegt wird. Trennen Sie mehrere URIs in der Liste durch ein Komma.

Im Folgenden finden Sie ein Beispiel für den Filtereintrag in der Datei *web.xml* für die WAR-Datei ***SAMPLE***:

```java
<filter> 
       <filter-name> filter-name </filter-name> 
       <filter-class> com.adobe.idp.um.auth.filter.RemoteCSRFFilter </filter-class> 
     <!-- default is false --> 
     <init-param> 
      <param-name> CSRF_ALLOW_NULL_REFERER </param-name> 
      <param-value> false </param-value> 
     </init-param> 
     <!-- default is false --> 
     <init-param> 
      <param-name> CSRF_CHECK_GETS </param-name> 
      <param-value> true </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
       <param-name> CSRF_NULL_REFERER_EXCEPTIONS </param-name> 
       <param-value> /SAMPLE/login, /SAMPLE/logout  </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
      <param-name> CSRF_ALLOWED_REFERER_EXCEPTIONS </param-name> 
      <param-value> SAMPLE_ALLOWED_REF_EXP_ID </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
      <param-name> CSRF_ALLOWED_URIS_LIST_NAME </param-name> 
      <param-value> SAMPLE_ALLOWED_URI_LIST_ID     </param-value> 
     </init-param> 
</filter> 
    ........ 
    <filter-mapping> 
      <filter-name> filter-name </filter-name> 
      <url-pattern>/*</url-pattern> 
    </filter-mapping>
```

**Fehlerbehebung**

Wenn rechtmäßige Server-Anfragen vom CSRF-Filter blockiert werden, haben Sie folgende Möglichkeiten:

* Wenn die abgelehnte Anfrage eine Referrer-Kopfzeile hat, sollte sorgfältig abgewogen werden, ob sie in die Liste der erlaubten Referrer aufgenommen werden soll. Fügen Sie nur Referrer hinzu, denen Sie vertrauen.
* Wenn die abgelehnte Anfrage keine Referrer-Kopfzeile hat, ändern Sie Ihr Client-Programm so, dass eine Referrer-Kopfzeile eingefügt wird.
* Wenn der Client einen Browser verwenden kann, versuchen Sie es mit diesem Bereitstellungsmodell.
* Als letztes Mittel können Sie die Ressource zur Liste der zulässigen URIs hinzufügen. Dies ist keine empfohlene Einstellung.

## Sichere Netzwerkkonfiguration {#secure-network-configuration}

In diesem Abschnitt finden Sie Beschreibungen der für AEM Forms on JEE erforderlichen Protokolle und Ports sowie Empfehlungen für die Bereitstellung von AEM Forms on JEE in einer sicheren Netzwerkkonfiguration.

### Von AEM Forms on JEE verwendete Netzwerkprotokolle {#network-protocols-used-by-aem-forms-on-jee}

Wenn Sie, wie im vorherigen Abschnitt beschrieben, eine sichere Netzwerkarchitektur konfigurieren, sind die folgenden Netzwerkprotokolle für die Interaktion zwischen AEM Forms on JEE und anderen Systemen in Ihrem Unternehmensnetzwerk erforderlich.

<table> 
 <thead> 
  <tr> 
   <th><p>Protokoll</p> </th> 
   <th><p>Verwenden Sie</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>HTTP</p> </td> 
   <td> 
    <ul> 
     <li><p>Browser zeigt Configuration Manager und Endbenutzer-Web-Anwendungen an</p> </li> 
     <li><p>Alle SOAP-Verbindungen</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td> 
    <ul> 
     <li><p>Web-Dienst-Client-Anwendungen wie .NET-Anwendungen</p> </li> 
     <li><p>Adobe Reader® verwendet SOAP für AEM Forms on JEE-Server-Web-Dienste</p> </li> 
     <li><p>Adobe Flash®-Anwendungen verwenden SOAP für Formular-Server-Web-Dienste</p> </li> 
     <li><p>AEM Forms on JEE SDK-Aufrufe bei Verwendung im SOAP-Modus</p> </li> 
     <li><p>Workbench-Entwurfsumgebung</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>RMI</p> </td> 
   <td><p>AEM Forms on JEE SDK-Aufrufe bei Verwendung im Enterprise JavaBeans-Modus (EJB)</p> </td> 
  </tr> 
  <tr> 
   <td><p>IMAP/POP3</p> </td> 
   <td> 
    <ul> 
     <li><p>Auf E-Mail basierende Eingabe für einen Dienst (E-Mail-Endpunkt)</p> </li> 
     <li><p>Benachrichtigungen zu Benutzeraufgaben per E-Mail</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>UNC-Dateieingabe/-ausgabe</p> </td> 
   <td><p>AEM Forms on JEE-Überwachung von überwachten Ordnern auf Eingabe in einen Dienst (Endpunkt des überwachten Ordners)</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td> 
    <ul> 
     <li><p>Synchronisierung von Informationen über Benutzerinnen bzw. Benutzer und Gruppen der Organisation in einem Ordner</p> </li> 
     <li><p>LDAP-Authentifizierung für interaktive Benutzerinnen und Benutzer</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>JDBC</p> </td> 
   <td> 
    <ul> 
     <li><p>Abfrage- und Prozeduraufrufe an eine externe Datenbank, die während des Ausführung eines Prozesses mithilfe des JDBC-Diensts durchgeführt werden</p> </li> 
     <li><p>Interner Zugriff auf das Repository von AEM Forms on JEE</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebDAV</p> </td> 
   <td><p>Ermöglicht das Remote-Durchsuchen des Repositorys von AEM Forms on JEE während des Entwurfs (Formulare, Fragmente usw.) durch einen beliebigen WebDAV-Client</p> </td> 
  </tr> 
  <tr> 
   <td><p>AMF</p> </td> 
   <td><p>Adobe Flash-Anwendungen, bei denen Server-Dienste von AEM Forms on JEE mit einem Remoting-Endpunkt konfiguriert sind</p> </td> 
  </tr> 
  <tr> 
   <td><p>JMX</p> </td> 
   <td><p>AEM Forms on JEE stellt MBeans für die Überwachung mit JMX bereit</p> </td> 
  </tr> 
 </tbody> 
</table>

### Ports für Anwendungs-Server {#ports-for-application-servers}

In diesem Abschnitt werden die Standardanschlüsse (und alternativen Konfigurationsbereiche) für jeden unterstützten Anwendungsservertyp beschrieben. Diese Ports müssen in der inneren Firewall aktiviert oder deaktiviert werden, je nachdem, welche Netzwerkfunktionalität Sie für Clients zulassen möchten, die eine Verbindung zum Anwendungs-Server herstellen, auf dem AEM Forms on JEE ausgeführt wird.

>[!NOTE]
>
>Standardmäßig legt der Server mehrere JMX MBeans unter dem Namespace adobe.com offen. Dabei werden nur für die Überwachung des Serverzustands nützliche Informationen offengelegt. Um jedoch die Offenlegung von Informationen zu verhindern, sollten Sie verhindern, dass Aufrufe von einem nicht vertrauenswürdigen Netzwerk JMX-MBeans suchen und auf Konsistenzmetriken zugreifen.

**JBoss-Ports**

<table> 
 <thead> 
  <tr> 
   <th><p>Zweck</p> </th> 
   <th><p>Port</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Zugriff auf Web-Anwendungen</p> </td> 
   <td><p>[JBOSS_Root]/standalone/configuration/lc_[database].xml</p> <p>HTTP/1.1 Connector-Port 8080</p> <p>AJP 1.3 Connector-Port 8009</p> <p>SSL-/TLS-Connector-Port 8443</p> </td> 
  </tr> 
  <tr> 
   <td><p>CORBA-Unterstützung</p> </td> 
   <td><p>[JBoss-Stammordner]/server/all/conf/jacorb.properties</p> <p>OAPort 3528</p> <p>OASSLPort 3529</p> </td> 
  </tr> 
 </tbody> 
</table>

**WebLogic-Ports**

<table> 
 <thead> 
  <tr> 
   <th><p>Zweck</p> </th> 
   <th><p>Port</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Zugriff auf Web-Anwendungen</p> </td> 
   <td> 
    <ul> 
     <li><p>Lauschender Port des Admin-Servers: 7001 (Standard)</p> </li> 
     <li><p>Lauschender SSL-Port des Admin-Servers: 7002 (Standard)</p> </li> 
     <li><p>Für verwalteten Server konfigurierter Anschluss, z. B. 8001</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic-Administrations-Ports sind für den Zugriff auf AEM Forms on JEE nicht erforderlich</p> </td> 
   <td> 
    <ul> 
     <li><p>Lauschender Port des verwalteten Servers: Konfigurierbar zwischen 1 und 65534</p> </li> 
     <li><p>Lauschender Port des verwalteten SSL-Servers: Konfigurierbar zwischen 1 und 65534</p> </li> 
     <li><p>Lauschender Port von Node Manager: 5556 (Standard)</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**WebSphere -Anschlüsse**

Informationen zu WebSphere-Anschlüssen, die für AEM Forms auf JEE erforderlich sind, finden Sie unter der Einstellung der Port-Nummer in der Benutzeroberfläche des WebSphere-Programm-Servers.

### Konfigurieren von SSL {#configuring-ssl}

Bezüglich der physischen Architektur, die im Abschnitt [Physische Architektur von AEM Forms auf JEE](hardening-aem-forms-jee-environment.md#aem-forms-on-jee-physical-architecture) beschrieben wird, sollten Sie SSL für alle Verbindungen konfigurieren, die Sie verwenden möchten. Besonders alle SOAP-Verbindungen müssen über SSL erfolgen, um die Offenlegung von Benutzerberechtigungen im Netzwerk zu verhindern.

Anleitungen für die Konfiguration von SSL unter JBoss, WebLogic und WebSphere finden Sie unter „Konfigurieren von SSL“ in der [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_64_de).

Anweisungen zum Importieren von Zertifikaten in JVM (Java Virtual Machine), die für einen AEM Forms-Server konfiguriert sind, finden Sie im Abschnitt „Gegenseitige Authentifizierung“ in der [Hilfe zu AEM Forms Workbench](https://www.adobe.com/go/learn_aemforms_workbench_65_de).

### Konfigurieren der SSL-Umleitung {#configuring-ssl-redirect}

Nachdem Sie Ihren Anwendungs-Server für die Unterstützung von SSL konfiguriert haben, müssen Sie sicherstellen, dass der gesamte HTTP-Traffic zu Anwendungen und Diensten gezwungen wird, den SSL-Port zu verwenden.

Informationen zum Konfigurieren der SSL-Umleitung für WebSphere oder WebLogic finden Sie in der Dokumentation zu Ihrem jeweiligen Anwendungs-Server.

1. Öffnen Sie eine Eingabeaufforderung, navigieren Sie zum Ordner „/JBOSS_HOME/standalone/configuration“ und führen Sie den folgenden Befehl aus:

   `keytool -genkey -alias jboss7 -keyalg RSA -keystore server.keystore -validity 10950`

1. Öffnen Sie die Datei „JBOSS_HOME/standalone/configuration/standalone.xml“ zur Bearbeitung.

   Fügen Sie nach dem Element &lt;subsystem xmlns=&quot;urn:jboss:domain:web:1.1&quot; native=&quot;false&quot; default-virtual-server=&quot;default-host&quot;> die folgenden Details hinzu:

   &lt;connector name=&quot;https&quot; protocol=&quot;HTTP/1.1&quot; scheme=&quot;https&quot; socket-binding=&quot;https&quot; enabled=&quot;true&quot; secure=&quot;true&quot;/>

1. Fügen Sie den folgenden Code im https-Connector-Element hinzu:

   ```xml
   <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true" enabled="true"> 
    <ssl name="jboss7_ssl" key-alias="jboss71" password="Tibco321" certificate-key-file="../standalone/configuration/server.keystore" protocol="TLSv1"/> 
    </connector>
   ```

   Speichern und schließen Sie die Datei standalone.xml.

## Windows-spezifische Sicherheitsempfehlungen {#windows-specific-security-recommendations}

Dieser Abschnitt enthält Sicherheitsempfehlungen, die speziell für Windows gelten, wenn AEM Forms on JEE dort ausgeführt wird.

### JBoss-Dienstkonten {#jboss-service-accounts}

Bei der AEM Forms on JEE-Turnkey-Installation wird standardmäßig unter Verwendung des Kontos „Lokales System“ ein Dienstkonto eingerichtet. Das integrierte Benutzerkonto „Lokales System“ hat hohe Zugriffsrechte; es gehört zur Gruppe „Administratoren“. Wenn eine Worker-Prozess-Identität als Benutzerkonto „Lokales System“ ausgeführt wird, hat dieser Worker-Prozess vollen Zugriff auf das gesamte System.

#### Ausführen des Anwendungs-Servers unter Verwendung eines Kontos ohne Administratorrechte {#run-the-application-server-using-a-non-administrative-account}

1. Erstellen Sie in der Microsoft Management Console (MMC) einen lokalen Benutzer für den Formular-Server-Dienst, der sich wie folgt anmeldet:

   * Wählen Sie **Benutzer kann Passwort nicht ändern** aus.
   * Stellen Sie sicher, dass auf der Registerkarte **Mitglied von** die Gruppe „Benutzer“ aufgeführt ist.

1. Wählen Sie **Einstellungen** > **Verwaltungstools** > **Dienste**.
1. Doppelklicken Sie auf den Dienst für den Anwendungs-Server und halten Sie diesen an.
1. Wählen Sie auf der Registerkarte **Anmelden** die Option **Dieses Konto** aus, suchen Sie das von Ihnen erstellte Benutzerkonto und geben Sie das Passwort für das Konto ein.
1. Weisen Sie im Fenster „Lokale Sicherheitseinstellungen“ unter „Zuweisen von Benutzerrechten“ dem Benutzerkonto, unter dem der Formular-Server ausgeführt wird, die folgenden Rechte zu:

   * Anmeldung über Terminal-Dienste verweigern
   * Anmeldung bei „locallyxx“ verweigern
   * Als Dienst anmelden (sollte bereits festgelegt sein)

1. Weisen Sie dem neuen Benutzerkonto Berechtigungen zum Ändern der folgenden Verzeichnisse zu:
   * **Verzeichnis des globalen Dokumentenspeichers (GDS)**: Der Speicherort des GDS-Verzeichnisses wird während der Installation von AEM Forms manuell konfiguriert. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Verzeichnis unter dem Installationsverzeichnis des Anwendungsservers gewählt: `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository-Verzeichnis**: Der Standardspeicherort lautet `[AEM-Forms-installation-location]\crx-repository`
   * **Temporäre Verzeichnisse von AEM Forms**:
      * (Windows) TMP- oder TEMP-Pfad gemäß Einstellung in den Umgebungsvariablen
      * (AIX, Linux oder Solaris) Basisordner der angemeldeten Person
Auf UNIX-basierten Systemen kann eine Benutzerin oder ein Benutzer ohne Stammordner den folgenden Ordner als temporären Ordner verwenden:
      * (Linux) /var/tmp oder /usr/tmp
      * (AIX) /tmp oder /usr/tmp
      * (Solaris) /var/tmp oder /usr/tmp
1. Weisen Sie dem neuen Benutzerkonto Schreibberechtigungen für die folgenden Verzeichnisse zu:
   * [JBoss-directory]\standalone\deployment
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\

   >[!NOTE]
   >
   >Der standardmäßige Installationsspeicherort von JBoss Application Server ist folgender:
   >
   >* Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   >* Linux: /opt/jboss/.

1. Starten Sie den Anwendungs-Server-Dienst.

### Dateisystemsicherheit {#file-system-security}

AEM Forms on JEE verwendet das Dateisystem wie folgt:

* Speichert temporäre Dateien, die bei der Verarbeitung von Dokumenteingabe und -ausgabe verwendet werden
* Speichert Dateien im globalen Archivspeicher, die zur Unterstützung der installierten Lösungskomponenten verwendet werden
* Überwachte Ordner speichern abgelegte Dateien, die als Eingabe für einen Dienst von einem Ordnerspeicherort im Dateisystem aus verwendet werden

Wenn Sie überwachte Ordner als Möglichkeit zum Senden und Empfangen von Dokumenten mit einem Formular-Server-Dienst verwenden, sollten Sie zusätzliche Vorsichtsmaßnahmen im Hinblick auf die Dateisystemsicherheit treffen. Wenn ein Benutzer Inhalte in einem überwachten Ordner ablegt, werden diese Inhalte durch den überwachten Ordner offengelegt. In diesem Fall wird der tatsächliche Endbenutzer nicht vom Dienst authentifiziert. Stattdessen stützt er sich auf ACL- und Freigabesicherheit, die auf Ordnerebene festgelegt werden, um zu bestimmen, wer den Dienst tatsächlich aufrufen kann.

## JBoss-spezifische Sicherheitsempfehlungen {#jboss-specific-security-recommendations}

Dieser Abschnitt enthält spezielle Empfehlungen für die Anwendungsserverkonfiguration, die gelten, wenn JBoss 7.0.6 für die Ausführung von AEM Forms on JEE verwendet wird.

### Deaktivieren von JBoss Management-Konsole und JMX-Konsole {#disable-jboss-management-console-and-jmx-console}

Wenn Sie AEM Forms mit der Turnkey-Installationsmethode unter JBoss installieren, ist der Zugriff auf JBoss Management Console und die JMX-Konsole bereits konfiguriert (die JMX-Überwachung ist deaktiviert). Wenn Sie Ihren eigenen JBoss-Anwendungs-Server verwenden, stellen Sie sicher, dass der Zugriff auf die JBoss Management-Konsole und die JMX-Überwachungskonsole abgesichert ist. Der Zugriff auf die JMX-Überwachungskonsole wird in der JBoss-Konfigurationsdatei „jmx-invoker-service.xml“ festgelegt.

### Deaktivieren der Ordnersuche {#disable-directory-browsing}

Nachdem Sie sich bei der Administration-Console angemeldet haben, können Sie durch Ändern der URL zur Ordnerliste der Konsole wechseln. Wenn Sie beispielsweise die URL in eine der folgenden URLs ändern, wird eine Liste angezeigt:

```java
https://<servername>:8080/adminui/secured/ 
https://<servername>:8080/um/
```

## WebLogic-spezifische Sicherheitsempfehlungen {#weblogic-specific-security-recommendations}

Dieser Abschnitt enthält Empfehlungen für die Anwendungs-Server-Konfiguration zum Schützen von WebLogic 9.1 beim Ausführen von AEM Forms on JEE.

### Deaktivieren der Ordnersuche {#disable_directory_browsing-1}

Stellen Sie in der Datei „weblogic.xml“ die Eigenschaften zu „index-directories“ auf `false` ein, wie im folgenden Beispiel gezeigt:

```xml
<container-descriptor> 
    <index-directory-enabled>false 
    </index-directory-enabled> 
</container-descriptor>
```

### Aktivieren des SSL-Ports in WebLogic {#enable-weblogic-ssl-port}

WebLogic aktiviert den SSL-Standardüberwachungs-Port 7002 standardmäßig nicht. Aktivieren Sie diesen Port in der WebLogic-Server-Administration-Console, bevor Sie SSL konfigurieren.

## WebSphere-spezifische Sicherheitsempfehlungen {#websphere-specific-security-recommendations}

Dieser Abschnitt enthält Empfehlungen zur Konfiguration des Anwendungs-Servers zum Schützen von WebSphere beim Ausführen von AEM Forms on JEE.

### Deaktivieren der Ordnersuche {#disable_directory_browsing-2}

Legen Sie in der Datei „ibm-web-ext.xml“ die Eigenschaft `directoryBrowsingEnabled` auf `false` fest.

### Aktivieren der administrativen Sicherheit in WebSphere {#enable-websphere-administrative-security}

1. Melden Sie sich bei WebSphere Administrative Console an.
1. Navigieren Sie in der Navigationsstruktur zu **Sicherheit** > **Globale Sicherheit**
1. Wählen Sie **Enable administrative security**.
1. Deaktivieren Sie sowohl **Enable application security** als auch **Use Java 2 security**.
1. Klicken auf **OK** oder **Apply**.
1. Klicken Sie im Feld **Messages** auf **Save directly to the master configuration**.
