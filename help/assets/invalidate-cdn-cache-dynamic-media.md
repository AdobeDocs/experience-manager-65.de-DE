---
title: Invalidierung des CDN-Cache über Dynamic Media
description: Indem Sie die Inhalte im CDN (Content Delivery Network)-Cache ungültig machen, können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Sie müssen dazu also nicht auf einen Ablauf des Cache warten.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.6/ASSETS
topic-tags: dynamic-media
content-type: reference
role: Business Practitioner, Administrator
exl-id: 23d3c274-0736-49f7-8d44-a56a55cfd06d
feature: CDN-Cache
source-git-commit: 9134130f349c6c7a06ad9658a87f78a86b7dbf9c
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 55%

---

# Invalidierung des CDN-Cache über Dynamic Media {#invalidating-cdn-cache-for-dm-assets}

Dynamic Media-Assets werden vom CDN (Content Delivery Network) zwischengespeichert, um eine schnelle Bereitstellung an Ihre Kunden zu ermöglichen. Wenn Sie jedoch Aktualisierungen an diesen Assets vornehmen, möchten Sie, dass diese Änderungen sofort auf Ihrer Website wirksam werden. Durch Löschen oder Invalidierung des CDN-Cache können Sie von Dynamic Media bereitgestellte Assets schnell aktualisieren. Anstatt darauf zu warten, dass der Cache mit einem TTL-Wert (Time To Live) abläuft (der Standardwert lautet zehn Stunden), können Sie eine Anfrage aus Dynamic Media senden, damit der Cache innerhalb von Minuten abläuft.

>[!NOTE]
>
>Für diese Funktion müssen Sie das vordefinierte CDN verwenden, das im Lieferumfang von Adobe Experience Manager Dynamic Media enthalten ist. Mit dieser Funktion werden keine anderen benutzerdefinierten CDNs unterstützt.

>[!IMPORTANT]
>
>Die folgenden Schritte gelten nur für den Dynamic Media-Scene7-Modus in Adobe Experience Manager 6.5, Service Pack 6 (Experience Manager 6.5.6) oder höher. Für diese CDN-Invalidierung müssen Sie außerdem das vordefinierte CDN verwenden, das im Lieferumfang von Experience Manager Dynamic Media enthalten ist. andere benutzerdefinierte CDNs werden nicht unterstützt.<br>Wenn Sie Dynamic Media in Experience Manager 6.5, Service Pack 5 (Experience Manager 6.5.5) oder früher verwenden, führen Sie die Schritte unter  [Invalidierung des CDN-Cache über Dynamic Media Classic aus.](/help/assets/invalidate-cdn-cache-dm-classic.md)

