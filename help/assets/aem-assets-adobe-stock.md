---
title: Verwalten [!DNL Adobe Stock] Assets
description: Suchen, lizenzieren, verwalten und rufen Sie [!DNL Adobe Stock] -Assets in [!DNL Adobe Experience Manager] ab. Nutzen Sie die lizenzierten Assets wie jedes andere digitale Asset.
contentOwner: AG
feature: Search, Adobe Stock
role: Geschäftspraktiker, Administrator
translation-type: tm+mt
source-git-commit: 2e734041bdad7332c35ab41215069ee696f786f4
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 86%

---


# Verwenden von [!DNL Adobe Stock]-Assets in [!DNL Adobe Experience Manager Assets] {#use-adobe-stock-assets-in-aem-assets}

Organisationen können ihr [!DNL Adobe Stock]-Unternehmensabo mit [!DNL Experience Manager Assets] integrieren, damit lizenzierte Assets für kreative und Marketing-Projekte umfassend verfügbar sind und mit den leistungsstarken Asset-Management-Funktionen von [!DNL Experience Manager] verwaltet werden können.

Der [!DNL Adobe Stock]-Service bietet Designern und Unternehmen Zugang zu Millionen von hochwertigen, kuratierten und gebührenfreien Fotos, Vektorgrafiken, Illustrationen, Videos, Vorlagen und 3D-Assets für sämtliche Kreativprojekte. [!DNL Experience Manager]-Benutzer können [!DNL Adobe Stock]-Assets, die in [!DNL Experience Manager] gespeichert sind, schnell finden, eine Vorschau anzeigen und die Lizenz abrufen, ohne ihre [!DNL Experience Manager]-Oberfläche zu verlassen.

## Voraussetzungen {#prerequisites}

Die Integration erfordert einen [enterprise [!DNL Adobe Stock] plan](https://stockenterprise.adobe.com/).

## Integrieren von [!DNL Experience Manager] und [!DNL Adobe Stock] {#integrate-aem-and-adobe-stock}

Um die Kommunikation zwischen [!DNL Experience Manager] und [!DNL Adobe Stock] zu ermöglichen, erstellen Sie eine IMS- sowie eine [!DNL Adobe Stock]-Konfiguration in [!DNL Experience Manager].

>[!NOTE]
>
>Nur [!DNL Experience Manager]- und [!DNL Admin Console]-Administratoren einer Organisation können die Integration durchführen, da hierfür Administratorrechte erforderlich sind.

### Erstellen einer IMS-Konfiguration  {#create-an-ims-configuration}

1. Navigieren Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Adobe IMS-Konfigurationen]**. Klicken Sie auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Cloud-Lösung]** > **[!UICONTROL Adobe Stock]**.
1. Verwenden Sie entweder ein bestehendes Zertifikat oder wählen Sie **[!UICONTROL Neues Zertifikat erstellen]** aus.
1. Klicken Sie auf **[!UICONTROL Zertifikat erstellen]**. Laden Sie nach der Erstellung den öffentlichen Schlüssel herunter. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Fügen Sie den heruntergeladenen Schlüssel zu Ihrem [!DNL Adobe Developer Console]-Service-Konto hinzu. Klicken Sie auf **[!UICONTROL Weiter]**. Lassen Sie den Bildschirm [!UICONTROL Konfiguration des technischen Adobe IMS-Kontos] geöffnet, um die Werte in Kürze anzugeben.
1. Greifen Sie auf die [Adobe Developer Console](https://console.adobe.io) zu. Stellen Sie sicher, dass Ihr Konto über Administratorrechte für die Organisation verfügt, für die die Integration benötigt wird.
1. Klicken Sie auf **[!UICONTROL Neues Projekt erstellen]** und dann auf **[!UICONTROL API hinzufügen]**. Wählen Sie **[!UICONTROL Adobe Stock]** aus der Liste der zur Verfügung stehenden APIs. Wählen Sie [!UICONTROL OAUTH 2.0 Web]. Konfigurieren und kopieren Sie die verschiedenen angezeigten Werte.
1. Geben Sie in [!DNL Experience Manager] in den Feldern **[!UICONTROL Titel]**, **[!UICONTROL Autorisierungs-Server]**, **[!UICONTROL API-Schlüssel]**, **[!UICONTROL Client-Geheimnis]** und **[!UICONTROL Payload]** die entsprechenden Werte ein. Genaue Informationen zu diesen Werten finden Sie in der [Schnellanleitung zur JWT-Authentifizierung](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/JWT/JWT.md).

<!-- TBD: Update the URL to update the terminology when AIO team updates their documentation URL. Logged issue github.com/AdobeDocs/adobeio-auth/issues/63.
-->

### Erstellen der [!DNL Adobe Stock]-Konfiguration in [!DNL Experience Manager] {#create-adobe-stock-configuration-in-aem}

1. Navigieren Sie in [!DNL Experience Manager] zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Stock]**.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um eine Konfiguration zu erstellen und sie Ihrer bestehenden IMS-Konfiguration zuzuordnen. Wählen Sie `PROD` als Umgebungsparameter aus.
1. Lassen Sie den Speicherort im Feld **[!UICONTROL Pfad lizenzierter Assets]** unverändert. Ändern Sie den Speicherort nicht in den Pfad, in dem Sie die [!DNL Adobe Stock]-Assets speichern möchten.
1. Schließen Sie die Erstellung ab, indem Sie alle erforderlichen Eigenschaften hinzufügen. Klicken Sie auf **[!UICONTROL Speichern und schließen]**.
1. Fügen Sie [!DNL Experience Manager]-Benutzer oder -Gruppen hinzu, die die Assets lizenzieren können.

