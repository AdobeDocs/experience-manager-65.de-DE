---
title: Dokumentensicherheit | Umgang mit Benutzerdaten
description: Mit AEM Forms Document Security können Sie Benutzerdaten und Datenspeicher verwalten sowie Benutzerdaten aufrufen, löschen und exportieren.
uuid: 1624a465-8b0c-4347-a53f-1118bfa6e18f
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 898268cb-4426-421f-8f63-d75bd85cb57f
role: Admin
exl-id: 00c01a12-1180-4f35-9179-461bf177c787
source-git-commit: 0e5b89617d481c69882ec5d4658e76855aa9b691
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 63%

---

# Dokumentensicherheit | Umgang mit Benutzerdaten {#document-security-handling-user-data}

Mit AEM Forms Document Security können Sie vordefinierte Sicherheitseinstellungen erstellen, speichern und auf Ihre Dokumente anwenden. Dadurch wird sichergestellt, dass nur autorisierte Benutzer die Dokumente verwenden können. Sie können Dokumente mithilfe von Richtlinien schützen. Eine Richtlinie ist eine Sammlung von Informationen, die Sicherheitseinstellungen und eine Liste autorisierter Benutzer enthalten. Sie können eine Richtlinie auf ein oder mehrere Dokumente anwenden und Benutzer autorisieren, die in der AEM Forms JEE-Benutzerverwaltung hinzugefügt werden.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Document Security speichert Richtlinien und Daten zu geschützten Dokumenten, einschließlich Benutzerdaten, in einer Datenbank wie My Sql, Oracle, MS SQL Server und IBM DB2. Darüber hinaus werden die Daten für autorisierte Benutzer in einer Richtlinie in der Benutzerverwaltung gespeichert. Informationen zu den in der Benutzerverwaltung gespeicherten Daten finden Sie unter [Benutzerverwaltung für Formulare: Umgang mit Benutzerdaten](/help/forms/using/user-management-handling-user-data.md).

Die folgende Tabelle zeigt, wie Document Security Daten in Datenbanktabellen organisiert.

<table>
 <tbody>
  <tr>
   <td>Datenbanktabelle</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalKeyEntity</code></td>
   <td>Speichert Informationen über Hauptschlüssel für die Benutzer. Die Schlüssel werden in Offline-Document Security-Workflows verwendet.</td>
  </tr>
  <tr>
   <td><code>EdcAuditEntity</code></td>
   <td>Speichert Informationen über Auditing-Ereignisse wie Benutzer-, Dokumenten- und Richtlinienereignisse.</td>
  </tr>
  <tr>
   <td><p><code>EdcLicenseEntity</code></p> </td>
   <td>Speichert den Datensatz eines geschützten Dokuments. Es speichert Lizenzdetails für jedes geschützte Dokument.</td>
  </tr>
  <tr>
   <td><p><code>EdcDocumentEntity</code></p> </td>
   <td>Speichert den Dokumentnamen für jede im System erstellte Lizenz.</td>
  </tr>
  <tr>
   <td><p><code>EdcRevokationEntity</code></p> </td>
   <td>Speichert Informationen zum Widerruf und zur Wiederherstellung geschützter Dokumente.</td>
  </tr>
  <tr>
   <td><code>EdcMyPolicyListEntity</code></td>
   <td>Speichert Informationen zu Benutzern, die persönliche Richtlinien erstellen können, die auf der Seite „Richtlinien“ auf der Registerkarte „Meine Richtlinien“ angezeigt werden. </td>
  </tr>
  <tr>
   <td><code>EdcPolicyEntity</code></td>
   <td>Speichert Informationen zu Richtlinien. Jede Richtlinie entspricht einer Zeile in dieser Tabelle.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyXmlEntity</code></td>
   <td>Speichert XML-Dateien für aktive Richtlinien. Ein Richtlinien-XML<sup> </sup>enthält Verweise auf die Haupt-IDs der mit der Richtlinie verbundenen Benutzer. Richtlinien-XML wird als Blob-Objekt gespeichert.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyArchiveEntity</code></td>
   <td>Speichert Informationen zu archivierten Richtlinien. Eine archivierte Richtlinie enthält ihre Richtlinien-XML, die als Blob-Objekt gespeichert ist.</td>
  </tr>
  <tr>
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code><br /> (Oracle- und MS SQL-Datenbanken)</p> </td>
   <td>Speichert die Zuordnung zwischen Richtliniensatz und Benutzern.</td>
  </tr>
  <tr>
   <td><code>EdcInvitedUserEntity</code></td>
   <td>Speichert Informationen zu eingeladenen Benutzern.</td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können Document Security-Daten für Benutzer in den Datenbanken aufrufen und exportieren und bei Bedarf dauerhaft löschen.

