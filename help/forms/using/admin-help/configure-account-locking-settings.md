---
title: Einstellungen für die Kontosperrung konfigurieren
seo-title: Configure account-locking settings
description: Verwenden Sie die Option „Kontosperrung aktivieren“, um Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler zu sperren.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: eb8c748d-51d9-4684-97c5-e982ad84ba9f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '194'
ht-degree: 100%

---

# Einstellungen für die Kontosperrung konfigurieren {#configure-account-locking-settings}

Wenn Sie eine Domain hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option „Kontosperrung aktivieren“ aktiviert ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler gesperrt. Nach einem bestimmten Zeitraum kann der Benutzer eine erneute Authentifizierung versuchen. Dies verhindert, dass Benutzer verschiedene Berechtigungskombinationen für den Systemzugriff zu verwenden versuchen.

Geben Sie mithilfe der Einstellungen auf der Seite „Domain-Verwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domains, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Einstellungen > User Management > Domain-Verwaltung]**.
1. Geben Sie in das Feld „Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler“ ein, wie oft sich ein Benutzer aufeinanderfolgend fehlerhaft anmelden darf, bevor sein Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld „Sperre für Konto aufheben nach (Minuten)“ die Minutenzahl ein, für die das Benutzerkonto gesperrt wird. Nach einer bestimmten Minutenzahl kann der Benutzer eine erneute Anmeldung versuchen. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