Siehe auch [Übersicht über Caching in Dynamic Media](https://helpx.adobe.com/de/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**So machen Sie den Inhalt im CDN-Cache für Dynamic Media-Assets ungültig:**

*Teil 1 von 2: Erstellen einer Vorlage für die CDN-Invalidierung*

1. Tippen Sie in Experience Manager 6.5.6 oder höher auf **[!UICONTROL Tools > Assets > CDN-Invalidierung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-template2.png)

1. Führen Sie auf der Seite mit der **[!UICONTROL Vorlage für CDN-Invalidierung]** je nach Ihrem Szenario eine der folgenden Optionen aus:

   | Szenario | Option |
   | --- | --- |
   | Ich habe mit Dynamic Media Classic bereits früher eine Vorlage für CDN-Invalidierung erstellt. | Das Textfeld **[!UICONTROL Vorlage erstellen]** wird vorab mit Ihren Vorlagendaten ausgefüllt. In diesem Fall können Sie entweder die Vorlage bearbeiten oder mit dem nächsten Schritt fortfahren. |
   | Ich muss eine Vorlage erstellen. Was gebe ich ein? | Geben Sie im Textfeld **[!UICONTROL Vorlage erstellen]** eine Bild-URL (einschließlich Bildvorgaben oder Modifikatoren) ein, die auf `<ID>` verweist, anstatt auf eine bestimmte Bild-ID wie im folgenden Beispiel:<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br>Wenn die Vorlage nur `<ID>` enthält, füllt Dynamic Media `https://<publishserver_name>/is/image/<company_name>/<ID>` aus, wobei `<publishserver_name>` der Name Ihres Veröffentlichungsservers ist, der in den allgemeinen Einstellungen in Dynamic Media Classic definiert ist. . `<company_name>` ist der Name Ihres Unternehmensstamms, der dieser Experience Manager-Instanz zugeordnet ist, und `<ID>` ist die ausgewählten Assets über die Asset-Auswahl, die ungültig gemacht werden sollen.<br>Alle Vorgaben/Modifikatoren `<ID>` werden im Istzustand in die URL-Definition kopiert.<br>Nur Bilder - also  `/is/image` - können basierend auf der Vorlage automatisch erstellt werden.<br>Wenn bei `/is/content/` mit der Asset-Auswahl Assets wie Videos oder PDFs hinzugefügt werden, werden keine automatischen URLs generiert. Stattdessen müssen Sie diese Assets entweder in der Vorlage für CDN-Invalidierung angeben oder die URL den Assets manuell hinzufügen in *Teil 2 von 2: Festlegen von CDN-Invalidierungsoptionen*.<br>**Beispiele:**<br> In diesem ersten Beispiel enthält die Vorlage für die Invalidierung `<ID>` zusammen mit der Asset-URL, die `/is/content` aufweist. Beispiel: `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>`. Dynamic Media bildet die URL auf Grundlage dieses Pfads, wobei `<ID>` die über die Asset-Auswahl ausgewählten Assets ist, die ungültig gemacht werden sollen.<br>In diesem zweiten Beispiel enthält die Vorlage für die Invalidierung die vollständige URL des Assets, das in Ihren Web-Eigenschaften verwendet wird, mit `/is/content` (unabhängig von der Asset-Auswahl). Beispiel: `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack`, wobei „backpack“ die Asset-ID ist.<br>Asset-Formate, die in Dynamic Media unterstützt werden, können ungültig gemacht werden. Zu den Asset-Dateitypen, die *nicht* für die CDN-Invalidierung unterstützt werden, gehören PostScript®, Encapsulated PostScript®, Adobe Illustrator, Adobe InDesign, Microsoft Powerpoint, Microsoft Excel, Microsoft Word und Rich Text Format.<br>Achten Sie beim Erstellen der Vorlage genau auf Syntax und mögliche Rechtschreibfehler. Dynamic Media nimmt keine Vorlagenüberprüfung vor.<br>Geben Sie URLs für smartes Zuschneiden von Bildern entweder in dieser Vorlage für CDN-Invalidierung oder im Textfeld  **[!UICONTROL URL hinzufügen in]**   *Teil 2 an: Festlegen von CDN-Invalidierungsoptionen.*<br>**Wichtig:** Jeder Eintrag in einer Vorlage für CDN-Invalidierung muss sich in einer eigenen Zeile befinden.<br>*Das folgende Vorlagenbeispiel dient nur zur Veranschaulichung.* |

   ![Vorlage für CDN-Invalidierung – Erstellen](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

1. Tippen Sie in der rechten oberen Ecke der Seite **[!UICONTROL Vorlage für CDN-Invalidierung]** auf **[!UICONTROL Speichern]** und dann auf **[!UICONTROL OK.]**<br>

   *Teil 2 von 2: Einrichten von CDN-Invalidierunsoptionen*
   <br>

1. Tippen Sie in Experience Manager as a Cloud Service auf **[!UICONTROL Tools > Assets > CDN-Invalidierung.]**

   ![CDN-Validierungsfunktion](/help/assets/assets-dm/cdn-invalidation-path2.png)

1. Wählen Sie auf der Seite **[!UICONTROL CDN-Invalidierung - Details hinzufügen]** die Assets für die CDN-Invalidierung aus.

   ![CDN-Invalidierung – Details hinzufügen](/help/assets/assets-dm/cdn-invalidation-add-details-2.png)

   >[!NOTE]
   >
   >Wenn Sie die Optionen **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** *und* **[!UICONTROL Invalidierung anhand von Vorlage]** deaktiviert lassen, wird zur Invalidierung die Basis-URL der ausgewählten Assets gebildet. Verwenden Sie diese Optionsanordnung nur für Bilder.


   | Option | Beschreibung |
   | --- | --- |
   | **[!UICONTROL Invalidierungs-Asset hat Bildvorgaben in CDN zugeordnet]** | (Optional) Wenn Sie diese Option aktivieren, werden ausgewählte Assets und alle zugehörigen Bildvorgabe-URLs für die Cache-Invalidierung automatisch gebildet.<br>Assets und die zugehörigen vordefinierten Vorgabe-URLs werden für die Invalidierung automatisch erstellt. Diese Option funktioniert nur bei Bild-Assets. |
   | **[!UICONTROL Invalidierung anhand von Vorlage]** | (Optional) Aktivieren Sie diese Option, um nur die definierte Vorlage für die URL-Bildung zu verwenden. |
   | **[!UICONTROL Assets hinzufügen]** | Verwenden Sie die Asset-Auswahl, um Assets auszuwählen, die ungültig gemacht werden sollen. Sie können entweder veröffentlichte Assets oder Assets auswählen, deren Veröffentlichung rückgängig gemacht wurde.<br>Die Zwischenspeicherung im CDN erfolgt URL-basiert und nicht Asset-basiert. Daher müssen Sie sich der vollständigen URLs auf Ihrer Website bewusst sein. Nachdem Sie die URLs ermittelt haben, können Sie sie der Vorlage hinzufügen. Anschließend können Sie die Assets auswählen und die URLs in einem Schritt ungültig machen. <br>Verwenden Sie diese Option mit  **[!UICONTROL Invalidierungs-Asset-Bildvorgaben in CDN]**,  **[!UICONTROL Invalidierung basierend auf Vorlage]** oder beidem. |
   | **[!UICONTROL URL hinzufügen]** | Fügen Sie für Dynamic Media-Assets, deren CDN-Cache Sie ungültig machen möchten, manuell vollständige URL-Pfade hinzu oder fügen Sie sie ein. Nutzen Sie diese Option, wenn Sie in ***Teil 1 von 2: Erstellen einer Vorlage für CDN-Invalidierung*** eine Vorlage für CDN-Invalidierung erstellt haben und nur über einige Assets zur Invalidierung verfügen.<br>**Wichtig:** Jede URL, die Sie hinzufügen, muss sich in einer eigenen Zeile befinden.<br>Sie können bis zu 1.000 URLs auf einmal ungültig machen. Wenn die Anzahl der URLs im Textfeld **[!UICONTROL URL hinzufügen]** höher als 1.000 ist, können Sie nicht auf **[!UICONTROL Weiter]** tippen. In dem Fall müssen Sie rechts neben einem ausgewählten Asset oder einer manuell hinzugefügten URL auf **[!UICONTROL X]** tippen, um das Asset oder die URL aus der Liste für die Invalidierung zu löschen.<br>Geben Sie URLs für smartes Zuschneiden von Bildern entweder in der Vorlage für CDN-Invalidierung oder im Textfeld  **[!UICONTROL URL hinzufügen]** an. |

1. Tippen Sie oben rechts auf **[!UICONTROL Weiter]**.
1. Auf der Seite **[!UICONTROL CDN-Invalidierung - Bestätigen]** im Listenfeld **[!UICONTROL URLs]** können Sie eine Liste mit einer oder mehreren URLs sehen, die aus der zuvor erstellten Vorlage für CDN-Invalidierung und den soeben hinzugefügten Assets generiert wurden.

   Nehmen wir zum Beispiel an, dass Sie mit der Vorlage für CDN-Invalidierung, die in den vorherigen Schritten beschrieben wurde, ein Asset namens `spinset` hinzugefügt haben. Wenn Sie auf **[!UICONTROL Tools > Assets > CDN-Invalidierung]** tippen, werden die folgenden fünf generierten URLs in der Benutzeroberfläche **[!UICONTROL CDN-Invalidierung - Confirm]** erstellt:

   ![CDN-Invalidierung – Bestätigen](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Falls erforderlich, tippen Sie rechts neben einer URL auf **X**, um sie aus dem Invalidierungsprozess zu entfernen.

1. Tippen Sie in der rechten oberen Ecke der Seite auf **[!UICONTROL Übermitteln]**, um die CDN-Invalidierung zu starten.

## Behebung von Fehlern bei der CDN-Invalidierung

In jedem Fall wird entweder der gesamte Batch zur Invalidierung verarbeitet oder schlägt der gesamte Batch fehl.

| Fehler | Erklärung |
| --- | --- |
| *URLs für ausgewählte Assets konnten nicht abgerufen werden.* | Tritt auf, wenn eines der folgenden Szenarien erfüllt ist:<br>- Eine Dynamic Media-Konfiguration wurde nicht gefunden.<br>- Beim Abrufen eines Dienstbenutzers, über den die Dynamic Media-Konfiguration gelesen wird, gibt es eine Ausnahme.<br>- Der Veröffentlichungs-Server oder der Unternehmensstamm, der zum Erstellen der URLs verwendet wird, fehlt in der Dynamic Media-Konfiguration. |
| *Einige URLs sind nicht richtig definiert. Korrigieren und übermitteln Sie sie erneut.* | Tritt auf, wenn die IPS CDN-Cache-Invalidierungs-API einen Fehler zurückgibt, dass die URL auf ein anderes Unternehmen verweist. Oder, wenn die URL gemäß der von der IPS `cdnCacheInvalidation`-API durchgeführten Überprüfung ungültig ist. |
| *CDN-Cache konnte nicht ungültig gemacht werden.* | Tritt auf, wenn die Anfrage zur Invalidierung des CDN-Cache aus einem anderen Grund fehlschlägt. |
| *Keine URLs eingegeben, die ungültig gemacht werden sollen.* | Tritt auf, wenn auf der Seite **[!UICONTROL CDN-Invalidierung - Bestätigen]** keine URLs vorhanden sind und Sie auf **[!UICONTROL Senden.]** tippen. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, tap **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
