---
title: 'Best Practices für die Freigabe von Ordnern auf [!DNL Adobe Creative Cloud] '
description: Konfigurieren Sie [!DNL Adobe Experience Manager] to allow users in [!DNL Experience Manager Assets] zum Austausch von Ordnern mit Adobe Creative Cloud (CC)-Benutzern.
contentOwner: AG
role: Business Practitioner, Administrator
feature: Collaboration
translation-type: tm+mt
source-git-commit: 174e0703ae541641e3dc602e700bcd31624ae62c
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 18%

---


# [!DNL Adobe Experience Manager] zur  [!DNL Adobe Creative Cloud] Ordnerfreigabe  {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Funktion [!DNL Experience Manager] bis [!DNL Creative Cloud] &quot;Ordnerfreigabe&quot;wird nicht mehr unterstützt. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/adobe-asset-link.ug.html) oder [Experience Manager Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die Integration von Experience Managern und Creative Clouden](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] können so konfiguriert werden, dass Benutzer Ordner  [!DNL Assets] für die Benutzer von  [!DNL Adobe Creative Cloud] Apps freigeben können, sodass sie als freigegebene Ordner im  [!DNL Adobe Creative Cloud] Assets-Dienst verfügbar sind. Die Funktion kann zum Austausch von Dateien zwischen Kreativteams und [!DNL Assets]-Benutzern verwendet werden, insbesondere dann, wenn die Kreativbenutzer keinen Zugriff auf die [!DNL Assets]-Bereitstellung haben (sie befinden sich nicht im Unternehmensnetzwerk).

Diese Art der Integration kann in den folgenden Anwendungsfällen verwendet werden, besonders bei der Arbeit mit Benutzern, die keinen direkten Zugriff auf [!DNL Assets] haben:

* [!DNL Assets] Benutzer verwenden eine Reihe spezifischer digitaler Assets für  [!DNL Adobe Creative Cloud] Dateibenutzer (z. B. eine Kreativbeschreibung und eine Reihe genehmigter Assets für die Entwurfsarbeit in einer neuen Marketing-Aktivität).
* [!DNL Assets] Benutzer erhalten neue Dateien, die von  [!DNL Adobe Creative Cloud] App-Benutzern erstellt wurden.

>[!NOTE]
>
>Bevor Sie dieses Dokument lesen, können Sie die Best Practices für die Experience Manager- und Creative Cloud-Integration von [ überprüfen, um einen Überblick über die Integration zu erhalten.](/help/assets/aem-cc-integration-best-practices.md)

## Überblick {#overview}

[!DNL Experience Manager] zum  [!DNL Creative Cloud] Freigeben von Ordnern setzt die serverseitige Freigabe von Ordnern und Dateien zwischen  [!DNL Assets] und  [!DNL Creative Cloud] Konten voraus. Kreativprofis, die die [!DNL Creative Cloud]-Desktop-App auf ihren Desktops verwenden, können die freigegebenen Ordner zusätzlich mithilfe der [!DNL Adobe CreativeSync]-Technologie direkt auf ihren Datenträgern verfügbar machen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Experience Manager Assets]** im Unternehmensnetzwerk (verwaltete Dienste oder lokale Dienste) bereitgestellt werden: Die Freigabe von Ordnern wird hier initiiert.
* **[!DNL Adobe Marketing Cloud Assets]Hauptdienst**: fungiert als Vermittler zwischen  [!DNL Experience Manager] und  [!DNL Creative Cloud] Datenspeicherung. Ein Administrator eines Unternehmens, das die Integration verwendet, muss eine Vertrauensbeziehung zwischen dem Marketing Cloud und der [!DNL Assets]-Bereitstellung herstellen. Außerdem definieren sie [eine Liste von freigegebenen Creative Cloud-Mitarbeitern](https://experienceleague.adobe.com/docs/core-services/interface/assets/t-admin-add-cc-user.html), die [!DNL Assets]-Benutzer zur zusätzlichen Sicherheit freigeben können.

* **[!DNL Creative Cloud]Assets Web Services**  (Web-Benutzeroberfläche für Datenspeicherung und  [!DNL Creative Cloud] Dateien): Hier können bestimmte Creative Cloud-App-Benutzer, für die ein  [!DNL Assets] Ordner freigegeben wurde, die Einladung annehmen und den Ordner in ihrer Creative Cloud-Konto-Datenspeicherung anzeigen.
* **Creative Cloud-Desktop-App**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit der  [!DNL Creative Cloud] Assets-Datenspeicherung.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einfache Übertragung von Änderungen:** Dateiänderungen werden nur in eine Richtung weitergeleitet - vom System ([!DNL Experience Manager] oder  [!DNL Creative Cloud Assets]), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollautomatische Zweiwegsynchronisierung zwischen beiden Systemen.
* **Versionierung:**

   * [!DNL Experience Manager] erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von stammt und dort aktualisiert wird.[!DNL Experience Manager]
   * [!DNL Creative Cloud] Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Aktualisierungen werden bis zu zehn Tage gespeichert).

