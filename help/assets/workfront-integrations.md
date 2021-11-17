---
title: '[!DNL Experience Manager Assets] integration with [!DNL Adobe Workfront]'
description: Einführung in die Integration zwischen [!DNL Assets] und [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
source-git-commit: c742e89a56c383e6dde8a6aee5bc3d124d73343d
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 4%

---


# [!DNL Adobe Experience Manager Assets] Integration mit [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] ist ein Programm für das Arbeits-Management, mit dem Sie den gesamten Arbeitszyklus an einem Ort verwalten können. Die Integration zwischen [!DNL Workfront] und [!DNL Adobe Experience Manager Assets] ermöglicht es Unternehmen, die Geschwindigkeit von Inhalten und die Time-to-Market zu verbessern, indem sie Arbeit und Digital Asset Management intern miteinander verbinden. Im Rahmen der Verwaltung ihrer Arbeit in Workfront haben Benutzer Zugriff auf die erforderlichen Dokumente und Bilder.

Die [!DNL Workfront for Experience Manager enhanced connector] ermöglicht erweiterte Geschäftsprozesse mit durchgängigen Workflows und bietet personalisierte End-to-End-Kundenerlebnisse und zentralen Speicher. Adobe bietet einen Standard-Connector und einen erweiterten Connector zur Integration der beiden Lösungen. Nachfolgend finden Sie einen Vergleich der unterstützten Funktionen. Weitere Informationen finden Sie unter [Neue Funktionen in der [!DNL enhanced connector]](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

[!DNL Workfront for Experience Manage enhanced connector] ermöglicht Ihrem Unternehmen Folgendes:

* Erstellen Sie automatisch verknüpfte Ordner in Workfront und organisieren Sie die Experience Manager anhand von Workfront-Portfolios, -Programmen und -Projekten.
* Synchronisieren Sie Workfront-Projektmetadaten mit verknüpften Experience Manager-Ordnern.
* Experience Manager-Metadaten werden mit neuen Versionen aktualisiert.
* Legen Sie mithilfe von Experience Manager-Workflows den Workfront-Objektstatus anhand konfigurierbarer Bedingungen fest.
* Veröffentlichen Sie Assets in der Experience Manager-Veröffentlichungsumgebung oder in Brand Portal.

Siehe Plattformunterstützung und [Voraussetzungen für den erweiterten Connector](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe erfordert Bereitstellung und Konfiguration der [!DNL Adobe Workfront for Experience Manager enhanced connector] nur über zertifizierte Partner oder [!DNL Adobe Professional Services]. Wird ohne zertifizierten Partner bereitgestellt und konfiguriert oder [!DNL Adobe Professional Services], wird sie von Adobe nicht unterstützt.
>
>Adobe veröffentlicht möglicherweise Aktualisierungen für [!DNL Adobe Workfront] und [!DNL Adobe Experience Manager] die diesen Connector redundant machen; In diesem Fall kann es erforderlich sein, dass Kunden von der Verwendung dieses Connectors übergehen.

## Vergleichen verschiedener Integrationen zwischen [!DNL Assets] und [!DNL Workfront] {#feature-parity-matrix}

Im Folgenden finden Sie Details zu den Funktionen, die durch verschiedene Integrationstypen zwischen [!DNL Assets] und [!DNL Workfront].

| Funktion | Beschreibung | [!DNL Workfront] und [!DNL Assets Essentials] | [!DNL Workfront] für [!DNL Experience Manager] Connector | [!DNL Workfront for Experience Manager enhanced connector] |
|----|----|----|------|-----|
| Bereitstellungsmethoden | Für welche [!DNL Assets] anbieten. | Assets Essentials | Cloud Service, Adobe Managed Services, On-Premise | Cloud Service, Adobe Managed Services, On-Premise |
| Senden digitaler Dateien aus [!DNL Workfront] nach [!DNL Assets] | Die neueste Version eines WF-Dokuments kann in AEM Assets hochgeladen werden, das als neue Version des Dokuments verknüpft wird. | ✓ | verwalten | verwalten |
| Manuelles Verknüpfen AEM Ordnern mit Workfront-Objekten | Vorhandene AEM können als Workfront-Ordner verknüpft werden und die untergeordneten Assets werden als neue Workfront-Dokumente verknüpft. | verwalten | verwalten | verwalten |
| Link [!DNL Assets] zu Workfront-Objekten | Vorhandene Assets in AEM können mit einem neuen Workfront-Dokument oder einer neuen Version eines vorhandenen Dokuments verknüpft werden. | verwalten | verwalten | verwalten |
| Assets, die verknüpften Ordnern hinzugefügt wurden, werden automatisch an AEM gesendet | Wenn ein Dokument zu einem verknüpften Ordner hinzugefügt wird, wird das verknüpfte Asset automatisch als neues Asset in AEM Assets hochgeladen. | verwalten | verwalten | verwalten |
| Verknüpfte AEM Assets aus Workfront herunterladen | Wenn ein Asset in Workfront verknüpft ist, kann der Benutzer die Bytes des Assets herunterladen. | verwalten | verwalten | verwalten |
| Suchen nach AEM Assets in Workfront | Der AEM Assets-Selektor in Workfront ermöglicht die Volltextsuche nach Assets. | verwalten | verwalten | verwalten |
| Anzeigen und Navigieren AEM Ordnerhierarchie in Workfront | Der AEM Assets-Selektor in Workfront ermöglicht das Durchsuchen der AEM Assets-Hierarchie, die durch die zugehörigen Zugriffssteuerungen und Berechtigungen des Benutzers in AEM eingeschränkt ist. | verwalten | verwalten | verwalten |
| Aufheben der Verknüpfung von Assets mit AEM Assets in Workfront | Ein vorhandenes verknüpftes Asset aus AEM kann vom zugehörigen Workfront-Dokument getrennt werden. Dadurch wird das ursprüngliche Asset in AEM nicht gelöscht. | verwalten | verwalten | verwalten |
| Hinzufügen von neu versionierten Assets zu AEM Assets aus Workfront | Wenn eine neu hinzugefügte Version zu einem Dokument in Workfront hinzugefügt wird, kann ein Benutzer die neue Version an AEM senden, um die vorhandene Version zu ersetzen. | verwalten | verwalten | verwalten |
| In Workfront verknüpfte Assets, wenn auf &quot;Direkter Benutzer zu AEM&quot;geklickt wurde | Benutzer werden zu AEM weitergeleitet, um eine Vorschau eines verknüpften Assets aus Workfront anzuzeigen. | verwalten | verwalten | Benutzerdefiniert |
| Automatisch verknüpfte AEM Ordner in Workfront erstellen | Erstellen Sie automatisch verknüpfte AEM in Workfront mithilfe des Objektstatus. Organisieren Sie AEM Ordner automatisch auf der Basis von Workfront-Portfolios, -Programmen und -Projekten. | Nein | Nein | verwalten |
| Kommentarsynchronisierung | Automatische Synchronisierung von Kommentaren für Assets aus [!DNL Workfront] nach [!DNL Assets] | Nein | verwalten | verwalten |
| Zuordnen von Workfront Asset-Metadaten zu AEM Assets | Workfront-Objekt und benutzerdefinierte Formulareigenschaften können AEM Asset-Metadateneigenschaften zugeordnet werden. Die Werte werden beim ersten Hochladen/Link gesendet. | verwalten | verwalten | verwalten |
| Benutzerdefinierte Forms für Dokumente automatisch in Workfront erstellen | Fügen Sie benutzerdefinierte Formulare mithilfe AEM Workflows an Workfront-Dokumente, Aufgaben und Probleme an. | Nein | Fügen Sie das benutzerdefinierte Formular manuell hinzu, dann funktioniert die automatisierte Synchronisierung | verwalten |
| Bidirektionale automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront | Automatische Aktualisierung von Metadaten zwischen AEM Assets und Workfront. | Nein | verwalten | verwalten |
| Zuordnen von Workfront-Metadaten zu AEM Assets-Ordnern | Synchronisieren Sie Workfront-Projektmetadaten mit verknüpften AEM. | Nein | Nein | verwalten |
| AEM von Metadaten mit neuen Versionen | Es kann eine Konfiguration in AEM vorgenommen werden, um zu bestimmen, ob ein neu versioniertes Asset in Workfront auch mit allen an den Metadaten vorgenommenen Änderungen gepusht wird. | Nein | Nein | verwalten |
| Automatische Aktualisierung AEM Metadaten bei Änderungen an benutzerdefiniertem Forms in Workfront | Workfront ist so konfiguriert, dass die angegebenen AEM Asset-Metadateneigenschaften einem benutzerdefinierten Formular für Dokumente zugeordnet werden. Wenn ein Asset anfänglich verknüpft wird oder ein Asset aktualisiert wird, werden die Werte dieser Metadateneigenschaften in das entsprechende benutzerdefinierte Formularfeld für das Workfront-Dokument kopiert. Es muss darauf geachtet werden, dass die Änderung nicht an AEM zurückgesendet AEM, als wäre dies eine Änderung, die von Workfront ausgeht. | Nein | verwalten | verwalten |
| Erstellen einer neuen Testversion für verknüpfte Assets | Beim Verknüpfen eines Assets in Workfront kann automatisch ein Testversand generiert werden. | Nein | verwalten | Benutzerdefiniert |
| Status auf Workfront-Objekte festlegen | Festlegen des Workfront-Objektstatus anhand konfigurierbarer Bedingungen mithilfe von AEM-Workflows | Nein | Nein | verwalten |
| Veröffentlichen von Assets in der AEM-Veröffentlichungsumgebung oder in Brand Portal | Weisen Sie Workfront-Benutzern die Möglichkeit zu, verknüpfte Assets automatisch in einer AEM-Veröffentlichungsumgebung oder in Brand Portal zu veröffentlichen. | Nein | Nein | verwalten |
