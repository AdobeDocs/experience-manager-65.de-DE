---
title: Technische Anforderungen
seo-title: Technical Requirements
description: Eine Liste der unterstützten Client- und Serverplattformen für AEM.
seo-description: A list of the supported client and server platforms for AEM.
content-type: reference
topic-tags: platform
exl-id: 47529b9a-c4e5-434f-ac26-b01714ff863b
source-git-commit: 80298613370c7187288b33e5a665a074ccb5cd3e
workflow-type: tm+mt
source-wordcount: '3292'
ht-degree: 83%

---

# Technische Anforderungen{#technical-requirements}

Adobe unterstützt Adobe Experience Manager (AEM) auf den Plattformen, die in diesem Dokument ausführlich beschrieben werden.

Bei Problemen, die speziell mit der Plattform in Verbindung stehen, wenden Sie sich an den Plattformanbieter.

>[!NOTE]
>
>Je nach Plattform, auf der Sie AEM installieren, können die Anforderungen für die Benutzerverwaltung variieren.

## Voraussetzungen {#prerequisites}

Mindestanforderungen für die Installation von Adobe Experience Manager:

* Installierte Java-Plattform, Standard Edition JDK oder andere unterstützte [Java Virtual Machines](#java-virtual-machines)
* Experience Manager Quickstart-Datei (eigenständige JAR-Datei oder Web-Anwendungsbereitstellungs-WAR-Datei)

### Mindestgrößenanforderungen {#minimum-sizing-requirements}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* 5 GB freier Speicherplatz im Installationsverzeichnis
* 2 GB Arbeitsspeicher

>[!NOTE]
>
>* Digitale Assets benötigen mehr Grundspeicher. Einzelheiten finden Sie unter [Bereitstellung und Wartung](/help/sites-deploying/deploy.md#default-local-install).
>* Das [AEM Forms Add-on-Paket](/help/forms/using/installing-configuring-aem-forms-osgi.md) benötigt 15 GB temporären Speicherplatz. 
>


Weitere Informationen finden Sie in den [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md).

### Unterstützungsebenen {#support-levels}

In diesem Dokument werden die unterstützten Client- und Serverplattformen für Adobe Experience Manager aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für empfohlene und andere Konfigurationen gelten.

### Unterstützte Konfigurationen {#supported-configurations}

Adobe empfiehlt diese Konfigurationen und stellt im Zuge der standardmäßigen Vereinbarung für die Softwarewartung vollständige Unterstützung bereit.

<table>
 <tbody>
  <tr>
   <td>Unterstützungsebene</td>
   <td>Beschreibung<br /> </td>
  </tr>
  <tr>
   <td><strong>A: Unterstützt</strong></td>
   <td>Adobe bietet eine vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird durch den Adobe-Qualitätssicherungsprozess abgedeckt.</td>
  </tr>
  <tr>
   <td><strong>R: Eingeschränkte Unterstützung </strong></td>
   <td>Um den Projekterfolg der Kunden sicherzustellen, bietet Adobe innerhalb eines eingeschränkten Unterstützungsprogramms vollständige Unterstützung, wofür bestimmte Bedingungen erfüllt sein müssen. Für die Unterstützung auf R-Level sind eine formale Kundenanfrage und die Bestätigung durch Adobe erforderlich. Weitere Informationen erhalten Sie von der Adobe-Kundenunterstützung.</td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| **Z: Nicht unterstützt** | Die Konfiguration wird nicht unterstützt. Adobe macht keinerlei Aussagen, ob die Konfiguration funktioniert, und unterstützt diese nicht. |

## Unterstützte Plattformen {#supported-platforms}

### Java Virtual Machines {#java-virtual-machines}

Für die Anwendung muss eine Java Virtual Machine ausgeführt werden, die durch das Java Development Kit (JDK) verteilt wird.

Adobe Experience Manager funktioniert mit den folgenden Versionen von Java Virtual Machine:

>[!CAUTION]
>
>Es wird empfohlen, die Sicherheitsbulletins vom Java-Anbieter zu verfolgen, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java-Aktualisierungen zu installieren.

| **Plattform** | **Unterstützungsebene** | **Verknüpfung** |
|---|---|---|
| Oracle Java SE 11 JDK – 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+11*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=24&lt;td>) |
| Oracle Java SE 10 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java SE 9 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java SE 8 JDK – 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+8*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=10) |
| IBM J9 VM - Build 2.9, JRE 1.8.0 | A: Unterstützt `[2]` |
| IBM J9 VM - Build 2.8, JRE 1.8.0 | A: Unterstützt `[2]` |
| Azul Zulu OpenJDK 11 - 64 Bit | A: Unterstützt `[3]` |  |
| Azul Zulu OpenJDK 8 - 64 Bit | A: Unterstützt `[3]` |  |

1. Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java SE-Produkte umgestiegen. Java 9, Java 10 und Java 12 sind Nicht-LTS-Versionen von Oracle (siehe [Oracle Java SE-Support-Roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Um AEM in Produktionsumgebungen bereitzustellen, unterstützt Adobe ausschließlich LTS-Versionen von Java. Der Support und die Bereitstellung von Oracle Java SE, einschließlich aller Wartungsupdates von LTS-Versionen, werden von Adobe direkt für alle AEM-Kunden unterstützt, die die Oracle Java SE-Technologie nutzen. Siehe [Java-Unterstützungsrichtlinie für Adobe Experience Manager](assets/Java_Policy_for_Adobe_Experience_Manager.pdf) für weitere Informationen.


1. Die IBM JRE wird nur zusammen mit WebSphere Application Server unterstützt.

1. Azul Zulu OpenJDK LTS-Versionen werden für lokale AEM-Bereitstellungen ab Version 6.5 SP9 unterstützt. Der Support und die Verteilung der Azul Zulu JDK LTS Versionen müssen von unseren Kunden direkt von Azul lizenziert werden.


### Speicher und Persistenz {#storage-persistence}

Es gibt verschiedene Optionen, um das Repository von Adobe Experience Manager bereitzustellen. Die folgende Liste enthält die unterstützten Technologien und Speicheroptionen.

| **Plattform** | **Beschreibung** | **Unterstützungsebene** |
|---|---|---|
| **Dateisystem mit TAR-Dateien** `[1]` | Repository | A: Unterstützt  |
| **Dateisystem mit Datenspeicher** `[1]` | Binärdateien | A: Unterstützt |
| Speichern von Binärdateien in TAR-Dateien im Dateisystem `[1]` | Binärdateien | Z: Nicht für die Produktion unterstützt |
| Amazon S3 | Binärdateien | A: Unterstützt |
| Microsoft Azure Blob Storage | Binärdateien | A: Unterstützt |
| MongoDB Enterprise 4.2 | Repository | A: Unterstützt `[2, 3, 4]` |
| MongoDB Enterprise 4.0 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.6 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.4 | Repository | Z: Nicht unterstützt |
| IBM DB2 10.5 | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung  `[5]` |
| Oracle Database 12c (12.1.x) | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung  |
| Microsoft SQL Server 2016 | Forms-Datenbank | A: Unterstützt |
| **Apache Lucene (Schnellstart integriert)**  | Suchservice | A: Unterstützt |
| Apache Solr | Suchservice | A: Unterstützt |

1. „Dateisystem“ umfasst POSIX-konformen Blockspeicher. Dies umfasst eine Netzwerkspeichertechnologie. Beachten Sie, dass die Dateisystemleistung möglicherweise variieren kann und sich auf die Gesamtleistung auswirkt. Es wird empfohlen, einen Lasttest für AEM in Verbindung mit dem Netzwerk/Remote-Dateisystem durchzuführen.
1. MongoDB Enterprise 4.2 erfordert mindestens AEM 6.5 SP9.
1. MongoDB Sharding wird in AEM nicht unterstützt.
1. Es wird nur MongoDB Storage Engine WiredTiger unterstützt.
1. Unterstützt für AEM Forms-Upgrade-Kunden. Wird für neue Installationen nicht unterstützt.

>[!NOTE]
>
>Weitere Informationen zur Funktion von AEM Communities finden Sie unter [Bereitstellen von Communities](/help/communities/deploy-communities.md).

>[!NOTE]
>
>MongoDB ist eine Drittanbietersoftware und nicht Bestandteil des AEM-Lizenzierungspakets. Weitere Informationen finden Sie auf der Seite für die [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
>
>Adobe empfiehlt die Lizenzierung der MongoDB Enterprise-Version, damit Sie von professioneller Unterstützung profitieren und die AEM-Bereitstellung mit MongoDB optimal nutzen können. Siehe [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) für weitere Informationen.
>
>Die Lizenz umfasst eine Standard-Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
>
>Falls Sie die Autoren- und Veröffentlichungsbereitstellung von MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
>
>Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen.
>
>Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Unterstützte relationale Datenbanken wie die oben aufgeführten sind eine Drittanbietersoftware und nicht Bestandteil des AEM-Lizenzierungspakets.
>
>Um AEM 6.5 mit einer unterstützten relationalen Datenbank auszuführen, benötigen Sie einen gesonderten Supportvertrag mit dem Datenbankanbieter. Die Adobe-Kundenunterstützung unterstützt Sie beim Qualifizieren von Problemen, die mit der Verwendung von relationalen Datenbanken mit AEM 6.5 in Zusammenhang stehen.
>
>**Die meisten relationalen Datenbanken werden derzeit mit Level-R in AEM 6.5 unterstützt, d. h. im Rahmen von Supportkriterien und einem Supportprogramm, wie oben in der Beschreibung zu Level-R angegeben.**

### Servlet-Engines/Anwendungsserver {#servlet-engines-application-servers}

Adobe Experience Manager kann als eigenständiger Server (die quickstart-JAR-Datei) oder als Web-Applikation auf einem Drittanbieter-Anwendungsserver (die WAR-Datei) ausgeführt werden.

Als Servlet-API-Version ist mindestens Servlet 3.1 erforderlich.

| Plattform | Unterstützungsebene |
|---|---|
| **In „Quickstart“ integrierte Servlet-Engine (Jetty 9.4)** | A: Unterstützt |
| Oracle WebLogic Server 12.2 (12cR2) | Z: Nicht unterstützt |
| Continuous Delivery für IBM WebSphere Application Server (LibertyProfile) mit Web Profile 7.0 und IBM JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| IBM WebSphere Application Server 9.0 und IBM JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| Apache Tomcat 8.5.x | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| JBoss EAP 7.2.x mit JBoss Application Server | Z: Nicht unterstützt |
| JBoss EAP 7.1.4 mit JBoss Application Server | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| JBoss EAP 7.0.x mit JBoss Application Server | Z: Nicht unterstützt |

1. Für Bereitstellungen mit AEM Forms empfohlen.
1. Der Start von AEM 6.5-Bereitstellungen auf Anwendungsservern wird nun eingeschränkt unterstützt. Bestehende Kunden können auf AEM 6.5 aktualisieren und weiterhin Anwendungsserver verwenden. Für neue Kunden gelten Supportkriterien und ein Supportprogramm, wie oben in der Beschreibung zu Level-R angegeben.

### Serverbetriebssysteme {#server-operating-systems}

Adobe Experience Manager funktioniert mit den folgenden Serverplattformen in Produktionsumgebungen:

| **Plattform** | **Unterstützungsebene** |
|---|---|
| **Linux, auf Basis der Red Hat-Distribution** | A: Unterstützt `[1]` `[3]` |
| Linux, auf Basis der Debian-Distribution einschl. Ubuntu | A: Unterstützt `[2]` |
| Linux, auf Basis der SUSE-Distribution | A: Unterstützt |
| Microsoft Windows Server 2019 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge |
| Microsoft Windows Server 2016 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft Windows Server 2012 R2 | Z: Nicht unterstützt |
| Oracle Solaris 11 | Z: Nicht unterstützt |
| IBM AIX 7.2 | Z: Nicht unterstützt |

1. Der Linux-Kernel 2.6, 3.x und 4.x enthält Derivate von Red Hat-Distribution, einschließlich Red Hat Enterprise Linux, CentOS, Oracle Linux und Amazon Linux. AEM Forms-Add-On-Funktionen werden nur unter CentOS 7, Red Hat Enterprise Linux 7 und Red Hat Enterprise Linux 8 unterstützt.
1. AEM Forms wird nur auf Ubuntu 16.04 LTS unterstützt.
1. Linux-Distribution wird von Adobe Managed Services unterstützt.
1. Microsoft Windows-Produktionsimplementierungen werden für Kunden unterstützt, die auf 6.5 aktualisieren, und für Nicht-Produktionsumgebungen. Neue Bereitstellungen erfolgen auf Anforderung für AEM Sites und Assets.
1. AEM Forms wird auf Microsoft Windows Server ohne Support-Level-R-Einschränkungen unterstützt..


### Virtuelle und Cloud-Computing-Umgebungen {#virtual-cloud-computing-environments}

Die Ausführung von Adobe Experience Manager in einer virtuellen Maschine in Cloud-Computing-Umgebungen wie Microsoft Azure und Amazon Web Services (AWS) wird im Einklang mit den auf dieser Seite genannten technischen Anforderungen und den Standard-Supportbedingungen von Adobe unterstützt.

Adobe empfiehlt, Adobe Managed Services hinzuzuziehen, um AEM auf Azure oder AWS bereitzustellen. Adobe Managed Services liefert die Erfahrung und Kenntnisse, die Experten zur Bereitstellung und Ausführung von AEM in diesen Cloud-Computing-Umgebungen benötigen. Siehe [Zusätzliche Dokumentation zu Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

In allen anderen Fällen, in denen AEM auf Azure, AWS oder in einer anderen Cloud-Computing-Umgebung bereitgestellt wird, beschränkt sich die Unterstützung von Adobe auf die virtuelle Computing-Umgebung im Einklang mit den auf dieser Seite genannten technischen Anforderungen. Für die Ausführung von AEM in einer dieser Cloud-Umgebungen gemeldete Probleme müssen unabhängig von einem für diese Cloud-Computing-Umgebung spezifischen Cloud-Service reproduzierbar sein, es sei denn, der Cloud-Service wird explizit als Teil der auf dieser Seite genannten technischen Anforderungen unterstützt, beispielsweise Azure Blob Storage oder AWS S3.

Für die Bereitstellung von AEM auf Azure oder AWS ohne Adobe Managed Services wird von Adobe dringend empfohlen, direkt mit dem Cloud-Anbieter oder einem Adobe-Partner, der die Bereitstellung von AEM in der gewünschten Cloud-Umgebung unterstützt, zusammenzuarbeiten. Der ausgewählte Cloud-Anbieter oder Partner ist für die Größenspezifikation, das Design und die Implementierung der von ihm unterstützten Architektur verantwortlich, um Ihre spezifischen Anforderungen an Leistung, Last, Skalierbarkeit und Sicherheit zu erfüllen.

### Dispatcher-Plattformen (Webserver) {#dispatcher-platforms-web-servers}

Beim Dispatcher handelt es sich um eine Zwischenspeicherungs- und Lastenausgleichskomponente. [Laden Sie die neueste Dispatcher-Version herunter](https://helpx.adobe.com/de/experience-manager/dispatcher/release-notes.html). Für Experience Manager 6.5 ist die Dispatcher-Version 4.3.2 oder höher erforderlich.

Die folgenden Webserver werden für die Verwendung mit der Dispatcher-Version 4.3.2 unterstützt:

| Plattform | Unterstützungsebene |
|---|---|
| **Apache httpd 2.4.x** `[1,2]` | A: Unterstützt |
| Microsoft IIS 10 (Internet Information Server) | A: Unterstützt |
| Microsoft IIS 8.5 (Internet Information Server) | Z: Nicht unterstützt |

1. Auf Grundlage des Apache-httpd-Quellcodes erstellte Webserver verfügen über dieselbe Unterstützungsebene wie die Version von httpd, auf der sie basiert. Wenden Sie sich bei Zweifeln hinsichtlich der Unterstützungsebene des jeweiligen Serverprodukts zur Bestätigung an Adobe. Folgende Fälle:

   1. Der HTTP-Server wurde nur mithilfe von offiziellen Apache-Quellverteilungen erstellt oder
   1. der HTTP-Server wurde als Bestandteil des Betriebssystems geliefert, auf dem er ausgeführt wird. Beispiele: IBM HTTP Server, Oracle HTTP Server

1. Dispatcher steht für Apache 2.4x für Windows-Betriebssysteme nicht zur Verfügung.

## Unterstützte Clientplattformen {#supported-client-platforms}

### Unterstützte Browser für die Autoren-Benutzeroberfläche {#supported-browsers-for-authoring-user-interface}

Die Adobe Experience Manager-Benutzeroberfläche funktioniert mit den folgenden Clientplattformen. Alle Browser wurden mit dem Standardsatz von Plug-ins und Add-ons getestet.

Die AEM-Benutzeroberfläche ist für die Verwendung auf größeren Bildschirmen (für gewöhnlich Notebooks und Desktopcomputer) und dem Tablet-Formfaktor (wie Apple, iPad oder Microsoft Surface) optimiert. Der Telefon-Formfaktor wird nicht unterstützt.

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Veröffentlichungszyklen:**
>
>Mozilla Firefox, Google Chrome und Microsoft Edge veröffentlichen alle paar Monate Aktualisierungen. Adobe ist bestrebt, Aktualisierungen für Adobe Experience Manager bereitzustellen, um die Unterstützungsebene wie unten aufgeführt für die künftigen Versionen dieser Browser aufrechtzuerhalten.

<table>
 <tbody>
  <tr>
   <td><strong>Browser</strong></td>
   <td><strong>Unterstützung für Benutzeroberfläche<br /> </strong></td>
   <td><strong>Unterstützung für klassische Benutzeroberfläche</strong></td>
  </tr>
  <tr>
   <td><strong>Google Chrome (Evergreen)</strong></td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Microsoft Edge (Evergreen)</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Microsoft Internet Explorer 11</td>
   <td>Z: Nicht unterstützt</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Mozilla Firefox (Evergreen)</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Mozilla Firefox letztes ESR [1]</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Apple Safari auf macOS (Evergreen)</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Apple Safari 11.x auf macOS</td>
   <td>Z: Nicht unterstützt</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Apple Safari auf iOS 12.x</td>
   <td>A: Unterstützt (2)</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Apple Safari auf iOS 11.x</td>
   <td>Z: Nicht unterstützt</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
 </tbody>
</table>

1. Erweiterte Supportversion von Firefox: [Weitere Informationen darüber finden Sie auf mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. Unterstützung für Apple iPad 

### Unterstützte Browser für Websites {#supported-browsers-for-websites}

Im Allgemeinen hängt die Browserunterstützung für mit AEM Sites gerenderte Websites von der Implementierung der AEM-Seitenvorlagen, dem Design und der Komponentenausgabe ab und wird daher von der Partei kontrolliert, die diese Teile implementiert.

### WebDAV-Clients {#webdav-clients}

**Microsoft Windows 7+**

Um Microsoft Windows 7+ erfolgreich mit einer nicht über SSL gesicherten AEM-Instanz zu verbinden, muss die Standardauthentifizierung über das nicht gesicherte Netzwerk in Windows aktiviert sein. Dafür muss in der Windows-Registrierung des WebClients eine Änderung vorgenommen werden:

1. Suchen Sie nach dem Registry-Unterschlüssel:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Fügen Sie diesem Unterschlüssel den Registry-Eintrag „BasicAuthLevel“ mit einem Wert von 2 oder höher hinzu.

Informationen zur Verbesserung der Reaktionsfähigkeit des WebDav-Clients unter Windows finden Sie unter [Microsoft-Support KB 2445570](https://support.microsoft.com/kb/2445570)

## Zusätzliche Hinweise zu Plattformen {#additional-platform-notes}

Dieser Abschnitt enthält besondere Hinweise und weitere detaillierte Informationen über das Ausführen von Adobe Experience Manager und der zugehörigen Add-ons.

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von Adobe Experience Manager (Instanz, Dispatcher) können in IPv4- und IPv6-Netzwerken installiert werden.

Der Betrieb verläuft nahtlos, da keine gesonderte Konfiguration erforderlich ist. Sie können gegebenenfalls einfach eine IP-Adresse in dem Format angeben, das für Ihren Netzwerktyp geeignet ist.

Wenn eine IP-Adresse angegeben werden muss, können Sie (je nach Bedarf) aus den folgenden Optionen auswählen:

* eine IPv6-Adresse, z. B. `https://[ab12::34c5:6d7:8e90:1234]:4502`

* eine IPv4-Adresse, z. B. `https://123.1.1.4:4502`

* beispielsweise einen Servernamen, `https://www.yourserver.com:4502`

* Der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert, zum Beispiel `https://localhost:4502`.

### Anforderungen für das Add-on AEM Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media ist standardmäßig deaktiviert. Siehe hier zu [Dynamic Media aktivieren](/help/assets/config-dynamic.md#enabling-dynamic-media).

Wenn Dynamic Media aktiviert ist, gelten die folgenden zusätzlichen technischen Anforderungen. 

>[!NOTE]
>
>Diese **Systemanforderungen** gelten, wenn Sie den Modus „Dynamic Media –Hybrid“ verwenden. Der Modus „Dynamic Media –Hybrid“ verfügt über einen eingebetteten Bildserver, der nur für bestimmte Betriebssysteme zertifiziert ist.
>
>Für Dynamic Media-Kunden, die den Modus „Dynamic Media - Scene7“ ausführen (d. h. Ausführungsmodus **dynamicmedia_scene7**) gelten keine weiteren Systemanforderungen. Es gelten dieselben Systemanforderungen wie für AEM. Die Architektur des Dynamic Media Scene 7-Modus verwendet den Cloud-basierten Bilddienst und nicht den in AEM eingebetteten Dienst.

#### Hardware {#hardware}

Die folgenden Hardwareanforderungen gelten für Linux und Windows:

* Intel Xeon- oder AMD Opteron-CPU mit mindestens 4 Kernen
* Mindestens 16 GB RAM

#### Linux {#linux}

Wenn Sie „Dynamische Medien“ auf Linux verwenden, müssen die folgenden Voraussetzungen erfüllt sein:

* Red Hat Enterprise 7 oder CentOS 7 und höher mit den neuesten Fix-Patches
* 64-Bit-Betriebssystem
* Austausch deaktiviert (empfohlen)
* SELinux deaktiviert (siehe hierzu den folgenden Hinweis)

>[!NOTE]
>
>Falls das Gebietsschema so festgelegt ist, dass LC_CTYPE nicht `en_US.UTF-8` entspricht, funktioniert Dynamic Media nicht. Um den Wert zu überprüfen, geben Sie „locale“ in das Befehlszeilenfenster ein. Falls der Wert nicht dem genannten Wert entspricht, legen Sie für die LC_CTYPE-Umgebungsvariable eine leere Zeichenfolge fest, indem Sie „export LC_CTYPE=“ eingeben, bevor Sie AEM ausführen.

>[!NOTE]
>
>**Deaktivieren von SELinux:** Image-Serving funktioniert nicht, wenn SELinux aktiviert ist. Diese Option ist standardmäßig aktiviert. Bearbeiten Sie zum Beheben dieses Problems die Datei **/etc/selinux/config** und ändern Sie den SELinux-Wert von:
>
>`SELINUX=enforcing` **nach** `SELINUX=disabled`

>[!NOTE]
>
>**NUMA-Architektur:** Systeme mit Prozessen mit AMD64 und Intel EM64T sind für gewöhnlich als NUMA-Plattformen (Non-Uniform Memory Architecture) konfiguriert. Die Kernel-Konstrukte multiplizieren die Arbeitsspeicherknoten demnach zur Startzeit, anstatt dass ein einzelner Arbeitsspeicherknoten erstellt wird.
>
>Das Konstrukt mit mehreren Knoten kann dazu führen, dass der Arbeitsspeicher bei mindestens einem Knoten ausgeschöpft ist, bevor dies bei anderen Knoten der Fall ist. Bei einer Arbeitsspeicherausschöpfung kann der Kernel Prozesse beenden (beispielsweise den Image-Server oder Plattformserver), auch wenn Arbeitsspeicher verfügbar ist.
>
>Daher empfiehlt Adobe, dass Sie, sofern Sie ein derartiges System ausführen, NUMA mithilfe der Startoption **numa=off** deaktivieren, um zu verhindern, dass der Kernel diese Prozesse beendet.

>[!NOTE]
>
>**Hostname des Servers muss aufgelöst werden:** Stellen Sie sicher, dass der Hostname des Servers über eine IP-Adresse aufgelöst werden kann. Wenn dies nicht möglich ist, fügen Sie den vollständig qualifizierten Hostnamen und die IP-Adresse zu **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Tauschen Sie Speicherplatz aus, der mindestens dem Zweifachen der Menge des physischen Arbeitsspeichers (RAM) entspricht.

Um Dynamic Media unter Windows zu verwenden, müssen Sie verteilbare Microsoft Visual Studio 2010-, 2013- und 2015-Dateien für x64 und x86 installieren.

Windows x64:

* Microsoft Visual Studio 2010-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/de-de/download/details.aspx?id=13523)
* Microsoft Visual Studio 2013-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/de-de/download/details.aspx?id=40784)
* Microsoft Visual Studio 2015-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

Windows x86:

* Microsoft Visual Studio 2010-Redistributable unter [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Microsoft Visual Studio 2013-Redistributable unter [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft Visual Studio 2015-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/de-de/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x und höher
* Wird nur für Testversions- und Demozwecke unterstützt

### Anforderungen für AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt</strong></p> </th>
   <th><p><strong>Unterstützte Formate für die Konvertierung ins PDF-Format </strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 Classic Track</a> neueste Version</td>
   <td>XPS, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF und DWF</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2016</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td>
  </tr>
  <tr>
   <td>WordPerfect X7</td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Office Visio 2016<br /> </td>
   <td>VSD, VSDX</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2016<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Project 2016<br /> </td>
   <td>MPP</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.2</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* Für PDF Generator ist eine 32-Bit-Version von erforderlich. [Acrobat 2017 Klassische Track-Version 17.011.30078 oder höher](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) , um die Konvertierung durchzuführen.
>* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft Office Professional Plus und andere für die Konvertierung erforderliche Software.
>* PDF Generator unterstützt nicht Microsoft Office 365.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt.
>* Die Funktionen von OCR PDF, Optimize PDF und Export PDF werden nur unter Windows unterstützt.
>* Eine Version von Acrobat wird im Paket mit AEM Forms bereitgestellt, um die PDF Generator-Funktionen zu aktivieren. Auf diese Version sollte während der während der Geltungsdauer der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur vom Programm aus mit AEM Forms zugegriffen werden. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung entsprechend Ihrer Implementierung ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>
>* Der PDF Generator-Dienst unterstützt nicht Microsoft Windows 10.
>


### Anforderungen für AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server oder Microsoft® Windows® 10
* Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher – 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Grafik-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
* Administratorrechte für die Installation von Designer.

### Anforderungen für das Zurückschreiben von XMP-Metadaten der AEM-Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

Die XMP-Zurückschreibung wird für die folgenden Plattformen und Dateiformate unterstützt und aktiviert:

* **Betriebssysteme:**

   * Linux (32-Bit und 32-Bit-Anwendungsunterstützung auf 64-Bit-Systemen). Anweisungen zum Installieren von 32-Bit-Client-Bibliotheken finden Sie unter [So aktivieren Sie XMP Extraktion und Zurückschreiben auf 64-Bit RedHat Linux](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

   * Windows Server
   * Mac OS X (64 Bit)

* **Dateiformate**: JPEG, PNG, TIFF, PDF, INDD, AI und EPS.

### Anforderungen an AEM Assets zur Verarbeitung von Metadaten-lastigen Assets unter Linux {#assetsonlinux}

Für den XMPFilesProcessor-Prozess ist die Bibliothek GLIBC_2.14 erforderlich. Verwenden Sie einen Linux-Kernel, der GLIBC_2.14 enthält, zum Beispiel Linux-Kernel Version 3.1.x. Sie verbessert die Leistung bei der Verarbeitung von Assets, die eine große Menge an Metadaten enthalten, z. B. PSD-Dateien. Die Verwendung einer früheren Version von GLIBC führt zu Fehlern in Protokollen, die mit `com.day.cq.dam.core.impl.handler.xmp.NCommXMPHandler Failed to read XMP`.
