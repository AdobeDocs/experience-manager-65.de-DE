---
title: Best Practices für E-Mail-Vorlagen
description: Hier finden Sie Best Practices zum Erstellen von E-Mail-Vorlagen in AEM.
uuid: 07417a63-7ca6-484c-b55d-57b319428329
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration, best-practices
content-type: reference
discoiquuid: 2418777e-4eb2-4d82-aa9e-8d1b0bf740f3
docset: aem65
exl-id: 6666eddc-dc17-4bd4-9d55-e6522f40a680
source-git-commit: d673a447e9ce2377c8645c87f12be81cbad06238
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 41%

---

# Best Practices für E-Mail-Vorlagen {#best-practices-for-email-templates}

>[!CAUTION]
>
>Dieser Artikel gilt für die veralteten Foundation-Komponenten, die auf E-Mail-Komponenten AEM.
>
>Benutzer sollten die moderne [Kernkomponenten E-Mail-Komponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/email/introduction.html)

In diesem Dokument werden einige Best Practices zum E-Mail-Design beschrieben, die zu einer gut entwickelten E-Mail-Kampagnenvorlage führen.

Die in AEM verfügbare Demokampagne folgt diesen Best Practices. Wie die Best Practices in der Demokampagne implementiert werden, wird für jede Best Practice beschrieben.

Verwenden Sie diese Best Practices bei der Erstellung Ihres eigenen Newsletters.

>[!NOTE]
>
>Alle Kampagneninhalte sollten unter einer `master`-Seite des Typs `cq/personalization/components/ambitpage` erstellt werden.
>
>Ihre geplante Kampagnenstruktur sieht beispielsweise etwa so aus:
>
>`/content/campaigns/teasers/en/campaign-promotion-global`
>
>Stellen Sie sicher, dass er sich unter einem `master` page
>
>`/content/campaigns/teasers/master/en/campaign-promotion-global`

>[!NOTE]
>
>Beim Erstellen einer E-Mail-Vorlage für Adobe Campaign müssen Sie die -Eigenschaft einbeziehen **acMapping** mit dem Wert **mapRecipient** im **jcr:content** Knoten der Vorlage. Ist dies nicht der Fall, können Sie die Adobe Campaign-Vorlage nicht in **Seiteneigenschaften** des Experience Managers (Feld ist deaktiviert).

## Vorlage/Seitenkomponente {#template-page-component}

***/libs/mcm/campaign/components/campaign_newsletterpage***

