---
title: Document Security | Umgang mit Benutzerdaten
seo-title: Document Security | Umgang mit Benutzerdaten
description: 'null'
seo-description: 'null'
uuid: 1624a465-8b0c-4347-a53f-1118bfa6e18f
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 898268cb-4426-421f-8f63-d75bd85cb57f
translation-type: tm+mt
source-git-commit: 66a3db6cd50ae25849dc173e0714df7c140c1774

---


# Document Security | Umgang mit Benutzerdaten {#document-security-handling-user-data}

Mit AEM Forms Document Security können Sie vordefinierte Sicherheitseinstellungen erstellen, speichern und auf Ihre Dokumente anwenden. Es stellt sicher, dass nur autorisierte Benutzer die Dokumente verwenden können. Sie können Dokumente durch Richtlinien schützen. Eine Richtlinie ist eine Zusammenstellung von Informationen, die unter anderem Sicherheitseinstellungen und eine Liste berechtigter Benutzer umfasst. Sie können eine Richtlinie auf ein oder mehrere Dokumente anwenden und Benutzer autorisieren, die in der AEM Forms JEE-Benutzerverwaltung hinzugefügt wurden.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Document Security speichert Richtlinien und Daten in Bezug auf geschützte Dokumente, einschließlich Benutzerdaten in einer Datenbank, z. B. MySQL, Oracle, MS SQL Server und IBM DB2. Darüber hinaus sind die Daten für autorisierte Benutzer in einer Richtlinie in der Benutzerverwaltung gespeichert. For information about data stored in user management, see [Forms User Management: Handling user data](/help/forms/using/user-management-handling-user-data.md).

Die folgende Tabelle zeigt, wie die Dokumentensicherheit Daten in Datenbanktabellen organisiert.

<table>
 <tbody>
  <tr>
   <td>Datenbanktabelle</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalKeyEntity</code></td>
   <td>Speichert Informationen über Prinzipalschlüssel für die Benutzer. Die Schlüssel werden in Offline-Document-Security-Workflows verwendet.</td>
  </tr>
  <tr>
   <td><code>EdcAuditEntity</code></td>
   <td>Speichert Informationen zum Überwachungsereignis wie Benutzerereignisse, Dokumentereignisse und Richtlinienereignisse.</td>
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
   <td>Speichert Informationen über den Widerruf und die Wiederherstellung geschützter Dokumente.</td>
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
   <td>Speichert XML-Dateien für aktive Richtlinien. A policy XML<sup> </sup>contains references to principal IDs of users associated with the policy. Richtlinien-XML wird als Blob-Objekt gespeichert.</td>
  </tr>
  <tr>
   <td><code>EdcPolicyArchiveEntity</code></td>
   <td>Speichert Informationen zu archivierten Richtlinien. Eine archivierte Richtlinie enthält ihre Richtlinien-XML, die als Blob-Objekt gespeichert ist.</td>
  </tr>
  <tr>
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code> (Oracle- und MS SQL-Datenbanken)</p> </td>
   <td>Speichert die Zuordnung zwischen Richtliniensatz und Benutzern.</td>
  </tr>
  <tr>
   <td><code>EdcInvitedUserEntity</code></td>
   <td>Speichert Informationen zu eingeladenen Benutzern.</td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können auf Document Security-Daten für Benutzer in den Datenbanken zugreifen und sie exportieren und bei Bedarf dauerhaft löschen.

Um Benutzerdaten aus der Benutzerverwaltungsdatenbank zu exportieren oder zu löschen, müssen Sie mithilfe eines Datenbank-Clients eine Verbindung mit der Datenbank herstellen und anhand von PII des Benutzers die Prinzipal-ID ermitteln. Um beispielsweise die Prinzipal-ID eines Benutzers mit einer Anmelde-ID abzurufen, führen Sie den folgenden `select`-Befehl in der Datenbank aus.

In the `select` command, replace the `<user_login_id>` with the login ID of the user whose principal ID you want to retrieve from the `EdcPrincipalUserEntity` database table.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Nachdem Sie die Prinzipal-ID kennen, können Sie die Benutzerdaten exportieren oder löschen.

