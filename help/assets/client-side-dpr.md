---
title: Verwenden der intelligenten Bildbearbeitung mit Client-seitigem Gerätepixelverhältnis (Device Pixel Ratio).
description: Erfahren Sie, wie Sie das Client-seitige Gerätepixelverhältnis mit der intelligenten Bildbearbeitung in Adobe Experience Manager as a Cloud Service mit Dynamic Media verwenden.
role: Admin,User
exl-id: e38f522a-242a-4ea9-a866-d8d129950831
source-git-commit: c8682118f15132063073df5cdc2b576b6e62a0c8
workflow-type: ht
source-wordcount: '323'
ht-degree: 100%

---

# Informationen zur intelligenten Bildbearbeitung mit Client-seitigem Gerätepixelverhältnis (Device Pixel Ratio, DPR). {#client-side-dpr}

Die aktuelle Lösung für die intelligente Bildbearbeitung verwendet Benutzeragenten-Zeichenfolgen, um den verwendeten Gerätetyp (Desktop, Tablet, Mobilgerät usw.) zu bestimmen.

Die Funktionen zur Geräteerkennung – DPR auf Basis von Benutzeragenten-Zeichenfolgen – sind häufig ungenau, insbesondere bei Apple-Geräten. Außerdem muss jedes neue Gerät, das gestartet wird, validiert werden.

Client-seitiges DPR liefert 100 % genaue Werte und funktioniert für jedes Gerät, das gestartet wird, unabhängig davon, ob es sich um Apple oder ein anderes neues Gerät handelt.

## Verwenden des Client-seitigen DPR-Codes.

**Server-seitig gerenderte Apps.**

1. Laden Sie „service worker init“ (`srvinit.js`), indem Sie das folgende Skript in den Header-Abschnitt Ihrer HTML-Seite einfügen:

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   ```

   Adobe empfiehlt, dieses Skript _vor_ allen anderen Skripten zu laden, damit der Service Worker sofort mit der Initialisierung beginnt.

1. Fügen Sie den folgenden DPR-Bild-Tag-Code oben im Body-Abschnitt Ihrer HTML-Seite ein:

   ```html
   <img src="aem_dm_dpr_1x.jpg" style="width:1px;height:1px;display:none"
       srcset="aem_dm_dpr_1x.jpg 1x, aem_dm_dpr_1.1x.jpg 1.1x, aem_dm_dpr_1.2x.jpg 1.2x, aem_dm_dpr_1.3x.jpg 1.3x, aem_dm_dpr_1.4x.jpg 1.4x, aem_dm_dpr_1.5x.jpg 1.5x, aem_dm_dpr_1.6x.jpg 1.6x,          aem_dm_dpr_1.7x.jpg 1.7x, aem_dm_dpr_1.8x.jpg 1.8x, aem_dm_dpr_1.9x.jpg 1.9x,
       aem_dm_dpr_2x.jpg 2x, aem_dm_dpr_2.1x.jpg 2.1x, aem_dm_dpr_2.2x.jpg 2.2x, aem_dm_dpr_2.3x.jpg 2.3x, aem_dm_dpr_2.4x.jpg 2.4x, aem_dm_dpr_2.5x.jpg 2.5x, aem_dm_dpr_2.6x.jpg 2.6x, aem_dm_dpr_2.7x.jpg 2.7x, aem_dm_dpr_2.8x.jpg 2.8x, aem_dm_dpr_2.9x.jpg 2.9x,
       aem_dm_dpr_3x.jpg 3x, aem_dm_dpr_3.1x.jpg 3.1x, aem_dm_dpr_3.2x.jpg 3.2x, aem_dm_dpr_3.3x.jpg 3.3x, aem_dm_dpr_3.4x.jpg 3.4x, aem_dm_dpr_3.5x.jpg 3.5x, aem_dm_dpr_3.6x.jpg 3.6x, aem_dm_dpr_3.7x.jpg 3.7x, aem_dm_dpr_3.8x.jpg 3.8x, aem_dm_dpr_3.9x.jpg 3.9x,
       aem_dm_dpr_4x.jpg 4x, aem_dm_dpr_4.1x.jpg 4.1x, aem_dm_dpr_4.2x.jpg 4.2x, aem_dm_dpr_4.3x.jpg 4.3x, aem_dm_dpr_4.4x.jpg 4.4x, aem_dm_dpr_4.5x.jpg 4.5x, aem_dm_dpr_4.6x.jpg 4.6x, aem_dm_dpr_4.7x.jpg 4.7x, aem_dm_dpr_4.8x.jpg 4.8x, aem_dm_dpr_4.9x.jpg 4.9x,
       aem_dm_dpr_5x.jpg 5x">
   ```

   Sie müssen diesen DPR-Bild-Tag-Code _vor_ allen statischen Bildern auf Ihrer HTML-Seite einfügen.

**Client-seitig gerenderte Apps.**

1. Schließen Sie die folgenden DPR-Skripte in den Header-Abschnitt Ihrer HTML-Seite ein:

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   <script type="text/javascript" src="dprImageInjection.js"></script>
   ```

   Sie können die beiden DPR-Skripte zusammenfassen, um mehrere Netzwerkanforderungen zu vermeiden.

   Adobe empfiehlt, diese Skripte _vor_ allen anderen Skripten auf der HTML-Seite zu laden.
Adobe empfiehlt auch, Ihre App unter dem HTML-Tag „diff“ und nicht unter einem Body-Element zu laden. Der Grund dafür ist, dass `dprImageInjection.js` das Bild-Tag dynamisch am Anfang des Body-Abschnitts auf der HTML-Seite einfügt.

## Herunterladen von JavaScript-Dateien. {#client-side-dpr-script}

Die folgenden JavaScript-Dateien im Download werden nur als Beispielreferenz bereitgestellt. Wenn Sie diese Dateien auf HTML-Seiten verwenden möchten, stellen Sie sicher, dass Sie den Code jeder Datei Ihren eigenen Anforderungen entsprechend bearbeiten.

* `dprImageInjection.js`
* `srvinit.js`
* `srvwrk.js`

[Herunterladen von JavaScript-Dateien.](/help/assets/assets-dm/aem-dynamicmedia-smartimaging-dpr.zip)

>[!MORELIKETHIS]
>
>* [Intelligente Bildbearbeitung](/help/assets/imaging-faq.md)

