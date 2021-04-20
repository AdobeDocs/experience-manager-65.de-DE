---
title: Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“
seo-title: Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“
description: Erfahren Sie, wie Sie die Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen können.
seo-description: Erfahren Sie, wie Sie die Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen können.
uuid: ac2e80ee-a9c7-44e6-801e-fe5a840cb7f8
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 154255e7-468a-42e6-a33d-eee691cf854d
feature: Forms Portal
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 70%

---


# Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“{#custom-storage-for-drafts-and-submissions-component}

## Überblick {#overview}

Mit AEM Forms können Sie ein Formular als Entwurf speichern. Mit der Entwurfsfunktion können Sie ein aktuelles Formular beibehalten, welches Sie zu einem späteren Zeitpunkt auf einem anderen Gerät abschließen und senden können.

Standardmäßig speichert AEM Forms die mit dem Entwurf und der Übermittlung eines Formulars verknüpften Benutzerdaten im Knoten `/content/forms/fp` in der Veröffentlichungsinstanz. Darüber hinaus stellen die AEM Forms-Portalkomponenten Datendienste bereit, die Sie zum Anpassen des Speicherns der Benutzerdaten für Entwürfe und Übermittlungen verwenden können. Beispielsweise können Sie Benutzerdaten in einem Datenspeicher speichern.

## Voraussetzungen  {#prerequisites}

