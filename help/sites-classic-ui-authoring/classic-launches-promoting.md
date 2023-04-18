---
title: Weiterleiten von Launches
description: Sie müssen Launch-Seiten weiterleiten, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert.
uuid: 91f1c6ac-8c4e-4459-aaab-feaa32befc45
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8d38c6f7-8fea-4d27-992d-03b604b9541f
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 3013adc3-bec6-4ecc-aefd-f8df2b86dfef
source-git-commit: f4b6eb2ded17ec641f23a1fc3b977ce77169c8a1
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 42%

---

# Weiterleiten von Launches{#promoting-launches}

Sie müssen Launch-Seiten weiterleiten, damit der Inhalt vor der Veröffentlichung wieder in die Quelle (Produktion) verschoben wird. Beim Weiterleiten einer Launch-Seite wird die entsprechende Seite der Quellseiten mit dem Inhalt der weitergeleiteten Seite aktualisiert. Beim Anzeigen einer Launch-Seite stehen die folgenden Optionen zur Verfügung:

* Gibt an, ob nur die aktuelle Seite oder der gesamte Launch weitergeleitet werden soll.
* Gibt an, ob die untergeordneten Seiten der aktuellen Seite weitergeleitet werden sollen.
* Ob der vollständige Launch weitergeleitet werden soll oder nur Seiten, die geändert wurden.

## Weiterleiten von Launch-Seiten {#promoting-launch-pages}

Um Seiten weiterzuleiten, führen Sie beim Bearbeiten der Launch-Seite, die Sie weiterleiten möchten, die folgenden Schritte aus:

1. Im **Seite** Registerkarte im Sidekick auf **Launch bewerben**.
1. Geben Sie die zu bewertenden Seiten an:

   * (Standard) Um nur die aktuelle Seite weiterzuleiten, wählen Sie **Änderungen an der Seite in Produktionsversion weiterleiten** aus.
   * Um auch die untergeordneten Seiten der aktuellen Seite weiterzuleiten, wählen Sie **Unterseiten einschließen** aus.
   * Um alle Seiten im Launch weiterzuleiten, wählen Sie **Vollständigen Launch zur Produktionsversion weiterleiten**.

1. Um die Produktionsseiten einem Workflow-Paket hinzuzufügen, wählen Sie **Hinzufügen zum Workflow-Paket** und wählen Sie dann das Workflow-Paket aus.
1. Klicken **Bewerben**.

## Bearbeiten weitergeleiteter Seiten mit einem AEM-Workflow {#processing-promoted-pages-using-aem-workflow}

Verwenden Sie Workflow-Modelle, um eine Massenverarbeitung von beworbenen Launches-Seiten durchzuführen:

1. Erstellen Sie ein Workflow-Paket.
1. Wenn Autoren Launch-Seiten weiterleiten, speichern sie sie im Workflow-Paket.
1. Starten Sie ein Workflow-Modell mit dem -Paket als Payload.

So starten Sie einen Workflow automatisch, wenn Seiten weitergeleitet werden: [Konfigurieren eines Workflow-Starters](/help/sites-administering/workflows-starting.md#workflows-launchers) für den Paketknoten.

Sie können z. B. automatisch Seitenaktivierungsanfragen generieren, wenn Autoren Launches-Seiten weiterleiten. Konfigurieren Sie einen Workflow-Starter, um den Workflow Anforderungsaktivierung zu starten, wenn der Paketknoten geändert wird.

![chlimage_1-136](assets/chlimage_1-136.png)