>[!NOTE]
>
>Wenn mehrere [!DNL Adobe Stock]-Konfigurationen vorhanden sind, wählen Sie im Feld „Benutzereinstellungen“ die gewünschte Konfiguration aus.  Klicken Sie zum Aufrufen des Bedienfelds von der Startseite [!DNL Experience Manager] auf das Benutzersymbol und dann auf **[!UICONTROL Benutzereinstellungen]** > **[!UICONTROL Lagerkonfiguration]**.

## Verwenden und Verwalten von [!DNL Adobe Stock]-Assets in [!DNL Experience Manager] {#usemanage}

Mit dieser Funktion können Organisationen ihren Benutzern die Arbeit mit [!DNL Adobe Stock]-Assets in [!DNL Experience Manager Assets] ermöglichen. Benutzer können aus der [!DNL Experience Manager]-Benutzeroberfläche heraus nach [!DNL Adobe Stock]-Assets suchen und die erforderlichen Assets lizenzieren.

Sobald ein [!DNL Adobe Stock]-Asset in [!DNL Experience Manager] lizenziert ist, kann es wie ein typisches Asset verwendet und verwaltet werden. Benutzer können Assets in [!DNL Experience Manager] suchen und eine Vorschau zu diesen anzeigen, Assets kopieren und veröffentlichen, Assets in [!DNL Brand Portal] teilen, Assets per [!DNL Experience Manager]-Desktop-Programm aufrufen und verwenden und vieles mehr.

![Suchen nach  [!DNL Adobe Stock] Assets und Filtern der Ergebnisse aus Ihrem  [!DNL Adobe Experience Manager] Arbeitsbereich](assets/adobe-stock-search-results-workspace.png)

*Abbildung: Suchen Sie nach  [!DNL Adobe Stock] Assets und filtern Sie die Ergebnisse aus Ihrer  [!DNL Experience Manager] Oberfläche.*

**A.**[!DNL Adobe Stock] Suchen Sie Assets, die den Assets ähneln, deren ID bereitgestellt wird. **B.** Nach Assets suchen, die Ihrer Form- und Ausrichtungswahl entsprechen. **C.** Suchen Sie nach einem der unterstützten Asset-Typen  **D.** Öffnen Sie den Bereich &quot;Filter&quot; **E.** Lizenz und speichern Sie das ausgewählte Asset in  [!DNL Experience Manager] **F.** Speichern Sie das Asset  [!DNL Experience Manager] mit dem Wasserzeichen  **G.**   [!DNL Adobe Stock]   ****   [!DNL Adobe Stock]   ****   **** Untersuchen Sie Assets auf der Website, die dem ausgewählten Asset ähnlich sind.Ansicht der ausgewählten Assets auf der SeiteI.AnsichtAnzahl der ausgewählten Assets SuchergebnisseAnsicht der  zwischen Karte und Liste

### Suchen von Assets {#find-assets}

Ihre [!DNL Experience Manager]-Benutzer können in [!DNL Experience Manager] und [!DNL Adobe Stock] nach Assets suchen. Wenn die Suche nicht auf [!DNL Adobe Stock] beschränkt ist, werden Suchergebnisse aus [!DNL Experience Manager] und [!DNL Adobe Stock] angezeigt.

* Um nach [!DNL Adobe Stock]-Assets zu suchen, klicken Sie auf **[!UICONTROL Navigation]** > **[!UICONTROL Assets]** > **[!UICONTROL Adobe Stock durchsuchen]**.

* Um in [!DNL Adobe Stock] und [!DNL Experience Manager Assets] nach Assets zu suchen, klicken Sie auf ![Suchen](assets/do-not-localize/search_icon.png).

Geben Sie alternativ `Location: Adobe Stock` in die Suchleiste ein, um [!DNL Adobe Stock]-Assets auszuwählen. [!DNL Experience Manager] bietet erweiterte Filterfunktionen, mit denen Benutzer schnell die gewünschten Assets finden können. Hierzu stehen Filter, wie z. B. unterstützte Asset-Typen, Bildausrichtung und Lizenzstatus, zur Verfügung.

