---
title: Technische Anforderungen
description: In diesem Dokument werden die unterstützten Client- und Server-Plattformen für Adobe Experience Manager aufgeführt.
topic-tags: platform
exl-id: 47529b9a-c4e5-434f-ac26-b01714ff863b
source-git-commit: d5e7f0301259fdc12b507f9568befcc34ebe9408
workflow-type: tm+mt
source-wordcount: '3644'
ht-degree: 93%

---

# Technische Anforderungen{#technical-requirements}

Adobe unterstützt Adobe Experience Manager (AEM) auf den Plattformen, wie in den folgenden Informationen in diesem Dokument beschrieben.

Wenden Sie sich bei Problemen, die speziell mit der Plattform in Verbindung stehen, an den Plattformanbieter.

>[!NOTE]
>
>Je nach Plattform, auf der Sie AEM installieren, kann es verschiedene Anforderungen für die Benutzerverwaltung geben.

## Voraussetzungen {#prerequisites}

Mindestanforderungen für die Ausführung von Adobe Experience Manager:

* Installierte Java™-Plattform, Standard Edition JDK oder andere unterstützte [Java Virtual Machines](#java-virtual-machines)
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
   <td>Um den Projekterfolg unserer Kundinnen und Kunden sicherzustellen, bietet Adobe im Rahmen eines eingeschränkten Support-Programms volle Unterstützung an. Dafür müssen bestimmte Bedingungen erfüllt sein. Der Support auf R-Ebene erfordert eine formelle Kundenanfrage und eine Bestätigung durch Adobe. Weitere Informationen erhalten Sie bei der Kundenunterstützung von Adobe.</td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| **Z: Nicht unterstützt** | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

## Unterstützte Plattformen {#supported-platforms}

### Java™ Virtual Machines {#java-virtual-machines}

Für die Anwendung ist eine Java™ Virtual Machine erforderlich, die mit der Verteilung des Java™ Development Kit bereitgestellt wird.

Adobe Experience Manager funktioniert mit den folgenden Versionen der Java™ Virtual Machine:

>[!CAUTION]
>
>Verfolgen Sie die Sicherheitsbulletins des Java™-Anbieters. Auf diese Weise wird die Sicherheit der Produktionsumgebungen gewährleistet. Installieren Sie außerdem immer die neuesten Java™-Updates.

| **Plattform** | **Unterstützungsebene** | **Verknüpfung** |
|---|---|---|
| Oracle Java™ SE 17 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 11 JDK − 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+11*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=24&lt;td>) |
| Oracle Java™ SE 10 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 9 JDK | Z: Nicht unterstützt `[1]` |
| Oracle Java™ SE 8 JDK − 64 Bit | A: Unterstützt `[1]` | [Download](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+8*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=10) |
| IBM® J9 VM − Build 2.9, JRE 1.8.0 | A: Unterstützt `[2]` |
| IBM® J9 VM − Build 2.8, JRE 1.8.0 | A: Unterstützt `[2]` |
| Azul Zulu OpenJDK 11 − 64 Bit | A: Unterstützt `[3]` | |
| Azul Zulu OpenJDK 8 − 64 Bit | A: Unterstützt `[3]` | |

