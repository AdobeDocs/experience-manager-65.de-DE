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
translation-type: tm+mt
source-git-commit: 76908a565bf9e6916db39d7db23c04d2d40b3247

---


# AEM Forms für OSGi-Gruppen und -Berechtigungen{#aem-forms-on-osgi-groups-and-privileges}

Sie können [Gruppen erstellen](/help/sites-administering/user-group-ac-admin.md#group-administration) und Richtlinien zuweisen und [Benutzer](/help/sites-administering/user-group-ac-admin.md#user-administration) zu den Gruppen in AEM zuweisen. Diese Richtlinien steuern die Berechtigungen der Benutzer, die Teil der Gruppe sind.

Sobald Sie [AEM Forms Add-On-Paket](../../forms/using/installing-configuring-aem-forms-osgi.md) installiert haben, werden die in diesem Artikel genannten Gruppen, wie Formularbenutzer und Formular-Power-Benutzer automatisch für die Zuordnung zur Verfügung gestellt. In der folgenden Tabelle sind die Aufgaben aufgeführt, die ein Benutzer für AEM Forms auf OSGi basierend auf den Gruppenzuweisungen ausführen kann:

<table>
 <tbody>
  <tr>
   <td>Gruppe</td> 
   <td>Aufgaben</td> 
  </tr>
  <tr>
   <td>forms-user <sup><a href="#main-pars-text">[1]</a></sup></td> 
   <td>
    <ul> 
     <li>Erstellen Sie eine Vorschau, veröffentlichen und senden Sie adaptive Formulare</li> 
     <li>Interaktive Kommunikation und Dokumentfragmente erstellen, in der Vorschau anzeigen und veröffentlichen</li> 
     <li>Assets in eine AEM-Instanz hochladen</li> 
     <li>Themen erstellen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Formular-Power-Benutzer</td> 
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
   <td>template-authors <sup><a href="#main-pars-text">[2]</a></sup></td> 
   <td>
    <ul> 
     <li>Adaptive Formulare oder interaktive Kommunikationsvorlagen erstellen oder in der Vorschau anzeigen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-power-user</td> 
   <td>
    <ul> 
     <li>Adaptive Formulare oder interaktive Kommunikationsvorlagen erstellen oder in der Vorschau anzeigen</li> 
     <li>Erstellen von Skripten für adaptive Formulare oder interaktive Kommunikationsvorlagen mit dem Code-Editor</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-authors</p> </td> 
   <td>
    <ul> 
     <li>Formulardatenmodell erstellen und ändern</li> 
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
     <li>Workflow-Modell erstellen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflow-users</td> 
   <td>
    <ul> 
     <li>AEM-Posteingangsanwendungen<br /> verwenden <strong>Hinweis: Für </strong>den Zugriff auf die Benutzeroberfläche von Interactive Communications Agent im AEM-Posteingang müssen cm-agent-users und Gruppen von Workflow-Benutzern zugewiesen sein.</li> 
     <li>Workflow-Instanzen verwalten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-administrators</td> 
   <td>
    <ul> 
     <li>PDF Generator konfigurieren</li> 
     <li>Überwachten Ordner konfigurieren</li> 
     <li>Workflow-Anwendungen verwalten</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. Der Benutzer mit Berechtigungen für Formularbenutzergruppen kann keine Skripte für adaptive Formulare schreiben.
1. Der Benutzer mit Gruppenberechtigungen für Vorlagenautoren kann keine Skripte für Vorlagen schreiben.

