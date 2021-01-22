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
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 48%

---


# Integrieren von Einstiegsseiten in Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM hat die Landingpages-Lösung mit [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) mithilfe der folgenden Aktionsaufruf-Komponenten (CTA) integriert:

1. Click Through-Komponente
1. Grafischer Link

Diese Komponenten stellen bestimmte Attribute zur Verfügung, die über Adobe Analytics-Variablen (Traffic, Konversionsvariablen) und Erfolgsvariablen zugeordnet werden können, um Informationen an Adobe Analytics zu senden.

## Voraussetzungen {#prerequisites}

Adobe empfiehlt, die [bestehende AEM-Adobe Analytics-Integration](/help/sites-administering/adobeanalytics.md) zu durchlaufen, um zu verstehen, wie diese Integration funktioniert.

## Verfügbare Komponenten für die Zuordnung {#components-available-for-mapping}

In AEM können die Komponenten **Aktionsaufruf** - **ClickThroughLink** und **GraphicalLink** -, die hier im Sidekick angezeigt werden, Adobe Analytics-Variablen zugeordnet werden.

![chlimage_1-21](assets/chlimage_1-21a.jpeg)

### Zuordnen von Einstiegsseitenkomponenten zu Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

Sie können wie folgt Einstiegsseitenkomponenten zu Adobe Analytics zuordnen:

1. Wählen Sie nach dem Erstellen der Adobe Analytics-Konfiguration und dem Erstellen eines neuen Frameworks die entsprechende Berichte-Suite aus dem Dropdownmenü. Hierdurch erfolgt das Abrufen der Adobe Analytics-Variablen und ihre Anzeige in der Inhaltssuche.
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
   <td><i>eventData.clickthroughLinkLabel</i> <br /> </td>
   <td>Die Beschriftung auf dem Link oder der Text des Links </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventData.clickthroughLinkTarget</i> <br /> </td>
   <td>Das Ziel, an dem Sie sich befinden, wenn Sie auf den Link klicken </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventData.Ereignisses.clickthroughLinkClick</i> <br /> </td>
   <td>Das Klickereignis </td>
  </tr>
  <tr>
   <td><strong>CTA-Grafiklink</strong></td>
   <td><i>eventData.clicktroughImageLabel</i> <br /> </td>
   <td>Der Titel des CTA-Bildes </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventData.clicktroughImageTarget</i> <br /> </td>
   <td>Das Ziel, das aufgerufen wird, wenn Sie auf das Bild mit Link klicken</td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventData.clicktroughImageAsset</i> <br /> </td>
   <td>Der Pfad zum Bild-Asset im Repository </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventData.Ereignisses.clicktroughImageClick</i> <br /> </td>
   <td>Das Klickereignis</td>
  </tr>
 </tbody>
</table>

1. Weisen Sie diese offengelegten Attribute beliebigen Adobe Analytics-Variablen aus der Inhaltssuche zu. Das Framework ist nun einsatzbereit.
1. Sie können jetzt eine neue Landingpage erstellen oder eine vorhandene Landingpage mit vorhandenen CTA-Komponenten öffnen und im Sidekick auf die Registerkarte **Cloud Services** unter **Seiteneigenschaften** klicken (in der touchoptimierten Benutzeroberfläche wählen Sie **Eigenschaften öffnen** und klicken Sie auf **Cloud Services**) und konfigurieren Sie das Framework für die Verwendung mit Landingpage. Wählen Sie das Framework aus der Dropdown-Liste aus.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Nach dem Konfigurieren des Frameworks für die Einstiegsseite können Sie nun die instrumentierten Komponenten verwenden. Sämtliche Klicks auf den Aktionsaufrufen werden dann in Adobe Analytics aufgezeichnet.