1. Oracle ist auf ein LTS-Modell (Long Term Support) für Oracle Java™ SE-Produkte umgestiegen. Java™ 9, Java™ 10 und Java™ 12 sind Nicht-LTS-Versionen von Oracle (weitere Informationen finden Sie in der [Roadmap für Oracle Java™ SE-Support](https://www.oracle.com/technetwork/java/eol-135779.html)). Um AEM in einer Produktionsumgebung bereitzustellen, unterstützt Adobe ausschließlich LTS-Versionen von Java™. Der Support und die Bereitstellung des Oracle Java™ SE JDK, einschließlich aller Wartungsupdates von LTS-Versionen, werden von Adobe direkt für alle AEM-Kundinnen und -Kunden unterstützt, die die Oracle Java™ SE-Technologie nutzen. Weitere Informationen finden Sie in der [Richtlinie zur Java™-Unterstützung für Adobe Experience Manager](assets/Java_Policy_for_Adobe_Experience_Manager.pdf).
   **Wichtig: Oracle Java™ 11 wird noch mindestens bis September 2026 unterstützt. Unterstützung für Oracle Java™ 17 wird derzeit vorbereitet.**

1. Die IBM® JRE wird nur zusammen mit WebSphere Application Server unterstützt.

1. Azul Zulu OpenJDK LTS-Versionen werden für lokale AEM-Implementierungen ab Version 6.5 SP9 unterstützt. Der Support und die Verteilung der Azul Zulu JDK LTS-Versionen müssen durch Adobe-Kundinnen und -Kunden direkt von Azul lizenziert werden.


### Speicherung und Persistenz {#storage-persistence}

Es gibt verschiedene Optionen zum Bereitstellen des Repositorys von Adobe Experience Manager. In der folgenden Liste finden Sie unterstützte Technologien und Speicheroptionen.

| **Plattform** | **Beschreibung** | **Unterstützungsebene** |
|---|---|---|
| **Dateisystem mit TAR-Dateien** `[1]` | Repository | A: Unterstützt |
| **Dateisystem mit Datastore** `[1]` | Binärdateien | A: Unterstützt |
| Speichern von Binärdateien in TAR-Dateien im Dateisystem `[1]` | Binärdateien | Z: Wird nicht für die Produktion unterstützt |
| Amazon S3 | Binärdateien | A: Unterstützt |
| Microsoft® Azure Blob Storage | Binärdateien | A: Unterstützt |
| MongoDB Enterprise 6.0 | Repository | A: Unterstützt `[3, 4]` |
| MongoDB Enterprise 5.0 | Repository | A: Unterstützt `[3, 4]` |
| MongoDB Enterprise 4.4 | Repository | A: Unterstützt `[2, 3, 4, 7]` |
| MongoDB Enterprise 4.2 | Repository | A: Unterstützt `[2, 3, 4, 7]` |
| MongoDB Enterprise 4.0 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.6 | Repository | Z: Nicht unterstützt |
| MongoDB Enterprise 3.4 | Repository | Z: Nicht unterstützt |
| IBM® DB2® 10.5 | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung `[5]` |
| Oracle Database 12c (12.1.x) | Repository und Forms-Datenbank | R: Eingeschränkte Unterstützung  |
| Microsoft® SQL Server 2016 | Forms-Datenbank | A: Unterstützt |
| **Apache Lucene (Schnellstart integriert)** | Suchdienst | A: Unterstützt |
| Apache Solr | Suchdienst | A: Unterstützt |

1. „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Führen Sie Lasttests für AEM mit dem Netzwerk-/Remote-Dateisystem durch.
1. Für die MongoDB Enterprise-Versionen 4.2 und 4.4 ist mindestens AEM 6.5 SP9 erforderlich.
1. MongoDB Sharding wird in AEM nicht unterstützt.
1. Nur MongoDB Storage Engine WiredTiger wird unterstützt.
1. Wird für Kundinnen und Kunden von AEM Forms-Upgrades unterstützt. Wird für neue Installationen nicht unterstützt.
1. Gilt nur für AEM Forms:
   * Die Unterstützung für Oracle Database 12c wurde entfernt und die Unterstützung für Oracle Database 19c wurde hinzugefügt.
   * Die Unterstützung für Microsoft® SQL Server 2016 wurde entfernt und die Unterstützung für Microsoft® SQL Server 2019 wurde hinzugefügt.
1. Wird für AEM Forms nicht unterstützt.

>[!NOTE]
>
>Weitere Informationen zur Funktion von AEM Communities finden Sie unter [Bereitstellen von Communities](/help/communities/deploy-communities.md).

>[!NOTE]
>
>MongoDB ist ein Drittanbieter-Software-Programm und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie auf der Seite zur [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.com/licensing/server-side-public-license/faq).
>
>Um Ihre AEM-Implementierung mit MongoDB optimal nutzen zu können, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten. Weitere Informationen finden Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk).
>
>Die Lizenz umfasst eine Standard-Replikatgruppe. Diese besteht aus einer primären und zwei sekundären Instanzen, die für die Autoren- oder Veröffentlichungsbereitstellungen verwendet werden können.
>
>Wenn Sie sowohl Author als auch Publish in MongoDB ausführen möchten, müssen zwei separate Lizenzen erworben werden.
>
>Die Adobe-Kundenunterstützung hilft beim Qualifizieren von Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen.
>
>Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Unterstützte relationale Datenbanken wie oben aufgeführt sind Software von Drittanbietern und sind nicht im AEM-Lizenzierungspaket enthalten.
>
>Um AEM 6.5 mit einer unterstützten relationalen Datenbank ausführen zu können, ist ein separater Support-Vertrag mit einem Datenbankanbieter erforderlich. Die Adobe-Kundenunterstützung hilft beim Qualifizieren von Problemen, die mit der Verwendung von relationalen Datenbanken mit AEM 6.5 in Zusammenhang stehen.
>
>**Die meisten relationalen Datenbanken werden derzeit in Level-R auf AEM 6.5 unterstützt, das mit Support-Kriterien und einem Support-Programm geliefert wird, wie in der obigen Beschreibung zu Level-R angegeben.**

### Servlet-Engines/Anwendungs-Server {#servlet-engines-application-servers}

Adobe Experience Manager kann als eigenständiger Server (quickstart-JAR-Datei) oder als Web-Anwendung auf einem Drittanbieter-Anwendungs-Server (WAR-Datei) ausgeführt werden.

Als Servlet-API-Version ist mindestens Servlet 3.1 erforderlich.

| Plattform | Unterstützungsebene |
|---|---|
| **Integrierte Schnellstart-Servlet-Engine (Jetty 9.4)** | A: Unterstützt |
| Oracle WebLogic Server 12.2 (12cR2) | Z: Nicht unterstützt |
| Kontinuierliche Bereitstellung für IBM® WebSphere® Application Server (LibertyProfile) mit Web Profile 7.0 und IBM® JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| IBM® WebSphere® Application Server 9.0 und IBM® JRE 1.8 | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| Apache Tomcat 8.5.x | R: Eingeschränkte Unterstützung für neue Verträge `[2]` |
| JBoss® EAP 7.2.x mit JBoss® Application Server | Z: Nicht unterstützt |
| JBoss® EAP 7.1.4 mit JBoss® Application Server | R: Eingeschränkte Unterstützung für neue Verträge `[1]` `[2]` |
| JBoss® EAP 7.0.x mit JBoss® Application Server | Z: Nicht unterstützt |

1. Wird für Bereitstellungen mit AEM Forms empfohlen.
1. Der Start von AEM 6.5-Bereitstellungen auf Anwendungs-Servern wird nun eingeschränkt unterstützt. Bestehende Kunden können auf AEM 6.5 aktualisieren und weiterhin Anwendungs-Server verwenden. Für neue Kundinnen und Kunden werden Support-Kriterien und ein Support-Programm zur Verfügung gestellt, wie oben in der Beschreibung zu Level-R angegeben.
1. Gilt nur für AEM Forms:
   * Unterstützung für JBoss® EAP 7.1.4 entfernt und Unterstützung für JBoss® EAP 7.4.10 hinzugefügt.

### Server-Betriebssysteme {#server-operating-systems}

Adobe Experience Manager arbeitet mit den folgenden Server-Plattformen für Produktionsumgebungen:

| **Plattform** | **Unterstützungsebene** |
|---|---|
| **Linux®, basierend auf der Red Hat®-Verteilung** | A: Unterstützt `[1]` `[3]` |
| Linux®, auf Basis der Debian-Verteilung einschl. Ubuntu | A: Unterstützt `[1]` `[2]` |
| Linux®, auf Basis der SUSE®-Verteilung | A: Unterstützt `[1]` |
| Microsoft® Windows Server 2019 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft® Windows Server 2016 `[4]` | R: Eingeschränkte Unterstützung für neue Verträge `[5]` |
| Microsoft® Windows Server 2012 R2 | Z: Nicht unterstützt |
| Oracle Solaris™ 11 | Z: Nicht unterstützt |
| IBM® AIX® 7.2 | Z: Nicht unterstützt |

1. Linux® Kernel 2.6, 3. x, 4. x und 5. x umfasst Derivate der Red Hat-Verteilung, einschließlich Red Hat® Enterprise Linux®, CentOS, Oracle Linux und Amazon Linux®. Die Add-on-Funktionen von AEM Forms werden nur unter CentOS 7, Red Hat® Enterprise Linux® 7, Red Hat® Enterprise Linux® 8 und Red Hat® Enterprise Linux® 9 unterstützt.
1. AEM Forms wird auf Ubuntu 20.04 LTS unterstützt.
1. Die Linux®-Verteilung wird von Adobe Managed Services unterstützt.

   >[!NOTE]
   >
   >Für Linux-basierte Server (OSGI- und JEE-Stack) erfordert das AEM Forms-Add-on Laufzeitabhängigkeiten wie:
   >* glibc.x86_64 (2.17-196)
   >* libX11.x86_64 (1.6.7-4)
   >* zlib.x86-64 (1.2.7-17)
   >* libxcb.x86_64 (1.13-1.el7)
   >* libXau.x86_64 (1.0.8-2.1.el7)

1. Produktionsimplementierungen von Microsoft® Windows werden für Kundinnen und Kunden unterstützt, die ein Upgrade auf 6.5 durchführen, sowie für die Nutzung außerhalb der Produktion. Neue Bereitstellungen erfolgen auf Anfrage für AEM Sites und Assets.
1. AEM Forms wird auf Microsoft Windows® Server ohne die Einschränkungen von Support-Level R unterstützt.
1. AEM Forms unterstützt Microsoft® Windows Server 2016 nicht mehr.

>[!NOTE]
>
>Wenn Sie AEM Forms 6.5 installieren, stellen Sie sicher, dass Sie die folgenden 32-Bit-Versionen von Microsoft® Visual C++ Redistributable installiert haben.
>
>* Microsoft® Visual C++ 2008 Redistributable
>* Microsoft® Visual C++ 2010 Redistributable
>* Microsoft® Visual C++ 2012 Redistributable
>* Microsoft® Visual C++ 2013 Redistributable
>* Microsoft® Visual C++ 2019 (VC14.28 oder höher) Redistributable


### Virtuelle und Cloud-Computing-Umgebungen {#virtual-cloud-computing-environments}

Adobe Experience Manager wird in einer virtuellen Maschine in Cloud-Computing-Umgebungen unterstützt. Zu diesen Umgebungen gehören Microsoft® Azure und Amazon Web Services (AWS), die gemäß den auf dieser Seite aufgeführten technischen Anforderungen und den standardmäßigen Support-Bedingungen von Adobe ausgeführt werden.

Für eine Cloud-native Umgebung sollten Sie sich das neueste Angebot aus der AEM-Produktlinie ansehen: Adobe Experience Manager as a Cloud Service. Weitere Informationen finden Sie in der [Dokumentation zu Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de).

Adobe bietet auch Adobe Managed Services an, um AEM auf Azure oder AWS bereitzustellen. Adobe Managed Services liefert die Erfahrung und Kenntnisse, die Experten zur Bereitstellung und Ausführung von AEM in diesen Cloud-Computing-Umgebungen benötigen. Siehe die [zusätzliche Dokumentation zu Adobe Managed Services](https://business.adobe.com/de/products/experience-manager/managed-services.html?aemClk=t).

In allen anderen Fällen der Bereitstellung von AEM auf Azure, AWS oder einer anderen Cloud-Computing-Umgebung beschränkt sich Unterstützung von Adobe auf die virtuelle Rechenumgebung. Diese virtuelle Umgebung muss in Übereinstimmung mit den auf dieser Seite aufgeführten technischen Spezifikationen ausgeführt werden. Jedes gemeldete Problem, das im Zusammenhang mit AEM in einer dieser Cloud-Umgebungen auftritt, muss unabhängig von einem Cloud-Service reproduzierbar sein, der speziell für die Cloud-Computing-Umgebung gilt. Das heißt, es sei denn, der Cloud-Service wird im Rahmen der auf dieser Seite aufgelisteten technischen Anforderungen unterstützt, z. B. Azure Blob Storage oder AWS S3.

Für die Bereitstellung von AEM auf Azure oder AWS außerhalb von Adobe Managed Services wird von Adobe dringend empfohlen, direkt mit dem Cloud-Anbieter zu arbeiten. Oder Sie arbeiten mit Adobe-Partnern zusammen, die die Bereitstellung von AEM in der gewünschten Cloud-Umgebung unterstützen. Der ausgewählte Cloud-Anbieter oder -Partner ist für die Größenspezifikationen, das Design und die Implementierung der Architektur verantwortlich, um Ihre spezifischen Anforderungen an Leistung, Auslastung, Skalierbarkeit und Sicherheit zu erfüllen.

### Dispatcher-Plattformen (Webserver) {#dispatcher-platforms-web-servers}

Beim Dispatcher handelt es sich um eine Zwischenspeicherungs- und Lastenausgleichskomponente. [Laden Sie die neueste Dispatcher-Version herunter](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html?lang=de). Für Experience Manager 6.5 ist die Dispatcher-Version 4.3.2 oder höher erforderlich.

Die folgenden Web-Server werden für die Verwendung mit der Dispatcher-Version 4.3.2 unterstützt:

| Plattform | Unterstützungsebene |
|---|---|
| **Apache httpd 2.4.x** `[1,2]` | A: Unterstützt |
| Microsoft IIS® 10 (Internet Information Server) | A: Unterstützt |
| Microsoft® IIS 8.5 (Internet Information Server) | Z: Nicht unterstützt |

1. Auf Apache HTTPD-Quell-Code basierende Webserver werden im gleichen Umfang unterstützt wie die HTTPD-Version, auf der sie basieren. Wenden Sie sich bei Zweifeln hinsichtlich der Unterstützungsebene des jeweiligen Serverprodukts zur Bestätigung an Adobe. Die folgenden Fälle:

   1. Der HTTP-Server wurde nur mit offiziellen Apache-Quellverteilungen erstellt, oder
   1. Der HTTP-Server wurde als Teil des Betriebssystems bereitgestellt, auf dem er ausgeführt wird. Beispiele: IBM® HTTP Server, Oracle HTTP Server

1. Der Dispatcher ist nicht für Apache 2.4.x für Windows-Betriebssysteme verfügbar.

## Unterstützte Client-Plattformen {#supported-client-platforms}

### Unterstützte Browser für die Authoring-Benutzeroberfläche {#supported-browsers-for-authoring-user-interface}

Die Adobe Experience Manager-Benutzeroberfläche funktioniert mit den folgenden Client-Plattformen. Alle Browser werden mit dem Standardsatz von Plug-ins und Add-ons getestet.

Die AEM-Benutzeroberfläche ist für größere Bildschirme (normalerweise Notebooks und Desktop-Computer) und den Tablet-Formfaktor (z. B. Apple iPad oder Microsoft® Surface) optimiert. Der Telefon-Formfaktor wird nicht unterstützt.

>[!NOTE]
>
>**Unterstützung für Browser mit schnellen Versionszyklen:**
>
>Die Versionen von Mozilla Firefox, Google Chrome und Microsoft® Edge werden alle paar Monate aktualisiert. Adobe setzt sich dafür ein, Aktualisierungen für Adobe Experience Manager bereitzustellen, um die unten beschriebene Unterstützungsebene mit den kommenden Versionen dieser Browser beizubehalten.

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
   <td>Microsoft® Edge (Evergreen)</td>
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

1. Version mit erweiterter Unterstützung von Firefox [Weitere Informationen dazu finden Sie auf mozilla.org](https://www.mozilla.org/de-DE/firefox/enterprise/)
1. Unterstützung für Apple iPad

### Unterstützte Browser für Websites {#supported-browsers-for-websites}

Im Allgemeinen hängt die Browser-Unterstützung für mit AEM Sites gerenderte Websites von der Implementierung der AEM-Seitenvorlagen, dem Design und der Komponentenausgabe ab und wird daher von der Partei kontrolliert, die diese Teile implementiert.

### WebDAV-Clients {#webdav-clients}

**Microsoft® Windows 7+**

Um eine erfolgreiche Verbindung mit Microsoft® Windows 7+ zu einer AEM-Instanz herzustellen, die nicht mit SSL gesichert ist, muss unter Windows die Standardauthentifizierung über ein ungesichertes Netzwerk aktiviert sein. Dies erfordert eine Änderung in der Windows-Registrierung des WebClient:

1. Suchen Sie den Registrierungsunterschlüssel:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Fügen Sie diesem Unterschlüssel den Registrierungseintrag „BasicAuthLevel“ mit dem Wert 2 oder mehr hinzu.

## Zusätzliche Hinweise zu Platform {#additional-platform-notes}

Dieser Abschnitt enthält spezielle Hinweise und detailliertere Informationen zum Ausführen von Adobe Experience Manager und seinen Add-ons.

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von Adobe Experience Manager (Instance, Dispatcher) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb ist nahtlos, da keine spezielle Konfiguration erforderlich ist. Sie können bei Bedarf einfach eine IP-Adresse im Format angeben, das Ihrem Netzwerktyp entspricht.

Wenn eine IP-Adresse angegeben werden muss, können Sie (nach Bedarf) aus folgenden Optionen auswählen:

* Eine IPv6-Adresse. Beispiel: `https://[ab12::34c5:6d7:8e90:1234]:4502`

* Eine IPv4-Adresse. Beispiel: `https://123.1.1.4:4502`

* Ein Servername. Beispiel: `https://www.yourserver.com:4502`

* Der Standardfall `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen angenommen. Beispiel: `https://localhost:4502`

### Voraussetzungen für das AEM Dynamic Media-Add-on {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media ist standardmäßig deaktiviert. Hier finden Sie Informationen zum [Aktivieren von Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Wenn Dynamic Media aktiviert ist, gelten die folgenden zusätzlichen technischen Anforderungen.

>[!NOTE]
>
>Diese **Systemanforderungen** gelten, wenn Sie den Modus „Dynamic Media –Hybrid“ verwenden. Der Modus „Dynamic Media –Hybrid“ verfügt über einen eingebetteten Bildserver, der nur für bestimmte Betriebssysteme zertifiziert ist.
>
>Für Dynamic Media-Kunden, die den Modus „Dynamic Media – Scene7“ ausführen (d. h. Ausführungsmodus **dynamicmedia_scene7**) gelten keine weiteren Systemanforderungen. Es gelten dieselben Systemanforderungen wie für AEM. Die Architektur des Dynamic Media Scene7-Modus verwendet den Cloud-basierten Bilddienst und nicht den in AEM eingebetteten Dienst.

#### Hardware {#hardware}

Die folgenden Hardware-Anforderungen gelten für Linux® und Windows:

* Intel Xeon®- oder AMD® Opteron-CPU mit mindestens vier Kernen
* Mindestens 16 GB RAM

#### Linux® {#linux}

Wenn Sie Dynamic Media auf Linux® verwenden, müssen die folgenden Voraussetzungen erfüllt sein:

* Red Hat® Enterprise 7 oder CentOS 7 und höher mit den neuesten Fix-Patches
* 64-Bit-Betriebssystem
* Swapping deaktiviert (empfohlen)
* SELinux deaktiviert (siehe folgenden Hinweis)

>[!NOTE]
>
>Falls das Gebietsschema so festgelegt ist, dass LC_CTYPE nicht `en_US.UTF-8` entspricht, funktioniert Dynamic Media nicht. Geben Sie bei der Eingabeaufforderung den Wert „locale“ ein, um den Wert zu ermitteln. Wenn er nicht richtig eingestellt ist, legen Sie die Umgebungsvariable LC_CTYPE auf die leere Zeichenfolge fest, indem Sie „export LC_CTYPE=“ eingeben, bevor Sie AEM ausführen.

>[!NOTE]
>
>**Deaktivieren von SELinux**: Die Bereitstellung von Bildern funktioniert nicht, wenn SELinux aktiviert ist. Diese Option ist standardmäßig aktiviert. Um dieses Problem zu beheben, bearbeiten Sie die Datei **/etc/selinux/config** und ändern Sie den SELinux-Wert von:
>
>`SELINUX=enforcing` **nach** `SELINUX=disabled`

>[!NOTE]
>
>**NUMA-Architektur:** Systeme mit Prozessoren mit AMD64 und Intel® EM64T sind normalerweise als NUMA-Plattformen (Non-Uniform Memory Architecture) konfiguriert. Das heißt, der Kernel erstellt mehrere Speicherknoten beim Booten, anstatt einen einzelnen Speicherknoten zu erstellen.
>
>Das Konstrukt mit mehreren Knoten kann zu einer Speichererschöpfung auf einem oder mehreren Knoten führen, bevor andere Knoten erschöpft sind. Wenn die Speichererschöpfung eintritt, kann der Kernel Prozesse beenden (z. B. den Bild- oder Platform-Server), selbst wenn verfügbarer Speicher vorhanden ist.
>
>Daher empfiehlt Adobe, dass Sie NUMA bei der Ausführung eines solchen Systems mit der Boot-Option **numa=off** ausschalten, um zu vermeiden, dass der Kernel diese Prozesse beendet.

>[!NOTE]
>
>**Host-Name des Servers muss aufgelöst werden**: Stellen Sie sicher, dass der Host-Name des Servers in eine IP-Adresse aufgelöst werden kann. Wenn dies nicht möglich ist, fügen Sie zu **/etc/hosts** den vollqualifizierten Hostnamen und die IP-Adresse hinzu:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft® Windows Server 2016
* Swap-Speicherplatz, der mindestens der doppelten Menge des physischen Speichers (RAM) entspricht

Um Dynamic Media auf Windows zu verwenden, installieren Sie Microsoft® Visual Studio 2010, 2013 und 2015 Redistributable für x64 und x86.

Für Windows x64:

* Microsoft® Visual Studio 2010 Redistributable ist hier erhältlich: [https://www.microsoft.com/de-de/download/details.aspx?id=26999](https://www.microsoft.com/de-de/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013 Redistributable ist hier erhältlich: [https://www.microsoft.com/de-de/download/details.aspx?id=40784](https://www.microsoft.com/de-de/download/details.aspx?id=40784)
* Microsoft® Visual Studio 2015 Redistributable ist hier erhältlich: [https://www.microsoft.com/de-de/download/details.aspx?id=48145](https://www.microsoft.com/de-de/download/details.aspx?id=48145)

Windows x86:

* Microsoft® Visual Studio 2010 Redistributable ist hier erhältlich: [https://www.microsoft.com/de-de/download/details.aspx?id=26999](https://www.microsoft.com/de-de/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013 Redistributable ist hier erhältlich: [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft® Visual Studio 2015 Redistributable ist hier erhältlich: [https://www.microsoft.com/de-de/download/details.aspx?id=52685](https://www.microsoft.com/de-de/download/details.aspx?id=52685)

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
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* PDF Generator erfordert die 32-Bit-Version der [klassischen Acrobat 2020-Version 20.004.30006](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) oder der Acrobat 2017-Version 17.011.30078, um die Konvertierung durchzuführen.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt®.
>* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft® Office Professional Plus und andere für die Konvertierung unter einem Windows-Betriebssystem erforderliche Software.
>* PDF Generator unterstützt 32-Bit- und 64-Bit-Versionen von OpenOffice unter dem Linux®-Betriebssystem.
>* PDF Generator unterstützt nicht Microsoft® Office 365.
>* Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
>* Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur programmatisch mit AEM Forms zugänglich sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung für Ihre Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))
>* Der PDF Generator-Service unterstützt nicht Microsoft® Windows 10.
>* PDF Generator kann keine Dateien mit Microsoft® Visio 2019 konvertieren. Sie können weiterhin Microsoft® Visio 2016 verwenden, um `.VSD`- und `.VSDX`-Dateien zu konvertieren.
>* PDF Generator kann keine Dateien mit Microsoft® Project 2019 konvertieren. Sie können weiterhin Microsoft® Project 2016 verwenden, um `.VSD`- und `.VSDX`-Dateien zu konvertieren.
>

### Anforderungen für AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 oder Windows® 11
* Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher – 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Video-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC
* Administratorrechte für die Installation von Designer
* Microsoft Visual C++ 2019 (VC 14.28 oder höher) 32-Bit-Laufzeit für 32-Bit-AEM Forms Designer
* Microsoft Visual C++ 2019 (VC 14.28 oder höher) 64-Bit-Laufzeitumgebung für AEM Forms Designer 64-Bit (sowohl für OSGI- als auch JEE-Stack)

### Anforderungen für das Zurückschreiben von XMP-Metadaten der AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

Das Zurückschreiben von XMP-Daten wird für die folgenden Plattformen und Dateiformate unterstützt und aktiviert:

* **Betriebssysteme:**

   * Linux® (Unterstützung von 32-Bit- und 64-Bit-Anwendungen auf 64-Bit-Systemen). Schritt-für-Schritt-Anleitungen zur Installation von 32-Bit-Client-Bibliotheken finden Sie unter [Aktivieren von XMP-Extraktion und -Writeback auf Red Hat Linux® (64 Bit)](https://helpx.adobe.com/de/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

   * Windows Server
   * macOS X (64 Bit)

* **Dateiformate**: JPEG, PNG, TIFF, PDF, INDD, AI und EPS.

### Anforderungen an AEM Assets zur Verarbeitung von Metadaten-lastigen Assets unter Linux® {#assetsonlinux}

Für den XMPFilesProcessor-Prozess ist die Bibliothek GLIBC_2.14 erforderlich. Verwenden Sie einen Linux®-Kernel, der GLIBC_2.14 enthält, z. B. Linux® Kernel Version 3.1.x. Sie verbessert die Leistung bei der Verarbeitung von Assets, die eine große Menge an Metadaten enthalten, z. B. PSD-Dateien. Die Verwendung einer früheren Version von GLIBC führt zu Fehlern in Protokollen, die mit `com.day.cq.dam.core.impl.handler.xmp.NCommXMPHandler Failed to read XMP` beginnen.