---
title: Technische Anforderungen
description: Eine Liste der unterstützten Client- und Serverplattformen für Adobe Experience Manager.
content-type: reference
topic-tags: platform
exl-id: 47529b9a-c4e5-434f-ac26-b01714ff863b
source-git-commit: 32af8ee1680bb0a357e64d614f22234ed331d314
workflow-type: tm+mt
source-wordcount: '3513'
ht-degree: 58%

---

# Technische Anforderungen {#technical-requirements}

Adobe unterstützt (AEM) Adobe Experience Manager auf den Plattformen, wie in den folgenden Informationen in diesem Dokument beschrieben.

Wenden Sie sich bei Problemen mit der Plattform an den Plattformanbieter.

>[!NOTE]
>
>Je nach Plattform, auf der Sie AEM installieren, kann es verschiedene Anforderungen für die Benutzerverwaltung geben.

## Voraussetzungen {#prerequisites}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* Installierte Java™-Plattform, Standard Edition JDK oder andere unterstützte [Java™ Virtual Machines](#java-virtual-machines)
* Experience Manager Quickstart-Datei (eigenständige JAR-Datei oder Web-Anwendungsbereitstellungs-WAR-Datei)

### Mindestgrößenanforderungen {#minimum-sizing-requirements}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* 5 GB freier Speicherplatz im Installationsverzeichnis
* 2 GB Arbeitsspeicher

>[!NOTE]
>
>* Anwendungsfälle für digitale Assets benötigen mehr Arbeitsspeicher. Siehe [Bereitstellung und Wartung](/help/sites-deploying/deploy.md#default-local-install) für mehr Details.
>* Das [AEM Forms Add-on-Paket](/help/forms/using/installing-configuring-aem-forms-osgi.md) benötigt 15 GB temporären Speicherplatz.
>


Weitere Informationen finden Sie in den [Hardware-Skalierungsrichtlinien](/help/managing/hardware-sizing-guidelines.md).

### Unterstützungsebenen {#support-levels}

In diesem Dokument werden die unterstützten Client- und Server-Plattformen für Adobe Experience Manager aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für empfohlene und andere Konfigurationen gelten.

### Unterstützte Konfigurationen {#supported-configurations}

Adobe empfiehlt diese Konfigurationen und bietet im Zuge der standardmäßigen Vereinbarung für die Software-Wartung vollständige Unterstützung.

<table>
 <tbody>
  <tr>
   <td>Unterstützungsebene</td>
   <td>Beschreibung<br /> </td>
  </tr>
  <tr>
   <td><strong>A: Unterstützt</strong></td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt.</td>
  </tr>
  <tr>
   <td><strong>R: Eingeschränkte Unterstützung </strong></td>
   <td>Um den Projekterfolg der Kunden sicherzustellen, bietet Adobe uneingeschränkten Support im Rahmen eines eingeschränkten Support-Programms an, für das bestimmte Bedingungen erfüllt sein müssen. Der Support auf R-Ebene erfordert eine formelle Kundenanfrage und eine Bestätigung durch Adobe. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe.</td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| **Z: Nicht unterstützt** | Die Konfiguration wird nicht unterstützt. Adobe gibt keine Informationen dazu ab, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Plattformen {#supported-platforms}

### Java™ Virtual Machines {#java-virtual-machines}

Für die Anwendung ist eine Java™ Virtual Machine erforderlich, die von der Java™ Development Kit-Distribution (JDK) bereitgestellt wird.

Adobe Experience Manager arbeitet mit den folgenden Versionen der Java™ Virtual Machines:

>[!CAUTION]
>
>Verfolgen Sie die Sicherheitsbulletins vom Java™-Anbieter. Auf diese Weise wird die Sicherheit der Produktionsumgebungen gewährleistet. Installieren Sie außerdem immer die neuesten Java™-Updates.

| **Plattform** | **Unterstützungsebene** | **Verknüpfung** |
|---|---|---|
| Oracle Java™ SE 17 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 11 JDK - 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+11*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=24&lt;td>) |
| Oracle Java™ SE 10 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 9 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 8 JDK - 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+8*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=10) |
| IBM® J9 VM - Build 2.9, JRE 1.8.0 | A: Unterstützt `[2]` |
| IBM® J9 VM - Build 2.8, JRE 1.8.0 | A: Unterstützt `[2]` |
| Azul Zulu OpenJDK 11 − 64 Bit | A: Unterstützt `[3]` |  |
| Azul Zulu OpenJDK 8 − 64 Bit | A: Unterstützt `[3]` |  |