Um Benutzerdaten aus einer Datenbank zu exportieren oder zu löschen, müssen Sie mithilfe eines Datenbank-Clients eine Verbindung zur Datenbank herstellen und die Prinzipal-ID anhand einiger persönlich identifizierbarer Informationen des Benutzers ermitteln. Um beispielsweise die Haupt-ID eines Benutzers mit einer Anmelde-ID abzurufen, führen Sie den folgenden Befehl `select` in der Datenbank aus.

Ersetzen Sie im Befehl `select` die `<user_login_id>` durch die Anmelde-ID des Benutzers, dessen Haupt-ID Sie aus der Datenbanktabelle `EdcPrincipalUserEntity` abrufen möchten.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Sobald Sie die Prinzipal-ID kennen, können Sie die Benutzerdaten exportieren oder löschen.

### Benutzerdaten exportieren {#export-user-data}

Führen Sie die folgenden Datenbankbefehle aus, um Benutzerdaten für eine Prinzipal-ID aus Datenbanktabellen zu exportieren. Ersetzen Sie `<principal_id>` im Befehl `select` durch die Haupt-ID des Benutzers, dessen Daten Sie exportieren möchten.

>[!NOTE]
>
>Die folgenden Befehle verwenden Datenbanktabellennamen in My SQL- und IBM DB2-Datenbanken. Wenn Sie diese Befehle auf Oracle- und MS SQL-Datenbanken ausführen, ersetzen Sie `EdcPolicySetPrincipalEntity` durch `EdcPolicySetPrincipalEnt` in den Befehlen.

```sql
Select * from EdcPrincipalKeyEntity where principalid = '<principal_id>';

Select * from EdcLicenseEntity where publisherId = '<principal_id>';

Select * from EdcDocumentEntity where id in (Select documentid from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcRevokationEntity where licenseid in (Select id from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcMyPolicyListEntity where principalId = '<principal_id>';

Select * from edcpolicyentity where policyownerId = '<principal_id>';

Select * from edcpolicyxmlentity where policyidref in (Select id from edcpolicyentity where policyownerId = '<principal_id>');

Select * from edcpolicyarchiveentity where policyownerId = '<principal_id>';

Select * from edcpolicysetprincipalentity where principalId = '<principal_id>';

Select * from edcinviteduserentity where principalId = '<principal_id>';
```

