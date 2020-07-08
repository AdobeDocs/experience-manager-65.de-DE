---
title: Best Practices für die Freigabe von Adobe Experience Managern in Adobe Creative Cloud
description: Konfigurieren Sie Adobe Experience Manager so, dass Benutzer in Experience Manager Assets Ordner mit Benutzern von Adobe Creative Cloud (CC) austauschen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 678e91699523c22a7048bd7b344fa539b849ae8b
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 29%

---


# Freigeben von Adobe Experience Managern für Adobe Creative Cloud-Ordner {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Der Experience Manager zur Funktion zur Freigabe von Ordnern in Creative Cloud ist veraltet. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager Desktop-App](https://helpx.adobe.com/de/experience-manager/desktop-app/aem-desktop-app.html). Learn more in [Experience Manager and Creative Cloud integration best practices](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager kann so konfiguriert werden, dass Benutzer in Assets Ordner für die Benutzer von Adobe Creative Cloud-Apps freigeben können, sodass sie als freigegebene Ordner im Adobe Creative Cloud Assets-Dienst verfügbar sind. Mit dieser Funktion können Dateien zwischen Kreativteams und Assets-Benutzern ausgetauscht werden, insbesondere dann, wenn die Kreativbenutzer keinen Zugriff auf die Assets-Bereitstellung haben (sie befinden sich nicht im Unternehmensnetzwerk).

Diese Art der Integration kann in beiden Fällen verwendet werden, insbesondere bei der Zusammenarbeit mit Benutzern, die keinen direkten Zugriff auf  Assets haben:

* Benutzer von Assets geben Benutzern von Adobe Creative Cloud-Dateien bestimmte Assets aus AEM Assets frei (z. B. einen Überblick für das Kreativteam und genehmigte Assets für das Design einer neuen Marketingaktivität).
* Assets-Benutzer erhalten neue Dateien, die von Benutzern der Adobe Creative Cloud-Applikationen erstellt werden.

>[!NOTE]
>
>Before reading this document, you can review the overall [Experience Manager and Creative Cloud integration best practices](/help/assets/aem-cc-integration-best-practices.md) for a higher-level overview of the topic.

## Übersicht {#overview}

Die Freigabe von Experience Managern für Creative Cloud-Ordner erfolgt über die serverseitige Freigabe von Ordnern und Dateien zwischen Assets und Creative Cloud-Konten. Kreativschaffende, die die Creative Cloud-Desktop-Applikation auf ihren Desktops verwenden, können die freigegebenen Ordner mithilfe der neuen CreativeSync-Technologie von Adobe direkt auf ihren Datenträgern zur Verfügung stellen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **Experience Manager Assets-Server** , der im Unternehmensnetzwerk bereitgestellt wird (verwaltete Dienste oder lokale Dienste): Die Freigabe von Ordnern wird hier initiiert.
* **Hauptdienst**&quot;Adobe Marketing Cloud Assets&quot;: fungiert als Vermittler zwischen Experience Manager- und Creative Cloud-Datenspeicherung-Diensten. Der Administrator der Firma, die die Integration verwendet, muss eine Vertrauensbeziehung zwischen der Marketing Cloud-Organisation und der Assets-Bereitstellung herstellen. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://docs.adobe.com/content/help/en/core-services/interface/assets/t-admin-add-cc-user.html), mit denen  Assets-Benutzer freigegebene Ordner gemeinsam nutzen können.

* **Creative Cloud Assets-Webdienste** (Web-Benutzeroberfläche &quot;Datenspeicherung&quot;und &quot;Creative Cloud-Dateien&quot;): Hier können bestimmte Creative Cloud-App-Benutzer, für die ein Asset-Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrer Creative Cloud-Konto-Datenspeicherung anzeigen.
* **Creative Cloud-Desktop-App**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit der Creative Cloud Assets-Datenspeicherung.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einseitige Verbreitung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen - vom System (Experience Manager oder Creative Cloud Assets), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.
* **Versionierung:**

   * Experience Manager erstellt Versionen eines Assets nur bei Updates, wenn die Datei aus Experience Manager stammt und dort aktualisiert wird.
   * Creative Cloud Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Platzbeschränkungen:** Dateigrößen und Dateimengen, die ausgetauscht werden, sind durch das spezifische [Creative Cloud-Asset-Kontingent](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) für kreative Benutzer (je nach Abonnement) und eine Beschränkung der Dateigröße auf 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Raumbedarf:** Die Dateien in freigegebenen Ordnern müssen auch physisch in Experience Manager und dann im Creative Cloud-Konto mit einer zwischengespeicherten Kopie im Hauptdienst Marketing Cloud Assets gespeichert werden.
* **Netzwerk und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnerart**: Die Freigabe eines Asset-Ordners vom Typ `sling:OrderedFolder` wird bei der Freigabe in Adobe Marketing Cloud nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in Assets freigeben möchten, wählen Sie nicht die Option „Geordnet“ aus.

## Best Practices {#best-practices}

Die bewährten Verfahren zur Nutzung des Experience Managers für die Freigabe von Creative Cloud-Ordnern sind unter anderem:

* **Volumenaspekte:** Experience Manager/Creative Cloud-Ordnerfreigabe sollte verwendet werden, um eine kleinere Anzahl von Dateien freizugeben, z. B. für eine bestimmte Kampagne oder Aktivität. Verwenden Sie andere Verteilungsmethoden (z. B. Asset Brand Portal) oder die Desktop-App Experience Manager, um größere Assets freizugeben, wie alle genehmigten Assets im Unternehmen.

* **Vermeiden Sie die Freigabe von tiefen Hierarchien:** Die Freigabe funktioniert rekursiv und lässt keine selektive Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr flachen Hierarchie, wie z. B. 1 Unterordnerebene, für die Freigabe in Betracht gezogen werden.
* **Separate Ordner für die einmalige Freigabe:** Für die Freigabe von endgültigen Assets aus Assets in Creative Cloud-Dateien und für die Freigabe von kreativen Assets aus Creative Cloud-Dateien in Assets sollten separate Ordner verwendet werden. Zusammen mit einer guten Benennungsregel für diese Ordner wird eine verständlichere Umgebung für Assets und Creative Cloud-Benutzer erstellt.
* **WIP im freigegebenen Ordner vermeiden:** Freigegebener Ordner sollte nicht für Work in Progress verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud-Dateien, um Aufgaben auszuführen, die häufige Änderungen an der Datei erfordern.
* **Beginn neuer Arbeiten außerhalb des freigegebenen Ordners:** Neue Entwürfe (kreative Dateien) sollten im separaten WIP-Ordner in Creative Cloud-Dateien gestartet werden. Sobald sie für die Freigabe mit Assets-Benutzern bereit sind, sollten sie in den freigegebenen Ordner verschoben oder gespeichert werden.
* **Vereinfachen der Freigabestruktur:** Für ein besser handhabbares Betriebssystem sollten Sie sich überlegen, die Freigabestruktur zu vereinfachen. Statt für alle kreativen Benutzer freizugeben, sollten Assets-Ordner nur für Teamvertreter freigegeben werden, z. B. für einen Kreativdirektor oder Teammanager. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können die Arbeit mit den Funktionen der Creative Cloud-Zusammenarbeit koordinieren und schließlich Assets, die für die Freigabe bereit sind, in ihren kreativen freigegebenen Ordner zurücklegen.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von  Assets.

![chlimage_1-180](assets/chlimage_1-407.png)
