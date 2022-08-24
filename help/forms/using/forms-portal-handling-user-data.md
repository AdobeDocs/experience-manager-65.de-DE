---
title: Formularportal | Umgang mit Benutzerdaten
seo-title: Forms Portal | Handling user data
description: Formularportal | Umgang mit Benutzerdaten
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
role: Admin
exl-id: 791524a4-a8bb-4632-a68d-e96864e139a9
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 100%

---

# Formularportal | Umgang mit Benutzerdaten {#forms-portal-handling-user-data}

Das [!DNL AEM Forms]-Portal stellt Komponenten bereit, mit denen Sie adaptive Formulare, HTML5-Formulare und andere Formular-Assets auf der [!DNL AEM Sites]-Seite auflisten können. Darüber hinaus können Sie es so konfigurieren, dass Entwürfe und übermittelte adaptive Formulare und HTML5-Formulare für einen angemeldeten Benutzer angezeigt werden. Weitere Informationen zum Formularportal finden Sie unter [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md).

Wenn ein angemeldeter Benutzer ein adaptives Formular als Entwurf speichert oder übermittelt, wird es auf den Registerkarten Entwürfe und Sendungen im Forms-Portal angezeigt. Die Daten für Entwürfe oder übermittelte Formulare werden in dem für die AEM-Bereitstellung konfigurierten Datenspeicher gespeichert. Die Entwürfe und Sendungen anonymer Benutzer werden nicht auf der Forms-Portalseite angezeigt. Die Daten werden jedoch im konfigurierten Datenspeicher gespeichert. Weitere Informationen finden Sie unter [Konfigurieren von Speicher-Services für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Das Forms-Portal speichert Daten für Entwürfe und übermittelte Formulare in folgenden Szenarien:

* Die Sendeaktion, die im adaptiven Formular konfiguriert wird, lautet **Formularportal-Sendeaktion**.
* Für andere Sendeaktionen als die **Formularportal-Sendeaktion** ist die Option **[!UICONTROL Daten im Formularportal speichern]** in den **[!UICONTROL Übermitteln]**-Eigenschaften des adaptiven Formular-Containers aktiviert.

Forms-Portal speichert für jeden Entwurf und jedes übermittelte Formular für angemeldete und anonyme Benutzer folgende Daten:

* Formularmetadaten wie Formularname, Formularpfad, Entwurfs- oder Sendungs-ID, Anlagenpfad und Benutzerdaten-ID
* Formularanhang als Datenbytes
* Formulardaten als Datenbytes

Abhängig von der konfigurierten Datenspeicherpersistenz werden Entwürfe und übermittelte Formulardaten an den folgenden Speicherorten gespeichert.

<table>
 <tbody>
  <tr>
   <td><p><strong>Persistenztyp</strong></p> </td>
   <td><p><strong>Datenspeicher</strong></p> </td>
   <td><p><strong>Speicherort</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standard</p> </td>
   <td><p>AEM-Repository von Author- und Veröffentlichungsinstanzen</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Remote</p> </td>
   <td><p>AEM-Repository von Author- und Remote-AEM-Instanzen</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Datenbank</p> </td>
   <td><p>AEM-Repository von Author-Instanz- und Datenbanktabellen</p> </td>
   <td>Datenbanktabellen <code>data</code>, <code>metadata</code> und <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Formulardaten für angemeldete und anonyme Benutzer zugreifen und diese bei Bedarf löschen.

### AEM-Instanzen {#aem-instances}

Alle Entwürfe und eingereichten Formulardaten in AEM-Instanzen (Autoren-, Veröffentlichungs- oder Remote-Instanzen) für angemeldete und nicht angemeldete Benutzer werden im Knoten `/content/forms/fp/` des entsprechenden AEM-Repositorys gespeichert. Jedes Mal, wenn ein angemeldeter oder anonymer Benutzer einen Entwurf speichert oder ein Formular übermittelt, wird eine `draft ID` oder eine `submission ID`, eine `user data ID` und eine zufällige `ID` für jeden Anhang (falls zutreffend) generiert, die dem jeweiligen Entwurf oder der Übermittlung zugeordnet ist.

#### Zugreifen auf Benutzerdaten {#access-user-data}

Wenn ein angemeldeter Benutzer einen Entwurf speichert oder ein Formular absendet, wird ein untergeordneter Knoten mit seiner Benutzer-ID erstellt. Zum Beispiel werden Entwurfs- und Sendedaten für Sarah Rose, deren Benutzer-ID `srose` lautet, im Knoten `/content/forms/fp/srose/` im AEM-Repository gespeichert. Innerhalb des Benutzer-ID-Knotens sind die Daten in einer hierarchischen Struktur organisiert.

In der folgenden Tabelle wird erläutert, wie die Daten für alle Entwürfe von `srose` im AEM-Repository gespeichert werden.

>[!NOTE]
>
>Eine exakte Struktur wie `drafts` wird für eingereichte Formulare für `srose` unter dem Knoten `/content/forms/fp/srose/submit/` repliziert.
>
>Alle Entwürfe und Sendungen von `anonymous` Benutzer werden unter dem Knoten `/content/forms/fp/anonymous/` gespeichert, in dem Entwürfe und Sendungen für alle anonymen Benutzer unter den Knoten `draft` und `submit` organisiert werden.

| Knoten | Beschreibung |
|---|---|
| `/content/forms/fp/srose/drafts` | Container-Knotendaten für alle Entwürfe durch den Benutzer |
| `/content/forms/fp/srose/drafts/attachments/` | Organisiert alle Anhänge für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Enthält den Anhang für die ausgewählte ID im Binärformat |
| `/content/forms/fp/srose/drafts/metadata/` | Organisiert Formularmetadaten für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Enthält Formularmetadaten für die ausgewählte Entwurfs-ID |
| `/content/forms/fp/srose/drafts/data/` | Organisiert Formulardaten für den Benutzer anhand der Benutzerdaten-ID |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Enthält Formulardaten für die ausgewählte Benutzerdaten-ID im Binärformat |

#### Löschen von Benutzerdaten {#delete-user-data}

Um Benutzerdaten aus Entwürfen und Sendungen für einen angemeldeten Benutzer vollständig von AEM-Systemen zu löschen, müssen Sie den Knoten `user ID` für einen bestimmten Benutzer aus dem Autorenknoten löschen. Sie müssen Daten manuell aus allen anwendbaren AEM-Instanzen löschen.

Entwurfs- und Sendedaten für alle anonymen Benutzer werden in den allgemeinen Knoten `drafts` und `submit` unter `/content/forms/fp/anonymous` gespeichert. Es gibt keine Methode, um Daten für einen bestimmten anonymen Benutzer zu finden, es sei denn, es sind einige identifizierbare Informationen bekannt. In diesem Fall können Sie nach den Informationen suchen, die den anonymen Anwender im AEM-Repository identifizieren, und den Knoten, der ihn enthält, manuell aus allen entsprechenden AEM-Instanzen löschen, um die Daten aus dem AEM-System zu entfernen. Wenn Sie jedoch die Daten für alle anonymen Anwender löschen möchten, können Sie den Koten `anonymous` löschen, um Entwürfe und Sendedaten für alle anonymen Anwender zu entfernen.

### Datenbank {#database}

Wenn AEM zum Speichern von Daten in einer Datenbank konfiguriert ist, werden die Formularentwurfs- und Sendedaten für das Portal in den folgenden Datenbanktabellen für angemeldete und anonyme Benutzer gespeichert:

* Daten
* Metadaten
* additionalmetadata

#### Zugreifen auf Benutzerdaten {#access-user-data-1}

Führen Sie den folgenden Datenbankbefehl aus, um auf Entwürfe und Sendedaten für angemeldete und anonyme Benutzer in den Datenbanktabellen zuzugreifen. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, auf deren Daten Sie zugreifen möchten, oder durch `anonymous` für anonyme Benutzer.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Löschen von Benutzerdaten {#delete-user-data-1}

Um Entwürfe und Sendedaten für den angemeldeten Benutzer aus den Datenbanktabellen zu löschen, führen Sie den folgenden Datenbankbefehl aus. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, deren Daten Sie löschen möchten, oder durch `anonymous` für anonyme Benutzer. Beachten Sie: Um Daten für einen bestimmten anonymen Anwender aus der Datenbank zu löschen, müssen Sie die Daten mit einigen identifizierbaren Informationen suchen und sie aus den Datenbanktabellen löschen, die diese Informationen enthalten.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
