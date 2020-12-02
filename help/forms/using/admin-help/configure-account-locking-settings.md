---
title: Einstellungen für die Kontosperrung konfigurieren
seo-title: Einstellungen für die Kontosperrung konfigurieren
description: Verwenden Sie die Option „Kontosperrung aktivieren“, um Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler zu sperren.
seo-description: Verwenden Sie die Option „Kontosperrung aktivieren“, um Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler zu sperren.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 95%

---


# Einstellungen für die Kontosperrung konfigurieren {#configure-account-locking-settings}

Wenn Sie eine Domäne hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option „Kontosperrung aktivieren“ aktiviert ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler gesperrt. Nach einem bestimmten Zeitraum kann der Benutzer eine erneute Authentifizierung versuchen. Dies verhindert, dass Benutzer verschiedene Berechtigungskombinationen für den Systemzugriff zu verwenden versuchen.

Geben Sie mithilfe der Einstellungen auf der Seite „Domänenverwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domänen, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > User Management > Domänenverwaltung]**.
1. Geben Sie in das Feld „Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler“ ein, wie oft sich ein Benutzer aufeinanderfolgend fehlerhaft anmelden darf, bevor sein Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld „Sperre für Konto aufheben nach (Minuten)“ die Minutenzahl ein, für die das Benutzerkonto gesperrt wird. Nach einer bestimmten Minutenzahl kann der Benutzer eine erneute Anmeldung versuchen. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

