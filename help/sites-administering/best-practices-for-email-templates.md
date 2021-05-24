---
title: Best Practices für E-Mail-Vorlagen
seo-title: Best Practices für E-Mail-Vorlagen
description: Finden Sie Best Practices zur Erstellung von E-Mail-Vorlagen in AEM.
seo-description: Finden Sie Best Practices zur Erstellung von E-Mail-Vorlagen in AEM.
uuid: 07417a63-7ca6-484c-b55d-57b319428329
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration, best-practices
content-type: reference
discoiquuid: 2418777e-4eb2-4d82-aa9e-8d1b0bf740f3
docset: aem65
exl-id: 6666eddc-dc17-4bd4-9d55-e6522f40a680
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 43%

---

# Best Practices für E-Mail-Vorlagen  {#best-practices-for-email-templates}

>[!CAUTION]
>
>Die AEM E-Mail-Komponenten werden nicht mehr unterstützt. Aufgrund der Art der E-Mail, in der Inhalt und Stil zusammengeführt werden, werden die standardmäßig von AEM bereitgestellten E-Mail-Komponenten für Kunden nur eingeschränkt wiederverwendet, da benutzerdefinierte Stile in alle für Projekte erforderlichen Komponenten implementiert werden müssen.
>
>E-Mail-Komponenten können auf Projektebene implementiert werden. Die veralteten E-Mail-AEM veranschaulichen, wie dies erreicht werden kann. Diese veralteten Komponenten sollten jedoch nicht für Projekte verwendet werden.

Dieses Dokument beschreibt einige der Best Practices zum E-Mail-Design, die eine gut entwickelte E-Mail-Kampagnenvorlage ermöglichen.

Die in AEM verfügbare Demokampagne befolgt all diese Best Practices. Zu jeder Best Practice ist beschrieben, wie dieses Best Practices in der Demokampagne implementiert werden.

Verwenden Sie diese Best Practices bei der Erstellung Ihres eigenen Newsletters.

>[!NOTE]
>
>Alle Kampagneninhalte sollten unter einer `master`-Seite vom Typ `cq/personalization/components/ambitpage` erstellt werden.
>
>Wenn Ihre geplante Kampagnenstruktur beispielsweise etwa so aussieht:
>
>`/content/campaigns/teasers/en/campaign-promotion-global`
>
>Sie sollten sicherstellen, dass sie sich unter einer `master`-Seite befindet.
>
>`/content/campaigns/teasers/master/en/campaign-promotion-global`

>[!NOTE]
>
>Beim Erstellen einer E-Mail-Vorlage für Adobe Campaign müssen Sie die Eigenschaft **acMapping** mit dem Wert **mapRecipient** im Knoten **jcr:content** der Vorlage einbeziehen oder Sie können die Adobe Campaign-Vorlage nicht im Knoten **Seiteneigenschaften** der AEM auswählen (Feld ist deaktiviert).

## Vorlage/Seitenkomponente {#template-page-component}

***/libs/mcm/campaign/components/campaign_newsletterpage***

