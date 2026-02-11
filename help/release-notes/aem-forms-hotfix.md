---
title: Hotfixes für AEM Forms
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
source-git-commit: 598bd1a0b3ad48a958f09ae3810b4f2663ee1014
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 89%

---

# Hotfixes für Adobe Experience Manager Forms{#aem-form-hotfix}

In diesem Artikel werden die wichtigen Fehlerbehebungen aufgelistet, die implementiert wurden, um bekannte Probleme zu beheben, die Systemstabilität zu verbessern und die Gesamtleistung von AEM Forms zu verbessern.

>[!NOTE]
>
> Die Hotfixes sind kumulativ konzipiert und umfassen alle vorherigen Fehlerbehebungen. Wenn Sie das neueste Hotfix auf eine Version anwenden, wird nicht nur das jüngste Problem behoben, sondern das Hotfix enthält auch alle vorherigen Fehlerbehebungen und Verbesserungen.

## Hotfixes für AEM Forms {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Downloadlink (AEM Software Distribution-Link)</strong></td>
    <td><strong>Behobene Probleme</strong></td>
  </tr>
    <tr>
    <td>
      <strong>10. Februar 2026</strong><br>
      <em>Gilt für:</em> AEM Forms SP24<br>
    </td>
    <td>
    <ul> <a href = "https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bb-expressionmanager-pkg-10.0.48.zip"> AEM 6.5 Forms-Add-on-Hotfix</a>
    </ul>
    </td>
    <td>
    <ul>
    <li><b>FORMS-23875</b> Bei der Formulardatenmodellsuche wird ein HTML-Tag in der Benutzeroberfläche angezeigt, auch wenn keine relevante Entität vorhanden ist.
      <ul></tr>
  <tr>
    <td>
      <strong>14. Oktober 2025</strong><br>
      <em>Gilt für:</em> ImgToPdf schlägt mit AEM Forms SP23 Jboss fehl<br>
    </td>
    <td>
    <ul> Zur Lösung wenden Sie sich an den <a href="https://business.adobe.com/de/support/main.html">Adobe Experience Manager Forms-Support</a>
    </ul>
    </td>
    <td>
    <ul>
    <li> <b>(FORMS-22029):</b> Verbessert die Konvertierungszuverlässigkeit von PDF, indem ein Problem behoben wird, bei dem PDF Generator (PDFG) Bilddateien nach dem Upgrade auf SP23 nicht in PDF konvertieren kann, was zu unerwarteten Nachbearbeitungsfehlern führt.
      <ul></tr>
  <tr>
    <td>
      <strong>23. September 2025</strong><br>
    </td>
    <td>
    <ul>
    <strong>JBoss:</strong>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/jboss/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-jboss.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für JBoss JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/jboss/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für JBoss JEE-Server</a></li>
    <strong>WebLogic:</strong>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/weblogic/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-weblogic.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Weblogic JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/weblogic/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-weblogic.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Weblogic JEE-Server</a></li>
    <strong>WebSphere:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/websphere/adobe-aem-forms-jee-hotfix3-6.5.23.0-win-websphere.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Websphere JEE Server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-23-0-hotfix-3/websphere/adobe-aem-forms-jee-hotfix3-6.5.23.0-linux-websphere.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Websphere JEE Server</a></li>
    </ul>
    </td>
    <td>
    <ul>
    <strong>Dieser Hotfix behebt Folgendes:</strong> 
    <li> <b>(FORMS-21378):</b> Verbesserte Zuverlässigkeit der Formularübermittlung durch Beheben eines Problems, bei dem Übermittlungen fehlschlagen, wenn die Server-seitige Validierung (SSV) aktiviert ist und berechnete Meta-Informationen leer sind.

