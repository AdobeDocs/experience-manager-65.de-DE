---
title: Best Practices für die Ordnerfreigabe für  [!DNL Adobe Creative Cloud]
description: Konfigurieren Sie [!DNL Adobe Experience Manager] so, dass Benutzende in [!DNL Experience Manager Assets] Ordner mit Benutzenden von Adobe Creative Cloud austauschen können.
contentOwner: AG
role: User, Admin
feature: Collaboration
exl-id: 130cec6d-1cdd-4304-94bb-65e6bb573e55
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: ht
source-wordcount: '928'
ht-degree: 100%

---

# Ordnerfreigabe von [!DNL Adobe Experience Manager] für [!DNL Adobe Creative Cloud] {#aem-to-creative-cloud-folder-sharing-best-practices}

>[!CAUTION]
>
>Die Ordnerfreigabe von [!DNL Experience Manager] für [!DNL Creative Cloud] ist veraltet. Adobe empfiehlt dringend die Verwendung neuerer Funktionen wie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) oder die [Experience Manager-Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=de). Weitere Informationen finden Sie unter [Best Practices für die Integration von Experience Manager und Creative Cloud](/help/assets/aem-cc-integration-best-practices.md).

[!DNL Adobe Experience Manager] kann so konfiguriert werden, dass Benutzende in [!DNL Assets] Ordner für Benutzende von [!DNL Adobe Creative Cloud]-Apps freigeben können, sodass sie als freigegebene Ordner im [!DNL Adobe Creative Cloud]-Asset-Dienst zur Verfügung stehen. Die Funktion kann verwendet werden, um Dateien zwischen Kreativ-Teams und Benutzende von [!DNL Assets] auszutauschen, insbesondere wenn die Kreativprofis keinen Zugriff auf die [!DNL Assets]-Bereitstellung haben (weil sie sich außerhalb des Unternehmensnetzwerks befinden).

Diese Art der Integration kann in folgenden Fällen verwendet werden, insbesondere bei der Zusammenarbeit mit Benutzenden, die keinen direkten Zugriff auf [!DNL Assets] haben:

* Benutzende von [!DNL Assets] geben bestimmte digitale Assets für Benutzende von [!DNL Adobe Creative Cloud]-Dateien frei (z. B. einen Überblick für das Kreativ-Team und genehmigte Assets für das Design einer neuen Marketing-Maßnahme).
* Benutzende von [!DNL Assets] erhalten neue Dateien, die von Benutzenden einer [!DNL Adobe Creative Cloud]-App erstellt wurden.

>[!NOTE]
>
>Vor der Lektüre dieses Dokuments können Sie sich die allgemeinen [Best Practices zur Experience Manager- und Creative Cloud-Integration](/help/assets/aem-cc-integration-best-practices.md) durchlesen, wenn Sie sich zunächst einen Überblick über dieses Integration verschaffen möchten.

## Übersicht {#overview}

Die Ordnerfreigabe von [!DNL Experience Manager] für [!DNL Creative Cloud] stützt sich auf die Server-seitige Freigabe von Ordnern und Dateien zwischen [!DNL Assets]- und [!DNL Creative Cloud]-Konten. Kreativschaffende, die die [!DNL Creative Cloud]-Desktop-App auf ihren Desktops verwenden, können die freigegebenen Ordner mithilfe der neuen [!DNL Adobe CreativeSync]-Technologie direkt auf ihren Datenträgern zur Verfügung stellen.

Das folgende Diagramm bietet einen Überblick über die Integration.

![chlimage_1-179](assets/chlimage_1-406.png)

Die Integration umfasst folgende Elemente:

