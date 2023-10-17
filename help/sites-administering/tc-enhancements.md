---
title: Verbesserungen an der Übersetzung
description: Inkrementelle Verbesserungen und Verbesserungen bei AEM Übersetzungsmanagement-Funktionen.
topic-tags: site-features
content-type: reference
feature: Language Copy
exl-id: 2011a976-d506-4c0b-9980-b8837bdcf5ad
source-git-commit: eaffc71c23c18d26ec5cbb2bbb7524790c4826fe
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 83%

---

# Verbesserungen an der Übersetzung{#translation-enhancements}

Auf dieser Seite werden schrittweise Verbesserungen und Verbesserungen AEM Übersetzungsmanagementfunktionen vorgestellt.

## Automatisierung von Übersetzungsprojekten {#translation-project-automation}

Es wurden Optionen zur Verbesserung der Produktivität bei der Arbeit mit Übersetzungsprojekten hinzugefügt, z. B. zum automatischen Hervorheben und Löschen von Übersetzungsstarts und zum Planen der wiederholten Ausführung eines Übersetzungsprojekts.

1. Klicken oder tippen Sie in Ihrem Übersetzungsprojekt unten auf der Kachel **Zusammenfassung der Übersetzung** auf die Auslassungspunkte.

   ![screen_shot_2018-04-19at222622](assets/screen_shot_2018-04-19at222622.jpg)

1. Wechseln Sie zur Registerkarte **Erweitert**. Unten können Sie die Option **Übersetzungsstarts automatisch hervorheben** wählen.

   ![screen_shot_2018-04-19at223430](assets/screen_shot_2018-04-19at223430.jpg)

1. Optional können Sie auswählen, ob Übersetzungsstarts nach Erhalt des Übersetzungsinhalts automatisch hervorgehoben und gelöscht werden sollen.

   ![screen_shot_2018-04-19at224033](assets/screen_shot_2018-04-19at224033.jpg)

1. Um die wiederholte Ausführung eines Übersetzungsprojekts festzulegen, wählen Sie die Häufigkeit in der Dropdown-Liste **Übersetzung wiederholen** aus. Bei der wiederholten Projektausführung werden Übersetzungsaufträge in den angegebenen Intervallen automatisch erstellt und ausgeführt.

   ![screen_shot_2018-04-19at223820](assets/screen_shot_2018-04-19at223820.jpg)

## Mehrsprachige Übersetzungsprojekte {#multilingual-translation-projects}

Es ist möglich, mehrere Zielsprachen in einem Übersetzungsprojekt zu konfigurieren, um die Anzahl der insgesamt erstellten Übersetzungsprojekte zu reduzieren.

1. Klicken oder tippen Sie in Ihrem Übersetzungsprojekt unten auf der Kachel **Zusammenfassung der Übersetzung** auf die Punkte.

   ![screen_shot_2018-04-19at222622](assets/screen_shot_2018-04-19at222622.jpg)

1. Wechseln Sie zur Registerkarte **Erweitert**. Sie können unter **Zielsprache** mehrere Sprachen hinzufügen.

   ![screen_shot_2018-04-22at212601](assets/screen_shot_2018-04-22at212601.jpg)

1. Falls Sie die Übersetzung über die Verweisleiste in Sites initiieren, können Sie alternativ hierzu Sprachen hinzufügen und die Option **Mehrsprachiges Übersetzungsprojekt erstellen** wählen.

   ![screen_shot_2018-04-22at212941](assets/screen_shot_2018-04-22at212941.jpg)

1. Im Projekt werden Übersetzungsaufträge für jede Zielsprache erstellt. Sie können entweder einzeln im Projekt oder gemeinsam gestartet werden, indem das Projekt global auf der Admin-Ebene für Projekte ausgeführt wird.

   ![screen_shot_2018-04-22at213854](assets/screen_shot_2018-04-22at213854.jpg)

## Translation-Memory-Aktualisierungen {#translation-memory-updates}

Für manuelle Bearbeitungen von übersetzten Inhalten kann eine Synchronisierung mit dem Translation Management System (TMS) durchgeführt werden, um das Translation Memory zu trainieren.

