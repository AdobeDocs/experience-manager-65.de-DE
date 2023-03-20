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
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '7665'
ht-degree: 57%

---

# Härtung Ihrer AEM Forms on JEE-Umgebung {#hardening-your-aem-forms-on-jee-environment}

Erfahren Sie mehr über die verschiedenen Einstellungen zum Stärken der Sicherheit, um die Sicherheit von AEM Forms auf JEE bei der Ausführung in einem firmeninternen Intranet zu verbessern.

In diesem Artikel werden Empfehlungen und Best Practices zum Schützen von Servern beschrieben, auf denen AEM Forms on JEE ausgeführt wird. Dieses Dokument stellt keine umfassende Anleitung zum Härten (Absichern) des Hosts für das Betriebssystem und die Anwendungsserver dar. Stattdessen werden in diesem Artikel eine Reihe von Einstellungen zum Stärken der Sicherheit beschrieben, die Sie implementieren sollten, um die Sicherheit von AEM Forms auf JEE bei der Ausführung in einem firmeninternen Intranet zu verbessern. Um sicherzustellen, dass die AEM Forms on JEE-Anwendungsserver sicher bleiben, sollten Sie jedoch auch Verfahren zur Sicherheitsüberwachung, -erkennung und -reaktion implementieren.

In diesem Artikel werden Härtungsverfahren beschrieben, die in den folgenden Phasen des Installations- und Konfigurationszyklus angewendet werden sollten:

* **Vorinstallation:** Verwenden Sie diese Verfahren, bevor Sie AEM Forms on JEE installieren.
* **Installation**: Verwenden Sie diese Verfahren während der Installation von AEM Forms auf JEE.
* **Nach der Installation:** Verwenden Sie diese Verfahren nach der Installation und danach in regelmäßigen Abständen.

AEM Forms on JEE ist in hohem Maße anpassbar und kann in vielen verschiedenen Umgebungen verwendet werden. Einige der Empfehlungen entsprechen möglicherweise nicht den Anforderungen Ihres Unternehmens.

## Vorinstallation {#preinstallation}

Vor der Installation von AEM Forms on JEE können Sie Sicherheitslösungen auf die Netzwerkschicht und das Betriebssystem anwenden. In diesem Abschnitt werden einige Probleme beschrieben und Empfehlungen zur Reduzierung von Sicherheitslücken in diesen Bereichen gegeben.

**Installation und Konfiguration unter UNIX und Linux**

Sie sollten AEM Forms on JEE nicht mit einer Root Shell installieren oder konfigurieren. Standardmäßig werden alle Dateien im Ordner „/opt“ installiert. Der Benutzer, der die Installation durchführt, benötigt daher sämtliche Dateiberechtigungen für den Ordner „/opt“. Alternativ kann eine Installation unter dem Verzeichnis /user eines einzelnen Benutzers durchgeführt werden, für den bereits alle Dateiberechtigungen vorliegen.

**Installation und Konfiguration unter Windows**

Sie müssen die Installation unter Windows als Administrator durchführen, wenn Sie AEM Forms on JEE mit der Turnkey-Methode oder PDF Generator installieren. Wenn Sie PDF Generator unter Windows mit nativer Anwendungsunterstützung installieren, müssen Sie die Installation außerdem als der Windows-Benutzer ausführen, der Microsoft Office installiert hat. Weitere Informationen zu Installationsberechtigungen finden Sie im Dokument „Installieren und Bereitstellen von AEM Forms auf JEE“ für Ihren Programm-Server.

### Sicherheit der Netzwerkschicht {#network-layer-security}

