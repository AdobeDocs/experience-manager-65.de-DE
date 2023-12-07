---
title: Konfigurieren der Einstellungen für die Kontosperrung
description: Verwenden Sie die Option Kontosperrung aktivieren , um Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler zu sperren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: eb8c748d-51d9-4684-97c5-e982ad84ba9f
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 37%

---

# Konfigurieren der Einstellungen für die Kontosperrung {#configure-account-locking-settings}

Wenn Sie eine Domain hinzufügen, geben Sie an, ob die Kontosperrung aktiviert werden soll. Wenn die Option Kontosperrung aktivieren ausgewählt ist, werden Benutzerkonten nach einer bestimmten Anzahl aufeinander folgender Authentifizierungsfehler gesperrt. Nach einer bestimmten Zeitdauer kann der Benutzer versuchen, sich erneut zu authentifizieren. Diese Funktion verhindert, dass Benutzer verschiedene Berechtigungskombinationen für den Zugriff auf das System ausprobieren.

Geben Sie mithilfe der Einstellungen auf der Seite „Domain-Verwaltung“ die maximale Anzahl von Authentifizierungsfehlern sowie die Länge des Zeitraums, für den Konten gesperrt werden, an. Diese Einstellungen gelten für alle Domains, bei denen die Kontosperrung aktiviert ist.

1. Klicken Sie in der Administration-Console auf **[!UICONTROL Einstellungen > User Management > Domain-Verwaltung]**.
1. Geben Sie in das Feld Maximale Anzahl aufeinander folgender Authentifizierungsfehler an, wie oft ein Benutzer nacheinander nicht erfolgreich versuchen kann, sich anzumelden, bevor sein Konto gesperrt wird. Der Standardwert ist 20.
1. Geben Sie in das Feld &quot;Konto entsperren nach (Minuten)&quot;die Anzahl der Minuten ein, nach denen das Benutzerkonto gesperrt ist. Nach der angegebenen Anzahl von Minuten kann der Benutzer versuchen, sich erneut anzumelden. Der Standardwert ist 30.
1. Klicken Sie auf **[!UICONTROL Speichern]**.
