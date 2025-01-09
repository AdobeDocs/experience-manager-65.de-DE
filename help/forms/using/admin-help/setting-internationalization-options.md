---
title: Festlegen der Internationalisierungsoptionen
description: Erfahren Sie, wie Sie das Gebietsschema angeben, das verwendet wird, um Formulare zu rendern, und wie Sie den Zeichensatz angeben, mit dem der Ausgabe-Stream kodiert wird.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 6cf82c2b-29f0-49d5-a138-99d7801d5a28
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: ht
source-wordcount: '236'
ht-degree: 100%

---

# Festlegen der Internationalisierungsoptionen{#setting-internationalization-options}

>[!NOTE]
> 
> Stellen Sie sicher, dass Benutzende über Adminberechtigungen für den Zugriff auf die Administrationskonsole verfügen.

## Festlegen des Gebietsschemas zum Rendern von Formularen {#specify-the-locale-used-to-render-forms}

Sie können das Gebietsschema angeben, das beim Rendern eines PDF-Formulars verwendet wird. Die Felder in einem PDF-Formular verwenden das angegebene Gebietsschema, um Daten anzuzeigen. Wenn das Gebietsschema beispielsweise auf Deutsch festgelegt ist, verwendet das Formular deutsche Dezimaltrennzeichen für numerische Werte. Das Gebietsschema wird außerdem zum Senden von Überprüfungsmeldungen an Client-Anwendungen wie Webbrowser als Teil von HTML-Transformationen verwendet.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „Formulare“.
1. Wählen Sie unter „Internationalisierung“ in der Liste „Sprachen“ das Gebietsschema, das zum Wiedergeben eines Formulars verwendet wird. Der Standardwert ist „Deutsch (Deutschland)“.
1. Klicken Sie auf Speichern.

## Geben Sie den Zeichensatz an, der zum Kodieren des Ausgabe-Streams verwendet wird {#specify-the-character-set-used-to-encode-the-output-stream}

1. Wählen Sie unter „Internationalisierung“ in der Liste „Zeichensatz“ einen Zeichensatz aus. Diese Einstellung hängt von der verwendeten API ab, entweder renderHTMLForm oder renderPDFForm. Um einen anderen Zeichensatz als die aufgelisteten anzugeben, wählen Sie „Benutzerdefiniert“ aus und geben Sie in dem angezeigten Feld einen Codierungswert ein.

   Bei HTML-Transformationen unterstützt AEM Forms Zeichenkodierungswerte, die vom Paket `java.nio.charset` definiert werden. Wenn sFormPreference auf PDFForm festgelegt ist, werden nur bestimmte Zeichensätze unterstützt. Der Zeichensatz muss ein gültiger kanonischer Name sein. Der Standardwert ist ISO-8859-1.

1. Klicken Sie auf Speichern.
