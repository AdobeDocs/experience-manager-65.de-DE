---
title: Konfigurieren der Einstellungen für die Kontosperrung
description: Verwenden Sie die Option „Kontosperrung aktivieren“, um Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler zu sperren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: eb8c748d-51d9-4684-97c5-e982ad84ba9f
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Konfigurieren der Einstellungen für die Kontosperrung {#configure-account-locking-settings}

Wenn Sie eine Domain hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option „Kontosperrung aktivieren“ aktiviert ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler gesperrt. Nach einem bestimmten Zeitraum können Benutzende dann eine erneute Authentifizierung versuchen. Dies verhindert, dass Benutzende versuchen, verschiedene Berechtigungskombinationen für den Systemzugriff zu verwenden.

Geben Sie mithilfe der Einstellungen auf der Seite „Domain-Verwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domains, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Einstellungen > User Management > Domain-Verwaltung]**.
1. Geben Sie in das Feld „Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler“ ein, wie oft sich Benutzende aufeinanderfolgend fehlerhaft anmelden dürfen, bevor ihr Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld „Sperre für Konto aufheben nach (Minuten)“ die Minutenzahl ein, für die das Benutzerkonto dann gesperrt wird. Nach der so bestimmten Minutenzahl können die Benutzenden eine erneute Anmeldung versuchen. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
