---
title: '„Correspondence Management: Fehlerbehebung“'
description: Erfahren Sie, wie Sie Fehler beheben können, die beim Speichern eines Briefs in einer AEM Forms-Umgebung auftreten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: cf06796b-bb8c-4a65-8f42-02fb0cfa3ebd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '217'
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

Setzen Sie den Brief-Cache für die Veröffentlichungs-Instanz zurück, indem Sie folgende Schritte durchführen. Versuchen Sie dann erneut, den Brief anzuzeigen:

1. Navigieren Sie zu **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** und melden Sie sich als Administrator an.
1. Wählen Sie **Correspondence Management-Konfigurationens**.
1. Deaktivieren Sie in **Correspondence Management-Konfigurationen** die Option **Briefcache aktivieren** und klicken Sie auf **Speichern.**
1. Aktivieren Sie **Brief-Cache aktivieren** und klicken Sie dann auf **Speichern**.
1. Versuchen sie noch einmal, den Brief anzuzeigen.
