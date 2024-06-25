---
title: Forms-Benutzerverwaltung | Umgang mit Benutzerdaten
description: Erfahren Sie, wie Sie mit der User Management-Komponente in AEM Forms JEE Benutzende erstellen, autorisieren und verwalten können, die Zugriff auf AEM Forms benötigen.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: eeeab5d1-073a-4e13-a781-391dfe70bb37
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '904'
ht-degree: 100%

---

# Forms-Benutzerverwaltung | Umgang mit Benutzerdaten {#forms-user-management-handling-user-data}

User Management ist eine AEM Forms JEE-Komponente, die das Erstellen, Verwalten und Autorisieren von AEM Forms-Benutzenden für den Zugriff auf AEM Forms ermöglicht. User Management verwendet Domains als Verzeichnisse zum Abrufen von Benutzerinformationen. Die folgenden Domain-Typen werden unterstützt:

**Lokale Domains**: Eine lokale Domain ist nicht mit einem Speichersystem eines Drittanbieters verbunden. Benutzer und Gruppen werden stattdessen lokal erstellt und befinden sich bei diesem Domain-Typ in der User Management-Datenbank. Kennwörter werden lokal gespeichert und die Authentifizierung erfolgt mithilfe einer lokalen Datenbank.

**Hybrid-Domains**: Diese Art von Domain ist nicht mit einem Speichersystem eines Drittanbieters verbunden. Benutzer und Gruppen werden stattdessen lokal erstellt und befinden sich bei diesem Domain-Typ in der User Management-Datenbank. Im Gegensatz zu lokalen Domains nutzen Hybrid-Domains einen externen Authentifizierungsanbieter, bei dem es sich um LDAP, Kerberos, SAML oder einen benutzerdefinierten Authentifizierungsanbieter handeln kann.

**Unternehmens-Domain**: Eine Unternehmens-Domain besteht aus Benutzern und Gruppen, die sich in einem Speichersystem von Drittanbietern wie etwa einem LDAP-Ordner befinden. User Management schreibt nicht in das Speichersystem von Drittanbietern. Stattdessen synchronisiert User Management die Benutzer- und Gruppeninformationen mit der Benutzerverwaltungsdatenbank. Unternehmens-Domains nutzen ferner einen externen Authentifizierungsanbieter, bei dem es sich um LDAP, Kerberos, SAML oder einen benutzerdefinierten Authentifizierungsanbieter handeln kann.

<!-- Fix broken links For more information about how user management works and configured, see AEM Forms JEE administration help. -->

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

User Management speichert Benutzerdaten in einer Datenbank, z. B. MySQL, Oracle, MS® SQL Server und IBM® DB2®. Darüber hinaus wird jeder Benutzer, der sich mindestens einmal in Forms-Programmen als AEM-Autor auf `https://'[server]:[port]'lc` angemeldet hat, im AEM-Repository erstellt. Daher wird die Benutzerverwaltung in den folgenden Datenspeichern gespeichert:

* Datenbank
* AEM-Repository
* Drittanbieterspeicher, z. B. LDAP-Verzeichnissen

>[!NOTE]
>
>In diesem Dokument geht es nicht um Daten, die in Drittanbieterspeichern gespeichert sind. Wenden Sie sich direkt an den Drittanbieter, um Benutzerdaten in solchen Speichern zu verwalten.

### Datenbank {#database}

User Management speichert Benutzerdaten in den folgenden Datenbanktabellen:

