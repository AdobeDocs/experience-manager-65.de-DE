---
title: Anzeigen und Verstehen der Analytics-Berichte in AEM Forms
description: AEM Forms kann mit Adobe Analytics integriert werden und bietet Ihnen eine Zusammenfassung und detaillierte Analysen zu Ihren veröffentlichten adaptiven Formularen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: c5a4e6f6-f331-41e9-a0a9-51a30df6e2cd
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '1056'
ht-degree: 100%

---

# Anzeigen und Verstehen der Analytics-Berichte in AEM Forms {#view-and-understand-aem-forms-analytics-reports}

Adobe Experience Manager Forms ermöglicht die Integration in Adobe Analytics, sodass Sie Leistungsmetriken für Ihre veröffentlichten Formulare und Dokumente erfassen und verfolgen können. Ziel dieser Analyse ist es, informierte, auf Daten basierende Entscheidungen zu erforderlichen Formularänderungen treffen zu können, durch die Formulare oder Dokumente benutzerfreundlicher werden.

## Einrichten von Analysen {#setting-up-analytics}

Die Analysefunktion in AEM Forms ist als Teil des AEM Forms-Add-On-Pakets verfügbar. Weitere Informationen zum Installieren des Add-On-Pakets finden Sie unter [Installieren und Konfigurieren von AEM Forms](../../forms/using/installing-configuring-aem-forms-osgi.md).

