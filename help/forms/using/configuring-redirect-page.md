---
title: Konfigurieren einer Umleitungsseite
seo-title: Configuring redirect page
description: Nachdem sie ein adaptives Formular ausgefüllt haben, können Benutzer zu einer Webseite umgeleitet werden, die Formularersteller beim Erstellen des Formulars konfigurieren können.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: f9d304b4-920d-4e50-a674-40eca48c530c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0ffbb4d3-9371-4705-8496-f98e22d9c4a6
docset: aem65
feature: Adaptive Forms
exl-id: be1a774f-5681-443f-b195-28e89a020547
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 100%

---

# Konfigurieren einer Umleitungsseite{#configuring-redirect-page}

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Absenden eines Formulars umgeleitet werden.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, klicken Sie dann auf ![field-level](assets/field-level.png) > **Container für ein adaptives Formular** und anschließend auf ![cmppr](assets/cmppr.png).

1. Klicken Sie in der Seitenleiste auf **Übermittlung**.

1. Geben Sie die URL der Umleitungsseite unter der Danksagung im Bereich „Senden“ an.
1. Optional können Sie unter „Übermittlungsaktion“ für die Aktion „An REST-Endpunkt übermitteln“ den Parameter konfigurieren, der zur Umleitungsseite weitergeleitet wird.

![Konfigurieren der Umleitungsseite](assets/thank-you-setting-1.png)

Konfigurieren der Umleitungsseite

Formularersteller können folgende Parameter verwenden, die zur Dankeseite weitergeleitet werden. Bei allen verfügbaren Übermittlungsaktionen werden `status`- und `owner`-Parameter übergeben. Neben diesen beiden Parametern werden für die folgenden Übermittlungsaktionen einige weitere Parameter weitergeleitet:

* **Aktion für Inhaltsspeicherung** (veraltet): `contentPath` – der Pfad des Knotens im Repository, in dem gesendete Daten gespeichert werden – wird weitergeleitet.

* **Aktion zum Speichern einer PDF** (veraltet): `contentPath` – die gesendeten Daten und der Pfad des Knoten im Repository, in dem die PDF-Datei gespeichert wird, werden weitergeleitet.

* **An Formular-Workflow übermitteln**: Ausgabeparameter, die aus dem Formular-Workflow zurückgegeben wurden, werden weitergeleitet.

* **An REST-Endpunkt übermitteln**: Parameter, die für die Zuordnung feldinterner Werte zu Parametern hinzugefügt wurden, werden weitergeleitet. Die Parameter `status` und `owner` werden bei dieser Übermittlungsaktion nicht weitergeleitet. Weitere Informationen finden Sie unter [Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](../../forms/using/configuring-submit-actions.md). 
