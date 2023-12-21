---
title: Funktionsunterschiede zwischen HTML5- und PDF-Formularen
description: Erfahren Sie mehr über die Funktionsunterschiede zwischen HTML5-Formularen und PDF forms.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms
exl-id: 3150f95f-7150-4eee-b5a9-121422dec2a1
source-git-commit: 524475c8f9dbd02bae30ecd558a376505fbe0aed
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 30%

---

# Funktionsunterschiede zwischen HTML5- und PDF-Formularen {#feature-differentiation-between-html-forms-and-pdf-forms}

Die folgende Tabelle zeigt die Funktionsunterstützung für HTML5-Formulare und PDF forms:

<table>
 <tbody>
  <tr>
   <th>Funktion</th>
   <th>HTML5-Formulare</th>
   <th>PDF</th>
  </tr>
  <tr>
   <td>Barcodes<br /> </td>
   <td>Nicht auf Benutzeroberflächenebene verfügbar. </td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td>Unterschriftsfeld<br /> </td>
   <td><strong>Digitale Signaturen</strong> werden nicht unterstützt, aber ein neuer <strong>Scribble-Signatur</strong> wird für papierähnliche Signaturen hinzugefügt. Sie können ihre Signatur mithilfe des <strong>Scribble-Signatur</strong> -Feld. Die Signatur wird im Formular als Bild gespeichert. Sie können Geolocation-Informationen im Abschnitt <strong>Scribble-Signatur</strong> -Feld.</td>
   <td>Signaturfeld verfügbar für <strong>Digitale Signaturen</strong>.</td>
  </tr>
  <tr>
   <td>Datenzusammenführung</td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
  <tr>
   <td>Bilder</td>
   <td>Das Daten-URI-Schema wird zum Anzeigen von Bildern verwendet. Alle modernen Versionen von Browsern unterstützen dieses Schema, es gibt jedoch Unterschiede in der Bandbreite der Bildformate, die von jedem Browser unterstützt werden.<br /> </td>
   <td>Die Formate .gif, .png, .jpeg, .bmp und .tiff werden unterstützt.</td>
  </tr>
  <tr>
   <td>Seitenumbruch<br /> </td>
   <td><p>Ein HTML5-Formular ist in Bereiche und Felder unterteilt, damit es ähnlich wie PDF forms aussieht. Die Seitengröße wird dynamisch berechnet. Wenn der gesamte Seiteninhalt in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, wird die leere Seite ausgeblendet. Zwischen den Seiten über und unter der leeren Seite wird kein leeres Leerzeichen (Leerzeichen) angezeigt.</p> <p>Wenn Datenzusammenführung oder Skripte Inhalte zu einer Seite hinzufügen, wird die Länge der Seite erweitert, um den neu hinzugefügten Inhalt aufzunehmen. Dem Formular werden keine neuen Seiten hinzugefügt, um den neu hinzugefügten Inhalt aufzunehmen. </p> <p><strong>Hinweis:</strong> Wenn der gesamte Seiteninhalt in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, bleibt die leere Seite (Leerraum) zwischen der ersten und zweiten Seite sichtbar, jedoch nicht zwischen allen anderen Seiten.</p> </td>
   <td>Paginierung in PDF hängt vom zusammengeführten Dateninhalt oder dem Benutzerinhalt ab. Abhängig davon wird die Seitenanzahl erhöht bzw. verringert.</td>
  </tr>
  <tr>
   <td>Kopf- und Fußzeilen </td>
   <td>Unterstützt. <br /> <br /> Da HTML5-Mobile Forms Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Sie können sie jedoch im Layout so einrichten, dass sie an mehreren Stellen in der Mobile Forms-Vorschau angezeigt werden.<br /> </td>
   <td>Unterstützt.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Widgets</td>
   <td>Widgets können angepasst werden, um das Benutzererlebnis auf Mobilgeräten zu verbessern.<br /> </td>
   <td>Alle Widgets sind gesperrt und kein benutzerdefiniertes Widget kann als Plug-in verwendet werden.<br /> </td>
  </tr>
  <tr>
   <td>XFA-Skript-API</td>
   <td>Unterstützt die am häufigsten verwendeten XFA-Skriptkonstrukte. Eine detaillierte Liste der unterstützten Konstrukte finden Sie unter <a href="/help/forms/using/scripting-support.md">Skriptunterstützung</a>.</td>
   <td>Unterstützt alle XFA-Skriptkonstrukte.</td>
  </tr>
  <tr>
   <td>Acrobat-Skript-APIs </td>
   <td>HTML5-Formulare unterstützen die am häufigsten verwendeten APIs. Weitere Informationen finden Sie unter <a href="/help/forms/using/scripting-support.md">Unterstützung für Skripterstellung</a>.</td>
   <td>Wenn die PDF-Datei in Acrobat oder Reader geöffnet ist, unterstützt sie auch alle Skript-APIs, die Acrobat bereitstellt.</td>
  </tr>
  <tr>
   <td>Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung </td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
 </tbody>
</table>

<!--Follow the best practices to enable a form template for HTML5 renditions and ensure that the behavior and appearance of HTML5 forms and XFA-based PDF is consistent. For detailed list of best practices, see [Best practices to design an HTML5 form.](/help/forms/using/best-practices-design-html5-forms.md)-->
