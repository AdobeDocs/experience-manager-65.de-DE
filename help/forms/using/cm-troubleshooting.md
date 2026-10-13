---
title: 'Correspondence Management: Fehlerbehebung'
description: Erfahren Sie, wie Sie Fehler beheben können, die beim Speichern eines Briefs in einer AEM Forms-Umgebung auftreten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: cf06796b-bb8c-4a65-8f42-02fb0cfa3ebd
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: 3f00fc92-85ee-583e-abd1-3bc3d96de3a0
    internal-label: Correspondence Management
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 100%
---
# Correspondence Management: Fehlerbehebung {#correspondence-management-troubleshooting}

## Fehler beim Speichern eines Briefs {#errors-when-saving-a-letter}

### Problem {#issue}

Einer der folgenden Fehler wird beim Speichern eines Briefs angezeigt:

* Datenbindung für das Textmodul nicht vorhanden
* Geben Sie die Eigenschaftsangaben an, die für Folgendes benötigt werden

### Grund {#reason}

Diese Fehler können aus einem der folgenden Gründe auftreten:

* Ein Datenwörterbuch ist mit dem Brief verbunden, ist aber nicht auf dem Server vorhanden.
* Ein Datenwörterbuch ist mit dem Brief verbunden, hat aber einen Unterstrich (_) in seinem Namen.

### Problemumgehung {#workaround}

Vergewissern Sie sich, dass das Datenwörterbuch, das Sie im Brief verwenden, auf dem Server vorhanden ist und keinen Unterstrich (_) im Namen enthält.

## Fehler bei der Briefvorschau {#error-when-previewing-a-letter}

### Problem {#issue-1}

Bei der Vorschau eines Briefs wird der Fehler „Fehler beim Laden des Briefs: Asset konnte nicht aus der XML-Eingabe importiert werden“ angezeigt, selbst wenn ein zuvor unveröffentlichtes Textelement im Brief veröffentlicht wird.

### Problemumgehung {#workaround-1}

Setzen Sie den Brief-Cache für die Veröffentlichungsinstanz zurück, indem Sie folgende Schritte durchführen. Versuchen Sie dann erneut, den Brief anzuzeigen:

1. Navigieren Sie zu **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** und melden Sie sich als Administrator an.
1. Wählen Sie **Correspondence Management-Konfigurationens**.
1. Deaktivieren Sie in **Correspondence Management-Konfigurationen** die Option **Briefcache aktivieren** und klicken Sie auf **Speichern.**
1. Aktivieren Sie **Brief-Cache aktivieren** und klicken Sie dann auf **Speichern**.
1. Versuchen sie noch einmal, den Brief anzuzeigen.
