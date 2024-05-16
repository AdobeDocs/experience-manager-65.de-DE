---
title: Aktivieren von Anlagen für ein HTML5-Formular
description: Standardmäßig ist die Anlagenunterstützung für HTML5-Formulare deaktiviert.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 8eebfcd6-0597-44ed-b718-bf9a1baa6c12
feature: HTML5 Forms
exl-id: 68912260-179a-4d1b-b944-0a1777c021ac
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '339'
ht-degree: 100%

---

# Aktivieren von Anlagen für ein HTML5-Formular {#enabling-attachments-for-an-html-form}

Sie können Anlagen mit HTML5-Formularen hochladen, in einer Vorschau anzeigen und übermitteln. Standardmäßig ist die Anlagenunterstützung deaktiviert. Gehen Sie wie folgt vor, um die Unterstützung der Anlage zu aktivieren:

1. Erstellen Sie ein [benutzerdefiniertes Profil](/help/forms/using/custom-profile.md) mit einer `mfAttachmentOptions` Mehrfachauswahl-Zeichenfolgeneigenschaft. Jede Zeichenfolge in der `mfAttachmentOptions`-Eigenschaft muss über ein `property=value`-Format verfügen, um Optionen des Dateianhang-Widgets zu konfigurieren. `property` und `value` können einen der folgenden Werte haben:

   | Eigenschaft | Wert |
   |--- |---|
   | multiSelect | „true“ oder „false“ (true standardmäßig ausgewählt) |
   | fileSizeLimit | Zahl in MB (standardmäßig 2 MB). Zum Beispiel 5. |
   | buttonText | Schaltflächentext für Popupfenster (standardmäßig „Anhängen“) |
   | Akzeptieren der Bedingungen | durch Kommas getrennte Liste der zu akzeptierenden Dateitypen („audio/&amp;ast;, video/&amp;ast;, image/&amp;ast;, text/&amp;ast;, .pdf“ standardmäßig) |

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
