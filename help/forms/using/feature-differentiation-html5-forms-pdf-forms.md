---
title: Funktionsunterschiede zwischen HTML5- und PDF-Formularen
description: Erfahren Sie mehr über die Funktionsunterschiede zwischen HTML5- und PDF-Formularen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 3150f95f-7150-4eee-b5a9-121422dec2a1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 100%

---

# Funktionsunterschiede zwischen HTML5- und PDF-Formularen {#feature-differentiation-between-html-forms-and-pdf-forms}

Die folgende Tabelle zeigt die Funktionsunterstützung für HTML5- und PDF-Formulare:

<table>
 <tbody>
  <tr>
   <th>Funktion</th>
   <th>HTML5-Formulare</th>
   <th>PDF</th>
  </tr>
  <tr>
   <td>Barcodes<br /> </td>
   <td>Nicht verfügbar auf Benutzeroberflächenebene. </td>
   <td>Unterstützt</td>
  </tr>
  <tr>
   <td>Unterschriftsfeld<br /> </td>
   <td><strong>Digitale Signaturen</strong> werden nicht unterstützt, aber ein neues <strong>Freihand-Signatur</strong>-Feld wurde für papierähnliche Signaturen hinzugefügt. Die Signatur kann im Feld <strong>Freihand-Signatur</strong> auf dem Formular eingegeben werden. Die Signatur wird auf dem Formular als Bild gespeichert.  Sie können die Geotagging-Informationen im Feld <strong>Freihand-Signatur</strong> speichern.</td>
   <td>Signaturfeld für <strong>digitale Signaturen</strong> verfügbar.</td>
  </tr>
  <tr>
   <td>Datenzusammenführung</td>
   <td>Unterstützt</td>
   <td>Unterstützt </td>
  </tr>
  <tr>
   <td>Bilder</td>
   <td>Das Daten-URI-Schema wird für die Darstellung von Bildern verwendet.  Alle modernen Browser unterstützen dieses Schema, es gibt jedoch Unterschiede bei den Bildformaten, die die einzelnen Browser unterstützen.<br /> </td>
   <td>Die Formate .gif, .png, .jpeg, .bmp und .tiff werden unterstützt.</td>
  </tr>
  <tr>
   <td>Seitenumbruch<br /> </td>
   <td><p>Ein HTML5-Formular ist in Bereiche und Felder unterteilt, damit es wie ein PDF-Formular wirkt. Die Seitengröße wird dynamisch berechnet. Wenn der gesamte Seiteninhalt in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, wird die leere Seite ausgeblendet. Zwischen den Seiten über und unter der leeren Seite wird kein Leerzeichen angezeigt.</p> <p>Wird einer Seite durch Datenzusammenführung oder Skripte Inhalt hinzugefügt, wird die Seite erweitert, damit der neu hinzukommende Inhalt Platz findet. Dem Formular werden keine neuen Seiten für den neuen Inhalt hinzugefügt. </p> <p><strong>Hinweis:</strong> Wenn der gesamte Inhalt einer Seite in einem HTML5-Formular gelöscht oder als ausgeblendet markiert wird, bleibt zwischen der ersten und zweiten, nicht jedoch zwischen anderen Seiten ein Leerzeichen sichtbar.</p> </td>
   <td>Paginierung in PDF hängt vom zusammengeführten Dateninhalt oder dem Benutzerinhalt ab. Abhängig davon wird die Seitenanzahl erhöht bzw. verringert.</td>
  </tr>
  <tr>
   <td>Kopf- und Fußzeilen </td>
   <td>Unterstützt. <br /> <br /> Da HTML5-Mobile Forms Seitenumbrüche nicht unterstützen, werden Kopf- und Fußzeilen nur einmal angezeigt. Sie können sie jedoch im Layout so einrichten, dass sie an mehreren Stellen in der Vorschau für Mobile-Formulare angezeigt werden.<br /> </td>
   <td>Unterstützt.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Widgets</td>
   <td>Widgets können angepasst werden, um das Anwendererlebnis auf mobilen Geräten zu optimieren.<br /> </td>
   <td>Alle Widgets werden blockiert und kein benutzerdefiniertes Widget kann als Plug-In verwendet werden.<br /> </td>
  </tr>
  <tr>
   <td>XFA-Skript-API</td>
   <td>Unterstützt die am häufigsten verwendeten XFA-Skriptkonstrukte. Eine detaillierte Liste der unterstützten Konstrukte finden Sie unter <a href="/help/forms/using/scripting-support.md">Unterstützung der Skripterstellung</a>.</td>
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
