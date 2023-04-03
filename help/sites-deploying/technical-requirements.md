---
title: Technische Anforderungen
seo-title: Technical Requirements
description: Eine Liste der unterstützten Client- und Serverplattformen für AEM.
seo-description: A list of the supported client and server platforms for AEM.
content-type: reference
topic-tags: platform
exl-id: 47529b9a-c4e5-434f-ac26-b01714ff863b
source-git-commit: 64a15e970bc72114c14ed60e4bec3e694584eb16
workflow-type: tm+mt
source-wordcount: '3546'
ht-degree: 55%

---

# Technische Anforderungen {#technical-requirements}

Adobe unterstützt Adobe Experience Manager (AEM) auf den Plattformen, wie in den folgenden Informationen in diesem Dokument beschrieben.

Wenden Sie sich bei Problemen, die speziell mit der Plattform in Verbindung stehen, an den Plattformanbieter.

>[!NOTE]
>
>Je nach Plattform, auf der Sie AEM installieren, kann es verschiedene Anforderungen für die Benutzerverwaltung geben.

## Voraussetzungen {#prerequisites}

Mindestanforderungen für die Installation von Adobe Experience Manager:

* Installierte Java-Plattform, Standard Edition JDK oder andere unterstützte [Java Virtual Machines](#java-virtual-machines)
* Experience Manager Quickstart-Datei (eigenständige JAR-Datei oder Web-Anwendungsbereitstellungs-WAR-Datei)

### Mindestgrößenanforderungen {#minimum-sizing-requirements}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* 5 GB freier Speicherplatz im Installationsverzeichnis
* 2 GB Arbeitsspeicher

>[!NOTE]
>
>* Anwendungsfälle für digitale Assets benötigen mehr Basisspeicher. Siehe [Bereitstellung und Wartung](/help/sites-deploying/deploy.md#default-local-install) für Details.
>* Das [AEM Forms Add-on-Paket](/help/forms/using/installing-configuring-aem-forms-osgi.md) benötigt 15 GB temporären Speicherplatz. 
>


Weitere Informationen finden Sie im [Richtlinien zur Hardware-Skalierung](/help/managing/hardware-sizing-guidelines.md).

### Unterstützungsebenen {#support-levels}

In diesem Dokument werden die unterstützten Client- und Serverplattformen für Adobe Experience Manager aufgeführt. Adobe bietet mehrere Unterstützungsebenen, sowohl für empfohlene Konfigurationen als auch für andere Konfigurationen.

### Unterstützte Konfigurationen {#supported-configurations}

Adobe empfiehlt diese Konfigurationen und unterstützt sie im Rahmen des Standard-Software-Wartungsvertrags.

<table>
 <tbody>
  <tr>
   <td>Unterstützungsebene</td>
   <td>Beschreibung<br /> </td>
  </tr>
  <tr>
   <td><strong>A: Unterstützt</strong></td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird durch das Qualitätssicherungsverfahren der Adobe abgedeckt.</td>
  </tr>
  <tr>
   <td><strong>R: Eingeschränkte Unterstützung </strong></td>
   <td>Um den Projekterfolg unserer Kunden sicherzustellen, bietet Adobe im Rahmen eines eingeschränkten Support-Programms volle Unterstützung an, was erfordert, dass bestimmte Bedingungen erfüllt werden. Der Support auf R-Ebene erfordert eine formelle Kundenanfrage und eine Bestätigung durch die Adobe. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe.</td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| **Z: Nicht unterstützt** | Die Konfiguration wird nicht unterstützt. Adobe gibt keine Informationen dazu ab, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Plattformen {#supported-platforms}

### Java Virtual Machines {#java-virtual-machines}

Für die Anwendung ist eine Java Virtual Machine erforderlich, die von der Java Development Kit-Distribution (JDK) bereitgestellt wird.

Adobe Experience Manager funktioniert mit den folgenden Versionen von Java Virtual Machine:

>[!CAUTION]
>
>Es wird empfohlen, die Sicherheitsbulletins vom Java-Anbieter zu verfolgen, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java-Aktualisierungen zu installieren.

| **Plattform** | **Unterstützungsebene** | **Verknüpfung** |
|---|---|---|
| Oracle Java SE 11 JDK − 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+11*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=24&lt;td>) |
| Oracle Java SE 10 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java SE 9 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java SE 8 JDK – 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+8*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=10) |
| IBM J9 VM - Build 2.9, JRE 1.8.0 | A: Unterstützt `[2]` |
| IBM J9 VM - Build 2.8, JRE 1.8.0 | A: Unterstützt `[2]` |
| Azul Zulu OpenJDK 11 − 64 Bit | A: Unterstützt `[3]` |  |
| Azul Zulu OpenJDK 8 − 64 Bit | A: Unterstützt `[3]` |  |

1. Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java SE-Produkte umgestiegen. Java 9, Java 10 und Java 12 sind Nicht-LTS-Releases von Oracle (weitere Informationen finden Sie in der [Roadmap für Oracle Java SE-Support](https://www.oracle.com/technetwork/java/eol-135779.html)). Um AEM in Produktionsumgebungen bereitzustellen, unterstützt Adobe ausschließlich LTS-Versionen von Java. Der Support und die Bereitstellung von Oracle Java SE, einschließlich aller Wartungsupdates von LTS-Versionen, werden von Adobe direkt für alle AEM-Kunden unterstützt, die die Oracle Java SE-Technologie nutzen. Weitere Informationen finden Sie in der [Richtlinie zur Java-Unterstützung für Adobe Experience Manager](assets/Java_Policy_for_Adobe_Experience_Manager.pdf).
   **Wichtig: Java 11 wird mindestens bis September 2026 unterstützt.**

1. Die IBM JRE wird nur zusammen mit WebSphere Application Server unterstützt.

1. Azul Zulu OpenJDK LTS-Versionen werden für lokale AEM-Implementierungen ab Version 6.5 SP9 unterstützt. Der Support und die Verteilung der Azul Zulu JDK LTS-Versionen müssen von unseren Kunden direkt von Azul lizenziert werden.


### Speicherung und Persistenz {#storage-persistence}

Es gibt verschiedene Optionen zum Bereitstellen des Repositorys von Adobe Experience Manager. In der folgenden Liste finden Sie unterstützte Technologien und Speicheroptionen.

| **Plattform** | **Beschreibung** | **Unterstützungsebene** |
|---|---|---|
| **Dateisystem mit TAR-Dateien** `[1]` | Repository | A: Unterstützt |
| **Dateisystem mit Datastore** `[1]` | Binärdateien | A: Unterstützt |
| Speichern von Binärdateien in TAR-Dateien im Dateisystem `[1]` | Binärdateien | Z: Wird nicht für die Produktion unterstützt |
| Amazon S3 | Binärdateien | A: Unterstützt |
| Microsoft Azure Blob Storage | Binärdateien | A: Unterstützt |
| MongoDB Enterprise 4.4 | Repository | A: Unterstützt `[2, 3, 4]` |
| MongoDB Enterprise 4.2 | Repository | A: Unterstützt `[2, 3, 4]` |
| MongoDB Enterprise 4.0 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.6 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.4 | Repository | Z: Nicht unterstützt |
| IBM DB2 10.5 | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung `[5]` |
| Oracle Database 12c (12.1.x) | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung  |
| Microsoft SQL Server 2016 | Forms-Datenbank | A: Unterstützt |
| **Apache Lucene (Schnellstart integriert)** | Suchdienst | A: Unterstützt |
| Apache Solr | Suchdienst | A: Unterstützt |

1. &quot;Dateisystem&quot;umfasst einen POSIX-kompatiblen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren kann und die Gesamtleistung beeinflusst. Es wird empfohlen, AEM in Kombination mit dem Netzwerk-/Remote-Dateisystem zu laden.
1. Für MongoDB Enterprise-Versionen 4.2 und 4.4 ist mindestens AEM 6.5 SP9 erforderlich.
1. MongoDB Sharding wird in AEM nicht unterstützt.
1. MongoDB Storage Engine WiredTiger wird nur unterstützt.
1. Wird für AEM Forms-Upgrade-Kunden unterstützt. Wird für neue Installationen nicht unterstützt.

>[!NOTE]
>
>Weitere Informationen zur Funktion von AEM Communities finden Sie unter [Bereitstellen von Communities](/help/communities/deploy-communities.md).

>[!NOTE]
>
>MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie unter [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/) Seite.
>
>Um Ihre AEM Bereitstellung mit MongoDB optimal nutzen zu können, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten. Weitere Informationen finden Sie unter [Empfohlene Implementierungen](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk).
>
>Die Lizenz umfasst eine Standard-Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
>
>Wenn Sie die Autoren- und Veröffentlichungsinstanz in MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
>
>Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen.
>
>Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Unterstützte relationale Datenbanken wie oben aufgeführt sind Software von Drittanbietern und sind nicht im AEM-Lizenzierungspaket enthalten.
>
>Um AEM 6.5 mit einer unterstützten relationalen Datenbank ausführen zu können, ist ein separater Supportvertrag mit einem Datenbankanbieter erforderlich. Die Adobe-Kundenunterstützung unterstützt Sie bei der Qualifizierung von Problemen im Zusammenhang mit der Verwendung von relationalen Datenbanken mit AEM 6.5.
>
>**Die meisten relationalen Datenbanken werden derzeit in Level-R auf AEM 6.5 unterstützt, das mit Supportkriterien und einem Supportprogramm geliefert wird, wie in der obigen Beschreibung zu Level-R angegeben.**

### Servlet-Engines/Anwendungsserver {#servlet-engines-application-servers}

Adobe Experience Manager kann entweder als eigenständiger Server (die Schnellstart-JAR-Datei) oder als Webanwendung auf einem Drittanbieter-Anwendungsserver (die WAR-Datei) ausgeführt werden.

Mindestens erforderliche Servlet-API-Version ist Servlet 3.1

| Plattform | Unterstützungsebene |
|---|---|
| **Integrierte Schnellstart-Servlet-Engine (Jetty 9.4)** | A: Unterstützt |
| Oracle WebLogic Server 12.2 (12cR2) | Z: Nicht unterstützt |
| Continuous Delivery für IBM WebSphere Application Server (LibertyProfile) mit Web Profile 7.0 und IBM JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| IBM WebSphere Application Server 9.0 und IBM JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| Apache Tomcat 8.5.x | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| JBoss EAP 7.2.x mit JBoss Application Server | Z: Nicht unterstützt |
| JBoss EAP 7.1.4 mit JBoss Application Server | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| JBoss EAP 7.0.x mit JBoss Application Server | Z: Nicht unterstützt |

1. Wird für Bereitstellungen mit AEM Forms empfohlen.
1. Ab AEM 6.5-Bereitstellung auf Anwendungsservern wird der Support eingeschränkt. Bestehende Kunden können auf AEM 6.5 aktualisieren und weiterhin Anwendungsserver verwenden. Für neue Kunden werden Support-Kriterien und ein Support-Programm bereitgestellt, wie in der Beschreibung zu Level-R angegeben.

### Serverbetriebssysteme {#server-operating-systems}

Adobe Experience Manager arbeitet mit den folgenden Serverplattformen für Produktionsumgebungen:

| **Plattform** | **Unterstützungsebene** |
|---|---|
| **Linux, basierend auf der Red Hat-Distribution** | A: Unterstützt `[1]` `[3]` |
| Linux, auf Basis der Debian-Distribution einschl. Ubuntu | A: Unterstützt `[1]` `[2]` |
| Linux, auf Basis der SUSE-Distribution | A: Unterstützt `[1]` |
| Microsoft Windows Server 2019 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft Windows Server 2016 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft Windows Server 2012 R2 | Z: Nicht unterstützt |
| Oracle Solaris 11 | Z: Nicht unterstützt |
| IBM AIX 7.2 | Z: Nicht unterstützt |

1. Linux-Kernel 2.6, 3. x, 4. x und 5. x umfasst Derivate der Red Hat-Distribution, einschließlich Red Hat Enterprise Linux, CentOS, Oracle Linux und Amazon Linux. Die Add-On-Funktionen von AEM Forms werden nur unter CentOS 7, Red Hat Enterprise Linux 7, Red Hat Enterprise Linux 8 und Red Hat Enterprise Linux 9 unterstützt.
1. AEM Forms wird auf Ubuntu 20.04 LTS unterstützt.
1. Linux-Distribution wird von Adobe Managed Services unterstützt.
1. Microsoft Windows-Produktionsimplementierungen werden für Kunden unterstützt, die ein Upgrade auf 6.5 durchführen, sowie für produktionsfremden Einsatz. Neue Bereitstellungen werden auf Anfrage für AEM Sites und Assets bereitgestellt.
1. AEM Forms wird auf Microsoft Window Server ohne die Einschränkungen der Unterstützungsebene R unterstützt.

>[!NOTE]
>
>Wenn Sie AEM Forms 6.5 installieren, stellen Sie bitte sicher, dass Sie die folgenden verteilbaren 32-Bit-Dateien von Microsoft Visual C++ installiert haben.
>
>* Microsoft Visual C++ 2008 Redistributable
>* Microsoft Visual C++ 2010 Redistributable
>* Microsoft Visual C++ 2012 Redistributable
>* Microsoft Visual C++ 2013 Redistributable (für 6.5)



### Virtuelle und Cloud-Computing-Umgebungen {#virtual-cloud-computing-environments}

Adobe Experience Manager wird in einer virtuellen Maschine in Cloud-Computing-Umgebungen wie Microsoft Azure und Amazon Web Services (AWS) unterstützt, wenn die auf dieser Seite aufgeführten technischen Anforderungen erfüllt sind und die Standard-Support-Bedingungen von Adobe eingehalten werden.

Für eine Cloud-native Umgebung sollten Sie sich das neueste Angebot aus der AEM-Produktlinie ansehen: Adobe Experience Manager as a Cloud Service. Weitere Informationen finden Sie in der [Dokumentation zu Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

Adobe bietet auch Adobe Managed Services an, um AEM auf Azure oder AWS bereitzustellen. Adobe Managed Services liefert die Erfahrung und Kenntnisse, die Experten zur Bereitstellung und Ausführung von AEM in diesen Cloud-Computing-Umgebungen benötigen. Siehe [Zusätzliche Dokumentation zu Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

In allen anderen Fällen, in denen AEM auf Azure, AWS oder einer anderen Cloud-Computing-Umgebung bereitgestellt wird, wird die Unterstützung von Adobe in der virtuellen Compute-Umgebung gemäß den auf dieser Seite aufgelisteten technischen Spezifikationen enthalten sein. Jedes gemeldete Problem, das im Zusammenhang mit der AEM in einer dieser Cloud-Umgebungen auftritt, muss unabhängig von jedem Cloud-Service reproduzierbar sein, der für die Cloud-Computing-Umgebung spezifisch ist, es sei denn, der Cloud-Service wird speziell im Rahmen der auf dieser Seite aufgelisteten technischen Anforderungen unterstützt, z. B. Azure Blob Storage oder AWS S3.

Für Empfehlungen zur Bereitstellung von AEM auf Azure oder AWS außerhalb von Adobe Managed Services empfiehlt Adobe dringend, direkt mit dem Cloud-Anbieter oder Adobe-Partnern zusammenzuarbeiten, die die Bereitstellung von AEM in der von Ihnen ausgewählten Cloud-Umgebung unterstützen. Der ausgewählte Cloud-Anbieter oder -Partner ist für die Größenspezifikationen, das Design und die Implementierung der Architektur verantwortlich, um Ihre spezifischen Anforderungen an Leistung, Auslastung, Skalierbarkeit und Sicherheit zu erfüllen.

### Dispatcher-Plattformen (Webserver) {#dispatcher-platforms-web-servers}

Beim Dispatcher handelt es sich um eine Zwischenspeicherungs- und Lastenausgleichskomponente. [Laden Sie die neueste Dispatcher-Version herunter](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Für Experience Manager 6.5 ist die Dispatcher-Version 4.3.2 oder höher erforderlich.

Die folgenden Webserver werden für die Verwendung mit Dispatcher Version 4.3.2 unterstützt:

| Plattform | Unterstützungsebene |
|---|---|
| **Apache httpd 2.4.x** `[1,2]` | A: Unterstützt |
| Microsoft IIS 10 (Internet Information Server) | A: Unterstützt |
| Microsoft IIS 8.5 (Internet Information Server) | Z: Nicht unterstützt |

1. Auf Grundlage des Apache-httpd-Quell-Codes erstellte Webserver verfügen über dieselbe Unterstützungsebene wie die Version von httpd, auf der sie basiert. Wenden Sie sich bei Zweifeln hinsichtlich der Unterstützungsebene des jeweiligen Serverprodukts zur Bestätigung an Adobe. Folgende Fälle:

   1. Der HTTP-Server wurde nur mit offiziellen Apache-Quellverteilungen erstellt, oder
   1. Der HTTP-Server wurde als Teil des Betriebssystems bereitgestellt, auf dem er ausgeführt wird. Beispiele: IBM HTTP Server, Oracle HTTP Server

1. Der Dispatcher ist nicht für Apache 2.4.x für Windows-Betriebssysteme verfügbar.

## Unterstützte Client-Plattformen {#supported-client-platforms}

### Unterstützte Browser für die Authoring-Benutzeroberfläche {#supported-browsers-for-authoring-user-interface}

Die Adobe Experience Manager-Benutzeroberfläche funktioniert mit den folgenden Client-Plattformen. Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

Die AEM Benutzeroberfläche ist für größere Bildschirme (normalerweise Notebooks und Desktop-Computer) und den Tablet-Formfaktor (z. B. Apple iPad oder Microsoft Surface) optimiert. Der Telefonformularfaktor wird nicht unterstützt.

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Versionszyklen:**
>
>Die Versionen von Mozilla Firefox, Google Chrome und Microsoft Edge werden alle paar Monate aktualisiert. Adobe hat sich verpflichtet, Aktualisierungen für Adobe Experience Manager bereitzustellen, um die unten beschriebene Unterstützungsebene mit den kommenden Versionen dieser Browser beizubehalten.

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
   <td>Microsoft Edge (Evergreen)</td>
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
   <td>Mozilla Firefox letzte ESR [1]</td>
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
   <td>A: Unterstützt [2]</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Apple Safari auf iOS 11.x</td>
   <td>Z: Nicht unterstützt</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
 </tbody>
</table>

1. Erweiterte Unterstützung für Firefox [Weitere Informationen dazu finden Sie auf mozilla.org](https://www.mozilla.org/de-DE/firefox/organizations/faq/)
1. Unterstützung für Apple iPad

### Unterstützte Browser für Websites {#supported-browsers-for-websites}

Im Allgemeinen hängt die Browserunterstützung für von AEM Sites gerenderte Websites von der Implementierung AEM Seitenvorlagen, Designs und Komponentenausgabe ab und ist daher für die Partei verantwortlich, die diese Teile implementiert.

### WebDAV-Clients {#webdav-clients}

**Microsoft Windows 7+**

Um eine erfolgreiche Verbindung mit Microsoft Windows 7+ zu einer AEM Instanz herzustellen, die nicht mit SSL gesichert ist, muss unter Windows die grundlegende Authentifizierung über ein ungesichertes Netzwerk aktiviert sein. Dies erfordert eine Änderung in der Windows-Registrierung des WebClient:

1. Suchen Sie den Registrierungsunterschlüssel:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Fügen Sie diesem Unterschlüssel den Registry-Eintrag BasicAuthLevel mit dem Wert 2 oder mehr hinzu.

Informationen über das Verbessern der Reaktionsfähigkeit des WebDav-Clients unter Windows finden Sie im [Microsoft Support KB 2445570](https://support.microsoft.com/kb/2445570).

## Zusätzliche Hinweise zu Platform {#additional-platform-notes}

Dieser Abschnitt enthält spezielle Hinweise und detailliertere Informationen zum Ausführen von Adobe Experience Manager und seinen Add-ons.

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von Adobe Experience Manager (Instanz, Dispatcher) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb ist nahtlos, da keine spezielle Konfiguration erforderlich ist. Sie können bei Bedarf einfach eine IP-Adresse in dem Ihrem Netzwerktyp entsprechenden Format angeben.

Wenn eine IP-Adresse angegeben werden muss, können Sie (je nach Bedarf) aus den folgenden Optionen auswählen:

* einer IPv6-Adresse,
zum Beispiel `https://[ab12::34c5:6d7:8e90:1234]:4502`

* einer IPv4-Adresse,
zum Beispiel `https://123.1.1.4:4502`

* einem Servernamen,
zum Beispiel `https://www.yourserver.com:4502`

* Der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert,
zum Beispiel `https://localhost:4502`.

### Voraussetzungen für AEM Dynamic Media Add-on {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media ist standardmäßig deaktiviert. Hier finden Sie Informationen zum [Aktivieren von Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Wenn Dynamic Media aktiviert ist, gelten die folgenden zusätzlichen technischen Anforderungen. 

>[!NOTE]
>
>Diese **Systemanforderungen** gelten, wenn Sie den Modus „Dynamic Media –Hybrid“ verwenden. Der Modus „Dynamic Media –Hybrid“ verfügt über einen eingebetteten Bildserver, der nur für bestimmte Betriebssysteme zertifiziert ist.
>
>Für Dynamic Media-Kunden, die den Modus „Dynamic Media - Scene7“ ausführen (d. h. Ausführungsmodus **dynamicmedia_scene7**) gelten keine weiteren Systemanforderungen. Es gelten dieselben Systemanforderungen wie für AEM. Die Architektur des Dynamic Media Scene7-Modus verwendet den Cloud-basierten Bilddienst und nicht den in AEM eingebetteten Dienst.

#### Hardware {#hardware}

Die folgenden Hardwareanforderungen gelten für Linux und Windows:

* Intel Xeon- oder AMD Opteron-CPU mit mindestens 4 Kernen
* Mindestens 16 GB RAM

#### Linux {#linux}

Wenn Sie Dynamic Media auf Linux verwenden, müssen die folgenden Voraussetzungen erfüllt sein:

* Red Hat Enterprise 7 oder CentOS 7 und höher mit aktuellen Fix-Patches
* 64-Bit-Betriebssystem
* Swapping disabled (empfohlen)
* SELinux deaktiviert (siehe Hinweis, der folgt)

>[!NOTE]
>
>Falls das Gebietsschema so festgelegt ist, dass LC_CTYPE nicht `en_US.UTF-8` entspricht, funktioniert Dynamic Media nicht. Geben Sie an der Eingabeaufforderung den Wert &quot;locale&quot;ein. Wenn dies nicht festgelegt ist, legen Sie die Umgebungsvariable LC_CTYPE auf die leere Zeichenfolge fest, indem Sie &quot;export LC_CTYPE=&quot;eingeben, bevor Sie AEM ausführen.

>[!NOTE]
>
>**Deaktivieren von SELinux:** Image Serving funktioniert nicht, wenn SELinux aktiviert ist. Diese Option ist standardmäßig aktiviert. Um dieses Problem zu beheben, bearbeiten Sie die **/etc/selinux/config** und ändern Sie den SELinux-Wert von:
>
>`SELINUX=enforcing` **nach** `SELINUX=disabled`

>[!NOTE]
>
>**NUMA-Architektur:** Systeme mit Prozessoren mit AMD64 und Intel EM64T sind normalerweise als NUMA-Plattformen (Non-Uniform Memory Architecture) konfiguriert, was bedeutet, dass der Kernel beim Starten mehrere Speicherknoten erstellt, anstatt einen einzelnen Speicherknoten zu erstellen.
>
>Das Konstrukt mit mehreren Knoten kann zu einer Speichererschöpfung auf einem oder mehreren Knoten führen, bevor andere Knoten erschöpft sind. Wenn die Speichererschöpfung eintritt, kann der Kernel Prozesse beenden (z. B. den Image-Server oder Platform-Server), obwohl verfügbarer Speicher vorhanden ist.
>
>Daher empfiehlt Adobe, dass Sie NUMA bei der Ausführung eines solchen Systems mit der **numa=off** Boot-Option, um zu vermeiden, dass der Kernel diese Prozesse beendet.

>[!NOTE]
>
>**Der Hostname des Servers muss aufgelöst werden:** Stellen Sie sicher, dass der Hostname des Servers in eine IP-Adresse aufgelöst werden kann. Wenn dies nicht möglich ist, fügen Sie zu **/etc/hosts** den vollqualifizierten Hostnamen und die IP-Adresse hinzu:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Swap-Speicherplatz, der mindestens der doppelten Menge des physischen Speichers (RAM) entspricht

Um Dynamic Media unter Windows zu verwenden, installieren Sie Microsoft Visual Studio 2010, 2013 und 2015-Redistributables für x64 und x86.

Für Windows x64:

* Abruf von Microsoft Visual Studio 2010 Redistributable unter [https://www.microsoft.com/de-de/download/details.aspx?id=13523](https://www.microsoft.com/de-de/download/details.aspx?id=13523)
* Abruf von Microsoft Visual Studio 2013 Redistributable unter [https://www.microsoft.com/de-de/download/details.aspx?id=40784](https://www.microsoft.com/de-de/download/details.aspx?id=40784)
* Abruf von Microsoft Visual Studio 2015 Redistributable unter [https://www.microsoft.com/de-de/download/details.aspx?id=48145](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

Windows x86:

* Abruf von Microsoft Visual Studio 2010 Redistributable unter [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Abruf von Microsoft Visual Studio 2013 Redistributable unter [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Abruf von Microsoft Visual Studio 2015 Redistributable unter [https://www.microsoft.com/de-de/download/details.aspx?id=52685](https://www.microsoft.com/de-de/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x und höher
* Nur für Test- und Demozwecke unterstützt

### Anforderungen für AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

### Software-Support für PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt</strong></p> </th>
   <th><p><strong>Unterstützte Formate für die Konvertierung ins PDF-Format </strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html">Klassischer Modus von Acrobat 2020</a> neueste Version</td>
   <td>XPS, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF und DWF</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html">Klassischer Modus von Acrobat 2017</a> neueste Version (nicht mehr unterstützt)</td>
   <td>XPS, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF und DWF</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2019</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2016 (nicht mehr unterstützt)</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td>
  </tr>
  <tr>
   <td>WordPerfect 2020<br /> </td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Office Visio 2016 (nicht mehr unterstützt)<br /> </td>
   <td>VSD, VSDX</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2019<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2016 (nicht mehr unterstützt)<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Project 2016 (nicht mehr unterstützt)<br /> </td>
   <td>MPP</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.10</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.2 (nicht mehr unterstützt)</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF und TXT</td>
  </tr>  
 </tbody>
</table>

>[!NOTE]
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* PDF Generator erfordert die 32-Bit-Version der [klassischen Acrobat 2020-Version 20.004.30006](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) oder der Acrobat 2017-Version 17.011.30078, um die Konvertierung durchzuführen.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt.
>* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft Office Professional Plus und andere für die Konvertierung unter einem Windows-Betriebssystem erforderliche Software.
>* PDF Generator unterstützt die 32-Bit- und 64-Bit-Versionen von OpenOffice unter Linux.
>* PDF Generator unterstützt nicht Microsoft Office 365.
>* Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
>* Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktion zu aktivieren. Der Zugriff auf die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz nur mit AEM Forms für die Verwendung mit AEM Forms PDF Generator programmgesteuert sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung für Ihre Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))
>* Der PDF Generator-Service unterstützt nicht Microsoft Windows 10.
>* PDF Generator kann Dateien mit Microsoft Visio 2019 nicht konvertieren. Sie können Microsoft Visio 2016 weiterhin verwenden, um .VSD- und .VSDX-Dateien zu konvertieren.
>* PDF Generator kann Dateien mit Microsoft Project 2019 nicht konvertieren. Sie können weiterhin Microsoft Project 2016 verwenden, um .VSD- und .VSDX-Dateien zu konvertieren.
>


### Anforderungen für AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server oder Microsoft® Windows® 10
* Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher – 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Video-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
* Administratorrechte für die Installation von Designer.

### Anforderungen für das Zurückschreiben von XMP-Metadaten der AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

XMP Writeback wird für die folgenden Plattformen und Dateiformate unterstützt und aktiviert:

* **Betriebssysteme:**

   * Linux (32-Bit- und 32-Bit-Anwendungsunterstützung auf 64-Bit-Systemen). Schrittweise Anleitungen zur Installation von 32-Bit-Clientbibliotheken finden Sie unter [Aktivieren von XMP-Extraktion und -Writeback unter RedHat Linux (64 Bit)](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

   * Windows Server
   * Mac OS X (64 Bit)

* **Dateiformate**: JPEG, PNG, TIFF, PDF, INDD, AI und EPS.

### Anforderungen für die Verarbeitung von Metadaten-lastigen Assets durch AEM Assets unter Linux {#assetsonlinux}

Für den XMPFilesProcessor-Prozess ist die Bibliothek GLIBC_2.14 erforderlich. Verwenden Sie einen Linux-Kernel, der GLIBC_2.14 enthält, zum Beispiel Linux-Kernel Version 3.1.x. Dies verbessert die Leistung bei der Verarbeitung von Assets, die eine große Menge an Metadaten enthalten, z. B. PSD-Dateien. Die Verwendung einer früheren Version von GLIBC führt zu Fehlern in Protokollen, die mit `com.day.cq.dam.core.impl.handler.xmp.NCommXMPHandler Failed to read XMP` beginnen.
