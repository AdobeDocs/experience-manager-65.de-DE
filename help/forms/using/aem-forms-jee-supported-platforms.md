---
title: Unterstützte Plattformen für AEM Forms on JEE
description: Liste der für die Installation von AEM Forms on JEE erforderlichen und unterstützten Infrastrukturkomponenten
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
exl-id: 74d22cf4-56b2-48f5-92d9-928eaa134866
source-git-commit: 3d80ea6a6fbad05afcdd1f41f4b9de70921ab765
workflow-type: tm+mt
source-wordcount: '3685'
ht-degree: 56%

---


# Unterstützte Plattformen für AEM Forms on JEE {#supported-platforms-for-aem-forms-on-jee}

## Unterstützte Plattformen {#supported-platforms}

<div class="preview">

Adobe hat ein [Vollinstallationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) mit AEM 6.5 Forms Service Pack 12 (6.5.12.0) on JEE zusammen mit den Patch-Installationsprogrammen veröffentlicht. Das Vollinstallationsprogramm bietet Unterstützung für neue Plattformen, während das Patch-Installationsprogramm nur Fehlerkorrekturen enthält.

Wenn Sie eine Neuinstallation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms on JEE-Umgebung planen, empfiehlt Adobe die Verwendung des [Vollinstallationsprogramms für AEM 6.5.12.0 Forms on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) vom 03. März 2022 anstelle des AEM 6.5 Forms-Installationsprogramms vom 08. April 2019.

</div>

### Unterstützungsebenen {#support-levels}

AEM Forms on JEE-Server kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungsservern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden.

In diesem Dokument werden die unterstützten Client- und Serverplattformen für AEM Forms on JEE aufgeführt. Adobe bietet mehrere Unterstützungsebenen, sowohl für Adobe empfohlene Konfigurationen als auch für andere Konfigurationen. Das Dokument listet auch andere unterstützte Software und deren Versionen, Ausnahmen, Patch-Definitionen und Richtlinien zur Unterstützung von Software-Patches von Drittanbietern auf.

>[!NOTE]
>
>- Eine vollständige Liste der Ausnahmen für unterstützte Serverplattformen finden Sie unter [Ausnahmen für unterstützte Serverplattformen](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p).
>- AEM Forms on JEE unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.

### Empfohlene Konfigurationen {#recommendedconfigurations}

Adobe empfiehlt diese Konfigurationen und bietet vollständige oder eingeschränkte Unterstützung im Rahmen des Standard-Software-Wartungsvertrags:

<table>
 <tbody>
  <tr>
   <th>Unterstützungsebene</th>
   <th>Beschreibung</th>
  </tr>
  <tr>
   <td>A: Unterstützt<br /> </td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt.</td>
  </tr>
  <tr>
   <td>R: Eingeschränkte Unterstützung </td>
   <td>Adobe unterstützt diese Konfiguration vollständig, wenn bestimmte Voraussetzungen erfüllt sind. Wenden Sie sich an den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren und um Support anzufordern.</td>
  </tr>
  <tr>
   <td>L: Eingeschränkte Unterstützung</td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration, wenn bestimmte Voraussetzungen erfüllt sind. Nicht alle Funktionen sind in der Konfiguration verfügbar. Wenden Sie sich an den Support von Adobe Enterprise, um mehr über die Voraussetzungen zu erfahren und um Support anzufordern.<br /> </td>
  </tr>
 </tbody>
</table>

### Nicht unterstützte Konfigurationen {#unsupported-configurations}

| Unterstützungsebene | Beschreibung |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| E: Funktionsfähigkeit wird erwartet | Es wird erwartet, dass die Konfiguration funktioniert, und es wird nichts Gegenteiliges berichtet. |
| Z: Nicht unterstützt | Die Konfiguration wird nicht unterstützt. Adobe macht keine Angaben dazu, ob die Konfiguration funktioniert, und unterstützt sie nicht. |

