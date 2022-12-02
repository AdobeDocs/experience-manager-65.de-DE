---
title: Bestehende Domains bearbeiten und konvertieren
seo-title: Editing and converting existing domains
description: Erfahren Sie, wie Sie auf der Seite „Domain-Verwaltung“ die Einstellungen für bestehende Domains ändern. Konvertieren Sie eine bestehende Unternehmens-Domain in eine Hybrid-Domain oder umgekehrt.
seo-description: Learn how to change the settings for existing domains from the Domain Management page. Convert an existing enterprise domain to a hybrid domain or vice versa.
uuid: 4cc9547e-b4ec-4588-b1cf-18720f06149a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 44dec184-3ef7-4ba6-a87f-ad171d3cb188
exl-id: 34ac5f8b-f209-4f99-ad71-4df6f2c88c1e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '310'
ht-degree: 100%

---

# Bestehende Domains bearbeiten und konvertieren{#editing-and-converting-existing-domains}

Sie können auf der Seite „Domain-Verwaltung“ die Einstellungen für bestehende Domains ändern. Sie können auch eine bestehende Unternehmens-Domain in eine Hybrid-Domain umwandeln.

## Eine vorhandene Domain bearbeiten {#edit-an-existing-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Domain, die bearbeitet werden soll.
1. Um den Domain-Namen zu ändern, bearbeiten Sie den Text im Feld „Name“.
1. Um die Authentifizierungsinformationen für eine Unternehmens- oder Hybrid-Domain zu ändern, klicken Sie auf den entsprechenden Authentifizierungsnamen am unteren Rand der Seite. Ändern Sie auf der Seite „Authentifizierung bearbeiten“ die Einstellungen den Anforderungen entsprechend. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Um die Ordnerinformationen für eine Unternehmens-Domain zu ändern, klicken Sie auf den entsprechenden Ordnernamen am unteren Rand der Seite. Ändern Sie auf der Seite „Verzeichnis bearbeiten“ die Einstellungen den Anforderungen entsprechend. (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. Wenn Sie die gewünschten Änderungen durchgeführt haben, klicken Sie auf „OK“.

## Konvertieren einer Unternehmens-Domain in eine Hybrid-Domain {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Unternehmens-Domain, die umgewandelt werden soll.
1. Klicken Sie auf „In Hybrid-Domain konvertieren“.
1. Überprüfen Sie die zu Benutzern und Gruppen und zur Benutzerauthentifizierung angezeigten Informationen und klicken Sie auf „OK“.
1. Bearbeiten Sie die Einstellungen der Hybrid-Domain und klicken Sie auf „OK“.

>[!NOTE]
>
>Wenn die Unternehmens-Domain, die Sie konvertieren, keine Ordnereinstellungen enthält, gehen alle LDAP-Authentifizierungseinstellungen verloren.

## Eine Hybrid-Domain in eine Unternehmens-Domain umwandeln {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Klicken Sie auf den Namen der Hybrid-Domain, die umgewandelt werden soll.
1. Klicken Sie auf „In Unternehmens-Domain konvertieren“.
1. Überprüfen Sie die zu Benutzern und Gruppen und zur Benutzerauthentifizierung angezeigten Informationen und klicken Sie auf „OK“.
1. Klicken Sie auf „Verzeichnis hinzufügen“ und konfigurieren Sie die erforderlichen Ordnerinformationen. (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
