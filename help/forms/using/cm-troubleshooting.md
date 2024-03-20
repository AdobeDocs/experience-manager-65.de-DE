---
title: "Correspondence Management: Fehlerbehebung"
description: Erfahren Sie, wie Sie Fehler beheben können, die beim Speichern eines Briefs in einer AEM Forms-Umgebung auftreten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
exl-id: cf06796b-bb8c-4a65-8f42-02fb0cfa3ebd
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 17%

---

# Correspondence Management: Fehlerbehebung {#correspondence-management-troubleshooting}

## Fehler beim Speichern eines Briefs {#errors-when-saving-a-letter}

### Problem {#issue}

Einer der folgenden Fehler wird beim Speichern eines Briefs angezeigt:

* Datenbindung für das Textmodul nicht vorhanden
* Geben Sie die für Folgendes erforderlichen Eigenschaftsinformationen an

### Grund {#reason}

Diese Fehler können aus einem der folgenden Gründe auftreten:

* Ein Datenwörterbuch ist an den Brief gebunden, aber nicht auf dem Server vorhanden.
* Ein Datenwörterbuch ist an den Brief gebunden, hat jedoch einen Unterstrich (_) in seinem Namen.

### Problemumgehung {#workaround}

Stellen Sie sicher, dass das Datenwörterbuch, das Sie im Brief verwenden, auf dem Server vorhanden ist und keinen Unterstrich (_) im Namen enthält.

## Fehler bei der Briefvorschau {#error-when-previewing-a-letter}

### Problem {#issue-1}

Bei der Vorschau eines Briefs wird der Fehler &quot;Fehler beim Laden des Briefs: Asset konnte nicht aus der XML-Eingabe importiert werden&quot;angezeigt, selbst wenn ein zuvor unveröffentlichtes Textelement im Brief veröffentlicht wird.

### Problemumgehung {#workaround-1}

Setzen Sie den Brief-Cache auf der Veröffentlichungsinstanz mit den folgenden Schritten zurück und versuchen Sie dann erneut, den Brief anzuzeigen:

1. Navigieren Sie zu **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** und melden Sie sich als Administrator an.
1. Wählen Sie **Correspondence Management-Konfigurationens**.
1. Deaktivieren Sie in **Correspondence Management-Konfigurationen** die Option **Briefcache aktivieren** und klicken Sie auf **Speichern.**
1. Überprüfen **Briefcache aktivieren** und klicken Sie anschließend auf **Speichern**.
1. Versuchen sie noch einmal, den Brief anzuzeigen.