### Benutzerdaten exportieren {#export-user-data}

Führen Sie die folgenden Datenbankbefehle aus, um Benutzerdaten für eine Prinzipal-ID aus Datenbanktabellen zu exportieren. In the `select` command, replace `<principal_id>` with the principal ID of the user whose data you want to export.

>[!NOTE]
>
>Die folgenden Befehle verwenden Datenbanktabellennamen in My SQL- und IBM DB2-Datenbanken. When running these commands on Oracle and MS SQL databases, replace `EdcPolicySetPrincipalEntity` with `EdcPolicySetPrincipalEnt` in the commands.

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
>To export data from the `EdcAuditEntity` table, use the [EventManager.exportEvents](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API that takes [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) as a parameter to export audit data based on `principalId`, `policyId`, or `licenseId`.

Um vollständige Daten über einen Benutzer im System zu erhalten, müssen Sie auf Daten aus der Benutzerverwaltungsdatenbank zugreifen und diese exportieren. For more information, see [Forms user management: Handling user data](/help/forms/using/user-management-handling-user-data.md).

### Benutzerdaten löschen {#delete-user-data}

Führen Sie folgende Schritte aus, um Document Security-Daten für eine Prinzipal-ID aus Datenbanktabellen zu löschen.

1. Fahren Sie den AEM Forms-Server herunter.
1. Führen Sie die folgenden Datenbankbefehle aus, um Daten für die Principal-ID aus den Datenbanktabellen für die Document Security zu löschen. In the `Delete` command, replace `<principal_id>` with the principal ID of the user whose data you want to delete.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >To delete data from the `EdcAuditEntity` table, use the [EventManager.deleteEvents](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) API that takes [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-5/forms/programlc/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) as a parameter to delete audit data based on `principalId`, `policyId`, or `licenseId`.

1. Active and archived policy XML files are stored in the `EdcPolicyXmlEntity` and `EdcPolicyArchiveEntity` database tables, respectively. Führen Sie die folgenden Schritte aus, um Daten für einen Benutzer aus diesen Tabellen zu löschen:

   1. Open the XML blob of each row in the `EdcPolicyXMLEntity` or `EdcPolicyArchiveEntity` table and extract the XML file. Die XML-Datei ähnelt der unten gezeigten.
   1. Bearbeiten Sie die XML-Datei, um den Blob für die Prinzipal-ID zu entfernen.
   1. Wiederholen Sie die Schritte 1 und 2 für die andere Datei.
   >[!NOTE]
   >
   >You must remove the complete blob within the `Principal` tag for a principal ID or the policy XML may get corrupt or unusable.

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

   **Verwenden der Adminstration Console** 

   1. As an administrator, log into the Forms JEE administration console at https://[*server*]:[*port*]/adminui.
   1. Navigate to **[!UICONTROL Services > Document Security > Policy Sets]**.
   1. Öffnen Sie eine Richtliniengruppe und löschen Sie den Benutzer aus der Richtlinie.
   **Verwenden der Document Security-Webseite**

   Document Security-Benutzer, die zum Erstellen persönlicher Richtlinien berechtigt sind, können Benutzerdaten aus ihren Richtlinien löschen. Gehen Sie dazu wie folgt vor:

   1. Users who have personal policies log into their document security web page at https://[*server*]:[*port*]/edc.
   1. Navigate to **[!UICONTROL Services > Document Security > My Policies]**.
   1. Öffnen Sie eine Richtliniengruppe und löschen Sie den Benutzer aus der Richtlinie.
   **Hinweis**: Administratoren können in Administration Console unter &quot; **[!UICONTROL Dienste&quot;> &quot;Document Security&quot;> &quot;Meine Richtlinien&quot;Benutzerdaten suchen, aufrufen und aus den persönlichen Richtlinien anderer Benutzer löschen. Dies geschieht in Administration Console]** .

1. Löschen Sie die Daten für die Prinzipal-ID aus der Benutzerverwaltungsdatenbank. For detailed steps, see [Forms User Management | Handling user data](/help/forms/using/user-management-handling-user-data.md).
1. Starten Sie den AEM Forms-Server.