<table>
 <tbody>
  <tr>
   <td><strong>Best Practice</strong></td>
   <td><strong>Implementierung</strong></td>
  </tr>
  <tr>
   <td><p>Geben Sie den Dokumenttyp an, um eine konsistente Wiedergabe zu gewährleisten.</p> <p>Fügen Sie DOCTYPE am Anfang hinzu (HTML oder XHTML).</p> </td>
   <td><p>Ist durch Änderung des Designs der Eigenschaft <i>cq:doctype</i> in <i>/etc/designs/default/jcr:content/campaign_newsletterpage</i> konfigurierbar.</p> <p>Der Standardwert ist „XHTML“:</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional/EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Kann in „HTML_5“ geändert werden:</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Geben Sie die Zeichendefinition an, um die korrekte Darstellung von Sonderzeichen sicherzustellen.</p> <p>Fügen Sie die CHARSET-Deklaration hinzu (z. B. ISO-8859-15, UTF-8) zu &lt;head&gt;</p> </td>
   <td><p>Ist auf „UTF-8“ festgelegt.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Codieren Sie die gesamte Struktur mithilfe des &lt;table&gt;-Elements. Bei komplizierteren Layouts sollten Sie Tabellen zur Erstellung komplexer Strukturen verschachteln.</p> <p>E-Mails sollten auch ohne css gut aussehen.</p> </td>
   <td><p>Innerhalb der gesamten Vorlage werden Tabellen zur Strukturierung von Inhalten verwendet. Aktuell werden maximal vier verschachtelte Tabellen verwendet (1 Basistabelle + maximal 3 Verschachtelungsebenen).</p> <p>&lt;div&gt;-Tags werden nur im Autorenmodus verwendet, um eine ordnungsgemäße Komponentenbearbeitung sicherzustellen.</p> </td>
  </tr>
  <tr>
   <td>Verwenden Sie Elementattribute (wie „cellpadding“, „valign“ und „width“), um die Tabellenmaße festzulegen. Diese Methode erzwingt eine Box-Modell-Struktur.</td>
   <td><p>Alle Tabellen enthalten die erforderlichen Attribute wie <i>border</i>, <i>cellpadding</i>, <i>cellspacing</i>und <i>width</i>.</p> <p>Zur Harmonisierung der Elementpositionierung innerhalb von Tabellen ist für alle Tabellenzellen das Attribut <i>valign="top"</i> festgelegt.</p> </td>
  </tr>
  <tr>
   <td><p>Achten Sie nach Möglichkeit auf eine Eignung für mobile Geräte. Verwenden Sie Medienabfragen zur Erhöhung der Textgrößen auf kleinen Bildschirmen und stellen Sie zu Links Trefferbereiche im Miniaturformat bereit.</p> <p>Erstellen Sie falls möglich ein responsives E-Mail-Design.</p> </td>
   <td>Sofern CSS-Stile zum Illustrieren des Demo-Designs verwendet werden, werden Medienabfragen für die Bereitstellung einer für mobile Geräte geeigneten Version verwendet.</td>
  </tr>
  <tr>
   <td>Inline-CSS ist besser, als den gesamten CSS-Code am Anfang anzugeben.</td>
   <td><p>Um die zugrunde liegende HTML-Struktur besser zu demonstrieren und die Möglichkeit zur Anpassung der Newsletterstruktur zu erleichtern, wurden nur einige CSS-Definitionen inline zusammengefasst.</p> <p>Basisstile und Vorlagenvarianten wurden im &lt;head&gt; der Seite in einen Stilblock extrahiert. Bei der endgültigen Übermittlung des Newsletters werden diese CSS-Definitionen in die HTML eingebettet. Ein automatischer Inline-Mechanismus ist geplant, derzeit jedoch nicht verfügbar.</p> </td>
  </tr>
  <tr>
   <td>Halten Sie CSS einfach. Vermeiden Sie zusammengesetzte Stildeklarationen, Kurzcode, CSS-Layouteigenschaften, komplexe Selektoren und Pseudoelemente.</td>
   <td>Bei der Verwendung von CSS-Stilen zur Illustration des Demo-Designs werden die CSS-Empfehlungen befolgt.</td>
  </tr>
  <tr>
   <td>Die maximale Breite von E-Mails sollte 600 – 800 Pixel betragen. Durch diese Größenanpassung wird das Verhalten der Benutzer innerhalb der von vielen Clients bereitgestellten Größe des Vorschaufensters verbessert.</td>
   <td>Die <i>width</i> der Inhaltstabelle ist im Demodesign auf 600 Pixel begrenzt.</td>
  </tr>
 </tbody>
</table>

### Bilder {#images}

/libs/mcm/campaign/components/image

| **Best Practice** | **Implementierung** |
|---|---|
| Fügen Sie *alt*-Attribute für Bilder hinzu. | Das *alt*-Attribut wurde als obligatorisch für die Bildkomponente definiert. |
| Verwenden Sie das *jpg*- statt des *png*-Formats für Bilder. | Bilder werden von der Bildkomponente immer als JPG bereitgestellt. |
| Verwenden Sie das `<img>`-Element statt Hintergrundbilder in einer Tabelle. | In den Vorlagen werden keine Hintergrundbilddaten verwendet. |
| Fügen Sie den Bildern das Attribut „style=&quot;display block&quot;“hinzu. Auf diese Weise können sie gut auf Gmail angezeigt werden. | Alle Bilder enthalten standardmäßig das Attribut *style=&quot;display block&quot;*. |

### Text und Links {#text-and-links}

/libs/mcm/campaign/components/heading, /libs/mcm/campaign/components/textimage