>[!NOTE]
>
>Um Daten aus der Tabelle `EdcAuditEntity` zu exportieren, verwenden Sie die API [EventManager.exportEvents](https://helpx.adobe.com/de/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html), die [EventSearchFilter](https://helpx.adobe.com/de/experience-manager/6-5/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als Parameter benötigt, um Audit-Daten auf der Grundlage von `principalId`, `policyId` oder `licenseId` zu exportieren.

Um vollständige Daten über einen Benutzer im System zu erhalten, müssen Sie auf Daten aus der Benutzerverwaltungsdatenbank zugreifen und diese exportieren. Weitere Informationen finden Sie unter [Benutzerverwaltung für Formulare: Umgang mit Benutzerdaten](/help/forms/using/user-management-handling-user-data.md).

### Benutzerdaten löschen {#delete-user-data}

Führen Sie die folgenden Schritte aus, um Document Security-Daten für eine Prinzipal-ID aus Datenbanktabellen zu löschen.

1. Fahren Sie den AEM Forms-Server herunter.
1. Gehen Sie wie folgt vor, um die Dokumentensicherheitsdaten für eine Haupt-ID aus den Datenbanktabellen zu löschen. Ersetzen Sie im Befehl `Delete` den Wert `<principal_id>` durch die Haupt-ID des Benutzers, dessen Daten Sie löschen möchten.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Um Daten aus der Tabelle `EdcAuditEntity` zu löschen, verwenden Sie die API [EventManager.deleteEvents](https://helpx.adobe.com/de/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html), die [EventSearchFilter](https://helpx.adobe.com/de/experience-manager/6-5/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) als Parameter benötigt, um Audit-Daten auf der Grundlage von `principalId`, `policyId` oder `licenseId` zu löschen.

1. Aktive und archivierte Richtlinien-XML-Dateien werden in den Datenbanktabellen `EdcPolicyXmlEntity` bzw. `EdcPolicyArchiveEntity` gespeichert. Führen Sie die folgenden Schritte aus, um Daten für einen Benutzer aus diesen Tabellen zu löschen:

   1. Öffnen Sie den XML-Blob jeder Zeile in der Tabelle `EdcPolicyXMLEntity` oder `EdcPolicyArchiveEntity` und extrahieren Sie die XML-Datei. Die XML-Datei ähnelt der unten gezeigten.
   1. Bearbeiten Sie die XML-Datei, um den Blob für die Prinzipal-ID zu entfernen.
   1. Wiederholen Sie die Schritte 1 und 2 für die andere Datei.

   >[!NOTE]
   >
   >Sie müssen den kompletten Blob innerhalb des `Principal`-Tags für eine Prinzipal-ID entfernen, da sonst die XML-Richtlinie beschädigt oder unbrauchbar werden kann.

   ```xml
   <ns2:Principal PrincipalNameType="USER">
       <ns2:PrincipalDomain>OID</ns2:PrincipalDomain>
       <ns2:PrincipalName>56F33FEB-098A-1036-A651-00000A2A2656</ns2:PrincipalName>
   </ns2:Principal>
   </ns2:PolicyEntry>
       <ns2:Property PropertyName="isCertified">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">false</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="encryptionAlgorithm">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">AES128</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="AccessDeniedErrorMessage">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string"></ns2:PropertyValue>
       </ns2:Property>
   <ns2:PolicyEntry>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.onlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.copy" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.offlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.accessible" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.editNotes" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.edit" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.fillAndSign" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printHigh" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printLow" Access="ALLOW"/>
   ```

   Neben dem Löschen von Daten direkt aus der Tabelle `EdcPolicyXmlEntity` gibt es zwei weitere Möglichkeiten, um dies zu erreichen:

   **Verwenden der Verwaltungskonsole** 

   1. Melden Sie sich als Administrator an der Forms-JEE-Verwaltungskonsole unter https://[*Server*]:[*Port*]/adminui an.
   1. Navigieren Sie zu **[!UICONTROL Dienste > Dokumentensicherheit > Richtliniensätze]**.
   1. Öffnen Sie einen Richtliniensatz und löschen Sie den Benutzer aus der Richtlinie.

   **Verwenden der Document Security-Webseite**

   Document Security-Benutzer mit Berechtigungen zum Erstellen persönlicher Richtlinien können Benutzerdaten aus ihren Richtlinien löschen. Gehen Sie dazu wie folgt vor:

   1. Benutzer, die über persönliche Richtlinien verfügen, melden sich auf ihrer Dokumentensicherheits-Webseite unter https://[*Server*]:[*Port*]/edc an.
   1. Navigieren Sie zu **[!UICONTROL Dienste > Dokumentensicherheit > Meine Richtlinien]**.
   1. Öffnen Sie eine Richtliniengruppe und löschen Sie den Benutzer aus der Richtlinie.

   >[!NOTE]
   >
   >Administratoren können über die Verwaltungskonsole in **[!UICONTROL Dienste > Dokumentensicherheit > Meine Richtlinien]** Benutzerdaten aus persönlichen Richtlinien anderer Benutzer suchen, darauf zugreifen und sie löschen.

1. Löschen Sie die Daten für die Prinzipal-ID aus der Benutzerverwaltungsdatenbank. Detaillierte Schritte finden Sie unter [Benutzerverwaltung für Formulare | Umgang mit Benutzerdaten](/help/forms/using/user-management-handling-user-data.md).
1. Starten Sie den AEM Forms-Server.
