---
title: Best Practices für die Ordnerfreigabe für  [!DNL Adobe Creative Cloud]
description: Konfigurieren Sie [!DNL Adobe Experience Manager] so, dass Benutzende in [!DNL Experience Manager Assets] Ordner mit Benutzenden von Adobe Creative Cloud austauschen können.
contentOwner: AG
role: User, Admin
feature: Collaboration
exl-id: 130cec6d-1cdd-4304-94bb-65e6bb573e55
source-git-commit: 260f71acd330167572d817fdf145a018b09cbc65
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 64%

---

# Ordnerfreigabe von [!DNL Adobe Experience Manager] für [!DNL Adobe Creative Cloud] {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Ordnerfreigabe von [!DNL Experience Manager] für [!DNL Creative Cloud] ist veraltet. Adobe empfiehlt die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder [Experience Manager-Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die Integration von Experience Manager und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] kann so konfiguriert werden, dass Benutzende in [!DNL Assets] Ordner für Benutzende von [!DNL Adobe Creative Cloud]-Apps freigeben können, sodass sie als freigegebene Ordner im [!DNL Adobe Creative Cloud]-Asset-Dienst zur Verfügung stehen. Die Funktion kann verwendet werden, um Dateien zwischen Kreativ-Teams und Benutzende von [!DNL Assets] auszutauschen, insbesondere wenn die Kreativprofis keinen Zugriff auf die [!DNL Assets]-Bereitstellung haben (weil sie sich außerhalb des Unternehmensnetzwerks befinden).

Diese Art der Integration kann in folgenden Fällen verwendet werden, insbesondere bei der Zusammenarbeit mit Benutzenden, die keinen direkten Zugriff auf [!DNL Assets] haben:

* Benutzende von [!DNL Assets] geben bestimmte digitale Assets für Benutzende von [!DNL Adobe Creative Cloud]-Dateien frei (z. B. einen Überblick für das Kreativ-Team und genehmigte Assets für das Design einer neuen Marketing-Maßnahme).
* Benutzende von [!DNL Assets] erhalten neue Dateien, die von Benutzenden einer [!DNL Adobe Creative Cloud]-App erstellt wurden.

>[!NOTE]
>
>Vor der Lektüre dieses Dokuments können Sie sich die allgemeinen [Best Practices zur Experience Manager- und Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md) durchlesen, wenn Sie sich zunächst einen Überblick über dieses Integration verschaffen möchten.

## Übersicht {#overview}

Die Ordnerfreigabe von [!DNL Experience Manager] für [!DNL Creative Cloud] stützt sich auf die Server-seitige Freigabe von Ordnern und Dateien zwischen [!DNL Assets]- und [!DNL Creative Cloud]-Konten. Kreativprofis, die die [!DNL Creative Cloud] Das -Desktop-Programm kann die freigegebenen Ordner auch direkt auf den Datenträgern mithilfe von [!DNL Adobe CreativeSync] Technologie.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Experience Manager Assets]** im Unternehmensnetzwerk (Managed Services oder On-Premise) bereitgestellt werden: Die Ordnerfreigabe wird hier initiiert.
* **[!DNL Adobe Experience Cloud Assets]-Hauptdienst**: Vermittler zwischen [!DNL Experience Manager]- und [!DNL Creative Cloud]-Speicherdiensten. Ein Administrator einer Organisation, die die Integration verwendet, muss eine Vertrauensbeziehung zwischen der Experience Cloud-Organisation und der [!DNL Assets] Implementierung. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://experienceleague.adobe.com/docs/core-services/interface/services/assets/t-admin-add-cc-user.html), für die Benutzende von [!DNL Assets] Ordner freigeben können.

* **[!DNL Creative Cloud]Assets Web-Services** (Web-Benutzeroberfläche für Speicher und [!DNL Creative Cloud]-Dateien): Hier können bestimmte Benutzende der Creative Cloud-App, für die ein [!DNL Assets]-Ordner freigegeben wurde, eine Einladung annehmen und den Ordner in ihrem Speicherort im Creative Cloud-Konto sehen.
* **Creative Cloud-Desktop-Programm**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien vom Desktop des kreativen Benutzers über die Synchronisierung mit [!DNL Creative Cloud] Asset-Speicher.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einwegübertragung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen, d. h. aus dem System ([!DNL Experience Manager] oder [!DNL Creative Cloud Assets]), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollständig automatisierte bidirektionale Synchronisation zwischen den beiden Systemen.
* **Versionierung:**

   * [!DNL Experience Manager] erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von [!DNL Experience Manager] stammt und dort aktualisiert wird.
   * [!DNL Creative Cloud] Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html) , die auf laufende Aktualisierungen ausgerichtet ist (im Wesentlichen Aktualisierungen für bis zu zehn Tage speichert)

