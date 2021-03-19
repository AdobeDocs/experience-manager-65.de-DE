---
title: Speichern eines HTML5-Formulars als Entwurf
seo-title: Speichern eines HTML5-Formulars als Entwurf
description: Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen.
seo-description: Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen.
uuid: 70cd5f6f-f125-470c-8cee-ee14d2127713
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 66%

---


# Speichern eines HTML5-Formulars als Entwurf {#saving-an-html-form-as-a-draft}

Sie können ein HTML5-Formular als Entwurf speichern, und das Formular zu einem späteren Zeitpunkt ausfüllen. Im Forms Portal können Benutzer HTML5-Formulare speichern und wiederherstellen. Um die Funktion &quot;Als Entwurf speichern&quot;zu aktivieren, fügen Sie dem Profil-Knoten die folgenden Konfigurationen hinzu:

## benutzerdefiniertes Profil zum Aktivieren der Funktion „Als Entwurf speichern“{#custom-profile-to-allow-save-as-draft-feature}

Standardmäßig stellt AEM Forms das Profil **Als Entwurf speichern** bereit. Sie können ein Formular mit dem Profil „Als Entwurf speichern“ wiedergeben, um für ein HTML5-Formular die Entwurffunktion zu aktivieren. Sie können HTML-Renderprofile für ein Formular in [Forms Manager](/help/forms/using/introduction-managing-forms.md) angeben.

Um die Funktion &quot;Als Entwurf speichern&quot;für Ihr vorhandenes [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) zu aktivieren, fügen Sie Ihrem benutzerdefinierten Profil-Knoten die folgenden Eigenschaften hinzu:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>mfAllowFPDraft</td>
   <td>Zeichenfolge</td>
   <td>true</td>
   <td><p>Aktiviert die Funktion „Als Entwurf speichern“</p> <p>für dieses Profil.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>Zeichenfolge</td>
   <td>true</td>
   <td><p>Ermöglicht das Hochladen von Anlagen</p> <p>mit diesem Profil.</p> </td>
  </tr>
 </tbody>
</table>

## Speicherung und Auflistung von Entwürfen {#drafts-storage-and-listing}

Nach der Aktivierung der Funktion „Als Entwurf speichern“ wird das Formular, wenn es gespeichert wurde, in der Komponente [Drafts and Submission (Entwurf und Übermittlung)](/help/forms/using/draft-submission-component.md) aufgelistet. Sie können das gespeicherte Formular aus der Komponente „Drafts and Submissions“ abrufen und mit dem Ausfüllen beginnen.

Um die Formularauflistung für die Komponente &quot;Drafts and Submission&quot;zu aktivieren, fügen Sie die folgende Eigenschaft zum Profil-Knoten hinzu:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschaftsname</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Wert</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>fp.enablePortalSubmit</td>
   <td>Zeichenfolge</td>
   <td>true</td>
   <td>So aktivieren Sie, dass Entwürfe und Formulare nach dem Senden in der Komponente "Forms Portal-Entwürfe und -Übermittlungen"aufgelistet werden<br /></td>
  </tr>
 </tbody>
</table>

Standardmäßig speichert AEM Forms die mit dem Entwurf und der Übermittlung eines Formulars verknüpften Benutzerdaten im Knoten /content/forms/fp in der Veröffentlichungsinstanz. Sie können einen benutzerdefinierten Speicheranbieter hinzufügen. Weitere Informationen finden Sie unter [Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“](/help/forms/using/adding-custom-storage-provider-forms.md).
