---
title: Unterstützte Plattformen für AEM Forms on JEE
description: Liste der Infrastrukturkomponenten, die für die Installation von AEM Forms on JEE erforderlich sind und unterstützt werden
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
exl-id: 74d22cf4-56b2-48f5-92d9-928eaa134866
solution: Experience Manager, Experience Manager Forms
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '4010'
ht-degree: 96%

---


# Unterstützte Plattformen für AEM Forms on JEE {#supported-platforms-for-aem-forms-on-jee}

## Unterstützte Plattformen {#supported-platforms}

<div class="preview">

Adobe hat ein [Vollinstallationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) mit AEM 6.5 Forms Service Pack 18 (6.5.18.0) on JEE zusammen mit den Patch-Installationsprogrammen veröffentlicht. Das vollständige Installationsprogramm bietet Unterstützung für neue Plattformen, während das Patch-Installationsprogramm nur Fehlerkorrekturen enthält.
Wenn Sie eine Neuinstallation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms on JEE-Umgebung planen, empfiehlt Adobe die Verwendung des [Vollinstallationsprogramms für AEM 6.5.18.0 Forms on JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) vom 31. August 2023 anstelle des AEM 6.5 Forms-Installationsprogramms vom 08. April 2019 oder des AEM 6.5.12 Forms-Installationsprogramms vom 03. März 2022.

</div>

### Unterstützungsebenen {#support-levels}

AEM Forms on JEE-Server kann mit einer beliebigen Kombination von unterstützten Betriebssystemen, Anwendungs-Servern, Datenbanken, Datenbanktreibern, JDK-, LDAP-Servern und E-Mail-Servern eingerichtet werden.

In diesem Dokument werden die unterstützten Client- und Server-Plattformen für AEM Forms on JEE aufgeführt. Adobe bietet verschiedene Unterstützungsebenen an, die für von Adobe empfohlene und andere Konfigurationen gelten. In diesem Dokument werden auch andere unterstützte Software und deren Versionen, Ausnahmen, Patch-Definitionen sowie die Richtlinien zur Unterstützung für Software-Patches von Drittanbietern aufgeführt.

>[!NOTE]
>
>- Eine vollständige Liste der Ausnahmen für unterstütze Server-Plattformen finden Sie unter [Ausnahmen für unterstützte Server-Plattformen](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p).
>- AEM Forms on JEE unterstützt nur englische, französische, deutsche und japanische Versionen der unterstützten Betriebssysteme und Anwendungen.

### Upgrade- und Support-Richtlinie

#### Vollständiges Installationsprogramm

- **Upgrade-Unterstützung für vollständige Installationsprogramme**: Ein vollständiges Installationsprogramm wird mit jeder sechsten AEM Service Pack-Version veröffentlicht. Beispielsweise wurde ein vollständiges Installationsprogramm mit den SP-Versionen 6.5.12.0 und 6.5.18.0 veröffentlicht. AEM Forms ermöglicht direkte Upgrades ausschließlich über die letzten beiden vollständigen Installationsprogramme. Beispielsweise ermöglicht AEM Forms direkte Upgrades auf Version 6.5.18.0 nur von den letzten beiden vollständigen Installationsprogrammen, nämlich 6.5.12.0 und 6.5.6.0. Wenn Sie ein Upgrade von einem früheren Upgrade benötigen, können Sie ein Multihop-Upgrade verwenden, um zunächst zu einer unterstützten Version des vollständigen Installationsprogramms und dann zur neuesten Version zu wechseln. 

- **Einstellung und Entfernung**: Die Plattformunterstützung wird mit jeder Version des vollständigen Installationsprogramms aktualisiert. Jede Software, die in einer Version des vollständigen Installationsprogramms in der Plattformmatrix als veraltet gekennzeichnet wurde, kann in einer nachfolgenden Version des vollständigen Installationsprogramms aus der Matrix der unterstützten Plattformen entfernt werden, was das Ende der Unterstützung für die Software angibt.

#### Service Packs

- **Service Pack-Abdeckung**: Adobe bietet technischen Support für AEM Forms-Umgebungen mit den sechs neuesten Service Packs. Wenn Ihre aktuelle Version vor den sechs letzten Service Packs liegt, empfiehlt Adobe dringend ein Upgrade auf die neueste Version, um optimale Leistung, Sicherheit und kontinuierlichen Support zu erhalten.

- **Richtlinien für Patch-Installationsprogramme**: Während die Patch-Installationsprogramme zur Aktualisierung verwendet werden, ist es wichtig zu überprüfen, ob die zugrunde liegende Version des vollständigen Installationsprogramms nicht um mehr als zwei Versionen zurückliegt. Stellen Sie beispielsweise während der Installation von Service Pack 6.5.19.0 sicher, dass die zugrunde liegende Version des vollständigen Installationsprogramms 6.5.18.0 oder 6.5.12.0 ist.