<table>
 <tbody>
  <tr>
   <td><strong>Best Practice</strong></td>
   <td><strong>Implementierung</strong></td>
  </tr>
  <tr>
   <td><p>Geben Sie den Dokumenttyp an, um eine konsistente Wiedergabe sicherzustellen.</p> <p>Hinzufügen von DOCTYPE am Anfang (HTML oder XHTML)</p> </td>
   <td><p>Ist konfigurierbar, indem die <i>cq:doctype</i>-Eigenschaft in<i>"/etc/designs/default/jcr:content/campaign_newsletterpage"</i> geändert wird.</p> <p>Der Standardwert ist "XHTML":</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Kann in "HTML_5"geändert werden:</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Geben Sie die Zeichendefinition an, um die korrekte Darstellung von Sonderzeichen sicherzustellen.</p> <p>Fügen Sie die CHARSET-Deklaration (z. B. iso-8859-15, UTF-8) zu &lt;head&gt; hinzu.</p> </td>
   <td><p>Ist auf UTF-8 festgelegt.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Codieren Sie die gesamte Struktur mithilfe des Elements &lt;table&gt;. Bei komplizierteren Layouts sollten Sie Tabellen zur Erstellung komplexer Strukturen verschachteln.</p> <p>E-Mail sollte auch ohne CSS gut aussehen.</p> </td>
   <td><p>Tabellen werden in der gesamten Vorlage zur Strukturierung von Inhalten verwendet. Aktuell werden maximal vier verschachtelte Tabellen (1 Basistabelle + max. 3 Verschachtelungsebenen)</p> <p>&lt;div&gt; -Tags werden nur im Autorenmodus verwendet, um eine ordnungsgemäße Komponentenbearbeitung sicherzustellen.</p> </td>
  </tr>
  <tr>
   <td>Verwenden Sie Elementattribute (z. B. cellpadding, valign und width), um Tabellendimensionen festzulegen. Dies erzwingt eine Verschachtelungsmodellstruktur.</td>
   <td><p>Alle Tabellen enthalten die erforderlichen Attribute wie <i>border</i>, <i>cellpadding</i>, <i>cellspacing</i> und <i>width</i>.</p> <p>Um die Elementpositionierung in Tabellen zu harmonisieren, wird für alle Tabellenzellen das Attribut <i>valign="top"</i> festgelegt.</p> </td>
  </tr>
  <tr>
   <td><p>Berücksichtigen Sie nach Möglichkeit die Mobilfreundlichkeit. Verwenden Sie Medienabfragen zur Erhöhung der Textgrößen auf kleinen Bildschirmen und stellen Sie zu Links Trefferbereiche im Miniaturformat bereit.</p> <p>Erstellen Sie falls möglich ein responsives E-Mail-Design.</p> </td>
   <td>Sofern CSS-Stile zum Illustrieren des Demodesigns verwendet werden, werden Medienabfragen für die Bereitstellung einer mobilfreundlichen Version verwendet.</td>
  </tr>
  <tr>
   <td>Inline-CSS ist besser, als alle CSS am Anfang zu platzieren.</td>
   <td><p>Um die zugrunde liegende HTML-Struktur besser zu demonstrieren und die Möglichkeit zur Anpassung der Newsletterstruktur zu erleichtern, erfolgen nur einige CSS-Definitionen inline.</p> <p>Basisstile und Vorlagenvarianten wurden in einen Stilblock im &lt;head&gt; der Seite extrahiert. Bei der finalen Übermittlung des Newsletters sollten diese CSS-Definitionen inline in HTML vorhanden sein. Ein automatischer Inlining-Mechanismus ist geplant, aktuell jedoch noch nicht verfügbar.</p> </td>
  </tr>
  <tr>
   <td>Halten Sie CSS einfach. Vermeiden Sie zusammengesetzte Stildeklarationen, Kompaktcode, CSS-Layouteigenschaften, komplexe Selektoren und Pseudoelemente.</td>
   <td>Bei der Verwendung von CSS-Stilen zur Illustration des Demodesigns werden die CSS-Empfehlungen befolgt.</td>
  </tr>
  <tr>
   <td>Die maximale Breite von E-Mails sollte 600-800 Pixel betragen. Dies sorgt dafür, dass diese in der von vielen Clients bereitgestellten Vorschaufenstergröße besser funktionieren.</td>
   <td>Die <i>Breite</i> der Inhaltstabelle ist im Demodesign auf 600 px beschränkt.</td>
  </tr>
 </tbody>
</table>

### Bilder {#images}

/libs/mcm/campaign/components/image

| **Best Practice** | **Implementierung** |
|---|---|
| Hinzufügen von Attributen *alt* zu Bildern | Das Attribut *alt* wurde für die Bildkomponente als obligatorisch definiert. |
| Verwenden Sie das Format *jpg* anstelle des Formats *png* für Bilder. | Bilder werden von der Bildkomponente immer als JPG bereitgestellt. |
| Verwenden Sie in einer Tabelle das Element `<img>` anstelle von Hintergrundbildern. | In den Vorlagen werden keine Hintergrundbilddaten verwendet. |
| Fügen Sie den Bildern das Attribut style=&quot;display block&quot; hinzu. Dies ermöglicht eine gute Anzeige in Gmail. | Alle Bilder enthalten standardmäßig das Attribut *style=&quot;display block&quot;* . |

### Text und Links {#text-and-links}

/libs/mcm/campaign/components/heading, /libs/mcm/campaign/components/textimage

