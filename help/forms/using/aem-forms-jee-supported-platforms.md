---
title: Unterstützte Plattformen für AEM Forms on JEE
seo-title: Unterstützte Plattformen für AEM Forms on JEE
description: Liste der Infrastrukturkomponenten, die für die Installation von AEM Forms on JEE erforderlich sind und unterstützt werden
seo-description: Liste der Infrastrukturkomponenten, die für die Installation von AEM Forms on JEE erforderlich sind und unterstützt werden
uuid: 777f943b-4cb4-444e-a036-8032b9fce5be
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: f777865e-d4a8-40ef-87b0-130c19eb1b91
docset: aem65
role: Administrator
exl-id: 74d22cf4-56b2-48f5-92d9-928eaa134866
source-git-commit: 1cef6f87fa66fd78d439c23e6ac907f9531b8fd6
workflow-type: tm+mt
source-wordcount: '3309'
ht-degree: 75%

---

# Unterstützte Plattformen für AEM Forms on JEE{#supported-platforms-for-aem-forms-on-jee}

## Unterstützte Plattformen {#supported-platforms}

### Unterstützungsebenen {#support-levels}

AEM Forms on JEE-Server kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungsservern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden.

In diesem Dokument werden die unterstützten Client- und Serverplattformen für AEM Forms on JEE aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für empfohlene und andere Konfigurationen gelten. In diesem Dokument werden auch andere unterstützte Software und deren Versionen, Ausnahmen, Patch-Definitionen sowie die Richtlinie zur Unterstützung für Software-Patches von Drittanbietern aufgeführt.

>[!NOTE]
>
>* Eine vollständige Liste der Ausnahmen für unterstütze Serverplattformen finden Sie unter [Ausnahmen für unterstützte Serverplattformen](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p).
>* AEM Forms on JEE unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>



### Empfohlene Konfigurationen {#recommendedconfigurations}

Adobe empfiehlt die folgenden Konfigurationen und bietet vollständige oder eingeschränkte Unterstützung im Rahmen des Standard-Software-Wartungsvertrags:

<table>
 <tbody>
  <tr>
   <th>Unterstützungsebene</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>A: Unterstützt<br /> </td>
   <td>Adobe bietet eine vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird durch den Adobe-Qualitätssicherungsprozess abgedeckt.</td>
  </tr>
  <tr>
   <td>R: Eingeschränkte Unterstützung </td>
   <td>Adobe bietet vollständige Unterstützung für diese Konfiguration, sofern bestimmte Voraussetzungen erfüllt sind. Kontaktieren Sie den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren und stellen Sie eine Supportanfrage.</td>
  </tr>
  <tr>
   <td>L: Begrenzte Unterstützung</td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfigurationen, sofern bestimmte Voraussetzungen erfüllt sind. In der Konfiguration sind nicht alle Funktionen verfügbar. Kontaktieren Sie den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren, und stellen Sie eine Supportanfrage.<br /> </td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
|---|---|
| E: Funktionsfähigkeit wird erwartet | Es wird erwartet, dass die Konfiguration funktioniert, und es wird nichts Gegenteiliges berichtet. |
| Z: Nicht unterstützt | Die Konfiguration wird nicht unterstützt. Adobe macht keinerlei Aussagen, ob die Konfiguration funktioniert, und unterstützt diese nicht. |

>[!NOTE]
>
>Um AEM Forms-Kunden dabei zu helfen, die Eigentümerkosten zu reduzieren, die Bereitstellungsarchitektur zu vereinfachen und den Entwicklungs-Stack zu modernisieren, verlagert sich die Adobe Experience Manager-Unternehmensplattform von anwendungsserverbasierten Implementierungen hin zu eigenständigen OSGi-basierten Implementierungen. Adobe unterstützt weiterhin den AEM Forms JEE-Stack mit einer reduzierten Matrix von Infrastrukturkomponenten.
>
>Mit Version 6.5 werden Infrastrukturkomponenten, die die geringste Nutzung unter unseren Kunden aufweisen, nicht mehr wie folgt unterstützt:
>・ IBM DB2-Datenbank
>・ IBM AIX- und Sun Solaris-Betriebssysteme
>
>Bei neuen Installationen wird empfohlen, AEM Forms auf dem modernen OSGi-Stack bereitzustellen, um die neuesten Innovationen rund um das responsive adaptive Forms für mobile, interaktive mehrkanalige Kommunikation und Backend-Datenintegrationen mithilfe des Formulardatenmodells zu nutzen.
>
>Wir erkennen an, dass bestehende Benutzer AEM Forms on JEE Stack weiterhin bereitstellen müssen. In solchen Fällen erfordert die Adobe die Bereitstellung von AEM Forms JEE auf unterstützter Infrastruktur, wie in dieser Dokumentation beschrieben. Wenn Sie ein Upgrade auf AEM 6.5 Forms durchführen und eine nicht unterstützte Plattform aus der vorherigen AEM Forms-Version verwenden, können Sie sich an den Adobe Support wenden, um Hilfe beim Upgrade auf eine unterstützte Plattform zu erhalten.