- **Patch-Upgrade-Support**: Sie können weiterhin auf das neueste Service Pack aktualisieren, bis Sie auch auf die neuesten unterstützten Plattformen aktualisieren. Beispielsweise ist ein Upgrade von Service Pack 6.5.12.0 auf 6.5.19.0 möglich, vorausgesetzt, Sie wechseln zu einer Plattformkombination, die für 6.5.19.0 unterstützt wird.

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
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration. Diese Konfiguration wird über den Qualitätssicherungsvorgang von Adobe abgedeckt.</td>
  </tr>
  <tr>
   <td>R: Eingeschränkte Unterstützung </td>
   <td>Adobe bietet vollständige Unterstützung für diese Konfiguration, sofern bestimmte Voraussetzungen erfüllt sind. Kontaktieren Sie den Unternehmens-Support von Adobe, um mehr über die Voraussetzungen zu erfahren und stellen Sie eine Supportanfrage.</td>
  </tr>
  <tr>
   <td>L: Begrenzte Unterstützung</td>
   <td>Adobe bietet vollständige Unterstützung und Wartung für diese Konfiguration, sofern bestimmte Voraussetzungen erfüllt sind. In der Konfiguration sind nicht alle Funktionen verfügbar. Kontaktieren Sie den Unternehmens-Support von Adobe, um mehr über die Voraussetzungen zu erfahren, und stellen Sie eine Supportanfrage.<br /> </td>
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
>Um Kunden und Kundinnen von AEM Forms dabei zu helfen, die Nutzungskosten zu reduzieren, die Bereitstellungsarchitektur zu vereinfachen und den Entwicklungs-Stack zu modernisieren, wird die Enterprise-Plattform Adobe Experience Manager von Anwendungsserver-basierten Bereitstellungen auf eigenständige OSGi-basierte Bereitstellungen umgestellt. Adobe unterstützt weiterhin den JEE-Stack von AEM Forms mit einer reduzierten Matrix von Infrastrukturkomponenten.
>
>Mit der Veröffentlichung von 6.5 werden die folgenden Infrastrukturkomponenten, die von Adobe-Kundinnen und -Kunden am wenigsten genutzt werden, nicht mehr unterstützt:
>
>- IBM® DB2®-Datenbank
>- IBM® AIX®- und Sun Solaris™-Betriebssysteme
>
>Bei neuen Installationen wird empfohlen, AEM Forms möglichst auf dem modernen OSGi-Stack bereitzustellen, um die neuesten Innovationen für responsive Adaptive Forms für mobile, interaktive mehrkanalige Kommunikation und Backend-Datenintegrationen mithilfe des Formulardatenmodells optimal zu nutzen.
>
>Adobe erkennt an, dass bestehende Benutzerinnen und Benutzer AEM Forms on JEE Stack weiterhin bereitstellen müssen. In solchen Fällen erfordert Adobe die Bereitstellung von AEM Forms JEE auf unterstützter Infrastruktur, wie in dieser Dokumentation beschrieben. Wenn Sie ein Upgrade auf AEM 6.5 Forms durchführen und eine nicht unterstützte Plattform aus der vorherigen Version von AEM Forms verwenden, können Sie sich an den Adobe Support wenden, um Hilfe beim Upgrade auf eine unterstützte Plattform zu erhalten.

### Java™ Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms erfordert eine Java™ Virtual Machine, die durch die Java™ Development Kit(JDK)-Verteilung bereitgestellt wird. Adobe Experience Manager funktioniert mit den folgenden Versionen der Java™ Virtual Machine:

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
   <td>Azul Zulu OpenJDK 11 – 64 Bit</td>
   <td>Z: Nicht unterstützt</td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Azul Zulu OpenJDK 8 – 64 Bit</td>
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
>- Verfolgen Sie die Sicherheitsbulletins vom Java™-Anbieter, um den Schutz und die Sicherheit von Produktionsumgebungen sicherzustellen und die neuesten Java™-Aktualisierungen zu installieren.
>- AEM Forms on JEE unterstützt nur 64-Bit-JVMs für Produktionsumgebungen.

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
   <td><p> MongoDB Enterprise 5.0</p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
    <tr>
   <td><p> MongoDB Enterprise 6.0 </p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
   <tr>
   <td>Oracle-Datenbank 19c (Standard, Real Application Clusters (RAC) und Enterprise-Editionen) </td>
   <td>Repository Microkernal </td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2019 </p> </td>
   <td><p>Repository-Mikrokernel</p> </td>
   <td><p>Unterstützt</p> </td>
  </tr>
  <tr>
   <td>IBM® DB2® 11.1 (veraltet)</td>
   <td>Repository-Mikro-Kernel</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
  <tr>
  <tr>
   <td>MySQL 8.0.27</td>
   <td>-</td>
   <td>R: Eingeschränkte Unterstützung </td>
  </tr>
 </tbody>
