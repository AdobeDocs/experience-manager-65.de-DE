---
title: Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen
description: Erfahren Sie, wie Sie Speicher für Entwürfe und Übermittlungen konfigurieren
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 51ca2844-91f0-453a-9b39-b876399ebecb
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 34%

---

# Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen {#configuring-storage-services-for-drafts-and-submissions}

## Übersicht {#overview}

Mit AEM Forms können Sie Folgendes speichern:

* **Entwürfe**: Ein Formular, an dem sie gerade arbeiten, das Endbenutzer ausfüllen, zur späteren Verwendung speichern und schließlich übermitteln.

* **Übermittlungen**: Die übermittelten Formulare mit den von den Benutzern angegebenen Daten.

Die Daten- und Metadatendienste von AEM Forms Portal unterstützen Entwürfe und Übermittlungen. Standardmäßig werden die Daten in der Veröffentlichungsinstanz gespeichert, die dann in die konfigurierte Autoreninstanz zurückrepliziert wird, um für die Perkolation mit anderen Veröffentlichungsinstanzen verfügbar zu sein.

Das Problem mit dem vorhandenen vordefinierten Ansatz besteht darin, dass alle Daten in der Veröffentlichungsinstanz gespeichert werden, einschließlich der Daten, bei denen es sich um personenbezogene Daten (PII) handeln kann.

Zusätzlich zum oben genannten Standardansatz ist auch eine alternative Implementierung verfügbar, mit der die Formulardaten direkt zur Verarbeitung übertragen werden, anstatt sie lokal zu speichern. Kunden, die Bedenken bei der Speicherung potenziell vertraulicher Daten in der Veröffentlichungsinstanz haben, können die alternative Implementierung wählen, in der die Daten an einen Verarbeitungsserver gesendet werden. Da die Verarbeitung in der Autoreninstanz erfolgt, verbleibt sie normalerweise in einer sicheren Zone.

>[!NOTE]
>
>Wenn Sie die Forms Portal Aktion-Übermittlungsaktion verwenden oder die Store-Daten über die Forms-Portal-Optionen im adaptiven Formular aktivieren, werden die Formulardaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. Stattdessen müssen Sie die Entwurfs- und Übermittlungskomponente mit einem sicheren Speicher wie der Unternehmensdatenbank integrieren, um Entwürfe und übermittelte Formulardaten zu speichern.
>
>Weitere Informationen finden Sie im [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

## Konfigurieren von Forms Portal-Diensten für Entwurf und Übermittlung {#configuring-forms-portal-drafts-and-submissions-services}

Klicken Sie in der AEM-Web-Konsolenkonfiguration (`https://[host]:'port'/system/console/configMgr`), um die **Konfiguration des Formularportals für Entwurf und Übermittlung** im Bearbeitungsmodus zu öffnen.

Geben Sie die Werte für die Eigenschaften entsprechend Ihren Anforderungen an, wie unten beschrieben:

### Vorkonfigurierte Dienste zum Speichern von Daten in der Veröffentlichungsinstanz {#out-of-the-box-services-to-store-data-on-publish-instance}

Die Daten werden auf die konfigurierte Autoreninstanz zurückrepliziert.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Forms Portal Draft Data Service (Bezeichner für den Entwurfsdatendienst (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Entwurf (Bezeichner für den Metadatendienst für Entwurf (<strong>draft.metadata.service</strong>))</td>
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

### Vorkonfigurierte Dienste zum Speichern von Daten auf der Remote-Verarbeitungsinstanz {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Daten werden direkt an die konfigurierte Remote-Instanz gesendet

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Forms Portal Draft Data Service (Bezeichner für den Entwurfsdatendienst (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal-Metadatendienst für Entwurf (Bezeichner für den Metadatendienst für Entwurf (<strong>draft.metadata.service</strong>))</td>
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

Geben Sie neben der oben angegebenen Konfiguration Informationen zur konfigurierten Remote-Verarbeitungsinstanz an.

Klicken Sie in der AEM-Web-Konsolenkonfiguration (`https://[host]:'port'/system/console/configMgr`), um den **AEM DS-Einstellungen-Service** im Bearbeitungsmodus zu öffnen. Geben Sie im Dialogfeld AEM DS Settings Service Informationen zu URL des Verarbeitungsservers, Benutzername des Verarbeitungsservers und Kennwort ein.

>[!NOTE]
>
>Außerdem wird eine Beispielimplementierung zum Speichern von Benutzerdaten in einer Datenbank bereitgestellt. Um zu verstehen, wie Sie Daten- und Metadaten-Services konfigurieren, um Benutzerdaten in einer externen Datenbank zu speichern, siehe [Beispiel für die Integration der Komponente „Entwürfe und Übermittlungen“ mit der Datenbank](/help/forms/using/integrate-draft-submission-database.md).
