---
title: Anpassen von Entwurfs- und Übermittlungsdatendiensten
description: AEM Forms speichert standardmäßig Entwürfe von adaptiven Formularen und gesendete adaptive Formulare in einem Standardknoten auf der Veröffentlichungsinstanz. Sie können jedoch die Entwurfs- und Übermittlungsdatendienste von AEM Forms konfigurieren, um die Speicherung von Entwürfen von adaptiven Formularen und gesendeten adaptiven Formularen anzupassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
exl-id: ed10ef8c-7b9c-43cf-bea8-7cf9742a8cac
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 7da902b6-fe94-5180-8e7c-f6d1e38d01d5
    internal-label: Foundation Components
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 100%
---
# Anpassen von Entwurfs- und Übermittlungsdatendiensten {#customizing-draft-and-submission-data-services}

## Übersicht {#overview}

Mit AEM Forms können Benutzerinnen und Benutzer ein adaptives Formular als Entwurf speichern. Die Entwurfsfunktion bietet Benutzerinnen und Benutzern die Möglichkeit, ein Formular zu führen, das derzeit bearbeitet wird. Eine Benutzerin bzw. ein Benutzer kann das Formular dann jederzeit von jedem Gerät aus ausfüllen und senden.

Standardmäßig speichert AEM Forms die mit dem Entwurf und der Übermittlung verknüpften Benutzerdaten auf der Veröffentlichungsinstanz im `/content/forms/fp`-Knoten.

Komponenten des AEM-Formularportals bieten jedoch Datendienste, mit denen Sie die Implementierung der Speicherung von Benutzerdaten für Entwürfe und Übermittlungen anpassen können. Beispiel: Sie können die Daten in einem Datenspeicher speichern, der derzeit in Ihrem Unternehmen implementiert ist.

Um die Speicherung von Benutzerdaten anzupassen, müssen Sie die Dienste [Entwurfsdaten](/help/forms/using/custom-draft-submission-data-services.md#p-draft-data-service-p) und [Übermittlungsdaten](/help/forms/using/custom-draft-submission-data-services.md#p-submission-data-service-p) implementieren.

## Voraussetzungen {#prerequisites}

* Aktivieren von [Formularportal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* Erstellen einer [Formularportal-Seite](/help/forms/using/creating-form-portal-page.md)
* Aktivieren von [adaptiven Formularen für das Formularportal](/help/forms/using/draft-submission-component.md)
* Erfahren Sie mehr über [Implementierungsdetails für benutzerdefiniertes Speichern](/help/forms/using/draft-submission-component.md#customizing-the-storage)

## Entwurfsdatendienst {#draft-data-service}

Um die Speicherung von Benutzerentwurfsdaten anzupassen, müssen Sie die Implementierung für alle Methoden der `DraftAFDataService`-Oberfläche bereitstellen.

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
  * @param draftUserDataMap contains Form Data (key - "guideState"), Adaptive Form Name (Key - "guideName"), and Draft DataID (Key - "userDataID") if there is update
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

Um die Speicherung von Benutzerübermittlungsdaten anzupassen, müssen Sie die Implementierung für alle Methoden der `SubmittedAFDataService`-Oberfläche bereitstellen.

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
