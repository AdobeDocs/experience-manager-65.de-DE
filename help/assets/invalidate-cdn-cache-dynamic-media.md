---
title: Ungültigmachen des CDN-Cache über dynamische Medien
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Caches warten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.6/ASSETS
topic-tags: dynamic-media
content-type: reference
translation-type: tm+mt
source-git-commit: 6a44c4ac11f2fdf794895c28468c2a600a09b3c0
workflow-type: tm+mt
source-wordcount: '1345'
ht-degree: 4%

---


# Ungültigmachen des CDN-Cache über dynamische Medien {#invalidating-cdn-cache-for-dm-assets}

Dynamic Media-Assets werden vom CDN (Content Versand Network) zwischengespeichert, um einen schnellen Versand zu Ihren Kunden zu ermöglichen. Wenn Sie jedoch Aktualisierungen an diesen Assets vornehmen, möchten Sie möglicherweise, dass diese Änderungen sofort auf Ihrer Website wirksam werden. Durch das Löschen oder Ungültigmachen des CDN-Cache können Sie schnell die von dynamischen Medien bereitgestellten Assets aktualisieren. Anstatt darauf zu warten, dass der Cache mit einem TTL-Wert (Time To Live) abläuft (Standard ist 10 Stunden), können Sie eine Anforderung von der Benutzeroberfläche von Dynamic Media senden, damit der Cache innerhalb von Minuten abläuft.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für den Modus &quot;Dynamische Medien - Scene7&quot;in AEM 6.5, Service Pack 6 (AEM 6.5.6) oder höher. Für diese Funktion zur Ungültigmachung von CDN müssen Sie auch das im Lieferumfang von AEM Dynamic Media enthaltene Out-of-the-Box-CDN verwenden. andere benutzerdefinierte CDN werden nicht unterstützt.<br>Wenn Sie dynamische Medien in AEM 6.5, Service Pack 5 (AEM 6.5.5) oder früher verwenden, befolgen Sie die Schritte unter [Ungültigmachen des CDN-Cache mithilfe von Dynamic Media Classic](/help/assets/invalidate-cdn-cache-dm-classic.md)

See also [Caching overview in Dynamic Media](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den im CDN zwischengespeicherten Inhalt für dynamische Medienelemente ungültig:**

*Teil 1 von 2: Erstellen einer Vorlage zum Ungültigmachen eines CDN*

1. Tippen Sie in AEM 6.5.6 oder höher auf **[!UICONTROL Werkzeuge > Assets > CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-template2.png)

1. Führen Sie auf der Seite mit der Vorlage **[!UICONTROL für]** CDN-Ungültigmachung je nach Szenario eine der folgenden Optionen aus:

   | Szenario | Option |
   | --- | --- |
   | Ich habe mit Dynamic Media Classic bereits eine Vorlage für die Ungültigmachung von CDN erstellt. | Das Textfeld Vorlage **[!UICONTROL erstellen]** wird vorab mit Ihren Vorlagendaten ausgefüllt. In diesem Fall können Sie entweder die Vorlage bearbeiten oder mit dem nächsten Schritt fortfahren. |
   | Ich muss eine Vorlage erstellen. Was gebe ich ein? | Geben Sie im Textfeld &quot;Vorlage **[!UICONTROL erstellen]** &quot;eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>`verweist, anstatt einer bestimmten Bild-ID wie im folgenden Beispiel:<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br>Wenn die Vorlage nur `<ID>`enthält, füllen dynamische Medien `https://<publishserver_name>/is/image/<company_name>/<ID>` aus, wobei `<publishserver_name>` der Name Ihres Publish-Servers in den allgemeinen Einstellungen in Dynamic Media Classic definiert ist; der Name `<company_name>` des Stammordners Ihrer Firma, der dieser AEM Instanz zugeordnet ist, und `<ID>` die ausgewählten Assets über die Elementauswahl werden ungültig.<br>Alle Beiträge zu Vorgaben/Modifikatoren `<ID>` werden wie in der URL-Definition beschrieben kopiert.<br>Nur Bilder - also `/is/image` - können automatisch basierend auf der Vorlage erstellt werden.<br>Beim Hinzufügen von Assets wie Videos oder PDFs mit der Asset-Auswahl werden keine URLs automatisch generiert. `/is/content/` Stattdessen müssen Sie diese Assets entweder in der Vorlage &quot;CDN-Ungültigmachung&quot;angeben oder Sie können diese Assets manuell in *Teil 2 von 2 hinzufügen: Festlegen von Optionen* für die CDN-Ungültigmachung.<br>**Beispiele:**<br> In diesem ersten Beispiel enthält die Vorlage für die Ungültigmachung `<ID>` zusammen mit der Asset-URL `/is/content`. Beispiel: `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>`. Dynamische Medien bilden die URL auf dieser Grundlage, wobei es sich um die über die Asset-Auswahl ausgewählten Assets handelt, die ungültig werden sollen. `<ID>`<br>In diesem zweiten Beispiel enthält die Vorlage für die Ungültigmachung die vollständige URL des Assets, das in Ihren Webeigenschaften verwendet wird `/is/content` (unabhängig von der Asset-Auswahl). Beispiel: `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack` &quot;backpack&quot;ist die Asset-ID.<br>Asset-Formate, die in dynamischen Medien unterstützt werden, können ungültig gemacht werden. Zu den Asset-Dateitypen, die für die CDN-Ungültigmachung *nicht* unterstützt werden, zählen Postscript, Encapsulated PostScript, Adobe Illustrator, Adobe InDesign, Microsoft Powerpoint, Microsoft Excel, Microsoft Word und Rich Text Format.<br>Wenn Sie die Vorlage erstellen, achten Sie jedoch darauf, dass Sie die Syntax und die Schreibweise genau beachten; Bei dynamischen Medien wird keine Vorlagenüberprüfung durchgeführt.<br>Beachten Sie, dass Sie URLs für intelligente Imagemaps entweder in dieser Vorlage für die CDN-Ungültigmachung oder im Textfeld **[!UICONTROL Hinzufügen URL]** in *Teil 2 angeben müssen: Einstellen der Optionen für die CDN-Ungültigmachung.*<br>**Wichtig:**Jeder Eintrag in einer CDN-Ungültigtenvorlage muss sich in einer eigenen Zeile befinden.<br>*Das folgende Beispiel dient nur zur Veranschaulichung.* |

   ![Vorlage für die Ungültigmachung von CDN - Erstellen](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL für die Vorlage]** zur CDN-Ungültigmachung auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK.]**<br>   *Teil 2 von 2: Festlegen von Optionen für die CDN-Ungültigkeit*
   <br>

