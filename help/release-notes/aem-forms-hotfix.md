---
title: Hotfix für AEM Formular Service Pack
description: Enthält Informationen zum Herunterladen und Installieren des Hotfixes für das AEM Forms Service Pack
source-git-commit: 169d407835098add0312b0d12c2c80035b525762
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 17%

---


# Adobe Experience Manager Hotfixes{#aem-form-hotfix}

Die Installation der neuesten [AEM Service Pack](/help/release-notes/release-notes.md) wird empfohlen, die Sicherheits-, Leistungs-, Stabilitäts- und wichtige Fehlerbehebungen und Verbesserungen umfasst, die seit der allgemeinen Verfügbarkeit von Adobe Experience Manager 6.5 veröffentlicht wurden.

## Hotfixes für adaptive Forms {#hotfix-for-adaptive-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Namen</strong></td>
    <td><strong>Fehlerkorrekturen</strong></td>
   </tr>
   <tr>
    <td>20. November 2023</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Linux</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1016-002.zip">Hotfix für AEM Service Pack 6.5.18.0 für Mac OS</a></li>
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

## Herunterladen und Installieren von Hotfix {#download-install-hotfix}

Führen Sie die folgenden Schritte aus, um das Hotfix herunterzuladen und zu installieren:

1. Herunterladen [Hotfix](#hotfix-for-adaptive-forms) aus der SD-Verknüpfung.
1. Extrahieren Sie die Hotfix-Archivdatei, damit Sie ein Experience Manager-Paket (.zip) und Bundle-Dateien (.jar) abrufen können.
1. Laden Sie das Paket (.zip) über den Package Manager hoch und installieren Sie es.
1. Öffnen Sie die Bundles des Konfigurations-Managers `https://server:host/system/console/bundles`, laden Sie sie hoch und installieren Sie das Bundle (.jar).
