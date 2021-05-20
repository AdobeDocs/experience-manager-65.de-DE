---
title: Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen
seo-title: Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen
description: Hier wird beschrieben, wie Sie Speicher für Entwürfe und Übermittlungen konfigurieren
seo-description: Hier wird beschrieben, wie Sie Speicher für Entwürfe und Übermittlungen konfigurieren
uuid: 2f4efc07-312c-4908-8c91-84f4e6c5ad25
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6ebb6420-68b6-4abc-b298-c252db038416
exl-id: 51ca2844-91f0-453a-9b39-b876399ebecb
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 89%

---

# Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen {#configuring-storage-services-for-drafts-and-submissions}

## Überblick {#overview}

Mit AEM Forms können Sie speichern:

* **Entwürfe**: Ein Formular, an dem sie gerade arbeiten, das Endbenutzer ausfüllen, zur späteren Verwendung speichern und schließlich übermitteln.

* **Übermittlungen**: Die übermittelten Formulare mit den von den Benutzern angegebenen Daten.

Die AEM Forms Portal-Daten- und -Metadatendienste bieten Unterstützung für Entwürfe und Übermittlungen. Standardmäßig werden die Daten in der Veröffentlichungsinstanz gespeichert, die anschließend in die konfigurierte Autoreninstanz zurückrepliziert wird und damit zur Weiterleitung an andere Veröffentlichungsinstanzen zur Verfügung steht.

Das bestehende vordefinierte Verfahren ist insofern problematisch, als sämtliche Daten dabei in der Veröffentlichungsinstanz gespeichert werden, einschließlich solcher Daten, die eventuell personenbezogene Informationen (PII) sind.

Neben dem oben erwähnten Standardverfahren steht als Alternative eine Implementierung zur Verfügung, bei der die Formulardaten nicht lokal gespeichert, sondern direkt zur Verarbeitung weitergeleitet werden. Kunden, die Bedenken bei der Speicherung potenziell vertraulicher Daten in der Veröffentlichungsinstanz haben, können diese alternative Implementierung wählen, bei der die Daten an einen Verarbeitungsserver gesendet werden. Da die Verarbeitung in der Autoreninstanz erfolgt, läuft sie normalerweise in einer sichereren Zone ab.

>[!NOTE]
>
>Wenn Sie die Forms Portal Aktion-Übermittlungsaktion verwenden oder die Store-Daten über die Forms-Portal-Optionen im adaptiven Formular aktivieren, werden die Formulardaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. Stattdessen müssen Sie die Entwurfs- und Übermittlungskomponente mit einem sicheren Speicher wie der Unternehmensdatenbank integrieren, um Entwürfe und übermittelte Formulardaten zu speichern.
>
>Weitere Informationen finden Sie unter [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

## Konfigurieren von Forms Portal-Diensten für Entwürfe und Übermittlungen  {#configuring-forms-portal-drafts-and-submissions-services}

Klicken Sie in der AEM Web Console Configuration ( `https://[host]:'port'/system/console/configMgr`) auf , um **Forms Portal Draft and Submission Configuration** im Bearbeitungsmodus zu öffnen.

Geben Sie wie unten beschrieben die Werte für die Eigenschaften an wie für Ihre Zwecke benötigt:

### Standardmäßige Dienste zum Speichern der Daten in der Veröffentlichungsinstanz  {#out-of-the-box-services-to-store-data-on-publish-instance}

Daten werden auf die konfigurierte Autoreninstanz zurückrepliziert.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Forms Portal-Datendienst für Entwürfe (Bezeichner für den Datendienst für Entwürfe (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Entwürfe (Bezeichner für den Metadatendienst für Entwürfe (<strong>draft.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Datendienst für Übermittlung (Bezeichner für den Datendienst für Übermittlung (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Übermittlung (Bezeichner für den Metadatendienst für Übermittlung (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceImpl<br /> </td>
  </tr>
 </tbody>
</table>

### Standardmäßige Dienste zum Speichern der Daten in der Fernverarbeitungsinstanz  {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Daten werden direkt an die konfigurierte Ferninstanz weitergeleitet.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Forms Portal-Datendienst für Entwürfe (Bezeichner für den Datendienst für Entwürfe (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Entwürfe (Bezeichner für den Metadatendienst für Entwürfe (<strong>draft.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Datendienst für Übermittlung (Bezeichner für den Datendienst für Übermittlung (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Übermittlung (Bezeichner für den Metadatendienst für Übermittlung (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Geben Sie außer der oben angegebenen Konfiguration Informationen über die konfigurierte Fernverarbeitungsinstanz an.

Klicken Sie in der AEM Web Console Configuration ( `https://[host]:'port'/system/console/configMgr`) auf , um **AEM DS Settings Service** im Bearbeitungsmodus zu öffnen. Geben Sie im Dialogfeld des AEM DS-Einstellungsdienstes Informationen zu URL, Benutzername und Kennwort des Verarbeitungsservers an.

>[!NOTE]
>
>Eine Beispielimplementierung für die Speichern von Benutzerdaten in einer Datenbank wird ebenfalls bereitgestellt. Informationen zum Konfigurieren von Daten- und Metadatendiensten zum Speichern von Benutzerdaten in einer externen Datenbank finden Sie unter [Beispiel für die Integration der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).
