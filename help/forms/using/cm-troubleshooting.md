---
title: '"Correspondence Management: Fehlerbehebung"'
seo-title: Correspondence Management - Fehlerbehebung
description: Correspondence Management - Fehlerbehebung
seo-description: Correspondence Management - Fehlerbehebung
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Korrespondenzverwaltung
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 90%

---


# Correspondence Management: Fehlerbehebung {#correspondence-management-troubleshooting}

## Fehler beim Speichern eines Briefs {#errors-when-saving-a-letter}

### Problem {#issue}

Einer der folgenden Fehler wird angezeigt, wenn ein Brief gespeichert wird:

* Datenbindung für das Textmodul nicht vorhanden
* Geben Sie die Eigenschaftsangaben an, die für Folgendes benötigt werden

### Grund {#reason}

Diese Fehler können aus folgendem Grund auftreten:

* Ein Datenwörterbuch ist mit dem Brief verbunden, ist aber nicht auf dem Server vorhanden.
* Ein Datenwörterbuch ist mit dem Brief verbunden, hat aber einen Unterstrich (_) in seinem Namen.

### Problemumgehung {#workaround}

Vergewissern Sie sich, dass das Datenwörterbuch, das Sie im Brief verwenden, auf dem Server vorhanden ist und keinen Unterstrich (_) im Namen enthält.

## Fehler bei der Vorschau eines Briefs {#error-when-previewing-a-letter}

### Problem {#issue-1}

Bei der Vorschau eines Briefs wird, selbst wenn ein zuvor unveröffentlichtes Textelement im Brief veröffentlicht wird, der folgende Fehler angezeigt: „Fehler beim Laden des Briefs: Asset konnte nicht aus der XML-Eingabe importiert werden“.

### Problemumgehung {#workaround-1}

Setzen Sie den Brief-Cache für die Veröffentlichungs-Instanz zurück, indem Sie folgende Schritten durchführen. Versuchen Sie dann erneut den Brief anzuzeigen:

1. Gehen Sie zu **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** und melden Sie sich als Administrator an.
1. Wählen Sie **Correspondence Management-Konfigurationen**.
1. Deaktivieren Sie in **Correspondence Management-Konfigurationen** die Option **Briefcache aktivieren** und klicken Sie auf **Speichern.**
1. Aktivieren Sie **Brief-Cache aktivieren** und klicken Sie dann auf **Speichern**.
1. Versuchen sie noch einmal, den Brief anzuzeigen.

