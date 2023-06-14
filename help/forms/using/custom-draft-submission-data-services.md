---
title: Anpassen von Entwurfs- und Übermittlungsdatendiensten
description: AEM Forms speichert standardmäßig Entwurfs- und gesendete adaptive Formulare in einem Standardknoten auf der Veröffentlichungsinstanz. Sie können jedoch die Entwurfs- und Übermittlungsdatendienste von AEM Forms konfigurieren, um die Speicherung von Entwurfs- und gesendeten adaptiven Formularen anzupassen.
uuid: c3ec1708-3b11-4142-93f0-1cffb6643f34
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: 602fd6a9-9a65-411c-8475-a4082a3fdee0
exl-id: ed10ef8c-7b9c-43cf-bea8-7cf9742a8cac
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 28%

---

# Anpassen von Entwurfs- und Übermittlungsdatendiensten {#customizing-draft-and-submission-data-services}

## Übersicht {#overview}

Mit AEM Forms können Benutzer ein adaptives Formular als Entwurf speichern. Die Entwurfsfunktion bietet Benutzern die Möglichkeit, ein Formular zu verwalten, das derzeit bearbeitet wird. Ein Benutzer kann das Formular dann jederzeit von jedem Gerät aus ausfüllen und senden.

Standardmäßig speichert AEM Forms Benutzerdaten, die mit dem Entwurf und der Übermittlung verknüpft sind, in der Veröffentlichungsinstanz im `/content/forms/fp` Knoten.

AEM Forms Portal-Komponenten bieten jedoch Datendienste, mit denen Sie die Implementierung der Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen können. Beispiel: Sie können die Daten in einem Datenspeicher speichern, der derzeit in Ihrem Unternehmen implementiert ist.

Um die Speicherung von Benutzerdaten anzupassen, müssen Sie die [Entwurfsdaten](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) und [Übermittlungsdaten](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) Dienste.

## Voraussetzungen {#prerequisites}

* Aktivieren [Forms Portal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* Erstellen Sie eine [Forms Portal-Seite](/help/forms/using/creating-form-portal-page.md)
* Aktivieren [adaptive Formulare für Forms Portal](/help/forms/using/draft-submission-component.md)
* Erfahren Sie mehr über [Implementierungsdetails für benutzerdefiniertes Speichern](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Entwurfsdatendienst {#draft-data-service}

Um die Speicherung von Benutzerentwurfsdaten anzupassen, müssen Sie die Implementierung für alle Methoden des `DraftAFDataService` -Schnittstelle.

Eine Beschreibung der Methoden und deren Argumente finden Sie im folgenden Code-Beispiel der Schnittstelle:

```java
public interface DraftAFDataService {

 /**
  * Deletes the user data stored against the ID passed as the argument
  *
  * @param draftDataID
  * @return status for the just occurred delete draft UserData operation
  * @throws FormsPortalException
  */
 public Boolean deleteAFDraftUserData (String draftDataID) throws FormsPortalException;

 /**
  * Saves user data provided in the argument map
  *
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") in case of update
  * @return userData ID would be returned which needs to be saved in metadata node
  * @throws FormsPortalException
  */
 public String saveAFUserData (Map<String, Object> draftUserDataMap) throws FormsPortalException;

 /**
  * Gets the user data stored against the ID passed as the argument
  *
  * @param Draft DataID
  * @return guideState (which would then be populated in adaptive form to reload the draft) which is stored against draftDataID
  * @throws FormsPortalException
  */
 public byte[] getAFDraftUserData(String draftDataID) throws FormsPortalException;

 /**
  * Saves the attachments for current adaptive form instance
  *
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String saveAttachments(byte[] attachmentBytes) throws FormsPortalException;
}
```

## Übermittlungsdatendienst {#submission-data-service}

Um die Speicherung von Benutzerübermittlungsdaten anzupassen, müssen Sie die Implementierung für alle Methoden der `SubmittedAFDataService` -Schnittstelle.

Eine Beschreibung der Methoden und deren Argumente finden Sie im folgenden Code-Beispiel der Schnittstelle:

```java
public interface SubmittedAFDataService {

 /**
  * Submits the user data passed in argument map
  *
  * @param submittedAFUserdataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID")
  * @return userData ID is returned that needs to be saved in the metadata node
  * @throws FormsPortalException
  */
 public String submitAFUserData (Map<String, Object> submittedAFUserdataMap) throws FormsPortalException;

 /**
  * Gets the user data stored against the ID passed as argument
  *
  * @param submitDataID
  * @return guideState which would be used to open DOR
  * @throws FormsPortalException
  */
 public byte[] getSubmittedAFUSerData(String submitDataID) throws FormsPortalException;

 /**
  * Deletes user data stored against the ID passed as argument
  *
  * @param Submit DataID
  * @return status of the delete operation on Submitted User data
  * @throws FormsPortalException
  */

 public Boolean deleteSubmittedAFUserData(String submitDataID) throws FormsPortalException;

 /**
  * Submits the attachment bytes passed as argument
  *
  * @param attachmentsBytes would expect byte array of the attachment to be saved
  * @return id for the attachment just saved (so that it could be retrieved later)
  * @throws FormsPortalException
  */
 public String submitAttachments(Object attachmentBytes) throws FormsPortalException;

}
```