### Java Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms erfordert eine Java Virtual Machine, die durch die Java Development Kit(JDK)-Verteilung bereitgestellt wird. Adobe Experience Manager funktioniert mit den folgenden Versionen von Java Virtual Machine:

<table>
 <tbody>
  <tr>
   <th><p><strong>Plattform</strong></p> </th>
   <th><p><strong>Unterstützungsebene</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Oracle Java™ SE 11 (64 Bit)</p> </td>
   <td><p>Z: Nicht unterstützt</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Oracle Java™ SE 8 (64 Bit)</td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (Build 2.8, JRE 1.8.0)</td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (Build 2.9, JRE 1.8.0)<br /> </td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Es wird empfohlen, die Sicherheitsbulletins vom Java-Anbieter zu verfolgen, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java-Aktualisierungen zu installieren.
>* AEM Forms on JEE wird nur von 64-Bit-JVMs für Produktionsumgebungen unterstützt.


### Datenbanken und CRX-Persistenz {#databases-and-crx-persistence}

<table>
 <tbody>
  <tr>
   <td><p><strong>Plattform</strong></p> </td>
   <td><p><strong> Beschreibung</strong></p> </td>
   <td><p><strong>Unterstützungsebene</strong></p> </td>
  </tr>
  <tr>
   <td><p>Dateisystem</p> </td>
   <td><p>Repository Microkernel (TAR MK-Dateien)</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>MongoDB Enterprise 4.0 </p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>Oracle Database 12c Release 1</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
   <tr>
   <td><p>Oracle Database 12c Release 2 (12.2.0.1.0)</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td>Oracle Database 18c </td>
   <td>Repository-Mikrokernel</td>
   <td>Unterstützt</td>
  </tr> 
   <tr>
   <td>Oracle Database 19c (Standard, Real Application Clusters (RAC) und Enterprise Editions) </td>
   <td>Repository Microkernal </td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td><p>Microsoft SQL Server 2016</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>Microsoft SQL Server 2019</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td>IBM DB2 11.1</td>
   <td>Repository-Mikrokernel</td>
   <td>R: Eingeschränkte Unterstützung</td>
  </tr>
    <tr>
   <td>MySQL 5.7.19 </td>
   <td>-</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
 </tbody>
</table>

