---
title: Forms-Portal | Umgang mit Benutzerdaten
seo-title: Forms-Portal | Umgang mit Benutzerdaten
description: 'null'
seo-description: 'null'
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
translation-type: tm+mt
source-git-commit: 4e0709031aca030e50840811a9b3717f3cb20340
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 60%

---


# Forms-Portal | Umgang mit Benutzerdaten {#forms-portal-handling-user-data}

[!DNL AEM Forms] portal stellt Komponenten bereit, die Sie zur Liste adaptiver Formulare, HTML5-Formulare und anderer Forms-Elemente auf der [!DNL AEM Sites] Seite verwenden können. Darüber hinaus können Sie sie so konfigurieren, dass Entwürfe und eingereichte adaptive Formulare und HTML5-Formulare für einen angemeldeten Benutzer angezeigt werden. For more information about forms portal, see [Introduction to publishing forms on a portal](/help/forms/using/introduction-publishing-forms.md).

Wenn ein angemeldeter Benutzer ein adaptives Formular als Entwurf speichert oder übermittelt, wird es auf den Registerkarten Entwürfe und Sendungen im Forms-Portal angezeigt. Die Daten für Entwürfe oder übermittelte Formulare werden in dem für die AEM-Bereitstellung konfigurierten Datenspeicher gespeichert. Die Entwürfe und Sendungen anonymer Benutzer werden nicht auf der Forms-Portalseite angezeigt. Die Daten werden jedoch im konfigurierten Datenspeicher gespeichert. Weitere Informationen finden Sie unter [Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Das Forms-Portal speichert Daten für Entwürfe und übermittelte Formulare in folgenden Szenarien:

* Die Sendeaktion, die im adaptiven Formular konfiguriert wird, lautet **Forms-Portal-Sendeaktion**.
* For submit actions other than **Forms Portal Submit Action**, the **[!UICONTROL Store data in forms portal]** option is enabled in the **[!UICONTROL Submission]** properties of the adaptive form container.

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
   <td><p><strong>Ort</strong></p> </td>
  </tr>
  <tr>
   <td><p>Default</p> </td>
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
   <td>Datenbanktabellen <code>data</code>, <code>metadata</code>und <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Formulardaten für angemeldete und anonyme Benutzer zugreifen und diese bei Bedarf löschen.

### AEM-Instanzen {#aem-instances}

All drafts and submitted forms data in AEM instances (author, publish, or remote) for logged-in and anonymous users are stored in the `/content/forms/fp/` node of the applicable AEM repository. Every time a logged-in or anonymous user saves a draft or submits a form, a `draft ID` or `submission ID`, a `user data ID`, and a random `ID` for each attachment (if applicable) is generated, which is associated with the respective draft or submission.

#### Zugreifen auf Benutzerdaten {#access-user-data}

Wenn ein angemeldeter Benutzer einen Entwurf speichert oder ein Formular absendet, wird ein untergeordneter Knoten mit seiner Benutzer-ID erstellt. For example, drafts and submissions data for Sarah Rose whose user ID is `srose` are stored in `/content/forms/fp/srose/` node in AEM repository. Innerhalb des Benutzer-ID-Knotens sind die Daten in einer hierarchischen Struktur organisiert.

The following table explains how the data for all drafts by `srose` is stored in AEM repository.

>[!NOTE]
>
>An exact structure like `drafts` is replicated for submitted forms for `srose` under the `/content/forms/fp/srose/submit/` node.
>
>All drafts and submissions by `anonymous` users are stored under the `/content/forms/fp/anonymous/` node, which organizes drafts and submissions for all anonymous users under the `draft` and `submit` nodes.

| Node | Beschreibung |
|---|---|
| `/content/forms/fp/srose/drafts` | Container-Knotendaten für alle Entwürfe durch den Benutzer |
| `/content/forms/fp/srose/drafts/attachments/` | Organisiert alle Anhänge für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Enthält Anhang für die ausgewählte ID im Binärformat |
| `/content/forms/fp/srose/drafts/metadata/` | Organisiert Formularmetadaten für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Enthält Formularmetadaten für die ausgewählte Entwurfs-ID |
| `/content/forms/fp/srose/drafts/data/` | Organisiert Formulardaten für den Benutzer anhand der Benutzerdaten-ID |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Enthält Formulardaten für die ausgewählte Benutzerdaten-ID im Binärformat |

#### Benutzerdaten löschen {#delete-user-data}

Um Benutzerdaten aus Entwürfen und Sendungen für einen angemeldeten Benutzer von AEM-Systemen vollständig zu löschen, müssen Sie den Knoten `user ID` für einen bestimmten Benutzer vom Author-Knoten löschen. Sie müssen Daten manuell von allen anwendbaren AEM-Instanzen löschen.

Drafts and submission data for all anonymous users is stored within the common `drafts` and `submit` nodes under `/content/forms/fp/anonymous`. Es gibt keine Methode, Daten für einen bestimmten anonymen Benutzer zu finden, es sei denn, es sind bestimmte identifizierbare Informationen bekannt. In diesem Fall können Sie in AEM Repository nach Informationen suchen, die den anonymen Benutzer identifizieren, und den Knoten, der ihn enthält, manuell aus allen entsprechenden AEM-Instanzen löschen, um Daten aus dem AEM zu entfernen. However, to delete data for all anonymous users, you can delete the `anonymous` node to remove drafts and submissions data for all anonymous users.

### Datenbank {#database}

Wenn AEM zum Speichern von Daten in einer Datenbank konfiguriert ist, werden die Formularentwurfs- und Sendedaten für das Portal in den folgenden Datenbanktabellen für angemeldete und anonyme Benutzer gespeichert:

* data
* metadata
* additionalmetadata

#### Zugreifen auf Benutzerdaten {#access-user-data-1}

Führen Sie den folgenden Datenbankbefehl aus, um auf Entwürfe und Sendedaten für angemeldete und anonyme Benutzer in den Datenbanktabellen zuzugreifen. In the query, replace `logged-in user` with the user ID whose data you want to access or with `anonymous` for anonymous users.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Benutzerdaten löschen {#delete-user-data-1}

Um Entwürfe und Sendedaten für den angemeldeten Benutzer aus den Datenbanktabellen zu löschen, führen Sie den folgenden Datenbankbefehl aus. In the query, replace `logged-in user` with the user ID whose data you want to delete or with `anonymous` for anonymous users. Beachten Sie: Um Daten für einen bestimmten anonyme Benutzer aus der Datenbank zu löschen, müssen Sie die Daten mit einigen identifizierbaren Informationen suchen und sie aus den Datenbanktabellen, die diese Informationen enthalten, löschen.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```

