---
title: Festlegen der Internationalisierungsoptionen
description: Erfahren Sie, wie Sie das Gebietsschema angeben, das zum Rendern von Formularen verwendet wird, und wie Sie den Zeichensatz angeben, der zum Kodieren des Ausgabestreams verwendet wird.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6cf82c2b-29f0-49d5-a138-99d7801d5a28
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 32%

---

# Festlegen der Internationalisierungsoptionen{#setting-internationalization-options}

## Festlegen des Gebietsschemas zum Rendern von Formularen {#specify-the-locale-used-to-render-forms}

Sie können das Gebietsschema angeben, das beim Rendern eines PDF-Formulars verwendet wird. Die Felder in einem PDF-Formular verwenden das angegebene Gebietsschema, um Daten anzuzeigen. Wenn das Gebietsschema beispielsweise auf Deutsch festgelegt ist, verwendet das Formular deutsche Dezimaltrennzeichen für numerische Werte. Das Gebietsschema wird auch zum Senden von Validierungsmeldungen an Clientgeräte wie Webbrowser im Rahmen von HTML-Transformationen verwendet.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Wählen Sie unter &quot;Internationalisierung&quot;in der Liste &quot;Sprache&quot;das Gebietsschema aus, das zum Rendern eines Formulars verwendet wird. Der Standardwert ist Englisch (USA).
1. Klicken Sie auf Speichern.

## Geben Sie den Zeichensatz an, der zum Kodieren des Ausgabe-Streams verwendet wird {#specify-the-character-set-used-to-encode-the-output-stream}

1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung hängt von der verwendeten API ab, entweder renderHTMLForm oder renderPDFForm. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen Codierungswert ein.

   Bei HTML-Transformationen unterstützt AEM Forms Zeichenkodierungswerte, die vom Paket `java.nio.charset` definiert werden. Wenn sFormPreference auf PDFForm festgelegt ist, werden nur bestimmte Zeichensätze unterstützt. Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist ISO-8859-1.

1. Klicken Sie auf Speichern.
