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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
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
source-wordcount: '210'
ht-degree: 100%
---
# Konfigurieren der Einstellungen für die Kontosperrung {#configure-account-locking-settings}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

Wenn Sie eine Domain hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option „Kontosperrung aktivieren“ aktiviert ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinanderfolgender Authentifizierungsfehler gesperrt. Nach einem bestimmten Zeitraum können Benutzende dann eine erneute Authentifizierung versuchen. Dies verhindert, dass Benutzende versuchen, verschiedene Berechtigungskombinationen für den Systemzugriff zu verwenden.

Geben Sie mithilfe der Einstellungen auf der Seite „Domain-Verwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domains, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Einstellungen > User Management > Domain-Verwaltung]**.
1. Geben Sie in das Feld „Maximale Anzahl aufeinanderfolgender Authentifizierungsfehler“ ein, wie oft sich Benutzende aufeinanderfolgend fehlerhaft anmelden dürfen, bevor ihr Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld „Sperre für Konto aufheben nach (Minuten)“ die Minutenzahl ein, für die das Benutzerkonto dann gesperrt wird. Nach der so bestimmten Minutenzahl können die Benutzenden eine erneute Anmeldung versuchen. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
