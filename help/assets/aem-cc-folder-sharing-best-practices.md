---
title: Best Practices für die Ordnerfreigabe aus AEM in Creative Cloud
description: Konfigurieren Sie Adobe Experience Manager (AEM) so, dass Benutzer in AEM Assets Ordner mit Adobe Creative Cloud (CC)-Benutzern austauschen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 70a88085a0fd6e949974aa7f1f92fdc3def3d98e

---


# Best Practices für die Ordnerfreigabe aus AEM in Creative Cloud {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Ordnerfreigabe von AEM in Creative Cloud wird nicht mehr unterstützt. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) oder [AEM Desktop-App](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html). Learn more in [AEM and Creative Cloud integration best practices](/help/assets/aem-cc-integration-best-practices.md).

Adobe Experience Manager (AEM) kann so konfiguriert werden, dass Benutzer in AEM Assets Ordner für die Benutzer von Adobe Creative Cloud-Apps freigeben können, sodass sie als freigegebene Ordner im Adobe Creative Cloud Assets-Dienst verfügbar sind. Diese Funktion kann verwendet werden, um Dateien zwischen Kreativteams und AEM Assets-Benutzern auszutauschen, insbesondere wenn die kreativen Benutzer keinen Zugriff auf die AEM Assets-Instanz (d. h. keinen Zugriff auf das Unternehmensnetzwerk) haben.

Diese Art der Integration kann in beiden Fällen verwendet werden, insbesondere bei der Zusammenarbeit mit Benutzern, die keinen direkten Zugriff auf AEM Assets haben:

* Benutzer von AEM Assets geben Benutzern von Adobe Creative Cloud-Dateien bestimmte Assets aus AEM Assets frei (z. B. einen Überblick für das Kreativteam und genehmigte Assets für das Design einer neuen Marketingaktivität).
* AEM Assets-Benutzer erhalten neue Dateien, die von Benutzern der Adobe Creative Cloud-Applikationen erstellt werden.

>[!NOTE]
>
>Vor der Lektüre dieses Dokuments können Sie sich die allgemeinen [Best Practices zur AEM- und Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md) durchlesen, wenn Sie sich zunächst einen Überblick über dieses Thema verschaffen möchten.

## Überblick {#overview}

Die Freigabe von AEM in Creative Cloud-Ordnern beruht auf der serverseitigen Freigabe von Ordnern und Dateien zwischen AEM Assets und Creative Cloud-Konten. Kreativschaffende, die die Creative Cloud-Desktop-Applikation auf ihren Desktops verwenden, können die freigegebenen Ordner mithilfe der neuen CreativeSync-Technologie von Adobe direkt auf ihren Datenträgern zur Verfügung stellen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **AEM Assets-Server** im Unternehmensnetzwerk bereitgestellt (verwaltete Dienste oder lokal): Die Freigabe von Ordnern wird hier initiiert.
* **Zentraler Assets-Dienst in Adobe Marketing Cloud**: Vermittelnder Dienst zwischen AEM und Creative Cloud-Speicherdiensten. Die Verwaltung des Unternehmens, das die Integration nutzt, muss auf einem Vertrauensverhältnis zwischen dem Marketing Cloud-Unternehmen und der AEM Assets-Instanz basieren. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://marketing.adobe.com/resources/help/en_US/mcloud/t_admin_add_cc_user.html), mit denen AEM Assets-Benutzer freigegebene Ordner gemeinsam nutzen können.