1. Wählen Sie in der Sites-Konsole nach dem Aktualisieren des Textinhalts auf einer übersetzten Seite die Option **Translation Memory aktualisieren** aus.

   ![screen_shot_2018-04-22at234430](assets/screen_shot_2018-04-22at234430.jpg)

1. In einer Listenansicht werden die Quelle und die Übersetzung für jede bearbeitete Textkomponente nebeneinander verglichen. Wählen Sie aus, welche Übersetzungsaktualisierungen mit der Translation Memory synchronisiert werden sollen, und wählen Sie die Option **Speicher aktualisieren** aus.

   ![screen_shot_2018-04-22at235024](assets/screen_shot_2018-04-22at235024.jpg)

AEM aktualisiert die Übersetzung der vorhandenen Zeichenfolgen im Translation Memory des konfigurierten TMS.

* Die Aktion aktualisiert die Übersetzung vorhandener Zeichenfolgen im Translation Memory des konfigurierten TMS.
* Es werden keine neuen Übersetzungsvorgänge erstellt.
* Die Übersetzungen werden über die AEM-Übersetzungs-API an das TMS zurückgesendet (siehe unten).

So verwenden Sie diese Funktion:

* Ein TMS muss für die Verwendung mit AEM konfiguriert werden.
* Der Connector muss die Methode [`storeTranslation`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/translation/api/TranslationService.html) implementieren.
   * Der Code innerhalb dieser Methode bestimmt, was mit der Aktualisierungsanfrage für das Translation Memory geschieht.
   * Das AEM-Übersetzungs-Framework sendet die Zeichenfolgenwertpaare (ursprüngliche und aktualisierte Übersetzung) über diese Methodenimplementierung zurück an das TMS.

Die Aktualisierungen des Translation Memory können auch umgeleitet und an ein benutzerdefiniertes Ziel gesendet werden, wenn ein proprietäres Translation Memory verwendet wird.

## Sprachkopien auf mehreren Ebenen {#language-copies-on-multiple-levels}

Sie können Sprach-Stämme jetzt unter Knoten gruppieren, z. B. nach Region. Diese werden weiterhin als Stämme von Sprachkopien erkannt.

![screen_shot_2018-04-23at144012](assets/screen_shot_2018-04-23at144012.jpg)

>[!CAUTION]
>
>Hierbei ist nur eine Ebene zulässig. Beispielsweise lässt Folgendes nicht zu, dass die Seite &quot;es&quot;in eine Sprachkopie aufgelöst wird:
>
>* `/content/we-retail/language-masters/en`
>* `/content/we-retail/language-masters/americas/central-america/es`
>
>Die Sprachkopie `es` wird nicht erkannt, da sie zwei Ebenen (americas/central-america) vom Knoten `en` entfernt ist.

>[!NOTE]
>
>Sprachstämme können einen beliebigen Seitennamen haben, nicht nur den ISO-Code der Sprache. AEM prüft immer zuerst den Pfad und den Namen, aber wenn der Seitenname keine Sprache identifiziert, überprüft AEM die Eigenschaft cq:language der Seite auf die Sprachkennung.

## Berichte zum Übersetzungsstatus {#translation-status-reporting}

Eine Eigenschaft kann jetzt in der Sites-Listenansicht ausgewählt werden, die anzeigt, ob eine Seite übersetzt wurde, sich in der Übersetzung befindet oder noch nicht übersetzt wurde. Sie können dies wie folgt anzeigen:

1. Wechseln Sie in Sites zur **Listenansicht**.

   ![screen_shot_2018-04-23at130646](assets/screen_shot_2018-04-23at130646.jpg)

1. Klicken oder tippen Sie auf **Anzeigeeinstellungen**.

   ![screen_shot_2018-04-23at130844](assets/screen_shot_2018-04-23at130844.jpg)

1. Aktivieren Sie unter **Übersetzung** das Kontrollkästchen **Übersetzt** und tippen bzw. klicken Sie auf **Aktualisieren**.

   ![screen_shot_2018-04-23at130955](assets/screen_shot_2018-04-23at130955.jpg)

Die Spalte **Übersetzt** mit dem Übersetzungsstatus der Seiten wird angezeigt.

![screen_shot_2018-04-23at133821](assets/screen_shot_2018-04-23at133821.jpg)