<table>
 <tbody>
  <tr>
   <td>Datenbanktabelle</td>
   <td>Beschreibung</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalEntity</code></td>
   <td><p>Speichert Informationen über Prinzipalentitäten. Ein Prinzipal kann eine Person, eine Gruppe oder eine Rolle sein.</p> <p> </p> </td>
  </tr>
  <tr>
   <td><code>EdcPrincipalUserEntity</code></td>
   <td>Speichert personenbezogene Daten (Personally Identifiable Information, PII) von Benutzenden. Es enthält einen Eintrag für jeden Benutzer aus lokalen, Unternehmens- und Hybrid-Domains.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalLocalAccountEntity</code></p> <p><code class="code">EdcPrincipalLocalAccount
       </code>(Oracle- und MS SQL®-Datenbanken)</p> </td>
   <td>Speichert Daten nur für lokale Benutzende.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalEmailAliasEntity</code></p> <p><code class="code">EdcPrincipalEmailAliasEn
       </code>(Oracle- und MS SQL®-Datenbanken)</p> </td>
   <td>Enthält Einträge aller Benutzer aus lokalen, Unternehmens- und Hybrid-Domains. Enthält Benutzer-E-Mail-IDs.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalGrpCtmntEntity</code></p> <p><code>EdcPrincipalGrpCtmntEnti</code><br /> (Oracle- und MS SQL®-Datenbanken)</p> </td>
   <td>Speichert die Zuordnung zwischen Benutzenden und Gruppen.</td>
  </tr>
  <tr>
   <td><code>EdcPrincipalRoleEntity</code></td>
   <td>Speichert die Zuordnung zwischen Rollen und Prinzipalen für Benutzende und Gruppen.</td>
  </tr>
  <tr>
   <td><code>EdcPriResPrmEntity</code></td>
   <td>Speichert die Zuordnung zwischen Prinzipal und Berechtigungen für Benutzende und Gruppen.</td>
  </tr>
  <tr>
   <td><p><code>EdcPrincipalMappingEntity</code></p> <p><code>EdcPrincipalMappingEntit</code><br /> (Oracle- und MS SQL®-Datenbanken)</p> </td>
   <td>Speichert alte und neue Attributwerte, die einem Prinzipal entsprechen.<br /> </td>
  </tr>
 </tbody>
</table>

### AEM-Repository {#aem-repository}

User Management-Daten für Benutzer, die mindestens einmal auf die Forms-Programme unter `https://'[server]:[port]'lc` zugegriffen haben, werden ebenfalls im AEM-Repository gespeichert.

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können auf Benutzerverwaltungsdaten für Benutzende in den Benutzerverwaltungsdatenbanken und im AEM-Repository zugreifen und sie exportieren sowie ggf. dauerhaft löschen.

### Datenbank {#database-1}

Um Benutzerdaten aus der Benutzerverwaltungsdatenbank zu exportieren oder zu löschen, müssen Sie mithilfe eines Datenbank-Clients eine Verbindung zu der Datenbank herstellen und anhand von PII der Person die Prinzipal-ID ermitteln. Um beispielsweise die Prinzipal-ID eines Benutzers mit einer Anmelde-ID abzurufen, führen Sie den folgenden `select`-Befehl in der Datenbank aus.

Ersetzen Sie im Befehl `select` die `<user_login_id>` durch die Anmelde-ID des Benutzers, dessen Prinzipal-ID Sie abrufen möchten.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Wenn Sie die Prinzipal-ID kennen, können Sie die Benutzerdaten exportieren oder löschen.

#### Exportieren von Benutzerdaten {#export-user-data}

Führen Sie die folgenden Datenbankbefehle aus, damit Sie Benutzerverwaltungsdaten für eine Prinzipal-ID aus Datenbanktabellen exportieren können. Ersetzen Sie `<principal_id>` im Befehl `select` durch die Haupt-ID der Person, deren Daten Sie exportieren möchten.

>[!NOTE]
>
>Die folgenden Befehle verwenden Datenbanktabellennamen in My SQL- und IBM® DB2®-Datenbanken. Ersetzen Sie beim Ausführen dieser Befehle in Oracle- und MS® SQL-Datenbanken die folgenden Tabellennamen in den Befehlen:
>
>* Ersetzen Sie `EdcPrincipalLocalAccountEntity` durch `EdcPrincipalLocalAccount`.
>
>* Ersetzen Sie `EdcPrincipalEmailAliasEntity` durch `EdcPrincipalEmailAliasEn`.
>
>* Ersetzen Sie `EdcPrincipalMappingEntity` durch `EdcPrincipalMappingEntit`.
>
>* Ersetzen Sie `EdcPrincipalGrpCtmntEntity` durch `EdcPrincipalGrpCtmntEnti`
>

