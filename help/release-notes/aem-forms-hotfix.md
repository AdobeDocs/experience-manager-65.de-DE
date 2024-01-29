---
title: Hotfixes für AEM Forms
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
source-git-commit: 4685a4babbec07dc09fe19c9264b4141b9989fbb
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 9%

---

# Adobe Experience Manager Forms Hotfixes{#aem-form-hotfix}

In diesem Artikel werden die kritischen Fehlerbehebungen aufgelistet, die implementiert wurden, um bekannte Probleme zu beheben, die Systemstabilität zu verbessern und die Gesamtleistung von AEM Forms zu verbessern.

>[!NOTE]
>
> Die Hotfixes sind kumulativ konzipiert und umfassen alle vorherigen Fehlerbehebungen. Wenn Sie das neueste Hotfix auf eine Version anwenden, wird nicht nur das neueste Problem behoben, sondern es enthält auch alle vorherigen Fehlerbehebungen und Verbesserungen.

## Hotfixes für adaptive Forms {#hotfix-for-adaptive-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Downloadlink (AEM Software Distribution-Link)</strong></td>
    <td><strong>Behobene Probleme</strong></td>
  </tr>
  <tr>
    <td>Dienstag, 29. Januar 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fforms-foundation-qs-content-4.0.170-FORMS-12692-B0001.zip">Hotfix für AEM Service Pack 6.5.19.0 für Windows on JEE-Server</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>In AEM Forms auf dem JEE-Server kann die HTML5 Forms, die den Kontextpfad verwenden, nicht gerendert werden. (FORMS-12485).</li>
    </ul>
    </td>    
  </tr>
  <tr>
    <td>Dienstag, 29. Januar 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-win-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-linux-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Linux</a></li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffd%2Fadobe-aemfd-osx-pkg-6.0.1016-004.zip">Hotfix für AEM Service Pack 6.5.18.0 für Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li> Die OOTB Scribble-Signatur-Komponente kann für eine Vorschau in einem adaptiven Formular nicht gerendert werden. (FORMS-12073).</li>
    </ul>
    </td>    
   </tr>
   <tr>
    <td>Dienstag, 20. November 2023</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Apple macOS</a></li>
     </ul>
     </td>
    <td>
    <ul>
    <li>Inline-Signatur funktioniert nicht mehr, wenn eine Umleitungs-URL im Guide-Container eines adaptiven Formulars festgelegt ist. (FORMS-10493)</li>
    <li>Datensatzdokumentvorlagen können für lokalisierte adaptive Forms nicht veröffentlicht werden. (FORMS-10535)</li>
    <li>Die interaktive Kommunikation mit großen Inline-Bildern kann im Bearbeitungsmodus nicht geöffnet werden. (FORMS-10578)</li>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Hotfix herunterladen und installieren {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Herunterladen [Hotfix](#hotfix-for-adaptive-forms) über den Link Softwareverteilung.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über die [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Öffnen Sie die Konfigurations-Manager-Pakete. `https://server:host/system/console/bundles`, laden Sie das Bundle hoch und installieren Sie es (.jar). Der Hotfix ist installiert.
