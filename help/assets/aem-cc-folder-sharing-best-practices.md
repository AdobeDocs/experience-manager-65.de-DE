---
title: Ordnerfreigabe an [!DNL Adobe Creative Cloud] Best Practices
description: Konfigurieren [!DNL Adobe Experience Manager] -Benutzer in [!DNL Experience Manager Assets] , um Ordner mit Adobe Creative Cloud-Benutzern auszutauschen.
contentOwner: AG
role: User, Admin
feature: Collaboration
exl-id: 130cec6d-1cdd-4304-94bb-65e6bb573e55
source-git-commit: a76772b8761e35a828814ffe0ac3b019266ff008
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 18%

---

# [!DNL Adobe Experience Manager] nach [!DNL Adobe Creative Cloud] Ordnerfreigabe {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die [!DNL Experience Manager] nach [!DNL Creative Cloud] Die Funktion zur Ordnerfreigabe wird nicht mehr unterstützt. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) oder [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die Integration von Experience Managern und Creative Clouden](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] kann so konfiguriert werden, dass Benutzer [!DNL Assets] , um Ordner für Benutzer von freizugeben. [!DNL Adobe Creative Cloud] Apps verwenden, sodass sie als freigegebene Ordner im [!DNL Adobe Creative Cloud] Asset-Dienst. Die Funktion kann zum Austausch von Dateien zwischen Kreativ-Teams und [!DNL Assets] -Benutzer, insbesondere dann, wenn die kreativen Benutzer keinen Zugriff auf die [!DNL Assets] Bereitstellung (sie befinden sich nicht im Unternehmensnetzwerk).

Diese Art der Integration kann in den folgenden Anwendungsfällen verwendet werden, insbesondere bei der Arbeit mit Benutzern, die keinen direkten Zugriff auf [!DNL Assets]:

* [!DNL Assets] Benutzer verwenden eine Reihe bestimmter digitaler Assets für Benutzer von [!DNL Adobe Creative Cloud] -Dateien (z. B. eine Kreativbeschreibung und eine Reihe genehmigter Assets für das Design für eine neue Marketing-Aktivität).
* [!DNL Assets] -Benutzer erhalten neue Dateien, die von [!DNL Adobe Creative Cloud] App-Benutzer.

>[!NOTE]
>
>Bevor Sie dieses Dokument lesen, können Sie die [Best Practices für die Integration von Experience Managern und Creative Clouden](/help/assets/aem-cc-integration-best-practices.md) für einen Überblick über die Integration.

## Übersicht {#overview}

[!DNL Experience Manager] nach [!DNL Creative Cloud] Die Ordnerfreigabe beruht auf der serverseitigen Freigabe von Ordnern und Dateien zwischen [!DNL Assets] und [!DNL Creative Cloud] Konten. Kreativprofis, die die [!DNL Creative Cloud] Das -Desktop-Programm kann die freigegebenen Ordner auf den Desktops zusätzlich direkt auf den Festplatten verfügbar machen, indem es [!DNL Adobe CreativeSync] Technologie.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Experience Manager Assets]** im Unternehmensnetzwerk (Managed Services oder On-Premise) bereitgestellt werden: Die Ordnerfreigabe wird hier initiiert.
* **[!DNL Adobe Marketing Cloud Assets]Hauptdienst**: Vermittler zwischen [!DNL Experience Manager] und [!DNL Creative Cloud] Speicherdienste. Ein Administrator einer Organisation, die die Integration verwendet, muss eine Vertrauensbeziehung zwischen der Marketing Cloud-Organisation und der [!DNL Assets] Implementierung. Sie [eine Liste genehmigter Projektmitarbeiter definieren](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html), dass [!DNL Assets] Benutzer können Ordner für zusätzliche Sicherheit freigeben.

