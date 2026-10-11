---
title: Gruppen und Berechtigungen bei AEM Forms auf OSGi
description: Zuweisen von Benutzenden zu Gruppen, um Adobe Experience Manager (AEM) Forms auf OSGi zu verwalten
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: d802ac53-e3db-45ca-afcb-7e99d0bb7877
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%
---
# Gruppen und Berechtigungen bei AEM Forms auf OSGi{#aem-forms-on-osgi-groups-and-privileges}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Sie können [Gruppen erstellen](/help/sites-administering/user-group-ac-admin.md#group-administration) und Richtlinien zuweisen sowie [Benutzende](/help/sites-administering/user-group-ac-admin.md#user-administration) zu den Gruppen in Adobe Experience Manager (AEM) zuweisen. Diese Richtlinien steuern die Berechtigungen der Benutzenden, die zu der jeweiligen Gruppe gehören.

Sobald Sie das [AEM Forms-Add-On-Paket](../../forms/using/installing-configuring-aem-forms-osgi.md) installiert haben, werden die in diesem Artikel genannten Gruppen, wie „forms-users“ und „forms-power-user“, automatisch für die Zuweisung zur Verfügung gestellt. In der folgenden Tabelle sind die Aufgaben aufgeführt, die Benutzende für AEM Forms auf OSGi basierend auf den Gruppenzuweisungen ausführen können:

<table>
 <tbody>
  <tr>
   <td>Gruppe</td> 
   <td>Aufgaben</td> 
  </tr>
  <tr>
   <td>forms-users <sup>[1]</sup></td> 
   <td>
    <ul> 
     <li>Erstellen, Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
     <li>Erstellen, Anzeigen (in der Vorschau) und Veröffentlichen von interaktiven Kommunikationen und Dokumentfragmenten</li> 
     <li>Hochladen von Assets in eine AEM-Instanz</li> 
     <li>Erstellen von Designs</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>Erstellen, Vorschau, Veröffentlichen und Senden adaptiver Formulare</li> 
     <li>Erstellen, Anzeigen (in der Vorschau) und Veröffentlichen von interaktiven Kommunikationen und Dokumentfragmenten</li> 
     <li>Erstellen von Skripten für adaptive Formulare mithilfe des Code-Editors</li> 
     <li>Hochladen von Assets einschließlich Skripten</li> 
     <li>Erstellen von Designs</li> 
     <li>Importieren von Paketen, die XDP enthalten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-submission-reviewers</td> 
   <td>
    <ul> 
     <li>Überprüfen von Übermittlungen</li> 
     <li>Genehmigen oder Ablehnen von Übermittlungen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-authors <sup>[2]</sup></td> 
   <td>
    <ul> 
     <li>Adaptive Formulare oder interaktive Kommunikationsvorlagen erstellen oder in der Vorschau anzeigen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Erstellen und Ändern des Formulardatenmodells</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-agent-users</td> 
   <td>
    <ul> 
     <li>Zugriff auf Correspondence Management-Briefe oder interaktive Kommunikationen über die Agent-Benutzeroberfläche</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Erstellen einer Posteingangs-Anwendung</li> 
     <li>Erstellen Sie ein Workflow-Modell</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-users</td> 
   <td>
    <ul> 
     <li>Verwenden Sie AEM-Posteingangs-Anwendungen<br /> <strong>Hinweis: </strong>Sie müssen über Gruppenzuweisungen für „cm-agent-users“ und „workflow-users“ verfügen, um im AEM-Posteingang auf die Benutzeroberfläche des Interactive Communications Agent zuzugreifen.</li> 
     <li>Verwalten von Workflow-Instanzen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Konfigurieren von PDF Generator</li> 
     <li>Konfigurieren des überwachten Ordners</li> 
     <li>Verwalten von Workflow-Programmen</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. Der Benutzer mit „forms-users group“-Berechtigungen kann keine Skripte für adaptive Formulare schreiben.
1. Der Benutzer mit Gruppenberechtigungen für Vorlagenautoren kann keine Skripte für Vorlagen schreiben.
