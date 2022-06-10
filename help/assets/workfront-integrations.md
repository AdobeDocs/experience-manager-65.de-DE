---
title: „Integration von [!DNL Experience Manager Assets] mit  [!DNL Adobe Workfront]“
description: Einführung in die Integration zwischen [!DNL Assets] und [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
exl-id: 57e2bffe-8094-4557-99c8-7b482681687e
source-git-commit: 57304cfb7706377fa5dd7cce0e5863839ffee553
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 95%

---

# Integration von [!DNL Adobe Experience Manager Assets] mit [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] ist ein Programm für das Arbeits-Management, mit dem Sie den gesamten Arbeitszyklus an einem Ort verwalten können. Die Integration von [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] ermöglicht es Unternehmen, die Geschwindigkeit von Inhalten und die Zeit bis zur Markteinführung zu verbessern, indem sie Workfront und Digital Asset Management miteinander verbinden. Im Rahmen der Verwaltung ihrer Arbeit in Workfront haben Benutzer Zugriff auf die erforderlichen Dokumente und Bilder.

Der [!DNL Workfront for Experience Manager enhanced connector] ermöglicht erweiterte Geschäftsprozesse mit durchgängigen Workflows und bietet durchgängige, personalisierte Kundenerlebnisse und zentralen Speicher. Adobe bietet einen Standard-Connector und einen erweiterten Connector zur Integration der beiden Lösungen. Nachfolgend finden Sie einen Vergleich der unterstützten Funktionen. Weitere Informationen finden Sie unter [Neue Funktionen in der [!DNL enhanced connector]](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

[!DNL Workfront for Experience Manage enhanced connector] ermöglicht Ihrer Organisation Folgendes:

* Erstellen von automatisch verknüpften Experience Manager-Ordnern in Workfront und organisieren dieser Ordner anhand von Workfront-Portfolios, -Programmen und -Projekten.
* Synchronisieren der Workfront-Projektmetadaten mit den verknüpften Experience Manager-Ordnern.
* Aktualisierung der Experience Manager-Metadaten mit neuen Versionen.
* Setzen des Status von Workfront-Objekten auf der Grundlage konfigurierbarer Bedingungen mit Experience Manager-Workflows.
* Veröffentlichen von Assets in der Veröffentlichungsumgebung von Experience Manager oder in Brand Portal.

Siehe Plattformunterstützung und [Voraussetzungen für den erweiterten Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe erfordert die Implementierung und Konfiguration des [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird diese ohne zertifizierten Partner oder [!DNL Adobe Professional Services] bereitgestellt oder konfiguriert, wird sie von Adobe nicht unterstützt.
>
>* Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager], die diesen Connector redundant machen. In diesem Fall kann es erforderlich sein, dass Kunden diesen Connector nicht mehr verwenden.
>
>* Adobe unterstützt erweiterte Connector-Versionen 1.7.4 und höher. Frühere Vorabversionen und benutzerdefinierte Versionen werden nicht unterstützt. Navigieren Sie zur erweiterten Connector-Version, um sie zu überprüfen. `digital.hoodoo` im linken Bereich in [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de).
>
>* Siehe [Partnerzertifizierungsprüfung für den erweiterten Connector von Workfront for Experience Manager Assets](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Informationen zur Prüfung finden Sie unter [Prüfungsleitfaden](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


## Vergleichen verschiedener Integrationen zwischen [!DNL Assets] und [!DNL Workfront] {#feature-parity-matrix}

Im Folgenden finden Sie Details zu den Funktionen, die durch verschiedene Integrationstypen zwischen [!DNL Assets] und [!DNL Workfront] verfügbar sind.

| Funktion | Beschreibung | [!DNL Workfront] und [!DNL Assets Essentials] | [!DNL Workfront] für [!DNL Experience Manager]-Connector | [!DNL Workfront for Experience Manager enhanced connector] |
|----|----|----|------|-----|
| Implementierungsmethoden | Passend für welches [!DNL Assets]-Angebot. | Assets Essentials | Cloud Service, Adobe Managed Services, On-Premise | Cloud Service, Adobe Managed Services, On-Premise |
| Senden digitaler Dateien von [!DNL Workfront] zu [!DNL Assets] | Die neueste Version eines WF-Dokuments kann in AEM Assets hochgeladen werden, wo sie als neue Version des Dokuments verknüpft wird. | ✓ | ✓ | ✓ |
| Manuelles Verknüpfen von AEM-Ordnern mit Workfront-Objekten | Vorhandene AEM-Ordner können als Workfront-Ordner verknüpft werden, wobei die untergeordneten Assets als neue Workfront-Dokumente verknüpft werden. | ✓ | ✓ | ✓ |
| Verknüpfen von [!DNL Assets] mit Workfront-Objekten | Vorhandene Assets in AEM können mit einem neuen Workfront-Dokument oder einer neuen Version eines vorhandenen Dokuments verknüpft werden. | ✓ | ✓ | ✓ |
| Assets, die verknüpften Ordnern hinzugefügt wurden, werden automatisch an AEM gesendet | Wenn ein Dokument zu einem verknüpften Ordner hinzugefügt wird, wird das verknüpfte Asset automatisch als neues Asset in AEM Assets hochgeladen. | ✓ | ✓ | ✓ |
| Herunterladen von verknüpften AEM Assets aus Workfront | Wenn ein Asset in Workfront verknüpft ist, kann der Benutzer die Bytes des Assets herunterladen. | ✓ | ✓ | ✓ |
| Suchen nach AEM Assets in Workfront | Der AEM Assets-Selektor in Workfront ermöglicht die Volltextsuche nach Assets. | ✓ | ✓ | ✓ |
| Anzeigen von und Navigieren in der AEM-Ordnerhierarchie in Workfront | Der AEM Assets-Selektor in Workfront ermöglicht das Durchsuchen der AEM Assets-Hierarchie im Rahmen der in AEM festgelegten Zugriffssteuerungen und -berechtigungen des Benutzers. | ✓ | ✓ | ✓ |
| Aufheben der Verknüpfung von Assets mit AEM Assets in Workfront | Ein vorhandenes verknüpftes Asset aus AEM kann vom zugehörigen Workfront-Dokument getrennt werden. Dadurch wird das ursprüngliche Asset in AEM nicht gelöscht. | ✓ | ✓ | ✓ |
| Hinzufügen von neu versionierten Assets zu AEM Assets aus Workfront | Wenn eine neu hinzugefügte Version zu einem Dokument in Workfront hinzugefügt wird, kann ein Benutzer die neue Version an AEM senden, um die vorhandene Version zu ersetzen. | ✓ | ✓ | ✓ |
| In Workfront verknüpfte Assets, wenn auf „Benutzer zu AEM leiten“ geklickt wurde | Benutzer werden zu AEM weitergeleitet, um eine Vorschau eines verknüpften Assets aus Workfront anzuzeigen. | ✓ | ✓ | Benutzerdefiniert |
| Automatisches Erstellen von verknüpften AEM-Ordnern in Workfront | Sie können automatisch verknüpfte AEM-Ordner in Workfront erstellen, indem Sie Objektstatus verwenden. Organisieren Sie AEM-Ordner automatisch auf der Basis von Workfront-Portfolios, -Programmen und -Projekten. | Nein | Nein | ✓ |
| Synchronisierung von Kommentaren | Automatische Synchronisierung von Kommentaren für Assets aus [!DNL Workfront] nach [!DNL Assets] | Nein | ✓ | ✓ |
| Zuordnen von Workfront Asset-Metadaten zu AEM Assets | Eigenschaften von Workfront-Objekten und benutzerdefinierten Formularen können mit Metadateneigenschaften von AEM-Assets verknüpft werden. Die Werte werden beim ersten Hochladen/Verknüpfen übertragen. | ✓ | ✓ | ✓ |
| Automatisches Erstellen von benutzerdefinierten Dokumentenformularen in Workfront | Hängen Sie mithilfe von AEM-Workflows benutzerdefinierte Formulare an Workfront-Dokumente, Aufgaben und Probleme an. | Nein | Wenn Sie das benutzerdefinierte Formular manuell hinzufügen, dann funktioniert die automatisierte Synchronisierung | ✓ |
| Bidirektionale automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront | Automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront. | Nein | ✓ | ✓ |
| Zuordnen von Workfront-Metadaten zu AEM Assets-Ordnern | Synchronisieren Sie Metadaten von Workfront-Projekten mit verknüpften AEM-Ordnern. | Nein | Nein | ✓ |
| Aktualisierungen der AEM-Metadaten mit neuen Versionen | Es kann eine Konfiguration in AEM vorgenommen werden, um zu bestimmen, ob ein neu versioniertes Asset in Workfront auch mit allen an den Metadaten vorgenommenen Änderungen gepusht wird. | Nein | Nein | ✓ |
| Automatische Aktualisierung von AEM Metadaten bei Änderungen an benutzerdefinierten Formularen in Workfront | Workfront ist so konfiguriert, dass die angegebenen Metadateneigenschaften von AEM Assets einem benutzerdefinierten Formular für Dokumente zugeordnet werden. Wenn ein Asset erstmals verknüpft wird oder ein Asset aktualisiert wird, werden die Werte dieser Metadateneigenschaften in das entsprechende benutzerdefinierte Formularfeld für das Workfront-Dokument kopiert. Es muss darauf geachtet werden, dass die Änderung nicht von AEM an AEM zurückgesendet wird, als wäre dies eine Änderung, die von Workfront ausgeht. | Nein | ✓ | ✓ |
| Erstellen einer neuen Testversion für verknüpfte Assets | Beim Verknüpfen eines Assets in Workfront kann automatisch ein Testversand generiert werden. | Nein | ✓ | Benutzerdefiniert |
| Festlegen des Status von Workfront-Objekten | Festlegen des Status von Workfront-Objekten anhand konfigurierbarer Bedingungen mithilfe von AEM-Workflows | Nein | Nein | ✓ |
| Veröffentlichen von Assets in der AEM-Veröffentlichungsumgebung oder in Brand Portal | Sie können Workfront-Benutzern die Möglichkeit geben, verknüpfte Assets automatisch in einer AEM-Veröffentlichungsumgebung oder in Brand Portal zu veröffentlichen. | Nein | Nein | ✓ |
