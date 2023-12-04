---
title: Integrieren mit BrightEdge Content Optimizer
seo-title: Integrating with BrightEdge Content Optimizer
description: Erfahren Sie mehr über die Integration von AEM mit BrightEdge Content Optimizer.
seo-description: Learn about integrating AEM with BrightEdge Content Optimizer.
uuid: 7075dd3c-2fd6-4050-af1c-9b16ad4366ec
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: cf25c9a8-0555-4c67-8aa5-55984fd8d301
exl-id: f14cc5fd-aeab-4619-b926-b6f1df7e50e5
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 9%

---

# Integrieren mit BrightEdge Content Optimizer{#integrating-with-brightedge-content-optimizer}

Erstellen Sie eine BrightEdge-Cloud-Konfiguration, damit AEM über die Anmeldedaten Ihres BrightEdge-Kontos eine Verbindung herstellen können. Sie können mehrere Konfigurationen erstellen, wenn Sie mehrere Konten verwenden.

Wenn Sie die Konfiguration erstellen, geben Sie einen Titel an. Der Titel sollte beschreibend sein, damit Benutzer die Konfiguration mit dem BrightEdge-Konto korrelieren können. Wenn ein Seitenautor oder -administrator eine Webseite mit dem BrightEdge-Konto verknüpft, wird dieser Titel in einer Dropdown-Liste angezeigt.

1. Klicken Sie auf der Leiste auf Tools > Vorgänge > Cloud > Cloud Service.
1. Klicken Sie auf den Link, der im Abschnitt BrightEdge Content Optimizer angezeigt wird. Ob eine BrightEdge-Konfiguration erstellt wurde, bestimmt den Link-Text:

   * Jetzt konfigurieren: Dieser Link wird angezeigt, wenn keine Konfiguration erstellt wurde.
   * Konfigurationen anzeigen: Dieser Link wird angezeigt, wenn eine oder mehrere Konfigurationen erstellt wurden.

   ![chlimage_1-4](assets/chlimage_1-4a.png)

1. Wenn Sie auf Konfigurationen anzeigen geklickt haben, klicken Sie auf den Link + neben Verfügbare Konfigurationen.
1. Geben Sie einen Titel für die Konfiguration ein. Geben Sie optional einen Namen für den Knoten ein, der zum Speichern der Konfiguration im Repository verwendet wird. Klicken Sie auf „Erstellen“.
1. Geben Sie im Dialogfeld &quot;Konfiguration des BrightEdge Content Optimizer&quot;den Benutzernamen und das Kennwort des BrightEdge-Kontos ein und klicken Sie auf &quot;OK&quot;.

## Bearbeiten einer BrightEdge-Konfiguration {#editing-a-brightedge-configuration}

Ändern Sie bei Bedarf den Benutzernamen und das Kennwort einer BrightEdge-Konfiguration. Die Änderungen betreffen alle Seiten, die die Konfiguration verwenden.

1. Klicken Sie auf der Leiste auf Tools > Vorgänge > Cloud > Cloud Service.
1. Klicken Sie im Abschnitt &quot;BrightEdge Content Optimizer&quot;auf Konfigurationen anzeigen .

   ![chlimage_1-5](assets/chlimage_1-5a.png)

1. Klicken Sie auf den Namen der Konfiguration, die Sie bearbeiten möchten.
1. Klicken Sie auf &quot;Bearbeiten&quot;, ändern Sie die Eigenschaftswerte und klicken Sie auf &quot;OK&quot;.

## Verknüpfen von Seiten mit einer BrightEdge-Konfiguration {#associating-pages-with-a-brightedge-configuration}

Verknüpfen Sie Seiten mit einer BrightEdge-Konfiguration, um Seitendaten zur Analyse an den BrightEdge-Dienst zu senden. Wenn Sie eine Seite mit einer Konfiguration verknüpfen, übernehmen die untergeordneten Seiten die Zuordnung. In der Regel verknüpfen Sie die Startseite Ihrer Site so, dass Daten von allen Seiten an BrightEdge gesendet werden.

1. Öffnen Sie die klassische Websites-Konsole. ([http://localhost:4502/siteadmin#/content](http://localhost:4502/siteadmin#/content))
1. Wählen Sie in der Website-Struktur den Ordner oder die Seite aus, der/die die Seite enthält, die Sie mit der BrightEdge-Konfiguration verknüpfen möchten.
1. Klicken Sie in der Liste der Seiten mit der rechten Maustaste auf die zu konfigurierende Seite und klicken Sie auf Eigenschaften.
1. Klicken Sie auf der Registerkarte &quot;Cloud Service&quot;auf die Schaltfläche &quot;Dienst hinzufügen&quot;, wählen Sie im Dialogfeld &quot;Cloud Service&quot;die Option &quot;BrightEdge Content Optimizer&quot;und klicken Sie dann auf &quot;OK&quot;.
1. Wählen Sie in der Liste &quot;BrightEdge Content Optimizer&quot;die BrightEdge-Konfiguration aus, die mit der Seite verknüpft werden soll, und klicken Sie dann auf &quot;OK&quot;.

   ![chlimage_1-6](assets/chlimage_1-6a.png)

## Aktivieren einer BrightEdge-Konfiguration {#activating-a-brightedge-configuration}

Aktivieren Sie eine BrightEdge-Konfiguration, um sie in der Veröffentlichungsinstanz zu replizieren und veröffentlichte Seiten für die Interaktion mit dem BrightEdge-Dienst zu aktivieren.

1. Klicken Sie in der Leiste auf Sites , navigieren Sie zu der Seite, die Sie mit der BrightEdge-Konfiguration verknüpft haben, und wählen Sie sie aus.
1. Klicken Sie auf das Symbol Veröffentlichen und dann auf Veröffentlichen .

   ![chlimage_1-7](assets/chlimage_1-7a.png)

1. Überprüfen Sie, ob in der angezeigten Liste der Konfigurationen Ihre BrightEdge-Konfiguration ausgewählt ist, und klicken Sie dann auf „Veröffentlichen“.

   ![chlimage_1-8](assets/chlimage_1-8a.png)