>[!NOTE]
>
>Um Kunden von AEM Forms dabei zu helfen, die Nutzungskosten zu reduzieren, die Bereitstellungsarchitektur zu vereinfachen und den Entwicklungs-Stack zu modernisieren, wird die Enterprise-Plattform Adobe Experience Manager von Anwendungsserver-basierten Bereitstellungen auf eigenständige OSGi-basierte Bereitstellungen umgestellt. Adobe unterstützt weiterhin den JEE-Stack von AEM Forms mit einer reduzierten Matrix von Infrastrukturkomponenten.
>
>Ab Version 6.5 werden Infrastrukturkomponenten mit der geringsten Nutzung unter Adobe-Kunden nicht mehr wie folgt unterstützt:
>
>- IBM® DB2®-Datenbank
- IBM® AIX® und Sun Solaris™ Betriebssysteme
>
Bei neuen Installationen wird empfohlen, AEM Forms auf dem modernen OSGi-Stack bereitzustellen, um die neuesten Innovationen rund um das responsive adaptive Forms für mobile, interaktive mehrkanalige Kommunikation und Backend-Datenintegrationen mithilfe des Formulardatenmodells zu verwenden.
>
Adobe erkennt, dass bestehende Benutzer AEM Forms on JEE Stack weiterhin bereitstellen müssen. In solchen Fällen erfordert Adobe die Bereitstellung von AEM Forms JEE auf unterstützter Infrastruktur, wie in dieser Dokumentation beschrieben. Wenn Sie ein Upgrade auf AEM 6.5 Forms durchführen und eine nicht unterstützte Plattform aus der vorherigen Version von AEM Forms verwenden, können Sie sich an den Adobe Support wenden, um Hilfe beim Upgrade auf eine unterstützte Plattform zu erhalten.

### Java™ Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms erfordert eine Java™ Virtual Machine, die von der Java™ Development Kit-Distribution (JDK) bereitgestellt wird. Adobe Experience Manager funktioniert mit den folgenden Versionen der Java™ Virtual Machine:

<table>
 <tbody>
  <tr>
   <th><p><strong>Plattform</strong></p> </th>
   <th><p><strong>Unterstützungsebene</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr> 
   <td><p>Oracle Java™ SE 11 (64 Bit) <sup> [8] </sup> </p>  </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Nebenversionen und Updates </p> </td>
  </tr>
  <tr>
   <td>Azul Zulu OpenJDK 11 - 64 Bit</td>
   <td>Z: Nicht unterstützt</td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Azul Zulu OpenJDK 8 - 64 Bit</td>
   <td>Z: Nicht unterstützt</td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Oracle Java™ SE 8 (64 Bit)</td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (Build 2.9, JRE 1.8.0) IBM® JDK SR6-FP26<br /> </td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
  <tr>
   <td>IBM® JAVA1.8.0_291(Build 8.0.6.30)<br /> </td>
   <td>A: Unterstützt</td>
   <td>Nebenversionen und Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
- Verfolgen Sie die Sicherheitsbulletins des Java™-Anbieters, um die Sicherheit der Produktionsumgebungen sicherzustellen und die neuesten Java™-Aktualisierungen zu installieren.
- AEM Forms on JEE unterstützt nur 64-Bit-JVMs in Produktionsumgebungen.

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
   <td><p> MongoDB Enterprise 4.0 (Veraltet) </p> </td>
   <td><p>Repository-Mikro-Kernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>MongoDB Enterprise 4.2 </p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>Oracle-Datenbank 12c Version 2 (12.2.0.1.0) (Veraltet)</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
   <tr>
   <td>Oracle-Datenbank 19c (Standard, Real Application Clusters (RAC) und Enterprise-Editionen) </td>
   <td>Repository Microkernal </td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2016 (überholt)</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2019</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td>IBM® DB2® 11.1 (überholt)</td>
   <td>Repository-Mikro-Kernel</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
  <tr>
   <td>MySQL 5.7.35 (veraltet) </td>
   <td>-</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
  <tr>
   <td>MySQL 8.0.27</td>
   <td>-</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
 </tbody>
</table>

