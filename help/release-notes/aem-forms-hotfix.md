---
title: Hotfixes für AEM Forms
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: f472766dbfeb8d84b0b97f621828b1c0491529c4
workflow-type: tm+mt
source-wordcount: '1340'
ht-degree: 87%

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
    <td>SP23 Hotfix-</td>
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
    <li><strong>Dieses Hotfix behebt Folgendes:</strong>
      <ul>
        <li><strong>FORMS-20533:</strong> AEM Forms enthält jetzt ein Upgrade der Struts-Version von 2.5.33 auf 6.x für die Formularkomponente. Dies liefert bis jetzt fehlende Struts-Änderungen, die nicht in SP23 enthalten waren. Die Unterstützung wurde über einen Hotfix hinzugefügt, den Sie herunterladen und installieren können, um Unterstützung für die neueste Version von Struts hinzuzufügen.</li>
        <li><strong>FORMS-20532:</strong> AEM Forms enthält jetzt ein Upgrade der Struts-Version von 2.5.33 auf 6.x für die Ausgabekomponente. Dies liefert bis jetzt fehlende Struts-Änderungen, die nicht in SP23 enthalten waren. Die Unterstützung wurde über einen Hotfix hinzugefügt, den Sie herunterladen und installieren können, um Unterstützung für die neueste Version von Struts hinzuzufügen.</li>
        <li><strong>FORMS-20203:</strong> Wenn ein Benutzer Struts von AEM Service Pack 2.5.x auf AEM Forms Service Pack 6.x aktualisiert, kann die Richtlinien-Benutzeroberfläche nicht alle Konfigurationen anzeigen, z. B. die Option zum Hinzufügen eines Wasserzeichens. Sie können den Hotfix zur Lösung dieses Problems herunterladen und installieren.</li>
        <li><strong>FORMS-20360:</strong> Nach dem Upgrade auf AEM Forms Service Pack 6.5.23.0 schlägt der ImageToPDF-Konvertierungsdienst mit folgendem Fehler fehl:<br>
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
     <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf JBoss JEE-Server </a> </li>
      <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf Weblogic JEE-Server </a> </li>
       <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf Webshpere JEE Server </a> </li>
        <li><a href="https://nam04.safelinks.protection.outlook.com/?url=https%3A%2F%2Fexperience.adobe.com%2F%23%2Fdownloads%2Fcontent%2Fsoftware-distribution%2Fen%2Faem.html%3Fpackage%3D%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2FPaperCaptureSvc.zip&amp;data=05%7C02%7Cruchitas%40adobe.com%7Cf50f80aab6994875271a08dc91f2f137%7Cfa7b1b5a7b34438794aed2c178decee1%7C0%7C0%7C638545719814675925%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&amp;sdata=9pTrMfiMD%2B5kQezxsZwTdOmaaktxURR99d7f6wHr%2FWQ%3D&amp;reserved=0">Hotfix für AEM Service Pack 6.5.21.0 oder AEM Forms Service Pack 6.5.22.0 auf OSGi-Server-</a> </li>
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

## Herunterladen und Installieren eines Hotfixes {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Laden Sie das [Hotfix](#hotfix-for-adaptive-forms) über den Software Distribution-Link herunter.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über den [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.
1. Öffnen Sie die Bundles des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Bundle (.jar). Das Hotfix wird installiert.


## Herunterladen und Installieren des Hotfixes für das Problem mit Briefentwürfen {#install-hotfix}

Um das Problem zu beheben, führen Sie die folgenden Schritte aus:

1. Laden Sie den [Hotfix](#hotfix-for-adaptive-forms) über das Software-Verteilungsportal herunter.
2. Laden Sie das Paket (.zip) über den [CRX Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=de#accessing) hoch und installieren Sie es.