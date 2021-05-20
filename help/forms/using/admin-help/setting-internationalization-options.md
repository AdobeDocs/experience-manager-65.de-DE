---
title: Internationalisierungsoptionen festlegen
seo-title: Internationalisierungsoptionen festlegen
description: Erfahren Sie, wie Sie das Gebietsschema angeben, das verwendet wird, um Formulare zu rendern, und wie Sie den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird.
seo-description: Erfahren Sie, wie Sie das Gebietsschema angeben, das verwendet wird, um Formulare zu rendern, und wie Sie den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 6cf82c2b-29f0-49d5-a138-99d7801d5a28
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 100%

---

# Internationalisierungsoptionen festlegen{#setting-internationalization-options}

## Gebietsschema zum Wiedergeben von Formularen angeben {#specify-the-locale-used-to-render-forms}

Sie können das Gebietsschema angeben, dass beim Wiedergeben eines PDF-Formulars verwendet wird. Die Felder in einem PDF-Formular verwenden das angegebene Gebietsschema, um Daten anzuzeigen. Wenn beispielsweise das Gebietsschema für Deutsch festgelegt wird, verwendet das Formular deutsche dezimale Trennzeichen für numerische Werte. Das Gebietsschema wird außerdem zum Senden von Überprüfungsmeldungen an Clientanwendungen wie Webbrowser als Teil von HTML-Transformationen verwendet.

1. Klicken Sie in Administration Console auf „Dienste“ > „Forms“.
1. Wählen Sie unter „Internationalisierung“ in der Liste „Sprachen“ das Gebietsschema, das zum Wiedergeben eines Formulars verwendet wird. Der Standardwert ist „Deutsch (Deutschland)“.
1. Klicken Sie auf Speichern.

## Den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird {#specify-the-character-set-used-to-encode-the-output-stream}

1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung hängt von der verwendeten API ab, entweder „renderHTMLForm“ oder „renderPDFForm“. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen kodierten Wert ein.

   Bei HTML-Transformationen unterstützt AEM Forms Zeichenkodierungswerte, die vom Paket `java.nio.charset` definiert werden. Wenn sFormPreference auf PDFForm festgelegt ist, werden nur bestimmte Zeichensätze unterstützt. Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist „ISO-8859-1“.

1. Klicken Sie auf Speichern.