* **[!DNL Creative Cloud]Assets-Webdienste** (Lagerung und [!DNL Creative Cloud] Dateien (Web-Benutzeroberfläche): Hier finden Sie bestimmte Creative Cloud-App-Benutzer, für die ein [!DNL Assets] -Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrem Creative Cloud-Kontospeicher anzeigen kann.
* **Creative Cloud-Desktop-Programm**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit [!DNL Creative Cloud] Asset-Speicher.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einwegübertragung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen - vom System ([!DNL Experience Manager] oder [!DNL Creative Cloud Assets]), wo das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.
* **Versionierung:**

   * [!DNL Experience Manager] erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von stammt und dort aktualisiert wird.[!DNL Experience Manager]
   * [!DNL Creative Cloud] Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Platzbeschränkungen:** Größe und Volumen der ausgetauschten Dateien sind durch die spezifischen [Creative Cloud Assets-Kontingent](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) für kreative Benutzer (abhängig von der Abonnementebene) und eine Beschränkung der maximalen Dateigröße von 5 GB. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Raumbedarf:** Die Dateien in freigegebenen Ordnern müssen auch physisch in [!DNL Experience Manager] und dann [!DNL Creative Cloud] -Konto mit einer zwischengespeicherten Kopie in [!DNL Marketing Cloud Assets] Hauptdienst.
* **Netzwerke und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnertyp**: Freigeben einer [!DNL Assets] Ordner des Typs `sling:OrderedFolder`wird im Kontext der Freigabe in nicht unterstützt. [!DNL Adobe Marketing Cloud]. Wenn Sie einen Ordner freigeben möchten, beim Erstellen in [!DNL Assets], wählen Sie nicht die [!UICONTROL Bestellt] -Option.

## Best Practices {#best-practices}

Best Practices für die Nutzung der [!DNL Experience Manager] nach [!DNL Creative Cloud] Die Ordnerfreigabe umfasst:

* **Überlegungen zum Volumen:** [!DNL Experience Manager] und [!DNL Creative Cloud] Die Ordnerfreigabe sollte verwendet werden, um eine kleinere Anzahl von Dateien freizugeben, z. B. für eine bestimmte Kampagne oder Aktivität. Verwenden Sie andere Verteilungsmethoden, um größere Asset-Sets wie alle genehmigten Assets in der Organisation freizugeben (z. B. [!DNL Assets Brand Portal]) oder [!DNL Experience Manager] Desktop-Programm.
* **Vermeiden Sie die Freigabe tiefer Hierarchien:** Die Freigabe erfolgt rekursiv und lässt keine selektive Aufhebung der Freigabe zu. In der Regel sollten nur Ordner ohne Unterordner oder mit einer sehr flachen Hierarchie, z. B. 1 Unterordnerebene, für die Freigabe berücksichtigt werden.
* **Separate Ordner für die unidirektionale Freigabe:** Separate Ordner sollten für die Freigabe von endgültigen Assets aus verwendet werden [!DNL Assets] nach [!DNL Creative Cloud] Dateien und zum Freigeben von kreativen Assets aus [!DNL Creative Cloud] Dateien in [!DNL Assets]. Zusammen mit einer guten Benennungskonvention für diese Ordner wird eine besser verständliche Arbeitsumgebung für [!DNL Assets] und [!DNL Creative Cloud] -Benutzer gleichermaßen.
* **Vermeiden Sie WIP im freigegebenen Ordner:** Freigegebener Ordner sollte nicht für laufende Arbeit verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files , um Arbeiten durchzuführen, die häufige Dateiänderungen erfordern.
* **Starten Sie neue Arbeit außerhalb des freigegebenen Ordners:** Neue Designs (Kreativdateien) sollten im separaten WIP-Ordner in Creative Cloud Files gestartet werden und wenn sie für die Freigabe bereit sind. [!DNL Assets] -Benutzern verwenden, sollten sie in den freigegebenen Ordner verschoben oder gespeichert werden.
* **Vereinfachung der Freigabestruktur:** Für eine besser verwaltbare Funktionsweise sollten Sie über eine Vereinfachung der Freigabestruktur nachdenken. Statt für alle kreativen Benutzer freizugeben, [!DNL Assets] -Ordner sollten nur für Teamvertreter wie Kreativdirektor oder Teammanager freigegeben werden. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können Funktionen zur Zusammenarbeit mit Creative Clouden verwenden, um die Arbeit zu koordinieren und schließlich Assets auszuwählen und zu platzieren, die bereit sind, sie zu teilen. [!DNL Assets] in den Ordner, der für kreative Zwecke genutzt werden kann.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
