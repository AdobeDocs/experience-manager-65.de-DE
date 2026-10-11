---
title: Aktivieren von Anlagen für ein HTML5-Formular
description: Standardmäßig ist die Anlagenunterstützung für HTML5-Formulare deaktiviert.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms,Mobile Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
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
source-wordcount: '339'
ht-degree: 94%
---
# Aktivieren von Anlagen für ein HTML5-Formular {#enabling-attachments-for-an-html-form}

Sie können Anlagen mit HTML5-Formularen hochladen, in einer Vorschau anzeigen und übermitteln. Standardmäßig ist die Anlagenunterstützung deaktiviert. Gehen Sie wie folgt vor, um die Unterstützung der Anlage zu aktivieren:

1. Erstellen Sie ein [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) mit einer `mfAttachmentOptions` Mehrfachauswahl-Zeichenfolgeneigenschaft. Jede Zeichenfolge in der `mfAttachmentOptions`-Eigenschaft muss über ein `property=value`-Format verfügen, um Optionen des Dateianhang-Widgets zu konfigurieren. `property` und `value` können einen der folgenden Werte haben:

   | Eigenschaft | Wert |
   |--- |---|
   | multiSelect | „true“ oder „false“ (true standardmäßig ausgewählt) |
   | fileSizeLimit | Zahl in MB (standardmäßig 2 MB). Zum Beispiel 5. |
   | buttonText | Schaltflächentext für Popupfenster (standardmäßig „Anhängen“) |
   | Akzeptieren der Bedingungen | Durch Kommas getrennte Liste der zu akzeptierenden Dateitypen („audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf“ standardmäßig) |

   Beispiel:

   ![Optionen konfigurieren](assets/mfAttachmentOptions.png)

   Bei Bedarf können Sie auch weitere benutzerdefinierte Optionen für die Eigenschaft `mfAttachmentOptions` angeben.

   >[!NOTE]
   >
   >In Microsoft Internet Explorer 9 können Benutzende Dateien anfügen, die größer sind, als der angegebene Grenzwert. Hierbei handelt es sich um ein bekanntes Problem.

1. Verwenden Sie den [Metadaten-Editor](/help/forms/using/manage-form-metadata.md), um das benutzerdefinierte Profil auszuwählen, das Sie oben für HTML-5-Formulare erstellt haben.
1. Sie können die Formularvorlage mit dem benutzerdefinierten Profil rendern; das Anlagensymbol wird dann in der Symbolleiste „Formulare“ angezeigt.

   >[!NOTE]
   >
   >Standardmäßig bietet das Formularportal ein benutzerdefiniertes Profil mit aktivierter Entwurfs- und Anlagenfunktion. Weitere Informationen zum Profil **Als Entwurf speichern** finden Sie unter [HTML5 Forms als Entwurf speichern](/help/forms/using/saving-html5-form-draft.md).

1. Klicken Sie auf das Anlagensymbol. Es wird ein Dialogfeld zur Anlagenauswahl angezeigt. Suchen Sie nach der Anlage, wählen Sie sie aus und klicken Sie auf **Anhängen**.

   >[!NOTE]
   >
   >Klicken Sie zum Anzeigen einer Anlage in der Vorschau auf den Anlagennamen.

   >[!NOTE]
   >
   >Die Option „Dateivorschau“ ist nicht für anonyme Benutzer verfügbar.

## Anlagenformat beim Übermitteln {#attachment-submission-format}

Wenn Anlagen aktiviert sind, übermittelt das HTML5-Formular mehrteilige Daten. Die mehrteiligen Übermittlungsdaten bestehen aus zwei Teilen **dataXml** und **Anhängen**.

>[!NOTE]
>
>Wenn die Option `mfAllowAttachments` deaktiviert ist, senden die HTML5-Formulare aus Gründen der Abwärtskompatibilität keine mehrteiligen Daten. Es sendet einfache Daten-XML im Format **application/xml**.

Wenn das Flag „mfAllowAttachments“ aktiviert ist, werden die mehrteiligen Daten vom [Sendedienst Proxydienst](/help/forms/using/service-proxy.md) mit dataXml und Anlagen gesendet.
