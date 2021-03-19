---
title: Forms-Portal | Umgang mit Benutzerdaten
seo-title: Forms-Portal | Umgang mit Benutzerdaten
description: Forms-Portal | Umgang mit Benutzerdaten
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 60%

---


# Forms-Portal | Umgang mit Benutzerdaten {#forms-portal-handling-user-data}

[!DNL AEM Forms] portal bietet Komponenten, die Sie zur Liste adaptiver Formulare, HTML5-Formulare und anderer Forms-Elemente auf der  [!DNL AEM Sites] Seite verwenden können. Darüber hinaus können Sie sie so konfigurieren, dass Entwürfe und eingereichte adaptive Formulare und HTML5-Formulare für einen angemeldeten Benutzer angezeigt werden. Weitere Informationen zum Forms Portal finden Sie unter [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md).

Wenn ein angemeldeter Benutzer ein adaptives Formular als Entwurf speichert oder übermittelt, wird es auf den Registerkarten Entwürfe und Sendungen im Forms-Portal angezeigt. Die Daten für Entwürfe oder übermittelte Formulare werden in dem für die AEM-Bereitstellung konfigurierten Datenspeicher gespeichert. Die Entwürfe und Sendungen anonymer Benutzer werden nicht auf der Forms-Portalseite angezeigt. Die Daten werden jedoch im konfigurierten Datenspeicher gespeichert. Weitere Informationen finden Sie unter [Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Das Forms-Portal speichert Daten für Entwürfe und übermittelte Formulare in folgenden Szenarien:

* Die Sendeaktion, die im adaptiven Formular konfiguriert wird, lautet **Forms-Portal-Sendeaktion**.
* Bei anderen Übermittlungsaktionen als **Forms Portal-Übermittlungsaktion** ist die Option **[!UICONTROL Daten im Formularportal]** speichern in den Eigenschaften **[!UICONTROL Übermitteln]** des Containers für adaptive Formulare aktiviert.

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
   <td><p><strong>Standort</strong></p> </td>
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
   <td>Datenbanktabellen <code>data</code>, <code>metadata</code> und <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Formulardaten für angemeldete und anonyme Benutzer zugreifen und diese bei Bedarf löschen.

### AEM-Instanzen {#aem-instances}

Alle Entwürfe und gesendeten Formulardaten in AEM Instanzen (Autor, Veröffentlichung oder Remote) für angemeldete und anonyme Benutzer werden im Knoten `/content/forms/fp/` des entsprechenden AEM Repository gespeichert. Jedes Mal, wenn ein angemeldeter oder anonymer Benutzer einen Entwurf speichert oder ein Formular sendet, werden für jede Anlage `draft ID` oder `submission ID`, `user data ID` und für jede Anlage (falls zutreffend) ein `ID`-Zufallswert generiert, der mit dem entsprechenden Entwurf oder der entsprechenden Übermittlung verknüpft ist.

#### Zugreifen auf Benutzerdaten {#access-user-data}

Wenn ein angemeldeter Benutzer einen Entwurf speichert oder ein Formular absendet, wird ein untergeordneter Knoten mit seiner Benutzer-ID erstellt. Beispiel: Entwürfe und Übermittlungsdaten für Sarah Rose, deren Benutzer-ID `srose` lautet, werden im `/content/forms/fp/srose/`-Knoten AEM Repository gespeichert. Innerhalb des Benutzer-ID-Knotens sind die Daten in einer hierarchischen Struktur organisiert.

Die folgende Tabelle erläutert, wie die Daten für alle Entwürfe von `srose` im AEM Repository gespeichert werden.

>[!NOTE]
>
>Eine exakte Struktur wie `drafts` wird für gesendete Formulare für `srose` unter dem Knoten `/content/forms/fp/srose/submit/` repliziert.
>
>Alle Entwürfe und Übermittlungen von `anonymous`-Benutzern werden unter dem Knoten `/content/forms/fp/anonymous/` gespeichert, der Entwürfe und Übermittlungen für alle anonymen Benutzer unter den Knoten `draft` und `submit` organisiert.

| Node | Beschreibung |
|---|---|
| `/content/forms/fp/srose/drafts` | Container-Knotendaten für alle Entwürfe durch den Benutzer |
| `/content/forms/fp/srose/drafts/attachments/` | Organisiert alle Anhänge für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Enthält Anhang für die ausgewählte ID im Binärformat |
| `/content/forms/fp/srose/drafts/metadata/` | Organisiert Formularmetadaten für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Enthält Formularmetadaten für die ausgewählte Entwurfs-ID |
| `/content/forms/fp/srose/drafts/data/` | Organisiert Formulardaten für den Benutzer anhand der Benutzerdaten-ID |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Enthält Formulardaten für die ausgewählte Benutzerdaten-ID im Binärformat |

#### Benutzerdaten löschen  {#delete-user-data}

Um Benutzerdaten aus Entwürfen und Sendungen für einen angemeldeten Benutzer von AEM-Systemen vollständig zu löschen, müssen Sie den Knoten `user ID` für einen bestimmten Benutzer vom Author-Knoten löschen. Sie müssen Daten manuell von allen anwendbaren AEM-Instanzen löschen.

Entwürfe und Übermittlungsdaten für alle anonymen Benutzer werden innerhalb der allgemeinen `drafts`- und `submit`-Knoten unter `/content/forms/fp/anonymous` gespeichert. Es gibt keine Methode, Daten für einen bestimmten anonymen Benutzer zu finden, es sei denn, es sind bestimmte identifizierbare Informationen bekannt. In diesem Fall können Sie in AEM Repository nach Informationen suchen, die den anonymen Benutzer identifizieren, und den Knoten, der ihn enthält, manuell aus allen entsprechenden AEM-Instanzen löschen, um Daten aus dem AEM zu entfernen. Um jedoch Daten für alle anonymen Benutzer zu löschen, können Sie den Knoten `anonymous` löschen, um Daten zu Entwürfen und Übermittlungen für alle anonymen Benutzer zu entfernen.

### Datenbank {#database}

Wenn AEM zum Speichern von Daten in einer Datenbank konfiguriert ist, werden die Formularentwurfs- und Sendedaten für das Portal in den folgenden Datenbanktabellen für angemeldete und anonyme Benutzer gespeichert:

* data
* metadata
* additionalmetadata

#### Zugreifen auf Benutzerdaten  {#access-user-data-1}

Führen Sie den folgenden Datenbankbefehl aus, um auf Entwürfe und Sendedaten für angemeldete und anonyme Benutzer in den Datenbanktabellen zuzugreifen. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, auf deren Daten Sie zugreifen möchten, oder durch `anonymous` für anonyme Benutzer.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Benutzerdaten löschen {#delete-user-data-1}

Um Entwürfe und Sendedaten für den angemeldeten Benutzer aus den Datenbanktabellen zu löschen, führen Sie den folgenden Datenbankbefehl aus. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, deren Daten Sie löschen möchten, oder bei anonymen Benutzern durch `anonymous`. Beachten Sie: Um Daten für einen bestimmten anonyme Benutzer aus der Datenbank zu löschen, müssen Sie die Daten mit einigen identifizierbaren Informationen suchen und sie aus den Datenbanktabellen, die diese Informationen enthalten, löschen.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```

