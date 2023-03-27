---
title: Asset-Auswahl
description: Erfahren Sie, wie Sie mit der Asset-Auswahl Metadaten für Assets in Adobe Experience Manager Assets suchen, filtern, durchsuchen und abrufen können. Erfahren Sie außerdem, wie Sie die Benutzeroberfläche des Asset-Wählers anpassen.
contentOwner: AG
feature: Asset Management,Metadata,Search
role: User
exl-id: 4b518ac0-5b8b-4d61-ac31-269aa1f5abe4
source-git-commit: 4139b42d5cd3d7d1d93863dc07cfafd58c3f64f2
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 43%

---

# Asset-Wähler {#asset-selector}

>[!NOTE]
>
>Der Asset-Selektor wurde als [Asset-Auswahl](https://helpx.adobe.com/de/experience-manager/6-2/assets/using/asset-picker.html) in früheren Versionen von [!DNL Experience Manager].

Mit der Asset-Auswahl können Sie Assets in [!DNL Adobe Experience Manager] Assets. Sie können auch die Metadaten von Assets abrufen, die Sie mithilfe des Asset-Wählers auswählen. Um die Benutzeroberfläche des Asset-Wählers anzupassen, können Sie sie mit unterstützten Anforderungsparametern starten. Diese Parameter legen den Kontext des Asset-Wählers für ein bestimmtes Szenario fest.

Derzeit können Sie die Anforderungsparameter übergeben `assettype` (*Bild/Video/Text*) und Auswahl `mode` (*Einfach/Mehrere*) als Kontextinformationen für die Asset-Auswahl, die während der Auswahl intakt bleiben.

Der Asset-Selektor verwendet HTML5 **Window.postMessage** -Meldung, um Daten für das ausgewählte Asset an den Empfänger zu senden.

Der Asset-Wähler basiert auf dem Vokabular der Foundation-Auswahl von Granite. Standardmäßig befindet sich der Asset-Wähler im Suchmodus. Sie können jedoch mithilfe des Omnisearch-Erlebnisses Filter anwenden, um Ihre Suche nach bestimmten Assets zu verfeinern.

Sie können jede Web-Seite (unabhängig davon, ob sie Teil des CQ-Containers ist) mit der Asset-Auswahl (`https://[AEM_server]:[port]/aem/assetpicker.html`).

## Kontextparameter {#contextual-parameters}

Sie können die folgenden Anfrageparameter in einer URL übergeben, um den Asset-Wähler in einem bestimmten Kontext zu starten:

| Name | Werte | Beispiel | Zweck |
|---|---|---|---|
| resource suffix (B) | Ordnerpfad als Ressourcensuffix in der URL:  `http://localhost:4502/aem/`<br>`assetpicker.html/<folder_path>` | Zum Starten des Asset-Wählers mit einem bestimmten Ordner, z. B. mit ausgewähltem Ordner `/content/dam/we-retail/en/activities`, sollte die URL wie folgt aussehen: `http://localhost:4502/aem/assetpicker.html`<br>`/content/dam/we-retail/en/activities?assettype=images` | Wenn beim Starten des Asset-Wählers ein bestimmter Ordner ausgewählt sein soll, können Sie ihn als Ressourcensuffix übergeben. |
| mode | single, multiple | `http://localhost:4502/aem/assetpicker.html`<br>`?mode=multiple` <br> `http://localhost:4502/aem/assetpicker.html`<br>`?mode=single` | Im Modus „multiple“ können Sie mit dem Asset-Wähler mehrere Assets gleichzeitig auswählen. |
| Dialogfeld | true, false | `http://localhost:4502/aem/assetpicker.html`<br>`?dialog=true` | Verwenden Sie diese Parameter, um den Asset-Wähler als Granite-Dialogfeld zu öffnen. Diese Option ist nur relevant, wenn Sie den Asset-Wähler per Granite-Pfadfeld starten und als pickerSrc-URL konfigurieren. |
| root | `<folder_path>` | `http://localhost:4502/aem/`<br>`assetpicker.html?assettype=images`<br>`&root=/content/dam/we-retail/en/activities` | Verwenden Sie diese Option, um den Stammordner für den Asset-Wähler anzugeben. In diesem Fall können Sie mit dem Asset-Wähler nur untergeordnete Assets (direkt/indirekt) unter dem Stammordner auswählen. |
| viewmode | Suchen |  | So starten Sie die Asset-Auswahl im Suchmodus mit den Parametern Assettyp und MIME-Typ . |
| assettype (S) | Bilder, Dokumente, Multimedia, Archive | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=images`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=documents`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=multimedia`</li> <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&assettype=archives`</li> | Verwenden Sie diese Option, um Asset-Typen anhand des übergebenen Werts zu filtern. |
| mimetype | MIME-Typen (`/jcr:content/metadata/dc:format`) eines Assets (Platzhalter wird ebenfalls unterstützt) | <ul><li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=image/png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&?mimetype=*png`</li>  <li>`http://localhost:4502/aem/assetpicker.html?viewmode=search&mimetype=*presentation`</li>  <li>`http://localhost:4502/aem/assetpicker?viewmode=search&mimetype=*presentation&mimetype=*png`</li></ul> | Filtern von Assets nach MIME-Typ(en) |

## Verwenden der Asset-Auswahl {#using-the-asset-selector}

1. Wechseln Sie für den Zugriff auf die Benutzeroberfläche des Asset-Wählers zu `https://[AEM_server]:[port]/aem/assetpicker`.
1. Navigieren Sie zum gewünschten Ordner und wählen Sie mindestens ein Asset aus.

   ![chlimage_1-441](assets/chlimage_1-441.png)

   Alternativ können Sie im OmniSearch-Feld nach dem gewünschten Asset suchen und es dann auswählen.

   ![chlimage_1-442](assets/chlimage_1-442.png)

   Wenn Sie über das OmniSearch-Feld nach Assets suchen, können Sie verschiedene Filter aus dem **[!UICONTROL Filter]** -Bereich, um die Suche zu verfeinern.

   ![chlimage_1-443](assets/chlimage_1-443.png)

1. Tippen/klicken **[!UICONTROL Auswählen]** aus der Symbolleiste.
