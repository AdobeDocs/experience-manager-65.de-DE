---
title: Vorbereiten von Inhalten für die Übersetzung
description: Erfahren Sie, wie Sie Inhalte für die Übersetzung in Adobe Experience Manager vorbereiten.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 81978733-89a6-4436-bcf1-4bde962ed54f
source-git-commit: 10b370fd8f855f71c6d7d791c272137bb5e04d97
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 56%

---

# Vorbereiten von Inhalten für die Übersetzung{#preparing-content-for-translation}

Bei mehrsprachigen Websites wird in der Regel ein Teil der Inhalte in mehreren Sprachen bereitgestellt. Die Website wird in einer Sprache verfasst und anschließend in weitere Sprachen übersetzt. Im Allgemeinen bestehen mehrsprachige Websites aus Zweigen von Seiten, wobei jeder Zweig die Seiten der Website in einer anderen Sprache enthält.

Die Beispiel-Geometrixx Demosite enthält mehrere Sprachzweige und weist die folgende Struktur auf:

```xml
/content
    |- geometrixx
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Jeder Sprachzweig einer Website wird als Sprachkopie bezeichnet. Die Stammseite einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. Beispielsweise stellt `/content/geometrixx/fr` den Sprachstamm der französischen Sprachkopie dar. Sprachkopien müssen [korrekt konfigurierter Sprachstamm](/help/sites-administering/tc-prep.md#creating-a-language-root) , damit bei der Übersetzung von Quell-Sites die richtige Sprache angesprochen wird.

Die Sprachkopie, für die Sie ursprünglich Inhalte verfassen, ist der Sprach-Master. Die Sprach-Master-Vorlage ist die Quelle, die in andere Sprachen übersetzt wird.

Führen Sie die folgenden Schritte aus, um Ihre Website für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Der Sprachstamm der englischen Beispiel-Geometrixx-Website ist z. B. /content/geometrixx/en. Stellen Sie sicher, dass der Sprachstamm entsprechend den Informationen unter [Erstellen eines Sprachstamms](/help/sites-administering/tc-prep.md#creating-a-language-root) konfiguriert ist.
1. Verfassen Sie den Inhalt des Sprach-Masters.
1. Erstellen Sie den Sprachstamm jeder Sprachkopie für die Website. Beispielsweise lautet die französische Sprachkopie der Geometrixx-Beispiel-Site /content/geometrixx/fr.

Wenn Sie die Inhalte für die Übersetzung vorbereitet haben, können Sie automatisch fehlende Seiten in den Sprachkopien und zugehörigen Übersetzungsprojekten erstellen. (Siehe [Erstellen eines Übersetzungsprojekts](/help/sites-administering/tc-manage.md).) Einen Überblick über den Prozess der Inhaltsübersetzung in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Websites](/help/sites-administering/translation.md).

## Erstellen eines Sprachstamms {#creating-a-language-root}

Erstellen Sie einen Sprachstamm als Stammseite einer Sprachkopie, die die Sprache der Inhalte identifiziert. Nachdem Sie den Sprachstamm erstellt haben, können Sie Übersetzungsprojekte erstellen, die die Sprachkopie umfassen.

Um den Sprachstamm zu erstellen, erstellen Sie eine Seite und verwenden Sie einen ISO-Sprach-Code als Wert für die Eigenschaft Name. Der Sprach-Code muss eines der folgenden Formate aufweisen:

* `<language-code>`Der unterstützte Sprachcode ist ein aus zwei Buchstaben bestehender Code gemäß ISO-639-1, beispielsweise: `en`.

* `<language-code>_<country-code>` oder `<language-code>-<country-code>`Der unterstützte Ländercode ist ein aus zwei Kleinbuchstaben bestehender Code mit zwei Buchstaben in Kleinbuchstaben oder Großbuchstaben gemäß ISO 3166, beispielsweise: `en_US`, `en_us`, `en_GB`, `en-gb`.

Sie können jedes dieser Formate verwenden, passend zur Struktur Ihrer globalen Website.  Beispielsweise verfügt die Stammseite der französischen Sprachkopie der Geometrixx-Website über die „Name“-Eigenschaft `fr`. Die Eigenschaft &quot;Name&quot;wird als Name des Seitenknotens im Repository verwendet und bestimmt daher den Pfad der Seite. (http://localhost:4502/content/geometrixx/fr.html)

Im folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche verwendet, um eine Sprachkopie einer Website zu erstellen. Anweisungen zur Verwendung der klassischen Benutzeroberfläche finden Sie unter [Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche](/help/sites-administering/tc-lroot-classic.md).

1. Navigieren Sie zu Sites .
1. Klicken Sie auf die Site, für die Sie eine Sprachkopie erstellen möchten.

   Wenn Sie beispielsweise eine Sprachkopie der Geometrixx Outdoors-Site erstellen möchten, klicken Sie auf Geometrixx Outdoors-Site.

1. Klicken Sie auf Erstellen und dann auf Seite erstellen .

   ![chlimage_1-21](assets/chlimage_1-21a.png)

1. Wählen Sie die Seitenvorlage aus und klicken Sie auf Weiter.
1. Geben Sie in das Feld Name den Ländercode im Format `<language-code>` oder `<language-code>_<country-code>`, beispielsweise `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Geben Sie einen Titel für die Seite ein.

   ![chlimage_1-22](assets/chlimage_1-22a.png)

1. Klicken Sie auf „Erstellen“. Klicken Sie im Bestätigungsdialogfeld auf **Fertig** zur Konsole &quot;Sites&quot;zurückzukehren oder **Öffnen** , um die Sprachkopie zu öffnen.

## Anzeigen des Status der Sprachstämme {#seeing-the-status-of-language-roots}

Die Touch-optimierte Benutzeroberfläche bietet einen Bereich &quot;Verweise&quot;, der eine Liste der erstellten Sprachstämme anzeigt.

![chlimage_1-23](assets/chlimage_1-23a.png)

Das folgende Verfahren verwendet die Touch-optimierte Benutzeroberfläche, um den Bereich „Verweise“ für eine Seite anzuzeigen.

1. Wählen Sie in der Sites-Konsole eine Seite der Site aus und klicken Sie auf **Verweise**.

   ![chlimage_1-24](assets/chlimage_1-24a.png)

1. Klicken Sie im Bereich &quot;Verweise&quot;auf **Sprachkopien**. Im Bereich Sprachkopien werden die Sprachkopien der Website angezeigt.
