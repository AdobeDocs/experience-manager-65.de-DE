---
title: Speichern eines HTML5-Formulars als Entwurf
description: Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: HTML5 Forms,Mobile Forms
exl-id: a9879445-d626-4279-8a95-a9009294b483
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 97aafc4b-2598-52d6-9012-295a95969e38
    internal-label: HTML5 Forms
  - id: 59f95943-e802-56ac-990d-21ab923984c1
    internal-label: Mobile Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 100%
---
# Speichern eines HTML5-Formulars als Entwurf {#saving-an-html-form-as-a-draft}

Sie können ein HTML5-Formular als Entwurf speichern und das Formular zu einem späteren Zeitpunkt ausfüllen. Im Formularportal können Benutzende HTML5-Formulare speichern und wiederherstellen. Fügen Sie zum Aktivieren der Funktion „Als Entwurf speichern“ die folgenden Konfigurationen zum Profilknoten hinzu:

## Benutzerdefiniertes Profil zum Aktivieren der Funktion „Als Entwurf speichern“ {#custom-profile-to-allow-save-as-draft-feature}

In AEM Forms gibt es standardmäßig das Profil **Als Entwurf speichern**. Sie können ein Formular mit dem Profil „Als Entwurf speichern“ rendern, um die Entwurfsfunktion für ein HTML5-Formular zu aktivieren. Sie können HTML-Render-Profile für ein Formular in [Forms Manager](/help/forms/using/introduction-managing-forms.md) angeben.

Fügen Sie zum Aktivieren der Funktion „Als Entwurf speichern“ für Ihr bestehendes [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) die folgenden Eigenschaften zu Ihrem benutzerdefinierten Profilknoten hinzu:

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
   <td>Ja</td>
   <td><p>Aktiviert die Funktion „Als Entwurf speichern“</p> <p>für dieses Profil.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>Zeichenfolge</td>
   <td>Ja</td>
   <td><p>Ermöglicht das Hochladen von Anhängen</p> <p>mit diesem Profil.</p> </td>
  </tr>
 </tbody>
</table>

## Speichern und Auflisten von Entwürfen {#drafts-storage-and-listing}

Nach der Aktivierung der Funktion „Als Entwurf speichern“ wird das Formular, wenn es gespeichert wurde, in der Komponente [Drafts and Submission (Entwurf und Übermittlung)](/help/forms/using/draft-submission-component.md) aufgelistet. Sie können das gespeicherte Formular aus der Komponente „Drafts and Submissions“ (Entwurf und Übermittlung) abrufen und mit dem Ausfüllen beginnen.

Fügen Sie zum Aktivieren der Formularauflistung für die Komponente „Entwürfe und Übermittlungen“ die folgende Eigenschaft zum Profilknoten hinzu:

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
   <td>Ja</td>
   <td>Gehen Sie wie folgt vor, um Entwürfe und Formulare nach dem Übermitteln in<br /> der Komponente „Entwürfe und Übermittlungen“ des Formularportals aufzulisten</td>
  </tr>
 </tbody>
</table>

Standardmäßig speichert AEM Forms die Benutzerdaten, die mit dem Entwurf und der Übermittlung eines Formulars im Knoten /content/forms/fp in der Veröffentlichungsinstanz verknüpft sind. Sie können einen benutzerdefinierten Speicheranbieter hinzufügen. Weitere Informationen finden Sie unter [Benutzerdefinierter Speicher für Komponenten „Drafts and Submissions (Entwurf und Übermittlung)“](/help/forms/using/adding-custom-storage-provider-forms.md).