- IBM® DB2® wird bei Neuinstallationen nicht unterstützt. Es wird nur für Bestandskunden unterstützt, die auf AEM 6.5 Forms aktualisieren.
- MongoDB ist eine Drittanbietersoftware und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie unter [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
- Um Ihre AEM optimal nutzen zu können, empfiehlt Adobe die Lizenzierung der MongoDB Enterprise-Version, um professionellen Support zu erhalten.
- Die Adobe-Kundenunterstützung unterstützt Sie bei bestimmten Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen. Weitere Informationen finden Sie auf der Seite für [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
- „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Es wird empfohlen, AEM mit dem Netzwerk-/Remote-Dateisystem zu laden.
- Nur MongoDB Storage Engine WiredTiger wird unterstützt.
- MongoDB Sharding wird in AEM nicht unterstützt.
- AEM Forms on JEE unterstützt keine MySQL für RDBMK-Persistenz.
- Das Document Security-Modul verwendet kein Content Repository. Dies bedeutet, dass Sie, wenn Sie nur Document Security verwenden und nicht HTML Workspace, HTML5-Formulare oder adaptive Formulare verwenden möchten, Content Repository nicht installieren.
- AEM Forms auf JEE unterstützt nicht die Verwendung von MySQL für das persistente AEM Repository (CRX-Repository).

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
   <td>Microsoft® SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-Treiber 6.2.1.0 (veraltet) <br /> </p> <p>sqljdbc6.jar</p> </td>
   <td><p>AEM Forms on JEE-Installation im Paket enthalten.</p> </td>
  </tr>
    <tr>
   <td>Microsoft® SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-Treiber 6.2.2.0 <br /> </p> <p>sqljdbc6.jar</p> </td>
   <td><p>AEM Forms on JEE-Installation im Paket enthalten.</p> </td>
  </tr>
  <tr>
   <td>Microsoft® SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-Treiber 8.2.2<br /> </p> <p>sqljdbc8.jar</p> </td>
   <td><p>Laden Sie von der Microsoft®-Website herunter.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>Oracle Database 19.3.0.0.0 JDBC-Treiber</p> <p>ojdbc8.jar (Version 19.3.0.0.0)<br /> </p> </td>
   <td><p>Download von <a href="https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html">Oracle-Website</a>.</p> </td>
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
   <td>IBM® WebSphere® Application Server 9.0.0.10 <sup>[1] [4]</sup><br /> </td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.1.4 <sup>[2] [3] [7]</sup> (Veraltet) </p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Patches und kumulative Patches  für die unterstützte EAP-Version</p> </td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application-Plattform (EAP) 7.4 <sup>[2] [3] [7]</sup> </p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Patches und kumulative Patches  für die unterstützte EAP-Version</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
IBM® WebSphere®-Cluster werden nur in Network Deployment-Editionen unterstützt.

### Serverbetriebssysteme {#server-operating-systems}

#### Produktionsumgebungen {#production-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong> Plattform</strong></p> </th>
   <th><p><strong>Unterstützungsebene</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
   <tr>
   <td>Microsoft® Windows Server 2019 (64 Bit)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td>Ubuntu 20.04</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td> Microsoft® Windows Server 2016 (64 Bit) (veraltet)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64 Bit)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Nebenversionen, kumulative Updates und wichtige Updates</p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 7 (Kernel 3.x) (64 Bit) (veraltet)</td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Nebenversionen, kumulative Updates und wichtige Updates</p> </td>
  </tr>
  <tr>
   <td><p>SUSE® Linux® Enterprise Server 12 (64-Bit)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3  (64-Bit)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td>
  </tr>
  <tr>
   <td>CentOS 7 (64-Bit)<sup> [6]</sup></td>
   <td>A: Unterstützt</td>
   <td>Service Packs, kumulative Patches und wichtige Sicherheitsupdates</td>
  </tr>
 </tbody>
</table>

#### Virtualisierte Umgebung {#virtualized-environment}

Sie können AEM Forms on JEE auf einem physischen Computer oder in einer virtuellen Umgebung ausführen. Wenn Sie jedoch auf ein Problem mit AEM Forms in einer virtuellen Umgebung stoßen, versuchen Sie, das Problem auf einem physischen Computer zu replizieren. Wenn das Problem auf dem physischen Computer weiterhin besteht, wenden Sie sich in Hinblick auf Unterstützung an den Adobe-Support. Bei Problemen, die Sie auf einem physischen Computer nicht replizieren können, wenden Sie sich an den Verkäufer Ihrer virtuellen Umgebung.

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

Beachten Sie beim Auswählen einer Plattform für die Einrichtung Ihres AEM Forms on JEE-Servers die folgenden Ausnahmen.

1. AEM Forms on JEE unterstützt IBM® WebSphere® mit MySQL nicht.
1. AEM Forms on JEE unterstützt und JBoss® nicht unter SUSE® Linux® Enterprise Server 12. Nur IBM® WebSphere® wird auf SUSE® Linux® Enterprise Server 12 unterstützt.
1. AEM Forms on JEE unterstützt mit JBoss® kein anderes JDK als Oracle Java™ SE.
1. AEM Forms on JEE unterstützt mit IBM® WebSphere® kein anderes JDK als IBM® JDK.
1. CRX-Repository unterstützt Persistenz des Typs TarMK, MongoDB und relationale Datenbanken (RDBMK). Sie dürfen nicht zwei verschiedene Datenbanksysteme zwischen dem Anwendungsserver und dem CRX-Repository haben. In einer AEM Forms on JEE-Umgebung können Sie MongoMK jedoch mit dem CRX-Repository und einer unterstützten relationalen Datenbank mit Anwendungsserver verwenden.
1. AEM Forms on JEE unterstützt WebSphere®-Anwendungsserver unter CentOS nicht.
1. AEM Forms on JEE unterstützt keine rollenbasierte JBoss®-Zugriffskontrolle (RBAC).
1. AEM Forms on JEE unterstützt nur Oracle Java™ SE 11 (64 Bit) SDK für Anwendungsserver JBoss® EAP 7.4.

Beachten Sie außerdem die folgenden Punkte bei der Auswahl der Software für Adobe AEM Forms on JEE-Implementierungen:

- AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zur angegebenen Haupt- und Nebenversion der unterstützten Software. Die Aktualisierung auf die nächste Haupt- oder Nebenversion wird jedoch nicht unterstützt, sofern nichts anderes angegeben ist.
- Clusterbasierte Installationen unterstützen keine TarMK-Persistenz. Informationen zur unterstützten Persistenz finden Sie unter [Persistenztyp für eine AEM Forms-Installation auswählen](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- AEM Forms on JEE unterstützt verschiedene Software von Drittanbietern gemäß der Adobe [Richtlinie zur Unterstützung von Software von Drittanbietern](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
- AEM Forms on JEE-Unterstützungsplattformen gemäß der Unterstützung durch Drittanbieter. Einige Kombinationen sind möglicherweise von Drittanbietern nicht zulässig. Zum Beispiel haben viele Anbieter ihre Anwendungsserver nicht mit Oracle zertifiziert. Daher unterstützt AEM Forms on JEE diese Kombinationen auch nicht. Um sicherzugehen, dass Sie die unterstützten Softwareversionen auswählen, sollten Sie auch die Supportmatrix dieser Drittanbieter überprüfen.
- AEM Forms on JEE unterstützt keine TarMK Cold Standby.
- AEM Forms on JEE unterstützt kein vertikales Clustering.
- AEM Forms on JEE unterstützt die MySQL-Datenbank in einer Cluster-Umgebung nicht.
- Eine Liste der entfernten bzw. der aktualisierten Plattformen finden Sie in dem Dokument [AEM 6.5 Forms - Übersicht über die neuen Funktionen](../../forms/using/whats-new.md).

### LDAP-Server (optional) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2016</td>
   <td>Maintenance Release und Fix Packs</td>
  </tr>
  <tr>
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td>
   <td><p>Feature Packs und Interim Fixes</p> </td>
  </tr>
 </tbody>
</table>

### E-Mail-Server (optional) {#email-servers-optional}

| Produkt |
| ----------------------- |
| Microsoft® Exchange 2013 |
| Microsoft® Office 365 |

### Content Manager und entsprechende Connectoren {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Produkt<br /> </strong></td>
   <td><strong>Version</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum®</td>
   <td>7.3</td>
  </tr>
  <tr>
   <td>IBM® FileNet</td>
   <td>5.5.2</td>
  </tr>
  <tr>
   <td>IBM® Content Manager Server (nicht mehr unterstützt) </td>
   <td>8.5 Fixpack 2</td>
  </tr>
  <tr>
   <td> IBM® Content Manager Client (nicht mehr unterstützt)</td>
   <td>8.5 </td>
  </tr>
  <tr>
   <td>Microsoft® Sharepoint </td>
   <td>2016 (veraltet)<br /> </td>
  </tr>
  <tr>
   <td>Microsoft® Sharepoint </td>
   <td>2019<br /> </td>
  </tr>
 </tbody>
</table>

### Unterstützung für Cordova {#support-for-cordova}

AEM Forms App unterstützt jetzt Apache Cordova. Die folgenden plattformspezifischen Versionen von Cordova werden unterstützt:

- Apache Cordova 6.4.0
- Cordova iOS 4.3.0
- Cordova Android™ 6.0.0
- Cordova Windows 4.4.3

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
PDF Generator unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.
>
Zusätzlich gilt Folgendes:
>
- PDF Generator erfordert die 32-Bit-Version der [klassischen Acrobat 2020-Version 20.004.30006](https://helpx.adobe.com/de/acrobat/release-note/release-notes-acrobat-reader.html) oder der Acrobat 2017-Version 17.011.30078, um die Konvertierung durchzuführen.
- PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft® Office Professional Plus und andere für die Konvertierung erforderliche Software.
- PDF Generator unterstützt nicht Microsoft® Office 365.
- PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt®.
- Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
- Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur programmatisch mit AEM Forms zugänglich sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung je nach Ihrer Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html)).
>
- Der PDF Generator-Service unterstützt nicht Microsoft® Windows 10.
- PDF Generator kann keine Dateien mit Microsoft® Visio 2019 konvertieren. Sie können weiterhin Microsoft® Visio 2016 verwenden, um .VSD- und .VSDX-Dateien zu konvertieren.
- PDF Generator kann keine Dateien mit Microsoft® Project 2019 konvertieren. Sie können Microsoft® Project 2016 weiterhin verwenden, um .MPP-Dateien zu konvertieren.
>

### Ausnahmen der Barrierefreiheit {#exceptions-to-accessibility-support}

Die folgenden Teilsysteme von AEM Forms sind nicht [508](https://www.section508.gov/) kompatibel:

- Adaptive Forms Authoring-Benutzeroberfläche
- Forms Manager Authoring-Benutzeroberfläche
- Benutzeroberfläche für Correspondence Management Authoring
- Administrator-Benutzeroberfläche (Benutzeroberfläche der Administration Console)

## Systemanforderungen für AEM Forms on JEE {#system-requirements-for-aem-forms-on-jee}

### Mindestanforderungen an die Hardware {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Plattform</td>
   <td>Mindestanforderungen an die Hardware</td>
  </tr>
  <tr>
   <td>Microsoft® Windows Server</td>
   <td>Intel Xeon® E5-2680, 2,4 GHz-Prozessor oder gleichwertiger Prozessor<br /> VMWare ESX 5.1 oder höher<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 15 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>SUSE® Linux® Enterprise Server</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor<br /> AWS m3.medium (3 ECU)<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>Red Hat® Enterprise Linux®</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor<br /> AWS m3.medium (3 ECU)<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE<br /> </td>
  </tr>
  <tr>
   <td>Hardwareanforderungen für eine kleine Produktionsumgebung</td>
   <td>
    <ul>
     <li><strong>Intel®-gestützte Umgebung</strong>: Intel Xeon® E5-2680, 2,4 GHz oder höher. Durch die Verwendung eines Dualcore-Prozessors wird die Leistung weiter verbessert</li>
     <li><strong>Speicher: </strong>4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Für zusätzliche Anforderungen siehe:

- [Systemanforderungen für eine Bereitstellung von AEM Forms on JEE auf einem Einzelserver](https://www.adobe.com/go/learn_aemforms_sysreq_single_65_de)
- [Systemanforderungen für eine Clusterbereitstellung von AEM Forms on JEE](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_65_de)

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

- Erforderlicher Speicherplatz auf der Festplatte: 1,7 GB nur für Workbench, 2,7 GB auf einem einzelnen Laufwerk für eine vollständige Installation von Workbench, Designer und der Assembly mit den Beispielen, 400 MB für temporäre Installationsordner: 200 MB im Ordner „temp“ des Benutzers und 200 MB im temporären Ordner von Windows. Wenn sich alle diese Speicherorte auf einem einzigen Laufwerk befinden, muss während der Installation 1,5 GB Speicherplatz verfügbar sein. Die Dateien, die in die temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

- Speicher für Ausführung von Workbench: 2 GB RAM
- Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD®-Prozessor, 1 GHz
- Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher
- TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms on JEE-Server
- Sie müssen über Administratorrechte verfügen, um Workbench unter Windows installieren zu können. Wenn Sie die Installation mit einem Konto ohne Adminrechte durchführen, werden Sie vom Installationsprogramm zur Eingabe der Anmeldeinformationen für ein entsprechendes Konto aufgefordert.

### Designer {#designer}

- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server oder Microsoft® Windows® 10
- Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
- 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
- 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
- Grafikspeicher – 128 MB GPU (256 MB empfohlen)
- 2,35 GB verfügbarer Festplattenspeicher
- Bildschirmauflösung 1024 x 768 Pixel oder höher
- Beschleuniger für Video-Hardware (optional)
- Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC.
- Administratorrechte für die Installation von Designer.

### Adobe Acrobat und Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat und Adobe Reader (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2020 (Classic)</td>
   <td>Version 20.004.30006 oder neuer<br /> </td>
  </tr>
  <tr>
   <td>Acrobat 2017 (Klassischer Modus) (nicht mehr unterstützt)</td>
   <td>Version 17.011.30078 oder neuer<br /> </td>
  </tr>

</tbody>
</table>

>[!NOTE]
>
Die Acrobat DC-Produktfamilie führt zwei Spuren für Acrobat und Reader ein, die unterschiedliche Produkte sind: &quot;Classic&quot;und &quot;Kontinuierlich&quot;. Weitere Informationen und einen Vergleich der beiden Tracks finden Sie unter [https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html).

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
   <td><p>Microsoft® Edge (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td><p>Service Packs und Updates</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Mozilla Firefox ESR</td>
   <td>E: Funktionsfähigkeit wird erwartet</td>
   <td> Alle Updates</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Unterstützt</p> </td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Apple Safari unter macOS</td>
   <td>A: Unterstützt</td>
   <td>Alle Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
Einige browserbezogene Ausnahmen für Desktops lauten wie folgt:
>
- Safari wird nur unter Mac OS X unterstützt.
- Workspace unterstützt Safari 5.1 unter Macintosh OS X 10.6 und 10.7 mit Acrobat DC oder höheren Versionen. Weitere Informationen zur Kompatibilität von Safari 5.1 mit Adobe Acrobat Reader finden Sie unter [https://helpx.adobe.com/de/x-productkb/multi/safari-5-1-incompatible-reader.html](https://helpx.adobe.com/de/x-productkb/multi/safari-5-1-incompatible-reader.html).
- Administration Console wird in Safari nicht unterstützt.
- Correspondence Management unterstützt nicht Windows® Internet Explorer 9.0 für AEM 6.1-Formulare.
- Forms Portal unterstützt die Barrierefreiheit von JAWS 14.0-Bildschirmlesehilfen in Internet Explorer 11.

#### Mobile Clients {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome unter Android™ 4.1.2 und höher</p> </td>
   <td><p>Alle Updates</p> </td>
  </tr>
  <tr>
   <td>Safari unter iOS 15.1 und höher</td>
   <td>Alle Updates</td>
  </tr>
  <tr>
   <td>Microsoft® Edge<br /> </td>
   <td>Alle Updates<br /> </td>
  </tr>
  <tr>
   <td>Nativer Android™-Browser unter Android™ 4.4 und höher</td>
   <td>Alle Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
- Forms Portal wird nur auf einem iPad nur in Safari unterstützt.

### AEM Forms-App {#aem-forms-workspace-app}

#### Mobilgeräteunterstützung {#mobile-device-support}

Das AEM Forms-Programm ist auf den folgenden Plattformen verfügbar:

| **Plattform** | **Unterstützte Geräte** |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Apple iOS | Apple iPhone, iPad, iPad Air und iPad mini mit iOS 15.1 und höher. |
| Google Android™ | Android™ 5.1 und höher. Die Mobile App von AEM Forms ist für Samsung Galaxy-Tablets (7 und 10 Zoll) und beliebte Smartphone-Modelle zertifiziert. |
| Microsoft® Windows | Microsoft® Surface-Geräte, Tablets, Laptops und Desktops mit dem Betriebssystem Microsoft® Windows 10. |

### Adobe Document Security Extension for Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}

Klicken Sie [hier](https://www.adobe.com/de/products/livecycle/rightsmanagement/extension/downloads.html), um die Systemanforderungen für Adobe Document Security Extension for Microsoft® Office anzuzeigen.

### Ausnahmen der Clientunterstützung {#exceptions-to-client-support}

AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zur angegebenen Haupt- und Nebenversion der unterstützten Software. Die Aktualisierung auf die nächste Haupt- oder Nebenversion wird jedoch nicht unterstützt, sofern nichts anderes angegeben ist.

## Richtlinie zur Unterstützung von Patches von Drittanbietern {#third-party-patch-support-policy}

Die Anforderungen an Drittpartei-Software für AEM Forms on JEE werden im Abschnitt „Systemanforderungen“ der jeweiligen Produktdokumente erläutert. Auf alle Dokumentationen zugreifen über [https://adobe.com/go/learn_aemforms_documentation_65](https://adobe.com/go/learn_aemforms_documentation_65_de) .

Die Referenzplattformen von AEM Forms on JEE von Drittanbietern geben den spezifischen Patch-Level der Infrastruktur von Drittanbietern an, der während der Entwicklung und Veröffentlichung von AEM Forms on JEE aktuell war, sowie den minimalen Patch-/Service Pack-Level der Infrastruktur, die von dieser Version von AEM Forms on JEE unterstützt wird.

Adobe unterstützt dringende oder empfohlene Patches von Drittanbietern bei deren Veröffentlichung, vorausgesetzt, dass Drittanbieter die Abwärtskompatibilität mit den von AEM Forms on JEE unterstützten Versionen sicherstellen. Adobe unterstützt nur Patches, die nach dem in der AEM Forms on JEE-Dokumentation angegebenen Mindest-Patch-Level veröffentlicht wurden.

Manchmal unterstützt Adobe keine Updates von Drittanbietern, die die Hauptfunktionalität ändern und daher keine vollständige Abwärtskompatibilität unterstützen. Einzelheiten zu den unterstützten Updates finden Sie unter [Unterstützte Patch-Definitionen](https://helpx.adobe.com/de/aem-forms/aem-forms-third-party-software-patch.html) für bestimmte Herstellerprodukte und die von Adobe unterstützten Arten von Patches.

Unter Umständen, die außerhalb der Kontrolle von Adobe liegen, können Patches von Drittanbietern, die Abwärtskompatibilität beanspruchen, negative Auswirkungen auf die Produkte von Adobe oder die Kundenumgebung haben. In solchen Fällen empfiehlt die Adobe, dass die Kunden die Auswirkungen eines dringenden Patches von einem Dritten bewerten, bevor diese auf kritische Systeme angewendet werden. Adobe arbeitet mit Dritten zusammen, indem sie vernünftige geschäftliche Anstrengungen unternimmt, um solche Probleme zu lösen, entweder durch reguläre Unterstützungsprogramme für Adoben oder durch Dritte, die das Problem in ihrem Patch beheben. Dies garantiert nicht, dass ein neu veröffentlichtes Drittanbieter-Patch, das von Adobe unterstützt wird, wie in der Dokumentation des Anbieters oder mit AEM Forms on JEE funktioniert.

Adobe behält sich das Recht vor, die von einer AEM Forms on JEE-Version unterstützten Referenzplattformen von Drittanbietern und deren unterstützte Patch-Definitionen jederzeit zu ändern.

Weitere Informationen zu Patches von Drittanbietern finden Sie auch auf der Adobe Enterprise Support-Site in Knowledgebase-Artikeln, die sich auf Ihr Produkt beziehen.

## Plattformaktualisierungen {#platform-updates}

Die folgenden Plattformen werden mit der AEM Forms-Version 6.5.13.0 vom 2. Juni 2022 als veraltet gekennzeichnet:

- Microsoft® SharePoint 2016

Die folgenden Plattformen werden mit der AEM Forms-Version 6.5.12.0 vom 3. März 2022 als veraltet gekennzeichnet:

- MongoDB Enterprise 4.0
- IBM® DB2® 11.1
- Oracle-Datenbank 12c Version 2
- MySQL 5.7.35
- Microsoft® SQL Server JDBC-Treiber 6.2.1.0
- JBoss® Enterprise Application-Plattform (EAP) 7.1.4
- IBM® Content Manager Server 8.5 Fix Pack 2
- IBM® Content Manager Client 8.5
- Microsoft® SQL Server 2016

Die folgenden Plattformen werden mit der AEM Forms-Version 6.5.10.0 vom 7. September 2021 als veraltet gekennzeichnet:

- Adobe Acrobat 2017 – [Die grundlegende Unterstützung für Adobe Acrobat 2017 endet am 6. Juni 2022](https://helpx.adobe.com/de/support/programs/eol-matrix.html).
- Microsoft® Windows Server 2016 (64 Bit)
- Red Hat® Enterprise Linux® 7 (Kernel 3.x) (64 Bit)
- Microsoft® Office 2016
- OpenOffice 4.1.2

>[!NOTE]
>
Die Plattformen, die mit AEM Forms 6.5.12.0 und 6.5.10.0 als [veraltet gekennzeichnet werden, werden bis zur Freigabe von AEM Forms 6.5 Service Pack 18 (6.5.18.0) weiterhin unterstützt](https://helpx.adobe.com/de/support/programs/eol-matrix.html).

## Revisionsverlauf {#revision-history}

- 01. September 2022

   - Unterstützung für Oracle Java™ SE 11 (64 Bit) SDK für Anwendungsserver JBoss® EAP 7.4 hinzugefügt.

- 03. März 2022

   - Die Unterstützung für Folgendes wurde entfernt:
      - IBM® J9 Virtual Machine (Build 2.8, JRE 1.8.0)
      - Oracle-Datenbank 12c Version 1
      - Oracle Database 18c
      - Oracle Unified Directory (OUD) 11g Version 2
      - IBM® Lotus Domino 9.0
      - IBM® FileNet 5.2
      - Adobe Flash Player

- 10. Oktober 2021

   - Die unterstützte Version von iOS für die Mobile App von AEM Forms wurde in iOS 15.1 geändert. Die vorherige Version war iOS 12.

- 07. September 2021
   - **Plattformaktualisierungen**: [!DNL Adobe Experience Manager Forms] on JEE unterstützt nun die folgenden Plattformen:
      - [!DNL Adobe Acrobat 2020]
      - [!DNL Ubuntu 20.04]
      - [!DNL Open Office 4.1.10]
      - [!DNL Microsoft® Office 2019]
      - [!DNL Microsoft® Windows Server 2019]
      - [!DNL RHEL8]

- 03. Dezember 2020
   - Mit AEM Forms 6.5.7.0 oder höher wurde Unterstützung für die folgende Plattform hinzugefügt:
      - [!DNL Microsoft® SQL Server 2019]

- 09. September 2020

   - Die unterstützte Version von iOS für die Mobile App von AEM Forms wurde in iOS 12 geändert. Die vorherige Version war iOS 11.