* **Platzbeschränkungen:** Größe und Volumen der ausgetauschten Dateien sind durch die spezifischen [Creative Cloud Assets-Kontingent](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) für kreative Benutzer (abhängig von der Abonnementebene) und eine Beschränkung der maximalen Dateigröße von 5 GB. Der Speicherplatz wird auch durch das Asset-Kontingent begrenzt, das das Unternehmen in Adobe Experience Cloud Assets Core Service hat.

* **Raumbedarf:** Die Dateien in freigegebenen Ordnern müssen auch physisch in [!DNL Experience Manager] und dann [!DNL Creative Cloud] -Konto mit einer zwischengespeicherten Kopie in [!DNL Experience Cloud Assets] Hauptdienst.
* **Netzwerke und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Updates müssen über das Netzwerk zwischen den Systemen übertragen werden. Stellen Sie sicher, dass nur relevante Dateien und Updates freigegeben sind.
* **Ordnerart**: Die Freigabe eines [!DNL Assets]-Ordners vom Typ `sling:OrderedFolder` wird bei der Freigabe in [!DNL Adobe Experience Cloud] nicht unterstützt. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen in [!DNL Assets] nicht die Option [!UICONTROL Geordnet] aus.

## Best Practices {#best-practices}

Best Practices für die Verwendung der [!DNL Experience Manager] nach [!DNL Creative Cloud] Die Ordnerfreigabe umfasst:

* **Überlegungen zum Volumen:** Die Ordnerfreigabe zwischen [!DNL Experience Manager] und [!DNL Creative Cloud] sollte für eine kleinere Anzahl von Dateien verwendet werden, z. B. für eine bestimmte Kampagne oder Aktivität. Greifen Sie für das Freigeben größerer Mengen von Assets, z. B. aller genehmigten Assets in der Organisation, besser auf andere Methoden (z. B. [!DNL Assets Brand Portal]) oder auf das [!DNL Experience Manager]-Desktop-Programm zurück.
* **Vermeiden Sie die Freigabe tiefer Hierarchien:** Die Freigabe erfolgt rekursiv und lässt keine selektive Aufhebung der Freigabe zu. In der Regel sollten nur Ordner ohne Unterordner oder mit einer flachen Hierarchie (wie eine Unterordnerebene) für die Freigabe berücksichtigt werden.
* **Separate Ordner für die Einwegfreigabe:** Für das Freigeben von endgültigen Assets aus [!DNL Assets] für [!DNL Creative Cloud]-Dateien und umgekehrt zum Freigeben von Assets für die kreative Bearbeitung aus [!DNL Creative Cloud]-Dateien für [!DNL Assets] sollten separate Ordner verwendet werden. In Verbindung mit einer sinnvollen Benennungskonvention für diese Ordner entsteht eine Arbeitsumgebung, die für Benutzende von [!DNL Assets] und [!DNL Creative Cloud] gleichermaßen verständlich ist.
* **Vermeidung von laufenden Arbeiten in einem freigegebenen Ordner:** Freigegebene Ordner sollten nicht für laufende Arbeiten verwendet werden. Verwenden Sie einen separaten Ordner in Creative Cloud Files, um Arbeiten zu erledigen, die häufige Änderungen an der Datei erfordern.
* **Beginn neuer Arbeit außerhalb eines freigegebenen Ordners:** Es empfiehlt sich, mit der Erstellung neuer Designs (kreativer Dateien) in einem separaten Ordner für laufende Prozesse in Creative Cloud Files zu beginnen. Sobald die Designs für Benutzende von [!DNL Assets] freigegeben werden können, sollten sie in den freigegebenen Ordner verschoben oder in diesem gespeichert werden.
* **Vereinfachung der Freigabestruktur:** Überlegen Sie sich für eine besser verwaltbare Funktionsweise, die Freigabestruktur zu vereinfachen. Statt für alle kreativen Benutzer freizugeben, [!DNL Assets] -Ordner sollten nur für Teamvertreter wie Kreativdirektor oder Teammanager freigegeben werden. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können die Creative Cloud-Zusammenarbeitsfunktionen verwenden, um die Arbeit zu koordinieren, und Assets, die für die Freigabe bereit sind, auswählen und wieder für [!DNL Assets] im Ordner für kreatives Arbeiten freigeben.

Das folgende Diagramm zeigt eine Beispielkonfiguration zum Erstellen von Designs, die auf vorhandenen endgültigen Assets aus [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