>[!NOTE]
>
>In [!DNL Adobe Stock] durchsuchte Assets werden nur in [!DNL Experience Manager] angezeigt. [!DNL Adobe Stock]-Assets werden nur dann abgerufen und im [!DNL Experience Manager]-Repository gespeichert, wenn Benutzer [Assets speichern](/help/assets/aem-assets-adobe-stock.md#saveassets) oder [Assets lizenzieren und speichern](/help/assets/aem-assets-adobe-stock.md#licenseassets). Assets, die bereits in [!DNL Experience Manager] gespeichert sind, werden angezeigt und hervorgehoben, um einfachen Zugriff und eine schnelle Referenzierung zu ermöglichen. Außerdem werden die [!DNL Stock]-Assets mit einigen zusätzlichen Metadaten gespeichert, um die Quelle als [!DNL Stock] anzugeben.

![Filter in  [!DNL Experience Manager] und hervorgehobene  [!DNL Adobe Stock] Assets in Suchergebnissen suchen](assets/aem-search-filters2.jpg)

*Abbildung: Suchfilter in [!DNL Experience Manager] und hervorgehobene [!DNL Adobe Stock]-Assets in Suchergebnissen.*

### Speichern und Anzeigen erforderlicher Assets {#saveassets}

Wählen Sie ein Asset aus, das Sie in [!DNL Experience Manager] speichern möchten. Klicken Sie in der oberen Symbolleiste auf [!UICONTROL Speichern] und geben Sie den Namen und Speicherort des Assets an. Unlizenzierte Assets werden lokal mit Wasserzeichen gespeichert.

Wenn Sie erneut nach Assets suchen, werden die gespeicherten Assets durch ein Symbol hervorgehoben, um anzuzeigen, dass diese Assets in [!DNL Experience Manager Assets] verfügbar sind.

>[!NOTE]
>
>Bei den kürzlich hinzugefügten Assets wird das Symbol „Neu“ anstelle des Symbols „Lizenziert“ angezeigt.

### Lizenzieren von Assets {#licenseassets}

Benutzer können [!DNL Adobe Stock]-Assets über das Kontingent ihres [!DNL Adobe Stock]-Unternehmensplans lizenzieren. Wenn Sie ein Asset lizenzieren, wird es ohne Wasserzeichen gespeichert und ist in der Suche sowie für die Verwendung in [!DNL Experience Manager Assets] verfügbar.

![Dialogfeld zum Lizenzieren und Speichern von  [!DNL Adobe Stock] Assets in  [!DNL Experience Manager Assets]](assets/aem-stock_licenseandsave.jpg)

*Abbildung: Dialogfeld zum Lizenzieren und Speichern von [!DNL Adobe Stock]-Assets in [!DNL Experience Manager Assets].*

### Anzeigen von Metadaten und Asset-Eigenschaften {#access-metadata-and-asset-properties}

Benutzer können Metadaten, einschließlich der [!DNL Adobe Stock]-Metadateneigenschaften für Assets, die in [!DNL Experience Manager] gespeichert wurden, öffnen bzw. eine Vorschau dieser Daten anzeigen und **[!UICONTROL Lizenzreferenzen]** für Assets hinzufügen. Die Änderungen an der Lizenzreferenz werden zwischen [!DNL Experience Manager] und der [!DNL Adobe Stock]-Website jedoch nicht synchronisiert.

Benutzer können die Eigenschaften für lizenzierte und unlizenzierte Assets anzeigen.

![Metadaten und Lizenzreferenzen gespeicherter Assets anzeigen](assets/metadata_properties.jpg)

*Abbildung: Metadaten und Lizenzreferenzen gespeicherter Assets anzeigen und aufrufen.*

## Bekannte Einschränkungen {#known-limitations}

* **Redaktionelle Bildwarnung wird nicht angezeigt**: Bei der Lizenzierung eines Bilds können Benutzer nicht prüfen, ob ein Bild ausschließlich der redaktionellen Verwendung dient. Um zu verhindern, dass Bilder falsch verwendet werden, können Administratoren den Zugriff auf redaktionelle Assets über die Admin Console deaktivieren.

* **Falscher Lizenztyp wird angezeigt**: Es ist möglich, dass in [!DNL Experience Manager] ein falscher Lizenztyp für ein Asset angezeigt wird. Benutzer können sich bei der [!DNL Adobe Stock]-Website anmelden, um den richtigen Lizenztyp zu ermitteln.

* **Referenzfelder und Metadaten werden nicht synchronisiert**: Wenn ein Benutzer ein Lizenzreferenzfeld aktualisiert, werden die Lizenzreferenzdaten in [!DNL Experience Manager] aktualisiert, jedoch nicht auf der [!DNL Adobe Stock]-Website. Ebenso werden Änderungen, die Benutzer an den Referenzfeldern auf der [!DNL Adobe Stock]-Website vornehmen, nicht mit [!DNL Experience Manager] synchronisiert.

>[!MORELIKETHIS]
>
>* [Videoschulung zum  [!DNL Adobe Stock] Verwenden von Assets mit [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/adobe-stock.html?lang=de)
>* [[!DNL Adobe Stock] Enterprise-Plan](https://helpx.adobe.com/de/enterprise/using/adobe-stock-enterprise.html)
>* [[!DNL Adobe Stock] Häufig gestellte Fragen (FAQ)](https://helpx.adobe.com/de/stock/faq.html)