1. Oracle wurde auf ein LTS-Modell (Long Term Support) für Oracle Java™ SE-Produkte umgestellt. Java™ 9, Java™ 10 und Java™ 12 sind nicht-LTS-Versionen von Oracle (siehe [Support-Roadmap für oracle Java™ SE](https://www.oracle.com/technetwork/java/eol-135779.html)). Um AEM in Produktionsumgebungen bereitzustellen, unterstützt Adobe ausschließlich LTS-Versionen von Java™. Der Support und die Verteilung des Oracle Java™ SE JDK, einschließlich aller Wartungsupdates der LTS-Versionen über das Ende der öffentlichen Updates hinaus, wird von Adobe direkt für alle AEM Kunden unterstützt, die die Oracle Java™ SE-Technologie verwenden. Siehe [Java™-Unterstützungsrichtlinie für Adobe Experience Manager](assets/Java_Policy_for_Adobe_Experience_Manager.pdf).
**Wichtig: Oracle Java™ 11 wird mindestens bis September 2026 unterstützt. Oracle Java™ 17 wird derzeit unterstützt. **

1. IBM® JRE wird nur zusammen mit WebSphere® Application Server unterstützt.

1. Azul Zulu OpenJDK LTS-Versionen werden für lokale AEM-Implementierungen ab Version 6.5 SP9 unterstützt. Der Support und die Distribution der Azul Zulu JDK LTS-Versionen müssen von Adobe-Kunden direkt von Azul lizenziert werden.


### Speicherung und Persistenz {#storage-persistence}

Es gibt verschiedene Optionen zum Bereitstellen des Repositorys von Adobe Experience Manager. In der folgenden Liste finden Sie unterstützte Technologien und Speicheroptionen.

| **Plattform** | **Beschreibung** | **Unterstützungsebene** |
|---|---|---|
| **Dateisystem mit TAR-Dateien** `[1]` | Repository | A: Unterstützt |
| **Dateisystem mit Datastore** `[1]` | Binärdateien | A: Unterstützt |
| Speichern von Binärdateien in TAR-Dateien im Dateisystem `[1]` | Binärdateien | Z: Wird nicht für die Produktion unterstützt |
| Amazon S3 | Binärdateien | A: Unterstützt |
| Microsoft® Azure Blob-Speicher | Binärdateien | A: Unterstützt |
| MongoDB Enterprise 4.4 | Repository | A: Unterstützt `[2, 3, 4]` |
| MongoDB Enterprise 4.2 | Repository | A: Unterstützt `[2, 3, 4]` |
| MongoDB Enterprise 4.0 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.6 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.4 | Repository | Z: Nicht unterstützt |
| IBM® DB2® 10.5 | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung `[5]` |
| Oracle Database 12c (12.1.x) | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung  |
| Microsoft® SQL Server 2016 | Forms-Datenbank | A: Unterstützt |
| **Apache Lucene (Schnellstart integriert)** | Suchdienst | A: Unterstützt |
| Apache Solr | Suchdienst | A: Unterstützt |

1. „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Enthält Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Laden Sie AEM mit dem Netzwerk-/Remote-Dateisystem.
1. Für MongoDB Enterprise-Versionen 4.2 und 4.4 ist mindestens AEM 6.5 SP9 erforderlich.
1. MongoDB Sharding wird in AEM nicht unterstützt.
1. Nur MongoDB Storage Engine WiredTiger wird unterstützt.
1. Wird für Kundinnen und Kunden von AEM Forms-Upgrades unterstützt. Wird für neue Installationen nicht unterstützt.

>[!NOTE]
Weitere Informationen zur Funktion von AEM Communities finden Sie unter [Bereitstellen von Communities](/help/communities/deploy-communities.md).

>[!NOTE]
MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie unter [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.com/community/licensing) Seite.
Um Ihre AEM-Implementierung mit MongoDB optimal nutzen zu können, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten. Weitere Informationen finden Sie unter [Empfohlene Implementierungen](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk).
Die Lizenz umfasst eine Standard-Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
Wenn Sie die Autoren- und Veröffentlichungsinstanz in MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
Die Kundenunterstützung von Adobe unterstützt Sie bei der Qualifizierung von Problemen im Zusammenhang mit der Verwendung von MongoDB mit AEM.
Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
Unterstützte relationale Datenbanken wie oben aufgeführt sind Software von Drittanbietern und sind nicht im AEM-Lizenzierungspaket enthalten.
Um AEM 6.5 mit einer unterstützten relationalen Datenbank ausführen zu können, ist ein separater Support-Vertrag mit einem Datenbankanbieter erforderlich. Die Adobe-Kundenunterstützung unterstützt Sie bei der Qualifizierung von Problemen im Zusammenhang mit der Verwendung von relationalen Datenbanken mit AEM 6.5.
**Die meisten relationalen Datenbanken werden derzeit in Level-R auf AEM 6.5 unterstützt, das mit Support-Kriterien und einem Support-Programm geliefert wird, wie in der obigen Beschreibung zu Level-R angegeben.**

### Servlet-Engines/Anwendungs-Server {#servlet-engines-application-servers}

Adobe Experience Manager kann entweder als eigenständiger Server (die Schnellstart-JAR-Datei) oder als Web-Anwendung auf einem Drittanbieter-Anwendungs-Server (die WAR-Datei) ausgeführt werden.

Die mindestens erforderliche Servlet-API-Version ist Servlet 3.1

| Plattform | Unterstützungsebene |
|---|---|
| **Integrierte Schnellstart-Servlet-Engine (Jetty 9.4)** | A: Unterstützt |
| Oracle WebLogic Server 12.2 (12cR2) | Z: Nicht unterstützt |
| IBM® WebSphere® Application Server Continuous Delivery (LibertyProfile) mit Webprofil 7.0 und IBM® JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| IBM® WebSphere® Application Server 9.0 und IBM® JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| Apache Tomcat 8.5.x | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| JBoss® EAP 7.2.x mit JBoss® Application Server | Z: Nicht unterstützt |
| JBoss® EAP 7.1.4 mit JBoss® Application Server | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| JBoss® EAP 7.0.x mit JBoss® Application Server | Z: Nicht unterstützt |

1. Wird für Bereitstellungen mit AEM Forms empfohlen.
1. Der Start von AEM 6.5-Bereitstellungen auf Anwendungs-Servern wird nun eingeschränkt unterstützt. Bestehende Kunden können auf AEM 6.5 aktualisieren und weiterhin Anwendungs-Server verwenden. Für neue Kunden werden Support-Kriterien und ein Support-Programm bereitgestellt, wie in der Beschreibung zu Level-R angegeben.

### Server-Betriebssysteme {#server-operating-systems}

Adobe Experience Manager arbeitet mit den folgenden Server-Plattformen für Produktionsumgebungen:

| **Plattform** | **Unterstützungsebene** |
|---|---|
| **Linux® basierend auf Red Hat® Distribution** | A: Unterstützt `[1]` `[3]` |
| Linux®, basierend auf der Debian-Distribution einschl. Ubuntu | A: Unterstützt `[1]` `[2]` |
| Linux® basierend auf der SUSE®-Distribution | A: Unterstützt `[1]` |
| Microsoft® Windows Server 2019 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft® Windows Server 2016 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft® Windows Server 2012 R2 | Z: Nicht unterstützt |
| Oracle Solaris™ 11 | Z: Nicht unterstützt |
| IBM® AIX® 7.2 | Z: Nicht unterstützt |

1. Linux® Kernel 2.6, 3. x, 4. x und 5. x enthält Derivate von Red Hat®-Distribution, einschließlich Red Hat® Enterprise Linux®, CentOS, Oracle Linux® und Amazon Linux®. AEM Forms-Add-On-Funktionen werden nur von CentOS 7, Red Hat® Enterprise Linux® 7, Red Hat® Enterprise Linux® 8 und Red Hat® Enterprise Linux® 9 unterstützt.
1. AEM Forms wird auf Ubuntu 20.04 LTS unterstützt.
1. Linux®-Distribution, die von Adobe Managed Services unterstützt wird.
1. Microsoft® Windows-Produktionsimplementierungen werden für Kunden unterstützt, die auf 6.5 aktualisieren, und für Nicht-Produktionsumgebungen. Neue Bereitstellungen erfolgen auf Anfrage für AEM Sites und Assets.
1. AEM Forms wird auf Microsoft® Windows Server ohne Einschränkungen der Unterstützungsebene R unterstützt.

>[!NOTE]
Wenn Sie AEM Forms 6.5 installieren, stellen Sie sicher, dass Sie die folgende 32-Bit-Version von Microsoft® Visual C++ installiert haben.
* Redistributable Microsoft® Visual C++ 2008
* Redistributable Microsoft® Visual C++ 2010
* Redistributable Microsoft® Visual C++ 2012
* Microsoft® Visual C++ 2013 Redistributable (ab 6.5)



### Virtuelle und Cloud-Computing-Umgebungen {#virtual-cloud-computing-environments}

Adobe Experience Manager wird in einer virtuellen Maschine in Cloud-Computing-Umgebungen unterstützt. Zu diesen Umgebungen gehören Microsoft® Azure und Amazon Web Services (AWS), die gemäß den auf dieser Seite aufgeführten technischen Anforderungen und den standardmäßigen Supportbedingungen von Adobe ausgeführt werden.

Für eine Cloud-native Umgebung sollten Sie sich das neueste Angebot aus der AEM-Produktlinie ansehen: Adobe Experience Manager as a Cloud Service. Weitere Informationen finden Sie in der [Dokumentation zu Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

Adobe bietet auch Adobe Managed Services an, um AEM auf Azure oder AWS bereitzustellen. Adobe Managed Services liefert die Erfahrung und Kenntnisse, die Experten zur Bereitstellung und Ausführung von AEM in diesen Cloud-Computing-Umgebungen benötigen. Siehe die [zusätzliche Dokumentation zu Adobe Managed Services](https://business.adobe.com/products/experience-manager/managed-services.html?aemClk=t).

In allen anderen Fällen der Bereitstellung von AEM auf Azure, AWS oder einer anderen Cloud-Computing-Umgebung ist die Unterstützung von Adobe in der virtuellen Compute-Umgebung enthalten. Diese virtuelle Umgebung muss in Übereinstimmung mit den auf dieser Seite aufgeführten technischen Spezifikationen ausgeführt werden. Jedes gemeldete Problem, das im Zusammenhang mit AEM in einer dieser Cloud-Umgebungen auftritt, muss unabhängig von einem Cloud-Service reproduzierbar sein, der speziell für die Cloud-Computing-Umgebung gilt. Das heißt, es sei denn, der Cloud-Service wird im Rahmen der auf dieser Seite aufgelisteten technischen Anforderungen unterstützt, z. B. Azure Blob Storage oder AWS S3.

Für Empfehlungen zur Bereitstellung von AEM auf Azure oder AWS außerhalb von Adobe Managed Services empfiehlt Adobe, direkt mit dem Cloud-Anbieter zu arbeiten. Oder Sie arbeiten mit Adobe-Partnern zusammen, die die Bereitstellung von AEM in der gewünschten Cloud-Umgebung unterstützen. Der ausgewählte Cloud-Anbieter oder -Partner ist für die Größenspezifikationen, das Design und die Implementierung der Architektur verantwortlich, um Ihre spezifischen Anforderungen an Leistung, Auslastung, Skalierbarkeit und Sicherheit zu erfüllen.

### Dispatcher-Plattformen (Web-Server) {#dispatcher-platforms-web-servers}

Der Dispatcher ist die Komponente zum Zwischenspeichern und Lastenausgleich. [Laden Sie die neueste Dispatcher-Version herunter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html?lang=en). Für Experience Manager 6.5 ist die Dispatcher-Version 4.3.2 oder höher erforderlich.

Die folgenden Web-Server werden für die Verwendung mit der Dispatcher-Version 4.3.2 unterstützt:

| Plattform | Unterstützungsebene |
|---|---|
| **Apache httpd 2.4.x** `[1,2]` | A: Unterstützt |
| Microsoft® IIS 10 (Internet Information Server) | A: Unterstützt |
| Microsoft® IIS 8.5 (Internet Information Server) | Z: Nicht unterstützt |

1. Auf Apache HTTPD-Quellcode basierende Webserver unterstützen genauso viel wie die HTTPD-Version, auf der sie basieren. Wenden Sie sich bei Zweifeln hinsichtlich der Unterstützungsebene des jeweiligen Serverprodukts zur Bestätigung an Adobe. Folgende Fälle:

   1. Der HTTP-Server wurde nur mit offiziellen Apache-Quellverteilungen erstellt, oder
   1. Der HTTP-Server wurde als Teil des Betriebssystems bereitgestellt, auf dem er ausgeführt wird. Beispiele: IBM® HTTP-Server, Oracle HTTP-Server

1. Der Dispatcher ist nicht für Apache 2.4.x für Windows-Betriebssysteme verfügbar.

## Unterstützte Client-Plattformen {#supported-client-platforms}

### Unterstützte Browser für die Authoring-Benutzeroberfläche {#supported-browsers-for-authoring-user-interface}

Die Adobe Experience Manager-Benutzeroberfläche funktioniert mit den folgenden Client-Plattformen. Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

Die AEM Benutzeroberfläche ist für größere Bildschirme (normalerweise Notebooks und Desktop-Computer) und den Tablet-Formfaktor (z. B. Apple iPad oder Microsoft® Surface) optimiert. Der Telefon-Formfaktor wird nicht unterstützt.

>[!NOTE]
**Unterstützung für Browser mit schnellen Versionszyklen:**
Die Versionen von Mozilla Firefox, Google Chrome und Microsoft® Edge werden alle paar Monate aktualisiert. Adobe setzt sich dafür ein, Aktualisierungen für Adobe Experience Manager bereitzustellen, um die unten beschriebene Unterstützungsebene mit den kommenden Versionen dieser Browser beizubehalten.

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
   <td>Microsoft® Edge (Evergreen)</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Microsoft® Internet Explorer 11</td>
   <td>Z: Nicht unterstützt</td>
   <td>Z: Nicht unterstützt</td>
  </tr>
  <tr>
   <td>Mozilla Firefox (Evergreen)</td>
   <td>A: Unterstützt</td>
   <td>A: Unterstützt</td>
  </tr>
  <tr>
   <td>Letztes ESR von Mozilla Firefox [1]</td>
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

1. Erweiterte Unterstützung für Firefox [Weitere Informationen zu mozilla.org](https://www.mozilla.org/en-US/firefox/enterprise/)
1. Unterstützung für Apple iPad

### Unterstützte Browser für Websites {#supported-browsers-for-websites}

Im Allgemeinen hängt die Browser-Unterstützung für von AEM Sites gerenderte Websites von der Implementierung von Seitenvorlagen, Designs und der Komponentenausgabe von AEM ab und unterliegt daher der Kontrolle der Seite, die diese Teile implementiert.

### WebDAV-Clients {#webdav-clients}

**Microsoft® Windows 7+**

Bei der Verbindung mit Microsoft® Windows 7+ mit einer AEM Instanz, die nicht mit SSL gesichert ist, muss die grundlegende Authentifizierung über ein ungesichertes Netzwerk in Windows aktiviert sein. Dies erfordert eine Änderung in der Windows-Registrierung des WebClient:

1. Suchen Sie den Registrierungsunterschlüssel:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Fügen Sie diesem Unterschlüssel den Registrierungseintrag „BasicAuthLevel“ mit dem Wert 2 oder mehr hinzu.

## Zusätzliche Hinweise zu Platform {#additional-platform-notes}

Dieser Abschnitt enthält spezielle Hinweise und detailliertere Informationen zum Ausführen von Adobe Experience Manager und seinen Add-ons.

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von Adobe Experience Manager (Instance, Dispatcher) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb ist nahtlos, da keine spezielle Konfiguration erforderlich ist. Sie geben bei Bedarf eine IP-Adresse in dem für Ihren Netzwerktyp geeigneten Format an.

Wenn eine IP-Adresse angegeben werden muss, können Sie (nach Bedarf) aus folgenden Optionen auswählen:

* Eine IPv6-Adresse. Beispiel: `https://[ab12::34c5:6d7:8e90:1234]:4502`

* Eine IPv4-Adresse. Beispiel: `https://123.1.1.4:4502`

* Ein Servername. Beispiel: `https://www.yourserver.com:4502`

* Der Standardfall von `localhost` wird sowohl für IPv4- als auch für IPv6-Netzwerkinstallationen interpretiert. Beispiel: `https://localhost:4502`

### Voraussetzungen für das AEM Dynamic Media-Add-on {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media ist standardmäßig deaktiviert. Hier finden Sie Informationen zum [Aktivieren von Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Wenn Dynamic Media aktiviert ist, gelten die folgenden zusätzlichen technischen Anforderungen.

>[!NOTE]
Diese **Systemanforderungen** gelten, wenn Sie den Modus „Dynamic Media –Hybrid“ verwenden. Der Modus „Dynamic Media –Hybrid“ verfügt über einen eingebetteten Bildserver, der nur für bestimmte Betriebssysteme zertifiziert ist.
Für Dynamic Media-Kunden, die den Dynamic Media - Scene7 -Modus ausführen (d. h. **dynamicmedia_scene7** Ausführungsmodus), gibt es keine zusätzlichen Systemanforderungen; gelten nur die gleichen Systemanforderungen wie AEM. Die Architektur des Dynamic Media Scene7-Modus verwendet den Cloud-basierten Bilddienst und nicht den in AEM eingebetteten Dienst.

#### Hardware {#hardware}

Die folgenden Hardwareanforderungen gelten für Linux® und Windows:

* Intel Xeon® oder AMD® Opteron-CPU mit mindestens vier Kernen
* Mindestens 16 GB RAM

#### Linux® {#linux}

Wenn Sie Dynamic Media unter Linux® verwenden, müssen die folgenden Voraussetzungen erfüllt sein:

* Red Hat® Enterprise 7 oder CentOS 7 und höher mit aktuellen Fix-Patches
* 64-Bit-Betriebssystem
* Swapping deaktiviert (empfohlen)
* SELinux deaktiviert (siehe folgenden Hinweis)

>[!NOTE]
Falls das Gebietsschema so festgelegt ist, dass LC_CTYPE nicht `en_US.UTF-8` entspricht, funktioniert Dynamic Media nicht. Geben Sie an der Eingabeaufforderung den Wert &quot;locale&quot;ein, um zu sehen, welcher Wert lautet. Wenn sie nicht richtig festgelegt ist, legen Sie die Umgebungsvariable LC_CTYPE auf die leere Zeichenfolge fest, indem Sie &quot;export LC_CTYPE=&quot;eingeben, bevor Sie AEM ausführen.

>[!NOTE]
**Deaktivieren von SELinux**: Die Bereitstellung von Bildern funktioniert nicht, wenn SELinux aktiviert ist. Diese Option ist standardmäßig aktiviert. Um dieses Problem zu beheben, bearbeiten Sie die Datei **/etc/selinux/config** und ändern Sie den SELinux-Wert von:
`SELINUX=enforcing` **nach** `SELINUX=disabled`

>[!NOTE]
**NUMA-Architektur:** Systeme mit Prozessoren mit AMD64 und Intel® EM64T sind normalerweise als NUMA-Plattformen (Non-Uniform Memory Architecture) konfiguriert. Das heißt, der Kernel erstellt mehrere Speicherknoten beim Booten, anstatt einen einzelnen Speicherknoten zu erstellen.
Das Konstrukt mit mehreren Knoten kann zu einer Speichererschöpfung auf einem oder mehreren Knoten führen, bevor andere Knoten erschöpft sind. Wenn die Speichererschöpfung eintritt, kann der Kernel Prozesse beenden (z. B. den Bild- oder Platform-Server), selbst wenn verfügbarer Speicher vorhanden ist.
Daher empfiehlt Adobe, dass Sie NUMA bei der Ausführung eines solchen Systems mit der Boot-Option **numa=off** ausschalten, um zu vermeiden, dass der Kernel diese Prozesse beendet.

>[!NOTE]
**Host-Name des Servers muss aufgelöst werden**: Stellen Sie sicher, dass der Host-Name des Servers in eine IP-Adresse aufgelöst werden kann. Wenn dies nicht möglich ist, fügen Sie zu **/etc/hosts** den vollqualifizierten Hostnamen und die IP-Adresse hinzu:
`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft® Windows Server 2016
* Swap-Speicherplatz, der mindestens der doppelten Menge des physischen Speichers (RAM) entspricht

Um Dynamic Media unter Windows zu verwenden, installieren Sie Microsoft® Visual Studio 2010, 2013 und 2015, Redistributable for x64 and x86.

Für Windows x64:

* Microsoft® Visual Studio 2010-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=26999](https://www.microsoft.com/de-de/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/de-de/download/details.aspx?id=40784)
* Microsoft® Visual Studio 2015-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

Windows x86:

* Microsoft® Visual Studio 2010-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=26999](https://www.microsoft.com/de-de/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013-Redistributable unter [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft® Visual Studio 2015-Redistributable unter [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/de-de/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x und höher
* Wird nur für Test- und Demozwecke unterstützt

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
PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
Zusätzlich gilt Folgendes,
* PDF Generator erfordert die 32-Bit-Version der [klassischen Acrobat 2020-Version 20.004.30006](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) oder der Acrobat 2017-Version 17.011.30078, um die Konvertierung durchzuführen.
* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt®.
* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft® Office Professional Plus und andere für die Konvertierung unter Windows-Betriebssystemen erforderliche Software.
* PDF Generator unterstützt die 32-Bit- und 64-Bit-Versionen von OpenOffice unter Linux® Betriebssystemen.
* PDF Generator unterstützt Microsoft® Office 365 nicht.
* Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
* Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Programmgesteuerter Zugriff auf die gebündelte Version nur mit AEM Forms während der Laufzeit der AEM Forms-Lizenz für die Verwendung mit AEM Forms PDF Generator. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung entsprechend Ihrer Implementierung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))
* Der PDF Generator-Dienst unterstützt Microsoft® Windows 10 nicht.
* PDF Generator kann Dateien mit Microsoft® Visio 2019 nicht konvertieren. Sie können weiterhin Microsoft® Visio 2016 zum Konvertieren verwenden `.VSD` und `.VSDX` Dateien.
* PDF Generator kann Dateien mit Microsoft® Project 2019 nicht konvertieren. Sie können weiterhin das Microsoft® Project 2016 verwenden, um `.VSD` und `.VSDX` Dateien.
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

Das Zurückschreiben von XMP-Daten wird für die folgenden Plattformen und Dateiformate unterstützt und aktiviert:

* **Betriebssysteme:**

   * Linux® (32-Bit- und 32-Bit-Anwendungsunterstützung auf 64-Bit-Systemen). Anweisungen zum Installieren von 32-Bit-Client-Bibliotheken finden Sie unter [So aktivieren Sie XMP Extraktion und Zurückschreiben auf 64-Bit Red Hat® Linux®](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

   * Windows Server
   * macOS X (64 Bit)

* **Dateiformate**: JPEG, PNG, TIFF, PDF, INDD, AI und EPS.

### Anforderungen für die Verarbeitung von Metadaten-lastigen Assets durch AEM Assets unter Linux® {#assetsonlinux}

Für den XMPFilesProcessor-Prozess ist die Bibliothek GLIBC_2.14 erforderlich. Verwenden Sie einen Linux®-Kernel, der GLIBC_2.14 enthält, z. B. Linux® Kernel Version 3.1.x. Sie verbessert die Leistung bei der Verarbeitung von Assets, die eine große Menge an Metadaten enthalten, z. B. PSD-Dateien. Die Verwendung einer früheren Version von GLIBC führt zu Fehlern in Protokollen, die mit `com.day.cq.dam.core.impl.handler.xmp.NCommXMPHandler Failed to read XMP` beginnen.