* **[!DNL Experience Manager Assets]**, bereitgestellt im Unternehmensnetzwerk (Managed Services oder On-Premise): Die Ordnerfreigabe wird hier initiiert.
* **[!DNL Adobe Experience Cloud Assets]-Hauptdienst**: Wirkt als Vermittler zwischen [!DNL Experience Manager] und [!DNL Creative Cloud]-Speicherdiensten. In einer Organisation, die die Integration verwendet, müssen Admins eine Vertrauensbeziehung zwischen der Experience Cloud-Organisation und der [!DNL Assets]-Bereitstellung herstellen. Um für zusätzliche Sicherheit zu sorgen, wird [eine Liste von zugelassenen Creative Cloud-Mitwirkenden definiert](https://experienceleague.adobe.com/docs/core-services/interface/services/assets/t-admin-add-cc-user.html?lang=de), für die Benutzende von [!DNL Assets] Ordner freigeben können.

* **[!DNL Creative Cloud]Assets Web-Services** (Web-Benutzeroberfläche für Speicher und [!DNL Creative Cloud]-Dateien): Hier können bestimmte Benutzende der Creative Cloud-App, für die ein [!DNL Assets]-Ordner freigegeben wurde, eine Einladung annehmen und den Ordner in ihrem Speicherort im Creative Cloud-Konto sehen.
* **Creative Cloud-Desktop-App**: (Optional) Ermöglicht den direkten Zugriff auf freigegebene Ordner/Dateien über den Desktop der Kreativschaffenden per Synchronisierung mit dem [!DNL Creative Cloud] Assets-Speicher.

## Funktionen und Einschränkungen {#characteristics-and-limitations}

* **Einwegübertragung von Änderungen:** Dateiänderungen werden nur in eine Richtung übertragen, d. h. aus dem System ([!DNL Experience Manager] oder [!DNL Creative Cloud Assets]), in dem das Asset ursprünglich erstellt (hochgeladen) wurde. Die Integration bietet keine vollständig automatisierte bidirektionale Synchronisation zwischen den beiden Systemen.
* **Versionierung:**

   * [!DNL Experience Manager] erstellt bei Aktualisierungen nur dann Versionen eines Assets, wenn die Datei von [!DNL Experience Manager] stammt und dort aktualisiert wird.
   * [!DNL Creative Cloud] Assets bietet eine eigene [Versionierungsfunktion](https://helpx.adobe.com/de/creative-cloud/help/versioning-faq.html), die für laufende Aktualisierungen vorgesehen ist (Im Wesentlichen werden Aktualisierungen bis zu zehn Tage gespeichert).

* **Speicherplatzbeschränkungen:** Die Größe und Menge der ausgetauschten Dateien ist für Kreativschaffende (je nach Stufe des Abonnements) durch das [Creative Cloud Assets-Kontingent](https://helpx.adobe.com/de/creative-cloud/kb/file-storage-quota.html) und eine Begrenzung der Dateigröße auf maximal 5 GB beschränkt. Darüber hinaus wird der Speicherplatz durch das Assets-Kontingent beschränkt, das für das Unternehmen im zentralen Adobe Experience Cloud Assets-Dienst festgelegt ist.

* **Erforderlicher Speicherplatz:** Die Dateien in freigegebenen Ordnern müssen auch physisch in [!DNL Experience Manager] und anschließend im [!DNL Creative Cloud]-Konto gespeichert werden. Eine Kopie muss im zentralen [!DNL Experience Cloud Assets]-Dienst zwischengespeichert werden.
* **Netzwerk und Bandbreite:** Die Dateien in freigegebenen Ordnern und alle Aktualisierungen müssen über das Netzwerk zwischen den Systemen transportiert werden. Sie sollten sicherstellen, dass nur relevante Dateien und Aktualisierungen freigegeben werden.
* **Ordnerart**: Die Freigabe eines [!DNL Assets]-Ordners vom Typ `sling:OrderedFolder` wird bei der Freigabe in [!DNL Adobe Experience Cloud] nicht unterstützt. Wenn Sie einen Ordner freigeben möchten, wählen Sie beim Erstellen in [!DNL Assets] nicht die Option [!UICONTROL Geordnet] aus.

## Best Practices {#best-practices}

Zu den Best Practices für die Verwendung der Ordnerfreigabe von [!DNL Experience Manager] für [!DNL Creative Cloud] gehört Folgendes:

* **Überlegungen zum Volumen:** Die Ordnerfreigabe zwischen [!DNL Experience Manager] und [!DNL Creative Cloud] sollte für eine kleinere Anzahl von Dateien verwendet werden, z. B. für eine bestimmte Kampagne oder Aktivität. Greifen Sie für das Freigeben größerer Mengen von Assets, z. B. aller genehmigten Assets in der Organisation, besser auf andere Methoden (z. B. [!DNL Assets Brand Portal]) oder auf das [!DNL Experience Manager]-Desktop-Programm zurück.
* **Vermeiden Sie die Freigabe komplexer Hierarchien:** Die Freigabe erfolgt rekursiv und erlaubt kein selektives Aufheben der Freigabe. Normalerweise sollten nur Ordner ohne Unterordner oder mit einer einfachen Hierarchie, z. B. nur einer Unterordnerebene, für die Freigabe in Erwägung gezogen werden.
* **Separate Ordner für die Einwegfreigabe:** Für das Freigeben von endgültigen Assets aus [!DNL Assets] für [!DNL Creative Cloud]-Dateien und umgekehrt zum Freigeben von Assets für die kreative Bearbeitung aus [!DNL Creative Cloud]-Dateien für [!DNL Assets] sollten separate Ordner verwendet werden. In Verbindung mit einer sinnvollen Benennungskonvention für diese Ordner entsteht eine Arbeitsumgebung, die für Benutzende von [!DNL Assets] und [!DNL Creative Cloud] gleichermaßen verständlich ist.
* **Vermeidung von laufenden Arbeiten in einem freigegebenen Ordner:** Verwenden Sie keine freigegebene Ordner für laufende Arbeiten. Verwenden Sie einen separaten Ordner in Creative Cloud Files, um Arbeiten zu erledigen, die häufige Änderungen an der Datei erfordern.
* **Beginn neuer Arbeit außerhalb eines freigegebenen Ordners:** Es empfiehlt sich, mit der Erstellung neuer Designs (kreativer Dateien) in einem separaten Ordner für laufende Prozesse in Creative Cloud Files zu beginnen. Sobald die Designs für Benutzende von [!DNL Assets] freigegeben werden können, sollten sie in den freigegebenen Ordner verschoben oder in diesem gespeichert werden.
* **Vereinfachung der Freigabestruktur:** Im Sinne einer besser überschaubaren Organisation sollten Sie darüber nachdenken, die Freigabestruktur zu vereinfachen. Anstatt [!DNL Assets]-Ordner für alle kreativen Benutzenden freizugeben, sollten sie nur für Personen freigegeben werden, die das Team repräsentieren, z. B. die Person, die für den Kreativbereich zuständig ist oder das Team leitet. Auf diese Weise kann der Leiter des Kreativbereichs endgültige Assets erhalten, über die Arbeitsaufteilung entscheiden und dann die Designer in ihren eigenen Creative Cloud-Konten an den unfertigen Assets arbeiten lassen. Sie können die Creative Cloud-Zusammenarbeitsfunktionen verwenden, um die Arbeit zu koordinieren, und Assets, die für die Freigabe bereit sind, auswählen und wieder für [!DNL Assets] im Ordner für kreatives Arbeiten freigeben.

Das folgende Diagramm veranschaulicht eine Beispielkonfiguration zum Erstellen von Designs auf der Basis bestehender endgültiger Assets von [!DNL Assets].

![chlimage_1-180](assets/chlimage_1-407.png)
