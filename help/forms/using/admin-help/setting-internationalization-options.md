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
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
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
