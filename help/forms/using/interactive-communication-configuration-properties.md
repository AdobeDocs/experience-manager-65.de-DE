---
title: Konfigurationseigenschaften für interaktive Kommunikation
description: Bearbeiten von Standardkonfigurationseigenschaften für interaktive Kommunikation
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: interactive-communications
docset: aem65
feature: Interactive Communication
exl-id: 09eeade6-e16d-4159-b26a-803c7201097a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '610'
ht-degree: 48%

---

# Konfigurationseigenschaften für interaktive Kommunikation{#interactive-communications-configuration-properties}

Interaktive Kommunikation enthält Eigenschaften, die nach der Installation des Pakets [AEM Forms Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) automatisch konfiguriert werden. Autoren der interaktiven Kommunikation können diese Standardkonfigurationseigenschaften mit Hilfe der Seite **Konfiguration von Adobe Experience Manager Web Console** bearbeiten.

Öffnen Sie die Seite für die **Konfiguration von Adobe Experience Manager Web Console** unter der folgenden URL:

`https:/[server]:[port]/<contextPath>/system/console/configMgr`

Die Konfigurationseigenschaften umfassen Folgendes:

* [Konfiguration für Dokumentfragment](#document-fragments-configuration)
* [Korrespondenzkonfiguration erstellen](#create-correspondence-configuration)
* [Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Konfiguration für Dokumentfragment {#document-fragments-configuration}

Auswählen **Konfiguration von Dokumentfragmenten** auf **Konfiguration der Adobe Experience Manager-Web-Konsole** Seite, um die Konfigurationseigenschaften für Dokumentfragmente anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Datenanzeigeformate</td> 
   <td>Gebietsschema-spezifisches Anzeigeformat für Felder, Variablen und Formulardatenmodellelemente, die beim Erstellen einer interaktiven Kommunikation für Druck- und Webkanäle verfügbar sind.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR und ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>--</p> </td> 
  </tr> 
  <tr> 
   <td>Einzug</td> 
   <td>Die Breite einer Einzugseinheit, die auf Text in Listendokumentfragmenten angewendet wird.</td> 
   <td>12,7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite bei römischen Zahlen</td> 
   <td>Mindestbreite für das Aufzählungs- oder Zahlenfeld bei Verwendung von römischen Zahlen in Listendokumentfragmenten. </td> 
   <td>12,7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite bei Zahlen</td> 
   <td>Mindestbreite für das Aufzählungs- oder Zahlenfeld bei nummerierten Listen, mit Ausnahme der römischen Zahlen in Listendokumentfragmenten.</td> 
   <td>8,0 mm</td> 
   <td>Zahl</td> 
  </tr> 
 </tbody> 
</table>

## Erstellen der Korrespondenzkonfiguration {#create-correspondence-configuration}

Auswählen **Korrespondenzkonfiguration erstellen** auf **Konfiguration der Adobe Experience Manager-Web-Konsole** Seite, um die Konfigurationseigenschaften für die Benutzeroberfläche für Agenten anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Gelösten Inhalt zur Bearbeitung anzeigen</td> 
   <td>Aktivieren Sie das Kontrollkästchen, um aufgelösten Inhalt (tatsächliche Werte anstelle von Platzhaltern) beim Bearbeiten des Textmoduls auf der Benutzeroberfläche für Agenten anzuzeigen.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Anwenden von Wasserzeichen während der Vorschau</td> 
   <td>Aktivieren Sie das Kontrollkästchen, um das Wasserzeichen auf den Druckkanal der interaktiven Kommunikation im Vorschaumodus anzuwenden.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Aktivieren der Schrifteinbettung in PDF</td> 
   <td><p>Aktivieren Sie das Kontrollkästchen, um das Einbetten von Schriftarten in die PDF-Dokumente zu aktivieren. Nach Auswahl dieser Option können Sie neue Schriftarten einbetten, nachdem Sie die PDF-Dokumente über die Benutzeroberfläche für Agenten generiert oder in der Vorschau angezeigt haben. Verwenden Sie den Druckkanal der interaktiven Kommunikation, um PDF-Dokumente zu generieren und in der Vorschau anzuzeigen.</p> <p>Das Einbetten von Schriftarten in ein PDF-Dokument ist nützlich, wenn eine Schriftart auf einem Computer verfügbar ist, der zum Generieren des PDF verwendet wird, und nicht auf dem Clientcomputer verfügbar ist, der auf das PDF zugreift.</p> <p>Weitere Informationen zum Einbetten von Schriftarten finden Sie unter <a href="../../forms/using/customize-text-editor.md" target="_blank">Texteditor anpassen</a>.</p> </td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

## Konfiguration des Web-Kanals für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-configuration}

Auswählen **Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation** auf **Konfiguration der Adobe Experience Manager-Web-Konsole** Seite, um die Konfigurationseigenschaften für den Webkanal &quot;Adaptive Forms&quot;und &quot;Interaktive Kommunikation&quot;anzuzeigen. In der folgenden Tabelle werden die Eigenschaften im Zusammenhang mit interaktiver Kommunikation beschrieben:

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Platzhalter anzeigen | Aktivieren Sie das Kontrollkästchen, um die Anzeige von Platzhaltern für Felder zu aktivieren, die in adaptiven Formularen und interaktiver Kommunikation enthalten sind. | Ausgewählt | Nicht zutreffend |
| Maximale Cache-Einträge | Legen Sie die maximale Anzahl adaptiver Formulare und interaktiver Kommunikation fest, die mithilfe des Cache-Speichers abgerufen werden können. | 100 | Zahl |
| Dateinamen eindeutig machen | Aktivieren Sie das Kontrollkästchen, um eindeutige Namen für Dateien zu erhalten, die als Anhänge in Adaptive Forms und interaktive Kommunikation enthalten sind. | Nicht ausgewählt | Nicht zutreffend |

## Konfiguration der Web-Kanalthemen für adaptive Formulare und interaktive Kommunikation {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Auswählen **Webkanal-Designkonfiguration für adaptive Formulare und interaktive Kommunikation** auf **Konfiguration der Adobe Experience Manager-Web-Konsole** Seite, um die Konfigurationseigenschaften für Webkanalthemen zu adaptiven Forms- und interaktiven Kommunikationen anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Schriftlistenname</td> 
   <td>Liste der Schriftarten, die beim Erstellen der adaptiven Forms- und interaktiven Kommunikation verwendet werden können.</td> 
   <td><p>Georgia</p> <p>Buch Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Schwarz</p> <p>Auswirkungen</p> <p>Palatino-Linotyp</p> </td> 
   <td>Alle gültigen Adobe-Serverschriftarten</td> 
  </tr> 
 </tbody> 
</table>
