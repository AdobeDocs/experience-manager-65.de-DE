---
title: Bestehende Domänen bearbeiten und konvertieren
seo-title: Bestehende Domänen bearbeiten und konvertieren
description: Erfahren Sie, wie Sie auf der Seite „Domänenverwaltung“ die Einstellungen für bestehende Domänen ändern. Konvertieren Sie eine bestehende Unternehmensdomäne in eine Hybriddomäne oder umgekehrt.
seo-description: Erfahren Sie, wie Sie auf der Seite „Domänenverwaltung“ die Einstellungen für bestehende Domänen ändern. Konvertieren Sie eine bestehende Unternehmensdomäne in eine Hybriddomäne oder umgekehrt.
uuid: 4cc9547e-b4ec-4588-b1cf-18720f06149a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 44dec184-3ef7-4ba6-a87f-ad171d3cb188
exl-id: 34ac5f8b-f209-4f99-ad71-4df6f2c88c1e
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 100%

---

# Bestehende Domänen bearbeiten und konvertieren{#editing-and-converting-existing-domains}

Sie können auf der Seite „Domänenverwaltung“ die Einstellungen für bestehende Domänen ändern. Sie können auch eine bestehende Unternehmensdomäne in eine Hybriddomäne umwandeln.

## Eine vorhandene Domäne bearbeiten {#edit-an-existing-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf den Namen der Domäne, die bearbeitet werden soll.
1. Um den Domänennamen zu ändern, bearbeiten Sie den Text im Feld „Name“.
1. Um die Authentifizierungsinformationen für eine Unternehmens- oder Hybriddomäne zu ändern, klicken Sie auf den entsprechenden Authentifizierungsnamen am unteren Rand der Seite. Ändern Sie auf der Seite „Authentifizierung bearbeiten“ die Einstellungen den Anforderungen entsprechend. (Siehe [Authentifizierungseinstellungen](/help/forms/using/admin-help/configuring-authentication-providers.md#authentication-settings).)
1. Um die Ordnerinformationen für eine Unternehmensdomäne zu ändern, klicken Sie auf den entsprechenden Ordnernamen am unteren Rand der Seite. Ändern Sie auf der Seite „Verzeichnis bearbeiten“ die Einstellungen den Anforderungen entsprechend. (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
1. Wenn Sie die gewünschten Änderungen durchgeführt haben, klicken Sie auf „OK“.

## Eine Unternehmensdomäne in eine Hybriddomäne konvertieren  {#convert-an-enterprise-domain-to-a-hybrid-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf den Namen der Unternehmensdomäne, die umgewandelt werden soll.
1. Klicken Sie auf „In Hybriddomäne konvertieren“.
1. Überprüfen Sie die zu Benutzern und Gruppen und zur Benutzerauthentifizierung angezeigten Informationen und klicken Sie auf „OK“.
1. Bearbeiten Sie die Einstellungen der Hybriddomäne und klicken Sie auf „OK“.

>[!NOTE]
>
>Wenn die Unternehmensdomäne, die Sie konvertieren, keine Ordnereinstellungen enthält, gehen alle LDAP-Authentifizierungseinstellungen verloren.

## Eine Hybriddomäne in eine Unternehmensdomäne umwandeln  {#convert-a-hybrid-domain-to-an-enterprise-domain}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Klicken Sie auf den Namen der Hybriddomäne, die umgewandelt werden soll.
1. Klicken Sie auf In Unternehmensdomäne konvertieren.
1. Überprüfen Sie die zu Benutzern und Gruppen und zur Benutzerauthentifizierung angezeigten Informationen und klicken Sie auf „OK“.
1. Klicken Sie auf „Verzeichnis hinzufügen“ und konfigurieren Sie die erforderlichen Ordnerinformationen. (Siehe [Ordner oder benutzerdefinierten SPIs hinzufügen](/help/forms/using/admin-help/configuring-directories.md#adding-directories-or-custom-spis).)