1. Tippen Sie in AEM als Cloud Service auf **[!UICONTROL Werkzeuge > Assets > CDN-Ungültigmachung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-path2.png)

1. Wählen Sie auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Hinzufügen Details]** &quot;die Assets für die Ungültigmachung des CDN aus.

   ![CDN-Ungültigerklärung - Hinzufügen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Wenn Sie die Optionen Asset- **[!UICONTROL verknüpfte Bildvorgaben im CDN]** *ungültig machen* und **[!UICONTROL auf der Grundlage der Vorlage]** ungültig machen möchten, wird die Basis-URL der ausgewählten Assets zur Ungültigmachung formatiert. Sie sollten diese Option nur für Bilder verwenden.


   | Option | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** | (Optional) Wenn Sie diese Option aktivieren, werden ausgewählte Assets und alle zugehörigen Bildvorgabe-URLs automatisch für die Cache-Ungültigmachung gebildet.<br>Assets und die zugehörigen vordefinierten URLs werden automatisch zur Ungültigmachung erstellt. Diese Option funktioniert nur für Bild-Assets. |
   | **[!UICONTROL Auf Vorlage basierende Ungültigmachung]** | (Optional) Aktivieren Sie diese Option, um nur die definierte Vorlage für die URL-Bildung zu verwenden. |
   | **[!UICONTROL Assets hinzufügen]** | Verwenden Sie die Asset-Auswahl, um Assets auszuwählen, die ungültig gemacht werden sollen. Sie können veröffentlichte oder unveröffentlichte Assets auswählen.<br>Die Zwischenspeicherung im CDN erfolgt URL-basiert und nicht Asset-basiert. Daher müssen Sie sich über die vollständigen URLs auf Ihrer Website im Klaren sein. Nachdem Sie diese URLs ermittelt haben, können Sie sie der Vorlage hinzufügen. Anschließend können Sie diese Assets auswählen und hinzufügen und die URLs in einem Schritt für ungültig erklären. <br>Verwenden Sie diese Option in Verbindung mit **[!UICONTROL Ungültigmachen von Asset-zugeordneten Bildvorgaben im CDN]**, **[!UICONTROL Ungültigmachen auf der Grundlage einer Vorlage]** oder beidem. |
   | **[!UICONTROL URL hinzufügen]** | Fügen Sie Dynamischen Medien-Assets, deren CDN-Cache Sie ungültig machen möchten, manuell vollständige URL-Pfade hinzu oder fügen Sie sie ein. Verwenden Sie diese Option, wenn Sie in ***Teil 1 von 2 keine Vorlage für das Ungültigmachen eines CDN erstellt haben: Erstellen einer Vorlage*** für die Ungültigmachung von CDN und nur wenige Assets zum Ungültigmachen.<br>**Wichtig:** Jede URL, die Sie hinzufügen, muss sich in einer eigenen Zeile befinden.<br>Sie können bis zu 1000 URLs zu einem bestimmten Zeitpunkt für ungültig erklären. Wenn die Anzahl der URLs im Textfeld **[!UICONTROL Hinzufügen URL]** größer als 1000 ist, können Sie nicht auf **[!UICONTROL Weiter]** tippen. In diesem Fall müssen Sie auf **[!UICONTROL X]** rechts neben einem ausgewählten Asset oder auf eine manuell hinzugefügte URL tippen, um es aus der Liste für die Ungültigmachung zu löschen.<br>Beachten Sie, dass Sie URLs für intelligente Imagemaps entweder in der Vorlage &quot;CDN-Ungültigmachung&quot;oder in diesem Textfeld für die **[!UICONTROL Hinzufügen URL]** angeben müssen. |

1. Near the upper-right corner of the page, tap **[!UICONTROL Next.]**
1. Auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;wird im Feld &quot; **[!UICONTROL URLs]** -Liste&quot;eine Liste einer oder mehrerer URLs angezeigt, die aus der zuvor erstellten Vorlage zur Ungültigmachung des CDN und den soeben hinzugefügten Assets generiert wurden.

   Beispiel: Angenommen, Sie haben ein einzelnes Asset namens hinzugefügt, das in den vorherigen Schritten gezeigt wurde, und verwenden das Beispiel für eine Vorlage zum Ungültigmachen von CDN, das zuvor gezeigt wurde `spinset`. Wenn Sie auf **[!UICONTROL Extras > Assets > CDN-Ungültigmachung]** tippen, werden die folgenden fünf generierten URLs in der Benutzeroberfläche &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;angezeigt:

   ![CDN-Ungültigerklärung - Bestätigen](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Falls erforderlich, tippen Sie auf **X** rechts neben einer URL, um sie aus dem Ungültigmachen-Prozess zu löschen.

1. Tippen Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Senden]** , um den CDN-Ungültigkeitsprozess zu starten.

## Fehlerbehebung bei CDN-Ungültigkeitsfehlern

In allen Fällen wird entweder der gesamte Stapel zur Ungültigmachung verarbeitet oder der gesamte Stapel ist fehlgeschlagen.

| Fehler | Erklärung |
| --- | --- |
| *URL(s) für ausgewählte Assets konnten nicht abgerufen werden.* | Tritt auf, wenn eines der folgenden Szenarien erfüllt ist:<br>- Eine Konfiguration für dynamische Medien wurde nicht gefunden.<br>- Beim Abrufen eines Dienstbenutzers, über den die Konfiguration für dynamische Medien gelesen wird, gibt es eine Ausnahme.<br>- Der Veröffentlichungsserver bzw. der Firma-Stammordner, der zum Erstellen der URLs verwendet wird, fehlen in der Konfiguration für dynamische Medien. |
| *Einige URLs sind nicht korrekt definiert. Bitte korrigieren und erneut einreichen.* | Tritt auf, wenn die IPS CDN-Cache-Ungültigungs-API einen Fehler zurückgibt, dass die URL auf eine andere Firma verweist, oder wenn die URL gemäß der von der IPS cdnCacheInvalidation API durchgeführten Überprüfung ungültig ist. |
| *CDN-Cache konnte nicht ungültig gemacht werden.* | Tritt auf, wenn die Anforderung zum Ungültigmachen des CDN-Cache aus einem anderen Grund fehlschlägt. |
| *Keine URL(s) eingegeben, um ungültig zu werden.* | Tritt auf, wenn auf der Seite &quot; **[!UICONTROL CDN-Ungültigmachung - Bestätigen]** &quot;keine URLs vorhanden sind und Sie auf **[!UICONTROL &quot;Senden&quot;tippen.]** |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
