---
title: Von Acrobat Reader DC Extensions verwendete Zertifikatstypen
description: Erfahren Sie mehr über die Zertifikatstypen, die von Acrobat Reader DC-Erweiterungen verwendet werden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 800bffd5-0cdc-4251-bba4-e350f226f019
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 23%

---

# Von Acrobat Reader DC Extensions verwendete Zertifikatstypen {#certificate-types-used-by-acrobat-reader-dc-extensions}

Die Zertifikatanzeige stellt die folgenden Informationen zum Zertifikat bereit:

* Anzeigename des Zertifikats
* Zertifikatprofile
* Gültigkeitsdauer
* Verwendungsrechte für Acrobat Reader DC Extensions

## Anzeigename des Zertifikats {#certificate-friendly-name}

Der Anzeigename eines Acrobat Reader DC Extensions-Zertifikats ist eine Zeichenfolge, die die Eigenschaften des Zertifikats beschreibt, wie im folgenden Beispiel gezeigt:

ARE 2D Barcode Full Production V6.1 P8 0002054

Die Zeichenfolge enthält die folgenden Elemente:

**Zertifikatstyp:** Beschreibt die AEM Forms-Module, die das Zertifikat aktiviert, sowie den Grad der Aktivierung (beispielsweise ARE 2D Barcode Full). Eine Liste der verfügbaren Zertifikatstypen finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Typ“.

**Bereitstellungstyp:** Gibt den vorgesehenen Zweck des Zertifikats an (z. B. Produktion). Der Wert kann „Test“ oder „Produktion“ lauten. Eine Liste der Bereitstellungstypen für jeden Zertifikatstyp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Bereitstellungstyp“.

**Verwendungsrechteversion:** Beschreibt die Version des Verwendungsrechtealgorithmus, für die das Zertifikat verwendet werden kann (z. B. V6.1). Diese Version gibt nicht die Version von Acrobat oder Acrobat Reader DC Extensions an.

**Profilcode:** Der Profilcode ist eine Kurzbeschreibung der vollständigen Zertifikateigenschaften (beispielsweise P8). Eine Liste der Profilcodes für jeden Dateityp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Profilcode“.

**Seriennummer:** Jedem von Adobe ausgestellten Zertifikat wird eine Seriennummer zugewiesen (z. B. 0002054). Adobe Enterprise Support oder ein Adobe Enterprise-Kundenbetreuer können diese Seriennummer verwenden, um das Zertifikat auf eine bestimmte Produktbestellung oder auf eine OEM-Beziehung zu verfolgen.

## Zertifikatprofile {#certificate-profiles}

In der folgenden Tabelle sind die Zertifikatprofile aufgeführt, auf die Sie bei der Analyse von Acrobat Reader DC Extensions-Zertifikaten stoßen können.

<table>
 <thead>
  <tr>
   <th><p>Profilcode</p></th>
   <th><p>Typ</p></th>
   <th><p>Gültigkeitsdauer</p></th>
   <th><p>Bereitstellungstyp</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>P1</p></td>
   <td><p>SAP-Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P2</p></td>
   <td><p>SAP Interner Test</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Auswertung und Test</p></td>
  </tr>
  <tr>
   <td><p>P3</p></td>
   <td><p>Acrobat Reader DC-Erweiterungen, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P4</p></td>
   <td><p>Acrobat Reader DC-Erweiterungen, interne Adobe-Verwendung</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P5</p></td>
   <td><p>Acrobat Reader DC-Erweiterungen, Partnerintegration</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Auswertung und Test</p></td>
  </tr>
  <tr>
   <td><p>P6</p></td>
   <td><p>Acrobat Reader DC-Erweiterungen, Auswertung</p></td>
   <td><p>60 Tage</p></td>
   <td><p>Test</p></td>
  </tr>
  <tr>
   <td><p>P8</p></td>
   <td><p>Forms, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P9</p></td>
   <td><p>Adobe Acrobat 7.x, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>I10</p></td>
   <td><p>Forms; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I11</p></td>
   <td><p>Forms; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I12</p></td>
   <td><p>Nur Signatur; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I13</p></td>
   <td><p>Nur Offline-Kommentierung; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I14</p></td>
   <td><p>Nur Kommentierung; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
  <tr>
   <td><p>I15</p></td>
   <td><p>Vollständige Berechtigungen; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Auswertung</p></td>
  </tr>
 </tbody>
</table>

## Gültigkeitsdauer {#validity-period}

Testzertifikate werden Kunden und Entwicklern ausgestellt, damit sie Beispielanwendungen für Produkte auswerten und entwickeln können. Die Gültigkeitsdauer dieser Zertifikate beträgt 60 bis 90 Tage. Sie laufen am Ende des zweiten Monats ab, der auf die Ausgabedaten folgt.

Partnerintegrationszertifikate werden an Adobe-Geschäftspartner ausgestellt, um die Softwareentwicklung, -integration, -prototypisierung und -demonstration zu unterstützen. Diese Zertifikate sind ab dem Ausstellungsdatum zwei Jahre lang gültig.