<li> <b>(FORMS-21721):</b> Es wurde ein Problem behoben, bei dem Konvertierungen von PS in PDF und HTML in PDF (WebKit) nach der Bereitstellung des Hotfixes (veröffentlicht am <b>. August 2025</b>) für 6.5.23.0 fehlschlagen. 
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>
  <tr>
    <td>
      <strong>5. August 2025</strong><br>
      <em>Gilt für:</em> AEM 6.5 Forms Service Pack 23<br>
      <em>Setup-Anweisungen:</em>
      <a href="/help/forms/using/mitigating-xxe-and-configuration-vulnerabilities-for-experience-manager-forms-jee.md#option-1-for-users-on-version-65230-install-latest-hotfix">
        Minimieren von Schwachstellen durch XXE, Konfiguration und Ausführung von Remote-Code (CVE-2025-49533) für AEM Forms auf JEE
      </a>
    </td>
    <td>
    <ul>
    <li><strong>JBoss:</strong></li>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-jboss.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für JBoss JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/jboss/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für JBoss JEE-Server</a></li>
    <li><strong>Weblogic:</strong></li>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-weblogic.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Weblogic JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/weblogic/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-weblogic.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Weblogic JEE-Server</a></li>
    <li><strong>Websphere:</strong></li>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.23.0-win-websphere.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Websphere JEE Server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-02/websphere/adobe-aem-forms-jee-hotfix2-6.5.23.0-linux-websphere.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Websphere JEE Server</a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li>Verbesserte Sicherheit durch Behebung einer Schwachstelle bei der Ausführung von Remote-Code (RCE) in Adobe Experience Manager (AEM) Forms. Das Problem stand im Zusammenhang mit dem Struts-Entwicklungsmodus in der Admin-Benutzeroberfläche (UI), der eine beliebige Auswertung der Object-Graph Navigation Language (OGNL) durch die Debugging-Funktion ermöglichte. Durch diese Fehlerbehebung wird sichergestellt, dass der Struts-Entwicklungsmodus deaktiviert ist und geeignete Sicherheitsfilter angewendet werden, um einen nicht autorisierten Zugriff zu verhindern.</li>
    <li>Verbesserter Schutz vor Sicherheitslücken in Extensible Markup Language (XML) External Entity (XXE) im Modul der elektronischen Dokumentkomponente (EDC) von Adobe Experience Manager (AEM) Forms. Die Sicherheitslücken waren auf eine unsichere Verarbeitung von XML-Dokumenten ohne XXE-Schutz zurückzuführen, was das Auslesen lokaler Dateien ermöglichen konnte. Die Korrektur umfasst Folgendes:
      <ul>
        <li>Sie stellt sicher, dass die in der SecurityCheckHandler-Klasse verwendete DocumentBuilderFactory so konfiguriert ist, dass sie XXE-Angriffe verhindert.</li>
        <li>Der EDC-Webservice wird aktualisiert, um XML-Dokumente sicher zu verarbeiten und einen nicht autorisierten Zugriff auf lokale Dateien zu verhindern.</li>
      </ul>
    </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>
      <strong>5. August 2025</strong><br>
      <em>Gilt für:</em> AEM 6.5 Forms Service Pack 18–22<br>
      <em>Setup-Anweisungen:</em>
      <a href="/help/forms/using/mitigating-xxe-and-configuration-vulnerabilities-for-experience-manager-forms-jee.md#option-2-for-users-on-65180---65220-manual-hotfix-installation">
        Manuelle Hotfix-Installation für Service Packs 18–22
      </a>
    </td>
    <td>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-xxe-configuration-hotfix.zip">Patch für AEM 6.5 Forms Service Pack 18 – AEM 6.5 Forms Service Pack 22 </a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li>Verbesserte Sicherheit durch Behebung einer Schwachstelle bei der Ausführung von Remote-Code (RCE) in Adobe Experience Manager (AEM) Forms. Das Problem stand im Zusammenhang mit dem Struts-Entwicklungsmodus in der Admin-Benutzeroberfläche (UI), der eine beliebige Auswertung der Object-Graph Navigation Language (OGNL) durch die Debugging-Funktion ermöglichte. Durch diese Fehlerbehebung wird sichergestellt, dass der Struts-Entwicklungsmodus deaktiviert ist und geeignete Sicherheitsfilter angewendet werden, um einen nicht autorisierten Zugriff zu verhindern.</li>
    <li>Verbesserter Schutz vor Schwachstellen durch XML External Entity (XXE) im Document-Security-Modul von Adobe Experience Manager (AEM) Forms.
