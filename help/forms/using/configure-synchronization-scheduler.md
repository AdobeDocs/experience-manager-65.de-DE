---
title: Konfigurieren der Synchronisierungsplanung
description: Erfahren Sie, wie Sie Assets migrieren und synchronisieren, den Synchronisierungs-Scheduler konfigurieren und Ordner zum Anordnen von Assets verwenden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
exl-id: 34db1f76-ee40-4612-85da-22041e7560fb
solution: Experience Manager, Experience Manager Forms
feature: Workbench, Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---

# Konfigurieren der Synchronisierungsplanung {#configuring-the-synchronization-scheduler}

Standardmäßig wird der Synchronisierungs-Scheduler alle 3 Minuten ausgeführt, um sämtliche geänderten und aktualisierten Elemente im Repository über LiveCycle Workbench 11 zu synchronisieren. Anwendungen, die Formulare und Ressourcen enthalten, sind in der AEM Forms-Benutzeroberfläche sichtbar, sobald der Synchronisierungsprozess abgeschlossen ist.

## Ändern des Intervalls für den Synchronisierungs-Scheduler {#change-interval-of-the-synchronization-scheduler}

Führen Sie die folgenden Schritte aus, um das Intervall für den Synchronisierungs-Scheduler zu ändern:

1. Melden Sie sich bei AEM Configuration Manager an. Die URL des Configuration Managers lautet `https://'[server]:[port]'/lc/system/console/configMgr`

1. Suchen Sie das Bundle **FormsManagerConfiguration** und öffnen Sie es.

1. Geben Sie für die Option **Häufigkeit für Synchronisierungs-Scheduler** einen neuen Wert an.

   Die Einheit für die Frequenz ist Minuten. Um den Scheduler beispielsweise so zu konfigurieren, dass er alle 60 Minuten ausgeführt wird, geben Sie „60“ ein.

## Synchronisieren von Assets {#synchronizing-assets}

Sie können die Option **Assets aus Repository synchronisieren** verwenden, um die Elemente manuell zu synchronisieren. Führen Sie die folgenden Schritte aus, um die Assets manuell zu synchronisieren:

1. Melden Sie sich bei AEM Forms an. Die Standardeinstellung ist `https://'[server]:[port]'/lc/aem/forms/`.

   ![AEM Forms-Benutzeroberfläche](assets/aem_forms_ui.png)

   **Abbildung:** *Benutzeroberfläche von AEM Forms*

1. Klicken Sie auf das Symbol ![aem6forms_sync](assets/aem6forms_sync.png) in der Symbolleiste. Wenn im zuletzt konfigurierten Pfad keine Elemente vorhanden sind, wird das nachfolgende Dialogfeld angezeigt. Klicken Sie auf **Start**, um die Synchronisierung zu starten.

   ![Das Dialogfeld „Synchronisierung“](assets/migrate-and-syncronize.png)

   **Abbildung:** *Dialogfeld „Synchronisierung“*

## Fehlerbehebung bei Synchronisierungsfehlern {#troubleshooting-synchronization-error}

Sie können neue Anwendungen im Workflow Designer (LiveCycle Workbench) erstellen.

Wenn eine neu erstellte Anwendung und ein Ordner unter /content/dam/formsanddocuments identische Namen haben, wird der Fehler „*Ein Element mit demselben Namen wie diese Anwendung ist bereits auf der Stammebene vorhanden.*“ protokolliert. 

Benennen Sie zum Beheben des Konflikts die Anwendung um und synchronisieren Sie die Elemente manuell.

![Das Dialogfeld „Konflikte bei der Synchronisierung von Elementen“](assets/sync-conflict.png)

**Abbildung:** *Dialogfeld „Konflikte bei der Synchronisierung von Elementen“*