Adobe Internal Use-Zertifikate werden innerhalb von Adobe verwendet, um Softwareentwicklung, -integration, -prototypisierung und -demonstration zu unterstützen. Diese Zertifikate sind ab dem Ausstellungsdatum zwei Jahre lang gültig.

Produktionszertifikate werden Kunden ausgestellt, die Acrobat Reader DC-Erweiterungen erworben haben. Diese Zertifikate gelten für den von der Zertifizierungsstelle (CA) maximal zulässigen Zeitraum, wie hier angegeben: *Max* in der Tabelle &quot;Zertifikatprofile&quot;ein.

## Verwendungsrechte für Acrobat Reader DC Extensions {#acrobat-reader-dc-extensions-usage-rights}

Wenn Sie das Acrobat Reader DC Extensions-Zertifikat in der Zertifikatanzeige untersuchen, können Sie das Element Verwendungsrechte auf der Registerkarte Details auswählen (sofern konfiguriert), um eine Auflistung der Adobe Reader-Verwendungsrechte anzuzeigen, die das Zertifikat aktivieren kann. Die für ein bestimmtes Dokument aktivierten Verwendungsrechte können eine Teilmenge der vom Zertifikat aktivierten Rechte sein.

Wenn Onlinekommentierung in einer nicht kollaborativen Umgebung erforderlich ist, wenden Sie sich für weitere Informationen an den Adobe Support. Die Mode-Eigenschaft stimmt mit dem Bereitstellungstyp überein und entspricht entweder *production* oder *Evaluierung*.

Die zulässigen Acrobat Reader DC Extensions-Verwendungsrechte bestehen aus einem oder mehreren bestimmten Elementen. Diese Elemente werden in verschiedenen Kombinationen verwendet, um verschiedene lizenzierte Produktfunktionen zu erzielen.

<table>
 <thead>
  <tr>
   <th><p>Element "Verwendungsrechte"</p></th>
   <th><p>Funktion in Adobe Reader aktiviert, wenn ein PDF-Dokument mit aktivierten Benutzerrechten angezeigt wird</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>FormFillInAndSave</p></td>
   <td><p>Füllen Sie die Formularfelder aus und speichern Sie die Dateien lokal.</p></td>
  </tr>
  <tr>
   <td><p>FormImportExport</p></td>
   <td><p>Importieren und exportieren Sie Formulardaten als FDF-, XFDF-, XML- und XDP-Dateien.</p></td>
  </tr>
  <tr>
   <td><p>FormAddDelete</p></td>
   <td><p>Hinzufügen, Ändern oder Löschen von Feldern und Feldeigenschaften auf dem PDF-Formular.</p></td>
  </tr>
  <tr>
   <td><p>SubmitStandalone</p></td>
   <td><p>Senden Sie Daten per E-Mail oder offline an einen Server, wenn dieser nicht in einer Browsersitzung ausgeführt wird.</p></td>
  </tr>
  <tr>
   <td><p>SpawnTemplate</p></td>
   <td><p>Erstellen Sie Seiten aus Vorlagenseiten innerhalb desselben PDF-Formulars.</p></td>
  </tr>
  <tr>
   <td><p>Signing</p></td>
   <td><p>Digitales Signieren und Speichern von PDF-Dokumenten und Löschen digitaler Signaturen.</p></td>
  </tr>
  <tr>
   <td><p>AnnotModify</p></td>
   <td><p>Dokumentanmerkungen wie Kommentare erstellen und ändern.</p></td>
  </tr>
  <tr>
   <td><p>AnnotImportExport</p></td>
   <td><p>Speichern Sie Anmerkungen wie Kommentare in einer separaten Datendatei und laden Sie Kommentare aus einer Datei.</p></td>
  </tr>
  <tr>
   <td><p>BarcodePlaintext</p></td>
   <td><p>Drucken Sie ein Dokument mit Formulardaten, die in unverschlüsselter Form mit Strichcode versehen sind und für die keine lizenzierte Serversoftware zum Dekodieren erforderlich ist.</p></td>
  </tr>
  <tr>
   <td><p>AnnotOnline</p></td>
   <td><p>Laden Sie Anmerkungen wie Kommentare von und auf einen Online-Dokumentüberprüfungs- und -Kommentar-Server hoch und laden Sie sie herunter.</p></td>
  </tr>
  <tr>
   <td><p>FormOnline</p></td>
   <td><p>Stellen Sie eine Verbindung zu Webdiensten oder Datenbanken her, die in einem PDF-Formular definiert sind.</p></td>
  </tr>
  <tr>
   <td><p>EFModif</p></td>
   <td><p>Ändern Sie die eingebetteten Dateiobjekte, die mit dem PDF-Dokument verknüpft sind.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Acrobat Reader DC Extensions-Verwendungsrechte können nur in bestimmten Kombinationen, die zusammenarbeiten, von Adobe lizenziert werden. Es ist nicht möglich, diese Funktionen unabhängig zu lizenzieren. Informationen zu den verfügbaren Kombinationen von Verwendungsrechten erhalten Sie von einem AEM Forms-Kundenbetreuer.
