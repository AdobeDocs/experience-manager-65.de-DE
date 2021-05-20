---
title: Konfigurationseigenschaften für interaktive Kommunikation
seo-title: Konfigurationseigenschaften für interaktive Kommunikation
description: Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikation
seo-description: Bearbeiten Sie die Standardkonfigurationseigenschaften für interaktive Kommunikation
uuid: 4030078f-64a3-40bb-9892-49e22a8da561
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: acb61d37-cd22-422e-bbf3-a2979b13ad41
docset: aem65
feature: Interaktive Kommunikation
exl-id: 09eeade6-e16d-4159-b26a-803c7201097a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 60%

---

# Konfigurationseigenschaften für interaktive Kommunikation{#interactive-communications-configuration-properties}

Interaktive Kommunikation enthält Eigenschaften, die nach der Installation des Pakets [AEM Forms Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) automatisch konfiguriert werden. Autoren der interaktiven Kommunikation können diese Standardkonfigurationseigenschaften mit Hilfe der Seite **Konfiguration von Adobe Experience Manager Web Console** bearbeiten.

Öffnen Sie die Seite **Adobe Experience Manager Web Console Configuration** mithilfe der folgenden URL:

`https:/[server]:[port]/<contextPath>/system/console/configMgr`

Die Konfigurationseigenschaften umfassen Folgendes:

* [Konfiguration für Dokumentfragment](#document-fragments-configuration)
* [Korrespondenzkonfiguration erstellen](#create-correspondence-configuration)
* [Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Konfiguration für Dokumentfragment {#document-fragments-configuration}

Tippen Sie auf **Document Fragments configuration** auf der Seite **Adobe Experience Manager Web Console Configuration** , um die Konfigurationseigenschaften für Dokumentfragmente anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Default</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Datenanzeigeformate</td> 
   <td>Gebietsschemaspezifisches Anzeigeformat für Felder, Variablen und Formulardatenmodellelemente, die beim Erstellen einer interaktiven Kommunikation für Druck- und Webkanäle verfügbar sind.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR und ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Einzug</td> 
   <td>Die Breite der einzelnen Einzugseinheit, die auf den Text in Listendokumentfragmenten angewendet wird.</td> 
   <td>12.7mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite von römischen Zahlen</td> 
   <td>Mindestbreite für das Aufzählungsfeld oder Zahlenfeld, wenn römische Zahlen in Listendokumentfragmenten verwendet werden. </td> 
   <td>12.7 mm</td> 
   <td>Zahl</td> 
  </tr> 
  <tr> 
   <td>Mindestbreite von Nummer</td> 
   <td>Mindestbreite für das Aufzählungsfeld oder Zahlenfeld, wenn römische Zahlen in Listendokumentfragmenten verwendet werden.</td> 
   <td>8.0mm</td> 
   <td>Number-Wert</td> 
  </tr> 
 </tbody> 
</table>

## Korrespondenzkonfiguration erstellen {#create-correspondence-configuration}

Tippen Sie auf **Korrespondenzkonfiguration erstellen** auf der Seite **Adobe Experience Manager Web Console Configuration** , um die Konfigurationseigenschaften für die Agent-Benutzeroberfläche anzuzeigen.

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
   <td>Aktivieren Sie das Kontrollkästchen, um aufgelösten Inhalt (tatsächliche Werte anstelle von Platzhaltern) anzuzeigen, während Sie Textmodule auf der Agentenbenutzeroberfläche bearbeiten.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Wasserzeichen während der Vorschau anwenden</td> 
   <td>Aktivieren Sie das Kontrollkästchen, um ein Wasserzeichen auf den Druckkanal der interaktiven Kommunikation im Vorschaumodus anzuwenden.</td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
  <tr> 
   <td>Aktivieren der Schrifteinbettung in PDF</td> 
   <td><p>Aktivieren Sie das Kontrollkästchen, um das Einbetten von Schriftarten in PDF-Dokumente zu aktivieren. Nach Auswahl dieser Option können Sie neue Schriftarten einbetten, nachdem Sie die PDF-Dokumente über die Benutzeroberfläche für Agenten generiert oder in der Vorschau angezeigt haben. Verwenden Sie den Druckkanal der interaktiven Kommunikation, um PDF-Dokumente zu generieren und in der Vorschau anzuzeigen.</p> <p>Das Einbetten von Schriftarten in ein PDF-Dokument ist nützlich, wenn eine Schriftart auf einem Computer verfügbar ist, der zum Generieren der PDF-Datei verwendet wird, und nicht auf dem Clientcomputer verfügbar ist, der auf die PDF-Datei zugreift.</p> <p>Weitere Informationen zum Einbetten von Schriftarten finden Sie unter <a href="../../forms/using/customize-text-editor.md" target="_blank">Texteditor anpassen</a>.</p> </td> 
   <td>Nicht ausgewählt</td> 
   <td>Nicht zutreffend</td> 
  </tr> 
 </tbody> 
</table>

## Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation  {#adaptive-form-and-interactive-communication-web-channel-configuration}

Tippen Sie auf **Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation** auf der Seite **Adobe Experience Manager Web Console Configuration** , um die Konfigurationseigenschaften für den Webkanal für adaptive Forms und interaktive Kommunikation anzuzeigen. Die folgende Tabelle beschreibt die Eigenschaften, die sich auf die interaktive Kommunikation bezieht:

| Eigenschaft | Beschreibung | Standard | Zulässige Werte |
|---|---|---|---|
| Platzhalter anzeigen | Aktivieren Sie das Kontrollkästchen, um die Anzeige von Platzhaltern für Felder zu aktivieren, die in adaptiven Formularen und in interaktiver Kommunikation enthalten sind. | Ausgewählt | Nicht zutreffend |
| Maximale Cache-Einträge | Legen Sie die maximale Anzahl an adaptiven Formularen und interaktiver Kommunikation fest, die mithilfe des Cache-Speichers abgerufen werden können. | 100 | Zahl |
| Dateinamen als eindeutig festlegen | Aktivieren Sie das Kontrollkästchen, um eindeutige Namen für Dateien zu erhalten, die als Anhänge in adaptiven Formularen und interaktiver Kommunikation enthalten sind. | Nicht ausgewählt | Nicht zutreffend |

## Webkanalthemen-Konfiguration für adaptive Formulare und interaktive Kommunikation  {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Tippen Sie auf der Seite **Web-Kanal-Designkonfiguration für adaptive Formulare und interaktive Kommunikation** auf der Seite **Adobe Experience Manager Web Console Configuration** , um die Konfigurationseigenschaften für Webkanalthemen für adaptive Forms und interaktive Kommunikation anzuzeigen.

<table>
 <tbody> 
  <tr> 
   <td>Eigenschaft</td> 
   <td>Beschreibung</td> 
   <td>Standard</td> 
   <td>Zulässige Werte</td> 
  </tr> 
  <tr> 
   <td>Name der Schriftartliste</td> 
   <td>Liste der Schriftarten, die beim Erstellen von adaptiven Formularen und interaktiver Kommunikation verwendet werden können.</td> 
   <td><p>Georgia</p> <p>Buch Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial Schwarz</p> <p>Auswirkungen</p> <p>Palatino-Linotyp</p> </td> 
   <td>Alle gültigen Adobe-Server-Schriftarten</td> 
  </tr> 
 </tbody> 
</table>
