---
title: AEM Forms für OSGi-Gruppen und -Berechtigungen
seo-title: AEM Forms für OSGi-Gruppen und -Berechtigungen
description: Weisen Sie den Gruppen Benutzer zu, um AEM Forms auf OSGi zu verwalten
seo-description: Weisen Sie den Gruppen Benutzer zu, um AEM Forms auf OSGi zu verwalten
uuid: f269a206-356d-4cee-b449-05c5da87121a
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: Configuration
discoiquuid: 1717b1b4-1c2a-450e-8e79-4156a974d5fa
docset: aem65
role: Admin
exl-id: d802ac53-e3db-45ca-afcb-7e99d0bb7877
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 79%

---

# AEM Forms für OSGi-Gruppen und -Berechtigungen{#aem-forms-on-osgi-groups-and-privileges}

Sie können [Gruppen erstellen](/help/sites-administering/user-group-ac-admin.md#group-administration) und Richtlinien zuweisen und [Benutzer](/help/sites-administering/user-group-ac-admin.md#user-administration) zu den Gruppen in AEM zuweisen. Diese Richtlinien steuern die Berechtigungen der Benutzer, die Teil der Gruppe sind.

Nachdem Sie [AEM Forms Add-On-Paket](../../forms/using/installing-configuring-aem-forms-osgi.md) installiert haben, stehen die in diesem Artikel genannten Gruppen, wie z. B. Formularbenutzer und Formular-Power-User, automatisch für die Zuweisung zur Verfügung. In der folgenden Tabelle sind die Aufgaben aufgeführt, die ein Benutzer für AEM Forms auf OSGi basierend auf den Gruppenzuweisungen ausführen kann:

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
     <li>Erstellen Sie eine Vorschau, veröffentlichen und senden Sie adaptive Formulare</li> 
     <li>Interaktive Kommunikation und Dokumentfragmente erstellen, in der Vorschau anzeigen und veröffentlichen</li> 
     <li>Assets in eine AEM-Instanz hochladen</li> 
     <li>Themen erstellen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>forms-power-users</td> 
   <td>
    <ul> 
     <li>Erstellen Sie eine Vorschau, veröffentlichen und senden Sie adaptive Formulare</li> 
     <li>Interaktive Kommunikation und Dokumentfragmente erstellen, in der Vorschau anzeigen und veröffentlichen</li> 
     <li>Erstellen Sie Skripte für adaptive Formulare mit dem Code-Editor</li> 
     <li>Laden Sie Assets einschließlich Skripte hoch</li> 
     <li>Themen erstellen</li> 
     <li>Importieren Sie Pakete, die XDP enthalten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Reviewer für Formularübermittlung</td> 
   <td>
    <ul> 
     <li>Übermittlungen überprüfen</li> 
     <li>Übermittlungen genehmigen oder ablehnen</li> 
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
     <li>Auf Correspondence Management-Briefe oder interaktive Kommunikation über die Benutzeroberfläche des Agenten zugreifen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workflow-editors</p> </td> 
   <td>
    <ul> 
     <li>Erstellen einer Posteingangs-Anwendung</li> 
     <li>Erstellen eines Workflow-Modells</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-users</td> 
   <td>
    <ul> 
     <li>Verwenden Sie AEM Posteingangsanwendungen<br /> <strong>Hinweis: </strong>Sie müssen über cm-agent-users und workflow-users-Gruppenzuweisungen verfügen, um auf die Benutzeroberfläche von Interactive Communications Agent im Posteingang zuzugreifen.</li> 
     <li>Workflow-Instanzen verwalten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>PDF Generator konfigurieren</li> 
     <li>Überwachten Ordner konfigurieren</li> 
     <li>Verwalten von Workflow-Programmen</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. Benutzer mit Gruppenberechtigungen für Formularbenutzer können keine Skripte für adaptive Formulare schreiben.
1. Der Benutzer mit Gruppenberechtigungen für Vorlagenautoren kann keine Skripte für Vorlagen schreiben.