```sql
Select * from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (Select id from EDCPRINCIPALENTITY where id='<principal_id>'));

Select * from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');

Select * from EdcPrincipalEntity where id='<principal_id>';
```

#### Benutzerdaten löschen {#delete-user-data}

Gehen Sie folgendermaßen vor, um Benutzerverwaltungsdaten für eine Prinzipal-ID aus Datenbanktabellen zu löschen.

1. Löschen Sie ggf. Benutzerdaten aus dem AEM-Repository, wie unter [Löschen von Benutzerdaten](/help/forms/using/user-management-handling-user-data.md#delete-aem) beschrieben.
1. Fahren Sie den AEM-Fomular-Server herunter.
1. Führen Sie die folgenden Datenbankbefehle aus, damit Sie Benutzerverwaltungsdaten für eine Prinzipal-ID aus Datenbanktabellen löschen können. Ersetzen Sie im Befehl `Delete` den Wert `<principal_id>` durch die Haupt-ID der Person, deren Daten Sie löschen möchten.

   ```sql
   Delete from EdcPrincipalLocalAccountEntity where refuserprincipalid in (Select id from EdcPrincipalUserEntity where refprincipalid in (select id from EdcPrincipalEntity where id='<principal_id>'));
   
   Delete from EdcPrincipalEmailAliasEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalRoleEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPriResPrmEntity where refprinid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalUserEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalMappingEntity where refprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalGrpCtmntEntity where refchildprincipalid in (Select id from EdcPrincipalEntity where id='<principal_id>');
   
   Delete from EdcPrincipalEntity where id='<principal_id>';
   ```

1. Starten Sie den AEM-Formular-Server.

### AEM-Repository {#aem-repository-1}

Die Daten der Forms JEE-Benutzenden sind im AEM-Repository vorhanden, wenn sie mindestens einmal auf die AEM Forms-Autoreninstanz zugegriffen haben. Sie können auf ihre Benutzerdaten zugreifen und diese aus dem AEM-Repository löschen.

#### Zugreifen auf Benutzerdaten {#access-user-data}

Um die im AEM-Repository erstellten Benutzer anzuzeigen, melden Sie sich bei `https://'[server]:[port]'/lc/useradmin` mit AEM-Administratorrechten an. Beachten Sie, dass `server` und `port` in der URL die der AEM-Author-Instanz sind. Hier können Sie nach Benutzenden anhand ihres Benutzernamens suchen. Doppelklicken Sie auf eine Person, um Informationen wie Eigenschaften, Berechtigungen und Gruppen für diese Person anzuzeigen. Die Eigenschaft `Path`für einen Benutzer gibt den Pfad zum Benutzerknoten an, der im AEM-Repository erstellt wurde.

#### Benutzerdaten löschen {#delete-aem}

So löschen Sie eine Person:

1. Navigieren Sie zu `https://'[server]:[port]'/lc/useradmin` mit AEM Administratorberechtigungen.
1. Suchen Sie nach einem Benutzer und doppelklicken Sie auf den Benutzernamen, um die Benutzereigenschaften zu öffnen. Kopieren Sie die `Path`-Eigenschaft.
1. Wechseln Sie zu AEM CRXDE Lite unter `https://'[server]:[port]'/lc/crx/de/index.jsp` und navigieren Sie zum Benutzerpfad oder suchen Sie ihn.
1. Löschen Sie den Pfad und klicken Sie auf **[!UICONTROL Alle speichern]**, um die Person dauerhaft aus dem AEM-Repository zu löschen.
