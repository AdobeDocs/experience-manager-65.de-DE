---
title: Formularportal | Umgang mit Benutzerdaten
description: Erfahren Sie mehr über die Verwaltung von Benutzerdaten wie Zugriff, Löschen und Datenspeicher in AEM Forms Portal.
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin
exl-id: 791524a4-a8bb-4632-a68d-e96864e139a9
source-git-commit: 000c22028259eb05a61625d43526a2e8314a1d60
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 73%

---

# Formularportal | Umgang mit Benutzerdaten {#forms-portal-handling-user-data}

[!DNL AEM Forms] Portal stellt Komponenten bereit, mit denen Sie adaptive Formulare, HTML5-Formulare und andere Forms-Assets auf der [!DNL AEM Sites] Seite. Darüber hinaus können Sie es so konfigurieren, dass Entwürfe und übermittelte adaptive Formulare und HTML5-Formulare für einen angemeldeten Benutzer angezeigt werden. Weitere Informationen zu Forms Portal finden Sie unter [Einführung in das Veröffentlichen von Formularen in einem Portal](/help/forms/using/introduction-publishing-forms.md).

Wenn ein angemeldeter Benutzer ein adaptives Formular als Entwurf speichert oder sendet, wird es auf den Registerkarten Entwürfe und Übermittlungen im Forms Portal angezeigt. Die Daten für entworfene oder übermittelte Formulare werden in dem für die AEM-Bereitstellung konfigurierten Datenspeicher gespeichert. Die Entwürfe und Übermittlungen anonymer Benutzer werden nicht auf der Forms Portal-Seite angezeigt. Die Daten werden jedoch im konfigurierten Datenspeicher gespeichert. Siehe [Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

## Benutzerdaten und Datenspeicher {#user-data-and-data-stores}

Forms Portal speichert Daten für Entwurfs- und gesendete Formulare in den folgenden Szenarien:

* Die Sendeaktion, die im adaptiven Formular konfiguriert wird, lautet **Formularportal-Sendeaktion**.
* Für Sendeaktionen, die nicht **Übermittlungsaktion für Forms Portal**, die **[!UICONTROL Speichern von Daten in Forms Portal]** ist in der **[!UICONTROL Einsendung]** Eigenschaften des Containers für adaptive Formulare.

Für jeden Entwurf und jedes gesendete Formular für angemeldete und anonyme Benutzer speichert das Forms-Portal die folgenden Daten:

* Formularmetadaten wie Formularname, Formularpfad, Entwurfs- oder Übermittlungs-ID, Anhangspfad und Benutzerdaten-ID
* Formularanhang als Daten-Bytes
* Formulardaten als Daten-Bytes

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
   <td><p>AEM Repository der Autoren- und Veröffentlichungsinstanzen</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Remote</p> </td>
   <td><p>AEM Repository von Autoren- und Remote-AEM-Instanzen</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Datenbank</p> </td>
   <td><p>AEM Repository der Autoreninstanz und Datenbanktabellen</p> </td>
   <td>Datenbanktabellen <code>data</code>, <code>metadata</code> und <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Zugreifen auf und Löschen von Benutzerdaten {#access-and-delete-user-data}

Sie können in den konfigurierten Datenspeichern auf Entwürfe und übermittelte Formulardaten für angemeldete und anonyme Benutzende zugreifen und diese bei Bedarf löschen.

### AEM-Instanzen {#aem-instances}

Alle Entwürfe und eingereichten Formulardaten in AEM-Instanzen (Autoren-, Veröffentlichungs- oder Remote-Instanzen) für angemeldete und nicht angemeldete Benutzer werden im Knoten `/content/forms/fp/` des entsprechenden AEM-Repositorys gespeichert. Jedes Mal, wenn angemeldete oder anonyme Benutzende einen Entwurf speichern oder ein Formular übermitteln, wird eine `draft ID` oder `submission ID`, eine `user data ID` und eine zufällige `ID` für jeden Anhang (falls vorhanden) generiert. Diese ist mit dem entsprechenden Entwurf oder der Übermittlung verknüpft.

#### Zugreifen auf Benutzerdaten {#access-user-data}

Wenn ein angemeldeter Benutzer einen Entwurf speichert oder ein Formular sendet, wird ein untergeordneter Knoten mit seiner Benutzer-ID erstellt. Zum Beispiel werden Entwurfs- und Sendedaten für Sarah Rose, deren Benutzer-ID `srose` lautet, im Knoten `/content/forms/fp/srose/` im AEM-Repository gespeichert. Innerhalb des Benutzer-ID-Knotens sind die Daten in einer hierarchischen Struktur organisiert.

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
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Enthält einen Anhang für die ausgewählte ID im Binärformat |
| `/content/forms/fp/srose/drafts/metadata/` | Organisiert Formularmetadaten für den Benutzer basierend auf der Entwurfs-ID |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Enthält Formularmetadaten für die ausgewählte Entwurfs-ID |
| `/content/forms/fp/srose/drafts/data/` | Organisiert Formulardaten für den Benutzer anhand der Benutzerdaten-ID |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Enthält Formulardaten für die ausgewählte Benutzerdaten-ID im Binärformat |

#### Löschen von Benutzerdaten {#delete-user-data}

Um Benutzerdaten aus Entwürfen und Sendungen für einen angemeldeten Benutzer vollständig von AEM-Systemen zu löschen, müssen Sie den Knoten `user ID` für einen bestimmten Benutzer aus dem Autorenknoten löschen. Löschen Sie Daten manuell aus allen anwendbaren AEM-Instanzen.

Entwurfs- und Sendedaten für alle anonymen Benutzer werden in den allgemeinen Knoten `drafts` und `submit` unter `/content/forms/fp/anonymous` gespeichert. Es gibt keine Methode, um Daten für einen bestimmten anonymen Benutzer zu finden, es sei denn, es sind einige identifizierbare Informationen bekannt. In diesem Fall können Sie im AEM-Repository nach den Informationen suchen, die die anonyme Person identifizieren, und den Knoten, der sie enthält, manuell aus allen entsprechenden AEM-Instanzen löschen, um die Daten aus dem AEM-System zu entfernen. Wenn Sie jedoch die Daten für alle anonymen Anwender löschen möchten, können Sie den Koten `anonymous` löschen, um Entwürfe und Sendedaten für alle anonymen Anwender zu entfernen.

### Datenbank {#database}

Wenn AEM zum Speichern von Daten in einer Datenbank konfiguriert ist, werden die Entwurfs- und Sendedaten von Forms Portal in den folgenden Datenbanktabellen sowohl für angemeldete als auch für anonyme Benutzer gespeichert:

* Daten
* Metadaten
* additionalmetadata

#### Zugreifen auf Benutzerdaten {#access-user-data-1}

Um auf Entwürfe und Sendedaten für eine angemeldete und anonyme Person in den Datenbanktabellen zuzugreifen, führen Sie den folgenden Datenbankbefehl aus. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, auf deren Daten Sie zugreifen möchten, oder durch `anonymous` für anonyme Benutzer.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Löschen von Benutzerdaten {#delete-user-data-1}

Um Entwürfe und Sendedaten für eine angemeldete Person aus den Datenbanktabellen zu löschen, führen Sie den folgenden Datenbankbefehl aus. Ersetzen Sie in der Abfrage `logged-in user` durch die Benutzer-ID, deren Daten Sie löschen möchten, oder durch `anonymous` für anonyme Benutzer. Um Daten für eine bestimmte anonyme Person aus der Datenbank zu löschen, müssen Sie die Daten mit einigen identifizierbaren Informationen suchen und sie aus den Datenbanktabellen löschen, die diese Informationen enthalten.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
