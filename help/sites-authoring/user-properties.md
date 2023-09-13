---
title: Konfigurieren der Kontoumgebung
description: AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: 6079431d-7d08-4973-8bb4-a8d10626a795
source-git-commit: 474a726058b141985f52a0faec6161a34be1e9dc
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 57%

---

# Konfigurieren der Kontoumgebung{#configuring-your-account-environment}

AEM bietet Ihnen die Möglichkeit, Ihr Konto und bestimmte Aspekte der Autorenumgebung zu konfigurieren.

Mit der Option [Benutzer](/help/sites-authoring/user-properties.md#user-settings) in der [Kopfzeile](/help/sites-authoring/basic-handling.md#the-header) und dem verbundenen Dialogfeld [Benutzereinstellungen](#userpreferences) können Sie Benutzeroptionen bearbeiten.

Beginnen Sie, indem Sie in der Kopfzeile die Option [Benutzer](/help/sites-authoring/user-properties.md#user-settings) aufrufen.

## Benutzereinstellungen {#user-settings}

Die **Benutzer** Über das Dialogfeld &quot;Einstellungen&quot;haben Sie Zugriff auf:

* Identität annehmen als

   * Mit dem [Identität annehmen als](/help/sites-administering/security.md#impersonating-another-user) -Funktion kann ein Benutzer im Namen eines anderen Benutzers arbeiten.

* Profil

   * Über das Profil kann bequem über einen Link auf [Benutzereinstellungen](/help/sites-administering/security.md) zugegriffen werden.

* [Benutzereinstellungen](/help/sites-authoring/user-properties.md#my-preferences)

   * Hier können verschiedene auf den jeweiligen Benutzer zugeschnittene Einstellungen festgelegt werden.

![screen_shot_2018-03-20at103808](assets/screen_shot_2018-03-20at103808.png)

### Benutzereinstellungen {#my-preferences}

Auf das Dialogfeld **Benutzereinstellungen** kann über die Option [Benutzer](/help/sites-authoring/user-properties.md#user-settings) in der Kopfzeile zugegriffen werden.

Jeder Benutzer kann bestimmte Eigenschaften für sich selbst festlegen.

![screen-shot_2019-03-05at100322](assets/screen-shot_2019-03-05at100322.png)

* **Sprache**

  Dadurch wird die Sprache definiert, die für die Benutzeroberfläche der Authoring-Umgebung verwendet werden soll. Wählen Sie in der Liste die gewünschte Sprache aus.

  Diese Konfiguration wird auch für die klassische Benutzeroberfläche verwendet.

* **Fensterverwaltung**

  Dies definiert das Verhalten oder das Öffnen von Fenstern. Wählen Sie eine der folgenden beiden Optionen aus:

   * **Mehrere Fenster** (Standard)

      * Seiten werden in einem neuen Fenster geöffnet.

   * **Einfaches Fenster**

      * Seiten werden im aktuellen Fenster geöffnet.

* **Desktop-Aktionen für Assets anzeigen**

  Für diese Option ist ein AEM Desktop-Programm erforderlich.

* **Anmerkungsfarbe**

  Dadurch wird die Standardfarbe definiert, die beim Erstellen von Anmerkungen verwendet wird.

   * Klicken Sie auf den Farbblock, damit Sie die Musterauswahl öffnen und eine Farbe auswählen können.
   * Alternativ dazu können Sie in das Feld den Hexcode für die gewünschte Farbe eingeben.

* **Darstellung des relativen Datums**

  Um die Lesbarkeit zu verbessern, rendert AEM Datumsangaben innerhalb der letzten sieben Tage als relative Daten (z. B. vor drei Tagen) und ältere Daten als exakte Datumswerte (z. B. 20. März 2017).

  Diese Option definiert, wie Daten im System angezeigt werden. Die folgenden Optionen sind verfügbar:

   * **Immer exaktes Datum anzeigen**: Es wird immer das genaue Datum angezeigt (niemals ein relatives Datum).
   * **1 Tag**: Das relative Datum wird für Datumsangaben innerhalb eines Tages angezeigt; ansonsten wird das genaue Datum angegeben.

   * **7 Tage (Standard)**: Das relative Datum wird für Datumsangaben innerhalb eines Zeitraums von sieben Tages angezeigt; ansonsten wird das genaue Datum angegeben.

   * **1 Monat**: Das relative Datum wird für Datumsangaben innerhalb eines Monats angezeigt; ansonsten wird das genaue Datum angegeben.

   * **1 Jahr**: Das relative Datum wird für Datumsangaben innerhalb eines Jahres angezeigt; ansonsten wird das genaue Datum angegeben.

   * **Immer relatives Datum anzeigen**: Es werden niemals genaue Datumsangaben, sondern nur relative Daten angezeigt.

* **Tastaturbefehle aktivieren**

  AEM unterstützt mehrere Tastaturbefehle, die die Bearbeitung effizienter machen.

   * [Tastaturbefehle für die Seitenbearbeitung](/help/sites-authoring/page-authoring-keyboard-shortcuts.md)
   * [Tastaturbefehle für Konsolen](/help/sites-authoring/keyboard-shortcuts.md)

  Diese Option aktiviert Tastaturbefehle. Sie sind standardmäßig aktiviert, können jedoch deaktiviert werden, z. B. wenn ein Benutzer bestimmte Barrierefreiheitsanforderungen hat.

* **Klassisches Authoring-Erlebnis verwenden**

  Diese Option ermöglicht eine auf der [klassischen Benutzeroberfläche](/help/sites-classic-ui-authoring/home.md) basierende Seitenbearbeitung. Im Normalfall wird die Standard-Benutzeroberfläche verwendet.

* **Asset-Homepage aktivieren**

  Diese Option ist nur verfügbar, wenn Ihr Systemadministrator das Asset-Homepage-Erlebnis für die gesamte Organisation aktiviert hat.

* **Stock-Konfiguration**

  Mit dieser Option können Sie die bevorzugte Adobe Stock-Konfiguration angeben. Sie ist nur verfügbar, wenn Ihr Systemadministrator die Option [Adobe Stock-Integration](/help/assets/aem-assets-adobe-stock.md).
