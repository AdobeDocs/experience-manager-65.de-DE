---
title: Von Acrobat Reader DC Extensions verwendete Zertifikatstypen
seo-title: Von Acrobat Reader DC Extensions verwendete Zertifikatstypen
description: Erfahren Sie mehr über die Zertifikatstypen, die in Acrobat Reader DC-Erweiterungen verwendet werden.
seo-description: Erfahren Sie mehr über die Zertifikatstypen, die in Acrobat Reader DC-Erweiterungen verwendet werden.
uuid: 93c02abc-2d5a-44ed-b93c-981afbd0553d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 331b9317-87b5-4a96-a1bc-429675ff90c5
exl-id: 800bffd5-0cdc-4251-bba4-e350f226f019
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '955'
ht-degree: 89%

---

# Von Acrobat Reader DC Extensions verwendete Zertifikatstypen {#certificate-types-used-by-acrobat-reader-dc-extensions}

Die Zertifikatsanzeige enthält die folgenden Informationen zum Zertifikat:

* Anzeigenamen des Zertifikats
* Zertifikatprofile
* Gültigkeitsdauer
* Acrobat Reader DC Extensions-Verwendungsrechte

## Anzeigenamen des Zertifikats {#certificate-friendly-name}

Der Anzeigename eines Acrobat Reader DC Extensions-Zertifikats ist eine Zeichenfolge mit den Eigenschaften des Zertifikats (siehe folgendes Beispiel):

ARE 2D Barcode Full Production V6.1 P8 0002054

Die Zeichenfolge enthält folgende Elemente:

**Zertifikatstyp:** Beschreibt die AEM Formularmodule, die vom Zertifikat aktiviert werden, und den Aktivierungsgrad, z. B. ARE 2D Barcode Full. Eine Liste der verfügbaren Zertifikatstypen finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Typ“.

**Bereitstellungstyp:** Gibt die vorgesehene Verwendung des Zertifikats an, z. B. Produktion. Der Wert kann „Test“ oder „Produktion“ lauten. Eine Liste der Bereitstellungstypen für jeden Zertifikatstyp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Bereitstellungstyp“.

**Version der Verwendungsrechte:** Beschreibt die Version des Verwendungsrechtealgorithmus, für die das Zertifikat verwendet werden kann, z. B. V6.1. Diese Version gibt nicht die Version der Acrobat- oder Acrobat Reader DC-Erweiterungen an.

**Profilcode:** Der Profilcode ist eine Kurzbeschreibung der vollständigen Zertifikateigenschaften, z. B. P8. Eine Liste der Profilcodes für jeden Dateityp finden Sie im Abschnitt „Zertifikatprofile“ in der Tabelle in der Spalte „Profilcode“.

**Seriennummer:** Jedem von der Adobe ausgestellten Zertifikat wird eine Seriennummer zugewiesen, z. B. 0002054. Der Support von Adobe Enterprise oder ein Adobe Enterprise-Kundenbetreuer kann anhand dieser Seriennummer das Zertifikat einer bestimmten Produktbestellung oder einem OEM-Vertrag zuordnen.

## Zertifikatprofile  {#certificate-profiles}

Die folgende Tabelle enthält die Zertifikatprofile, die Sie beim Analysieren von Acrobat Reader DC Extensions-Zertifikaten vorfinden können.

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
   <td><p>SAP- Interner Test</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Testversion</p></td>
  </tr>
  <tr>
   <td><p>P3</p></td>
   <td><p>Acrobat Reader DC Extensions, Produktion</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P4</p></td>
   <td><p>Acrobat Reader DC Extensions, Interne Verwendung durch Adobe</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Produktion</p></td>
  </tr>
  <tr>
   <td><p>P5</p></td>
   <td><p>Acrobat Reader DC Extensions, Partnerintegration</p></td>
   <td><p>2 Jahre</p></td>
   <td><p>Testversion</p></td>
  </tr>
  <tr>
   <td><p>P6</p></td>
   <td><p>Acrobat Reader DC Extensions, Text</p></td>
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
   <td><p>Produktion und Test</p></td>
  </tr>
  <tr>
   <td><p>I11</p></td>
   <td><p>Forms; kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Test</p></td>
  </tr>
  <tr>
   <td><p>I12</p></td>
   <td><p>Nur Signatur. Kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Test</p></td>
  </tr>
  <tr>
   <td><p>I13</p></td>
   <td><p>Nur Offline-Kommentierung. Kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Test</p></td>
  </tr>
  <tr>
   <td><p>I14</p></td>
   <td><p>Nur Kommentierung. Kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Test</p></td>
  </tr>
  <tr>
   <td><p>I15</p></td>
   <td><p>Vollständige Berechtigungen. Kann von OEMs verwendet werden</p></td>
   <td><p>Maximal</p></td>
   <td><p>Produktion und Test</p></td>
  </tr>
 </tbody>
</table>

## Gültigkeitsdauer  {#validity-period}

Testzertifikate werden Kunden und Entwicklern ausgestellt, damit diese Beispielanwendungen für Produkte entwickeln und testen können. Die Gültigkeitsdauer dieser Zertifikate ist 60 bis 90 Tage. Der Ablauf erfolgt am Ende des zweiten Monats nach dem Datum der Ausstellung.

