---
title: Konfigurieren der Umleitungsseite
seo-title: Konfigurieren der Umleitungsseite
description: Nachdem sie ein adaptives Formular ausgefüllt haben, können Benutzer zu einer Webseite umgeleitet werden, die Formularersteller beim Erstellen des Formulars konfigurieren können.
seo-description: Nachdem sie ein adaptives Formular ausgefüllt haben, können Benutzer zu einer Webseite umgeleitet werden, die Formularersteller beim Erstellen des Formulars konfigurieren können.
uuid: f9d304b4-920d-4e50-a674-40eca48c530c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0ffbb4d3-9371-4705-8496-f98e22d9c4a6
docset: aem65
translation-type: tm+mt
source-git-commit: 8e724af4d69cb859537dd088119aaca652ea3931

---


# Konfigurieren der Umleitungsseite{#configuring-redirect-page}

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Senden eines Formulars umgeleitet werden.

1. In the edit mode, select a component, then click ![field-level](assets/field-level.png) > **Adaptive Form Container**, and then click ![cmppr](assets/cmppr.png).

1. Klicken Sie in der Randleiste auf **Senden**.

1. Geben Sie die URL der Umleitungsseite unter der Danksagung im Bereich „Senden“ an.
1. Optional können Sie unter „Übermittlungsaktion“ für die Übermittlungsaktion „An REST-Endpunkt übermitteln“ den Parameter konfigurieren, der zur Umleitungsseite geleitet werden soll.

![Konfigurieren der Umleitungsseite](assets/thank-you-setting-1.png)

Konfigurieren der Umleitungsseite

Formularersteller können folgende Parameter verwenden, die zur Dankeseite weitergeleitet werden. For all the available submit actions, `status` and `owner` parameters are passed. Neben diesen beiden Parametern werden für die folgenden Übermittlungsaktionen einige weitere Parameter weitergeleitet:

* **Aktion** zum Speichern von Inhalten (nicht mehr unterstützt): `contentPath`- der Pfad des Knotens im Repository, in dem die gesendeten Daten gespeichert werden, wird übergeben.

* **PDF-Aktion** speichern (nicht mehr unterstützt): `contentPath`- der gesendeten Daten und des Pfades zu dem Knoten, der die PDF-Datei im Repository speichert - wird weitergeleitet.

* **An Formular-Workflow übermitteln**: Ausgabeparameter, die aus dem Formular-Workflow zurückgegeben wurden, werden weitergeleitet.

* **An REST-Endpunkt übermitteln**: Parameter, die für die Zuordnung feldinterner Werte zu Parametern hinzugefügt wurden, werden weitergeleitet. Die Parameter `status` und `owner` werden bei dieser Übermittlungsaktion nicht weitergeleitet. Weitere Informationen finden Sie unter [Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](../../forms/using/configuring-submit-actions.md). 