<table>
 <tbody>
  <tr>
   <td><strong>Best Practice</strong></td>
   <td><strong>Implementierung</strong></td>
  </tr>
  <tr>
   <td>Verwenden Sie HTML &lt;font&gt; anstelle von Stil in CSS (Schriftfamilie)</td>
   <td>Der RichTextEditor (z. B. in der textimage-Komponente) unterstützt jetzt die Auswahl und Anwendung von Schriftfamilien und Schriftgrößen für ausgewählte Texte. Sie werden als &lt;font&gt;-Tags gerendert.</td>
  </tr>
  <tr>
   <td>Verwenden Sie einfache, plattformübergreifende Schriftarten wie <i>Arial, Verdana, Georgia</i> und <i>Times New Roman</i>.</td>
   <td><p>Hängt vom Newsletter-Design ab.</p> <p>Für das Demodesign wird die Schrift "Helvetica"verwendet, wird jedoch auf die allgemeine sans-serif-Schrift zurückgesetzt, falls nicht vorhanden.</p> </td>
  </tr>
 </tbody>
</table>

### Generisch {#generic}

| **Best Practice** | **Implementierung** |
|---|---|
| Verwenden Sie den W3C-Validator, um den HTML-Code zu korrigieren. Stellen Sie sicher, dass alle offenen Tags ordnungsgemäß geschlossen werden. | Der Code wurde validiert. Für XHTML-Übergangsdokumentation fehlt nur das fehlende xmlns-Attribut für das Element `<html>` . |
| Verwenden Sie weder JavaScript noch Flash - diese Technologien werden von E-Mail-Clients größtenteils nicht unterstützt. | In der Newslettervorlage werden weder JavaScript noch Flash verwendet. |
| Fügen Sie eine Textversion für mehrteilige Sendungen hinzu. | Es wurde ein neues Widget in die Seiteneigenschaften integriert, mit dem im Handumdrehen eine Nur-Text-Version aus den Seiteninhalten extrahiert werden kann. Dies kann als Ausgangspunkt für die finale Nur-Text-Version verwendet werden. |

## Kampagnen-Newsletter – Vorlagen und Beispiele {#campaign-newsletter-templates-and-examples}

AEM bietet Ihnen standardmäßig mehrere Vorlagen und Komponenten zur Erstellung von Kampagnen-Newslettern. Sie können diese Vorlagen und Komponenten zur Erstellung Ihrer benutzerdefinierten Newsletter verwenden.

### Vorlagen {#templates}

Um eine solide Grundlage zu schaffen und die Vielfalt der Möglichkeiten für den Inhaltsfluss zu erweitern, stehen standardmäßig drei leicht voneinander abweichende Vorlagentypen zur Verfügung. Sie können diese einfach verwenden, um einen benutzerdefinierten Newsletter zu erstellen.

Alle haben einen **header**, eine **Fußzeile** und einen **body** -Abschnitt. Unter dem Hauptteil unterscheidet sich jede Vorlage in **Spaltendesign** (1, 2 oder 3 Spalten).

![](assets/chlimage_1-69.png)

### Komponenten  {#components}

Es stehen aktuell [sieben Komponenten zur Verfügung, die innerhalb von Kampagnenvorlagen verwendet werden können](/help/sites-authoring/adobe-campaign-components.md). Diese Komponenten basieren alle auf der Adobe-Markup-Sprache **HTL**.

| **Komponentenname** | **Komponentenpfad** |
|---|---|
| Überschrift | /libs/mcm/campaign/components/heading |
| Bild | /libs/mcm/campaign/components/image |
| Text und Personalisierung | /libs/mcm/campaign/components/personalization |
| Textimage | /libs/mcm/campaign/components/textimage |
| Verknüpfung | /libs/mcm/campaign/components/reference |
| Dynamic Media Classic (früher Scene7)-Bildvorlage | /libs/mcm/campaign/s7image |
| Zielgerichteter Verweis | /libs/mcm/campaign/components/reference |

>[!NOTE]
>
>Diese Komponenten sind für Mail-Inhalte optimiert, d. h. sie befolgen die in diesem Dokument beschriebenen Best Practices. Die Verwendung standardmäßiger Komponenten verstößt in der Regel gegen diese Regeln.

Diese Komponenten sind unter [Adobe Campaign-Komponenten](/help/sites-authoring/adobe-campaign-components.md) detailliert beschrieben.