Die Sicherheitslücken waren auf eine unsichere Verarbeitung von XML-Dokumenten ohne XXE-Schutz zurückzuführen, was das Auslesen lokaler Dateien ermöglichen konnte. Die Korrektur umfasst Folgendes:
      <ul>
        <li>Sie stellt sicher, dass die in der SecurityCheckHandler-Klasse verwendete DocumentBuilderFactory so konfiguriert ist, dass sie XXE-Angriffe verhindert.</li>
        <li>Der Document Security-Webservice wird aktualisiert, um XML-Dokumente sicher zu verarbeiten und einen nicht autorisierten Zugriff auf lokale Dateien zu verhindern.</li>
      </ul>
    </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>10. Juli 2025</td>
    <td>
    <ul>
    <li><strong>JBoss:</strong></li>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/jboss/adobe-aem-forms-jee-hotfix-6.5.23.0-win-jboss.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für JBoss JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/jboss/adobe-aem-forms-jee-hotfix-6.5.23.0-linux-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für JBoss JEE-Server</a></li>
    <li><strong>Weblogic:</strong></li>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/weblogic/adobe-aem-forms-jee-hotfix-6.5.23.0-win-weblogic.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Weblogic JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/weblogic/adobe-aem-forms-jee-hotfix-6.5.23.0-win-weblogic.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Weblogic JEE-Server</a></li>
    <li><strong>Websphere:</strong></li>
    <li>Windows: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/websphere/adobe-aem-forms-jee-hotfix-6.5.23.0-win-websphere.zip">Hotfix für AEM Service Pack 6.5.23.0 unter Windows für Websphere JEE-Server</a></li>
    <li>Linux: <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-2/websphere/adobe-aem-forms-jee-hotfix-6.5.23.0-linux-websphere.tar.gz">Hotfix für AEM Service Pack 6.5.23.0 unter Linux für Websphere JEE-Server</a></li>
    </ul>
    </td>
    <td>
    <ul>
    <li><strong>Dieser Hotfix behebt Folgendes:</strong>
      <ul>
        <li><strong>FORMS-20533:</strong> AEM Forms enthält jetzt eine Aktualisierung der Struts-Version von 2.5.33 auf 6.x für die Formularkomponente. Dies liefert bis jetzt fehlende Struts-Änderungen, die nicht in SP23 enthalten waren. Die Unterstützung wurde über einen Hotfix hinzugefügt. Diesen können Sie herunterladen und installieren, um Unterstützung für die neueste Version von Struts hinzuzufügen.</li>
        <li><strong>FORMS-20532:</strong> AEM Forms enthält jetzt eine Aktualisierung der Struts-Version von 2.5.33 auf 6.x für die Output-Komponente. Dies liefert bis jetzt fehlende Struts-Änderungen, die nicht in SP23 enthalten waren. Die Unterstützung wurde über einen Hotfix hinzugefügt. Diesen können Sie herunterladen und installieren, um Unterstützung für die neueste Version von Struts hinzuzufügen.</li>
        <li><strong>FORMS-20203:</strong> Wenn Benuztende Struts von AEM Service Pack 2.5.x auf AEM Forms Service Pack 6.x aktualisieren, werden in der Richtlinien-Benutzeroberfläche nicht alle Konfigurationen angezeigt, beispielsweise die Option zum Hinzufügen eines Wasserzeichens. Sie können den Hotfix herunterladen und installieren, um das Problem zu beheben.</li>
        <li><strong>FORMS-20360:</strong> Nach der Aktualisierung auf AEM Forms Service Pack 6.5.23.0 schlägt der ImageToPDF-Konvertierungsdienst mit folgendem Fehler fehl:<br>
        <code>17:15:44,468 ERROR [com.adobe.pdfg.GeneratePDFImpl] (default task-49) ALC-PDG-001-000-ALC-PDG-011-028-Error occurred while converting the input image file to PDF. com/adobe/internal/pdftoolkit/core/encryption/EncryptionImp</code><br>
        Sie können den Hotfix zur Lösung dieses Problems herunterladen und installieren.</li>
      </ul>
    </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>26. März 2025 </br> </br> Um diese Fehlerbehebung zu installieren, folgen Sie den Anweisungen zum <a href="/help/forms/using/mitigating-spring-framework-vulnerabilities-for-aem-forms-on-jee.md"> Beheben von Spring Framework-Schwachstellen für AEM Forms on JEE</a>.</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/jboss/adobe-aem-forms-jee-hotfix-6.5.22.0-win-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Windows für einen JBoss JEE-Server </a> </li>
      <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/jboss/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Linux für einen JBoss JEE-Server </a> </li>
       <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/weblogic/adobe-aem-forms-jee-hotfix-6.5.22.0-win-weblogic.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Windows für einen WebLogic JEE-Server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/weblogic/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-weblogic.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Linux für einen WebLogic JEE-Server</a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/websphere/adobe-aem-forms-jee-hotfix-6.5.22.0-win-websphere.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Windows für einen WebSphere JEE-Server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/websphere/adobe-aem-forms-jee-hotfix-6.5.22.0-linux-websphere.tar.gz">Hotfix für AEM Service Pack 6.5.22.0 unter Linux für einen WebSphere JEE-Server</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Beheben von Spring Framework-Schwachstellen für AEM Forms on JEE</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>10. Juli 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/jboss/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-jboss.zip.zip">Hotfix für AEM Service Pack 6.5.21.0 unter Windows für JBoss JEE-Server </a> </li>
      <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/jboss/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-jboss.tar.gz">Hotfix für AEM Service Pack 6.5.21.0 unter Linux für JBoss JEE-Server </a> </li>
       <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/websphere/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-websphere.zip.zip">Hotfix für AEM Service Pack 6.5.21.0 unter Windows für WebSphere JEE-Server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/websphere/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-websphere.tar.gz">Hotfix für AEM Service Pack 6.5.21.0 unter Linux für WebSphere JEE-Server</a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/weblogic/win/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-windows-weblogic.zip.zip">Hotfix für AEM Service Pack 6.5.21.0 unter Windows für WebLogic JEE-Server </a> </li>
        <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/aemforms-6-5-0-0089/weblogic/linux/adobe-aem-forms-jee-service-pack-6.5.21.0-hotfix-linux-weblogic.tar.gz">Hotfix für AEM Service Pack 6.5.21.0 unter Linux für WebLogic JEE-Server</a> </li>
     </ul>
     </td>
    <td>
    <ul><li>Wenn Benutzende auf AEM Forms Service Pack 20 (6.5.20.0) auf JEE Server aktualisieren und mithilfe von Ausgabe-Services PDF-Dateien generieren, werden die PDF-Dateien mit Problemen bezüglich der Barrierefreiheit gerendert. (LC-3922112)</li><li>Für getaggte PDF-Dateien, die mit dem Ausgabe-Service von AEM Forms JEE generiert werden, wird eine Warnung zu einer unangemessenen Struktur angezeigt. (LC-3922038)</li><li>Wenn ein Formular auf AEM Forms JEE gesendet wird, werden die Instanzen eines sich wiederholenden XML-Elements aus den Daten entfernt. (LC-3922017)</li><li>Wenn Benutzende in einer Linux-Umgebung ein adaptives Formular (auf JEE) in HTML rendern, schlägt das Rendern fehl. (LC-3921957)</li><li>Wenn Benutzende mithilfe des Output-Services auf AEM Forms JEE eine XTG-Datei in das PostScript-Format konvertieren, schlägt der Vorgang mit einem Fehler fehl: AEM_OUT_001_003: Unerwartete Ausnahme: PAExecute-Fehler: XFA_RENDER_FAILURE. (LC-3921720)</li><li>Nach dem Upgrade auf AEM Forms Service Pack 18 (6.5.18.0) auf JEE Server wird ein von Benutzenden gesendetes Formular nicht als HTML5- oder PDF-Formular gerendert und XMLFM stürzt ab. (LC-3921718)
    </ul>
    </td>    
  </tr>
  <tr>
    <td>21. Juni 2024</td>
     <td>
     <ul>
     <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf JBoss JEE-Server </a> </li>
      <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf Weblogic JEE-Server </a> </li>
       <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf Webshpere JEE Server </a> </li>
        <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf OSGi-Server-</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li> Nach der Aktualisierung auf AEM Forms Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 kann der PaperCapture-Dienst OCR-Vorgänge (Optical Character Recognition) für PDFs nicht ausführen. Installationsanweisungen finden Sie im Artikel <a href="/help/forms/using/papercapture-service-resolution.md">Fehlerbehebung</a>.(CQDOC-21680) </li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>21. Juni 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Fccm-ccr-content-10.0.206.zip">Hotfix für AEM Service Pack 6.5.21.0 </a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Briefentwürfe mit XML-Daten bleiben während der Vorschau im Ladezustand hängen. Informationen zum Herunterladen und Installieren des Hotfixes finden Sie im Abschnitt<a href="#install-hotfix"> Herunterladen und Installieren des Hotfixes für das Problem mit Briefentwürfen</a>.(FORMS-14521)</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>16. Mai 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Apple macOS</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>In einem adaptiven Formular, das auf einer XDP mit eingebetteten Skripten auf Kontrollkästchen basiert, werden die Skripte für Elemente nach diesen Kontrollkästchen nicht ausgeführt. Für dieses Problem ist ein Hotfix verfügbar. (FORMS-14244) </li>
     <li> Im Widget für die Datumsauswahl werden die Zeilen abgeschnitten, wenn Sie im Popup-Widget mit dem Muster Bearbeiten/Anzeigen nach Feldern durch die Monate blättern. Für dieses Problem ist ein Hotfix verfügbar. (FORMS-13620) </li>
     <li>Formulareinreichungen schlagen fehl, wenn versucht wird, den DoR-Service (Document of Record; Nachweis) im Backend zu verwenden. Die Fehlermeldung lautet: „Sendeaktion konnte nicht abgeschlossen werden, da die Formularressource nicht ordnungsgemäß zugewiesen ist“. (FORMS-13798) </li>
     <li>Wenn ein adaptives Formular aus einer Adobe Experience Manager-Veröffentlichungsinstanz an einen Adobe Experience Manager-Workflow gesendet wird, können die Anlagen nicht vom Workflow gespeichert werden.  (FORMS-14209) </li>
     <li> Bei der Installation des AEM 6.5 Forms Service Pack 20-Pakets (AEM Forms-Add-on-Paket für SP20) verschlechtert sich die Leistung der AEM Sites-Benutzeroberfläche erheblich.  (FORMS-13791) </li>
     <li>Der Vorbefüllungsdienst schlägt in interaktiven Kommunikationen mit einer NULL-Zeigerausnahme fehl. (CQDOC-21355)</li>
     <li>Konfigurationen, die den älteren Cloud-Service für Adobe Analytics mit einer auf Benutzeranmeldeinformationen basierenden Authentifizierung verwenden, funktionieren nicht ordnungsgemäß, wodurch Analyseregeln nicht ausgeführt werden. (FORMS-15428)
    </ul>
    </td>    
  </tr>
  <tr>
    <td>29. Januar 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fforms-foundation-qs-content-4.0.170-FORMS-12692-B0001.zip">Hotfix für AEM Service Pack 6.5.19.0 für Windows on JEE-Server</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Unter AEM Forms für den JEE-Server kann das HTML5-Formular, das den Kontextpfad verwendet, nicht gerendert werden. (FORMS-12485, FORMS-12691).</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>29. Januar 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-win-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-linux-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Linux</a></li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-osx-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li> Bei der vorkonfigurierten Komponente „Freihandsignatur“ kann in einem adaptiven Formular keine Vorschau gerendert werden. (FORMS-12073).</li>
    </ul>
    </td>    
   </tr>
   <tr>
    <td>20. November 2023</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Die Inline-Signatur funktioniert nicht mehr, wenn eine Umleitungs-URL im Guide-Container eines adaptiven Formulars festgelegt ist. (FORMS-10493)</li>
    <li>DoR-Vorlagen können für lokalisierte, adaptive Formulare nicht veröffentlicht werden. (FORMS-10535)</li>
    <li>Die interaktive Kommunikation mit großen Inline-Bildern kann im Bearbeitungsmodus nicht geöffnet werden. (FORMS-10578)</li>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Herunterladen und Installieren eines OSGi-Hotfixes {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Laden Sie das [Hotfix](#hotfix-for-adaptive-forms) über den Software Distribution-Link herunter.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über den [Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.
1. Öffnen Sie die Bundles des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Bundle (.jar). Das Hotfix wird installiert.

## Installieren eines JEE-Patches {#download-install-jee-patch}

Anweisungen zum Installieren eines JEE-Patches finden Sie in der [Dokumentation zum AEM Forms JEE-Patch-Installationsprogramm](/help/release-notes/jee-patch-installer-65.md).


## Herunterladen und Installieren des Hotfixes für das Problem mit Briefentwürfen {#install-hotfix}

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Laden Sie den [Hotfix](#hotfix-for-adaptive-forms) über das Software-Verteilungsportal herunter.
2. Laden Sie das Paket (.zip) über den [CRX-Paket-Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.