<table>
 <tbody>
  <tr>
   <td><strong>Best Practice</strong></td>
   <td><strong>Implementierung</strong></td>
  </tr>
  <tr>
   <td>Verwenden Sie den HTML-Code &lt;font&gt; statt „style“ in CSS (Schriftfamilie).</td>
   <td>Der RichTextEditor (z. B. in der textimage-Komponente) unterstützt jetzt die Auswahl und Anwendung von Schriftfamilien und Schriftgrößen für ausgewählte Texte. Sie werden als Tags gerendert.</td>
  </tr>
  <tr>
   <td>Verwenden Sie einfache, plattformübergreifende Schriftarten wie <i>Arial®, Verdana, Georgia</i>und <i>Times New Roman®</i>.</td>
   <td><p>Hängt vom Newsletter-Design ab.</p> <p>Für das Demodesign wird die Schrift "Helvetica®"verwendet, aber sie wird auf eine generische sans-serif-Schrift zurückgesetzt, falls nicht vorhanden.</p> </td>
  </tr>
 </tbody>
</table>

### Generisch {#generic}

| **Best Practice** | **Implementierung** |
|---|---|
| Verwenden Sie den W3C-Validator, um den HTML-Code zu korrigieren. Stellen Sie sicher, dass alle geöffneten Tags ordnungsgemäß geschlossen sind. | Der Code wurde validiert. Nur für XHTML-Übergangsdokumenttypen das fehlende xmlns-Attribut für die `<html>` -Element fehlt. |
| Vermeiden Sie die Verwendung von JavaScript oder Flash - diese Technologien werden häufig von E-Mail-Clients nicht unterstützt. | JavaScript oder Flash wird nicht in der Newsletter-Vorlage verwendet. |
| Fügen Sie eine Nur-Text-Version für das mehrteilige Senden hinzu. | Ein neues Widget wurde in die Seiteneigenschaften integriert, um eine einfache Textanwendung aus dem Seiteninhalt zu extrahieren. Sie können es als Ausgangspunkt für die endgültige Klartextversion verwenden. |

## Vorlagen und Beispiele für Campaign-Newsletter {#campaign-newsletter-templates-and-examples}

AEM enthält standardmäßig mehrere Vorlagen und Komponenten, mit denen Sie Kampagnen-Newsletter erstellen können. Sie können diese Vorlagen und Komponenten verwenden, um Ihre benutzerdefinierten Newsletter zu erstellen.

### Vorlagen {#templates}

Um eine solide Basis zu bieten und die Vielfalt an Inhaltsflussmöglichkeiten zu erweitern, stehen standardmäßig drei leicht unterschiedliche Vorlagentypen zur Verfügung. Sie können diese drei Typen einfach verwenden, um einen benutzerdefinierten Newsletter zu erstellen.

Alle haben eine **header**, **Fußzeile** und **body** Abschnitt. Unter dem Abschnitt &quot;Text&quot;unterscheidet sich jede Vorlage in **Spaltendesign** (eine, zwei oder drei Spalten).

![](assets/chlimage_1-69.png)

### Komponenten {#components}

Es gibt derzeit [sieben Komponenten zur Verwendung in Kampagnenvorlagen](/help/sites-authoring/adobe-campaign-components.md). Diese Komponenten basieren alle auf der Adobe Markup-Sprache **HTL**.

| **Komponentenname** | **Komponentenpfad** |
|---|---|
| Überschrift | /libs/mcm/campaign/components/heading |
| Bild | /libs/mcm/campaign/components/image |
| Text und Personalisierung | /libs/mcm/campaign/components/personalization |
| Textbild | /libs/mcm/campaign/components/textimage |
| Link | /libs/mcm/campaign/components/reference |
| Dynamic Media Classic-Bildvorlage (früher Scene7) | /libs/mcm/campaign/s7image |
| Zielgerichteter Verweis | /libs/mcm/campaign/components/reference |

>[!NOTE]
>
>Diese Komponenten sind für E-Mail-Inhalte optimiert. d. h. sie halten sich an die in diesem Dokument beschriebenen Best Practices. Die Verwendung anderer vordefinierter Komponenten verstößt normalerweise gegen diese Regeln.

Diese Komponenten werden ausführlich unter [Adobe Campaign-Komponenten](/help/sites-authoring/adobe-campaign-components.md).
