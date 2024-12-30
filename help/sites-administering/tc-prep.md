---
title: Vorbereiten von Inhalten für die Übersetzung
description: Erfahren Sie, wie Sie Inhalte für die Übersetzung in Adobe Experience Manager vorbereiten.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 81978733-89a6-4436-bcf1-4bde962ed54f
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 96%

---

# Vorbereiten von Inhalten für die Übersetzung{#preparing-content-for-translation}

Bei mehrsprachigen Websites wird in der Regel ein Teil der Inhalte in mehreren Sprachen bereitgestellt. Die Website wird in einer Sprache verfasst und anschließend in weitere Sprachen übersetzt. Im Allgemeinen bestehen mehrsprachige Websites aus Zweigen von Seiten, wobei jeder Zweig die Seiten der Website in einer anderen Sprache enthält.

Die beispielhafte Geometrixx-Demo-Site umfasst mehrere Sprachzweige und weist die folgende Struktur auf:

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

Jeder Sprachzweig einer Website wird als Sprachkopie bezeichnet. Die Stammseite einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. Beispielsweise stellt `/content/geometrixx/fr` den Sprachstamm der französischen Sprachkopie dar. Sprachkopien müssen einen [korrekt konfigurierten Sprachstamm](/help/sites-administering/tc-prep.md#creating-a-language-root) verwenden, damit die korrekte Sprache angesprochen wird, wenn Übersetzungen von einer Quell-Website durchgeführt werden.

Die Sprachkopie, für die Sie ursprünglich Inhalte verfassen, ist der Sprach-Master. Die Sprach-Master-Vorlage ist die Quelle, die in andere Sprachen übersetzt wird.

Führen Sie die folgenden Schritte aus, um Ihre Website für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Der Sprachstamm der englischen Beispiel-Geometrixx-Website ist z. B. /content/geometrixx/en. Stellen Sie sicher, dass der Sprachstamm entsprechend den Informationen unter [Erstellen eines Sprachstamms](/help/sites-administering/tc-prep.md#creating-a-language-root) konfiguriert ist.
1. Verfassen Sie den Inhalt des Sprach-Masters.
1. Erstellen Sie den Sprachstamm jeder Sprachkopie für die Website. Die Sprachkopie der französischen Geometrixx-Beispiel-Site ist z. B. „/content/geometrixx/fr“.

Wenn Sie die Inhalte für die Übersetzung vorbereitet haben, können Sie automatisch fehlende Seiten in den Sprachkopien und zugehörigen Übersetzungsprojekten erstellen. (Siehe [Erstellen eines Übersetzungsprojekts](/help/sites-administering/tc-manage.md).) Einen Überblick über den Prozess der Inhaltsübersetzung in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Websites](/help/sites-administering/translation.md).

## Erstellen eines Sprachstamms {#creating-a-language-root}

Erstellen Sie einen Sprachstamm als Stammseite einer Sprachkopie, die die Sprache der Inhalte identifiziert. Nachdem Sie den Sprachstamm erstellt haben, können Sie Übersetzungsprojekte erstellen, die die Sprachkopie umfassen.

Um den Sprachstamm zu erstellen, erstellen Sie eine Seite und verwenden Sie einen ISO-Sprach-Code als Wert für die Eigenschaft Name. Der Sprach-Code muss eines der folgenden Formate aufweisen:

* `<language-code>`: Der unterstützte Sprach-Code ist ein Code mit zwei Buchstaben gemäß ISO-639-1, z. B. `en`.

* `<language-code>_<country-code>` oder `<language-code>-<country-code>`: Der unterstützte Länder-Code ist ein Code mit zwei Groß- oder zwei Kleinbuchstaben gemäß ISO 3166, z. B. `en_US`, `en_us`, `en_GB`, `en-gb`.

Sie können jedes dieser Formate verwenden, passend zur Struktur Ihrer globalen Website.  Beispielsweise verfügt die Stammseite der französischen Sprachkopie der Geometrixx-Website über die „Name“-Eigenschaft `fr`. Beachten Sie, dass die Eigenschaft „Name“ als Name des Seitenknotens im Repository verwendet wird und daher den Pfad der Seite bestimmt. (http://localhost:4502/content/geometrixx/fr.html).

Im folgenden Verfahren wird die Touch-optimierte Benutzeroberfläche genutzt, um eine Sprachkopie einer Website zu erstellen. Die entsprechenden Anleitungen für die klassische Benutzeroberfläche finden Sie unter [Erstellen eines Sprachstamms über die klassische Benutzeroberfläche](/help/sites-administering/tc-lroot-classic.md).

1. Navigieren Sie zu „Sites“.
1. Klicken Sie auf die Site, für die Sie eine Sprachkopie erstellen möchten.

   Wenn Sie z. B. eine Sprachkopie der Geometrixx Outdoors-Site erstellen möchten, klicken Sie auf „Geometrixx Outdoors Site“.

1. Klicken Sie auf „Erstellen“ und anschließend auf „Seite erstellen“.

   ![chlimage_1-21](assets/chlimage_1-21a.png)

1. Wählen Sie die Seitenvorlage aus und klicken Sie dann auf „Weiter“.
1. Geben Sie für den Feldtyp „Name“ den Länder-Code im Format `<language-code>` oder `<language-code>_<country-code>` ein, z. B. `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Geben Sie einen Titel für die Seite ein.

   ![chlimage_1-22](assets/chlimage_1-22a.png)

1. Klicken Sie auf „Erstellen“. Klicken Sie im Bestätigungsdialogfeld entweder auf **Fertig**, um zur Sites-Konsole zurückzukehren, oder auf **Öffnen**, um die Sprachkopie zu öffnen.

## Anzeigen des Status der Sprachstämme {#seeing-the-status-of-language-roots}

Die Touch-optimierte Benutzeroberfläche umfasst das Bedienfeld „Verweise“, in dem eine Liste der erstellten Sprachstämme angezeigt wird.

![chlimage_1-23](assets/chlimage_1-23a.png)

Das folgende Verfahren verwendet die Touch-optimierte Benutzeroberfläche, um den Bereich „Verweise“ für eine Seite anzuzeigen.

1. Wählen Sie in der Sites-Konsole eine Seite der Site aus und klicken Sie dann auf **Verweise**.

   ![chlimage_1-24](assets/chlimage_1-24a.png)

1. Klicken Sie im Bedienfeld „Verweise“ auf **Sprachkopien**. Im Bedienfeld „Sprachkopien“ werden die Sprachkopien der Website angezeigt.
