---
title: AEM Forms für OSGi-Gruppen und -Berechtigungen
description: Benutzer Gruppen zuweisen, um Adobe Experience Manager (AEM) Forms auf OSGi zu verwalten
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: Configuration
docset: aem65
role: Admin
exl-id: d802ac53-e3db-45ca-afcb-7e99d0bb7877
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 56%

---

# AEM Forms für OSGi-Gruppen und -Berechtigungen{#aem-forms-on-osgi-groups-and-privileges}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Sie können [Gruppen erstellen](/help/sites-administering/user-group-ac-admin.md#group-administration) und Richtlinien zuweisen und [Benutzer](/help/sites-administering/user-group-ac-admin.md#user-administration) zu den Gruppen in Adobe Experience Manager (AEM). Diese Richtlinien steuern die Berechtigungen der Benutzer, die Teil der Gruppe sind.

Nach der Installation [AEM Forms Add-On-Paket](../../forms/using/installing-configuring-aem-forms-osgi.md), sind die in diesem Artikel erwähnten Gruppen, wie Formularbenutzer und Formular-Power-Benutzer, automatisch für die Zuweisung verfügbar. In der folgenden Tabelle sind die Aufgaben aufgeführt, die ein Benutzer je nach Gruppenzuweisung für AEM Forms unter OSGi ausführen kann:

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
     <li>Erstellen von Skripten für adaptive Formulare mithilfe eines Code-Editors</li> 
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
     <li>Verwenden AEM Inbox-Anwendungen<br /> <strong>Hinweis: </strong>Sie müssen über Gruppenzuweisungen für cm-agent-users und workflow-users verfügen, um in AEM Posteingang auf die Benutzeroberfläche für interaktive Kommunikationsagenten zugreifen zu können.</li> 
     <li>Verwalten von Workflow-Instanzen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>Konfigurieren von PDF Generator</li> 
     <li>Überwachten Ordner konfigurieren</li> 
     <li>Verwalten von Workflow-Programmen</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. Der Benutzer mit „forms-users group“-Berechtigungen kann keine Skripte für adaptive Formulare schreiben.
1. Der Benutzer mit Gruppenberechtigungen für Vorlagenautoren kann keine Skripte für Vorlagen schreiben.