* Aktivieren Sie [Forms Portal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* Erstellen einer [Forms Portal-Seite](/help/forms/using/creating-form-portal-page.md)
* Aktivieren Sie [adaptive Formulare für das Formularportal](/help/forms/using/draft-submission-component.md)
* Informationen zu [Implementierungsdetails der benutzerdefinierten Datenspeicherung](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Entwurfsdatendienst {#draft-data-service}

Um das Speichern der Benutzerdaten für Entwürfe anzupassen, müssen Sie alle Methoden der `DraftDataService`-Schnittstelle implementieren. Im Folgenden Beispielcode werden die Methoden und die Argumente beschrieben.

```java
/**
 * DraftDataService service will get/delete/save user data (attachments and form data) filled with a draft instance of Form
 */

public interface DraftDataService {

    /**
     * To save/modify user data for this userDataID, it will be null in case of creation
     * @param draftDataID: unique identifier associated with the form data
     * @param formName: name of the form whose draft is being saved
     * @param formData: user data associated with this draft
     * @return userdataID corresponding to which user data has been stored and which can be used later to retrieve this user data
     * @throws FormsPortalException
     */
    public String saveData (String draftDataID, String formName, String formData) throws FormsPortalException;

    /**
     * Returns the user data stored against the ID passed as the argument
     * @param userDataID: unique data id for user data associated with a draft
     * @return user data associated with this data ID
     * @throws FormsPortalException
     */

    public byte[] getData (String userDataID) throws FormsPortalException;

    /**
     * To delete data associated with this draft
     * @param userDataID: unique data id for data associated with a draft
     * @return status of delete operation on data associated with this draft
     * @throws FormsPortalException
     */

    public boolean deleteData (String userDataID) throws FormsPortalException;

    /**
     * Saves the attachment for current form instance
     * @param attachmentsBytes: byte array of the attachment to be saved
     * @return unique id (attachmentID) for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachment (byte[] attachmentBytes) throws FormsPortalException;

    /**
     * To delete an attachment
     * @param attachmentID: unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;

    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

>[!NOTE]
>
>Der Mindestwert für die Länge des Entwurfs-ID-Felds beträgt 26 Zeichen. Adobe empfiehlt, die Entwurfslänge der ID auf 26 Zeichen oder mehr festzulegen.

## Übermittlungsdatendienst {#submission-data-service}

Um das Speichern der Benutzerdaten für Übermittlungen anzupassen, müssen Sie alle Methoden der `SubmitDataService`-Schnittstelle implementieren. Im Folgenden Beispielcode werden die Methoden und die Argumente beschrieben.

```java
/**
 * SubmitDataService service will get/delete/submit user data (attachments and form data) filled with a submission of Form
 */
public interface SubmitDataService {

    /**
     * Submits the user data passed in argument map
     * @param userDataID, unique identifier associated with this user data
     * @param formName, name of the form whose draft is being submitted
     * @param formData, user data associated with this submission
     * @return userdataID, corresponding to which the user data has been stored and which can be used later to retrieve this data
     * @throws FormsPortalException
     */
    public String saveData (String userDataID, String formName, String formData) throws FormsPortalException;

    /**
     * Submits the user data provided as byte array
     * @param id
     * @param data
     * @return id corresponding to saved data
     * @throws FormsPortalException
     */
    public String saveData (String id, byte[] data) throws FormsPortalException;

    /** Submits the user data provided as byte array asynchronously for the user name provided in the options map
     * @param data data to be saved in bytes
     * @param options map containing options that affect this save
     * @return id of the saved data instance
     */
    public String saveDataAsynchronusly(byte[] data, Map<String, Object> options) throws FormsPortalException;

    /**
     * Gets the user data stored against the ID passed as argument
     * @param userDataID: unique id associated with this user data for this submission
     * @return user data associated with this submission
     * @throws FormsPortalException
     */
    public byte[] getData(String userDataID) throws FormsPortalException;

    /**
     * Deletes user data stored against the userDataID
     * @param userDataID: unique id associated with this user data for this submission
     * @return status of the delete operation on this submission
     * @throws FormsPortalException
     */

    public boolean deleteData(String userDataID) throws FormsPortalException;

    /**
     * Submits the attachment bytes passed as argument
     * @param attachmentsBytes: would expect byte array of the attachment for this submission
     * @return attachmentID for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachment(byte[] attachmentBytes) throws FormsPortalException;

    /** Submits the attachment bytes passed as argument asynchronously for the user id provided in options map.
     * @param attachmentBytes would expect byte array of the attachment for this submission
     * @param options map containing options that affect this save
     * @return attachmentID for the attachment just saved (so that it could be retrieved later)
     * @throws FormsPortalException
     */
    public String saveAttachmentAsynchronously(byte[] attachmentBytes, Map<String, Object> options) throws FormsPortalException;

    /**
     * To delete an attachment
     * @param attachmentID: Unique id for this attachment
     * @return status of delete operation performed on attachment corresponding to this attachment ID
     * @throws FormsPortalException
     */
    public boolean deleteAttachment (String attachmentID) throws FormsPortalException;

    /**
     * To get attachment bytes
     * @param attachmentID: unique id for this attachment
     * @return data corresponding to this attachmentID
     * @throws FormsPortalException
     */
    public byte[] getAttachment (String attachmentID) throws FormsPortalException;
}
```

Forms Portal verwendet das Konzept eines UUID (Universally Unique Identifier), um eine eindeutige ID für die einzelnen Entwürfe und übermittelten Formulare zu generieren. Sie können auch selbst eine eindeutige ID generieren. Sie können die Schnittstelle FPKeyGeneratorService implementieren, deren Methoden überschreiben und eine benutzerdefinierte Logik entwickeln, um eine benutzerdefinierte eindeutige ID für jeden Entwurf und jedes gesendete Formular zu generieren. Legen Sie außerdem den Dienstrang der benutzerdefinierten ID-Generierungsimplementierung auf einen Wert über 0. Dies stellt sicher, dass die benutzerdefinierte Implementierung anstelle der Standardimplementierung verwendet wird.

```java
public interface FPKeyGeneratorService {
    /**
     * returns a unique id for draft and submission
     *
     * @param none
     * @return unique id in string format as per the implementation
     * @throws FormsPortalException
     */
    public String getUniqueId() throws FormsPortalException;
}
```

Mit der folgenden Anmerkung können Sie die Servicebewertung für die mit dem obigen Code generierte benutzerdefinierte ID erhöhen:

`@Properties(value = { @Property(name = "service.ranking", intValue = 15) } )`

Um die oben stehende Anmerkung zu verwenden, importieren Sie Folgendes in Ihr Projekt:

```java
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
```

