---
title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
seo-title: Strukturierung von Multisite-Management für zielgerichtete Inhalte
description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
seo-description: Im Diagramm ist der Aufbau der Multisite-Unterstützung für zielgerichtete Inhalte dargestellt.
uuid: 2d30cdf0-ab77-490d-aac0-db3a0d417a58
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 7dd851ab-3fa7-426e-89cb-08b67e9b5999
exl-id: d8ba91ff-ad6e-4540-baff-a2c0c764a299
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 100%

---

# Strukturierung von Multisite-Management für zielgerichtete Inhalte{#how-multisite-management-for-targeted-content-is-structured}

Im folgenden Diagramm ist der Aufbau der Multisite-Unterstützung für Targeting-Inhalte dargestellt.

Gebiete werden unter **/content/campaigns/&lt;Marke>** eingeordnet und jede Marke verfügt standardmäßig über ein automatisch erstelltes Master-Gebiet. In jedem Gebiet ist ein eigener Satz Aktivitäten, Erlebnisse und Angebote enthalten.

![chlimage_1-268](assets/chlimage_1-268.png)

Seiten oder Sites können Gebieten zugeordnet werden, sodass sich Targeting-Inhalte nachschlagen lassen. Sollte kein Gebiet konfiguriert sein, bezieht sich AEM für diese Marke auf das Mastergebiet.

Im folgenden Diagramm finden Sie ein Beispiel dafür, wie die Logik im Falle der drei Sites Site1, Site2 und Site3 funktioniert.

![chlimage_1-269](assets/chlimage_1-269.png)

* Site1 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf AnderesGebiet2, basierend auf der Gebietszuordnung.
* Site2 bezieht sich für Marke1 auf MeinGebiet1 und für Marke2 auf das Mastergebiet, da nur für Marke1 Gebiete zugewiesen wurden.
* Site3 bezieht sich für Marke1 und für Marke2 auf das Mastergebiet, weil für diese Site keine Gebietszuordnung vorgenommen wurde.