Sicherheitslücken der Netzwerkschicht gehören zu den Hauptbedrohungen für Internet- oder Intranet-orientierte Anwendungsserver. In diesem Abschnitt wird der Prozess zum Absichern von Hostrechnern im Netzwerk gegen diese Schwachstellen beschrieben. Es befasst sich mit der Netzwerksegmentierung, der Stapelhärtung des TCP/IP-Stacks (Transmission Control Protocol/Internet Protocol) und der Verwendung von Firewalls für den Hostschutz.

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
   <td><p>Stellen Sie Formularserver in einer demilitarisierten Zone (DMZ) bereit. Die Segmentierung sollte in mindestens zwei Schichten bestehen, wobei sich der Anwendungsserver, auf dem AEM Forms on JEE ausgeführt wird, hinter der inneren Firewall befindet. Schirmen Sie das externe Netzwerk von der DMZ ab, die die Webserver enthält, und schirmen Sie die DMZ wiederum vom internen Netzwerk ab. Verwenden Sie Firewalls für die Implementierung der Abschirmungsebenen. Kategorisieren und steuern Sie den Traffic, der durch die einzelnen Netzwerkschichten geleitet wird, um sicherzustellen, dass nur das absolute Minimum der erforderlichen Daten zulässig ist.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Private IP-Adressen</p> </td> 
   <td><p>Verwenden Sie auf AEM Forms-Programm-Servern durch NAT (Network Address Translation) geschützte private IP-Adressen gemäß RFC 1918. Weisen Sie private IP-Adressen (10.0.0.0/8, 172.16.0.0/12 und 192.168.0.0/16) zu, um es einem Angreifer zu erschweren, Netzwerkverkehr über das Internet zu und von einem internen Host mit NAT zu leiten.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Firewalls</p> </td> 
   <td><p>Verwenden Sie die folgenden Kriterien, um eine Firewall-Lösung auszuwählen:</p> 
    <ul> 
     <li><p>Implementieren von Firewalls, die Proxy-Server unterstützen und/oder <em>gründliche Überprüfung</em> anstelle von einfachen Paketfilterlösungen.</p> </li> 
     <li><p>Verwenden Sie eine Firewall, die ein Sicherheitsparadigma unterstützt, das <em>alle Services verweigert, außer denen, die ausdrücklich erlaubt sind</em>.</p> </li> 
     <li><p>Implementieren Sie eine Dual-Homed- oder Multi-Homed-Firewall-Lösung. Diese Architektur bietet ein Höchstmaß an Sicherheit und hilft, zu verhindern, dass nicht autorisierte Benutzer die Firewall-Sicherheit umgehen.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Datenbankanschlüsse</p> </td> 
   <td><p>Verwenden Sie keine standardmäßigen Listening-Anschlüsse für Datenbanken (MySQL - 3306, Oracle - 1521, MS SQL - 1433). Informationen zum Ändern von Datenbankanschlüssen finden Sie in der Datenbankdokumentation.</p> <p>Die Verwendung eines anderen Datenbankanschlusses wirkt sich auf die gesamte AEM Forms on JEE-Konfiguration aus. Wenn Sie die Standardanschlüsse ändern, müssen Sie entsprechende Änderungen in anderen Konfigurationsbereichen vornehmen, z. B. in den Datenquellen für AEM Forms on JEE.</p> <p>Informationen zum Konfigurieren von Datenquellen in AEM Forms auf JEE finden Sie unter „Installieren und Aktualisieren von AEM Forms auf JEE“ oder „Aktualisieren auf AEM Forms auf JEE“ für Ihren Programm-Server im <a href="/help/forms/using/introduction-aem-forms.md" target="_blank">AEM Forms-Benutzerhandbuch</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Betriebssystemsicherheit {#operating-system-security}

In der folgenden Tabelle werden einige potenzielle Ansätze zur Minimierung von Sicherheitslücken im Betriebssystem beschrieben.

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
   <td><p>Wenn vom Hersteller bereitgestellte Sicherheits-Patches und -Aktualisierungen nicht zeitnah installiert werden, besteht ein erhöhtes Risiko, dass nicht autorisierte Benutzer Zugriff auf den Anwendungsserver erlangen. Testen Sie Sicherheits-Patches, bevor Sie sie auf Produktionsserver anwenden.</p><p>Erstellen Sie zudem Richtlinien und Prozeduren, damit regelmäßig Patches gesucht und installiert werden.</p></td> 
  </tr> 
  <tr> 
   <td><p>Virenschutzsoftware</p></td> 
   <td><p>Virenscanner können infizierte Dateien erkennen, indem sie nach einer Signatur suchen oder ungewöhnliches Verhalten ermitteln. Virenscanner speichern die Virussignaturen in einer Datei, die in der Regel auf der lokalen Festplatte abgelegt wird. Da häufig neue Viren entdeckt werden, sollten Sie diese Datei regelmäßig aktualisieren, damit der Virenscanner alle aktuellen Viren erkennt.</p></td> 
  </tr> 
  <tr> 
   <td><p>Network Time Protocol (NTP)</p></td> 
   <td><p>Für die forensische Analyse sollten Sie die genaue Zeit auf den Formularservern beibehalten. Verwenden Sie NTP, um die Zeit auf allen Systemen zu synchronisieren, die direkt mit dem Internet verbunden sind.</p></td> 
  </tr> 
 </tbody> 
</table>

Weitere Informationen zur Sicherheit für Ihr Betriebssystem finden Sie unter [Informationen zur Betriebssystemsicherheit](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/general-security-considerations.html#operating_system_security_information).

## Installation {#installation}

In diesem Abschnitt werden Verfahren beschrieben, die Sie während des AEM Forms-Installationsprozesses verwenden können, um Sicherheitslücken zu schließen. In einigen Fällen nutzen diese Verfahren Optionen, die Teil des Installationsprozesses sind. In der folgenden Tabelle werden diese Techniken beschrieben.

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
   <td><p>Softwarequelle</p> </td> 
   <td><p>Laden Sie AEM Forms on JEE nicht aus nicht vertrauenswürdigen Quellen herunter oder führen Sie es aus.</p> <p>Bösartige Programme können Code enthalten, der die Sicherheit auf verschiedene Weise verletzt, etwa durch Diebstahl, Ändern und Löschen von Daten sowie Dienstblockade (Denial of Service = DoS). Installieren Sie AEM Forms on JEE von der Adobe-DVD oder nur von einer vertrauenswürdigen Quelle.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Festplattenpartitionen</p> </td> 
   <td><p>Platzieren Sie AEM Forms on JEE auf einer dedizierten Festplattenpartition. Die Festplattenaufteilung ist ein Prozess, bei dem bestimmte Daten auf dem Server auf separaten physischen Festplatten verwaltet werden, um die Sicherheit zu erhöhen. Durch eine solche Datenanordnung lässt sich das Risiko von Directory Traversal-Angriffen verringern. Planen Sie die Erstellung einer von der Systempartition getrennten Partition, auf der Sie das AEM Forms on JEE-Inhaltsverzeichnis installieren können. (Unter Windows enthält die Systempartition den Ordner system32 oder die Boot-Partition.)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Komponenten</p> </td> 
   <td><p>Prüfen Sie die vorhandenen Dienste und deaktivieren oder deinstallieren Sie nicht erforderliche Dienste. Installieren Sie keine unnötigen Komponenten und Dienste.</p> <p>Die Standardinstallation eines Anwendungsservers kann Dienste beinhalten, die Sie nicht benötigen. Sie sollten alle unnötigen Dienste vor der Bereitstellung deaktivieren, um die Einstiegspunkte für Angriffe zu minimieren. Auf JBoss können Sie beispielsweise unnötige Dienste in der Deskriptordatei META-INF/jboss-service.xml auskommentieren.</p> </td> 
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

Nach der erfolgreichen Installation von AEM Forms on JEE ist es wichtig, die Umgebung aus Sicherheitsgründen regelmäßig zu warten.

Im folgenden Abschnitt werden die verschiedenen Aufgaben, die zum Schützen des bereitgestellten Formularservers empfohlen werden, ausführlich beschrieben.

### AEM Forms-Sicherheit {#aem-forms-security}

Die folgenden empfohlenen Einstellungen gelten für den AEM Forms on JEE-Server außerhalb der Verwaltungs-Webanwendung. Um die Sicherheitsrisiken für den Server zu verringern, wenden Sie diese Einstellungen unmittelbar nach der Installation von AEM Forms on JEE an.

**Sicherheits-Patches**

Wenn vom Hersteller bereitgestellte Sicherheits-Patches und -Aktualisierungen nicht zeitnah installiert werden, besteht ein erhöhtes Risiko, dass nicht autorisierte Benutzer Zugriff auf den Anwendungsserver erlangen. Testen Sie Sicherheits-Patches, bevor Sie sie auf Produktionsserver anwenden, um die Kompatibilität und Verfügbarkeit von Anwendungen sicherzustellen. Erstellen Sie zudem Richtlinien und Prozeduren, damit Patches regelmäßig gesucht und installiert werden. AEM Forms on JEE-Aktualisierungen finden Sie auf der Download-Site für Enterprise-Produkte.

**Dienstkonten (nur JBoss-Turnkey unter Windows)**

AEM Forms on JEE installiert standardmäßig einen Dienst unter Verwendung des Kontos LocalSystem . Das integrierte Benutzerkonto „Lokales System“ hat hohe Zugriffsrechte; es gehört zur Gruppe „Administratoren“. Wenn eine Worker Process-Identität als das Benutzerkonto &quot;LocalSystem&quot;ausgeführt wird, hat dieser Worker Process vollen Zugriff auf das gesamte System.

Um den Anwendungsserver, auf dem AEM Forms on JEE bereitgestellt wird, mit einem bestimmten Konto ohne Administratorrechte auszuführen, führen Sie die folgenden Anweisungen aus:

1. Erstellen Sie in der Microsoft Management Console (MMC) einen lokalen Benutzer für den Formularserverdienst, der sich wie folgt anmeldet:

   * Auswählen **Benutzer können Kennwort nicht ändern**.
   * Stellen Sie sicher, dass auf der Registerkarte **Mitglied von** die Gruppe **Benutzer** aufgeführt ist.

   >[!NOTE]
   >
   >Sie können diese Einstellung für PDF Generator nicht ändern.

1. Auswählen **Starten** > **Einstellungen** > **Administrationstools** > **Dienste**.
1. Doppelklicken Sie auf JBoss für AEM Forms on JEE und beenden Sie den Dienst.
1. Im **Anmelden** Registerkarte, wählen Sie **Dieses Konto**, suchen Sie nach dem von Ihnen erstellten Benutzerkonto und geben Sie das Kennwort für das Konto ein.
1. Öffnen Sie im MMC **Lokale Sicherheitseinstellungen** und wählen Sie **Lokale Richtlinien** > **Zuweisung von Benutzerrechten**.
1. Weisen Sie dem Benutzerkonto, unter dem der Formularserver ausgeführt wird, die folgenden Berechtigungen zu:

   * Anmeldung über Terminaldienste verweigern
   * Lokale Anmeldung verweigern
   * Als Dienst anmelden (sollte bereits festgelegt sein)

1. Weisen Sie dem neuen Benutzerkonto Berechtigungen zum Ändern der folgenden Verzeichnisse zu:
   * **Verzeichnis des globalen Dokumentenspeichers (GDS)**: Der Speicherort des GDS-Verzeichnisses wird während der Installation von AEM Forms manuell konfiguriert. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Verzeichnis unter dem Installationsverzeichnis des Anwendungsservers gewählt: `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository-Verzeichnis**: Der Standardspeicherort lautet `[AEM-Forms-installation-location]\crx-repository`
   * **Temporäre Verzeichnisse von AEM Forms**:
      * (Windows) TMP- oder TEMP-Pfad gemäß Einstellung in den Umgebungsvariablen
      * (AIX, Linux oder Solaris) Basisordner des angemeldeten Benutzers Auf UNIX-basierten Systemen kann ein Benutzer ohne Stammordner den folgenden Ordner als temporären Ordner verwenden:
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

**Bootstrap-Servlet von Configuration Manager deaktivieren**

Configuration Manager verwendete ein auf Ihrem Anwendungsserver bereitgestelltes Servlet, um das Bootstrapping der AEM Forms on JEE-Datenbank durchzuführen. Da Configuration Manager auf dieses Servlet zugreift, bevor die Konfiguration abgeschlossen ist, wurde der Zugriff darauf für autorisierte Benutzer nicht gesichert und sollte deaktiviert werden, nachdem Sie Configuration Manager erfolgreich für die Konfiguration von AEM Forms on JEE verwendet haben.

1. Dekomprimieren Sie die Datei „adobe-livecycle-[Programm-Server].ear“.
1. Öffnen Sie die Datei META-INF/application.xml .
1. Suchen Sie den Abschnitt adobe-bootstrapper.war :

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
1. Kommentieren Sie das Verzeichnis adobe-bootstrapper.war und adobe-lcm-bootstrapper-redirectory aus. WAR-Module wie folgt:

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

1. Speichern und schließen Sie die Datei &quot;META-INF/application.xml&quot;.
1. Komprimieren Sie die EAR-Datei und stellen Sie sie erneut auf dem Anwendungsserver bereit.
1. Starten Sie den AEM Forms-Server.
1. Geben Sie die nachstehende URL in einen Browser ein, um die Änderung zu testen und sicherzustellen, dass sie nicht mehr funktioniert.

   https://&lt;localhost>:&lt;port>/adobe-bootstrapper/bootstrap

**Remote-Zugriff auf den Trust Store sperren**

Configuration Manager ermöglicht Ihnen, eine Berechtigung für Acrobat Reader DC Extensions in den Trust Store von AEM Forms on JEE hochzuladen. Das bedeutet, dass der Zugriff auf den Trust Store-Berechtigungsdienst über Remote-Protokolle (SOAP und EJB) standardmäßig aktiviert wurde. Dieser Zugriff ist nicht mehr notwendig, nachdem Sie die Berechtigung für Berechtigungsnachweise mithilfe von Configuration Manager hochgeladen haben, oder wenn Sie beschließen, Berechtigungen später mit der Administration-Console zu verwalten.

Sie können den Remote-Zugriff auf alle Trust Store-Dienste deaktivieren, indem Sie die Schritte im Abschnitt [Nicht erforderlichen Remote-Zugriff auf Dienste deaktivieren](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_remote_access_to_services).

**Den gesamten nicht erforderlichen anonymen Zugriff deaktivieren**

Einige Formularserverdienste verfügen über Vorgänge, die von einem anonymen Aufrufer aufgerufen werden können. Wenn kein anonymer Zugriff auf diese Dienste erforderlich ist, deaktivieren Sie ihn, indem Sie die Schritte unter [Nicht erforderlichen anonymen Zugriff auf Dienste deaktivieren](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_anonymous_access_to_services).

#### Standardkennwort des Administrators ändern {#change-the-default-administrator-password}

Beim Installieren von AEM Forms on JEE wird ein Standardbenutzerkonto für den Benutzer „Superadministrator“ mit der Anmelde-ID „Administrator“ und dem Standardkennwort *password* erstellt. Sie sollten dieses Kennwort sofort mit Configuration Manager ändern.

1. Geben Sie die folgende URL in einen Webbrowser ein:

   ```java
   https://[host name]:[port]/adminui
   ```

   Die Standardportnummer lautet wie folgt:

   **JBoss**: 8080

   **WebLogic Server:** 7001

   **WebSphere:** 9080.

1. Geben Sie in das Feld **Benutzername** den Wert `administrator` und in das Feld **Kennwort** den Wert `password` ein.
1. Klicken Sie auf **Einstellungen** > **User Management** > **Benutzer und Gruppen**.
1. Geben Sie den Begriff `administrator` in das Feld **Suchen** ein und klicken Sie auf **Suchen**.
1. Klicken **Superadministrator** aus der Liste der Benutzer.
1. Klicken **Kennwort ändern** auf der Seite &quot;Benutzer bearbeiten&quot;.
1. Geben Sie das neue Kennwort an und klicken Sie auf **Speichern**.

Darüber hinaus wird empfohlen, das Standardkennwort für CRX Administrator zu ändern, indem Sie die folgenden Schritte ausführen:

1. Melden Sie sich bei `https://[server]:[port]/lc/libs/granite/security/content/useradmin.html` mit dem standardmäßigen Benutzernamen/Kennwort an.
1. Geben Sie „Administrator“ in das Suchfeld ein und klicken Sie auf **Suchen**.
1. Wählen Sie **Administrator** aus dem Suchergebnis und klicken Sie auf das Symbol **Bearbeiten** unten rechts auf der Benutzeroberfläche.
1. Geben Sie das neue Kennwort in das Feld **Neues Kennwort** und das alte Kennwort in das Feld **Ihr Kennwort** ein.
1. Klicken Sie auf das Symbol „Speichern“ unten rechts auf der Benutzeroberfläche.

#### WSDL-Generierung deaktivieren {#disable-wsdl-generation}

Die WSDL-Generierung (Web Service Definition Language) sollte nur in Entwicklungsumgebungen aktiviert sein, in denen Entwickler mithilfe der WSDL-Generierung Clientanwendungen erstellen. Sie können die WSDL-Generierung in einer Produktionsumgebung deaktivieren, um zu vermeiden, dass interne Details eines Dienstes offen gelegt werden.

1. Geben Sie die folgende URL in einen Webbrowser ein:

   ```java
   https://[host name]:[port]/adminui
   ```

1. Klicken **Einstellungen > Core-Systemeinstellungen > Konfigurationen**.
1. Deaktivieren Sie **WSDL aktivieren** und klicken Sie auf **OK**.

### Sicherheit des Anwendungsservers {#application-server-security}

In der folgenden Tabelle werden einige Verfahren zum Schützen des Anwendungsservers nach der Installation der AEM Forms on JEE-Anwendung beschrieben.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Verwaltungskonsole des Anwendungsservers</p> </td> 
   <td><p>Nach der Installation, Konfiguration und Bereitstellung von AEM Forms on JEE auf dem Anwendungsserver müssen Sie den Zugriff auf die Verwaltungskonsolen des Anwendungsservers deaktivieren. Weitere Informationen finden Sie in der Dokumentation zum Anwendungsserver .</p> </td> 
  </tr> 
  <tr> 
   <td><p>Cookie-Einstellungen des Anwendungsservers</p> </td> 
   <td><p>Anwendungs-Cookies werden vom Anwendungsserver gesteuert. Beim Bereitstellen der Anwendung kann der Administrator des Anwendungsservers Cookie-Voreinstellungen serverweit oder anwendungsspezifisch festlegen. Standardmäßig haben die Servereinstellungen Vorrang.</p> <p>Alle vom Anwendungsserver erstellten Sitzungs-Cookies müssen das <code>HttpOnly</code>-Attribut enthalten. Wenn Sie beispielsweise den JBoss Application Server verwenden, können Sie das Element „SessionCookie“ in der Datei <code>WEB-INF/web.xml</code> auf <code>httpOnly="true"</code> ändern.</p> <p>Sie können festlegen, dass Cookies ausschließlich unter Verwendung von HTTPS gesendet werden. Dadurch wird verhindert, dass Cookies unverschlüsselt über HTTP gesendet werden. Anwendungsserveradministratoren sollten sichere Cookies für den Server global aktivieren. Bei Verwendung des JBoss-Anwendungsservers können Sie beispielsweise das Element „connector“ in der Datei <code>secure=true</code> in <code>server.xml</code> ändern.</p> <p>Weitere Informationen zu Cookie-Einstellungen finden Sie in der Dokumentation zum Anwendungsserver .</p> </td> 
  </tr> 
  <tr> 
   <td><p>Directory Browsing</p> </td> 
   <td><p>Wenn eine Person eine nicht vorhandene Seite oder den Namen eines Ordners anfordert (die Anforderungszeichenfolge endet in diesem Fall mit einem Schrägstrich (/)), sollte der Anwendungsserver den Inhalt dieses Ordners nicht zurückgeben. Damit dies nicht geschieht, können Sie das Directory Browsing auf Ihrem Anwendungsserver deaktivieren. Dies sollten Sie für die Administration Console-Anwendung und für andere Anwendungen tun, die auf Ihrem Server ausgeführt werden.</p> <p>Für JBoss stellen Sie in der Datei „web.xml“ den Wert des Auflistungsinitialisierungsparameters der Eigenschaft <code>DefaultServlet</code> auf <code>false</code> ein, wie im folgenden Beispiel gezeigt wird:</p> <p>&lt;servlet&gt;</p> <p>&lt;servlet-name&gt;default&lt;/servlet-name&gt;</p> <p>&lt;servlet-class&gt;</p> <p>org.apache.catalina.servlets.DefaultServlet</p> <p>&lt;/servlet-class&gt;</p> <p>&lt;init-param&gt;</p> <p>&lt;param-name&gt;listings&lt;/param-name&gt;</p> <p>&lt;param-value&gt;false&lt;/param-value&gt;</p> <p>&lt;/init-param&gt;</p> <p>&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;</p> <p>&lt;/servlet&gt;</p> <p>Für WebSphere stellen Sie in der Datei „ibm-web-ext.xml“ die Eigenschaft <code>directoryBrowsingEnabled</code> auf <code>false</code> ein.</p> <p>Für WebLogic stellen Sie in der Datei „weblogic.xml“ die Eigenschaften zu „index-directories“ auf <code>false</code> ein, wie im folgenden Beispiel gezeigt:</p> <p>&lt;container-descriptor&gt;</p> <p>&lt;index-directory-enabled&gt;false</p> <p>&lt;/index-directory-enabled&gt;</p> <p>&lt;/container-descriptor&gt;</p> </td> 
  </tr> 
 </tbody> 
</table>

### Datenbanksicherheit {#database-security}

Beim Schützen der Datenbank sollten Sie die vom Datenbankhersteller beschriebenen Sicherheitsmaßnahmen implementieren. Sie sollten einem Datenbankbenutzer die minimal für die Verwendung von AEM Forms on JEE erforderlichen Datenbankberechtigungen zuweisen. Verwenden Sie beispielsweise kein Konto mit Datenbankadministrator-Berechtigungen.

Unter Oracle benötigt das verwendete Datenbankkonto nur die Berechtigungen CONNECT, RESOURCE und CREATE VIEW. Für ähnliche Anforderungen an andere Datenbanken siehe [Vorbereiten der Installation von AEM Forms on JEE (Einzelserver)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64_de).

#### Integrierte Sicherheit für SQL Server unter Windows für JBoss konfigurieren {#configuring-integrated-security-for-sql-server-on-windows-for-jboss}

1. Ändern Sie [JBOSS_HOME]\\standalone\configuration\lc_{datasource.xml}, um `integratedSecurity=true` zur Verbindungs-URL hinzuzufügen, wie in diesem Beispiel gezeigt:

   ```java
    jdbc:sqlserver://<serverhost>:<port>;databaseName=<dbname>;integratedSecurity=true
   ```

1. Fügen Sie die Datei „sqljdbc_auth.dll“ zum Windows-Systempfad (C:\Windows) auf dem Computer hinzu, auf dem der Anwendungsserver ausgeführt wird. Die Datei „sqljdbc_auth.dll“ wird zusammen mit dem Microsoft SQL JDBC 6.2.1.0-Treiber installiert.
1. Ändern Sie die Eigenschaft des JBoss Windows-Dienstes (JBoss for AEM Forms on JEE) für „Anmelden als“ von „Lokales System“ in ein Anmeldekonto mit einer AEM Forms-Datenbank und einem Mindestsatz von Berechtigungen. Wenn Sie JBoss über die Befehlszeile anstatt als Windows-Dienst ausführen, müssen Sie diesen Schritt nicht ausführen.
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

#### Integrierte Sicherheit für SQL Server unter Windows für WebSphere konfigurieren {#configuring-integrated-security-for-sql-server-on-windows-for-websphere}

Unter WebSphere können Sie die integrierte Sicherheit nur konfigurieren, wenn Sie einen externen SQL Server-JDBC-Treiber verwenden, nicht aber den SQL Server JDBC-Treiber, der in WebSphere eingebettet ist.

1. Melden Sie sich bei WebSphere Administrative Console an.
1. Klicken Sie in der Navigationsstruktur auf **Resources** > **JDBC** > **Data Sources** und klicken Sie dann im rechten Bereich auf **IDP_DS**.
1. Klicken Sie im rechten Bereich unter „Additional Properties“ auf **Custom Properties** und dann auf **New**.
1. Geben Sie in das Feld **Name** den Wert `integratedSecurity` und in das Feld **Value** den Wert `true` ein.
1. Klicken Sie in der Navigationsstruktur auf **Resources** > **JDBC** > **Data Sources** und dann im rechten Bereich auf **RM_DS**.
1. Klicken Sie im rechten Bereich unter „Additional Properties“ auf **Custom Properties** und dann auf **New**.
1. Geben Sie in das Feld **Name** den Wert `integratedSecurity` und in das Feld **Value** den Wert `true` ein.
1. Fügen Sie auf dem Computer, auf dem WebSphere installiert ist, die Datei „sqljdbc_auth.dll“ dem Windows-Systempfad (C:\Windows) hinzu. Die Datei „sqljdbc_auth.dll“ befindet sich am selben Speicherort wie die Microsoft SQL JDBC 1.2-Treiberinstallation (standardmäßig unter *[Installationsordner]*/sqljdbc_1.2/enu/auth/x86).
1. Auswählen **Starten** > **Control Panel** > **Dienste** klicken Sie mit der rechten Maustaste auf den Windows-Dienst für WebSphere (IBM WebSphere Application Server). &lt;version> - &lt;node>) und wählen Sie **Eigenschaften**.
1. Klicken Sie im Dialogfeld Eigenschaften auf die **Anmelden** Registerkarte.
1. Auswählen **Dieses Konto** und geben Sie die Informationen an, die zum Festlegen des gewünschten Anmeldekontos erforderlich sind.
1. Sicherheitseinstellungen für SQL Server von **Gemischt** Modus zu **Nur Windows-Authentifizierung**.

### Schutz des Zugriffs auf vertrauliche Inhalte in der Datenbank {#protecting-access-to-sensitive-content-in-the-database}

Das AEM Forms-Datenbankschema enthält sensible Informationen über die Systemkonfiguration und Geschäftsprozesse und sollte hinter der Firewall geschützt sein. Die Datenbank sollte innerhalb derselben Vertrauensgrenze wie der Formularserver betrachtet werden. Um die Offenlegung von Informationen und den Diebstahl von Geschäftsdaten zu verhindern, muss die Datenbank vom Datenbankadministrator (DBA) so konfiguriert werden, dass nur autorisierte Administratoren Zugriff erhalten.

Als zusätzliche Vorsichtsmaßnahme sollten Sie erwägen, datenbankherstellerspezifische Tools zum Verschlüsseln von Spalten in Tabellen zu verwenden, die die folgenden Daten enthalten:

* Rights Management Document Keys
* HSM-PIN-Verschlüsselungsschlüssel für Trust Store
* Hashes für lokale Benutzerkennwörter

Informationen zu herstellerspezifischen Tools finden Sie unter [Informationen zur Datenbanksicherheit](https://helpx.adobe.com/de/aem-forms/6-1/hardening-security/general-security-considerations.html#database_security_information).

### LDAP-Sicherheit {#ldap-security}

AEM Forms on JEE nutzt meist einen LDAP-Ordner (Lightweight Directory Access Protocol) als Quelle für Informationen über Unternehmensbenutzer und Gruppen sowie zur Durchführung der Kennwortauthentifizierung. Sie sollten sicherstellen, dass Ihr LDAP-Ordner für die Verwendung von Secure Socket Layer (SSL) konfiguriert ist und AEM Forms on JEE für den Zugriff auf Ihren LDAP-Ordner über dessen SSL-Anschluss konfiguriert ist.

#### LDAP-Dienstverweigerung {#ldap-denial-of-service}

Angriffe mittels LDAP bestehen häufig darin, dass ein Angreifer die Authentifizierung bewusst mehrmals fehlschlagen lässt. Dies zwingt den LDAP Directory Server, einen Benutzer von allen LDAP-abhängigen Diensten abzusperren.

Sie können die Anzahl fehlgeschlagener Versuche sowie die nachfolgende Sperrdauer festlegen, die AEM Forms implementiert, wenn die AEM Forms-Authentifizierung eines Benutzers wiederholt fehlschlägt. Wählen Sie in der Administration-Console niedrige Werte. Bei der Auswahl der Anzahl fehlgeschlagener Versuche ist zu beachten, dass AEM Forms den Benutzer nach allen Versuchen sperrt, bevor dies vom LDAP-Ordnerserver erfolgt.

#### Automatische Kontosperrung festlegen {#set-automatic-account-locking}

1. Melden Sie sich bei Administration Console an.
1. Klicken Sie auf **Einstellungen** > **User Management** > **Domain-Verwaltung**.
1. Legen Sie unter &quot;Einstellungen für die automatische Kontosperrung&quot;fest. **Maximale Anzahl aufeinander folgender Authentifizierungsfehler** auf eine niedrige Zahl, z. B. 3.
1. Klicken Sie auf **Speichern**.

### Auditing und Protokollierung {#auditing-and-logging}

Der richtige und sichere Einsatz der Anwendungsprüfung und -protokollierung kann dazu beitragen, dass sicherheitsrelevante und andere, unnormale Ereignisse schnellstmöglich verfolgt und erkannt werden. Die effektive Verwendung von Prüfung und Protokollierung innerhalb einer Anwendung umfasst Elemente wie das Tracking erfolgreicher und fehlgeschlagener Anmeldungen sowie wichtige Anwendungsereignisse wie das Erstellen oder Löschen von Schlüsseldatensätzen.

Sie können die Prüfung verwenden, um viele Arten von Angriffen zu erkennen, darunter die folgenden:

* Brute-Force-Kennwortangriffe
* Denial-of-Service-Angriffe
* Einschleusen von feindseligen Eingaben und ähnlichen Klassen von Skriptangriffen

In dieser Tabelle werden Prüfungs- und Protokollierungsverfahren beschrieben, mit denen Sie die Sicherheitslücken Ihres Servers verringern können.

<table> 
 <thead> 
  <tr> 
   <th><p>Problem</p> </th> 
   <th><p>Beschreibung</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>ACLs der Protokolldatei</p> </td> 
   <td><p>Legen Sie die entsprechenden Zugriffssteuerungslisten (ACLs) für die AEM Forms on JEE-Protokolldatei fest.</p> <p>Das Festlegen der entsprechenden Anmeldeinformationen verhindert, dass Angreifer die Dateien löschen.</p> <p>Als Sicherheitsberechtigung für das Protokolldateiordner sollte „Alle Berechtigungen“ für Administratoren und SYSTEM-Gruppen festgelegt werden. Das AEM Forms-Benutzerkonto sollte nur Lese- und Schreibberechtigungen besitzen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Redundanz der Protokolldatei</p> </td> 
   <td><p>Wenn die Ressourcen dies zulassen, senden Sie Protokolle in Echtzeit an einen anderen Server, auf den der Angreifer nicht zugreifen kann (nur Schreiben), indem Sie Syslog, Tivoli, den Microsoft Operations Manager (MOM)-Server oder einen anderen Mechanismus verwenden.</p> <p>Wenn Sie Protokolle auf diese Weise schützen, erschweren Sie damit mögliche Manipulationen. Das Speichern von Protokollen in einem zentralen Repository erleichtert zudem die Korrelation und Überwachung (z. B. wenn mehrere Formularserver verwendet werden und auf mehreren Computern, auf denen jeder Computer nach einem Kennwort abgefragt wird, ein Password Guessing-Angriff stattfindet).</p> </td> 
  </tr> 
 </tbody> 
</table>

### Nicht-Administrator-Benutzer zum Ausführen von PDF Generator aktivieren

Sie können Benutzern ohne Administratorrechte die Verwendung von PDF Generator ermöglichen. Normalerweise können nur Benutzer mit Administratorrechten PDF Generator verwenden. Führen Sie die folgenden Schritte aus, um Benutzern ohne Administratorrechte die Ausführung von PDF Generator zu ermöglichen:

1. Erstellen Sie den Umgebungsvariablennamen PDFG_NON_ADMIN_ENABLED.

1. Legen Sie als Wert der Variablen TRUE fest.

1. Starten Sie die AEM Forms-Instanz neu.

## Konfigurieren von AEM Forms on JEE für den Zugriff außerhalb des Unternehmens {#configuring-aem-forms-on-jee-for-access-beyond-the-enterprise}

Nachdem Sie AEM Forms on JEE erfolgreich installiert haben, müssen Sie die Sicherheitseinrichtungen der Umgebung unbedingt in regelmäßigen Abständen warten. In diesem Abschnitt werden die empfohlenen Aufgaben zur Gewährleistung der Sicherheit Ihres AEM Forms on JEE-Produktionsservers beschrieben.

### Reverse-Proxy für Webzugriff einrichten {#setting-up-a-reverse-proxy-for-web-access}

Sie können einen *Reverse-Proxy* verwenden, um sicherzustellen, dass eine Gruppe von URLs für AEM Forms on JEE-Webanwendungen sowohl für externe als auch interne Benutzer verfügbar ist. Diese Konfiguration bietet mehr Sicherheit als die Erlaubnis für Benutzer, eine direkte Verbindung zu dem Anwendungsserver herzustellen, auf dem AEM Forms on JEE ausgeführt wird. Der Reverse-Proxy führt alle HTTP-Anfragen für den Anwendungsserver durch, auf dem AEM Forms on JEE läuft. Benutzer haben nur Netzwerkzugriff auf den Reverse-Proxy und können nur URL-Verbindungen versuchen, die vom Reverse-Proxy unterstützt werden.

**Stammordner-URLs in AEM Forms auf JEE für die Verwendung mit dem Reverse-Proxy-Server**

Die folgenden Anwendungsstamm-URLs für jede AEM Forms on JEE-Webanwendung. Sie sollten Ihren Reverse-Proxy nur so konfigurieren, dass URLs für Webanwendungsfunktionen verfügbar gemacht werden, die Sie Endbenutzern bereitstellen möchten.

Einige URLs sind als Endbenutzer-orientierte Webanwendungen gekennzeichnet. Sie sollten vermeiden, andere URLs für Configuration Manager für den Zugriff auf externe Benutzer über den Reverse-Proxy verfügbar zu machen.

<table> 
 <thead> 
  <tr> 
   <th><p>Stamm-URL</p> </th> 
   <th><p>Zweck und/oder verknüpfte Webanwendung</p> </th> 
   <th><p>Webbasierte Benutzeroberfläche</p> </th> 
   <th><p>Endbenutzerzugriff</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>/ReaderExtensions/*</p> </td> 
   <td><p>Acrobat Reader DC Extensions-Webanwendung für Endbenutzer zum Anwenden von Verwendungsrechten auf PDF-Dokumente</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/*</p> </td> 
   <td><p>Rights Management-Webanwendung für Endbenutzer</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edcws/*</p> </td> 
   <td><p>Webdienst-URL für Rights Management</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/pdfgui/*</p> </td> 
   <td><p>PDF Generator-Webanwendung für die Administration</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/Arbeitsbereich/*</p> </td> 
   <td><p>Workspace-Webanwendung für Endbenutzer</p> </td> 
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
   <td><p>Servlet für das Bootstrapping des AEM Forms on JEE-Repositorys</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/soap/*</p> </td> 
   <td><p>Informationsseite für Formularserver-Webdienste</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/soap/services/*</p> </td> 
   <td><p>Webdienst-URL für alle Formularserverdienste</p> </td> 
   <td><p>Nein</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/admin/*</p> </td> 
   <td><p>Rights Management Administration-Webanwendung</p> </td> 
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
   <td><p>Forms IVS-Anwendung zum Testen und Debuggen der Formularwiedergabe</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/OutputIVS/*</p> </td> 
   <td><p>Output IVS-Anwendung zum Testen und Debuggen des Output-Dienstes</p> </td> 
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
   <td><p>Forms-Webanwendungsdateien</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nein</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServer/GetImage</p> <p>Servlet</p> </td> 
   <td><p>Wird zum Abrufen von JavaScript während der HTML-Transformation verwendet</p> </td> 
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
   <td><p>Benutzeroberfläche "Anwendungen und Dienste"</p> </td> 
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
   <td><p>Übrige Support-Seiten</p> </td> 
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
   <td><p>Hochladen und Herunterladen von Dokumenten, die beim Zugriff auf Remoting-Endpunkte, SOAP WSDL-Endpunkte und das Java SDK über SOAP-Transport oder EJB-Transport mit aktivierten HTTP-Dokumenten verarbeitet werden sollen.</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
 </tbody> 
</table>

## Schutz vor Cross-Site Request Forgery-Angriffen {#protecting-from-cross-site-request-forgery-attacks}

Bei einem Cross-Site Request Forgery-Angriff (CSRF) wird die Vertrauensstellung einer Website für den Benutzer ausgenutzt, um Befehle zu übertragen, die vom Benutzer nicht autorisiert wurden und vom Benutzer nicht beabsichtigt sind. Dazu wird ein Link oder ein Skript in eine Web-Seite bzw. eine URL in eine E-Mail-Nachricht eingefügt, um auf eine andere Website zuzugreifen, für die der Benutzer bereits authentifiziert wurde.

Sie könnten beispielsweise bei der Administration-Console angemeldet sein und gleichzeitig eine andere Website durchsuchen. Eine der Webseiten kann ein HTML-Bild-Tag mit einem `src`-Attribut enthalten, dessen Ziel ein serverseitiges Skript auf einer Opfer-Website ist. Webbrowser verwenden einen auf Cookies basierenden Mechanismus zur Sitzungsauthentifizierung. Dies wird von der angreifenden Website ausgenutzt. Sie sendet bösartige Anforderungen an das serverseitige Opferskipt und gibt vor, der rechtmäßige Benutzer zu sein. Weitere Beispiele finden Sie unter [https://owasp.org/www-community/attacks/csrf#Examples](https://owasp.org/www-community/attacks/csrf#Examples).

Die folgenden Eigenschaften sind für CSRF-Dateien üblich:

* Betreffen Sites, die auf der Identität eines Benutzers basieren.
* Nutzen Sie das Vertrauen der Site in diese Identität.
* Bringen Sie den Browser des Benutzers dazu, HTTP-Anfragen an eine Ziel-Site zu senden.
* Schließen HTTP-Anfragen mit Nebenwirkungen ein.

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
   1. Wenn es sich nicht um eine Ausnahme handelt, wird die Anforderung übergeben.

1. Wenn in der Anfrage kein Referrer angegeben ist, prüft der Server, ob ein Null-Referrer zulässig ist:

   1. Wenn ein Null-Referrer zulässig ist, wird die Anfrage übergeben.
   1. Wenn ein Null-Referrer nicht zulässig ist, prüft der Server, ob der angeforderte URI eine Ausnahme für den Null-Referrer ist, und behandelt die Anfrage entsprechend.

### Verwalten des Referrer-Filters {#managing-referer-filtering}

AEM Forms auf JEE bietet einen Referrer-Filter, um Referrer anzugeben, denen der Zugriff auf Server-Ressourcen erlaubt wird. Der Referrer-Filter filtert standardmäßig keine Anfragen, die eine sichere HTTP-Methode, z. B. GET, verwenden, es sei denn, *CSRF_CHECK_GETS* ist auf „true“ festgelegt. Wenn die Port-Nummer für den Eintrag eines zulässigen Referrers auf 0 festgelegt ist, lässt AEM Forms auf JEE alle Anfragen mit Referrern von diesem Host unabhängig von der Port-Nummer zu. Wenn keine Anschlussnummer angegeben wird, werden nur Anforderungen vom Standardanschluss 80 (HTTP) oder von Anschluss 443(HTTPS) zugelassen. Der Referrer-Filter wird deaktiviert, wenn alle Einträge in der Liste der zulässigen Referrer gelöscht werden.

Wenn Sie Document Services zum ersten Mal installieren, wird die Liste für zulässige Referrer mit der Adresse des Servers aktualisiert, auf dem Document Services installiert wird. Die Einträge für den Server enthalten den vollständig Servernamen, die IPv4-Adresse, die IPv6-Adresse, wenn IPv6 aktiviert ist, die Loopback-Adresse und einen „localhost“-Eintrag. Die Namen, die zur Liste der zulässigen verweisenden Stellen (auch als Liste „Zulässige Referrer“ bezeichnet)“ hinzugefügt wurden, werden vom Betriebssystem des Hosts zurückgegeben. Beispielsweise enthält ein Server mit der IP-Adresse 10.40.54.187 die folgenden Einträge: `https://server-name:0, https://10.40.54.187:0, https://127.0.0.1:0, http://localhost:0`. Für nicht qualifizierten Namen, die vom Host-Betriebssystem zurückgegeben wurden (Namen, die keine IPv4-Adresse, IPv6-Adresse oder qualifizierte Domain-Namen haben), erfolgt keine Aktualisierung der Zulassungsliste. Ändern Sie die Liste der zulässigen verweisenden Stellen entsprechend Ihrer Geschäftsumgebung. Den Formular-Server nicht mit der Standardliste der zulässigen verweisenden Stellen in der Produktionsumgebung bereitstellen. Nachdem Sie die zulässigen Referrer, Referrer-Ausnahmen oder URIs geändert haben, müssen Sie den Server neu starten, damit die Änderungen wirksam werden.

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

Verwenden Sie die Liste ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** für „Zulässige Referrer – Ausnahmen“ auf globaler Ebene, d. h. um Ausnahmen zu definieren, die für alle Anwendungen gelten. Diese Liste enthält nur URIs mit entweder einem absoluten Pfad (z. B. `/index.html`) oder einem relativen Pfad (z. B. `/sample/`). Sie können auch einen regulären Ausdruck am Ende eines relativen URI anhängen, z. B. `/sample/(.)*`.

Die Listen-ID ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** wird als Konstante in der Klasse `UMConstants` des Namespace `com.adobe.idp.um.api` definiert, der in `adobe-usermanager-client.jar` zu finden ist. Sie können die AEM Forms-APIs zum Erstellen, Ändern oder Bearbeiten dieser Liste verwenden. Um beispielsweise die Liste für globale zulässigen Referrer - Ausnahmen zu verwenden, gehen Sie folgendermaßen vor:

```java
addAllowedRefererExceptions(UMConstants.LC_GLOBAL_ALLOWED_REFERER_EXCEPTION, Arrays.asList("/index.html", "/sample/(.)*"))
```

Verwenden Sie die Liste ***CSRF_ALLOWED_REFERER_EXCEPTIONS*** für anwendungsspezifische Ausnahmen.

**Deaktivieren des Referrer-Filters**

Falls der Referrer-Filter den Zugriff auf den Formularserver vollkommen sperrt und Sie die Liste der zulässigen verweisenden Stellen nicht bearbeiten können, können Sie das Startskript des Server aktualisieren und die Referrer-Filterung deaktivieren. 

Fügen Sie das JAVA-Argument `-Dlc.um.csrffilter.disabled=true` in das Startskript ein und starten Sie den Server neu. Löschen Sie das JAVA-Argument, nachdem Sie die Liste der zulässigen verweisenden Stellen entsprechend neu konfiguriert haben.

**Referrer-Filterung bei benutzerdefinierten WAR-Dateien**

Möglicherweise haben Sie benutzerdefinierte WAR-Dateien für die Verwendung mit AEM Forms on JEE speziell für Ihre Geschäftsanforderungen erstellt. Um die Referrer-Filterung bei benutzerdefinierten WAR-Dateien zu aktivieren, fügen Sie ***adobe-usermanager-client.jar*** in den Klassenpfad für die WAR-Datei ein und nehmen Sie in die Datei web.xml einen Filtereintrag mit den folgenden Parametern vor:

**CSRF_CHECK_GETS** – steuert die Referrer-Prüfung bei GET-Anforderungen. Wenn dieser Parameter nicht definiert ist, wird für den Standardwert „false“ festgelegt. Schließen Sie diesen Parameter nur ein, wenn Sie Ihre GET-Anforderungen filtern möchten.

**CSRF_ALLOWED_REFERER_EXCEPTIONS** – ist die ID der Liste „Zulässige Referrer – Ausnahmen“. Der Referrer-Filter verhindert, dass Anfragen, die von Referrern in der durch die Listen-ID identifizierten Liste stammen, Ressourcen auf dem Formularserver aufrufen.

**CSRF_ALLOWED_URIS_LIST_NAME** ist die ID der Liste „Zulässige URIs“. Der Referrer-Filter blockiert keine Anfragen an Ressourcen der Liste, die unabhängig vom Wert des Referrer-Headers in der Anfrage durch die Listen-ID identifiziert wird.

**CSRF_ALLOW_NULL_REFERER** – steuert das Verhalten des Referrer-Filters, wenn der Referrer null oder nicht vorhanden ist. Wenn dieser Parameter nicht definiert wird, wird für den Standardwert „false“ festgelegt. Fügen Sie diesen Parameter nur ein, wenn Sie Null-Referrer zulassen möchten. Das Zulassen eines Null-Referrers kann einige Arten von CSRF-Angriffen ermöglichen.

**CSRF_NULL_REFERER_EXCEPTIONS** – ist eine Liste der URIs, für die keine Referrer-Prüfung durchgeführt wird, wenn der Referrer null ist. Dieser Parameter ist nur aktiviert, wenn *CSRF_ALLOW_NULL_REFERER* auf &quot;false&quot;gesetzt ist. Trennen Sie mehrere URIs in der Liste durch ein Komma.

Im Folgenden finden Sie ein Beispiel für den Filtereintrag im *web.xml* -Datei ***BEISPIEL*** WAR-Datei:

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

Wenn vom CSRF-Filter legitime Serveranforderungen blockiert werden, versuchen Sie eine der folgenden Aktionen:

* Wenn die abgelehnte Anfrage eine Referrer-Kopfzeile hat, sollte sorgfältig abgewogen werden, ob sie in die Liste der erlaubten Referrer aufgenommen werden soll. Fügen Sie nur Referrer hinzu, denen Sie vertrauen.
* Wenn die abgelehnte Anfrage keine Referrer-Kopfzeile hat, ändern Sie Ihr Client-Programm so, dass eine Referrer-Kopfzeile eingefügt wird.
* Wenn der Client in einem Browser arbeiten kann, versuchen Sie dieses Bereitstellungsmodell.
* Als letztes Mittel können Sie die Ressource zur Liste der zulässigen URIs hinzufügen. Dies ist keine empfohlene Einstellung.

## Sichere Netzwerkkonfiguration {#secure-network-configuration}

In diesem Abschnitt werden die Protokolle und Anschlüsse beschrieben, die für AEM Forms on JEE erforderlich sind, und es werden Empfehlungen für die Bereitstellung von AEM Forms on JEE in einer sicheren Netzwerkkonfiguration bereitgestellt.

### Von AEM Forms on JEE verwendete Netzwerkprotokolle {#network-protocols-used-by-aem-forms-on-jee}

Wenn Sie eine sichere Netzwerkarchitektur wie im vorherigen Abschnitt beschrieben konfigurieren, sind die folgenden Netzwerkprotokolle für die Interaktion zwischen AEM Forms on JEE und anderen Systemen in Ihrem Unternehmensnetzwerk erforderlich.

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
     <li><p>Browser zeigt Configuration Manager und Webanwendungen für Endbenutzer an</p> </li> 
     <li><p>Alle SOAP-Verbindungen</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td> 
    <ul> 
     <li><p>Webdienst-Clientanwendungen wie .NET-Anwendungen</p> </li> 
     <li><p>Adobe Reader® verwendet SOAP für AEM Forms on JEE-Server-Webdienste</p> </li> 
     <li><p>Adobe Flash®-Anwendungen verwenden SOAP für Formularserver-Webdienste</p> </li> 
     <li><p>AEM Forms on JEE SDK-Aufrufe bei Verwendung im SOAP-Modus</p> </li> 
     <li><p>Workbench-Design-Umgebung</p> </li> 
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
     <li><p>E-Mail-basierte Eingabe für einen Dienst (E-Mail-Endpunkt)</p> </li> 
     <li><p>Benachrichtigungen zu Benutzeraufgaben über E-Mails</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>UNC File IO</p> </td> 
   <td><p>AEM Forms on JEE-Überwachung von überwachten Ordnern auf Eingabe in einen Dienst (Endpunkt des überwachten Ordners)</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td> 
    <ul> 
     <li><p>Synchronisation von Informationen zu Organisationsbenutzern und -gruppen in einem Ordner</p> </li> 
     <li><p>LDAP-Authentifizierung für interaktive Benutzer</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>JDBC</p> </td> 
   <td> 
    <ul> 
     <li><p>Abfrage- und Prozessaufrufe, die während der Ausführung eines Prozesses mit dem JDBC-Dienst an eine externe Datenbank gesendet werden</p> </li> 
     <li><p>Interner Zugriff auf das AEM Forms on JEE-Repository</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebDAV</p> </td> 
   <td><p>Ermöglicht das Remote-Durchsuchen des Entwurfszeitrepository von AEM Forms on JEE (Formulare, Fragmente usw.) durch einen beliebigen WebDAV-Client</p> </td> 
  </tr> 
  <tr> 
   <td><p>AMF</p> </td> 
   <td><p>Adobe Flash-Anwendungen, bei denen AEM Forms on JEE-Serverdienste mit einem Remoting-Endpunkt konfiguriert sind</p> </td> 
  </tr> 
  <tr> 
   <td><p>JMX</p> </td> 
   <td><p>AEM Forms on JEE stellt MBeans für die Überwachung mit JMX bereit</p> </td> 
  </tr> 
 </tbody> 
</table>

### Ports für Anwendungsserver {#ports-for-application-servers}

In diesem Abschnitt werden die Standardanschlüsse (und alternativen Konfigurationsbereiche) für jeden unterstützten Anwendungsservertyp beschrieben. Diese Ports müssen in der inneren Firewall aktiviert oder deaktiviert werden, je nachdem, welche Netzwerkfunktionalität Sie für Clients zulassen möchten, die eine Verbindung zum Anwendungsserver herstellen, auf dem AEM Forms on JEE ausgeführt wird.

>[!NOTE]
>
>Standardmäßig legt der Server mehrere JMX MBeans unter dem Namespace adobe.com offen. Dabei werden nur für die Überwachung des Serverzustands nützliche Informationen offengelegt. Um jedoch die Offenlegung von Informationen zu verhindern, sollten Sie Aufrufer in einem nicht vertrauenswürdigen Netzwerk daran hindern, JMX MBeans zu suchen und auf Gesundheitsmetriken zuzugreifen.

**JBoss-Anschlüsse**

<table> 
 <thead> 
  <tr> 
   <th><p>Zweck</p> </th> 
   <th><p>Port</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Zugriff auf Webanwendungen</p> </td> 
   <td><p>[JBOSS_Root]/standalone/configuration/lc_[database].xml</p> <p>HTTP/1.1 Connector-Anschluss 8080</p> <p>AJP 1.3 Connector-Anschluss 8009</p> <p>SSL-/TLS-Connector-Anschluss 8443</p> </td> 
  </tr> 
  <tr> 
   <td><p>CORBA-Unterstützung</p> </td> 
   <td><p>[JBoss-Stammordner]/server/all/conf/jacorb.properties</p> <p>OAPort 3528</p> <p>OASSLPort 3529</p> </td> 
  </tr> 
 </tbody> 
</table>

**WebLogic-Anschlüsse**

<table> 
 <thead> 
  <tr> 
   <th><p>Zweck</p> </th> 
   <th><p>Port</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Zugriff auf Webanwendungen</p> </td> 
   <td> 
    <ul> 
     <li><p>Überwachungsanschluss des Administrationsservers: Standardwert ist 7001</p> </li> 
     <li><p>Überwachungsanschluss des Administrationsservers: Standardwert ist 7002</p> </li> 
     <li><p>Für verwalteten Server konfigurierter Anschluss, z. B. 8001</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic-Administrationsports sind für den Zugriff auf AEM Forms on JEE nicht erforderlich</p> </td> 
   <td> 
    <ul> 
     <li><p>Überwachungsanschluss des verwalteten Servers: Konfigurierbar zwischen 1 und 65534</p> </li> 
     <li><p>Verwalteter Server-SSL-Überwachungsanschluss: Konfigurierbar zwischen 1 und 65534</p> </li> 
     <li><p>Node Manager - Überwachungsanschluss: Standardwert ist 5556.</p> </li> 
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

### SSL-Umleitung konfigurieren {#configuring-ssl-redirect}

Nachdem Sie Ihren Anwendungsserver für die Unterstützung von SSL konfiguriert haben, müssen Sie sicherstellen, dass der gesamte HTTP-Traffic zu Anwendungen und Diensten zur Verwendung des SSL-Anschlusses erzwungen wird.

Informationen zum Konfigurieren der SSL-Umleitung für WebSphere oder WebLogic finden Sie in der Dokumentation zum Anwendungsserver.

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

Dieser Abschnitt enthält Sicherheitsempfehlungen, die für Windows spezifisch sind, wenn AEM Forms on JEE ausgeführt wird.

### JBoss-Dienstkonten {#jboss-service-accounts}

Bei der AEM Forms on JEE-Turnkey-Installation wird standardmäßig unter Verwendung des Kontos „Lokales System“ ein Dienstkonto eingerichtet. Das integrierte Benutzerkonto „Lokales System“ hat hohe Zugriffsrechte; es gehört zur Gruppe „Administratoren“. Wenn eine Worker Process-Identität als das Benutzerkonto &quot;Lokales System&quot;ausgeführt wird, hat dieser Worker Process vollen Zugriff auf das gesamte System.

#### Ausführen des Anwendungsservers mit einem Konto ohne Administratorrechte {#run-the-application-server-using-a-non-administrative-account}

1. Erstellen Sie in der Microsoft Management Console (MMC) einen lokalen Benutzer für den Formularserverdienst, der sich wie folgt anmeldet:

   * Auswählen **Benutzer können Kennwort nicht ändern**.
   * Stellen Sie sicher, dass auf der Registerkarte **Mitglied von** die Gruppe „Benutzer“ aufgeführt ist.

1. Auswählen **Einstellungen** > **Administrationstools** > **Dienste**.
1. Doppelklicken Sie auf den Dienst für den Anwendungsserver und beenden Sie den Dienst.
1. Im **Anmelden** Registerkarte, wählen Sie **Dieses Konto**, suchen Sie nach dem von Ihnen erstellten Benutzerkonto und geben Sie das Kennwort für das Konto ein.
1. Weisen Sie im Fenster &quot;Lokale Sicherheitseinstellungen&quot;unter &quot;Zuweisung von Benutzerrechten&quot;dem Benutzerkonto, unter dem der Formularserver ausgeführt wird, die folgenden Berechtigungen zu:

   * Anmeldung über Terminaldienste verweigern
   * Anmeldung bei „locallyxx“ verweigern
   * Als Dienst anmelden (sollte bereits festgelegt sein)

1. Weisen Sie dem neuen Benutzerkonto Berechtigungen zum Ändern der folgenden Verzeichnisse zu:
   * **Verzeichnis des globalen Dokumentenspeichers (GDS)**: Der Speicherort des GDS-Verzeichnisses wird während der Installation von AEM Forms manuell konfiguriert. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Verzeichnis unter dem Installationsverzeichnis des Anwendungsservers gewählt: `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository-Verzeichnis**: Der Standardspeicherort lautet `[AEM-Forms-installation-location]\crx-repository`
   * **Temporäre Verzeichnisse von AEM Forms**:
      * (Windows) TMP- oder TEMP-Pfad gemäß Einstellung in den Umgebungsvariablen
      * (AIX, Linux oder Solaris) Basisordner des angemeldeten Benutzers Auf UNIX-basierten Systemen kann ein Benutzer ohne Stammordner den folgenden Ordner als temporären Ordner verwenden:
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


1. Starten Sie den Anwendungsserverdienst.

### Dateisystemsicherheit {#file-system-security}

AEM Forms on JEE verwendet das Dateisystem wie folgt:

* Speichert temporäre Dateien, die bei der Verarbeitung von Dokumenteingabe und -ausgabe verwendet werden
* Speichert Dateien im globalen Archiv, die zur Unterstützung der installierten Lösungskomponenten verwendet werden
* In überwachten Ordnern werden abgelegte Dateien gespeichert, die von einem Speicherort des Dateisystemordners aus als Eingabe für einen Dienst verwendet werden

Wenn Sie überwachte Ordner als Möglichkeit zum Senden und Empfangen von Dokumenten mit einem Formularserverdienst verwenden, sollten Sie zusätzliche Vorsichtsmaßnahmen im Hinblick auf die Dateisystemsicherheit treffen. Wenn ein Benutzer Inhalte in einem überwachten Ordner ablegt, werden diese Inhalte durch den überwachten Ordner offengelegt. In diesem Fall wird der tatsächliche Endbenutzer nicht vom Dienst authentifiziert. Stattdessen ist es darauf angewiesen, dass die Sicherheit auf ACL- und Freigabeebene auf Ordnerebene festgelegt wird, um zu bestimmen, wer den Dienst effektiv aufrufen kann.

## JBoss-spezifische Sicherheitsempfehlungen {#jboss-specific-security-recommendations}

Dieser Abschnitt enthält spezielle Empfehlungen für die Anwendungsserverkonfiguration, die gelten, wenn JBoss 7.0.6 für die Ausführung von AEM Forms on JEE verwendet wird.

### JBoss Management Console und JMX Console deaktivieren {#disable-jboss-management-console-and-jmx-console}

Wenn Sie AEM Forms mit der Turnkey-Installationsmethode unter JBoss installieren, ist der Zugriff auf JBoss Management Console und die JMX-Konsole bereits konfiguriert (die JMX-Überwachung ist deaktiviert). Wenn Sie Ihren eigenen JBoss Application Server verwenden, stellen Sie sicher, dass der Zugriff auf die JBoss Management Console und die JMX-Überwachungskonsole gesichert ist. Der Zugriff auf die JMX-Überwachungskonsole wird in der JBoss-Konfigurationsdatei jmx-invoker-service.xml festgelegt.

### Ordnersuche deaktivieren {#disable-directory-browsing}

Nach der Anmeldung bei Administration Console können Sie die Ordnerliste der Konsole durchsuchen, indem Sie die URL ändern. Wenn Sie beispielsweise die URL in eine der folgenden URLs ändern, wird eine Liste angezeigt:

```java
https://<servername>:8080/adminui/secured/ 
https://<servername>:8080/um/
```

## WebLogic-spezifische Sicherheitsempfehlungen {#weblogic-specific-security-recommendations}

Dieser Abschnitt enthält Empfehlungen für die Anwendungsserverkonfiguration zum Schützen von WebLogic 9.1 beim Ausführen von AEM Forms on JEE.

### Ordnersuche deaktivieren {#disable_directory_browsing-1}

Stellen Sie in der Datei „weblogic.xml“ die Eigenschaften zu „index-directories“ auf `false` ein, wie im folgenden Beispiel gezeigt:

```xml
<container-descriptor> 
    <index-directory-enabled>false 
    </index-directory-enabled> 
</container-descriptor>
```

### WebLogic SSL-Anschluss aktivieren {#enable-weblogic-ssl-port}

Standardmäßig aktiviert WebLogic nicht den standardmäßigen SSL Listen Port 7002. Aktivieren Sie diesen Anschluss in WebLogic Server Administration Console, bevor Sie SSL konfigurieren.

## WebSphere-spezifische Sicherheitsempfehlungen {#websphere-specific-security-recommendations}

Dieser Abschnitt enthält Empfehlungen zur Konfiguration des Anwendungsservers zum Schützen von WebSphere beim Ausführen von AEM Forms on JEE.

### Ordnersuche deaktivieren {#disable_directory_browsing-2}

Legen Sie in der Datei „ibm-web-ext.xml“ die Eigenschaft `directoryBrowsingEnabled` auf `false` fest.

### Administrative Sicherheit von WebSphere aktivieren {#enable-websphere-administrative-security}

1. Melden Sie sich bei WebSphere Administrative Console an.
1. Navigieren Sie in der Navigationsstruktur zu **Sicherheit** > **Globale Sicherheit**
1. Auswählen **Administrative Sicherheit aktivieren**.
1. Deaktivieren Sie beide **Anwendungssicherheit aktivieren** und **Java 2-Sicherheit verwenden**.
1. Klicken **OK** oder **Anwenden**.
1. Im **Nachrichten** Feld, klicken Sie auf **Direktes Speichern in der Übergeordneten Konfiguration**.