Zertifikate für die Partnerintegration werden Adobe-Geschäftspartnern ausgestellt, um die Softwareentwicklung, Integration, Erstellung von Prototypen und Demos zu unterstützen. Diese Zertifikate gelten zwei Jahre ab dem Ausstellungsdatum.

Zertifikate für die interne Verwendung bei Adobe werden innerhalb des Unternehmens Adobe verwendet, um die Softwareentwicklung, Integration, Erstellung von Prototypen und Demos zu unterstützen. Diese Zertifikate gelten zwei Jahre ab dem Ausstellungsdatum.

Produktionszertifikate werden an Kunden, die Acrobat Reader DC Extensions erworben haben, ausgegeben. Diese Zertifikate sind für den von der Zertifizierungsstelle maximal zugelassenen Zeitraum gültig (siehe die Spalte „*Maximal*“ in der Tabelle „Zertifikatprofile“).

## Acrobat Reader DC Extensions-Verwendungsrechte  {#acrobat-reader-dc-extensions-usage-rights}

Wenn Sie das Acrobat Reader DC Extensions-Zertifikat in der Zertifikatanzeige untersuchen, können Sie das Element „Verwendungsrechte“ auf der Registerkarte „Details“ auswählen (falls konfiguriert), um eine in Elemente untergliederte Liste der Adobe Reader-Verwendungsrechte anzuzeigen, die vom Zertifikat aktiviert werden können. Die für ein bestimmtes Dokument aktivierten Verwendungsrechte stellen eine Teilmenge der vom Zertifikat aktivierten Rechte dar.

Wenn Onlinekommentierung in einer Umgebung ohne Zusammenarbeitsfunktionalität erforderlich ist, wenden Sie sich wegen weiterer Informationen an den Adobe-Support. Die Mode-Eigenschaft entspricht dem Bereitstellungstyp und lautet entweder *production* (Produktion) oder *evaluation* (Test).

Die zulässigen Acrobat Reader DC Extensions-Verwendungsrechte umfassen mindestens ein spezifisches Element. Diese Elemente werden in verschiedenen Kombinationen verwendet, um Variationen lizenzierter Produktfunktionen zu ermöglichen.

<table>
 <thead>
  <tr>
   <th><p>Verwendungsrechte – Element</p></th>
   <th><p>In Adobe Reader aktivierte Funktion bei der Anzeige eines PDF-Dokuments mit aktivierten Verwendungsrechten</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>FormFillInAndSave</p></td>
   <td><p>Formularfelder auszufüllen und Dateien lokal speichern</p></td>
  </tr>
  <tr>
   <td><p>FormImportExport</p></td>
   <td><p>Formulardaten als FDF-, XFDF-, XML- und XDP-Dateien importieren und exportieren</p></td>
  </tr>
  <tr>
   <td><p>FormAddDelete</p></td>
   <td><p>Felder und Feldeigenschaften im PDF-Formular hinzufügen, ändern oder löschen</p></td>
  </tr>
  <tr>
   <td><p>SubmitStandalone</p></td>
   <td><p>Daten per E-Mail oder offline an einen Server senden, der nicht in einer Browsersitzung ausgeführt wird</p></td>
  </tr>
  <tr>
   <td><p>SpawnTemplate</p></td>
   <td><p>Seiten aus Vorlagenseiten innerhalb desselben Formulars erstellen</p></td>
  </tr>
  <tr>
   <td><p>Signing</p></td>
   <td><p>PDF-Dokumente digital signieren und speichern und digitale Signaturen löschen</p></td>
  </tr>
  <tr>
   <td><p>AnnotModify</p></td>
   <td><p>Dokumentanmerkungen (z. B. Kommentare) erstellen und ändern</p></td>
  </tr>
  <tr>
   <td><p>AnnotImportExport</p></td>
   <td><p>Anmerkungen (z. B. Kommentare) in einer getrennten Datei speichern und Kommentare aus einer Datei laden</p></td>
  </tr>
  <tr>
   <td><p>BarcodePlaintext</p></td>
   <td><p>Ein Dokument mit Formulardaten in einem unverschlüsselten Strichcodeformat drucken, für das zum Dekodieren keine lizenzierte Serversoftware erforderlich ist</p></td>
  </tr>
  <tr>
   <td><p>AnnotOnline</p></td>
   <td><p>Anmerkungen (z. B. Kommentare) auf einen Server für die Online-Überprüfung und -Kommentierung hochladen und von diesem herunterladen</p></td>
  </tr>
  <tr>
   <td><p>FormOnline</p></td>
   <td><p>Mit Webdiensten oder Datenbanken verbinden, die in einem PDF-Formular definiert sind</p></td>
  </tr>
  <tr>
   <td><p>EFModif</p></td>
   <td><p>Eingebettete Dateiobjekte ändern, die mit dem PDF-Dokument verknüpft sind</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Acrobat Reader DC Extensions-Verwendungsrechte können von Adobe nur in bestimmten Kombinationen lizenziert werden, die zusammen funktionieren. Es ist nicht möglich, diese Funktionen einzeln zu lizenzieren. Informationen zu den möglichen Kombinationen von Verwendungsrechten erhalten Sie von Ihrem AEM Forms-Kundenbetreuer.
