---
title: Integrieren von Einstiegsseiten in Adobe Analytics
seo-title: Integrieren von Einstiegsseiten in Adobe Analytics
description: Erfahren Sie, wie Sie mit Adobe Analytics Einstiegsseiten integrieren können.
seo-description: Erfahren Sie, wie Sie mit Adobe Analytics Einstiegsseiten integrieren können.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
exl-id: da3f7b7e-87e5-446a-9a77-4b12b850a381
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 48%

---

# Integrieren von Einstiegsseiten in Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM hat die Landingpage-Lösung mit [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) integriert, indem die folgenden Aktionsaufruf-Komponenten (CTA) verwendet werden:

1. Click Through-Komponente
1. Grafischer Link

Diese Komponenten legen bestimmte Attribute offen, die über Adobe Analytics-Variablen (Traffic- und Konversionsvariablen) und Erfolgsereignisse zugeordnet werden können, um Informationen an Adobe Analytics zu senden.

## Voraussetzungen {#prerequisites}

Adobe empfiehlt, die [vorhandene AEM-Adobe Analytics-Integration](/help/sites-administering/adobeanalytics.md) durchzugehen, um zu verstehen, wie diese Integration funktioniert.

## Verfügbare Komponenten für die Zuordnung {#components-available-for-mapping}

In AEM können die Komponenten **Aktionsaufruf** - **ClickThroughLink** und **GraphicalLink** - die hier im Sidekick angezeigt werden, Adobe Analytics-Variablen zugeordnet werden.

![chlimage_1-21](assets/chlimage_1-21a.jpeg)

### Zuordnen von Einstiegsseitenkomponenten zu Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

Sie können wie folgt Einstiegsseitenkomponenten zu Adobe Analytics zuordnen:

1. Nachdem Sie die Adobe Analytics-Konfiguration erstellt und ein neues Framework erstellt haben, wählen Sie die entsprechende Report Suite aus dem Dropdown-Menü aus. Hierdurch erfolgt das Abrufen der Adobe Analytics-Variablen und ihre Anzeige in der Inhaltssuche.
1. Ziehen Sie Aktionsaufrufkomponenten bei Bedarf vom Sidekick in den Zuordnungsbereich in der Mitte der Seite und legen Sie sie dort ab.

<table>
 <tbody>
  <tr>
   <td><strong>Komponentenname</strong></td>
   <td><strong>Angegebene Attribute</strong></td>
   <td><strong>Bedeutung des Attributs</strong></td>
  </tr>
  <tr>
   <td><strong>CTA-Click-Through-Link</strong></td>
   <td><i>eventdata.clickthroughLinkLabel</i> <br /> </td>
   <td>Titel des Links oder Text des Links </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td>
   <td>Das Ziel, an dem Sie beim Klicken auf den Link gelangt sind </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickthroughLinkClick</i> <br /> </td>
   <td>Das Klickereignis </td>
  </tr>
  <tr>
   <td><strong>CTA-Grafiklink</strong></td>
   <td><i>eventdata.clicktroughImageLabel</i> <br /> </td>
   <td>Der Titel des CTA-Bildes </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clicktroughImageTarget</i> <br /> </td>
   <td>Das Ziel, das aufgerufen wird, wenn Sie auf das Bild mit Link klicken</td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clicktroughImageAsset</i> <br /> </td>
   <td>Der Pfad zum Bild-Asset im Repository </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clicktroughImageClick</i> <br /> </td>
   <td>Das Klickereignis</td>
  </tr>
 </tbody>
</table>

1. Weisen Sie diese offengelegten Attribute beliebigen Adobe Analytics-Variablen aus der Inhaltssuche zu. Das Framework ist nun einsatzbereit.
1. Sie können jetzt eine neue Landingpage erstellen oder eine vorhandene Landingpage mit vorhandenen CTA-Komponenten öffnen und im Sidekick auf die Registerkarte **Cloud Services** in **Seiteneigenschaften** klicken (in der Touch-optimierten Benutzeroberfläche wählen Sie **Eigenschaften öffnen** aus und klicken Sie auf **Cloud Services**) und konfigurieren Sie das für die Landingpage zu verwendende Framework. Wählen Sie das Framework aus der Dropdown-Liste aus.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Nach dem Konfigurieren des Frameworks für die Einstiegsseite können Sie nun die instrumentierten Komponenten verwenden. Sämtliche Klicks auf den Aktionsaufrufen werden dann in Adobe Analytics aufgezeichnet.
