---
title: Integrieren von Landing-Pages in Adobe Analytics
seo-title: Integrating Landing Pages with Adobe Analytics
description: Erfahren Sie, wie Sie Landingpages in Adobe Analytics integrieren können.
seo-description: Learn how to integrate landing pages with Adobe Analytics.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
exl-id: da3f7b7e-87e5-446a-9a77-4b12b850a381
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 64%

---

# Integrieren von Landing-Pages in Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM hat die Einstiegsseitenlösung mithilfe des folgenden Aktionsaufrufs in [Adobe Analytics](https://www.omniture.com/de/products/analytics/sitecatalyst) integriert:

1. Clickthrough-Komponente
1. Grafische Link-Komponente

Diese Komponenten legen bestimmte Attribute offen, die über Adobe Analytics-Variablen (Traffic, Konversionsvariablen) und Erfolgsereignisse zugeordnet werden können, um Informationen an Adobe Analytics zu senden.

## Voraussetzungen {#prerequisites}

Adobe empfiehlt Ihnen, die [vorhandene AEM-Adobe Analytics-Integration](/help/sites-administering/adobeanalytics.md) durchzugehen, um deren Funktionsweise zu verstehen.

## Verfügbare Komponenten für die Zuordnung {#components-available-for-mapping}

In AEM können die **Aktionsaufruf**-Komponenten – **ClickThroughLink** und **GraphicalLink** –, die hier im Sidekick angezeigt werden, den Adobe Analytics-Variablen zugeordnet werden.

![chlimage_1-21](assets/chlimage_1-21a.jpeg)

### Zuordnen von Einstiegsseitenkomponenten zu Adobe Analytics {#mapping-landing-page-components-to-adobe-analytics}

So ordnen Sie Einstiegsseitenkomponenten Adobe Analytics zu:

1. Nachdem Sie die Adobe Analytics-Konfiguration erstellt und ein Framework erstellt haben, wählen Sie die entsprechende Report Suite aus dem Dropdownmenü aus. Dadurch werden die Adobe Analytics-Variablen abgerufen und im Content Finder angezeigt.
1. Ziehen Sie die Komponenten &quot;Aktionsaufruf (CTA)&quot;aus dem Sidekick in den Zuordnungsbereich in der Mitte der Seite, falls zutreffend.

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
   <td>Das Etikett oder der Text des Links </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickthroughLinkTarget</i> <br /> </td>
   <td>Das Ziel, das aufgerufen wird, wenn Sie auf den Link klicken </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickthroughLinkClick</i> <br /> </td>
   <td>Das Klickereignis </td>
  </tr>
  <tr>
   <td><strong>CTA-Grafiklink</strong></td>
   <td><i>eventdata.clicktroughImageLabel</i> <br /> </td>
   <td>Der Titel des CTA Bildes </td>
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
1. Sie können jetzt eine Landingpage erstellen oder eine vorhandene Landingpage mit vorhandenen CTA-Komponenten öffnen und auf **Cloud Service** Registerkarte in **Seiteneigenschaften** Wählen Sie im Sidekick (in der Touch-optimierten Benutzeroberfläche die Option **Eigenschaften öffnen** und klicken **Cloud Service**) und konfigurieren Sie das Framework für die Verwendung mit der Landingpage. Wählen Sie das Framework aus der Dropdown-Liste aus.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Nach dem Konfigurieren des Frameworks für die Einstiegsseite können Sie nun die instrumentierten Komponenten verwenden. Sämtliche Klicks auf den Aktionsaufrufen werden dann in Adobe Analytics aufgezeichnet.