Zusätzlich zum Add-On-Paket benötigen Sie ein Adobe Analytics-Konto. Informationen zur Lösung finden Sie unter [Adobe Analytics](https://www.adobe.com/de/solutions/digital-analytics.html).

Wenn Sie über das Add-On-Paket für AEM Forms und ein Adobe Analytics-Konto verfügen, integrieren Sie das Adobe Analytics-Konto in AEM Forms und aktivieren Sie das Tracking in Ihren Formularen oder Dokumenten, wie unter [Konfigurieren von Analysen und Berichten](../../forms/using/configure-analytics-forms-documents.md) beschrieben.

### Aufzeichnung von Informationen zu Benutzerinteraktionen {#how-user-interaction-information-is-recorded}

Wenn eine Benutzerin bzw. ein Benutzer mit dem Formular interagiert, werden die Interaktionen aufgezeichnet und an den Analytics-Server gesendet. Die folgende Liste zeigt Server-Aufrufe für verschiedene Benutzeraktivitäten:

* 2 Aufrufe pro Feld pro Besuch
* 1 für Bereichsbesuch
* 1 für Speichern
* 2 für Übermitteln
* 2 für Speichern
* 1 für Hilfe
* 1 für jeden Validierungsfehler
* 1 für Formular-Ausgabedarstellung + 1 für standardmäßigen Bereichsbesuch + 1 für standardmäßigen ersten Feldbesuch
* 2 für Formularabbruch

>[!NOTE]
>
>Diese Liste ist nicht vollständig.

### Anzeigen von Analytics-Berichten {#summary-report}

Führen Sie die folgenden Schritte aus, um Analytics-Berichte anzuzeigen:

1. Melden Sie sich unter `https://[hostname]:'port'` beim AEM-Portal an
1. Klicken Sie auf **Formulare > Formulare und Dokumente**.
1. Wählen Sie das Formular aus, für das Sie die Analytics-Berichte anzeigen möchten.
1. Wählen Sie **Mehr > Analytics-Berichte** aus.

![analyticsreport](assets/analyticsreport.png)

**A.** Analytics-Berichtsbefehl

AEM Forms zeigt Analytics-Berichte für das Formular und für jeden Bereich im Formular an, wie unten dargestellt.

![Zusammenfassungsbericht eines adaptiven Formulars](assets/analyticsdashboard_callout.png)

**A.** Konvertierungen **B.** Zusammenfassung auf Formularebene **C.** Zusammenfassung auf Bereichsebene **D.** Browser der Besucher – Filter **E.** Betriebssystem der Besucher – Filter **F.** Sprache der Besucher – Filter

Standardmäßig wird der Analysebericht für die letzten sieben Tage angezeigt. Sie können Berichte für die letzten 15 Tage, den letzten Monat usw. anzeigen oder einen Datumsbereich angeben.

>[!NOTE]
>
>Die Optionen wie „Letzte 7 Tage“ und „Letzte 15 Tage“ enthalten keine Daten für den Tag, an dem Sie den Analysebericht generieren. Um die Daten des aktuellen Tages einzubeziehen, müssen Sie den Datumsbereich einschließlich des aktuellen Tages angeben und dann den Bericht ausführen.

![date-range](assets/date-range.png)

### Konversionsdiagramm für adaptive und HTML5-Formulare {#conversions-graph-for-adaptive-and-html-forms}

Das Konversionsdiagramm auf Formularebene bietet Ihnen einen Einblick in die Leistung des Formulars in Bezug auf die folgenden wichtigen Leistungsindikatoren (KPIs):

* **Ausgabedarstellungen**: Gibt an, wie oft ein Formular geöffnet wurde
* **Besuchende**: Die Anzahl der Besuchenden des Formulars
* **Übermittlungen**: Angabe, wie oft ein Formular übermittelt wird

![conversion-graph](assets/conversion-graph.png)

### Analysebericht für adaptive und HTML5-Formulare {#analytics-report-for-adaptive-and-html-forms}

Im Zusammenfassungsabschnitt auf Formularebene erhalten Sie einen Einblick in die Leistung des Formulars in Bezug auf die folgenden wichtigen Leistungsindikatoren (KPIs):

* **Durchschnittliche Füllzeit**: Durchschnittliche Zeit, die für das Ausfüllen des Formulars verwendet wird. Wenn Benutzer Zeit aufwenden, um das Formular auszufüllen, es aber nicht abschicken, dann wird diese Zeit in dieser Berechnung nicht berücksichtigt.
* **Ausgabeformate**: Gibt an, wie oft das Formular wiedergegeben oder geöffnet wurde
* **Entwürfe**: Gibt an, wie oft das Formular als Entwurf gespeichert wurde.
* **Übermittlungen**: Gibt an, wie oft das Formular übermittelt wurde.
* **Abbruch**: Gibt an, wie oft Benutzende das Ausfüllen des Formulars begonnen und dann abgebrochen haben
* **Unique Visitors**: Gibt an, wie oft das Formular von einzelnen Besuchern erstellt wird. Weitere Informationen über individuelle Besucher finden Sie unter [Individuelle Besicher, Besuche und Kundenverhalten](https://helpx.adobe.com/de/analytics/kb/unique-visitors-visitor-behavior.html). 

![Erweiterter zusammenfassender Analysebericht auf Formularebene](assets/analytics-report.png)

### Bereichsbericht {#bottom-summary-report}

Die Zusammenfassung auf Bereichsebene enthält die folgenden Informationen zu den einzelnen Bereichen im Formular:

* **Durchschnittliche Füllzeit**: Durchschnittlich aufgewandte Zeit im Bereich, egal ob das Formular übermittelt wurde oder nicht 
* **Aufgetretene Fehler**: Durchschnittliche Anzahl der Fehler, auf die die Benutzer in Feldern eines Bereichs gestoßen sind. „Aufgetretene Fehler“ wird berechnet, indem die Gesamtzahl der Fehler in einem Feld durch die Zahl der Ausgabedarstellungen des Formulars dividiert wird. 
* **Zugriff auf Hilfe**: Durchschnittliche Anzahl der Aufrufe der kontextbezogenen Hilfe für die Felder im Bereich. „Zugriff auf Hilfe“ wird berechnet, indem die Gesamtzahl der Hilfe-Aufrufe eines Feldes durch die Zahl der Ausgabedarstellungen des Formulars dividiert wird.

#### Detaillierter Bedienfeldbericht {#detailed-panel-report}

Sie können auch Details für jedes Bedienfeld anzeigen, indem Sie auf den Namen eines Bedienfelds im Bedienfeldbericht klicken.

![Detaillierter Bereichsbericht](assets/panel-report-detailed.png)

Der detaillierte Bericht zeigt Werte für alle Felder im Bedienfeld an.

Der Bedienfeldbericht hat drei Registerkarten:

* **Zeitbericht** (Standard): Zeigt die Zeit in Sekunden an, die damit verbracht wurde, jedes Feld im Bereich auszufüllen
* **Fehlerbericht**: Zeigt die Anzahl der Fehler, die von den Benutzern beim Ausfüllen der Felder gefunden wurden
* **Hilfebericht**: Anzahl der Hilfeaufrufe für ein bestimmtes Feld

Sie können zwischen den Bereichen navigieren, wenn mehrere Bereiche verfügbar sind.

### Filter: Browser, Betriebssystem und Sprache {#filters-browser-os-and-language}

Die Tabellen „Browser-Verteilung“, „Betriebssystemverteilung“ und „Sprachverteilung“ zeigen die Ausgabedarstellungen, Besuchenden und Übermittlungen gemäß Browser, Betriebssystem und Sprache der Benutzerinnen und Benutzer des Formulars an. Diese Tabellen zeigen standardmäßig maximal fünf Einträge an. Sie können auf „Mehr anzeigen“ klicken, um weitere Einträge anzuzeigen, und auf „Weniger anzeigen“, um zu den fünf oder weniger regulären Einträgen zurückzukehren.

Um die Analysedaten weiter zu filtern, können Sie auf einen Eintrag in einer der Tabellen klicken. Wenn Sie beispielsweise in der Tabelle „Browser-Verteilung“ auf Google Chrome klicken, wird der Bericht erneut mit den für den Google Chrome-Browser relevanten Daten wie folgt gerendert:

![Filter angewendet auf Analytics-Bericht - Google Chrome ](assets/filter-1.png)

Wenn Sie den Bereichsbericht anzeigen, nachdem Sie einen Filter angewendet haben, werden die Bereichsberichtdaten auch in Übereinstimmung mit dem angewendeten Filter angezeigt.

 Sobald ein Filter angewendet wird:

* Die Verteilungstabellen sind schreibgeschützt, da jeweils nur ein Filter angewendet werden kann.
* Die Tabelle des angewendeten Filters wird nicht mehr angezeigt.
* Sie können auf die Schaltfläche „Schließen“ klicken (unten hervorgehoben), um den angewendeten Filter zu entfernen.

![Schließen-Schaltfläche zum Entfernen des angewendeten Filters](assets/close-filter.png)

### A/B-Tests {#a-b-testing}

Wenn Sie A/B-Tests aktiviert und für das Formular eingerichtet haben, verfügt die Berichtseite über eine Dropdown-Liste, mit der Sie den A/B-Test-Bericht anzeigen können. Der A/B-Test-Bericht zeigt den Leistungsvergleich zweier Versionen des Formulars an, die Sie eingerichtet haben. 

Weitere Informationen zu A/B-Tests finden Sie unter [Erstellen und Verwalten von A/B-Test für adaptive Formulare](../../forms/using/ab-testing-adaptive-forms.md).