* IBM DB2 wird bei Neuinstallationen nicht unterstützt. Es wird nur für bestehende Kunden unterstützt, die auf AEM 6.5 Forms aktualisieren.
* MongoDB ist eine Drittanbietersoftware und nicht Bestandteil des AEM-Lizenzierungspakets. Weitere Informationen finden Sie auf der Seite mit der [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
* Adobe empfiehlt die Lizenzierung der MongoDB Enterprise-Version, damit Sie von der professionellen Unterstützung profitieren und die AEM-Bereitstellung optimal nutzen können.
* Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen. Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
* „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dies umfasst eine Netzwerkspeichertechnologie. Beachten Sie, dass die Dateisystemleistung möglicherweise variieren kann und sich auf die Gesamtleistung auswirkt. Es wird empfohlen, einen Lasttest für AEM in Verbindung mit dem Netzwerk/Remote-Dateisystem durchzuführen.
* Nur MongoDB Storage Engine WiredTiger wird unterstützt.
* MongoDB Sharding wird in AEM nicht unterstützt.
* AEM Forms on JEE unterstützt MySQL für RDBMK-Persistenz.
* Das Document Security-Modul verwendet nicht das Content Repository. Das bedeutet, wenn Sie nur Document Security und nicht HTML Workspace, HTML5 Forms und adaptive Formulare verwenden möchten, müssen Sie Content Repository nicht installieren.
* AEM Forms on JEE unterstützt nicht die Verwendung von MySQL für die Persistenz AEM Repositorys (CRX-Repository).


### Datenbanktreiber {#database-drivers}

<table>
 <tbody>
  <tr>
   <th>Datenbank </th>
   <th><p><strong>Plattform</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>MySQL</td>
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.44-bin.jar (Version 5.1.44)</p> </td>
   <td><p>AEM Forms on JEE-Installation im Paket enthalten</p> </td>
  </tr>
  <tr>
   <td>Microsoft SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-Treiber 6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td>
   <td><p>AEM Forms on JEE-Installation im Paket enthalten.</p> </td>
  </tr>
  <tr>
   <td>Microsoft SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-Treiber 8.2.2<br /> </p> <p>sqljdbc8.jar</p> </td>
   <td><p>Laden Sie von der Microsoft-Website herunter.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>Oracle Database 19.3.0.0.0 JDBC-Treiber</p> <p>ojdbc8.jar (Version 19.3.0.0.0)<br /> </p> </td>
   <td><p>Laden Sie von der <a href="https://www.oracle.com/technetwork/database/features/jdbc/jdbc-ucp-122-3110062.html">Oracle-Website</a> herunter.</p> </td>
  </tr>
 </tbody>
</table>

### Anwendungsserver {#application-servers}

<table>
 <tbody>
  <tr>
   <td><p><strong> Plattform</strong></p> </td>
   <td><p><strong>Unterstützungsebene</strong></p> </td>
   <td><p><strong>Unterstützte Patch-Definitionen</strong></p> </td>
  </tr>
  <tr>
   <td>Oracle WebLogic Server 12.2.1 (12c R2)</td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td>IBM® WebSphere® Application Server 9.0 <sup>[1] [4]</sup><br /> </td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application-Plattform (EAP) 7.1.4 <sup>[2] [3] [7]</sup></p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Patches und kumulative Patches für die unterstützte EAP-Version</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>IBM® WebSphere®-Cluster werden nur in Network Deployment-Editionen unterstützt.

### Server-Betriebssysteme {#server-operating-systems}

#### Produktionsumgebungen {#production-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong> Plattform</strong></p> </th>
   <th><p><strong>Unterstützungsebene</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft Windows Server 2016 (64 Bit)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td><p>Red Hat Enterprise Linux 7 (Kernel 3.x) (64-Bit)</br><b>Hinweis:</b> <a href="https://access.redhat.com/articles/4665701">Red Hat Enterprise Linux 6</a> erreicht das Ende der Wartungsphase und wechselt zur Phase des erweiterten Lebenszyklus-Supports am 30. November 2020. Adobe empfiehlt Red Hat Enterprise Linux 7 für Upgrades und neue Installationen. Bestehende Installationen können Red Hat Enterprise Linux 6 während der Erweiterten Life Cycle Support-Phase verwenden.</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Nebenversionen, kumulative Updates und wichtige Updates</p> </td>
  </tr>
  <tr>
   <td><p>SUSE® Linux® Enterprise Server 12 (64 Bit)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3 (64-Bit)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td>
  </tr>
  <tr>
   <td>CentOS 7 (64 Bit)<sup> [6]</sup></td>
   <td>A: Unterstützt</td>
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td>
  </tr>
 </tbody>
</table>

#### Virtualisierte Umgebung {#virtualized-environment}

Sie können AEM Forms on JEE auf einem physischen Computer oder in einer virtuellen Umgebung ausführen. Wenn Sie mit AEM Forms in einer virtuellen Umgebung auf Probleme stoßen, versuchen Sie, das Problem auf einer physischen Maschine zu reproduzieren. Wenn das Problem auf dem physischen Computer weiterhin auftritt, wenden Sie sich an den Support der Adobe, um eine Lösung zu erhalten. Wenden Sie sich für Probleme, die Sie nicht auf einem physischen Computer replizieren können, an Ihren Anbieter für virtuelle Umgebungen.

#### Entwicklungsumgebungen {#development-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong>Plattform (Basisversion)</strong></p> </th>
   <th>Unterstützungsebene</th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 64-Bit</p> </td>
   <td>E: Funktionsfähigkeit wird erwartet</td>
   <td><p>Service Pack und wichtige Updates</p> </td>
  </tr>
 </tbody>
</table>

### Ausnahmen für unterstützte Serverplattformen {#exceptions-to-supported-server-platforms}

Beachten Sie die folgenden Ausnahmen, wenn Sie eine Plattform auswählen, auf der Sie AEM Forms on JEE-Server einrichten.

1. AEM Forms on JEE unterstützt IBM® WebSphere® mit MySQL nicht.
1. AEM Forms on JEE unterstützt und JBoss nicht unter SUSE Linux Enterprise Server 12. Nur IBM WebSphere wird auf SUSE Linux Enterprise Server 12 unterstützt.
1. AEM Forms on JEE unterstützt kein anderes JDK mit JBoss® als Oracle Java™ SE.
1. AEM Forms on JEE unterstützt kein anderes JDK mit IBM® WebSphere® als IBM® JDK.
1. CRX-Repository unterstützt Persistenz des Typs TarMK, MongoDB und relationale Datenbanken (RDBMK). Sie können zwischen dem Anwendungsserver und dem CRX-Repository nicht zwei verschiedene Datenbanksysteme haben. In einer AEM Forms on JEE-Umgebung können Sie MongoMK jedoch mit CRX-Repository und einer unterstützten relationalen Datenbank mit Anwendungsserver verwenden.
1. AEM Forms on JEE unterstützt keinen WebSphere-Anwendungsserver unter CentOS.
1. AEM Forms on JEE unterstützt keine rollenbasierte Zugriffssteuerung (RBAC) für JBoss.

Außerdem sollten Sie die folgenden Punkte beachten, wenn Sie die Software für Implementierungen von Adobe AEM Forms on JEE auswählen:

* AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zu der angegebenen Haupt- oder Nebenversion der unterstützten Software. Das Update auf die nächste Haupt- oder Nebenversion wird jedoch nur unterstützt, wenn entsprechend angegeben.
* Clusterbasierte Installationen unterstützen keine TarMK-Persistenz. Weitere Informationen zur unterstützten Persistenz finden Sie unter [Auswählen eines Persistenztyps für eine AEM Forms-Installation](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
* AEM Forms on JEE unterstützt die Software verschiedener Drittanbieter gemäß der [Richtlinie zur Unterstützung der Software von Drittanbietern](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
* AEM Forms on JEE unterstützt Plattformen in Abhängigkeit der Unterstützung durch Drittanbieter. Einige Kombinationen sind durch Drittanbieter möglicherweise nicht zulässig. Beispielsweise haben viele Anbieter ihre Anwendungsserver nicht mit Oracle zertifiziert. Daher unterstützt AEM Forms on JEE diese Kombinationen ebenfalls nicht. Um sicherzugehen, dass Sie die unterstützten Softwareversionen auswählen, sollten Sie auch die Supportmatrix dieser Drittanbieter überprüfen.
* AEM Forms on JEE unterstützt keine TarMK Cold Standby.
* AEM Forms on JEE unterstützt kein vertikales Clustering.
* AEM Forms on JEE unterstützt nicht MySQL-Datenbank in Cluster-Umgbungen.
* Eine Liste der entfernten oder aktualisierten Plattformen finden Sie im Dokument [AEM 6.5 Forms New Feature Summary](../../forms/using/whats-new.md) .

### LDAP-Server (optional) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Oracle Unified Directory (OUD) 11g Release 2</td>
   <td>Service Packs</td>
  </tr>
  <tr>
   <td>Microsoft Active Directory 2016</td>
   <td>Maintenance-Release und Fix Packs</td>
  </tr>
  <tr>
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td>
   <td><p>Feature Packs und Interim Fixes</p> </td>
  </tr>
 </tbody>
</table>

### E-Mail-Server (optional) {#email-servers-optional}

| Produkt |
|---|
| IBM Lotus Domino 9.0 |
| Microsoft Exchange 2013 |
| Microsoft Office 365 |

### Content Manager und zugehörige Connectors {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Produkt<br /> </strong></td>
   <td><strong>Version</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum</td>
   <td>7,3</td>
  </tr>
  <tr>
   <td>IBM Filenet</td>
   <td>5.2</td>
  </tr>
  <tr>
   <td>IBM Filenet</td>
   <td>5,5,2</td>
  </tr>
  <tr>
   <td>IBM Content Manager Server</td>
   <td>8.5 Fixpack 2</td>
  </tr>
  <tr>
   <td>IBM Content Manager Client</td>
   <td>8,5 </td>
  </tr>
  <tr>
   <td>Microsoft Sharepoint</td>
   <td>2016<br /> </td>
  </tr>
 </tbody>
</table>

### Unterstützung für Cordova {#support-for-cordova}

AEM Forms App unterstützt jetzt Apache Cordova. Die folgenden plattformspezifischen Versionen von Cordova werden unterstützt:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### Software-Support für PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt</strong></p> </th>
   <th><p><strong>Unterstützte Formate für die Konvertierung ins PDF-Format </strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 - Klassische </a> Trackingneueste Version</td>
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
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, Bildformate (BMP, GIF, JPEG, JPEG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, JPC, JPC), HTML, HTM, RTF und TXT</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
>Zusätzlich gilt Folgendes:
>
>* Für PDF Generator ist eine 32-Bit-Version von [Acrobat 2017 Classic Track Version 17.011.30078 oder höher](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) erforderlich, um die Konvertierung durchzuführen.
>* PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft Office Professional Plus und andere für die Konvertierung erforderliche Software.
>* PDF Generator unterstützt nicht Microsoft Office 365.
>* PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt.
>* Die Funktionen von OCR PDF, Optimize PDF und Export PDF werden nur unter Windows unterstützt.
>* Eine Version von Acrobat wird im Paket mit AEM Forms bereitgestellt, um die PDF Generator-Funktionen zu aktivieren. Auf diese Version sollte während der während der Geltungsdauer der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur vom Programm aus mit AEM Forms zugegriffen werden. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung entsprechend Ihrer Implementierung ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
   >
   >
* Der PDF Generator-Dienst unterstützt nicht Microsoft Windows 10.
>



### Ausnahmen der Barrierefreiheit {#exceptions-to-accessibility-support}

Die folgenden Untersysteme von AEM Forms sind nicht mit [508](https://www.section508.gov/) kompatibel:

* Benutzeroberfläche für Authoring adaptiver Formulare
* Benutzeroberfläche für Forms Manager Authoring
* Benutzeroberfläche für Correspondence Management Authoring
* Administrator-Benutzeroberfläche (Benutzeroberfläche der Administration Console)

## Systemanforderungen für AEM Forms on JEE {#system-requirements-for-aem-forms-on-jee}

### Mindestanforderungen an die Hardware {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Plattform</td>
   <td>Mindestanforderungen an die Hardware</td>
  </tr>
  <tr>
   <td>Microsoft Windows Server </td>
   <td>Intel® Xeon® E5-2680, 2,4 GHz-Prozessor oder ähnlich<br /> VMWare ESX 5.1 oder höher<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 15 GB temporärer Speicherplatz plus 22GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>SUSE Linux Enterprise Server</td>
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor <br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>Red Hat Enterprise Linux</td>
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor <br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 6 GB temporärer Leertaste plus 22 GB<br /> für AEM Forms on JEE<br /> </td>
  </tr>
  <tr>
   <td>Hardwareanforderungen für kleine Produktionsumgebungen</td>
   <td>
    <ul>
     <li><strong>Intel-gestützte Umgebung </strong>: Intel® Xeon® E5-2680, 2,4 GHz oder höher. Durch Verwenden eines Dual-Core-Prozessors wird die Leistung weiter verbessert</li>
     <li><strong>Speicher: </strong>4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Für zusätzliche Anforderungen siehe:

* [Systemanforderungen für eine AEM Forms on JEE-Bereitstellung auf einem Einzelserver](https://www.adobe.com/go/learn_aemforms_sysreq_single_63)
* [Systemanforderungen für eine Clusterbereitstellung von AEM Forms on JEE](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_63)

## Unterstützte Clients für AEM Forms on JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

<table>
 <tbody>
  <tr>
   <th><p><strong>Plattform</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 (Enterprise, Pro, Basic)</p> <p>32-Bit- oder 64-Bit-Version</p> <p> </p> </td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td>Microsoft® Windows® 2016 Server</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
 </tbody>
</table>

* Erforderlicher Speicherplatz auf der Festplatte: 1,7 GB nur für Workbench, 2,7 GB auf einem einzelnen Laufwerk für eine vollständige Installation von Workbench, Designer und der Assembly mit den Beispielen, 400 MB für temporäre Installationsordner: 200 MB im Ordner „temp“ des Benutzers und 200 MB im temporären Ordner von Windows. Wenn sich diese Speicherorte alle auf einem einzigen Laufwerk befinden, müssen während der Installation 1,5 GB Speicherplatz zur Verfügung stehen. Die Dateien, die in den temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

* Speicher für Ausführung von Workbench : 2 GB RAM
* Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD-Prozessor, 1 GHz
* Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher
* TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms on JEE-Server
* Unter Windows müssen Sie über Administratorrechte verfügen, um Workbench installieren zu können. Wenn Sie die Installation nicht unter einem Administratorkonto durchführen, werden Sie vom Installationsprogramm zur Eingabe der Berechtigungen für ein passendes Konto aufgefordert.

### Designer {#designer}

* Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server oder Microsoft® Windows® 10
* Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
* 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
* 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
* Grafikspeicher - 128 MB GPU (256 MB empfohlen)
* 2,35 GB verfügbarer Festplattenspeicher
* Bildschirmauflösung 1024 x 768 Pixel oder höher
* Beschleuniger für Grafik-Hardware (optional)
* Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
* Administratorberechtigungen für die Installation von Designer.

### Adobe Acrobat und Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat und Adobe Reader (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2017 (Classic)</td>
   <td>Version 17.011.30078 oder neuer<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Die Acrobat DC-Produktfamilie führt zwei Spuren für Acrobat und Reader ein, die im Wesentlichen zwei verschiedene Produkte sind: „Klassik“ und „Fortlaufend“. Weitere Informationen und einen Vergleich der beiden Tracks finden Sie unter [https://www.adobe.com/go/acrobatdctracks.](https://www.adobe.com/go/acrobatdctracks)

### Browser {#browsers}

#### Desktops {#desktops}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützungsebene</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft Edge (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Service Packs und Updates</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Microsoft Firefox ESR</td>
   <td>E: Funktionsfähigkeit wird erwartet</td>
   <td> Alle Updates</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Google Chrome und Firefox unter Mac OS X</td>
   <td>A: Unterstützt<br /> <br /> </td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Apple Safari 11.x</td>
   <td>A: Unterstützt</td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Apple Safari 12.x<br /> <br /> </td>
   <td>A: Unterstützt</td>
   <td>Alle Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Für Desktops gelten die folgenden Browser-bedingten Ausnahmen:
>
>* Die meisten modernen Browser unterstützen keine NPAPI-basierten Plug-Ins mehr. Weitere Informationen zu den Auswirkungen auf AEM Forms-Anwendungen und -Workflows finden Sie unter [Abbruch von NPAPI-Browser-Plug-ins und deren Auswirkungen](https://helpx.adobe.com/de/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html).
>* Safari wird nur unter Mac OS X unterstützt.
>* Workspace unterstützt Safari 5.1 unter Macintosh OS X 10.6 und 10.7 mit Acrobat DC oder höheren Versionen. Weitere Informationen zur Kompatibilität von Safari 5.1 mit Adobe Reader und Acrobat finden Sie unter [https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html](https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html).
>* Administration Console wird in Safari nicht unterstützt.
>* Correspondence Management unterstützt nicht Windows® Internet Explorer 9.0 für AEM 6.1 Forms.
>* Forms Portal unterstützt die JAWS 14.0-Bildschirmlesehilfe-Software in Internet Explorer 11 für einen leichteren Zugriff.
>



#### Mobile Clients {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome on Android™ 4.1.2 und höher</p> </td>
   <td><p>Alle Updates</p> </td>
  </tr>
  <tr>
   <td>Safari unter iOS 11.0 und höher</td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Microsoft Edge<br /> </td>
   <td>Alle Updates<br /> </td>
  </tr>
  <tr>
   <td>Nativer Android-Browser on Android™ 4.4 und höher</td>
   <td>Alle Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Forms Portal wird nur auf einem iPad nur in Safari unterstützt.
>



### AEM Forms-App {#aem-forms-workspace-app}

#### Unterstützung für Mobilgeräte {#mobile-device-support}

Die AEM Forms-App ist für die folgenden Plattformen verfügbar:

| **Plattform** | **Unterstützte Geräte** |
|---|---|
| Apple iOS | Apple iPhone, iPad, iPad Air und iPad mini mit iOS 12 und höher. |
| Google Android | Android 5.1 und höher. Die AEM Forms-App ist für Samsung Galaxy-Tablets (7 und 10 Zoll) und beliebte Smartphones zertifiziert. |
| Microsoft Windows | Microsoft Surface-Geräte, Tablets, Laptops und Desktops mit Microsoft Windows 10-Betriebssystem. |

### Adobe Flash Player {#adobe-flash-player}

<table>
 <tbody>
  <tr>
   <th><p><strong>Flash Player (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Flash Player – neueste Version</p> </td>
   <td><p>Nebenversionen und Updates</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Adobe wird [die Aktualisierung und Verteilung des Flash Players Ende 2020 einstellen](https://theblog.adobe.com/adobe-flash-update/).

### Adobe Document Security Extension for Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

Klicken Sie [hier](https://www.adobe.com/de/products/livecycle/rightsmanagement/extension/downloads.html), um die Systemanforderungen für Adobe Document Security Extension for Microsoft® Office anzuzeigen.

### Ausnahmen der Clientunterstützung {#exceptions-to-client-support}

AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zu der angegebenen Haupt- oder Nebenversion der unterstützten Software. Das Update auf die nächste Haupt- oder Nebenversion wird jedoch nur unterstützt, wenn entsprechend angegeben.

## Supportrichtlinie für Patches von Drittanbietern {#third-party-patch-support-policy}

Die Anforderungen an Drittpartei-Software für AEM Forms on JEE werden im Abschnitt „Systemanforderungen“ der jeweiligen Produktdokumente erläutert. Die gesamte Dokumentation ist unter [https://adobe.com/go/learn_aemforms_documentation_65](https://adobe.com/go/learn_aemforms_documentation_65) verfügbar.

Die für AEM Forms on JEE verwendeten Referenzplattformen von Drittanbietern stellen ein spezifisches Patchlevel für die Infrastruktur von Drittanbietern dar, das während der Entwicklung und Veröffentlichung der jeweiligen Versionen von AEM Forms on JEE aktuell war, und bilden das Mindest-Patchlevel oder Service Pack-Level der Infrastruktur, die von dieser Version von AEM Forms on JEE unterstützt wird.

Adobe unterstützt dringende oder empfohlene Patches von Drittanbietern und geht bei deren Veröffentlichung davon aus, dass Drittanbieter die Abwärtskompatibilität mit den Versionen gewährleisten, die AEM Forms on JEE unterstützt. Adobe unterstützt nur Patches, die nach dem in der Dokumentation von AEM Forms on JEE angegebenen Mindest-Patchlevel veröffentlicht wurden.

In einigen Fällen unterstützt Adobe keine Updates von Drittanbietern, die Hauptfunktionen verändern und dadurch keine vollständige Abwärtskompatibilität gewährleisten. Weitere Informationen zu den unterstützten Updates finden Sie unter [Unterstützte Patch-Definitionen](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) für bestimmte Produkte von Anbietern und die von der Adobe unterstützte Patch-Typen.

Unter gewissen Voraussetzungen, auf die Adobe keinen Einfluss hat, können sich Patches von Drittanbietern, die Abwärtskompatibilität garantieren, möglicherweise negativ auf die Adobe-Produkte oder Kundenumgebungen auswirken. In diesen Fällen empfiehlt Adobe Kunden, die Auswirkungen dringender Drittanbieter-Patches vor ihrer Anwendung in kritischen Systemen zuerst zu prüfen. Adobe wird mit Drittanbietern die entsprechenden geschäftlichen Anstrengungen unternehmen, um solche Probleme zu beheben, entweder durch die üblichen Adobe-Supportprogramme oder, indem Drittanbieter das Problem in ihrem Patch beheben. Dies ist keine Garantie dafür, dass ein neu veröffentlichtes Drittanbieter-Patch, das von Adobe unterstützt wird, wie in der Dokumentation des Anbieters funktioniert oder mit AEM Forms on JEE kompatibel ist.

Adobe behält sich das Recht vor, die von einer Version von AEM Forms on JEE unterstützten Referenzplattformen von Drittanbietern und deren unterstützte Patch-Definitionen jederzeit zu ändern.

Weitere Informationen über Patches von Drittanbietern erhalten Sie auch auf der Adobe Enterprise-Supportseite, indem Sie nach Knowledgebase-Artikeln für Ihr jeweiliges Produkt suchen.

## Revisionsverlauf {#revision-history}

* 09. September 2020
   * Die unterstützte Version von iOS für AEM Forms App wurde in iOS 12 geändert. Die vorherige Version war iOS 11.
