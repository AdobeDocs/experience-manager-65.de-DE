---
title: Entwicklermodus
seo-title: Developer Mode
description: Der Entwicklermodus öffnet ein seitliches Bedienfeld mit mehreren Registerkarten, die Entwicklern Informationen zur aktuellen Seite bereitstellen
seo-description: Developer mode opens a side panel with several tabs that provide a developer with infomation about the current page
uuid: 8301ab51-93d6-44f9-a813-ba7f03f54485
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 589e3a83-7d1a-43fd-98b7-3b947122829d
docset: aem65
exl-id: aef0350f-4d3d-47f4-9c7e-5675efef65d9
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 57%

---

# Entwicklermodus{#developer-mode}

Beim Bearbeiten von Seiten in AEM sind diverse [Modi](/help/sites-authoring/author-environment-tools.md#modestouchoptimizedui) verfügbar, u. a. auch der Entwicklermodus. Dadurch wird ein seitliches Bedienfeld mit mehreren Registerkarten geöffnet, die Entwicklern Informationen über die aktuelle Seite bereitstellen. Die drei Registerkarten sind:

* **[Komponenten](#components)** zur Anzeige von Struktur- und Leistungsinformationen.
* **[Tests](#tests)** für die Durchführung von Tests und die Analyse der Ergebnisse.
* **[Fehler](#errors)** um eventuelle Probleme zu erkennen.

Diese Informationen unterstützen Entwickler bei Folgendem:

* Discover: woraus Seiten bestehen.
* Debuggen Sie, was an welcher Stelle und zu welchem Zeitpunkt geschieht und wie Probleme gelöst werden können.
* Test: verhält sich die Anwendung erwartungsgemäß.

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
>Der Entwicklermodus ist nur für eine Standard-Autoreninstanz verfügbar, die nicht den Ausführungsmodus nosamplecontent verwendet.
>
>Bei Bedarf kann sie für die Verwendung konfiguriert werden:
>
>* auf einer Autoreninstanz mit dem Ausführungsmodus „nosamplecontent“
>* auf einer Veröffentlichungsinstanz
>
>Der Modus sollte nach der Verwendung wieder deaktiviert werden.

>[!NOTE]
>
>Siehe:
>
>* Knowledge Base-Artikel, [Fehlerbehebung AEM TouchUI-Probleme](https://helpx.adobe.com/de/experience-manager/kb/troubleshooting-aem-touchui-issues.html), um weitere Tipps und Tools zu erhalten.
>* AEM Gems-Sitzung [AEM 6.0 Entwicklermodus](https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2014/aem-developer-mode.html?lang=en).
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
* Zeigt die Server-seitige Verarbeitungszeit, die zum Rendern der Komponente benötigt wird.
* Sie können die Struktur erweitern und spezifische Komponenten innerhalb der Struktur auswählen. Die Auswahl bietet Zugriff auf Komponentendetails, z. B.:

   * Repository-Pfad
   * Links zu den Skripten (Zugriff über CRXDE Lite)

* Die ausgewählten Komponenten (im Inhaltsfluss, durch einen blauen Rahmen gekennzeichnet) werden in der Inhaltsstruktur hervorgehoben (und umgekehrt).

Dies kann dazu beitragen,

* Bestimmen und Vergleichen der Render-Zeit nach Komponente
* Anzeigen und Verstehen der Hierarchie
* Verstehen und Verbessern der Seitenladezeit durch Identifizieren langsamer Komponenten

Jeder Komponenteneintrag kann Folgendes anzeigen (z. B.:

![chlimage_1-13](assets/chlimage_1-13.png)

* **Details anzeigen**: einen Link zu einer Liste, die Folgendes anzeigt:

   * alle Komponentenskripte, die zum Rendern der Komponente verwendet werden.
   * den Repository-Inhaltspfad für diese spezifische Komponente.

   ![chlimage_1-14](assets/chlimage_1-14.png)

* **Skript bearbeiten**: einen Link, der

   * öffnet das Komponentenskript in CRXDE Lite.

* Das Erweitern eines Komponenteneintrags (Pfeilspitze) kann auch Folgendes anzeigen:

   * Die Hierarchie innerhalb der ausgewählten Komponente.
   * Die Render-Zeiten nur für die ausgewählte Komponente, für einzelne darin verschachtelte Komponenten und für alle Komponenten insgesamt.

   ![chlimage_1-15](assets/chlimage_1-15.png)

>[!CAUTION]
>
>Einige Links zeigen auf das Skript unter `/libs`. Diese sind allerdings nur für Referenzzwecke bestimmt. Sie dürfen **keine** Elemente unter `/libs` bearbeiten, da von Ihnen gemachte Änderungen möglicherweise verloren gehen. Grund dafür ist, dass diese Verzweigung jedes Mal geändert wird, wenn Sie ein Upgrade durchführen oder ein Hotfix/Feature Pack anwenden. Alle erforderlichen Änderungen sollten unter `/apps` erfolgen. Weitere Informationen hierzu finden Sie in [Überlagerungen und Überschreibungen](/help/sites-developing/overlays.md).

### Fehler {#errors}

![chlimage_1-16](assets/chlimage_1-16.png)

Zwar ist zu hoffen, dass die Registerkarte **Fehler** niemals Daten anzeigt (wie oben), falls jedoch Probleme auftreten, werden zur jeweiligen Komponente folgende Details angezeigt:

* Eine Warnung, falls die Komponente einen Eintrag in das Fehlerprotokoll schreibt, und Details zum Fehler sowie direkte Links zum entsprechenden Code in CRXDE Lite.
* Eine Warnung, falls die Komponente eine Admin-Sitzung öffnet.

Wenn beispielsweise eine nicht definierte Methode aufgerufen wird, wird der resultierende Fehler im **Fehler** tab:

![chlimage_1-17](assets/chlimage_1-17.png)

Der Komponenteneintrag in der Baumstruktur der Registerkarte &quot;Komponenten&quot;wird ebenfalls mit einem Indikator markiert, wenn ein Fehler auftritt.

### Tests {#tests}

>[!CAUTION]
>
>In AEM 6.2 wurden die Testfunktionen des Entwicklermodus als eigenständige Tools-Anwendung neu implementiert.
>
>Ausführliche Informationen finden Sie in [Testen der Benutzeroberfläche](/help/sites-developing/hobbes.md).