</table>

- IBM® DB2® wird bei Neuinstallationen nicht unterstützt. Es wird nur für bestehende Kundinnen und Kunden unterstützt, die auf AEM 6.5 Forms aktualisieren.
- MongoDB ist eine Drittanbieter-Software und nicht im AEM-Lizenzierungspaket enthalten. Weitere Informationen finden Sie in der [MongoDB-Lizenzierungsrichtlinie](https://www.mongodb.org/about/licensing/).
- Adobe empfiehlt die Lizenzierung der MongoDB Enterprise-Version, damit Sie von professioneller Unterstützung profitieren und die AEM-Bereitstellung optimal nutzen können.
- Die Adobe-Kundenunterstützung hilft beim Qualifizieren von Problemen, die mit der Verwendung von MongoDB mit AEM in Zusammenhang stehen. Weitere Informationen finden Sie auf der Seite von [MongoDB für Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
- „Dateisystem“ umfasst den POSIX-konformen Blockspeicher. Dazu gehört auch die Netzwerkspeichertechnologie. Beachten Sie, dass die Leistung des Dateisystems variieren und die Gesamtleistung beeinflussen kann. Es wird empfohlen, AEM mit dem Netzwerk-/Remote-Dateisystem zu laden und zu testen.
- Nur MongoDB Storage Engine WiredTiger wird unterstützt.
- MongoDB Sharding wird in AEM nicht unterstützt.
- AEM Forms on JEE unterstützt MySQL für RDBMK-Persistenz nicht.
- Das Document Security-Modul verwendet nicht das Content-Repository. Das bedeutet, wenn Sie nur Document Security und nicht HTML Workspace, HTML5 Forms und adaptive Formulare verwenden möchten, müssen Sie das Content-Repository nicht installieren.
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
   <td><p>Microsoft® SQL Server JDBC-Treiber 8.2.2<br /> </p> <p>sqljdbc8.jar</p> </td>
   <td><p>Laden Sie dies von der Microsoft®-Website herunter.</p> </td>
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
   <td>Oracle WebLogic Server 12.2.1 (12c R2) (veraltet) <sup>[9]</sup></td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td>Oracle WebLogic Server 14c <sup>[9]</sup></td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td>IBM® WebSphere® Application Server 9.0.0.10 <sup>[1] [4]</sup><br /> </td>
   <td>A: Unterstützt</td>
   <td>Service Pack und wichtige Updates</td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application-Plattform (EAP) 7.4 <sup>[2] [3] [7]</sup> </p> </td>
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
   <td>Microsoft® Windows Server 2019 (64 Bit) (veraltet)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
     <tr>
   <td>Microsoft® Windows Server 2022 (64 Bit)</td>
   <td>A: Unterstützt</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td>Ubuntu 20.04</td>
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
   <td>Oracle Linux® 7 Update 3 (64 Bit)</td>
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

Sie können AEM Forms on JEE auf einem physischen Computer oder in einer virtuellen Umgebung ausführen. Wenn Sie mit AEM Forms in einer virtuellen Umgebung auf Probleme stoßen, versuchen Sie, das Problem auf einer physischen Maschine zu reproduzieren. Wenn das Problem auf dem physischen Computer weiterhin besteht, wenden Sie sich in Hinblick auf Unterstützung an den Adobe-Support. Bei Problemen, die Sie auf einem physischen Computer nicht replizieren können, wenden Sie sich an den Verkäufer Ihrer virtuellen Umgebung.

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

### Ausnahmen für unterstützte Server-Plattformen {#exceptions-to-supported-server-platforms}

Beachten Sie die folgenden Ausnahmen, wenn Sie eine Plattform auswählen, auf der Sie AEM Forms on JEE-Server einrichten.

1. AEM Forms on JEE unterstützt IBM® WebSphere® mit MySQL nicht.
1. AEM Forms on JEE unterstützt JBoss® unter SUSE® Linux® Enterprise Server 12 nicht. Nur IBM® WebSphere® wird auf SUSE® Linux® Enterprise Server 12 unterstützt.
1. AEM Forms on JEE unterstützt kein anderes JDK mit JBoss® als Oracle Java™ SE.
1. AEM Forms on JEE unterstützt kein anderes JDK mit IBM® WebSphere® als IBM® JDK.
1. CRX-Repository unterstützt Persistenz des Typs TarMK, MongoDB und relationale Datenbanken (RDBMK). Sie dürfen nicht zwei verschiedene Datenbanksysteme zwischen dem Anwendungsserver und dem CRX-Repository haben. In einer AEM Forms on JEE-Umgebung können Sie MongoMK jedoch mit dem CRX-Repository und einer unterstützten relationalen Datenbank mit Anwendungsserver verwenden.
1. AEM Forms on JEE unterstützt keinen WebSphere®-Anwendungs-Server unter CentOS.
1. AEM Forms on JEE unterstützt keine rollenbasierte Zugriffssteuerung (RBAC) für JBoss®.
1. AEM Forms on JEE unterstützt Oracle Java™ SE 11 (64 Bit) SDK nur für Anwendungs-Server® JBoss EAP 7.4.
1. JDK-Versionen, die höher als 1.8.0_281 sind, werden für WebLogic-Server nicht unterstützt. (FORMS-8498)
1. JDK 11.0.20 wird zur Installation des AEM Forms auf JEE-Installationsprogramms nicht unterstützt. Nur JDK 11.0.19 oder frühere Versionen werden zur Installation des AEM Forms on JEE-Installationsprogramms unterstützt.

<!-- 
1. [!DNL Microsoft&reg; Windows Server 2019] does not support [!DNL MySQL 5.7] and [!DNL JBoss&reg; EAP 7.1], [!DNL Microsoft&reg; Windows Server 2019] does not support turnkey installations for [!DNL Experience Manager Forms Service Pack 6.5.10.0 and later]. (CQDOC-18312) 
-->

Außerdem sollten Sie die folgenden Punkte beachten, wenn Sie die Software für Implementierungen von Adobe AEM Forms on JEE auswählen:

- AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zu der angegebenen Haupt- oder Nebenversion der unterstützten Software. Das Update auf die nächste Haupt- oder Nebenversion wird jedoch nur unterstützt wenn entsprechend angegeben.
- Cluster-basierte Installationen unterstützen keine TarMK-Persistenz.  Weitere Informationen zur unterstützten Persistenz finden Sie unter [Auswählen eines Persistenztyps für eine AEM Forms-Installation](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- AEM Forms on JEE unterstützt die Software verschiedener Drittanbieter gemäß der [Richtlinie zur Unterstützung der Software von Drittanbietern](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p) von Adobe.
- AEM Forms on JEE unterstützt Plattformen in Abhängigkeit der Unterstützung durch Drittanbieter.  Einige Kombinationen werden von Drittanbietern möglicherweise nicht zugelassen. Zum Beispiel haben viele Anbieter ihre Anwendungsserver nicht mit Oracle zertifiziert. Daher unterstützt auch AEM Forms on JEE diese Kombinationen nicht.  Um sicherzugehen, dass Sie die unterstützten Softwareversionen auswählen, sollten Sie auch die Support-Matrix dieser Drittanbieter überprüfen.
- AEM Forms auf JEE unterstützt keine TarMK Cold Standby.
- AEM Forms auf JEE unterstützt kein vertikales Clustering.
- AEM Forms on JEE unterstützt keine MySQL-Datenbank in einer Clusterumgebung.
- Eine Liste der entfernten bzw. der aktualisierten Plattformen finden Sie in dem Dokument [AEM 6.5 Forms - Übersicht über die neuen Funktionen](../../forms/using/whats-new.md).

### LDAP-Server (optional) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Produkt (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2016 (veraltet)</td>
   <td>Wartungsversion und Fixpacks</td>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2022</td>
   <td>Wartungsversion und Fixpacks</td>
  </tr>
  <tr>
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td>
   <td><p>Feature Packs und Zwischenkorrekturen</p> </td>
  </tr>
 </tbody>
</table>

### E-Mail-Server (optional) {#email-servers-optional}

| Produkt |
| ----------------------- |
| Microsoft® Exchange 2013 |
| Microsoft® Office 365 |

### Content-Manager und entsprechende Connectoren {#content-managers-and-corresponding-connectors}

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
   <td>IBM® Content Manager Server (veraltet) </td>
   <td>8.5 Fixpack 2</td>
  </tr>
  <tr>
   <td> IBM® Content Manager Client (veraltet)</td>
   <td>8.5 </td>
  </tr>
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
   <td>Microsoft® Office 2019</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF und TXT</td>
  </tr>
  <tr>
   <td>WordPerfect 2020<br /> </td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2019<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.10</td>
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
>- PDF Generator unterstützt nur die 32-Bit-Einzelhandelsversion von Microsoft® Office Professional Plus und andere für die Konvertierung erforderliche Software.
>- PDF Generator unterstützt nicht Microsoft® Office 365.
>- PDF Generator-Konvertierungen für OpenOffice werden nur unter Windows und Linux unterstützt®.
>- Die Funktionen von OCR PDF, PDF optimieren und PDF erstellen werden nur unter Windows unterstützt.
>- Eine Version von Acrobat ist im Lieferumfang von AEM Forms enthalten, um die PDF Generator-Funktionalität zu aktivieren. Die gebündelte Version sollte während der Laufzeit der AEM Forms-Lizenz zur Verwendung mit AEM Forms PDF Generator nur programmatisch mit AEM Forms zugänglich sein. Weitere Informationen finden Sie in der AEM Forms-Produktbeschreibung für Ihre Bereitstellung ([On-Premise](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-on-premise.html) oder [Managed Services](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-managed-services.html))
>- Der PDF Generator-Service unterstützt nicht Microsoft® Windows 10.
>- PDF Generator kann keine Dateien mit Microsoft® Visio 2019 konvertieren.
>- PDF Generator kann keine Dateien mit Microsoft® Project 2019 konvertieren.
>- Wenn eine Microsoft® Office-Installation aus irgendeinem Grund deaktiviert oder nicht lizenziert wird, z. B. wenn eine lizenzierte Volumeninstallation einen KMS-Host nicht innerhalb eines bestimmten Zeitraums finden kann, können Konvertierungen fehlschlagen, bis die Installation neu lizenziert und reaktiviert wird.

<!-- Removed lines: >- PDF Generator fails to convert files using Microsoft&reg; Visio 2019. You can continue to use Microsoft&reg; Visio 2016 to convert .VSD and .VSDX files.
>- PDF Generator fails to convert files using Microsoft&reg; Project 2019. You can continue to use Microsoft&reg; Project 2016 to convert .MPP files.-->

### Ausnahmen der Barrierefreiheit {#exceptions-to-accessibility-support}

Die folgenden Untersysteme von AEM Forms sind nicht mit [508](https://www.section508.gov/) kompatibel:

- Benutzeroberfläche für das Authoring adaptiver Formulare
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
   <td>Intel Xeon® E5-2680, 2,4-GHz-Prozessor oder ähnlich<br /> VMWare ESX 5.1 oder höher<br /> RAM: 6 GB (64-Bit-Betriebssystem mit 64-Bit-JVM)<br /> Freier Speicherplatz: 15 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>SUSE® Linux® Enterprise Server</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor <br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE</td>
  </tr>
  <tr>
   <td>Red Hat® Enterprise Linux®</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz-Prozessor <br /> AWS m3.medium (3 ECUs)<br /> RAM: 6 GB (64 Bit OS mit 64 Bit JVM)<br /> Freier Speicherplatz: 6 GB temporärer Speicherplatz plus 22 GB<br /> für AEM Forms on JEE<br /> </td>
  </tr>
  <tr>
   <td>Hardware-Anforderungen für kleine Produktionsumgebungen</td>
   <td>
    <ul>
     <li><strong>Intel®-gestützte Umgebung</strong>: Intel Xeon® E5-2680, 2,4 GHz oder höher. Durch die Verwendung eines Dual-Core-Prozessors wird die Leistung weiter verbessert</li>
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
   <td>Microsoft® Windows® 2019 Server (veraltet)</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
  <tr>
   <td>Microsoft® Windows® 2022 Server</td>
   <td>Service Packs und wichtige Updates</td>
  </tr>
 </tbody>
</table>

- Erforderlicher Speicherplatz auf der Festplatte: 1,7 GB nur für Workbench, 2,7 GB auf einem einzelnen Laufwerk für eine vollständige Installation von Workbench, Designer und der Assembly mit den Beispielen, 400 MB für temporäre Installationsordner: 200 MB im Ordner „temp“ des Benutzers und 200 MB im temporären Ordner von Windows. Wenn sich diese Speicherorte alle auf einem einzigen Laufwerk befinden, müssen während der Installation 1,5 GB Speicherplatz zur Verfügung stehen. Die Dateien, die in die temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

- Speicher für Ausführung von Workbench: 2 GB RAM
- Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD®-Prozessor, 1 GHz-Prozessor
- Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher
- TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms on JEE-Server
- Unter Windows müssen Sie über Administratorrechte verfügen, um Workbench installieren zu können. Wenn Sie die Installation mit einem Konto ohne Administratorrechte durchführen, werden Sie vom Installationsprogramm zur Eingabe der Anmeldeinformationen für ein entsprechendes Konto aufgefordert.

### Designer {#designer}

- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 oder Windows® 11
- Prozessor mit 1 GHz oder höher mit Unterstützung für PAE, NX und SSE2.
- 1 GB RAM für 32-Bit-Betriebssysteme oder 2 GB RAM für 64-Bit-Betriebssysteme
- 16 GB Speicherplatz für 32-Bit-Betriebssysteme oder 20 GB Speicherplatz für 64-Bit-Betriebssysteme
- Grafikspeicher – 128 MB GPU (256 MB empfohlen)
- 2,35 GB verfügbarer Festplattenspeicher
- Bildschirmauflösung 1024 x 768 Pixel oder höher
- Beschleuniger für Video-Hardware (optional)
- Acrobat Pro DC, Acrobat Standard DC oder Adobe Acrobat Reader DC
- Administratorrechte für die Installation von Designer
- Microsoft® Visual C++ 2019 (VC 14.28 oder höher) 32-Bit-Runtime

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

</tbody>
</table>

>[!NOTE]
>
>Die Acrobat DC-Produktfamilie führt zwei Linien für Acrobat und Reader ein, wobei es sich um zwei verschiedene Produkte handelt: „Klassik“ und „Fortlaufend“. Weitere Informationen und einen Vergleich der beiden Linien finden Sie unter [https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html).

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
>Für Desktops gelten die folgenden Browser-bedingten Ausnahmen:
>
>- Safari wird nur unter Mac OS X unterstützt.
>- Workspace unterstützt Safari 5.1 unter Macintosh OS X 10.6 und 10.7 mit Acrobat DC oder höheren Versionen. Weitere Informationen zur Kompatibilität von Safari 5.1 mit Adobe Acrobat Reader finden Sie unter [https://helpx.adobe.com/de/x-productkb/multi/safari-5-1-incompatible-reader.html](https://helpx.adobe.com/de/x-productkb/multi/safari-5-1-incompatible-reader.html).
>- Administration Console wird in Safari nicht unterstützt.
>- Correspondence Management unterstützt nicht Windows® Internet Explorer 9.0 für AEM 6.1-Formulare.
>- Das Formularportal unterstützt die JAWS 14.0-Bildschirmlesehilfe-Software in Internet Explorer 11 für einen leichteren Zugriff.

#### Mobile Clients {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (Basisversion)</strong></p> </th>
   <th><p><strong>Unterstützte Patch-Definitionen</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome für Android™ 4.1.2 und höher</p> </td>
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
   <td>Nativer Android™-Browser für Android™ 4.4 und höher</td>
   <td>Alle Updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Forms Portal wird nur auf einem iPad nur in Safari unterstützt.

### AEM Forms-App {#aem-forms-workspace-app}

#### Unterstützung für Mobilgeräte {#mobile-device-support}

Die AEM Forms-Mobile App ist für die folgenden Plattformen verfügbar:

| **Plattform** | **Unterstützte Geräte** |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Apple iOS | Apple iPhone, iPad, iPad Air und iPad mini mit iOS 15.1 und höher. |
| Google Android™ | Android™ 5.1 und höher. Die AEM Forms-Mobile App ist für Samsung Galaxy-Tablets (7 und 10 Zoll) und beliebte Smartphone-Modelle zertifiziert. |
| Microsoft® Windows | Microsoft® Surface-Geräte, Tablets, Laptops und Desktops mit Microsoft® Windows 10. |

### Adobe Document Security Extension für Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}

Klicken Sie [hier](https://www.adobe.com/de/products/livecycle/rightsmanagement/extension/downloads.html), um die Systemanforderungen für Adobe Document Security Extension for Microsoft® Office anzuzeigen.

### Ausnahmen der Clientunterstützung {#exceptions-to-client-support}

AEM Forms on JEE unterstützt Updates, Patches und Fix Packs zusätzlich zu der angegebenen Haupt- oder Nebenversion der unterstützten Software. Das Update auf die nächste Haupt- oder Nebenversion wird jedoch nur unterstützt wenn entsprechend angegeben.

## Richtlinie zur Unterstützung für Patches von Drittanbietern {#third-party-patch-support-policy}

Die Anforderungen an Drittpartei-Software für AEM Forms on JEE werden im Abschnitt „Systemanforderungen“ der jeweiligen Produktdokumente erläutert. Die gesamte Dokumentation ist unter [https://adobe.com/go/learn_aemforms_documentation_65_de](https://adobe.com/go/learn_aemforms_documentation_65_de) verfügbar.

Die Referenzplattformen von AEM Forms on JEE von Drittanbietern geben den spezifischen Patch-Level der Infrastruktur von Drittanbietern an, der während der Entwicklung und Veröffentlichung von AEM Forms on JEE aktuell war, sowie den minimalen Patch-/Service Pack-Level der Infrastruktur, die von dieser Version von AEM Forms on JEE unterstützt wird.

Adobe unterstützt dringende oder empfohlene Patches von Drittanbietern und geht bei deren Veröffentlichung davon aus, dass Drittanbieter die Abwärtskompatibilität mit den Versionen gewährleisten, die AEM Forms on JEE unterstützt. Adobe unterstützt nur Patches, die nach dem in der Dokumentation von AEM Forms on JEE angegebenen Mindest-Patchlevel veröffentlicht wurden.

In einigen Fällen unterstützt Adobe keine Updates von Drittanbietern, die Hauptfunktionen verändern und dadurch keine vollständige Abwärtskompatibilität gewährleisten. Einzelheiten zu den unterstützten Updates finden Sie unter [Unterstützte Patch-Definitionen](https://helpx.adobe.com/de/aem-forms/aem-forms-third-party-software-patch.html) für bestimmte Herstellerprodukte und die von Adobe unterstützten Arten von Patches.

Unter Umständen, die außerhalb der Kontrolle von Adobe liegen, können Patches von Drittanbietern, die Abwärtskompatibilität beanspruchen, negative Auswirkungen auf die Produkte von Adobe oder die Kundenumgebung haben. In solchen Fällen empfiehlt Adobe, dass Kunden die Auswirkungen eines dringenden Patches von einem Drittanbieter bewerten, bevor sie es auf kritische Systeme anwenden. Adobe wird mit Drittanbietern zusammen die entsprechenden geschäftlichen Anstrengungen unternehmen, um solche Probleme zu beheben, entweder durch die üblichen Adobe-Support-Programme oder, indem Drittanbieter das Problem in ihrem Patch beheben. Dies ist keine Garantie dafür, dass ein neu veröffentlichtes Drittanbieter-Patch, das von Adobe unterstützt wird, wie in der Dokumentation des Anbieters funktioniert oder mit AEM Forms on JEE kompatibel ist.

Adobe behält sich das Recht vor, die von einer Version von AEM Forms on JEE unterstützten Referenzplattformen von Drittanbietern und deren unterstützte Patch-Definitionen jederzeit zu ändern.

Weitere Informationen über Patches von Drittanbietern erhalten Sie auch auf der Adobe Enterprise-Support-Seite, indem Sie nach Knowledgebase-Artikeln für Ihr jeweiliges Produkt suchen.

<!--

## Platform updates {#platform-updates}

The following platforms are marked as deprecated with AEM Forms 6.5.18.0 release on August 31, 2023:

- Microsoft&reg; Windows Server 2019 (64-bit)
- Microsoft&reg; Active Directory 2016

The following platforms are marked as deprecated with AEM Forms 6.5.13.0 release on June 2, 2022:
- Microsoft&reg; SharePoint 2016

The following platforms are marked as deprecated with AEM Forms 6.5.10.0 release on September 7, 2021:

- Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
- Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
- Microsoft&reg; Windows Server 2016 (64-bit) 
- Microsoft&reg; Office 2016
- OpenOffice 4.1.2

-->


## Revisionsverlauf {#revision-history}

<!--

- 6.5.18.0 (Aug 31, 2023)
  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - MongoDB Enterprise 4.4
    - Oracle WebLogic Server 14c
    - My SQL JDBC connector 8
    - Active Directory 2022
    - Microsoft&reg; Windows Server 2022 (64-bit)

  - **Removed support**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
    - Windows Server 2016 (64-bit)
    - MongoDB Enterprise 4.0
    - Oracle Database 12c Release 2 (12.2.0.1.0)
    - MySQL 5.7.35
    - Microsoft&reg; SQL Server 2016
    - JBoss&reg; EAP 7.1.4
    - My SQL JDBC connector 5.1.44
    - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
    - Microsoft&reg; SQL Server JDBC driver 6.2.2.0
    - Microsoft&reg; JDBC Driver 8.x for SQL Server

    The release has also removed support for the following platforms for PDF Generator and in-general:
    - Microsoft&reg; Sharepoint 2016
    - Microsoft&reg; Office 2016
    - Microsoft&reg; Office Visio 2016 
    - Microsoft&reg; Publisher 2016
    - Microsoft&reg; Project 2016
    - OpenOffice 4.1.2
    - Acrobat 2017 (Classic track) Version 17.011.30078 or later

  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:
    - Microsoft&reg; Windows Server 2019 (64-bit)
    - Microsoft&reg; Active Directory 2016
    
- 6.5.13.0 (June 2, 2022)

  The following platforms are deprecated with AEM Forms 6.5.13.0 release on:
 
  - Microsoft&reg; SharePoint 2016

- 6.5.12.0 (March 3, 2022)

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
      - IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0)
      - Oracle Database 12c Release 1
      - Oracle Database 18c
      - Oracle Unified Directory (OUD) 11g Release 2
      - IBM&reg; Lotus Domino 9.0
      - IBM&reg; FileNet 5.2
      - Adobe Flash Player

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

      - MongoDB Enterprise 4.0
      - MongoDB Enterprise 4.2
      - IBM&reg; DB2&reg; 11.1
      - Oracle Database 12c Release 2
      - MySQL 5.7.35
      - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
      - JBoss&reg; Enterprise Application Platform (EAP) 7.1.4
      - IBM&reg; Content Manager Server 8.5 Fix pack 2
      - IBM&reg; Content Manager Client 8.5
      - Microsoft&reg; SQL Server 2016

- 6.5.10.0 (Sep 01, 2022)

  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platform:
  
    - Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4.
  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

    - Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
    - Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
    - Microsoft&reg; Windows Server 2016 (64-bit) 
    - Microsoft&reg; Office 2016
    - OpenOffice 4.1.2


-->

### Version 6.5.19.1 (15. Dezember 2023)

| Unterstützung hinzugefügt | Unterstützung entfernt | Unterstützung eingestellt |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 6.0 | MongoDB Enterprise 4.4 |  |
| MongoDB Enterprise 5.0 |  |  |
|  | |  |

### Version 6.5.18.0 (31. August 2023)

| Unterstützung hinzugefügt | Unterstützung entfernt | Unterstützung eingestellt |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 4.4 | Windows Server 2016 (64 Bit) | Microsoft® Windows Server 2019 (64 Bit) |
| Oracle WebLogic Server 14c | MongoDB Enterprise 4.0 | Microsoft® Active Directory 2016 |
| My SQL JDBC Connector 8 | Oracle Database 12c Version 2 (12.2.0.1.0) |  |
| Active Directory 2022 | MySQL 5.7.35 |  |
| Microsoft® Windows Server 2022 (64 Bit) | Microsoft® SQL Server 2016 |  |
|  | JBoss® EAP 7.1.4 |  |
|  | My SQL JDBC Connector 5.1.44 |  |
|  | Microsoft® SQL Server JDBC-Treiber 6.2.1.0 |  |
|  | Microsoft® SQL Server JDBC-Treiber 6.2.2.0 |  |
|  | Microsoft® JDBC-Treiber 8.x für SQL Server |  |
|  |  |  |
|  | **Unterstützung entfernt (PDF Generator und allgemein):** |  |
|  | Microsoft® Sharepoint 2016 |  |
|  | Microsoft® Office 2016 |  |
|  | Microsoft® Office Visio 2016 |  |
|  | Microsoft® Publisher 2016 |  |
|  | Microsoft® Project 2016 |  |
|  | OpenOffice 4.1.2 |  |
|  | Acrobat 2017 (klassische Version) Version 17.011.30078 oder höher |  |


### Version 6.5.13.0 (2. Juni 2022)

| Unterstützung hinzugefügt | Unterstützung entfernt | Unterstützung eingestellt |
| -------------- | --------------- | ------------------- |
|  |  | Microsoft® SharePoint 2016 |


### Version 6.5.12.0 (3. März 2022)

| Unterstützung hinzugefügt | Unterstützung entfernt | Unterstützung eingestellt |
| -------------- | --------------- | ------------------- |
|  | IBM® J9 Virtual Machine (Build 2.8, JRE 1.8.0) | MongoDB Enterprise 4.0 |
|  | Oracle-Datenbank 12c Version 1 | MongoDB Enterprise 4.2 |
|  | Oracle Database 18c | IBM® DB2® 11.1 |
|  | Oracle Unified Directory (OUD) 11g Version 2 | Oracle Database 12c Version 2 |
|  | IBM® Lotus Domino 9.0 | MySQL 5.7.35 |
|  | IBM® FileNet 5.2 | Microsoft® SQL Server JDBC-Treiber 6.2.1.0 |
|  | Adobe Flash Player | JBoss® Enterprise Application Platform (EAP) 7.1.4 |
|  | | IBM® Content Manager Server 8.5 Fix Pack 2 |
|  | | IBM® Content Manager Client 8.5 |
|  | | Microsoft® SQL Server 2016 |
|  | | Microsoft® Windows Server 2016 |

### Version 6.5.10.0 (1. September 2022)

| Unterstützung hinzugefügt | Unterstützung entfernt | Unterstützung eingestellt |
| -------------- | --------------- | ------------------- |
| Oracle Java™ SE 11 (64 Bit) SDK für Anwendungs-Server JBoss® EAP 7.4 | | [Adobe Acrobat 2017 – Die grundlegende Unterstützung für Adobe Acrobat 2017 endet am 6. Juni 2022.](https://helpx.adobe.com/de/support/programs/eol-matrix.html) |
|  | | Red Hat® Enterprise Linux® 7 (Kernel 3.x) (64 Bit) |
|  | | Microsoft® Windows Server 2016 (64 Bit) |
|  | | Microsoft® Office 2016 |
|  | | OpenOffice 4.1.2 |


>[!NOTE]
>
> Eine veraltete Plattform erhält weiterhin Unterstützung, bis die nächste Version des Vollinstallationsprogramms veröffentlicht oder die Unterstützung des Drittanbieters für die Plattform eingestellt wird, je nachdem, was früher eintritt.

<!-- 
- Oct 10, 2021

  - Changed supported version of iOS for AEM Forms App to iOS 15.1. The previous version was iOS 12.

- Sep 07, 2021
  - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - [!DNL Adobe Acrobat 2020]
    - [!DNL Ubuntu 20.04]
    - [!DNL Open Office 4.1.10]
    - [!DNL Microsoft&reg;&reg; Office 2016]
    - [!DNL Microsoft&reg;&reg; Windows Server 2016]
    - [!DNL RHEL8]

- Dec 03, 2020
  - Support added with AEM Forms 6.5.7.0 or later for the following platform:
    - [!DNL Microsoft&reg;&reg; SQL Server 2019]

- Sep 09, 2020

    - Changed supported version of iOS for AEM Forms App to iOS 12. The previous version was iOS 11.

    -->

