---
title: Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche
description: Erfahren Sie, wie Sie mithilfe der klassischen Benutzeroberfläche einen Sprachstamm in Adobe Experience Manager erstellen.
contentOwner: Guillaume Carlino
feature: Language Copy
exl-id: 1ae21d80-0683-4ab9-afaa-4d733ff47720
solution: Experience Manager, Experience Manager Sites
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: d9d38edd-df1b-480c-8f5e-72b62576f390
    internal-label: Site and page features
subfeature_v2:
  - id: e15a4109-ae5d-497d-b301-31149e35aed4
    internal-label: Language Copy Wizard
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 98%
---
# Erstellen eines Sprachstamms mithilfe der klassischen Benutzeroberfläche{#creating-a-language-root-using-the-classic-ui}

Im folgenden Verfahren wird die klassische Benutzeroberfläche zum Erstellen eines Sprachstamms einer Site verwendet. Weitere Informationen hierzu finden Sie unter [Erstellen eines Sprachstamms](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. Wählen Sie in der Websites-Konsole in der Baumstruktur „Websites“ die Stammseite der Site aus. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Fügen Sie eine neue untergeordnete Seite hinzu, die der Sprachversion der Site entspricht:

   1. Klicken Sie auf „Neu“ > „Neue Seite“.
   1. Geben Sie in das Dialogfeld den Titel und den Namen ein. Der Name muss im Format `<language-code>` oder `<language-code>_<country-code>` vorliegen, beispielsweise „en“, „en_US“, „en_us“, „en_GB“, „en_gb“.

      * Der unterstützte Sprach-Code ist ein aus zwei Buchstaben bestehender Code in Kleinbuchstaben gemäß ISO-639-1.
      * Der unterstützte Länder-Code ist ein aus zwei Buchstaben bestehender Code in Klein- oder Großbuchstaben gemäß ISO-3166.

   1. Wählen Sie die Vorlage aus und klicken Sie auf „Erstellen“.

   ![newpagefr](assets/newpagefr.png)

1. Wählen Sie in der Websites-Konsole in der Baumstruktur „Websites“ die Stammseite der Site aus.
1. Wählen Sie im Menü „Tools“ die Option „Sprachkopie“ aus.

   ![toolslanguagecopy](assets/toolslanguagecopy.png)

   Das Dialogfeld „Sprachkopie“ zeigt eine Matrix der verfügbaren Sprachversionen und Web-Seiten an. Ein X in einer Sprachspalte bedeutet, dass die Seite in dieser Sprache verfügbar ist.

   ![languagecopydialog](assets/languagecopydialog.png)

1. Um eine vorhandene Seite oder Seitenbaumstruktur in eine Sprachversion zu kopieren, wählen Sie die Zelle für diese Seite in der Sprachspalte aus. Klicken Sie auf den Pfeil und wählen Sie den Typ der zu erstellenden Kopie aus.

   Im folgenden Beispiel wird die Seite „equipment/sunglasses/irian“ in die französische Sprachversion kopiert.

   ![languagecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Art der Sprachkopie | Beschreibung |
   |---|---|
   | auto | Übernimmt das Verhalten der übergeordneten Seiten |
   | ignore | Erstellt keine Kopie dieser Seite und ihrer untergeordneten Elemente |
   | `<language>+`(z. B. Französisch+) | Kopiert die Seite und alle untergeordneten Elemente aus dieser Sprache |
   | `<language>`(z. B. Französisch) | Kopiert nur die Seite aus dieser Sprache |

1. Klicken Sie auf „OK“, um das Dialogfeld zu schließen.
1. Klicken Sie im nächsten Dialogfeld auf „Ja“, um die Kopie zu bestätigen.
