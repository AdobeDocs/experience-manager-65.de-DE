---
title: Hotfixes für AEM Forms
description: Enthält Informationen zum Herunterladen und Installieren eines Hotfixes für AEM Forms.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 5e2799505bc6d69cd5898445a9300ad162ef74fd
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 86%

---

# Hotfixes für Adobe Experience Manager Forms{#aem-form-hotfix}

In diesem Artikel werden die wichtigen Fehlerbehebungen aufgelistet, die implementiert wurden, um bekannte Probleme zu beheben, die Systemstabilität zu verbessern und die Gesamtleistung von AEM Forms zu verbessern.

>[!NOTE]
>
> Die Hotfixes sind kumulativ konzipiert und umfassen alle vorherigen Fehlerbehebungen. Wenn Sie das neueste Hotfix auf eine Version anwenden, wird nicht nur das jüngste Problem behoben, sondern das Hotfix enthält auch alle vorherigen Fehlerbehebungen und Verbesserungen.

## Hotfixes für adaptive Formulare {#hotfix-for-adaptive-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-Downloadlink (AEM Software Distribution-Link)</strong></td>
    <td><strong>Behobene Probleme</strong></td>
  </tr>
  <tr>
    <td>Freitag, 16. Mai 2024</td>
     <td>
     <ul>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-win-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Microsoft Windows</a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-linux-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Linux </a> </li>
     <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/adobe-aemfd-osx-pkg-6.0.1192-010.zip">Hotfix für AEM Service Pack 6.5.20.0 für Apple macOS</a> </li>
     </ul>
     </td>
    <td>
    <ul>
    <li>In einem adaptiven Formular, das auf einer XDP mit eingebetteten Skripten auf Kontrollkästchen basiert, werden die Skripte für Elemente nach diesen Kontrollkästchen nicht ausgeführt. Für dieses Problem ist ein Hotfix verfügbar. (FORMS-14244) </li>
     <li> Zeilen im Datumsauswahl-Widget werden abgeschnitten, wenn im Popup-Widget für Felder mit Bearbeitungs-/Anzeigemuster Monate durchlaufen werden. Für dieses Problem ist ein Hotfix verfügbar. (FORMS-13620) </li>
     <li>Formulareinreichungen schlagen fehl, wenn versucht wird, den DoR-Service (Document of Record; Nachweis) im Backend zu verwenden. Die Fehlermeldung lautet: „Sendeaktion konnte nicht abgeschlossen werden, da die Formularressource nicht ordnungsgemäß zugewiesen ist“. (FORMS-13798) </li>
     <li>Wenn ein adaptives Formular von einer Adobe Experience Manager-Veröffentlichungsinstanz an einen Adobe Experience Manager-Workflow gesendet wird, kann der Workflow die Anlagen nicht speichern.  (FORMS-14209) </li>
     <li> Bei der Installation des AEM 6.5 Forms Service Pack 20-Pakets (AEM Forms Add-On-Paket für SP20) weist die AEM Sites-Benutzeroberfläche eine erhebliche Leistungsbeeinträchtigung auf.  (FORMS-13791) </li>
     <li>Der Vorbefüllungsdienst schlägt in interaktiven Kommunikationen mit einer NULL-Zeigerausnahme fehl. (CQDOC-21355)</li>
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
