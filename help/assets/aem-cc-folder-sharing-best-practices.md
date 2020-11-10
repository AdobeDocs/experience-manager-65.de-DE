---
title: Best [!DNL Adobe Creative Cloud] Practices für die Ordnerfreigabe
description: Konfigurieren Sie [!DNL Adobe Experience Manager] to allow users in [!DNL Experience Manager Assets] den Ordneraustausch mit Adobe Creative Cloud (CC)-Benutzern.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 12c56c27c7f97f1029c757ec6d28f482516149d0
workflow-type: tm+mt
source-wordcount: '953'
ht-degree: 17%

---


# [!DNL Adobe Experience Manager] zur [!DNL Adobe Creative Cloud] Ordnerfreigabe {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>The [!DNL Experience Manager] to [!DNL Creative Cloud] Folder Sharing feature is deprecated. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html). Learn more in [Experience Manager and Creative Cloud integration best practices](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] können so konfiguriert werden, dass Benutzer in Ordner [!DNL Assets] für die Benutzer von [!DNL Adobe Creative Cloud] Apps freigeben können, sodass sie als freigegebene Ordner im [!DNL Adobe Creative Cloud] Assets-Dienst verfügbar sind. The feature can be used to exchange files between creative teams and [!DNL Assets] users, especially when the creative users do not have access to the [!DNL Assets] deployment (they are not on the enterprise network).

This type of integration can be used in the following use cases, especially when working with users who do not have direct access to [!DNL Assets]:

* [!DNL Assets] Die Benutzer nutzen eine Reihe von bestimmten digitalen Assets für die Benutzer von [!DNL Adobe Creative Cloud] Dateien (z. B. eine Kreativbeschreibung und eine Reihe von genehmigten Assets für die Entwurfsarbeit in einer neuen Marketing-Aktivität).
* [!DNL Assets] Benutzer erhalten neue Dateien, die von [!DNL Adobe Creative Cloud] App-Benutzern erstellt wurden.

>[!NOTE]
>
>Before reading this document, you can review the overall [Experience Manager and Creative Cloud integration best practices](/help/assets/aem-cc-integration-best-practices.md) for an overview of the integration.

## Überblick {#overview}

[!DNL Experience Manager] zum [!DNL Creative Cloud] Freigeben von Ordnern setzt die serverseitige Freigabe von Ordnern und Dateien zwischen [!DNL Assets] und [!DNL Creative Cloud] Konten voraus. Creative professionals, who use the [!DNL Creative Cloud] desktop app on their desktops, can additionally make the shared folders available directly on their disks using [!DNL Adobe CreativeSync] technology.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Experience Manager Assets]** im Unternehmensnetzwerk (verwaltete Dienste oder lokale Dienste) bereitgestellt werden: Die Freigabe von Ordnern wird hier initiiert.
* **[!DNL Adobe Marketing Cloud Assets]Hauptdienst**: fungiert als Vermittler zwischen [!DNL Experience Manager] und [!DNL Creative Cloud] Datenspeicherung. Ein Administrator eines Unternehmens, das die Integration verwendet, muss eine Vertrauensbeziehung zwischen dem Marketing Cloud und der [!DNL Assets] Bereitstellung herstellen. They also [define a list of approved Creative Cloud collaborators](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html), that [!DNL Assets] users can share folders too for additional security.

* **[!DNL Creative Cloud]Assets Web Services** (Web-Benutzeroberfläche für Datenspeicherung und [!DNL Creative Cloud] Dateien): Hier können bestimmte Creative Cloud-App-Benutzer, für die ein [!DNL Assets] Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrer Creative Cloud-Konto-Datenspeicherung anzeigen.
* **Creative Cloud-Desktop-App**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit der [!DNL Creative Cloud] Assets-Datenspeicherung.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einseitige Verbreitung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen - vom System ([!DNL Experience Manager] oder [!DNL Creative Cloud Assets]), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.
* **Versionierung:**

   * [!DNL Experience Manager] erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von stammt und dort aktualisiert wird.[!DNL Experience Manager]
   * [!DNL Creative Cloud] Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Platzbeschränkungen:** Dateigrößen und Dateimengen, die ausgetauscht werden, sind durch das spezifische Asset- [Kontingent](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) für kreative Anwender (je nach Abonnement) und eine Beschränkung der Dateigröße auf 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Raumbedarf:** Die Dateien in freigegebenen Ordnern müssen auch physisch in [!DNL Experience Manager] und dann in [!DNL Creative Cloud] Konto gespeichert werden, mit einer zwischengespeicherten Kopie im [!DNL Marketing Cloud Assets] Hauptdienst.
* **Netzwerk und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnertyp**: Die Freigabe eines [!DNL Assets] Ordners des Typs `sling:OrderedFolder`wird im Zusammenhang mit der Freigabe in nicht unterstützt [!DNL Adobe Marketing Cloud]. If you want to share a folder, when creating it in [!DNL Assets], do not select the [!UICONTROL Ordered] option.

## Best Practices {#best-practices}

Best practices for leveraging the [!DNL Experience Manager] to [!DNL Creative Cloud] folder sharing include:

* **Volumenaspekte:** [!DNL Experience Manager] und [!DNL Creative Cloud] &quot;Freigeben von Ordnern&quot;verwendet werden, um beispielsweise eine kleinere Anzahl von Dateien freizugeben, die für eine bestimmte Kampagne oder Aktivität relevant sind. To share larger sets of assets, like all approved assets in the organization, use other distribution methods (for example, [!DNL Assets Brand Portal]) or [!DNL Experience Manager] desktop app.
* **Vermeiden Sie die Freigabe von tiefen Hierarchien:** Die Freigabe funktioniert rekursiv und lässt keine selektive Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr flachen Hierarchie, wie z. B. 1 Unterordnerebene, für die Freigabe in Betracht gezogen werden.
* **Separate Ordner für die einmalige Freigabe:** Separate Ordner sollten verwendet werden, um endgültige Assets von [!DNL Assets] in [!DNL Creative Cloud] Dateien freizugeben und um kreative Assets wieder von [!DNL Creative Cloud] Dateien in freizugeben [!DNL Assets]. Together with a good naming convention for these folders, it creates an easier-to-understand working environment for [!DNL Assets] and [!DNL Creative Cloud] users alike.
* **WIP im freigegebenen Ordner vermeiden:** Freigegebener Ordner sollte nicht für Work in Progress verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files, um Arbeiten durchzuführen, die häufige Dateiänderungen erfordern.
* **Beginn neuer Arbeiten außerhalb des freigegebenen Ordners:** Neue Entwürfe (Kreativdateien) sollten im separaten WIP-Ordner in &quot;Creative Cloud Files&quot;gestartet werden. Sobald sie für die Freigabe durch [!DNL Assets] Benutzer bereit sind, sollten sie verschoben oder in den freigegebenen Ordner gespeichert werden.
* **Vereinfachen der Freigabestruktur:** Für ein besser handhabbares Betriebssystem sollten Sie sich überlegen, die Freigabestruktur zu vereinfachen. Instead of sharing with all creative users, [!DNL Assets] folders should be shared with team representative(s) only, like a creative director or team manager. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. They can use Creative Cloud collaboration features to coordinate the work, and finally select and put assets that are ready to share back to [!DNL Assets] into their creative-ready shared folder.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