* **Platzbeschränkungen:** Dateigrößen und Dateigrößen, die ausgetauscht werden, sind durch die für Kreativbenutzer  [angegebene Anzahl von ](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) Creative Cloud-Assets (je nach Abonnement) und eine Beschränkung der Dateigröße auf 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, die das Unternehmen im zentralen Assets-Dienst von Adobe Marketing Cloud festgelegt hat.

* **Platzanforderungen:** Die Dateien in freigegebenen Ordnern müssen auch physisch in  [!DNL Experience Manager] und dann in  [!DNL Creative Cloud] Konto mit einer zwischengespeicherten Kopie im  [!DNL Marketing Cloud Assets] Hauptdienst gespeichert werden.
* **Vernetzung und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnertyp**: Die Freigabe eines  [!DNL Assets] Ordners des Typs  `sling:OrderedFolder`wird im Zusammenhang mit der Freigabe in nicht unterstützt  [!DNL Adobe Marketing Cloud]. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen in [!DNL Assets] nicht die Option [!UICONTROL Bestellt].

## Best Practices {#best-practices}

Zu den bewährten Verfahren für die Nutzung des Ordners [!DNL Experience Manager] in [!DNL Creative Cloud] gehören:

* **Volumenaspekte:** [!DNL Experience Manager] und  [!DNL Creative Cloud] Ordnerfreigabe sollten verwendet werden, um eine kleinere Anzahl von Dateien freizugeben, z. B. die für eine bestimmte Kampagne oder Aktivität relevant sind. Verwenden Sie andere Verteilungsmethoden (z. B. [!DNL Assets Brand Portal]) oder [!DNL Experience Manager]-Desktop-App, um wie alle genehmigten Assets in der Organisation größere Assets freizugeben.
* **Vermeiden Sie die Freigabe von tiefen Hierarchien:** Die Freigabe funktioniert rekursiv und lässt keine selektive Freigabe zu. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer sehr flachen Hierarchie, wie z. B. 1 Unterordnerebene, für die Freigabe in Betracht gezogen werden.
* **Separate Ordner für die einmalige Freigabe:** Separate Ordner sollten verwendet werden, um endgültige Assets von  [!DNL Assets] in  [!DNL Creative Cloud] Dateien freizugeben und um kreative Assets wieder von  [!DNL Creative Cloud] Dateien in freizugeben  [!DNL Assets]. Zusammen mit einer guten Benennungsregel für diese Ordner wird eine verständlichere Umgebung für [!DNL Assets]- und [!DNL Creative Cloud]-Benutzer erstellt.
* **Vermeiden Sie WIP im freigegebenen Ordner:** Freigegebener Ordner sollte nicht für Work in Progress verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files, um Aufgaben auszuführen, die häufige Dateiänderungen erfordern.
* **Neue Beginn-Arbeit außerhalb des freigegebenen Ordners:** Neue Entwürfe (Kreativdateien) sollten im separaten WIP-Ordner unter &quot;Creative Cloud-Dateien&quot;gestartet werden. Sobald sie für die Freigabe an  [!DNL Assets] Benutzer freigegeben werden können, sollten sie verschoben oder in den freigegebenen Ordner gespeichert werden.
* **Vereinfachen Sie die Freigabestruktur:** Für ein besser zu handhabendes Betriebssystem sollten Sie die Freigabestruktur vereinfachen. Statt für alle kreativen Benutzer freizugeben, sollten [!DNL Assets]-Ordner nur für Teamvertreter freigegeben werden, z. B. für einen Kreativdirektor oder Teammanager. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können die Arbeit mithilfe von Funktionen für die Zusammenarbeit mit Creative Clouden koordinieren und schließlich Assets auswählen und in ihren kreativen freigegebenen Ordner verschieben, die bereit sind, sie an [!DNL Assets] weiterzugeben.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen neuer Designs auf der Basis bestehender endgültiger Assets von [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
