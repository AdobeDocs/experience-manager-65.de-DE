---
title: Entwicklermodus
description: Der Entwicklermodus öffnet ein seitliches Bedienfeld mit mehreren Registerkarten, die Entwicklern Informationen über die aktuelle Seite bereitstellen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
exl-id: aef0350f-4d3d-47f4-9c7e-5675efef65d9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 71%

---

# Entwicklermodus{#developer-mode}

Beim Bearbeiten von Seiten in Adobe Experience Manager (AEM) werden mehrere [Modi](/help/sites-authoring/author-environment-tools.md#modestouchoptimizedui) verfügbar sind, einschließlich des Entwicklermodus. Dadurch wird ein seitliches Bedienfeld mit mehreren Registerkarten geöffnet, über die Entwickler Informationen zur aktuellen Seite erhalten. Die drei Registerkarten sind:

* **[Komponenten](#components)** zum Anzeigen von Struktur- und Leistungsinformationen.
* **[Tests](#tests)** für die Durchführung von Tests und die Analyse der Ergebnisse.
* **[Fehler](#errors)** um alle auftretenden Probleme zu sehen.

Diese Informationen unterstützen Entwickler bei Folgendem:

* Identifizieren, woraus sich die Seiten zusammensetzen.
* Debuggen Sie, was an welcher Stelle und zu welchem Zeitpunkt geschieht und wie Probleme gelöst werden können.
* Testen, ob sich die Anwendung erwartungsgemäß verhält.

>[!CAUTION]
>
>Entwicklermodus:
>
>* Ist nur in der Touch-optimierten Benutzeroberfläche verfügbar (beim Bearbeiten von Seiten).
>* Der Modus ist (aufgrund von Größenbeschränkungen) nicht auf mobilen Geräten oder in kleinen Desktop-Fenstern verfügbar.
>
>   * Dies gilt bei einer Breite von weniger als 1024 Pixel.
>* Ist nur für Benutzer verfügbar, die Mitglieder der Gruppe `administrators` sind.

>[!CAUTION]
>
>Der Entwicklermodus ist nur für eine Standard-Authoring-Instanz verfügbar, die nicht den Ausführungsmodus „nosamplecontent“ verwendet.
>
>Bei Bedarf kann er für die Verwendung konfiguriert werden:
>
>* auf einer Autoreninstanz mit dem Ausführungsmodus „nosamplecontent“
>* auf einer Veröffentlichungsinstanz
>
>Der Modus sollte nach der Verwendung wieder deaktiviert werden.

>[!NOTE]
>
>Siehe:
>
>* Knowledgebase-Artikel zum [Beheben von Fehlern in der Touch-optimierten AEM-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/kb/troubleshooting-aem-touchui-issues.html) für weitere Tipps und Tools.
>* AEM-Gems-Sitzung [AEM 6.0 Entwicklermodus](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2014/aem-developer-mode.html).
>

## Öffnen des Entwicklermodus {#opening-developer-mode}

Der Entwicklermodus ist als Seitenbereich im Seiten-Editor implementiert. Um den Bereich zu öffnen, wählen Sie in der Symbolleiste des Seiten-Editors aus der Modusauswahl die Option **Entwickler** aus:

![chlimage_1-11](assets/chlimage_1-11.png)

Der Bereich ist in zwei Registerkarten unterteilt:

* **[Komponenten](/help/sites-developing/developer-mode.md#components)** – Hier sehen Sie die Komponentenstruktur, die der [Inhaltsstruktur](/help/sites-authoring/author-environment-tools.md#content-tree) für Autoren ähnelt.

* **[Fehler](/help/sites-developing/developer-mode.md#errors)** – Wenn ein Problem auftritt, werden hier die Details für die jeweilige Komponente angezeigt.

### Komponenten {#components}

![chlimage_1-12](assets/chlimage_1-12.png)

Diese Registerkarte enthält eine Komponentenstruktur mit folgenden Attributen:

* Erläutert die Kette von Komponenten und Vorlagen, die auf der Seite gerendert werden (SLY, JSP usw.). Die Struktur kann erweitert werden, sodass sie Kontext innerhalb der Hierarchie anzeigt.
* Zeigt die Server-seitige Berechnungszeit zum Rendern der Komponente an.
* Ermöglicht das Erweitern der Baumstruktur und Auswählen bestimmter Komponenten innerhalb der Baumstruktur. Die Auswahl bietet Zugriff auf Komponentendetails, z. B.:

   * Repository-Pfad
   * Links zu den Skripten (Zugriff über CRXDE Lite)

* Die ausgewählten Komponenten (im Inhaltsfluss durch einen blauen Rahmen gekennzeichnet) werden in der Inhaltsstruktur hervorgehoben (und umgekehrt).

Dies kann Folgendes erleichtern:

* Bestimmen und Vergleichen der Render-Zeit nach Komponente
* Anzeigen und Verstehen der Hierarchie
* Verstehen und Verbessern der Seitenladezeit durch Identifizieren langsamer Komponenten

Jeder Komponenteneintrag kann (z. B.) Folgendes beinhalten:

![chlimage_1-13](assets/chlimage_1-13.png)

* **Details anzeigen**: Ein Link zu einer Liste, die Folgendes enthält:

   * Alle zum Rendern der Komponente verwendeten Komponentenskripte
   * Den Repository-Inhaltspfad für diese spezifische Komponente

  ![chlimage_1-14](assets/chlimage_1-14.png)

* **Skript bearbeiten**: ein Link, der

   * das Komponentenskript in CRXDE Lite öffnet.

* Wenn Sie einen Komponenteneintrag erweitern (Pfeilspitze), kann außerdem Folgendes angezeigt werden:

   * Die Hierarchie innerhalb der ausgewählten Komponente.
   * Die Render-Zeiten nur für die ausgewählte Komponente, für einzelne darin verschachtelte Komponenten und für alle Komponenten insgesamt.

  ![chlimage_1-15](assets/chlimage_1-15.png)

>[!CAUTION]
>
>Einige Links zeigen auf das Skript unter `/libs`. Diese sind allerdings nur für Referenzzwecke bestimmt. Sie dürfen **keine** Elemente unter `/libs` bearbeiten, da von Ihnen gemachte Änderungen möglicherweise verloren gehen. Dies liegt daran, dass sich diese Verzweigung bei jedem Upgrade oder Anwenden eines Hotfixes oder Feature Packs ändern kann. Nehmen Sie die erforderlichen Änderungen unter `/apps`. Siehe [Überlagerungen und Überschreibungen](/help/sites-developing/overlays.md).

### Fehler {#errors}

![chlimage_1-16](assets/chlimage_1-16.png)

Zwar ist zu hoffen, dass die Registerkarte **Fehler** niemals Daten anzeigt (wie oben), falls jedoch Probleme auftreten, werden zur jeweiligen Komponente folgende Details angezeigt:

* Eine Warnung, falls die Komponente einen Eintrag in das Fehlerprotokoll schreibt, und Details zum Fehler sowie direkte Links zum entsprechenden Code in CRXDE Lite.
* Eine Warnung, falls die Komponente eine Admin-Sitzung öffnet.

Wenn beispielsweise eine nicht definierte Methode aufgerufen wird, wird der resultierende Fehler im **Fehler** tab:

![chlimage_1-17](assets/chlimage_1-17.png)

Der Komponenteneintrag in der Struktur auf der Registerkarte „Komponenten“ wird ebenfalls entsprechend markiert, wenn ein Fehler auftritt.

### Tests {#tests}

>[!CAUTION]
>
>In AEM 6.2 wurden die Testfunktionen des Entwicklermodus als eigenständige Tools-Anwendung neu implementiert.
>
>Ausführliche Informationen finden Sie unter [Testen der Benutzeroberfläche](/help/sites-developing/hobbes.md).
