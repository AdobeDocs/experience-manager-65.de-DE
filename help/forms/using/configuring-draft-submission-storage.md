---
title: Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen
description: Erfahren Sie, wie Sie die Datenspeicherung für Entwürfe und Übermittlungen konfigurieren
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 51ca2844-91f0-453a-9b39-b876399ebecb
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 100%

---

# Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen {#configuring-storage-services-for-drafts-and-submissions}

## Übersicht {#overview}

Mit AEM Forms können Sie Folgendes speichern:

* **Entwürfe**: Ein Formular, an dem sie gerade arbeiten, das Endbenutzer ausfüllen, zur späteren Verwendung speichern und schließlich übermitteln.

* **Übermittlungen**: Die übermittelten Formulare mit den von den Benutzern angegebenen Daten.

Die AEM Forms Portal-Daten- und -Metadatendienste bieten Unterstützung für Entwürfe und Übermittlungen. Die Daten werden standardmäßig in der Veröffentlichungsinstanz gespeichert, die dann in die konfigurierte Autoreninstanz zurückrepliziert wird, um für andere Veröffentlichungsinstanzen verfügbar zu sein.

Das Problem mit dem bestehenden vorkonfigurierten Ansatz besteht darin, dass alle Daten auf der Veröffentlichungsinstanz gespeichert werden, einschließlich personenbezogener Daten (Personal Identifiable Information, PII).

Zusätzlich zum oben genannten Standardansatz ist auch eine alternative Implementierung verfügbar, um die Formulardaten direkt zur Verarbeitung zu übertragen, anstatt sie lokal zu speichern. Kundinnen und Kunden, die Bedenken hinsichtlich der Speicherung potenziell sensibler Daten auf der Veröffentlichungsinstanz haben, können die alternative Implementierung wählen, bei der die Daten an einen Verarbeitungs-Server gesendet werden. Da die Verarbeitung auf der Autoreninstanz erfolgt, bleibt sie normalerweise in einem sicheren Bereich.

>[!NOTE]
>
>Wenn Sie die Forms Portal Aktion-Übermittlungsaktion verwenden oder die Store-Daten über die Forms-Portal-Optionen im adaptiven Formular aktivieren, werden die Formulardaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. Stattdessen müssen Sie die Entwurfs- und Übermittlungskomponente mit einem sicheren Speicher wie der Unternehmensdatenbank integrieren, um Entwürfe und übermittelte Formulardaten zu speichern.
>
>Weitere Informationen finden Sie im [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](/help/forms/using/integrate-draft-submission-database.md).

## Konfigurieren der Formularportal-Dienste für Entwürfe und Sendungen {#configuring-forms-portal-drafts-and-submissions-services}

Klicken Sie in der AEM-Web-Konsolenkonfiguration (`https://[host]:'port'/system/console/configMgr`), um die **Konfiguration des Formularportals für Entwurf und Übermittlung** im Bearbeitungsmodus zu öffnen.

Geben Sie die Werte für Eigenschaften basierend auf Ihren Anforderungen wie unten beschrieben an:

### Sofort einsatzbereite Dienste zum Speichern von Daten auf der Veröffentlichungsinstanz {#out-of-the-box-services-to-store-data-on-publish-instance}

Die Daten werden in die konfigurierte Autoreninstanz zurückrepliziert.

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Entwurfsdatendienst des Formularportals (Kennung für den Entwurfsdatendienst (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Entwurfsmetadatendienst des Formularportals (Kennung für den Entwurfsmetadatendienst (<strong>draft.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Datenübermittlungsdienst des Formularportals (Kennung für den Datenübermittlungsdienst (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Metadatenübermittlungsdienst des Formularportals (Kennung für den Metadatenübermittlungsdienst (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceImpl<br /> </td>
  </tr>
 </tbody>
</table>

### Sofort einsatzbereite Dienste zum Speichern von Daten auf einer Remote-Verarbeitungsinstanz {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Daten werden direkt an die konfigurierte Remote-Instanz übertragen

<table>
 <tbody>
  <tr>
   <th>Eigenschaft</th>
   <th>Wert</th>
  </tr>
  <tr>
   <td>Entwurfsdatendienst des Formularportals (Kennung für den Entwurfsdatendienst (<strong>draft.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Entwurfsmetadatendienst des Formularportals (Kennung für den Entwurfsmetadatendienst (<strong>draft.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Datenübermittlungsdienst des Formularportals (Kennung für den Datenübermittlungsdienst (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Metadatenübermittlungsdienst des Formularportals (Kennung für den Metadatenübermittlungsdienst (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Geben Sie neben der oben angegebenen Konfiguration auch Informationen zur konfigurierten Remote-Verarbeitungsinstanz an.

Klicken Sie in der AEM-Web-Konsolenkonfiguration (`https://[host]:'port'/system/console/configMgr`), um den **AEM DS-Einstellungen-Service** im Bearbeitungsmodus zu öffnen. Geben Sie im Dialogfeld „AEM DS-Einstellungsdienst“ Informationen zur Verarbeitungs-Server-URL, zum Verarbeitungs-Server-Benutzernamen und zum Kennwort an.

>[!NOTE]
>
>Außerdem wird eine Beispielimplementierung zum Speichern von Benutzerdaten in einer Datenbank bereitgestellt. Um zu verstehen, wie Sie Daten- und Metadaten-Services konfigurieren, um Benutzerdaten in einer externen Datenbank zu speichern, siehe [Beispiel für die Integration der Komponente „Entwürfe und Übermittlungen“ mit der Datenbank](/help/forms/using/integrate-draft-submission-database.md).