* **Creative Cloud Assets-Webdienste** (Web-Benutzeroberfläche für Speicher- und Creative Cloud-Dateien): Hier können bestimmte Benutzer von Creative Cloud-Apps, für die ein AEM Assets-Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrem Creative Cloud-Kontospeicher anzeigen.
* **Creative Cloud-Desktop-App**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit dem Speicher der Creative Cloud-Elemente.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **** Einseitige Verbreitung von Änderungen: Dateiänderungen werden nur in eine Richtung übertragen - vom System (AEM oder Creative Cloud Assets), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.
* **Versionierung:**

   * AEM erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von AEM stammt und dort aktualisiert wird.
   * Creative Cloud Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **** Platzbeschränkungen: Die Größe und Menge der ausgetauschten Dateien wird durch das spezifische [Creative Cloud-Asset-Kontingent](https://helpx.adobe.com/creative-cloud/kb/file-storage-quota.html) für kreative Benutzer (abhängig von der Abonnementebene) und eine Beschränkung der maximalen Dateigröße von 5 GB begrenzt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **** Raumbedarf: Die Dateien in freigegebenen Ordnern müssen auch physisch in AEM und dann im Creative Cloud-Konto gespeichert werden, wobei eine zwischengespeicherte Kopie im Hauptdienst Marketing Cloud Assets gespeichert werden muss.
* **** Netzwerk und Bandbreite: Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnerart**: Die Freigabe eines Asset-Ordners vom Typ `sling:OrderedFolder` wird bei der Freigabe in Adobe Marketing Cloud nicht unterstützt. Wenn Sie einen Ordner bei seiner Erstellung in AEM Assets freigeben möchten, wählen Sie nicht die Option „Geordnet“ aus.

## Best Practices {#best-practices}

Best Practices für die Verwendung der Ordnerfreigabe von AEM in Creative Cloud:

* **** Volumenaspekte: Die Freigabe von AEM/Creative Cloud-Ordnern sollte verwendet werden, um kleinere Dateien freizugeben, z. B. für eine bestimmte Kampagne oder Aktivität. Greifen Sie für das Freigeben größerer Mengen von Assets, z. B. aller genehmigten Assets in der Organisation, besser auf andere Methoden zurück (z. B. AEM Assets Brand Portal) oder die AEM Desktop App.

* **** Vermeiden Sie die Freigabe von tiefen Hierarchien: Die Freigabe funktioniert rekursiv und lässt keine selektive Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr flachen Hierarchie, wie z. B. 1 Unterordnerebene, für die Freigabe in Betracht gezogen werden.
* **** Separate Ordner für die einmalige Freigabe: Für die Freigabe von endgültigen Assets aus AEM Assets in Creative Cloud-Dateien und für die Freigabe von kreativen Assets aus Creative Cloud-Dateien in AEM Assets sollten separate Ordner verwendet werden. Zusammen mit einer guten Benennungskonvention für diese Ordner wird eine verständlichere Arbeitsumgebung für AEM Assets- und Creative Cloud-Benutzer erstellt.
* **** WIP im freigegebenen Ordner vermeiden: Freigegebener Ordner sollte nicht für Work in Progress verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud-Dateien, um Aufgaben auszuführen, die häufige Dateiänderungen erfordern.
* **** Neue Arbeit außerhalb des freigegebenen Ordners starten: Neue Entwürfe (kreative Dateien) sollten im separaten WIP-Ordner in Creative Cloud-Dateien gestartet werden. Sobald sie für die Freigabe mit AEM Assets-Benutzern bereit sind, sollten sie in den freigegebenen Ordner verschoben oder gespeichert werden.
* **** Vereinfachen der Freigabestruktur: Für ein besser handhabbares Betriebssystem sollten Sie sich überlegen, die Freigabestruktur zu vereinfachen. Statt für alle Kreativbenutzer freizugeben, sollten AEM Assets-Ordner nur für Teamvertreter freigegeben werden, z. B. für einen Kreativdirektor oder Teammanager. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können die Arbeit mit den Funktionen der Creative Cloud-Zusammenarbeit koordinieren und schließlich Assets auswählen und in ihren kreativen freigegebenen Ordner einfügen, die für die Freigabe an AEM Assets bereit sind.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von AEM Assets.

![chlimage_1-180](assets/chlimage_1-407.png)
